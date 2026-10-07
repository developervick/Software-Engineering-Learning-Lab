# How to use this repo

## The concept loop (Stages 1–4)

Before challenges, you drill concepts **one at a time** in [`../curriculum/`](../curriculum/):

```
Concept
  → read the Goal
  → do the Drill ALONE
  → pass the Done-when gate
  → record the reflection
  → mark it in progress/concept-tracker.md
```

The concept file **never** contains the solution. Move on only when its gate is met.

## The challenge loop (Stages 5–6)

Every challenge runs the same loop:

```
Challenge
  → restate the requirements
  → state your assumptions
  → identify the invariants
  → design
  → implement
  → run tests
  → debug
  → refactor
  → explain your decisions
  → get a review
```

Only **after your own attempt** does AI get involved — and only as far as you ask.

## The AI assistance ladder

| Level | You get |
|-------|---------|
| 0 | The problem only *(default)* |
| 1 | A clarifying question |
| 2 | A small conceptual hint |
| 3 | A direction / design consideration |
| 4 | A review of your design or code |
| 5 | A partial solution (only the concept you're stuck on) |
| 6 | The complete solution (only when you explicitly ask) |

Say which level you want. "I'm stuck" alone does **not** unlock the next level.

## Rules for yourself

- Attempt first. **Struggle is the training**, not a failure.
- State assumptions **before** coding.
- Prefer the **simplest design** that meets the real requirements.
- Don't add an abstraction you can't justify with a concrete, likely change.
- Always provide a way to **run/test** the behavior.
- **Explain your decisions** — the explanation is half the work.

## Where things go

| Output | Destination |
|--------|-------------|
| A solution | `challenges/solutions/CH-XXX/` |
| A concept note (only *after* a challenge) | `notes/` |
| A recurring mistake (log the 3rd time) | `mistakes/` |
| A reflection | `journal/CH-XXX.md` |
| A term you can't define | `docs/glossary.md` (meaning + example + mini-practice) |
| Concept mastery update | `progress/concept-tracker.md` |
| Capability update | `progress/capabilities.md` |
| A gap / weakness | `progress/gaps.md` |

## If you're a newcomer

You do not need to read everything. Do this:

1. Read `../ROADMAP.md`.
2. Start in `../curriculum/01-fundamentals/` — begin with `00-classes-and-objects.md`, do **one**
   concept's drill, then the next. Stuck on a word? Look it up in `../docs/glossary.md`.
3. Only after the relevant gates are met, do a challenge from `../challenges/`.

That's the whole idea: one starting point, one step at a time.
