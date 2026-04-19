# Attributions

This file records the provenance of every skill in this repository that was adapted from an external source, as required by `CLAUDE.md` → *Attribution for Imported Skills*.

Skills authored from scratch inside this repo are **not** listed here.

| Skill / Plugin | Source (reference URL) | Original author | License | Imported | Notes |
|----------------|------------------------|-----------------|---------|----------|-------|
| `andrej-karpathy-skills` → `karpathy-guidelines` | [multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills/tree/main) | [forrestchang](https://github.com/forrestchang) (original); redistributed by multica-ai | MIT | 2026-04-19 | Four behavioral principles; inspired by [Karpathy's X post](https://x.com/karpathy/status/2015883857489522876). License file was absent in `multica-ai` — MIT taken from SKILL.md frontmatter and upstream `forrestchang/andrej-karpathy-skills`. |

## How to add a new entry

When importing a skill from elsewhere:

1. Append a row to the table above with: skill/plugin name, upstream URL (pinned to the commit or tag you imported from, if possible), original author, license, import date (YYYY-MM-DD), and any modifications notes.
2. Also add a `## Credits & References` section (or equivalent) to the plugin's own `README.md` — attribution must be visible to anyone who installs just that plugin.
3. Copy the upstream `LICENSE` file into the plugin directory verbatim if the license requires it (MIT, Apache-2.0, BSD, etc.).
4. If you modified the imported content, note *what* changed in the "Notes" column — don't silently diverge from upstream.
