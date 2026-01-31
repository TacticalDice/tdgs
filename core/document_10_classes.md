*Document 10*

# Classes

*What you've trained to become*

## Purpose

This document defines what Classes are, how they work, and how to build them. It establishes the mechanics that all Classes follow, then provides template examples.

Classes represent training, profession, and learned capability. Race is what you ARE. Class is what you've BECOME.

## What Classes Provide

Every Class provides three things:

### 1. Abilities

Classes grant abilities of any type:

- **Skills** (leveled, tiered, trained)
- **Spells** (unleveled, tiered, magical)
- **Traits** (binary, passive, innate to the training)

What abilities a Class grants depends on what that Class is FOR. A Fighter grants combat skills. A Mage grants spells. A Thief grants stealth skills. A Peasant grants... not much.

### 2. Tier Unlocks

Higher-tier abilities become available as you level. A Level 1 Fighter can't learn Tier 4 abilities. A Level 60 Fighter can.

WHEN tiers unlock is defined per Class. A prodigy Class might unlock tiers early. A slow-burn Class might unlock late.

### 3. Stat Bonuses

Classes grant stat bonuses over time based on what the Class DOES. A Thief practices dexterity constantly, so the Thief Class grants DEX bonuses. A Fighter swings heavy weapons, so the Fighter Class grants STR bonuses.


## Class Structure

Every Class follows this structure:

```
CLASS DEFINITION:

Name:          [Class Name]
Purpose:       [What this class is FOR]
Primary Stats: [Which stats this class uses most]
Recommended Minimums: [Soft stat requirements]

Progression Table:
  Level 1:   [Starting abilities]
  Level 10:  [Abilities], [Tier unlock], [Stat bonus]
  Level 20:  [Abilities], [Stat bonus]
  ...
  Level 100: [Capstone abilities]
```

### Name

What the Class is called. Should convey purpose at a glance.

### Purpose

A brief statement of what this Class is FOR. Not fluff. Functional description.

Examples:

- Fighter: "Front-line martial combat"
- Thief: "Stealth, infiltration, and precision"
- Mage: "Arcane magic and scholarly knowledge"
- Peasant: "Survival and mundane labor"

### Primary Stats

Which stats this Class uses most. Guides players on where to invest. Also indicates which stats will receive bonuses.

Examples:

- Fighter: STR, CON
- Thief: DEX, REF
- Mage: INT, WIS
- Cleric: WIS, CHA

### Progression Table

What you get at each level. The heart of the Class.

### Recommended Minimums

Classes list recommended minimum stats. These are guidance, not gates.

A STR 6 character CAN take Fighter. They'll struggle with melee combat, miss more often, deal less damage. But the system allows it. The math handles consequences.

This preserves player agency while providing clear guidance. Want to play against type? Go ahead. Just understand the trade-offs.

```
Fighter
  Recommended: STR 10+, CON 10+
  
A Fighter with STR 8 and CON 8 is allowed.
They'll have lower hit chance, lower damage, fewer HP.
The choice is valid. The consequences are real.
```

## Ability Progression

### Skills Use +1 Modifiers

Classes grant Skills as modifiers.

```
"Power Strike +1" means:
  - If you DON'T have Power Strike: Learn it at Skill Level 1
  - If you ALREADY have Power Strike: Add 1 to your Skill Level
```

Skills can improve over time as the Class grants additional +1s.

### The Level 1 Exception

**A Level 1 class grant can NEVER add to an already-learned skill.**

If Fighter 1 grants "Power Strike +1" and you already know Power Strike from another source, you get nothing. You already know the basics.

This prevents multiclass dipping abuse. You can't take Level 1 of six different combat classes to stack +6 on a skill.

```
Example:
  Character takes Fighter 1: Power Strike +1 → Learns Power Strike (Lvl 1)
  Character takes Barbarian 1: Power Strike +1 → Already knows it, no bonus
  Character takes Fighter 10: Power Strike +1 → Now Skill Lvl 2
  Character takes Barbarian 10: Power Strike +1 → Now Skill Lvl 3
```

### Spells: Learn or Don't

Spells have no levels. Classes grant spells as "Learn [Spell Name]".

If you already know the spell, nothing happens. Want a stronger version? Learn a higher-tier spell.

### Traits: Have or Don't

Traits are binary. Classes grant traits as "Gain [Trait Name]".

If you already have the trait, nothing happens.

## Guidelines

These are suggestions, not rules. Classes can deviate based on purpose.

### Tier Unlock Guidelines

| Tier | Typical Unlock |
|------|----------------|
| Tier 1 | Available from Level 1 |
| Tier 2 | Around Level 10-20 |
| Tier 3 | Around Level 25-40 |
| Tier 4 | Around Level 50-70 |
| Tier 5 | Around Level 80+ |

A combat-focused Class might unlock tiers faster. A support Class might unlock slower. A Peasant Class might never unlock Tier 3.

### Stat Bonus Guidelines

```
~1 stat point per 10 levels
~10 total stat points by level 100
```

A combat Class might front-load STR bonuses. A Peasant Class might be stingy. Match the stat distribution to what the Class actually DOES.

## Template Classes

The following six templates demonstrate Class design patterns. They are examples, not canonical content.

> **Note:** THESE ARE EXAMPLES ONLY. TDGS is an engine, not a game. These templates show PATTERNS: how to structure a Class, how to pace tier unlocks, how to distribute stat bonuses, how a high-power Class differs from a low-power Class. Copy them. Modify them. Ignore them entirely. They're models, not scripture.

### Fighter

**Purpose:** Front-line martial combat  
**Primary Stats:** STR, CON  
**Recommended Minimums:** STR 10+, CON 10+

A Fighter hits things and doesn't die. Simple. Effective. The baseline for martial Classes.

| Level | Gains |
|-------|-------|
| 1 | Power Strike +1, Shield Use +1, Armor Training (Trait) |
| 10 | Power Strike +1, Battle Cry +1, **Unlock Tier 2**, +1 STR |
| 20 | Shield Use +1, Weapon Mastery +1, +1 CON |
| 40 | Power Strike +1, Cleave +1, **Unlock Tier 3**, +1 STR, +1 CON |
| 60 | Weapon Mastery +1, Unstoppable (Trait), **Unlock Tier 4**, +1 STR |
| 80 | Power Strike +1, Legend Strike +1, **Unlock Tier 5**, +1 STR, +1 CON |
| 100 | Weapon Mastery +1, Undying (Trait), +1 STR, +1 CON |

**Total Stat Bonuses by 100:** +5 STR, +4 CON (9 points)

*Design Notes: Front-loads combat skills. Tier unlocks at 10/40/60/80 (steady progression). Traits are passive survivability (Armor Training, Unstoppable, Undying). Heavy STR focus with CON support.*

### Thief

**Purpose:** Stealth, infiltration, and precision  
**Primary Stats:** DEX, REF  
**Recommended Minimums:** DEX 10+, REF 10+

A Thief goes where they shouldn't, takes what isn't theirs, and leaves without a trace. Precision over power.

| Level | Gains |
|-------|-------|
| 1 | Sneak +1, Pickpocket +1, Nimble (Trait) |
| 10 | Sneak +1, Backstab +1, **Unlock Tier 2**, +1 DEX |
| 20 | Lockpicking +1, Trap Sense +1, +1 REF |
| 40 | Sneak +1, Backstab +1, **Unlock Tier 3**, +1 DEX, +1 REF |
| 60 | Shadow Step +1, Evasion (Trait), **Unlock Tier 4**, +1 DEX |
| 80 | Backstab +1, Assassinate +1, **Unlock Tier 5**, +1 DEX, +1 REF |
| 100 | Shadow Step +1, Ghost (Trait), +1 DEX, +1 REF |

**Total Stat Bonuses by 100:** +5 DEX, +4 REF (9 points)

*Design Notes: Sneak and Backstab are core, upgraded repeatedly. Tier unlocks match Fighter (steady). Traits enhance mobility and evasion. DEX/REF focus for dodging and precision.*

### Mage

**Purpose:** Arcane magic and scholarly knowledge  
**Primary Stats:** INT, WIS  
**Recommended Minimums:** INT 10+, WIS 8+

A Mage wields arcane power through study and intellect. Glass cannon. Devastating offense, fragile defense.

| Level | Gains |
|-------|-------|
| 1 | Learn Fire Bolt (Spell), Learn Arcane Shield (Spell), Arcane Focus +1 |
| 10 | Learn Fireball (Spell), Spell Shaping +1, **Unlock Tier 2**, +1 INT |
| 20 | Learn Lightning Bolt (Spell), Arcane Focus +1, +1 WIS |
| 40 | Learn Meteor (Spell), Learn Teleport (Spell), **Unlock Tier 3**, +1 INT, +1 WIS |
| 60 | Learn Time Stop (Spell), Spell Mastery (Trait), **Unlock Tier 4**, +1 INT |
| 80 | Learn Disintegrate (Spell), Arcane Focus +1, **Unlock Tier 5**, +1 INT, +1 WIS |
| 100 | Learn Wish (Spell), Archmage (Trait), +1 INT, +1 WIS |

**Total Stat Bonuses by 100:** +5 INT, +4 WIS (9 points)

*Design Notes: Primarily grants Spells, few Skills. Arcane Focus is the main Skill (improves casting). Tier unlocks match Fighter (steady). INT focus with WIS support. High-tier spells are appropriately dramatic (Time Stop, Wish).*

### Cleric

**Purpose:** Divine magic and support  
**Primary Stats:** WIS, CHA  
**Recommended Minimums:** WIS 10+, CHA 8+

A Cleric channels divine power to heal, protect, and smite. The party's backbone.

| Level | Gains |
|-------|-------|
| 1 | Learn Heal (Spell), Learn Bless (Spell), Divine Focus +1 |
| 10 | Learn Smite (Spell), Turn Undead +1, **Unlock Tier 2**, +1 WIS |
| 20 | Learn Protection (Spell), Divine Focus +1, +1 CHA |
| 40 | Learn Resurrection (Spell), Learn Divine Wrath (Spell), **Unlock Tier 3**, +1 WIS, +1 CHA |
| 60 | Learn Sanctuary (Spell), Blessed (Trait), **Unlock Tier 4**, +1 WIS |
| 80 | Learn Miracle (Spell), Divine Focus +1, **Unlock Tier 5**, +1 WIS, +1 CHA |
| 100 | Learn Divine Intervention (Spell), Avatar (Trait), +1 WIS, +1 CHA |

**Total Stat Bonuses by 100:** +5 WIS, +4 CHA (9 points)

*Design Notes: Mix of healing, protection, and offensive spells. Divine Focus is the main Skill. Turn Undead is a class-defining Skill. WIS for power, CHA for presence. High-tier abilities are appropriately divine (Miracle, Divine Intervention).*

### Ranger

**Purpose:** Ranged combat, tracking, and nature affinity  
**Primary Stats:** DEX, WIS  
**Recommended Minimums:** DEX 10+, WIS 8+

A Ranger excels at range and thrives in the wild. Hybrid of combat and utility.

| Level | Gains |
|-------|-------|
| 1 | Archery +1, Tracking +1, Wilderness Survival (Trait) |
| 10 | Archery +1, Animal Companion +1, **Unlock Tier 2**, +1 DEX |
| 20 | Tracking +1, Camouflage +1, +1 WIS |
| 40 | Archery +1, Called Shot +1, **Unlock Tier 3**, +1 DEX, +1 WIS |
| 60 | Learn Nature's Wrath (Spell), Predator (Trait), **Unlock Tier 4**, +1 DEX |
| 80 | Archery +1, Deadeye +1, **Unlock Tier 5**, +1 DEX, +1 WIS |
| 100 | Called Shot +1, One With Nature (Trait), +1 DEX, +1 WIS |

**Total Stat Bonuses by 100:** +5 DEX, +4 WIS (9 points)

*Design Notes: Primarily Skills with occasional Spell access. Archery is upgraded repeatedly (core identity). Animal Companion is a class-defining Skill. Mix of combat (Archery, Called Shot) and utility (Tracking, Camouflage). DEX for shooting, WIS for perception and nature magic.*

### Peasant

**Purpose:** Survival and mundane labor  
**Primary Stats:** CON, WIS  
**Recommended Minimums:** None (anyone can be a peasant)

A Peasant is not a hero. They're an ordinary person doing ordinary things. This template demonstrates low-power Class design.

| Level | Gains |
|-------|-------|
| 1 | Labor +1, Endure (Trait) |
| 10 | Labor +1, Haggle +1, +1 CON |
| 20 | Common Sense +1, **Unlock Tier 2**, +1 WIS |
| 40 | Labor +1, Animal Handling +1, +1 CON |
| 60 | Stubborn (Trait), +1 WIS |
| 80 | Labor +1, **Unlock Tier 3**, +1 CON |
| 100 | Survivor (Trait), +1 CON, +1 WIS |

**Total Stat Bonuses by 100:** +4 CON, +3 WIS (7 points)

*Design Notes: Fewer abilities than heroic Classes. Tier unlocks are SLOW (Tier 2 at 20, Tier 3 at 80, never reaches Tier 4 or 5). Fewer stat bonuses (7 instead of 9). Abilities are mundane (Labor, Haggle, Common Sense). Traits emphasize endurance over power. A Level 100 Peasant is remarkably resilient but not heroic.*

## Building Your Own Classes

When designing a Class, ask these questions:

### 1. What is this Class FOR?

Be specific. "Combat" is too vague. "Front-line martial combat with sword and shield" is better. "Dealing maximum damage while ignoring personal safety" is even better.

Purpose drives every other decision.

### 2. What stats matter?

Pick 1-2 primary stats. These are:

- What the Class uses for its abilities
- What the Class grants bonuses to
- What players should invest in

### 3. What abilities define this Class?

Every Class has 2-3 "core" abilities that get upgraded repeatedly. For Fighter, it's Power Strike and Weapon Mastery. For Thief, it's Sneak and Backstab.

These are the Class identity. Everything else is support.

### 4. How fast should power scale?

Heroic Classes unlock tiers on schedule and grant full stat bonuses. Low-power Classes unlock slower and grant less.

Match the scaling to the fantasy. A "Berserker" might front-load offense and unlock Tier 3 early. A "Scholar" might unlock slowly but have broader utility.

### 5. What makes this Class different?

If your Class feels like another Class with different names, reconsider. Classes should have distinct identities.

Fighter and Barbarian both hit things. What makes them different? Barbarian might:

- Trade armor for damage
- Have rage-based abilities
- Grant more STR but less CON
- Unlock offensive tiers faster, defensive tiers slower

Differentiation creates meaningful choice.

## Multiclassing

Characters can have levels in multiple Classes. Here's the summary:

- **Unrestricted:** Any Class, any combination
- **Single XP Pool:** XP is earned once, player chooses how to split
- **Separate Progression:** Level 20 Fighter / Level 10 Thief pays Journeyman costs for Fighter levels, Novice costs for Thief levels
- **Level 1 Exception:** Taking Level 1 of a new Class doesn't add to already-learned Skills

Multiclassing lets players build hybrids. A Fighter/Mage. A Thief/Ranger. A Cleric/Fighter. The system doesn't restrict. The math handles it.

## Summary

| Component | Description |
|-----------|-------------|
| Classes Provide | Abilities, Tier Unlocks, Stat Bonuses |
| Structure | Name, Purpose, Primary Stats, Progression Table |
| Skills | +1 system, can improve, Level 1 exception |
| Spells | Learn or don't, no +1 system |
| Traits | Have or don't, no +1 system |
| Tier Guidelines | T1=1, T2=10-20, T3=25-40, T4=50-70, T5=80+ |
| Stat Guidelines | ~1 per 10 levels, ~10 total by level 100 |

Templates demonstrate patterns. Adapt them to your needs.

## Document Status

> **Status:** Canonical

This document defines Class mechanics and provides template examples for TDGS. All Classes in TDGS-based systems should follow the structure and mechanics defined here.

---
