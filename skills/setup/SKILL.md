---
name: setup
description: Record how this project works (issue tracker for now) in docs/setup.md for the other skills.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run.

## The config

`docs/setup.md` is the single place other skills look up how this project works. One section per topic:

```markdown
# Project setup

## Issue tracker
- Tracker: <which one>
- Location: <URL or project key>
- Access: <the tool or command that reads and writes issues>
- Order: <where the customer's ordering of issues lives>
```

**Order**: trackers with built-in ranking (Jira) carry the order themselves; on GitHub it lives in a GitHub Project, so ask which one, and help create it when there is none.

Credentials stay with the customer's tools; the config names the tool, never a secret.

## Steps

1. **Existing config.** If `docs/setup.md` exists, read it; this run changes only what is missing or what the customer wants changed.
2. **Detect.** Gather what the project and its tools already reveal: git remotes, `gh`, tracker links and issue templates in the repo, connected tracker tools.
3. **Confirm and ask.** Show what you found for confirmation, then ask for whatever is still unknown.
4. **No tracker yet.** Ask which tracker the customer wants and help set it up. Confirm with the customer before creating anything outside the project folder.
5. **Verify.** Read the issue list through the recorded access.
   Done when that read succeeds.
6. **Save.** Show the config and save it to `docs/setup.md` once the customer approves.
