# Title: Action Taxonomy
# Version: 1.0
# Purpose: AI-readable specification for base actions
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

An action is any discrete thing an entity does that requires resolution.

RESOLUTION FORMULA (unchanged):
  d20 + (Your Stat - Opposing Stat) + Modifiers >= 11

ACTION PROPERTIES:
  - TYPE: Physical, Mental, Magical, Utility, Defensive
  - STATS: Your Stat vs Their Stat, or Your Stat vs Difficulty
  - COST: Action, Free, or Interrupt

================================================================================
ACTION COSTS
================================================================================

ACTION
  - Default cost
  - 1 per turn
  - Consumes primary activity

FREE
  - No cost
  - Usually limited (once per turn, no resolution, etc.)

INTERRUPT
  - Fires in response to something else
  - Never free by default
  - Requires: Skill, Ability, Spell, or Readied action

================================================================================
DIFFICULTY AS VIRTUAL STAT
================================================================================

When no defender exists, GM assigns Difficulty as virtual stat.

STANDARD SCALE:
  Challenge      | Virtual Stat | Success @ Stat 10
  ---------------|--------------|------------------
  Trivial        | 0            | 95%
  Easy           | 5            | 70%
  Moderate       | 10           | 50%
  Hard           | 15           | 30%
  Very Hard      | 20           | 5% (nat 20 only)
  Legendary      | 25+          | 5% (nat 20 only)

OBJECT EXAMPLES:
  - Simple lock: DEX 5
  - Quality lock: DEX 10
  - Masterwork lock: DEX 15
  - Legendary vault: DEX 25

================================================================================
PHYSICAL ACTIONS
================================================================================

Action         | ATK Stat | DEF Stat | Cost
---------------|----------|----------|------------------
Melee Attack   | STR      | REF      | Action
Ranged Attack  | DEX      | REF      | Action
Grapple        | STR      | STR      | Action
Shove          | STR      | STR      | Action
Hide           | DEX      | WIS      | Action
Search         | WIS      | DEX      | Action
Chase          | MOV      | MOV      | Action
Flee           | MOV      | MOV      | Action
Move           | —        | —        | Action
Step           | —        | —        | Free (once/turn)

DEFINITIONS:
  Melee Attack: Strike adjacent target. STR vs REF.
  Ranged Attack: Strike distant target. DEX vs REF.
  Grapple: Grab and restrain. STR vs STR. Success = grappled.
  Shove: Push away or knock down. STR vs STR.
  Hide: Become unseen. DEX vs WIS of observers.
  Search: Find hidden things. WIS vs DEX of hidden (or Difficulty).
  Chase: Pursue fleeing target. MOV vs MOV.
  Flee: Escape pursuer. MOV vs MOV.
  Move: Relocate any distance. Costs Action.
  Step: Relocate adjacent. Free, once per turn.

================================================================================
MENTAL ACTIONS
================================================================================

Action           | ATK Stat | DEF Stat   | Cost
-----------------|----------|------------|--------
Persuade         | CHA      | WIS        | Action
Intimidate       | CHA      | WIS        | Action
Deceive          | CHA      | INT        | Action
Insight          | WIS      | CHA        | Action
Recall Knowledge | INT      | Difficulty | Action
Concentrate      | —        | —          | Action

RECALL KNOWLEDGE DIFFICULTY:
  Knowledge Type | Virtual Stat
  ---------------|-------------
  Common         | 5
  Uncommon       | 10
  Rare           | 15
  Legendary      | 20

CONCENTRATE: Maintain ongoing effect requiring concentration.

================================================================================
CONCENTRATE MECHANICS
================================================================================

BREAKING CONCENTRATION:

Trigger: Taking damage while concentrating
Formula: d20 + (CON - Damage Taken) >= 11
Success: Concentration maintained
Failure: Effect ends immediately

- Nat 1: Always fails
- Nat 20: Always succeeds
- Luck: Applies normally

EXAMPLE (CON 10):
  Damage 5:  75% success (+5 delta, need 6+)
  Damage 10: 50% success (+0 delta, need 11+)
  Damage 15: 25% success (-5 delta, need 16+)
  Damage 20: 5% success (-10 delta, nat 20 only)

VOLUNTARY END:
  - Free action
  - No roll required
  - End your own concentration at any time

MULTIPLE CONCENTRATIONS:
  Default: One concentration at a time
  New concentration ends previous
  Abilities MAY override this limit

================================================================================
MAGICAL ACTIONS
================================================================================

Action              | ATK Stat | DEF Stat        | Cost
--------------------|----------|-----------------|--------
Cast Spell (Arcane) | INT      | WIS             | Action
Cast Spell (Divine) | WIS      | WIS             | Action
Dispel (Arcane)     | INT      | Caster's INT    | Action
Dispel (Divine)     | WIS      | Caster's WIS    | Action
Identify            | INT      | Difficulty      | Action

ARCANE: Learned, studied, precise. INT vs WIS.
DIVINE: Granted, intuited, purposeful. WIS vs WIS.
DISPEL: End active spell. Your stat vs original caster's stat.
IDENTIFY: Recognize magical effect. INT vs Difficulty by rarity.

IDENTIFY DIFFICULTY:
  Spell Rarity | Virtual Stat
  -------------|-------------
  Common       | 5
  Uncommon     | 10
  Rare         | 15
  Legendary    | 20

================================================================================
UTILITY ACTIONS
================================================================================

Action             | Effect                              | Cost
-------------------|-------------------------------------|------------------
Use Item           | Activate item effect                | Action
Interact (Simple)  | Open door, pull lever, pick up      | Free
Interact (Complex) | Pick lock, disable trap, machinery  | Action
Ready              | Hold action for trigger             | Action
Delay              | Act later in initiative             | Free
Help               | Grant +2 to ally's next roll        | Action

READY:
  - Declare trigger + held action
  - Trigger fires: execute as Interrupt (even mid-action)
  - No trigger: action lost

DELAY:
  - Move to later initiative position this round
  - Cannot delay past next round start
  - Resets to natural position (REF) each round

HELP:
  - +2 to one ally's next roll
  - Must occur before your next turn
  - Must be narratively plausible

================================================================================
DEFENSIVE ACTIONS
================================================================================

Action | Effect                    | Cost
-------|---------------------------|----------
Dodge  | Avoid incoming attack     | Interrupt
Block  | Absorb incoming attack    | Interrupt
Parry  | Deflect incoming attack   | Interrupt

BASE DEFENSE:
  - REF IS your defense (no roll)
  - Attackers roll against your REF
  - Everyone has this

ACTIVE DEFENSE:
  - Requires Skill, Ability, or Spell
  - Uses Interrupt
  - Dodge: Add bonus to effective REF
  - Block: Reduce damage
  - Parry: Deflect, potentially counter

NO FREE INTERRUPTS: Characters without abilities have no defensive options beyond REF.

================================================================================
TECHNOLOGY ACTIONS (OPTIONAL EXPANSION)
================================================================================

Action    | ATK Stat   | DEF Stat             | Cost
----------|------------|----------------------|--------
Hack      | INT        | INT or Difficulty    | Action
Interface | INT        | Difficulty           | Action
Scan      | WIS        | Difficulty           | Action
Repair    | INT or DEX | Difficulty           | Action
Override  | INT        | System Difficulty    | Action

INTERFACE DIFFICULTY:
  Technology       | Virtual Stat
  -----------------|-------------
  Consumer-grade   | 5
  Professional     | 10
  Military/Research| 15
  Alien/Ancient    | 20

SCAN DIFFICULTY:
  Target               | Virtual Stat
  ---------------------|-------------
  Obvious signatures   | 5
  Hidden or faint      | 10
  Shielded or encrypted| 15
  Unknown/exotic       | 20

REPAIR DIFFICULTY:
  Damage Level      | Virtual Stat
  ------------------|-------------
  Minor malfunction | 5
  Moderate damage   | 10
  Severe damage     | 15
  Catastrophic      | 20

================================================================================
PSIONIC ACTIONS (OPTIONAL EXPANSION)
================================================================================

Action      | ATK Stat | DEF Stat          | Cost
------------|----------|-------------------|--------
Mind Probe  | WIS      | WIS               | Action
Telepathy   | WIS      | WIS or willing    | Action
Telekinesis | INT      | Difficulty        | Action
Dominate    | CHA      | WIS               | Action
Psi Sense   | WIS      | Difficulty        | Action

TELEKINESIS DIFFICULTY:
  Task                           | Virtual Stat
  -------------------------------|-------------
  Light object, close            | 5
  Medium object, close           | 10
  Heavy object or medium distant | 15
  Massive or fine manipulation   | 20

TELEKINESIS AS ATTACK: INT vs target's REF

PSI SENSE DIFFICULTY:
  Target                    | Virtual Stat
  --------------------------|-------------
  Strong emotions nearby    | 5
  Specific mind you know    | 10
  Hidden or shielded minds  | 15
  Traces of past psionic use| 20

DOMINATE: Typically hostile/evil. Target aware of control.

================================================================================
EXTENDING THE TAXONOMY
================================================================================

To create new actions:
  1. Name the action
  2. Assign Action Type (Physical, Mental, Magical, Utility)
  3. Determine stat pairing (ATK vs DEF, or ATK vs Difficulty)
  4. Set cost (Action, Free with limits, Interrupt with requirements)

Formula remains: d20 + (Your Stat - Opposing Stat) + Modifiers >= 11

SETTING EXAMPLES:
  - Nautical: Navigate (WIS vs Difficulty), Command Crew (CHA vs Difficulty)
  - Intrigue: Scheme (INT vs INT), Rally (CHA vs Difficulty)
  - Horror: Resist Fear (WIS vs Difficulty), Banish (WIS vs Entity WIS)
  - Superhero: Power Stunt (varies), Monologue (CHA vs WIS)

================================================================================
SUMMARY: BY COST
================================================================================

ACTIONS (1 per turn):
  Physical: Melee Attack, Ranged Attack, Grapple, Shove, Hide, Search, Chase, Flee, Move
  Mental: Persuade, Intimidate, Deceive, Insight, Recall Knowledge, Concentrate
  Magical: Cast Spell, Dispel, Identify
  Utility: Use Item, Interact (Complex), Ready, Help
  Technology: Hack, Interface, Scan, Repair, Override
  Psionics: Mind Probe, Telepathy, Telekinesis, Dominate, Psi Sense

FREE:
  Step (once per turn)
  Interact (Simple)
  Delay
  Telepathy (willing target)

INTERRUPT (Requires Ability):
  Dodge, Block, Parry
  Readied actions (when triggered)

================================================================================
SUMMARY: BY STAT
================================================================================

STAT | ATTACKS WITH                                              | DEFENDS AGAINST
-----|-----------------------------------------------------------|------------------
STR  | Melee Attack, Grapple, Shove                              | Grapple, Shove
DEX  | Ranged Attack, Hide, Repair (precision)                   | Search
REF  | —                                                         | Melee, Ranged, TK attack
CON  | —                                                         | Concentration checks
MOV  | Chase, Flee                                               | Chase, Flee
INT  | Cast(Arc), Dispel(Arc), Identify, Recall, Hack, Interface,| Deceive, Hack (defended)
     | Repair (understanding), Override, Telekinesis             |
WIS  | Search, Cast(Div), Dispel(Div), Insight, Scan,            | Persuade, Intimidate,
     | Mind Probe, Telepathy, Psi Sense                          | Cast, Mind Probe, Telepathy, Dominate
CHA  | Persuade, Intimidate, Deceive, Dominate                   | Insight
LUK  | (Tiebreaker only)                                         | (Tiebreaker only)

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

All actions in TDGS either appear in this document or extend from it.
Skills, Abilities, Spells, and Traits may modify or create new actions.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/actions
AI-optimized:   https://tacticaldice.com/docs/tdgs/actionsforai

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

export default function TDGSActionsForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="actions" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS ACTIONS - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 5 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_ACTIONS_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## ACTION COSTS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Cost Type</th>
                <th style={styles.th}>Description</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Action</td><td style={styles.td}>Default cost. 1 per turn. Consumes primary activity.</td></tr>
              <tr><td style={styles.td}>Free</td><td style={styles.td}>No cost. Usually limited (once per turn, no resolution, etc.)</td></tr>
              <tr><td style={styles.td}>Interrupt</td><td style={styles.td}>Fires in response to something else. Requires skill/ability/spell.</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## PHYSICAL ACTIONS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Action</th>
                <th style={styles.th}>ATK Stat</th>
                <th style={styles.th}>DEF Stat</th>
                <th style={styles.th}>Cost</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Melee Attack</td><td style={styles.td}>STR</td><td style={styles.td}>REF</td><td style={styles.td}>Action</td></tr>
              <tr><td style={styles.td}>Ranged Attack</td><td style={styles.td}>DEX</td><td style={styles.td}>REF</td><td style={styles.td}>Action</td></tr>
              <tr><td style={styles.td}>Grapple</td><td style={styles.td}>STR</td><td style={styles.td}>STR</td><td style={styles.td}>Action</td></tr>
              <tr><td style={styles.td}>Shove</td><td style={styles.td}>STR</td><td style={styles.td}>STR</td><td style={styles.td}>Action</td></tr>
              <tr><td style={styles.td}>Hide</td><td style={styles.td}>DEX</td><td style={styles.td}>WIS</td><td style={styles.td}>Action</td></tr>
              <tr><td style={styles.td}>Search</td><td style={styles.td}>WIS</td><td style={styles.td}>DEX</td><td style={styles.td}>Action</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## DIFFICULTY SCALE</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Challenge</th>
                <th style={styles.th}>Virtual Stat</th>
                <th style={styles.th}>Success @ Stat 10</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Trivial</td><td style={styles.td}>0</td><td style={styles.td}>95%</td></tr>
              <tr><td style={styles.td}>Easy</td><td style={styles.td}>5</td><td style={styles.td}>70%</td></tr>
              <tr><td style={styles.td}>Moderate</td><td style={styles.td}>10</td><td style={styles.td}>50%</td></tr>
              <tr><td style={styles.td}>Hard</td><td style={styles.td}>15</td><td style={styles.td}>30%</td></tr>
              <tr><td style={styles.td}>Very Hard</td><td style={styles.td}>20</td><td style={styles.td}>5%</td></tr>
              <tr><td style={styles.td}>Legendary</td><td style={styles.td}>25+</td><td style={styles.td}>5%</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(123, 63, 228, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/actions"
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
