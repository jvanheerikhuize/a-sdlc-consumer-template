# AGENTS.md — Consumer Project Agent Entrypoint

> Read this file first. This is the primary entrypoint for all agents operating in this repository.
> This file extends the governance framework defined in `a-sdlc/AGENTS.md`.

---

## What This Repository Is

This is a **consumer project** governed by the [Agentic Software Development Life Cycle (A-SDLC)](a-sdlc/README.md).

- **Language / platform agnostic** — adapt to the stack used by this project.
- **All A-SDLC controls are binding** — governance comes from the `a-sdlc/` submodule.
- **This repository is the workspace** — stage artifacts, feature specs, and decisions live here.

---

## Mandatory Startup Sequence

Before performing any work, execute these steps **in order**:

1. **Load Core Directives (IMMUTABLE — non-negotiable):**
   ```
   a-sdlc/directives/core/core-directives.yaml
   ```

2. **Load the governance agent entrypoint:**
   ```
   a-sdlc/AGENTS.md
   ```

3. **Load the framework manifest:**
   ```
   a-sdlc/asdlc.yaml
   ```

4. **Load the consumer project manifest:**
   ```
   asdlc-consumer.yaml
   ```

5. **Load the task index (for task-driven navigation):**
   ```
   a-sdlc/tasks.yaml
   ```

6. **Load the stage context bundle for the stage you are entering:**
   ```
   a-sdlc/stages/NN-<stage-name>/NN-<stage-name>.yaml
   ```

---

## Repository Layout

```
<project-root>/
├── a-sdlc/                        ← Governance framework (git submodule — DO NOT EDIT)
├── AGENTS.md                      ← This file — consumer agent entrypoint
├── CLAUDE.md                      ← Claude Code specific instructions
├── README.md                      ← Project overview
├── asdlc-consumer.yaml            ← Consumer project manifest (name, stack, config)
│
├── specs/                         ← Feature specifications (FEAT-XXXX-title.yaml)
│   └── FEAT-0000-template.yaml    ← Template — copy and fill in for each new feature
│
└── stages/                        ← Stage workspaces — artifacts produced here
    ├── 01-intent-ingestion/
    │   └── artifacts/
    │       ├── inputs/            ← Change requests submitted here (CR-XXXX-title.yaml)
    │       └── outputs/           ← Agent-produced artifacts from Stage 1
    ├── 02-system-design/
    │   └── artifacts/
    │       └── outputs/
    ├── 03-coding-implementation/
    │   └── artifacts/
    │       └── outputs/
    ├── 04-testing-documentation/
    │   └── artifacts/
    │       └── outputs/
    ├── 05-deployment-release/
    │   └── artifacts/
    │       └── outputs/
    └── 06-observability-maintenance/
        └── artifacts/
            └── outputs/
```

---

## Stage Entry Points

| Stage | Load this governance file | Write artifacts to |
|-------|--------------------------|-------------------|
| 1 — Intent Ingestion | `a-sdlc/stages/01-intent-ingestion/01-intent-ingestion.yaml` | `stages/01-intent-ingestion/artifacts/outputs/` |
| 2 — System Design | `a-sdlc/stages/02-system-design/02-system-design.yaml` | `stages/02-system-design/artifacts/outputs/` |
| 3 — Coding & Implementation | `a-sdlc/stages/03-coding-implementation/03-coding-implementation.yaml` | `stages/03-coding-implementation/artifacts/outputs/` |
| 4 — Testing & Documentation | `a-sdlc/stages/04-testing-documentation/04-testing-documentation.yaml` | `stages/04-testing-documentation/artifacts/outputs/` |
| 5 — Deployment & Release | `a-sdlc/stages/05-deployment-release/05-deployment-release.yaml` | `stages/05-deployment-release/artifacts/outputs/` |
| 6 — Observability & Maintenance | `a-sdlc/stages/06-observability-maintenance/06-observability-maintenance.yaml` | `stages/06-observability-maintenance/artifacts/outputs/` |

---

## Working With Features

### Starting a new feature
1. Copy `stages/01-intent-ingestion/artifacts/inputs/CR-0000-template.yaml`
2. Rename to `CR-XXXX-short-title.yaml` and fill in all fields
3. Enter Stage 1 — load `a-sdlc/stages/01-intent-ingestion/01-intent-ingestion.yaml`
4. Agent transforms the CR into a Feature Specification → saved as `specs/FEAT-XXXX-title.yaml`

### Continuing an in-progress feature
1. Find the Feature Spec in `specs/`
2. Check which stage artifacts already exist under `stages/`
3. Load the governance file for the current stage
4. Continue from where the last completed artifact left off

---

## Key Behavioural Rules (inherited from governance)

All rules from `a-sdlc/AGENTS.md` apply. Summary:

- Log everything — GC-01 requires timestamped, attributable log entries for every control
- Never auto-approve your own output — human approval controls must wait for a human
- Flag conflicts explicitly — never silently resolve conflicts in the user's favour
- Escalate on ambiguity — refuse and explain rather than proceeding optimistically
- Declare provenance — all code and artifacts must be tagged per GC-03
- Respect stage boundaries — do not perform Stage N+1 work before passing Stage N gates

---

## Updating the Governance Framework

```bash
git submodule update --remote a-sdlc
```

Review the changelog before updating to understand any breaking changes.
