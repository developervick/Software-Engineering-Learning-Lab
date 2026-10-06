# State machines

- **Track:** lld-topics
- **Prereqs:** fundamentals 2
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Model behavior that changes with state, with **explicit allowed transitions** and no illegal
states reachable.

## Drill — do this alone

Model an **order**: `Created → Paid → Shipped → Delivered`, with `Cancelled` reachable from
`Created`/`Paid` only. Enumerate states, events, and legal transitions **on paper first**.
Then implement it so an illegal transition (e.g. `Delivered → Paid`) is rejected.

## Done when

- [ ] I listed states, events, and the full transition table before coding.
- [ ] Every illegal transition raises a clear error (no silent no-op).
- [ ] The current state is inspectable; the set of states is closed (no stringly-typed states).
- [ ] I tested the happy path **and** at least two illegal transitions.

## Reflection

- When is a full state machine overkill vs. an enum + `if`?
- Where do side effects (emails, events) belong on a transition — before or after the state
  change? Why does order matter?

## Theory & resources

- Resources: UML state diagrams; *Game Programming Patterns* (State), LLD interview material.
