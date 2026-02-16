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

## Group XP Rules

XP remains based on Personal Difficulty. In group encounters, each character's XP is adjusted by a group-size multiplier, and only characters who meaningfully participated are eligible.

### Participation Gate

A character is eligible for XP if they performed **at least one** of the following during the encounter:

1. **Combat Engagement:** Initiated or was the target of at least one resolution roll against the enemy. This is the primary gate. Standing in the room while someone else fights does not qualify. You must have entered the resolution system.
2. **Support:** Provided healing or mitigation to a character who is eligible under another category. Healers earn XP by supporting real combatants. A carry cannot heal another carry to create mutual eligibility.
3. **Objective:** Spent an action that directly advanced the win condition (objective progress, puzzle interaction, etc.).

Characters who do not meet any participation category receive **0 XP** for that encounter.

### Group Size Multiplier

When multiple eligible characters participate in an encounter, each character's Personal XP is multiplied by a group-size factor reflecting shared effort.

| Eligible Players | Multiplier | Example (60 Personal XP) |
|------------------|------------|--------------------------|
| 1 | 1.00 | 60 XP |
| 2 | 0.80 | 48 XP |
| 3 | 0.67 | 40 XP |
| 4 | 0.57 | 34 XP |
| 5 | 0.50 | 30 XP |
| 6 | 0.44 | 26 XP |
| 7 | 0.40 | 24 XP |
| 8 | 0.36 | 21 XP |

```
XP_award = floor(Personal_XP × GroupMultiplier)
If Personal_XP > 0 and XP_award rounds to 0, award 1 XP instead.
```

### Group XP Calculation

1. Determine eligible contributors (participation gate above).
2. For each eligible character, compute Personal XP normally from Difficulty Spectrum.
3. Look up the group-size multiplier for the number of eligible characters.
4. Each eligible character's award = floor(Personal_XP × GroupMultiplier).
5. Non-eligible characters receive 0 XP.

Each player still calculates their own XP based on their own Personal Difficulty. There is no cap, no averaging, and no penalty based on other group members' stats.

### Why This Works

- **Powerleveling is dead.** A carry standing idle cannot enter the resolution system against enemies far above their stats. They fail the participation gate and earn nothing.
- **Mixed-level groups work.** A level 15 and a level 20 fighting together both earn their own Personal XP, adjusted only by the group multiplier. The lower-level player is not punished for grouping with a stronger ally.
- **Healers are covered.** Support eligibility is earned by healing or mitigating for someone who engaged in combat. No special-case rules needed.
- **Personal Difficulty preserved.** Your XP reflects your relationship to the challenge, not the weakest member's.

### Luck and XP

Luck does NOT factor into Difficulty calculation.

A lucky character who rolls well against a dragon still FOUGHT A DRAGON. Fortune helped them survive. The challenge was real. The growth is earned.

Difficulty uses the stats that represent effort and capability, not probability manipulation.

## Leveling

XP buys class levels. The cost depends on how high you're climbing.

### Leveling Cost Brackets

| Current Level | XP per Level |
|---------------|--------------|
| 1-5 | 80 |
| 6-10 | 160 |
| 11-15 | 280 |
| 16-20 | 500 |
| 21-30 | 800 |
| 31-40 | 1,200 |
| 41-50 | 2,000 |
| 51-60 | 3,500 |
| 61-70 | 6,000 |
| 71-80 | 10,000 |
| 81-90 | 16,000 |
| 91-100 | 25,000 |

### Cumulative Totals (Single Class)

| Level | Total XP | Moderate Encounters (~15 XP) |
|-------|----------|------------------------------|
| 20 | 4,600 | ~307 |
| 40 | 23,900 | ~1,593 |
| 60 | 76,600 | ~5,107 |
| 80 | 230,100 | ~15,340 |
| 100 | 625,100 | ~41,673 |

Encounter density varies enormously between tabletop and digital. A tabletop session might see 10-20 encounters. A MUD session might see 100+. The curve is designed to feel responsive early and long-term late regardless of deployment context.

### The Escalating Wall

The cost curve is continuous and exponential. There is no single wall. Every bracket costs more than the last, and the ratio keeps climbing.

At Level 80, a single level costs 10,000 XP. At Level 91, it costs 25,000. Most characters will never reach the highest tiers. That's the point. The math filters naturally.

## Stat Increases

XP can also increase your base stats directly.

### Stat Increase Cost

| Current Stat | Cost for +1 |
|--------------|-------------|
| 1-5 | 50 XP |
| 6-10 | 100 XP |
| 11-20 | 300 XP |
| 21-30 | 500 XP |
| 31-40 | 800 XP |
| 41+ | 1000 XP |

Cost is based on your CURRENT stat value before the increase.

**Example:**

```
STR 10 → 11 costs 100 XP (current stat in 6-10 bracket)
STR 20 → 21 costs 300 XP (current stat in 11-20 bracket)
STR 30 → 31 costs 500 XP (current stat in 21-30 bracket)
```

### Soft Cap

There is no hard cap on stats. The escalating cost IS the cap.

**Example: Raising STR from 10 to 40**

```
10→20: ~2,800 XP
20→30: ~4,800 XP
30→40: ~7,700 XP
Total: ~15,300 XP
```

That's roughly the same XP as reaching Level 32. The math limits you naturally.

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

Each level costs XP based on its bracket. Level 15 costs 280 XP. Level 45 costs 2,000 XP.

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

Next Fighter level (26): 800 XP (21-30 bracket)
Next Mage level (6): 80 XP (1-5 bracket)
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

| Current Level | XP/Level |
|---------------|----------|
| 1-5 | 80 |
| 6-10 | 160 |
| 11-15 | 280 |
| 16-20 | 500 |
| 21-30 | 800 |
| 31-40 | 1,200 |
| 41-50 | 2,000 |
| 51-60 | 3,500 |
| 61-70 | 6,000 |
| 71-80 | 10,000 |
| 81-90 | 16,000 |
| 91-100 | 25,000 |

### Stat Increase Costs

| Current Stat | Cost for +1 |
|--------------|-------------|
| 1-5 | 50 XP |
| 6-10 | 100 XP |
| 11-20 | 300 XP |
| 21-30 | 500 XP |
| 31-40 | 800 XP |
| 41+ | 1,000 XP |


## Document Status

> **Status:** Canonical

This document defines the progression mechanics for TDGS. All advancement in the system follows the rules established here.

---
