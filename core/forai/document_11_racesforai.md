# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 11
# Title: Races
# Version: 1.0
# Purpose: AI-readable specification for races
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
RACE DEFINITION
================================================================================

RACE_DEFINITION:
  - A Race represents inherent nature, biology, and inborn capability
  - Class is what you've BECOME
  - Race is what you ARE

RACES_PROVIDE: [
  "Innate Traits (including natural weapons and armor)",
  "Base Stat Ranges (starting limits)",
  "Size",
  "Slots (equipment locations)"
]

================================================================================
RACE STRUCTURE
================================================================================

race: {
    name: string,
    size: string,
    description: string,
    
    base_stat_ranges: {
        str: {min: integer, max: integer},
        dex: {min: integer, max: integer},
        con: {min: integer, max: integer},
        int: {min: integer, max: integer},
        wis: {min: integer, max: integer},
        cha: {min: integer, max: integer},
        ref: {min: integer, max: integer},
        mov: {min: integer, max: integer},
        luk: {min: integer, max: integer}
    },
    
    slots: {
        [location: string]: integer  // e.g., "head": 1, "finger": 10
    },
    
    natural_weapons: [
        {name: string, damage: string}  // "+5" or "+1d6" or "+2 + 1d4"
    ],
    
    natural_armor: [
        {name: string, deflection: float}  // 0.0 to 0.75
    ],
    
    traits: [string]
}

================================================================================
STAT RANGE RULES
================================================================================

STAT_RANGES: Starting Limits Only

Characters START within racial stat ranges.
Training, items, and class bonuses can exceed later.

Example:
  Human STR range: 6-14
  Human starts with STR 6-14
  Human can later exceed 14 through advancement

================================================================================
HUMAN BASELINE
================================================================================

HUMAN_BASELINE:
  average_stat: 10
  typical_range: 6-14

All other races compared to Human:
  "Stronger than Human" = higher STR range
  "Less intelligent than Human" = lower INT range

================================================================================
LUK RANGE
================================================================================

DEFAULT_LUK_RANGE: -3 to +3

Most races use default.
Exceptions noted in race definition.

Examples:
  Leprechaun: +2 to +6 (inherently lucky)
  Cursed Bloodline: -6 to -2 (inherently unlucky)

================================================================================
SLOTS
================================================================================

SLOTS:
  - Define where equipment CAN be worn/wielded
  - Races determine available slots
  - Non-humanoids may have different slot layouts

STANDARD_HUMANOID_SLOTS: {
    "head": 1,
    "face": 1,
    "ears": 2,
    "neck": 1,
    "torso": 1,
    "back": 1,
    "arm": 2,
    "hand": 2,
    "finger": 10,
    "waist": 1,
    "leg": 2,
    "foot": 2
}
// Total: 26 slots

DRAGON_SLOTS: {
    "head": 1,
    "face": 1,
    "ears": 2,
    "neck": 1,
    "torso": 1,
    "back": 1,
    "wing": 2,
    "foreleg": 2,
    "claw": 4,
    "hindleg": 2,
    "tail": 1
}
// No finger/hand slots (claws can't manipulate fine objects)

================================================================================
NATURAL WEAPONS
================================================================================

NATURAL_WEAPONS:
  - Listed as race traits
  - Using natural weapon is an action
  - Cannot combine with held weapon in same attack
  - Damage can be flat (+5) or dice (+1d6) or both (+2 + 1d4)

Example:
  dragon.natural_weapons = [
    {name: "Claws", damage: "+2d6"},
    {name: "Bite", damage: "+3d6"},
    {name: "Tail Sweep", damage: "+1d8"}
  ]

================================================================================
NATURAL ARMOR
================================================================================

NATURAL_ARMOR:
  - Listed as race traits
  - STACKS with worn armor
  - Respects 75% deflection cap

Example:
  dragon.natural_armor = [
    {name: "Dragon Scales", deflection: 0.40}
  ]
  
  // Dragon (40%) + Chain Mail (30%) = 70% deflection
  // Dragon (40%) + Plate (50%) = 75% deflection (capped)

================================================================================
TEMPLATE RACES
================================================================================

Race    | Size       | Power Level | Key Traits
--------|------------|-------------|--------------------------------
Human   | Medium     | Baseline    | Adaptable, Versatile
Elf     | Medium     | Baseline+   | Darkvision, Longevity, Arcane Affinity
Dwarf   | Medium     | Baseline+   | Darkvision, Poison Resistance, Sturdy
Orc     | Medium     | Baseline+   | Intimidating Presence, Relentless
Goblin  | Small      | Low         | Darkvision, Cowardly, Nimble Escape
Dragon  | Gargantuan | High        | Flight, Breath Weapon, Frightening Presence

================================================================================
POWER SPECTRUM
================================================================================

POWER_LEVELS:
  low:      Goblin (cannon fodder, underdog PCs)
  baseline: Human (default, versatile)
  baseline+: Elf, Dwarf, Orc (specialized but balanced)
  high:     Dragon (boss monster, special PCs)

// TDGS doesn't assume balanced parties
// System handles any combination

================================================================================
KEY CONSTANTS
================================================================================

HUMAN_AVERAGE = 10
HUMAN_TYPICAL_RANGE = {min: 6, max: 14}
DEFAULT_LUK_RANGE = {min: -3, max: 3}
DEFLECTION_CAP = 0.75
NATURAL_ARMOR_STACKS = true
STAT_RANGES_ARE_STARTING_LIMITS = true

================================================================================
END OF DOCUMENT 11
================================================================================
