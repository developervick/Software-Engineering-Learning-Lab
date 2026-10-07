# Chapter 5 — System design + implementation

**Goal:** combine everything across process and network boundaries.

**Concepts:** persistence · caching · queues · retries · idempotency · observability ·
failure handling · API design · scale.

## Challenges

| ID | Title | Type | Status |
|----|-------|------|--------|
| [CH-025](CH-025-url-shortener-slice.md) | URL Shortener Slice | Design + Implementation + Failure | not started |
| [CH-026](CH-026-order-pipeline-retries-idempotency.md) | Order Pipeline (Retries & Idempotency) | Design + Implementation + Failure | not started |
| [CH-027](CH-027-notification-delivery-dlq.md) | Notification Delivery (with Dead-Letter) | Design + Implementation + Failure | not started |
| [CH-028](CH-028-distributed-rate-limiter.md) | Distributed Rate Limiter | Design + Implementation + Failure + Trade-off | not started |
| [CH-029](CH-029-metrics-ingest-backpressure.md) | Metrics Ingest (Backpressure) | Design + Implementation + Failure + Trade-off | not started |

**You practice:** making decisions that hold up when parts are remote, unreliable, and slow.

**Move on when:** you instinctively ask the senior-engineer question set — what changes?
what stays stable? who owns this? what depends on what? what happens when it fails? how do I
test it? what trade-off am I making?

[← Level 4](../level-04-advanced-lld/) · [Roadmap](../../ROADMAP.md)
