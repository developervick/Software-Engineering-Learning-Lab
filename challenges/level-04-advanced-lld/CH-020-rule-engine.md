# CH-020 — Rule Engine

- **Challenge ID:** CH-020
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–5 hours
- **Combines:** OCP · strategy/composite · immutability · trade-off analysis · extensibility
- **Prereqs (gates):** [`../../curriculum/02-solid/02-ocp.md`](../../curriculum/02-solid/02-ocp.md) ·
  [`../../curriculum/03-design-patterns/08-composite.md`](../../curriculum/03-design-patterns/08-composite.md) ·
  [`../../curriculum/04-lld-topics/05-immutability.md`](../../curriculum/04-lld-topics/05-immutability.md) ·
  [`../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md`](../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md)

## Why this problem

A rule engine tests your ability to make **business logic data-driven and composable** without building
a general-purpose language. It also forces **explainability**: a decision no one can justify is a
liability.

## Requirements (deliberately a little ambiguous)

Evaluate **rules** against a set of **facts** to produce a decision.

- A rule is a condition that evaluates to true/false over facts.
- Rules compose with **and / or / not**.
- The engine evaluates a rule set and returns a **decision** (plus which rules fired).
- A new rule can be added **without editing** the engine.

## Deliberate ambiguities — YOU decide and justify

1. **Representation:** are rules objects (a small class hierarchy) or data (a JSON/DSL tree the engine
   interprets)? Why is that the right trade-off for the scope?
2. **Conflict resolution:** when several rules disagree, how is the final decision made — priority,
   first-match, or a vote? State the rule.
3. **Missing facts:** what if a rule needs a fact that isn't present — treat as false, error, or
   tri-state/unknown?
4. **Explainability:** how do you report **why** a decision was made (which sub-rules passed/failed)?
5. **Performance/side effects:** do rules stay **pure** (no side effects), or may they act? Argue it.

## Constraints

- **In-memory only**; facts are simple maps/objects. No persistence.
- **No third-party dependencies.**
- Roughly **200–400 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the rule abstraction, the composite operators, and the decision model.
3. **Implementation.**
4. **Tests** for each operator, a conflict case, a missing-fact case, and the explanation output.
5. **Explanation** — data-vs-objects and explainability trade-offs, and what you'd change for a
   hot-reloadable rule set.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: rules compose cleanly, "add a rule" is additive, and every decision can be explained.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-020/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
