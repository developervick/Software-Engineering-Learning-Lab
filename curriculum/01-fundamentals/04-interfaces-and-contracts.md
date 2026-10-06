# 4. Interfaces & contracts

- **Track:** fundamentals
- **Prereqs:** 1, 3
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Depend on an **abstraction** (what) rather than a concrete class (how).

## Drill — do this alone

`ReportService` is welded to a concrete database. Introduce an interface for the data source,
implement **two** different implementations (a real one and an in-memory one), and make
`ReportService` accept either.

```python
class PostgresDb:
    def query(self, sql):
        return [...]          # concrete

class ReportService:
    def __init__(self):
        self.db = PostgresDb()   # welded to one implementation

    def monthly(self):
        return self.db.query("select ...")
```

## Done when

- [ ] `ReportService` depends on an interface, not on `PostgresDb`.
- [ ] Two implementations satisfy the same interface.
- [ ] Swapping implementations is a one-line change at the composition root.
- [ ] The interface names **intent** (`DataSource.find_orders`) not mechanism (`query_sql`).

## Reflection

- How small did I keep the interface? Could it be smaller?
- What did the interface *hide* that callers should not know?

## Theory & resources

- A contract = the promises a type makes. Keep interfaces **narrow** and **intent-revealing**.
- Resources: *Clean Architecture*, *Head First Design Patterns*.
