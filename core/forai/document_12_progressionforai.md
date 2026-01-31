# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 12
# Title: Progression
# Version: 1.0
# Purpose: AI-readable specification for XP and advancement
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
CORE CONCEPT
================================================================================

XP_CONCEPT:
  - XP is earned by overcoming challenges
  - The harder the challenge relative to YOUR capabilities, the more you learn
  - Same enemy = different XP for different characters (Personal Difficulty)

================================================================================
DIFFICULTY FORMULA
================================================================================

DIFFICULTY = 11 - (Your_Stat - Their_Stat) - Modifiers

// This is the Resolution formula rearranged:
//   Resolution: d20 + Delta + Mods >= 11  (Did I succeed?)
//   Difficulty: 11 - Delta - Mods         (What do I need to roll?)
// Same math, different question.

================================================================================
DIFFICULTY SPECTRUM
================================================================================

DIFFICULTY_SPECTRUM = {
    "trivial":     {"range": "<=2",   "success_xp": 1,   "failure_xp": 0},
    "simple":      {"range": "3-4",   "success_xp": 3,   "failure_xp": 0},
    "easy":        {"range": "5-6",   "success_xp": 6,   "failure_xp": 0},
    "routine":     {"range": "7-8",   "success_xp": 10,  "failure_xp": 0},
    "moderate":    {"range": "9-10",  "success_xp": 15,  "failure_xp": 0},
    "challenging": {"range": "11-12", "success_xp": 25,  "failure_xp": 0},
    "difficult":   {"range": "13-14", "success_xp": 40,  "failure_xp": 20},
    "hard":        {"range": "15-16", "success_xp": 60,  "failure_xp": 30},
    "heroic":      {"range": "17-18", "success_xp": 85,  "failure_xp": 42},
    "legendary":   {"range": "19-20", "success_xp": 120, "failure_xp": 60},
    "mythic":      {"range": "21+",   "success_xp": 175, "failure_xp": 87}
}

// Difficulty <= 0: No XP (too easy)
// Failure XP: Only Tier 7+ (Difficult and above)
// Failure XP: Half of success, requires survival

================================================================================
XP CALCULATION FUNCTION
================================================================================

function calculate_xp(your_stat, their_stat, modifiers, succeeded, survived):
    delta = your_stat - their_stat
    difficulty = 11 - delta - modifiers
    
    if difficulty <= 0:
        return 0  // Too easy, no growth
    
    tier = get_tier_from_difficulty(difficulty)
    
    if succeeded:
        return tier.success_xp
    elif tier.failure_xp > 0 and survived:
        return tier.failure_xp
    else:
        return 0

================================================================================
XP TIMING
================================================================================

XP_TIMING:
  when: "End of encounter"
  per: "Challenge overcome"
  
// "Overcome" = defeated, bypassed, resolved, solved, concluded
// Three goblins = three XP awards
// One negotiation = one XP award

================================================================================
LEVELING COST BRACKETS
================================================================================

LEVELING_BRACKETS = {
    "novice":     {"levels": "1-20",   "xp_per_level": 50},
    "journeyman": {"levels": "21-40",  "xp_per_level": 100},
    "veteran":    {"levels": "41-60",  "xp_per_level": 200},
    "master":     {"levels": "61-80",  "xp_per_level": 400},
    "legend":     {"levels": "81-100", "xp_per_level": 1500}
}

CUMULATIVE_XP = {
    20: 1000,
    40: 3000,
    60: 7000,
    80: 15000,
    100: 45000
}

// Legend Wall: 400 -> 1500 jump is intentional
// Most characters never cross it

================================================================================
STAT INCREASE COSTS
================================================================================

STAT_INCREASE_COST = {
    "1-10":  50,
    "11-20": 100,
    "21-30": 200,
    "31-40": 400,
    "41+":   800
}

function get_stat_increase_cost(current_stat):
    if current_stat <= 10: return 50
    if current_stat <= 20: return 100
    if current_stat <= 30: return 200
    if current_stat <= 40: return 400
    return 800

// Cost based on CURRENT stat before increase
// No hard cap; cost IS the soft cap

================================================================================
WHAT XP BUYS
================================================================================

XP_PURCHASES = ["class_levels", "stat_increases"]

// XP does NOT buy:
//   - Individual skills
//   - Individual spells
//   - Individual traits
//   - Items
//   - Narrative outcomes

// Skills from outside class: narrative only (items, training, GM)

================================================================================
MULTICLASSING
================================================================================

MULTICLASSING:
  restrictions: None
  xp_pool: Single (player chooses split)
  level_costs: Per-class (based on level in THAT class)
  level_1_exception: true

// Example:
// Fighter 25 / Mage 5
// Next Fighter level (26): 100 XP (Journeyman)
// Next Mage level (6): 50 XP (Novice)

// Level 1 Exception:
// Taking Level 1 of new class never adds to existing skills
// Prevents multiclass dipping abuse

================================================================================
XP SPENDING TIMING
================================================================================

XP_SPENDING:
  default: "Between scenes"
  override: "GM discretion"
  
// No mid-combat level ups by default
// GMs can change ANY ruling for their table

================================================================================
SKILLS OUTSIDE CLASS
================================================================================

SKILLS_OUTSIDE_CLASS:
  xp_purchase: false
  sources: ["items", "narrative", "gm_discretion", "transformation"]
  
// Want Power Strike without Fighter?
// Find mentor, find item, convince GM
// Cannot buy directly with XP

================================================================================
GROUP XP RULES
================================================================================

GROUP_PENALTY: None

// Personal Difficulty already differentiates
// Positional advantages already reduce Difficulty
// Large groups have real-world costs
// Solo players not punished
// Each player calculates own XP

================================================================================
LUCK AND XP
================================================================================

LUCK_IN_XP: false

// LUK does not factor into Difficulty calculation
// Difficulty uses effort/capability stats only
// Lucky roll against dragon = still fought a dragon

================================================================================
KEY CONSTANTS
================================================================================

BASE_DIFFICULTY = 11
FAILURE_XP_THRESHOLD = 7  // Tier "Difficult" and above
FAILURE_XP_MULTIPLIER = 0.5
NO_XP_THRESHOLD = 0  // Difficulty <= 0 = no XP

LEGEND_WALL_BEFORE = 400   // Master bracket
LEGEND_WALL_AFTER = 1500   // Legend bracket

================================================================================
DESIGN NOTES
================================================================================

DESIGN_PRINCIPLES:
  - Difficulty is the resolution formula rearranged
  - Personal Difficulty means same enemy = different XP for different characters
  - Failure XP requires survival ("the dead learn nothing")
  - No group penalty; Difficulty Spectrum handles everything
  - Stats-only builds are allowed but naturally punished (no abilities)
  - Legend Wall filters legendary characters intentionally
  - GMs can override XP spending timing
  - Skills outside class go through narrative, not XP

================================================================================
END OF DOCUMENT 12
================================================================================
