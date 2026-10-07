# CH-022 — Plugin Architecture

- **Challenge ID:** CH-022
- **Level:** 4 (advanced LLD)
- **Type:** Design + Implementation
- **Language:** your choice (Python is a fine default)
- **Status:** not started
- **Estimated effort:** ~4–6 hours
- **Combines:** extensibility & plugin seams · DIP · ISP · trade-off analysis
- **Prereqs (gates):** [`../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md`](../../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md) ·
  [`../../curriculum/02-solid/05-dip.md`](../../curriculum/02-solid/05-dip.md) ·
  [`../../curriculum/02-solid/04-isp.md`](../../curriculum/02-solid/04-isp.md) ·
  [`../../curriculum/04-lld-topics/10-tradeoff-analysis.md`](../../curriculum/04-lld-topics/10-tradeoff-analysis.md)

## Why this problem

A plugin host is the purest form of "open for extension, closed for modification". It also tests
**boundary discipline**: the host must depend on small contracts, discover capabilities, and contain a
misbehaving plugin — without knowing any concrete plugin.

## Requirements (deliberately a little ambiguous)

Build a **host** that loads **plugins** and uses their capabilities.

- The host defines a small **capability contract** (interface) plugins implement.
- Plugins **register** themselves (or are discovered) and are invoked **by capability**, not by name.
- Adding a new plugin requires **no edits** to the host.
- A plugin that **fails** must not take down the host or the other plugins.

## Deliberate ambiguities — YOU decide and justify

1. **Discovery:** explicit registration, a registry/entry-point scan, or a directory convention? Pick
   one and justify for this scope.
2. **Contract size:** one fat interface or several small capabilities (ISP)? What does each plugin
   promise?
3. **Isolation:** if a plugin throws or loops, what's the blast radius, and how do you contain it?
4. **Lifecycle:** do plugins have `init`/`teardown`? Who calls them and when?
5. **Versioning:** how do you handle a plugin written against an older contract? Complain, adapt, or
   ignore?

## Constraints

- **In-memory only**; plugins are in-process classes (no real dynamic loading required — but note where
  it'd plug in).
- **No third-party dependencies.**
- Roughly **200–400 lines**.
- Must be **exercisable without a UI** (script or tests).

## Deliverables (in this order)

1. **Assumptions & scope** — written **before** you code.
2. **Design sketch** — the host, the capability contract(s), and the discovery/registry seam.
3. **Implementation** with **two** example plugins.
4. **Tests** for discovery, invocation by capability, adding a plugin without host edits, and a failing
   plugin isolated.
5. **Explanation** — discovery + isolation trade-offs, and what you'd change for out-of-process plugins.

## What I will evaluate

- **Correctness**, **design**, **simplicity**, **extensibility**, **testability**, **maintainability**,
  **engineering judgment**, and **learning**.
- Specifically: host depends only on abstractions, plugins are additive, and a bad plugin is contained.

## Suggested workflow

Restate → assumptions → sketch → implement → test → explain. Put your work in
`challenges/solutions/CH-022/`. Say **"done"** for a review. No solution first.

## Assistance ladder

**hint → direction → design review → partial → full** — name the level you want.
