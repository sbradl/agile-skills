# agile-skills

Skills for Claude Code that keep the decisions with you. You decide what gets built, in which order, how it is designed and when it is done. The agent estimates, points out risks and does the building.

## Why

Coding agents are eager. Give one a vague request and it will invent the missing requirements, choose a design and carry on with whatever it thinks comes next. What comes out looks finished, but much of it was never decided by anyone.

With these skills the agent asks instead of assuming. It asks one question at a time and keeps its own answer to itself. Advice comes only on request, as options with their pros and cons. Choosing is your job.

The agent still has plenty to do. It reads everything, researches with sources, notices when a document contradicts an issue, sketches UI variants for you to choose from, and writes code test-first without cutting corners.

Two habits run through all the skills. The project has one vocabulary, kept in a glossary per bounded context, and the agent uses it everywhere, in code too. And work moves in small steps, so you see each one before the next starts.

The rules are written down in the [working agreement](WORKING-AGREEMENT.md). Every skill reads it before doing anything else.

## The skills

- **`setup`**: Notes how the project works: issue tracker, commits, branching.
  - When: At the start of a project, and again when the way of working changes.
  - Why: Every other skill needs to know the tracker and the commit rules. Written down once, the agent neither guesses nor asks again in every session.
  - Writes: `docs/setup.md`
- **`vision`**: Captures the product vision, or revises it.
  - When: At the start, and again when the direction changes.
  - Why: Without a written vision nothing says what belongs in the product and what does not. It is the yardstick the backlog is measured against, so it stays short and holds only the big picture.
  - Writes: `docs/vision.md`
- **`ddd`**: Leads a group session to find the shared language.
  - When: With the whole group in one room, to talk through how a part of the business works.
  - Why: Two words for one thing, or one word for two things, end up as misunderstandings and confusing code. A session settles the terms with the people who know the business, and the agent then uses them everywhere. It also helps to carry the concepts over into code: for each central one the session notes which building block it could become, such as an entity, a value object or an aggregate, and `build` picks these ideas up.
  - Writes: `docs/contexts/`
- **`issues`**: Works on the issues in the tracker. It has three operations:
  - Create: turns notes into issues, one per feature or topic. For getting ideas out of notes and documents and into the tracker.
  - Refine: an interview until every acceptance criterion can be checked. For an issue that is not yet clear enough to build.
  - Split: comes in two kinds. Splitting into feature issues shrinks a feature that is too big: parts move out into issues of their own. Splitting into subtasks keeps the feature as it is and breaks it into pieces that can be built one after the other.
  - When: Before building: when there are new notes, when acceptance criteria are unclear, when an issue is too big.
  - Why: An issue is the one place where a requirement lives, with acceptance criteria that tell done from not done. An agent left with unclear criteria fills the gap by inventing, so such an issue stays blocked until it is refined.
  - Writes: the tracker
- **`backlog-review`**: Compares the top of the backlog with the vision. Changes nothing.
  - When: Now and then, to see whether the backlog still fits the vision.
  - Why: Backlogs drift: off-topic features and upkeep crowd out what the vision asks for. The review shows the drift and leaves the decision to you.
  - Writes: nothing
- **`build`**: Builds an issue test-first. Starts with a short design session that you lead.
  - When: An issue is ready to be built.
  - Why: The design and the choice of what to test are yours, so nothing is built on a design nobody decided. Going one test at a time keeps the agent from writing more than was asked for.
  - Writes: code
- **`commit`**: Conventional commits, one per logical change, plus a changelog for end users.
  - When: The work is done. You review and push.
  - Why: One commit per logical change keeps the history readable and easy to review. The changelog is written while the change is fresh, in words an end user understands.
  - Writes: git, `CHANGELOG.json`
- **`research`**: Looks into a question and writes a note with sources.
  - When: Any time a question needs sources.
  - Why: An agent answering from memory may be wrong or out of date. A note built on first-hand sources can be checked and used again.
  - Writes: `docs/research/`
- **`help-me`**: For when it is unclear what to do next. Asks a few questions, then lists options with pros and cons.
  - When: Any time, also in the middle of another skill.
  - Why: Sometimes you are stuck. The questions come first, so the thinking stays with you and the options fit your answers.
  - Writes: nothing

The list follows the usual order of work. A skill is called by name, followed by what it should work on, for example `/issues refine #12`.

The paths are inside the project where the skill runs.

Still missing: code review (`build` ends with one but has nothing to call yet) and `retro`.

## Using them

Link the skills into the project:

```sh
mkdir -p .claude/skills
ln -s /path/to/agile-skills/WORKING-AGREEMENT.md .claude/
ln -s /path/to/agile-skills/skills/* .claude/skills/
```

The working agreement has to be linked as well, because the skills look for it two folders up.

After that, start with `/setup`. Apart from `research`, no skill starts on its own. They run when called.

The repo also has a plugin manifest, so `claude --plugin-dir /path/to/agile-skills` should work too. The skills are then called `/agile-skills:setup` and so on. That route is little tested.
