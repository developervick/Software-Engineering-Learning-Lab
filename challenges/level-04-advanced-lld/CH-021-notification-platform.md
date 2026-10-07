# CH-021 — Notification Platform

- **Challenge ID:** CH-021
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** OCP · observer/events · plugin seams · DIP · layering · error handling
- **Prereqs (gates):** [`../../curriculum/02-solid/02-ocp.md`](../../curriculum/02-solid/02-ocp.md) ·
  [`../../curriculum/03-design-patterns/11-observer.md`](../../curriculum/03-design-patterns/11-observer.md) ·
  [`../../curriculum/04-lld-topics/03-layering.md`](../../curriculum/04-lld-topics/03-layering.md) ·
  [`../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md`](../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md)

## Why this problem

This is the "grown-up" version of CH-004: routing a message to channels becomes a **policy** problem
(preferences, priorities, quiet hours, fallback), and providers become **plugins**. It's where OCP and
layering earn their keep — or turn into over-engineering if you can't name the change they protect.

## Requirements (deliberately a little ambiguous)

Route messages to the right **channel(s)** per user.

- Users have **preferences** (preferred channel, quiet hours, opt-outs).
- A message has a **priority** (e.g. transactional vs marketing).
- The platform chooses channel(s) and sends via **pluggable providers**.
- If a channel fails, the platform may **fall back** to another per a policy.
- Adding a provider or a preference rule must not edit the core routing logic.

## Deliberate ambiguities — YOU decide and justify

1. **Precedence:** when preferences, priority, and quiet hours disagree, who wins? Write the rule
   down explicitly.
2. **Routing policy location:** is channel selection a **policy object** (swappable), a rule engine, or
   hard code? What concrete change justifies your choice?
3. **Fallback:** which failures trigger fallback, in what order, and how many attempts?
4. **Quiet hours:** defer or drop? Does priority `transactional` override quiet hours?
5. **Dedup/rate:** in scope? If a user is notified twice, is that a bug here or a downstream concern?

## Constraints

- **In-memory only**; providers are fakes with scripted failures.
- **No third-party dependencies.**
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the routing/policy layer, the provider plugins, and the layering.
3. **Implementation.**
4. **Tests** for preference precedence, quiet hours, a provider failure with fallback, and adding a
   provider.
5. **Explanation** — your precedence rules, why the routing layer is separable, and what you'd change
   for a scale-out queue.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: explicit, written precedence rules; providers as clean plugins; and a core closed to
  edits when a provider/rule is added.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-021/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
