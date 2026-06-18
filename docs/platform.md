# Platform

Haresign is a free tools and data platform for general practice and primary care
networks in England.

The platform brings together public NHS datasets, practical calculators, and
benchmarking dashboards so practices and PCNs can understand their position
without needing to build local analysis pipelines from scratch.

## Who It Is For

- GP practice managers and partners
- PCN managers and clinical directors
- Analysts working with primary care data
- Commissioners and support teams
- Developers building internal dashboards or integrations

## What The Platform Provides

| Area | What it helps with |
|---|---|
| Benchmarking | Compare practice or PCN metrics against peers and national context. |
| Planning | Model funding, reimbursement, payroll, and workforce scenarios. |
| Public data access | Use cleaned and structured public NHS datasets from one place. |
| Developer access | Query the same reference datasets through the API. |
| Transparency | See data sources and methodology notes alongside the tools. |

## Web Tools and API

The website and API are complementary:

- The web tools are designed for interactive exploration and decision support.
- The API is designed for developers and analysts who want structured data for
  their own reports, dashboards, or workflows.

The API documentation is generated from the live OpenAPI schema:

- Swagger UI: `https://haresign.net/api/docs/`
- ReDoc: `https://haresign.net/api/redoc/`
- Raw schema: `https://haresign.net/api/schema/`

## Typical User Journey

1. Start at the tools index.
2. Choose a tool based on the question you are trying to answer.
3. Search for a practice, PCN, or geography.
4. Review headline figures.
5. Drill into trend, benchmark, or breakdown views.
6. Check interpretation notes before using a result externally.
7. Create an account if you want workspaces, saved presets, or repeated use.

## Public And Account Features

Many tools are public. Account features are there to make repeated use easier,
not to block basic exploration.

| Without an account | With an account |
|---|---|
| Browse public tools. | Link practice and PCN workspaces. |
| Use many calculators and dashboards. | Save common presets. |
| View public data and methodology. | Switch between linked organisations. |
| Read API schema and docs. | Manage your uploaded documents. |

## Public Documentation Boundary

These docs explain how to use Haresign and how to understand the public API.
They do not include internal deployment, hosting, or administrative runbooks.
Operational details may change without affecting how users interact with the
platform.

## Data Principles

Haresign aims to keep the platform:

- grounded in public, citable NHS data sources;
- clear about the difference between raw headcount, weighted populations, and
  derived indicators;
- cautious about interpretation, especially where source data has known quality
  limitations;
- useful to non-technical users while still exposing structured data for
  technical users.
