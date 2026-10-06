# Trade-off analysis

- **Track:** lld-topics
- **Prereqs:** all previous
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Be able to **defend a design choice against a simpler alternative** in writing. Good engineers
don't pick the "best" pattern; they pick the design whose costs they can live with.

## Drill — do this alone

Pick one earlier exercise you solved with a pattern (e.g. Strategy or Observer). Write a
**one-page decision record**:

1. The problem and the forces at play (requirements, constraints, expected changes).
2. **Option A** — the simple/no-pattern solution. **Option B** — the patterned solution.
3. Costs and benefits of each (readability, testability, extension cost, cognitive load).
4. Your decision + the **conditions under which you'd reverse it**.

## Done when

- [ ] I named a genuinely **simpler** alternative (not a strawman).
- [ ] I listed concrete costs of the pattern I chose, not just benefits.
- [ ] I stated a **falsifiable trigger** for revisiting the decision.
- [ ] Someone else could disagree with me using my own document.

## Reflection

- Did I choose the pattern because it fit, or because it's familiar/prestigious?
- What's the smallest change to requirements that flips my decision?

## Theory & resources

- Architecture Decision Records (ADRs); "reversibility" as a design criterion.
- Resources: *A Philosophy of Software Design*, ADR articles.
