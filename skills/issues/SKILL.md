---
name: issues
description: Create issues from notes, refine existing issues, or split an issue in the project's tracker.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. Reach the tracker through the access recorded in `docs/setup.md`.

## The issue

Every issue this skill writes has this shape:

- **Title**: the goal, what should be achieved rather than how. Feature titles use product words; non-feature titles may use technical terms.
- **Description**: short.
- **Acceptance criteria**: a checklist; each item lets the user tell done from not done.

An issue whose acceptance criteria are missing or unclear is blocked: label it `needs refinement`, using the tracker's existing label for that where one exists.

**Single source**: the issue is the source of truth for its requirements. In every mode, search the project documents and the other issues for duplicate knowledge: text that restates this issue's requirements. Replace each duplicate with a reference to the issue by id and name. `docs/vision.md` is exempt: leave it exactly as it is.

**Approval**: one issue per message, one approval per issue. Show the user the full text of a single issue you are about to create or change, and list beneath it the duplicate replacements and any document deletion that come with it. Their approval covers all of it: write the issue, apply the listed changes, then move to the next issue.

## Modes

Take the mode from the invocation or from the skill that sent you here.

### Create

Turn the notes you were given into issues, one per feature or topic. Fill the shape from the notes alone; where the notes hold no acceptance criteria, leave them empty and the issue blocked.

When the notes came from a document describing the feature, delete that document once the issue exists.

### Refine

Read the issue, then interview the user until the acceptance criteria are clear.
Done when every criterion is checkable; then remove `needs refinement`.

### Split

There are two kinds of split; take the kind from the user's words.

In both kinds, every issue that comes out still has an end user's need behind it, and its description says which. Where a part is so technical that you cannot name the need it serves, object once with the reason; the user decides.

**Into feature issues**, to shrink a feature. The user names the issue and the parts to move out. If a part cannot be built or accepted on its own, object once with the reason; the user decides. The original issue stays, shortened to what remains; each moved part becomes a new issue that links back to the original.

**Into subtasks**, to build an issue piece by piece. The feature keeps its size, so the original issue stays as it is. The user names the subtasks, which may be more technical than a feature issue. Where they have not named them, ask what the subtasks are and propose none of your own. Each subtask becomes a sub-issue of the original, using the tracker's own sub-issues; where the tracker has none, a new issue that links back to the original.
