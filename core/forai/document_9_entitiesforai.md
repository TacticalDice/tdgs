# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 9
# Title: Entities
# Version: 1.0
# Purpose: AI-readable specification for entity structure
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
ENTITY DEFINITION
================================================================================

ENTITY_TEST: Can it take a turn? If yes, it's an Entity.

INCLUDES: [
  "Player characters",
  "NPCs",
  "Creatures",
  "Constructs",
  "Spirits",
  "Divine beings"
]

EXCLUDES: [
  "Objects",
  "Environmental effects",
  "Abstract concepts"
]

================================================================================
ENTITY STRUCTURE
================================================================================

entity: {
    identity: {
        name: string,
        type: string,           // "Player" | "NPC" | "Creature" | etc.
        race: string,           // Provides innate Traits
        class_levels: [         // Provides Skills/Spells
            {class: string, level: integer}
        ],
        size: string            // Tiny|Small|Medium|Large|Huge|Gargantuan
    },
    
    stats: {
        str: integer,
        dex: integer,
        con: integer,
        int: integer,
        wis: integer,
        cha: integer,
        ref: integer,
        mov: integer,
        luk: integer            // Range: -10 to +10
    },
    
    derived: {
        hp: integer,                    // apparent_con × 5
        knockout_threshold: integer,    // hp × 0.05, rounded down
        base_power_tier: integer,       // sum of 8 base stats / 8 (no LUK)
        apparent_power_tier: integer    // sum of 8 apparent stats / 8 (no LUK)
    },
    
    abilities: {
        skills: [skill],        // From Class, Training (levels 1-8, tiers)
        spells: [spell],        // From Class, Training (no levels, tiers)
        traits: [trait]         // From Race, Transformation (no levels, no tiers)
    },
    
    equipment: {
        weapons: [weapon],
        armor: [armor],
        accessories: [accessory],   // Rings, cloaks, boots, etc. (non-armor)
        items: [item]               // Consumables, tools, carried objects
    },
    
    status: {
        current_hp: integer,
        conditions: [condition],
        xp: integer | null      // May not apply to all entities
    }
}

================================================================================
SIZE CATEGORIES
================================================================================

Category    | Space    | Reach        | Examples
------------|----------|--------------|---------------------------
Tiny        | <1 sq    | 0            | Rat, pixie, insect
Small       | 1 sq     | 1 sq         | Goblin, halfling, dog
Medium      | 1 sq     | 1 sq         | Human, elf, orc
Large       | 2×2 sq   | 2 sq         | Horse, ogre, dire wolf
Huge        | 3×3 sq   | 3 sq         | Giant, elephant, young dragon
Gargantuan  | 4×4+ sq  | 4+ sq        | Ancient dragon, kraken, titan

SIZE AFFECTS:

1. SPACE OCCUPIED:
   Squares controlled on grid

2. NATURAL REACH:
   Distance creature can strike without moving
   Measured from any edge of creature's space

3. GRAPPLING MODIFIERS:
   Same size:           +0
   1 category smaller:  +2 to larger creature
   2 categories smaller: +4 to larger creature
   3+ categories smaller: Auto-success for larger

4. FORCED MOVEMENT RESISTANCE:
   Same size:            Normal
   Target 1 cat larger:  Distance halved
   Target 2+ cat larger: No forced movement

5. CARRYING CAPACITY:
   Base: STR × 10 WU (Weight Units)
   Multiplier by size:
     Tiny:       ×0.25
     Small:      ×0.5
     Medium:     ×1
     Large:      ×2
     Huge:       ×4
     Gargantuan: ×8+

6. SQUEEZING:
   Can squeeze through space 1 category smaller
   While squeezing:
     - Movement costs double
     - Attacks at -2
     - Attackers gain +2

================================================================================
DERIVED VALUE CALCULATIONS
================================================================================

function calculate_derived_values(entity):
    // HP
    apparent_con = entity.stats.con + sum(entity.con_bonuses)
    hp = apparent_con × 5
    knockout_threshold = floor(hp × 0.05)
    
    // Power Tier (excludes LUK)
    base_stats = [str, dex, con, int, wis, cha, ref, mov]  // base values
    base_power_tier = floor(sum(base_stats) / 8)
    
    apparent_stats = [apparent_str, apparent_dex, ...]      // with bonuses
    apparent_power_tier = floor(sum(apparent_stats) / 8)
    
    return {hp, knockout_threshold, base_power_tier, apparent_power_tier}

================================================================================
TYPE
================================================================================

TYPE_MECHANICAL_EFFECT: none  // Label only

VALID_TYPES: ["Player", "NPC", "Creature", "Construct", "Spirit", "Divine", ...]

TYPE_MEANINGS: {
    "Player": "Player-controlled character",
    "NPC": "GM-controlled character",
    "Creature": "Monster, animal, etc."
}

// Mechanical meaning comes from Race and Class, not Type

================================================================================
RACE
================================================================================

race: {
    name: string,
    traits: [trait],            // Innate abilities
    base_stat_ranges: {},       // Suggested stat ranges for this race
    size: string,               // Default size
    natural_weapons: [trait],   // Claws, Bite, etc. (if any)
    natural_armor: [trait]      // Scales, Shell, etc. (if any)
}

// Race provides what you ARE

================================================================================
CLASS LEVELS
================================================================================

class_level: {
    class: string,
    level: integer              // 1-100
}

MULTICLASS: allowed
// Example: [{class: "Warrior", level: 5}, {class: "Mage", level: 2}]
// XP is single pool, player chooses how to split

// Class provides what you've TRAINED to be

================================================================================
NATURAL WEAPONS AND ARMOR
================================================================================

NATURAL_WEAPONS: {
    type: "Trait",
    action_required: true,      // Using is an action
    stacks_with_held: false,    // Cannot use + held weapon in same action
    example: "Claws (+8 damage)"
}

NATURAL_ARMOR: {
    type: "Trait",
    stacks_with_worn: true,     // STACKS with worn armor
    deflection_cap: 0.75,       // Respects 75% deflection cap
    example: "Dragon Scales (40% Deflection)"
}

// Dragon (40%) + Chain Mail (30%) = 70% deflection
// Turtle (50%) + Plate (50%) = 75% deflection (capped)

================================================================================
POWER TIER
================================================================================

BASE_POWER_TIER = floor((base_STR + base_DEX + base_CON + base_INT + 
                         base_WIS + base_CHA + base_REF + base_MOV) / 8)

APPARENT_POWER_TIER = floor((apparent_STR + apparent_DEX + apparent_CON + 
                            apparent_INT + apparent_WIS + apparent_CHA + 
                            apparent_REF + apparent_MOV) / 8)

LUK_EXCLUDED: true  // Different scale, affects probability not capability

Tier Range | Examples
-----------|------------------------------------------
1-5        | Insects, vermin, tiny creatures
6-10       | Peasants, common animals, goblins
11-15      | Trained soldiers, adventurers, large predators
16-25      | Heroes, elite warriors, young dragons
26-40      | Legendary figures, adult dragons, giants
41-60      | Ancient dragons, demon lords, demigods
61-80      | Avatars, arch-angels, lesser gods
81-100     | Greater gods, cosmic entities

================================================================================
EQUIPMENT CATEGORIES
================================================================================

WEAPONS: {
    description: "Items used to attack",
    properties: ["hit_bonus", "damage_bonus"]
}
  
ARMOR: {
    description: "Items that protect",
    properties: ["deflection_percent", "ablative_pool", "evasion_bonus"]
}

ACCESSORIES: {
    description: "Worn items that aren't armor",
    examples: ["rings", "necklaces", "cloaks", "boots", "belts"],
    properties: ["stat_bonuses", "special_effects"]
}

ITEMS: {
    description: "Carried objects",
    examples: ["consumables", "tools", "keys", "misc"],
    properties: "varies by item"
}

================================================================================
STATUS
================================================================================

status: {
    current_hp: integer,        // 0 = dead, <= knockout_threshold = unconscious
    conditions: [               // Active buffs and debuffs
        {name: string, duration: string | integer, source: string}
    ],
    xp: integer | null          // For entities that track advancement
}

================================================================================
ENTITY BUILDING ORDER
================================================================================

BUILD_ORDER: [
    {
        step: 1,
        source: "RACE",
        description: "What you ARE",
        provides: [
            "base stat ranges",
            "innate Traits",
            "Size",
            "natural weapons/armor (if any)"
        ]
    },
    {
        step: 2,
        source: "CLASS",
        description: "What you've TRAINED",
        provides: [
            "Skills",
            "Spells",
            "Multiple classes allowed (multiclassing)"
        ]
    },
    {
        step: 3,
        source: "EQUIPMENT",
        description: "What you HAVE",
        provides: [
            "Affects Apparent Stats",
            "weapons, armor, accessories",
            "Affects Apparent Power Tier"
        ]
    }
]

================================================================================
EXAMPLE ENTITY: GOBLIN
================================================================================

{
    "identity": {
        "name": "Goblin",
        "type": "Creature",
        "race": "Goblin",
        "class_levels": [],
        "size": "Small"
    },
    "stats": {
        "str": 8, "dex": 12, "con": 8,
        "int": 6, "wis": 8, "cha": 6,
        "ref": 11, "mov": 10, "luk": 0
    },
    "derived": {
        "hp": 40,
        "knockout_threshold": 2,
        "base_power_tier": 8,
        "apparent_power_tier": 8
    },
    "abilities": {
        "skills": [],
        "spells": [],
        "traits": ["Darkvision", "Cowardly"]
    },
    "equipment": {
        "weapons": [{"name": "Rusty Dagger", "hit_bonus": 0, "damage_bonus": 1}],
        "armor": [{"name": "Leather Scraps", "deflection": 0.10}],
        "accessories": [],
        "items": [{"name": "Copper Coins", "quantity": 3}]
    },
    "status": {
        "current_hp": 40,
        "conditions": [],
        "xp": null
    }
}

================================================================================
KEY CONSTANTS
================================================================================

HP_MULTIPLIER = 5
KNOCKOUT_PERCENT = 0.05
POWER_TIER_STATS = 8          // Excludes LUK
DEFLECTION_CAP = 0.75
NATURAL_ARMOR_STACKS = true
LUK_RANGE = [-10, +10]

================================================================================
DESIGN NOTES
================================================================================

UNIVERSAL_STRUCTURE: true     // All entities use identical structure
TYPE_MECHANICAL_EFFECT: none  // Label only
RACE_PROVIDES: ["Traits"]
CLASS_PROVIDES: ["Skills", "Spells"]
NATURAL_WEAPONS: "Traits"     // Action to use, doesn't stack with held
NATURAL_ARMOR_STACKS: true    // Respects 75% cap
POWER_TIER_LUK: excluded      // Different scale
BASE_VS_APPARENT: "Inherent vs current capability"
SIZE_CATEGORIES: ["Tiny", "Small", "Medium", "Large", "Huge", "Gargantuan"]

================================================================================
CROSS-REFERENCES
================================================================================

REFERENCES: [
    "Document 2: Core Attributes (the 9 stats)",
    "Document 7: Abilities (Skills, Spells, Traits)",
    "Document 8: Combat (HP, Conditions)"
]

REFERENCED_BY: [
    "Document 10: Classes (what classes provide)",
    "Document 11: Races (what races provide)",
    "Document 13: Character Creation (building entities)"
]

================================================================================
END OF DOCUMENT 9
================================================================================
