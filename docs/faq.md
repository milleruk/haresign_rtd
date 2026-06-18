# FAQ

## Do I Need An Account?

Not always. Many tools can be used without signing in. An account is useful if
you want linked practice or PCN workspaces, saved presets, or document features.

## How Do I Create An Account?

Go to:

```text
https://haresign.net/accounts/register/
```

Register, verify your email, then sign in. See
[Accounts and Workspaces](accounts.md) for the full process.

## How Do Practice And PCN Workspaces Work?

A workspace is the practice or PCN context attached to your account. Some tools
can use that context to pre-select organisations or save presets.

Practice and PCN links may require approval before they become active.

## Why Does A Figure Differ From Our Local System?

Common reasons include:

- the public dataset covers a different reporting period;
- local systems have more recent data;
- coding or mapping differs between local and national reporting;
- local extracts include records excluded from published data;
- the public dataset has been revised;
- denominators differ, for example registered population versus weighted
  population.

Use the source and methodology notes before treating a difference as an error.

## How Often Is Data Refreshed?

Haresign follows source publication schedules. Some datasets are monthly, some
annual, and some update on a less regular publication cycle.

See [Data Sources](data-import.md) for the main cadence by dataset.

## Can I Use Outputs In Board Reports?

Yes, but include context:

- source dataset;
- reporting period;
- organisation selected;
- comparator used;
- numerator and denominator where relevant;
- caveats where source data has known limitations.

The tools are designed to support reporting, but formal decisions should still
refer to source guidance and local validation.

## Can I Export Data?

Some tools provide exports or report views. For structured data access, use the
developer API where the relevant dataset is exposed.

## How Do I Get An API Key?

The schema and documentation are public, but most API endpoints require a bearer
API key. Contact Haresign through the website if you need access.

The API docs are available at:

```text
https://haresign.net/api/docs/
```

## Is The API The Same As The Website?

The API exposes structured datasets behind many of the tools. The website adds
interactive charts, calculations, comparison panels, and workflow-specific
views.

Use the API when you need data in another system. Use the website when you want
interactive exploration.

## Are Uploaded Files Stored?

Some tools accept uploads for analysis. Read the instructions on the specific
tool page before uploading. Avoid uploading unnecessary patient-identifiable
information.

## Can Haresign Tell Me What Action To Take?

Haresign can highlight patterns and support planning. It does not replace local
governance, contractual guidance, professional judgement, or formal advice.

## What Should I Do If A Tool Looks Wrong?

Check:

1. selected organisation;
2. selected month or year;
3. whether the source data has known caveats;
4. whether the denominator is what you expected;
5. whether another tool shows the same pattern.

If it still looks wrong, contact Haresign with the tool name, organisation,
time period, and what you expected to see.
