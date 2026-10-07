# CH-008 — Report Generation

- **Challenge ID:** CH-008
- **Level:** 2 (SOLID & basic LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–3 hours
- **Combines:** SRP · template method · OCP · separation of concerns (data vs format) · facade
- **Prereqs (gates):** [`../../curriculum/02-solid/01-srp.md`](../../curriculum/02-solid/01-srp.md) ·
  [`../../curriculum/03-design-patterns/14-template-method.md`](../../curriculum/03-design-patterns/14-template-method.md) ·
  [`../../curriculum/02-solid/02-ocp.md`](../../curriculum/02-solid/02-ocp.md) ·
  [`../../curriculum/04-lld-topics/03-layering.md`](../../curriculum/04-lld-topics/03-layering.md)

## Why this problem

Reports mix two axes that change independently: **what data** (sales, inventory, …) and **what
format** (text, CSV, HTML). Beginners fuse them; good design keeps them orthogonal so `N` data kinds
and `M` formats give `N + M` pieces of code, not `N × M`.

## Requirements (deliberately a little ambiguous)

Generate reports from data.

- Support at least **two report kinds** (e.g. sales, inventory) and **two formats** (e.g. text, CSV).
- Generating a report for a kind in a format must not require touching other kinds/formats.
- A single entry point asks for "report X as format Y" and returns the rendered output.

## Deliberate ambiguities — YOU decide and justify

1. **The seam:** where exactly do "data" and "format" split? What is the stable skeleton and what do
   subclasses/strategies fill in?
2. **Headers/summaries:** are section headers, totals, and footers part of the *format* or the *data*?
3. **Large reports:** render fully into a string, or stream rows? Does that change the design?
4. **Unknown combination:** what happens for a kind+format you haven't implemented — error, fallback,
   or registration failure?
5. **Ownership:** who decides column order — the data kind or the formatter?

## Constraints

- **In-memory only**; sample data can be hard-coded fixtures.
- **No third-party dependencies** (no CSV/HTML libraries — hand-roll the tiny formatting).
- Roughly **120–220 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the data axis, the format axis, and the point where they meet.
3. **Implementation.**
4. **Tests** for each kind × format combination you support.
5. **Explanation** — argue why adding a third format touches only new code; what you'd change for a
   streaming JSON exporter.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: the orthogonality of the two axes, SRP on each class, and whether a new format is
  additive.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-008/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
