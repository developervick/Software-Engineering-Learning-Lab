# CH-028 — Distributed Rate Limiter

- **Challenge ID:** CH-028
- **Level:** 5 (system design + implementation)
- **Type:** Design + Implementation + Failure + Trade-off
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** concurrency · strategy (algorithms) · shared-state abstraction · failure handling · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md) ·
  [`../../curriculum/04-lld-topics/10-tradeoff-analysis.md`](../../curriculum/04-lld-topics/10-tradeoff-analysis.md)

## Why this problem

CH-016 limited a single process; real limiters must be **shared** across instances. Here the hard
questions are about the **shared store** (atomicity, latency, partial failure) and the **policy when
it's unavailable** — a decision with real product consequences.

## Requirements (deliberately a little ambiguous)

Enforce a **global** rate limit across multiple app instances.

- Multiple "instances" share a limiter state via a **store abstraction**.
- An atomic **check-and-consume** decides allow/deny per key.
- Provide an in-memory store **and** a "slow/failing" store to exercise failure.
- The limiter reports **remaining** and behaves **definedly** when the store is down.

## Deliberate ambiguities — YOU decide and justify

1. **Shared-state algorithm:** which algorithm do you put in the shared store (fixed window, sliding
   window, token bucket), and how do you make check-and-consume **atomic**?
2. **Fail mode:** if the store is down, **fail-open** (allow) or **fail-closed** (deny)? Justify with a
   concrete product consequence of each.
3. **Latency:** the store is remote and slow — what do you do (timeout, cache, degrade)? 
4. **Clock & skew:** whose clock wins across instances, and what breaks at window boundaries?
5. **Hot keys:** one key dominates traffic — how does that affect correctness and cost?

## Constraints

- **In-memory store** simulating a shared backend, behind an interface. **No real networks.**
- **No third-party dependencies.**
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (script or tests, including a store-down run).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the limiter, the store abstraction, and the failure policy.
3. **Implementation** with an injectable slow/failing store.
4. **Tests** for allow/deny, the atomicity property, and the store-down path per your fail-mode choice.
5. **Explanation** — the fail-open vs fail-closed trade-off, atomicity approach, and what you'd change
   for a real Redis-like store.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: an atomic check-and-consume, a deliberate fail-mode, and honest reasoning about latency
  and clock skew.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-028/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
