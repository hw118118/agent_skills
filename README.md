# agent_skills

An industrial-grade, **general-purpose** Claude Code skill marketplace. Skills here are intended to be portable across projects — no org-specific paths, hostnames, or credentials baked in.

## Plugins in this marketplace

| Plugin | Skills | Description |
|--------|--------|-------------|
| [`andrej-karpathy-skills`](andrej-karpathy-skills/) | `karpathy-guidelines` | Behavioral guidelines to reduce common LLM coding mistakes — Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution. |
| [`codebase-analyzer-docs`](codebase-analyzer-docs/) | `codebase-analyzer-docs` | Generate deep, structured onboarding documentation for a whole codebase — architecture, module deep-dives, grounded code snippets, and Mermaid diagrams. |

## Install

Every plugin in this repo supports **two** installation paths.

### 1. Claude Code marketplace (recommended)

```
/plugin marketplace add <git-url-of-this-repo>
/plugin install <plugin-name>
```

The repo-level [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) is the manifest.

### 2. npm

Each plugin is also published to npm under the shared `@hd-agent-skills` scope so it can be installed standalone:

```bash
npm install @hd-agent-skills/<plugin-name>
/plugin marketplace add ./node_modules/@hd-agent-skills/<plugin-name>
/plugin install <plugin-name>
```

Note: `/plugin install` always takes the **plugin name** (e.g. `andrej-karpathy-skills`), not the skill name inside it (e.g. `karpathy-guidelines`). Plugin names are listed in the table above and in [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json).

The `postinstall` hook prints the exact `marketplace add` path.

## Authoring & attribution

- See [`CLAUDE.md`](CLAUDE.md) for the skill-authoring conventions, packaging layout, and "industrial-grade" acceptance bar.
- Skills adapted from external sources must be recorded in [`ATTRIBUTIONS.md`](ATTRIBUTIONS.md) **and** credited in the plugin's own `README.md`.
