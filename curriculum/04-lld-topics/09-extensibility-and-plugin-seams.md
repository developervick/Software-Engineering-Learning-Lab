# Extensibility & plugin seams

- **Track:** lld-topics
- **Prereqs:** SOLID OCP/DIP, coupling & direction
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Decide where the design should be **open to extension** — and, deliberately, where it should
**not** be. Extensibility has a cost.

## Drill — do this alone

Take a small pipeline (e.g. "process an order": validate → price → persist → notify). Make
**one** step pluggable (say, notification channels: email/SMS/push) via a registration seam,
so adding a channel needs no edit to the pipeline. Leave the other steps fixed — and write a
short paragraph on **why you chose that step and not the others**.

## Done when

- [ ] The chosen step is extensible via registration/interface (no edit to the pipeline).
- [ ] I justified why the *other* steps are intentionally **not** pluggable.
- [ ] Adding a new plugin is a single new file + one registration line.
- [ ] I can name the cost I accepted (indirection, harder navigation).

## Reflection

- "We might need it someday" — how do I avoid speculative generality?
- What's the signal that a hard-coded step should *become* a seam (not before)?

## Theory & resources

- Rule of three; YAGNI vs. designing for the known axes of change.
- Resources: *Clean Architecture*, *A Philosophy of Software Design*.
