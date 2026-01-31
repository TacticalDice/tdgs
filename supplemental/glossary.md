*Supplemental*

# Glossary

*Canonical definitions for all TDGS terminology*

This glossary contains the official definitions for all terms used in TDGS. When a term appears in any TDGS document, its meaning is defined here. Click any document link to jump to the full specification.

## Requirement Levels

These terms follow RFC 2119 conventions used in technical specifications.

| Term | Meaning |
|------|---------|
| **SHALL / MUST** | Required. Non-negotiable. The engine requires this. |
| **SHOULD** | Recommended. Best practice. May be omitted with good reason. |
| **MAY** | Optional. Permitted but not expected. |

## Core Concepts

### Action

Any discrete thing an entity does that requires resolution. Actions are categorized by Action Type and modified by Timing. See Document 5: Action Taxonomy.

### Action Type

The category of an action. Determines which stats are used for resolution. Core types: Physical, Mental, Magical. See Document 5: Action Taxonomy.

### Magnitude

How much happens when an action succeeds. Includes damage, duration, area, quantity. Magnitude is always resolved separately from Resolution. **Luck never affects Magnitude.** See Document 1: Dice and Document 4: Luck.

### Resolution

Whether an action succeeds or fails. Determined by the core formula: `d20 + (Your Stat - Their Stat) + Modifiers >= 11`. Luck affects Resolution. See Document 3: Resolution.

### Round

One full cycle where all entities act. Contains an Instant Phase followed by an Action Phase. See Document 6: Action Economy.

### Scene

A continuous sequence of Rounds during active conflict. Armor durability and some effects reset between Scenes. A Scene ends when combat resolves (death, escape, surrender, etc.). See Document 6: Action Economy.

## Attributes

### STR (Strength)

Raw physical force. Scale 0-100. Used for melee attacks, grappling, feats of strength. See Document 2: Core Attributes.

### DEX (Dexterity)

Precision and coordination. Scale 0-100. Used for ranged attacks, stealth, fine manipulation. See Document 2: Core Attributes.

### REF (Reflex)

Reaction time. Scale 0-100. Determines initiative order. Used for dodging, responding to threats. See Document 2: Core Attributes.

### CON (Constitution)

Endurance and pain tolerance. Scale 0-100. Used for resisting poison, enduring hardship, staying conscious. Determines HP (Apparent CON × 5). See Document 2: Core Attributes and Document 8: Combat.

### MOV (Movement)

Speed of locomotion. Scale 0-100. Used for chasing, fleeing, racing. See Document 2: Core Attributes and Document 14: Movement.

### INT (Intelligence)

Reasoning and learning capacity. Scale 0-100. Used for arcane magic, knowledge, problem-solving. See Document 2: Core Attributes.

### WIS (Wisdom)

Judgment and awareness. Scale 0-100. Used for divine magic, perception, resisting mental effects. See Document 2: Core Attributes.

### CHA (Charisma)

Presence and influence. Scale 0-100. Used for persuasion, intimidation, deception. See Document 2: Core Attributes.

### LUK (Luck)

Abnormal relationship with probability. Scale -10 to +10. Modifies resolution by setting floors (positive) or ceilings (negative) on success rates. See Document 4: Luck.

## Abilities

### Ability

A learned or innate capability that modifies or enables actions. Base class for Skills, Spells, and Traits. See Document 7: Abilities.

### Skill

A trained Ability with levels (1-8). Granted by Classes. Improves with use/investment. Formula: bonus = floor(level / 2). See Document 7: Abilities.

### Spell

A magical Ability. No levels (fixed power). Uses Arcane (INT) or Divine (WIS) magic. Almost always has cooldowns. See Document 7: Abilities.

### Trait

An innate Ability without levels. Binary (have or don't). Granted by race, creature type, or transformation. Examples: Darkvision, Venom Bite, Flight. See Document 7: Abilities and Document 11: Races.

### Tier

The inherent power level of a Skill or Spell. Higher tiers unlock new capabilities. Tier 1 is basic, Tier 5+ is legendary. See Document 7: Abilities.

### Cooldown

A limiter on how often an Ability can be used. Types: None (unlimited), Round (next round), Scene (next scene), Day (after long rest). See Document 7: Abilities.

## Timing

### Action (Timing)

The default timing. Occurs during the Action Phase in initiative order. 1 per turn, use or lose. See Document 6: Action Economy.

### Instant

Pre-emptive ability that fires before normal turn order during the Instant Phase at the start of each Round. Ordered by the Instant's own REF stat. See Document 6: Action Economy.

### Interrupt

Reactive timing. Fires in response to another entity's action. Requires skills/abilities to use. No free interrupts. See Document 6: Action Economy.

### Concentration

Mental focus required to maintain certain ongoing effects. Taking damage may trigger a Concentration check. Failure ends the effect. Only one Concentration effect at a time by default. See Document 5: Action Taxonomy.

### Initiative

The order in which entities act. Determined by: REF (higher first) → LUK (higher first) → d2 (coin flip). Not rolled. See Document 6: Action Economy.

### Step

Free movement to an adjacent position. Once per turn. Does not cost an action. Does not trigger opportunity attacks. See Document 14: Movement.

## Resolution Terms

### Delta

The difference between attacking stat and defending stat. `Delta = Your Stat - Their Stat`. See Document 3: Resolution.

### Threshold

The number that must be met or exceeded for success. Always 11 in standard resolution. See Document 3: Resolution.

### Natural 1

Rolling a 1 on the d20 before any modifiers. **Always fails**, regardless of math. Triggers critical failure check. See Document 1: Dice.

### Natural 20

Rolling a 20 on the d20 before any modifiers. **Always succeeds**, regardless of math. Triggers critical success check. See Document 1: Dice.

### Critical Success

A natural 20. Triggers a d4 roll for magnitude: 1 = normal success, 2 = minor bonus, 3 = notable bonus, 4 = major bonus. See Document 3: Resolution.

### Virtual Stat

A stat assigned by the GM to represent difficulty when no defender exists. Example: A master lock might have Virtual DEX 15. See Document 5: Actions.

## Luck Terms

### Luck Ceiling

For negative LUK, the maximum success rate possible. LUK -5 caps success at 25% regardless of other factors. See Document 4: Luck.

### Luck Floor

For positive LUK, the minimum success rate guaranteed. LUK +5 guarantees at least 75% success regardless of other factors. See Document 4: Luck.

### Play Range (Luck)

LUK -2 to +2. Normal play range where luck nudges outcomes without dominating. See Document 4: Luck.

### Narrative Range (Luck)

|LUK| >= 3. Reserved for NPCs and special story circumstances. Dramatically affects every scene. See Document 4: Luck.

### Triple 20 / Triple 1

Rolling three natural 20s (or 1s) in a row. Increases (or decreases) LUK by 1. Probability: 1/8,000. See Document 4: Luck.

## Combat Terms

### Absorption

Damage reduction. The amount of incoming damage negated before applying to health pools. TDGS supports two absorption models (see Document 8: Combat):

- **Deflection:** Flat reduction per hit. Armor absorbs a fixed amount of damage from each attack.
- **Ablative:** Armor has its own health pool. Damage depletes armor before reaching the entity.

Content chooses which model to use. Both are valid implementations of absorption.

### HP (Hit Points)

Total damage an entity can sustain before death. Calculated as Apparent CON × 5. Does NOT scale with level. See Document 8: Combat.

### Apparent Stat

The effective value of a stat after all bonuses. Apparent Stat = Base Stat + all bonuses from items, skills, effects, and narrative sources. See Document 8: Combat.

### Knockout

Rendered unconscious from damage. Occurs when HP reaches 5% of maximum (rounded down). Entity gains the Unconscious condition. See Document 8: Combat.

### Ablative Armor

Armor with a damage pool. Absorbs incoming damage until depleted. Absorbs before deflection. No cap. See Document 8: Combat.

### Deflection Armor

Armor that reduces incoming damage by percentage. Capped at 75% (always take at least 25%). Applies after ablative. See Document 8: Combat.

### Minimum Damage

Every successful hit deals at least 1 damage, regardless of armor. "You hit? You scratch the paint." See Document 8: Combat.

### Condition

A temporary state affecting an entity. Can be Buff (positive) or Debuff (negative). Examples: Stunned, Hasted, Poisoned, Invisible. See Document 8: Combat.

## Entity Terms

### Entity

Anything that can take a turn in the game world. The test: Can it take a turn? If yes, it's an Entity. See Document 9: Entities.

### Race

What an entity IS. Provides innate Traits, natural weapons, natural armor, base stat ranges, and Size. See Document 11: Races.

### Class

What an entity has TRAINED to be. Provides Skills and Spells. An entity can have no classes, one class, or multiple classes. See Document 10: Classes.

### Natural Weapon

A Trait that allows an attack. Using a natural weapon is an action. Cannot combine with held weapon in same attack. See Document 11: Races.

### Power Tier

A measure of overall capability. Sum of 8 base stats divided by 8. LUK excluded. Used to compare entities. See Document 9: Entities.

### Size

Physical scale of an entity. Categories: Tiny, Small, Medium, Large, Huge, Gargantuan. Affects space occupied, reach, grappling modifiers, forced movement resistance, carrying capacity, and squeezing. See Document 9: Entities.

## Progression Terms

### XP (Experience Points)

Currency for progression. Earned from combat, milestones, GM awards, and successful actions. See Document 12: Progression.

### Level

Measure of experience within a Class. Unlocks Skills and Abilities. Range 1-100. Does not directly increase stats. See Document 12: Progression.

### Difficulty Spectrum

A scale mapping challenge difficulty to XP rewards. The spectrum has 10 numbered tiers (1-10) plus **Mythic** as a category beyond the scale.

| Tier | Difficulty | Description |
|------|------------|-------------|
| 1-3 | Low | Routine challenges |
| 4-6 | Medium | Standard adventuring |
| 7-9 | High | Dangerous encounters |
| 10 | Extreme | Near-impossible |
| Mythic | Beyond scale | Godlike, world-shaping |

Note: Mythic is not "Tier 11"—it represents challenges that transcend normal difficulty measurement. See Document 12: Progression for full XP values.

### Legend Wall

The steep XP increase between Master bracket (400 XP/level) and Legend bracket (1,500 XP/level). Most characters never cross it. See Document 12: Progression.

### Soft Cap

A limit enforced by escalating cost rather than a hard rule. Stats have no maximum, but increasing XP cost acts as a natural limit. See Document 12: Progression.

## Movement & Positioning Terms

### Range Band

Abstract distance measurement. Four bands: Adjacent (0-1 squares), Near (2-4), Far (5-10), Distant (11+). See Document 14: Movement.

### Difficult Terrain

Terrain that costs extra movement. Half MOV (round down). Examples: mud, rubble, undergrowth. See Document 14: Movement.

### Cover

Protection from ranged attacks. Partial (+2 REF), Half (+4 REF), Full (untargetable). See Document 14: Movement.

### Opportunity Attack

A free melee attack triggered when an enemy leaves your adjacent square. Avoided by Step or Disengage. See Document 14: Movement.

### Flanking

Positioning bonus when two allies are on opposite sides of an enemy. Both must be adjacent. Grants +2 to hit. See Document 14: Movement.

## Equipment & Measurement Terms

### Slot

A location on an entity where equipment can be worn or wielded. Races define what slots an entity has. Items define what slots they require. See Document 15: Equipment & Slots.

### Equipped

An item in a slot, actively worn or wielded. Equipped items grant their mechanical benefits (stat bonuses, absorption, damage bonuses). Contrast with Carried. See Document 15: Equipment & Slots.

### Carried

An item in inventory, not slotted. Carried items provide no mechanical benefit until equipped. Counts toward weight but not slot limits. Contrast with Equipped. See Document 15: Equipment & Slots.

### Encumbered

State when total carried weight exceeds carrying capacity. Encumbered entities cannot take the Move action. See Document 15: Equipment & Slots.

### Weight Unit (WU)

The abstract unit of weight in TDGS. Content defines the scale (1 WU = 1 pound, 0.5 kg, etc.). The engine calculates in WU and is agnostic to measurement systems. See Document 15: Equipment & Slots.

### Square

The abstract unit of distance in TDGS. Content defines the scale (1 square = 5 feet, 1.5 meters, etc.). The engine calculates in squares and is agnostic to measurement systems. See Document 14: Movement.

## Character Creation Terms

### Delta Method

Stat generation formula using 4d6 drop lowest. Delta = Roll - 12. Final Stat = Racial Average + Delta, capped to racial range. See Document 13: Character Creation.

### Base Pool

In point buy, the sum of all racial stat averages. Must be spent within racial ranges. See Document 13: Character Creation.

### Heroic Pool

Optional bonus points (2d6 drop lowest) that CAN exceed racial ranges. Represents the spark that makes heroes exceptional. See Document 13: Character Creation.

### Soft Minimum

Recommended stat for a class, not enforced. A Fighter recommends STR 10+, but lower is allowed. The system allows bad decisions. See Document 13: Character Creation and Document 10: Classes.

## Document References

Each term category has a primary document where it is fully defined:

| Category | Primary Document |
|----------|------------------|
| Dice & Uncertainty | Document 1 |
| Core Attributes | Document 2 |
| Resolution | Document 3 |
| Luck | Document 4 |
| Action Taxonomy | Document 5 |
| Action Economy | Document 6 |
| Abilities | Document 7 |
| Combat | Document 8 |
| Entities | Document 9 |
| Classes | Document 10 |
| Races | Document 11 |
| Progression | Document 12 |
| Character Creation | Document 13 |
| Movement & Positioning | Document 14 |

## Status

> **Status:** Living Document

This glossary is updated as new terms are locked in design sessions and formalized in canonical documents.

---