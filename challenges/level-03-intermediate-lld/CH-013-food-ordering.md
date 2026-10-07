# CH-013 — Food Ordering

- **Challenge ID:** CH-013
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–4 hours
- **Combines:** state machines · observer · command · invariants · error handling
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/11-observer.md`](../../curriculum/03-design-patterns/11-observer.md) ·
  [`../../curriculum/03-design-patterns/13-command.md`](../../curriculum/03-design-patterns/13-command.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

Restaurant orders move through **states** with **rules about which moves are legal**, and the kitchen
and the customer both want to be **notified**. The meat is: who owns transition legality, and how do
observers react without coupling the order to them.

## Requirements (deliberately a little ambiguous)

Model an order that flows from placement to service.

- An **order** contains **items** and moves through stages such as
  placed → preparing → ready → served (and a terminal **cancelled**).
- Only **some** transitions are legal at each stage.
- **Observers** (kitchen display, customer notifier) are informed when an order changes stage.
- A user can **place** an order and later **cancel** it, if the rules allow.

## Deliberate ambiguities — YOU decide and justify

1. **Legality owner:** where do the legal transitions live — a table on the order, a separate state
   object, or the service? Justify against a growing set of states.
2. **Notifications:** synchronous observer calls or queued messages? What happens if an observer
   throws?
3. **Partial progress:** can items become ready at different times, or is readiness whole-order?
4. **Cancellation:** which stages allow it, and what does cancelling mean (refund, discard food)?
5. **Command history:** do you model each action as a **command** so it can be logged/undone? Where's
   the line between helpful and over-engineered here?

## Constraints

- **In-memory only**; observers are fakes/loggers.
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the order state machine, observers, and the transition boundaries.
3. **Implementation.**
4. **Tests** for legal and illegal transitions and for observer notification on transitions.
5. **Explanation** — your legality model, observer-decoupling choice, and what you'd change to add a
   new stage.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: one clear owner of transition legality, illegal transitions rejected cleanly, and
  observers that can be added/removed without editing the order.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-013/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
