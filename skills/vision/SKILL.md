---
name: vision
description: Capture or revise the product vision in docs/vision.md.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run.

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
- "What it does" stays at **elevator pitch** altitude: the few core capabilities of the product as it should exist, in one short paragraph or a handful of bullets. Feature details and anything meant for later go to **feature notes**.
- The appendix is optional: findings about similar products and what this one should do better, each with its source.
- Reading time: a few minutes. The reader knows the problem domain, so skip the basics.
- Phrase it yourself for clarity and good formatting; every piece of content comes from the customer.

## Feature notes

Detail too fine for the vision is kept in `docs/features/<feature>.md`, one file per feature. A feature note is **raw notes**: only what the customer said about that feature, unrefined; later skills refine it. When the file exists, append to it.

## Steps

1. **Existing vision.** If `docs/vision.md` exists, read it and ask what changed. Steps 2–5 then cover only the changed parts; the rest of the document stays as it is.
2. **Customer talks first.** Take the idea from the invocation, or ask the customer to describe it freely. Listen until they finish.
3. **Interview.** Ask about gaps (sections the customer left uncovered) and challenge weak spots (an unconvincing "why", answers that contradict each other). Every question serves one section of the document.
   Done when every section is covered and you find no weak spot left, or when the customer ends it.
4. **Similar products.** The customer may bring this information at any point. You may offer research: suggest a topic, let the customer sharpen it, then follow [`../research/SKILL.md`](../research/SKILL.md) on up to five products unless the customer asks for more. Discuss the findings; the customer decides what enters the appendix.
5. **Approval.** Show the full draft and the feature notes, and apply the customer's edits. Save the vision and the feature notes once the customer approves.
