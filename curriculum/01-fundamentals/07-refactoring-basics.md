# 7. Refactoring basics

- **Track:** fundamentals
- **Prereqs:** 1–6
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Make small, **behavior-preserving** changes; leave the code clearer after each one. Extract,
rename, remove duplication, use guard clauses.

## Drill — do this alone

Refactor this method in **small steps**, keeping a test green after *each* step. No behavior
change.

```python
def calc(user, items):
    r = 0
    if user is not None:
        if user["vip"] is True:
            for i in items:
                if i["type"] == "book":
                    r = r + i["price"] * 0.8
                else:
                    r = r + i["price"] * 0.9
        else:
            for i in items:
                r = r + i["price"]
    else:
        r = -1
    return r
```

Do at least: write a test first, replace magic numbers with named constants, extract a
pricing function, and replace the nested `if` with guard clauses / early returns.

## Done when

- [ ] I wrote a test **before** refactoring and it stayed green.
- [ ] Each change was small and reversible.
- [ ] Duplication removed; names reveal intent; nesting reduced.
- [ ] Behavior is identical (I can prove it).

## Reflection

- Which refactorings were safest? Which felt risky, and why?
- Did I change structure and behavior at the same time? (You never should.)

## Theory & resources

- Refactoring = changing structure without changing behavior, in tiny steps, with tests.
- Resources: *Refactoring* (Fowler) — a catalog of named refactorings.
