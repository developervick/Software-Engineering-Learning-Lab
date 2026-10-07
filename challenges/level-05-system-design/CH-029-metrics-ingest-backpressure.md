# CH-029 — Metrics Ingest (Backpressure)

- **Challenge ID:** CH-029
- **Level:** 5 (system design + implementation)
- **Type:** Design + Implementation + Failure + Trade-off
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** concurrency · queues · backpressure · observability · failure handling · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md) ·
  [`../../curriculum/04-lld-topics/10-tradeoff-analysis.md`](../../curriculum/04-lld-topics/10-tradeoff-analysis.md) ·
  [`../../curriculum/01-fundamentals/05-validation-and-fail-fast.md`](../../curriculum/01-fundamentals/05-validation-and-fail-fast.md)

## Why this problem

Ingest is where rate **exceeds** capacity, and the grown-up answer is not "buffer forever" but a
**degradation policy** you chose on purpose. This challenge is about behaving predictably under
overload instead of collapsing.

## Requirements (deliberately a little ambiguous)

Ingest a high rate of **metrics** without falling over.

- Producers submit metric samples faster than the downstream can accept.
- A **bounded buffer** sits between producers and the downstream.
- The system **aggregates** samples (e.g. per key/window) before flushing downstream.
- Under overload it follows a defined **degradation policy** (drop, sample, or shed by priority).
- It exposes **health/metrics** (throughput, dropped, buffer depth).

## Deliberate ambiguities — YOU decide and justify

1. **Buffer policy:** bound size and behavior at the limit — block producers, drop oldest, drop newest,
   or reject with a signal? Justify.
2. **Degradation:** what do you drop first? Is there a notion of **priority** or a "canary" metric that
   must never be dropped?
3. **Aggregation:** what's the window and key? What's lost by aggregating (and is that acceptable for
   metrics vs, say, audit logs)?
4. **Recovery:** after an overload spike, how does the system return to normal without a second spike?
5. **Observability:** what must the system report so an operator can tell "we're shedding, and why"?

## Constraints

- **In-memory only**; a **deterministic driver** to simulate bursts. **No real networks.**
- **No third-party dependencies.**
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (drive load in tests, including an overload burst).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — producers, buffer, aggregator, downstream boundary, and the shed policy.
3. **Implementation.**
4. **Tests** for steady state, a burst that triggers dropping per your policy, and recovery afterward.
5. **Explanation** — your degradation policy and its trade-offs, and what you'd change for a
   multi-consumer, persisted pipeline.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a bounded, explicit overload policy; no unbounded memory growth; and observability that
  explains the shedding.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-029/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
