# 1. Responsibilities & cohesion

- **Track:** fundamentals
- **Prereqs:** none
- **Status:** not-started
- **Est. time:** 45–90 min

## The words (LLD meaning — not the grammar meaning)

- **Responsibility** = a **reason this type would need to change** — normally tied to one *actor*
  (the person/team/system that asks for the change). It is not "a thing it does"; it is "who makes
  me edit this".
- **Cohesion** = how strongly the parts **inside one unit** belong together and serve **one** job.
  High cohesion → everything in the class exists for the same reason. Low cohesion → the class is
  a grab-bag of unrelated jobs.

```python
# LOW cohesion: one class, several unrelated reasons to change
class Report:
    def build_rows(self): ...
    def to_pdf(self): ...
    def save_to_db(self): ...
    def email_to_manager(self): ...

# HIGH cohesion: each class does one job and has one reason to change
class ReportData: ...        # builds rows
class PdfRenderer: ...       # renders
class ReportRepository: ...  # persists
class ReportMailer: ...      # emails
```

> **Cohesion vs coupling:** *cohesion* is about what's **inside one unit**; *coupling* is about how
> units **depend on each other**. Full definitions: [`../../docs/glossary.md`](../../docs/glossary.md#cohesion).

**Practice:** the drill below **is** your cohesion challenge — work it alone; the answer is not
provided anywhere.

## Goal

Give each type **one clear job** — so you can name what it does in a sentence without "and".

## Drill — do this alone

Below is a single class doing far too much. **Without changing behavior**, split it so each
piece has one responsibility. Then write down, in one sentence each, the job of every type
you end up with.

```python
class OrderManager:
    def __init__(self):
        self.orders = []

    def place_order(self, user_email, items, card_number):
        # 1. validate
        if not user_email or "@" not in user_email:
            raise ValueError("bad email")
        if not items:
            raise ValueError("no items")
        if not self._luhn_ok(card_number):
            raise ValueError("bad card")

        # 2. price
        total = 0
        for it in items:
            total += it["price"] * it["qty"]
        if total > 100:
            total *= 0.9  # discount

        # 3. persist
        order = {"email": user_email, "items": items, "total": total}
        self.orders.append(order)

        # 4. notify
        print(f"Email to {user_email}: order placed, total={total}")

        # 5. return
        return order

    def _luhn_ok(self, card_number):
        return len(str(card_number)) >= 12
```

(Port to your language if it isn't Python.)

## Done when

- [ ] I can describe each resulting type's job in one sentence, with no "and".
- [ ] `place_order`'s behavior is unchanged (same inputs → same effect).
- [ ] No type reaches into another's internals.
- [ ] I can explain **why** I drew the boundaries where I did.

## Reflection (write in `journal/`)

- Where was the boundary obvious? Where was it genuinely a judgment call?
- Did I create a class that just forwards calls? Does it earn its place?

## Theory & resources (read *after* attempting)

- One responsibility = one **reason to change**. If two unrelated changes force edits to the
  same class, it's doing two jobs. (This is the seed of SRP, formalized in `02-solid/`.)
- Resources: [`../../resources/books.md`](../../resources/books.md) — *Clean Code*, *Refactoring*.
