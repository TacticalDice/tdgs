*Document 13*

# Character Creation

*Building a character from scratch*

## Purpose

This document walks through character creation step by step. It brings together Race, Class, Stats, and everything else into a complete process.

Character creation has seven steps. Follow them in order.

## The Seven Steps

```
1. Choose Race
2. Generate Stats
3. Roll Luck
4. Choose Class(es)
5. Apply Class Bonuses
6. Calculate Derived Values
7. Finishing Touches
```

## Step 1: Choose Race

Race defines what you ARE. Choose first because it determines:

- **Stat Ranges:** Your minimum and maximum starting values
- **Size:** How big you are
- **Innate Traits:** Natural abilities, weapons, and armor

Your Race sets the boundaries. Everything else works within them.

See Document 11 (Races) for Race structure and templates.

## Step 2: Generate Stats

Once you know your Race, generate your eight primary stats: STR, DEX, CON, INT, WIS, CHA, REF, MOV.

LUK is handled separately in Step 3.

### Method 1: Rolling (Default)

Roll 4d6, drop the lowest die. Do this for each stat.

Then apply the delta method:

```
ROLLING FORMULA:

1. Roll 4d6, drop lowest for each stat
2. Delta = Roll - 12
3. Racial Average = (Racial Min + Racial Max) / 2
4. Final Stat = Racial Average + Delta
5. Cap to racial range (min and max)
6. Roll Heroic Pool (2d6 drop lowest, optional)
7. Distribute heroic points to any stats
8. Heroic pool CAN exceed racial ranges
```

### Why Baseline 12?

4d6 drop lowest averages 12.25, not 10. Using baseline 10 would skew everyone toward the top of their range. Baseline 12 centers the distribution properly, giving a true bell curve within your racial range.

**Example: Human STR (range 6-14, average 10)**

```
Roll 15 → Delta +3 → 10 + 3 = 13 ✓
Roll 12 → Delta  0 → 10 + 0 = 10 ✓
Roll  8 → Delta -4 → 10 - 4 = 6  ✓
Roll  5 → Delta -7 → 10 - 7 = 3  → capped to 6
```

**Example: Dragon STR (range 30-50, average 40)**

```
Roll 15 → Delta +3 → 40 + 3 = 43 ✓
Roll 12 → Delta  0 → 40 + 0 = 40 ✓
Roll  8 → Delta -4 → 40 - 4 = 36 ✓
```

Same dice. Same process. Works for Goblins and Gods alike.

### Heroic Pool (Rolling)

After rolling all stats, roll the optional heroic pool (2d6 drop lowest—keep the higher die). These points can be distributed to any stats and CAN exceed racial ranges—just like point buy. A Human who rolled STR 14 (capped at max) could use heroic points to push it to 16.

### Method 2: Point Buy

For tables that prefer balance over randomness.

```
POINT BUY FORMULA:

Base Pool = Sum of all racial stat averages (8 stats)
Heroic Pool = 2d6 drop lowest (optional, GM discretion)
Total Points = Base Pool + Heroic Pool
```

**Base Pool** must stay within racial ranges. You cannot buy a stat above your racial maximum or below your racial minimum.

**Heroic Pool** CAN buy outside racial ranges. This is what makes heroes exceptional. Those extra 1-6 points can push you beyond your race's normal limits.

**Example: Human**

```
All stats average 10
Base Pool = 10 × 8 = 80 points
Heroic Pool = 2d6 drop lowest (roll 3 and 5, keep 5) = 5 points
Total = 85 points to spend

Spend 1:1 within ranges.
Those 5 heroic points can exceed the 14 max if desired.
```

**Example: Dragon**

```
Stat averages: STR 40, DEX 20, CON 45, INT 20, WIS 20, CHA 30, REF 20, MOV 27
Base Pool = 222 points
Heroic Pool = 2d6 drop lowest
```

**Heroic Pool is Optional:**

- Player characters typically get it
- NPCs and creatures may not (GM discretion)
- It represents the spark that makes heroes different

### Choosing Your Method

| Method | Best For |
|--------|----------|
| Rolling | Drama, surprise, classic feel |
| Point Buy | Balance, optimization, competitive tables |

Rolling is the default. Point buy is the alternative. GM decides which method the table uses.

### Extending the System

TDGS is MIT licensed. Extend it. Hack it. Make it yours.

Want a standard array? Build one. Want 3d6 straight down the line? Go for it. Want different point pools? Your table, your rules.

We provide the foundation. You build the house.

## Step 3: Roll Luck

LUK is special. It's always rolled, never bought.

```
LUCK GENERATION:

Roll d20:
  1     = LUK -1
  2-19  = LUK 0
  20    = LUK +1
```

Most characters have LUK 0. Being lucky or unlucky is rare—5% chance each.

**Exception:** If your Race specifically grants a LUK range (like a Leprechaun with +2 to +6), use the delta method for that range instead of the d20.

## Step 4: Choose Class(es)

Class defines what you've TRAINED to become. It provides:

- **Abilities:** Skills, Spells, and Traits
- **Tier Unlocks:** Access to higher-tier abilities
- **Stat Bonuses:** Bonuses from training (applied in Step 5)

### Checking Requirements

Classes have recommended minimum stats. These are soft requirements—guidance, not gates.

A STR 6 character CAN take Fighter. They'll struggle. That's their choice. TDGS allows bad decisions. The math handles consequences.

### Starting Level

New characters typically start at Class Level 1. Your GM may allow higher starting levels for experienced campaigns.

### Multiclassing

You can start with levels in multiple classes if your GM allows and you have the XP. Most new characters start with a single class at Level 1.

See Document 10 (Classes) for Class structure and templates.

## Step 5: Apply Class Bonuses

Your Class Level 1 may grant stat bonuses. Apply them now.

```
Example:
  Base STR (from rolling): 12
  Fighter 1 grants: +1 STR
  Apparent STR: 13
```

These bonuses can push stats above racial ranges. That's training exceeding natural limits.

## Step 6: Calculate Derived Values

With your stats finalized, calculate:

### Hit Points

```
HP = Apparent CON × 5
```

### Knockout Threshold

```
Knockout = HP × 0.05 (round down)

When current HP <= Knockout Threshold, you fall unconscious.
```

### Base Power Tier

```
Base Power Tier = (STR + DEX + CON + INT + WIS + CHA + REF + MOV) / 8

Use BASE stats (before equipment/buffs).
Round down. LUK excluded.
```

### Apparent Power Tier

```
Apparent Power Tier = (Apparent stats) / 8

Use APPARENT stats (with all bonuses).
Round down. LUK excluded.
```

At character creation, Base and Apparent Power Tier are often the same or very close. They diverge as characters acquire equipment.

**Example: Human Fighter**

```
Stats: STR 13, DEX 10, CON 12, INT 10, WIS 10, CHA 10, REF 10, MOV 10

HP = 12 × 5 = 60
Knockout = 60 × 0.05 = 3

Base Power Tier = (13+10+12+10+10+10+10+10) / 8 = 85 / 8 = 10
```

## Step 7: Finishing Touches

The mechanics are done. Now make them a person.

### Equipment

Starting equipment is content-dependent. Your setting determines what's available.

Medieval fantasy? Swords and shields. Sci-fi? Pistols and neural jacks. Post-apocalypse? Scrap and scavenged gear.

Your GM will tell you how to acquire starting equipment for their setting.

### Everything Else

- **Name:** What are you called?
- **Background:** Where did you come from?
- **Personality:** How do you act?
- **Goals:** What do you want?
- **Appearance:** What do you look like?

These aren't mechanical, but they matter. A character is more than numbers.

## Quick Reference

### Rolling Stats (Default)

```
For each of 8 stats:
  1. Roll 4d6, drop lowest
  2. Subtract 12 (this is your delta)
  3. Add delta to racial average
  4. Cap to racial range

Then:
  5. Roll Heroic Pool (2d6 drop lowest, optional)
  6. Distribute points to any stats
  7. Heroic pool can exceed racial range
```

### Point Buy

```
1. Calculate Base Pool (sum of racial averages)
2. Roll Heroic Pool (2d6 drop lowest, optional)
3. Spend points 1:1
4. Base pool stays in racial range
5. Heroic pool can exceed racial range
```

### Luck

```
Roll d20: 1 = -1, 2-19 = 0, 20 = +1
(Unless race grants LUK range)
```

### Derived Values

```
HP = Apparent CON × 5
Knockout = HP × 0.05
Power Tier = Sum of 8 stats / 8 (no LUK)
```

## Example: Creating a Human Fighter

Let's walk through a complete example.

### Step 1: Choose Race

Human. Stat ranges are 6-14 for most stats, 8-12 for MOV.

### Step 2: Generate Stats (Rolling)

```
STR: Roll 14 → Delta +2 → 10 + 2 = 12
DEX: Roll 11 → Delta -1 → 10 - 1 = 9
CON: Roll 15 → Delta +3 → 10 + 3 = 13
INT: Roll  9 → Delta -3 → 10 - 3 = 7
WIS: Roll 12 → Delta  0 → 10 + 0 = 10
CHA: Roll 10 → Delta -2 → 10 - 2 = 8
REF: Roll 13 → Delta +1 → 10 + 1 = 11
MOV: Roll  8 → Delta -4 → 10 - 4 = 6 → capped to 8

Heroic Pool: Roll 2d6 drop lowest → (2, 5) → keep 5
Distribute: +3 to STR (now 15), +2 to CON (now 15)
```

### Step 3: Roll Luck

Roll d20: 7 → LUK 0

### Step 4: Choose Class

Fighter. Recommended STR 10+. We have STR 12. Good fit.

Gain Level 1 abilities: Power Strike +1, Shield Use +1, Armor Training (Trait)

### Step 5: Apply Class Bonuses

Fighter 1 doesn't grant stat bonuses at Level 1 (varies by class design).

Final Stats: STR 15, DEX 9, CON 15, INT 7, WIS 10, CHA 8, REF 11, MOV 8, LUK 0

### Step 6: Calculate Derived Values

```
HP = 15 × 5 = 75
Knockout = 75 × 0.05 = 3
Base Power Tier = (15+9+15+7+10+8+11+8) / 8 = 83 / 8 = 10
```

### Step 7: Finishing Touches

Name: Garrett Cole  
Background: Former town guard  
Personality: Cautious, protective  
Goals: Earn enough gold to buy a farm  
Equipment: (Per GM/setting)

**Done.** Garrett Cole is ready to play.

## Document Status

> **Status:** Canonical

This document defines the character creation process for TDGS. All characters in TDGS-based systems should follow this process, adapted as needed for specific settings.

---
