# Changelog

All notable changes to client-status are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/). Versions match `plugin.json`.

## [0.1.0] — Initial release

### Added
- Weekly client status update drafting (`/client-status [client?]`) — pulls from cortex memory (client node living summary, recent commits, knowledge entries, open threads), project-setup (engagement data, current phase, milestones), calendar (this week's external meetings), CRM activity, and optionally time-tracking (hours logged this period).
- Default sections in drafts: What we did this week / What we learned / What's next / Anything we need from you / optional Thought-leadership share.
- User-editable status template at `references/templates/status-template.md`.
- `/setup-status` interview — captures cadence (weekly / bi-weekly / monthly), day to send, status template path, per-client overrides (longer / shorter / different sections / EXCLUDE), optional inclusions (time-tracking hours, thought-leadership shares), delivery channel.
- Drafts go for user review and manual send — never auto-sent.
- Optional cortex changelog entry after sending so future sessions know what was sent.
- Honors `[INTERNAL]` and `[CONFIDENTIAL]` tags in cortex memory — never surfaces those in client-facing drafts.
- Setup reads `~/Documents/Claude/identity.md` and `~/Documents/Claude/voice.md` (shared config from cortex) when available.
