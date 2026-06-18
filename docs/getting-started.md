# Getting Started

Haresign is designed so you can start with a question, choose the relevant tool,
and then move between practice, PCN, regional, and national context.

## Start With A Question

Common starting points:

| Question | Suggested area |
|---|---|
| How does my practice compare on access and appointment activity? | GP Appointments, Online Consultations, Cloud Telephony |
| What does our registered population look like? | List Size Dashboards, Practice Overview |
| How do our patient experience scores compare? | GP Patient Survey |
| What income or reimbursement should we plan for? | ARRS, PCN Funding Split, QOF Income, GP Reimbursement, NHS Payments |
| What does our workforce profile look like? | NWRS Workforce |
| How are PCN DES or contract indicators performing? | PCN DES, GP Contract |
| Can I pull structured data into another dashboard? | Developer API |

## Basic Navigation

1. Go to `https://haresign.net/tools/`.
2. Choose the tool that matches your question.
3. Search for a practice, PCN, or geography where the tool asks for one.
4. Review the headline cards first.
5. Use the charts and comparison panels to understand what is driving the
   headline result.
6. Check the methodology or data-source notes before using a figure in a formal
   report.

## Working With Practice Or PCN Context

Some tools work best when a practice or PCN has been selected. You can usually
search directly inside the tool. If you create an account, you can also link
practice and PCN workspaces so the site can remember your common context.

See [Accounts and Workspaces](accounts.md) for the full flow.

## Using A Dashboard

Most dashboards follow a similar pattern:

| Section | What it is for |
|---|---|
| Search or selector | Choose the practice, PCN, month, year, or benchmark group. |
| KPI cards | Fast read of the most important figures. |
| Trend charts | Show movement over time. |
| Benchmark cards | Compare against PCN, ICB, region, England, or peer groups. |
| Breakdowns | Explain the composition of a result, for example age band, payment category, appointment mode, or indicator group. |
| Notes | Explain source data, caveats, or methodology. |

## Using Calculators

Calculator tools are scenario models. They normally ask for a small number of
inputs, then calculate funding, reimbursement, or cost estimates.

Good practice:

- check the year or scheme version shown by the calculator;
- keep a note of assumptions used in any scenario;
- treat outputs as planning support, not formal contractual advice;
- check current NHS England or commissioner guidance before making a claim or
  submitting a financial return.

## Using Uploaded Data Tools

Some tools, such as the GPAD Analyser, can work with a file that you upload.
Use these tools when you want to understand your own local extract rather than a
published national dataset.

Before uploading:

- check that the file is the expected format;
- remove anything the tool does not need;
- avoid uploading unnecessary patient-identifiable information;
- read the on-page instructions for that specific upload.

## Getting API Access

The API is for developers and analysts who want structured data. The schema is
public, but most endpoints need an API key.

Start here:

- Schema and Swagger UI: `https://haresign.net/api/docs/`
- API guide: [Developer API](api.md)

## If Something Looks Wrong

When a result surprises you:

1. Check the selected practice, PCN, month, or year.
2. Compare the numerator and denominator where shown.
3. Look for data-quality notes on the page.
4. Check whether the source data was revised or recently refreshed.
5. Use the contact route on Haresign if you think the tool is behaving
   incorrectly.
