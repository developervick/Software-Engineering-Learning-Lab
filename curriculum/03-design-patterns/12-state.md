# State

- **Track:** design-patterns · behavioral
- **Prereqs:** Strategy, LLD topic: state machines
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Let an object **change its behavior when its internal state changes** — the object appears to
change its class.

## Drill — do this alone

A traffic light cycles `Red → Green → Yellow → Red`. Each state has a different duration and
a **different behavior** (e.g. `can_go()`). Implement it with a **State** object per light
state, where each state knows its successor — so there is no `switch` over state names.

> Deliberately **not** the vending machine (that's CH-001) — practice the pattern cleanly first.

## Done when

- [ ] Each state is a class with the same interface.
- [ ] Transitions are triggered by events/actions, not by a giant conditional.
- [ ] Adding a state touches only the states involved in the transition, not the context.
- [ ] I can draw the state diagram and the code matches it.

## When NOT to use it

- There are 2 states and 2 transitions — an enum + `if` is honest and clearer.
- The "state" doesn't actually change behavior, only data.

## Reflection

- State vs Strategy: both delegate. What forces the difference here?
- Where is the transition logic better kept — in each state, or in the context? Trade-offs?

## Theory & resources

- Resources: *Design Patterns* (GoF, State), UML state-machine tutorials.
