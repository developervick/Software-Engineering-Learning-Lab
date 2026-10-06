# Concurrency basics

- **Track:** lld-topics
- **Prereqs:** immutability, encapsulation
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Recognize **shared mutable state** as the root problem, and know basic defenses: immutability,
confinement, synchronization, atomic operations.

## Drill — do this alone

Write a `Counter` with `increment()` and a `get()`. Start N threads/workers incrementing it
M times. Observe the **lost updates** (result < N·M). Then fix it **three ways**:
(1) synchronize/mutex, (2) atomic primitive, (3) no shared state (each worker returns a
partial; sum at the end). Compare.

## Done when

- [ ] I reproduced a data race (with a test or by reasoning).
- [ ] I fixed it with at least two approaches and can explain each.
- [ ] I can name which approach I'd prefer and why (throughput, simplicity, correctness).
- [ ] I can state the invariant that was being violated.

## Reflection

- When is "avoid shared mutable state" better than "lock it"?
- What new failure modes does locking introduce (deadlock, contention)?

## Theory & resources

- Happens-before, atomicity, visibility; thread-confinement.
- Resources: *Java Concurrency in Practice*, *The Art of Multiprocessor Programming* (intro).
