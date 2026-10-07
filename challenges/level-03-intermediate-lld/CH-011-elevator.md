# CH-011 — Elevator

- **Challenge ID:** CH-011
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–5 hours
- **Combines:** state machines · scheduling · observer/events · concurrency basics · invariants
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/11-observer.md`](../../curriculum/03-design-patterns/11-observer.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/01-fundamentals/01-responsibilities-and-cohesion.md`](../../curriculum/01-fundamentals/01-responsibilities-and-cohesion.md)

## Why this problem

Elevators are a compact lesson in **scheduling**: a request arrives, several servers (cars) can serve
it, each car has a state and a direction, and the "best" choice depends on a policy you must make
explicit and testable.

## Requirements (deliberately a little ambiguous)

Control a bank of elevators serving several floors.

- There are **N cars** and **M floors**; each car has a state (idle / moving / doors-open) and a
  direction (up/down).
- **Hall calls** (floor + desired direction) and **cabin calls** (destination floor) can be made.
- The system assigns/executes requests so calls are eventually served.
- The system can report each car's **floor, direction, and pending stops**.

## Deliberate ambiguities — YOU decide and justify

1. **Dispatch policy:** which car takes a hall call (nearest, same-direction-first, round-robin)? Where
   does the policy live so it can be swapped?
2. **Service order within a car:** classic SCAN (sweep up/down) or simplest-first? Define it precisely.
3. **Direction change:** when does a car reverse? What request loses?
4. **Simulation model:** do you need real threads/timers, or a **step/tick** model that is
   deterministic and testable? Justify.
5. **Edge cases:** calls while doors open, a floor with both up and down calls, overload.

## Constraints

- **In-memory only**; prefer a **deterministic tick loop** over real concurrency (state it).
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (drive the tick loop in tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — cars, controller/dispatcher, requests, and the tick loop.
3. **Implementation.**
4. **Tests** that assert cars serve a fixed sequence of calls in a defined order.
5. **Explanation** — your dispatch + ordering policy, worst-case behavior, and what you'd change to
   minimize average wait.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a swappable dispatch policy, a precisely defined service order, and determinism that
  makes the system testable.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-011/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
