# Repository surface

## Identity

- **Path:** `/agent/repos/Avivmorad`
- **Remote:** `https://github.com/Avivmorad/Avivmorad`
- **Default branch:** `main`
- **Active audit branch:** `avivmoradbot/audit-environment-map-d875`

## In-tree contents (profile repo)

This repository is a **personal profile and project index**, not an application monorepo. At audit time the tracked product surface is:

- `README.md` — bio, skills, education, experience, and links to external projects
- `.orchestrate/audit/` — orchestrate plan and (when the loop runs) state/handoffs for this audit run
- `audit/` — committed environment atlas produced by this audit

There is no `package.json`, application source, or `.cursor/` directory in the repo yet.

## Git workflow notes

- Cloud agent branch naming policy for this run: `avivmoradbot/<descriptive-name>-d875`
- Orchestrate worker branches would use `orch/audit/<task-name>` when spawned via the orchestrate CLI

## External work

Implementation for MailPriority, InterviewPilot, Banger or Bot, and Agent-Biz lives in other repositories or private repos referenced from the README. See [02-linked-projects.md](./02-linked-projects.md).
