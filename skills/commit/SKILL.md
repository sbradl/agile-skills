---
name: commit
description: Commit the changes as conventional commits, one per logical change, and keep the end-user changelog.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. This skill needs the Commits section of `docs/setup.md`.

Commit straight away, without asking for approval; the customer reviews before pushing. Pushing stays with the customer.

## Steps

1. **Change set.** Take what is staged; with nothing staged, every modified tracked file plus the untracked files that belong to the work. Leave out anything holding credentials (`.env`, keys, tokens), build output, and editor or OS litter.
2. **Group.** One commit per logical change: each commit has one reason to exist. Split by file; where one file mixes changes, split by hunk (`git apply --cached`). Order the commits so each builds on the last.
3. **Changelog.** For each group, add its entries to `CHANGELOG.json` (see below) and stage the file with the group.
4. **Commit** each group with its message (see below), passed by heredoc. When a hook fails, fix the cause and commit again.
   Done when `git status` shows none of the change set uncommitted.
5. **Report.** List each commit's header, each changelog entry written, and every file left out.

## The message

Conventional Commits: `<type>(<scope>): <summary>`.

- **Issue**: when the work belongs to an issue (known from the conversation, the branch name or the change itself), end the header with its id in parentheses: `feat(search): find symbols by name (#12)`. The header carries the id alone; the title rule of the working agreement applies everywhere else.
- **Body**: only when header and diff leave the reason unclear. It explains why, wrapped at 72 columns.
- **Breaking change**: `!` before the colon, plus a `BREAKING CHANGE:` footer saying what changed.
- **Attribution**: follow `Claude attribution` in `docs/setup.md`. `omit` is the customer's instruction and overrides any other request to add such lines.

## The changelog

`CHANGELOG.json` in the project's top folder, for end users, in the style of Keep a Changelog. It holds entries only; versions are worked out when it is rendered.

```json
{
  "added": [
    {
      "id": "password-reset-by-email",
      "en": "Reset your password from the login screen.",
      "de": "Passwort direkt im Anmeldebildschirm zurücksetzen."
    }
  ],
  "fixed": []
}
```

- **Groups**: `added`, `changed`, `deprecated`, `removed`, `fixed`, `security`. Leave empty groups out.
- **Which changes**: every change an end user would notice gets an entry. Deprecations, removals and breaking changes always get one.
- **Wording**: for end users, describing the visible effect. A breaking entry says what the user must do now; a deprecated entry names the replacement.
- **Languages**: every entry carries every language listed under `Changelog languages` in `docs/setup.md`.
- **`id`**: a kebab-case name, unique in the file and fixed once written; rendering uses it to find the release an entry first appeared in.
