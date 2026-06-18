# Haresign Docs

Haresign provides free NHS data tools, benchmarking dashboards, and a developer
API for GP practices, PCNs, analysts, and partner systems.

## Quick Links

- Haresign platform: `https://haresign.net/`
- Tools index: `https://haresign.net/tools/`
- Live API endpoint index: `https://haresign.net/api/v1/`
- Live Swagger UI: `https://haresign.net/api/docs/`
- Live ReDoc UI: `https://haresign.net/api/redoc/`
- Raw OpenAPI schema: `https://haresign.net/api/schema/`

## Documentation Sections

- [Platform](platform.md) explains what Haresign is for and how the tools fit
  together.
- [Tools](tools.md) summarises the public tools and what each one helps with.
- [Data Sources](data-import.md) lists the public datasets behind the platform
  and how refreshes are handled at a high level.
- [Developer API](api.md) covers authentication, available endpoints, filters,
  pagination, and example calls.

## Authentication Summary

Most API endpoints require an API key:

```http
Authorization: Bearer <api_key>
```

The schema and documentation pages are public so developers can inspect the API
contract before a key is issued.
