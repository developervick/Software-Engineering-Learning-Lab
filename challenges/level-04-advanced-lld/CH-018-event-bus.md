# CH-018 — Event Bus

- **Challenge ID:** CH-018
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–5 hours
- **Combines:** observer/events · extensibility & plugin seams · DIP · OCP · concurrency basics · error handling
- **Prereqs (gates):** [`../../curriculum/03-design-patterns/11-observer.md`](../../curriculum/03-design-patterns/11-observer.md) ·
  [`../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md`](../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md) ·
  [`../../curriculum/02-solid/05-dip.md`](../../curriculum/02-solid/05-dip.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md)

## Why this problem

An event bus is the canonical **extensibility** exercise: new subscribers appear without the publisher
ever changing. But it also drags in the hard questions — delivery guarantees, isolation of failing
handlers, and ordering — that separate a toy from a design you can defend.

## Requirements (deliberately a little ambiguous)

Provide a **publish/subscribe** bus.

- **Publishers** emit events (typed); **subscribers** register interest in an event type.
- A published event is delivered to **all** matching subscribers.
- A subscriber that **throws** must not prevent other subscribers from receiving the event.
- Subscribers can **unsubscribe**.
- The caller of `publish` receives a summary of what happened (delivered, failed, count).

## Deliberate ambiguities — YOU decide and justify

1. **Sync vs async:** is delivery synchronous within `publish`, or handed to a queue/thread pool? What
   does the caller learn in each case?
2. **Guarantees:** at-most-once, at-least-once, or best-effort? What happens to a failed handler's
   event — dropped, retried, or dead-lettered? Define "delivery" for this scope.
3. **Ordering:** are events delivered to a subscriber in publish order? Is that a promise you can
   keep across types/handlers?
4. **Type matching:** exact type only, or base-type/hierarchy matching (subscriber to `DomainEvent`
   gets all)? Who owns that rule?
5. **Isolation & failure:** does one slow handler block others? What's the blast radius of a bad
   subscriber?

## Constraints

- **In-memory only**, single process.
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the bus, subscription registry, and the delivery model.
3. **Implementation.**
4. **Tests** for multi-subscriber delivery, a throwing subscriber isolated from the rest, unsubscribe,
   and the ordering promise you chose.
5. **Explanation** — your delivery/guarantee model, and what you'd change to make it a durable,
   cross-process bus.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: publishers decoupled from subscribers, failing handlers isolated, and a stated,
  honest delivery guarantee.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-018/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
