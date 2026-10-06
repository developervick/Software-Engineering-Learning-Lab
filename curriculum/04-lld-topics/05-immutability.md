# Immutability

- **Track:** lld-topics
- **Prereqs:** fundamentals 6
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Prefer objects whose state cannot change after creation — fewer bugs, safe sharing, easy to
reason about.

## Drill — do this alone

Take a mutable class (e.g. a `Point` or a `Config`) with setters. Make it **immutable**: all
fields final, no setters, defensive copies of collections, and "modifying" operations return
**new** instances. Then convert a piece of code that mutated it into code that reassigns.

## Done when

- [ ] All fields are set once in the constructor and never change.
- [ ] "Changers" return new instances (e.g. `withX(...)`).
- [ ] Any mutable input/output collection is defensively copied.
- [ ] I can explain a concurrency benefit I now get for free.

## Reflection

- Where did immutability make the code more verbose? Was the trade worth it?
- Which parts of my domain genuinely need to be mutable (entities), and which don't?

## Theory & resources

- Resources: *Effective Java* (minimize mutability), *Functional thinking* intro material.
