# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository collects and produces industrial-grade, **general-purpose** Claude Code skills — skills intended to be reusable across projects rather than tied to a single codebase or team. A skill added here should be polished enough to ship as-is to another engineer's machine.

The repo is currently empty; everything authored here is greenfield.

## Skill Authoring Conventions

A Claude Code skill is a directory containing a `SKILL.md` with YAML frontmatter:

```
---
name: <slug>
description: <one-line trigger description used by the model to decide when to invoke>
---

<body: rules, commands, reference material>
```

The `description` is the primary signal the model uses to match user intent — write it as a concrete trigger ("Use when …"), not a feature summary. Vague descriptions cause the skill to never fire.

When creating, modifying, or evaluating a skill in this repo, use the `skill-creator` skill (available in the session). It handles scaffolding, description optimization, and variance-aware benchmarking — do not hand-roll these steps.

## Packaging & Distribution

Skills are shipped inside a **plugin**, and plugins are discovered through a **marketplace manifest**. Standard layout:

```
<repo>/
├── .claude-plugin/marketplace.json     # lists plugins in this marketplace
└── <plugin-name>/
    ├── .claude-plugin/plugin.json      # plugin metadata
    └── skills/<skill-name>/SKILL.md    # one skill per subdirectory
```

Each plugin in this repo must support **both** installation paths:

1. **Claude Code marketplace** — installable via `/plugin marketplace add <git-url>` followed by `/plugin install <plugin-name>`. The repo-level `.claude-plugin/marketplace.json` is the source of truth.
2. **npm** — each plugin also publishes as an npm package under the shared `@hd-agent-skills` scope (e.g. `@hd-agent-skills/<plugin-name>`). Users install with `npm install @hd-agent-skills/<plugin-name>` and then register the resulting `node_modules/@hd-agent-skills/<plugin-name>` path as a local Claude Code marketplace. Include the necessary `package.json` inside the plugin directory.

Organise skills by **capability domain** (e.g. `git/`, `testing/`, `docs/`) rather than by team or product. Do not bake in org-specific paths, hostnames, or container images — a skill in this repo must be portable to any machine.

## Attribution for Imported Skills

If a skill is adapted from an external source (another repo, blog post, gist, upstream project) rather than written from scratch, its provenance **must** be recorded. Either:

- add a `## References` / `## Credits` section to the skill's own `SKILL.md` or a sibling `README.md`, **or**
- add an entry to a top-level `ATTRIBUTIONS.md` that maps skill → source URL + original author + license.

Record the upstream URL, the original author/project, the license, and the date imported. If the upstream license requires it (MIT, Apache-2.0, etc.), preserve the original copyright notice verbatim. Skills with missing attribution should not be merged.

## What "Industrial-Grade" Means Here

Before adding a skill, confirm it clears this bar:

- **Generality** — no hard-coded paths, credentials, or org-specific assumptions; portable to a fresh machine.
- **Deterministic trigger** — description unambiguously distinguishes when to fire vs. when to skip (include negative examples in the body if the boundary is fuzzy).
- **Self-contained** — any referenced scripts, templates, or assets live inside the skill directory.
- **Benchmarked** — triggering accuracy measured via `skill-creator`'s eval flow before merging.
