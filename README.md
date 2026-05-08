# client-status

Weekly client status updates, auto-drafted from your existing context.

The pain: clients who get regular updates renew at higher rates and refer more often. But manually writing weekly updates per active engagement is tedious work that slips. This plugin closes that gap. Pull from cortex memory + project-setup + calendar + CRM → produce a draft status update per active engagement → you review and send.

## What it does

**`/client-status [client?]`** — drafts a weekly update for one client (named) or all active engagements (no arg). For each, the draft includes:

- **What we did this week** — meetings held, deliverables produced, milestones hit
- **What we learned** — relevant insights captured in cortex memory this week
- **What's next** — upcoming work, milestones, decisions you need from them
- **Anything we need from you** — blockers, asks, decisions pending
- **Optional: a thought-leadership share** — a relevant article, framework, or insight (configurable)

Drafts are presented for your review. You edit and send via your normal channel (email, client portal, Slack DM).

## Install

Recommended: via the [BrightWayAI marketplace](https://github.com/BrightWayAI/claude-plugins).

```
/plugin marketplace add BrightWayAI/claude-plugins
/plugin install client-status@claude-plugins
```

## First-time setup

Run `/setup-status`. Captures:

- **Cadence** — weekly / bi-weekly / monthly
- **Day to send** — Friday afternoon (most common) / Monday morning
- **Voice match** — defaults to `~/Documents/Claude/voice.md` (cortex's shared voice file)
- **Status template** — `references/templates/status-template.md` (user-editable starter)
- **Per-client overrides** — some clients want longer / shorter / different sections; capture overrides
- **Delivery channel** — email (default) / Slack / portal / Drive folder

Saved to `references/user-context.md` (gitignored).

## Companion plugins

- **`claude-cortex`** — primary input source. Pulls `client:[name]` node memory: living summary, recent commits, open threads, knowledge entries.
- **`project-setup`** — provides engagement data (deliverables, phases, current phase, next milestone).
- **Calendar connector** — pulls meetings held this week.
- **CRM connector** — pulls recent activity (notes, deals, tasks completed).
- **`time-tracking`** — optional; if installed, can include "hours invested this week" if the user wants that level of transparency.

Works without them, but the value is mostly in the integrations — without cortex memory, the "what we learned" section is thin.

## What's inside

```
.claude-plugin/plugin.json
commands/
  client-status.md          Draft status update workflow
  setup-status.md           Interview
skills/
  client-status/SKILL.md    Auto-fires on status phrases
  setup/SKILL.md            Auto-fires on setup phrases
references/
  user-context.template.md  Structure (committed)
  user-context.md           Your config (gitignored)
  templates/
    status-template.md      Starter status template (user-editable)
```

## License

MIT.
