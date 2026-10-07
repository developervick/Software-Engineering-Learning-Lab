# Glossary — LLD terminology, in plain words

Every term here is defined **in the context of Low-Level Design (LLD)** — the meaning a
designer actually means, **not** the English-grammar meaning.

Each entry gives you four things:

- **In LLD terms** — the meaning you must be able to say out loud.
- **Example** — the smallest Python that shows it (some entries link to a fuller example).
- **Practice** — a mini challenge. The answer is **not** here.
- **See** — the concept file where you drill it fully, with its Done-when gate.

> **How to use this page:** don't read it front-to-back. When a concept file uses a word you
> can't define, look it up here, do the **Practice**, then go back to the concept.

## Contents

- [A. Building blocks](#a-building-blocks)
- [B. Fundamentals](#b-fundamentals)
- [C. SOLID](#c-solid)
- [D. Design patterns](#d-design-patterns)
- [E. LLD topics](#e-lld-topics)

[← Repo home](../README.md) · entry point: [START HERE →](../START-HERE.md)

---

## A. Building blocks

*(the words the whole lab is built on — full drill:
[Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md))*

### Class
- **In LLD terms:** a **blueprint** describing the data (attributes) and behavior (methods) of a
  kind of thing. It is a *type*, not a thing.
- **Example:** `class Account: ...`
- **Practice:** write two different classes (`Email`, `Money`) and one object of each.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md)

### Object (instance)
- **In LLD terms:** a **concrete thing created from a class**, holding its own copy of the
  instance data. Calling the class creates one.
- **Example:** `a = Account()` → `a` is an object; `Account` is the class.
- **Practice:** create two objects of one class and show they have **independent** state.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md)

### Attribute
- **In LLD terms:** **data** held by an object or by a class. An *instance* attribute belongs to
  one object; a *class* attribute is shared by all.
- **Example:**
  ```python
  class Account:
      currency = "USD"                      # class attribute (shared)
      def __init__(self): self.balance = 0  # instance attribute (per object)
  ```
- **Practice:** give a class one class attribute and one instance attribute, then show the class
  attribute is shared by every object.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md)

### Method & `self`
- **In LLD terms:** a **function inside a class** that acts on that object's data. `self` is the
  reference to *this* object — the first parameter of an instance method.
- **Example:** `def deposit(self, amt): self.balance += amt`
- **Practice:** add `deposit`/`withdraw` to a class and call them on an object.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md)

### Constructor
- **In LLD terms:** the method that **sets an object up** when it is created. In Python it is
  `__init__`.
- **Example:** `def __init__(self, balance): self.balance = balance`
- **Practice:** make a constructor that rejects invalid input so an object can't exist in a bad
  state.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md)

### Instance / class / static methods
- **In LLD terms:** three method kinds by *what they belong to*. **Instance** acts on one object
  (`self`); **class** acts on the class (`cls`, e.g. an alternative constructor); **static** needs
  neither — a helper that lives with the class for organization.
- **Example:**
  ```python
  class A:
      def inst(self): ...            # instance
      @classmethod
      def make(cls): return cls()    # class
      @staticmethod
      def helper(): return 42        # static
  ```
- **Practice:** for a `Money` class, write one of each kind — and explain why each is that kind.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md)

### Abstract method
- **In LLD terms:** a method **declared but not implemented** in a base type; subclasses **must**
  implement it. It defines a **contract** the base cannot satisfy by itself.
- **Example:**
  ```python
  from abc import ABC, abstractmethod
  class Shape(ABC):
      @abstractmethod
      def area(self): ...
  ```
- **Practice:** define an abstract `PaymentMethod.pay(amount)` and force two subclasses to
  implement it; show the base cannot be instantiated.
- **See:** [Classes & objects](../curriculum/01-fundamentals/00-classes-and-objects.md),
  [Interfaces & contracts](../curriculum/01-fundamentals/04-interfaces-and-contracts.md)

### Property (getter / setter)
- **In LLD terms:** a method that looks like an attribute, used to **control reads and writes**
  (and protect an invariant) instead of exposing a raw field.
- **Example:**
  ```python
  class Wallet:
      @property
      def balance(self): return self._balance
      @balance.setter
      def balance(self, v):
          if v < 0: raise ValueError("negative balance")
          self._balance = v
  ```
- **Practice:** make a `temperature` property that forbids values below absolute zero.
- **See:** [Encapsulation](../curriculum/01-fundamentals/02-encapsulation.md)

---

## B. Fundamentals

*(drill each in [`curriculum/01-fundamentals/`](../curriculum/01-fundamentals/))*

### Responsibility
- **In LLD terms:** a **reason a type would need to change** — normally tied to one *actor* (the
  person/team/system that asks for the change). Not "something it does", but "who makes me edit
  this".
- **Example:** a `Report` that changes when *sales* change (add a column) **and** when *finance*
  changes (reformat money) has two responsibilities.
- **Practice:** list the *reasons to change* of a class **before** splitting it.
- **See:** [Responsibilities & cohesion](../curriculum/01-fundamentals/01-responsibilities-and-cohesion.md)

### Cohesion
- **In LLD terms:** how strongly the parts **inside one unit** belong together and serve **one**
  job. High cohesion → everything in the class exists for the same reason. Low cohesion → the
  class is a grab-bag.
- **Example:**
  ```python
  # LOW cohesion: build + render + save + email in one class
  class Report:
      def build_rows(self): ...
      def to_pdf(self): ...
      def save_to_db(self): ...
      def email_to_manager(self): ...
  # HIGH cohesion: one job per class
  class ReportData: ...        # builds rows
  class PdfRenderer: ...       # renders
  class ReportRepository: ...  # persists
  class ReportMailer: ...      # emails
  ```
- **Practice:** take the `OrderManager` drill and, *before editing*, write one sentence per
  responsibility you can find; then split.
- **See:** [Responsibilities & cohesion](../curriculum/01-fundamentals/01-responsibilities-and-cohesion.md)

### Coupling
- **In LLD terms:** how much one unit **depends on the details of another**. Tight coupling =
  changing one forces changing many; loose coupling = units meet at a small, stable interface.
- **Example:** `ReportService` doing `self.db = PostgresDb()` is tightly coupled to Postgres;
  taking a `DataSource` interface instead decouples it.
- **Practice:** find a class that creates its own dependency internally, then break that coupling.
- **See:** [Interfaces & contracts](../curriculum/01-fundamentals/04-interfaces-and-contracts.md),
  [Coupling & dependency direction](../curriculum/04-lld-topics/01-coupling-and-dependency-direction.md)

### Encapsulation
- **In LLD terms:** hiding internal state behind a **small, meaningful interface** so the object
  **cannot be pushed into an invalid state** from outside. It protects *invariants*, not just
  "private fields".
- **Example:** a `Wallet` whose `balance` is read-only and changes only via `deposit`/`withdraw`,
  so it can never go negative.
- **Practice:** redesign a `Wallet` so `wallet.balance = -500` is impossible; write 3 client lines
  that *should* fail.
- **See:** [Encapsulation](../curriculum/01-fundamentals/02-encapsulation.md)

### Invariant
- **In LLD terms:** a rule that must **always be true** about an object/state (e.g. "balance ≥ 0",
  "end ≥ start"). An object must never be observable in a state that breaks it.
- **Example:** during `transfer`, the sum of both balances must stay constant.
- **Practice:** name the invariants of a `DateRange(start, end)` and enforce them in the
  constructor.
- **See:** [Encapsulation](../curriculum/01-fundamentals/02-encapsulation.md),
  [Value objects vs entities](../curriculum/01-fundamentals/06-value-objects-vs-entities.md)

### Abstraction
- **In LLD terms:** exposing **what** something does while hiding **how**. You depend on the
  abstraction (a name/contract), and the implementation can change underneath.
- **Example:** code calling `repo.find_order(id)` doesn't know if it's Postgres, SQLite, or a fake.
- **Practice:** hide a concrete class behind an interface that names *intent*, not *mechanism*.
- **See:** [Interfaces & contracts](../curriculum/01-fundamentals/04-interfaces-and-contracts.md)

### Interface & contract
- **In LLD terms:** an **interface** is the set of operations a type exposes; the **contract** is
  the promises those operations make (inputs, outputs, errors). Callers depend on the contract,
  not the class.
- **Example:** `DataSource.find_orders(date)` promised to return the orders for a date — any
  implementation must honor that.
- **Practice:** define an interface for a data source and write **two** implementations (real +
  in-memory).
- **See:** [Interfaces & contracts](../curriculum/01-fundamentals/04-interfaces-and-contracts.md)

### Inheritance
- **In LLD terms:** a child class **automatically gets the parent's attributes and methods**
  (`class Child(Parent)`) and may override them. It models **is-a with the same behavior
  contract** — a child must be usable anywhere the parent is.
- **Example:**
  ```python
  class Animal:
      def eat(self): return "eating"
  class Dog(Animal):        # Dog gets eat() for free
      pass
  Dog().eat()               # -> "eating"
  ```
- **Practice:** model pets with inheritance, then find a subtype that **breaks** the parent's
  contract (a bird that can't fly) — and decide whether inheritance was the right tool.
- **See:** [Composition vs inheritance](../curriculum/01-fundamentals/03-composition-vs-inheritance.md)

### Composition
- **In LLD terms:** a class **holds another object** and delegates work to it (`has-a`). The part
  can be **swapped** without touching the whole.
- **Example:**
  ```python
  class Engine:
      def start(self): return "vroom"
  class Car:
      def __init__(self, engine): self.engine = engine
      def start(self): return self.engine.start()   # delegates
  ```
- **Practice:** refactor a flying-bird hierarchy to composition so adding a new bird needs **no**
  edits to existing classes.
- **See:** [Composition vs inheritance](../curriculum/01-fundamentals/03-composition-vs-inheritance.md)

### Polymorphism
- **In LLD terms:** the same call works on **different types** because they share a contract — you
  call `shape.area()` and each shape answers its own way. It is what lets you replace one
  implementation with another.
- **Example:** `for s in shapes: s.area()` where `shapes` holds circles and squares.
- **Practice:** write a loop that calls one method on a list of different concrete types.
- **See:** [Interfaces & contracts](../curriculum/01-fundamentals/04-interfaces-and-contracts.md),
  [LSP](../curriculum/02-solid/03-lsp.md)

### Value object & entity
- **In LLD terms:** a **value object** has **no identity** — two are equal if their values match,
  and it is immutable (`Money(5, "USD") == Money(5, "USD")`). An **entity** has **identity** that
  persists while its attributes change (`Order #123` stays #123 even if its total changes).
- **Example:** `Email`, `Money`, `DateRange` are values; `Customer`, `Order` are entities.
- **Practice:** build `Email` and `Money` so neither can exist invalid and both are equal by value;
  prove it with a test.
- **See:** [Value objects vs entities](../curriculum/01-fundamentals/06-value-objects-vs-entities.md)

### Immutability
- **In LLD terms:** an object whose state **cannot change after creation**. Operations return a
  **new** instance instead of mutating. Immutable objects are safe to share and reason about.
- **Example:** `Money.add(other)` returns a new `Money`; it never changes `self`.
- **Practice:** make a `Money` immutable and show a "modify" operation returns a new object.
- **See:** [Value objects vs entities](../curriculum/01-fundamentals/06-value-objects-vs-entities.md),
  [Immutability](../curriculum/04-lld-topics/05-immutability.md)

### Refactoring
- **In LLD terms:** improving the **structure** of code **without changing behavior**, in small
  steps, kept safe by tests. It is not adding features.
- **Example:** extract a method, rename a variable, replace a magic number with a constant — tests
  green before and after each step.
- **Practice:** refactor a messy `calc()` in tiny steps with a test green after **each** step.
- **See:** [Refactoring basics](../curriculum/01-fundamentals/07-refactoring-basics.md)

---

## C. SOLID

*(five design principles; drill each in [`curriculum/02-solid/`](../curriculum/02-solid/))*

### Single Responsibility Principle (SRP)
- **In LLD terms:** a class should have **one reason to change** — one actor it answers to. It is
  about *who asks for the change*, not "one method".
- **Example:** an `Invoice` that also emails itself answers to both Accounting and Marketing → split.
- **Practice:** give one class two actors, then split it so each part answers to exactly one.
- **See:** [SRP](../curriculum/02-solid/01-srp.md)

### Open/Closed Principle (OCP)
- **In LLD terms:** types should be **open for extension, closed for modification** — add new
  behavior **without editing** existing, working code.
- **Example:** a `Discount` type per customer kind, instead of a growing `if kind == ...` chain.
- **Practice:** take an `if/elif` chain and refactor so a new case needs a **new** class, not an edit.
- **See:** [OCP](../curriculum/02-solid/02-ocp.md)

### Liskov Substitution Principle (LSP)
- **In LLD terms:** a **subtype must be usable anywhere its supertype is**, without breaking the
  supertype's contract. A subclass may **strengthen** outputs / **weaken** preconditions — never the
  reverse.
- **Example:** a `Square` that forces `set_width` to also change height surprises callers of
  `Rectangle` → violates LSP.
- **Practice:** find a subclass that throws/misbehaves on a parent method call; fix the design.
- **See:** [LSP](../curriculum/02-solid/03-lsp.md)

### Interface Segregation Principle (ISP)
- **In LLD terms:** no client should be **forced to depend on methods it doesn't use**. Prefer many
  small, focused interfaces over one fat one.
- **Example:** split a fat `Machine` (print + scan + fax) so a simple printer needn't implement
  `fax`.
- **Practice:** take an interface with 6 methods and split it so each implementer uses **all** of
  its methods.
- **See:** [ISP](../curriculum/02-solid/04-isp.md)

### Dependency Inversion Principle (DIP)
- **In LLD terms:** high-level policy should **not depend on low-level detail**; both depend on an
  **abstraction**, and the detail depends on the abstraction (interfaces owned by the caller).
- **Example:** `ReportService` depends on a `DataSource` protocol, not on `PostgresDb`.
- **Practice:** invert a class that `new`s its own dependency so the caller injects an interface.
- **See:** [DIP](../curriculum/02-solid/05-dip.md)

---

## D. Design patterns

*(named solutions to recurring problems; full drills in
[`curriculum/03-design-patterns/`](../curriculum/03-design-patterns/) — each entry: the idea, then
the file to drill it)*

### Factory Method
- **In LLD terms:** a method whose job is to **create** an object, often with subclasses choosing
  the concrete type — callers ask for a product without naming the class.
- **See:** [Factory Method](../curriculum/03-design-patterns/01-factory-method.md)

### Abstract Factory
- **In LLD terms:** a factory that creates a **family of related products** (a whole UI kit) so the
  client never names a concrete class.
- **See:** [Abstract Factory](../curriculum/03-design-patterns/02-abstract-factory.md)

### Builder
- **In LLD terms:** construct a **complex object step by step**, separating *how it's assembled*
  from *what it is* — handy when a constructor has too many optional parameters.
- **See:** [Builder](../curriculum/03-design-patterns/03-builder.md)

### Singleton *(anti-pattern talk)*
- **In LLD terms:** guarantee **one instance** of a class with a global access point. Taught, then
  usually discouraged — it hides dependencies and hurts testability.
- **See:** [Singleton (anti-pattern)](../curriculum/03-design-patterns/04-singleton-antipattern.md)

### Adapter
- **In LLD terms:** wrap an object behind the **interface your code expects**, translating calls, so
  incompatible APIs can work together.
- **See:** [Adapter](../curriculum/03-design-patterns/05-adapter.md)

### Decorator
- **In LLD terms:** attach **extra behavior** by wrapping an object in another of the same
  interface — composable, unlike subclassing.
- **See:** [Decorator](../curriculum/03-design-patterns/06-decorator.md)

### Facade
- **In LLD terms:** a **simple front door** to a complex subsystem — one friendly interface over
  many parts.
- **See:** [Facade](../curriculum/03-design-patterns/07-facade.md)

### Composite
- **In LLD terms:** treat **one object and a group of objects the same way** via a shared interface
  (a folder and a file are both nodes).
- **See:** [Composite](../curriculum/03-design-patterns/08-composite.md)

### Proxy
- **In LLD terms:** a **stand-in for another object** that controls access to it (lazy load, cache,
  permission check) while keeping the same interface.
- **See:** [Proxy](../curriculum/03-design-patterns/09-proxy.md)

### Strategy
- **In LLD terms:** make an **algorithm swappable** by putting it behind an interface and injecting
  it — pick behavior at runtime, no `if` chain.
- **See:** [Strategy](../curriculum/03-design-patterns/10-strategy.md)

### Observer
- **In LLD terms:** a subject **notifies a list of subscribers** when it changes, without knowing
  who they are (publish/subscribe).
- **See:** [Observer](../curriculum/03-design-patterns/11-observer.md)

### State
- **In LLD terms:** let an object **change its behavior when its state changes**, by delegating to
  state objects instead of a big `switch`.
- **See:** [State](../curriculum/03-design-patterns/12-state.md)

### Command
- **In LLD terms:** turn a request into an **object**, so it can be queued, logged, undone, or
  retried (the request "is a" value).
- **See:** [Command](../curriculum/03-design-patterns/13-command.md)

### Template Method
- **In LLD terms:** a base method defines the **skeleton** of an algorithm and calls overridable
  steps a subclass fills in.
- **See:** [Template Method](../curriculum/03-design-patterns/14-template-method.md)

### Iterator
- **In LLD terms:** provide a way to **walk a collection** element by element without exposing how
  it is stored.
- **See:** [Iterator](../curriculum/03-design-patterns/15-iterator.md)

---

## E. LLD topics

*(broader engineering ideas; full drills in
[`curriculum/04-lld-topics/`](../curriculum/04-lld-topics/))*

### Coupling & dependency direction
- **In LLD terms:** *coupling* = how much unit A depends on unit B (see [Coupling](#coupling)).
  **Dependency direction** = which way the arrows point; keep them aimed at **stable abstractions**,
  not volatile details.
- **See:** [Coupling & dependency direction](../curriculum/04-lld-topics/01-coupling-and-dependency-direction.md)

### Dependency injection (DI)
- **In LLD terms:** **passing** an object's dependencies **in** from outside (constructor/parameter)
  instead of creating them inside — so behavior can be swapped and tested.
- **Example:** `ReportService(db)` beats `self.db = PostgresDb()`.
- **See:** [Dependency injection](../curriculum/04-lld-topics/02-dependency-injection.md)

### Layering & separation of concerns
- **In LLD terms:** organize code into **layers with clear jobs** (UI → domain → data), each
  depending only on the layer beneath, through abstractions.
- **See:** [Layering & separation of concerns](../curriculum/04-lld-topics/03-layering.md)

### State machine
- **In LLD terms:** model an object as a set of **states** plus the **allowed transitions** between
  them — legal moves are explicit, illegal ones rejected. (See also the [State](#state) pattern.)
- **See:** [State machines](../curriculum/04-lld-topics/04-state-machines.md)

### Immutability
- **In LLD terms:** objects that **never change** after creation (see [Immutability](#immutability)).
  Removes a whole class of bugs around shared, mutable state.
- **See:** [Immutability](../curriculum/04-lld-topics/05-immutability.md)

### Error-handling strategy
- **In LLD terms:** a **consistent** decision about how failures surface (exceptions, result types,
  error codes) — which failures are *expected* vs *exceptional*, and where they are handled.
- **See:** [Error-handling strategy](../curriculum/04-lld-topics/06-error-handling-strategy.md)

### Testability & seams
- **In LLD terms:** designing so parts can be **tested in isolation**; a *seam* is a place where you
  can swap a real dependency for a fake.
- **See:** [Testability & seams](../curriculum/04-lld-topics/07-testability-and-seams.md)

### Concurrency basics
- **In LLD terms:** what can run **at the same time**, and the danger of **shared mutable state**
  (race conditions) — plus the tools that tame it (locks, immutability, message passing).
- **See:** [Concurrency basics](../curriculum/04-lld-topics/08-concurrency-basics.md)

### Extensibility & plugin seams
- **In LLD terms:** designing extension points so **new behavior is added without editing** the core
  (pairs with [OCP](#openclosed-principle-ocp)).
- **See:** [Extensibility & plugin seams](../curriculum/04-lld-topics/09-extensibility-and-plugin-seams.md)

### Trade-off analysis
- **In LLD terms:** naming the **costs** of every choice (time, complexity, coupling) and choosing
  the simplest design that meets the **real, likely** requirements.
- **See:** [Trade-off analysis](../curriculum/04-lld-topics/10-tradeoff-analysis.md)

---

[← Repo home](../README.md) · entry point: [START HERE →](../START-HERE.md)
