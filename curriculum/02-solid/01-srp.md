# SRP — Single Responsibility Principle

- **Track:** solid
- **Prereqs:** fundamentals 1–7
- **Status:** not-started
- **Est. time:** 60 min

## Goal

A class should have **one reason to change** — i.e. one actor/stakeholder whose needs drive
its edits.

## Drill — do this alone

This class changes for at least three different reasons. **Identify each reason**, then split
so each new type has exactly one.

```python
class Employee:
    def __init__(self, name, hours, rate):
        self.name = name
        self.hours = hours
        self.rate = rate

    def calculate_pay(self):
        return self.hours * self.rate

    def save_to_db(self):
        # writes SQL directly
        ...

    def render_payslip_html(self):
        return f"<h1>{self.name}: {self.calculate_pay()}</h1>"
```

## Done when

- [ ] I listed the **distinct reasons to change** before touching the code (accounting vs
      persistence vs presentation).
- [ ] Each resulting type has one reason to change.
- [ ] `Employee` (or its replacement) no longer knows about SQL or HTML.
- [ ] I can name the *actor* behind each responsibility.

## Reflection

- Is "a class with 3 methods = 3 classes" always right? When is splitting over-engineering?
- Which responsibility is the *core* of the entity, and which are collaborators?

## Theory & resources

- "One reason to change" ≈ one **actor** (a person/team/system that asks for the change).
- Resources: *Clean Architecture* (SRP chapter), *Clean Code*.
