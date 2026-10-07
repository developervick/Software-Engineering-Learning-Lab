# CH-010 — Parking Lot

- **Challenge ID:** CH-010
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–4 hours
- **Combines:** state machines · entities & invariants · strategy (pricing) · composition · concurrency basics
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/01-fundamentals/06-value-objects-vs-entities.md`](../../curriculum/01-fundamentals/06-value-objects-vs-entities.md)

## Why this problem

A parking lot looks like lists of spots, but it is really about **assignment**, **time**, and
**invariants under repetition**: never hand the same spot to two cars, compute a fair fee, and stay
sane when several vehicles move at once.

## Requirements (deliberately a little ambiguous)

Model a parking lot that issues **tickets** and charges on exit.

- The lot has multiple **floors** and spots in **sizes** (motorcycle / car / truck).
- On **entry**, a vehicle is assigned a suitable free spot and gets a **ticket**.
- On **exit**, the ticket's fee is computed from **duration** and **vehicle/spot type**, and the spot
  is freed.
- The system can report **availability** (free spots, by size or floor).
- A spot must **never** be assigned to two active tickets.

## Deliberate ambiguities — YOU decide and justify

1. **Assignment policy:** which free spot does a vehicle get (first-fit, best-fit, by floor)? Can a
   truck use a larger spot; can a car use a truck spot? Where does this policy live?
2. **Pricing granularity:** per hour, per started hour, rounding, free first N minutes — and who owns
   the pricing rule so a new scheme doesn't edit the lot?
3. **Lost ticket / overstay:** what fee applies? What if the spot was never freed?
4. **Concurrency:** two entries at the same time must not get the same spot — how is that guaranteed?
5. **Full lot:** what does entry do when no suitable spot exists?

## Constraints

- **In-memory only.** No UI, DB, or network. Time may be **injected** (a clock) so fees are testable.
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — spot/floor/ticket/vehicle objects and the assignment flow.
3. **Implementation.**
4. **Tests** for assignment, fee computation, availability, full lot, and a same-spot race.
5. **Explanation** — your assignment + pricing choices and what you'd change for multiple gates and
   persisted state.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: the "no double-assignment" invariant, a swappable pricing rule, and honest handling of
  the full-lot and concurrency cases.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-010/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
