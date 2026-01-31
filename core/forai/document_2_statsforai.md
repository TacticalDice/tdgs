# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 2
# Title: Core Attributes (Stats)
# Version: 1.0
# Purpose: AI-readable specification for character attributes
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

This document defines the nine core attributes of TDGS.
These attributes describe capability, permission, and constraint.

CORE PRINCIPLE:
  Stats define what CAN happen. They do not dictate what MUST happen.

================================================================================
UNIT POLICY
================================================================================

ABSTRACT UNITS:
  Distance: square (content defines scale, e.g., 5 feet, 1.5 meters)
  Weight: WU - Weight Unit (content defines scale, e.g., 1 pound, 0.5 kg)

ENGINE IS AGNOSTIC:
  Calculates in squares and WU
  Content defines real-world equivalents
  Examples in documentation use feet/pounds for familiarity

SEE ALSO: Document 14 (Movement), Document 15 (Equipment & Slots)

================================================================================
ATTRIBUTE LIST (Canonical Order)
================================================================================

1. STR  - Strength
2. DEX  - Dexterity
3. REF  - Reflex
4. CON  - Constitution
5. MOV  - Movement
6. INT  - Intelligence
7. WIS  - Wisdom
8. CHA  - Charisma
9. LUK  - Luck

================================================================================
ATTRIBUTE: STRENGTH (STR)
================================================================================

DEFINITION:
  Raw physical force. How much force can be exerted against resistance.

SCALE: 0–100 (logarithmic, non-linear)
  - STR 0   = No meaningful force
  - STR 10  = Peak human (strongest deadlift on record)
  - STR 100 = Planetary-scale force (Earth mass)

STRENGTH IS:
  - The ability to apply force
  - Abstracted from leverage, biomechanics, cleverness

STRENGTH IS NOT:
  - Technique
  - Coordination
  - Endurance
  - A guarantee of success
  - Damage on its own

STRENGTH BAND ANCHORS:

Formula: STR × 10 = Carrying Capacity (WU)

Weight Units (WU) are abstract. Content defines scale.
See Document 15: Equipment & Slots.

STR | Capacity (WU) | Interpretation
----|---------------|---------------------------
0   | 0             | No meaningful force (insects, swarms)
5   | 50            | Child, small creature
10  | 100           | Average adult
15  | 150           | Trained, athletic
20  | 200           | Elite athlete, strongman
25  | 250           | Peak mortal
30  | 300           | Superhuman begins
40  | 400           | Heroic, legendary
50  | 500           | Titanic, monstrous
75  | 750           | Mythic, godlike
100 | 1000          | Cosmic, world-shaping

MEANINGFUL FORCE THRESHOLD:
  Entities too small to register (insects, microbes) = STR 0 individually.
  They matter through swarms, counts, traits, and narrative effects.
  Strength measures INDIVIDUAL force, not collective danger.

TYPICAL PLAY RANGE: STR 3–15
Above 25: Heroic/mythic territory

Reference: /docs/tdgs/equipment
Reference: /docs/tdgs/equipment#carrying-capacity
Reference: /docs/tdgs/equipment#measurement-units

================================================================================
ATTRIBUTE: DEXTERITY (DEX)
================================================================================

DEFINITION:
  Precision and coordination. What degree of precise control is possible
  if everything goes right.

SCALE: 0–100 (asymptotic)
  Improvements at high levels = refinement, not transformation.

DEXTERITY IS:
  - Fine motor control
  - Accuracy potential
  - Delicate manipulation capability

DEXTERITY IS NOT:
  - Speed
  - Reaction time
  - A guarantee of success

LOOKUP TABLE:
  DEX | Interpretation   | Example
  ----|------------------|------------------
  0   | No coordination  | Inanimate
  3   | Poor control     | Clumsy beings
  5   | Average          | Adult human
  8   | Exceptional      | Surgeons
  10  | Peak human       | World-class
  20  | Superhuman       | Mythic heroes
  40  | Inhuman          | Constructs
  100 | Absolute         | Divine

TYPICAL PLAY RANGE: DEX 4–10

================================================================================
ATTRIBUTE: REFLEX (REF)
================================================================================

DEFINITION:
  Temporal responsiveness. How quickly an entity notices something
  and begins to act.

SCALE: 0–100 (diminishing returns)
  Early improvements matter enormously.
  Later improvements compress toward theoretical limits.

REFLEX IS:
  - The moment between stimulus and response
  - Reaction speed

REFLEX IS NOT:
  - Movement speed
  - Precision

LOOKUP TABLE:
  REF | Interpretation | Example
  ----|----------------|------------------
  0   | No reaction    | Objects
  5   | Average        | Adult human
  10  | Peak human     | Elite athlete
  20  | Superhuman     | Enhanced
  60  | Near instant   | Legendary
  100 | Absolute       | Conceptual

TYPICAL PLAY RANGE: REF 4–10

================================================================================
ATTRIBUTE: CONSTITUTION (CON)
================================================================================

DEFINITION:
  Endurance and pain tolerance. How much stress, injury, and pain
  can be endured before failure.

SCALE: 0–100 (compressive)
  Higher values = survivability, not invulnerability.

CONSTITUTION IS:
  - Ability to function while injured
  - Pain tolerance
  - Stress endurance

CONSTITUTION IS NOT:
  - Healing rate
  - Damage reduction

LOOKUP TABLE:
  CON | Interpretation | Example
  ----|----------------|------------------
  0   | Cannot endure  | Fragile matter
  5   | Average        | Adult human
  10  | Peak human     | Extreme survivor
  20  | Superhuman     | Enhanced
  60  | Extreme        | Colossal
  100 | Absolute       | Divine

TYPICAL PLAY RANGE: CON 4–10

================================================================================
ATTRIBUTE: MOVEMENT (MOV)
================================================================================

DEFINITION:
  Translational speed. How fast an entity can move through space
  under its own power.

SCALE: 0–100

MOVEMENT IS:
  - Raw locomotion speed

MOVEMENT IS NOT:
  - Reaction time
  - Precision
  - Stamina

MOVEMENT LOOKUP TABLE:

MOV determines squares moved per Move action.
See Document 14: Movement & Positioning.

MOV | Interpretation
----|---------------------------
0   | Immobile (objects, rooted)
3   | Slow (encumbered, crawling)
5   | Average adult
6   | Standard humanoid baseline
8   | Quick, athletic
10  | Fast, trained runner
12  | Very fast, cavalry
15  | Exceptional speed
20  | Superhuman
30+ | Heroic, mythic

Most play: MOV 4-10
Above 15: Outpaces normal creatures

Reference: /docs/tdgs/movement

================================================================================
ATTRIBUTE: INTELLIGENCE (INT)
================================================================================

DEFINITION:
  Reasoning, abstraction, and learning. How complex a problem
  an entity can understand.

SCALE: 0–100

INTELLIGENCE IS:
  - Problem complexity ceiling
  - Learning capacity
  - Abstract reasoning

INTELLIGENCE IS NOT:
  - Good decision making (see WIS)
  - Wisdom or judgment

LOOKUP TABLE:
  INT | Interpretation | Example
  ----|----------------|------------------
  0   | No cognition   | Object
  5   | Average        | Adult human
  10  | Peak human     | Genius
  20  | Superhuman     | AI
  100 | Absolute       | Conceptual

TYPICAL PLAY RANGE: INT 4–10

================================================================================
ATTRIBUTE: WISDOM (WIS)
================================================================================

DEFINITION:
  Judgment and consequence awareness. "Is this a good idea?"

SCALE: 0–100

WISDOM IS:
  - Decision quality potential
  - Consequence awareness
  - Prudence

WISDOM IS NOT:
  - Intelligence or reasoning (see INT)
  - Speed

NOTE: A wise character may be slow. A foolish character may be brilliant.

LOOKUP TABLE:
  WIS | Interpretation | Example
  ----|----------------|------------------
  0   | No judgment    | Object
  5   | Average        | Adult human
  10  | Peak human     | Sage
  20  | Superhuman     | Ancient
  100 | Absolute       | Divine

TYPICAL PLAY RANGE: WIS 4–10

================================================================================
ATTRIBUTE: CHARISMA (CHA)
================================================================================

DEFINITION:
  Presence and influence. The ability to shape social outcomes
  through force of personality.

SCALE: 0–100

CHARISMA IS:
  - Social influence capability
  - Force of personality

CHARISMA IS NOT:
  - Physical beauty (separate trait)

LOOKUP TABLE:
  CHA | Interpretation | Example
  ----|----------------|------------------
  0   | No influence   | Object
  5   | Average        | Adult human
  10  | Peak human     | Leader
  20  | Superhuman     | Mythic
  100 | Absolute       | Divine

TYPICAL PLAY RANGE: CHA 4–10

================================================================================
ATTRIBUTE: LUCK (LUCK) - SPECIAL
================================================================================

DEFINITION:
  An abnormal relationship with probability.

SCALE: −10 to +10 (UNIQUE: only attribute allowing negative values)

PROPERTIES:
  - Luck is permanent
  - Luck is rare
  - Luck is powerful
  - Luck modifies probability through dice interaction, NOT narrative fiat

LUCK CAN:
  - Add modifiers
  - Add or subtract dice
  - Influence rerolls
  - Affect success or failure

┌─────────────────────────────────────────────────────────────────────────────┐
│ CRITICAL RULE: Luck NEVER affects magnitude.                                │
│ Luck touches the dice themselves—not what the dice represent.               │
└─────────────────────────────────────────────────────────────────────────────┘

LOOKUP TABLE:
  LUCK | Interpretation
  -----|-------------------------
  −10  | Catastrophic misfortune
  −1   | Unlucky
  0    | Normal
  +1   | Lucky
  +10  | Mythic fortune

TYPICAL PLAY RANGE: LUCK −1 to +1

================================================================================
SUMMARY TABLE
================================================================================

Attr | Name         | Scale    | Definition (one line)
-----|--------------|----------|------------------------------------------
STR  | Strength     | 0–100    | Raw physical force
DEX  | Dexterity    | 0–100    | Precision and coordination
REF  | Reflex       | 0–100    | Temporal responsiveness
CON  | Constitution | 0–100    | Endurance and pain tolerance
MOV  | Movement     | 0–100    | Translational speed
INT  | Intelligence | 0–100    | Reasoning, abstraction, learning
WIS  | Wisdom       | 0–100    | Judgment and consequence awareness
CHA  | Charisma     | 0–100    | Presence and influence
LUCK | Luck         | −10–+10  | Abnormal relationship with probability

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical

All nine attributes are FINALIZED.
They form the complete stat block for TDGS.
These nine core stats are IMMUTABLE.

================================================================================
END OF DOCUMENT
================================================================================
