# Microsoft Graph email sending

System email (account notifications, SLA alerts, contact replies, etc.) is sent
through the **Microsoft Graph API** using an Azure **App Registration** with
**application permissions** and the OAuth2 client-credentials flow.

```
Django  →  Azure App Registration (Mail.Send, application)  →  POST /users/no-reply@haresign.net/sendMail
```

No SMTP. No login as the shared mailbox. No delegated/user token.

All mail is sent **as the shared mailbox** `no-reply@haresign.net`, and an
Exchange **Application Access Policy** restricts the app so it can *only* send
from that one mailbox.

## How it fits the codebase

- `haresign/graph_email.py` — `GraphEmailBackend`
  (a Django `BaseEmailBackend`) plus a `send_graph_mail()` helper and cached
  token acquisition.
- `haresign/settings.py` — selects
  `EMAIL_BACKEND = 'haresign.graph_email.GraphEmailBackend'` automatically when
  the Graph credentials are present; otherwise falls back to SMTP.

Because it's a standard Django backend, **every existing `msg.send()` call** —
including `website/tasks.py` and `_html_email()` — routes through Graph with no
code changes. HTML emails (`EmailMultiAlternatives` with a `text/html`
alternative) are sent as HTML; plain-only messages are sent as text. `to`, `cc`,
`bcc`, `reply_to`, subject, body and (tuple-form) attachments are all supported.

## Environment variables

| Variable | Required | Notes |
|----------|----------|-------|
| `GRAPH_MAIL_TENANT_ID` | yes | Azure AD (Entra) tenant ID (Directory ID). |
| `GRAPH_MAIL_CLIENT_ID` | yes | App Registration Application (client) ID. |
| `GRAPH_MAIL_CLIENT_SECRET` | yes | Client secret **value** (not the secret ID). |
| `GRAPH_MAIL_SENDER` | yes | `no-reply@haresign.net` — the shared mailbox. |
| `GRAPH_MAIL_SAVE_TO_SENT` | no | `True` to keep a copy in Sent Items (default `False`). |
| `DEFAULT_FROM_EMAIL` | recommended | Set to `no-reply@haresign.net` for header consistency. |

Set these in the deployment `.env` (consumed by `docker-compose.yml` for both
the web and `qcluster` worker services). **Never commit the secret.** If all
four required vars are empty, the app silently falls back to SMTP, so local/dev
keeps working.

## One-time Microsoft 365 / Azure setup

### 1. Create the shared mailbox
Microsoft 365 admin centre → **Teams & groups → Shared mailboxes → Add** →
name `no-reply`, address `no-reply@haresign.net`. A shared mailbox needs no
licence. Do **not** set or use a password for it.

### 2. Create the Azure App Registration
[Entra admin centre](https://entra.microsoft.com) → **App registrations → New
registration**. Name e.g. `haresign-net-mailer`, single tenant, no redirect URI.
After creation, copy the **Application (client) ID** and **Directory (tenant)
ID**.

### 3. Add a client secret
App → **Certificates & secrets → New client secret**. Copy the secret **Value**
immediately (it's only shown once) → `GRAPH_MAIL_CLIENT_SECRET`.

### 4. Grant the Graph application permission `Mail.Send`
App → **API permissions → Add a permission → Microsoft Graph → Application
permissions** → search **`Mail.Send`** → add. Make sure it's the *Application*
type, not Delegated.

### 5. Grant admin consent
On the **API permissions** page click **Grant admin consent for <tenant>**.
The `Mail.Send` row should show a green **Granted** state.

### 6. Restrict the app to only the no-reply mailbox
Without this, the app could send as *any* mailbox in the tenant. Lock it down
with an **Application Access Policy** (Exchange Online PowerShell):

```powershell
Connect-ExchangeOnline

# A mail-enabled security group whose only member is the no-reply mailbox.
New-DistributionGroup -Name "GraphMailSenders" -Type Security `
  -PrimarySmtpAddress graph-mail-senders@haresign.net
Add-DistributionGroupMember -Identity "GraphMailSenders" `
  -Member no-reply@haresign.net

# Restrict the app (use the App Registration's Application/client ID) to
# only send as members of that group.
New-ApplicationAccessPolicy `
  -AppId "<GRAPH_MAIL_CLIENT_ID>" `
  -PolicyScopeGroupId "graph-mail-senders@haresign.net" `
  -AccessRight RestrictAccess `
  -Description "Restrict haresign-net-mailer to the no-reply shared mailbox"

# Verify (allow a few minutes to propagate):
Test-ApplicationAccessPolicy -Identity no-reply@haresign.net -AppId "<GRAPH_MAIL_CLIENT_ID>"
# AccessCheckResult should be "Granted". Any other mailbox should be "Denied".
```

## Verify it works

```bash
docker compose exec haresign_net python manage.py test_graph_email ben@haresign.net
```

A `202 Accepted` from Graph means success; the command prints a confirmation.
Failures (bad credentials, missing consent, access-policy denial) are logged and
reported with the Graph status code.
