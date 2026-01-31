*Document 12*

# Progression

*How you grow and advance*

## Purpose

This document defines how entities improve over time. It establishes the XP system, leveling costs, stat increases, and the rules governing advancement.

TDGS uses a unified progression system. Whether you're fighting dragons, negotiating treaties, or solving ancient puzzles, the same rules apply. Challenge yourself, survive, grow.

## Experience Points (XP)

XP is earned by overcoming challenges. The harder the challenge relative to YOUR capabilities, the more you learn from it.

## The Difficulty Spectrum

Every challenge has a Difficulty based on how hard it is FOR YOU.

```
Difficulty = 11 - (Your Stat - Their Stat) - Modifiers
```

This formula should look familiar. It's the resolution formula from Document 3, rearranged.

**Resolution (Doc 3):** "Did I succeed?"

```
d20 + (Your Stat - Their Stat) + Modifiers ≥ 11
```

**Difficulty (Doc 12):** "What do I need to roll?"

```
Difficulty = 11 - (Your Stat - Their Stat) - Modifiers
```

Same math. Different question. Resolution asks if you passed. Difficulty tells you the target number. The Difficulty Spectrum then maps that target number to XP.

### Same Formula, Different Questions

**Example: You (STR 14) vs Goblin (REF 10)**

Using Resolution:

```
d20 + (14 - 10) + 0 ≥ 11
d20 + 4 ≥ 11
d20 ≥ 7
You need to roll 7 or higher to hit.
```

Using Difficulty:

```
Difficulty = 11 - (14 - 10) - 0
Difficulty = 11 - 4 = 7
The target number is 7.
```

Same answer. Difficulty 7 = Routine = 10 XP on success.

### Calculating Difficulty

**Example 1: Fighting a Goblin**

```
You (STR 14) attack Goblin (REF 10)
Delta = 14 - 10 = 4
Difficulty = 11 - 4 = 7
Difficulty 7 = Routine (Tier 4) = 10 XP on success
```

**Example 2: Fighting a Dragon**

```
You (STR 10) attack Dragon (REF 25)
Delta = 10 - 25 = -15
Difficulty = 11 - (-15) = 26
Difficulty 26 = Mythic = 175 XP on success
```

**Example 3: Easy Fight With Advantage**

```
You (STR 20) attack Peasant (REF 8), flanking (+2)
Delta = 20 - 8 = 12
Difficulty = 11 - 12 - 2 (flanking) = -3
Difficulty ≤ 0 = No XP (too easy to learn from)
```

This is personal. A dragon that's Challenging for a warrior might be Legendary for a wizard. Same dragon, different lessons learned.

### The Difficulty Spectrum Table

| Tier | Difficulty | Name | Success XP | Failure XP |
|------|------------|------|------------|------------|
| 1 | 2 | Trivial | 1 | 0 |
| 2 | 3-4 | Simple | 3 | 0 |
| 3 | 5-6 | Easy | 6 | 0 |
| 4 | 7-8 | Routine | 10 | 0 |
| 5 | 9-10 | Moderate | 15 | 0 |
| 6 | 11-12 | Challenging | 25 | 0 |
| 7 | 13-14 | Difficult | 40 | 20 |
| 8 | 15-16 | Hard | 60 | 30 |
| 9 | 17-18 | Heroic | 85 | 42 |
| 10 | 19-20 | Legendary | 120 | 60 |
| — | 21+ | Mythic | 175 | 87 |

**Difficulty ≤ 0:** No XP. If it's that easy, you're not learning anything.

## XP Timing

XP is awarded at the **end of an encounter**, per challenge overcome.

- Defeat three goblins? Three XP awards (one per goblin).
- Negotiate a treaty? One XP award (one challenge).
- Solve a puzzle then fight its guardian? Two XP awards.

"Overcome" means defeated, bypassed, resolved, solved, or concluded. The method doesn't matter. The result does.

## Failure XP

Failure teaches, but only if you survive to learn from it.

**Tier 7+ only:** Failure XP is only available for Difficult challenges and above.

**Half XP:** Failure awards half the success XP (rounded down).

**Survival required:** You must survive the failure. The ones who didn't survive? They learned nothing.

## No Group Penalty

TDGS has no group XP penalty. Here's why:

- **Personal Difficulty already differentiates.** The warrior finds the goblin trivial (3 XP). The wizard finds it challenging (25 XP). Same fight, different growth.
- **Positional advantages already reduce Difficulty.** Flanking grants +2, surrounded grants +4. These reduce your Difficulty naturally.
- **Large groups have real-world costs.** Scheduling, slow combat, split spotlight. The game doesn't need to punish you mechanically too.
- **Solo players aren't punished.** Playing alone is already harder. Why make it worse?
- **Transparency and player agency.** Every player calculates their own XP. No hidden math.
- **Simplicity.** One system. The Difficulty Spectrum handles everything.

### Luck and XP

Luck does NOT factor into Difficulty calculation.

A lucky character who rolls well against a dragon still FOUGHT A DRAGON. Fortune helped them survive. The challenge was real. The growth is earned.

Difficulty uses the stats that represent effort and capability, not probability manipulation.

## Leveling

XP buys class levels. The cost depends on how high you're climbing.

### Leveling Cost Brackets

| Bracket | Levels | XP per Level |
|---------|--------|--------------|
| Novice | 1-20 | 50 |
| Journeyman | 21-40 | 100 |
| Veteran | 41-60 | 200 |
| Master | 61-80 | 400 |
| Legend | 81-100 | 1,500 |

### Cumulative Totals (Single Class)

| Level | Total XP | Typical Timeline |
|-------|----------|------------------|
| 20 | 1,000 | ~20 sessions |
| 40 | 3,000 | ~60 sessions (~1 year) |
| 60 | 7,000 | ~140 sessions (~3 years) |
| 80 | 15,000 | ~300 sessions (~6 years) |
| 100 | 45,000 | ~900 sessions (~17 years) |

These assume ~50 XP per session on average. Your table will vary.

### The Legend Wall

Notice the jump from Master (400 XP/level) to Legend (1,500 XP/level).

This is intentional.

Crossing into Legend is transcendence, not progression. Most characters will never reach it. That's the point. Level 80 is mastery. Level 81 is something else entirely.

## Stat Increases

XP can also increase your base stats directly.

### Stat Increase Cost

| Current Stat | Cost for +1 |
|--------------|-------------|
| 1-10 | 50 XP |
| 11-20 | 100 XP |
| 21-30 | 200 XP |
| 31-40 | 400 XP |
| 41+ | 800 XP |

Cost is based on your CURRENT stat value before the increase.

**Example:**

```
STR 10 → 11 costs 100 XP (entering 11-20 bracket)
STR 20 → 21 costs 200 XP (entering 21-30 bracket)
STR 30 → 31 costs 400 XP (entering 31-40 bracket)
```

### Soft Cap

There is no hard cap on stats. The escalating cost IS the cap.

**Example: Raising STR from 10 to 40**

```
10→20: ~1,000 XP
20→30: 2,000 XP
30→40: 4,000 XP
Total: ~7,000 XP
```

That's roughly the same XP as reaching Level 60. The math limits you naturally.

### The Stats-Only Trap

Dumping all XP into stats is allowed. It's also a trap.

A character with STR 40 and no class levels:

- Hits hard
- Has no abilities
- No skills, no spells, no traits from class
- Can only do what a basic attack covers

A character with STR 15 and Fighter 30:

- Hits reasonably hard
- Has Power Strike, Cleave, Battle Cry
- Has Tier 3 abilities unlocked
- Can do things beyond "I swing"

Stats without abilities is a one-trick pony. The system allows it. The math punishes it.


## What XP Buys

XP purchases exactly two things:

### 1. Class Levels

Each level costs XP based on its bracket. Level 15 costs 50 XP (Novice). Level 45 costs 200 XP (Veteran).

Class levels grant:

- Abilities (Skills, Spells, Traits)
- Tier unlocks
- Stat bonuses (as defined by the class)

### 2. Stat Increases

Direct stat purchases at scaling cost. No class required.

### What XP Does NOT Buy

- Individual skills
- Individual spells
- Individual traits
- Items
- Narrative outcomes

Skills, spells, and traits come from classes. Want Power Strike without taking Fighter? Find a mentor, find a magic item, convince your GM. Don't just throw XP at it.

This preserves class identity while keeping the world flexible.

## Multiclassing

Characters can have levels in multiple classes. There are no restrictions.

### Single XP Pool

XP is earned once and pooled. You choose how to split it.

```
Earn 150 XP from a session.
Choose: 100 to Fighter, 50 to Mage.
NOT: 150 to Fighter AND 150 to Mage.
```

### Separate Level Costs

Each class tracks its own level. Costs are based on level in THAT class.

```
Character: Fighter 25 / Mage 5

Next Fighter level (26): 100 XP (Journeyman bracket)
Next Mage level (6): 50 XP (Novice bracket)
```

### Level 1 Exception

Taking Level 1 of a new class never adds to skills you already know. This prevents multiclass dipping abuse.

```
Have Power Strike from Fighter.
Take Barbarian 1 (also grants Power Strike +1).
Result: No bonus. You already know it.
```

Higher levels still add normally. The exception only applies to Level 1 grants.


## When To Spend XP

### Default: Between Scenes

XP is spent between scenes. Finish the fight, catch your breath, realize you've grown.

No mid-combat level ups. No sudden power spikes in the middle of a negotiation.

### GM Override

GMs can change this ruling for their table. GMs can change ANY ruling for their table. It's THEIR table.

Want instant level ups? Your game. Want to require weeks of downtime training? Your game. TDGS provides defaults. GMs provide final authority.

## Skills From Outside Classes

Skills can come from sources other than classes:

- **Items:** A magic sword that grants a skill
- **Narrative/Training:** An old master teaches you
- **GM Discretion:** Story events grant abilities
- **Transformation:** New racial abilities from changing what you are

Skills CANNOT be purchased directly with XP. The path to abilities outside your class goes through the fiction, not the character sheet.

## Bonus XP

GMs and systems can award bonus XP at their discretion.

Suggestions:

- Exceptional roleplay
- Clever solutions
- Character milestones
- Session MVP
- Completing story arcs

Bonus XP is gravy. The Difficulty Spectrum is the meal.

## Summary Tables

### XP Awards (Difficulty Spectrum)

| Difficulty | Tier | Success | Failure |
|------------|------|---------|---------|
| 2 | Trivial | 1 | 0 |
| 3-4 | Simple | 3 | 0 |
| 5-6 | Easy | 6 | 0 |
| 7-8 | Routine | 10 | 0 |
| 9-10 | Moderate | 15 | 0 |
| 11-12 | Challenging | 25 | 0 |
| 13-14 | Difficult | 40 | 20 |
| 15-16 | Hard | 60 | 30 |
| 17-18 | Heroic | 85 | 42 |
| 19-20 | Legendary | 120 | 60 |
| 21+ | Mythic | 175 | 87 |

### Leveling Costs

| Bracket | Levels | XP/Level |
|---------|--------|----------|
| Novice | 1-20 | 50 |
| Journeyman | 21-40 | 100 |
| Veteran | 41-60 | 200 |
| Master | 61-80 | 400 |
| Legend | 81-100 | 1,500 |

### Stat Increase Costs

| Current Stat | Cost for +1 |
|--------------|-------------|
| 1-10 | 50 XP |
| 11-20 | 100 XP |
| 21-30 | 200 XP |
| 31-40 | 400 XP |
| 41+ | 800 XP |


## Document Status

> **Status:** Canonical

This document defines the progression mechanics for TDGS. All advancement in the system follows the rules established here.

---
