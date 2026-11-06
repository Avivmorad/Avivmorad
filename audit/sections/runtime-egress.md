# Runtime and egress

Captured read-only on the cloud agent VM (2026-11-06).

## Host

- Kernel: Linux 6.12.113+ on x86_64 (`uname -a`)
- User: `ubuntu`; workspace: `/workspace`
- Environment build: **no finished builds**; pod booted with **default image fallback** (see cursor-cloud `environment-info` for this run)

## Key paths

| Path | Role |
| --- | --- |
| `/workspace` | Checked-out target repo |
| `/cursor/stores` | FUSE-mounted agent store (user skills, per-run artifacts) |
| `/exec-daemon` | Agent tooling on PATH (node, gh, rg, …) |
| `/tmp/plugins/orchestrate/...` | Orchestrate CLI used for this smoke run (sparse clone) |

## Egress

From cursor-cloud MCP for this run: **egress not restricted** (`restricted: false`), agent-tree narrowing off.

## Orchestrate substrate (this run)

- Bun installed at `~/.bun/bin/bun` (1.4.4); dependencies installed under orchestrate `scripts/`
- `bun cli.ts run --root /workspace/.orchestrate/ai-env-audit` exits **2** with `CURSOR_API_KEY required` — worker spawn cannot proceed until a Cursor user API key is available in the environment

## Evidence commands

```bash
uname -a
whoami
free -h
df -h /workspace
```
