# CH-005 — Pricing Strategies

- **Challenge ID:** CH-005
- **Level:** 2 (SOLID & basic LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–3 hours
- **Combines:** strategy · OCP · immutability/value objects · SRP
- **Prereqs (gates):** [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/02-solid/02-ocp.md`](../../curriculum/02-solid/02-ocp.md) ·
  [`../../curriculum/01-fundamentals/06-value-objects-vs-entities.md`](../../curriculum/01-fundamentals/06-value-objects-vs-entities.md) ·
  [`../../curriculum/04-lld-topics/05-immutability.md`](../../curriculum/04-lld-topics/05-immutability.md)

## Why this problem

Pricing rules are where `if/else` chains metastasize. The skill is to make the **algorithm swappable**
while keeping each rule small and testable — and to recognise when a rule is *not* worth a class.

## Requirements (deliberately a little ambiguous)

Compute the price of a **basket** under different pricing rules.

- Implement at least **three** rules: regular price, a percentage discount, and a tiered/volume rule
  (or buy-one-get-one).
- A caller can pick which rule(s) apply.
- Adding a **new rule** must not edit existing rules.
- The result must be a **stable money value** (no drifting floats, no currency mixing).

## Deliberate ambiguities — YOU decide and justify

1. **Composition:** can multiple rules apply at once, and in what **order**? Does order change the
   result? Who owns the ordering?
2. **Rounding:** where does rounding happen so child totals still sum to the parent total?
3. **Empty/edge baskets:** empty basket, zero price, a discount larger than the total.
4. **Immutability:** are rules and the resulting price immutable? What breaks if they aren't?
5. **Data vs behavior:** should a rule read its parameters from config/data, or be pure code?

## Constraints

- **In-memory only**, no persistence/UI/network.
- **No third-party dependencies.**
- Roughly **120–220 lines**; keep each rule small.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — what is stable vs what varies across rules.
3. **Implementation.**
4. **Tests** for each rule and for the combined/ordered case.
5. **Explanation** — when a plain function beats a strategy class here, and what you'd change to add
   a rule that depends on customer history.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: whether "add a rule" is truly a new-file change, and whether composition/ordering is
  reasoned about rather than accidental.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-005/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
