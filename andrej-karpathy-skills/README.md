# andrej-karpathy-skills

Behavioral guidelines to reduce common LLM coding mistakes, derived from [Andrej Karpathy's observations](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls.

Ships the `karpathy-guidelines` skill, covering four principles:

| Principle | Addresses |
|-----------|-----------|
| **Think Before Coding** | Wrong assumptions, hidden confusion, missing tradeoffs |
| **Simplicity First** | Overcomplication, bloated abstractions |
| **Surgical Changes** | Orthogonal edits, touching code you shouldn't |
| **Goal-Driven Execution** | Verifiable success criteria, test-first loops |

See [`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md) for the full rules.

## Install

### Option A — Claude Code marketplace

From the parent `agent_skills` repo:

```
/plugin marketplace add <git-url-of-agent_skills>
/plugin install andrej-karpathy-skills
```

### Option B — npm

```bash
npm install @hd-agent-skills/andrej-karpathy-skills
# then register the installed directory as a local marketplace:
/plugin marketplace add ./node_modules/@hd-agent-skills/andrej-karpathy-skills
/plugin install andrej-karpathy-skills
```

The `postinstall` script prints the exact `marketplace add` path to use.

## Credits & References

This plugin is **not original work** — it repackages an existing skill for distribution through this marketplace.

- **Primary source referenced for this import:** [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) (commit on `main`, imported 2026-04-19).
- **Original author:** [forrestchang](https://github.com/forrestchang) — [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills).
- **Inspiration:** [Andrej Karpathy's X post](https://x.com/karpathy/status/2015883857489522876) on LLM coding pitfalls.
- **License:** MIT (see [LICENSE](LICENSE) — original copyright preserved).

If upstream updates the guidelines, re-sync this plugin from the source above rather than editing in place.
