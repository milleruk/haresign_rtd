# Data Sources

Haresign tools use public NHS and government datasets. This page explains the
main sources at a high level so users and developers can understand what sits
behind the dashboards and API.

## Source Summary

| Area | Main source | Used for |
|---|---|---|
| Practices and PCNs | NHS Organisation Data Service and NHS England reference data | Practice lookup, PCN membership, geography, benchmarking context. |
| Registered patients | NHS Digital Patients Registered at a GP Practice | List size dashboards, age/sex population breakdowns, local population context. |
| Appointments | NHS Digital Appointments in General Practice | GP appointments dashboard and API appointment metrics. |
| Online consultations | NHS England online consultation publications | Online consultation volumes, supplier comparisons, and timing patterns. |
| Cloud telephony | NHS England Cloud Based Telephony in General Practice | Call demand, answer patterns, wait distributions, and telephony indicators. |
| Workforce | NHS Digital National Workforce Reporting System | Workforce mix, full-time equivalent measures, and peer comparisons. |
| QOF | NHS England and NHS Digital QOF publications | QOF income, achievement, prevalence, and indicator metadata. |
| GP Patient Survey | NHS England / Ipsos GP Patient Survey | Patient experience and access indicators. |
| NHS payments | NHS Digital NHS Payments to General Practice | Practice and PCN payment benchmarking. |
| GP Contract Services | NHS Digital GP Contract Services | Contract, vaccination, and service achievement indicators. |
| PCN DES | NHS England PCN DES achievement publications | PCN DES indicator achievement and comparison. |
| OHID Fingertips | Office for Health Improvement and Disparities Fingertips API | Public health profiles and indicator exploration. |
| CQC reference content | Care Quality Commission public framework and local configuration | CQC search and assurance support tools. |

## Refresh Cadence

Different datasets update on different schedules. Haresign follows the source
publication cadence rather than inventing its own dates.

| Dataset type | Typical cadence |
|---|---|
| Registered patient list size | Monthly |
| GP appointments | Monthly |
| Online consultations | Monthly or periodic publication |
| Cloud telephony | Monthly or periodic publication |
| NWRS workforce | Monthly or periodic snapshot |
| GP Patient Survey | Annual |
| NHS payments | Annual |
| QOF achievement and prevalence | Annual |
| GP Contract Services | Periodic publication |
| PCN DES | Periodic publication |
| OHID Fingertips | Varies by indicator/profile |

When a source publishes revised data, Haresign may refresh the affected dataset
and the values shown in tools or returned by the API may change.

## Important Interpretation Notes

### Registered Patient Counts

Registered patient list size is a raw headcount from the published patient
registration data. It is not the same as weighted population used for some
funding calculations.

### Appointment Data

Published GP appointment data depends on appointment-book configuration and
mapping quality. It is useful for benchmarking and trend analysis, but local
coding and workflow differences can affect comparisons.

### Survey Data

GP Patient Survey figures are survey estimates. They should be interpreted
alongside response volumes, confidence intervals, local context, and year-on-year
methodology changes.

### Payment Data

NHS payments data is a published financial dataset. It can support benchmarking,
but it does not by itself explain contract type, local service arrangements,
population need, premises arrangements, or one-off payments.

### QOF and Contract Data

QOF, GP Contract Services, vaccination, and PCN DES indicators are tied to
published business rules and reporting periods. Always check the source
guidance before using outputs for formal submissions or contractual decisions.

## Why Figures Can Differ From Local Systems

Haresign generally uses published NHS or government data. A value may differ
from a local system because:

- the reporting period is different;
- the source publication has been revised;
- the local system uses live operational data while the published dataset is a
  snapshot;
- coding or mapping rules differ;
- the organisation has changed PCN, ICB, or contract context;
- a local report filters records differently;
- weighted population is being compared with registered list size.

When investigating a difference, check the source name, reporting period,
organisation code, denominator, and filter choices before assuming either value
is wrong.

## API Availability

Many cleaned datasets are exposed through the developer API. The live API schema
is the best source for exact response fields:

- Swagger UI: `https://haresign.net/api/docs/`
- ReDoc: `https://haresign.net/api/redoc/`
- Raw schema: `https://haresign.net/api/schema/`

See [Developer API](api.md) for endpoint examples.

## Source Links

Source publication pages can move over time, so the live Haresign tools and API
documentation focus on dataset names and methodology. When using outputs in
formal papers, board reports, or external submissions, cite the original NHS or
government publication for the relevant reporting period.
