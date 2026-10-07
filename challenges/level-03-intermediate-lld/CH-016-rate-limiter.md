# CH-016 — Rate Limiter

- **Challenge ID:** CH-016
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–4 hours
- **Combines:** concurrency basics · strategy (algorithms) · value objects/immutability · invariants · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/04-lld-topics/05-immutability.md`](../../curriculum/04-lld-topics/05-immutability.md) ·
  [`../../curriculum/04-lld-topics/10-tradeoff-analysis.md`](../../curriculum/04-lld-topics/10-tradeoff-analysis.md)

## Why this problem

A rate limiter is a small piece of code with a large design surface: the **algorithm** (fixed vs
sliding window vs token bucket) is a strategy, the **clock** is a dependency, and the whole thing is
easily wrong under concurrency.

## Requirements (deliberately a little ambiguous)

Limit requests **per key** (e.g. per client/user).

- Given a key, decide **allow / deny** for a request at the current time.
- The limiter is configured with a **rate** (limit + window), per key or globally.
- At least **two algorithms** must be selectable (e.g. fixed window and token bucket).
- The limiter reports **remaining** allowance (for headers).

## Deliberate ambiguities — YOU decide and justify

1. **Algorithm choice:** implement two and be ready to argue **when each is right**. What's the burst
   behavior at a window boundary?
2. **Clock:** real wall-clock vs an **injected** clock? Why does that matter for testability?
3. **Concurrency:** two allowed checks in the same tick — can they both pass and over-allow? What
   guarantees the invariant?
4. **Per-key memory:** when are unused keys cleaned up? What's the memory trade-off?
5. **Fail mode:** if the limiter itself errors, deny (fail-closed) or allow (fail-open)? Justify.

## Constraints

- **In-memory only**; single process. Provide a way to **drive time** deterministically.
- **No third-party dependencies.**
- Roughly **150–300 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the limiter, the algorithm seam, and the clock dependency.
3. **Implementation** (both algorithms).
4. **Tests** — the exact-boundary cases and a same-tick double-check.
5. **Explanation** — your algorithm trade-off, and what you'd change for a **distributed** limiter.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a swappable algorithm, an injected clock, and a correct answer to "can this over-allow
  under concurrency?".

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-016/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
