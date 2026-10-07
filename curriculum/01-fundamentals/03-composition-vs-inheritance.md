# 3. Composition vs inheritance

- **Track:** fundamentals
- **Prereqs:** 1, 2
- **Status:** not-started
- **Est. time:** 60–90 min

## The words (LLD meaning — not the grammar meaning)

- **Inheritance** (`class Child(Parent)`) = a child class **automatically gets the parent's
  attributes and methods**, so it can reuse and (optionally) override them. It models an **is-a**
  relationship **with the same behavior contract** — a child must be usable anywhere the parent is
  (`Penguin` that can't `fly()` breaks that).
- **Composition** = a class **holds another object** and delegates work to it (`self.engine`). It
  models **has-a / uses-a** and lets you **swap the part** without touching the whole.

```python
# Inheritance: Child IS-A Parent; reuses its methods
class Animal:
    def eat(self): return "eating"
class Dog(Animal):          # Dog gets eat() for free
    pass
Dog().eat()                 # -> "eating"

# Composition: Car HAS-A Engine; swap the part freely
class Engine:
    def start(self): return "vroom"
class Car:
    def __init__(self, engine): self.engine = engine
    def start(self): return self.engine.start()   # delegates
Car(Engine()).start()       # -> "vroom"
```

> Rule of thumb: use inheritance for **is-a with an identical contract**; otherwise compose.
> Full definitions: [`../../docs/glossary.md`](../../docs/glossary.md#inheritance).

**Practice:** the drill below is your challenge — decide when inheritance is a trap and refactor to
composition. The answer is not provided.

## Goal

Reach for **composition** by default; recognize when an inheritance hierarchy is a trap.

## Drill — do this alone

This hierarchy breaks the moment a new kind of bird appears. First **explain the flaw in
writing**, then **refactor to composition** so adding `Penguin` requires no edits to
existing flying logic.

```python
class Bird:
    def fly(self):
        return "flapping"

class Sparrow(Bird):
    pass

class Penguin(Bird):
    def fly(self):
        raise Exception("penguins can't fly")   # violates Bird's contract
```

## Done when

- [ ] I can explain *why* `Penguin(Bird)` is a broken model (not just "penguins don't fly").
- [ ] New birds are added without editing existing classes.
- [ ] Behavior is composed from parts (e.g. a `Flying` / `NotFlying` behavior), not overridden.
- [ ] I can state when inheritance **is** the right tool.

## Reflection

- What rule did I use to decide inheritance vs composition?
- Did I over-correct into needless objects?

## Theory & resources

- "Favor composition over inheritance." Inheritance = **is-a with an identical behavior
  contract**; composition = **has-a behavior you can swap**.
- Resources: *Design Patterns* (intro), *Effective Java* (composition over inheritance).
