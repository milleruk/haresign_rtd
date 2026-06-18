# Haresign Developer Docs

Haresign provides free NHS data tools, benchmarking dashboards, and a developer
API for GP practices, PCNs, analysts, and partner systems.

## Quick Links

- Live API endpoint index: `https://haresign.net/api/v1/`
- Live Swagger UI: `https://haresign.net/api/docs/`
- Live ReDoc UI: `https://haresign.net/api/redoc/`
- Raw OpenAPI schema: `https://haresign.net/api/schema/`

## Documentation Sections

- [Developer API](api.md) covers authentication, available endpoints, filters,
  pagination, and example calls.
- [Read the Docs Setup](readthedocs.md) explains how to publish this directory
  through Read the Docs.
- [Data Imports](data-import.md) covers operational data import workflows.
- [Graph Email](graph-email.md) covers Microsoft Graph email configuration.

## Authentication Summary

Most API endpoints require an API key:

```http
Authorization: Bearer <api_key>
```

The schema and documentation pages are public so developers can inspect the API
contract before a key is issued.
