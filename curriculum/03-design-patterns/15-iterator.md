# Iterator

- **Track:** design-patterns · behavioral
- **Prereqs:** fundamentals 2–4
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

Provide a way to **traverse** a collection's elements **without exposing its internal
representation**.

## Drill — do this alone

Build a custom `Playlist` backed by an internal structure of your choosing (list, linked
nodes, map…). Expose a **PlaylistIterator** so callers can loop over songs in order without
knowing the backing store. Then support a second traversal (e.g. shuffled) without changing
the collection's API.

## Done when

- [ ] The iterator exposes `has_next()` / `next()` (or your language's protocol).
- [ ] The collection's internals are **not** exposed — callers can't index into the raw store.
- [ ] Two different iterators can traverse the same collection independently.
- [ ] `Playlist` didn't grow methods for every possible traversal.

## When NOT to use it

- Your language already gives iterators for free (most do) — don't reinvent it.
- There's one fixed traversal and the backing store is already a plain list.

## Reflection

- Why is exposing the raw internal list a mistake (coupling)?
- What happens if the collection is **modified during** iteration? Should I care?

## Theory & resources

- Resources: *Design Patterns* (GoF, Iterator), your language's iteration protocol.
