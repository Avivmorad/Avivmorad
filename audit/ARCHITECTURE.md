# Architecture — repo, cloud VM, and agent stack

```mermaid
flowchart TB
  subgraph repo["Git repo Avivmorad"]
    README[README.md profile index]
    AUDIT[audit/ atlas]
    ORCH_PLAN[".orchestrate/audit/plan.json"]
  end

  subgraph vm["Cloud agent VM"]
    BUILD[Environment build snapshot]
    CHECKOUT[Git checkout on branch]
    SHELL[Shell + Node + Bun]
  end

  subgraph cursor["Cursor agent runtime"]
    PLUGINS[Plugins: orchestrate team-kit github]
    SKILLS[skills-cursor + user store]
    MCP[MCP: Github Context7 cursor-cloud subscriptions]
    SUB[Subagents Task tool]
  end

  subgraph orch["Orchestrate loop optional"]
    CLI[cli.ts run]
    SPAWN[Spawn cloud workers]
    HO[handoffs/]
  end

  BUILD --> CHECKOUT
  CHECKOUT --> repo
  CHECKOUT --> SHELL
  SHELL --> cursor
  ORCH_PLAN --> CLI
  CLI -->|"CURSOR_API_KEY"| SPAWN
  SPAWN --> HO
  HO --> AUDIT
  PLUGINS --> SKILLS
  MCP --> SUB
  README -.->|links| EXT[External project repos]
```

## Data flow for this audit

1. Dispatcher/SDK kickoff created root planner `bc-bbc9707f-...` with goal `audit: ...`.
2. Root planner wrote `plan.json` and committed the `audit/` atlas (orchestrate `run` blocked on missing API key).
3. Downstream agents should read `audit/reference/` before rescanning the VM.

## Trust boundaries

- **Git + disk** — authoritative for orchestrate state when `syncStateToGit: true`
- **Slack** — optional mirror; not required for correctness
- **MCP** — side channels for GitHub, docs, cloud diagnostics; not orchestrate task state
