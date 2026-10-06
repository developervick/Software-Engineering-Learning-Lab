# Adapter

- **Track:** design-patterns · structural
- **Prereqs:** fundamentals 4, SOLID DIP
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Convert the interface of a class into another interface clients expect — let incompatible
things work together **without changing either**.

## Drill — do this alone

Your app speaks `PaymentGateway.charge(cents)`. A third-party library exposes
`StripeApi.pay(amount_minor_units, currency)`. Write an **adapter** so the app uses the
third-party library through your interface, and you could swap in a second provider later.

```python
class PaymentGateway:
    def charge(self, cents: int): ...

class StripeApi:                       # you can't change this (3rd party)
    def pay(self, amount_minor_units: int, currency: str): ...
```

## Done when

- [ ] No changes to the third-party class or to the client.
- [ ] The adapter translates both **calls** and **data shapes** (and errors, if they differ).
- [ ] A second provider can be added as another adapter behind the same interface.
- [ ] The adapter contains **translation only** — no business logic.

## When NOT to use it

- You control both interfaces and can just change one — an adapter is needless ceremony.
- The "adapter" is accumulating business rules; then it's really a domain service.

## Reflection

- Adapter vs Facade — both wrap. What's the different intent?
- Did translation errors/exceptions too, or did third-party errors leak out?

## Theory & resources

- Resources: *Design Patterns* (GoF, Adapter), *Head First Design Patterns*.
