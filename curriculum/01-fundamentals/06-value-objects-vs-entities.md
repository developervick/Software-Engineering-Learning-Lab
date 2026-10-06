# 6. Value objects vs entities

- **Track:** fundamentals
- **Prereqs:** 1, 2
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Kill *primitive obsession*: model concepts like money, email, and date-range as **immutable
value objects** (equal by value). Entities are things with **identity** that changes over time.

## Drill — do this alone

Refactor away the primitives. `Money` must never be a float; `Email` must never be invalid.

```python
def create_invoice(customer_email: str, total: float):
    # total is a float... customer_email is any string...
    ...
```

Introduce `Email` and `Money` value objects. Decide:

- how equality works for each,
- whether they're immutable,
- where validation happens (construction),
- how `Money` avoids floating-point drift.

## Done when

- [ ] `Email` and `Money` **cannot** be constructed in an invalid state.
- [ ] They are immutable; operations return new instances.
- [ ] Equality is by value, not identity, and I proved it with a test.
- [ ] `Money` does not store its amount as a float.

## Reflection

- Which of my domain concepts are values, and which are entities? Why?
- Did I accidentally make a value object mutable?

## Theory & resources

- Value object: no identity, interchangeable if fields match, immutable.
  Entity: identity persists while attributes change.
- Resources: *Domain-Driven Design* (Evans), *Implementing DDD* (Vernon).
