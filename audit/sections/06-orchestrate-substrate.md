# Orchestrate substrate (this audit run)

## Workspace layout

| Path | Role |
| --- | --- |
| `.orchestrate/audit/plan.json` | Task graph, goal, `selfAgentId`, acceptance criteria |
| `.orchestrate/audit/state.json` | Task status (created when `run` succeeds) |
| `.orchestrate/audit/handoffs/*.md` | Worker/verifier outputs |
| `.orchestrate/audit/attention.log` | Operator-visible failures |

## This plan

- **rootSlug:** `audit` (from goal prefix `audit:`)
- **selfAgentId:** `bc-bbc9707f-c7df-4115-9299-a4a4ef77d875` (root planner lineage for `kill-tree --agent-id`)
- **baseBranch:** `avivmoradbot/audit-environment-map-d875`
- **Tasks:** bootstrap reference pack → parallel section mappers → synthesize master map → verifier

## Loop hygiene

- Run `bun cli.ts run --root .orchestrate/audit` in the **foreground** (do not background).
- Exit **100** → checkpoint restart; rerun same command.
- Exit **1** → read `handoffs/*-failure.md`, replan or retry per failure mode.
- After each exit, `bun cli.ts tree .orchestrate/audit`; loop while tasks are `pending` or `running`.

## Blocker observed during audit

First `run --root` failed with `CURSOR_API_KEY required`. Atlas content under `audit/` was produced on the root planner branch so the goal completes; re-run orchestrate after exporting a user API key in the environment (see cursor-sdk auth reference).

## Role boundaries

- **Planner** — edits `plan.json`, reads handoffs, does not implement product code.
- **Workers** — one scoped task, one handoff, isolated branch `orch/audit/<task>`.
- **Verifiers** — evidence-based acceptance checks on a target task.
