# CH-023 — Job Processing System

- **Challenge ID:** CH-023
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** concurrency basics · command · state machines · error handling · idempotency · layering
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/03-design-patterns/13-command.md`](../../curriculum/03-design-patterns/13-command.md) ·
  [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

This is a mini worker/queue system — the shape behind almost every backend. It forces you to make
**at-least-once delivery** explicit and then confront the question it raises: what makes processing a
**duplicate** job safe?

## Requirements (deliberately a little ambiguous)

Enqueue **jobs** and process them with **workers**.

- Jobs are submitted and processed by a bounded number of **workers**.
- A failing job is **retried** with a policy; after a limit it moves to a **dead-letter** collection.
- Each job has a **status** (queued → running → succeeded / failed / dead-lettered).
- The system exposes basic **metrics** (queued, in-flight, succeeded, failed).

## Deliberate ambiguities — YOU decide and justify

1. **Execution model:** real threads, `asyncio`, or a deterministic driver you tick in tests? Justify
   for testability.
2. **Ordering:** FIFO, priority, or unordered? What do you actually promise?
3. **Delivery guarantee:** at-least-once means jobs can repeat. How do you make a **re-processed** job
   safe (idempotency)?
4. **Retry policy:** backoff shape, max attempts, and what "dead-letter" means.
5. **Backpressure/shutdown:** what happens when the queue is unbounded? How do workers stop cleanly?

## Constraints

- **In-memory only**; a fake job (e.g. sleeps or throws) is fine.
- **No third-party dependencies.**
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (drive ticks/loops in tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — queue, worker, job state, retry/dead-letter, and the idempotency seam.
3. **Implementation.**
4. **Tests** for normal processing, retry-then-succeed, retry-exhausted→dead-letter, a duplicate job
   staying safe, and metric counts.
5. **Explanation** — your delivery guarantee, idempotency approach, and what you'd change for a
   multi-process queue.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: an honest delivery guarantee, a duplicate-safe design, and a clear failure path to
  dead-letter.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-023/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
