*Document 7*

# Abilities

*What you can do beyond your innate capabilities*

## Purpose

This document defines the Ability system in TDGS: how characters gain, use, and improve capabilities beyond their base stats.

It establishes:

- What an Ability is
- The three types of Abilities (Skills, Spells, Traits)
- How Abilities are structured
- How Skills level and scale
- How Skill Tiers work
- How Spells and their cooldowns work
- Where Abilities come from

This document builds upon Document 2 (Core Attributes) and Document 5 (Action Taxonomy). Stats define what you ARE. Abilities define what you can DO.

## Stats vs Abilities

Stats and Abilities serve different purposes.

**Stats** are your innate capabilities. Your strength, reflexes, intelligence. They change rarely and slowly. They define the foundation of who you are.

**Abilities** are what you've learned, been granted, or were born with. They expand what you can do with your stats. They change through progression, acquisition, and circumstance.

A character with STR 10 and no combat training hits with +0.

A character with STR 10 and mastered combat skills across three tiers hits with +12 for relevant attacks.

**Stats are the foundation. Abilities are the specialization.**

## What Is an Ability?

An Ability is any capability a character possesses beyond their base stats.

Every Ability has:

```
NAME:         What the ability is called
DESCRIPTION:  What the ability does
TYPE:         Skill, Spell, or Trait
TIMING:       When it can be used (Action, Instant, Interrupt, Passive, etc.)
EFFECT:       What happens when used
COOLDOWN:     How long before it can be used again (if any)
```

Some Abilities also have:

```
PREREQUISITES:  What you need before gaining this ability
TIER:           The power level of this ability in its line
LEVEL:          How practiced you are (Skills only)
STAT BONUSES:   Modifiers to stats for relevant actions
```

## Cooldowns

Any Ability can have a cooldown. Cooldowns limit how often an Ability can be used.

### Cooldown Types

| Cooldown | Can Use Again |
|----------|---------------|
| None | Anytime you have actions |
| Round | Next round |
| Scene | Next scene |
| Day | After long rest |

A warrior's Devastating Blow might have a Scene cooldown. A dragon's Breath Weapon might have a Round cooldown. A priest's Divine Intervention might have a Day cooldown. A basic Melee Attack has no cooldown.

The Ability's description defines its cooldown (if any).

## The Three Types

All Abilities fall into one of three types.

### Skills

A **Skill** is a trained Ability that improves with practice.

Skills have levels (1-8). Higher levels mean greater mastery. Skills also belong to Tiers, with higher tiers representing more powerful capabilities that build on lower tiers.

Skills are the primary progression path for most characters. As you gain class levels, discover training, or acquire items, you gain and improve Skills.

**Examples:** Parry, Sneak Attack, Herbalism, Persuasion, Sniper

### Spells

A **Spell** is a magical Ability that channels supernatural power.

Spells do not have levels. A spell's power is fixed. Spells belong to Tiers; to gain more powerful magic, you learn higher tier spells.

Spells have cooldowns that limit how often they can be used (per round, per scene, or per day).

Spells use either Arcane magic (INT-based) or Divine magic (WIS-based).

**Examples:** Fire Bolt, Healing Touch, Invisibility, Lightning Strike, Resurrection

### Traits

A **Trait** is an innate Ability you possess by nature or circumstance.

Traits have no levels and no tiers. You either have a Trait or you don't. Traits come from your race, transformations, magical effects, or other sources.

If you want a more powerful version of a Trait, you need a different Trait entirely.

**Examples:** Darkvision, Poison Resistance, Flight, Regeneration, Amphibious

## Skill Levels

Skills have levels from 1 to 8. Level represents mastery of that specific skill.

### Progression

When you gain a Skill, you start at Level 1. As you practice, train, or gain class levels, your Skill level increases.

### Scaling

By default, Skills grant a +1 bonus at every even level:

| Level | Bonus | Notes |
|-------|-------|-------|
| 1 | +0 | Just learned |
| 2 | +1 | |
| 3 | +1 | |
| 4 | +2 | |
| 5 | +2 | |
| 6 | +3 | |
| 7 | +3 | |
| 8 | +4 | Mastery |

The maximum bonus from a single Skill is +4.

Some Skills may define custom scaling that overrides this default.

### What the Bonus Applies To

Skill bonuses apply to **relevant actions only** by default.

A Sniper skill grants +4 DEX for ranged attacks at long range. It does not help you dodge, pick locks, or do anything else with DEX. Your base DEX handles those.

Some Skills explicitly grant universal stat bonuses. The Skill description will say so.

## Skill Tiers

Skills exist in Tiers. Higher tier Skills are more powerful and build on lower tier Skills.

### What Tiers Represent

**Tier** represents the inherent power level of a Skill, not your mastery of it.

- A Tier 1 Skill at Level 8 is a master of basics.
- A Tier 3 Skill at Level 1 is a novice at advanced techniques.

The Tier 3 novice can do things the Tier 1 master simply cannot, because Tier unlocks capabilities.

### Tier Stacking

Bonuses from Skills in the same line stack for relevant actions.

**Sniper Line Example:**

```
Tier 1 - Shooter (Level 8)
  +4 DEX for ranged attacks
  Cooldown: None

Tier 2 - Sniper (Level 8)
  +4 DEX for ranged attacks (stacks)
  NEW: Can attack at extreme range
  Cooldown: None

Tier 3 - Master Sniper (Level 8)
  +4 DEX for ranged attacks (stacks)
  NEW: Ignore cover, critical hits are devastating
  NEW: "Perfect Shot" ability (Scene cooldown)

TOTAL: +12 DEX for ranged attacks, plus all unlocked capabilities
```

A character with DEX 10 and the full Sniper line maxed shoots like they have DEX 22 for those specific attacks.

### Tier Prerequisites

Higher tier Skills require:

- A lower tier Skill at a minimum level
- A minimum stat value
- Sometimes other requirements (narrative events, specific training, etc.)

TDGS provides the framework for prerequisites. The specific requirements are defined by content (class descriptions, setting guides, etc.).

## Spells

Spells are magical Abilities with fixed power.

### No Spell Levels

Unlike Skills, Spells do not have levels. Fire Bolt is Fire Bolt. It does what it does.

Want more powerful fire magic? Learn a higher tier spell. Fire Bolt → Flame Burst → Inferno.

### Spell Tiers

Spells belong to Tiers representing their power:

- **Tier 1:** Basic magic. Cantrips and minor effects.
- **Tier 2:** Standard adventurer magic. Reliable combat and utility spells.
- **Tier 3:** Powerful magic. Significant impact on encounters.
- **Tier 4:** Major magic. Changes the course of battles.
- **Tier 5+:** Legendary magic. World-altering effects.

Higher tier Spells typically require higher stats and knowledge of lower tier Spells.

### Spell Cooldowns

Most Spells have cooldowns. Minor spells might have Round cooldowns or none. Major spells typically have Scene or Day cooldowns.

The cooldown system is universal to all Abilities (see Cooldowns section above), but Spells almost always use it.

## Traits

Traits are innate Abilities with no progression.

### No Levels, No Tiers

Traits are binary. You have Darkvision or you don't. You have Poison Resistance or you don't.

There is no "Darkvision Level 5" or "Tier 2 Poison Resistance."

### Fixed Effects

A Trait's effect is fixed. Darkvision lets you see 60 feet in darkness. That's what it does. Always.

If you want better darkvision, you need a different Trait (Greater Darkvision), an item, or a spell.

### Trait Cooldowns

Some Traits have cooldowns. A Dragon's Breath Weapon is a Trait, but it can't be used every round. Passive Traits like Darkvision have no cooldown.

### Trait Sources

Traits commonly come from:

- **Race:** Your species grants innate Traits. A nocturnal race might have Darkvision. An aquatic race might be Amphibious.
- **Transformation:** Becoming something else grants new Traits. A werewolf gains Regeneration. A vampire gains Sunlight Vulnerability.
- **Items:** Magic items can grant Traits while equipped. Goggles of Night grant Darkvision.

When the source is removed, the Trait is removed. Lose the goggles, lose the Darkvision.

## Prerequisites

Some Abilities require other things before you can learn them.

### Prerequisite Types

| Type | Requirement |
|------|-------------|
| Skill Required | Must have [Skill Name] at Level [X] |
| Stat Required | Must have [Stat] at value [X] |
| Tier Required | Must have a Tier [X] skill in this line |
| Other | Narrative requirement (GM discretion) |

### Examples

**Sniper (Tier 2 Skill)**

```
Prerequisites:
  - Shooter at Level 4
  - DEX 15
```

**Resurrection (Tier 5 Spell)**

```
Prerequisites:
  - Healing Touch at any tier
  - WIS 25
  - Must have witnessed death and returned someone from it
```

**Dragon Slayer (Tier 4 Skill)**

```
Prerequisites:
  - Devastating Blow at Level 4
  - Dragon Lore at Level 2
  - Must have slain a dragon
```

### Framework, Not Content

TDGS provides the prerequisite framework. It does not define what every Skill, Spell, and Trait requires.

Content (class guides, setting books, monster manuals) defines specific prerequisites. TDGS just ensures the system supports them.

## Ability Sources

Where do Abilities come from?

### Class

Your class grants Abilities as you gain class levels. A warrior class gains combat Skills. A mage class gains Spells. Classes are the primary source of structured progression.

### Race

Your race grants starting Traits. A nocturnal race might have Darkvision. A mountain-dwelling race might have Altitude Tolerance. These are innate to what you are.

### Items

Equipment can grant Abilities while equipped. A Ring of Invisibility grants the Invisibility spell. Goggles of Night grant the Darkvision trait. Remove the item, lose the Ability.

### Effects

Temporary sources grant temporary Abilities. A potion of flight grants Flight for its duration. A divine boon might grant a Skill temporarily. A hex might grant a Trait you don't want.

### Training

A trainer can teach you Abilities outside your class structure. A warrior learns stealth techniques from a thief mentor. A mage learns swordplay from a blade master. This typically costs time and resources.

### Discovery

Found knowledge grants Abilities. An ancient tome teaches a forgotten Spell. A divine revelation grants a new Trait. A near-death experience unlocks a latent Skill.

### Source Doesn't Change Mechanics

The source of an Ability is narrative context. Mechanically, the Ability works the same regardless of where it came from.

Darkvision from being a nocturnal race, wearing enchanted goggles, or drinking a potion all function identically. You see in darkness. The source matters for story, not for rules.

## Ability Structure

Every Ability follows a consistent structure. This section provides templates for defining new Abilities.

### Skill Template

```
NAME: [Skill Name]
TYPE: Skill
TIER: [1-5+]
TIMING: [Action, Instant, Interrupt, Passive, Free]
COOLDOWN: [None, Round, Scene, or Day]

DESCRIPTION:
  [What this skill does]

PREREQUISITES:
  Skill Required: [Skill at Level X] (if any)
  Stat Required: [Stat at value X] (if any)
  Tier Required: [Tier X in this line] (if any)
  Other: [Narrative requirements] (if any)

EFFECT:
  [What happens when used]
  
STAT BONUS:
  [+X to STAT for relevant actions]
  Applies To: [What actions this bonus affects]
  Universal: [Yes/No - does it apply to all uses of that stat?]

SCALING:
  Default (+1 at levels 2, 4, 6, 8) or Custom: [define custom]

UNLOCKS AT TIER:
  [New capabilities this tier provides]
```

### Spell Template

```
NAME: [Spell Name]
TYPE: Spell
TIER: [1-5+]
MAGIC TYPE: [Arcane or Divine]
TIMING: [Action, Instant, Interrupt]
COOLDOWN: [None, Round, Scene, or Day]

DESCRIPTION:
  [What this spell does]

PREREQUISITES:
  Skill Required: [Skill at Level X] (if any)
  Stat Required: [Stat at value X] (if any)
  Spell Required: [Spell Name] (if any)
  Other: [Narrative requirements] (if any)

EFFECT:
  [What happens when cast]

RESOLUTION:
  Your Stat: [INT or WIS]
  Their Stat: [Target's WIS, or Difficulty]
```

### Trait Template

```
NAME: [Trait Name]
TYPE: Trait
SOURCE: [Racial, Transformation, Item, etc.]
COOLDOWN: [None, Round, Scene, or Day]

DESCRIPTION:
  [What this trait does]

EFFECT:
  [The fixed effect of this trait]

REMOVED WHEN:
  [Conditions under which this trait is lost, if any]
```

## Stat Bonuses in Detail

Skills often grant stat bonuses. Here's how they work.

### Relevant Actions

By default, a Skill's stat bonus applies only to actions relevant to that Skill.

**Shooter (Tier 1 Skill)**

```
Stat Bonus: +4 DEX (at Level 8)
Applies To: Ranged attacks

This bonus applies when:
  - Making a ranged attack
  
This bonus does NOT apply when:
  - Dodging
  - Picking a lock
  - Any other DEX-based action
```

### Universal Bonuses

Some Skills explicitly grant universal stat bonuses that apply to all uses of that stat.

**Physical Conditioning (Tier 1 Skill)**

```
Stat Bonus: +2 STR (at Level 8)
Applies To: ALL STR-based actions
Universal: Yes

This bonus applies when:
  - Making melee attacks
  - Grappling
  - Breaking down doors
  - Lifting heavy objects
  - Any STR-based action
```

Universal bonuses are rarer and typically lower than relevant-action bonuses.

### Stacking

Bonuses from different Skills stack if they apply to the same action.

**Making a sniper shot:**

```
Base DEX: 10
Shooter (Tier 1, Level 8): +4
Sniper (Tier 2, Level 8): +4
Master Sniper (Tier 3, Level 8): +4

Effective DEX: 22
```

Bonuses from the same Skill do not stack with itself (you can't have Shooter twice).

### Skills, Resolution, and Magnitude

Skills that raise Apparent Stats affect both resolution AND magnitude. This is intentional and does NOT violate the "Resolution and Magnitude Never Mix" principle.

The principle states: **The d20 roll never determines damage.**

What the principle means:

- The d20 determines IF you succeed
- Your stat determines HOW MUCH happens

What the principle does NOT mean:

- Stats can only affect one or the other

A skill that raises Apparent STR makes you:

- More likely to hit (higher stat in resolution formula)
- Hit harder (higher stat in damage formula)

This is correct. Training improves capability, not luck. The ROLL doesn't change magnitude. The STAT does. Skills change your stat for relevant actions, and that stat flows into both resolution and magnitude calculations.

## Summary Tables

### The Three Types

| Type | Levels | Tiers | Cooldowns |
|------|--------|-------|-----------|
| Skill | 1-8 | Yes | If defined |
| Spell | None | Yes | Almost always |
| Trait | None | None | If defined |

### Skill Scaling

| Level | Bonus |
|-------|-------|
| 1 | +0 |
| 2 | +1 |
| 3 | +1 |
| 4 | +2 |
| 5 | +2 |
| 6 | +3 |
| 7 | +3 |
| 8 | +4 |

### Ability Sources

| Source | Typical Types | Permanent? |
|--------|---------------|------------|
| Class | Skills, Spells | Yes |
| Race | Traits | Yes (until transformation) |
| Item | Any | While equipped |
| Effect | Any | For duration |
| Training | Skills, Spells | Yes |
| Discovery | Any | Yes |

## Document Status

> **Status:** Canonical

This document defines the Ability system for TDGS. All Skills, Spells, and Traits in the system conform to the structures and rules established here.

Specific Ability lists are defined in content documents (Classes, Races, Items, etc.), not in this core rules document.

---

