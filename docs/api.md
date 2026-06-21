# Developer API

The Haresign developer API exposes read-only NHS reference data and tool-backed
benchmarking datasets.

For more request patterns and integration examples, see
[API Cookbook](api-cookbook.md).

## Interactive Schema

Use the live OpenAPI documentation for the full response schemas:

- Swagger UI: `https://haresign.net/api/docs/`
- ReDoc: `https://haresign.net/api/redoc/`
- Raw schema: `https://haresign.net/api/schema/`

## Authentication

Protected endpoints use a bearer API key:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/practices/?search=elm"
```

If the key is missing, invalid, inactive, or rate limited, the API returns the
standard Django REST Framework error response with the relevant HTTP status.

## Pagination

Most list endpoints are paginated.

| Parameter | Description |
|---|---|
| `page` | Page number. |
| `page_size` | Results per page. Defaults to 100, maximum 500. |

Paginated responses follow this shape:

```json
{
  "count": 1234,
  "next": "https://haresign.net/api/v1/example/?page=2",
  "previous": null,
  "results": []
}
```

## Public Endpoints

| Endpoint | Description |
|---|---|
| `/api/v1/` | Endpoint index and authentication summary. |
| `/api/schema/` | OpenAPI schema. |
| `/api/docs/` | Swagger UI. |
| `/api/redoc/` | ReDoc UI. |

## Authenticated Endpoints

| Endpoint | Key filters | Description |
|---|---|---|
| `/api/v1/practices/` | `search`, `pcn`, `icb` | Practice lookup with PCN and ICB context. |
| `/api/v1/practices/{ods_code}/population/` | path `ods_code` | Practice population by financial year. |
| `/api/v1/pcns/` | `search`, `icb` | PCN lookup. |
| `/api/v1/nwrs/snapshots/` | none | Available NWRS snapshot dates. |
| `/api/v1/nwrs/` | `snapshot`, `practice`, `pcn`, `icb`, `region` | NWRS workforce rows. `snapshot` is required. |
| `/api/v1/qof/years/` | none | QOF year settings. |
| `/api/v1/qof/indicators/` | `year`, `domain`, `indicator`, `active` | QOF indicator metadata. |
| `/api/v1/qof/prevalence/` | `year`, `practice`, `indicator` | Practice QOF prevalence. Requires `year` or `practice`. |
| `/api/v1/qof/prevalence/national/` | `year`, `indicator` | National QOF prevalence. |
| `/api/v1/qof/achievement/` | `year`, `practice`, `indicator` | Practice QOF achievement. Requires `year` or `practice`. |
| `/api/v1/online-consultations/` | `month`, `practice`, `pcn`, `icb`, `supplier`, `metric` | Online consultation monthly metrics. Requires one geography or month filter. |
| `/api/v1/online-consultations/time/` | `date`, `practice`, `pcn`, `supplier` | Online consultation time metrics. Requires `date`, `practice`, or `pcn`. |
| `/api/v1/list-sizes/` | `month`, `org_type`, `org`, `pcn`, `sub_icb`, `icb`, `region` | Registered patient list size snapshots. Requires at least one listed filter except `org_type`. |
| `/api/v1/gp-appointments/` | `month`, `practice`, `pcn`, `sub_icb`, `supplier` | GP appointments monthly metrics. Requires one core filter. |
| `/api/v1/nhs-app/` | `month`, `practice`, `pcn`, `sub_icb` | NHS App usage monthly metrics — logins, unique logins, in-app self-service and active uptake (13+). Requires one core filter. `patients_registered` is the 13+ eligible base, not app sign-ups. |
| `/api/v1/digital-front-door/` | `practice` or `pcn`, `month` | Composite Digital Front Door score (NHS App + online consultations + online/video appointments) with per-channel national percentiles. Requires `practice` or `pcn`. |
| `/api/v1/gp-patient-survey/` | `year`, `practice`, `pcn`, `ics`, `region`, `list_band` | GP Patient Survey practice results. Requires one core filter. |
| `/api/v1/nhs-payments/practices/` | `year`, `practice`, `pcn`, `sub_icb`, `region`, `contract_type` | NHS payments by practice. Requires one core filter. |
| `/api/v1/nhs-payments/pcns/` | `year`, `pcn`, `icb` | NHS payments by PCN. Requires one listed filter. |
| `/api/v1/cloud-telephony/` | `month`, `practice`, `pcn`, `icb`, `indicator` | Cloud telephony monthly metrics. Requires one geography or month filter. |
| `/api/v1/cloud-telephony/time/` | `month`, `practice`, `pcn`, `icb`, `indicator`, `dimension` | Cloud telephony time metrics. Requires one geography or month filter. |
| `/api/v1/pcn-des/` | `date`, `practice`, `pcn`, `icb`, `ruleset`, `indicator` | PCN DES records. Requires one core filter. |
| `/api/v1/gp-contract/practices/` | `search`, `practice`, `pcn`, `sub_icb`, `icb`, `region` | GP Contract practice geography map. |
| `/api/v1/gp-contract/indicators/` | `search`, `indicator`, `quality_service` | GP Contract indicator metadata. |
| `/api/v1/gp-contract/values/` | `date`, `practice`, `indicator`, `quality_service`, `measure` | GP Contract values. Requires one core filter. |
| `/api/v1/gp-contract/carers/` | `date`, `sub_icb`, `indicator`, `quality_service`, `sex`, `age`, `ethnicity` | GP Contract carers demographics. Requires one core filter. |

## Example Calls

List practices matching a name or ODS code:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/practices/?search=elm&page_size=25"
```

Fetch GP appointments for a practice and month:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/gp-appointments/?practice=A12345&month=2026-01-01"
```

Fetch QOF achievement for a practice and year:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/qof/achievement/?practice=A12345&year=2025/26"
```

## Developer Notes

- Dates use ISO format, for example `2026-01-01`.
- Financial or survey years use the format stored by the source dataset, for
  example `2025/26` or `2026`.
- Large national datasets require at least one filter to avoid accidental bulk
  downloads.
- The OpenAPI schema is generated from the Django REST Framework serializers and
  view annotations.
- Store the reporting period returned by the API alongside values in your own
  system, because different source datasets refresh on different schedules.
