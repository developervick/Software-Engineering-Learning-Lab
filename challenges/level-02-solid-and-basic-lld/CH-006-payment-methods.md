# CH-006 — Payment Methods

- **Challenge ID:** CH-006
- **Level:** 2 (SOLID & basic LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–3 hours
- **Combines:** interfaces & contracts · LSP · DIP · validation · error-handling strategy
- **Prereqs (gates):** [`../../curriculum/02-solid/03-lsp.md`](../../curriculum/02-solid/03-lsp.md) ·
  [`../../curriculum/02-solid/05-dip.md`](../../curriculum/02-solid/05-dip.md) ·
  [`../../curriculum/01-fundamentals/04-interfaces-and-contracts.md`](../../curriculum/01-fundamentals/04-interfaces-and-contracts.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

Payment methods expose the classic **LSP trap**: not every method supports every operation (refunds,
partial capture). If your base type promises `refund()` and one implementation throws "not supported",
you built the wrong contract. This challenge is about *earning* the abstraction and keeping every
implementation honestly substitutable.

## Requirements (deliberately a little ambiguous)

Charge and refund money through different **payment methods**.

- Support at least **three** methods (e.g. card, wallet, bank transfer).
- A caller pays an **amount** and receives a **result** (success/failure with a reason).
- Some methods can also **refund**; the contract must stay truthful for all implementations.
- Failures (declined, insufficient funds, network) must be represented **consistently**.

## Deliberate ambiguities — YOU decide and justify

1. **The contract's shape:** one `PaymentMethod` with `pay` and `refund`, or a smaller `pay` contract
   plus a separate refundable capability? Defend it against LSP.
2. **Failure representation:** exception vs result object vs nullable — pick one policy and apply it
   everywhere, including "expected" business failures vs bugs.
3. **Idempotency of a charge:** how do you avoid double-charging on a retried `pay`? In scope or not?
4. **Amount rules:** can you pay zero / negative? Where is that validated?
5. **Async confirmation:** is a payment synchronous here, or does it return "pending"? Justify.

## Constraints

- **In-memory only**; methods are **fakes** with scripted successes/failures, no real networks.
- **No third-party dependencies.**
- Roughly **120–250 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the contract(s) and how substitutability is preserved.
3. **Implementation.**
4. **Tests** for success, each failure kind, and a refundable vs non-refundable method.
5. **Explanation** — why your contract does not force any implementation to fake an ability it
   doesn't have; what you'd change for partial refunds.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: contract honesty (LSP), one consistent error policy, and where validation lives.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-006/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
