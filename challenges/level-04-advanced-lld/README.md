# Chapter 4 — Advanced LLD

**Goal:** design extensible, decoupled systems.

**Concepts:** observer / events · dependency inversion · plugin boundaries · workflow &
rule engines · job processing · idempotency · distributed-lock abstraction.

## Challenges

| ID | Title | Type | Status |
|----|-------|------|--------|
| [CH-018](CH-018-event-bus.md) | Event Bus | Design + Implementation | not started |
| [CH-019](CH-019-workflow-engine.md) | Workflow Engine | Design + Implementation | not started |
| [CH-020](CH-020-rule-engine.md) | Rule Engine | Design + Implementation | not started |
| [CH-021](CH-021-notification-platform.md) | Notification Platform | Design + Implementation | not started |
| [CH-022](CH-022-plugin-architecture.md) | Plugin Architecture | Design + Implementation | not started |
| [CH-023](CH-023-job-processing-system.md) | Job Processing System | Design + Implementation | not started |
| [CH-024](CH-024-idempotent-command-processing.md) | Idempotent Command Processing | Design + Implementation | not started |

**You practice:** adding new capabilities without editing the core, and reasoning about
asynchronous flow, ordering, and repeated delivery.

**Move on when:** you can add a new capability without editing the core — and you know why.

[← Level 3](../level-03-intermediate-lld/) · next: [Level 5 →](../level-05-system-design/)
