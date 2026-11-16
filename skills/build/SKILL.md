---
name: build
description: Build an issue test-driven, starting with a short design session that the user leads.
disable-model-invocation: true
---

Read [`../../WORKING-AGREEMENT.md`](../../WORKING-AGREEMENT.md) first; it governs this run. This skill needs `docs/setup.md` to reach the issue.

Every build starts with a design session, however small the issue, and all production code is written test-driven. The **design is the user's**, and so is the decision **what to test**: they propose, you build.

## Your part in the design

- **Notes.** Speak up on your own for an obvious problem only: the design cannot work as stated, or it contradicts itself, the issue or a glossary. One note per problem; the user decides.
- **Check on request.** A review of the design waits until the user asks for one.
- **Enough detail.** You judge whether the design is detailed enough to build from, measured against the code that exists:
  - *Little or no code*: the user's words carry everything. Expect which projects to create, the parts in each, how the parts interact, down to methods or further where the user wants.
  - *Mature code*: the code leads by example. The design needs only what the existing examples leave open.

  The design is enough when, for every part the issue needs, you can point to its place, its name and its interactions either in the user's words or in existing code that sets the example. Ask for each part that fails this.

## Steps

1. **Issue.** Read the issue the user named. When it is labelled `needs refinement`, tell the user to refine it with `issues`, then stop.
2. **Code.** Read the code the issue touches. Tell the user in a line or two how much is there and which existing examples you would follow.
3. **Coding ideas.** Coding ideas live with the bounded context: `docs/contexts/<context name>/coding-ideas.md`. Restate those of every context this issue belongs to, each with its justification. With none, say so.
4. **Prototype**, only when the issue brings new UI. Ask the user for the variants they want to see, and recommend three of your own, a line each. Build the variants the user confirms as a throwaway prototype and show them side by side. The user picks the prototype's form: throwaway code in the app itself, or a small web page that looks like the existing app.
   As soon as the user has picked a variant, add a note to the issue: that a prototype decided this, and exactly what was decided, in enough detail to build the variant without the prototype. The note follows Approval in [`../issues/SKILL.md`](../issues/SKILL.md). Then delete all prototype code, in either form.
   Done when the note is on the issue and the prototype is gone; the design starts from the picked variant.
5. **Design.** Ask the user for their high-level design.
   Done when the design is enough.
6. **Scaffold.** Create the classes the design names, down to the methods it names, with empty methods: the minimum that compiles, no logic. A method that must return something returns a degenerate value such as `null`. This is the only production code written without a test.
   Done when it compiles.
7. **Test plan.** Ask the user where and what to test. They decide above method level; the plan covers at least every acceptance criterion of the issue, and they may add more. They may also leave the low-level tests to you: then you choose those yourself, and each one runs through the same loop as a planned test.
8. **Plan check.** Report holes, duplicates and general problems of the plan; the user decides on each.
   Done when every acceptance criterion has a test and every finding has a decision.
9. **TDD loop.** Take the tests one at a time, the simplest first and expanding from there: as the tests get more specific, the code gets more generic. Each test gets its own red and green subagent as described under "The TDD loop", except on the user's turn.
   Done when every planned test and every test you chose exists and the whole suite is green.
10. **Code review** of everything the issue changed. All cleanup waits for this step: until here, code stays exactly as the green subagents left it.

Where the design or the plan turns out not to fit the code, stop and bring it back to the user.

## The TDD loop

Brief each subagent with the design, the one test from the plan and the files concerned; it reports back the output of its test run.

- **Red subagent.** Writes the test and a dummy implementation: an empty method where nothing is returned, a degenerate return value such as `null` otherwise. That is just enough for the test to compile and run to its assert. Then runs the test.
  Done when the test fails for the **right reason**: the assert the test itself wrote. A compile error or an exception from unfinished code (`NotImplemented` and the like) is the wrong reason; keep working on the dummy until the assert is what fails. A test that passes at once comes back to the user.
- **Green subagent.** A fresh one. Writes the minimal production code that satisfies the test, choosing the simplest transformation by Uncle Bob's Transformation Priority Premise. Then runs the tests.
  Done when the whole suite is green.
- **The user's turn.** Every nth cycle the user writes one half themselves, so they stay in the code. Take n from the invocation, otherwise from `User's turn` in `docs/setup.md`; when neither gives it, ask before the loop starts. `never` switches the turns off.
  On such a cycle, name the test that is up and ask the user which half they write: the test or the implementation. A subagent does the other half as usual. Wait until the user says they are done, then run the tests yourself and hold their half to the same Done rule. When it misses the rule, show the output and leave the fix to them. Their code stays as they wrote it.
