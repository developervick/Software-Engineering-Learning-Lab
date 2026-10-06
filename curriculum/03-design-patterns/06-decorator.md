# Decorator

- **Track:** design-patterns · structural
- **Prereqs:** fundamentals 3–4, SOLID OCP
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Attach **additional behavior** to an object by wrapping it, at runtime, without touching the
original class and without subclass explosion.

## Drill — do this alone

You have a `DataSource.read()`. You need to add **compression** and **encryption**, in any
combination, chosen at runtime. Implement decorators so you can write:

```
new Encrypt(new Compress(new FileData()))
```

…and each decorator adds exactly one concern.

## Done when

- [ ] Each decorator implements the **same interface** it wraps.
- [ ] Decorators can be layered in any order and any subset.
- [ ] No changes to `FileData`; no combinatorial subclasses.
- [ ] Each decorator does **one** thing.

## When NOT to use it

- You only ever need one fixed combination — just put the logic in one place.
- Ordering can't actually vary, or the layering has subtle correctness rules that a single
  explicit pipeline would express more clearly.

## Reflection

- How is this different from inheritance? Draw the class explosion it avoids.
- What are the risks of deep wrapping (debuggability, ordering bugs)?

## Theory & resources

- Resources: *Design Patterns* (GoF, Decorator), *Effective Java* (Item on composition).
