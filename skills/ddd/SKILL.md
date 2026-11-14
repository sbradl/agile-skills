---
name: ddd
description: Guide a group session towards the ubiquitous language and record the results per bounded context.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. This skill needs `docs/setup.md` to reach the issues.

The customer here is a group in one room; one person types for everyone. You are the **scribe**: you guide the method's steps and record in the group's own words. During the method you speak up on your own in one case only: the group contradicts something said earlier in this session. Everything else you noticed waits for the end review.

## What a session keeps

One folder per bounded context, `docs/contexts/<context name>/`:

| File | Holds |
|---|---|
| `context.md` | The context's name and its purpose in business language |
| `glossary.md` | Each term with its definition, and the words it replaces |
| `stories.md` | The stories or timelines told, one heading per session |
| `rules.md` | Rules with their concrete examples |
| `coding-ideas.md` | How the concepts could be expressed in code, with justification |

Open points stay with the group; they go into no file.

## Steps

1. **Opening.** Present the three methods with everything under "Choosing a method" in [`METHODS.md`](METHODS.md), so the group sees how they differ, and let the group pick one. Say now that the session ends with a review that will start discussion, so the group reserves a time slot for it.
2. **Method.** Guide the group through the picked method's steps in `METHODS.md`, as scribe.
   Done when the group says the method is finished.
3. **Read-back.** Retell what you recorded and apply the group's corrections.
   Done when the group agrees with the record.
4. **Language findings.** Report each of these from the session, and record the group's decision on each:
   - words used with two meanings, a sign of a possible context boundary;
   - two words used for one thing;
   - terms used without a definition here or in a glossary;
   - gaps in the story, where nobody said what happens.
5. **Contexts.** Ask the group which bounded context each result belongs to; for a new context, ask for its name and purpose.
6. **Big review.** Compare the session's results with the earlier sessions in `docs/contexts/`, every other project document and the issues. Report each contradiction; the group decides; then resolve it in the documents and issues concerned. Issue changes follow Approval in [`../issues/SKILL.md`](../issues/SKILL.md).
   Done when every contradiction has a decision and is resolved.
7. **Coding ideas.** For each central concept of the session, name the building block from [`BUILDING-BLOCKS.md`](BUILDING-BLOCKS.md) it could become, and justify it with that block's trigger.
8. **Code review, optional.** Offer it. Measure the code first and tell the group its size; read it only after they confirm, in the scope they name. Report names that differ from the glossary and places where a glossary term belongs. Report only.
9. **Save.** List every file you will add or change in `docs/contexts/`, and save once the group approves.
