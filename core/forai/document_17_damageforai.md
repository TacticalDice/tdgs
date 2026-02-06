# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 17
# Title: Damage
# Version: 1.0
# Purpose: AI-readable specification for damage types, resistance, vulnerability, immunity, and absorption
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
QUICK REFERENCE
================================================================================

DAMAGE_TYPE: Category describing nature of damage (e.g. Fire, Cold, Slashing)
TYPED_DAMAGE: Has a Damage Type, flows through resistance/vulnerability/immunity
UNTYPED_DAMAGE: No category, bypasses resistance/vulnerability/immunity
CANONICAL_LIST: None (framework only, content defines specific types)

RESISTANCE_CAP: 75%
VULNERABILITY_CAP: None
IMMUNITY: Binary (immune or not)
ABSORPTION: Percentage (heals X%, takes remainder)

DELIVERY_MECHANISM: All damage interactions are Abilities (Traits, Spells, Skills)
ABILITY_SOURCES: Class, Race, Items, Effects, Training, Discovery (per Document 7)

DAMAGE_PIPELINE:
  Phase 1 (flat):
    1. Calculate raw damage (stat + bonus, per Document 8)
    2. Ablative armor absorbs (pool reduced)
  Phase 2 (percentage, order irrelevant):
    3. Deflection armor reduces (percentage, per Document 8)
    4. Resistance or Vulnerability applies (percentage, by type, this document)
  Final:
    5. Minimum 1 damage (unless Immune or fully Absorbed)

ROUNDING: Always down (consistent with all TDGS rounding)

================================================================================
DAMAGE TYPES
================================================================================

DEFINITION:
  A Damage Type is a category describing the nature of damage dealt.
  Every damage instance is either typed or untyped.

FRAMEWORK_NOT_CONTENT:
  TDGS defines: How Damage Types work (mechanics)
  Content defines: Which Damage Types exist (lists)
  No canonical Damage Type list exists in Core.

EXAMPLES_BY_SETTING:
  fantasy: [Fire, Cold, Lightning, Poison, Necrotic, Radiant,
            Piercing, Slashing, Bludgeoning, Psychic, Force, Acid]
  sci_fi:  [Plasma, Radiation, EMP, Kinetic, Cryo, Corrosive, Sonic]
  horror:  [Physical, Psychic, Spiritual, Corruption]

TYPED_VS_UNTYPED:
  typed:
    flows_through: resistance, vulnerability, immunity, absorption
    examples: Fire Bolt deals Fire, Longsword deals Slashing
  untyped:
    bypasses: resistance, vulnerability, immunity, absorption
    examples: falling (see Document 14), drowning, abstract HP loss

================================================================================
ASSIGNING DAMAGE TYPES
================================================================================

ABILITIES:
  rule: Any ability that deals damage can specify a Damage Type
  type_is_fixed: true  // Fire Bolt always deals Fire, no situational changes
  examples:
    - {name: "Fire Bolt", type: Spell, damage: "2d6 Fire"}
    - {name: "Sneak Attack", type: Skill, damage_bonus: "+3 Piercing"}

EQUIPMENT:
  mechanism: Weapons grant Traits while equipped; Traits carry the Damage Type
  multi_type: true  // A weapon can grant multiple Traits with different types
  examples:
    - name: "Longsword"
      grants: [{trait: "Slashing Weapon", bonus: "+3 Slashing"}]
    - name: "Enchanted Bow"
      grants: [
        {trait: "Piercing Weapon", bonus: "+2 Piercing"},
        {trait: "Flame Enchantment", bonus: "+1d4 Fire"}
      ]

NATURAL_WEAPONS:
  mechanism: Traits (per Document 9)
  examples:
    - {name: "Dragon Claws", type: Trait, bonus: "+2d6 Slashing"}
    - {name: "Dragon Fire Breath", type: Trait, damage: "Apparent STR Fire",
       area: "Cone AoE", cooldown: Scene}

ENVIRONMENTAL:
  rule: Traps, hazards, effects can specify a Damage Type
  content_decides: true
  examples:
    - {source: "Lava", damage: "10 Fire per round"}
    - {source: "Acid Pool", damage: "5 Acid per round"}
    - {source: "Falling", damage: "Untyped (see Document 14)"}
    - {source: "Drowning", damage: "5 Untyped per round"}

================================================================================
DAMAGE INTERACTIONS
================================================================================

DELIVERY:
  mechanism: Ability system (Document 7)
  types: [Trait, Spell, Skill]
  sources: [Class, Race, Items, Effects, Training, Discovery]
  entity_structure_change: false  // No new entity-level structures

FOUR_INTERACTIONS: [Resistance, Vulnerability, Immunity, Absorption]

================================================================================
RESISTANCE
================================================================================

FORMULA:
  Damage_Taken = Typed_Damage × (1 - Resistance%)

CAP: 75%
  mirrors: Document 8 deflection cap
  gm_override: allowed (same policy as deflection cap)

STACKING:
  method: additive
  cap: 75%
  example:
    Dragon_Scales_Trait: 25%
    Fire_Ward_Spell: 25%
    Fireproof_Cloak_Item_Trait: 25%
    TOTAL: 75% (cap reached, additional sources have no effect)

EXAMPLES:
  Source                    | Resistance | Incoming Fire | Damage Taken
  --------------------------|-----------|---------------|-------------
  (none)                    | 0%        | 20            | 20
  Fire Ward (Spell)         | 25%       | 20            | 15
  Dragon Scales (Trait)     | 50%       | 20            | 10
  Greater Fire Ward (Spell) | 75%       | 20            | 5

================================================================================
VULNERABILITY
================================================================================

FORMULA:
  Damage_Taken = Typed_Damage × (1 + Vulnerability%)

CAP: None
  rationale: Finding weakness should be devastating

STACKING:
  method: additive
  cap: none
  example:
    Curse_of_Flame_Spell: 50%
    Ice_Elemental_Body_Trait: 50%
    TOTAL: 100% (double damage)

OPPOSING_RESISTANCE:
  rule: Resistance and vulnerability to same type offset
  example:
    Dragon_Scales_Trait: 50% Fire Resistance
    Curse_of_Flame_Spell: 100% Fire Vulnerability
    NET: 50% Fire Vulnerability
    Damage_Taken = Typed_Damage × 1.50

EXAMPLES:
  Source                       | Vulnerability | Incoming Cold | Damage Taken
  -----------------------------|--------------|---------------|-------------
  (none)                       | 0%           | 20            | 20
  Cold-Blooded (Racial Trait)  | 50%          | 20            | 30
  Ice Bane (Curse Spell)       | 100%         | 20            | 40

================================================================================
IMMUNITY
================================================================================

FORMULA:
  If immune to Damage_Type: Damage = 0

BINARY: true  // Have it or don't. No partial immunity. That's Resistance.

MINIMUM_DAMAGE_EXCEPTION:
  Document 8 rule: "Every hit deals at least 1 damage"
  Immunity: Sole exception to this rule
  Hit still counts for: resolution, on-hit triggers, concentration breaks
  Hit does NOT count for: damage

PRIORITY:
  immunity_vs_vulnerability: Immunity wins (can't amplify zero)
  immunity_vs_resistance: Immunity supersedes (irrelevant when immune)

SOURCES:
  typical: [Racial Traits, powerful Spells, Legendary Item Traits]
  rarity: rare by design (removes entire damage category from play)

IMMUNITY_IS_NOT_HEALING:
  immune_to_fire_in_fire: 0 damage, not healing
  healing_from_damage: See Absorption

================================================================================
ABSORPTION
================================================================================

FORMULA:
  Absorbed_HP = Typed_Damage × Absorption%
  Remaining_Damage = Typed_Damage × (1 - Absorption%)

AT_100_PERCENT:
  heals: 100% of incoming typed damage
  takes: 0 damage
  effective_immunity: true

BELOW_100_PERCENT:
  heals: Absorption% of incoming typed damage
  takes: (1 - Absorption%) as damage
  effective_immunity: false

HEALING_CAP: Cannot exceed Max HP (excess wasted)

RARITY: Strongest possible damage interaction. Reserve for entities with deep
        thematic connection to the damage category.

EXAMPLES:
  Fire_Elemental_Greater:
    trait: "Fire Absorption (100%)"
    incoming_40_fire: heals 40, takes 0

  Fire_Attuned_Armor:
    grants_trait: "Partial Fire Absorption (50%)"
    incoming_30_fire: heals 15, takes 15

  Flame_Dancer:
    trait: "Minor Fire Absorption (25%)"
    incoming_40_fire: heals 10, takes 30

================================================================================
MULTI-TYPE DAMAGE
================================================================================

SPLIT_EVALUATION:
  rule: Each Damage Type portion evaluated separately through pipeline
  resistance_isolation: Resistance to one type does not affect other types

EXAMPLE:
  weapon: "Enchanted Flame Sword"
  grants: [Slashing +3, Fire +1d4]
  target: {fire_resistance: 50%, slashing_resistance: 0%}
  calculation:
    slashing: 3 → 3 (no resistance)
    fire: 1d4 (roll 3) → 3 × 0.50 = 1.5 → 1 (round down)
    total_bonus: 4

ROUNDING: Always down. Consistent with all TDGS rounding.

================================================================================
DAMAGE PIPELINE (DETAILED)
================================================================================

PHASE_1_FLAT:
  step_1: Calculate raw damage (stat + bonus, per Document 8)
  step_2: Ablative armor absorbs (pool reduced by raw amount)
  note: Subtraction. Order matters. Shield takes hit first.

PHASE_2_PERCENTAGE:
  step_3: Deflection armor (percentage, per Document 8)
  step_4: Resistance or Vulnerability (percentage, by Damage Type)
  note: Multiplication is commutative. Order within Phase 2 irrelevant.

FINAL:
  step_5: Minimum 1 damage if attack hit
  exceptions: [Immune, fully Absorbed]

PIPELINE_EXAMPLES:

  EXAMPLE_1 (fire vs armored resistant target):
    incoming: 40 Fire
    phase_1: ablative absorbs 10 → 30
    phase_2: deflection 50% → 15, fire_resistance 25% → 15 × 0.75 = 11.25 → 11
    result: 11 Fire damage to HP

  EXAMPLE_2 (piercing vs same target):
    incoming: 40 Piercing
    phase_1: ablative absorbs 10 → 30
    phase_2: deflection 50% → 15, fire_resistance: N/A (wrong type)
    result: 15 Piercing damage to HP

  EXAMPLE_3 (cold vs vulnerable target):
    incoming: 40 Cold
    phase_1: no ablative → 40
    phase_2: deflection 50% → 20, cold_vulnerability 50% → 20 × 1.50 = 30
    result: 30 Cold damage to HP

================================================================================
CONDITIONS AND DAMAGE TYPES
================================================================================

CONDITION_TYPING:
  rule: Conditions dealing damage over time should specify a Damage Type
  content_decision: true
  examples:
    - {condition: Burning, damage_type: Fire}
    - {condition: Bleeding, damage_type: Untyped, reason: "blood loss, not elemental"}
    - {condition: Poisoned, damage_type: Poison, note: "if dealing ongoing damage"}

IMMUNITY_AND_CONDITIONS:
  rule: Immune to type → immune to conditions dealing only that type
  example: Fire-immune entity cannot be set Burning by fire effects
  exception: Immunity to Fire does not prevent non-fire conditions
    example: Fire-immune entity can still be grappled by burning creature

GAINING_IMMUNITY_TO_ACTIVE_CONDITION:
  rule: Condition persists but deals 0 damage while immunity active
  condition_not_removed: true (not retroactively cleansed)
  if_immunity_expires: Condition resumes dealing damage normally
  content_override: Abilities may explicitly cleanse conditions on application

================================================================================
WEAPONS AND DEFAULT DAMAGE TYPES
================================================================================

MECHANISM: Weapons grant Traits while equipped. Traits carry Damage Type.

GRANULARITY_IS_CONTENT_DECISION:
  detailed_fantasy: [Slashing, Piercing, Bludgeoning]
  simple_horror: [Physical, Supernatural]
  note: Same framework regardless of granularity

================================================================================
INTERACTION PRIORITY
================================================================================

PRIORITY_TABLE:
  Situation                          | Resolution
  -----------------------------------|------------------------------------------
  Resistance + Vulnerability (same)  | Offset: net percentage applied
  Immunity + Vulnerability (same)    | Immunity wins
  Absorption + any (same)            | Absorption wins
  Absorption < 100% (same)           | Heal X%, take remainder
  Multiple resistances (same)        | Additive, capped at 75%
  Multiple vulnerabilities (same)    | Additive, no cap

================================================================================
ENTITY EXAMPLES
================================================================================

FIRE_ELEMENTAL:
  damage_interactions:
    - {type: Absorption, damage_type: Fire, value: "100%", source: "Racial Trait"}
    - {type: Vulnerability, damage_type: Cold, value: "100%", source: "Racial Trait"}

IRON_GOLEM:
  damage_interactions:
    - {type: Resistance, damage_type: Slashing, value: "50%", source: "Trait"}
    - {type: Resistance, damage_type: Piercing, value: "50%", source: "Trait"}
    - {type: Resistance, damage_type: Bludgeoning, value: "25%", source: "Trait"}
    - {type: Vulnerability, damage_type: Lightning, value: "50%", source: "Trait"}
    - {type: Vulnerability, damage_type: Acid, value: "50%", source: "Trait"}
    - {type: Immunity, damage_type: Poison, source: "Trait"}
    - {type: Immunity, damage_type: Psychic, source: "Trait"}

HUMAN_SOLDIER:
  damage_interactions: []  // None. Armor handles defense.

================================================================================
CROSS-REFERENCES
================================================================================

REFERENCES: [
    "Document 7: Abilities (delivery mechanism for all damage interactions)",
    "Document 8: Combat (damage calculation, armor, minimum damage rule)",
    "Document 9: Entities (natural weapons as Traits)",
    "Document 14: Movement (falling damage rules)",
    "Document 15: Equipment (weapons grant Traits while equipped)"
]

REFERENCED_BY: [
    "Document 7: Abilities (Damage Type fields on ability templates)",
    "Document 8: Combat (minimum damage exception for Immunity)"
]

================================================================================
DESIGN NOTES
================================================================================

DESIGN_PRINCIPLES: {
    "framework_not_content": true,       // No canonical Damage Type list
    "abilities_as_delivery": true,       // All interactions are Traits/Spells/Skills
    "no_entity_structure_change": true,  // Doc 9 untouched
    "resistance_mirrors_deflection": true, // 75% cap, same philosophy
    "vulnerability_uncapped": true,      // Weakness discovery should matter
    "immunity_is_rare": true,            // Removes entire category from play
    "absorption_implies_immunity_at_100": true, // Only full absorption = immune
    "partial_absorption_takes_remainder": true,  // Below 100% still hurts
    "pipeline_phases_matter": true,      // Flat first, then percentages
    "phase_2_order_irrelevant": true,    // Multiplication is commutative
    "untyped_bypasses_all": true         // Falling/drowning skip type system
}

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

================================================================================
END OF DOCUMENT 17
================================================================================
