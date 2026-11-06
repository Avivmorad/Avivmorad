# AI coding environment atlas (Avivmorad)

This folder maps **everything agents can see** when working in `github.com/Avivmorad/Avivmorad` on a Cursor cloud agent VM: the profile repo, linked external projects, installed plugins/skills, MCP tools, cloud runtime, and the orchestrate loop used for this audit.

## Start here

1. [ENVIRONMENT_MAP.md](./ENVIRONMENT_MAP.md) — executive summary and index
2. [ARCHITECTURE.md](./ARCHITECTURE.md) — diagram of layers
3. [reference/](./reference/) — inventories (do not duplicate full scans in sections)
4. [sections/](./sections/) — narrative deep dives

## Regenerating

- Reference pack: re-run discovery scripts or orchestrate task `bootstrap-reference-pack`
- Orchestrate loop: `bun <orchestrate>/cli.ts run --root .orchestrate/audit` (requires `CURSOR_API_KEY`)
