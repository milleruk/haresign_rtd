# AI Connections (Claude and ChatGPT)

AI Connections let you connect an AI assistant such as Claude or ChatGPT
directly to Haresign and ask about practice data in plain English. Instead of
opening each dashboard, you ask a question and the assistant pulls the live
figures for you.

Behind the scenes this uses the Model Context Protocol (MCP), an open standard
for connecting AI assistants to external tools and data. You do not need to know
anything about MCP to use it — you connect once, then just ask questions.

## What It Is For

- Get answers from Haresign data without opening individual tools.
- Ask follow-up questions and let the assistant combine several datasets.
- Search and compare any GP practice in England conversationally.
- Bring Haresign figures into the assistant you already use for drafting and
  analysis.

## What You Can Ask About

Every public dashboard is available conversationally. The assistant works out
which dataset it needs from your question.

| Area | Example data |
|---|---|
| Nationwide search and comparison | Find any practice in England and compare public metrics, even ones you are not registered to. |
| Registered patients and demographics | List size, age and sex profile, and how it is changing. |
| Appointments and access | Monthly appointment volumes, DNA rates, and GP versus other-staff mix (GPAD). |
| Online consultations | Online or eConsult submission volumes and the clinical/admin split. |
| Cloud telephony | Inbound, answered, abandoned, and callback call volumes. |
| Workforce | GP, nurse, direct-patient-care, and admin FTE, and patients per GP. |
| Patient experience | Headline GP Patient Survey scores against the national picture. |
| Disease prevalence | QOF recorded prevalence for each clinical condition. |
| QOF achievement | Achievement by clinical area for the latest QOF year. |
| Funding and payments | Total payments and £ per weighted patient versus PCN, ICB, region, and England. |
| Practice overview | A single cross-dataset summary of the headline numbers. |

### Example Questions

- "Find the practice 'Riverside Surgery' and show its list size and DNA rate."
- "Compare patients-per-GP across these three ODS codes."
- "What is the national median DNA rate, and where does my practice sit?"
- "How many patients are registered at my practice, and how is that trending?"
- "How much funding do we receive per weighted patient versus the England
  average?"
- "What is the diabetes and hypertension prevalence on my list?"
- "Give me a one-paragraph overview of how my practice is performing."

## How To Connect

Setup takes about two minutes. There are no keys to copy — Claude and ChatGPT use
a secure sign-in and approval step.

1. Sign in to Haresign and open your **AI Connections** page at
   `https://haresign.net/mcp/about/`.
2. In Claude or ChatGPT, add a custom connector and paste your Haresign
   endpoint:

   ```text
   https://haresign.net/mcp/
   ```

3. Approve access when the assistant prompts you, then start asking questions.

You can revoke any connection instantly from your AI Connections page. The
connection step uses OAuth, so you sign in to Haresign in the normal way and
approve the assistant — your password is never shared with the AI client.

!!! note "Client support"
    Custom connectors are available in Claude (claude.ai and Claude Desktop) and
    in ChatGPT on plans that support custom MCP connectors. Other MCP-compatible
    clients can use the same endpoint.

## Public vs Account Data

An AI Connection always requires you to sign in, so the assistant acts as you.
What that gives access to follows the same rules as the rest of the platform.

| Data type | Who can read it |
|---|---|
| **Public** — nationally published NHS data (GPAD, telephony, GPPS, list size, workforce, QOF, prevalence, NHS payments, online consultations, practice details) | Any signed-in connection, for any practice in England. |
| **Private** — user-entered, uploaded, or otherwise non-public practice data | Only where your account has an active, authorised role for that specific practice. |

Most questions use public data, so you can search and compare practices
nationwide. Anything private is limited to the practices on your account.

See [Public vs Account Access](public-vs-account.md) for how account roles work.

## Privacy and Safety

- **Read-only.** A connection can only read data — it can never change anything
  on your account or in Haresign.
- **No patient-identifiable data.** Only aggregate figures are ever returned, the
  same numbers you would see on the dashboards. No record-level or
  patient-identifiable data is exposed.
- **Scoped to your access.** Private data is strictly limited to practices you
  already have an active role for. A request for a practice you are not
  authorised to see returns a generic "not found or access denied".
- **Revocable.** You can remove any connection at any time from your AI
  Connections page.
- **Audited.** Every request is logged for security, without storing any
  free-text or patient-identifiable content.

## Interpreting Results

AI assistants can summarise and combine figures well, but they can also phrase
things more confidently than the underlying data supports. Treat answers as a
fast way to surface the numbers, then:

- check headline figures against the relevant dashboard before using them
  externally;
- read the [Interpreting Results](interpreting-results.md) notes for metric
  caveats and benchmarking guidance;
- remember that values change when the source NHS publication is refreshed.

## Related

- [Public vs Account Access](public-vs-account.md)
- [Tools](tools.md)
- [Interpreting Results](interpreting-results.md)
- [Developer API](api.md) for structured, programmatic access without an AI
  client.
