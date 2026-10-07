# CH-014 — Inventory

- **Challenge ID:** CH-014
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–4 hours
- **Combines:** invariants · value objects · observer/events · concurrency basics · error handling
- **Prereqs (gates):** [`../../curriculum/01-fundamentals/05-validation-and-fail-fast.md`](../../curriculum/01-fundamentals/05-validation-and-fail-fast.md) ·
  [`../../curriculum/03-design-patterns/11-observer.md`](../../curriculum/03-design-patterns/11-observer.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

Inventory is the single most common place **"never go negative"** is silently violated. The lesson
is to name the invariants precisely (on-hand vs reserved vs available) and to decide, deliberately,
what happens at the boundary.

## Requirements (deliberately a little ambiguous)

Track **stock** per SKU as it is received, reserved, shipped, and adjusted.

- Each SKU has a **quantity** that is changed by **receive**, **ship**, and **adjust** operations.
- The system supports **reservations** for pending orders (hold stock before shipping).
- The system emits a **low-stock** notification when stock crosses a threshold.
- Quantities must **never** go negative, and reservations must never exceed what exists.

## Deliberate ambiguities — YOU decide and justify

1. **Three numbers:** do you distinguish **on-hand**, **reserved**, and **available**? Which does the
   low-stock rule look at, and which does shipping decrement?
2. **Negative rule:** reject the operation, or allow backorder and track a deficit? Pick one and
   justify for a shop vs a warehouse.
3. **Concurrency:** two shipments of the same SKU at once must not oversell — what guarantees that?
4. **Reservation lifecycle:** can a reservation be released/expired? Who owns that transition?
5. **Units/batches:** do you need multiple units or lot numbers per SKU, or is a single count enough?
   Justify *not* adding complexity you don't need.

## Constraints

- **In-memory only**; thresholds/configurable values allowed.
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the SKU/stock model and where the invariants are enforced.
3. **Implementation.**
4. **Tests** for receive/ship/adjust, a reservation, the low-stock event, and a would-go-negative case.
5. **Explanation** — your on-hand/reserved/available model and what you'd change for multi-warehouse
   stock.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: precisely stated invariants, a single enforcement point, and a deliberate negative-stock
  policy.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-014/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
