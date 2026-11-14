# Practices for Discovering and Settling a Ubiquitous Language

## Abstract

In the practitioners' own material, terms and bounded contexts are discovered by having domain experts tell concrete stories or scenarios while someone records them visibly, in the experts' own words: Domain Storytelling (one sentence at a time, "who does what with what with whom", then retelling for agreement), EventStorming (everyone writes domain events alone, then the group merges them on a timeline and argues about duplicates), and Example Mapping (rules illustrated by concrete examples for one story). Bounded contexts surface where language changes: the same word meaning different things to different groups (Fowler's "meter", Brandolini's "Account"), apparent duplicates that turn out to be "the same language for different concepts", and pivotal events or organisational boundaries in the story. Disagreement is settled in three ways the sources describe: (1) read the recorded story back and ask whether all domain experts agree; (2) when a term conflict is real, do not invent a compromise term or a translation of the expert's word but treat it as two contexts and draw the boundary; (3) when nobody present can answer, capture the open point visibly (EventStorming hotspot, Example Mapping red question card, Bounded Context Canvas "Open Questions" and "Assumptions") and move on, to be resolved by the missing person or by research. Naming a context and writing its purpose in business language is itself used as an agreement step. The allowed sources fell short on three points: Nick Tune's workshop recipe could not be opened, Brandolini's current EventStorming writing (books) was not opened, and no source read describes a decision rule for who has the final say on a term.

## Question

Which practices do teams commonly use to arrive at a ubiquitous language in Domain-Driven Design: how they discover terms and bounded contexts, and how they settle disagreement or ambiguity about terms?

Why: agent skills are being designed that interview a product owner while writing a product vision and while creating or refining issues. Those interviews are where terms and bounded contexts first surface.

Out of scope: how the language is recorded. What the originators prescribe is covered in `ubiquitous-language.md` and is not repeated here.

## Method

First-hand sources only: practitioners or communities describing their own practice or method. Eight sources opened (the brief's limit). Research date: 2026-11-14.

| # | Source | Status | What was read |
|---|---|---|---|
| 1 | ddd-crew, *DDD Starter Modelling Process* (GitHub README) | Opened, full raw text | Whole README |
| 2 | ddd-crew, *Bounded Context Canvas* (GitHub README) | Opened, full raw text | Whole README |
| 3 | ddd-crew, *EventStorming Glossary & Cheat Sheet* (GitHub README; contributors Kenny Baas-Schwegler, Chris Richardson) | Opened, full raw text | Whole README |
| 4 | Martin Fowler, "BoundedContext" bliki (2014-01-15) | Opened, full page text | Whole article |
| 5 | Matt Wynne, "Introducing Example Mapping", cucumber.io (2015-12-08) | Opened, full page text | Whole article |
| 6 | Stefan Hofer & Henning Schwentner, domainstorytelling.org "Quick-Start Guide" | Opened, full page text | Whole page |
| 7 | Alberto Brandolini, "Strategic Domain Driven Design with Context Mapping", InfoQ (2009-11-25) | Opened, full page text | Passages on language, ambiguity and drawing the map; integration-pattern sections skimmed only |
| 8 | Vlad Khononov, "Revisiting the Basics of Domain-Driven Design", vladikk.com (2018-01-26) | Opened, full page text | Whole article |

Not opened: Nick Tune, "Modelling Bounded Contexts with the Bounded Context Design Canvas: A Workshop Recipe" (Medium, HTTP 403). Nothing from it is cited. The eventstorming.com resources page was opened only as a link list; it contains no method text and is not counted or cited.

All quotes below are from page text actually retrieved. No claim rests on recall.

## Findings

### A. Discovering terms

**A1. Have domain experts tell a concrete story; record it visibly, sentence by sentence, in their words** (Hofer & Schwentner, source 6)

- "Domain Storytelling is a conversation technique." Participants are "domain experts (often from several departments), IT experts and a moderator."
- Sentence shape: "Domain stories visualize who (actor) does what (activity) with what (work objects) with whom (other actors)." Actors and work objects are "labeled with a term from the domain language"; activities are "labeled with verbs from the domain language". "Actors and work objects are nouns, and activities are verbs."
- Moderator questions given by the authors: "What happens next?", "Where do you get this information?", "How do you determine what to do next?", "How do you do that?" In the worked example the modeller also asks "Who sells the tickets?" and "Who buys the tickets?" when the expert uses an unspecific "you".
- "Engage the participants without imposing your opinion on them. Use the language of the participants, not your own!"
- "The participants see what gets recorded and give feedback immediately."
- Result claimed in the example: after a few stories the modeller "knows terms like 'seating plan,' 'show,' 'cashier,' 'to search for available seats,' and 'to mark seats.'"
- "We use annotations to explain terms from the domain language, and to document assumptions or anything else that is noteworthy."

**A2. Concrete cases before abstractions** (sources 5, 6)

- Hofer & Schwentner: "premature abstractions are often wrong and not useful for understanding a domain." "First establish a sound understanding of typical cases—tell stories. Only then discuss what else could happen—collect rules." "We recommend you start with modeling the default case—the '80% case'—and the 'happy path' first." Assumptions are spoken and written down to keep one story line: "Assuming that there are still seats available, what do you do next?"
- Wynne: "Concrete examples are a tremendous way to help us explore the problem domain". In Example Mapping the story goes on a yellow card, each known rule on a blue card, examples under each rule on green cards, unanswered questions on red cards. Examples are named roughly ("The one where the customer forgot his receipt") rather than written as formal scenarios.

**A3. Everyone writes first, alone; then the group merges** (ddd-crew cheat sheet, source 3)

- Chaotic exploration: "Start with asking people to write their domain events that they know of for themselves. Here people must work by themselves so that we don't bias each other." "We want their perception on the paper."
- Enforce the timeline: "Start discussing the events", "Removing duplicate events, let them discuss if they really are duplicate events, it might be the same language for different concepts."
- Invite "everyone who brings knowledge and who needs the knowledge, usually domain experts and the engineers."
- Wording for business people: "the word 'Action' usually fits better with stakeholders than command"; "we prefer not to use the word aggregate with business stakeholders." The cheat sheet also says to "avoid jargon as much as possible, as it sets up the unnecessary insider-outsider distinction."
- Design-level EventStorming: "Together with business stakeholders, we design a shared language and represent that in a shared model that brings value in solving a problem within a bounded context."

**A4. Writing scenarios together develops the language early; later the product person reviews** (Wynne, source 5)

- "there is immense value in writing Gherkin together too, especially during the early days of a project. That's where you develop your ubiquitous language, and it's vital to have those scenarios expressed in a way that everyone on the team believes in."
- "For a team that's up and running, with a fairly mature domain language", the product person attends the example mapping session, the others draft the scenarios, and the product person gives feedback on the draft: "Is that how I would have written it?" Wynne calls this a test of "how effective the example mapping conversation was in transferring the product person's knowledge".

**A5. Discovery is continuous and comes before decomposition** (ddd-crew starter process, source 1)

- Step "Discover": "Discover the domain visually and collaboratively. This is the most crucial aspect of DDD. You cannot skip discovery."
- "Teams who are successful with DDD are practicing discovery techniques on a frequent basis. There is always more to learn about the domain."
- Tools listed for Discover: Domain Storytelling, Example Mapping, EventStorming, User Journey Mapping, User Story Mapping; EventStorming is the recommended starting point.
- Who to involve in Discover: people who build software, people with domain knowledge, people who understand product and business strategy, people who understand customers' needs, and "Real end users".
- Cadence from Wynne (source 5): "every other day is often a good rhythm. Just pick one story and give it 25 minutes of attention".

### B. Discovering bounded contexts

**B1. A word that means different things to different groups signals a boundary** (sources 4, 7, 3)

- Fowler: "Different groups of people will use subtly different vocabularies in different parts of a large organization." Example: "the word 'meter' meant subtly different things to different parts of the organization". "Time and time again I see this confusion recur with polysemes like 'Customer' and 'Product'." "These subtle polysemes could be smoothed over in conversation but not in the precise world of computers."
- Fowler on where boundaries lie: "Various factors draw boundaries between contexts. Usually the dominant one is human culture, since models act as Ubiquitous Language, you need a different model when the language changes."
- Brandolini: "Some words have different meaning depending on the context they're used in." Example: "Account" as a "container for money" versus authentication and user credentials. A second case: one concept used in two ways ("we are using it in different ways in our application") also indicates two contexts.
- ddd-crew cheat sheet: apparent duplicate events may be "the same language for different concepts" (see A3).

**B2. Contexts emerge from the big-picture story** (ddd-crew cheat sheet, source 3)

- "From a Big Picture EventStorming we can picture Emerging Bounded Contexts. They are the first indicators of where to start deep-diving towards designing bounded contexts around business problems." (The cheat sheet attributes this to Brandolini's chapter "Discovering Bounded Contexts with EventStorming", which was not opened.)
- "Pivotal Events": "we start looking for the few most significant events in the flow", "often the events with the highest number of people interested." Swimlanes by "actors or departments" are named as another way of structuring the flow. (Same attribution.)

**B3. Groups in a domain story can mark organisational boundaries and subdomains** (Hofer & Schwentner, source 6)

- A group outline can express, among other things, "Organizational boundaries" and "Subdomains". "Other artifacts of the software development process will crystallize and grow around the domain stories as well, for example context maps and requirements."

**B4. Draw a rough context map as an investigation** (Brandolini, source 7)

- "The basic idea is to draw context boundaries on the whiteboard, optionally filling them up with relevant domain terms of classes. This is not a precise well-defined UML diagram: it's a working tool that allows us to map a fuzzy situation, so a somewhat fuzzy look is necessary."
- "Drawing the context map is an investigation activity where many pieces of information might not be correct at first try, borders are initially blurred and several steps are required to get a clear snapshot of the overall picture."
- "A Context Map reflects our current level of understanding of the whole system, and will be updated as long as we learn something more".

**B5. Model more than once before fixing boundaries** (ddd-crew starter process, source 1)

- "Before you dive into the definition of individual bounded contexts, it may be beneficial to model the domain multiple times and look for different ways to decompose your system into sub-domains and teams."
- Step "Decompose": "we recommend carving up your event storm into sub-domains and Context Maps." Step "Connect": "challenge the initial design by applying concrete use-cases to uncover hidden complexity."
- Step "Define": "make explicit decisions about the choices which can have a significant impact on the overall design. Have these conversations early while it is still easy to change your mind and explore alternative models."

**B6. Naming and stating purpose as a discovery and agreement step** (ddd-crew Bounded Context Canvas, source 2)

- "Start with the name and description of the canvas to clarify its reason for existing and key responsibilities in a sentence or two."
- Name: "Naming is hard. Writing down the name of your context and gaining agreement as a team will frame how you design the context."
- Purpose: "A few sentences describing the why and what of the context in business language. No technical details here. Writing down the purpose forces you to clearly articulate fuzzy thoughts and ensure everybody in the team is on the same page."
- Ubiquitous Language section prompt: "What are the key domain terms that exist within this context, and what do they mean?"
- Challenge tips: "Experiment by moving something on the canvas to another context. How is the design affected?" and "Are the names of messages coherent with each other and the description of the context?"

**B7. Subdomains (Khononov, source 8): only loosely related**

- The article opens: "we always tend to disagree on the definitions of such basic terms as Domains and Subdomains", and settles the author's own usage by stating a working definition and its usefulness ("My view of Domains and Subdomains is not an absolute truth, just a model").
- It gives questions for classifying subdomains (for example "Does the system resemble a CRUD interface, and is it described by the Domain Experts in CRUD terms? - Simple") and says the model can be described "to business people in no time".
- It does not discuss discovering terms, bounded contexts, or settling term conflicts.

### C. Settling disagreement and ambiguity

**C1. Read the story back and ask for agreement** (Hofer & Schwentner, source 6)

- During recording: "Anna reads back what she has understood. ... 'Is that ok?'"
- At the end: "When the story seems to be finished, tell the story from the beginning and try to get agreement: Did we miss something? Is something obviously wrong? Do all domain experts agree with the story?"
- "Revisit the annotations for possible alternative stories. Let the participants decide which ones are minor variations and which deserve their own domain story."
- In the worked example the retelling surfaces a wrong assumption by the modeller ("I thought you sell special tickets for those." / "No, you only have to point out to the moviegoers which language the movie will be shown in.").

**C2. A real term conflict is two contexts, not a compromise word** (Brandolini, source 7)

- "Ambiguity is the super-villain of our Ubiquitous Language, and we need to get rid of it."
- "Everybody in the team should be able to agree on every specific term without ambiguities and no translation should be needed".
- When the domain expert "would insist that Account is the right term": "Resist the temptation to invent a specific trade-off term, or to introduce a translation offset from domain expert terms to code. You're facing two separate contexts here."
- Prefixing class names is described as a common fix that "might not always be a viable solution"; "on a conceptual level, we must be aware that we have two different contexts in play".
- "The best way for doing that is to expose the domain structure in terms of bounded contexts in a context map."
- Fowler (source 4) describes the same outcome: "Different contexts may have completely different models of common concepts with mechanisms to map between these polysemic concepts for integration."

**C3. Make the conflict visible and park it** (sources 3, 5, 2)

- ddd-crew cheat sheet: "Hotspots are used to visualise and capture hot conflicts. Conflicts caused by, and not exclusive to, inconsistencies (in language), frictions, questions, dissent, objections, issues or procrastinating going deep to explore for later." "During Step 2 we will get a lot of conflicts between several perceptions, which is good. ... to be able to manage these conflicts we add a pinkish sticky where there are conflicts." The facilitator has "a neutral role so that you can cut long discussions short and visualise them with hotspots."
- Wynne: "Whenever a conversation like this is going round in circles, it's because you don't have enough information. Probably someone is missing from the conversation, or maybe you need to do some user research, or a spike. Instead of letting everyone share their opinion about what they think the outcome should be, simply capture the question and move on." "You've just turned an unknown unknown into a known unknown."
- Wynne: "When the outcome (Then) is unclear, you don't have an example, you have a question."
- Bounded Context Canvas, Open Questions: "If you have questions that no one in the room can answer while running a workshop you can enter them into this section of the canvas." "Many questions are a good indicator towards a high degree of uncertainty." Assumptions: "Most design happens based on assumptions and it is highly recommended to make them explicit."

**C4. The amount of open conflict is read as a readiness signal** (Wynne, source 5)

- "A table covered in red (question) cards tells us that we still have a lot to learn about this story."
- If a story cannot be mapped in about 25 minutes, one option is to "let the product person go off and do some homework before you put story back into another example mapping session at a later date."
- "we use a quick thumb-vote after 25 minutes to determine whether we think the story is ready to pull into development. Even if there are some questions remaining, you might think they're minor enough that you can resolve them as you go. Let the group decide."

**C5. Who decides** (sources 3, 5, 6)

- ddd-crew cheat sheet, workshop agreements: "Everyone is right; nobody has the monopoly on the truth." Facilitator: "You have to observe and let the group figure out what their needs are, however sometimes you need to decide for them when the group can't."
- Wynne: invite "Anyone likely to help you discover new questions, or to turn questions into decisions during the conversation"; readiness is decided by the group (C4).
- Hofer & Schwentner: agreement is sought from "all domain experts"; participants decide which variations deserve their own story (C1).
- No source read names a single person with final authority over a term.

### D. Conflicts between sources

- **Precision.** Brandolini (source 7) asks for "a very precisely and unambiguously defined meaning" of each term. The same article says the context map itself must keep "a somewhat fuzzy look", and the ddd-crew cheat sheet (source 3) and Wynne (source 5) favour parking unresolved points over resolving them in the session. The sources apply precision to the terms inside one context and tolerance of fuzziness to the map and the workshop; none of them states this distinction as a rule.
- **Settle now or defer.** Hofer & Schwentner (source 6) try "to get agreement" on the story before finishing. Wynne (source 5) and the ddd-crew cheat sheet (source 3) say to capture the disagreement and move on when information is missing. Side by side: agreement on what was told versus deferral of what nobody present knows.
- **Who writes first.** ddd-crew cheat sheet (source 3): everyone writes individually and silently before discussing, "so that we don't bias each other". Hofer & Schwentner (source 6): one moderator records while the experts talk, "thus determining the pace of the storytelling".

## Limitations

- **Nick Tune not examined.** His workshop recipe (Big Picture EventStorming, candidate context modelling, flow storytelling, canvas) returned HTTP 403. The canvas README (source 2) is community-maintained and is the only canvas material read.
- **Brandolini's current EventStorming material not examined.** Source 7 is from 2009 and predates EventStorming. His chapter "Discovering Bounded Contexts with EventStorming" and the book *Introducing EventStorming* were not opened; findings B2 rest on the ddd-crew cheat sheet's attribution to them.
- **Vaughn Vernon not examined** in this note (size limit reached).
- **Khononov contributed little.** The article read (source 8) concerns subdomain classification. His writing on bounded contexts and language conflicts (books; other posts) was not opened.
- **Domain Storytelling book chapters** (language style, workshop difficulties, combining methods) were not opened; only the quick-start guide.
- Not examined: dddheuristics.com (design heuristics for boundaries), ddd-crew context-mapping and domain-message-flow-modelling repositories, Evans' Model Exploration Whirlpool, Verraes and Wirfs-Brock on splitting contexts (linked by Fowler), Example Mapping follow-up posts, talks and videos.
- No source read describes: an escalation or tie-break rule when domain experts keep disagreeing about a term within one context; how a one-to-one interview (single product owner, no group) changes these practices. All sources describe group workshops.
- The findings are what these authors say they do or advise. No source read gives evidence of how common each practice is among teams.

## References

1. ddd-crew, *Domain-Driven Design Starter Modelling Process*. https://github.com/ddd-crew/ddd-starter-modelling-process (first-hand, opened)
2. ddd-crew, *The Bounded Context Canvas*. https://github.com/ddd-crew/bounded-context-canvas (first-hand, opened)
3. ddd-crew, *EventStorming Glossary & Cheat sheet*. https://github.com/ddd-crew/eventstorming-glossary-cheat-sheet (first-hand, opened)
4. Martin Fowler, "BoundedContext", 15 January 2014. https://martinfowler.com/bliki/BoundedContext.html (first-hand, opened)
5. Matt Wynne, "Introducing Example Mapping", 8 December 2015. https://cucumber.io/blog/bdd/example-mapping-introduction/ (first-hand, opened)
6. Stefan Hofer & Henning Schwentner, "Quick-Start Guide", Domain Storytelling. https://domainstorytelling.org/quick-start-guide (first-hand, opened)
7. Alberto Brandolini, "Strategic Domain Driven Design with Context Mapping", InfoQ, 25 November 2009. https://www.infoq.com/articles/ddd-contextmapping/ (first-hand, opened)
8. Vlad Khononov, "Revisiting the Basics of Domain-Driven Design", 26 January 2018. https://vladikk.com/2018/01/26/revisiting-the-basics-of-ddd/ (first-hand, opened)

Not opened: Nick Tune, "Modelling Bounded Contexts with the Bounded Context Design Canvas: A Workshop Recipe". https://medium.com/skills-matter/modelling-bounded-contexts-with-the-bounded-context-design-canvas-a-workshop-recipe-6a081255efac (HTTP 403)
