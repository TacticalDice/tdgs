# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 3
# Title: Resolution Mechanics
# Version: 1.0
# Purpose: AI-readable specification for action resolution
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

This document defines how uncertain actions are resolved in TDGS.
It establishes the core formula, stat pairings, and critical outcome rules.

This document assumes LUK = 0. Luck modifications are defined in Document 4.

================================================================================
THE CORE FORMULA
================================================================================

┌─────────────────────────────────────────────────────────────────────────────┐
│  d20 + (Your Stat − Their Stat) + Modifiers >= 11                           │
└─────────────────────────────────────────────────────────────────────────────┘

COMPONENTS:
  - d20: Resolution die
  - Your Stat: Relevant stat for your action
  - Their Stat: Relevant stat for their defense (or virtual stat)
  - Modifiers: Equipment, temporary, situational bonuses
  - 11: Fixed threshold. ALWAYS 11. Never changes.

PROPERTIES:
  - Equal stats, zero modifiers = 50% success
  - Each point of delta = 5% success rate change
  - Bounded between 5% (nat 20 only) and 95% (nat 1 only fails)

================================================================================
NATURAL 1 AND NATURAL 20
================================================================================

┌─────────────────────────────────────────────────────────────────────────────┐
│  Natural 1 ALWAYS fails.                                                    │
│  Natural 20 ALWAYS succeeds.                                                │
│  Regardless of math. No exceptions.                                         │
└─────────────────────────────────────────────────────────────────────────────┘

================================================================================
STAT PAIRINGS
================================================================================

Each action type uses ONE attacking stat versus ONE defending stat.

PHYSICAL ACTIONS:
  Action              | Attacker | Defender
  --------------------|----------|----------
  Melee strike        | STR      | REF
  Ranged attack       | DEX      | REF
  Grapple / shove     | STR      | STR
  Chase / flee        | MOV      | MOV
  Hide / stealth      | DEX      | WIS
  Spot hidden         | WIS      | DEX

MENTAL ACTIONS:
  Action              | Attacker | Defender
  --------------------|----------|----------
  Persuade/intimidate | CHA      | WIS
  Deceive / bluff     | CHA      | INT
  Resist fear/charm   | —        | WIS

MAGICAL ACTIONS:
  Action              | Attacker | Defender
  --------------------|----------|----------
  Arcane (learned)    | INT      | WIS
  Divine (intuitive)  | WIS      | WIS

RESISTANCE ACTIONS:
  Action              | Defender
  --------------------|----------
  Resist poison/pain  | CON
  Endurance contest   | CON vs CON

KNOWLEDGE ACTIONS:
  Action              | Stat | Against
  --------------------|------|------------------
  Recall knowledge    | INT  | Virtual Difficulty

EXTENSIBILITY:
  These pairings are defaults. GMs may create additional pairings.
  The formula remains constant. Only the stats change.

================================================================================
NON-OPPOSED ACTIONS
================================================================================

When no defender exists, GM assigns a VIRTUAL STAT representing difficulty.

FORMULA:
  d20 + (Your Stat − Virtual Stat) + Modifiers >= 11

VIRTUAL STAT EXAMPLES:
  Task                | Stat | Virtual | Meaning
  --------------------|------|---------|------------------
  Simple lock         | DEX  | 5       | Trivial
  Quality lock        | DEX  | 10      | Professional
  Master lock         | DEX  | 15      | Expert
  Rough wall climb    | STR  | 6       | Easy
  Sheer cliff climb   | STR  | 12      | Demanding
  Common lore         | INT  | 4       | Widely known
  Obscure lore        | INT  | 14      | Specialist

FUTURE: Items may have inherent difficulty stats (deferred to item system).

================================================================================
CONTESTED RESOLUTION
================================================================================

When two entities directly oppose each other:

ASYMMETRIC CONTEST (attacker vs defender):
  Only attacker rolls. Defender stat creates delta.

SYMMETRIC CONTEST (both acting, e.g., grapple vs grapple):
  Both entities roll:
    Entity A: d20 + (A's Stat − B's Stat) + A's Modifiers
    Entity B: d20 + (B's Stat − A's Stat) + B's Modifiers
  Higher total succeeds. Lower total fails.

================================================================================
CONTESTED TIES
================================================================================

When contested rolls produce the same total:

PHYSICAL CONTESTS (grapple, melee, chase):
  Tiebreaker: REF → LUK → d2
  Higher REF wins. If equal, higher LUK. If equal, coin flip.

MAGICAL CONTESTS (spell vs spell, magical opposition):
  Tiebreaker: LUK → d2
  "Magic is inherently chaotic. Fortune favors whom it will, when it will."

================================================================================
CRITICAL OUTCOMES
================================================================================

Criticals occur ONLY on natural 1 or natural 20.
Resolution and magnitude are ALWAYS separate.

CRITICAL SUCCESS (Natural 20):
  Resolution: Automatic success
  Magnitude: Roll d4
    1 = Normal success
    2 = Minor bonus
    3 = Notable bonus
    4 = Major bonus

CRITICAL FAILURE (Natural 1):
  Resolution: Automatic failure
  Magnitude: Roll d4
    1 = Normal failure
    2 = Minor consequence
    3 = Notable consequence
    4 = Major consequence

CRITICAL MAGNITUDE DETAILS:
  See Doc 1 (Dice) for detailed examples:
    - Damage scaling (+25% to +100%)
    - Duration extensions
    - Area/target increases
    - Healing multipliers
  
  Content chooses interpretation per effect type.
  Reference: /docs/tdgs/dice#critical-effect-examples

┌─────────────────────────────────────────────────────────────────────────────┐
│  d20 = Resolution (did it happen?)                                          │
│  d4  = Critical magnitude (how extreme?)                                    │
│  These are ALWAYS separate rolls.                                           │
└─────────────────────────────────────────────────────────────────────────────┘

Specific effects defined by relevant system (combat, skills, GM discretion).

================================================================================
MODIFIERS
================================================================================

FORMULA:
  Final Roll = d20 + (Stat Delta) + Equipment + Temporary + Situational

MODIFIER SOURCES:
  Source      | Type                    | Example
  ------------|-------------------------|---------------------------
  Stat Delta  | Your stat − Their stat  | DEX 8 vs REF 5 = +3
  Equipment   | Weapons, armor, tools   | +2 sword, +1 lockpicks
  Temporary   | Buffs, debuffs          | Potion +2, Blinded −4
  Situational | Positioning, environment| High ground +2, darkness −2

EQUIPMENT DICE (Optional):
  Quality     | Modifier
  ------------|----------
  Mundane     | +1 or +2 (flat)
  Quality     | +d4
  Exceptional | +d6
  Legendary   | +d8 or +d12

================================================================================
MULTI-ENTITY SITUATIONS
================================================================================

Numeric advantage is resolved through ACTION ECONOMY, not roll bonuses.

PRINCIPLE:
  Six attackers vs one defender = six separate resolution rolls.
  NOT one enhanced roll. Each roll stands alone.

POSITIONAL MODIFIERS:
  Situation                              | Modifier
  ---------------------------------------|----------
  Flanking (2 attackers, opposite sides) | +2 to attackers
  Surrounded (3+ attackers, no escape)   | +4 to attackers

  These are situational modifiers. They stack with normal resolution.

MULTI-TARGET ACTIONS:
  Some skills allow single action to affect multiple targets.
  Resolution for multi-target actions defined in Skills system.

================================================================================
SUCCESS RATE REFERENCE TABLE
================================================================================

Delta     | Need  | Success%
----------|-------|----------
−9 worse  | 20    | 5%
−8        | 19+   | 10%
−7        | 18+   | 15%
−6        | 17+   | 20%
−5        | 16+   | 25%
−4        | 15+   | 30%
−3        | 14+   | 35%
−2        | 13+   | 40%
−1        | 12+   | 45%
0         | 11+   | 50%
+1        | 10+   | 55%
+2        | 9+    | 60%
+3        | 8+    | 65%
+4        | 7+    | 70%
+5        | 6+    | 75%
+6        | 5+    | 80%
+7        | 4+    | 85%
+8        | 3+    | 90%
+9 better | 2+    | 95%

================================================================================
DEFERRALS
================================================================================

This document does NOT define:
  - Luck modifications (Document 4)
  - Action economy (future document)
  - Combat specifics (future document)
  - Skill specifics (future document)
  - Item system (future document)
  - Critical effect details (relevant systems)

================================================================================
IMPLEMENTATION GUIDANCE FOR AI SYSTEMS
================================================================================

When resolving actions:
  1. Identify action type → select stat pairing
  2. Calculate delta: (Attacker Stat − Defender Stat)
  3. Sum modifiers: equipment + temporary + situational
  4. Roll d20
  5. If nat 1: automatic failure, roll d4 for consequence severity
  6. If nat 20: automatic success, roll d4 for bonus severity
  7. Otherwise: check if d20 + delta + modifiers >= 11

When handling ties:
  1. Identify contest type (physical or magical)
  2. Physical: compare REF → LUK → d2
  3. Magical: compare LUK → d2

When generating content:
  - Stat pairings are extensible; create new ones for setting-specific actions
  - Virtual stats for obstacles should feel like "if this were an entity"
  - The formula NEVER changes. Only the inputs change.

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

All resolution in TDGS uses this formula. Later systems build upon but do not
alter these rules.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/resolution
AI-optimized:   https://tacticaldice.com/docs/tdgs/resolutionforai

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

export default function TDGSResolutionForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="resolution" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS RESOLUTION - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 3 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_RESOLUTION_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## QUICK REFERENCE SUMMARY</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Concept</th>
                <th style={styles.th}>Rule</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Core Formula</td><td style={styles.td}>d20 + (Your Stat − Their Stat) + Modifiers &gt;= 11</td></tr>
              <tr><td style={styles.td}>Threshold</td><td style={styles.td}>Always 11. Never changes.</td></tr>
              <tr><td style={styles.td}>Natural 1</td><td style={styles.td}>Always fails, regardless of math</td></tr>
              <tr><td style={styles.td}>Natural 20</td><td style={styles.td}>Always succeeds, regardless of math</td></tr>
              <tr><td style={styles.td}>Critical Magnitude</td><td style={styles.td}>Roll d4 (1=normal, 2=minor, 3=notable, 4=major)</td></tr>
              <tr><td style={styles.td}>Equal Stats</td><td style={styles.td}>50% success rate</td></tr>
              <tr><td style={styles.td}>Physical Tie</td><td style={styles.td}>REF → LUK → d2</td></tr>
              <tr><td style={styles.td}>Magical Tie</td><td style={styles.td}>LUK → d2</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## COMMON STAT PAIRINGS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Action</th>
                <th style={styles.th}>Attacker</th>
                <th style={styles.th}>Defender</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Melee Attack</td><td style={styles.td}>STR</td><td style={styles.td}>REF</td></tr>
              <tr><td style={styles.td}>Ranged Attack</td><td style={styles.td}>DEX</td><td style={styles.td}>REF</td></tr>
              <tr><td style={styles.td}>Grapple/Shove</td><td style={styles.td}>STR</td><td style={styles.td}>STR</td></tr>
              <tr><td style={styles.td}>Chase/Flee</td><td style={styles.td}>MOV</td><td style={styles.td}>MOV</td></tr>
              <tr><td style={styles.td}>Hide/Stealth</td><td style={styles.td}>DEX</td><td style={styles.td}>WIS</td></tr>
              <tr><td style={styles.td}>Persuade/Intimidate</td><td style={styles.td}>CHA</td><td style={styles.td}>WIS</td></tr>
              <tr><td style={styles.td}>Deceive/Bluff</td><td style={styles.td}>CHA</td><td style={styles.td}>INT</td></tr>
              <tr><td style={styles.td}>Arcane Magic</td><td style={styles.td}>INT</td><td style={styles.td}>WIS</td></tr>
              <tr><td style={styles.td}>Divine Magic</td><td style={styles.td}>WIS</td><td style={styles.td}>WIS</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(123, 63, 228, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/resolution"
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
