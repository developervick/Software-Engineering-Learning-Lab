# CH-012 — Library System

- **Challenge ID:** CH-012
- **Level:** 3 (intermediate LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–4 hours
- **Combines:** entities vs value objects · state machines · strategy (loan rules) · error handling · invariants
- **Prereqs (gates):** [`../../curriculum/01-fundamentals/06-value-objects-vs-entities.md`](../../curriculum/01-fundamentals/06-value-objects-vs-entities.md) ·
  [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

The **title-vs-copy** distinction is the heart of this domain and a recurring modeling trap: a
"book" the user searches is not the physical object that gets borrowed. Get that split right and
loans, availability, and fees fall into place; get it wrong and everything is confused.

## Requirements (deliberately a little ambiguous)

Model a lending **library**.

- The library holds **titles** and physical **copies**.
- **Members** can **borrow** and **return** a copy.
- A copy can be **out** to at most one member at a time.
- There are **loan periods and limits**; overdue returns accrue a **fee**.
- The system can **search** the catalog and show **availability**.

## Deliberate ambiguities — YOU decide and justify

1. **Title vs copy:** how are they modeled and linked? Which one lives in the catalog search results?
2. **Loan rules:** loan length, max concurrent loans per member, renewals — and where these live so
   the rule can change without editing `Member` or `Copy`.
3. **Overdue fees:** flat vs per-day; is there a cap? When is the fee computed (on return only)?
4. **Reservations/holds:** in scope? If a title has no free copy, what happens?
5. **Unhappy paths:** losing a book, a suspended member, borrowing a copy already out.

## Constraints

- **In-memory only**; a fixed "today" may be **injected** so overdue math is testable.
- **No third-party dependencies.**
- Roughly **200–350 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — titles, copies, members, loans, and the loan-rule seam.
3. **Implementation.**
4. **Tests** for borrow, return, availability, limits, and an overdue fee.
5. **Explanation** — the title/copy decision, the loan-rule seam, and what you'd change to add
   reservations.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: the title-vs-copy model, a pluggable loan rule, and consistent handling of the unhappy
  paths.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-012/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
