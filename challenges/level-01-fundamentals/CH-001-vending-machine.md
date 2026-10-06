# CH-001 — Vending Machine

- **Challenge ID:** CH-001
- **Level:** 1 (baseline)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~1–3 hours (design + implement + tests)
- **Combines:** fundamentals (responsibilities, encapsulation, validation, value objects) + a state machine
- **Prereqs (gates):** [`../../curriculum/01-fundamentals/`](../../curriculum/01-fundamentals/) 1–6,
  [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md)

## Why this problem

The domain is intentionally **familiar**. Novelty would only add noise — I want to see your
*reasoning*, not your knowledge of an exotic domain. Watch the places where memorized
"vending machine designs" are usually weak: the exact invariants, how money is modeled,
error/edge behavior, the changing-behavior seam, and whether the vend flow is testable
without a UI.

## Requirements (deliberately a little ambiguous)

Build a single vending machine that sells snack items.

- The machine has **slots**. Each slot holds one product type, a **price**, and a
  **stock quantity**.
- A user can **insert coins** one at a time.
- A user can **select a slot** to buy.
- A purchase succeeds only if the slot has stock **and** enough money has been inserted.
- On success: dispense the item, reduce stock, and reset the purchase session.
- A user can **cancel** at any time and get back exactly the money they inserted.
- The machine reports the **current amount inserted** and, when funds are insufficient,
  how much **more is needed**.

## Deliberate ambiguities — YOU decide and justify

Don't ask me to resolve these. Decide, then write down the decision **and** the reasoning.

1. **Change:** Does the machine give change? If so, must it track its **own coin inventory**?
   What happens when it *cannot* make exact change?
2. **Money model:** How do you represent money so you never lose or create value and never
   hit floating-point drift?
3. **Out-of-stock selection:** auto-refund? block selection? keep the money? What does the
   user see?
4. **State:** what states does the machine have, and **who owns the transitions**?
5. **Ordering/failure edges:** what if the user inserts money then the price changes?
   What does a freshly-stocked vs. empty machine look like at startup?

## Constraints

- Single machine, single user at a time. **In-memory only.** No UI, no database, no network.
- Prefer the **simplest** design that meets the requirements.
- Aim for roughly **100–250 lines** of implementation. If you land far above that, ask
  yourself what complexity you added and whether it earns its place.
- **No third-party dependencies.**
- There must be a way to **exercise the vend flow without a UI** (a script or automated tests).

## Deliverables (in this order)

1. **Assumptions & scope** — a short bullet list, written **before** you code.
2. **Design sketch** — the responsibilities of the main objects and how they collaborate.
   Small. Not a 30-class diagram.
3. **Implementation.**
4. **Tests** (or a runnable scenario) covering the important behaviors and edge cases.
5. **Explanation** — key decisions, trade-offs, and what you'd change to add either
   (a) cashless payment or (b) an "exact-change-only" mode.

## What I will evaluate

- **Correctness**, **design** (responsibilities & dependencies), **simplicity**,
  **extensibility**, **testability**, **maintainability**, **engineering judgment**,
  and what you **learned**.
- Specifically: how you restate requirements, model the domain, choose (or avoid)
  abstractions, protect invariants, handle failure, and explain trade-offs.

## Suggested workflow

Restate → list assumptions + invariants → sketch responsibilities → implement → test →
explain. Put your work in `challenges/solutions/CH-001/`. When you're done, tell me
**"done"** and I'll review it using the standard review format. I will **not** hand you a
solution first.

## Assistance ladder (ask before I reveal anything)

I help only as far as you request: **hint → direction → design review → partial code
(only the concept you're stuck on) → full solution.** "I'm stuck" alone does not unlock
the next level — tell me which level you want.
