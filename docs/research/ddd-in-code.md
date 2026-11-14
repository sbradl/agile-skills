# Building Blocks for Expressing a Domain Model in Code, and the Criteria for Choosing Between Them

## Abstract

Evans' DDD Reference names nine "building blocks of a model-driven design": layered architecture, entities, value objects, domain events, services, modules, aggregates, repositories and factories. Each comes with a stated trigger. A concept is an **entity** when it is "distinguished by its identity, rather than its attributes" and has a lifecycle; a **value object** when "you care only about the attributes and logic" of it; a **domain event** when "something happened that domain experts care about"; a **service** when a significant process or transformation "is not a natural responsibility of an entity or value object"; a **module** for a cohesive set of concepts, chosen to "tell the story of the system"; an **aggregate** when a cluster of entities and values shares invariants that must hold as a whole; a **repository** for each aggregate type "that needs global access"; a **factory** when creating an aggregate or large value object "becomes complicated or reveals too much of the internal structure". Vernon's three essays supply the criteria for drawing aggregate boundaries: the boundary is a transactional consistency boundary drawn around *true invariants* (business rules that must always be consistent), aggregates are kept small, other aggregates are referenced by identity, and rules that span aggregates are made eventually consistent, typically via domain events. His tie-breaker, credited to Evans: ask whether making the data consistent is the job of the user executing the use case (then transactional, inside one aggregate) or of another user or the system (then eventual). Vernon and Fowler add tests for value versus entity: can the part be completely replaced rather than changed over time (Vernon); is equality decided by the values of the properties or by a reference/identifier (Fowler); and the answer depends on context (Fowler). First-hand sources answered the question within the five-source limit; three of Fowler's four named articles were left unread because of that limit.

## Question

Which building blocks does Domain-Driven Design use to express a domain model in code (aggregates, entities, value objects, domain events, services, repositories, factories, modules and so on), what is each one for, and by which criteria is one chosen over another?

Why: an agent skill is being designed that guides a team towards a ubiquitous language and, at the end of a session, gives ideas on how the surfaced domain concepts could be expressed in code, each with a justification. The skill needs the selection criteria, for example when a concept is a value object rather than an entity, and how aggregate boundaries are drawn.

## Method

First-hand sources only, as the brief required. Five documents were opened and read in full text (PDFs downloaded and converted with `pdftotext`; the HTML page downloaded and stripped of markup). The size limit of five was reached and the research stopped there.

| # | Source | Owner of the fact | How read |
|---|--------|-------------------|----------|
| 1 | Evans, *Domain-Driven Design Reference* (2015), ch. II "Building Blocks of a Model-Driven Design" (pp. 9-18) and ch. III "Supple Design" (pp. 19-27) | Evans, originator of the patterns | Full text of both chapters |
| 2 | Vernon, *Effective Aggregate Design Part I: Modeling a Single Aggregate* (2011) | Vernon, author of the aggregate rules of thumb | Full text |
| 3 | Vernon, *Effective Aggregate Design Part II: Making Aggregates Work Together* (2011) | Vernon | Full text |
| 4 | Vernon, *Effective Aggregate Design Part III: Gaining Insight Through Discovery* (2011) | Vernon | Full text |
| 5 | Fowler, "ValueObject" (martinfowler.com, 14 November 2016) | Fowler, for his own classification | Full text; code samples were stripped by the conversion and not read |

Notes on the reading:

- The Vernon PDFs were fetched from dddcommunity.org, where the essays are hosted; they carry Vernon's byline and copyright. The essays state that Eric Evans and Paul Rayner reviewed them.
- PDF text extraction interleaves columns in the Vernon essays. Quoted sentences were checked as contiguous text; figures (UML diagrams) were not seen.
- The two earlier notes in this directory (`ubiquitous-language.md`, `ubiquitous-language-practices.md`) were skimmed. Their findings on the language itself, on names in code conforming to the language, and on bounded contexts are not repeated here.
- No second-hand source was used as evidence.

## Findings

Page numbers for Evans refer to the printed page numbers of the DDD Reference. Vernon's essays are paginated continuously: Part I pp. 1-6, Part II pp. 7-11, Part III pp. 11-15.

### 1. What the building blocks are for, as a set (Evans, p. 9)

- "These patterns cast widely held best practices of object-oriented design in the light of domain-driven design. They guide decisions to clarify the model and to keep the model and implementation aligned with each other."
- The chapter lists, in this order: Layered Architecture, Entities, Value Objects, Domain Events, Services, Modules, Aggregates, Repositories, Factories.
- Domain Events is marked in the table of contents as a "new term introduced since the 2004 book".

### 2. Each block: purpose and the stated trigger for using it (Evans, pp. 10-18)

Each pattern in the Reference has a problem statement followed by "Therefore:" and the prescription. The trigger column quotes the condition Evans attaches.

| Block | Purpose (Evans) | Stated trigger ("when ...") | Page |
|-------|-----------------|-----------------------------|------|
| Layered Architecture | "Isolate the expression of the domain model and the business logic, and eliminate any dependency on infrastructure, user interface, or even application logic that is not business logic." | Domain-related code is "diffused through such a large amount of other code" that it is hard to see and reason about. "The key goal here is isolation"; "Hexagonal Architecture" and similar "may serve as well or better". | 10 |
| Entity (aka Reference Object) | Represents "a thread of continuity and identity, going through a lifecycle, though their attributes may change." | "When an object is distinguished by its identity, rather than its attributes, make this primary to its definition in the model." | 11 |
| Value Object | "Some objects describe or compute some characteristic of a thing." | "When you care only about the attributes and logic of an element of the model, classify it as a value object." | 12 |
| Domain Event | "Something happened that domain experts care about." | "Model information about activity in the domain as a series of discrete events"; make explicit "the events that the domain experts want to track or be notified of, or which are associated with state change in the other model objects." | 13 |
| Service | "Sometimes, it just isn't a thing." | "When a significant process or transformation in the domain is not a natural responsibility of an entity or value object, add an operation to the model as a standalone interface declared as a service." | 14 |
| Module (aka Package) | Divides concepts, not just code: "Choose modules that tell the story of the system and contain a cohesive set of concepts." | Always present ("Everyone uses modules, but few treat them as a full-fledged part of the model"); the criterion is partitioning "according to high-level domain concepts". | 15 |
| Aggregate | Guarantees "the consistency of changes to objects in a model with complex associations." | Entities and value objects are clustered and bounded; "Define properties and invariants for the aggregate as a whole." | 16 |
| Repository | "Query access to aggregates expressed in the ubiquitous language." | "For each type of aggregate that needs global access"; "Provide repositories only for aggregate roots that actually need direct access." | 17 |
| Factory | Encapsulates creation. | "When creation of an entire, internally consistent aggregate, or a large value object, becomes complicated or reveals too much of the internal structure." | 18 |

### 3. Entity: details (Evans, p. 11)

- The problem it answers: "Sometimes such an object must be matched with another object even though attributes differ. An object must be distinguished from other objects even though they might have the same attributes. Mistaken identity can lead to data corruption."
- Prescription: "Keep the class definition simple and focused on life cycle continuity and identity. Define a means of distinguishing each object regardless of its form or history."
- "Be alert to requirements that call for matching objects by attributes."
- The identifier "may come from the outside, or it may be an arbitrary identifier created by and for the system, but it must correspond to the identity distinctions in the model. The model must define what it means to be the same thing."

### 4. Value object: details (Evans, p. 12; Fowler)

Evans:

- "Many objects have no conceptual identity." Attaching identity to them "can hurt system performance, add analytical work, and muddle the model by making all objects look the same."
- A value object is not merely the absence of identity: "these objects have characteristics of their own, and their own significance to the model. These are the objects that describe things."
- "Make it express the meaning of the attributes it conveys and give it related functionality. Treat the value object as immutable. Make all operations Side-effect-free Functions that don't depend on any mutable state. Don't give a value object any identity."

Fowler ("ValueObject"):

- Definition by equality: "Objects that are equal due to the value of their properties ... are called value objects." Fowler distinguishes "value objects and reference objects, depending on how I tell them apart".
- Reference objects are compared by memory reference or by a unique identifier (his example: a sales order compared by order number).
- Relation to Evans' terms: "In Domain-Driven Design the Evans Classification contrasts value objects with entities. I consider entities to be a common form of reference object, but use the term 'entity' only within domain models while the reference/value object dichotomy is useful for all code."
- Immutability: "value objects should be immutable", to avoid aliasing bugs (a change in one place having consequences elsewhere). To change a value, "I create a new object instead." Alternative: "ensuring assignments always make a copy", as with structs in C#.
- Immutability alone does not make something a value object: an immutable sales order is still a reference object "if I'm determining equality based on a unique order number" (note 7).
- Examples he gives of value objects: a 2D point, an amount of money (number and currency), a date range, a telephone number.
- Replacing primitives: "It's often a good idea to replace common primitives, such as strings, with appropriate value objects." A telephone number object "makes variables and parameters more explicit (with type checking when the language supports it), a natural focus for validation, and avoiding inapplicable behaviors (such as doing arithmetic on integer id numbers)."
- Size: "Small objects, such as points, monies, or ranges, are good examples of value objects. But larger structures can often be programmed as value objects if they don't have any conceptual identity or don't need share references around a program."
- Behaviour: "once I've spotted a good set of value objects, I find I can create a rich behavior over them", for example a Range class that "prevents all sorts of duplicate fiddling with start and end attributes".
- Terminology warning: around 2000 some J2EE literature used "value object" for Data Transfer Object; "that usage has mostly disappeared".

### 5. Criteria: entity or value object?

The sources state these tests:

| Test | Points to value object when ... | Points to entity when ... | Source |
|------|---------------------------------|---------------------------|--------|
| What is cared about | "you care only about the attributes and logic" | the object "is distinguished by its identity, rather than its attributes" | Evans pp. 11-12 |
| Continuity | it has "no conceptual identity" | it is "a thread of continuity and identity, going through a lifecycle, though [its] attributes may change" | Evans pp. 11-12 |
| Matching | two instances with the same attributes are interchangeable | it "must be distinguished from other objects even though they might have the same attributes", or matched "even though attributes differ" | Evans p. 11 |
| Equality | equality is by the value of the properties | equality is by reference or a unique identifier | Fowler |
| Replace or change | "instances can be completely replaced" when change is necessary | the part "must itself change over time" | Vernon I |
| Sharing | it does not "need [to] share references around a program" | (the converse is implied, not stated) | Fowler |

Further statements bearing on the choice:

- It depends on context. Fowler: "Whether to treat a concept as a reference object or value object depends on your context. In many situations it's worth treating a postal address as a simple structure of text with value equality. But a more sophisticated mapping system might link postal addresses into a sophisticated hierarchic model where references make more sense. As with most modeling problems, different contexts lead to different solutions."
- Vernon states a preference inside aggregates: "What if you think you should model a contained part as an entity? First ask whether that part must itself change over time, or whether it can be completely replaced when change is necessary. If instances can be completely replaced, it points to the use of a value object rather than an entity. At times entity parts are necessary. Yet, if we run through this exercise on a case-by-case basis, many concepts modeled as entities can be refactored to value objects." (Part I)
- Vernon's stated advantages of value parts: values "can be serialized with the root entity, whereas entities usually require separately tracked storage"; "Value objects are smaller and safer to use (fewer bugs). Due to immutability it is easier for unit tests to prove their correctness." (Part I)
- "Favoring value types as aggregate parts doesn't mean the aggregate is immutable since the root entity itself mutates when one of its value-typed properties is replaced." (Vernon, Part I)
- Vernon distinguishes a "value-typed property" (an attribute holding a reference to a value object) from "a simple attribute such as a String or numeric type" (Part I, note 4).
- Evans gives a cost reason for the distinction as such: "We must make distinctions so that special handling is applied only where necessary." (p. 12)
- Evans: complex logic is moved "into value objects when a concept fitting the responsibility presents itself" (Side-Effect-Free Functions, p. 21); closed operations are "an opportunity to look for in the value objects", because "entities are not the sort of concepts that are likely to be the result of a computation" (Closure of Operations, p. 24).

### 6. Domain event: details (Evans, p. 13; Vernon II-III)

Evans:

- The gap it fills: an entity tracks its state, "But if you need to know the actual causes of the state changes, this is typically not explicit." Audit trails "are not usually suited to being used for the logic of the program itself"; change histories ignore "the meaning of those changes".
- "Represent each event as a domain object." "A domain event is a full-fledged part of the domain model, a representation of something that happened in the domain."
- Selection: "Ignore irrelevant domain activity while making explicit the events that the domain experts want to track or be notified of, or which are associated with state change in the other model objects."
- Domain events are "distinct from system events that reflect activity within the software itself".
- Shape: "Domain events are ordinarily immutable, as they are a record of something in the past." A domain event "typically contains a timestamp for the time the event occurred and the identity of entities involved in the event", often also a timestamp for when it was entered and who entered it. An identity for the event "can be based on some set of these properties".
- Second use, in distributed systems: "We keep the aggregates internally consistent at all times, while making other changes asynchronously"; "the state of an entity can be inferred from the domain events currently known to a particular node".

Vernon:

- Events are the mechanism for consistency between aggregates: "An aggregate command method publishes a domain event that is in time delivered to one or more asynchronous subscribers." Each subscriber "executes in a separate transaction, obeying the rule of aggregate to modify just one instance per transaction." (Part II)
- His examples are named in the past tense after what happened: `BacklogItemCommitted` (Part II), `TaskHoursRemainingEstimated` (Part III), the latter carrying `occurredOn`, the tenant identity, the identities of the aggregates involved and the value estimated.
- Across bounded contexts: "message-based domain events containing aggregate identities are sent around the enterprise. Message subscribers in foreign bounded contexts use the identities to carry out operations in their own domain models." (Part II)

### 7. Service: details (Evans, p. 14; Vernon)

- Evans: "Some concepts from the domain aren't natural to model as objects. Forcing the required domain functionality to be the responsibility of an entity or value either distorts the definition of a model-based object or adds meaningless artificial objects."
- "Define a service contract, a set of assertions about interactions with the service ... State these assertions in the ubiquitous language of a specific bounded context. Give the service a name, which also becomes part of the ubiquitous language."
- Vernon uses two kinds of service in his examples without defining them: a "transactional application service" that loads aggregates from repositories, calls one aggregate command and holds the transaction (Parts I-II), and a "domain service" to which an event subscriber delegates "to coordinate the consistency processing" (Part III). Evans' Reference mentions "application logic that is not business logic" as something the domain layer is isolated from (p. 10) but has no separate pattern for application services.

### 8. Module: details (Evans, p. 15)

- "Yet it isn't just code being divided into modules, but also concepts. There is a limit to how many things a person can think about at once (hence low coupling). Incoherent fragments of ideas are as hard to understand as an undifferentiated soup of ideas (hence high cohesion)."
- "Give the modules names that become part of the ubiquitous language. Modules are part of the model and their names should reflect insight into the domain."
- If low coupling does not result, "look for a way to change the model to disentangle the concepts, or an overlooked concept that might be the basis of a module that would bring the elements together in a meaningful way."
- What modules are contrasted with: code "broken down into all sorts of categories, from aspects of the technical architecture to developers' work assignments".

### 9. Aggregate: Evans' definition (p. 16)

- Problem: objects "can be blindsided by changes in other objects that are conceptually constituent parts. Cautious database locking schemes cause multiple users to interfere pointlessly with each other and can make a system unusable."
- "Cluster the entities and value objects into aggregates and define boundaries around each. Choose one entity to be the root of each aggregate, and allow external objects to hold references to the root only (references to internal members passed out for use within a single operation only)."
- "Define properties and invariants for the aggregate as a whole and give enforcement responsibility to the root or some designated framework mechanism."
- "Use the same aggregate boundaries to govern transactions and distribution. Within an aggregate boundary, apply consistency rules synchronously. Across boundaries, handle updates asynchronously. Keep an aggregate together on one server."
- "When these design decisions are not being guided well by the aggregate boundaries, reconsider the model. Is the domain scenario hinting at an important new insight?"
- Related: "Assertions define invariants on aggregates" and "State post-conditions of operations and invariants of classes and aggregates" (Assertions, p. 22).

### 10. Criteria: how aggregate boundaries are drawn (Vernon, Parts I-III)

Vernon summarises four "rules of thumb" (Part III summary):

1. "Model True Invariants In Consistency Boundaries"
2. "Design Small Aggregates"
3. "Reference Other Aggregates By Identity"
4. "Use Eventual Consistency Outside the Boundary (after asking whose job it is)"

**Rule 1: true invariants (Part I)**

- "When trying to discover the aggregates in a bounded context, we must understand the model's true invariants. Only with that knowledge can we determine which objects should be clustered into a given aggregate."
- "An invariant is a business rule that must always be consistent." When discussing invariants, "we are referring to transactional consistency", which is "immediate and atomic".
- "aggregate is synonymous with transactional consistency boundary." "The consistency of everything outside this boundary is irrelevant to the aggregate."
- "A properly designed aggregate is one that can be modified in any way required by the business with its invariants completely consistent within a single transaction. And a properly designed bounded context modifies only one aggregate instance per transaction in all cases." He calls the latter "a rule of thumb" that "should be the goal in most cases".
- "aggregates are chiefly about consistency boundaries and not driven by a desire to design object graphs."
- False invariants: in his example, the phrase "Products have backlog items, releases, and sprints" was read as composition and produced one large aggregate. The rules the developers added ("If a backlog item is committed to a sprint, we must not allow it to be removed from the system") were "false invariants ... artificial constraints imposed by developers", "not real business rules". Symptom: two users doing logically unrelated work (planning a backlog item, scheduling a release) caused each other's commits to fail.
- The two errors named: "designing for compositional convenience and make them too large", or to "strip all aggregates bare, and as a result fail to protect true invariants".
- Consequence for the interface: "the user interface should concentrate each request to execute a single command on just one aggregate instance."

**Rule 2: small aggregates (Part I)**

- "limit the aggregate to just the root entity and a minimal number of attributes and/or value-typed properties. The correct minimum is the ones necessary, and no more."
- "Which ones are necessary? The simple answer is: those that must be consistent with others, even if domain experts don't specify them as rules." Example: a product's name and description belong together; that is "an implicit" rule.
- Reasons given: large aggregates load large collections for basic operations ("thousands of backlog items would be loaded into memory just to add one new element"); "Smaller aggregates not only perform and scale better, they are also biased toward transactional success, meaning that conflicts preventing a commit are rare."
- Reported experience: on one project "approximately 70% of all aggregates" had "just a root entity containing some value-typed properties. The remaining 30% had just two to three total entities." Vernon adds: "This doesn't indicate that all domain models will have a 70/30 split."
- When a true consistency rule is found: "add another few entities, or possibly a collection, as necessary, but continue to push yourself to keep the overall size as small as possible."
- Evans' own multi-entity example, as cited by Vernon: a purchase order with a maximum allowable total that the sum of line items must not surpass. Vernon: "most of the time the invariants of business models are simpler to manage than that example."
- "Don't Trust Every Use Case": a use case that modifies several aggregate instances in one transaction "may not accurately reflect the true aggregates of our model". Two possible readings he gives: the team "has missed an invariant" and the aggregates fold into "one new concept with a new name"; or "the business goal can be achieved with eventual consistency between aggregates". "A user goal should not be viewed as synonymous with transaction."

**Rule 3: reference by identity (Part II)**

- "Prefer references to external aggregates only by their globally unique identity, not by holding a direct object reference". In the example, `BacklogItem` holds a `ProductId` rather than a `Product`.
- A reference "does not place the referenced aggregate inside the consistency boundary of the one referencing it".
- "If you are modifying multiple instances in a single transaction, it may be a strong indication that your consistency boundaries are wrong. If so, it is possibly a missed modeling opportunity; a concept of your ubiquitous language has not yet been discovered".
- Navigation: "Use a repository or domain service to look up dependent objects ahead of invoking the aggregate behavior." An application service may do the lookup and then dispatch to the aggregate.
- Benefits stated: smaller aggregates, less memory, and the ability to move persistent state around for scale and distribution.
- Cost stated: it "could make it more difficult to serve clients that assemble and render user interface views. You may have to use multiple repositories in a single use case to populate views." He mentions CQRS as an option to consider if query overhead becomes a performance issue.

**Rule 4: eventual consistency outside the boundary (Part II)**

- Vernon quotes Evans' book (p. 128): "Any rule that spans AGGREGATES will not be expected to be up-to-date at all times. Through event processing, batch processing, or other update mechanisms, other dependencies can be resolved within some specific time."
- "if executing a command on one aggregate instance requires that additional business rules execute on one or more other aggregates, use eventual consistency."
- "Ask the domain experts if they could tolerate some time delay between the modification of one instance and the others involved. Domain experts are sometimes far more comfortable with the idea of delayed consistency than are developers."
- The tie-breaker, "Ask Whose Job It Is", which Vernon attributes to a discussion with Evans: "When examining the use case (or story), ask whether it's the job of the user executing the use case to make the data consistent. If it is, try to make it transactionally consistent, but only by adhering to the other rules of aggregate. If it is another user's job, or the job of the system, allow it to be eventually consistent." He adds that it "may not always lead to the final answer ... but will usually provide deeper insight into the model" and "exposes the real system invariants".

**Where the invariant is found, and the worked decision (Part III)**

- "A key to making a proper determination lies in the ubiquitous language. Here is where an invariant is stated". His example sentences: "When a team member estimates that zero hours are remaining on a specific task, the backlog item checks all tasks for any remaining hours. If no hours remain on any tasks, the backlog item status is automatically changed to done."
- The team then weighs keeping `Task` inside the `BacklogItem` aggregate against splitting it, using: a back-of-the-envelope estimate of how many objects the aggregate holds and loads per request (25 at most in the example, judged "a small aggregate"); the common usage scenarios and whether several users contend for the same instance; whether domain experts accept a delay; the user-interface effect of a stale status; and whose job the consistency is.
- "If the developers learned that multiple users do indeed regularly want to add tasks together, it would change the analysis significantly."
- Outcome in the example: the team keeps `Task` inside `BacklogItem` for now, because they "can't be certain that splitting it now is worth the extra effort, the risk of leaving the true invariant unprotected, or allowing users to experience a possible stale status in the view", and keeps the split as an option after load tests. Vernon presents this as open: "which modeling option would you have chosen?"
- The exercise also surfaced a new domain aspect (a configurable workflow preference for manual or automatic completion). Vernon: such a discovery session "would require 30 minutes, and perhaps as much as 60 minutes at worse case".

**Stated reasons to break the rules (Part II)**

Vernon lists four, noting "we don't go in search of excuses to break the aggregate rules of thumb":

1. User interface convenience: creating a batch of aggregates at once, when "creating a batch of aggregate instances all at once is semantically no different than creating one at a time repeatedly".
2. Lack of technical mechanisms for eventual consistency (no messaging, timers or background threads); supported further by "user-aggregate affinity", where only one user works on a set of aggregate instances at a time.
3. Global (two-phase commit) transactions imposed by enterprise policy.
4. Query performance: "There may be times when it's best to hold direct object references to other aggregates."

### 11. Repository: details (Evans, p. 17; Vernon)

- Problem: "Proliferation of traversable associations used only for finding things muddles the model." Unconstrained queries "may pull specific fields from objects, breaching encapsulation, or instantiate a few specific objects from the interior of an aggregate, blindsiding the aggregate root". Result: "the entities and value objects become mere data containers."
- Prescription: "create a service that can provide the illusion of an in-memory collection of all objects of that aggregate's root type." "Provide methods to add and remove objects"; "Provide methods that select objects based on criteria meaningful to domain experts." "Return fully instantiated objects or collections of objects".
- Scope: "Provide repositories only for aggregate roots that actually need direct access."
- Vernon's examples follow this: one repository per aggregate type (`productRepository`, `backlogItemRepository`, `teamRepository`, `TaskRepository`), queried by identity. In Part III a repository also returns a computed sum (`totalBacklogItemTaskHoursRemaining`) instead of loading all instances, as an optimisation.

### 12. Factory: details (Evans, p. 18; Vernon I)

- Problem: "complex assembly operations do not fit the responsibility of the created objects." Having the client construct "breaches encapsulation of the assembled object or aggregate, and overly couples the client to the implementation of the created object."
- Prescription: "Shift the responsibility for creating instances of complex objects and aggregates to a separate object, which may itself have no responsibility in the domain model but is still part of the domain design." "Create an entire aggregate as a piece, enforcing its invariants. Create a complex value object as a piece, possibly after assembling the elements with a builder."
- Vernon shows a factory that is a method on another aggregate rather than a separate object: after the split, `Product.planBacklogItem(...)`, `scheduleRelease(...)` and `scheduleSprint(...)` "each respectively create a new aggregate instance and return a reference to it" and "act as factories". The application service then adds the new instance to its repository. The method names come from the ubiquitous-language statements ("New product backlog items are planned", "New product releases are scheduled").

### 13. "And so on": the supple-design patterns that shape how the blocks are written (Evans, pp. 19-27)

These are not building blocks of chapter II but are cross-referenced from them. Only the points that bear on the blocks above are listed; the rest of chapter III was read but is not summarised.

- Intention-Revealing Interfaces (p. 20): "Name classes and operations to describe their effect and purpose, without reference to the means by which they do what they promise." (The naming-conforms-to-the-language point is in the earlier note.)
- Side-Effect-Free Functions (p. 21): "Place as much of the logic of the program as possible into functions, operations that return results with no observable side effects. Strictly segregate commands ... into very simple operations that do not return domain information." "All operations of a value object should be side-effect-free functions."
- Assertions (p. 22): "Assertions define contracts of services and entity modifiers. Assertions define invariants on aggregates."
- Closure of Operations (p. 24): "This pattern is most often applied to the operations of a value object."
- Conceptual Contours (p. 27): "Decompose design elements (operations, interfaces, classes, and aggregates) into cohesive units, taking into consideration your intuition of the important divisions in the domain."

### 14. Differences between the sources, side by side

| Point | Evans (DDD Reference) | Vernon | Fowler |
|-------|-----------------------|--------|--------|
| References between aggregates | "allow external objects to hold references to the root only" (p. 16) | "Prefer references to external aggregates only by their globally unique identity, not by holding a direct object reference" (Part II). Vernon presents this as consistent with Evans' book ("[DDD] states that one aggregate may hold references to the root of other aggregates") and as a preference; he lists query performance as a reason to hold a direct reference. | not covered in the article read |
| Protecting a value object from aliasing | "Treat the value object as immutable." (p. 12) | values are immutable (Part I) | immutability is "my favorite technique", but copying on assignment is also possible |
| Name for the identity-bearing kind | "Entities (aka Reference Objects)" (p. 11) | entity | "reference object" for all code; "entity" only within domain models, as "a common form of reference object" |
| Transactional versus eventual consistency | "Within an aggregate boundary, apply consistency rules synchronously. Across boundaries, handle updates asynchronously." (p. 16), stated without exceptions | same as a rule of thumb, with four named reasons to break it (Part II) | not covered |

No direct contradiction was found; the differences are of strictness and vocabulary.

## Limitations

- **Source limit reached.** Three of the four Fowler articles named in the brief were not read: "DDD_Aggregate", "EvansClassification" and "DomainEvent". Fowler's own account of aggregates, of the entity/value/service classification and of domain events is therefore missing from this note. Fowler's "ValueObject" refers to "EvansClassification" for the entity contrast.
- **Evans' book not read.** The DDD Reference is a summary of patterns; the book's longer discussion, its examples (the purchase-order aggregate, which Vernon cites) and the Specification pattern are not in the Reference chapters read. Vernon's quote of the book's p. 128 is reported as Vernon quotes it, not checked against the book.
- **Vernon's book not read.** The essays say they are based on his then-upcoming book. Fowler points to Vernon's book for "how to decide between values and entities"; that fuller treatment was not examined. The essays cover aggregates only; Vernon's own criteria for services, events, modules, repositories and factories were not examined beyond what the examples show.
- **Application service versus domain service.** Vernon uses both terms in examples without defining the distinction; the Reference has no pattern for application services. A first-hand definition of the difference was not found in the five sources.
- **No selection criterion found for some pairs.** The sources read do not state a rule for choosing between a domain event and a plain state change on an entity beyond "events that the domain experts want to track or be notified of", nor a rule for when a factory is a separate object versus a method on an aggregate.
- **Language and paradigm.** All examples are object-oriented (Java with Hibernate in Vernon; Java, JavaScript and Clojure in Fowler). Evans frames the building blocks as "best practices of object-oriented design". How the blocks map to functional or other styles was not examined, apart from Fowler's remark that value objects are "a more natural fit with functional languages".
- **Dates.** The essays are from 2011, the Reference from 2015, Fowler's article from 2016. Whether the authors have since revised these positions was not checked.
- **Extraction.** Figures in the Vernon PDFs and code samples in Fowler's article were not seen.

## Recommended reading

1. Martin Fowler, "ValueObject": <https://martinfowler.com/bliki/ValueObject.html>. A short article on what makes something a value rather than a reference object, with the equality and immutability arguments.
2. Vaughn Vernon, "Effective Aggregate Design Part I: Modeling a Single Aggregate": <https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>. Six pages; a worked example of an aggregate drawn too large and then redrawn around true invariants.
3. Eric Evans, *DDD Reference*, chapter II only (pp. 9-18): <https://www.domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf>. One page per building block, each as problem and prescription.

## References

1. Eric Evans, *Domain-Driven Design Reference: Definitions and Pattern Summaries*, Domain Language, Inc., 2015 (CC BY 4.0). <https://www.domainlanguage.com/wp-content/uploads/2016/05/DDD_Reference_2015-03.pdf>. Chapters II and III read. First-hand.
2. Vaughn Vernon, "Effective Aggregate Design Part I: Modeling a Single Aggregate", 2011. <https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>. First-hand.
3. Vaughn Vernon, "Effective Aggregate Design Part II: Making Aggregates Work Together", 2011. <https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>. First-hand.
4. Vaughn Vernon, "Effective Aggregate Design Part III: Gaining Insight Through Discovery", 2011. <https://www.dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>. First-hand.
5. Martin Fowler, "ValueObject", martinfowler.com, 14 November 2016. <https://martinfowler.com/bliki/ValueObject.html>. First-hand.
