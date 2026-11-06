# Cursor plugins, skills, and rules

## Marketplace plugins on this VM

See [../reference/cursor-plugins-inventory.md](../reference/cursor-plugins-inventory.md) for paths and versions.

| Layer | What it provides |
| --- | --- |
| **Orchestrate** | Multi-agent cloud planning loop (`plan.json`, `cli.ts`, handoffs) |
| **Cursor Team Kit** | CI/review/shipping skills, control-cli/ui harnesses, workspace rules |
| **GitHub** | MCP tools for issues, PRs, code search, and repository operations |

## Skill discovery order (typical cloud agent)

1. User-invoked skills (e.g. `/orchestrate`, plugin skills)
2. `~/.cursor/skills-cursor/` (Cursor-maintained)
3. `/cursor/stores/user/skills/` (user-mounted store)
4. Plugin-bundled skills under `~/.cursor/plugins/cache/.../skills/`

## Rules affecting code generation

Always-on workspace rules from cursor-team-kit:

- Keep imports at module top (no inline imports unless documented circular dependency)
- TypeScript switches on unions/enums must use exhaustive `never` default

## User-specific skills

Documented in [../reference/skills-inventory.md](../reference/skills-inventory.md), including Discover_PlugIns_For_Project and autopilot merge skills.
