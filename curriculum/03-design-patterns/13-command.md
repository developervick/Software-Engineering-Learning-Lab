# Command

- **Track:** design-patterns · behavioral
- **Prereqs:** fundamentals 4
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Encapsulate a **request as an object**, so you can parameterize, queue, log, and **undo**
operations.

## Drill — do this alone

Build a simple text editor supporting `insert`, `delete`, and **undo/redo**. Each edit is a
`Command` object with `execute()` and `undo()`. Keep a history stack so undo/redo work
correctly across mixed operations.

## Done when

- [ ] Each operation is a command object (not just a method call).
- [ ] `undo()` reverses `execute()` **exactly**, including edge cases (undo an insert in the
      middle; redo after a new edit clears the redo stack).
- [ ] The invoker (history) doesn't know what the commands do.
- [ ] I can add a new command without changing the history/invoker.

## When NOT to use it

- No undo/queue/logging needed — a direct method call is simpler.
- Every "command" is a one-liner with no state; the wrapper adds nothing.

## Reflection

- Should undo be the command's job, or the receiver's? What breaks if state is captured
  poorly?
- Command vs Strategy: both wrap behavior. What does the *invoker/queue* angle add?

## Theory & resources

- Resources: *Design Patterns* (GoF, Command), examples of command queues/undo stacks.
