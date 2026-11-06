# Agent surface (skills, MCP, orchestration)

Read-only inventory for this cloud agent run.

## Cloud agent identity

- **bcId:** `bc-f70c487a-27a4-4d4b-b732-0d58f9b5ed6b`
- **Run name:** `ai-env-audit-root`
- **Source:** SDK kickoff with goal `ai-env-audit: comprehensive read-only audit of the AI coding environment`

## Skills

### Expected

Kickoff instructs: **Read `ai-env-audit` skill `SKILL.md`**. That skill **did not mount** under `/cursor/stores/user/skills/` after `provisionCloudManagedSkills` (only user-owned skills present).

### Mounted user skills (`/cursor/stores/user/skills/`)

- `autopilot-merge`
- `autopilotmerge`
- `aviv-upplai-batch-ats`
- `Discover_PlugIns_For_Project`

Cursor Team Kit skills are available via the local plugin cache under `~/.cursor/plugins/cache/cursor-public/677/.../skills/` (check-compiler-errors, fix-ci, orchestrate-adjacent tooling, etc.) but **`ai-env-audit` is not present** in public `cursor/plugins` either.

## Dynamic MCP (this session)

Namespaces exposed to the agent include **Github**, **Context7**, **cursor-cloud**, **cursor-subscriptions**, and **cursor** (native tools). Authentication state varies by namespace; failed MCP auth surfaces as run events (`mcp_auth_error`) when applicable.

## Subagents

Subagent types advertised to the root planner include `generalPurpose`, `explore`, `computerUse`, `ci-investigator`, `bugbot`, `security-review`, and others (see run system prompt). This audit did not spawn subagents.

## Orchestrate

- Planner workspace: `/workspace/.orchestrate/ai-env-audit/plan.json`
- CLI: `/tmp/plugins/orchestrate/skills/orchestrate/scripts/cli.ts`
- Blocker: **`CURSOR_API_KEY` unset** → loop cannot spawn workers

## Secrets hygiene (names only)

- Platform metadata: `CLOUD_AGENT_ALL_SECRET_NAMES=OpenRouterKey,TavilyApi`
- **Do not** commit credential-bearing `git remote` URLs; bootstrap reference uses sanitized GitHub HTTPS URLs only
