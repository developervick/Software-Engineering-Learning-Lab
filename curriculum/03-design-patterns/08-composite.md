# Composite

- **Track:** design-patterns · structural
- **Prereqs:** fundamentals 3
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Compose objects into **tree structures** and treat individual objects (leaves) and
compositions (containers) **uniformly**.

## Drill — do this alone

Model a file system: `File` (leaf) and `Folder` (container of files/folders). Both should
respond to `size()` and `print_tree()` **the same way**, so client code never asks "is this a
file or a folder?".

## Done when

- [ ] Leaf and container share one component interface.
- [ ] `size()` on a folder recurses into children; on a file it's trivial.
- [ ] Client code has **no** `isinstance`/type checks.
- [ ] I can add a new leaf type without editing the container.

## When NOT to use it

- The structure isn't actually a tree (a flat list is fine).
- Operations differ so much between leaf and container that forcing a shared interface is a lie.

## Reflection

- Where could an operation be placed so the container doesn't need to know all leaf types?
- Did I introduce a shared interface that some leaves can't honor (an LSP warning)?

## Theory & resources

- Resources: *Design Patterns* (GoF, Composite).
