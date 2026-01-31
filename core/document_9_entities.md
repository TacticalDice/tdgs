*Document 9*

# Entities

*What things ARE in the game world*

## Purpose

This document defines what an Entity is and what every Entity contains. It establishes the universal structure that applies to player characters, NPCs, creatures, and anything else that can act.

This is the skeleton. Race (Document 11) and Classes (Document 10) are the flesh that fills it.

## What Is An Entity?

An Entity is anything that can act in the game world.

The test is simple: **Can it take a turn?** If yes, it's an Entity.

This includes:

- Player characters
- NPCs (friendly, neutral, hostile)
- Creatures (animals, monsters, dragons)
- Constructs (golems, automatons)
- Spirits (ghosts, elementals)
- Divine beings (angels, demons, gods)

This does NOT include:

- Objects (doors, chests, traps)
- Environmental effects (weather, lava)
- Abstract concepts (factions, organizations)

A locked door has stats (hardness, hit points), but it doesn't take turns. It's an object, not an Entity. The golem guarding that door? Entity.

## Entity Structure

Every Entity in TDGS has the same structure. Some sections may be empty, but the structure is universal.

### Identity

Who or what is this Entity?

| Field | Description |
|-------|-------------|
| Name | What it's called |
| Type | Role in the game (Player, NPC, Creature, etc.) |
| Race | What it IS (Human, Dragon, Slime, etc.) |
| Class Levels | What it's TRAINED as (Warrior 5, Mage 2, etc.) |
| Size | How big it is (content defines meaning) |

**Type** is a label with no mechanical effect. It tells you how this Entity fits into the game: Is it player-controlled? GM-controlled? A monster?

**Race** determines innate Traits. A Dragon has Traits because it's a Dragon. A Human has different Traits because it's a Human.

**Class Levels** determine learned abilities. A Level 5 Warrior has Warrior skills. An Entity can have multiple classes (multiclassing) or no classes at all.

**Size** represents physical scale, from Tiny to Gargantuan. Size affects space occupied, natural reach, grappling, and forced movement. See Size Categories below.

### Stats

Every Entity has all nine stats.

| Stat | Governs |
|------|---------|
| STR | Physical power, melee damage |
| DEX | Agility, ranged damage, fine motor |
| CON | Toughness, health, endurance |
| INT | Reasoning, arcane magic, knowledge |
| WIS | Perception, divine magic, willpower |
| CHA | Presence, influence, force of personality |
| REF | Reaction speed, defense, initiative |
| MOV | Movement speed, pursuit, escape |
| LUK | Fortune, probability distortion |

There is no "N/A" stat. A mindless slime has INT. It's probably INT 1, but it has one. A statue brought to life has CHA. It's not charismatic, but it has the stat.

This universality matters. The resolution formula works on any Entity against any other Entity because they all have the same stats.

### Derived Values

Values calculated from stats.

| Value | Formula | Description |
|-------|---------|-------------|
| HP | Apparent CON × 5 | How much damage before death |
| Knockout Threshold | HP × 0.05 (rounded down) | When unconsciousness occurs |
| Base Power Tier | Sum of 8 base stats / 8 | Inherent power level |
| Apparent Power Tier | Sum of 8 apparent stats / 8 | Current effective power |

**HP** uses Apparent CON, not base CON. Gear that boosts CON boosts HP.

**Power Tier** excludes LUK. Luck operates on a different scale and affects probability, not capability. A lucky peasant is still a peasant.

**Base Power Tier** is what you ARE. It doesn't change when you equip gear. A dragon is Tier 40 whether naked or adorned in magic rings.

**Apparent Power Tier** is what you FUNCTION AS right now. Gear, buffs, and debuffs all affect it. A hero in divine armor might function as Tier 30. The same hero drunk and naked might function as Tier 15.

### Abilities

What this Entity can DO beyond basic actions.

| Category | Source | Has Levels? | Has Tiers? |
|----------|--------|-------------|------------|
| Skills | Class, Training | Yes (1-8) | Yes |
| Spells | Class, Training | No | Yes |
| Traits | Race, Transformation | No | No |

**Skills** are trained abilities. They come from Classes or special training. They have levels (1-8) and tiers. A Warrior learns combat skills. A Thief learns stealth skills.

**Spells** are magical abilities. They come from magical Classes or special sources. They have tiers but no levels. You learn new spells, not stronger versions of the same spell.

**Traits** are innate abilities. They come from Race or transformation. They have no levels and no tiers. You have them or you don't. A dragon breathes fire because it's a dragon, not because it studied fire-breathing.

**Natural Weapons and Armor** are Traits.

A dragon's claws are a Trait: "Claws (+5 damage)". Using claws is an action like any other attack. You can't swing claws AND a sword in the same action.

A turtle's shell is a Trait: "Shell (50% Deflection)". Natural armor stacks with worn armor, respecting the 75% deflection cap. A turtle in chain mail has 75% deflection, not 80%.

### Equipment

What this Entity is carrying and wearing.

| Category | Description |
|----------|-------------|
| Weapons | Things used to attack (sword, bow, wand) |
| Armor | Things that protect (plate, shield, robe) |
| Accessories | Worn items that aren't armor (rings, cloaks, boots) |
| Items | Carried objects (potions, tools, keys) |

Equipment may be empty. A ghost has no equipment. A wild wolf has no equipment. A peasant might have a rusty knife and the clothes on their back.

Equipment affects Apparent Stats. A ring of +2 STR increases Apparent STR. This affects damage, HP (if CON), Power Tier, and anything else derived from that stat.

### Status

The Entity's current state.

| Field | Description |
|-------|-------------|
| Current HP | How much health remains |
| Conditions | Active buffs and debuffs |
| XP | Experience points (if tracking) |

**Current HP** starts at max HP and changes through damage and healing.

**Conditions** are temporary states like Poisoned, Hasted, or Prone. See Combat for example conditions.

**XP** tracks experience for advancement. Not all Entities track XP. A random goblin doesn't need an XP total. Player characters do.

## Size Categories

Size represents physical scale and affects several mechanical systems.

### Categories

| Category | Space | Reach | Examples |
|----------|-------|-------|----------|
| Tiny | <1 sq | 0 | Rat, pixie, insect |
| Small | 1 sq | 1 sq (Adjacent) | Goblin, halfling, dog |
| Medium | 1 sq | 1 sq (Adjacent) | Human, elf, orc |
| Large | 2×2 sq | 2 sq (Near) | Horse, ogre, dire wolf |
| Huge | 3×3 sq | 3 sq (Near) | Giant, elephant, young dragon |
| Gargantuan | 4×4+ sq | 4+ sq (Near/Far) | Ancient dragon, kraken, titan |

### What Size Affects

**Space Occupied:** Larger creatures occupy more squares on the grid. A Large creature occupies 4 squares (2×2).

**Natural Reach:** Larger creatures can strike targets further away without moving. Reach is measured from any edge of the creature's space.

### Grappling

Size difference creates modifiers when grappling.

| Size Difference | Modifier |
|-----------------|----------|
| Same size | +0 |
| 1 category smaller | +2 to larger |
| 2 categories smaller | +4 to larger |
| 3+ categories smaller | Auto-success for larger |

A Medium creature grappling a Large creature has -2. The Large creature has +2.

### Forced Movement Resistance

Larger creatures resist being pushed, pulled, or slid.

| Size Difference | Effect |
|-----------------|--------|
| Same size | Normal |
| Target 1 category larger | Distance halved (round down) |
| Target 2+ categories larger | No forced movement |

### Carrying Capacity

Larger creatures can carry more. Base carrying capacity is STR × 10 WU (Weight Units), multiplied by size.

| Category | Multiplier |
|----------|------------|
| Tiny | ×0.25 |
| Small | ×0.5 |
| Medium | ×1 |
| Large | ×2 |
| Huge | ×4 |
| Gargantuan | ×8+ |

This determines weight-based capacity. For slot-based equipment (what you wear and wield), see Document 15 (Equipment & Slots).

### Squeezing

A creature can squeeze through a space one size category smaller than itself. While squeezing: movement costs double, attacks have -2, attackers have +2 against it.

## The Complete Entity Structure

```
ENTITY
│
├── IDENTITY
│   ├── Name
│   ├── Type
│   ├── Race
│   ├── Class Levels []
│   └── Size
│
├── STATS
│   ├── STR
│   ├── DEX
│   ├── CON
│   ├── INT
│   ├── WIS
│   ├── CHA
│   ├── REF
│   ├── MOV
│   └── LUK
│
├── DERIVED VALUES
│   ├── HP (Apparent CON × 5)
│   ├── Knockout Threshold (HP × 0.05)
│   ├── Base Power Tier (base stats / 8)
│   └── Apparent Power Tier (apparent stats / 8)
│
├── ABILITIES
│   ├── Skills []
│   ├── Spells []
│   └── Traits []
│
├── EQUIPMENT
│   ├── Weapons []
│   ├── Armor []
│   ├── Accessories []
│   └── Items []
│
└── STATUS
    ├── Current HP
    ├── Conditions []
    └── XP
```

## Examples

### Simple Creature: Goblin

```
IDENTITY
  Name: Goblin
  Type: Creature
  Race: Goblin
  Class Levels: None
  Size: Small

STATS
  STR: 8   DEX: 12  CON: 8
  INT: 6   WIS: 8   CHA: 6
  REF: 11  MOV: 10  LUK: 0

DERIVED VALUES
  HP: 40 (CON 8 × 5)
  Knockout: 2 (5% of 40)
  Base Power Tier: 8 ((8+12+8+6+8+6+11+10) / 8 = 69/8 = 8)
  Apparent Power Tier: 8 (no gear bonuses)

ABILITIES
  Skills: None
  Spells: None
  Traits: Darkvision, Cowardly

EQUIPMENT
  Weapons: Rusty Dagger (+0 hit, +1 dmg)
  Armor: Leather Scraps (10% Deflection)
  Accessories: None
  Items: 3 copper coins

STATUS
  Current HP: 40
  Conditions: None
  XP: N/A
```

### Player Character: Human Warrior

```
IDENTITY
  Name: Kira Stonefist
  Type: Player
  Race: Human
  Class Levels: Warrior 8
  Size: Medium

STATS
  STR: 16  DEX: 12  CON: 14
  INT: 10  WIS: 10  CHA: 11
  REF: 12  MOV: 10  LUK: +1

DERIVED VALUES
  HP: 80 (Apparent CON 16 × 5, includes +2 from belt)
  Knockout: 4 (5% of 80)
  Base Power Tier: 11 ((16+12+14+10+10+11+12+10) / 8 = 95/8 = 11)
  Apparent Power Tier: 13 ((18+12+16+10+10+11+14+10) / 8 = 101/8 = 12)

ABILITIES
  Skills: Power Strike (Lvl 6), Shield Bash (Lvl 4), Battle Cry (Lvl 3)
  Spells: None
  Traits: Adaptable (Human racial)

EQUIPMENT
  Weapons: Masterwork Longsword (+2 hit, +3 dmg)
  Armor: Steel Plate (50% Deflection), Tower Shield (Ablative 100, recharges)
  Accessories: Belt of Constitution (+2 CON), Ring of Reflexes (+2 REF)
  Items: 3 Healing Potions, 50 gold

STATUS
  Current HP: 80
  Conditions: None
  XP: 4,250
```

### Powerful Creature: Dragon

A fire dragon who studied fire magic. Because why not be *really* good at your thing?

```
IDENTITY
  Name: Flamey Eight-ball
  Type: Creature
  Race: Fire Dragon
  Class Levels: Wizard 12
  Size: Gargantuan

STATS
  STR: 38  DEX: 22  CON: 45
  INT: 20  WIS: 18  CHA: 35
  REF: 20  MOV: 28  LUK: +3

DERIVED VALUES
  HP: 225 (CON 45 × 5)
  Knockout: 11 (5% of 225)
  Base Power Tier: 28 ((38+22+45+20+18+35+20+28) / 8 = 226/8 = 28)
  Apparent Power Tier: 28 (no gear)

ABILITIES
  Skills: Arcane Focus (Lvl 6), Spell Shaping (Lvl 4)
  Spells: Fireball (Tier 3), Wall of Fire (Tier 3), Fire Shield (Tier 2), Warmth (Tier 1)
  Traits: 
    - Fire Breath (55 damage, cone, Scene cooldown)
    - Claws (+2d6 damage)
    - Bite (+3d6 damage)
    - Dragon Scales (40% Deflection)
    - Flight
    - Fire Immunity
    - Unsettlingly Friendly (CHA-based, targets are Charmed on failed WIS save)
    - Loves Campfires (heals 5% HP per round when near open flame)

EQUIPMENT
  Weapons: None (natural weapons)
  Armor: None (natural armor)
  Accessories: None
  Items: Collection of burnt marshmallows, singed friendship bracelets

STATUS
  Current HP: 225
  Conditions: None
  XP: N/A
```

## Building Entities

### From Race

Start with Race. Race provides:

- Base stat ranges (a Dragon has higher base stats than a Goblin)
- Innate Traits (Darkvision, Fire Breath, etc.)
- Size
- Natural weapons/armor (if any)

Race is what you ARE.

### From Class

Add Class Levels. Each level provides:

- Skills and/or Spells
- Possibly unlocks higher-tier abilities

Class is what you've TRAINED to be.

An Entity can have:

- No classes (wild creature, untrained peasant)
- One class (focused specialist)
- Multiple classes (multiclass character)

### From Equipment

Add Equipment. Equipment provides:

- Stat bonuses (affects Apparent Stats)
- Weapons (hit bonus, damage bonus)
- Armor (Deflection %, Ablative pools)
- Miscellaneous effects

Equipment is what you HAVE.

## Entity Comparison

Use Power Tier for quick comparisons.

| Tier Range | Examples |
|------------|----------|
| 1-5 | Insects, vermin, tiny creatures |
| 6-10 | Peasants, common animals, goblins |
| 11-15 | Trained soldiers, adventurers, large predators |
| 16-25 | Heroes, elite warriors, young dragons |
| 26-40 | Legendary figures, adult dragons, giants |
| 41-60 | Ancient dragons, demon lords, demigods |
| 61-80 | Avatars, arch-angels, lesser gods |
| 81-100 | Greater gods, cosmic entities |

A Tier 10 fighting a Tier 40 is outmatched. The math allows it. The outcome is predictable.

A Tier 10 with Apparent Tier 20 (great gear, buffs) fighting a Tier 40 with Apparent Tier 25 (cursed, weakened)? Now it's interesting.

## Summary

| Component | Contains |
|-----------|----------|
| Identity | Name, Type, Race, Class Levels, Size |
| Stats | STR, DEX, CON, INT, WIS, CHA, REF, MOV, LUK |
| Derived Values | HP, Knockout, Base Power Tier, Apparent Power Tier |
| Abilities | Skills, Spells, Traits |
| Equipment | Weapons, Armor, Accessories, Items |
| Status | Current HP, Conditions, XP |

Every Entity uses this structure. No exceptions. The universality is the point.

A goblin and a god use the same structure. They just have very different numbers.

## Document Status

> **Status:** Canonical

This document defines Entity structure for TDGS. All Entities in the system conform to this structure.

See Document 10 (Classes) for what classes provide and Document 11 (Races) for what races provide. See Document 13 (Character Creation) for how to build player character entities.

---
