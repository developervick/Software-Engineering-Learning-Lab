# OCP — Open/Closed Principle

- **Track:** solid
- **Prereqs:** SRP
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Software should be **open for extension, closed for modification** — add new behavior
without editing (and re-testing) existing code.

## Drill — do this alone

Every new discount type forces you to edit `PriceCalculator`. Refactor so a **new discount
is added without editing this class**.

```python
class PriceCalculator:
    def total(self, items, customer_type):
        subtotal = sum(i["price"] * i["qty"] for i in items)
        if customer_type == "regular":
            return subtotal
        elif customer_type == "vip":
            return subtotal * 0.9
        elif customer_type == "employee":
            return subtotal * 0.7
        # new type -> edit here every time
```

## Done when

- [ ] Adding a discount type requires **only** adding a new class, not editing existing ones.
- [ ] No growing `if/elif`/`switch` over types in the calculator.
- [ ] I can point to the exact seam that makes it extensible.
- [ ] Existing tests still pass unchanged.

## Reflection

- Did the `switch` really disappear, or just move somewhere else? Is that acceptable?
- What did I assume will **not** change? (OCP trades one kind of rigidity for another.)

## Theory & resources

- Extension points: polymorphism, strategy, plugin registration, template method.
- Resources: *Clean Architecture* (OCP), *Head First Design Patterns* (Strategy).
