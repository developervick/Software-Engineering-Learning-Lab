# ▶ START HERE

**This is the single entry point for the whole repository.** Read this page top to bottom,
then follow the numbered path **in order**. You never need to open anything that isn't the
*next* item on the list.

This lab is **concept-first**: you learn and drill one idea **alone**, pass its **gate**, and
only then **combine** concepts in challenges. Follow the order — skipping it is the most
common way to end up "understanding" a topic without being able to actually build it.

> **One-sentence rule:** never open the *next* file until you have passed the gate of the
> *current* one.

---

## 2-minute quickstart

1. Pick a language (Python is a fine default) and confirm you can run a test file.
2. Open **[`docs/how-to-use-this-repo.md`](docs/how-to-use-this-repo.md)** — the method + AI rules.
3. Start at **[`curriculum/01-fundamentals/00-classes-and-objects.md`](curriculum/01-fundamentals/00-classes-and-objects.md)**.
4. When you pass its gate, mark it in **[`progress/concept-tracker.md`](progress/concept-tracker.md)** and go to concept **#1** in that folder.

That's it. The rest of this page is just the full ordered map.

---

## The study order (follow it exactly)

The whole repo is **one path**. Every link below is in the order you should do it.

### Phase 0 — Orientation (once, ~20 minutes)
1. [`docs/how-to-use-this-repo.md`](docs/how-to-use-this-repo.md) — how the lab works, the two loops, the AI ladder.
2. [`ROADMAP.md`](ROADMAP.md) — the stages and what "move on" means.
3. [`prompts/first-prompt.md`](prompts/first-prompt.md) — paste this to your AI to set the rules.

### Phase 1 — Concepts (drill each one ALONE, in order)
Finish **every** concept in a track before moving to the next track. Inside a track, follow
the numbering. Pass each file's **Done-when gate** before moving on.

1. **Fundamentals** → [`curriculum/01-fundamentals/`](curriculum/01-fundamentals/) *(8 concepts)*
   0. Classes & objects (and methods) ← start here
   1. Responsibilities & cohesion
   2. Encapsulation
   3. Composition vs inheritance
   4. Interfaces & contracts
   5. Validation & fail-fast
   6. Value objects vs entities
   7. Refactoring basics
2. **SOLID** → [`curriculum/02-solid/`](curriculum/02-solid/) *(5)* — 1. SRP · 2. OCP · 3. LSP · 4. ISP · 5. DIP
3. **Design patterns** → [`curriculum/03-design-patterns/`](curriculum/03-design-patterns/) *(15)*
   - Creational: Factory Method · Abstract Factory · Builder · Singleton (anti-pattern talk)
   - Structural: Adapter · Decorator · Facade · Composite · Proxy
   - Behavioral: Strategy · Observer · State · Command · Template Method · Iterator
4. **LLD topics** → [`curriculum/04-lld-topics/`](curriculum/04-lld-topics/) *(10)*
   1. Coupling & dependency direction · 2. Dependency injection · 3. Layering ·
   4. State machines · 5. Immutability · 6. Error-handling strategy ·
   7. Testability & seams · 8. Concurrency basics · 9. Extensibility & plugin seams ·
   10. Trade-off analysis

### Phase 2 — Challenges (COMBINE concepts into a solution)
Start a challenge only once the concept gates it **Combines** are met (every challenge lists
its **Prereqs**). Do the levels in order:

1. [`challenges/level-01-fundamentals/`](challenges/level-01-fundamentals/) *(CH-001–003)* — e.g. [CH-001 Vending Machine](challenges/level-01-fundamentals/CH-001-vending-machine.md)
2. [`challenges/level-02-solid-and-basic-lld/`](challenges/level-02-solid-and-basic-lld/) *(CH-004–009)*
3. [`challenges/level-03-intermediate-lld/`](challenges/level-03-intermediate-lld/) *(CH-010–017)*
4. [`challenges/level-04-advanced-lld/`](challenges/level-04-advanced-lld/) *(CH-018–024)*
5. [`challenges/level-05-system-design/`](challenges/level-05-system-design/) *(CH-025–029)* ← this is **Stage 6**

Put your work in [`challenges/solutions/CH-XXX/`](challenges/solutions/).

### Phase 3 — Keep the loop turning
- Track concept mastery → [`progress/concept-tracker.md`](progress/concept-tracker.md)
- Track capabilities → [`progress/capabilities.md`](progress/capabilities.md)
- Log weaknesses → [`progress/gaps.md`](progress/gaps.md)
- Reflections → [`journal/`](journal/)
- Recurring mistakes → [`mistakes/`](mistakes/)
- Short notes → [`notes/`](notes/)

---

## Why this order (the rules)

- **Concepts before challenges.** You can't reliably combine (e.g. Strategy + OCP + DI) what
  you've never built alone.
- **Gate before next.** A concept is "done" only when you pass its checklist **without help** —
  not when you've read it.
- **Fundamentals → SOLID → patterns → LLD topics.** Each track assumes the previous one.
- **Isolation exposes gaps.** If a combined challenge feels impossible, the missing piece is
  almost always one un-drilled concept.
- **AI only after your own attempt** — hint → direction → review → partial → full.

---

## Where to go for details

- Project overview & philosophy → [`README.md`](README.md)
- The method & AI rules → [`docs/how-to-use-this-repo.md`](docs/how-to-use-this-repo.md)
- Any term you can't define → [`docs/glossary.md`](docs/glossary.md)
- The staged plan → [`ROADMAP.md`](ROADMAP.md)

---

## License

MIT — see [`LICENSE`](LICENSE). © 2026 vick.
