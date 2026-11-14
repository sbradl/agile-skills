# Building blocks

How a domain concept can be expressed in code, after Evans' DDD Reference, Vernon's "Effective Aggregate Design" and Fowler's "ValueObject". Justify each coding idea with the trigger of its block.

| Building block | Trigger: the concept... |
|---|---|
| Entity | is distinguished by its identity rather than its attributes, and has a lifecycle |
| Value object | matters only for its attributes and logic |
| Domain event | is something that happened and that domain experts care about |
| Service | is a significant process that is no natural responsibility of an entity or value object |
| Module | is a cohesive set of concepts that tells part of the system's story |
| Aggregate | is a cluster of entities and values sharing rules that must hold as a whole |
| Repository | is an aggregate type that needs global access |
| Factory | is an aggregate whose creation is complicated or reveals too much of its inner structure |

## Value object or entity

- Can it be completely replaced rather than changed over time? Then a value object (Vernon).
- Is equality decided by its values, or by an identifier? Values: value object. Identifier: entity (Fowler).
- The answer depends on the context; the same concept can be a value in one and an entity in another (Fowler).

## Aggregate boundaries (Vernon)

- Draw the boundary around true invariants: business rules that must always be consistent.
- Keep aggregates small; refer to other aggregates by identity.
- Rules spanning aggregates become consistent later, typically through domain events.
- Tie-breaker: when keeping the data consistent is the job of the user performing the action, it belongs in one aggregate; when it is another user's or the system's job, it may follow later.
