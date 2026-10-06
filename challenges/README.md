# Challenge Arena — combine concepts

Challenges are **Stage 5**: the **combination** stage. Each one integrates several concepts
you already drilled **alone** in [`../curriculum/`](../curriculum/). Do a challenge only when
the gates of the concepts it combines are met — see
[`../progress/concept-tracker.md`](../progress/concept-tracker.md).

One file per challenge: `CH-XXX-<slug>.md`.

## Levels

| Level | Folder | Focus |
|-------|--------|-------|
| 1 | [`level-01-fundamentals/`](level-01-fundamentals/) | Domain modeling, responsibilities, invariants |
| 2 | [`level-02-solid-and-basic-lld/`](level-02-solid-and-basic-lld/) | SOLID in practice, strategies, small LLD |
| 3 | [`level-03-intermediate-lld/`](level-03-intermediate-lld/) | State, rules, interactions |
| 4 | [`level-04-advanced-lld/`](level-04-advanced-lld/) | Extensible, decoupled systems |
| 5 | [`level-05-system-design/`](level-05-system-design/) | Persistence, concurrency, failure, scale |

Start at the lowest level you have **not** mastered. See [`../ROADMAP.md`](../ROADMAP.md).

## Challenge index

| ID | Title | Level | Type | Combines | Status |
|----|-------|-------|------|----------|--------|
| CH-001 | Vending Machine | 1 | Design + Implementation | [fundamentals 1–6](../curriculum/01-fundamentals/), [state machines](../curriculum/04-lld-topics/04-state-machines.md) | not started |

## Conventions

- Every challenge documents: **ID · title · level · type · concepts · prereqs · requirements ·
  constraints · deliverables · evaluation criteria**.
- Every challenge lists the **Prereqs** (concept gates that must be met first) and what it
  **Combines**.
- Requirements may be **intentionally ambiguous** — resolving them is part of the exercise.
- The challenge file **never contains the solution**.
- New challenges start from [`_template.md`](_template.md).

## Submitting work

Put your solution in [`solutions/CH-XXX/`](solutions/):

```
solutions/CH-XXX/
    ASSUMPTIONS.md   # written BEFORE coding
    notes.md         # design sketch, decisions, trade-offs, reflection
    <source files>
    <tests>
```
