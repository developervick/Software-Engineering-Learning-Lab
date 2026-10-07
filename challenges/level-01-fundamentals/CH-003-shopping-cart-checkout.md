# CH-003 — Shopping Cart & Checkout

- **Challenge ID:** CH-003
- **Level:** 1 (baseline)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~1–2 hours (design + implement + tests)
- **Combines:** value objects vs entities · encapsulation · invariants · interfaces & contracts · validation
- **Prereqs (gates):** [`../../curriculum/01-fundamentals/`](../../curriculum/01-fundamentals/) 02–06
  (encapsulation, composition, interfaces, validation, value objects vs entities)

## Why this problem

A cart looks trivial and hides one of the most instructive design decisions in LLD: **is a line in a
cart a value or an entity?** and **when is a price captured?** Get that wrong and totals, editing, and
discounts quietly go inconsistent.

## Requirements (deliberately a little ambiguous)

Model a shopping **cart** and its **checkout**.

- A cart holds **line items**, each with a product and a **quantity**.
- You can **add**, **change quantity**, and **remove** items.
- The cart reports a **subtotal**.
- **Checkout** applies **one discount** and produces the final total.
- Quantities can never go below zero; a removed item disappears.

## Deliberate ambiguities — YOU decide and justify

1. **Line identity:** two adds of the same product — merge into one line or keep separate? What makes
   two lines "the same"?
2. **Price snapshot vs live price:** does a line store the price **when added**, or read the product's
   current price at checkout? Argue which is correct here and why.
3. **Discount semantics:** percent vs fixed amount? Can it stack with future discounts? What about an
   empty cart or a discount larger than the subtotal?
4. **Modifying quantity to zero:** is that a remove, an error, or a no-op? Pick one and justify.
5. **Where the discount rule lives** so a *new* discount type later doesn't force edits to `Cart`.

## Constraints

- **In-memory only.** No UI, no database, no network.
- **No third-party dependencies.**
- Prefer the **simplest** design that meets the requirements; roughly **100–200 lines**.
- Must be **exercisable without a UI** (script or automated tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the responsibilities of the main objects. Small.
3. **Implementation.**
4. **Tests** (or a runnable scenario) covering the important behavior and edge cases.
5. **Explanation** — key decisions, trade-offs, and what you'd change to support a **second,
   independent discount** that stacks.

## What I will evaluate

- **Correctness**, **design** (responsibilities & dependencies), **simplicity**, **extensibility**,
  **testability**, **maintainability**, **engineering judgment**, and what you **learned**.
- Specifically: your value-vs-entity call, your price-capture decision, and how you keep the cart's
  invariants true no matter the call order.

## Suggested workflow

Restate → list assumptions + invariants → sketch responsibilities → implement → test → explain.
Put your work in `challenges/solutions/CH-003/`. When you're done, say **"done"** and I'll review it
using the standard review format. I will **not** hand you a solution first.

## Assistance ladder (ask before I reveal anything)

I help only as far as you request: **hint → direction → design review → partial code (only the
concept you're stuck on) → full solution.** Name which level you want.
