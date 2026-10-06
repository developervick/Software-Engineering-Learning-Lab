# Coupling & dependency direction

- **Track:** lld-topics
- **Prereqs:** fundamentals 3–4, SOLID DIP
- **Status:** not-started
- **Est. time:** 60 min

## Goal

See coupling as a **direction**, not a yes/no. Stable policy should not depend on volatile
detail.

## Drill — do this alone

Take (or write) a tiny module where a `PricingPolicy` imports a `StripeClient` and a
`PostgresRepo`. **Map every dependency arrow** on paper. Identify which arrows point from
stable policy toward volatile detail (wrong way). Invert them so arrows point **toward**
policy.

## Done when

- [ ] I drew the dependency graph, with arrow directions.
- [ ] I identified ≥2 arrows pointing the wrong way.
- [ ] After refactor, high-level policy has **no** import of any concrete I/O class.
- [ ] I can explain "stable" vs "volatile" in my own words for this code.

## Reflection

- Which dependency is hardest to reverse, and why?
- Is zero coupling a goal? (No — *appropriate* coupling is.)

## Theory & resources

- Acyclic dependencies; stable-dependencies principle; ports-and-adapters.
- Resources: *Clean Architecture* (boundaries), *A Philosophy of Software Design*.
