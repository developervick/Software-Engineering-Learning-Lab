# LSP — Liskov Substitution Principle

- **Track:** solid
- **Prereqs:** SRP, OCP
- **Status:** not-started
- **Est. time:** 60 min

## Goal

A subtype must be **usable anywhere its base type is**, without the client needing to know
which subtype it is — and without breaking the base type's promises.

## Drill — do this alone

The classic violation. **Explain what contract `Square` breaks**, then fix it — choosing
deliberately between "make them siblings" and "make them immutable", and justify the choice.

```python
class Rectangle:
    def __init__(self, w, h):
        self.w = w
        self.h = h
    def set_width(self, w):  self.w = w
    def set_height(self, h): self.h = h
    def area(self):          return self.w * self.h

class Square(Rectangle):
    def set_width(self, w):
        self.w = self.h = w      # keeps it square...
    def set_height(self, h):
        self.w = self.h = h
```

A client that does `r.set_width(5); r.set_height(4); assert r.area() == 20` **breaks** for a
`Square`. Write that client as a test to prove the violation.

## Done when

- [ ] I can state the base type's **behavioral contract** (invariants, pre/post-conditions).
- [ ] I wrote a test showing the subtype breaks a valid base-type client.
- [ ] My fix makes the whole hierarchy substitutable (or removes the bad `extends`).
- [ ] I can explain the difference between "is-a" *intuitively* and "is-substitutable"
      *behaviorally*.

## Reflection

- Which is the real culprit — `Square`, or the **mutable** `Rectangle` interface?
- Have I seen this same shape in my own code (a subclass that throws on a base method)?

## Theory & resources

- LSP is about **behavioral** substitutability, not just type inheritance.
- Resources: *Clean Architecture* (LSP), Barbara Liskov's original substitution idea.
