# TACTICAL DICE GAME SYSTEM (TDGS) - EXTENSION
# Title: Mass Combat
# Version: 1.0
# Purpose: AI-readable specification for armies, units, commanders, orders, and morale
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

Extension defining rules for mass combat: units (groups of soldiers as single
entities), commanders (who issue orders and inspire morale), and the morale
system that determines when armies break.

BUILDS ON:
  - Document 3: Resolution Mechanics
  - Document 4: Luck
  - Document 12: Progression
  - Document 14: Movement & Positioning

DOES NOT REDEFINE CORE RULES.

================================================================================
CORE PRINCIPLE
================================================================================

A unit IS an Entity. Standard Entity framework applies: race, class, nine stats,
HP, traits. Resolution formula unchanged. No parallel systems.

================================================================================
UNIT STATS
================================================================================

Physical Stats (Soldier Quality):
  STR = Collective fighting power
  DEX = Coordination, formation precision
  REF = Reaction speed as a group
  CON = Staying power, discipline under fire
  MOV = March speed, tactical mobility

Mental Stats (Unit Properties):
  INT = Tactical adaptability
  WIS = Situational awareness
  CHA = Unit cohesion, esprit de corps
  LUK = Fortune as a group

================================================================================
UNIT SCALE
================================================================================

Formation     | Size      | Stat Range
--------------|-----------|------------
Squad         | ~10       | 10-30
Platoon       | ~25-50    | 25-45
Company       | ~100-200  | 35-60
Battalion     | ~500-1000 | 50-80
Regiment      | ~2000+    | 65-100

Race template defines exact stats.
Scale mismatch is legal (squad vs battalion = bad odds for squad).

================================================================================
UNIT HP
================================================================================

FORMULA:
  HP = CON x 5 (per standard Entity rules)

MEANING:
  - Represents fighting strength (casualties + morale combined)
  - At 0 HP: unit destroyed, cannot be rallied

================================================================================
UNIT CREATION
================================================================================

RACE:
  Defines unit type and scale.
  Examples: Infantry Company, Cavalry Squadron, Archer Regiment
  Content defines unit races.

CLASS:
  Defines training and specialization.
  Examples: Veteran, Elite Guard, Irregulars
  Content defines unit classes.

PROCESS:
  1. Select race (unit type)
  2. Determine base stats from race
  3. Select class (training)
  4. Apply class abilities

================================================================================
UNIT PROGRESSION
================================================================================

BATTLE XP:
  Units earn XP from challenges per Document 12.
  They faced danger, they survived, they learn.

TRAINING XP:
  Downtime drilling awards XP.
  Content defines costs (gold, time, trainer) and XP awarded.

SPENDING XP:
  Units spend XP on class levels and stat increases.
  Standard progression rules (Document 12) apply.

================================================================================
CHA BONUS FORMULA
================================================================================

FORMULA:
  CHA Bonus = CHA / 10 (round down, minimum +1)

CHA   | Bonus
------|-------
1-10  | +1
11-20 | +2
21-30 | +3
31-40 | +4
50    | +5
80    | +8

================================================================================
COMMAND STRUCTURE
================================================================================

DIRECT COMMAND:
  - 1 unit
  - Full CHA bonus to morale checks
  - Must be within command range

EXTENDED COMMAND:
  - CHA bonus additional units
  - Half CHA bonus (round down, minimum +1)
  - Must be within command range

COMMAND RANGE:
  - Commander's CHA in squares

UNIT OWNERSHIP:
  - One commander per unit
  - Transfer = release (free action) + claim (action)

================================================================================
COMMANDER ACTIONS
================================================================================

Action          | Cost   | Effect
----------------|--------|------------------------------------------
Standing Orders | Free   | Units continue current orders
New Order       | Action | Change one unit's order
Personal Action | Action | Commander fights, casts, etc.
Rally           | Action | Attempt to recover one routed unit
Claim           | Action | Take command of one uncontrolled unit
Release         | Free   | Release one unit from command

ORDER TIMING:
  Orders issued on commander's turn.
  Units execute on unit's REF turn.

================================================================================
ORDER TYPES
================================================================================

Order     | Effect
----------|----------------------------------------------------------
Attack    | Engage nearest enemy. Standard combat. (Default)
Hold      | +10% REF. No movement. Can attack enemies in range.
Take Cover| +10% REF vs ranged. Limited movement. Requires cover.
Charge    | +10% STR, -10% REF until next turn. Move toward enemy.
Retreat   | Move away from enemy. No opportunity attacks. Cannot use if surrounded.

PERCENTAGE BONUS:
  10% Bonus = Stat / 10 (round down, minimum +1)

================================================================================
MORALE CHECK FORMULA
================================================================================

FORMULA:
  d20 + (Unit CON - Threat Value) + Commander CHA Bonus >= 11

UNCONTROLLED UNITS:
  d20 + (Unit CON - Threat Value) >= 11 (no CHA bonus)

LUCK:
  Applies per Document 4. This is a d20 resolution roll.

================================================================================
MORALE TRIGGERS
================================================================================

Trigger               | Threat Value    | Timing
----------------------|-----------------|----------------------------
50% HP                | 10              | Once when crossed
25% HP                | 14              | Once when crossed
Commander Lost        | 12              | Once when occurs
Friendly Break        | 10              | Once per adjacent unit that breaks
Surrounded            | 12              | Once when first surrounded
Terrifying Enemy      | Enemy's full CHA| Once when first engaged

DEFINITIONS:
  Adjacent: Per Document 14's adjacency rules
  Surrounded: Enemies on 3+ sides (N, S, E, W)
  Engaged: Attacks, is attacked, or is targeted by the entity

================================================================================
TERRIFYING TRAIT
================================================================================

Content-assigned trait for entities of overwhelming power or dread.
Examples: dragons, demon lords, legendary warlords, undead hordes

When unit engages or is targeted by Terrifying entity:
  Morale check with Threat Value = Terrifying entity's full CHA

================================================================================
MORALE CASCADE
================================================================================

When a unit breaks, adjacent friendly units check morale (Threat Value 10).

RESOLUTION ORDER:
  Lowest CON first.
  If weak unit breaks, may trigger additional cascades before stronger units roll.

CRITICAL:
  One weak unit crumbles -> neighbors check -> rout spreads through army.
  Position commander to prevent. Target enemy's weak point to start cascade.

================================================================================
BREAKING OUTCOMES
================================================================================

Outcome   | Condition           | Result
----------|---------------------|----------------------------------------
Routed    | Failed morale check | Flees toward safety, can be rallied
Destroyed | 0 HP                | Removed from battle, cannot be rallied

================================================================================
ROUTED UNITS
================================================================================

BEHAVIOR:
  - Move full MOV toward safety each turn
  - Cannot attack
  - Cannot receive orders
  - Trigger opportunity attacks when fleeing (per Document 14)
  - Can be attacked normally

SAFETY PRIORITY:
  1. Friendly board edge (if exists)
  2. Nearest friendly commander
  3. Directly away from threat

REACHING SAFETY:
  Removed from battle (not destroyed).
  Cannot return this engagement.

================================================================================
CORNERED
================================================================================

When routed unit has no escape route:

CORNERED CHECK:
  d20 + (Unit CON - Original Threat Value) + Commander CHA Bonus (if in range) >= 11

Result | Outcome
-------|--------------------------------------------------------
Pass   | Last stand: no longer routed, +10% STR until uncornered
Fail   | Surrender (removed) or destroyed (depends on enemy)

================================================================================
RALLY
================================================================================

RALLY ACTION:
  Cost: Action
  Range: Commander's CHA in squares
  Roll: d20 + (Commander CHA - Threat Value that caused rout) >= 11

Result  | Outcome
--------|------------------------------------------------------
Success | No longer routed, defaults to Attack order
Failure | Continues fleeing, try again next round

NOTE: Rally uses full CHA (not CHA bonus) - direct force of will vs fear.

================================================================================
CHAIN OF COMMAND
================================================================================

When commander is killed or incapacitated:
  1. Units make immediate morale checks
  2. If another commander in range has capacity: units fall to them
  3. If no commander available: units become uncontrolled

UNCONTROLLED UNITS:
  - Continue standing orders
  - Cannot receive new orders
  - No CHA bonus on morale checks
  - Vulnerable to morale collapse

================================================================================
EXPOSED COMMANDER
================================================================================

When commander's DIRECTLY commanded unit is destroyed:
  Entity that destroyed it gets one free attack on commander.

Extended command units do NOT trigger this.

================================================================================
COMBAT RESOLUTION
================================================================================

UNIT VS UNIT:
  d20 + (Attacker STR - Defender REF) + modifiers >= 11

HERO VS UNIT:
  Normal damage, no special rules.
  Unit HP scales via race template.

UNIT VS HERO:
  d20 + (Unit STR - Hero REF) + modifiers >= 11
  Unit stats scale with formation size.

================================================================================
POSITIONING
================================================================================

FACING:
  Units have facing.
  Document 14 flanking rules apply.

TERRAIN:
  Document 14 rules apply:
  - Flanking
  - Cover
  - Difficult terrain
  - Opportunity attacks

SIZE:
  Race defines grid footprint (e.g., 2x2 for squad, 6x6 for battalion).

================================================================================
TURN ORDER
================================================================================

All Entities (units and heroes) act in REF order per core rules.
No special mass combat initiative system.

================================================================================
XP
================================================================================

COMMANDER XP:
  None from commanding.
  Yes from personal combat.

UNIT XP:
  Battle XP per Document 12.
  Training XP per content.

================================================================================
QUICK REFERENCE
================================================================================

Mechanic          | Formula/Rule
------------------|--------------------------------------------
CHA Bonus         | CHA / 10 (min +1)
Percentage Bonus  | Stat / 10 (min +1)
Command Range     | CHA in squares
Direct Command    | 1 unit, full CHA bonus
Extended Command  | CHA bonus units, half CHA bonus
Morale Check      | d20 + (CON - Threat) + CHA Bonus >= 11
Rally Check       | d20 + (Commander CHA - Threat) >= 11
Uncontrolled      | d20 + (CON - Threat) >= 11
Cornered Check    | d20 + (CON - Threat) + CHA Bonus >= 11
Combat            | d20 + (STR - REF) + modifiers >= 11

================================================================================
STATUS TRANSITIONS
================================================================================

Normal -> [failed morale] -> Routed -> [reaches safety] -> Removed
Normal -> [failed morale] -> Routed -> [rallied] -> Normal (Attack order)
Normal -> [failed morale] -> Routed -> [cornered, pass] -> Last Stand (+10% STR)
Normal -> [failed morale] -> Routed -> [cornered, fail] -> Surrender/Destroyed
Normal -> [0 HP] -> Destroyed

================================================================================
EXTENSION STATUS
================================================================================

Status: Canonical Extension v1.0

Core documents referenced:
  - Document 3: Resolution Mechanics
  - Document 4: Luck
  - Document 12: Progression
  - Document 14: Movement and Positioning

Human-readable: https://tacticaldice.com/docs/tdgs/masscombat
AI-optimized:   https://tacticaldice.com/docs/tdgs/masscombatforai

================================================================================
END OF DOCUMENT
================================================================================

