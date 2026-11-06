# Skills and rules available to agents on this VM

## Cursor built-in skills (`~/.cursor/skills-cursor/`)

Includes agent-sdk-* skills, canvas, env-setup, migrate-to-builds, subscribe, walkthrough-artifacts, apps-database, apps-identity, and related Agent SDK workflows.

## User skill store (`/cursor/stores/user/skills/`)

| Skill directory | Purpose (from SKILL front matter) |
| --- | --- |
| Discover_PlugIns_For_Project | Recommend free Cursor marketplace plugins for the project |
| aviv-upplai-batch-ats | Batch ATS workflow (references local resume path in skill) |
| autopilotmerge / autopilot-merge | Autopilot merge helpers |

## Workspace rules (always applied in this repo)

From cursor-team-kit plugin cache:

- **no-inline-imports** — imports at top of module
- **typescript-exhaustive-switch** — `never` in default switch arms for unions/enums

## Orchestrate skill loading

- Explicit `/orchestrate <goal>` loads the orchestrate skill (`disable-model-invocation: true`).
- Root planner kickoff prompt: read orchestrate `SKILL.md`, write `plan.json`, drive `bun cli.ts run`.
- Goal prefix `audit:` sets `rootSlug` to `audit` via `inferKickoffRootSlug`.

## Subagent types (from agent runtime)

generalPurpose, explore, computerUse, videoReview, cursor-guide, ci-investigator, bugbot, security-review, best-of-n-runner, ci-watcher, thermo-nuclear-code-quality-review.
