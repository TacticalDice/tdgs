# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 13
# Title: Character Creation
# Version: 1.0
# Purpose: AI-readable specification for character creation
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
SEVEN STEPS
================================================================================

CHARACTER_CREATION_STEPS = [
    "1. Choose Race",
    "2. Generate Stats",
    "3. Roll Luck",
    "4. Choose Class(es)",
    "5. Apply Class Bonuses",
    "6. Calculate Derived Values",
    "7. Finishing Touches"
]

================================================================================
STEP 1: CHOOSE RACE
================================================================================

RACE_DETERMINES = [
    "stat_ranges",      // Min and max starting values per stat
    "size",             // How big you are
    "innate_traits"     // Natural abilities, weapons, armor
]

// See Document 11 (Races) for race structure and templates
// Race sets boundaries; everything else works within them

================================================================================
STEP 2: GENERATE STATS (ROLLING)
================================================================================

ROLLING_METHOD:
  dice: "4d6 drop lowest"
  baseline: 12  // 4d6 drop lowest averages 12.25, not 10
  
function roll_stat(racial_min, racial_max):
    roll = sum(sorted(roll_d6() for _ in range(4))[1:])  // 4d6 drop lowest
    delta = roll - 12
    racial_avg = (racial_min + racial_max) / 2
    final = racial_avg + delta
    return clamp(final, racial_min, racial_max)

// Example: Human STR (range 6-14, avg 10)
// Roll 15 -> Delta +3 -> 10 + 3 = 13 ✓
// Roll 8  -> Delta -4 -> 10 - 4 = 6  ✓
// Roll 5  -> Delta -7 -> 10 - 7 = 3  -> capped to 6

HEROIC_POOL_ROLLING:
  dice: "2d6 drop lowest"
  optional: true
  can_exceed_racial_range: true
  distribution: "any stats"

================================================================================
STEP 2: GENERATE STATS (POINT BUY)
================================================================================

POINT_BUY_METHOD:
  base_pool: "Sum of all racial stat averages (8 stats)"
  heroic_pool: "2d6 drop lowest (optional, GM discretion)"
  total: base_pool + heroic_pool
  
POINT_BUY_RULES:
  base_pool:
    stays_in_racial_range: true
  heroic_pool:
    can_exceed_racial_range: true
  cost: "1:1"

// Example: Human
// Base Pool = 10 × 8 = 80 points
// Heroic Pool = 2d6 drop lowest = 1-6 points
// Heroic points can push stats above racial max (14)

// Example: Dragon
// Base Pool = 40+20+45+20+20+30+20+27 = 222 points

================================================================================
STEP 3: ROLL LUCK
================================================================================

LUCK_GENERATION:
  dice: "d20"
  outcomes:
    1:     -1   // 5% chance
    2-19:   0   // 90% chance
    20:    +1   // 5% chance
  
// Exception: If race grants LUK range (e.g., Leprechaun +2 to +6),
// use delta method for that range instead of d20

function roll_luck(has_racial_luk_range=false, racial_luk_range=null):
    if has_racial_luk_range:
        return roll_stat_with_delta(racial_luk_range)
    
    roll = roll_d20()
    if roll == 1: return -1
    if roll == 20: return 1
    return 0

================================================================================
STEP 4: CHOOSE CLASS
================================================================================

CLASS_PROVIDES = [
    "abilities",      // Skills, Spells, Traits
    "tier_unlocks",   // Access to higher-tier abilities
    "stat_bonuses"    // Bonuses from training (Step 5)
]

CLASS_REQUIREMENTS:
  type: "soft"  // Guidance, not gates
  // A STR 6 character CAN take Fighter; they'll struggle
  // TDGS allows bad decisions; math handles consequences

STARTING_LEVEL:
  default: 1
  override: "GM discretion for experienced campaigns"
  
MULTICLASSING:
  allowed: true
  requires: "GM permission and XP"
  typical: "Single class at Level 1"
  
// See Document 10 (Classes) for class structure and templates

================================================================================
STEP 5: APPLY CLASS BONUSES
================================================================================

CLASS_BONUSES:
  timing: "After stat generation, before derived values"
  can_exceed_racial_range: true  // Training exceeds natural limits
  
// Example:
// Base STR (from rolling): 12
// Fighter 1 grants: +1 STR
// Apparent STR: 13

================================================================================
STEP 6: DERIVED VALUES
================================================================================

DERIVED_VALUES:
  HP = apparent_CON × 5
  Knockout = HP × 0.05  // Round down; unconscious when HP <= Knockout
  
POWER_TIER:
  base = (STR + DEX + CON + INT + WIS + CHA + REF + MOV) / 8
  apparent = (apparent_stats) / 8
  rounding: "down"
  luck_included: false
  
// At creation, Base and Apparent Power Tier are often same
// They diverge as equipment is acquired

// Example: Human Fighter
// Stats: STR 13, DEX 10, CON 12, INT 10, WIS 10, CHA 10, REF 10, MOV 10
// HP = 12 × 5 = 60
// Knockout = 60 × 0.05 = 3
// Base Power Tier = 85 / 8 = 10

================================================================================
STEP 7: FINISHING TOUCHES
================================================================================

FINISHING_TOUCHES = [
    "equipment",     // Setting-dependent
    "name",
    "background",
    "personality",
    "goals",
    "appearance"
]

EQUIPMENT:
  source: "Content-dependent (setting)"
  examples:
    medieval_fantasy: ["swords", "shields"]
    scifi: ["pistols", "neural jacks"]
    post_apocalypse: ["scrap", "scavenged gear"]
  determined_by: "GM/setting"

================================================================================
QUICK REFERENCE
================================================================================

// ROLLING STATS
for each of 8 stats:
    roll = 4d6_drop_lowest()
    delta = roll - 12
    stat = racial_avg + delta
    stat = clamp(stat, racial_min, racial_max)
heroic_pool = 2d6_drop_lowest()  // Optional
// Distribute heroic points; can exceed racial range

// POINT BUY
base_pool = sum(racial_averages)
heroic_pool = 2d6_drop_lowest()  // Optional
// Spend 1:1; base in range, heroic can exceed

// LUCK
roll_d20: 1=-1, 2-19=0, 20=+1
// Unless race grants LUK range

// DERIVED VALUES
HP = apparent_CON × 5
Knockout = HP × 0.05
Power_Tier = sum(8_stats) / 8  // No LUK

================================================================================
EXAMPLE: HUMAN FIGHTER
================================================================================

// Step 1: Race
race = "Human"
stat_ranges = {
    STR: [6, 14], DEX: [6, 14], CON: [6, 14], INT: [6, 14],
    WIS: [6, 14], CHA: [6, 14], REF: [6, 14], MOV: [8, 12]
}

// Step 2: Generate Stats (Rolling)
rolls = {STR: 14, DEX: 11, CON: 15, INT: 9, WIS: 12, CHA: 10, REF: 13, MOV: 8}
deltas = {STR: +2, DEX: -1, CON: +3, INT: -3, WIS: 0, CHA: -2, REF: +1, MOV: -4}
stats = {STR: 12, DEX: 9, CON: 13, INT: 7, WIS: 10, CHA: 8, REF: 11, MOV: 8}
// MOV capped from 6 to 8

heroic_pool = 5  // Rolled 2d6 drop lowest: (2, 5) -> keep 5
stats.STR += 3  // Now 15
stats.CON += 2  // Now 15

// Step 3: Roll Luck
luck_roll = 7  // d20 result
LUK = 0  // 2-19 = 0

// Step 4: Choose Class
class = "Fighter"
// Recommended STR 10+, have STR 12 ✓
// Gain: Power Strike +1, Shield Use +1, Armor Training (Trait)

// Step 5: Apply Class Bonuses
// Fighter 1 grants no stat bonuses in this example
final_stats = {STR: 15, DEX: 9, CON: 15, INT: 7, WIS: 10, CHA: 8, REF: 11, MOV: 8, LUK: 0}

// Step 6: Derived Values
HP = 15 × 5 = 75
Knockout = 75 × 0.05 = 3
Base_Power_Tier = (15+9+15+7+10+8+11+8) / 8 = 83 / 8 = 10

// Step 7: Finishing Touches
name = "Garrett Cole"
background = "Former town guard"
personality = "Cautious, protective"
goals = "Earn enough gold to buy a farm"

================================================================================
KEY CONSTANTS
================================================================================

STAT_GENERATION:
  ROLL_DICE = "4d6 drop lowest"
  ROLL_BASELINE = 12
  HEROIC_DICE = "2d6 drop lowest"
  
LUCK_GENERATION:
  DICE = "d20"
  UNLUCKY_ROLL = 1
  LUCKY_ROLL = 20
  
DERIVED_VALUES:
  HP_MULTIPLIER = 5
  KNOCKOUT_MULTIPLIER = 0.05
  POWER_TIER_DIVISOR = 8
  POWER_TIER_STAT_COUNT = 8  // Excludes LUK

================================================================================
DESIGN NOTES
================================================================================

DESIGN_PRINCIPLES:
  - Baseline 12 (not 10) because 4d6 drop lowest averages 12.25
  - Heroic Pool represents the spark that makes heroes exceptional
  - Class requirements are soft; TDGS allows bad decisions
  - Race sets boundaries; class bonuses can exceed them
  - LUK is special: rolled separately, never bought
  - Same system works for Goblins and Gods (delta method scales)
  - Equipment is content-dependent, not system-defined
  - Stats are capability; choices are character

================================================================================
END OF DOCUMENT 13
================================================================================
