---
name: vision
description: Capture or revise the product vision in docs/vision.md.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. This skill needs `docs/setup.md`: check for it before the first step.

## The document

`docs/vision.md`, always in this shape:

```markdown
# <Product name>

<One-sentence summary of the whole vision.>

## Why it exists
## Who it's for
## What it does
## What sets it apart
## What it won't be
## Appendix
```

- "Why it exists" carries the most weight.
- "What it does" stays at **elevator pitch** altitude: the few core capabilities of the product as it should exist, in one short paragraph or a handful of bullets. Feature details and anything meant for later become issues (step 6).
- The vision stands alone: it holds the big picture and never refers to issues.
- The appendix is optional: findings about similar products and what this one should do better, each with its source.
- Reading time: a few minutes. The reader knows the problem domain, so skip the basics.
- Phrase it yourself for clarity and good formatting; every piece of content comes from the user.

## Steps

1. **Existing vision.** If `docs/vision.md` exists, read it and ask what changed. Steps 2–6 then cover only the changed parts; the rest of the document stays as it is.
2. **The user talks first.** Take the idea from the invocation, or ask the user to describe it freely. Listen until they finish.
3. **Interview.** Ask about gaps (sections the user left uncovered) and challenge weak spots (an unconvincing "why", answers that contradict each other). Every question serves one section of the document.
   Done when every section is covered and you find no weak spot left, or when the user ends it.
4. **Similar products.** The user may bring this information at any point. You may offer research: suggest a topic, let the user sharpen it, then follow [`../research/SKILL.md`](../research/SKILL.md) on up to five products unless the user asks for more. Discuss the findings; the user decides what enters the appendix.
5. **Approval.** Show the full draft and apply the user's edits. Save to `docs/vision.md` once the user approves.
6. **Issues.** Collect what the user said that was too detailed for the vision as raw notes per feature, and ask whether to turn them into issues. On a yes, follow [`../issues/SKILL.md`](../issues/SKILL.md) in Create mode with those notes.
