# TACTICAL DICE GAME SYSTEM (TDGS) - GLOSSARY
# Title: Canonical Term Definitions
# Version: 1.0
# Status: Living Document
# Purpose: AI-readable glossary of all TDGS terminology
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

This glossary contains canonical definitions for all TDGS terms.
When a term appears in any TDGS document, this is its authoritative definition.

================================================================================
REQUIREMENT LEVELS (RFC 2119)
================================================================================

Term          | Meaning
--------------|----------------------------------------------------------
SHALL / MUST  | Required. Non-negotiable. The engine requires this.
SHOULD        | Recommended. Best practice. May be omitted with good reason.
MAY           | Optional. Permitted but not expected.

================================================================================
CORE CONCEPTS
================================================================================

Action
  Any discrete thing an entity does that requires resolution.
  Categorized by Action Type. Modified by Timing.
  See: Document 5

Action Type
  Category of an action determining which stats resolve it.
  Core types: Physical, Mental, Magical
  See: Document 5

Magnitude
  How much happens when an action succeeds.
  Includes: damage, duration, area, quantity
  CONSTRAINT: Always separate from Resolution
  CONSTRAINT: Luck NEVER affects Magnitude
  See: Documents 1, 4

Resolution
  Whether an action succeeds or fails.
  Formula: d20 + (Your Stat - Their Stat) + Modifiers >= 11
  Luck affects Resolution
  See: Document 3

Round
  One full cycle where all entities act.
  Contains: Instant Phase -> Action Phase
  See: Document 6

Scene
  Continuous sequence of Rounds during active conflict.
  Resets: Armor durability, some effects
  Ends: death, escape, surrender
  See: Document 6

================================================================================
ATTRIBUTES (Scale 0-100 unless noted)
================================================================================

STR (Strength)      Raw physical force. Melee, grappling, feats of strength.
DEX (Dexterity)     Precision and coordination. Ranged, stealth, fine manipulation.
REF (Reflex)        Reaction time. Initiative order. Dodging, responding to threats.
CON (Constitution)  Endurance and pain tolerance. Poison resist, HP calculation.
MOV (Movement)      Speed of locomotion. Chasing, fleeing, racing.
INT (Intelligence)  Reasoning and learning. Arcane magic, knowledge.
WIS (Wisdom)        Judgment and awareness. Divine magic, perception.
CHA (Charisma)      Presence and influence. Persuasion, intimidation.
LUK (Luck)          Scale: -10 to +10. Abnormal probability relationship.
                    Sets floors (positive) or ceilings (negative) on success.
                    See: Document 4

================================================================================
ABILITIES
================================================================================

Ability
  Learned or innate capability modifying/enabling actions.
  Base class for: Skills, Spells, Traits
  See: Document 7

Skill
  Trained Ability with levels (1-8).
  Granted by Classes. Improves with use.
  Formula: bonus = floor(level / 2)
  See: Document 7

Spell
  Magical Ability. No levels (fixed power).
  Uses: Arcane (INT) or Divine (WIS)
  Almost always has cooldowns.
  See: Document 7

Trait
  Innate Ability without levels. Binary (have or don't).
  Granted by: race, creature type, transformation
  Examples: Darkvision, Venom Bite, Flight
  See: Documents 7, 11

Tier
  Inherent power level of Skill or Spell.
  Higher tiers unlock new capabilities.
  Range: Tier 1 (basic) to Tier 5+ (legendary)
  See: Document 7

Cooldown
  Limiter on Ability usage frequency.
  Types: None, Round, Scene, Day
  See: Document 7

================================================================================
TIMING
================================================================================

Action (Timing)
  Default timing. Action Phase in initiative order.
  1 per turn. Use or lose.
  See: Document 6

Instant
  Pre-emptive timing. Instant Phase at round start.
  Ordered by Instant's own REF stat.
  See: Document 6

Interrupt
  Reactive timing. Responds to another entity's action.
  Requires skills/abilities. No free interrupts.
  See: Document 6

Concentration
  Mental focus required for certain ongoing effects.
  Breaking: d20 + (CON - Damage Taken) >= 11
  Failure: Effect ends immediately
  Limit: One concentration at a time (default)
  See: Document 5

Initiative
  Order in which entities act.
  Tiebreakers: REF -> LUK -> d2
  NOT rolled.
  See: Document 6

Step
  Free movement to adjacent position.
  Once per turn. Does not cost action.
  Does not trigger opportunity attacks.
  See: Document 14

================================================================================
RESOLUTION TERMS
================================================================================

Delta
  Difference between attacking and defending stat.
  Formula: Delta = Your Stat - Their Stat
  See: Document 3

Threshold
  Number that must be met or exceeded.
  Standard: 11
  See: Document 3

Natural 1
  Rolling 1 on d20 before modifiers.
  ALWAYS fails regardless of math.
  Triggers critical failure check.
  See: Document 1

Natural 20
  Rolling 20 on d20 before modifiers.
  ALWAYS succeeds regardless of math.
  Triggers critical success check.
  See: Document 1

Critical Success
  Natural 20 result.
  d4 magnitude: 1=normal, 2=minor+, 3=notable+, 4=major+
  See: Document 3

Virtual Stat
  GM-assigned stat for difficulty when no defender.
  Example: Master lock = Virtual DEX 15
  See: Document 5

================================================================================
LUCK TERMS
================================================================================

Luck Floor
  For positive LUK: minimum success rate guaranteed.
  LUK +5 = at least 75% success
  See: Document 4

Luck Ceiling
  For negative LUK: maximum success rate possible.
  LUK -5 = at most 25% success
  See: Document 4

Play Range
  LUK -2 to +2. Normal gameplay range.
  Nudges outcomes without dominating.
  See: Document 4

Narrative Range
  |LUK| >= 3. Reserved for NPCs/special circumstances.
  Dramatically affects every scene.
  See: Document 4

Triple 20 / Triple 1
  Three consecutive natural 20s (or 1s).
  Changes LUK by 1. Probability: 1/8,000
  See: Document 4

================================================================================
COMBAT TERMS
================================================================================

Absorption
  Damage reduction before applying to health pools.
  
  Two models (see Doc 8: Combat):
    - Deflection: Flat reduction per hit
    - Ablative: Armor has own health pool, depletes first
  
  Content chooses model. Both are valid absorption implementations.

HP (Hit Points)
  Total sustainable damage before death.
  Formula: Apparent CON × 5
  Does NOT scale with level.
  See: Document 8

Apparent Stat
  Effective stat value after all bonuses.
  = Base Stat + items + skills + effects + narrative
  See: Document 8

Knockout
  Unconscious from damage.
  Occurs at: HP = 5% of max (rounded down)
  Gains Unconscious condition.
  See: Document 8

Ablative Armor
  Armor with damage pool. Absorbs until depleted.
  Absorbs BEFORE deflection. No cap.
  See: Document 8

Deflection Armor
  Reduces incoming damage by percentage.
  Capped at 75% (always take at least 25%).
  Applies AFTER ablative.
  See: Document 8

Minimum Damage
  Every successful hit deals at least 1 damage.
  Regardless of armor.
  See: Document 8

Condition
  Temporary state affecting entity.
  Types: Buff (positive), Debuff (negative)
  See: Document 8

================================================================================
ENTITY TERMS
================================================================================

Entity
  Anything that can take a turn.
  Test: Can it take a turn? Yes = Entity.
  See: Document 9

Race
  What an entity IS.
  Provides: Traits, natural weapons/armor, stat ranges, Size
  See: Document 11

Class
  What an entity has TRAINED to be.
  Provides: Skills, Spells
  Can have: none, one, or multiple
  See: Document 10

Natural Weapon
  Trait allowing attack.
  Cannot combine with held weapon.
  See: Document 11

Power Tier
  Overall capability measure.
  Formula: sum of 8 base stats / 8 (LUK excluded)
  See: Document 9

Size
  Physical scale of entity.
  Categories: Tiny, Small, Medium, Large, Huge, Gargantuan
  Affects: space, reach, grappling, forced movement, carrying, squeezing
  See: Document 9

================================================================================
PROGRESSION TERMS
================================================================================

XP (Experience Points)
  Progression currency.
  Sources: combat, milestones, GM awards, successful actions
  See: Document 12

Level
  Experience measure within a Class.
  Range: 1-100
  Does NOT directly increase stats.
  See: Document 12

Difficulty Spectrum
  Scale: 10 numbered tiers (1-10) + Mythic

  Tier 1-3:  Low (routine)
  Tier 4-6:  Medium (standard adventuring)
  Tier 7-9:  High (dangerous)
  Tier 10:   Extreme (near-impossible)
  Mythic:    Beyond scale (godlike, world-shaping)

  NOTE: Mythic is NOT "Tier 11"—transcends normal measurement
  
  See Doc 12: Progression for XP values

Legend Wall
  Steep XP increase: Master (400/level) -> Legend (1,500/level)
  Most characters never cross it.
  See: Document 12

Soft Cap
  Limit via escalating cost, not hard rule.
  Stats have no maximum; cost acts as natural limit.
  See: Document 12

================================================================================
MOVEMENT TERMS
================================================================================

Range Band
  Abstract distance: Adjacent (0-1), Near (2-4), Far (5-10), Distant (11+)
  See: Document 14

Difficult Terrain
  Costs extra movement. Half MOV (round down).
  See: Document 14

Cover
  Protection from ranged attacks.
  Partial (+2 REF), Half (+4 REF), Full (untargetable)
  See: Document 14

Opportunity Attack
  Free melee attack when enemy leaves adjacent.
  Avoided by: Step, Disengage
  See: Document 14

Flanking
  Two allies on opposite sides of enemy.
  Both adjacent. Grants +2 to hit.
  See: Document 14

================================================================================
EQUIPMENT & MEASUREMENT TERMS
================================================================================

Slot
  Location on entity where equipment can be worn/wielded.
  Races define available slots.
  Items define required slots.
  See: Document 15

Equipped
  Item in a slot, actively worn or wielded.
  Grants mechanical benefits (stats, absorption, damage).
  Contrast: Carried
  See: Document 15

Carried
  Item in inventory, not slotted.
  No mechanical benefit until equipped.
  Counts toward weight, not slot limits.
  Contrast: Equipped
  See: Document 15

Encumbered
  State when carried weight > carrying capacity.
  Cannot take Move action.
  See: Document 15

Weight Unit (WU)
  Abstract unit of weight.
  Content defines scale (1 WU = 1 pound, 0.5 kg, etc.).
  Engine calculates in WU, agnostic to measurement systems.
  See: Document 15

Square
  Abstract unit of distance.
  Content defines scale (1 square = 5 feet, 1.5 meters, etc.).
  Engine calculates in squares, agnostic to measurement systems.
  See: Document 14

================================================================================
CHARACTER CREATION TERMS
================================================================================

Delta Method
  Stat generation: 4d6 drop lowest.
  Delta = Roll - 12
  Final = Racial Average + Delta (capped to range)
  See: Document 13

Base Pool
  Point buy: sum of racial stat averages.
  Must spend within racial ranges.
  See: Document 13

Heroic Pool
  Bonus points (2d6 drop lowest).
  CAN exceed racial ranges.
  See: Document 13

Soft Minimum
  Recommended stat for class. Not enforced.
  System allows bad decisions.
  See: Documents 10, 13

================================================================================
DOCUMENT REFERENCES
================================================================================

Category                      Primary Document
--------                      ----------------
Dice & Uncertainty            Document 1   /docs/tdgs/dice
Core Attributes               Document 2   /docs/tdgs/stats
Resolution Mechanics          Document 3   /docs/tdgs/resolution
Luck                          Document 4   /docs/tdgs/luck
Action Taxonomy               Document 5   /docs/tdgs/actions
Action Economy                Document 6   /docs/tdgs/actioneconomy
Abilities                     Document 7   /docs/tdgs/abilities
Combat                        Document 8   /docs/tdgs/combat
Entities                      Document 9   /docs/tdgs/entities
Classes                       Document 10  /docs/tdgs/classes
Races                         Document 11  /docs/tdgs/races
Progression                   Document 12  /docs/tdgs/progression
Character Creation            Document 13  /docs/tdgs/charactercreation
Movement & Positioning        Document 14  /docs/tdgs/movement

================================================================================
IMPLEMENTATION GUIDANCE FOR AI SYSTEMS
================================================================================

When parsing TDGS terminology:
1. Use this glossary as the authoritative source
2. Cross-reference Document numbers for full context
3. Note CONSTRAINT markers for inviolable rules
4. Formulas are canonical - implement exactly as shown

When generating TDGS content:
1. Verify term usage matches glossary definitions
2. Maintain separation between Resolution and Magnitude
3. Apply Luck rules correctly (affects Resolution only)
4. Reference appropriate documents for detailed mechanics

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/glossary
AI-optimized:   https://tacticaldice.com/docs/tdgs/glossaryforai

================================================================================
END OF GLOSSARY
================================================================================
