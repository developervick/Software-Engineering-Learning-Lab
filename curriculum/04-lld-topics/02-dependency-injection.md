# Dependency injection

- **Track:** lld-topics
- **Prereqs:** coupling & direction, SOLID DIP
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Supply an object's collaborators from **outside** rather than letting it create them — as a
technique, not a framework.

## Drill — do this alone

Take a class that constructs its own dependencies. Refactor it to **constructor injection**.
Then do it a second time with **method injection** for a dependency that's only needed by one
method. Write a single **composition root** that wires everything, and a test that injects a
fake.

## Done when

- [ ] The class receives dependencies via constructor (no `new`/direct-instantiation inside).
- [ ] One dependency is supplied per-method where that's more appropriate.
- [ ] There is exactly one place that decides *which* concretes to use.
- [ ] A unit test passes a fake without any global/monkey-patching tricks.

## Reflection

- Constructor vs method vs property injection — when is each the right tool?
- How is DI different from a DI *framework*? (The framework is optional.)

## Theory & resources

- Resources: *Dependency Injection Principles, Practices, and Patterns* (Seemann).
