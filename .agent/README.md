# .agent/ — Tool-Agnostic Agent Configuration

This directory is the single source of truth for agent behaviour in this project.
It is tool- and model-agnostic: any AI coding assistant can read it.

## Contents

| File | Purpose |
| ---- | ------- |
| `settings.yaml` | Structured agent config — startup sequence, paths, rules, read-only boundaries |

## How It Works

```
.agent/settings.yaml            ← canonical config (this directory)
        ↑
        referenced by
        ↓
AGENTS.md                       ← primary human-readable entry point (all agents)
.github/copilot-instructions.md ← GitHub Copilot adapter shim
```

## Adding a New Agent Adapter

1. Create a thin shim file in the project root (or the tool's required location).
2. The shim should instruct the agent to read `AGENTS.md` and `.agent/settings.yaml`.
3. Register it in `.agent/settings.yaml` under `adapters`.
4. Keep all logic in `AGENTS.md` — shims must not duplicate content.
