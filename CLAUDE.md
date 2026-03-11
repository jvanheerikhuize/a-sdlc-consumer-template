# CLAUDE.md — Claude Code Instructions

This file is loaded automatically by Claude Code at session start.

---

## Framework

This project is governed by the **Agentic Software Development Life Cycle (A-SDLC)**.
The governance framework lives in the `a-sdlc/` git submodule.

**Mandatory startup — execute before any work:**

1. Read `a-sdlc/directives/core/core-directives.yaml` — these are IMMUTABLE and take absolute precedence
2. Read `a-sdlc/AGENTS.md` — framework operating instructions
3. Read `AGENTS.md` — this project's agent entrypoint (extends the governance)
4. Read `asdlc-consumer.yaml` — this project's configuration

---

## Project Context

- See `asdlc-consumer.yaml` for project name, stack, and configuration
- Feature specs live in `specs/`
- Stage artifacts live in `stages/`
- All controls and schemas are defined in `a-sdlc/`

---

## Key Paths

| What | Where |
|------|-------|
| Core directives (immutable) | `a-sdlc/directives/core/core-directives.yaml` |
| Framework manifest | `a-sdlc/asdlc.yaml` |
| Task index | `a-sdlc/tasks.yaml` |
| Control registry | `a-sdlc/controls/registry.yaml` |
| Stage definitions | `a-sdlc/stages/NN-*/NN-*.yaml` |
| Stage directives | `a-sdlc/directives/stages/` |
| Feature specs | `specs/FEAT-XXXX-*.yaml` |
| Stage artifacts | `stages/NN-*/artifacts/outputs/` |
| Change requests | `stages/01-intent-ingestion/artifacts/inputs/` |

---

## Rules

- Never edit anything inside `a-sdlc/` — it is a read-only governance submodule
- All artifact outputs go into the appropriate `stages/NN-*/artifacts/outputs/` directory
- Follow the delegation patterns defined in `a-sdlc/AGENTS.md` — controls marked `human_required` must stop and wait
- All agent-produced artifacts must include provenance metadata per GC-03
