# 1. Responsibilities & cohesion

- **Track:** fundamentals
- **Prereqs:** none
- **Status:** not-started
- **Est. time:** 45–90 min

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
