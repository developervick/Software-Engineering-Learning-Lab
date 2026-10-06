# Builder

- **Track:** design-patterns · creational
- **Prereqs:** fundamentals 2, 6
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Construct a **complex** object step by step, separating construction from representation.

## Drill — do this alone

`HttpRequest` has many optional parts (method, url, headers, query params, body, timeout,
retries). A telescoping constructor is unreadable. Build a fluent `Builder` so a request is
built readably and validated at `build()`.

```python
class HttpRequest:
    def __init__(self, method, url, headers, params, body, timeout, retries):
        ...
# callers: HttpRequest("GET", url, None, None, None, 30, 0)  # what are these?!
```

## Done when

- [ ] No telescoping constructor; optional parts are set by named steps.
- [ ] `build()` validates — an invalid combination (e.g. GET with a body) is rejected there.
- [ ] The built object is immutable once built (optional but preferred).
- [ ] The client code reads like a sentence.

## When NOT to use it

- The object has 1–3 fields — a normal constructor or a dict is fine.
- You don't need step ordering / assembly logic — you just want named args (many languages
  give you that already).

## Reflection

- Builder vs named parameters vs a plain config object — what decided it here?
- Where does validation belong: in the builder, or the built object?

## Theory & resources

- Resources: *Design Patterns* (GoF, Builder), *Effective Java* (Builder item).
