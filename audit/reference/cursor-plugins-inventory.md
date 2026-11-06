# Installed Cursor marketplace plugins (VM cache)

| Plugin | Version | Display name | Cache path (under `~/.cursor/plugins/cache`) |
| --- | --- | --- | --- |
| orchestrate | 1.1.0 | Orchestrate | `cursor-plugins/85192052/2776ddd2355d6d6c8747d3964600f28daf62f049` |
| cursor-team-kit | 1.2.0 | Cursor Team Kit | `cursor-public/677/ae5650febf4320793844c12c4adaa937f417f8da` |
| github | 1.0.0 | GitHub | (MCP server bundled with GitHub integration) |

## Orchestrate CLI

- Skill: `.../skills/orchestrate/SKILL.md`
- Loop entrypoint: `.../skills/orchestrate/scripts/cli.ts`
- Requires `bun` and `CURSOR_API_KEY` for `run` / `kickoff` / spawn subcommands.

## Cursor Team Kit

Skills under `.../skills/` include: check-compiler-errors, control-cli, control-ui, fix-ci, fix-merge-conflicts, loop-on-ci, review-and-ship, run-smoke-tests, verify-this, weekly-review, workflow-from-chats, and others.

Rules shipped with the plugin:

- `rules/no-inline-imports.mdc`
- `rules/typescript-exhaustive-switch.mdc`
