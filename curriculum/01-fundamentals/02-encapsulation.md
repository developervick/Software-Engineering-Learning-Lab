# 2. Encapsulation

- **Track:** fundamentals
- **Prereqs:** 1. Responsibilities & cohesion
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Hide internal state behind a **minimal, meaningful interface** so an object cannot be pushed
into an invalid state from the outside.

## Drill — do this alone

This `Wallet` exposes its guts and can be corrupted. **Redesign it** so that:

1. no outside code can set the balance directly,
2. `balance` can never go negative,
3. the only operations are meaningful ones (`deposit`, `withdraw`, `balance`).

```python
class Wallet:
    def __init__(self):
        self.balance = 0
        self.transactions = []
```

Then write 2–3 lines of client code that **should fail** with your new design (e.g.
`wallet.balance = -500`).

## Done when

- [ ] All fields are private; state changes only through methods.
- [ ] The invariant "balance ≥ 0" is enforced in **one** place.
- [ ] I can state the object's **invariant** and where it is protected.
- [ ] I did not leak a mutable internal collection (e.g. returned the raw `transactions` list).

## Reflection

- Which getters did I *not* add, and why? (Not every field needs one.)
- Did exposing `transactions` by reference leak the invariant?

## Theory & resources

- Encapsulation is about **protecting invariants**, not just "private fields + getters".
- Resources: *Clean Code* (objects vs data structures), *Effective Java* (minimize mutability).
