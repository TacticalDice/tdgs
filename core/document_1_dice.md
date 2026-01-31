*Document 1*

# Dice and Uncertainty

*How uncertainty is resolved within the Tactical Dice Game System*

## Purpose

This document defines how uncertainty is resolved within the Tactical Dice Game System.

It establishes:

- What dice exist in TDGS
- What each die is allowed to represent
- How success and failure are determined
- How extreme outcomes are identified
- When dice are used and when they are not

This document does not define character capability, progression, skills, damage, or narrative interpretation. Those concerns are addressed in later documents.

The goal of this document is to ensure that all uncertainty in TDGS is resolved consistently, transparently, and in a way that remains readable by humans and deterministic for computers.

## Dice Taxonomy and Roles

Dice in TDGS are not interchangeable. Each die has a defined role. A die may only be used for the purposes listed here unless a later rule explicitly expands its use.

| Die | Primary Role |
|-----|--------------|
| d2 | Binary decisions. True or false. Yes or no. |
| d4 | Modifiers only. Never used as a primary roll. |
| d6 | Minor magnitude. Heavy modifiers. |
| d8 | Minor magnitude. Heavy modifiers. |
| d10 | Median magnitude. Selection. Duration. Area. |
| d12 | Median magnitude. Selection. Duration. Area. |
| d20 | Resolution of success or failure. |
| d100 | Large scale selection and extreme randomness. |

> **Key Constraint:** A single roll may not use one die to determine both resolution and magnitude. If a rule requires both, they must be resolved using separate dice.

## Resolution versus Magnitude

TDGS draws a strict boundary between:

- **Whether** something happens
- **How much** happens

**Resolution** determines success, failure, avoidance, or opposition.

**Magnitude** determines quantity, damage, duration, area, or scale.

Resolution and magnitude are always resolved separately, even if they occur as part of the same action.

> **This separation is foundational to TDGS and must not be bypassed.**

## Resolution Rolls

A resolution roll is any roll whose primary purpose is to determine whether an action succeeds or fails.

Resolution rolls:

- Use a **d20** by default
- May be opposed or unopposed
- Resolve independently of magnitude

A resolution roll produces one of four outcomes:

- **Critical Success** — The best possible outcome. Something exceptional happens.
- **Success** — The intended action succeeds as planned.
- **Failure** — The intended action does not succeed.
- **Critical Failure** — The worst possible outcome. Something goes terribly wrong.

**Resolution rolls never determine magnitude.**

## Critical Success and Critical Failure

Critical outcomes apply only to resolution rolls.

By default:

- A **natural minimum value** on the resolution die is a critical failure
- A **natural maximum value** on the resolution die is a critical success

Criticals are properties of the base resolution die only. Modifiers, secondary dice, or later adjustments do not create or suppress critical outcomes.

> **The following dice can never produce critical outcomes:**
> - d2
> - d4
>
> No die other than the d20 produces critical outcomes unless explicitly stated by a later rule.

### Critical Effect Examples

The magnitude roll (d4) produces four levels: Normal (1), Minor (2), Notable (3), Major (4). But what do these mean in practice?

The engine provides examples. Content chooses interpretation.

**For Damage:**

| Roll | Label | Example Effect |
|------|-------|----------------|
| 1 | Normal | +25% damage |
| 2 | Minor | +50% damage |
| 3 | Notable | +75% damage |
| 4 | Major | +100% damage (double) |

**For Duration:**

| Roll | Label | Example Effect |
|------|-------|----------------|
| 1 | Normal | +1 round |
| 2 | Minor | +2 rounds |
| 3 | Notable | +50% duration |
| 4 | Major | Double duration |

**For Area/Targets:**

| Roll | Label | Example Effect |
|------|-------|----------------|
| 1 | Normal | +1 target |
| 2 | Minor | +2 targets |
| 3 | Notable | +50% area |
| 4 | Major | Double area or all adjacent |

**For Healing:**

| Roll | Label | Example Effect |
|------|-------|----------------|
| 1 | Normal | +25% healing |
| 2 | Minor | +50% healing |
| 3 | Notable | +75% healing |
| 4 | Major | Double healing |

These are starting points, not mandates. Different effects scale differently. A critical hit with a sword might double damage. A critical success on a charm spell might double duration. Content creators choose the interpretation appropriate to each effect.

## Contested Resolution

When two entities oppose one another directly, each performs a resolution roll.

The final resolution values are compared:

- The **higher value** succeeds
- The **lower value** fails

Each side resolves its roll independently.

If the final resolution values are tied, and all reactions or instantaneous responses have been exhausted, the tie is resolved using a **d2**.

This represents a true binary outcome with no modifiers.

## When Dice Are Not Rolled

Dice are rolled only when **uncertainty and consequence intersect**.

If an outcome is certain, or if no meaningful consequence exists, no roll is required.

Automatic success and automatic failure are valid outcomes when appropriate.

> **No action in TDGS requires a roll by default.** Rolls exist to resolve uncertainty, not to create it.

## Notation Reference

Where formal dice expressions, probability descriptions, or roll structures are written in TDGS documentation, they may be expressed using the **Dice Expression Language (DEL)**.

DEL is a descriptive notation used to communicate dice mechanics clearly and unambiguously.

DEL is not required to play TDGS, nor is it required for an implementation to support it directly. Its use in documentation is intended to improve readability, consistency, and machine interpretability.

The DEL specification can be found at: [tacticaldice.com/delspec](/delspec)

## Deferrals and Dependencies

This document intentionally does not define:

- Difficulty values
- Modifiers
- Character attributes
- Skills
- Progression
- Damage or harm
- Action economy
- Narrative interpretation

Some systems may modify resolution rolls. These systems are defined in later documents.

One such system is **Luck**, which is defined separately and does not alter the neutral behavior of dice themselves.

## Status

> **Status:** Canonical

This document defines the foundational rules for dice and uncertainty in TDGS.

All later mechanics must conform to the rules established here.

Changes to this document should be rare, deliberate, and backward compatible whenever possible.

---
