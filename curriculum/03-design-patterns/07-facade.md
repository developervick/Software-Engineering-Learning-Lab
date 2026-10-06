# Facade

- **Track:** design-patterns · structural
- **Prereqs:** fundamentals 4
- **Status:** not-started
- **Est. time:** 45 min

## Goal

Provide a **simple, unified interface** to a complex subsystem.

## Drill — do this alone

Starting a video call touches: auth, network, media devices, UI. Right now the client wires
all four classes together by hand. Add a `VideoCallFacade.start()` that hides the choreography
behind one call — while still allowing the subsystem classes to be used directly when needed.

## Done when

- [ ] The common use case is one or two calls on the facade.
- [ ] The facade **coordinates** but doesn't reimplement subsystem logic.
- [ ] The subsystem classes are not made "dumber" or hidden forever — direct use is still possible.
- [ ] A newcomer could understand the happy path from the facade alone.

## When NOT to use it

- The subsystem is already simple — the facade just forwards and adds nothing.
- The facade is slowly absorbing business logic and becoming a god object.

## Reflection

- Facade vs Adapter vs Mediator — different intent, similar-looking wrapper. Which is this?
- Did my facade leak subsystem types to the client, defeating the point?

## Theory & resources

- Resources: *Design Patterns* (GoF, Facade), refactoring.guru.
