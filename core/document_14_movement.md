*Document 14*

# Movement & Positioning

*Where things are and how they get there*

## Purpose

This document defines spatial mechanics. It establishes how distance works, how movement happens, and how position affects combat.

TDGS supports both grid-based tactical play and theater-of-mind abstraction. The engine defines both systems. Your table chooses which to use.

## Distance

TDGS uses a hybrid distance system. Grid rules provide precision. Range bands provide abstraction. Both are valid.

### Grid System

```
1 MOV = 1 square
Content defines scale (e.g., 1 square = 5 feet, 1.5 meters)
```

A character with MOV 10 can move 10 squares with a Move action. TDGS calculates in squares - content defines what a square represents in your world.

Diagonal movement costs 1 square (not 1.5). Gameplay trumps geometry.

### Range Bands

For theater-of-mind play, distance is measured in bands:

| Band | Grid Equivalent | Description |
|------|-----------------|-------------|
| Adjacent | 0-1 squares | Touching, melee range |
| Near | 2-4 squares | Close, easy reach |
| Far | 5-10 squares | Ranged combat distance |
| Distant | 11+ squares | Long range, significant travel |

MOV determines how many bands you can cross per Move action:

- **MOV 6 or less:** 1 band
- **MOV 7-12:** 2 bands
- **MOV 13+:** 3 bands

### Measurement Units Note

TDGS uses **squares** as its abstract unit of distance. The engine calculates in squares and is agnostic to real-world measurement systems. Content defines what a square represents:

- Fantasy content: 1 square = 5 feet
- Metric content: 1 square = 1.5 meters
- Sci-fi content: 1 square = 2 meters

The examples in this document use feet for familiarity, but your content can use any scale. See also Document 15 (Equipment & Slots) for weight unit (WU) standardization.

## Movement

### Move Action

A Move action lets you move up to your MOV in squares.

```
Move Action = Up to MOV squares
```

This costs your Action for the turn. You can move before or after other activities on your turn, but the total cannot exceed MOV.

### Step

A Step is a free action allowing minor repositioning.

```
Step = 1 square
Always 1 square.
Not affected by terrain.
Does NOT trigger opportunity attacks.
```

Step is for small tactical adjustments. Need to move more? Use your Action.

### Terrain and Movement

Terrain affects how far you can travel:

| Terrain | Movement Cost | Examples |
|---------|---------------|----------|
| Normal | Full MOV | Roads, open ground, floors |
| Difficult | Half MOV (round down) | Mud, rubble, undergrowth, shallow water |
| Very Difficult | Quarter MOV (round down) | Deep snow, dense jungle, waist-deep water |

**Example (MOV 10):**

```
Normal terrain: 10 squares
Difficult terrain: 5 squares
Very Difficult: 2 squares
```

Step ignores terrain. It's always 1 square, always free.

## Terrain Types

The engine defines four terrain patterns. Content builds specific terrains using these.

### Difficult Terrain

Movement costs double. Half your MOV (round down).

**Examples:** Mud, rubble, undergrowth, shallow water, loose sand, icy ground.

### Hazardous Terrain

Deals damage when you enter or start your turn there.

Damage amount defined by content (fire might deal 1d6, acid pools 2d8, etc.).

**Examples:** Fire, acid pools, spike traps, extreme heat, toxic gas.

### Blocking Terrain

Cannot pass. Blocks line of sight.

**Examples:** Walls, boulders, closed doors, thick trees, pillars.

### Obscuring Terrain

Blocks line of sight. Does NOT block movement.

**Examples:** Fog, smoke, magical darkness, heavy rain, dense foliage.

## Line of Sight

To target something, you must see it.

```
Draw a line from the center of your square to the center of the target's square.

Clear = Line of sight (can target)
Blocked = No line of sight (cannot target)
```

Blocking terrain and Obscuring terrain block line of sight. One line. Clear or not. No arguments.

## Adjacency

```
Adjacent = Within 1 square (includes diagonals)
```

A character has 8 adjacent squares (the ring around them). Sharing an edge or corner both count as adjacent.

Melee attacks require adjacency unless the weapon has Reach.

## Range and Weapons

Weapons have range categories determining where they're effective.

### Weapon Range Table

| Range Type | Optimal Band | Extended (-2) | Maximum |
|------------|--------------|---------------|---------|
| Melee | Adjacent | — | Adjacent |
| Reach | Adjacent, Near | — | Near |
| Thrown | Near | Far | Far |
| Ranged | Far | Distant | Distant |
| Long Range | Distant | — | Distant |

**Optimal:** No penalty. This is where the weapon is designed to work.

**Extended:** -2 to hit. One band beyond optimal. Pushing the weapon's limits.

**Beyond Maximum:** Cannot hit. Out of range entirely.

### Melee and Reach

Melee weapons (swords, axes, fists) only work at Adjacent range. No extended range. You're in arm's reach or you're not.

Reach weapons (spears, polearms, whips) threaten both Adjacent AND Near. This is their advantage—zone control without sacrificing close combat.

## Cover

Cover makes you harder to hit with ranged attacks.

| Cover Type | Bonus | Description |
|------------|-------|-------------|
| Partial | +2 REF | 25-50% obscured (low wall, thin tree) |
| Half | +4 REF | 50-75% obscured (thick pillar, window) |
| Full | Untargetable | 75%+ obscured (complete concealment) |

Cover affects REF (making you harder to hit). If the attack still hits, armor reduces damage as normal.

Cover applies against ranged attacks. Melee attackers are already adjacent—a wall between you isn't helping.

## Opportunity Attacks

When you leave a hostile's threatened range, they get a free attack.

```
TRIGGER: Leaving an adjacent square of a hostile entity

RESULT: The hostile gets one free melee attack against you
  - Uses normal attack (STR vs REF)
  - Happens before you complete your movement
  - One opportunity attack per triggering movement
```

This prevents cost-free disengagement. Position matters. Leaving melee has consequences.

### Avoiding Opportunity Attacks

Two ways to leave safely:

**Step:** Your 1-square free action never triggers opportunity attacks. Small adjustment, always safe.

**Disengage:** Spend your Action to Disengage. You can then move up to MOV without triggering opportunity attacks this turn. You're trading your attack for safe escape.

### Reach and Opportunity Attacks

Reach weapons threaten Adjacent AND Near squares. Leaving either range triggers an opportunity attack from the reach weapon wielder.

The spearman controls more ground. That's the trade-off.

## Flanking

Coordinated positioning grants attack bonuses.

```
FLANKING: Two allies on opposite sides of an enemy

Requirement:
  - Both attackers adjacent to target
  - Positioned on opposite sides (straight line through target)

Bonus: +2 to hit for both flanking attackers
```

Flanking rewards teamwork and tactical movement.

### Surrounded

More attackers means more pressure.

| Condition | Adjacent Enemies | Bonus |
|-----------|------------------|-------|
| Flanked | 2 (opposite sides) | +2 to hit |
| Surrounded | 3+ | +4 to hit |
| Overwhelmed | 5+ | +6 to hit |

## High Ground (Optional Rule)

Elevation can provide advantage.

```
HIGH GROUND: +2 to hit when at higher elevation than target
```

This rule is optional. Use it if your table wants elevation to matter mechanically. Otherwise, handle elevation narratively through GM discretion.

## Falling

What goes up must come down. Usually painfully.

```
FALLING DAMAGE:

1d6 per 2 squares fallen
Cap: 10d6 (20 squares)
```

| Squares | Damage | Example (5ft scale) |
|---------|--------|---------------------|
| 2 | 1d6 | 10 feet |
| 4 | 2d6 | 20 feet |
| 10 | 5d6 | 50 feet |
| 20+ | 10d6 (capped) | 100+ feet |

After 20 squares, you've hit terminal velocity. The ground doesn't hit any harder.

**Reducing Fall Damage:** The engine doesn't mandate a method. Content may provide skills (Tumble, Acrobatics) or abilities (Slow Fall, Cat's Grace) that reduce or negate falling damage.

## Forced Movement

Some abilities push, pull, or slide targets.

| Type | Effect |
|------|--------|
| Push | Move target X squares directly away from you |
| Pull | Move target X squares directly toward you |
| Slide | Move target X squares in any direction |

**Critical:** Forced movement does NOT trigger opportunity attacks.

You're not choosing to leave. You're being moved. There's a difference.

## Summary Tables

### Movement Quick Reference

| Action | Distance | Notes |
|--------|----------|-------|
| Move | Up to MOV squares | Costs Action |
| Step | 1 square | Free action, no OA |
| Disengage | Up to MOV squares | Costs Action, no OA |

### Terrain Effects

| Terrain | Movement | Other |
|---------|----------|-------|
| Normal | Full MOV | — |
| Difficult | Half MOV | — |
| Very Difficult | Quarter MOV | — |
| Hazardous | Varies | Damage on entry/start |
| Blocking | Cannot pass | Blocks LoS |
| Obscuring | Normal | Blocks LoS |

### Positional Modifiers

| Condition | Modifier |
|-----------|----------|
| Flanking | +2 to hit |
| Surrounded (3+) | +4 to hit |
| Overwhelmed (5+) | +6 to hit |
| High Ground (optional) | +2 to hit |
| Partial Cover | +2 REF |
| Half Cover | +4 REF |
| Full Cover | Untargetable |
| Extended Range | -2 to hit |

### Range Bands

| Band | Squares | Typical Use |
|------|---------|-------------|
| Adjacent | 0-1 | Melee combat |
| Near | 2-4 | Reach weapons, close thrown |
| Far | 5-10 | Ranged weapons |
| Distant | 11+ | Long range weapons |

## Design Notes

### Why Hybrid Distance?

Some tables love grids. Some hate them. Both are valid. The engine supports both so content can choose.

### Why Diagonals Cost 1?

Technically, diagonal movement across a square is ~1.4 times the distance. Some systems alternate 1-2-1-2. We don't.

Simpler math means faster play. The geometric inaccuracy is a worthwhile trade for not arguing about whether your move was 7 or 7.5 squares.

### Why Opportunity Attacks?

Without them, melee combatants get kited. Ranged attackers just walk away forever. Opportunity attacks create sticky melee engagement and make positioning matter.

Step and Disengage provide escape options. The system creates tension, then gives you tools to manage it.

## Document Status

> **Status:** Canonical

This document defines movement and positioning for TDGS. All spatial mechanics in TDGS-based systems should follow these rules.

---
