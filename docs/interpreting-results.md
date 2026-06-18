# Interpreting Results

Haresign makes public NHS datasets easier to explore, but good interpretation
still matters. Use this page when a result looks surprising or when you are
preparing a report from the tools.

## Start With The Question

Before comparing a figure, be clear what question you are asking:

- Is this about demand, access, finance, workforce, quality, or population?
- Are you looking for trend, peer comparison, outliers, or planning assumptions?
- Is the result being used for internal discussion, board reporting, or a formal
  submission?

The same number can have different meaning depending on the question.

## Check The Context

Always check:

| Context | Why it matters |
|---|---|
| Organisation | Practice, PCN, ICB, region, and national figures can answer different questions. |
| Time period | Monthly, annual, and snapshot datasets should not be mixed without care. |
| Denominator | Per-patient, per-working-day, and raw counts tell different stories. |
| Peer group | Similar-list-size peers may be more useful than national averages for some questions. |
| Source refresh date | Public datasets often lag behind operational reality. |

## Counts, Rates, and Percentages

Raw counts are useful for workload and scale. Rates and percentages are useful
for comparison.

Examples:

- Total appointments show activity volume.
- Appointments per 1,000 registered patients help compare practices of
  different sizes.
- DNA percentage helps compare missed appointment rates, but the underlying DNA
  count still matters operationally.
- Survey percentage scores should be read with response volumes and confidence
  intervals where available.

## Numerator And Denominator

When a result is a percentage, look for the numerator and denominator.

Two organisations can have the same percentage for very different reasons:

- high numerator and high denominator;
- low numerator and low denominator;
- small denominator that makes the percentage volatile.

This matters especially for QOF, GP Contract, PCN DES, vaccination, and survey
measures.

## Benchmarks

Benchmarks help ask better questions; they do not automatically identify good or
bad performance.

Useful benchmark questions:

- Is the organisation different from its PCN, ICB, region, or England?
- Has the gap widened or narrowed over time?
- Is the difference explained by population, contract type, workforce, or local
  operating model?
- Is the value outside the usual range for similar organisations?

Avoid using a single benchmark as a verdict.

## Trend Interpretation

When reviewing a trend:

1. Check whether the source data cadence changed.
2. Look for missing months or outlier periods.
3. Consider seasonal effects.
4. Compare with known local events such as mergers, system changes, workforce
   gaps, or access model changes.
5. Avoid drawing conclusions from one month unless the change is very large and
   corroborated elsewhere.

## Common Dataset Caveats

### Appointment Data

Appointment figures depend on appointment-book setup, national-category mapping,
mode coding, and local workflow. Differences can reflect coding as well as
access.

### Online Consultations

Supplier configuration and triage model affect what is counted as clinical,
administrative, unknown, or other demand.

### Cloud Telephony

Call handling, callback configuration, and supplier reporting conventions can
affect waits, missed calls, and abandoned-call indicators.

### Registered Patients

Registered list size is not the same as weighted population. Use the correct
population measure for the question.

### Workforce

Workforce data depends on submitted role coding and may not capture informal or
locum arrangements in the way a local roster does.

### Payments

Payment data can reflect contract type, local enhanced services, premises,
dispensing status, and one-off adjustments.

### Survey Data

Survey measures reflect respondent experience and sample composition. They are
important, but should be read alongside operational data.

## Using Results In Reports

When copying a figure into a paper or board report:

- include the source dataset and reporting period;
- describe whether the value is a count, rate, or percentage;
- include the denominator where it matters;
- state the comparator used;
- avoid implying causation from a benchmark difference alone;
- check whether the source dataset has been revised.

## When To Investigate Further

A result is worth deeper review when:

- it changes sharply from the previous period;
- it is materially different from peers;
- it conflicts with local knowledge;
- it affects funding, contractual performance, or patient access;
- it is based on a small denominator;
- it is likely to be affected by coding or workflow changes.

## What Haresign Does Not Replace

Haresign does not replace:

- official NHS England guidance;
- contractual submissions;
- CQRS or local commissioner systems;
- clinical judgement;
- local data-quality review;
- formal financial or legal advice.

Use Haresign as a decision-support and exploration platform. For formal action,
check the original source publication and relevant guidance.
