# Tooling and CLI on this VM

| Tool | Version / notes |
| --- | --- |
| Node | v22.23.4 |
| Bun | 1.4.4 (installed under `~/.bun`, symlinked to `/usr/local/bin/bun` for orchestrate scripts) |
| Git | Standard; hooks under `~/.cursor/agent-hooks/` for commit-msg and pre-commit Cursor guards |
| tmux | Required for long-running shell sessions per cloud agent shell policy |
| ripgrep | `CURSOR_RIPGREP_PATH` set by platform |

## Orchestrate commands (from repo root)

```bash
ORCH=/home/ubuntu/.cursor/plugins/cache/cursor-plugins/85192052/2776ddd2355d6d6c8747d3964600f28daf62f049/skills/orchestrate/scripts/cli.ts
bun "$ORCH" run --root .orchestrate/audit
bun "$ORCH" tree .orchestrate/audit
```

**Requirements:** `bun install` once in `scripts/`; `CURSOR_API_KEY` for spawn/wait loop.

## PR management

This run uses Cursor **ManagePullRequest** (first-party) rather than GitHub MCP for PR create/update when instructed by cloud task rules.

## Secrets

- App secrets: via `cursor-cloud` bind-app-secrets / dashboard (none bound for this repo at audit time)
- `CURSOR_*` env names are reserved for platform; orchestrate expects `CURSOR_API_KEY` from dashboard integrations
