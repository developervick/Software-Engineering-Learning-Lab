# Challenge Arena — combine concepts

Challenges are **Stage 5**: the **combination** stage. Each one integrates several concepts
you already drilled **alone** in [`../curriculum/`](../curriculum/). Do a challenge only when
the gates of the concepts it combines are met — see
[`../progress/concept-tracker.md`](../progress/concept-tracker.md).

One file per challenge: `CH-XXX-<slug>.md`.

## Levels

| Level | Folder | Focus |
|-------|--------|-------|
| 1 | [`level-01-fundamentals/`](level-01-fundamentals/) | Domain modeling, responsibilities, invariants |
| 2 | [`level-02-solid-and-basic-lld/`](level-02-solid-and-basic-lld/) | SOLID in practice, strategies, small LLD |
| 3 | [`level-03-intermediate-lld/`](level-03-intermediate-lld/) | State, rules, interactions |
| 4 | [`level-04-advanced-lld/`](level-04-advanced-lld/) | Extensible, decoupled systems |
| 5 | [`level-05-system-design/`](level-05-system-design/) | Persistence, concurrency, failure, scale |

Start at the lowest level you have **not** mastered. See [`../ROADMAP.md`](../ROADMAP.md).

## Challenge index

| ID | Title | Level | Type | Combines | Status |
|----|-------|-------|------|----------|--------|
| [CH-001](level-01-fundamentals/CH-001-vending-machine.md) | Vending Machine | 1 | Design + Implementation | fundamentals · state machine | not started |
| [CH-002](level-01-fundamentals/CH-002-coffee-shop-order.md) | Coffee Shop Order | 1 | Design + Implementation | classes · responsibilities · value objects | not started |
| [CH-003](level-01-fundamentals/CH-003-shopping-cart-checkout.md) | Shopping Cart Checkout | 1 | Design + Implementation | value objects · invariants · interfaces | not started |
| [CH-004](level-02-solid-and-basic-lld/CH-004-notification-system.md) | Notification System | 2 | Design + Implementation | SOLID · strategy · DI | not started |
| [CH-005](level-02-solid-and-basic-lld/CH-005-pricing-strategies.md) | Pricing Strategies | 2 | Design + Implementation | strategy · OCP | not started |
| [CH-006](level-02-solid-and-basic-lld/CH-006-payment-methods.md) | Payment Methods | 2 | Design + Implementation | LSP · DIP · error handling | not started |
| [CH-007](level-02-solid-and-basic-lld/CH-007-file-storage-abstraction.md) | File Storage Abstraction | 2 | Design + Implementation | ISP · DIP · adapter | not started |
| [CH-008](level-02-solid-and-basic-lld/CH-008-report-generation.md) | Report Generation | 2 | Design + Implementation | SRP · template method | not started |
| [CH-009](level-02-solid-and-basic-lld/CH-009-simple-booking.md) | Simple Booking | 2 | Design + Implementation | fundamentals · light state machine | not started |
| [CH-010](level-03-intermediate-lld/CH-010-parking-lot.md) | Parking Lot | 3 | Design + Implementation | state · strategy · invariants | not started |
| [CH-011](level-03-intermediate-lld/CH-011-elevator.md) | Elevator | 3 | Design + Implementation | state · scheduling | not started |
| [CH-012](level-03-intermediate-lld/CH-012-library-system.md) | Library System | 3 | Design + Implementation | entities · strategy · observer | not started |
| [CH-013](level-03-intermediate-lld/CH-013-food-ordering.md) | Food Ordering | 3 | Design + Implementation | state · command · pricing | not started |
| [CH-014](level-03-intermediate-lld/CH-014-inventory.md) | Inventory | 3 | Design + Implementation | invariants · observer · concurrency | not started |
| [CH-015](level-03-intermediate-lld/CH-015-ride-booking.md) | Ride Booking | 3 | Design + Implementation | state · strategy · concurrency | not started |
| [CH-016](level-03-intermediate-lld/CH-016-rate-limiter.md) | Rate Limiter | 3 | Design + Implementation | concurrency · strategy | not started |
| [CH-017](level-03-intermediate-lld/CH-017-task-scheduler.md) | Task Scheduler | 3 | Design + Implementation | scheduling · concurrency | not started |
| [CH-018](level-04-advanced-lld/CH-018-event-bus.md) | Event Bus | 4 | Design + Implementation | observer · plugin seams | not started |
| [CH-019](level-04-advanced-lld/CH-019-workflow-engine.md) | Workflow Engine | 4 | Design + Implementation | state · command · seams | not started |
| [CH-020](level-04-advanced-lld/CH-020-rule-engine.md) | Rule Engine | 4 | Design + Implementation | OCP · composite | not started |
| [CH-021](level-04-advanced-lld/CH-021-notification-platform.md) | Notification Platform | 4 | Design + Implementation | OCP · layering · plugins | not started |
| [CH-022](level-04-advanced-lld/CH-022-plugin-architecture.md) | Plugin Architecture | 4 | Design + Implementation | plugin seams · DIP · ISP | not started |
| [CH-023](level-04-advanced-lld/CH-023-job-processing-system.md) | Job Processing System | 4 | Design + Implementation | concurrency · command · dead-letter | not started |
| [CH-024](level-04-advanced-lld/CH-024-idempotent-command-processing.md) | Idempotent Command Processing | 4 | Design + Implementation | command · idempotency | not started |
| [CH-025](level-05-system-design/CH-025-url-shortener-slice.md) | URL Shortener Slice | 5 | Design + Implementation + Failure | layering · caching · failure | not started |
| [CH-026](level-05-system-design/CH-026-order-pipeline-retries-idempotency.md) | Order Pipeline (Retries & Idempotency) | 5 | Design + Implementation + Failure | queue · retries · idempotency | not started |
| [CH-027](level-05-system-design/CH-027-notification-delivery-dlq.md) | Notification Delivery (with Dead-Letter) | 5 | Design + Implementation + Failure | queue · retries · dead-letter | not started |
| [CH-028](level-05-system-design/CH-028-distributed-rate-limiter.md) | Distributed Rate Limiter | 5 | Design + Implementation + Failure + Trade-off | concurrency · failure · trade-offs | not started |
| [CH-029](level-05-system-design/CH-029-metrics-ingest-backpressure.md) | Metrics Ingest (Backpressure) | 5 | Design + Implementation + Failure + Trade-off | queue · backpressure · failure | not started |

## Conventions

- Every challenge documents: **ID · title · level · type · concepts · prereqs · requirements ·
  constraints · deliverables · evaluation criteria**.
- Every challenge lists the **Prereqs** (concept gates that must be met first) and what it
  **Combines**.
- Requirements may be **intentionally ambiguous** — resolving them is part of the exercise.
- The challenge file **never contains the solution**.
- New challenges start from [`_template.md`](_template.md).

## Submitting work

Put your solution in [`solutions/CH-XXX/`](solutions/):

```
solutions/CH-XXX/
    ASSUMPTIONS.md   # written BEFORE coding
    notes.md         # design sketch, decisions, trade-offs, reflection
    <source files>
    <tests>
```
