# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 6
# Title: Action Economy
# Version: 1.0
# Purpose: AI-readable specification for timing, turns, and action structure
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

Action Economy defines WHEN actions happen.
Action Taxonomy (Doc 5) defines WHAT actions exist.

HIERARCHY:
  SCENE -> contains -> ROUNDS -> contains -> PHASES -> contains -> TURNS

================================================================================
SCENE
================================================================================

DEFINITION: A continuous tactical situation (combat, chase, negotiation)

SCENE ENDS WHEN:
  - Combat concludes (victory, defeat, surrender, escape)
  - Chase ends (caught, escaped, abandoned)
  - Negotiation finishes (agreement, breakdown, interruption)

ON SCENE END:
  - Armor durability resets
  - Per-scene abilities reset
  - Entities catch breath, reset stance

================================================================================
ROUND
================================================================================

DEFINITION: One complete cycle where every entity acts

STRUCTURE:
  ROUND
  |-- INSTANT PHASE (all Instants resolve)
  \`-- ACTION PHASE (all entities act in initiative order)

Rounds repeat until Scene ends.

================================================================================
INITIATIVE
================================================================================

ORDER: REF -> LUK -> d2

1. Higher REF acts first
2. If REF tied: higher LUK acts first
3. If both tied: flip d2

INITIATIVE IS NOT ROLLED. Stats determine order.

RATIONALE: REF 10 IS faster than REF 8. Not "probably faster." Faster.

MULTI-ENTITY TIES (3+ entities tied after REF and LUK):
  1. All tied entities flip d2 simultaneously
  2. Higher results act before lower results
  3. Remaining ties flip again
  4. Repeat until fully resolved

PERSISTENCE: Order determined once at Scene start, persists unless REF/LUK changes.

================================================================================
INSTANT PHASE
================================================================================

TIMING: Start of each round, before Action Phase

INSTANTS ARE:
  - Pre-emptive abilities
  - Granted by Skills, Spells, Traits
  - Declared at round start
  - Resolved before any normal actions

INSTANT ORDERING: Instant's REF -> Entity's LUK -> d2
  - Each Instant ability has its own REF value
  - Higher REF Instants resolve first
  - Ties broken by declaring entity's LUK, then d2

EXAMPLE:
  Fighter: "Battle Cry" (Instant REF 8)
  Rogue: "Quick Draw" (Instant REF 12)
  Wizard: "Premonition" (Instant REF 5)
  
  Order: Quick Draw (12), Battle Cry (8), Premonition (5)

================================================================================
INSTANT REF SOURCE
================================================================================

Instant abilities SHOULD define their own REF value.

Example:
  Battle Cry (Instant)
  Instant REF: 8
  Effect: Allies gain +2 to next attack

If Instant REF not defined: Default to entity's REF

RATIONALE:
  - Some abilities are inherently fast/slow
  - "Flash Step" is fast because it IS fast
  - Allows predictable ordering independent of user
  - Content creator controls when ability fires in Instant Phase

ORDERING REMINDER:
  1. Higher Instant REF resolves first
  2. Tie: Entity's LUK
  3. Still tied: d2

================================================================================
INSTANTS VS INTERRUPTS
================================================================================

| Property     | Instants              | Interrupts                |
|--------------|-----------------------|---------------------------|
| Timing       | Round start           | Response to trigger       |
| Nature       | Pre-emptive           | Reactive                  |
| Declaration  | Before Action Phase   | When trigger occurs       |
| Ordering     | By Instant's REF      | Immediate when triggered  |
| Limits       | Per ability           | Per ability               |

================================================================================
ACTION PHASE
================================================================================

TIMING: After Instant Phase

ENTITIES ACT: In initiative order (REF -> LUK -> d2)

YOUR TURN:
  - 1 ACTION (use or lose)
  - 1 STEP (free, adjacent, choose timing)
  - Unlimited FREE ACTIONS (simple interactions)

STEP TIMING:
  VALID: Step then Action, OR Action then Step
  INVALID: Step, Action, Step (only one Step)

UNUSED ACTIONS: Lost. No banking. No conversion.

================================================================================
ACTION ANATOMY
================================================================================

When taking an Action:

  1. DECLARE: State action and target
  2. INTERRUPT CHECK: Opponents may use Interrupts
  3. RESOLUTION: d20 + modifiers vs threshold
  4. MAGNITUDE: If success, determine how much

This applies to ALL actions: attacks, spells, social, etc.

================================================================================
INTERRUPTS
================================================================================

DEFINITION: Reactive abilities that fire in response to triggers

INTERRUPTS ARE:
  - Granted by Skills, Spells, Traits
  - Triggered by specific conditions
  - Resolved immediately when triggered

EXAMPLES:
  - Parry: When attacked in melee, deflect
  - Counterspell: When spell cast, attempt to negate
  - Opportunity Attack: When enemy moves away, strike
  - Dodge Roll: When targeted, evade

NO FREE INTERRUPTS:
  - Entities without relevant abilities have no Interrupts
  - Base defense is REF (passive, no roll)
  - Active defense requires learned Skills

INTERRUPT LIMITS:
  Each ability specifies its limit:
  - Per round: Resets each round
  - Per scene: Resets when Scene ends
  - Per day: Resets after long rest

  Examples:
    Parry (Lv1): 1/round
    Parry (Lv5): 2/round
    Counterspell: 1/scene
    Divine Intervention: 1/day

NO BASE POOL: Limits defined entirely by abilities.

INTERRUPT TIMING:
  Resolves IMMEDIATELY, before triggering action completes.
  
  Example (Parry):
    1. Enemy declares Melee Attack
    2. You declare Parry
    3. Parry resolves (you roll)
    4. Success: attack deflected
    5. Failure: attack continues

INTERRUPT VS INTERRUPT:
  Resolve in order declared (responder first).
  
  Example (Counterspell chain):
    1. Wizard A casts Fireball
    2. Wizard B uses Counterspell
    3. Wizard A uses Counter-Counterspell
    4. Resolve: Counter-Counterspell, then Counterspell, then Fireball

================================================================================
READIED ACTIONS
================================================================================

Ready (Action) converts your Action into a conditional Interrupt.

PROCESS:
  1. On your turn: Declare Ready (costs Action)
  2. State trigger and held action
  3. If trigger occurs before next turn:
     - Held action fires as Interrupt
     - Resolves immediately, even mid-action
  4. If no trigger: Action lost

PURPOSE: Primary way for characters WITHOUT Interrupt skills to react.

================================================================================
DELAY
================================================================================

Delay (Free) moves you later in initiative.

PROCESS:
  1. When your turn comes: Declare Delay
  2. Specify when to act ("after wizard", "at end")
  3. Move to that position THIS ROUND
  4. Next round: Reset to natural REF order

LIMIT: Cannot delay past start of next round.

================================================================================
SIMULTANEOUS EVENTS
================================================================================

TDGS resolves all events in order. No true simultaneity.

SAME PHASE, DIFFERENT REF:
  Higher REF resolves first.

SAME PHASE, SAME REF:
  1. Compare LUK
  2. If tied: flip d2

MUTUAL DESTRUCTION:
  If both events would prevent the other, resolve in REF order.
  Faster entity's action completes first.
  
  If REF and LUK identical: flip d2.
  Winner's action completes. Loser may not get to complete theirs.

================================================================================
SUMMARY: TIMING TYPES
================================================================================

Type     | When        | Limit        | Source
---------|-------------|--------------|------------------
Action   | Your turn   | 1/turn       | Everyone
Free     | Your turn   | Varies       | Everyone
Step     | Your turn   | 1/turn       | Everyone
Instant  | Round start | Per ability  | Skills/Abilities
Interrupt| Response    | Per ability  | Skills/Abilities
Readied  | On trigger  | 1 (Ready)    | Ready action

================================================================================
SUMMARY: FULL STRUCTURE
================================================================================

SCENE (combat, chase, negotiation)
|
\`-- ROUND (repeats until Scene ends)
    |
    |-- INSTANT PHASE
    |   \`-- All Instants resolve (by Instant REF -> LUK -> d2)
    |
    \`-- ACTION PHASE
        \`-- Each entity in initiative order (by Entity REF -> LUK -> d2)
            |
            \`-- TURN
                |-- Step (free, once, choose timing)
                |-- Action (one, use or lose)
                |   |-- Declare
                |   |-- Interrupt check
                |   |-- Resolution
                |   \`-- Magnitude
                \`-- Free actions (unlimited)
|
SCENE ENDS -> Effects reset (armor, per-scene abilities)

================================================================================
IMPLEMENTATION NOTES FOR AI SYSTEMS
================================================================================

INITIATIVE CALCULATION:
  entities.sort(by: REF desc, then LUK desc, then random)

INTERRUPT PROCESSING:
  on_action_declared(action):
    for each entity with relevant Interrupt:
      if entity.wants_to_interrupt(action):
        if entity.can_use_interrupt():
          resolve_interrupt()
          decrement_interrupt_uses()
    resolve_original_action()

INSTANT PROCESSING:
  at_round_start():
    collect_declared_instants()
    instants.sort(by: instant.REF desc, then entity.LUK desc, then random)
    for instant in instants:
      resolve_instant()

SCENE MANAGEMENT:
  on_scene_end():
    for entity in entities:
      reset_armor_durability()
      reset_per_scene_abilities()

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

All timing, turn structure, and action sequencing in TDGS conform to this document.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/actioneconomy
AI-optimized:   https://tacticaldice.com/docs/tdgs/actioneconomyforai

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

export default function TDGSActionEconomyForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="actioneconomy" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS ACTION ECONOMY - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 6 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_ACTION_ECONOMY_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## INITIATIVE ORDER</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Priority</th>
                <th style={styles.th}>Comparison</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>1st</td><td style={styles.td}>Higher REF acts first</td></tr>
              <tr><td style={styles.td}>2nd</td><td style={styles.td}>If REF tied: Higher LUK acts first</td></tr>
              <tr><td style={styles.td}>3rd</td><td style={styles.td}>If both tied: Flip d2 (coin flip)</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## YOUR TURN</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Component</th>
                <th style={styles.th}>Limit</th>
                <th style={styles.th}>Notes</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Action</td><td style={styles.td}>1</td><td style={styles.td}>Use it or lose it</td></tr>
              <tr><td style={styles.td}>Step</td><td style={styles.td}>1</td><td style={styles.td}>Free, choose timing</td></tr>
              <tr><td style={styles.td}>Free Actions</td><td style={styles.td}>Unlimited</td><td style={styles.td}>Simple interactions</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## TIMING TYPES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Type</th>
                <th style={styles.th}>When</th>
                <th style={styles.th}>Source</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Action</td><td style={styles.td}>Your turn</td><td style={styles.td}>Everyone</td></tr>
              <tr><td style={styles.td}>Free</td><td style={styles.td}>Your turn</td><td style={styles.td}>Everyone</td></tr>
              <tr><td style={styles.td}>Step</td><td style={styles.td}>Your turn</td><td style={styles.td}>Everyone</td></tr>
              <tr><td style={styles.td}>Instant</td><td style={styles.td}>Round start</td><td style={styles.td}>Skills/Abilities</td></tr>
              <tr><td style={styles.td}>Interrupt</td><td style={styles.td}>Response</td><td style={styles.td}>Skills/Abilities</td></tr>
              <tr><td style={styles.td}>Readied</td><td style={styles.td}>On trigger</td><td style={styles.td}>Ready action</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## INSTANTS VS INTERRUPTS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Property</th>
                <th style={styles.th}>Instants</th>
                <th style={styles.th}>Interrupts</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Timing</td><td style={styles.td}>Round start</td><td style={styles.td}>Response to trigger</td></tr>
              <tr><td style={styles.td}>Nature</td><td style={styles.td}>Pre-emptive</td><td style={styles.td}>Reactive</td></tr>
              <tr><td style={styles.td}>Ordering</td><td style={styles.td}>By Instant REF</td><td style={styles.td}>Immediate</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(123, 63, 228, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/actioneconomy"
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
