# CH-017 — Task Scheduler

- **Challenge ID:** CH-017
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–5 hours
- **Combines:** scheduling · concurrency basics · state machines · observer · error handling
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/11-observer.md`](../../curriculum/03-design-patterns/11-observer.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

Schedulers force you to make **ordering** and **failure** explicit: which task runs next, how many run
at once, and what happens when one throws. It's also a gentle on-ramp to the queue/pipeline ideas of
Level 5.

## Requirements (deliberately a little ambiguous)

Accept **tasks** and run them when due.

- A task has an **id**, a **run-at time**, and a **priority**.
- The scheduler runs tasks that are **due**, with a bounded **concurrency**.
- A task that fails may be **retried** a limited number of times.
- Each task has a **status** (pending → running → done / failed / retrying).
- Observers can be **notified** of status changes.

## Deliberate ambiguities — YOU decide and justify

1. **Execution model:** real threads/timers, `asyncio`, or a **deterministic tick loop** you drive in
   tests? Justify for correctness and testability.
2. **Ordering:** among due tasks, is it strict priority, FIFO within priority, or something else? Define
   ties.
3. **Retry policy:** fixed, linear, or exponential backoff? Max attempts? Who decides?
4. **Concurrency limit:** what happens when all worker slots are busy and a task is due?
5. **Dependencies:** do tasks depend on other tasks? If so, who owns readiness — and is that worth the
   complexity now?

## Constraints

- **In-memory only**; clock injectable/tickable; no external scheduler.
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (drive ticks/loops in tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — tasks, the scheduler, the retry policy, and the status model.
3. **Implementation.**
4. **Tests** for due-time firing, priority ordering, retry-then-succeed, retry-exhausted, and the
   concurrency bound.
5. **Explanation** — your execution model, retry policy, and what you'd change to persist tasks.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a deterministic, testable execution model, explicit ordering, and a well-defined
  failure/retry path.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-017/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
