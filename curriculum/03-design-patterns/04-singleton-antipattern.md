# Singleton *(anti-pattern talk)*

- **Track:** design-patterns · creational
- **Prereqs:** fundamentals 2, 4; SOLID DIP
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Understand the **global single instance** pattern — then understand, concretely, why it is
usually a trap and how dependency injection replaces it.

## Drill — do this alone

1. Implement a classic `Singleton` (one lazily-created global instance).
2. Then **prove it hurts** by writing a test that is hard because of it: the test cannot
   substitute a fake, and state leaks between tests.
3. **Refactor it away**: make the dependency injectable, and show the test becomes easy.

## Done when

- [ ] I implemented a working singleton.
- [ ] I wrote a test that is awkward *because* of the singleton (global state / no seam).
- [ ] I replaced it with an injected dependency and the test got simpler.
- [ ] I can list ≥3 concrete problems: hidden dependencies, global mutable state, hard to
      test, hard to run in parallel, violates DIP.
- [ ] I can name the *rare* cases where a singleton is acceptable (e.g. a stateless
      config/logging facade with no mutable lifecycle concerns).

## When NOT to use it

- Almost always, in application code you write. Prefer **one instance managed by your
  composition root / DI container** instead of a self-managing global.

## Reflection

- "One instance" and "globally reachable" are different. Which did I actually need?
- How would I give this same "only one" guarantee via DI?

## Theory & resources

- The complaint is rarely "one instance exists"; it's "everything can reach it secretly."
- Resources: *Clean Code*, *Dependency Injection Principles* (Seemann), industry post-mortems
  on singletons.
