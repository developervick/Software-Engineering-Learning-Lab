# DIP — Dependency Inversion Principle

- **Track:** solid
- **Prereqs:** SRP, OCP, ISP
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

High-level policy should not depend on low-level detail. **Both depend on abstractions**, and
the abstraction is owned by the high-level side.

## Drill — do this alone

`OrderService` (business policy) creates and depends on `MySqlOrderRepository` (detail).
Invert the dependency so the service depends on an abstraction it owns, and the detail
implements it. Wire the concrete up only at the entry point (composition root).

```python
class MySqlOrderRepository:
    def fetch(self, id): ...

class OrderService:
    def __init__(self):
        self.repo = MySqlOrderRepository()   # depends on a detail

    def reorder(self, id):
        order = self.repo.fetch(id)
        ...
```

## Done when

- [ ] `OrderService` imports/owns an **abstraction**, not the MySQL class.
- [ ] The concrete repository implements that abstraction.
- [ ] Swapping in an in-memory repo requires **no** change to `OrderService`.
- [ ] The choice of concrete is made in exactly one place (composition root).
- [ ] The dependency arrow between modules now points toward the policy.

## Reflection

- Who should **own** the interface — the caller or the implementation? Why?
- How is DIP different from "just use an interface"? (Direction of the arrows.)

## Theory & resources

- DIP = depend on abstractions + invert ownership so details depend on policy, not vice versa.
- Resources: *Clean Architecture* (DIP, boundaries), *Dependency Injection Principles* (Seemann).
