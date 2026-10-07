# CH-009 — Simple Booking

- **Challenge ID:** CH-009
- **Level:** 2 (SOLID & basic LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–3 hours
- **Combines:** responsibilities · value objects · invariants · validation · a light state machine
- **Prereqs (gates):** [`../../curriculum/01-fundamentals/01-responsibilities-and-cohesion.md`](../../curriculum/01-fundamentals/01-responsibilities-and-cohesion.md) ·
  [`../../curriculum/01-fundamentals/06-value-objects-vs-entities.md`](../../curriculum/01-fundamentals/06-value-objects-vs-entities.md) ·
  [`../../curriculum/01-fundamentals/05-validation-and-fail-fast.md`](../../curriculum/01-fundamentals/05-validation-and-fail-fast.md) ·
  [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md)

## Why this problem

Booking is where **time** and **ownership** collide. The interesting decisions are the *overlap rule*
and *who owns "is this slot free?"* — get them wrong and you double-book under the simplest of races.

## Requirements (deliberately a little ambiguous)

Book a **resource** (room, table, court, …) for a **time slot**.

- The system knows the resources and their booked slots.
- A user can **book** a resource for a start/end time.
- A user can **cancel** a booking.
- The system can **list available slots** for a resource on a day.
- The same resource must **never** be double-booked for overlapping times.

## Deliberate ambiguities — YOU decide and justify

1. **Time range rule:** are ranges half-open `[start, end)`? Do back-to-back bookings (end == next
   start) conflict or not? State and justify the rule.
2. **Availability owner:** which object answers "is this resource free?" — the resource, the booking
   service, or a schedule? Justify.
3. **Cancellation policy:** is cancel always allowed? Any cutoff? Does a cancelled slot become free?
4. **Booking lifecycle:** what states (held → confirmed → cancelled) exist, and who may transition?
5. **Holds:** do you need a temporary "hold" before confirming? In scope or not — and why?

## Constraints

- **In-memory only**; ignore time zones (pick one, state it).
- **No third-party dependencies.**
- Roughly **120–250 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — resources, bookings, and who enforces the overlap invariant.
3. **Implementation.**
4. **Tests** including two bookings that overlap (rejected) and back-to-back (per your rule).
5. **Explanation** — your overlap rule, and what you'd change for a distributed, multi-process
   booking system.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a crisp, defensible overlap rule and a single owner of the "no double-booking"
  invariant.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-009/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
