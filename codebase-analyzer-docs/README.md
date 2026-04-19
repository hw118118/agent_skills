# codebase-analyzer-docs

Generate **deep, structured onboarding documentation** for an entire codebase — not a polished README, but the doc suite a new engineer actually needs to start contributing.

Output is a multi-file set under `docs/codebase/` (inside the target repo):

```
docs/codebase/
├── OVERVIEW.md          # one-page tour, repo-level diagram
├── QUICKSTART.md        # clone → build → test, from real scripts
├── ARCHITECTURE.md      # layers, components, data flows, rationale
├── GLOSSARY.md          # project-specific vocabulary
├── diagrams/            # Mermaid: component, sequence, ER, state
├── modules/             # per-module deep-dives (5–8 typical)
└── decisions/           # ADR notes (deep mode only)
```

Every non-obvious claim cites `path/to/file.ext:line`. Diagrams reflect actual code, not templates. Uncertainty is flagged explicitly rather than papered over.

## Depth tiers

- **lite** — overview + quickstart + one diagram.
- **standard** *(default)* — all glue docs + 3–8 module deep-dives + 2–4 diagrams.
- **deep** — standard + per-submodule docs + ADR decisions + data-model doc.

Activate by asking Claude something like: *"Write a full architecture writeup for this repo"*, *"Help me onboard to this codebase"*, *"Produce onboarding docs for the backend service"*. The skill triggers on whole-codebase asks; single-file questions are handled inline.

## Install

### Option A — Claude Code marketplace

From the parent `agent_skills` repo:

```
/plugin marketplace add <git-url-of-agent_skills>
/plugin install codebase-analyzer-docs
```

### Option B — npm

```bash
npm install @hd-agent-skills/codebase-analyzer-docs
/plugin marketplace add ./node_modules/@hd-agent-skills/codebase-analyzer-docs
/plugin install codebase-analyzer-docs
```

The `postinstall` script prints the exact `marketplace add` path.

## What it will NOT do

- Single-file / single-function explanations (answer inline instead).
- API reference generation from docstrings (use Sphinx / TypeDoc / rustdoc).
- Top-level `README.md` polish.
- Hallucinated architecture — if evidence is missing, the skill marks uncertainty rather than guessing.

## License

MIT. Authored from scratch inside the [`agent_skills`](../) marketplace.
