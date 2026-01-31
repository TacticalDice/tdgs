# Title: Luck
# Version: 1.0
# Purpose: AI-readable specification for luck mechanics
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

Luck is the only attribute in TDGS that warps probability itself.

This document defines:
  - What Luck represents
  - The full -10 to +10 scale and its effects
  - How Luck is determined at character creation
  - How Luck changes through play
  - Why Luck is intentionally unfair

This document builds upon Document 3 (Resolution Mechanics).
Luck modifies the resolution system defined there.

================================================================================
WHAT LUCK IS
================================================================================

Luck is NOT skill. Luck is NOT effort. Luck is NOT preparation.

Luck is an ABNORMAL RELATIONSHIP WITH PROBABILITY.

Most entities exist in a neutral universe:
  - Dice are fair
  - Outcomes are random
  - Probability is blind

Entities with Luck do NOT live in that universe.

A blessed character walks through a collapsing building as debris misses them.
A cursed character trips on a clear path and falls into the one open pit.
Neither earned their fate. The universe simply treats them differently.

================================================================================
THE LUCK SCALE
================================================================================

Luck ranges from -10 to +10.

┌─────────────────────────────────────────────────────────────────────────────┐
│  LUK Range    │ Category                                                    │
│───────────────│─────────────────────────────────────────────────────────────│
│  -10 to -3    │ Narrative (Cursed)                                          │
│  -2 to -1     │ Play (Unlucky)                                              │
│  0            │ Neutral                                                     │
│  +1 to +2     │ Play (Lucky)                                                │
│  +3 to +10    │ Narrative (Blessed)                                         │
└─────────────────────────────────────────────────────────────────────────────┘

MOST ENTITIES HAVE LUK 0.
Most play occurs between LUK -2 and LUK +2.
Entities with |LUK| >= 3 are in NARRATIVE TERRITORY.

================================================================================
HOW LUCK MODIFIES RESOLUTION
================================================================================

At LUK 0, resolution follows Document 3:
  d20 + (Your Stat − Their Stat) + Modifiers >= 11

Luck changes what is possible.

NEGATIVE LUCK: THE CEILING
--------------------------
Negative Luck sets a MAXIMUM SUCCESS RATE.
No matter how favorable the odds, the universe limits how well things can go.

  LUK    │ Min Roll to Succeed │ Max Success Rate
  ───────│─────────────────────│──────────────────
  -10    │ 20                  │ 5%
  -9     │ 19                  │ 10%
  -8     │ 18                  │ 15%
  -7     │ 17                  │ 20%
  -6     │ 16                  │ 25%
  -5     │ 15                  │ 30%
  -4     │ 14                  │ 35%
  -3     │ 13                  │ 40%
  -2     │ 12                  │ 45%
  -1     │ 11                  │ 50%

Formula: Minimum roll to succeed = 11 + |LUK|

POSITIVE LUCK: THE FLOOR
------------------------
Positive Luck sets a MINIMUM SUCCESS RATE.
No matter how unfavorable the odds, the universe ensures things usually work out.

  LUK    │ Max Roll to Fail │ Min Success Rate
  ───────│──────────────────│──────────────────
  +1     │ 10               │ 55%
  +2     │ 9                │ 60%
  +3     │ 8                │ 65%
  +4     │ 7                │ 70%
  +5     │ 6                │ 75%
  +6     │ 5                │ 80%
  +7     │ 4                │ 85%
  +8     │ 3                │ 90%
  +9     │ 2                │ 95%
  +10    │ 1 (reroll)       │ 99.75%

Formula: Maximum roll to fail = 11 - LUK

================================================================================
THE ABSOLUTE RULES
================================================================================

┌─────────────────────────────────────────────────────────────────────────────┐
│  Natural 1 ALWAYS fails.                                                    │
│  Natural 20 ALWAYS succeeds.                                                │
│  EXCEPTION: LUK +10 may reroll a natural 1 ONCE.                            │
│  A second natural 1 still fails.                                            │
└─────────────────────────────────────────────────────────────────────────────┘

Even at LUK -10, a natural 20 succeeds. The universe is cruel, but not absolute.
Even at LUK +10, a natural 1 can fail. Fortune has limits.

================================================================================
THE MATHEMATICS OF LUK +10
================================================================================

At LUK +10:
  - Only a natural 1 fails
  - Character may reroll that 1 once
  - Failure requires rolling 1, then rolling 1 again

Probability: (1/20) × (1/20) = 1/400 = 0.25%

A LUK +10 character succeeds 99.75% OF THE TIME.

This is intentional.

================================================================================
LUCK AT CHARACTER CREATION
================================================================================

When creating a character, roll a d20:

  Roll    │ Starting LUK
  ────────│─────────────
  1       │ -1
  2-19    │ 0
  20      │ +1

90% of characters begin at LUK 0.
5% begin slightly cursed (-1).
5% begin slightly blessed (+1).

No one starts in narrative territory. That must be earned—or suffered.

================================================================================
LUCK PROGRESSION
================================================================================

Luck changes rarely. When it does, it matters.

INCREASING LUCK:
  Luck increases by 1 when:
    - Character rolls THREE NATURAL 20s IN A ROW (any rolls, any context)
    - Character acquires a LUCK-INCREASING ITEM (rare, GM-controlled)

DECREASING LUCK:
  Luck decreases by 1 when:
    - Character rolls THREE NATURAL 1s IN A ROW (any rolls, any context)
    - Character is affected by a LUCK-DECREASING CURSE/ITEM (rare, GM-controlled)

STREAK TRACKING:
  Track consecutive natural 1s and natural 20s separately.
  Any non-matching roll resets the relevant streak.

  Example:
    Roll 20 → streak_20 = 1
    Roll 15 → streak_20 = 0
    Roll 20 → streak_20 = 1
    Roll 20 → streak_20 = 2
    Roll 20 → streak_20 = 3 → LUK +1, reset to 0

THE PROBABILITY OF CHANGE:
  Triple 20: (1/20)³ = 1/8,000 = 0.0125%
  Triple 1:  (1/20)³ = 1/8,000 = 0.0125%

  At ~50 rolls per session and ~50 sessions per year:
  Expected time to triple 20: ~3.2 years

================================================================================
THE SPIRAL
================================================================================

Luck creates momentum.

DOWNWARD SPIRAL:
  LUK -3 → more failures → more 1s → more triple 1 chances → LUK -4

UPWARD SPIRAL:
  LUK +3 → more successes → more 20s → more triple 20 chances → LUK +4

This is intentional. The universe picks favorites. TDGS encodes that truth.

================================================================================
LUCK AND INITIATIVE
================================================================================

Luck serves as a TIEBREAKER for initiative, NOT a modifier.

  Physical contests: REF → LUK → d2
  Magical contests:  LUK → d2

A character with REF 6 and LUK +10 loses initiative to REF 7 and LUK -10.
The cursed character acts first. The cursed character probably misses.

Luck does not make you faster.
It makes your actions bend probability when they occur.

================================================================================
LUCK AND MAGNITUDE
================================================================================

┌─────────────────────────────────────────────────────────────────────────────┐
│  Luck affects RESOLUTION only.                                              │
│  Luck NEVER affects MAGNITUDE.                                              │
└─────────────────────────────────────────────────────────────────────────────┘

A LUK +10 character hits almost every time.
They do NOT hit harder.

Damage, duration, area, quantity—all magnitude values—are unaffected by Luck.
Fortune determines WHETHER something happens, not HOW MUCH happens.

================================================================================
IMPLEMENTATION GUIDANCE FOR AI SYSTEMS
================================================================================

RESOLUTION WITH LUCK:
  1. Calculate normal resolution: d20 + delta + modifiers vs 11
  2. If LUK < 0: Apply ceiling (must roll >= 11 + |LUK| to succeed)
  3. If LUK > 0: Apply floor (only rolls <= 11 - LUK fail)
  4. If LUK = +10 and roll = 1: Allow one reroll
  5. Natural 1 always fails (except LUK +10 reroll succeeds on non-1)
  6. Natural 20 always succeeds

DETERMINING EFFECTIVE SUCCESS RATE:
  function getSuccessRate(delta, modifiers, luck):
    // Normal calculation
    needed = 11 - delta - modifiers
    normalRate = clamp((21 - needed) * 5, 5, 95)
    
    if luck < 0:
      ceiling = (21 - (11 + abs(luck))) * 5  // e.g., LUK -5 = 30%
      return min(normalRate, ceiling)
    else if luck > 0:
      floor = (21 - (11 - luck)) * 5  // e.g., LUK +5 = 75%
      if luck == 10:
        floor = 99.75  // reroll rule
      return max(normalRate, floor)
    else:
      return normalRate

LUCK PROGRESSION TRACKING:
  struct LuckTracker {
    streak_ones: int = 0
    streak_twenties: int = 0
  }
  
  function processRoll(roll, tracker, character):
    if roll == 20:
      tracker.streak_ones = 0
      tracker.streak_twenties += 1
      if tracker.streak_twenties >= 3:
        character.luck += 1
        tracker.streak_twenties = 0
    else if roll == 1:
      tracker.streak_twenties = 0
      tracker.streak_ones += 1
      if tracker.streak_ones >= 3:
        character.luck -= 1
        tracker.streak_ones = 0
    else:
      tracker.streak_ones = 0
      tracker.streak_twenties = 0

================================================================================
WHY LUCK IS UNFAIR
================================================================================

TDGS makes a deliberate design choice: Luck is unfair because luck is unfair.

Real fortune does not care about balance. It does not distribute evenly.
It does not reward effort. Some people are simply luckier than others.
And that luck compounds.

TDGS does not pretend otherwise.

THE SAFEGUARDS:
  - Rarity at creation: 90% of characters start at LUK 0
  - Difficult progression: Triple 20s/1s are rare events
  - GM control over items: Luck-modifying items are explicitly rare
  - Narrative territory guidance: |LUK| >= 3 is flagged as exceptional

Most play occurs in the -2 to +2 range, where Luck nudges outcomes
without dominating them.

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

All luck-related mechanics in TDGS conform to the rules established here.
Changes should be rare, deliberate, and backward compatible.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/luck
AI-optimized:   https://tacticaldice.com/docs/tdgs/luckforai

================================================================================
END OF DOCUMENT
================================================================================`;

// Styles matching entitiesforai format
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
    borderBottom: '1px solid rgba(123, 63, 228, 0.3)',
  },
  nav: {
    marginBottom: 30,
  },
  navLink: {
    display: 'inline-flex',
    alignItems: 'center',
    gap: 8,
    color: '#a78bfa',
    textDecoration: 'none',
    fontSize: 13,
    padding: '8px 16px',
    background: 'rgba(123, 63, 228, 0.15)',
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
    color: '#c4b5fd',
    marginBottom: 16,
    paddingBottom: 8,
    borderBottom: '1px solid rgba(123, 63, 228, 0.2)',
  },
  codeBlock: {
    background: 'rgba(0, 0, 0, 0.4)',
    borderRadius: 8,
    padding: 20,
    marginBottom: 20,
    overflow: 'auto',
    border: '1px solid rgba(123, 63, 228, 0.2)',
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
    borderBottom: '1px solid rgba(123, 63, 228, 0.3)',
    color: '#c4b5fd',
    fontWeight: 600,
  },
  td: {
    padding: '10px 14px',
    borderBottom: '1px solid rgba(255, 255, 255, 0.05)',
    color: '#cbd5e1',
  },
};

export default function TDGSLuckForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="luck" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS LUCK - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 4 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_LUCK_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## LUCK SCALE</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>LUK Range</th>
                <th style={styles.th}>Category</th>
                <th style={styles.th}>Effect</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>-10 to -3</td><td style={styles.td}>Narrative (Cursed)</td><td style={styles.td}>Max success 5-40%</td></tr>
              <tr><td style={styles.td}>-2 to -1</td><td style={styles.td}>Play (Unlucky)</td><td style={styles.td}>Max success 45-50%</td></tr>
              <tr><td style={styles.td}>0</td><td style={styles.td}>Neutral</td><td style={styles.td}>Normal resolution</td></tr>
              <tr><td style={styles.td}>+1 to +2</td><td style={styles.td}>Play (Lucky)</td><td style={styles.td}>Min success 55-60%</td></tr>
              <tr><td style={styles.td}>+3 to +10</td><td style={styles.td}>Narrative (Blessed)</td><td style={styles.td}>Min success 65-99.75%</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## CORE RULES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Concept</th>
                <th style={styles.th}>Rule</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Negative Luck</td><td style={styles.td}>Sets ceiling: Must roll &gt;= 11 + |LUK| to succeed</td></tr>
              <tr><td style={styles.td}>Positive Luck</td><td style={styles.td}>Sets floor: Only rolls &lt;= 11 - LUK fail</td></tr>
              <tr><td style={styles.td}>LUK +10 Special</td><td style={styles.td}>May reroll natural 1 once (99.75% success)</td></tr>
              <tr><td style={styles.td}>Natural 1</td><td style={styles.td}>Always fails (except LUK +10 reroll)</td></tr>
              <tr><td style={styles.td}>Natural 20</td><td style={styles.td}>Always succeeds</td></tr>
              <tr><td style={styles.td}>Luck vs Magnitude</td><td style={styles.td}>Luck affects resolution ONLY, never magnitude</td></tr>
              <tr><td style={styles.td}>Character Creation</td><td style={styles.td}>d20: 1=-1 LUK, 2-19=0 LUK, 20=+1 LUK</td></tr>
              <tr><td style={styles.td}>Luck Increase</td><td style={styles.td}>Three natural 20s in a row = +1 LUK</td></tr>
              <tr><td style={styles.td}>Luck Decrease</td><td style={styles.td}>Three natural 1s in a row = -1 LUK</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## NEGATIVE LUCK CEILING TABLE</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>LUK</th>
                <th style={styles.th}>Min Roll</th>
                <th style={styles.th}>Max Success</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>-1</td><td style={styles.td}>12+</td><td style={styles.td}>45%</td></tr>
              <tr><td style={styles.td}>-2</td><td style={styles.td}>13+</td><td style={styles.td}>40%</td></tr>
              <tr><td style={styles.td}>-3</td><td style={styles.td}>14+</td><td style={styles.td}>35%</td></tr>
              <tr><td style={styles.td}>-4</td><td style={styles.td}>15+</td><td style={styles.td}>30%</td></tr>
              <tr><td style={styles.td}>-5</td><td style={styles.td}>16+</td><td style={styles.td}>25%</td></tr>
              <tr><td style={styles.td}>-6</td><td style={styles.td}>17+</td><td style={styles.td}>20%</td></tr>
              <tr><td style={styles.td}>-7</td><td style={styles.td}>18+</td><td style={styles.td}>15%</td></tr>
              <tr><td style={styles.td}>-8</td><td style={styles.td}>19+</td><td style={styles.td}>10%</td></tr>
              <tr><td style={styles.td}>-9</td><td style={styles.td}>20</td><td style={styles.td}>5%</td></tr>
              <tr><td style={styles.td}>-10</td><td style={styles.td}>20</td><td style={styles.td}>5%</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## POSITIVE LUCK FLOOR TABLE</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>LUK</th>
                <th style={styles.th}>Max Fail Roll</th>
                <th style={styles.th}>Min Success</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>+1</td><td style={styles.td}>10</td><td style={styles.td}>55%</td></tr>
              <tr><td style={styles.td}>+2</td><td style={styles.td}>9</td><td style={styles.td}>60%</td></tr>
              <tr><td style={styles.td}>+3</td><td style={styles.td}>8</td><td style={styles.td}>65%</td></tr>
              <tr><td style={styles.td}>+4</td><td style={styles.td}>7</td><td style={styles.td}>70%</td></tr>
              <tr><td style={styles.td}>+5</td><td style={styles.td}>6</td><td style={styles.td}>75%</td></tr>
              <tr><td style={styles.td}>+6</td><td style={styles.td}>5</td><td style={styles.td}>80%</td></tr>
              <tr><td style={styles.td}>+7</td><td style={styles.td}>4</td><td style={styles.td}>85%</td></tr>
              <tr><td style={styles.td}>+8</td><td style={styles.td}>3</td><td style={styles.td}>90%</td></tr>
              <tr><td style={styles.td}>+9</td><td style={styles.td}>2</td><td style={styles.td}>95%</td></tr>
              <tr><td style={styles.td}>+10</td><td style={styles.td}>1 (reroll)</td><td style={styles.td}>99.75%</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(123, 63, 228, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/luck"
            style={{
              ...styles.navLink,
              background: 'rgba(123, 63, 228, 0.25)',
            }}
          >
            View Human-Readable Version →
          </Link>
        </footer>
      </div>
    </div>
  );
