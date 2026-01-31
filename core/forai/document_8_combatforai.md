# Title: Combat
# Version: 1.0
# Purpose: AI-readable specification for damage, armor, healing, and conditions
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
QUICK REFERENCE
================================================================================

HP_FORMULA: Apparent_CON × 5
KNOCKOUT_THRESHOLD: 5% of Max HP (rounded down)
DEATH_THRESHOLD: 0 HP
MINIMUM_DAMAGE: 1 (always)

MELEE_DAMAGE: Apparent_STR + Weapon_Damage_Bonus
RANGED_DAMAGE: Apparent_DEX + Weapon_Damage_Bonus
SPELL_DAMAGE_ARCANE: Apparent_INT + Spell_Damage_Bonus
SPELL_DAMAGE_DIVINE: Apparent_WIS + Spell_Damage_Bonus

DEFLECTION_CAP: 75%
ABLATIVE_CAP: None

ARMOR_STACK_ORDER: Ablative_First → Deflection_Second

HEALING_SHORT_REST: 25% Max HP
HEALING_LONG_REST: 100% Max HP

================================================================================
HIT POINTS
================================================================================

FORMULA:
  Max_HP = Apparent_CON × 5
  Apparent_CON = Base_CON + all_bonuses

KNOCKOUT:
  Threshold = floor(Max_HP × 0.05)
  Effect: Entity falls Unconscious
  Warning: Next hit may kill

DEATH:
  Threshold = 0 HP
  Effect: Immediate death
  No death saves, no bleeding out timers

HP_EXAMPLES:
  Entity          | Base CON | Bonuses | Apparent CON | HP
  ----------------|----------|---------|--------------|-----
  Peasant         | 8        | +0      | 8            | 40
  Soldier         | 12       | +0      | 12           | 60
  Barbarian       | 18       | +5      | 23           | 115
  Dragon          | 40       | +10     | 50           | 250
  God             | 80       | +20     | 100          | 500

IMPORTANT: HP does NOT scale with character level.
  Level 50 warrior with CON 12 = 60 HP
  Level 1 peasant with CON 12 = 60 HP

================================================================================
DAMAGE CALCULATION
================================================================================

MELEE_ATTACK:
  Damage = Apparent_STR + Weapon_Damage_Bonus
  Minimum = 1

RANGED_ATTACK:
  Damage = Apparent_DEX + Weapon_Damage_Bonus
  Minimum = 1

SPELL_ARCANE:
  Damage = Apparent_INT + Spell_Damage_Bonus
  Minimum = 1

SPELL_DIVINE:
  Damage = Apparent_WIS + Spell_Damage_Bonus
  Minimum = 1

MINIMUM_DAMAGE_RULE:
  Every successful hit deals at least 1 damage
  No attack is completely negated by armor

DAMAGE_EXAMPLES:
  Attacker   | Stat    | Weapon     | Bonus | Damage
  -----------|---------|------------|-------|--------
  Peasant    | STR 8   | Fists      | +0    | 8
  Soldier    | STR 12  | Sword      | +2    | 14
  Barbarian  | STR 18  | Greatsword | +5    | 23
  Archer     | DEX 14  | Longbow    | +3    | 17
  Wizard     | INT 15  | Fire Bolt  | +3    | 18
  Dragon     | STR 40  | Claws      | +5    | 45

================================================================================
WEAPON PROPERTIES
================================================================================

Two separate properties (Resolution and Magnitude Never Mix):

HIT_BONUS:
  - Adds to resolution roll (d20 + mods)
  - Each +1 ≈ 5% better chance to hit
  - Does NOT affect damage

DAMAGE_BONUS:
  - Adds to damage dealt on successful hit
  - Does NOT affect chance to hit

WEAPON_RANGE:
  melee:
    optimal: "Adjacent"
    extended: null
    maximum: "Adjacent"
    
  reach:
    optimal: ["Adjacent", "Near"]
    extended: null
    maximum: "Near"
    opportunity_attack_range: ["Adjacent", "Near"]
    
  thrown:
    optimal: "Near"
    extended: "Far"
    extended_penalty: -2
    maximum: "Far"
    
  ranged:
    optimal: "Far"
    extended: "Distant"
    extended_penalty: -2
    maximum: "Distant"
    
  long_range:
    optimal: "Distant"
    extended: null
    maximum: "Distant"

RANGE_BANDS:
  adjacent: "0-1 squares"
  near: "2-4 squares"
  far: "5-10 squares"
  distant: "11+ squares"

WEAPON_EXAMPLES:
  Weapon          | Hit Bonus | Damage Bonus | Range      | Notes
  ----------------|-----------|--------------|------------|------------------
  Dagger          | +0        | +2           | Melee      | Simple, concealable
  Longsword       | +1        | +4           | Melee      | Balanced, reliable
  Spear           | +0        | +3           | Reach      | Keeps enemies at distance
  Throwing Knife  | +0        | +2           | Thrown     | Expendable
  Shortbow        | +1        | +3           | Ranged     | Quick, accurate
  Longbow         | +0        | +4           | Long Range | Powerful, slow
  Chaotic Blade   | +1        | +2d4         | Melee      | Unpredictable but exciting

================================================================================
ARMOR SYSTEMS
================================================================================

TWO_TYPES:
  1. ABLATIVE - Pool-based, absorbs damage until depleted
  2. DEFLECTION - Percentage-based, reduces all damage

--------------------------------------------------------------------------------
ABLATIVE ARMOR
--------------------------------------------------------------------------------

MECHANICS:
  - Has HP pool
  - Absorbs incoming damage until pool = 0
  - Once depleted: no protection until restored/replaced

PROPERTIES:
  pool: integer (current HP)
  max_pool: integer (maximum HP)
  recharges: boolean (true = between scenes, false = destroyed when depleted)

CAP: None (divine barrier could have 10,000 HP)

EXAMPLE (Energy Shield, Pool 100):
  Hit for 30 → Shield absorbs 30, pool = 70, take 0
  Hit for 30 → Shield absorbs 30, pool = 40, take 0
  Hit for 60 → Shield absorbs 40, depleted, take 20

--------------------------------------------------------------------------------
DEFLECTION ARMOR
--------------------------------------------------------------------------------

MECHANICS:
  - Reduces damage by percentage
  - Always active while worn
  - Degrades only on crit + max magnitude

CAP: 75% maximum
  - Always take at least 25% of incoming damage
  - GM can override for setting-specific items

DEGRADATION:
  Trigger: Natural 20 + Magnitude 4
  Effect: -10% deflection for rest of scene
  Resets: Between scenes
  Probability: ~1.25% per attack

EXAMPLE (Plate Armor, 50% Deflection):
  Hit for 30 → Reduced to 15, take 15
  Hit for 100 → Reduced to 50, take 50
  Armor continues working

--------------------------------------------------------------------------------
STACKING ORDER
--------------------------------------------------------------------------------

Order: ABLATIVE FIRST → DEFLECTION SECOND → MINIMUM 1

EXAMPLE (Shield Ablative 50 + Plate Deflection 50%):
  Hit for 80:
    1. Shield absorbs 50, depleted
    2. 30 remains, Plate reduces by 50%
    3. Take 15

  Next hit for 80:
    1. Shield depleted (no ablative)
    2. Plate reduces 80 by 50%
    3. Take 40

--------------------------------------------------------------------------------
EVASION
--------------------------------------------------------------------------------

Definition: Bonus to Apparent REF for defense

ARMOR_EXAMPLES:
  Armor        | Evasion | Deflection
  -------------|---------|------------
  Light Leather| +2      | 10%
  Chain Mail   | +0      | 30%
  Full Plate   | -2      | 50%

Trade-off: Light = dodge better, Heavy = absorb better

================================================================================
THREE LAYERS OF SURVIVAL
================================================================================

Layer 1: REF (AVOID)
  - Determines if attack lands
  - Source: Base REF + Evasion
  - Resolution: d20 + (ATK - REF) >= 11

Layer 2: ABSORPTION (REDUCE)
  - Reduces damage taken
  - Order: Ablative pools → Deflection percentage
  - Minimum: 1 damage always gets through

Layer 3: HP (SURVIVE)
  - How much damage you can take
  - Formula: Apparent_CON × 5
  - Knockout at 5%, Death at 0

================================================================================
HEALING
================================================================================

REST:
  Short Rest (minutes): Recover 25% of Max HP
    - Requires: Brief pause, no combat
  
  Long Rest (hours/sleep): Recover 100% Max HP
    - Requires: Extended rest, typically overnight

HEALING_EFFECTS:
  All healing uses PERCENTAGES, not flat amounts
  
  Examples:
    Heal Spell: 20% HP
    Greater Heal: 40% HP
    Healing Potion: 15% HP

WHY_PERCENTAGES:
  Scales automatically across power tiers
  
  Target   | Max HP | 20% Heal
  ---------|--------|----------
  Peasant  | 40     | +8 HP
  Soldier  | 60     | +12 HP
  Dragon   | 250    | +50 HP
  God      | 500    | +100 HP

================================================================================
CONDITIONS FRAMEWORK
================================================================================

STRUCTURE:
  NAME: string
  TYPE: "Buff" | "Debuff"
  EFFECT: What it does mechanically
  DURATION: "Rounds" | "Scene" | "Day" | "Until_Removed"
  STACKING: boolean
  SOURCE: What can apply it

APPLIED_BY:
  - Weapons (poison blade → Poisoned)
  - Spells (fear spell → Frightened)
  - Abilities (grapple action → Grappled)
  - Narrative (GM: fall in lava → Burning)

REMOVED_BY:
  - Duration expiring
  - Specific actions (stand → removes Prone)
  - Healing/cleansing effects
  - Narrative resolution

================================================================================
CORE DEBUFFS
================================================================================

GRAPPLED:
  Effect: Cannot move. Actions limited to: Attack grappler, Escape (STR vs STR)
  Duration: Until escaped or released
  Stacking: No

PRONE:
  Effect: -2 REF vs melee, +2 REF vs ranged. Standing costs Action
  Duration: Until stand (costs Action)
  Stacking: No

STUNNED:
  Effect: Cannot take Actions/Instants/Interrupts. REF = 0
  Duration: Rounds (source-defined)
  Stacking: No (refreshes duration)

FRIGHTENED:
  Effect: -2 all rolls while fear source visible. Cannot approach source
  Duration: Scene or Until source gone
  Stacking: No

POISONED:
  Effect: -2 STR, -2 DEX, -2 REF. May deal DoT (source-defined)
  Duration: Scene or Until treated
  Stacking: No (different poisons can stack)

BLEEDING:
  Effect: Lose X HP at start of each round (X = source-defined)
  Duration: Until treated or Scene ends
  Stacking: YES (multiple bleeds add)

BLINDED:
  Effect: -4 attacks, -4 REF. Auto-fail sight checks
  Duration: Rounds or Until removed
  Stacking: No

DEAFENED:
  Effect: Auto-fail hearing checks. No verbal benefits
  Duration: Rounds or Until removed
  Stacking: No

UNCONSCIOUS:
  Effect: Cannot act. REF = 0. Unaware of surroundings
  Duration: Until awakened
  Stacking: No
  Source: Knockout (5% HP), sleep, trauma

PARALYZED:
  Effect: Cannot move or physical actions. REF = 0. Mental actions OK
  Duration: Rounds or Until removed
  Stacking: No

SLOWED:
  Effect: MOV halved. No free Step. -2 REF
  Duration: Rounds or Until removed
  Stacking: No

BURNING:
  Effect: Lose X HP at start of each round. Can spread. Action to extinguish
  Duration: Until extinguished
  Stacking: YES (fire sources add)

CHARMED:
  Effect: Cannot harm charmer. Charmer +4 CHA vs you. May follow suggestions
  Duration: Scene or Until broken
  Stacking: No

================================================================================
CORE BUFFS
================================================================================

INVISIBLE:
  Effect: Auto-succeed Hide vs sight. +4 attack (unaware). Attackers -4 to hit
  Duration: Rounds/Scene/Until broken (attack or interact)
  Stacking: No

HASTED:
  Effect: +2 REF. Two Actions per turn instead of one
  Duration: Rounds (source-defined)
  Stacking: No

PROTECTED:
  Effect: +2 REF. +10% deflection (respects 75% cap)
  Duration: Rounds/Scene (source-defined)
  Stacking: No

REGENERATING:
  Effect: Recover X% HP at start of each round (X = source-defined)
  Duration: Rounds/Scene (source-defined)
  Stacking: No (highest wins)

STAT_BUFFS:
  Pattern: +2 to [STAT]
  Duration: Rounds/Scene (source-defined)
  Stacking: No (highest wins)
  
  Names:
    Strengthened: +2 STR
    Quickened: +2 DEX
    Fortified: +2 CON
    Sharpened: +2 INT
    Enlightened: +2 WIS
    Emboldened: +2 CHA
    Accelerated: +2 MOV
    Attuned: +2 REF

================================================================================
IMPLEMENTATION PSEUDOCODE
================================================================================

function calculate_hp(entity):
    apparent_con = entity.base_con + sum(entity.con_bonuses)
    max_hp = apparent_con * 5
    knockout_threshold = floor(max_hp * 0.05)
    return {max_hp, knockout_threshold}

function calculate_damage(attacker, attack_type, weapon):
    if attack_type == "melee":
        base = attacker.apparent_str
    elif attack_type == "ranged":
        base = attacker.apparent_dex
    elif attack_type == "spell_arcane":
        base = attacker.apparent_int
    elif attack_type == "spell_divine":
        base = attacker.apparent_wis
    
    raw_damage = base + weapon.damage_bonus
    return max(raw_damage, 1)

function apply_armor(incoming_damage, target):
    remaining = incoming_damage
    
    // Ablative first
    for ablative in target.ablative_armor:
        if ablative.pool > 0:
            absorbed = min(remaining, ablative.pool)
            ablative.pool -= absorbed
            remaining -= absorbed
        if remaining == 0:
            return 1  // minimum damage
    
    // Deflection second
    total_deflection = min(sum(target.deflection_percentages), 0.75)
    remaining = remaining * (1 - total_deflection)
    
    return max(floor(remaining), 1)

function check_hp_state(entity):
    if entity.current_hp <= 0:
        return "DEAD"
    elif entity.current_hp <= entity.knockout_threshold:
        apply_condition(entity, "Unconscious")
        return "UNCONSCIOUS"
    else:
        return "ACTIVE"

function apply_healing(target, heal_percentage):
    heal_amount = floor(target.max_hp * heal_percentage)
    target.current_hp = min(target.current_hp + heal_amount, target.max_hp)
    
    if target.current_hp > target.knockout_threshold:
        remove_condition(target, "Unconscious")

================================================================================
KEY CONSTANTS
================================================================================

HP_MULTIPLIER = 5
KNOCKOUT_PERCENT = 0.05
DEFLECTION_CAP = 0.75
MINIMUM_DAMAGE = 1
SHORT_REST_HEAL = 0.25
LONG_REST_HEAL = 1.0
DEFLECTION_DEGRADATION_TRIGGER = {crit: true, magnitude: 4}
DEFLECTION_DEGRADATION_AMOUNT = 0.10

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

All damage, armor, healing, and conditions in TDGS conform to this specification.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/combat
AI-optimized:   https://tacticaldice.com/docs/tdgs/combatforai

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

export default function TDGSCombatForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="combat" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS COMBAT - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 8 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_COMBAT_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## HP AND DEATH</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Threshold</th>
                <th style={styles.th}>Effect</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>5% HP</td><td style={styles.td}>Knockout (Unconscious)</td></tr>
              <tr><td style={styles.td}>0 HP</td><td style={styles.td}>Death (immediate)</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## DAMAGE FORMULAS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Attack Type</th>
                <th style={styles.th}>Formula</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Melee</td><td style={styles.td}>Apparent STR + Weapon Damage Bonus</td></tr>
              <tr><td style={styles.td}>Ranged</td><td style={styles.td}>Apparent DEX + Weapon Damage Bonus</td></tr>
              <tr><td style={styles.td}>Spell (Arcane)</td><td style={styles.td}>Apparent INT + Spell Damage Bonus</td></tr>
              <tr><td style={styles.td}>Spell (Divine)</td><td style={styles.td}>Apparent WIS + Spell Damage Bonus</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## ARMOR TYPES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Type</th>
                <th style={styles.th}>Mechanism</th>
                <th style={styles.th}>Cap</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Ablative</td><td style={styles.td}>Pool absorbs damage</td><td style={styles.td}>None</td></tr>
              <tr><td style={styles.td}>Deflection</td><td style={styles.td}>% reduces damage</td><td style={styles.td}>75%</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## HEALING</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Method</th>
                <th style={styles.th}>Recovery</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Short Rest</td><td style={styles.td}>25% Max HP</td></tr>
              <tr><td style={styles.td}>Long Rest</td><td style={styles.td}>100% Max HP</td></tr>
              <tr><td style={styles.td}>Effects</td><td style={styles.td}>Percentage-based</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## CORE DEBUFFS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Condition</th>
                <th style={styles.th}>Key Effect</th>
                <th style={styles.th}>Stacks?</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Grappled</td><td style={styles.td}>Cannot move, limited actions</td><td style={styles.td}>No</td></tr>
              <tr><td style={styles.td}>Prone</td><td style={styles.td}>-2 REF melee, +2 REF ranged</td><td style={styles.td}>No</td></tr>
              <tr><td style={styles.td}>Stunned</td><td style={styles.td}>No actions, REF 0</td><td style={styles.td}>No</td></tr>
              <tr><td style={styles.td}>Frightened</td><td style={styles.td}>-2 all rolls</td><td style={styles.td}>No</td></tr>
              <tr><td style={styles.td}>Poisoned</td><td style={styles.td}>-2 STR/DEX/REF</td><td style={styles.td}>No*</td></tr>
              <tr><td style={styles.td}>Bleeding</td><td style={styles.td}>X damage/round</td><td style={styles.td}>Yes</td></tr>
              <tr><td style={styles.td}>Blinded</td><td style={styles.td}>-4 attacks/REF</td><td style={styles.td}>No</td></tr>
              <tr><td style={styles.td}>Unconscious</td><td style={styles.td}>No actions, REF 0</td><td style={styles.td}>No</td></tr>
              <tr><td style={styles.td}>Burning</td><td style={styles.td}>X damage/round</td><td style={styles.td}>Yes</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## CORE BUFFS</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Condition</th>
                <th style={styles.th}>Key Effect</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Invisible</td><td style={styles.td}>+4 attack, -4 to be hit</td></tr>
              <tr><td style={styles.td}>Hasted</td><td style={styles.td}>+2 REF, two Actions</td></tr>
              <tr><td style={styles.td}>Protected</td><td style={styles.td}>+2 REF, +10% deflection</td></tr>
              <tr><td style={styles.td}>Regenerating</td><td style={styles.td}>X% HP per round</td></tr>
              <tr><td style={styles.td}>[Stat] Buff</td><td style={styles.td}>+2 to specific stat</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(123, 63, 228, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/combat"
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
