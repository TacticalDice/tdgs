# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 1
# Title: Dice and Uncertainty
# Version: 1.0
# Purpose: AI-readable specification for dice semantics and uncertainty resolution
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

This document defines dice semantics and uncertainty resolution for TDGS.

It establishes:
  - What dice exist in TDGS
  - What each die is allowed to represent
  - How success and failure are determined
  - How extreme outcomes are identified
  - When dice are used and when they are not

This document does NOT define:
  - Character capability
  - Progression
  - Skills
  - Damage
  - Narrative interpretation

================================================================================
DICE TAXONOMY AND ROLES
================================================================================

Each die has a defined role. A die may ONLY be used for the purposes listed
unless a later rule explicitly expands its use.

Die     Primary Role
---     ------------
d2      Binary decisions. True/false. Yes/no.
d4      Modifiers only. Never used as a primary roll.
d6      Minor magnitude. Heavy modifiers.
d8      Minor magnitude. Heavy modifiers.
d10     Median magnitude. Selection. Duration. Area.
d12     Median magnitude. Selection. Duration. Area.
d20     Resolution of success or failure.
d100    Large scale selection and extreme randomness.

CONSTRAINT: Dice roles are exclusive.

================================================================================
RESOLUTION VERSUS MAGNITUDE
================================================================================

TDGS draws a strict boundary between:
  1. WHETHER something happens (Resolution)
  2. HOW MUCH happens (Magnitude)

RESOLUTION: Determines success, failure, avoidance, or opposition.
MAGNITUDE:  Determines quantity, damage, duration, area, or scale.

┌─────────────────────────────────────────────────────────────────────────────┐
│ CRITICAL RULE: Resolution and magnitude are ALWAYS resolved separately.     │
│ A single roll may NOT use one die for both resolution AND magnitude.        │
│ This separation is foundational to TDGS and must NOT be bypassed.           │
└─────────────────────────────────────────────────────────────────────────────┘

================================================================================
RESOLUTION ROLLS
================================================================================

A resolution roll determines whether an action succeeds or fails.

Properties:
  - Default die: d20
  - May be opposed or unopposed
  - Resolves independently of magnitude
  - NEVER determines magnitude

OUTCOMES (exactly one per resolution roll):
  1. Critical Success  - Natural maximum on resolution die
  2. Success           - Roll meets or exceeds target
  3. Failure           - Roll does not meet target
  4. Critical Failure  - Natural minimum on resolution die

================================================================================
CRITICAL OUTCOMES
================================================================================

Criticals apply ONLY to resolution rolls.

Default behavior:
  - Natural MINIMUM value = Critical Failure
  - Natural MAXIMUM value = Critical Success

Properties:
  - Criticals are properties of the BASE resolution die only
  - Modifiers do NOT create or suppress critical outcomes
  - Secondary dice do NOT create or suppress critical outcomes

DICE THAT CAN NEVER PRODUCE CRITICALS:
  - d2
  - d4

DICE THAT CAN PRODUCE CRITICALS:
  - d20 (default and primary)
  - Other dice ONLY if explicitly stated by a later rule

================================================================================
CRITICAL EFFECT FRAMEWORK
================================================================================

Magnitude roll (d4): Minor (1), Notable (2), Bonus (3), Major (4)

Engine provides EXAMPLES, content chooses interpretation:

FOR DAMAGE:
  Minor (1):   +25% damage
  Notable (2): +50% damage
  Bonus (3):   +75% damage
  Major (4):   +100% damage (double)

FOR DURATION:
  Minor (1):   +1 round
  Notable (2): +2 rounds
  Bonus (3):   +50% duration
  Major (4):   Double duration

FOR AREA/TARGETS:
  Minor (1):   +1 target
  Notable (2): +2 targets
  Bonus (3):   +50% area
  Major (4):   Double area or all adjacent

FOR HEALING:
  Minor (1):   +25% healing
  Notable (2): +50% healing
  Bonus (3):   +75% healing
  Major (4):   Double healing

These are examples, not mandates. Content defines interpretation per effect type.

================================================================================
CONTESTED RESOLUTION
================================================================================

When two entities oppose each other directly:
  1. Each entity performs a resolution roll
  2. Final resolution values are compared
  3. Higher value succeeds
  4. Lower value fails

Each side resolves its roll independently.

TIE RESOLUTION:
  If final values are tied AND all reactions/responses exhausted:
    → Resolve using d2
    → True binary outcome with no modifiers

================================================================================
WHEN DICE ARE NOT ROLLED
================================================================================

Dice are rolled ONLY when:
  - Uncertainty exists AND
  - Meaningful consequence exists

If either condition is not met, no roll is required.

Valid outcomes without rolling:
  - Automatic success (when outcome is certain)
  - Automatic failure (when outcome is impossible)

PRINCIPLE: No action in TDGS requires a roll by default.
Rolls exist to resolve uncertainty, not to create it.

================================================================================
NOTATION REFERENCE
================================================================================

TDGS documentation may use Dice Expression Language (DEL) for:
  - Formal dice expressions
  - Probability descriptions
  - Roll structures

DEL Properties:
  - Descriptive notation for clear communication
  - NOT required to play TDGS
  - NOT required for implementation support
  - Improves readability, consistency, machine interpretability

DEL Specification: https://tacticaldice.com/delspec

================================================================================
DEFERRED SYSTEMS
================================================================================

The following are NOT defined in this document:
  - Difficulty values
  - Modifiers
  - Character attributes
  - Skills
  - Progression
  - Damage or harm
  - Action economy
  - Narrative interpretation

Related system (defined separately):
  - Luck: Affects resolution probability without altering neutral dice behavior

================================================================================
IMPLEMENTATION GUIDANCE FOR AI SYSTEMS
================================================================================

When generating TDGS content involving dice:
  1. Use d20 for resolution rolls
  2. Use separate dice for magnitude
  3. Never combine resolution and magnitude in one roll
  4. Apply criticals only to base d20 resolution rolls
  5. d2 and d4 cannot produce critical outcomes
  6. Only roll when uncertainty AND consequence exist

When interpreting TDGS dice mechanics:
  1. Identify if roll is resolution or magnitude
  2. Resolution = success/failure determination
  3. Magnitude = quantity/scale determination
  4. Check for critical outcomes on d20 resolution only
  5. Contested rolls compare final values, tie → d2

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/dice
AI-optimized:   https://tacticaldice.com/docs/tdgs/diceforai
DEL Spec:       https://tacticaldice.com/delspec

================================================================================
END OF DOCUMENT 1
================================================================================
