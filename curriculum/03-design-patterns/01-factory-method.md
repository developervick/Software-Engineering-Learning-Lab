# Factory Method

- **Track:** design-patterns · creational
- **Prereqs:** fundamentals 3–4, SOLID OCP/DIP
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Define an interface for creating an object, but let subclasses (or a factory) decide which
concrete class to instantiate.

## Drill — do this alone

A logistics app switches on a string to create the right transport. Refactor to a
**factory method** so the "create" decision has one home and callers don't switch on type.

```python
def create_transport(kind):
    if kind == "truck": return Truck()
    if kind == "ship":  return Ship()
    raise ValueError(kind)

def plan_delivery(kind):
    t = create_transport(kind)
    t.deliver()
```

## Done when

- [ ] Callers request a *product*, not a *kind string*.
- [ ] Adding a new transport doesn't edit the existing factory logic.
- [ ] I can say who owns the creation decision.
- [ ] No `if/elif` over product types remains at the call site.

## When NOT to use it

- Only one concrete product exists, or creation is trivial (`Foo()`) — a factory is noise.
- You don't actually have varying products yet (speculative generality).

## Reflection

- Is this really a factory, or a disguised `switch` that moved? Does that matter?
- How does this relate to OCP?

## Theory & resources

- Factory Method vs Abstract Factory vs Builder — know the *problem* each solves.
- Resources: *Design Patterns* (GoF), *Head First Design Patterns*.
