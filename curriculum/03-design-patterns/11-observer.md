# Observer

- **Track:** design-patterns · behavioral
- **Prereqs:** fundamentals 4
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Define a **one-to-many** dependency so that when one object changes state, all its
dependents are notified automatically.

## Drill — do this alone

A `StockTicker` changes price. Multiple consumers care: a `PriceDisplay`, an `AlertService`,
a `Logger`. Build **publish/subscribe**: subscribers register, and on each price change they
are notified — without the ticker knowing their concrete types.

## Done when

- [ ] A subject holds a list of observers behind an interface.
- [ ] `subscribe` / `unsubscribe` work; **unsubscribe actually stops** notifications (test it).
- [ ] The subject doesn't know concrete observer classes.
- [ ] Adding a new observer requires no change to the subject.

## When NOT to use it

- There's one fixed consumer — just call it directly.
- Notification order/loops matter and are subtle; a direct call or an explicit pipeline is
  easier to reason about than implicit fan-out.

## Reflection

- What happens if an observer throws — does the subject survive?
- Could this leak memory (observers never unsubscribed)? How would I detect it?

## Theory & resources

- Resources: *Design Patterns* (GoF, Observer), reactive/event-bus docs.
