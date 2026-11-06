# Cloud agent runtime

## Run identity

Snapshot: [../reference/cloud-runtime-snapshot.json](../reference/cloud-runtime-snapshot.json)

| Field | Value |
| --- | --- |
| Agent id | `bc-bbc9707f-c7df-4115-9299-a4a4ef77d875` |
| Model | composer-2.5-fast |
| Source | sdk (orchestrate kickoff) |
| Environment | Personal (`ac040046-d9b1-11f1-ba91-f63b1661ac50`) |
| Build | `bld-20261106-5fc1aebd-710a-4348-920d-6717b5ae74af` |
| Egress | Unrestricted (`restricted: false`) |

## VM layers

1. **Environment build snapshot** — OS, preinstalled toolchains, warm-fork boot (`lazy_load`, `gitSetup: reuse`)
2. **Git checkout** — branch checked out on top of snapshot (here: `avivmoradbot/audit-environment-map-d875`)
3. **Agent session** — MCP tools, subagents, shell, optional `start`/`terminals` from environment.json (not exposed for this personal environment)

## MCP and native tools

Namespace summary: [../reference/mcp-namespaces.json](../reference/mcp-namespaces.json)

- **Github** — repository and PR automation
- **Context7** — library documentation lookup
- **cursor-cloud** — run info, environment builds, publish-app, secrets binding
- **cursor-subscriptions** — wait for CI/PR/Slack/Linear events
- **cursor** — Task, TodoWrite, WebSearch, shell-adjacent helpers

## Subagents

Specialized subprocess types include explore, computerUse, ci-watcher, ci-investigator, bugbot, security-review, and others listed in the agent runtime configuration.

## Credential gap (orchestrate)

`CURSOR_API_KEY` is **not** exported in the agent shell environment, so `bun cli.ts run` cannot spawn child cloud agents from this VM until a user API key is available to the process. The run itself was created via SDK kickoff using platform credentials.
