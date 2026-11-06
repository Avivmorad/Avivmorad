# Environment map — executive summary

**Scope:** `/agent/repos/Avivmorad` on a Cursor cloud agent (composer-2.5-fast, personal environment build `bld-20261106-5fc1aebd-710a-4348-920d-6717b5ae74af`).

## One-screen picture

| Layer | What exists today | Detail |
| --- | --- | --- |
| **Repository** | Profile README + this audit; no app code in-tree | [sections/01-repository.md](./sections/01-repository.md) |
| **Linked products** | Four named projects (two private) | [sections/02-linked-projects.md](./sections/02-linked-projects.md) |
| **Cursor stack** | Orchestrate, Team Kit, GitHub MCP; user skills store | [sections/03-cursor-plugins-and-skills.md](./sections/03-cursor-plugins-and-skills.md) |
| **Cloud runtime** | MCP namespaces, subagents, build snapshot | [sections/04-cloud-agent-runtime.md](./sections/04-cloud-agent-runtime.md) |
| **Tooling** | Node 22, Bun for orchestrate CLI, git hooks | [sections/05-tooling-and-cli.md](./sections/05-tooling-and-cli.md) |
| **Orchestration** | `.orchestrate/audit/` plan; spawn blocked without API key | [sections/06-orchestrate-substrate.md](./sections/06-orchestrate-substrate.md) |

## Reference artifacts (machine-readable)

- [reference/repo-tree.txt](./reference/repo-tree.txt)
- [reference/cursor-plugins-inventory.md](./reference/cursor-plugins-inventory.md)
- [reference/skills-inventory.md](./reference/skills-inventory.md)
- [reference/mcp-namespaces.json](./reference/mcp-namespaces.json)
- [reference/cloud-runtime-snapshot.json](./reference/cloud-runtime-snapshot.json)

## Key findings

1. **Repo role** — This git root is a portfolio/index; agents must follow README links for real codebases.
2. **Plugins** — Orchestrate 1.1.0 drives multi-agent plans; Team Kit supplies CI/review skills and TS/import rules.
3. **Integrations** — GitHub + Context7 MCP, cursor-cloud diagnostics, cursor-subscriptions for async events.
4. **Gap** — `CURSOR_API_KEY` is not in the shell env, so the orchestrate spawn loop cannot run until a dashboard user key is exported for `cli.ts`.

## Acceptance checklist (planner)

- [x] `ENVIRONMENT_MAP.md` links every section
- [x] `reference/` holds reusable inventories
- [x] Six section files under `sections/`
- [x] `ARCHITECTURE.md` includes a mermaid diagram
