# Proxy

- **Track:** design-patterns · structural
- **Prereqs:** fundamentals 4
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Provide a **stand-in** for another object to **control access** to it — lazy creation,
permission checks, caching, or remote/network indirection.

## Drill — do this alone

`Image` loads a large file on construction — expensive when there are hundreds. Add a
**virtual proxy** that opens the real image only on first `display()`. Then extend the idea to
a **protection proxy** that blocks `display()` for unauthorized users.

## Done when

- [ ] The proxy implements the same interface as the real subject.
- [ ] The real object is created **lazily** (prove it — no load until first use).
- [ ] The client is unchanged and doesn't know it holds a proxy.
- [ ] The proxy's added concern (lazy / auth / cache) is isolated to the proxy.

## When NOT to use it

- You just need a simple wrapper once — a plain delegating class is clearer.
- The "proxy" is doing real business logic; then it isn't a proxy anymore.

## Reflection

- Proxy vs Decorator vs Adapter — all wrap the same interface. What distinguishes the **intent**?
- Did my proxy respect the subject's contract (LSP)?

## Theory & resources

- Resources: *Design Patterns* (GoF, Proxy), articles on lazy-loading proxies and ORMs.
