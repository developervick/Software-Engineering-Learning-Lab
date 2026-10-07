# CH-026 — Order Pipeline (Retries & Idempotency)

- **Challenge ID:** CH-026
- **Level:** 5 (system design + implementation)
- **Type:** Design + Implementation + Failure
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~5–7 hours
- **Combines:** command · queue · retries · idempotency · failure handling · observability · layering
- **Prereqs (gates):** [`../../curriculum/03-design-patterns/13-command.md`](../../curriculum/03-design-patterns/13-command.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/04-lld-topics/03-layering.md`](../../curriculum/04-lld-topics/03-layering.md)

## Why this problem

This is the "full slice" of an order flow with the parts that make real systems hard: a **multi-step
pipeline**, **retries**, **duplicate delivery**, and a **downstream that fails**. The design goal is to
make repeated processing safe and to know exactly what happened for any order.

## Requirements (deliberately a little ambiguous)

Process orders through a pipeline.

- An order enters and flows through steps such as
  **validate → charge payment → reserve inventory → fulfill**.
- Each step may **fail transiently** and be **retried** with a policy.
- Messages may be **delivered more than once** — reprocessing must be **safe**.
- The system exposes **status** and **metrics** per order and per step.
- A downstream dependency can be made **slow or failing** for testing.

## Deliberate ambiguities — YOU decide and justify

1. **Idempotency model:** what key makes a step idempotent, where is it stored, and what does a repeat
   return?
2. **Retry policy:** backoff shape, max attempts, and the criteria for "retry" vs "give up" (transient
   vs permanent failure).
3. **Partial failure:** if payment succeeds but inventory fails, do you **compensate** (refund) or
   **resume** from where you left off? Justify.
4. **Ordering/parallelism:** are steps strictly sequential, or can some run concurrently? What do you
   promise?
5. **Observability:** what do you log/emit so a failed order is diagnosable after the fact?

## Constraints

- **In-memory only**; a **deterministic driver** (ticks) rather than real infra. **No real networks.**
- **No third-party dependencies.**
- Roughly **300–500 lines**.
- Must be **exercisable without a UI** (drive the pipeline in tests, including a fault).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code (including the failure taxonomy).
2. **Design sketch** — the pipeline steps, the retry/idempotency seams, and the status model.
3. **Implementation** with an injectable fault.
4. **Tests** for the happy path, a transient failure that retries then succeeds, a duplicate message
   staying safe, and a permanent failure path.
5. **Explanation** — your idempotency + partial-failure strategy and the trade-offs you accepted.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: duplicate-safe steps, a clear retry/give-up taxonomy, and a defensible answer to
  partial failure.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-026/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
