*Document 11*

# Races

*What you ARE, inherently*

## Purpose

This document defines what Races are, how they work, and how to build them. It establishes the mechanics that all Races follow, then provides template examples.

Races represent inherent nature, biology, and inborn capability. Class is what you've BECOME. Race is what you ARE.

## What Races Provide

Every Race provides three things:

### 1. Innate Traits

Races grant Traits that are inherent to being that thing. A Dragon breathes fire because it's a Dragon, not because it studied fire-breathing. An Elf sees in the dark because Elves see in the dark.

This includes:

- Natural weapons (claws, bite, horns)
- Natural armor (scales, shell, thick hide)
- Innate abilities (darkvision, flight, breath weapons)

### 2. Base Stat Ranges

Races define starting stat ranges. A Dragon's minimum STR is higher than a Human's maximum. A Goblin's maximum CON is lower than a Dwarf's minimum.

These ranges define where you BEGIN, not where you end. Training, items, and class bonuses can push stats beyond racial limits later.

### 3. Size

Size is inherent to what you ARE. A Dragon is large because it's a Dragon. A Pixie is tiny because it's a Pixie. Size is a framework property; content defines what sizes mean mechanically.


## Race Structure

Every Race follows this structure:

```
RACE DEFINITION:

Name:         [Race Name]
Size:         [Size category]
Description:  [What this race IS]

Base Stat Ranges:
  STR: [min]-[max]
  DEX: [min]-[max]
  CON: [min]-[max]
  INT: [min]-[max]
  WIS: [min]-[max]
  CHA: [min]-[max]
  REF: [min]-[max]
  MOV: [min]-[max]
  LUK: [min]-[max]

Slots:
  [Location]: [count]
  [Location]: [count]
  ...

Natural Weapons:
  - [Weapon] (+X damage or +XdY damage)

Natural Armor:
  - [Armor] (X% Deflection)

Traits:
  - [Trait 1]
  - [Trait 2]
```

### Name

What the Race is called.

### Size

The typical size category for this Race. Content defines what sizes exist and what they mean.

### Description

A brief statement of what this Race IS. Not lore. Functional identity.

### Base Stat Ranges

Minimum and maximum starting values for each stat. Characters of this Race must start within these ranges. Advancement can exceed them later.

**Default LUK Range:** Most races have LUK -3 to +3. Races with unusual fortune (or misfortune) note exceptions.

### Natural Weapons

Innate attacks the Race can make. Listed with damage bonus. Using a natural weapon is an action (cannot combine with held weapon in same attack).

Damage can be flat (+5) or dice-based (+1d6) or both (+2 + 1d4). Content decides per weapon.

### Natural Armor

Innate protection the Race has. Listed with Deflection percentage. Stacks with worn armor, respecting the 75% cap. For how armor interacts with equipment slots, see Document 15 (Equipment & Slots).

### Slots

What equipment locations this Race has. A standard humanoid has Head, Face, Ears (2), Neck, Torso, Back, Arms (2), Hands (2), Fingers (10), Waist, Legs (2), and Feet (2). Non-humanoids may have different slots (a Dragon has no Finger slots; a spider has 8 Leg slots).

Slots define where equipment CAN go. What equipment EXISTS is content's job. For full slot mechanics, see Document 15 (Equipment & Slots).


### Traits

Other innate abilities. Binary (have or don't). No levels, no tiers.

## Human As Baseline

Human is the baseline Race. All other Races are implicitly compared to Human.

```
HUMAN BASELINE:
  Average stat: 10
  Typical range: 6-14

When designing a Race:
  "Stronger than Human" = higher STR range
  "Less intelligent than Human" = lower INT range
  "About as fast as Human" = similar MOV range
```

This makes Race design intuitive. Everyone understands what "Human" means.

## Template Races

The following six templates demonstrate Race design patterns. They are examples, not canonical content.

**THESE ARE EXAMPLES ONLY.**

TDGS is an engine, not a game. These templates show PATTERNS: how to structure a Race, how stat ranges convey racial identity, how a powerful Race differs from a weak Race, how Traits define racial flavor.

Copy them. Modify them. Ignore them entirely. They're models, not scripture.


### Human

**Size:** Medium

*The baseline. Adaptable, versatile, unremarkable in any single area but capable of anything.*

**Base Stat Ranges**

| Stat | Range |
|------|-------|
| STR | 6-14 |
| DEX | 6-14 |
| CON | 6-14 |
| INT | 6-14 |
| WIS | 6-14 |
| CHA | 6-14 |
| REF | 6-14 |
| MOV | 8-12 |
| LUK | -3 to +3 |

**Natural Weapons:** None.

**Natural Armor:** None.

**Slots:** Standard Humanoid: Head (1), Face (1), Ears (2), Neck (1), Torso (1), Back (1), Arm (2), Hand (2), Finger (10), Waist (1), Leg (2), Foot (2).

**Traits:**

- **Adaptable:** +1 to any single stat at character creation (player's choice)
- **Versatile:** No multiclassing restrictions or penalties

*Design Notes: Average 10 in everything. No natural advantages or disadvantages. Traits emphasize flexibility over specialization. The "default" against which all others are measured.*

### Elf

**Size:** Medium

*Agile, long-lived, magically inclined. Graceful but fragile compared to sturdier races.*

**Base Stat Ranges**

| Stat | Range |
|------|-------|
| STR | 4-12 |
| DEX | 8-16 |
| CON | 4-12 |
| INT | 8-16 |
| WIS | 8-16 |
| CHA | 6-14 |
| REF | 8-16 |
| MOV | 8-12 |
| LUK | -3 to +3 |

**Natural Weapons:** None.

**Natural Armor:** None.

**Slots:** Standard Humanoid: Head (1), Face (1), Ears (2), Neck (1), Torso (1), Back (1), Arm (2), Hand (2), Finger (10), Waist (1), Leg (2), Foot (2).

**Traits:**

- **Darkvision:** Can see in darkness as if dim light
- **Longevity:** Lifespan measured in centuries; resistant to aging effects
- **Arcane Affinity:** +1 to INT-based magic rolls

*Design Notes: Higher DEX, INT, WIS, REF than Human. Lower STR, CON than Human. Glass cannon profile: agile and smart, not tough. Traits lean magical and perceptive.*


### Dwarf

**Size:** Medium

*Stout, resilient, stubborn. Built like the mountains they often inhabit.*

**Base Stat Ranges**

| Stat | Range |
|------|-------|
| STR | 8-16 |
| DEX | 4-12 |
| CON | 10-18 |
| INT | 6-14 |
| WIS | 8-14 |
| CHA | 4-12 |
| REF | 4-12 |
| MOV | 6-10 |
| LUK | -3 to +3 |

**Natural Weapons:** None.

**Natural Armor:** None.

**Slots:** Standard Humanoid: Head (1), Face (1), Ears (2), Neck (1), Torso (1), Back (1), Arm (2), Hand (2), Finger (10), Waist (1), Leg (2), Foot (2).

**Traits:**

- **Darkvision:** Can see in darkness as if dim light
- **Poison Resistance:** +4 to CON saves against poison
- **Sturdy:** Cannot be knocked Prone by creatures of equal or smaller Size

*Design Notes: Higher STR, CON than Human. Lower DEX, CHA, REF, MOV than Human. Tank profile: tough and strong, not agile. Traits emphasize resilience and stability.*

### Orc

**Size:** Medium (large end)

*Powerful, aggressive, built for violence. Raw physical might over finesse.*

**Base Stat Ranges**

| Stat | Range |
|------|-------|
| STR | 10-18 |
| DEX | 4-12 |
| CON | 10-18 |
| INT | 4-10 |
| WIS | 4-12 |
| CHA | 4-12 |
| REF | 6-12 |
| MOV | 8-12 |
| LUK | -3 to +3 |

**Natural Weapons:** None (but often depicted with tusks that could be added as a Trait).

**Natural Armor:** None.

**Slots:** Standard Humanoid: Head (1), Face (1), Ears (2), Neck (1), Torso (1), Back (1), Arm (2), Hand (2), Finger (10), Waist (1), Leg (2), Foot (2).

**Traits:**

- **Intimidating Presence:** +2 to CHA-based intimidation rolls
- **Relentless:** Once per Scene, when reduced to Knockout threshold, may act for one more Round before falling unconscious
- **Low-Light Vision:** Can see in dim light as if bright light

*Design Notes: Higher STR, CON than Human. Lower INT, WIS, DEX, CHA than Human. Brute profile: hit hard, take hits, don't think too hard. Relentless makes them dangerous even when "beaten".*


### Goblin

**Size:** Small

*Small, weak, cowardly, but cunning and surprisingly hard to kill. The low end of the power spectrum.*

**Base Stat Ranges**

| Stat | Range |
|------|-------|
| STR | 4-10 |
| DEX | 8-14 |
| CON | 4-10 |
| INT | 4-12 |
| WIS | 6-12 |
| CHA | 4-10 |
| REF | 8-14 |
| MOV | 8-12 |
| LUK | -3 to +3 |

**Natural Weapons:** None.

**Natural Armor:** None.

**Slots:** Standard Humanoid: Head (1), Face (1), Ears (2), Neck (1), Torso (1), Back (1), Arm (2), Hand (2), Finger (10), Waist (1), Leg (2), Foot (2).

**Traits:**

- **Darkvision:** Can see in darkness as if dim light
- **Cowardly:** -2 to saves against Frightened, but +2 to REF when fleeing
- **Nimble Escape:** Can Disengage as a Free action once per Round

*Design Notes: Lower STR, CON, CHA, INT than Human. Higher DEX, REF than Human. Survivor profile: not good at fighting, very good at not dying. Cowardly is a double-edged Trait (penalty AND bonus). Demonstrates low-power Race design.*

### Dragon

**Size:** Gargantuan

*Apex predator. Ancient, powerful, terrifying. The high end of the power spectrum.*

**Base Stat Ranges**

| Stat | Range |
|------|-------|
| STR | 30-50 |
| DEX | 15-25 |
| CON | 35-55 |
| INT | 15-25 |
| WIS | 15-25 |
| CHA | 20-40 |
| REF | 15-25 |
| MOV | 20-35 |
| LUK | -3 to +3 |

**Natural Weapons:**

- **Claws** (+2d6 damage)
- **Bite** (+3d6 damage)
- **Tail Sweep** (+1d8 damage, can hit multiple targets)

**Natural Armor:**

- **Dragon Scales** (40% Deflection)

**Slots:** Draconic: Head (1), Face (1), Ears (2), Neck (1), Torso (1), Back (1), Wing (2), Foreleg (2), Claw (4), Hindleg (2), Tail (1). No Finger slots, no Hand slots (claws cannot manipulate fine objects without magic).

**Traits:**

- **Flight:** Can fly at MOV speed
- **Breath Weapon:** Powerful area attack (element and damage defined by content), Scene cooldown
- **Frightening Presence:** Enemies within sight must save vs WIS or become Frightened
- **Elemental Affinity:** Resistance or immunity to one element (defined by content)
- **Ancient Knowledge:** +2 to INT-based knowledge rolls

*Design Notes: ALL stats higher than Human maximums. Multiple natural weapons with significant damage. Natural armor provides substantial protection. Flight changes tactical assumptions entirely. Frightening Presence affects battles before they begin. Non-humanoid slot layout demonstrates how Races can have completely different equipment options. Not balanced against Human. Not supposed to be.*


## Building Your Own Races

When designing a Race, ask these questions:

### 1. What IS this Race?

Not backstory. Identity. "Big and strong" or "small and sneaky" or "magical and frail." The core truth that drives everything else.

### 2. How does it compare to Human?

Use Human as your anchor. Stronger? Smarter? Faster? Tougher? Where does this Race exceed Human baseline, and where does it fall short?

Most Races should have tradeoffs. Higher STR might mean lower INT. Higher DEX might mean lower CON. Pure upgrades (like Dragon) should be rare and intentional.

### 3. What makes it FEEL different?

Traits define racial flavor. An Elf without Darkvision and Longevity doesn't feel like an Elf. A Dwarf without Poison Resistance and Sturdy doesn't feel like a Dwarf.

Pick 2-4 Traits that capture the Race's essence.

### 4. Does it have natural weapons or armor?

Most humanoid Races don't. Beasts and monsters often do. Natural weapons and armor significantly increase combat power without requiring equipment.

A Race with 40% Deflection scales (Dragon) is dramatically tougher than a Race that needs to buy armor (Human).

### 5. What Size is it?

Size affects narrative and may affect mechanics depending on content implementation. A Tiny Race has different challenges than a Gargantuan Race.


## Power Spectrum

Races span a wide power range. This is intentional.

| Race | Power Level | Role |
|------|-------------|------|
| Goblin | Low | Cannon fodder, underdog PCs |
| Human | Baseline | Default, versatile |
| Elf | Baseline+ | Specialized but balanced |
| Dwarf | Baseline+ | Specialized but balanced |
| Orc | Baseline+ | Combat-focused |
| Dragon | High | Boss monster, special PCs |

A Goblin PC fighting alongside a Dragon PC creates imbalance. This isn't a bug. TDGS doesn't assume balanced parties. It provides the math to handle whatever you throw at it.

If your setting wants balanced parties, restrict Race choices. If your setting wants a Goblin sidekick to a Dragon hero, the system supports that too.

## Transformation

When an entity changes Race (human becomes vampire, wizard becomes snake), several things happen:

1. **Stats may change** to fit new racial ranges
2. **Racial Traits swap** (lose old racial Traits, gain new ones)
3. **Class abilities persist** (but may become Dormant if physically impossible)
4. **Power Tier recalculates** based on new stats

Transformation is covered in detail in Document 7 (Abilities). The key point: Race is what you ARE right now, and what you ARE can change.

## Summary

| Component | Description |
|-----------|-------------|
| Races Provide | Traits, Base Stat Ranges, Size, Slots |
| Stat Ranges | Starting limits only; can exceed later |
| Human Baseline | Human average = 10; compare other Races to Human |
| LUK Range | Default -3 to +3; exceptions noted |
| Slots | Equipment locations; standard humanoid has 26 total |
| Natural Weapons | Listed separately; use as action |
| Natural Armor | Listed separately; stacks with worn (75% cap) |
| Templates | 6 examples across power spectrum |

Races define what you ARE. Classes define what you BECOME. Together, they create an Entity.

## Document Status

> **Status:** Canonical

This document defines Race mechanics and provides template examples for TDGS. All Races in TDGS-based systems should follow the structure and mechanics defined here.

---
