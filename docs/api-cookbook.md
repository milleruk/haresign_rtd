# API Cookbook

The live schema is the source of truth for exact fields and response examples:

- Swagger UI: `https://haresign.net/api/docs/`
- ReDoc: `https://haresign.net/api/redoc/`
- Raw schema: `https://haresign.net/api/schema/`

This page gives common request patterns for developers.

## Base Pattern

Authenticated requests use a bearer API key:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/practices/?search=elm"
```

Most list endpoints are paginated:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/practices/?search=elm&page_size=25&page=1"
```

## Discover Organisations

Search practices before requesting practice-level datasets:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/practices/?search=A12345"
```

Search PCNs before requesting PCN-level datasets:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/pcns/?search=example"
```

Use ODS codes exactly as returned by lookup endpoints when calling more
specific dataset endpoints.

## Fetch Population Context

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/practices/A12345/population/"
```

Population endpoints are useful for adding list-size context to benchmark
outputs.

## Fetch Appointment Metrics

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/gp-appointments/?practice=A12345&month=2026-01-01"
```

For broader comparisons, use PCN, sub-ICB, or supplier filters where available.
Large datasets require filters to avoid accidental bulk downloads.

## Fetch QOF Data

Find available QOF years:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/qof/years/"
```

Find indicators:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/qof/indicators/?year=2025/26"
```

Fetch achievement:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/qof/achievement/?practice=A12345&year=2025/26"
```

Fetch prevalence:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/qof/prevalence/?practice=A12345&year=2025/26"
```

## Fetch Workforce Data

Check available snapshots first:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/nwrs/snapshots/"
```

Then request workforce rows for the snapshot:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/nwrs/?snapshot=2026-01-31&practice=A12345"
```

## Fetch Payment Data

Practice payments:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/nhs-payments/practices/?practice=A12345&year=2025/26"
```

PCN payments:

```bash
curl -H "Authorization: Bearer <api_key>" \
  "https://haresign.net/api/v1/nhs-payments/pcns/?pcn=U12345&year=2025/26"
```

## Handling Errors

Typical responses follow Django REST Framework conventions.

| Status | Meaning |
|---|---|
| `400` | A required filter or parameter is missing or invalid. |
| `401` | API key is missing or invalid. |
| `403` | The key is valid but not permitted for the requested resource. |
| `404` | The endpoint or object was not found. |
| `429` | Request rate limit reached. |
| `500` | Unexpected server error. Retry later or contact support. |

## Integration Tips

- Use the schema for field names rather than copying examples by hand.
- Filter early and page through results.
- Store the reporting period alongside values.
- Do not assume that every dataset refreshes on the same date.
- Treat ODS codes, PCN codes, and year strings as stable identifiers from the
  source data.
- Build graceful handling for empty result sets.
