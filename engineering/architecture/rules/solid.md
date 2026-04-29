# SOLID

## Decision

The five SOLID principles apply at module and class level, across both backend and frontend.

## Principles

- **SRP — Single Responsibility** — a class/module has one reason to change. If a change requires touching multiple modules at once, that's a smell.
- **OCP — Open/Closed** — open for extension, closed for modification. Add behavior via new types implementing an interface, not by branching on a type tag.
- **LSP — Liskov Substitution** — subtypes must be substitutable for their base. Narrowing preconditions or widening postconditions in a subclass breaks LSP.
- **ISP — Interface Segregation** — many small interfaces > one fat interface. Clients depend only on the methods they use.
- **DIP — Dependency Inversion** — depend on abstractions, not concretions. Hexagonal Architecture enforces DIP at the layer boundary; SOLID is the broader principle.

## Conventions

- A module / class with more than one major reason to change should be split.
- Conditional dispatch on a type tag (`if isinstance(...)`, `switch type`) is a hint to introduce a polymorphic interface.
- Public interfaces declare only the methods clients actually call.
- Constructor parameters take abstractions (ports), never concrete adapters.

## Forbidden

- God classes / kitchen-sink modules.
- Subclassing only to override a single method with incompatible behavior.
- Fat interfaces with optional / NotImplemented methods.
- New direct dependencies from `domain/` to anything concrete (also covered by the Hexagonal rule).

## Why

SOLID is the cheapest way to keep changes localized. SRP keeps blast radius small; OCP/LSP keep extension safe; ISP keeps coupling minimal; DIP makes adapters swappable.

## See also

- Architectural style: [`hexagonal-boundaries.md`](hexagonal-boundaries.md) *(enforces DIP at the layer boundary)*
- Audit: [`../../audit/commands/solid.md`](../../audit/commands/solid.md)
- Checklist: [`../../audit/references/06-solid-checklist.md`](../../audit/references/06-solid-checklist.md)
