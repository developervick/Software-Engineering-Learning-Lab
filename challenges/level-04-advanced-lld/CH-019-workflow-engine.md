# CH-019 — Workflow Engine

- **Challenge ID:** CH-019
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** state machines · command · extensibility & plugin seams · error handling · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/04-state-machines.md`](../../curriculum/04-lld-topics/04-state-machines.md) ·
  [`../../curriculum/03-design-patterns/13-command.md`](../../curriculum/03-design-patterns/13-command.md) ·
  [`../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md`](../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md)

## Why this problem

A workflow engine is where "steps with conditions" becomes a **design problem**: is a workflow *code*
or *data*? Who decides the next step? What does failure mean halfway through? Answering these exposes
your instinct for extensibility vs simplicity.

## Requirements (deliberately a little ambiguous)

Run a multi-step **workflow** to completion.

- A workflow has **steps**; each step does work and the engine decides what runs next.
- Transitions may be **conditional** (branch based on a step's result).
- Steps can **fail**; the workflow must define what that means (retry, stop, or compensate).
- Running a workflow returns a **final status** and enough history to explain the path taken.

## Deliberate ambiguities — YOU decide and justify

1. **Definition medium:** are steps/flows declared as **data** (a config/DSL) or **code** (objects)?
   What do you gain/lose? Which is right for this scope?
2. **Control of next step:** does the engine compute the next step from a transition table, or does the
   flow "return" its successor? Who owns branching logic?
3. **Failure semantics:** stop-on-failure, retry, or **compensation/rollback** of completed steps?
   Which do you implement, and why not the others?
4. **State persistence:** is an in-progress instance in memory only, or serializable so it can resume?
5. **Versioning:** what happens to running instances if the workflow definition changes?

## Constraints

- **In-memory only**; steps can be trivial fakes. No durable store required (but note where it'd go).
- **No third-party dependencies.**
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the workflow model, the engine, and the failure strategy.
3. **Implementation.**
4. **Tests** for a linear flow, a conditional branch, a step failure, and (if implemented) a retry or
   compensation path.
5. **Explanation** — data-vs-code and failure-strategy trade-offs, and what you'd change to persist and
   resume instances.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a deliberate definition medium, clear ownership of branching, and a failure strategy
  you can defend.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-019/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
