# Data Import Guide

This document describes how to refresh NHS data in Haresign.net from PracticeConnect (PC).

---

## Overview

Haresign.net stores data locally in its own PostgreSQL database.
Data is sourced from PracticeConnect via NDJSON exports and imported using Django management commands or the admin UI.

All commands below are run **on the host machine** (not inside a container).

---

## 1. Online Consultations (OC) Data

### One-liner (export from PC → import to Haresign)

```bash
docker exec practiceconnect-prod-web-1 python manage.py export_oc_data_json \
  | docker exec -i HaresignDotNet python manage.py import_oc_data_json
```

This streams ~2 million rows directly between containers without writing to disk.
Expected duration: 5–15 minutes depending on server load.

### Export to file first (then upload via admin UI)

```bash
# Export from PracticeConnect to a local file
docker exec practiceconnect-prod-web-1 python manage.py export_oc_data_json \
  > /tmp/oc_export.ndjson

# Then upload via admin: /admin/online_consultations/onlineconsultationimportlog/import-tool/
```

### Admin UI

Navigate to **Admin → Online Consultations → Import Tool** (`/admin/online_consultations/onlineconsultationimportlog/import-tool/`).

- Shows current row counts, practice count, and latest data month
- Upload an NDJSON file directly from your browser
- Options: clear existing data, monthly-only, time-only

### Management command flags

```
python manage.py import_oc_data_json [options]

  --file PATH      Read from a file instead of stdin
  --clear          Delete all existing OC data before importing
  --monthly-only   Only import monthly metrics (skip time-of-day)
  --time-only      Only import time-of-day metrics (skip monthly)
```

### ⚠️ PC export command not in image

The export command `export_oc_data_json` was added to PracticeConnect after its image was built.
If the PC container is recreated, the command must be copied in again:

```bash
docker cp \
  /opt/projects/practiceconnect-prod/modules/tools/online_consultations/management/commands/export_oc_data_json.py \
  practiceconnect-prod-web-1:/app/modules/tools/online_consultations/management/commands/export_oc_data_json.py
```

Verify it's available:

```bash
docker exec practiceconnect-prod-web-1 python manage.py export_oc_data_json --help
```

---

## 2. Prevalence Data

Prevalence data covers QOF register counts (disease prevalence by practice).

### One-liner

```bash
docker exec practiceconnect-prod-web-1 python manage.py export_prevalence_json \
  | docker exec -i HaresignDotNet python manage.py import_prevalence_json
```

### Management command flags

```
python manage.py import_prevalence_json [options]

  --file PATH   Read from a file instead of stdin
  --clear       Delete all existing prevalence data before importing
```

---

## 3. PCN / Practice Reference Data

PCN and practice mapping data is imported from NHS Digital / NHSPS CSV files.

```bash
# Import practice data (ODS)
docker exec HaresignDotNet python manage.py import_practices --file /path/to/practices.csv

# Import PCN data
docker exec HaresignDotNet python manage.py import_pcns --file /path/to/pcns.csv
```

> Check `website/management/commands/` for the exact command names and available flags.

---

## 4. Rebuilding After Container Recreation

After rebuilding the Haresign container (e.g. code changes), run migrations and verify:

```bash
docker compose up -d --build haresign_net
docker exec HaresignDotNet python manage.py migrate
docker exec HaresignDotNet python manage.py check
docker exec HaresignDotNet python manage.py test website --noinput
```

Data in the PostgreSQL container (`HaresignPostgres`) persists independently and does **not** need to be re-imported after a Haresign rebuild.

---

## 5. Verifying Imports

```bash
# Check row counts
docker exec HaresignDotNet python manage.py shell -c "
from online_consultations.models import OnlineConsultationMonthlyMetric, OnlineConsultationTimeMetric
print('Monthly:', OnlineConsultationMonthlyMetric.objects.count())
print('Time:', OnlineConsultationTimeMetric.objects.count())
"

# View recent import logs via admin
# /admin/online_consultations/onlineconsultationimportlog/
```


On your GDP question
"Replacing with exact published figures" meant swapping my hand-keyed approximations for the real HMT numbers — which I've now done. I pulled the official March 2026 release ("GDP deflators at market prices, and money GDP"), parsed the spreadsheet, and dropped the real index (2024/25 = 100) into GDP_DEFLATOR_INDEX. The factors now match exactly (e.g. 2020/21 → ×1.1751, i.e. 100 ÷ 85.10).

How to refresh it in future (HMT updates ~quarterly):

Go to the GDP deflators collection on gov.uk and open the newest release.
Download the .xlsx. In the financial-year table, column B is the year (2024-25), column C is the index (2024-25 = 100).
Copy the values into GDP_DEFLATOR_INDEX in services.py, converting dashes to slashes (2024-25 → 2024/25). _deflators() auto-picks the latest year as the base, so no other change needed.
I've saved that procedure to project memory so it's on hand next time.


## 6. List Size (Registered Patients) Data

The `list_size` tool uses NHS Digital's monthly **"Patients Registered at a GP
Practice"** (PDS) publication. Unlike OC/prevalence, this data is **not** exported
from PracticeConnect — the source files are downloaded manually from NHS Digital
(digital.nhs.uk is Cloudflare-blocked, so it can't be auto-fetched) and dropped
into `seeddata/listsize/`.

### Dropping in a month

Create a folder per month under `seeddata/listsize/` (the folder name is free —
the month is read from each file's `EXTRACT_DATE` column) containing **two** files:

```
seeddata/listsize/2026-06/
  gp-reg-pat-prac-quin-age.csv   # REQUIRED — master (all org levels × age × sex)
  gp-reg-pat-prac-map.csv        # recommended — org names + hierarchy
```

The other published files (`-all`, `-sing-age-*`) are ignored. `seeddata/listsize/`
is git-ignored and bind-mounted into both `haresign_net` and `qcluster`.

### Importing

```bash
docker compose exec haresign_net python manage.py import_list_size          # import new months in the folder
docker compose exec haresign_net python manage.py import_list_size --force  # re-import months already loaded
```

Already-loaded months are skipped automatically. Each `quin-age` file is paired
with the `map` file for the **same month** (by EXTRACT_DATE, not filename), so a
flat dump of many months into one folder still maps correctly. There is also a
staff web importer at `/tools/manage/list-size/`.

### Maps, geocoding & the monthly schedule

```bash
# Boundary GeoJSON for the choropleth maps (ONS Open Geography → uploads/listsize_geo)
docker compose exec haresign_net python manage.py fetch_boundaries

# Geocode practice postcodes for the "local landscape (within X miles)" panel (postcodes.io)
docker compose exec haresign_net python manage.py geocode_practices          # --force to re-do

# Register the monthly django-q job that re-runs fetch_boundaries (run once)
docker compose exec haresign_net python manage.py ensure_listsize_schedules
```

### One-time setup after a fresh deploy

Data and runtime state aren't in git, so on a new environment run:

```bash
docker compose exec haresign_net python manage.py migrate
docker compose exec haresign_net python manage.py import_list_size
docker compose exec haresign_net python manage.py geocode_practices
docker compose exec haresign_net python manage.py ensure_listsize_schedules
docker compose exec haresign_net python manage.py fetch_boundaries
```

### Verifying

```bash
docker compose exec haresign_net python manage.py shell -c "
from modules.data.list_size.models import ListSizeSnapshot, PracticeLocation
from django.db.models import Count
print('Org-month rows:', ListSizeSnapshot.objects.count())
print('Months:', ListSizeSnapshot.objects.values('month').distinct().count())
print('Geocoded practices:', PracticeLocation.objects.count())
print(list(ListSizeSnapshot.objects.values('org_type').annotate(n=Count('id'))))
"
```