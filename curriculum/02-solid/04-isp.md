# ISP — Interface Segregation Principle

- **Track:** solid
- **Prereqs:** SRP, LSP
- **Status:** not-started
- **Est. time:** 45–60 min

## Goal

No client should be forced to depend on methods it doesn't use. Prefer **several small,
role-specific interfaces** over one fat one.

## Drill — do this alone

Every machine is forced to implement `print`/`scan`/`fax` even when it can't. Write one
implementation that proves the pain (a method that must `throw NotImplemented`), then split
the interface into roles and make each machine implement only what it does.

```python
class MultiFunctionDevice:
    def print(self): ...
    def scan(self): ...
    def fax(self): ...

class BasicPrinter(MultiFunctionDevice):
    def print(self): ...
    def scan(self):  raise NotImplementedError   # forced, but meaningless
    def fax(self):   raise NotImplementedError
```

## Done when

- [ ] No client/implementation is forced to implement a method it can't meaningfully support.
- [ ] Interfaces are split by **role/client need**, not by class.
- [ ] I can name the client(s) that motivated each new interface.
- [ ] No `NotImplementedError` / empty overrides remain in the implementations.

## Reflection

- Did I split by "what a client needs" or by "what felt tidy"? Does it matter?
- Is a 1-method interface too small here? When is that fine?

## Theory & resources

- ISP = "make interfaces client-specific." It's SRP applied to interface boundaries.
- Resources: *Clean Architecture* (ISP), *Agile Software Development* (Martin).
