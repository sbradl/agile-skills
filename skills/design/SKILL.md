---
name: design
description: Find the design for an issue: the user brings a rough idea, questions expose its holes, and a review closes the session.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. This skill needs `docs/setup.md` to reach the issue.

The **design is the user's**. Your part is questions and, at the end, a review. Offer a solution only when the user explicitly asks for one; then give the working agreement's options table.

## Steps

1. **Ground.** Read the issue the user named, the code it touches, and the glossary and `coding-ideas.md` of every bounded context it belongs to. Tell the user in a line or two how much code is there.
2. **Idea.** Ask the user for their rough idea and listen until they finish.
3. **Questions.** Ask about each hole and each possible improvement you see, the one that matters most first. A question points at the spot and leaves the answer open. Holes are:
   - a part of the issue or an acceptance criterion that nothing in the design serves;
   - a part without a place, a name or its interactions;
   - a contradiction within the design, or with the issue, a glossary or the existing code;
   - a case nobody has said what happens in.

   Done when you see no hole left, or when the user ends it.
4. **Read-back.** Retell the design as it now stands and apply the user's corrections.
   Done when the user agrees with it.
5. **Review** the design against "What the review looks for". The user decides on each finding.
   Done when every finding has a decision.
6. **Hand over.** Retell the final design. When `build` sent you here, return to its Design step with this design.

## What the review looks for

Each finding names the place in the design, the rule it touches and what it costs to leave it.

- **Simplicity.** The design holds what this issue needs and nothing for later. Report every part, layer or abstraction that nothing in the issue calls for.
- **SOLID.** A part with more than one reason to change; a change that would force edits to working code where an extension could do; a subtype that breaks what its base promises; an interface that forces its users to depend on methods they do not use; a high-level rule that depends on a detail.
- **Clean Architecture.** Dependencies point inwards, towards the business rules. Business rules know nothing of UI, database or framework; where they need one, the interface belongs to the inner side.
- **Design patterns.** Where a pattern would remove a problem the design has today, name the pattern and the problem. A pattern that answers no present problem is a finding against simplicity.

How much weight simplicity gets depends on the code that exists. With little or no code, simplicity wins where it conflicts with another rule: report the conflict and say so. With mature code, the existing structure sets the standard.
