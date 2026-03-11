# CLAUDE.md — Claude Code Adapter

> This is a thin adapter shim. All agent instructions and project configuration
> live in `AGENTS.md` and `.agent/settings.yaml`.

## Startup

Before any work, read these files in order:

1. `a-sdlc/directives/core/core-directives.yaml` — IMMUTABLE, absolute precedence
2. `AGENTS.md` — mandatory operating instructions for this project
3. `.agent/settings.yaml` — structured config (paths, rules, read-only boundaries)
4. `asdlc-consumer.yaml` — project configuration
