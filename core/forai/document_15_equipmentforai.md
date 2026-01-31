# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 15
# Title: Equipment & Slots
# Version: 1.0
# Purpose: AI-readable specification for equipment system
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

KEY_CONCEPTS:
  - Slot Types: Where equipment can be worn/wielded
  - Equipped: In slot, grants effects
  - Carried: In inventory, no effects
  - Slot Cost: Items define what slots they require

================================================================================
MEASUREMENT UNITS
================================================================================

ABSTRACT_UNITS:
  engine_agnostic: true  // Engine uses abstract units

DISTANCE:
  unit: "Squares"
  content_defines: "1 square = 5 feet OR 1.5 meters OR setting-specific"

WEIGHT:
  unit: "Weight Units (WU)"
  content_defines: "1 WU = 1 pound OR 0.5 kg OR setting-specific"

TIME:
  unit: "Rounds, Scenes"
  note: "Already abstract"

================================================================================
CANONICAL SLOT TYPES (14)
================================================================================

SLOT_TYPES: [
  {type: "Head", description: "Skull, crown of head"},
  {type: "Face", description: "Eyes, nose, mouth area"},
  {type: "Ears", description: "Ear canal, outer ear (per ear)"},
  {type: "Neck", description: "Throat, nape"},
  {type: "Torso", description: "Chest, back, abdomen"},
  {type: "Back", description: "Upper back surface (cloaks, packs, wings)"},
  {type: "Arm", description: "Upper and lower arm (per arm)"},
  {type: "Hand", description: "Palm and fingers for gripping (per hand)"},
  {type: "Finger", description: "Individual digit (per finger)"},
  {type: "Waist", description: "Hip, belt line"},
  {type: "Leg", description: "Thigh and shin (per leg)"},
  {type: "Foot", description: "Ankle to toes (per foot)"},
  {type: "Tail", description: "Tail appendage (if present)"},
  {type: "Mount", description: "Saddle point (for mounts/vehicles)"}
]

EXTENSIBILITY:
  content_may_add: true
  missing_slot_rule: "If slot type not in race definition, race has 0 of that slot"

================================================================================
RACIAL SLOTS
================================================================================

RACIAL_SLOTS:
  inheritance: none  // Each race defines complete list
  
EXAMPLE_HUMAN:
  Head: 1, Face: 1, Ears: 2, Neck: 1, Torso: 1, Back: 1
  Arm: 2, Hand: 2, Finger: 10, Waist: 1, Leg: 2, Foot: 2

EXAMPLE_CENTAUR:
  Head: 1, Face: 1, Ears: 2, Neck: 1, Torso: 1, Back: 1
  Arm: 2, Hand: 2, Finger: 10, Waist: 1
  Leg: 4, Foot: 4, Mount: 1

EXAMPLE_SERPENTFOLK:
  Head: 1, Face: 1, Ears: 2, Neck: 1, Torso: 1, Back: 1
  Arm: 2, Hand: 2, Finger: 10, Waist: 1, Tail: 1

================================================================================
EQUIPPED VS CARRIED
================================================================================

ITEM_STATES:
  equipped:
    definition: "In slot, actively worn/wielded"
    mechanical_effect: "Grants all item benefits"
    
  carried:
    definition: "In inventory, not slotted"
    mechanical_effect: "No mechanical benefit"

RULE: "Only Equipped items grant effects (stats, abilities, absorption, damage)"
CARRIED_PURPOSE: ["narrative", "trading", "future use"]

================================================================================
ITEM STRUCTURE
================================================================================

ITEM_SCHEMA:
  required:
    name: string
    weight: integer  // In WU
    
  required_if_equippable:
    slot_requirements: {slot_type: count, ...}
    equip_speed: "Action" | "Free" | "X Actions"
    
  optional:
    abilities_granted: [string]  // Skills, Spells, Traits
    stat_bonuses: {stat: modifier, ...}
    absorption: integer  // Damage reduction
    damage_bonus: integer  // +X damage
    value: integer  // Cost/price
    rarity: "Common" | "Uncommon" | "Rare" | etc.
    description: string  // Flavor text

================================================================================
SLOT COST
================================================================================

SLOT_COST_RULE:
  requirement: "Entity must have ALL required slots available"
  
EXAMPLES:
  Longsword:     {Hand: 1}
  Greatsword:    {Hand: 2}
  Quad-Blade:    {Hand: 4}
  Ring:          {Finger: 1}
  Large Ring:    {Finger: 2}
  Full Plate:    {Torso: 1, Arm: 2, Leg: 2}

VALIDATION:
  human_hand_2_vs_quadblade_hand_4: "Cannot equip"
  four_armed_hand_4_vs_quadblade_hand_4: "Can equip"

================================================================================
SLOT CHANGES
================================================================================

SLOT_ACTIONS:
  equip_empty_slot: {cost: "Action"}
  unequip: {cost: "Action"}
  swap: {cost: "Action", note: "Replace equipped with new"}
  quick_swap: {cost: "Free", requires: "ability"}

SWAP_BEHAVIOR:
  replaced_item: "Goes to Carried (not dropped)"
  player_may_choose: "Drop instead"

DESIGN_NOTE:
  swap_is_1_action: true  // Not Unequip + Equip = 2 Actions
  reason: "Combat tuned for 4-6 rounds, 2 rounds to swap = devastating"

================================================================================
CARRYING CAPACITY
================================================================================

FORMULA:
  carrying_capacity: "STR × 10 × Size_Multiplier (in WU)"

SIZE_MULTIPLIERS:
  Tiny:       0.25
  Small:      0.5
  Medium:     1
  Large:      2
  Huge:       4
  Gargantuan: 8+

CONTAINERS:
  effect: "Add to carrying capacity while equipped"
  example: {name: "Backpack", bonus: "+20 WU"}

ENCUMBERED:
  trigger: "total_weight > carrying_capacity"
  effect: "Cannot take Move action"
  granularity: "Binary (content may extend)"

================================================================================
SLOT LOSS
================================================================================

SLOT_LOSS_RULES:
  on_slot_loss:
    - "Items in that slot immediately unequipped (go to Carried)"
    - "Cannot equip items requiring that slot"
    - "Restoration methods are content concerns"

EXAMPLE:
  event: "Lose left arm"
  effect: "Hand slot and Arm slot items → Carried"
  restriction: "Cannot equip Hand: 2 weapons until restored"

================================================================================
CONTENT EXTENSIONS
================================================================================

ENGINE_PROVIDES: "Framework"
CONTENT_EXTENDS: true

CURSED_ITEMS:
  engine_defines: false  // No "Locked" property
  content_may_create: "Abilities/traits preventing unequip"
  
ATTUNEMENT:
  engine_level: false
  future_extension: true
  
INVENTORY_LIMITS:
  engine_defines: "Weight-based only"
  content_may_add: "Item count limits, container requirements"
  
BANKING_STORAGE:
  engine_defines: false
  future_extension: true

================================================================================
EXAMPLE ITEMS (Not Canonical)
================================================================================

EXAMPLE_WEAPONS:
  Longsword:
    weight: 3
    slots: {Hand: 1}
    equip_speed: "Action"
    damage_bonus: +2
    
  Greatsword:
    weight: 6
    slots: {Hand: 2}
    equip_speed: "Action"
    damage_bonus: +4
    
  Dagger:
    weight: 1
    slots: {Hand: 1}
    equip_speed: "Free"
    damage_bonus: +1

EXAMPLE_ARMOR:
  Leather:
    weight: 10
    slots: {Torso: 1}
    equip_speed: "2 Actions"
    absorption: 2
    
  Full_Plate:
    weight: 45
    slots: {Torso: 1, Arm: 2, Leg: 2}
    equip_speed: "10 Actions"
    absorption: 6

EXAMPLE_ACCESSORIES:
  Ring_of_Protection:
    weight: 0
    slots: {Finger: 1}
    equip_speed: "Free"
    stat_bonus: {REF: +1}
    
  Backpack:
    weight: 2
    slots: {Back: 1}
    equip_speed: "Action"
    special: "+20 WU carrying capacity"

================================================================================
SUMMARY
================================================================================

QUICK_REFERENCE:
  slot_types: 14  // Canonical, content may add
  racial_slots: "Each race defines complete list"
  equipped: "In slot → grants effects"
  carried: "In inventory → no effects"
  slot_cost: "Item defines type(s) and count"
  equip_unequip_swap: "1 Action each"
  quick_swap: "Free (requires ability)"
  carrying_capacity: "STR × 10 × Size_Multiplier (WU)"
  encumbered: "Cannot Move"
  slot_loss: "Items unequipped, slot unusable"
  units: "Abstract (WU, squares); content defines scale"

================================================================================
CROSS-REFERENCES
================================================================================

REFERENCES: [
  "Document 9: Entities (entity structure)",
  "Document 11: Races (slot definitions)",
  "Document 8: Combat (Absorption, Damage Bonus)"
]

CANONICAL_URLS:
  human: "https://tacticaldice.com/docs/tdgs/equipment"
  ai: "https://tacticaldice.com/docs/tdgs/equipmentforai"

================================================================================
DOCUMENT STATUS
================================================================================

STATUS: Canonical
VERSION: 1.0

================================================================================
END OF DOCUMENT 15
================================================================================
