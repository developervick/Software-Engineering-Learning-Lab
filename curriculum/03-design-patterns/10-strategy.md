# Strategy

- **Track:** design-patterns · behavioral
- **Prereqs:** SOLID OCP/DIP, fundamentals 4
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Define a **family of interchangeable algorithms**, encapsulate each, and make them swappable
at runtime.

## Drill — do this alone

A checkout computes **shipping** several ways (flat rate, by weight, free over a threshold).
Right now it's a `switch`. Extract each into a `ShippingStrategy` and let the client choose
one at runtime — adding a new method must not edit existing code.

```python
def shipping_cost(method, order):
    if method == "flat": return 5
    if method == "weight": return order.weight * 0.5
    ...
```

## Done when

- [ ] Each algorithm is its own class implementing one `ShippingStrategy` interface.
- [ ] The context holds a strategy and delegates to it (no `switch` over method names).
- [ ] A new strategy is added without editing the context.
- [ ] Strategies are stateless (or clearly documented if not).

## When NOT to use it

- There's exactly one algorithm and no realistic second one.
- The variation is trivial (a single boolean) — an `if` is clearer than a class per branch.

## Reflection

- Strategy vs State — both delegate to a swappable object. Who decides when to swap?
- Strategy vs just passing a function — in what language is the class worth it?

## Theory & resources

- Resources: *Design Patterns* (GoF, Strategy), *Head First Design Patterns*.
