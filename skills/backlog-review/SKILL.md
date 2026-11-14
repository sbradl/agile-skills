---
name: backlog-review
description: Check the top of the backlog against the product vision and report whether the project is on track.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. This skill needs `docs/setup.md` with its Order entry, and `docs/vision.md`; when the vision is missing, tell the customer to run `vision`, then stop.

This is a **read-only** review: it reports in the conversation and leaves the tracker and every file as they are. What to do about a finding is the customer's decision.

## Steps

1. Read the vision, then fetch the top 20 open issues in the customer's order, through the access and Order recorded in `docs/setup.md`.
2. Sort every one of those issues into exactly one group:
   - **Towards the vision**: serves a named section of the vision.
   - **Upkeep**: bugs and technical tasks.
   - **Off-vision**: a feature that serves no section.
   - **Excluded**: falls inside "What it won't be".
3. Report in the shape below, then stop.

## The report

Start with the **verdict**: one line, "on track" or "drifting", with the main reason. Then these sections, leaving out any with nothing to report:

- **Excluded**: issues inside "What it won't be".
- **Off-vision**: issues serving no section of the vision.
- **Uncovered**: sections of the vision that none of the top 20 works towards.
- **Order**: places where the ranking works against progress towards the vision, such as vision-serving issues ranked below off-vision ones.
- **Balance**: a warning, with the counts, when upkeep issues outnumber those towards the vision.
- **Unrefined**: issues labelled `needs refinement` or lacking acceptance criteria.

Name each issue by id and title, with a one-line reason that cites the vision section it concerns.
