# 5. Validation & fail-fast

- **Track:** fundamentals
- **Prereqs:** 1, 2
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Reject bad input **early**, at the boundary, with errors a human can act on — and tell the
difference between a **programming error** and a **domain error**.

## Drill — do this alone

Harden this function. For each failure, decide whether it should be a validation error the
caller handles, or an exception that means "bug". Document your choice.

```python
def transfer(from_acct, to_acct, amount):
    from_acct.balance -= amount
    to_acct.balance += amount
```

Cover: negative/zero amount, insufficient funds, missing accounts, same account, currency
mismatch. Also: what happens if the credit step fails after the debit succeeds?

## Done when

- [ ] All inputs validated **before** any state changes.
- [ ] Each failure maps to a clear error type/message.
- [ ] I can explain which failures are "caller's problem" vs "bug".
- [ ] I noticed the **partial-failure** issue (debit without credit) and said how I'd prevent it.
- [ ] No silent failure; no catch-and-ignore.

## Reflection

- Where should validation live — the boundary, the entity, or both?
- Did I distinguish "invalid input" from "impossible state"?

## Theory & resources

- Fail fast; validate at boundaries; prefer explicit errors over sentinel values.
- Resources: *Clean Code* (error handling), *The Pragmatic Programmer* ("crash early").
