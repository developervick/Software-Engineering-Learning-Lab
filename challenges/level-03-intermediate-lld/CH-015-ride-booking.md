# CH-015 — Ride Booking

- **Challenge ID:** CH-015
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–5 hours
- **Combines:** state machines · strategy (matching) · concurrency basics · observer · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/04-lld-topics/10-tradeoff-analysis.md`](../../curriculum/04-lld-topics/10-tradeoff-analysis.md)

## Why this problem

Ride-hailing composes nearly everything at this level: a **trip lifecycle**, a **matching policy**, a
**driver availability invariant** (one driver, one active trip), and **failure** when no one accepts.
It rewards a design that keeps these seams separate.

## Requirements (deliberately a little ambiguous)

Match riders to drivers and track a trip.

- A **rider** requests a trip; the system **matches** a nearby available **driver**.
- A trip moves through states such as
  requested → matched → driver-arriving → in-progress → completed (or → cancelled).
- The driver may **accept/decline** a match request.
- The system computes a **fare** from distance and/or time.
- A driver can have **at most one** active trip at a time.

## Deliberate ambiguities — YOU decide and justify

1. **Matching policy:** nearest driver, best-rated, first-available? Where does the policy live so it
   can be swapped? How far does a driver have to be to be considered?
2. **Accept/decline:** after a decline, try the next driver or fail immediately? How many attempts?
3. **Fare model:** distance-only, time-only, or both, plus base/minimum and any surge? Who owns the
   fare rule?
4. **Cancellation:** who may cancel at which states, and is there a fee? Does it free the driver?
5. **No driver available:** what does the rider see, and how long do you wait?

## Constraints

- **In-memory only**; "nearby" may be a simple distance on coordinates. Time may be **injected**.
- **No third-party dependencies.**
- Roughly **250–400 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — riders, drivers, trips, the matcher, and the fare policy.
3. **Implementation.**
4. **Tests** for matching, accept/decline, the trip lifecycle, fare, and a driver's one-active-trip
   invariant.
5. **Explanation** — your matching + fare choices, failure handling, and the trade-offs you accepted.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a swappable matcher, a swappable fare rule, correct lifecycle states, and a truthful
  driver-availability invariant.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-015/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
