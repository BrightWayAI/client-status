# Security Policy

## What this plugin does with your data

Client Status auto-drafts weekly status updates per active client engagement, pulled from your existing context. Read across multiple sources; writes only drafts plus optional changelog entries.

**Reads:**
- **Cortex memory** (if installed) — `~/Documents/Claude/memory/client/[client-name].md` for living summary, recent commits, knowledge entries, open threads.
- **Project Setup** (if installed) — engagement data (phase, deliverables, milestones).
- **Calendar** — external meetings with client-domain attendees in the target week.
- **CRM** — recent notes, tasks, deals associated with the client.
- **Time Tracking** (optional, if installed and user-context enables it) — `~/Documents/Claude/time-log.csv` for hours-this-week per client.
- **Plugin references** — `references/user-context.md`, `references/templates/status-template.md`.
- **Shared user-level config** — `~/Documents/Claude/identity.md`, `~/Documents/Claude/voice.md` (read-only).

**Writes:**
- **Drafts** — produced inline for review. Not auto-sent.
- **Plugin user-context** — `references/user-context.md` (after `/setup-status`).
- **Cortex changelog entry** (only if user confirms after sending) — appends a `LOG` line to the client's memory node noting that a status update was sent on `[date]`.
- **CRM note** (only if user confirms) — logs a status-update-sent note on the contact record.

**Does not:**
- **Send status updates to clients.** All drafts go for user review and manual send.
- **Modify project-setup engagement data.** Read-only.
- **Modify time-log data.** Read-only.
- **Surface anything tagged `[INTERNAL]` or `[CONFIDENTIAL]` in cortex memory** — these are explicitly excluded from client-facing drafts.

## Where data lives

- Plugin reference files inside the installed plugin directory.
- Drafts produced inline in conversation; not persisted unless user explicitly saves.
- Shared identity/voice (read-only) at `~/Documents/Claude/`.
- Cortex memory and time-log are owned by their respective plugins.

## What gets sent off your machine

- Whatever your authorized CRM, calendar, Gmail connectors send when reading client context.

## Privacy note about drafts

Drafts may contain:
- Client names, contact names
- Engagement details (deliverables, phase status)
- Recent meeting topics
- Insights and lessons captured in cortex memory

Drafts are inline in your Cowork or Claude Code conversation. If you copy them to email or another tool, treat them with the same confidentiality you'd use for client-facing communications.

## Supported versions

| Version | Supported |
|---------|-----------|
| 0.1.x   | Yes       |

## Reporting a vulnerability

Report privately via GitHub Security Advisories:

https://github.com/BrightWayAI/client-status/security/advisories/new

Do not open a public issue for security concerns. We aim to respond within 5 business days.
