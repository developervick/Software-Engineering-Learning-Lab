# CH-007 — File Storage Abstraction

- **Challenge ID:** CH-007
- **Level:** 2 (SOLID & basic LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~2–3 hours
- **Combines:** ISP · DIP · adapter · interfaces & contracts · error handling
- **Prereqs (gates):** [`../../curriculum/02-solid/04-isp.md`](../../curriculum/02-solid/04-isp.md) ·
  [`../../curriculum/02-solid/05-dip.md`](../../curriculum/02-solid/05-dip.md) ·
  [`../../curriculum/03-design-patterns/05-adapter.md`](../../curriculum/03-design-patterns/05-adapter.md) ·
  [`../../curriculum/01-fundamentals/04-interfaces-and-contracts.md`](../../curriculum/01-fundamentals/04-interfaces-and-contracts.md)

## Why this problem

Two forces pull in opposite directions here: callers want **one simple storage API**, while different
backends support **different subsets** of operations (local disk can list; a write-only sink cannot).
This is where **ISP** stops being a slogan and becomes a design decision about how many small
interfaces to expose.

## Requirements (deliberately a little ambiguous)

Give an application file storage that it can swap without changing callers.

- The app must be able to **save** a named blob and **load** it back.
- Some callers also need to **delete** and **list** what is stored.
- Backends: at least a **local/in-memory** store and one **second** backend with a **different
  capability set** (e.g. append-only, or no listing).
- Adding a backend must not change existing callers or force backends to implement operations they
  can't support.

## Deliberate ambiguities — YOU decide and justify

1. **Interface granularity:** one big `Storage` interface, or several small ones (`Reader`, `Writer`,
   `Lister`, …)? Which callers depend on which? (ISP test: does any implementation throw "not
   supported"?)
2. **Identifier model:** are blobs addressed by a path-like string or an opaque id? Who validates it?
3. **Error model:** how does a missing blob surface — exception, optional/none, or result?
4. **Write semantics:** overwrite? atomic? what happens on a partial write failure?
5. **Listing:** return everything, page, or stream? (Consider very large stores.)

## Constraints

- **In-memory / local only.** No real cloud SDKs.
- **No third-party dependencies.**
- Roughly **120–250 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the interfaces, their consumers, and the dependency direction.
3. **Implementation** (including the second, differently-capable backend).
4. **Tests** proving each backend satisfies only the interfaces it can, and callers still work.
5. **Explanation** — how ISP and DIP shaped your boundaries; what you'd change to add a caching
   backend.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: interface segregation done for a reason, dependency arrows pointing inward, and a
  backend that never has to lie about its capabilities.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-007/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
