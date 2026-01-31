# TACTICAL DICE GAME SYSTEM (TDGS) - EXTENSION
# Title: Crafting System
# Version: 1.0
# Purpose: AI-readable specification for crafting items from recipes
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

Extension defining rules for crafting items from recipes in TDGS.

ESTABLISHES:
  - Two-phase resolution (success, then quality)
  - Quality tiers from Volatile to Masterwork
  - Skill-based quality pools
  - Material, tool, and time modifiers
  - Batch crafting
  - Failure and critical failure consequences

BUILDS ON:
  - Document 1: Dice
  - Document 3: Resolution
  - Document 7: Abilities
  - Document 12: Progression

DOES NOT REDEFINE CORE RULES.

================================================================================
THE CORE MECHANIC
================================================================================

Crafting uses two separate rolls: Resolution and Quality.

First, roll to see if you can complete the process at all.
Then, if successful, roll to see how well you did.

  Phase       | Die      | Question
  ------------|----------|------------------------------------------
  Resolution  | d20      | Can you complete the crafting process?
  Quality     | d12 pool | What tier of item did you produce?

Resolution determines success or failure.
Quality determines the tier of the result.
These are always separate.

================================================================================
RESOLUTION ROLL (PHASE 1)
================================================================================

THE ROLL:
  d20 + (Crafter Stat - Recipe Target) + Skill Bonus + Modifiers >= 11

TERMS:
  - Crafter Stat: The relevant stat for this type of crafting
  - Recipe Target: The difficulty value specified in the recipe
  - Skill Bonus: From relevant crafting skill (per Doc 7)
  - Modifiers: From tools, workspace, circumstances

This uses standard TDGS resolution (Doc 3). The recipe target acts as the
opposing force.

RESULTS:
  Outcome           | What Happens
  ------------------|--------------------------------------------
  Success (11+)     | Proceed to Quality roll
  Failure (2-10)    | Crafting fails, partial materials lost
  Critical Fail (1) | Total failure, all materials lost, consequences

Natural 1 always fails critically.
Natural 20 succeeds and grants +2d12 to quality pool.

================================================================================
QUALITY ROLL (PHASE 2)
================================================================================

If you succeed at crafting, roll for quality tier.

QUALITY TIERS:
  Tier        | Roll | Effect
  ------------|------|----------------------------------
  Volatile    | 1    | Functions but with drawback
  Rough       | 2    | Basic function only
  Crude       | 3    | Minor penalty
  Simple      | 4    | Standard, no modifiers
  Functional  | 5    | Reliable
  Decent      | 6    | Slightly above average
  Sound       | 7    | Solid quality
  Fine        | 8    | Minor bonus
  Superior    | 9    | Notable bonus
  Exceptional | 10   | Significant bonus
  Exquisite   | 11   | Major bonus
  Masterwork  | 12   | Maximum bonus plus special property

The d12 maps directly to tiers. Roll a 7, get Sound quality.

================================================================================
SKILL AND QUALITY POOL
================================================================================

Your crafting skill determines your quality pool size.

BASE QUALITY POOL:
  Quality Pool = (Skill Level)d12, keep highest

  Skill Level | Quality Pool | Expected Tier
  ------------|--------------|----------------------
  1 (Novice)  | 1d12         | ~6.5 (Decent)
  2           | 2d12kh1      | ~8.5 (Fine)
  3           | 3d12kh1      | ~9.5 (Superior)
  4           | 4d12kh1      | ~10 (Exceptional)
  5 (Master)  | 5d12kh1      | ~10.5 (Exceptional+)

Higher skill doesn't guarantee masterwork - but it makes poor results
increasingly rare.

DESIGN NOTE:
  The keep-highest mechanic means skill improvement primarily removes
  low results rather than guaranteeing high ones. A master can still
  roll poorly - it's just unlikely.

================================================================================
QUALITY POOL MODIFIERS
================================================================================

Several factors can add or remove dice from your quality pool.

ADDING DICE:
  Source                      | Bonus      | Limit
  ----------------------------|------------|-------------
  Natural 20 on Resolution    | +2d12      | -
  Superior Materials          | +1 to +3d12| Per recipe
  Quality Tools               | +1 to +2d12| Per tool type
  Dedicated Workspace         | +1d12      | One
  Extra Time (x2)             | +1d12      | One
  Assistants                  | +1d12 each | Max +3d12

REMOVING DICE (minimum 1d12):
  Circumstance          | Penalty
  ----------------------|---------
  Inferior Materials    | -1 to -3d12
  Poor/Missing Tools    | -1 to -2d12
  Rushed (1/2 time)     | -2d12
  Hostile Environment   | -1d12

Quality pool cannot go below 1d12.
If penalties would reduce it below 1, you simply roll 1d12.

================================================================================
ASSISTANCE
================================================================================

Others can help with crafting in two ways.

SKILLED ASSISTANCE:
  An assistant with at least 1 rank in the relevant skill can contribute:
  - +1d12 to quality pool per assistant
  - Maximum +3d12 from assistants total
  - Assistant must be present for full crafting time

UNSKILLED LABOR:
  Helpers without the skill can still assist:
  - Reduces crafting time by 10-25%
  - No quality pool bonus
  - Useful for batch crafting

Too many assistants create confusion. The +3d12 cap represents this limit.

================================================================================
BATCH CRAFTING
================================================================================

Creating multiple items at once.

BATCH SIZE BY RECIPE TARGET:
  Recipe Target     | Max Batch Size
  ------------------|---------------
  11-13 (Easy)      | 10 items
  14-16 (Moderate)  | 5 items
  17-19 (Difficult) | 3 items
  20+ (Complex)     | 1 item

BATCH RULES:
  - One Resolution roll for the entire batch
  - One Quality roll applies to all items
  - Materials required for all items in batch
  - Time is 150% of single item time for full batch

If Resolution fails, all materials for the batch are affected by
failure rules.

================================================================================
FAILURE AND CONSEQUENCES
================================================================================

What happens when crafting goes wrong.

STANDARD FAILURE (Roll 2-10):
  - Crafting does not complete
  - 50% of materials are lost/consumed
  - Remaining materials can be reused
  - No item produced

CRITICAL FAILURE (Natural 1):
  - All materials are lost/destroyed
  - Possible damage to tools (GM discretion)
  - Possible collateral damage for dangerous recipes
  - No item produced

IMPORTANT: Critical failures on volatile materials (alchemical compounds,
unstable reagents) may cause explosions, toxic releases, or other hazards
at GM discretion.

================================================================================
RECIPE STRUCTURE
================================================================================

Each recipe defines what you can craft and how.

RECIPE COMPONENTS:
  Component       | Description
  ----------------|------------------------------------------
  Name            | What the recipe produces
  Skill           | Required crafting skill
  Stat            | Stat used for Resolution (usually matches skill)
  Target          | Recipe difficulty (11-25+)
  Materials       | Required components
  Tools           | Required equipment
  Time            | Base crafting duration
  Quality Effects | What quality tiers mean for this item

================================================================================
EXAMPLE RECIPE
================================================================================

Recipe: Iron Longsword
Skill: Smithing
Stat: STR
Target: 15
Materials: 3 iron ingots, 1 leather strip, fuel
Tools: Forge, anvil, hammer
Time: 4 hours

Quality Effects:
  - Volatile (1): -1 damage, 50% break chance on critical miss
  - Rough (2): -1 damage
  - Crude (3): No modifier, poor appearance
  - Simple (4): Standard longsword
  - Functional (5): +0, reliable
  - Decent (6): +0, good balance
  - Sound (7): +1 damage or +1 to hit (choose)
  - Fine (8): +1 damage, +1 to hit
  - Superior (9): +2 damage, +1 to hit
  - Exceptional (10): +2 damage, +2 to hit
  - Exquisite (11): +3 damage, +2 to hit
  - Masterwork (12): +3 damage, +3 to hit, special property

================================================================================
EXPERIENCE AND CRAFTING
================================================================================

How crafting interacts with character progression.

STANDARD CRAFTING:
  No XP awarded.
  Crafting is production, not challenge.
  Using known recipes with available materials is work, not adventure.

WHEN CRAFTING AWARDS XP:
  - First successful craft of a new recipe: Small XP (discovery)
  - Creating something unprecedented: XP based on significance
  - Crafting under dramatic pressure: XP for the situation, not the craft

The GM determines when crafting contributes to story advancement
worthy of experience.

================================================================================
SUMMARY
================================================================================

Element            | Rule
-------------------|--------------------------------------------------
Resolution         | d20 + modifiers >= 11 (standard)
Quality            | (Skill)d12, keep highest = tier
Tiers              | 12 tiers, 1 (Volatile) to 12 (Masterwork)
Pool Bonuses       | Materials, tools, time, assistants (max +3d12)
Pool Penalties     | Poor materials, missing tools, rushed (min 1d12)
Critical Success   | Nat 20: auto-succeed, +2d12 quality
Failure            | 50% materials lost
Critical Failure   | Nat 1: all materials lost, possible consequences
Batch Crafting     | By recipe target, one roll for all
XP                 | None for standard crafting

================================================================================
KEY CONSTANTS
================================================================================

QUALITY_TIERS = 12
MIN_QUALITY_POOL = 1
MAX_ASSISTANT_BONUS = 3 // +3d12 max from assistants
NAT_20_QUALITY_BONUS = 2 // +2d12 on natural 20
FAILURE_MATERIAL_LOSS = 0.5 // 50% on standard failure
CRITICAL_FAILURE_LOSS = 1.0 // 100% on critical failure
BATCH_TIME_MULTIPLIER = 1.5 // 150% time for batch

BATCH_SIZE_LIMITS:
  Easy (11-13): 10
  Moderate (14-16): 5
  Difficult (17-19): 3
  Complex (20+): 1

================================================================================
CROSS-REFERENCES
================================================================================

Document 1: Dice
  - Die types and notation
  - Pool mechanics (keep highest)

Document 3: Resolution
  - Standard resolution (d20 + stat diff >= 11)
  - Success/failure thresholds

Document 7: Abilities
  - Skill system
  - Skill levels and bonuses

Document 12: Progression
  - XP awards
  - When challenges grant XP

================================================================================
EXTENSION STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

This extension builds on core TDGS rules. It does not redefine them.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/crafting
AI-optimized:   https://tacticaldice.com/docs/tdgs/craftingforai

================================================================================
END OF DOCUMENT
================================================================================
