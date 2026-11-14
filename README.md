# agile-skills

Customer-led agile skills for Claude Code. You are the customer: you own vision, scope, priority and acceptance. The agent owns estimates, risks and how to build.

Every skill runs under the [working agreement](WORKING-AGREEMENT.md).

## Skills

| Skill | What it does | Writes |
|---|---|---|
| `setup` | Records how the project works: issue tracker, commits, branching. Run it first. | `docs/setup.md` |
| `vision` | Captures or revises the product vision. | `docs/vision.md` |
| `issues` | Creates issues from notes, refines or splits existing ones. | the tracker |
| `backlog-review` | Checks the top of the backlog against the vision. Read-only. | nothing |
| `ddd` | Guides a group session towards the ubiquitous language. | `docs/contexts/*/glossary.md` |
| `research` | Researches a question into a sourced note. | `docs/research/` |
| `commit` | Commits as conventional commits, one per logical change, and keeps the end-user changelog. | git, `CHANGELOG.json` |

All paths are in the project you run the skill in.

## Use

This repo is a Claude Code plugin. Load it from a local checkout:

```sh
claude --plugin-dir /path/to/agile-skills
```

Then run a skill by name, starting with setup:

```
/agile-skills:setup
```

All skills except `research` run only when you call them.
