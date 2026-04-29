# DDD Tactical Patterns

## Decision

We apply Domain-Driven Design tactical patterns inside `domain/`. Strategic-side concerns (bounded contexts, ubiquitous language) are captured in design docs as needed.

## Patterns

- **Entity** — has an identity (`id`) that survives state changes. Equality by identity.
- **Value Object** — defined by its attributes, immutable, equality by value. Use for amounts, ranges, identifiers wrapped in a type.
- **Aggregate** — a cluster of Entity + Value Objects with a single root. External code references only the root; the root enforces invariants for the cluster.
- **Domain Service** — stateless logic that doesn't fit naturally on an Entity (e.g. cross-aggregate operations).
- **Repository** — collection-like interface in `domain/ports`, accessed only by aggregate root, implemented in `infra/`.
- **Domain Event** — a fact that occurred, named in past tense (`DocumentParsed`, not `ParseDocument`).

## Conventions

- One aggregate per file. The root entity gives the file its name.
- Value Objects: `@dataclass(frozen=True)` (Python) / `readonly` types (TypeScript).
- Repositories return aggregates, never partial DTOs.
- Domain Events emitted by aggregates, dispatched by services.

## Forbidden

- Anemic models — behavior must live on the Entity / Value Object, not in a service.
- Setters on entities. Mutation goes through named methods that enforce invariants.
- Cross-aggregate transactions. One transaction = one aggregate. Cross-aggregate consistency uses Domain Events + eventual consistency.
- ORM annotations on domain types. Mapping lives in the persistence adapter.

## Why

Tactical patterns make the domain shape explicit. Aggregates protect invariants; Value Objects eliminate primitive obsession; Domain Events decouple side effects. Without these, business rules drift into services and the domain becomes anemic.

## See also

- Architectural style: [`hexagonal-boundaries.md`](hexagonal-boundaries.md)
- Audit: [`../../audit/commands/ddd.md`](../../audit/commands/ddd.md)
- Checklist: [`../../audit/references/02-ddd-checklist.md`](../../audit/references/02-ddd-checklist.md)
