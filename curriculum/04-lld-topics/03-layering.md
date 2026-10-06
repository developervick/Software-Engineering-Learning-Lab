# Layering & separation of concerns

- **Track:** lld-topics
- **Prereqs:** coupling & direction
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Organize code so each layer has **one kind of concern** and dependencies flow one way
(e.g. presentation → application → domain → infrastructure).

## Drill — do this alone

Take an app with no structure (routes call SQL and format HTML in the same function). Split
into layers: **domain** (rules, no I/O), **application** (orchestration), **infrastructure**
(I/O), **presentation** (I/O format). Enforce that the domain imports **nothing** from
infrastructure.

## Done when

- [ ] I can name each layer's concern in one sentence.
- [ ] Dependency arrows flow in one direction only (no upward imports).
- [ ] The domain layer has **zero** framework/DB/HTTP imports.
- [ ] I can swap the infrastructure implementation without touching the domain.

## Reflection

- How many layers is *too many* for this size? Where did a layer just forward calls?
- Did I enforce the rule mechanically (module layout / lint) or just by convention?

## Theory & resources

- Hexagonal / ports-and-adapters; clean/onion architecture.
- Resources: *Clean Architecture*, *Implementing DDD*.
