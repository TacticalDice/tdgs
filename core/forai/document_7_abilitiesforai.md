# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 7
# Title: Abilities
# Version: 1.0
# Purpose: AI-readable specification for Skills, Spells, and Traits
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

Abilities are capabilities beyond base stats.
Stats define what you ARE. Abilities define what you can DO.

THREE TYPES:
  SKILL  - Trained, has levels (1-8) and tiers
  SPELL  - Magical, fixed power, tiers only, always has cooldowns
  TRAIT  - Innate, binary (have or don't), no progression

================================================================================
ABILITY COMPONENTS (ALL TYPES)
================================================================================

REQUIRED:
  NAME         What the ability is called
  DESCRIPTION  What it does
  TYPE         Skill | Spell | Trait
  TIMING       Action | Instant | Interrupt | Passive | Free
  EFFECT       What happens when used
  COOLDOWN     None | Round | Scene | Day

OPTIONAL:
  PREREQUISITES  Requirements to gain this ability
  TIER           Power level (Skills and Spells only)
  LEVEL          Mastery 1-8 (Skills only)
  STAT_BONUSES   Modifiers for relevant actions (Skills primarily)

================================================================================
COOLDOWNS
================================================================================

COOLDOWN_TYPES:
  None   -> Usable anytime (when you have actions)
  Round  -> Usable once per round, resets at round start
  Scene  -> Usable once per scene, resets when scene ends
  Day    -> Usable once per day, resets after long rest

APPLIES_TO: Any ability type can have cooldowns
  - Skills: If defined by ability
  - Spells: Almost always have cooldowns
  - Traits: If defined by ability (e.g., Dragon Breath)

================================================================================
SKILLS
================================================================================

DEFINITION: Trained abilities that improve with practice

PROPERTIES:
  - Has LEVELS: 1 to 8
  - Has TIERS: Power categories
  - May have COOLDOWNS: Per ability definition
  - May have PREREQUISITES: Lower tier skills, stats

LEVEL SCALING (DEFAULT):
  Level 1: +0 (just learned)
  Level 2: +1
  Level 3: +1
  Level 4: +2
  Level 5: +2
  Level 6: +3
  Level 7: +3
  Level 8: +4 (mastery)

FORMULA: bonus = floor(level / 2)

MAX_BONUS: +4 per skill

BONUS_APPLICATION:
  DEFAULT: Applies to relevant actions only
  - Sniper +4 DEX: Applies to long-range attacks ONLY
  - Does NOT apply to: dodging, lockpicking, other DEX uses
  
  UNIVERSAL: If explicitly stated, applies to ALL uses of stat
  - Physical Conditioning +2 STR (Universal): ALL STR actions

================================================================================
SKILL TIERS
================================================================================

TIER_MEANING:
  Tier = Inherent power level of skill
  Level = Your mastery of that skill

COMPARISON:
  Tier 1 Level 8 = Master of basics
  Tier 3 Level 1 = Novice at advanced techniques
  
  Tier 3 novice CAN DO things Tier 1 master CANNOT
  Tiers unlock capabilities, levels improve them

TIER_STACKING:
  Bonuses from same skill line STACK for relevant actions
  
  Example (Sniper Line):
    Shooter (Tier 1, Lv8):       +4 DEX ranged
    Sniper (Tier 2, Lv8):        +4 DEX ranged (stacks)
    Master Sniper (Tier 3, Lv8): +4 DEX ranged (stacks)
    TOTAL: +12 DEX for ranged attacks

  Character with base DEX 10 -> effective DEX 22 for ranged

================================================================================
SPELLS
================================================================================

DEFINITION: Magical abilities that channel supernatural power

PROPERTIES:
  - NO LEVELS: Power is fixed
  - Has TIERS: Power categories
  - Has COOLDOWNS: Almost always (None, Round, Scene, Day)
  - Uses MAGIC_TYPE: Arcane (INT) or Divine (WIS)

SPELL_TIERS:
  Tier 1: Cantrips, minor effects
  Tier 2: Standard adventurer magic
  Tier 3: Powerful, significant encounter impact
  Tier 4: Major, battle-changing
  Tier 5+: Legendary, world-altering

PROGRESSION:
  Want stronger magic? Learn higher tier spell.
  Fire Bolt (T1) -> Flame Burst (T2) -> Inferno (T3)

================================================================================
TRAITS
================================================================================

DEFINITION: Innate abilities possessed by nature or circumstance

PROPERTIES:
  - NO LEVELS: Binary (have or don't)
  - NO TIERS: One version only
  - May have COOLDOWNS: If defined (e.g., Dragon Breath)
  - FIXED EFFECT: Does exactly what it does, always

TRAIT_SOURCES:
  RACE:           Species grants innate traits (Darkvision, Amphibious)
  TRANSFORMATION: Becoming something new (Lycanthropy -> Regeneration)
  ITEM:           While equipped (Goggles of Night -> Darkvision)

TRAIT_REMOVAL:
  - Racial traits: Only by transformation
  - Item traits: Remove item, lose trait
  - Transformation traits: Cure/reverse transformation

UPGRADING_TRAITS:
  No "Darkvision Level 5" exists
  Want better darkvision? Get different trait: Greater Darkvision

================================================================================
PREREQUISITES
================================================================================

PREREQUISITE_TYPES:
  SKILL_REQUIRED:   Must have [Skill] at Level [X]
  STAT_REQUIRED:    Must have [Stat] at value [X]
  TIER_REQUIRED:    Must have Tier [X] skill in this line
  SPELL_REQUIRED:   Must know [Spell]
  OTHER:            Narrative requirement (GM discretion)

EXAMPLES:
  Sniper (Tier 2):
    - Shooter at Level 4
    - DEX 15

  Resurrection (Tier 5 Spell):
    - Healing Touch (any tier)
    - WIS 25
    - Must have witnessed death and returned someone from it

  Dragon Slayer (Tier 4):
    - Devastating Blow at Level 4
    - Dragon Lore at Level 2
    - Must have slain a dragon

================================================================================
ABILITY SOURCES
================================================================================

SOURCE          | TYPICAL_TYPES    | PERMANENT?
----------------|------------------|---------------------------
Class           | Skills, Spells   | Yes
Race            | Traits           | Yes (until transformation)
Item            | Any              | While equipped
Effect          | Any              | For duration
Training        | Skills, Spells   | Yes
Discovery       | Any              | Yes

SOURCE_MECHANICS:
  Source is NARRATIVE context only.
  Ability works IDENTICALLY regardless of source.
  
  Darkvision from:
    - Being nocturnal race
    - Wearing enchanted goggles
    - Drinking potion
  All function identically: you see in darkness.

================================================================================
ABILITY TEMPLATES
================================================================================

SKILL_TEMPLATE:
  NAME: [Skill Name]
  TYPE: Skill
  TIER: [1-5+]
  TIMING: [Action | Instant | Interrupt | Passive | Free]
  COOLDOWN: [None | Round | Scene | Day]
  DESCRIPTION: [What this skill does]
  PREREQUISITES:
    SKILL_REQUIRED: [Skill at Level X] (optional)
    STAT_REQUIRED: [Stat at value X] (optional)
    TIER_REQUIRED: [Tier X in this line] (optional)
    OTHER: [Narrative] (optional)
  EFFECT: [What happens when used]
  STAT_BONUS:
    VALUE: [+X to STAT]
    APPLIES_TO: [Relevant actions | Universal]
  SCALING: [Default | Custom: define]
  UNLOCKS: [New capabilities at this tier]
  DAMAGE (optional):
    DAMAGE_TYPE: [Content-defined type]
    DAMAGE_BONUS: [Flat | Dice | Both]

SPELL_TEMPLATE:
  NAME: [Spell Name]
  TYPE: Spell
  TIER: [1-5+]
  MAGIC_TYPE: [Arcane | Divine]
  TIMING: [Action | Instant | Interrupt]
  COOLDOWN: [None | Round | Scene | Day]
  DESCRIPTION: [What this spell does]
  PREREQUISITES:
    STAT_REQUIRED: [INT or WIS at value X]
    SPELL_REQUIRED: [Lower tier spell] (optional)
    OTHER: [Narrative] (optional)
  EFFECT: [What happens when cast]
  RESOLUTION:
    YOUR_STAT: [INT | WIS]
    THEIR_STAT: [Target stat | Difficulty]
  DAMAGE (optional):
    DAMAGE_TYPE: [Content-defined type]
    DAMAGE_VALUE: [Dice expression and/or flat value]

TRAIT_TEMPLATE:
  NAME: [Trait Name]
  TYPE: Trait
  SOURCE: [Racial | Transformation | Item | Other]
  COOLDOWN: [None | Round | Scene | Day]
  DESCRIPTION: [What this trait does]
  EFFECT: [Fixed effect]
  REMOVED_WHEN: [Conditions] (optional)
  DAMAGE (optional):
    DAMAGE_TYPE: [Content-defined type]
    DAMAGE_VALUE: [Fixed value | Dice | Bonus]

================================================================================
STAT BONUS MECHANICS
================================================================================

RELEVANT_VS_UNIVERSAL:
  RELEVANT (default):
    - Bonus applies to specific action subset
    - Sniper +4 DEX: ranged attacks only
    - Does NOT apply: dodge, stealth, lockpick
    
  UNIVERSAL (explicit):
    - Bonus applies to ALL uses of stat
    - Physical Conditioning +2 STR: ALL STR actions
    - Rarer, typically lower bonus

STACKING_RULES:
  DIFFERENT_SKILLS:
    - Stack if both apply to same action
    - Example: Shooter + Sniper for ranged attack = both bonuses
    
  SAME_SKILL:
    - Cannot have same skill twice
    - No stacking with itself

CALCULATION_EXAMPLE:
  Making a sniper shot:
    Base DEX:                    10
    Shooter (T1, Lv8):          +4
    Sniper (T2, Lv8):           +4
    Master Sniper (T3, Lv8):    +4
    ----------------------------
    Effective DEX:              22

================================================================================
SKILL BONUSES AND RESOLUTION/MAGNITUDE
================================================================================

Skills that raise Apparent Stat affect BOTH resolution AND magnitude.
This does NOT violate "Resolution and Magnitude Never Mix."

THE PRINCIPLE:
  The d20 roll never determines damage.
  - d20 = whether you succeed (resolution)
  - Stat = how much happens (magnitude)

A skill raising Apparent STR affects:
  - Hit chance (STR in resolution formula)
  - Damage dealt (STR in damage formula)

This is intentional. Training improves capability.
The ROLL doesn't change magnitude. The STAT does.

================================================================================
IMPLEMENTATION NOTES FOR AI SYSTEMS
================================================================================

SKILL_BONUS_CALCULATION:
  function getSkillBonus(level):
    return Math.floor(level / 2)

EFFECTIVE_STAT_CALCULATION:
  function getEffectiveStat(baseStat, relevantSkills, action):
    bonus = 0
    for skill in relevantSkills:
      if skill.appliesTo(action) or skill.isUniversal:
        bonus += getSkillBonus(skill.level)
    return baseStat + bonus

ABILITY_VALIDATION:
  function canLearnAbility(character, ability):
    for prereq in ability.prerequisites:
      if prereq.type == SKILL_REQUIRED:
        if character.getSkillLevel(prereq.skill) < prereq.level:
          return false
      if prereq.type == STAT_REQUIRED:
        if character.getStat(prereq.stat) < prereq.value:
          return false
    return true

TIER_LINE_STACKING:
  function getTotalLineBonus(character, skillLine, action):
    totalBonus = 0
    for tier in skillLine.tiers:
      skill = character.getSkillInLine(skillLine, tier)
      if skill and skill.appliesTo(action):
        totalBonus += getSkillBonus(skill.level)
    return totalBonus

================================================================================
SUMMARY TABLES
================================================================================

TYPE COMPARISON:
  Type   | Levels | Tiers | Cooldowns
  -------|--------|-------|------------
  Skill  | 1-8    | Yes   | If defined
  Spell  | None   | Yes   | Almost always
  Trait  | None   | None  | If defined

SKILL SCALING:
  Level | Bonus
  ------|------
  1     | +0
  2     | +1
  3     | +1
  4     | +2
  5     | +2
  6     | +3
  7     | +3
  8     | +4

COOLDOWN RESET:
  Cooldown | Resets When
  ---------|------------------
  None     | N/A (always available)
  Round    | Start of new round
  Scene    | Scene ends
  Day      | After long rest

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

All Skills, Spells, and Traits in TDGS conform to the structures defined here.
Specific ability lists are defined in content documents (Classes, Races, Items).

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/abilities
AI-optimized:   https://tacticaldice.com/docs/tdgs/abilitiesforai

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

export default function TDGSAbilitiesForAIPage() {
  return (
    <div style={styles.container}>
      <div style={styles.content}>
        <TDGSForAINav currentDoc="abilities" />

        <header style={styles.header}>
          <span style={styles.coreBadge}>Core</span>
          <h1 style={styles.title}># TDGS ABILITIES - AI REFERENCE</h1>
          <p style={styles.subtitle}>Document 7 | Structured specification for AI parsing</p>
        </header>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## FULL SPECIFICATION</h2>
          <div style={styles.codeBlock}>
            <code style={styles.code}>{TDGS_ABILITIES_SPEC}</code>
          </div>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## THE THREE TYPES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Type</th>
                <th style={styles.th}>Levels</th>
                <th style={styles.th}>Tiers</th>
                <th style={styles.th}>Cooldowns</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Skill</td><td style={styles.td}>1-8</td><td style={styles.td}>Yes</td><td style={styles.td}>If defined</td></tr>
              <tr><td style={styles.td}>Spell</td><td style={styles.td}>None</td><td style={styles.td}>Yes</td><td style={styles.td}>Almost always</td></tr>
              <tr><td style={styles.td}>Trait</td><td style={styles.td}>None</td><td style={styles.td}>None</td><td style={styles.td}>If defined</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## SKILL SCALING</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Level</th>
                <th style={styles.th}>Bonus</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>1</td><td style={styles.td}>+0</td></tr>
              <tr><td style={styles.td}>2</td><td style={styles.td}>+1</td></tr>
              <tr><td style={styles.td}>3</td><td style={styles.td}>+1</td></tr>
              <tr><td style={styles.td}>4</td><td style={styles.td}>+2</td></tr>
              <tr><td style={styles.td}>5</td><td style={styles.td}>+2</td></tr>
              <tr><td style={styles.td}>6</td><td style={styles.td}>+3</td></tr>
              <tr><td style={styles.td}>7</td><td style={styles.td}>+3</td></tr>
              <tr><td style={styles.td}>8</td><td style={styles.td}>+4</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## COOLDOWN TYPES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Cooldown</th>
                <th style={styles.th}>Resets When</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>None</td><td style={styles.td}>Always available</td></tr>
              <tr><td style={styles.td}>Round</td><td style={styles.td}>Start of new round</td></tr>
              <tr><td style={styles.td}>Scene</td><td style={styles.td}>Scene ends</td></tr>
              <tr><td style={styles.td}>Day</td><td style={styles.td}>After long rest</td></tr>
            </tbody>
          </table>
        </section>

        <section style={styles.section}>
          <h2 style={styles.sectionTitle}>## ABILITY SOURCES</h2>
          <table style={styles.table}>
            <thead>
              <tr>
                <th style={styles.th}>Source</th>
                <th style={styles.th}>Typical Types</th>
                <th style={styles.th}>Permanent?</th>
              </tr>
            </thead>
            <tbody>
              <tr><td style={styles.td}>Class</td><td style={styles.td}>Skills, Spells</td><td style={styles.td}>Yes</td></tr>
              <tr><td style={styles.td}>Race</td><td style={styles.td}>Traits</td><td style={styles.td}>Yes (until transform)</td></tr>
              <tr><td style={styles.td}>Item</td><td style={styles.td}>Any</td><td style={styles.td}>While equipped</td></tr>
              <tr><td style={styles.td}>Effect</td><td style={styles.td}>Any</td><td style={styles.td}>For duration</td></tr>
              <tr><td style={styles.td}>Training</td><td style={styles.td}>Skills, Spells</td><td style={styles.td}>Yes</td></tr>
              <tr><td style={styles.td}>Discovery</td><td style={styles.td}>Any</td><td style={styles.td}>Yes</td></tr>
            </tbody>
          </table>
        </section>

        <footer style={{ marginTop: 60, paddingTop: 20, borderTop: '1px solid rgba(123, 63, 228, 0.3)', textAlign: 'center' }}>
          <Link
            href="/docs/tdgs/abilities"
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
