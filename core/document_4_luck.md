*Document 4*

# Luck

*The attribute that bends reality*

## Purpose

This document defines Luck, the only attribute in TDGS that warps probability itself.

It establishes:

- What Luck represents
- The full -10 to +10 scale and its effects
- How Luck is determined at character creation
- How Luck changes through play
- Why Luck is intentionally unfair

This document builds upon Document 3 (Resolution Mechanics). Luck modifies the resolution system defined there.

## What Luck Is

Luck is not skill. Luck is not effort. Luck is not preparation.

Luck is an **abnormal relationship with probability**.

Most entities exist in a neutral universe. Dice are fair. Outcomes are random. Probability is blind.

Entities with Luck do not live in that universe.

A blessed character walks through a collapsing building as debris misses them by inches. A cursed character trips on a clear path and falls into the one open pit. Neither earned their fate. The universe simply treats them differently.

## The Luck Scale

Luck ranges from **-10 to +10**.

| LUK | Category |
|-----|----------|
| -10 to -3 | Narrative (Cursed) |
| -2 to -1 | Play (Unlucky) |
| 0 | Neutral |
| +1 to +2 | Play (Lucky) |
| +3 to +10 | Narrative (Blessed) |

**Most entities have LUK 0.**

Most play occurs between LUK -2 and LUK +2.

Entities with |LUK| >= 3 are in **narrative territory**: the cursed kings, the blessed oracles, the doomed knights. These are typically reserved for NPCs and story-driven characters, though players can reach these values through extraordinary circumstances.

## How Luck Modifies Resolution

At LUK 0, resolution follows Document 3:

```
d20 + (Your Stat - Their Stat) + Modifiers >= 11
```

Luck changes what is possible.

### Negative Luck: The Ceiling

Negative Luck sets a **maximum success rate**. No matter how favorable the odds, the universe limits how well things can go.

| LUK | Minimum Roll to Succeed | Maximum Success Rate |
|-----|-------------------------|----------------------|
| -10 | 20 | 5% |
| -9 | 19 | 10% |
| -8 | 18 | 15% |
| -7 | 17 | 20% |
| -6 | 16 | 25% |
| -5 | 15 | 30% |
| -4 | 14 | 35% |
| -3 | 13 | 40% |
| -2 | 12 | 45% |
| -1 | 11 | 50% |

A character with LUK -5 and a +20 delta still only succeeds 30% of the time. The math says they should auto-succeed. The universe disagrees.

### Positive Luck: The Floor

Positive Luck sets a **minimum success rate**. No matter how unfavorable the odds, the universe ensures things usually work out.

| LUK | Maximum Roll to Fail | Minimum Success Rate |
|-----|----------------------|----------------------|
| +1 | 10 | 55% |
| +2 | 9 | 60% |
| +3 | 8 | 65% |
| +4 | 7 | 70% |
| +5 | 6 | 75% |
| +6 | 5 | 80% |
| +7 | 4 | 85% |
| +8 | 3 | 90% |
| +9 | 2 | 95% |
| +10 | 1 (reroll) | 99.75% |

A character with LUK +5 and a -20 delta still succeeds 75% of the time. The math says they should auto-fail. The universe makes exceptions.

### The Absolute Rules

> **Critical Rule:**
> 
> **Natural 1 always fails.**
> **Natural 20 always succeeds.**
> 
> *Exception:* LUK +10 may reroll a natural 1 once. A second natural 1 still fails.

Even at LUK -10, a natural 20 succeeds. The universe is cruel, but not absolute.

Even at LUK +10, a natural 1 can fail. Fortune has limits.

## Worked Examples

### Example 1: Cursed Warrior vs Easy Target

**Setup:** A LUK -5 warrior attacks a weak opponent. Warrior has STR 8, opponent has REF 3.

```
Normal calculation:
  Delta = 8 - 3 = +5
  Need: 11 - 5 = 6+
  Normal success rate: 75%

Luck modification:
  LUK -5 ceiling: Must roll 15+ to succeed
  Luck success rate: 30%
```

**Result:** Despite the favorable matchup, the warrior only hits 30% of the time.

The warrior is skilled. The target is slow. But the universe intervenes. Swords slip, footing falters, the sun catches their eyes at the wrong moment. Skill is capped by misfortune.

### Example 2: Blessed Peasant vs Dragon

**Setup:** A LUK +7 peasant throws a rock at a dragon. Peasant has DEX 4, dragon has REF 18.

```
Normal calculation:
  Delta = 4 - 18 = -14
  Need: 11 + 14 = 25+ (impossible without nat 20)
  Normal success rate: 5% (nat 20 only)

Luck modification:
  LUK +7 floor: Only rolls 1-4 fail
  Luck success rate: 85%
```

**Result:** The peasant hits the dragon 85% of the time.

This should be impossible. The peasant is unskilled. The dragon is fast. But the rock catches an updraft, banks off a tree branch, and strikes the dragon's eye. Every time. The peasant cannot explain it. Neither can anyone watching.

### Example 3: Luck Doesn't Always Matter

**Setup:** A LUK +3 rogue picks a simple lock. Rogue has DEX 7, lock has virtual DEX 5.

```
Normal calculation:
  Delta = 7 - 5 = +2
  Need: 11 - 2 = 9+
  Normal success rate: 60%

Luck modification:
  LUK +3 floor: Only rolls 1-8 fail
  Luck success rate: 65%
```

**Result:** 65% success (luck only improves by 5%)

When the normal odds are already decent, positive luck provides a small boost. The rogue is competent, and luck nudges things slightly in their favor.

### Example 4: Negative Luck, Already Bad Odds

**Setup:** A LUK -4 apprentice attempts a master level spell. INT 5 vs difficulty 14.

```
Normal calculation:
  Delta = 5 - 14 = -9
  Need: 11 + 9 = 20 (nat 20 only)
  Normal success rate: 5%

Luck modification:
  LUK -4 ceiling: Must roll 14+ to succeed
  Luck ceiling: 35%
```

**Result:** 5% success (normal rules are already worse than luck ceiling)

When the normal odds are already terrible, negative luck doesn't make them worse—the task is already nearly impossible. The curse has nothing left to take.

### Example 5: The LUK +10 Reroll

**Setup:** A LUK +10 hero attempts to leap a chasm. DEX 6 vs difficulty 10.

```
Normal calculation:
  Delta = 6 - 10 = -4
  Need: 11 + 4 = 15+
  Normal success rate: 30%

Luck modification:
  LUK +10 floor: Only nat 1 fails, and reroll once
  Luck success rate: 99.75%

Roll sequence:
  First roll: 1 (would fail, but reroll granted)
  Second roll: 7 (success due to luck floor)
```

**Result:** The hero makes the leap.

The hero's foot slips on the edge. For an instant, they're falling. Then a gust of wind, an impossible handhold, a branch that wasn't there a moment ago—something intervenes. It always does.

## The Mathematics of LUK +10

At LUK +10, only a natural 1 fails. But the character may reroll that 1 once.

Failure requires rolling 1, then rolling 1 again.

```
Probability: (1/20) × (1/20) = 1/400 = 0.25%
```

A LUK +10 character succeeds **99.75% of the time**.

They walk into a room and walk out with everything they wanted. Plans that should fail succeed. Traps that should trigger don't. Enemies that should hit miss.

They leave nothing but pissed off people in their wake, wondering how anyone could be that fortunate.

*This is intentional.*

## Luck at Character Creation

When creating a character, roll a d20:

| Roll | Starting LUK |
|------|--------------|
| 1 | -1 |
| 2-19 | 0 |
| 20 | +1 |

**90% of characters begin at LUK 0.**

5% begin slightly cursed. 5% begin slightly blessed.

No one starts in narrative territory. That must be earned (or suffered).

## Luck Progression

Luck changes rarely. When it does, it matters.

### Increasing Luck

Luck increases by 1 when:

- The character rolls **three natural 20s in a row** (any rolls, any context)
- The character acquires a **Luck-increasing item** (rare, GM controlled)

### Decreasing Luck

Luck decreases by 1 when:

- The character rolls **three natural 1s in a row** (any rolls, any context)
- The character is affected by a **Luck-decreasing curse or item** (rare, GM controlled)

### Streak Tracking

Track consecutive natural 1s and natural 20s separately.

Any non-matching roll resets the relevant streak.

```
Example:
  Roll 20 → streak_20 = 1
  Roll 15 → streak_20 = 0
  Roll 20 → streak_20 = 1
  Roll 20 → streak_20 = 2
  Roll 20 → streak_20 = 3 → LUK +1, reset to 0
```

### The Probability of Change

```
Triple 20: (1/20)³ = 1/8,000 = 0.0125%
Triple 1:  (1/20)³ = 1/8,000 = 0.0125%
```

At ~50 rolls per session and ~50 sessions per year:

**Expected time to triple 20: ~3.2 years**

This is rare. When it happens, the table will remember.

## The Spiral

Luck creates momentum.

A character with LUK -3 fails more often. More failures mean more chances to roll 1s. More 1s mean more chances for triple 1. Triple 1 means LUK -4. The spiral deepens.

A character with LUK +3 succeeds more often. More successes mean more chances to roll 20s. More 20s mean more chances for triple 20. Triple 20 means LUK +4. The spiral ascends.

*This is intentional.*

The universe picks favorites. TDGS encodes that truth.

## Why Luck Is Unfair

Luck is the most powerful attribute in TDGS. It is also the hardest to change and the most constrained at character creation.

This is not an accident.

TDGS makes a deliberate design choice: **Luck is unfair because luck is unfair.**

Real fortune does not care about balance. It does not distribute evenly. It does not reward effort. Some people are simply luckier than others, and that luck compounds.

TDGS does not pretend otherwise.

The safeguards are:

- **Rarity at creation:** 90% of characters start at LUK 0
- **Difficult progression:** Triple 20s and triple 1s are rare events
- **GM control over items:** Luck-modifying items are explicitly rare and GM-gated
- **Narrative territory guidance:** |LUK| >= 3 is flagged as exceptional

Players who reach LUK +5 through years of play have earned something remarkable. Players who spiral to LUK -5 are living a tragedy. Both are valid stories.

But most play will occur in the -2 to +2 range, where Luck nudges outcomes without dominating them.

## Luck and Initiative

Luck serves as a **tiebreaker** for initiative, not a modifier.

```
Physical contests: REF → LUK → d2
Magical contests: LUK → d2
```

A character with REF 6 and LUK +10 loses initiative to a character with REF 7 and LUK -10.

The cursed character acts first. The cursed character probably misses.

Luck does not make you faster. It makes your actions bend probability when they occur.

## Luck and Magnitude

> **Critical Rule:**
> 
> **Luck affects RESOLUTION only.**
> **Luck NEVER affects MAGNITUDE.**

A LUK +10 character hits almost every time.

They do not hit harder.

Damage, duration, area, quantity—*all magnitude values*—are unaffected by Luck. Fortune determines whether something happens, not how much happens.

## Guidance for Game Masters

### Play Range (-2 to +2)

Most characters should remain in this range. Luck provides flavor and occasional dramatic moments without dominating play.

- A LUK +1 character has slightly better odds. They're "kind of lucky."
- A LUK -1 character has slightly worse odds. They're "a bit unlucky."
- Neither breaks the game.

### Narrative Range (|LUK| >= 3)

Reserve this for special circumstances:

- **NPCs:** The blessed oracle, the cursed knight, the fortunate merchant prince
- **Story arcs:** A character seeking to break a curse or preserve a blessing
- **Earned progression:** A player who achieves triple 20s through years of play

Narrative-range Luck changes the feel of every scene the character enters. Use it deliberately.

### Luck Modifying Items

These should be:

- **Rare:** Not available in shops
- **Significant:** Plot-relevant, not random loot
- **Costly:** Require sacrifice, quest, or consequence
- **Reversible** (usually): Curses can be broken, blessings can be lost

A +1 LUK item is a campaign defining treasure. A +3 LUK item is a world-altering artifact.

## Document Status

> **Status:** Canonical

This document defines Luck for TDGS. All luck-related mechanics in the system conform to the rules established here.

Changes to this document should be rare, deliberate, and backward compatible.

---
