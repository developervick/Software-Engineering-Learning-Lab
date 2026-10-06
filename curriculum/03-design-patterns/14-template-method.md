# Template Method

- **Track:** design-patterns · behavioral
- **Prereqs:** fundamentals 3 (inheritance), SOLID OCP
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Define the **skeleton** of an algorithm in a base method, letting subclasses override specific
steps without changing the overall structure.

## Drill — do this alone

You import data from CSV and JSON. The flow is identical — `read → parse → validate → store` —
but `parse` differs. Put the fixed skeleton in a base class and let each format override only
the step it changes.

## Done when

- [ ] The skeleton method is final/hard-to-break (steps cannot be reordered by subclasses).
- [ ] Subclasses override only the variable step(s).
- [ ] Adding a new format means a new subclass, not editing the skeleton.
- [ ] I can name which steps are "hooks" (optional) vs "required".

## When NOT to use it

- There's only one implementation, or the steps aren't actually fixed.
- **Composition would be better** — if the varying step can be a strategy object, prefer that
  over an inheritance hierarchy (this is a common over-use).

## Reflection

- Why is this pattern often replaced by Strategy? When does inheritance genuinely win?
- Did I use a protected method where an abstraction would be cleaner?

## Theory & resources

- Resources: *Design Patterns* (GoF, Template Method), *Head First Design Patterns*.
