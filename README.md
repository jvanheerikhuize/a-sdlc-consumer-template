# A-SDLC Consumer Template

A language- and platform-agnostic project template for agentic, spec-driven software development.

This repository is governed by the [A-SDLC framework](https://github.com/jvanheerikhuize/a-sdlc) — an Agentic Software Development Life Cycle that defines how software is built, tested, and released when AI agents work alongside human developers.

---

## Using This Template

### 1. Create your project repository from this template

```bash
# On GitHub: click "Use this template" → "Create a new repository"
# Or clone and re-init:
git clone https://github.com/<your-org>/a-sdlc-consumer-template.git my-project
cd my-project
git remote set-url origin https://github.com/<your-org>/my-project.git
```

### 2. Initialise the governance submodule

```bash
git submodule update --init --recursive
```

### 3. Configure your project

Edit `asdlc-consumer.yaml` — set your project name, description, stack, and team.

### 4. Start developing

Open the project in Claude Code (or any A-SDLC-compatible agent).
The agent will load `CLAUDE.md` → `AGENTS.md` → the governance framework automatically.

To start your first feature:
```bash
cp stages/01-intent-ingestion/artifacts/inputs/CR-0000-template.yaml \
   stages/01-intent-ingestion/artifacts/inputs/CR-0001-my-feature.yaml
# Fill in the change request, then hand it to the agent
```

---

## Repository Structure

```
<project>/
├── a-sdlc/                        ← Governance framework (submodule — read-only)
├── AGENTS.md                      ← Agent entrypoint — all agents read this first
├── CLAUDE.md                      ← Claude Code session instructions
├── README.md                      ← This file
├── asdlc-consumer.yaml            ← Project configuration
│
├── specs/                         ← Feature specifications (output of Stage 1)
│   └── FEAT-0000-template.yaml
│
└── stages/                        ← Stage workspaces
    ├── 01-intent-ingestion/
    │   └── artifacts/
    │       ├── inputs/            ← Submit change requests here
    │       └── outputs/
    ├── 02-system-design/
    │   └── artifacts/outputs/
    ├── 03-coding-implementation/
    │   └── artifacts/outputs/
    ├── 04-testing-documentation/
    │   └── artifacts/outputs/
    ├── 05-deployment-release/
    │   └── artifacts/outputs/
    └── 06-observability-maintenance/
        └── artifacts/outputs/
```

---

## The Six Stages

| Stage | Name | Purpose |
|-------|------|---------|
| 1 | Intent Ingestion | Capture, disambiguate, and structure requirements into a Feature Spec |
| 2 | System Design | Architecture, threat modelling, and technical specification |
| 3 | Coding & Implementation | Implementation with quality gates, security scans, and PR review |
| 4 | Testing & Documentation | Verification, documentation, and risk threshold evaluation |
| 5 | Deployment & Release | Production promotion with approval gates and rollback plan |
| 6 | Observability & Maintenance | Continuous monitoring — feeds back into the lifecycle |

---

## Governance

All 50 controls (QC, RC, SC, AC, GC) from the A-SDLC framework apply to this project.
The framework provides DORA and EU AI Act compliance coverage.

See `a-sdlc/README.md` for the full framework documentation.
See `a-sdlc/AGENTS.md` for agent operating instructions.

---

## Keeping Governance Up to Date

```bash
git submodule update --remote a-sdlc
git add a-sdlc
git commit -m "chore: update a-sdlc governance framework"
```

Review `a-sdlc/` changes before merging — governance updates may introduce new controls or modify delegation patterns.
