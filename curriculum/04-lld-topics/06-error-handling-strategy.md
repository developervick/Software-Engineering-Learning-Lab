# Error-handling strategy

- **Track:** lld-topics
- **Prereqs:** fundamentals 5
- **Status:** not-started
- **Est. time:** 60 min

## Goal

Choose a **consistent** way to signal and handle failure across a boundary: exceptions vs
result types, where to catch, what to log, what to rethrow.

## Drill — do this alone

Take a feature that does an HTTP call + a DB write. Decide and **document** your strategy:

- which failures are **expected** (validation, "not found") vs **exceptional** (bugs, outages),
- who catches what, and at which layer,
- what gets logged, what gets translated for the caller,
- how you avoid catch-and-ignore and catch-and-rethrow noise.

Then implement it and write tests for the "expected" failure paths.

## Done when

- [ ] Expected vs exceptional failures are treated differently, on purpose.
- [ ] No `catch` block silently swallows an error.
- [ ] Errors crossing a layer boundary are translated to something meaningful for that layer.
- [ ] The caller can distinguish "retryable" vs "fatal" vs "user error".
- [ ] Logging happens **once**, at the right level (not at every layer).

## Reflection

- Did I use exceptions for control flow? Was that justified?
- Where is the single place that turns a technical error into a user-facing message?

## Theory & resources

- Resources: *Clean Code* (error handling), "Railway oriented programming"/Result types.
