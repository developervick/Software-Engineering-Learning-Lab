# 0. Classes & objects (and the kinds of methods)

- **Track:** fundamentals
- **Prereqs:** none — this is the absolute starting point
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Know exactly what a **class** and an **object** are, and be fluent in the **kinds of methods**
(instance, class, static, abstract, property/getter-setter). Every other concept in this lab
assumes this vocabulary, so build it rock-solid first.

## The words (LLD meaning — not the grammar meaning)

| Word | What it means *here* | Looks like |
|------|----------------------|-----------|
| **Class** | A **blueprint** that defines the **data** (attributes) and **behavior** (methods) of a kind of thing. It is not a thing itself. | `class Account:` |
| **Object** | A **concrete thing built from a class**, with its **own** copy of the instance data. Also called an *instance*. | `a = Account()` |
| **Attribute** | **Data** an object (instance) or a class holds. | `self.balance`, `Account.rate` |
| **Method** | A **function defined inside a class** that acts on that object's data. | `def deposit(self, amt):` |
| **`self`** | A reference to **this particular object** — always the first parameter of an instance method. | `self.balance += amt` |
| **Constructor** | The method that **builds an object** at creation time. In Python: `__init__`. | `def __init__(self): ...` |

> One-liner: a **class is a type**, an **object is a value of that type**, and a **method is
> behavior attached to the type**.

## The kinds of methods (the part people mix up)

| Kind | Written as (Python) | Belongs to | Exists to… |
|------|--------------------|-----------|-----------|
| **Instance method** | `def m(self, ...)` | one object | read/write **that object's** state |
| **Class method** | `@classmethod` (first arg `cls`) | the class | alternative constructors, class-wide logic |
| **Static method** | `@staticmethod` | the class | a helper needing neither `self` nor `cls` |
| **Abstract method** | `@abstractmethod` in an `ABC` | the contract | **force** subclasses to implement it |
| **Property** | `@property` / `@x.setter` | one object | controlled (guarded) read/write of an attribute |

### Syntax, annotated

```python
from abc import ABC, abstractmethod

class Shape(ABC):                  # class = a blueprint
    kind = "shape"                 # CLASS attribute (shared by every shape)

    def __init__(self, name):      # constructor
        self.name = name           # INSTANCE attribute (one per object)

    @abstractmethod
    def area(self):                # abstract: every subclass MUST implement it
        ...

    @staticmethod
    def describe():                # static: needs no self / cls
        return "a geometric shape"

    @classmethod
    def from_name(cls, name):      # class method: an alternative constructor
        return cls(name)


class Circle(Shape):               # Circle IS-A Shape (inheritance)
    def __init__(self, r):
        super().__init__("circle") # call the parent constructor
        self._r = r

    def area(self):                # instance method
        return 3.14159 * self._r ** 2

    @property
    def radius(self):              # getter
        return self._r

    @radius.setter
    def radius(self, value):       # setter: guards the invariant r >= 0
        if value < 0:
            raise ValueError("radius must be >= 0")
        self._r = value


c = Circle(2)                       # c is an OBJECT (instance) of Circle
print(c.area())                     # instance method → acts on c
print(Shape.describe())             # static → called on the class
print(Circle.from_name("x").name)   # class method → builds an object
```

## Drill — do this alone

Build a tiny **`BankAccount`** from scratch (don't look up a finished version):

1. A class `BankAccount` with an **instance** attribute `balance` and a **class** attribute
   `currency = "USD"`.
2. A constructor that starts `balance` at `0`.
3. **Instance methods** `deposit(amount)` and `withdraw(amount)`.
4. A read-only **property** `balance` so outside code cannot set it directly.
5. A **class method** `from_cents(cls, cents)` that builds an account with an initial balance.
6. A **static method** `is_valid_amount(amount)` that returns a `bool`.
7. An **abstract** base `PaymentMethod` with `pay(amount)`, plus **two** subclasses that
   implement it.

Then, in your own words (write in `journal/`):

- In one sentence and one example each: what is the **difference between a class and an object**?
- Where did you use a **static** method, and why not an instance method there?
- Why make `balance` a **property** instead of a public attribute?

If a **syntax** detail is stuck, ask for **one** hint. Don't ask for the whole solution.

## Done when

- [ ] I can define class, object, instance, attribute, method, `self`, constructor and property
      **in LLD terms**.
- [ ] I used an instance method, a class method, a static method, an abstract method **and** a
      property — and can say **why** each one is that kind.
- [ ] `balance` can never be set to a negative value from outside the object.
- [ ] My mini-project runs and prints sensible output.

## Reflection (write in `journal/`)

- Which of the method kinds was hardest to justify? (Usually the one you don't actually need yet.)
- Did I put data in the wrong place (instance vs class attribute)? How would I have noticed?

## Theory & resources

- A class is a **type**; an object is a **value of that type**; a method is behavior attached to
  the type.
- Prefer the **smallest** method kind that works: instance → class → static. A static method that
  never touches state is often a free function in disguise.
- Every term above is defined, with an example and mini-practice, in
  [`../../docs/glossary.md`](../../docs/glossary.md).
- Resources: the Python docs on *classes*, `abc`, and `property`.
