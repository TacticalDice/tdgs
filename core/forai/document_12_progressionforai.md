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
    "1-5":    80,
    "6-10":   160,
    "11-15":  280,
    "16-20":  500,
    "21-30":  800,
    "31-40":  1200,
    "41-50":  2000,
    "51-60":  3500,
    "61-70":  6000,
    "71-80":  10000,
    "81-90":  16000,
    "91-100": 25000
}

CUMULATIVE_XP = {
    20: 4600,
    40: 23900,
    60: 76600,
    80: 230100,
    100: 625100
}

// Cost curve is continuous and exponential
// No single wall; every bracket costs more than the last
// Most characters never cross it

================================================================================
STAT INCREASE COSTS
================================================================================

STAT_INCREASE_COST = {
    "1-5":  50,
    "6-10" : 100,
    "11-20": 300,
    "21-30": 500,
    "31-40": 800,
    "41+": 1000
}

function get_stat_increase_cost(current_stat):
    if current_stat <= 5: return 50
    if current_stat <= 10: return 100
    if current_stat <= 20: return 300
    if current_stat <= 30: return 500
    if current_stat <= 40: return 800
    return 1000

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
// Next Fighter level (26): 800 XP (21-30 bracket)
// Next Mage level (6): 80 XP (1-5 bracket)

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

GROUP_XP_MODEL: Participation Gate + Group Multiplier

// Personal Difficulty still drives individual XP
// Participation gate determines eligibility
// Group multiplier adjusts for shared effort
// No cap based on other members' stats

PARTICIPATION_GATE:
  Eligible if AT LEAST ONE of:
  
  CATEGORY_1 (Combat Engagement):
    Initiated or was target of at least one resolution roll against the enemy
    // Must enter the d20 resolution system
    // Standing idle does not qualify
    // Tagging for 1 damage without a resolution roll does not qualify

  CATEGORY_2 (Support):
    Provided healing or mitigation to a character eligible under another category
    // Healers earn XP by supporting real combatants
    // Cannot chain eligibility between non-combatants
    // "Eligible under another category" prevents carry-heals-carry loops

  CATEGORY_3 (Objective):
    Spent an action that directly advanced the win condition
    // Covers objective-based and non-combat encounters

  NOT_ELIGIBLE: 0 XP for that encounter

GROUP_SIZE_MULTIPLIER = {
    1: 1.00,
    2: 0.80,
    3: 0.67,
    4: 0.57,
    5: 0.50,
    6: 0.44,
    7: 0.40,
    8: 0.36
}

GROUP_XP_FORMULA:
  XP_award = floor(Personal_XP × GroupMultiplier)
  If Personal_XP > 0 and XP_award == 0: award 1 XP (minimum-after-multiplier)

function calculate_group_xp(characters, encounter):
    eligible = [c for c in characters if meets_participation_gate(c, encounter)]
    n = len(eligible)
    multiplier = GROUP_SIZE_MULTIPLIER[min(n, 8)]
    
    for character in characters:
        if character not in eligible:
            character.xp_award = 0
            continue
        
        personal_xp = calculate_xp(character, encounter)  // From Difficulty Spectrum
        award = floor(personal_xp * multiplier)
        
        if personal_xp > 0 and award == 0:
            award = 1  // minimum-after-multiplier
        
        character.xp_award = award

function meets_participation_gate(character, encounter):
    // Category 1: Resolution engagement
    if character in encounter.resolution_participants:
        return true
    
    // Category 2: Support (must support someone eligible under another category)
    if character.healed_or_mitigated_for(encounter.resolution_participants):
        return true
    if character.healed_or_mitigated_for(encounter.objective_participants):
        return true
    
    // Category 3: Objective
    if character in encounter.objective_participants:
        return true
    
    return false

// ANTI-POWERLEVELING:
// Carry cannot qualify Category 1: can't survive resolution vs enemies 30+ stats above
// Carry cannot qualify Category 2: must support someone already eligible
// Carry cannot qualify Category 3: only applies to objective encounters
// Result: carry gets 0 XP. Other players keep their Personal XP.

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

LEVEL_80_COST = 10000    // High-tier bracket
LEVEL_91_COST = 25000    // Maximum bracket
// Cost curve is exponential; no single wall

GROUP_MULTIPLIER_MIN = 0.36  // 8 players
GROUP_MULTIPLIER_MAX = 1.00  // Solo
MINIMUM_AFTER_MULTIPLIER = 1  // If Personal_XP > 0 and award rounds to 0

================================================================================
DESIGN NOTES
================================================================================

DESIGN_PRINCIPLES:
  - Difficulty is the resolution formula rearranged
  - Personal Difficulty means same enemy = different XP for different characters
  - Failure XP requires survival ("the dead learn nothing")
  - No group penalty on Personal Difficulty; participation gate + group multiplier handle groups
  - Participation gate requires resolution engagement, support of eligible combatant, or objective action
  - Stats-only builds are allowed but naturally punished (no abilities)
  - Exponential cost curve filters high-level characters naturally
  - GMs can override XP spending timing
  - Skills outside class go through narrative, not XP

================================================================================
END OF DOCUMENT 12
================================================================================
