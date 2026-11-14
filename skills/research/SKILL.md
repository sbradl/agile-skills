---
name: research
description: Research a question into a sourced note in docs/research/. Use only when the customer runs it or has accepted a skill's research offer.
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run.

## Steps

1. **Existing note.** Look in `docs/research/` for a note on this topic. If one exists, read it; this run updates that file with what is new or missing.
2. **Brief.** Show the customer a brief of a few lines and wait for their corrections or approval:
   - **Question**: as you understood it.
   - **Sources**: first-hand only, unless the customer has allowed more.
   - **Size**: how much will be looked into (for example, up to five products).
3. **Dispatch.** Once the brief is approved, start a background agent with a fresh context. Hand it the approved brief plus the full text of "Rules for the researcher" and "The note" below.
4. **Report.** When it returns, show the customer the note's abstract, its recommended reading and the file path, then leave the discussion to them. If it reports that first-hand sources fell short, ask the customer whether to widen the sources, and dispatch again only on a yes.

## Rules for the researcher

- **First-hand sources**: the material of whoever owns the fact (official site, docs, source code, specs). Follow every claim back to its owner.
- Where the brief allows other sources (reviews, forums, comparisons), label each finding from them as second-hand.
- When first-hand sources cannot answer the question, stop and report that; the brief's source limit holds.
- When sources conflict, report each side with its source, side by side.
- Stop at the brief's size. List what remains unexamined under Limitations.
- Facts only: report what the sources say. Interpretation belongs to the customer's conversation.
- **Recommended reading**: pick up to three sources you opened that give a human a good overview of the topic, each readable in about 15 minutes (a short article rather than a book). These are an introduction, not evidence, so an overview by someone other than the fact's owner qualifies here.

## The note

One file per topic: `docs/research/<topic>.md`, structured as a research paper. Written for an agent to consult and a human to read.

```markdown
# <Title>

## Abstract
<The short answer.>

## Question
<What was asked and why.>

## Method
<Sources used, first-hand or second-hand, and the size examined.>

## Findings
<Each finding with its source.>

## Limitations
<What could not be found out; what remains unexamined.>

## Recommended reading
<Up to three short overviews, each with a link and one line on what it gives the reader.>

## References
<The source list.>
```
