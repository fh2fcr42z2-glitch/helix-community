# Cursor plugins and skills (this repo)

Vendored [continual-learning](https://github.com/cursor/plugins/tree/main/continual-learning) and [teaching](https://github.com/cursor/plugins/tree/main/teaching) (MIT, Cursor). Desktop can still `/add-plugin` those names; this tree is so Cloud Agents and clones see the skills without a marketplace click.

| Path | Job |
| --- | --- |
| `plugins/continual-learning/` | Stop hook + skill + `agents-memory-updater` → root `AGENTS.md` |
| `plugins/teaching/` | `create-learning-path` · `run-learning-retrospective` |
| `skills/` | Project copies of those skills (agent discovery) |
| `agents/agents-memory-updater.md` | Subagent spec for memory updates |
| `hooks.json` | Workspace stop hook (needs `bun` on the machine that runs hooks) |
| `hooks/state/` | Cadence + transcript index — **gitignored JSON**, no secrets |

Public contract: [docs/LEARNING-PATH.md](../docs/LEARNING-PATH.md). Live sessions: [`teaching/`](../teaching/). Chart bot retros stay in [`ta-learning/`](../ta-learning/). **No keys in any of these files.**
