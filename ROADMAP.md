# Roadmap — from fundamentals to senior

> **Entry point:** start with [`START-HERE.md`](START-HERE.md) for the full, ordered study path.

This is the **spine** of the lab. Work through it in order. Don't skip a stage because you
*understand* the theory — move on only when you can **build, break, fix, and explain** it.

The lab is **concept-first**: Stages 1–4 drill one idea at a time. Stage 5 is where you
**combine** them. Stage 6 is where you combine many across process/network boundaries.

```
Stage 0   Setup & habits
Stage 1   Fundamentals        (concept drills, alone)
Stage 2   SOLID               (concept drills, alone)
Stage 3   Design patterns     (concept drills, alone)
Stage 4   LLD topics          (concept drills, alone)
Stage 5   Challenges          (COMBINE several concepts into a solution)
Stage 6   System design       (combine many, across boundaries)
          → senior-level engineering judgment
```

Skill progression (not just topics):

```
Understand → Implement → Modify → Debug → Design →
Handle ambiguity → Handle trade-offs → Handle scale & failure
```

---

## Stage 0 — Setup & habits
**Goal:** understand how the lab works and finish one tiny thing end to end.
- Read [`docs/how-to-use-this-repo.md`](docs/how-to-use-this-repo.md).
- Pick your language and tooling (Python is a fine default).
- Learn the loop: assumptions → design → code → test → explain.
**Move on when:** you can run a test file and explain what it checks.

## Stage 1 — Fundamentals  →  [`curriculum/01-fundamentals/`](curriculum/01-fundamentals/)
**Goal:** drill each fundamental **alone** until you can apply it without thinking.
**Concepts (one file each):** classes & objects · responsibilities & cohesion ·
encapsulation · composition vs inheritance · interfaces & contracts · validation & fail-fast ·
value objects vs entities · refactoring basics.
**Move on when:** every fundamentals gate is checked in
[`progress/concept-tracker.md`](progress/concept-tracker.md).

## Stage 2 — SOLID  →  [`curriculum/02-solid/`](curriculum/02-solid/)
**Goal:** spot and fix each principle's violation; know when *not* to apply it.
**Concepts:** SRP · OCP · LSP · ISP · DIP.
**Move on when:** given a small messy class you can name the violated principle, fix it, and
explain why your fix doesn't violate the others.

## Stage 3 — Design patterns  →  [`curriculum/03-design-patterns/`](curriculum/03-design-patterns/)
**Goal:** build each pattern from memory and argue **when NOT to use it**.
**Concepts:** factory method · abstract factory · builder · singleton (anti-pattern talk) ·
adapter · decorator · facade · composite · proxy · strategy · observer · state · command ·
template method · iterator.
**Move on when:** for any pattern you can (a) build it, (b) name the real problem it solves,
and (c) name a case where a simpler solution is better.

## Stage 4 — LLD topics  →  [`curriculum/04-lld-topics/`](curriculum/04-lld-topics/)
**Goal:** practice the cross-cutting skills that aren't patterns.
**Concepts:** coupling & dependency direction · dependency injection · layering ·
state machines · immutability · error-handling strategy · testability & seams ·
concurrency basics · extensibility & plugin seams · trade-off analysis.
**Move on when:** you can build a small feature choosing a dependency direction, a state
model, and an error strategy — and defend each choice.

## Stage 5 — Challenges (combine concepts)  →  [`challenges/`](challenges/)
**Goal:** integrate several concepts into one working solution.
**Levels:** 1 fundamentals → 2 SOLID & basic LLD → 3 intermediate LLD → 4 advanced LLD →
5 system design (see [`challenges/README.md`](challenges/README.md)).
**Rule:** do a challenge only when the gates of the concepts it **combines** are met.
**Example challenges:** vending machine · notification system · parking lot · event bus ·
rate limiter.
**Move on when:** you can take a vague requirement, list assumptions and invariants, and
produce a small design whose pieces each have one clear job — and defend the trade-offs.

## Stage 6 — System design + implementation
**Goal:** combine everything across process/network boundaries.
**Concepts:** persistence · caching · queues · retries · idempotency · observability ·
failure handling · API design · scale.
**Example challenges:** end-to-end "design + build a slice" projects with faults injected.
**Move on when:** you instinctively ask the senior-engineer question set below.

---

## Where am I?

Live status: [`progress/README.md`](progress/README.md) (dashboard) and
[`progress/concept-tracker.md`](progress/concept-tracker.md) (per-concept).

---

## The senior-engineer question set (learn to ask these automatically)

- What changes? What stays stable?
- Who owns this responsibility?
- What depends on what?
- What happens when it fails?
- What are the invariants?
- How do I test it? How do I extend it?
- What is the simplest reasonable design?
- What trade-off am I making? What complexity am I introducing?
