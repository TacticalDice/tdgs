# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 10
# Title: Classes
# Version: 1.0
# Purpose: AI-readable specification for character classes
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
CLASS DEFINITION
================================================================================

CLASS_DEFINITION:
  - A Class represents training, profession, and learned capability
  - Race is what you ARE
  - Class is what you've BECOME

CLASSES_PROVIDE: [
  "Abilities (Skills, Spells, Traits)",
  "Tier Unlocks (access to higher-tier abilities)",
  "Stat Bonuses (based on class activities)"
]

================================================================================
CLASS STRUCTURE
================================================================================

class: {
    name: string,
    purpose: string,           // What this class is FOR
    primary_stats: [string],   // 1-2 stats (e.g., ["STR", "CON"])
    recommended_minimums: {stat: minimum_value},  // SOFT, not enforced
    progression: [
        {
            level: integer,
            abilities: [ability_grant],
            tier_unlock: integer | null,
            stat_bonuses: [{stat: string, value: integer}]
        }
    ]
}

ability_grant: {
    type: "skill" | "spell" | "trait",
    name: string,
    modifier: integer | null   // For skills only (+1, +2, etc.)
}

================================================================================
SOFT MINIMUMS
================================================================================

SOFT_MINIMUMS:
  enforced: false
  purpose: "Guidance, not gates"
  philosophy: "System allows bad decisions. Math handles consequences."

TEMPLATE_MINIMUMS:
  fighter: {STR: 10, CON: 10}
  thief: {DEX: 10, REF: 10}
  mage: {INT: 10, WIS: 8}
  cleric: {WIS: 10, CHA: 8}
  ranger: {DEX: 10, WIS: 8}
  peasant: {}  // No minimums - anyone can be a peasant

// A character CAN take any class regardless of stats
// They will struggle if they don't meet recommendations
// The choice is valid. The consequences are real.

================================================================================
ABILITY PROGRESSION RULES
================================================================================

// SKILLS (+1 SYSTEM)
function grant_skill(character, skill_name, modifier, is_level_1_grant):
    if skill_name not in character.skills:
        // Don't have it: learn at level 1
        character.skills[skill_name] = 1
    else:
        // Already have it: check Level 1 Exception
        if is_level_1_grant:
            // IRON EXCEPTION: Level 1 grants never add to existing skills
            return  // No effect
        else:
            // Add modifier to existing skill level
            character.skills[skill_name] += modifier

LEVEL_1_EXCEPTION: true
// Prevents multiclass dipping abuse
// Taking Level 1 of multiple classes cannot stack skill bonuses

// SPELLS (BINARY)
function grant_spell(character, spell_name):
    if spell_name not in character.spells:
        character.spells.add(spell_name)
    // Already known: no effect
    // No +1 system for spells

// TRAITS (BINARY)
function grant_trait(character, trait_name):
    if trait_name not in character.traits:
        character.traits.add(trait_name)
    // Already have: no effect
    // No +1 system for traits

================================================================================
TIER UNLOCK GUIDELINES
================================================================================

TIER_UNLOCK_GUIDELINES:
  Tier 1: Level 1 (always available)
  Tier 2: Level 10-20 (typical)
  Tier 3: Level 25-40 (typical)
  Tier 4: Level 50-70 (typical)
  Tier 5: Level 80+ (typical)

// Classes can deviate based on purpose
// Combat classes might unlock faster
// Low-power classes might unlock slower or never reach high tiers

================================================================================
STAT BONUS GUIDELINES
================================================================================

STAT_BONUS_GUIDELINES:
  frequency: ~1 stat point per 10 levels
  total: ~10 stat points by level 100

// Classes can be more or less generous
// Match stat distribution to class activities

TYPICAL_STAT_TOTAL = 9-10  // by level 100
LOW_POWER_STAT_TOTAL = 7   // for classes like Peasant

================================================================================
TEMPLATE CLASSES
================================================================================

Class     | Purpose                          | Primary Stats | Stat Total
----------|----------------------------------|---------------|------------
Fighter   | Front-line martial combat        | STR, CON      | +9
Thief     | Stealth, infiltration, precision | DEX, REF      | +9
Mage      | Arcane magic, scholarly knowledge| INT, WIS      | +9
Cleric    | Divine magic and support         | WIS, CHA      | +9
Ranger    | Ranged combat, tracking, nature  | DEX, WIS      | +9
Peasant   | Survival and mundane labor       | CON, WIS      | +7

// FIGHTER EXAMPLE
{
    "name": "Fighter",
    "purpose": "Front-line martial combat",
    "primary_stats": ["STR", "CON"],
    "tier_unlocks": {2: 10, 3: 40, 4: 60, 5: 80},
    "total_stat_bonuses": {"STR": 5, "CON": 4},
    "core_skills": ["Power Strike", "Weapon Mastery"],
    "design": "Steady progression, survivability traits"
}

// PEASANT EXAMPLE (LOW-POWER)
{
    "name": "Peasant",
    "purpose": "Survival and mundane labor",
    "primary_stats": ["CON", "WIS"],
    "tier_unlocks": {2: 20, 3: 80},
    "max_tier": 3,
    "total_stat_bonuses": {"CON": 4, "WIS": 3},
    "core_skills": ["Labor"],
    "design": "Fewer abilities, slower tier unlocks, fewer stat bonuses"
}

================================================================================
MULTICLASSING
================================================================================

MULTICLASSING_RULES:
  restriction: None (any class, any combination)
  xp_pool: Single (player chooses how to split)
  level_costs: Per-class (based on level in THAT class)
  level_1_exception: Applies (prevents skill stacking abuse)

// Example:
// Character has Fighter 20, takes Thief 1
// Thief 1 grants "Sneak +1" → Learns Sneak at Level 1
// If character already knew Sneak, no bonus (Level 1 Exception)

================================================================================
CLASS DESIGN QUESTIONS
================================================================================

CLASS_DESIGN_CHECKLIST: [
    "1. PURPOSE: What is this class FOR? (Be specific)",
    "2. STATS: What 1-2 stats matter most?",
    "3. CORE_ABILITIES: What 2-3 abilities define the class?",
    "4. POWER_SCALE: How fast should power increase?",
    "5. DIFFERENTIATION: What makes this class unique?"
]

================================================================================
KEY CONSTANTS
================================================================================

TYPICAL_STAT_TOTAL = 9-10        // by level 100
LOW_POWER_STAT_TOTAL = 7         // for classes like Peasant
STAT_FREQUENCY = 0.1             // ~1 per 10 levels
HEROIC_MAX_TIER = 5
LOW_POWER_MAX_TIER = 3           // varies by class
SKILL_MODIFIER_SYSTEM = "+1"     // skills use +1 modifiers
SPELL_SYSTEM = "binary"          // learn or don't
TRAIT_SYSTEM = "binary"          // have or don't
LEVEL_1_EXCEPTION = true         // prevents multiclass abuse

================================================================================
DESIGN NOTES
================================================================================

DESIGN_PRINCIPLES: {
    "packages_not_point_buy": true,    // Classes are designed packages
    "level_1_fixed": true,             // Level 1 grants are fixed (no choice)
    "plus_1_skills_only": true,        // +1 system ONLY applies to Skills
    "level_1_exception": true,         // Prevents multiclass dipping abuse
    "tier_timing_per_class": true,     // Not universal
    "templates_are_examples": true,    // Not canonical content
    "low_power_valid": true            // Peasant demonstrates non-heroic class
}

================================================================================
END OF DOCUMENT 10
================================================================================
