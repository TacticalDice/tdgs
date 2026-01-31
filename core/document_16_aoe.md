*Document 16*

# Area of Effect

*Fire doesn't pick favorites*

## Purpose

This document defines how Area of Effect (AoE) works in TDGS. It establishes:

- How to measure distance for AoE shapes
- Standard AoE shapes (circle, cone, line, rectangle)
- AoE notation
- How height interacts with AoE
- What AoE affects
- Where AoE originates

This document does NOT define which abilities have AoE. That's content's job. This document defines the framework content uses to describe AoE effects.

## The Core Principle

**AoE affects an area, not specific Entities.**

Fire doesn't choose who to burn. A shockwave doesn't skip the friendly knight standing next to the enemy. When an effect covers an area, everything in that area is affected.

This is intentional. It creates tactical positioning pressure. Don't cluster your troops if the enemy has a fireball. Don't stand next to the dragon when your wizard winds up. Friendly fire isn't a bug - it's a feature that rewards careful placement.

> **Note:** Specific abilities can override this. A "smart" fireball that only hits enemies is possible - but it's a trait of that specific ability, not a property of AoE in general. The core assumption is: area affects all.

## AoE Notation

TDGS uses standardized notation for AoE effects, similar to dice notation (3d6).

### Format

```
[Shape][Primary][Direction][wWidth][hHeight]
```

- Direction is required for Cones and Lines (N, NE, E, SE, S, SW, W, NW)
- Direction is not used for Circles or Rectangles

### Shape Codes

| Code | Shape |
|------|-------|
| Cir | Circle |
| Con | Cone |
| Lin | Line |
| Rec | Rectangle |

### Examples

| Notation | Meaning |
|----------|---------|
| Cir3 | Circle, radius 3 |
| Con4N | Cone, length 4, pointing North (forward) |
| Con4NE | Cone, length 4, pointing Northeast |
| Lin5E | Line, length 5, pointing East (right) |
| Lin5Sw2 | Line, length 5, width 2, pointing South (behind) |
| Rec3x4 | Rectangle, 3 wide × 4 long |
| Cir3h1 | Circle, radius 3, height 1 (ground-hugging) |
| Con6Nh10 | Cone, length 6, pointing North, height 10 (towering) |

### Reading Notation

- First comes the shape (Cir, Con, Lin, Rec)
- Then the primary dimension (radius for circles, length for cones/lines, W×L for rectangles)
- For cones and lines: direction suffix (N, NE, E, SE, S, SW, W, NW)
- Optional: w followed by width (lines only; defaults to 1 if not specified)
- Optional: h followed by height (overrides default)

## Direction Is Relative to Entity

**Critical:** Directions are relative to the entity, not the map.

- **North (N):** Directly in front of the entity
- **South (S):** Directly behind the entity
- **East (E):** To the entity's right
- **West (W):** To the entity's left
- **Diagonals (NE, SE, SW, NW):** Between the cardinal directions

This means "Con4N" always means "cone pointing forward from the caster" regardless of which way the map is oriented or which direction the caster is facing on the map.

When an entity casts a cone or line, they choose which of their 8 relative directions to project it. The notation records that choice relative to the caster, not the map.

## Measuring Distance

TDGS uses **Chebyshev distance** (also called King's distance or chessboard distance).

### Formula

```
Distance = max(|dx|, |dy|)
```

Where dx is horizontal squares and dy is vertical squares.

**In plain terms:** Distance is how many moves a chess king would take to get from point A to point B. Diagonal movement counts the same as orthogonal movement.

| From Center | Distance |
|-------------|----------|
| Adjacent orthogonal | 1 |
| Adjacent diagonal | 1 |
| Two squares away (any direction) | 2 |
| Three orthogonal + two diagonal | 3 |

### Why Chebyshev?

We chose this metric for specific reasons:

**For Humans:**

- Count squares like a chess king
- No complicated math
- No lookup tables required
- Easy to eyeball on a grid

**For Computers:**

- Single formula: max(|dx|, |dy|)
- O(1) calculation
- No floating point issues
- Clean boundary detection

**Tradeoff acknowledged:** Chebyshev distance produces square-ish shapes, not true circles. A "radius 3 circle" is actually a 7×7 square. We accept this tradeoff for simplicity. The tactical outcomes remain meaningful - being "within 3 squares" has consistent meaning regardless of direction.

### Boundaries Are Inclusive

**General principle:** All boundaries are inclusive.

"Within radius 3" means distance <= 3. If you're exactly at the edge, you're in the area. If any part of an Entity's space is within the boundary, that Entity is affected.

No arguments about "is distance 3 inside or outside radius 3?" It's inside. Always.

## Standard Shapes

TDGS defines four standard AoE shapes. Content uses these to describe effects.

| Shape | Parameters | Total Squares |
|-------|------------|---------------|
| Circle | Radius | (2R+1)² |
| Cone (Cardinal) | Length | L² |
| Cone (Diagonal) | Length | L(L+1)/2 |
| Line | Length, Width | L × W |
| Rectangle | Width, Length | W × L |

## Circle

A circle affects all squares within the specified radius of the center point.

**Notation:** Cir[radius]

**Parameters:**

- **Radius:** Distance from center (using Chebyshev distance)
- **Center:** The origin point of the effect

**Origin affected?** Yes. The center square is part of the circle.

**Total squares:** (2R+1)²

| Radius | Dimensions | Total Squares |
|--------|------------|---------------|
| 1 | 3×3 | 9 |
| 2 | 5×5 | 25 |
| 3 | 7×7 | 49 |
| 4 | 9×9 | 81 |
| 5 | 11×11 | 121 |

### Radius 2 Circle (Cir2)

```
X X X X X
X X X X X
X X O X X
X X X X X
X X X X X
```

O = center (origin). All X squares affected. Total: 25 squares.

### Radius 3 Circle (Cir3)

```
X X X X X X X
X X X X X X X
X X X X X X X
X X X O X X X
X X X X X X X
X X X X X X X
X X X X X X X
```

Total: 49 squares.

## Cone

A cone originates from a point and expands outward in a direction. Think dragon breath: starts at the mouth, spreads wider as it goes.

**Notation:** Con[length][direction]

**Parameters:**

- **Origin:** The starting square (typically the caster)
- **Direction:** One of 8 relative directions (N, NE, E, SE, S, SW, W, NW)
- **Length:** How far the cone extends

**Origin affected?** No. The origin is the source point. The effect starts in the squares beyond the origin.

## Cardinal Cones (N, E, S, W)

Cardinal cones expand evenly on both sides of the center axis.

**Width at distance N:** 2N - 1 (odd numbers: 1, 3, 5, 7, 9...)

**Total squares:** L² (Length squared)

| Distance | Width | Running Total |
|----------|-------|---------------|
| 1 | 1 | 1 |
| 2 | 3 | 4 |
| 3 | 5 | 9 |
| 4 | 7 | 16 |
| 5 | 9 | 25 |
| 6 | 11 | 36 |

**Memory trick:** Total squares = Length². A length-4 cone hits 16 squares. A length-5 cone hits 25 squares.

### Length 3 Cone pointing NORTH (Con3N)

```
X X X X X      ← distance 3 (5 wide)
  X X X        ← distance 2 (3 wide)
    X          ← distance 1 (1 wide)
    O          ← origin (caster here, NOT affected)
```

Total: 9 squares (3² = 9)

### Length 3 Cone pointing EAST (Con3E)

```
      X
    X X
O X X X        ← O is origin (NOT affected)
    X X
      X
```

Read left to right: distance 1 is 1 wide, distance 2 is 3 wide, distance 3 is 5 wide. Total: 9 squares.

### Length 4 Cone pointing NORTH (Con4N)

```
X X X X X X X    ← distance 4 (7 wide)
  X X X X X      ← distance 3 (5 wide)
    X X X        ← distance 2 (3 wide)
      X          ← distance 1 (1 wide)
      O          ← origin (NOT affected)
```

Total: 16 squares (4² = 16)

## Diagonal Cones (NE, SE, SW, NW)

Diagonal cones point toward corners and use a simpler expansion pattern.

**Width at distance N:** N

**Total squares:** L(L+1)/2

| Distance | Width | Running Total |
|----------|-------|---------------|
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |
| 4 | 4 | 10 |
| 5 | 5 | 15 |
| 6 | 6 | 21 |

### Length 3 Diagonal Cone pointing NE (Con3NE)

```
      X X X    ← distance 3 (width 3)
      X X      ← distance 2 (width 2)
      X        ← distance 1 (width 1)
O              ← origin (NOT affected)
```

Total: 1+2+3 = 6 squares

### Length 4 Diagonal Cone pointing NE (Con4NE)

```
        X X X X    ← distance 4 (width 4)
        X X X      ← distance 3 (width 3)
        X X        ← distance 2 (width 2)
        X          ← distance 1 (width 1)
O                  ← origin (NOT affected)
```

Total: 1+2+3+4 = 10 squares

### Cardinal vs Diagonal: The Tradeoff

| Cone Type | Width Formula | Total Squares | Directions |
|-----------|---------------|---------------|------------|
| Cardinal | 2N - 1 | L² | 4 (N, E, S, W) |
| Diagonal | N | L(L+1)/2 | 4 (NE, SE, SW, NW) |

**Diagonal cones cover less area** (~60% of cardinal) **but provide 8 total directions** instead of 4.

This is intentional. Diagonal cones trade raw power for positioning flexibility. A dragon breathing diagonally hits fewer squares but can target corners that cardinal directions can't reach.

### Quick Reference: Cone Sizes

| Length | Cardinal Total | Diagonal Total |
|--------|----------------|----------------|
| 2 | 4 | 3 |
| 3 | 9 | 6 |
| 4 | 16 | 10 |
| 5 | 25 | 15 |
| 6 | 36 | 21 |

## Line

A line is a straight path from the origin in a specified direction.

**Notation:** Lin[length][direction] or Lin[length][direction]w[width]

**Parameters:**

- **Origin:** The starting square
- **Direction:** One of 8 relative directions
- **Length:** How many squares long
- **Width:** Number of parallel lines (default 1)

**Origin affected?** No. The origin is the source point. The line starts in the square beyond the origin.

**Total squares:** Length × Width

**Wide lines:** For lines with width greater than 1, the origin expands to match the line's width, centered on the caster's position.

### Length 5 Line pointing EAST (Lin5E)

```
O X X X X X
```

O = origin (NOT affected). X = affected squares. Total: 5 squares.

### Length 4 Line pointing NORTH, Width 2 (Lin4Nw2)

```
X X    ← distance 4
X X    ← distance 3
X X    ← distance 2
X X    ← distance 1
O O    ← origin (NOT affected)
```

Total: 8 squares (4 × 2)

### Length 5 Line pointing NE (Lin5NE)

```
        X    ← distance 5
      X      ← distance 4
    X        ← distance 3
  X          ← distance 2
X            ← distance 1
O            ← origin (NOT affected)
```

Total: 5 squares (same as cardinal)

**Rule:** Line length = squares affected, regardless of direction.

## Rectangle

A rectangle is an axis-aligned grid of squares.

**Notation:** Rec[width]x[length]

**Parameters:**

- **Width:** Horizontal extent in squares (east-west on the grid)
- **Length:** Vertical extent in squares (north-south on the grid)
- **Origin:** A corner of the rectangle, placed within range

**Origin affected?** Yes. The origin corner is part of the rectangle.

**Total squares:** Width × Length

**Placement:** Unlike cones and lines (which project from the caster), rectangles are placed at range like circles. The caster chooses a point within range as one corner of the rectangle. The rectangle then extends from that corner in the positive width and length directions.

### Rec3x4 placed at range

```
X X X    ← far edge
X X X
X X X
O X X    ← origin corner (placed by caster)
```

O = origin corner chosen by caster. Total: 12 squares.

Content can specify orientation or alternate placement rules if needed (e.g., "centered on point" or "caster chooses orientation").

## Height

TDGS shapes are defined in 2D with an implicit height component.

**Rule:** An AoE shape's height equals its primary dimension.

| Shape | Primary Dimension | Default Height |
|-------|-------------------|----------------|
| Circle | Radius | Radius |
| Cone | Length | Length |
| Line | Length | Length |
| Rectangle | Larger dimension | Larger dimension |

**Example:** Cir3 (radius 3 circle) is a cylinder 3 squares tall, centered vertically on the origin point's elevation.

**Example:** Con4 (length 4 cone) is a 3D cone shape, 4 squares tall.

### Why This Approach?

**For Tabletop:** Ignore height entirely. Play on a 2D grid. The default height is generous enough that "if they're in the circle, they're hit" works fine.

**For Digital:** Height is defined. Code can check if targets are within both the 2D shape AND the height bounds.

**For Content:** Override when needed. A "ground-only" fog might specify Cir3h1 (height 1). A pillar of flame might specify Cir2h10.

## Where AoE Starts

Every AoE has an origin point - where the effect begins or centers.

**Default Rule:** The caster chooses the origin point within the effect's range.

### Origin by Shape

| Shape | Origin Role | Origin Affected? |
|-------|-------------|------------------|
| Circle | Center of the area | Yes |
| Cone | Source point (caster) | No |
| Line | Source point (caster) | No |
| Rectangle | Corner placed within range | Yes |

**Why the difference?**

Circles and rectangles define areas placed at range. The caster chooses where the area goes, and the origin is part of that area.

Cones and lines define projections from a source. The source emits the effect but isn't inside it. The dragon's mouth isn't inside its own breath weapon.

### Range to Origin

Content defines how far the caster can place the origin point.

**Example ability text:**

- "Fireball: Range 20, Cir3" - caster can place the center anywhere within 20 squares
- "Flame Breath: Con4, originates from caster" - cone starts at caster's square
- "Lightning Bolt: Range 15, Lin6" - line starts anywhere within 15 squares

If content doesn't specify range, assume the effect originates from the caster.

## Applying AoE Effects

**Timing:** AoE resolves immediately when triggered. Entities in the area cannot move or take actions in response before resolution occurs.

When an AoE effect occurs:

1. **Determine the origin point** (per ability definition or caster choice)
2. **Map the shape** (circle, cone, line, or rectangle with specified dimensions)
3. **Identify all Entities in the area** (every Entity with any part of its space within the footprint)
4. **Determine cover** (from origin to each Entity, per Document 14)
5. **Apply the effect to each Entity** (damage, conditions, forced movement, etc.)

Each Entity in the area is affected once, regardless of how much of their space overlaps with the AoE.

### Resolution Rolls

If the AoE effect requires a roll (attack vs defense), roll once per affected Entity. Each Entity resolves independently.

**AoE resolution rolls are standard d20 rolls. Luck applies per Document 4.**

### Cover

Cover is determined from the AoE's origin point to each Entity. Apply Document 14's cover rules:

| Cover Type | Bonus | Effect on AoE |
|------------|-------|---------------|
| Partial | +2 REF | Harder to hit |
| Half | +4 REF | Much harder to hit |
| Full | Untargetable | Not affected |

**Example:** A fireball (Cir3) explodes. One goblin is in the open, one is behind a low wall (partial cover), one is completely behind a pillar (full cover). The open goblin has no bonus. The wall goblin gets +2 REF. The pillar goblin isn't affected at all.

### Multi-Square Entities

For Entities occupying multiple squares (large creatures, units):

**Rule:** If ANY square of the Entity's space is within the AoE footprint, the Entity is affected.

The Entity is affected once, not once per overlapping square.

### Stacking AoE

If multiple AoE effects overlap:

**Rule:** Each effect applies independently. An Entity in the overlap is affected by all applicable effects.

Standing in the intersection of a fireball and a lightning bolt? Take damage from both.

## Content Guidance

When content creates an ability with AoE, specify:

| Property | Required? | Example |
|----------|-----------|---------|
| Shape | Yes | Cir3, Con4N, Lin5Ew2, Rec4x3 |
| Range | Yes | 20 squares, Self, Touch |
| Height | If non-default | h1, h10 |
| Effect | Yes | 3d6 fire damage, Difficult terrain |
| Resolution | Yes | INT vs REF, WIS vs CON |
| Smart Targeting | If applicable | "Allies excluded" |

### Example Ability Definitions

```
Fireball
Range: 20 squares
Shape: Cir3
Effect: Fire damage
Resolution: Caster INT vs Target REF
Damage: 5d6 (half on successful defense)
```

```
Dragon Breath
Range: Self (cone originates from dragon)
Shape: Con5N (direction chosen at use)
Effect: Fire damage
Resolution: Dragon CON vs Target REF
Damage: 8d6
```

```
Lightning Bolt
Range: Self
Shape: Lin8E (direction chosen at use)
Effect: Lightning damage
Resolution: Caster INT vs Target REF
Damage: 6d6
```

### Smart Targeting

Core AoE affects all Entities in the area. If content wants an ability that only affects enemies, that's a trait of that ability.

| Trait | Effect |
|-------|--------|
| Allies Excluded | Does not affect entities on caster's side |
| Enemies Only | Only affects hostile entities |
| Selective | Caster chooses which entities in area are affected |

These are content additions, not core mechanics. They should be rare - indiscriminate AoE creates better tactical play.

## Summary

### Notation Quick Reference

| Notation | Meaning |
|----------|---------|
| Cir3 | Circle, radius 3 |
| Con4N | Cone, length 4, forward |
| Con4NE | Cone, length 4, forward-right |
| Lin5E | Line, length 5, right |
| Lin5Sw2 | Line, length 5, width 2, behind |
| Rec3x4 | Rectangle, 3×4 |
| +h[N] | Height override |

**Directions:** N (forward), S (behind), E (right), W (left), NE/SE/SW/NW (diagonals) - relative to entity, not map.

### Shape Quick Reference

| Shape | Origin Affected | Total Squares |
|-------|-----------------|---------------|
| Circle | Yes | (2R+1)² |
| Cone (Cardinal) | No | L² |
| Cone (Diagonal) | No | L(L+1)/2 |
| Line | No | L × W |
| Rectangle | Yes | W × L |

### Cone Width Reference

| Distance | Cardinal Width | Diagonal Width |
|----------|----------------|----------------|
| 1 | 1 | 1 |
| 2 | 3 | 2 |
| 3 | 5 | 3 |
| 4 | 7 | 4 |
| 5 | 9 | 5 |

### Full Summary Table

| Concept | Rule |
|---------|------|
| Core Principle | AoE affects area, not entities; all entities in area affected |
| Distance Metric | Chebyshev (king's moves): max(\|dx\|, \|dy\|) |
| Boundaries | Always inclusive (<= not <) |
| Circle | All squares within radius of center; origin IS affected |
| Cone (Cardinal) | Width = 2N-1; Total = L²; origin NOT affected |
| Cone (Diagonal) | Width = N; Total = L(L+1)/2; origin NOT affected |
| Line | One square per length; origin NOT affected |
| Rectangle | W × L grid; origin IS affected; placed at range like circles |
| Default Height | Equals primary dimension (radius, length, etc.) |
| Origin | Caster chooses within range (default) |
| Cover | Applies from origin per Document 14 |
| Resolution | Per Entity, standard d20 rolls, Luck applies |
| Multi-Square Entities | Any overlap = affected (once) |
| Stacking | Each effect applies independently |
| Smart Targeting | Content adds as ability trait; not default |

## Design Notes

**Why Chebyshev distance?**
Simple for humans (count like a chess king), simple for computers (one formula), no lookup tables. Square-ish shapes are an acceptable tradeoff.

**Why 2D with height cap?**
Serves both tabletop (ignore height) and digital (height defined). Default height catches most cases; content overrides for exceptions.

**Why different cone formulas?**
Cardinal cones expand perpendicular to axis (easy on grid). Diagonal cones use simpler expansion to avoid awkward geometry. The tradeoff (less area, more directions) is documented and intentional.

**Why area-only targeting?**
Creates tactical meaning. Positioning matters when AoE doesn't discriminate. Smart targeting is a power upgrade, not the baseline.

## Document Status

> **Status:** Canonical

This document defines AoE mechanics for TDGS. Content references this document when creating AoE abilities.

**Related documents:**

- Document 3: Resolution Mechanics
- Document 4: Luck
- Document 14: Movement and Positioning

---
