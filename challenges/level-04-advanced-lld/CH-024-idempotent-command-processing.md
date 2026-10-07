# CH-024 — Idempotent Command Processing

- **Challenge ID:** CH-024
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~3–5 hours
- **Combines:** command · idempotency · error handling · concurrency basics · invariants
- **Prereqs (gates):** [`../../curriculum/03-design-patterns/13-command.md`](../../curriculum/03-design-patterns/13-command.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md) ·
  [`../../curriculum/04-lld-topics/08-concurrency-basics.md`](../../curriculum/04-lld-topics/08-concurrency-basics.md) ·
  [`../../curriculum/01-fundamentals/05-validation-and-fail-fast.md`](../../curriculum/01-fundamentals/05-validation-and-fail-fast.md)

## Why this problem

Idempotency is the antidote to the retries and duplicate delivery that every distributed system has.
Here it's isolated so you can learn the mechanism cleanly: an operation applied **exactly once**, even
though it is **submitted many times**.

## Requirements (deliberately a little ambiguous)

Apply **commands** so repeated submission is safe.

- Each command carries a unique **command id** and an operation to perform.
- Submitting the same command id **again** must **not** re-apply its effect.
- A duplicate submission should return the **same result** as the first (or a clear "already applied").
- The processor must be safe when two duplicates arrive **at the same time**.

## Deliberate ambiguities — YOU decide and justify

1. **Dedup storage:** where do you remember "already applied"? In memory? With what key, and for how
   long (a window)?
2. **Result replay:** must a duplicate return the *stored original result*, or is acknowledging enough?
   Justify.
3. **Concurrency:** two identical commands in flight — how do you ensure only one applies? What's the
   failure mode if you get it wrong?
4. **Recording order:** do you record "applied" **before** or **after** the effect, and what breaks in
   each case (crash between them)?
5. **Exactly-once vs at-least-once:** explain which one you actually deliver, and why "exactly-once"
   is usually marketing.

## Constraints

- **In-memory only**; the "effect" may be a counter or an append to a list so double-apply is visible.
- **No third-party dependencies.**
- Roughly **150–300 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the command, the processor, and the dedup/record seam.
3. **Implementation.**
4. **Tests** for first apply, duplicate apply (no second effect), stored-result replay, and a
   same-id concurrency case.
5. **Explanation** — your dedup model, the record-order decision, and an honest statement of the
   guarantee you provide.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: a duplicate provably does not double-apply, and you can articulate the exact guarantee.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-024/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
