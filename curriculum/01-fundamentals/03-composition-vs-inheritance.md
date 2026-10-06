# 3. Composition vs inheritance

- **Track:** fundamentals
- **Prereqs:** 1, 2
- **Status:** not-started
- **Est. time:** 60–90 min

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
