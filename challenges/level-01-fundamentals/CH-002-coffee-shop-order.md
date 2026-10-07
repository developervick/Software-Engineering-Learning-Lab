# CH-002 — Coffee Shop Order

- **Challenge ID:** CH-002
- **Level:** 1 (baseline)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~1–2 hours (design + implement + tests)
- **Combines:** classes & objects · responsibilities & cohesion · encapsulation · value objects · validation & fail-fast
- **Prereqs (gates):** [`../../curriculum/01-fundamentals/`](../../curriculum/01-fundamentals/) 00–06
  (classes & objects, responsibilities, encapsulation, composition, interfaces, validation,
  value objects)

## Why this problem

The domain is tiny, which is the point: with no place to hide, every misplaced responsibility shows
up immediately. Watch whether **pricing**, **customization**, and **order totals** each have one clear
home — and whether money is modeled so value is never invented or lost.

## Requirements (deliberately a little ambiguous)

Model a coffee shop that builds drink **orders**.

- A **drink** has a size (e.g. small/medium/large) and zero or more **modifiers**
  (extra shot, oat milk, syrup, …).
- Each size and each modifier has a **price**; a drink's price is derived from them.
- An **order** holds one or more drinks and can report its **total**.
- The shop can **place** an order and later **mark it paid**.
- Invalid input (unknown size, unknown modifier, empty order) must be **rejected clearly**.

## Deliberate ambiguities — YOU decide and justify

1. **Money model:** how do you represent money so totals never drift (integer cents? a value type?)
   and so you can't accidentally add two different currencies?
2. **Customization rule set:** can the same modifier appear twice? Is there a max? Where does that
   rule live — on the drink, the modifier, or a menu?
3. **Price ownership:** who computes a drink's price — the drink, the modifier, or a `Menu`/pricelist
   object? What happens when a menu price changes after a drink was added?
4. **Order lifecycle:** what states does an order move through, and **who** may change them?
5. **Empty / edge cases:** empty order, a drink with no modifiers, a quantity of zero.

## Constraints

- **In-memory only.** No UI, no database, no network.
- **No third-party dependencies.**
- Prefer the **simplest** design that meets the requirements; roughly **100–200 lines**.
- There must be a way to **exercise the flow without a UI** (a script or automated tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the responsibilities of the main objects and how they collaborate. Small.
3. **Implementation.**
4. **Tests** (or a runnable scenario) covering the important behavior and edge cases.
5. **Explanation** — key decisions, trade-offs, and what you'd change to add a **happy-hour
   time-of-day discount**.

## What I will evaluate

- **Correctness**, **design** (responsibilities & dependencies), **simplicity**, **extensibility**,
  **testability**, **maintainability**, **engineering judgment**, and what you **learned**.
- Specifically: where you put pricing and validation, how you protect the "no negative / no drifting
  money" invariants, and how you'd extend the menu without editing unrelated code.

## Suggested workflow

Restate → list assumptions + invariants → sketch responsibilities → implement → test → explain.
Put your work in `challenges/solutions/CH-002/`. When you're done, say **"done"** and I'll review it
using the standard review format. I will **not** hand you a solution first.

## Assistance ladder (ask before I reveal anything)

I help only as far as you request: **hint → direction → design review → partial code (only the
concept you're stuck on) → full solution.** "I'm stuck" alone does not unlock the next level — name
which level you want.
