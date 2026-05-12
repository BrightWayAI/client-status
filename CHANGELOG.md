# Changelog

All notable changes to client-status are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/). Versions match `plugin.json`.

## [0.2.4] — Person-page side effect on status updates (2026-05-12)

### Added
- **`/client-status` Step 6 — person-page Recent-interactions append.** After the user confirms a status update was sent (or when a draft is produced if send-confirmation was skipped), append a `<today> — status-update-sent — week of <week-start>: <highlights>` line to the primary contact's cortex person page if one exists at `<config-root>/memory/person/<slug>.md`. Updates Last meaningful contact and refreshes Relationship temperature toward Active.
- **Graceful degradation.** No-op if cortex isn't installed or the contact has no graduated page.

### Why this matters
Phase 3 of SECOND-BRAIN-V2-SPEC. The weekly cadence of client status updates is one of the strongest relationship-heartbeat signals available — and previously it left no trail at the person-page level. This side effect makes the relationship's regular rhythm visible on the canonical page.

## [0.2.3] — Platform-agnostic Step 0 (2026-05-12)

### Changed
- **Setup command Step 0 now platform-agnostic.** Every `request_cowork_directory(...)` call is conditional: "In Cowork, call `request_cowork_directory(...)`. In Claude Code (or any environment with direct filesystem access), no mount is needed." Same plugin source works in both runtimes.

### Why this matters
Phase 0 of SECOND-BRAIN-V2-SPEC. Removes the implicit Cowork-only assumption so Claude Code users do not hit unsupported tool calls during setup.

## [0.2.0] — Config-root refactor

### Changed
- **Plugin config moved to a user-chosen folder.** Reads/writes now go to `<config-root>/plugins/client-status.user-context.md` via the pointer at `~/Documents/.claude-plugin-config-root`.
- **`/setup-status` Step 0 bootstraps the config root** and reads shared identity + voice.
- **`/client-status` updated** to read from the new path.
- **User-facing prompts debranded** for fork-friendliness.

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
