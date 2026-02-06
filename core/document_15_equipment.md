*Document 15*

# Equipment & Slots

*What you wear, wield, and carry*

## Purpose

This document defines the equipment system in TDGS: how entities wear, wield, and carry items.

It establishes:

- Canonical slot types
- Equipped vs Carried distinction
- Item structure requirements
- Carrying capacity
- Slot management rules

This document builds upon Document 9 (Entities) and Document 11 (Races). Races define what slots an entity has. This document defines how those slots work.

## Measurement Units

TDGS uses abstract units. The engine calculates in units and is agnostic to measurement systems.

| Unit | Engine Term | Content Defines |
|------|-------------|-----------------|
| Distance | Squares | 1 square = 5 feet OR 1.5 meters OR setting-specific |
| Weight | Weight Units (WU) | 1 WU = 1 pound OR 0.5 kg OR setting-specific |
| Time | Rounds, Scenes | Already abstract |

This allows the same rules to work for any setting without conversion. Content creators choose the scale that fits their world.

## Slot Types

Slots represent where equipment can be worn or wielded. TDGS defines 14 canonical slot types.

| Slot Type | Description |
|-----------|-------------|
| Head | Skull, crown of head |
| Face | Eyes, nose, mouth area |
| Ears | Ear canal, outer ear (per ear) |
| Neck | Throat, nape |
| Torso | Chest, back, abdomen |
| Back | Upper back surface (cloaks, packs, wings) |
| Arm | Upper and lower arm (per arm) |
| Hand | Palm and fingers as unit for gripping (per hand) |
| Finger | Individual digit (per finger) |
| Waist | Hip, belt line |
| Leg | Thigh and shin (per leg) |
| Foot | Ankle to toes (per foot) |
| Tail | Tail appendage (if present) |
| Mount | Saddle point (for mounts/vehicles) |

Content MAY add additional slot types for exotic creatures or settings (Wings, Horns, Tentacle, etc.), but these 14 form the canonical base.

## Racial Slots

Each race defines its own complete slot list. There is no universal baseline - each race specifies exactly what slots it has.

### Example - Human

```
Slots:
  Head: 1
  Face: 1
  Ears: 2
  Neck: 1
  Torso: 1
  Back: 1
  Arm: 2
  Hand: 2
  Finger: 10
  Waist: 1
  Leg: 2
  Foot: 2
```

### Example - Centaur

```
Slots:
  Head: 1
  Face: 1
  Ears: 2
  Neck: 1
  Torso: 1
  Back: 1
  Arm: 2
  Hand: 2
  Finger: 10
  Waist: 1
  Leg: 4
  Foot: 4
  Mount: 1
```

### Example - Serpentfolk

```
Slots:
  Head: 1
  Face: 1
  Ears: 2
  Neck: 1
  Torso: 1
  Back: 1
  Arm: 2
  Hand: 2
  Finger: 10
  Waist: 1
  Tail: 1
```

**Rule:** If a slot type is not listed in a race's definition, that race has 0 of that slot.

## Equipped vs Carried

Every item an entity possesses is either Equipped or Carried.

| State | Definition | Mechanical Effect |
|-------|------------|-------------------|
| **Equipped** | In a slot, actively worn/wielded | Grants all item benefits |
| **Carried** | In inventory, not slotted | No mechanical benefit |

Only Equipped items grant their mechanical effects - stat bonuses, abilities, absorption, damage bonuses. Carried items exist for narrative, trading, and future use.

### Example

```
Equipped:
  Hand: Longsword (+2 damage)
  Torso: Chainmail (+4 Absorption)
  Finger: Ring of Protection (+1 REF)

Carried:
  Backup Dagger
  Healing Potion x3
  50 gold
  Rope
```

Only the Longsword, Chainmail, and Ring provide benefits. Everything else is just inventory.

## Item Structure

Every item in TDGS follows a consistent structure.

### Required Fields

| Field | Description |
|-------|-------------|
| Name | Item name |
| Weight | In Weight Units (WU) |

### Required If Equippable

| Field | Description |
|-------|-------------|
| Slot Requirements | Slot type(s) and cost per type |
| Equip Speed | Action (default), Free, or X Actions |

### Optional Fields

| Field | Description |
|-------|-------------|
| Abilities Granted | Skills, Spells, Traits while equipped |
| Stat Bonuses | +X to stat while equipped |
| Absorption | Damage reduction (armor) |
| Damage Bonus | +X damage (weapons) |
| Value | Cost/price |
| Rarity | Common, Uncommon, Rare, etc. |
| Description | Flavor text |

## Slot Cost

Items define which slots they require and how many.

**Rule:** Entity must have ALL required slots available to equip an item.

A Human with Hand: 2 cannot equip a weapon requiring Hand: 4. A four-armed creature with Hand: 4 can.

| Item | Slot Requirements |
|------|-------------------|
| Longsword | Hand: 1 |
| Greatsword | Hand: 2 |
| Quad-Blade | Hand: 4 |
| Ring | Finger: 1 |
| Large Ring | Finger: 2 |
| Full Plate | Torso: 1, Arm: 2, Leg: 2 |

Some items span multiple slot types. Full Plate requires Torso AND Arms AND Legs. All must be available.

## Slot Changes

Managing equipped items during play.

| Action | Cost |
|--------|------|
| Equip item (empty slot) | Action |
| Unequip item | Action |
| Swap item (replace equipped) | Action |
| Quick Swap | Free (requires ability) |

**Swap:** Replaces an equipped item with a new one in a single Action. The replaced item goes to Carried (not dropped) unless the player chooses to drop it.

**Quick Swap:** Some class abilities or item traits grant the ability to swap equipment as a Free action.

### Design Note

> **Note:** Swap costs 1 Action (not Unequip + Equip = 2 Actions) because combat is tuned for 4-6 rounds. Requiring 2 rounds to change weapons would devastate play experience. Quick Swap exists as an ability for builds that specialize in weapon flexibility.

## Carrying Capacity

How much an entity can carry (Equipped + Carried combined).

### Formula

```
Carrying Capacity = STR × 10 × Size Multiplier (in WU)
```

| Size | Multiplier |
|------|------------|
| Tiny | ×0.25 |
| Small | ×0.5 |
| Medium | ×1 |
| Large | ×2 |
| Huge | ×4 |
| Gargantuan | ×8+ |

**Example:** A Medium creature with STR 10 can carry 100 WU.

### Containers

Containers (backpacks, bags, pouches) add to carrying capacity while equipped.

```
Backpack
Weight: 2 WU
Slot Requirements: Back: 1
Special: +20 WU carrying capacity
```

### Encumbered

If total weight exceeds carrying capacity, the entity is **Encumbered**.

**Effect:** Cannot take the Move action.

This is a simple binary rule. Content MAY define more granular penalties (half speed, stat penalties, etc.) but the engine only mandates: over capacity = no Move.

## Slot Loss

When an entity loses a slot (arm severed, hand destroyed, etc.):

- Items equipped in that slot are immediately unequipped (go to Carried)
- The entity cannot equip items requiring that slot until the slot is restored

**Example:** A character loses their left arm. Items equipped in that Arm slot and Hand slot go to Carried. They cannot equip two-handed weapons (Hand: 2) until the arm is restored.

Restoration methods (healing magic, prosthetics, etc.) are content concerns.

## Content Layer Extensions

The engine provides the framework. Content extends it.

**Cursed Items:** The engine does not define a "Locked" property. Content MAY create abilities or traits that prevent unequipping (e.g., Trait "Cursed" - cannot be unequipped by normal means).

**Attunement:** Item bonding mechanics are not engine-level. Future extensions or content may add attunement systems.

**Inventory Limits:** Beyond weight, some settings may limit item count or require specific containers. This is content-layer concern.

**Banking/Storage:** External storage (vaults, banks, stashes) is a future extension.

## Example Items

These examples demonstrate the system. They are not canonical content.

```
EXAMPLE: Longsword
Weight: 3 WU
Slot Requirements: Hand: 1
Equip Speed: Action
Damage Bonus: +2

EXAMPLE: Greatsword
Weight: 6 WU
Slot Requirements: Hand: 2
Equip Speed: Action
Damage Bonus: +4

EXAMPLE: Dagger
Weight: 1 WU
Slot Requirements: Hand: 1
Equip Speed: Free
Damage Bonus: +1

EXAMPLE: Leather Armor
Weight: 10 WU
Slot Requirements: Torso: 1
Equip Speed: 2 Actions
Absorption: 2

EXAMPLE: Full Plate
Weight: 45 WU
Slot Requirements: Torso: 1, Arm: 2, Leg: 2
Equip Speed: 10 Actions
Absorption: 6

EXAMPLE: Ring of Protection
Weight: 0 WU
Slot Requirements: Finger: 1
Equip Speed: Free
Stat Bonus: +1 REF

EXAMPLE: Backpack
Weight: 2 WU
Slot Requirements: Back: 1
Equip Speed: Action
Special: +20 WU carrying capacity
```

## Summary

| Concept | Rule |
|---------|------|
| Slot Types | 14 canonical (content may add more) |
| Racial Slots | Each race defines its own complete list |
| Equipped | In slot, grants effects |
| Carried | In inventory, no effects |
| Slot Cost | Item defines type(s) and count needed |
| Equip/Unequip/Swap | 1 Action each |
| Quick Swap | Free (requires ability) |
| Carrying Capacity | STR × 10 × Size Multiplier (WU) |
| Encumbered | Cannot Move |
| Slot Loss | Items unequipped, slot unusable |
| Units | Abstract (WU, squares); content defines scale |

## Document Status

> **Status:** Canonical

This document defines the equipment and slot system for TDGS. All items and equipment in the system conform to the structures established here.

Specific item lists, weights, and values are defined in content documents, not in this core rules document.

---
