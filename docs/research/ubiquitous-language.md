# How a Ubiquitous Language Is Established and Enforced in Domain-Driven Design

## Abstract

In the originators' own material, a ubiquitous language is not established by writing a glossary and not enforced by a gatekeeper. Evans prescribes that the domain model is the backbone of the language, that the team commits to using that one language "relentlessly" in speech, writing, diagrams and code within one explicitly bounded context, and that it is refined by talking: describing scenarios out loud, experimenting with alternative expressions, and resolving confusion over terms in conversation. Enforcement is by coupling rather than policing: a change in the language is a change to the model, which is followed by renaming classes, methods and modules; names in code must conform to the language; continuous integration and constant use keep the model from fragmenting. Domain experts object to awkward terms, developers watch for ambiguity. The language is valid only inside its bounded context; between contexts, explicit translation is defined. Fowler restates Evans and adds that conversation with domain experts is a test of the model. First-hand coverage was complete only for Evans' DDD Reference and Fowler's article; Evans' book, Vernon's chapter on developing the language, and Brandolini's book could not be opened, so first-hand sources fell short on those three.

## Question

How is a ubiquitous language typically established and enforced in Domain-Driven Design practice?

Why: a set of agent skills is being designed that should keep a project's ubiquitous language consistent across conversations, documents, issues and code; the aim is to know what the originators of the practice actually prescribe.

## Method

First-hand sources only, as the brief requires. Four authors were examined (brief limit: five). Research date: 2026-11-14.

| Source | Status | What was actually read |
|---|---|---|
| Eric Evans, *Domain-Driven Design Reference* (2015 PDF, domainlanguage.com, CC BY 4.0) | Opened, full text extracted | Definitions page; Part I (Bounded Context, Ubiquitous Language, Continuous Integration, Model-Driven Design, Hands-on Modelers); every other mention of "ubiquitous language" in the document |
| Eric Evans, *Domain-Driven Design* (book, 2003) | **Not opened** (not freely available) | Nothing. Only the two sentences Fowler quotes from it |
| Martin Fowler, "UbiquitousLanguage" bliki (2006-10-31) | Opened, read through a summarising fetch tool | Short quoted passages; the full article text was not returned verbatim by the tool |
| Vaughn Vernon, *Domain-Driven Design Distilled* (2016) | **Partly opened**: publisher's 16-page sample PDF only | Table of contents, preface, Chapter 1, index. Chapter 2 ("Developing a Ubiquitous Language") **not opened** (O'Reilly returned 403) |
| Vaughn Vernon, *Implementing Domain-Driven Design* | **Not opened** | Nothing |
| Alberto Brandolini, "Introducing Event Storming" blog post (2013-11-18) | Opened, via summarising fetch tool | Short quoted passages |
| Alberto Brandolini, eventstorming.com home page and Leanpub page of *Introducing EventStorming* | Opened | Home page text; book description and table of contents. Book body **not opened** (sample link returned 404) |

No claim below rests on recall. Where a source could not be opened, the gap is stated instead of filled.

## Findings

### 1. Definition and scope (Evans, DDD Reference)

- Definition: "A language structured around the domain model and used by all team members within a bounded context to connect all the activities of the team with the software." (Definitions, p. vi)
- DDD itself is summarised in three points, the third being: "Speak a ubiquitous language within an explicitly bounded context." (Part I intro, p. 1)
- Context: "The setting in which a word or statement appears that determines its meaning." Bounded context: "A description of a boundary (typically a subsystem, or the work of a particular team) within which a particular model is defined and applicable." (Definitions, p. vi)

### 2. The problem the language addresses (Evans, DDD Reference, "Ubiquitous Language", p. 3)

- "Domain experts use their jargon while technical team members have their own language tuned for discussing the domain in terms of design."
- "The terminology of day-to-day discussions is disconnected from the terminology embedded in the code (ultimately the most important product of a software project)."
- "even the same person uses different language in speech and in writing, so that the most incisive expressions of the domain often emerge in a transient form that is never captured in the code or even in writing."
- "Translation blunts communication and makes knowledge crunching anemic."
- "none of these dialects can be a common language because none serves all needs."

### 3. How the language is established (Evans, DDD Reference, "Ubiquitous Language", pp. 3-4)

- "Use the model as the backbone of a language."
- "Play with the model as you talk about the system. Describe scenarios out loud using the elements and interactions of the model, combining concepts in ways allowed by the model. Find easier ways to say what you need to say, and then take those new ideas back down to the diagrams and code."
- "Iron out difficulties by experimenting with alternative expressions, which reflect alternative models."
- "Resolve confusion over terms in conversation, in just the way we come to agree on the meaning of ordinary words."
- Roles: "Domain experts should object to terms or structures that are awkward or inadequate to convey domain understanding; developers should watch for ambiguity or inconsistency that will trip up design."
- The pattern text calls for "a lively experimentation with language that seldom happens on software projects."

### 4. How the language is enforced (Evans, DDD Reference)

- Commitment to pervasive use: "Commit the team to exercising that language relentlessly in all communication within the team and in the code. Within a bounded context, use the same language in diagrams, writing, and especially speech." ("Ubiquitous Language", p. 4)
- Language and model are one thing: "Recognize that a change in the language is a change to the model." (p. 4)
- Code follows the language: "Then refactor the code, renaming classes, methods, and modules to conform to the new model." (p. 4)
- Code terminology comes from the model: "Draw from the model the terminology used in the design and the basic assignment of responsibilities. The code becomes an expression of the model, so a change to the code may be a change to the model. Its effect must ripple through the rest of the project's activities accordingly." ("Model-Driven Design", p. 6)
- One model for all purposes: "Demand a single model that serves both purposes well, in addition to supporting a fluent ubiquitous language." ("Model-Driven Design", p. 6)
- Consistency inside the boundary: "Apply Continuous Integration to keep model concepts and terms strictly consistent within these bounds, but don't be distracted or confused by issues outside." ("Bounded Context", p. 2)
- Against fragmentation: "Institute a process of merging all code and other implementation artifacts frequently, with automated tests to flag fragmentation quickly. Relentlessly exercise the ubiquitous language to hammer out a shared view of the model as the concepts evolve in different people's heads." ("Continuous Integration", p. 5)
- Everyone who touches code is in the conversation: "Every developer must be involved in some level of discussion about the model and have contact with domain experts. Those who contribute in different ways must consciously engage those who touch the code in a dynamic exchange of model ideas through the ubiquitous language." ("Hands-on Modelers", p. 7). Also: "If developers don't realize that changing code changes the model, then their refactoring will weaken the model rather than strengthen it."

### 5. Names in code are part of the language (Evans, DDD Reference)

- Services: state the service contract's assertions "in the ubiquitous language of a specific bounded context. Give the service a name, which also becomes part of the ubiquitous language." ("Services")
- Modules: "Give the modules names that become part of the ubiquitous language." ("Modules")
- Classes and operations: "These names should conform to the ubiquitous language so that team members can quickly infer their meaning." ("Intention-Revealing Interfaces")
- Bounded contexts themselves: "Name each bounded context, and make the names part of the ubiquitous language." ("Context Map")
- System metaphor, when adopted: "absorb it into the ubiquitous language." ("System Metaphor")

### 6. The language stops at the context boundary (Evans, DDD Reference)

- "Model expressions, like any other phrase, only have meaning in context." Therefore: "Explicitly define the context within which a model applies. Explicitly set boundaries in terms of team organization, usage within specific parts of the application, and physical manifestations such as code bases and database schemas." ("Bounded Context", p. 2)
- Between contexts: "Describe the points of contact between the models, outlining explicit translation..." ("Context Map")
- Two contexts share a language only by explicit arrangement: a Shared Kernel uses "a continuous integration process that will keep the kernel model tight and align the ubiquitous language of the teams"; a Conformist team "will share a ubiquitous language with your upstream team." ("Shared Kernel", "Conformist")
- For exchange between contexts: "Use a well-documented shared language that can express the necessary domain information..." ("Published Language"; only this fragment was read.)

### 7. What the DDD Reference does not say

- The word "glossary" does not occur anywhere in the DDD Reference (text search of the full PDF).
- No role of language owner or approver is named in the sections read; the stated mechanism for settling terms is conversation (Finding 3).

### 8. Fowler's restatement (Fowler, "UbiquitousLanguage", 2006)

- Attributes the term to Evans' *Domain-Driven Design*: a common, rigorous language between developers and users.
- "This language should be based on the Domain Model used in the software."
- Rigor is needed "since software doesn't cope well with ambiguity."
- "using the ubiquitous language in conversations with domain experts is an important part of testing it" (the model).
- "the language (and model) should evolve as the team's understanding of the domain grows."
- Quotes Evans' book: "By using the model-based language pervasively and not being satisfied until it flows..." and "Domain experts should object to terms or structures that are awkward or inadequate to convey domain understanding..." (the continuations of both quotes were not returned by the fetch tool).

### 9. Vernon (*DDD Distilled*, sample pages only)

- Chapter 1: "you will see how to develop a Ubiquitous Language as your domain model within an explicitly Bounded Context."
- Chapter 1: developers and Domain Experts develop it together; "The language you develop together through collaboration will become ubiquitous, pervasive, throughout the team's spoken communication and software model."
- Chapter 1: learning is "a matter of discovery through group conversation and experimentation."
- Table of contents and index show that Chapter 2 has a section "Developing a Ubiquitous Language" with subsection "Putting Scenarios to Work", and index entries "developing Ubiquitous Language as scenarios, 35-41", "Nouns, in Ubiquitous Language, 34-36", "Who? in Ubiquitous Language development, 36-38", "challenging/unifying mental models to create, 29-34", "maintenance phase of, 40-41", "Ubiquitous Languages: integrating different, 53", "translating with Published Languages, 58", "naming Domain Event types, 101-102", "Event Storming advantages, 113". **The content of those pages was not opened**; only the headings and index entries are reported.

### 10. Brandolini (EventStorming, own writing)

- The pages opened do not use the phrase "ubiquitous language".
- "Introducing Event Storming" (2013): the workshop aims to "bring people with the questions and people who know the answer in the same room"; under "Exploring Bounded Contexts" it says to "spot different interpretations of terms, as a trigger for discussion around the meaning" and to "draw the boundaries between the multiple consistent models that will coexist in your domain." The post carries a later disclaimer that EventStorming has evolved since 2013.
- eventstorming.com home page: workshop styles aim to "Support cross-discipline conversations between business, service designers and IT representatives" and "Enforce consistent storytelling between stakeholders and partners."
- Leanpub page of *Introducing EventStorming*: the description says conflicts are resolved "by leveraging bounded contexts"; the table of contents lists "Fuzziness vs. precision", a pattern "Fuzzy Definitions", an anti-pattern "Precise Notation", and a "Glossary" with subsection "Fuzzy by design". **The content of these chapters was not opened.**

### 11. Conflicts between sources

No direct contradiction was found in the text actually read. One tension is visible only at heading level and could not be verified: Fowler (after Evans) asks for a rigorous language because "software doesn't cope well with ambiguity", while Brandolini's table of contents lists "Fuzzy Definitions" as a pattern and "Precise Notation" as an anti-pattern for the workshop. What Brandolini means by these, and whether it concerns the language or only the workshop notation, was not read.

## Limitations

- **Evans' book not opened.** The DDD Reference is Evans' own summary of the book's patterns; the book's longer treatment (examples, discussion of documents and diagrams, any guidance on written glossaries) is unexamined.
- **Vernon largely unexamined.** Only preface, Chapter 1, contents and index of *DDD Distilled* were read. His concrete procedure (scenarios, nouns, "who", maintenance phase) is known here only by heading. *Implementing Domain-Driven Design* was not opened at all.
- **Brandolini largely unexamined.** The book body was not opened; what he says about language, definitions and glossaries is known only from a 2013 post and chapter titles.
- Fowler's article and Brandolini's post were read through a tool that returns summaries and short quotes, not the full verbatim text; quotes above are as the tool returned them.
- Only the "Ubiquitous Language"-related parts of the DDD Reference were read closely; the "Published Language" and "Context Map" patterns were read only in fragments.
- Not examined: Evans' talks and later writing, Vernon's website, Brandolini's later articles and talks, and any tooling or automation the originators may suggest for checking language consistency (none appeared in the text read, beyond "automated tests to flag fragmentation").
- A fifth author was not added; the brief's size was four named authors within a limit of five.

## References

1. Eric Evans, *Domain-Driven Design Reference: Definitions and Pattern Summaries*, Domain Language, Inc., 2015. https://www.domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf (first-hand, opened)
2. Martin Fowler, "UbiquitousLanguage", 31 October 2006. https://martinfowler.com/bliki/UbiquitousLanguage.html (first-hand, opened via summarising tool)
3. Vaughn Vernon, *Domain-Driven Design Distilled*, Addison-Wesley, 2016, publisher sample pages. https://ptgmedia.pearsoncmg.com/images/9780134434421/samplepages/9780134434421.pdf (first-hand, sample only)
4. Alberto Brandolini, "Introducing Event Storming", 18 November 2013. https://ziobrando.blogspot.com/2013/11/introducing-event-storming.html (first-hand, opened via summarising tool)
5. Alberto Brandolini, EventStorming site. https://www.eventstorming.com/ (first-hand, home page opened)
6. Alberto Brandolini, *Introducing EventStorming*, Leanpub page (description and table of contents only). https://leanpub.com/introducing_eventstorming (first-hand, book body not opened)

Not opened: Eric Evans, *Domain-Driven Design: Tackling Complexity in the Heart of Software*, Addison-Wesley, 2003; Vaughn Vernon, *Implementing Domain-Driven Design*, Addison-Wesley, 2013; *DDD Distilled* Chapter 2 (https://www.oreilly.com/library/view/domain-driven-design-distilled/9780134434964/ch02.html, HTTP 403).
