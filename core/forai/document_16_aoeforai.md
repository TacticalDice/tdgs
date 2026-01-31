# Title: Area of Effect
# Document: 16
# Version: 1.0
# Purpose: AI-readable specification for AoE shapes, distances, and targeting
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
CORE PRINCIPLE
================================================================================

AoE affects area, not entities. All entities in the area are affected.
No discrimination. Content can add smart targeting as ability trait.

================================================================================
NOTATION
================================================================================

FORMAT:
  [Shape][Primary][Direction][wWidth][hHeight]

SHAPE CODES:
  Code | Shape     | Direction Required?
  -----|-----------|--------------------
  Cir  | Circle    | No
  Con  | Cone      | Yes
  Lin  | Line      | Yes
  Rec  | Rectangle | No

DIRECTION CODES: N, NE, E, SE, S, SW, W, NW

DIRECTIONS ARE RELATIVE TO ENTITY:
  N = forward
  S = behind
  E = right
  W = left

NOTATION EXAMPLES:
  Notation   | Meaning
  -----------|----------------------------------
  Cir3       | Circle, radius 3
  Con4N      | Cone, length 4, forward
  Con4NE     | Cone, length 4, forward-right (diagonal)
  Lin5E      | Line, length 5, right
  Lin5Sw2    | Line, length 5, south, width 2
  Rec3x4     | Rectangle, 3 wide × 4 long
  Cir3h1     | Circle, radius 3, height 1
  Con6Nh10   | Cone, length 6, north, height 10

================================================================================
DISTANCE
================================================================================

CHEBYSHEV DISTANCE:
  Distance = max(|dx|, |dy|)

Diagonal = orthogonal. King's moves on chessboard.

BOUNDARIES: Always inclusive (≤ not <).

================================================================================
SHAPES SUMMARY
================================================================================

Shape              | Origin Affected | Total Squares  | Placement
-------------------|-----------------|----------------|------------
Circle             | Yes             | (2R+1)²        | At range
Cone (Cardinal)    | No              | L²             | From caster
Cone (Diagonal)    | No              | L(L+1)/2       | From caster
Line               | No              | L × W          | From caster
Rectangle          | Yes             | W × L          | At range

================================================================================
CIRCLE
================================================================================

NOTATION: Cir[radius]

FORMULA: All squares where max(|dx|, |dy|) ≤ R from center

TOTAL: (2R+1)²

  Radius | Dimensions | Squares
  -------|------------|--------
  1      | 3×3        | 9
  2      | 5×5        | 25
  3      | 7×7        | 49
  4      | 9×9        | 81
  5      | 11×11      | 121

ORIGIN: Center of circle. IS affected.

PLACEMENT: At range (caster chooses center within range).

================================================================================
CONE (CARDINAL: N, E, S, W)
================================================================================

NOTATION: Con[length][direction]

WIDTH AT DISTANCE N: 2N - 1

TOTAL: L²

  Distance | Width | Running Total
  ---------|-------|---------------
  1        | 1     | 1
  2        | 3     | 4
  3        | 5     | 9
  4        | 7     | 16
  5        | 9     | 25
  6        | 11    | 36

ORIGIN: Caster's square. NOT affected.

PLACEMENT: Projects from caster in chosen direction.

================================================================================
CONE (DIAGONAL: NE, SE, SW, NW)
================================================================================

NOTATION: Con[length][direction]

WIDTH AT DISTANCE N: N

TOTAL: L(L+1)/2

  Distance | Width | Running Total
  ---------|-------|---------------
  1        | 1     | 1
  2        | 2     | 3
  3        | 3     | 6
  4        | 4     | 10
  5        | 5     | 15
  6        | 6     | 21

ORIGIN: Caster's square. NOT affected.

TRADEOFF: ~60% area of cardinal, but 8 total directions available.

================================================================================
CONE SIZE COMPARISON
================================================================================

  Length | Cardinal | Diagonal
  -------|----------|----------
  2      | 4        | 3
  3      | 9        | 6
  4      | 16       | 10
  5      | 25       | 15
  6      | 36       | 21

================================================================================
LINE
================================================================================

NOTATION: Lin[length][direction] or Lin[length][direction]w[width]

TOTAL: L × W (width defaults to 1)

ORIGIN: Caster's square. NOT affected.

WIDE LINES: Origin expands to match width, centered on caster.

DIAGONAL LINES: One square per unit of length along diagonal path.

================================================================================
RECTANGLE
================================================================================

NOTATION: Rec[width]x[length]

  Width = horizontal (east-west)
  Length = vertical (north-south)

TOTAL: W × L

ORIGIN: Corner placed within range. IS affected.

PLACEMENT: At range (like circles). Caster chooses corner position.
Extends in positive W and L directions.

================================================================================
HEIGHT
================================================================================

DEFAULT RULE: Height = primary dimension

  Shape     | Primary Dimension | Default Height
  ----------|-------------------|---------------
  Circle    | Radius            | Radius
  Cone      | Length            | Length
  Line      | Length            | Length
  Rectangle | Larger of W, L    | Larger of W, L

OVERRIDE: Add h[N] to notation (e.g., Cir3h1)

================================================================================
RESOLUTION
================================================================================

TIMING: AoE resolves immediately. No reactions before resolution.

STEPS:
  1. Determine origin point
  2. Map shape
  3. Identify all entities in area
  4. Determine cover (from origin to each entity)
  5. Apply effect to each entity

ROLLS:
  - Per entity, independently
  - Standard d20 resolution
  - Luck applies (Document 4)

COVER (per Document 14):
  Cover Type | Bonus   | Effect
  -----------|---------|------------------
  Partial    | +2 REF  | Harder to hit
  Half       | +4 REF  | Much harder to hit
  Full       | —       | Not affected

Cover determined from AoE origin to each entity.

MULTI-SQUARE ENTITIES: Any overlap = affected (once).

STACKING: Multiple AoE effects apply independently.

================================================================================
CONTENT GUIDANCE
================================================================================

ABILITY DEFINITION:
  Property        | Required       | Example
  ----------------|----------------|----------------------------
  Shape           | Yes            | Cir3, Con4N, Lin5Ew2, Rec4x3
  Range           | Yes            | 20 squares, Self, Touch
  Height          | If override    | h1, h10
  Effect          | Yes            | 3d6 fire damage
  Resolution      | Yes            | INT vs REF
  Smart Targeting | If applicable  | Allies excluded

SMART TARGETING TRAITS:
  Trait           | Effect
  ----------------|-------------------------------
  Allies Excluded | Does not affect caster's side
  Enemies Only    | Only affects hostiles
  Selective       | Caster chooses targets in area

Not default. Content adds as needed.

================================================================================
QUICK REFERENCE - FORMULAS
================================================================================

  Shape          | Total Squares
  ---------------|---------------
  Circle         | (2R+1)²
  Cone Cardinal  | L²
  Cone Diagonal  | L(L+1)/2
  Line           | L × W
  Rectangle      | W × L

================================================================================
QUICK REFERENCE - ORIGIN RULES
================================================================================

  Shape     | Origin  | Affected? | Placement
  ----------|---------|-----------|------------
  Circle    | Center  | Yes       | At range
  Cone      | Caster  | No        | From caster
  Line      | Caster  | No        | From caster
  Rectangle | Corner  | Yes       | At range

================================================================================
QUICK REFERENCE - CONE WIDTH
================================================================================

  Distance | Cardinal | Diagonal
  ---------|----------|----------
  1        | 1        | 1
  2        | 3        | 2
  3        | 5        | 3
  4        | 7        | 4
  5        | 9        | 5

================================================================================
CROSS-REFERENCES
================================================================================

Document 3: Resolution Mechanics
  - Standard d20 resolution
  - Success thresholds

Document 4: Luck
  - Luck rerolls apply to AoE

Document 14: Movement and Positioning
  - Cover rules
  - Multi-square entities

================================================================================
CORE STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

This is a CORE document. It establishes fundamental AoE mechanics.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/aoe
AI-optimized:   https://tacticaldice.com/docs/tdgs/aoeforai

================================================================================
END OF DOCUMENT
================================================================================
`;
// Styles matching other forai pages
const styles = {
  container: {
    minHeight: '100vh',
    background: 'linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%)',
    color: '#e2e8f0',
    fontFamily: 'ui-monospace, SFMono-Regular, "SF Mono", Menlo, Consolas, monospace',
    fontSize: 14,
    lineHeight: 1.8,
    padding: '40px 20px',
  } as React.CSSProperties,
  content: {
    maxWidth: 900,
    margin: '0 auto',
  } as React.CSSProperties,
  header: {
    textAlign: 'center' as const,
    marginBottom: 40,
    paddingBottom: 20,
    borderBottom: '1px solid rgba(6, 182, 212, 0.3)',
  },
  navLink: {
    display: 'inline-flex',
    alignItems: 'center',
    gap: 8,
    color: '#22d3ee',
    textDecoration: 'none',
    fontSize: 13,
    padding: '8px 16px',
    background: 'rgba(6, 182, 212, 0.15)',
    borderRadius: 6,
    marginRight: 12,
    marginBottom: 8,
    transition: 'all 0.2s',
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    color: '#f8fafc',
    marginBottom: 8,
    letterSpacing: '-0.02em',
  },
  subtitle: {
    color: '#94a3b8',
    fontSize: 14,
  },
  coreBadge: {
    display: 'inline-block',
    background: 'linear-gradient(135deg, #10b981 0%, #059669 100%)',
    color: '#fff',
    padding: '4px 12px',
    borderRadius: 6,
    fontSize: 12,
    fontWeight: 'bold',
    marginBottom: 12,
  },
  section: {
    marginBottom: 40,
  },
  sectionTitle: {
    fontSize: 18,
    fontWeight: 'bold',
    color: '#22d3ee',
    marginBottom: 16,
    paddingBottom: 8,
    borderBottom: '1px solid rgba(6, 182, 212, 0.2)',
  },
  codeBlock: {
    background: 'rgba(0, 0, 0, 0.4)',
    borderRadius: 8,
    padding: 20,
    marginBottom: 20,
    overflow: 'auto',
    border: '1px solid rgba(6, 182, 212, 0.2)',
  },
  code: {
    color: '#e2e8f0',
    whiteSpace: 'pre' as const,
    display: 'block',
    fontSize: 13,
  },
  table: {
    width: '100%',
    borderCollapse: 'collapse' as const,
    marginBottom: 20,
    fontSize: 13,
  },
  th: {
    textAlign: 'left' as const,
    padding: '10px 14px',
    borderBottom: '1px solid rgba(6, 182, 212, 0.3)',
    color: '#22d3ee',
    fontWeight: 600,
  },
  td: {
    padding: '10px 14px',
    borderBottom: '1px solid rgba(255, 255, 255, 0.05)',
    color: '#cbd5e1',
  },
};

export default function TDGSAoEForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="aoe" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS AREA OF EFFECT - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 16 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_AOE_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## SHAPES SUMMARY</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Shape</th>
                <th style={styles.th}>Origin Affected</th>
                <th style={styles.th}>Total Squares</th>
                <th style={styles.th}>Placement</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Circle</td><td style={styles.td}>Yes</td><td style={styles.td}>(2R+1)²</td><td style={styles.td}>At range</td></tr>
              <tr><td style={styles.td}>Cone (Cardinal)</td><td style={styles.td}>No</td><td style={styles.td}>L²</td><td style={styles.td}>From caster</td></tr>
              <tr><td style={styles.td}>Cone (Diagonal)</td><td style={styles.td}>No</td><td style={styles.td}>L(L+1)/2</td><td style={styles.td}>From caster</td></tr>
              <tr><td style={styles.td}>Line</td><td style={styles.td}>No</td><td style={styles.td}>L × W</td><td style={styles.td}>From caster</td></tr>
              <tr><td style={styles.td}>Rectangle</td><td style={styles.td}>Yes</td><td style={styles.td}>W × L</td><td style={styles.td}>At range</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FORMULAS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Shape</th>
                <th style={styles.th}>Total Squares</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Circle</td><td style={styles.td}>(2R+1)²</td></tr>
              <tr><td style={styles.td}>Cone Cardinal</td><td style={styles.td}>L²</td></tr>
              <tr><td style={styles.td}>Cone Diagonal</td><td style={styles.td}>L(L+1)/2</td></tr>
              <tr><td style={styles.td}>Line</td><td style={styles.td}>L × W</td></tr>
              <tr><td style={styles.td}>Rectangle</td><td style={styles.td}>W × L</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## ORIGIN RULES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Shape</th>
                <th style={styles.th}>Origin</th>
                <th style={styles.th}>Affected?</th>
                <th style={styles.th}>Placement</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Circle</td><td style={styles.td}>Center</td><td style={styles.td}>Yes</td><td style={styles.td}>At range</td></tr>
              <tr><td style={styles.td}>Cone</td><td style={styles.td}>Caster</td><td style={styles.td}>No</td><td style={styles.td}>From caster</td></tr>
              <tr><td style={styles.td}>Line</td><td style={styles.td}>Caster</td><td style={styles.td}>No</td><td style={styles.td}>From caster</td></tr>
              <tr><td style={styles.td}>Rectangle</td><td style={styles.td}>Corner</td><td style={styles.td}>Yes</td><td style={styles.td}>At range</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## CONE WIDTH BY DISTANCE</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Distance</th>
                <th style={styles.th}>Cardinal</th>
                <th style={styles.th}>Diagonal</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>1</td><td style={styles.td}>1</td><td style={styles.td}>1</td></tr>
              <tr><td style={styles.td}>2</td><td style={styles.td}>3</td><td style={styles.td}>2</td></tr>
              <tr><td style={styles.td}>3</td><td style={styles.td}>5</td><td style={styles.td}>3</td></tr>
              <tr><td style={styles.td}>4</td><td style={styles.td}>7</td><td style={styles.td}>4</td></tr>
              <tr><td style={styles.td}>5</td><td style={styles.td}>9</td><td style={styles.td}>5</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## HEIGHT DEFAULTS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Shape</th>
                <th style={styles.th}>Primary Dimension</th>
                <th style={styles.th}>Default Height</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Circle</td><td style={styles.td}>Radius</td><td style={styles.td}>Radius</td></tr>
              <tr><td style={styles.td}>Cone</td><td style={styles.td}>Length</td><td style={styles.td}>Length</td></tr>
              <tr><td style={styles.td}>Line</td><td style={styles.td}>Length</td><td style={styles.td}>Length</td></tr>
              <tr><td style={styles.td}>Rectangle</td><td style={styles.td}>Larger of W, L</td><td style={styles.td}>Larger of W, L</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## KEY RULES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Rule</th>
                <th style={styles.th}>Value</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Distance Formula</td><td style={styles.td}>max(|dx|, |dy|) - Chebyshev</td></tr>
              <tr><td style={styles.td}>Boundaries</td><td style={styles.td}>Inclusive (≤ not &lt;)</td></tr>
              <tr><td style={styles.td}>Resolution</td><td style={styles.td}>Per entity, independently</td></tr>
              <tr><td style={styles.td}>Multi-Square Entities</td><td style={styles.td}>Any overlap = affected once</td></tr>
              <tr><td style={styles.td}>Stacking</td><td style={styles.td}>Multiple AoE apply independently</td></tr>
              <tr><td style={styles.td}>Smart Targeting</td><td style={styles.td}>Not default, content adds as trait</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(6, 182, 212, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/aoe"
            style={{
              ...styles.navLink,
              background: 'rgba(6, 182, 212, 0.25)',
            }}
          >
            View Human-Readable Version 
          </Link>
        </footer>
      </div>
    </div>
  );
