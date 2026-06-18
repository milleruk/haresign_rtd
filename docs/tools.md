# Tools

Haresign tools are grouped around common primary care management questions:
funding, workforce, demand, population, access, quality, and assurance.

Each tool is designed to answer a practical question, show enough context to
interpret the result, and make the underlying data easier to reuse.

## Practice Overview

Use this when you want a single view of a selected practice.

What it shows:

- practice identity and PCN context;
- population and list-size indicators;
- public access, demand, quality, and payment signals where available;
- links into the deeper dashboards for more detail.

How to use it:

1. Search for a practice by name or ODS code.
2. Review the headline sections first.
3. Follow dashboard links where a section needs investigation.
4. Use it as a starting point for board papers, operational review, or practice
   support conversations.

Interpretation notes:

- It brings together several datasets with different publication dates.
- Treat it as a navigation and triage page, not a single definitive score.

## List Size Dashboards

Use these dashboards to understand registered patient population.

What they show:

- registered list size by practice, PCN, sub-ICB, ICB, region, and England;
- age-band and sex breakdowns;
- dependency ratio and older-age indicators;
- trends and growth;
- national and local landscape views.

How to use them:

1. Choose a practice, PCN, or geography.
2. Check total registered patients and age structure.
3. Compare against wider geographies.
4. Use local landscape views where competition or neighbouring population
   changes matter.

Interpretation notes:

- Registered patients are raw headcount.
- Funding calculations often use weighted or adjusted populations, which are
  different measures.

## GP Appointments Dashboard

Use this to explore published monthly appointment activity.

What it shows:

- total appointments;
- attended, DNA, and unknown-status counts;
- GP and other-staff appointments;
- appointment mode;
- national category;
- booking-to-appointment wait bands;
- same-day and within-window access indicators;
- peer and geography comparisons.

How to use it:

1. Select a practice or PCN.
2. Choose the month or review the latest available month.
3. Start with total activity and DNA rate.
4. Use mode, category, and wait-band breakdowns to understand the drivers.
5. Compare with PCN, sub-ICB, and England figures.

Interpretation notes:

- Appointment-book setup and national-category mapping affect results.
- A high or low value may reflect coding behaviour as well as operational
  performance.

## GPAD Analyser

Use this when you have a local GP appointment extract and want deeper
slot-level or mapping analysis.

What it shows:

- mapping and data-quality signals;
- booking and attendance patterns;
- pressure points by slot, session, or category;
- improvement opportunities;
- board-report style summaries.

How to use it:

1. Open the GPAD Analyser.
2. Upload the expected appointment extract format.
3. Review data-quality warnings before acting on the metrics.
4. Use the dashboard tabs to move from overview to detailed improvement actions.

Interpretation notes:

- Uploaded data may reveal local configuration issues not visible in national
  published data.
- Check that the extract covers the intended period before drawing conclusions.

## Online Consultations Dashboard

Use this to understand online consultation usage and timing.

What it shows:

- monthly consultation volumes;
- clinical, administrative, and unknown/other split;
- supplier and geography context;
- time-of-day and weekday patterns where available.

How to use it:

1. Select a practice, PCN, or geography.
2. Review monthly totals and trend.
3. Compare clinical and administrative demand.
4. Look at timing patterns to support staffing and workflow decisions.

Interpretation notes:

- Supplier configuration and triage workflows can change what is counted.
- Use with appointments and telephony to understand total demand pressure.

## Cloud Telephony Dashboard

Use this to understand call demand and access through cloud-based telephony.

What it shows:

- inbound call volume;
- answered, missed, and abandoned call indicators;
- callback activity;
- wait-time distributions;
- call-duration distributions;
- time-of-day and weekday patterns;
- practice, PCN, ICB, and regional context where available.

How to use it:

1. Select a practice or PCN.
2. Review inbound calls and answer outcomes.
3. Use wait and duration breakdowns to identify pressure periods.
4. Compare with appointment and online-consultation demand.

Interpretation notes:

- Call handling models differ between suppliers and practices.
- Telephony data is strongest when used alongside staffing and appointment
  activity.

## GP Patient Survey Dashboard

Use this to explore patient experience and access indicators.

What it shows:

- overall experience;
- phone, website, NHS App, and reception access;
- appointment wait and choice;
- consultation quality indicators;
- continuity and preferred-professional measures;
- PCN, ICS, England, and list-size peer comparisons.

How to use it:

1. Select a practice or PCN.
2. Review headline indicators first.
3. Compare access indicators with appointment and telephony data.
4. Use confidence and response context when discussing changes.

Interpretation notes:

- Survey figures are estimates from respondents, not activity counts.
- Year-on-year changes may reflect method, response mix, or real experience
  changes.

## NWRS Workforce Dashboard

Use this to understand published workforce profile and staff mix.

What it shows:

- workforce headcount and full-time equivalent measures;
- role group breakdowns;
- clinical, administrative, and direct patient care mix;
- workforce per registered patient or per 1,000 patients where available;
- comparisons with national, ICB, and similar-list-size peers.

How to use it:

1. Select a practice.
2. Review total workforce and role mix.
3. Compare per-patient measures to peers.
4. Use alongside appointments and demand tools for capacity planning.

Interpretation notes:

- Workforce returns depend on submitted role coding.
- More or fewer staff per patient may reflect workload, service model,
  deprivation, premises, or local commissioning arrangements.

## QOF Income Calculator

Use this to estimate QOF income under different achievement assumptions.

What it shows:

- points and thresholds by indicator;
- estimated income using QOF year settings;
- list-size and prevalence effects;
- scenario outputs for planning.

How to use it:

1. Select the relevant QOF year.
2. Enter or review list-size and achievement assumptions.
3. Adjust scenarios to understand sensitivity.
4. Use exports or summaries for planning discussions.

Interpretation notes:

- It is a planning tool, not a replacement for official CQRS or commissioner
  calculations.
- Always check current QOF guidance for formal reporting.

## QOF Prevalence Dashboard

Use this to compare disease register prevalence.

What it shows:

- practice-level prevalence;
- national prevalence;
- numerator and denominator where available;
- indicator and condition breakdowns.

How to use it:

1. Select a practice, year, or indicator.
2. Compare prevalence against national context.
3. Use outliers to prompt review rather than as automatic conclusions.

Interpretation notes:

- Prevalence can reflect demographics, coding, disease burden, and register
  quality.

## PCN DES Dashboard

Use this to review PCN DES indicator performance.

What it shows:

- indicator achievement by practice and PCN;
- numerator, denominator, and percentage achievement;
- ruleset groupings;
- benchmark context where available;
- extra measures such as declined or exception-style counts where present in the
  source.

How to use it:

1. Select a PCN or practice.
2. Review indicator groups.
3. Identify variation across member practices.
4. Use the detail view to understand whether performance is driven by numerator,
   denominator, or additional measures.

Interpretation notes:

- Indicator definitions and payment rules can change by year.
- Always confirm current PCN DES guidance before making contractual decisions.

## GP Contract Dashboard

Use this to explore GP Contract Services and vaccination-related indicators.

What it shows:

- practice-level indicator values;
- numerator and denominator measures where published;
- vaccination programme activity;
- PCN, sub-ICB, ICB, region, and national context;
- carers demographic breakdowns where available.

How to use it:

1. Select a practice or geography.
2. Choose the relevant indicator or service group.
3. Review achievement and denominators.
4. Compare with appropriate peers.

Interpretation notes:

- Some indicators are counts while others are numerator/denominator measures.
- Read the source indicator definition before comparing unlike measures.

## NHS Payments Dashboard

Use this to benchmark published NHS payments.

What it shows:

- total payments by practice or PCN;
- payment line items and grouped categories;
- per-registered-patient and per-weighted-patient views where available;
- comparison against PCN, sub-ICB, region, England, or similar practices.

How to use it:

1. Select a practice or PCN.
2. Review headline payments and per-patient measures.
3. Use category breakdowns to identify what drives differences.
4. Compare against appropriate peers rather than raw totals alone.

Interpretation notes:

- Payment differences often reflect contract type, local services, premises,
  dispensing status, one-off payments, or population need.

## ARRS Calculator

Use this to model ARRS funding and workforce reimbursement scenarios.

What it shows:

- role-level assumptions;
- reimbursement or funding estimates;
- PCN or practice allocation scenarios where relevant.

How to use it:

1. Enter the relevant population, role, or allocation assumptions.
2. Adjust scenarios to test sensitivity.
3. Use outputs for planning conversations and workforce modelling.

Interpretation notes:

- Check current scheme rules before relying on a scenario for formal claims.

## PCN Funding Split

Use this to model how funding can be allocated between member practices.

What it shows:

- PCN funding amounts;
- member practice shares;
- alternative split methods;
- exportable summaries.

How to use it:

1. Select or enter PCN and practice data.
2. Choose a split method.
3. Review the resulting allocation.
4. Compare alternative scenarios before agreeing a final approach.

Interpretation notes:

- The "right" split depends on the purpose of the funding and local agreement.

## Payroll Forecaster

Use this to forecast staffing cost pressure.

What it shows:

- pay assumptions;
- recurring employment costs;
- annualised cost effects;
- scenario comparisons.

How to use it:

1. Enter roles, pay, hours, and employer-cost assumptions.
2. Review monthly and annual impact.
3. Adjust assumptions for increments, vacancies, or planned recruitment.

Interpretation notes:

- Local terms, pension assumptions, and employer on-costs should be checked.

## GP Reimbursement Calculator

Use this to explore GP reimbursement scheme assumptions.

What it shows:

- practice-level cap where available;
- route-specific reimbursement estimates;
- London weighting or adjusted population effects where relevant;
- recommended planning prompts.

How to use it:

1. Search for a practice.
2. Review the cap and route amounts.
3. Compare claim scenarios against the cap.
4. Check eligibility requirements before acting.

Interpretation notes:

- This is planning support. Always verify entitlement before submission.

## IIF Calculator

Use this to support Investment and Impact Fund scenario planning.

What it shows:

- indicator assumptions;
- points or value estimates;
- scenario outputs for PCN planning.

How to use it:

1. Choose the relevant year or indicator set.
2. Enter assumptions.
3. Compare different achievement scenarios.

Interpretation notes:

- IIF rules change over time. Confirm the current framework before using
  outputs in formal planning.

## Demand Forecaster

Use this to explore demand trends and future pressure.

What it shows:

- selected demand metrics over time;
- forecast or projection outputs;
- metric-level detail where available.

How to use it:

1. Select the practice or metric.
2. Review historical pattern first.
3. Compare forecast outputs against known local events.

Interpretation notes:

- Forecasts are directional planning aids, not guarantees.

## CQC Readiness Tools

Use these tools to support CQC evidence planning and preparation.

What they show:

- CQC quality statements or themed prompts;
- checklist-style evidence tracking;
- exportable summaries.

How to use them:

1. Select the relevant checklist.
2. Work through each prompt.
3. Add evidence notes and assign actions where supported.
4. Export or review progress for internal assurance.

Interpretation notes:

- The tool supports preparation. It does not replace CQC guidance, inspection
  judgement, or local governance.

## Enhanced Access Tool

Use this to support enhanced access planning and assurance.

What it shows:

- planned access sessions or coverage;
- exportable planning data where available;
- prompts for service design and reporting.

How to use it:

1. Enter or review planned enhanced access provision.
2. Check coverage and assumptions.
3. Export outputs for local review.

Interpretation notes:

- Local commissioner requirements and contract wording should be checked.

## Fingertips NHS Profiles

Use this to explore public OHID Fingertips data.

What it shows:

- public health profiles;
- indicator groups;
- values and comparisons supplied by the Fingertips API.

How to use it:

1. Select a profile or area.
2. Browse indicator groups.
3. Use the source context to interpret values.

Interpretation notes:

- Indicator definitions vary across profiles. Check metadata for each indicator.

## Developer API Coverage

Several datasets behind the tools are available through the developer API,
including practices, PCNs, population data, QOF, NWRS, online consultations,
list sizes, GP appointments, GP Patient Survey, NHS payments, cloud telephony,
PCN DES, and GP Contract data.

See [Developer API](api.md) for endpoints and examples.
