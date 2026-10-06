# Testability & seams

- **Track:** lld-topics
- **Prereqs:** dependency injection
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Design for **seams** — points where you can substitute a test double without hacks. Hard to
test usually means hard-coupled.

## Drill — do this alone

Take an untestable class (does `new Date()`, `random()`, `open(file)`, or a network call
inline). Introduce **seams** (inject a `Clock`, a `Random`, a storage interface), then write a
fast, deterministic unit test that covers a tricky branch.

## Done when

- [ ] The test runs **deterministically** (no real clock, no network, no flakiness).
- [ ] No test-only branches (`if testing:`) were added to production code.
- [ ] The seam is a **domain abstraction** (`Clock.now()`), not a leaky framework hook.
- [ ] The test documents a *behavior*, not an implementation detail.

## Reflection

- Which dependencies *should* the test use for real (pure logic) vs fake (I/O, time)?
- Did adding the seam reveal a design smell I should fix instead?

## Theory & resources

- "Test-induced damage" — avoid bending the design only to be testable; fix coupling instead.
- Resources: *Working Effectively with Legacy Code* (seams), *TDD by Example*.
