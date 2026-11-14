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
- **Acceptance criteria**: a checklist; each item lets the customer tell done from not done.

An issue whose acceptance criteria are missing or unclear is blocked: label it `needs refinement`, using the tracker's existing label for that where one exists.

**Single source**: the issue is the source of truth for its requirements. In every mode, search the project documents and the other issues for duplicate knowledge: text that restates this issue's requirements. Replace each duplicate with a reference to the issue by id and name; show these edits and apply them once the customer confirms.

**Approval**: show the customer the full text of every issue you are about to create or change, and write to the tracker once they approve.

## Modes

Take the mode from the invocation or from the skill that sent you here.

### Create

Turn the notes you were given into issues, one per feature or topic. Fill the shape from the notes alone; where the notes hold no acceptance criteria, leave them empty and the issue blocked.

When the notes came from a document describing the feature, delete that document once the issue exists and the customer confirms.

### Refine

Read the issue, then interview the customer until the acceptance criteria are clear.
Done when every criterion is checkable; then remove `needs refinement`.

### Split

The customer names the issue and the parts to move out. If a part cannot be built or accepted on its own, object once with the reason; the customer decides. The original issue stays, shortened to what remains; each moved part becomes a new issue that links back to the original.
