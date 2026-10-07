# CH-027 — Notification Delivery (with Dead-Letter)

- **Challenge ID:** CH-027
- **Level:** 5 (system design + implementation)
- **Type:** Design + Implementation + Failure
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** queue · retries · dead-letter · observability · idempotency · failure handling
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/04-lld-topics/03-layering.md`](../../curriculum/04-lld-topics/03-layering.md) ·
  [`../../curriculum/02-solid/05-dip.md`](../../curriculum/02-solid/05-dip.md)

## Why this problem

Delivery is where "it worked on my machine" meets **flaky providers** and **duplicate messages**. The
core skill is designing a **retry-then-give-up** path with a **dead-letter** bucket so nothing is lost
silently, while keeping **duplicate delivery** from annoying the user twice.

## Requirements (deliberately a little ambiguous)

Deliver notifications reliably.

- Notifications are queued and delivered by a **provider** behind an interface.
- A delivery that fails transiently is **retried** with backoff.
- After a limit, the message moves to a **dead-letter** collection.
- The system exposes **metrics** (queued, delivered, retrying, dead-lettered).
- A **flaky provider** and **duplicate messages** can both be injected for testing.

## Deliberate ambiguities — YOU decide and justify

1. **Retry vs give-up:** which failures are retryable? Define the taxonomy explicitly.
2. **Dead-letter:** where do dead letters live, and how (or **when**) are they **replayed**?
3. **Dedup:** how do you avoid double-delivering the same notification, and does that ever block a
   legitimate resend?
4. **Ordering:** is per-recipient ordering promised? What does that cost?
5. **Provider limits:** if the provider rate-limits you, is that a retry, a delay, or a shed?

## Constraints

- **In-memory only**; **deterministic driver**; providers are fakes. **No real networks.**
- **No third-party dependencies.**
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (drive ticks in tests, including faults).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — queue, worker, provider boundary, retry policy, and dead-letter.
3. **Implementation** with injectable flakiness and duplicates.
4. **Tests** for the happy path, retry-then-succeed, retry-exhausted→dead-letter, and a duplicate that
   does not double-deliver.
5. **Explanation** — your failure taxonomy, dead-letter replay stance, and what you'd change for real
   providers.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: nothing is lost silently, retries are bounded, and duplicates are handled deliberately.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-027/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
