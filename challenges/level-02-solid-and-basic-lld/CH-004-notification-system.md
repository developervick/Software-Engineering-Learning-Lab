# CH-004 — Notification System

- **Challenge ID:** CH-004
- **Level:** 2 (SOLID & basic LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–3 hours
- **Combines:** interfaces & contracts · OCP · DIP · strategy/polymorphism · dependency injection · coupling
- **Prereqs (gates):** [`../../curriculum/02-solid/`](../../curriculum/02-solid/) (all 5) ·
  [`../../curriculum/01-fundamentals/04-interfaces-and-contracts.md`](../../curriculum/01-fundamentals/04-interfaces-and-contracts.md) ·
  [`../../curriculum/03-design-patterns/10-strategy.md`](../../curriculum/03-design-patterns/10-strategy.md) ·
  [`../../curriculum/04-lld-topics/02-dependency-injection.md`](../../curriculum/04-lld-topics/02-dependency-injection.md)

## Why this problem

This is the textbook case where an abstraction is **justified by a concrete, likely change**: adding a
new channel (push, WhatsApp, Slack) must not edit the core. The trap is the opposite one too —
inventing an elaborate framework for a system that only ever sends email.

## Requirements (deliberately a little ambiguous)

Build a service that sends **notifications** to users.

- Support **at least two channels** (e.g. email and SMS).
- A caller can request a notification for a recipient with a message.
- Sending returns a **result** the caller can inspect (sent? which channel? why it failed?).
- Adding a **new channel** must not modify the existing send logic.

## Deliberate ambiguities — YOU decide and justify

1. **One channel or many:** does a notification go to a single channel, or fan out to all of a user's
   channels? Who decides?
2. **Selection:** is the channel chosen by the caller, by user preference, or by config? Where does
   that policy live?
3. **Failure model:** if one channel fails, is that a whole-notification failure? Do you return an
   exception, a result type, or both?
4. **Sync vs queued:** does `send` block, or hand off to a queue? Justify for this scope.
5. **Retries/dedup:** out of scope or in? If in, whose job is it?

## Constraints

- **In-memory only**; channels are **fakes/loggers**, not real integrations.
- **No third-party dependencies.**
- Roughly **120–250 lines**. If you go far beyond, name the complexity and justify it.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the main objects and the dependency direction between them.
3. **Implementation.**
4. **Tests** covering the send paths, a failing channel, and the new-channel seam.
5. **Explanation** — name the **exact change** your abstraction protects against, and say why you did
   or didn't add abstractions you considered.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: is the abstraction earned, is the contract small, and is the core closed to edits when
  a channel is added?

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-004/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — say which level you want.
