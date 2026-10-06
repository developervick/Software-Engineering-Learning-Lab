# Abstract Factory

- **Track:** design-patterns · creational
- **Prereqs:** Factory Method
- **Status:** not-started
- **Est. time:** 60–90 min

## Goal

Provide an interface for creating **families of related objects** without specifying their
concrete classes.

## Drill — do this alone

Build a cross-platform UI toolkit. There are two **families**: `Light` and `Dark`. Each family
produces a matching `Button` and `Checkbox` that must **not** be mixed.

Design an abstract factory so client code asks for "a widget set" and never mixes families.

## Done when

- [ ] One factory produces a consistent family (all light, or all dark).
- [ ] Client code never names a concrete widget class.
- [ ] Adding a new family (e.g. `HighContrast`) touches no existing factory or client.
- [ ] It's impossible to accidentally mix a light button with a dark checkbox.

## When NOT to use it

- There's only **one** family — a plain factory or direct construction is simpler.
- Products aren't actually related / don't need to be consistent as a set.

## Reflection

- Factory Method creates **one** product; Abstract Factory creates a **consistent set**. Can
  you state that difference in one line?
- Did I add this because I *have* families, or because I *imagine* I might?

## Theory & resources

- Resources: *Design Patterns* (GoF, Abstract Factory), refactoring.guru.
