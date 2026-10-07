# Concept tracker

Every concept on the concept-first path, with its **mastery status**. Update the row the
moment a concept's gate (in its file under [`../curriculum/`](../curriculum/)) is met.

**Status values:** `not-started` → `learning` → `drilled ✓` → `can-explain` → `can-teach`

> Be honest. `drilled ✓` means you did the drill alone and passed the gate — not that you read
> the file. `can-teach` means you could explain it and its "when NOT to use" to someone else.

## Stage 1 — Fundamentals (`curriculum/01-fundamentals/`)

| Concept | Status | Date | Evidence / notes |
|---|---|---|---|
| Classes & objects (and methods) | not-started | | |
| Responsibilities & cohesion | not-started | | |
| Encapsulation | not-started | | |
| Composition vs inheritance | not-started | | |
| Interfaces & contracts | not-started | | |
| Validation & fail-fast | not-started | | |
| Value objects vs entities | not-started | | |
| Refactoring basics | not-started | | |

## Stage 2 — SOLID (`curriculum/02-solid/`)

| Concept | Status | Date | Evidence / notes |
|---|---|---|---|
| SRP | not-started | | |
| OCP | not-started | | |
| LSP | not-started | | |
| ISP | not-started | | |
| DIP | not-started | | |

## Stage 3 — Design patterns (`curriculum/03-design-patterns/`)

| Concept | Status | Date | Evidence / notes |
|---|---|---|---|
| Factory Method | not-started | | |
| Abstract Factory | not-started | | |
| Builder | not-started | | |
| Singleton (anti-pattern talk) | not-started | | |
| Adapter | not-started | | |
| Decorator | not-started | | |
| Facade | not-started | | |
| Composite | not-started | | |
| Proxy | not-started | | |
| Strategy | not-started | | |
| Observer | not-started | | |
| State | not-started | | |
| Command | not-started | | |
| Template Method | not-started | | |
| Iterator | not-started | | |

## Stage 4 — LLD topics (`curriculum/04-lld-topics/`)

| Concept | Status | Date | Evidence / notes |
|---|---|---|---|
| Coupling & dependency direction | not-started | | |
| Dependency injection | not-started | | |
| Layering & separation of concerns | not-started | | |
| State machines | not-started | | |
| Immutability | not-started | | |
| Error-handling strategy | not-started | | |
| Testability & seams | not-started | | |
| Concurrency basics | not-started | | |
| Extensibility & plugin seams | not-started | | |
| Trade-off analysis | not-started | | |

## Stage 5 — Challenges (combine concepts)

Tracked separately once Stage 1–4 gates needed by a challenge are met. See
[`../challenges/README.md`](../challenges/README.md).

| Challenge | Combines | Status |
|---|---|---|
| [CH-001 Vending Machine](../challenges/level-01-fundamentals/CH-001-vending-machine.md) | fundamentals + state machine + validation | not started |
| [CH-002 Coffee Shop Order](../challenges/level-01-fundamentals/CH-002-coffee-shop-order.md) | responsibilities + encapsulation + value objects | not started |
| [CH-003 Shopping Cart Checkout](../challenges/level-01-fundamentals/CH-003-shopping-cart-checkout.md) | value objects + invariants + interfaces | not started |
| [CH-004 Notification System](../challenges/level-02-solid-and-basic-lld/CH-004-notification-system.md) | SOLID + strategy + DI | not started |
| [CH-005 Pricing Strategies](../challenges/level-02-solid-and-basic-lld/CH-005-pricing-strategies.md) | strategy + OCP | not started |
| [CH-006 Payment Methods](../challenges/level-02-solid-and-basic-lld/CH-006-payment-methods.md) | LSP + DIP + error handling | not started |
| [CH-007 File Storage Abstraction](../challenges/level-02-solid-and-basic-lld/CH-007-file-storage-abstraction.md) | ISP + DIP + adapter | not started |
| [CH-008 Report Generation](../challenges/level-02-solid-and-basic-lld/CH-008-report-generation.md) | SRP + template method | not started |
| [CH-009 Simple Booking](../challenges/level-02-solid-and-basic-lld/CH-009-simple-booking.md) | fundamentals + light state machine | not started |
| [CH-010 Parking Lot](../challenges/level-03-intermediate-lld/CH-010-parking-lot.md) | state + strategy + invariants | not started |
| [CH-011 Elevator](../challenges/level-03-intermediate-lld/CH-011-elevator.md) | state + scheduling | not started |
| [CH-012 Library System](../challenges/level-03-intermediate-lld/CH-012-library-system.md) | entities + strategy + observer | not started |
| [CH-013 Food Ordering](../challenges/level-03-intermediate-lld/CH-013-food-ordering.md) | state + command + pricing | not started |
| [CH-014 Inventory](../challenges/level-03-intermediate-lld/CH-014-inventory.md) | invariants + observer + concurrency | not started |
| [CH-015 Ride Booking](../challenges/level-03-intermediate-lld/CH-015-ride-booking.md) | state + strategy + concurrency | not started |
| [CH-016 Rate Limiter](../challenges/level-03-intermediate-lld/CH-016-rate-limiter.md) | concurrency + strategy | not started |
| [CH-017 Task Scheduler](../challenges/level-03-intermediate-lld/CH-017-task-scheduler.md) | scheduling + concurrency | not started |
| [CH-018 Event Bus](../challenges/level-04-advanced-lld/CH-018-event-bus.md) | observer + plugin seams | not started |
| [CH-019 Workflow Engine](../challenges/level-04-advanced-lld/CH-019-workflow-engine.md) | state + command + seams | not started |
| [CH-020 Rule Engine](../challenges/level-04-advanced-lld/CH-020-rule-engine.md) | OCP + composite | not started |
| [CH-021 Notification Platform](../challenges/level-04-advanced-lld/CH-021-notification-platform.md) | OCP + layering + plugins | not started |
| [CH-022 Plugin Architecture](../challenges/level-04-advanced-lld/CH-022-plugin-architecture.md) | plugin seams + DIP + ISP | not started |
| [CH-023 Job Processing System](../challenges/level-04-advanced-lld/CH-023-job-processing-system.md) | concurrency + command + dead-letter | not started |
| [CH-024 Idempotent Command Processing](../challenges/level-04-advanced-lld/CH-024-idempotent-command-processing.md) | command + idempotency | not started |
| [CH-025 URL Shortener Slice](../challenges/level-05-system-design/CH-025-url-shortener-slice.md) | layering + caching + failure | not started |
| [CH-026 Order Pipeline](../challenges/level-05-system-design/CH-026-order-pipeline-retries-idempotency.md) | queue + retries + idempotency | not started |
| [CH-027 Notification Delivery](../challenges/level-05-system-design/CH-027-notification-delivery-dlq.md) | queue + retries + dead-letter | not started |
| [CH-028 Distributed Rate Limiter](../challenges/level-05-system-design/CH-028-distributed-rate-limiter.md) | concurrency + failure + trade-offs | not started |
| [CH-029 Metrics Ingest](../challenges/level-05-system-design/CH-029-metrics-ingest-backpressure.md) | queue + backpressure + failure | not started |

[← Progress](README.md)
