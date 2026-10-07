# CH-025 — URL Shortener Slice

- **Challenge ID:** CH-025
- **Level:** 5 (system design + implementation)
- **Type:** Design + Implementation + Failure
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** layering · persistence · caching · idempotency · failure handling · API design · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/03-layering.md`](../../curriculum/04-lld-topics/03-layering.md) ·
  [`../../curriculum/04-lld-topics/06-error-handling-strategy.md`](../../curriculum/04-lld-topics/06-error-handling-strategy.md) ·
  [`../../curriculum/04-lld-topics/10-tradeoff-analysis.md`](../../curriculum/04-lld-topics/10-tradeoff-analysis.md) ·
  [`../../curriculum/02-solid/05-dip.md`](../../curriculum/02-solid/05-dip.md)

## Why this problem

This is the first **"design + build a slice"** project. It's familiar enough to not fight the domain,
so all your attention goes to the **boundaries**: the API, the store behind an interface, a cache in
front of it, and what happens when the store is slow or down.

## Requirements (deliberately a little ambiguous)

Build the core of a URL shortener.

- `shorten(url, [alias]) -> short_code` and `resolve(short_code) -> url`.
- Codes must be **unique**; an optional **custom alias** may be requested.
- Links may **expire** after a TTL.
- Keep a **store** behind an interface; put a **cache** in front of it.
- Provide the ability to simulate a **slow or failing** store so the failure path is exercised.

## Deliberate ambiguities — YOU decide and justify

1. **Code generation:** random, counter-with-encoding, or hash-based? How do you handle **collisions**
   and how do you keep them rare?
2. **Cache strategy:** cache-aside vs write-through, eviction policy, and **invalidation on expiry**
   — what's your approach?
3. **API/HTTP semantics:** for a redirect, 301 vs 302 (permanent vs temporary) — which, and why does it
   matter with analytics?
4. **Failure behavior:** if the store is down on `shorten`, what does the API return? If it's down on
   `resolve`, do you serve a stale cache or fail? Define it.
5. **Expiry semantics:** is an expired code an error, a 404, or a redirect elsewhere?

## Constraints

- **Single process, in-memory store** is fine — but keep it **behind an interface** so it can be
  swapped. **No real network.**
- **No third-party dependencies** (hand-roll any tiny encoding).
- Roughly **250–450 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code (including the API contract).
2. **Design sketch** — the layers (API → service → store) and the cache boundary.
3. **Implementation** with a "slow/failing store" switch.
4. **Tests** for shorten/resolve, alias collisions, expiry, a cache hit, and a store-down path.
5. **Explanation** — your failure and caching decisions, and what you'd change to run this across many
   machines.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: clean layer boundaries, a dependency-inverted store, and behavior you can defend when
  the store misbehaves.

## Suggested workflow

Restate → assumptions (+ API contract) → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-025/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
