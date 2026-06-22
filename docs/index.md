# Haresign Docs

Haresign provides free NHS data tools, benchmarking dashboards, and a developer
API for GP practices, PCNs, analysts, and partner systems.

## Quick Links

- Haresign platform: `https://haresign.net/`
- Tools index: `https://haresign.net/tools/`
- Public documentation: `https://haresign.readthedocs.io/en/latest/`
- Live API endpoint index: `https://haresign.net/api/v1/`
- Live Swagger UI: `https://haresign.net/api/docs/`
- Live ReDoc UI: `https://haresign.net/api/redoc/`
- Raw OpenAPI schema: `https://haresign.net/api/schema/`

## Documentation Sections

- [Platform](platform.md) explains what Haresign is for and how the tools fit
  together.
- [Getting Started](getting-started.md) walks through the first visit, choosing
  a tool, and using the site effectively.
- [Accounts and Workspaces](accounts.md) explains registration, email
  verification, practice/PCN linking, workspace switching, and saved presets.
- [Public vs Account Access](public-vs-account.md) explains what can be used
  immediately and what account features add.
- [AI Connections](ai-connections.md) explains how to connect Claude or ChatGPT
  to Haresign and ask about practice data in plain English.
- [Tools](tools.md) summarises the public tools and what each one helps with.
- [Tool Guides](tools/practice-overview.md) provide more detailed usage notes
  for the main dashboards and calculators.
- [Interpreting Results](interpreting-results.md) explains common metrics,
  caveats, and how to use benchmarks responsibly.
- [Worked Examples](workflows.md) shows practical ways to use Haresign for
  review, planning, and reporting.
- [Data Sources](data-import.md) lists the public datasets behind the platform
  and how refreshes are handled at a high level.
- [Developer API](api.md) covers authentication, available endpoints, filters,
  pagination, and example calls.
- [API Cookbook](api-cookbook.md) gives more concrete developer request
  patterns.
- [Glossary](glossary.md) explains common NHS, contract, and data terms.
- [FAQ](faq.md) answers common user and developer questions.

## Authentication Summary

Most API endpoints require an API key:

```http
Authorization: Bearer <api_key>
```

The schema and documentation pages are public so developers can inspect the API
contract before a key is issued.
