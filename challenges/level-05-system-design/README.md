# Chapter 5 — System design + implementation

**Goal:** combine everything across process and network boundaries.

**Concepts:** persistence · caching · queues · retries · idempotency · observability ·
failure handling · API design · scale.

**Example challenges (not yet written):** end-to-end "design + build a slice" projects with
faults injected (a dependency that fails, a duplicate message, a slow downstream).

**You practice:** making decisions that hold up when parts are remote, unreliable, and slow.

**Move on when:** you instinctively ask the senior-engineer question set — what changes?
what stays stable? who owns this? what depends on what? what happens when it fails? how do I
test it? what trade-off am I making?

[← Level 4](../level-04-advanced-lld/) · [Roadmap](../../ROADMAP.md)
