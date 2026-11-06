# AI coding environment audit (read-only)

**Run:** `bc-f70c487a-27a4-4d4b-b732-0d58f9b5ed6b` · **Repo:** [Avivmorad/Avivmorad](https://github.com/Avivmorad/Avivmorad) · **Date:** 2026-11-06

## Executive summary

This smoke run exercised the **orchestrate** substrate as root planner for goal `ai-env-audit: comprehensive read-only audit of the AI coding environment`. The VM is a standard Cursor cloud agent on a **default image fallback** (no successful prebuilt environment build). Tooling (Node, Bun, git, gh, ripgrep) is present. **Two blockers** prevented fully automated fan-out:

1. **`ai-env-audit` SKILL.md never mounted** (not in agent store, not in public `cursor/plugins`).
2. **`CURSOR_API_KEY` is unset**, so `bun cli.ts run --root .orchestrate/ai-env-audit` cannot spawn workers.

Deliverables below were completed read-only on the root planner branch; see `audit/sections/` and `audit/reference/` for detail.

## Runtime and egress

See [audit/sections/runtime-egress.md](./sections/runtime-egress.md).

- Linux 6.12.113+ / x86_64, user `ubuntu`
- Egress: unrestricted for this run (cursor-cloud)
- Orchestrate CLI installed under `/tmp/plugins/orchestrate/...` with `bun install` complete

## Agent surface

See [audit/sections/agent-surface.md](./sections/agent-surface.md).

- User skills: autopilot-merge, autopilotmerge, aviv-upplai-batch-ats, Discover_PlugIns_For_Project
- Dynamic MCP: Github, Context7, cursor-cloud, cursor-subscriptions, cursor
- **Missing:** cloud-managed `ai-env-audit` skill referenced by kickoff prompt

## Orchestrate plan

- Workspace: `.orchestrate/ai-env-audit/plan.json`
- `plan.selfAgentId`: `bc-f70c487a-27a4-4d4b-b732-0d58f9b5ed6b`
- `plan.dispatcher.firstName`: Aviv
- `plan.summary`: read-only audit of this cloud agent coding environment via orchestrate smoke run
- Tasks remain **unspawned** until `CURSOR_API_KEY` is configured for the loop host

## Limitations and follow-ups

| Item | Severity | Notes |
| --- | --- | --- |
| Missing `ai-env-audit` skill | High | Fix cloud-managed skill provisioning for SDK kickoff goals that reference it |
| Missing `CURSOR_API_KEY` | High | Export a user key for orchestrate spawn (`cursor-sdk` auth) |
| No environment build | Medium | Linked personal environment has `no_finished_builds`; agents skip custom `install` |
| Push protection | Info | Bootstrap must never include tokenized `git remote` URLs |

## Acceptance (planner-level)

| Criterion | Status |
| --- | --- |
| Report covers runtime, toolchain, agent surface, secrets/egress, orchestrate | Met (this file + sections) |
| Read-only (no unrelated repo edits) | Met |
| Evidence in paths / handoff-style sections | Met |
