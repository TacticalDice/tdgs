*Document 17*

# Damage

*What hurts, how it hurts, and what cares*

## Purpose

This document defines the Damage Type system in TDGS: how damage is categorized, how entities interact with different damage categories, and how resistance, vulnerability, and immunity work mechanically.

It establishes:

- What a Damage Type is
- How Damage Types are defined
- The resistance/vulnerability/immunity framework
- How typed damage flows through armor
- How Damage Types interact with conditions

This document builds upon Document 8 (Combat) and Document 7 (Abilities). Document 8 defines how damage is calculated and applied. This document defines what KIND of damage it is and what that means. All damage interactions are delivered through the Ability system established in Document 7.

## The Damage Type Truth

All damage reduces HP. One point of damage is one point of damage. That truth from Document 8 still holds.

But a sword and a fireball are not the same thing. The sword cuts. The fireball burns. A knight in plate armor doesn't care which one hits him. A fire elemental standing in lava very much does.

Without Damage Types, every source of damage is interchangeable. A dragon's fire breath and a rogue's dagger differ only in their numbers. That's fine for simple combat. It falls apart the moment you want a creature that laughs at fire but shatters when you throw ice at it.

Damage Types give content creators one tool: the ability to say "this kind of hurt is different from that kind of hurt, and here's what cares about the difference."

## What Is a Damage Type?

A Damage Type is a category that describes the nature of damage dealt.

Every instance of damage either has a Damage Type or it does not.

```
TYPED DAMAGE:    Fire, Cold, Lightning, Piercing, Necrotic, etc.
UNTYPED DAMAGE:  Raw HP loss with no category (falling, suffocation, abstract)
```

Falling off a cliff is just damage. It doesn't need a category unless the content creator wants it to have one. Drowning is just HP loss. The universe doesn't care what label you put on oxygen deprivation.

**Typed damage flows through the resistance/vulnerability/immunity system. Untyped damage does not.** Untyped damage hits, armor applies, done.

## Framework, Not Content

TDGS does not define a canonical list of Damage Types.

Same philosophy as Magic Types, Races, and Classes. TDGS defines how Damage Types work. Content defines which ones exist.

A fantasy setting might define:

```
Fire, Cold, Lightning, Poison, Necrotic, Radiant,
Piercing, Slashing, Bludgeoning, Psychic, Force, Acid
```

A sci-fi setting might define:

```
Plasma, Radiation, EMP, Kinetic, Cryo, Corrosive, Sonic
```

A horror setting might define:

```
Physical, Psychic, Spiritual, Corruption
```

Three different worlds. Same mechanical framework. The categories are different. The math is identical.

Define your Damage Types before creating abilities, equipment, and entities that reference them. You'll need the vocabulary before you can use it.

## Assigning Damage Types

Any source of damage can have a Damage Type.

### Abilities

An ability that deals damage can specify a Damage Type.

```
FIRE BOLT
Type: Spell
Damage: 2d6 Fire
Cooldown: None

SNEAK ATTACK
Type: Skill
Damage Bonus: +3 Piercing (for relevant attacks)
```

An ability's Damage Type is fixed. Fire Bolt always deals Fire damage. Always. No exceptions, no situational changes. Want lightning damage? Learn a different spell.

### Equipment

Weapons deal damage through Traits they grant while equipped.

```
LONGSWORD
Grants Trait: Slashing Weapon (+3 Slashing damage bonus)

ENCHANTED BOW
Grants Trait: Piercing Weapon (+2 Piercing damage bonus)
Grants Trait: Flame Enchantment (+1d4 Fire damage bonus)
```

A weapon can deal damage of multiple types through multiple granted Traits. The Enchanted Bow deals Piercing from its physical projectile and Fire from its enchantment. Each type is evaluated separately against the target's damage interactions.

### Natural Weapons

Entity natural weapons are Traits (as established in Document 9) and follow the same rules.

```
DRAGON CLAWS
Trait
Damage Bonus: +2d6 Slashing

DRAGON FIRE BREATH
Trait
Damage: Apparent STR Fire (Cone AoE)
Cooldown: Scene
```

### Environmental Sources

Traps, hazards, and environmental effects can specify a Damage Type.

```
Lava: 10 Fire damage per round
Acid Pool: 5 Acid damage per round
Falling: Untyped (see Document 14 for falling damage rules)
Drowning: 5 per round (Untyped)
```

Content decides what is typed and what is not.

## Damage Interactions

There are four ways an entity can interact with a Damage Type: Resistance, Vulnerability, Immunity, and Absorption.

All four are abilities. A fire elemental's Fire Absorption is a Racial Trait. A wizard's Fire Ward is a Spell granting temporary Resistance. A fireproof cloak grants a Resistance Trait while equipped. A curse inflicts Vulnerability as a Spell effect.

The six ability sources from Document 7 (Class, Race, Items, Effects, Training, Discovery) are the only way an entity acquires damage interactions. There is no separate "damage interaction" structure on entities. This document defines the mechanics. The Ability system is the delivery vehicle.

## Resistance

Resistance reduces incoming damage of a specific type.

### Formula

```
Damage Taken = Typed Damage × (1 - Resistance%)
```

An entity with a Trait granting 50% Fire Resistance takes half damage from Fire. The other half simply doesn't land. The fire washes over them and they walk through it, singed but standing.

### Examples

| Source | Resistance | Incoming Fire | Damage Taken |
|--------|-----------|---------------|--------------|
| (none) | 0% Fire | 20 | 20 |
| Fire Ward (Spell) | 25% Fire | 20 | 15 |
| Dragon Scales (Trait) | 50% Fire | 20 | 10 |
| Greater Fire Ward (Spell) | 75% Fire | 20 | 5 |

### Resistance Cap: 75%

Resistance to any single Damage Type caps at 75%. Stack all the fire wards you want. A quarter of the fire always gets through.

This mirrors the Deflection Armor cap from Document 8. True invincibility doesn't come from stacking percentages. That's what Immunity is for.

> **Note:** GMs can override this cap for their setting. The same logic from Document 8's deflection cap applies here. Want 90% Fire Resistance in your world? Your game, your rules. But stacking resistance and deflection together can push effective damage reduction very high. Break the math knowingly, not accidentally.

### Stacking

Multiple abilities granting resistance to the same type stack additively, up to the 75% cap.

```
Dragon Scales (Racial Trait):    25% Fire Resistance
Fire Ward (Spell):               25% Fire Resistance
Fireproof Cloak (Item Trait):    25% Fire Resistance

TOTAL: 75% Fire Resistance (cap reached)
```

A fourth source would change nothing. The cap holds.

## Vulnerability

Vulnerability increases incoming damage of a specific type.

### Formula

```
Damage Taken = Typed Damage × (1 + Vulnerability%)
```

An entity with 50% Cold Vulnerability takes 150% damage from Cold. Ice doesn't just hurt them. It devastates them.

### Examples

| Source | Vulnerability | Incoming Cold | Damage Taken |
|--------|--------------|---------------|--------------|
| (none) | 0% Cold | 20 | 20 |
| Cold-Blooded (Racial Trait) | 50% Cold | 20 | 30 |
| Ice Bane (Curse Spell) | 100% Cold | 20 | 40 |

### No Cap

There is no cap on vulnerability.

An entity with 200% Cold Vulnerability takes triple Cold damage. That's intentional. Finding an enemy's weakness should be devastating. If the party discovers the fire titan crumbles when you hit it with frost magic, that discovery should change the fight.

### Opposing Resistance and Vulnerability

If an entity has both resistance and vulnerability to the same type from different abilities, they offset.

```
Dragon Scales (Trait):         50% Fire Resistance
Curse of Flame (Spell Effect): 100% Fire Vulnerability

Net: 50% Fire Vulnerability
Damage Taken = Typed Damage × 1.50
```

### Stacking

Multiple sources of vulnerability to the same type stack additively.

```
Curse of Flame (Spell Effect):     50% Fire Vulnerability
Ice Elemental Body (Racial Trait): 50% Fire Vulnerability

TOTAL: 100% Fire Vulnerability (double damage)
```

## Immunity

Immunity completely negates damage of a specific type. Zero damage. Not reduced. Not mitigated. Zero.

### Formula

```
If immune to Damage Type: Damage = 0
```

Immunity is binary. You have an ability granting it or you don't. There is no partial immunity. That's what Resistance is for.

### The Minimum Damage Exception

Document 8 establishes that every hit deals at least 1 damage, regardless of armor. Immunity is the sole exception to that rule.

A fire elemental immune to Fire takes exactly 0 damage from Fire sources. Splash it with all the fire magic you want. It doesn't care. Not one point. Not a scratch.

The attack still "hits" for resolution purposes. It can trigger on-hit abilities, break concentration, or satisfy conditions that require landing a hit. But it deals no damage.

### Immunity Beats Everything

If an entity is immune to a Damage Type, vulnerability to that same type is irrelevant. Immunity wins. You can't amplify zero.

### Sources

Immunity typically comes from Racial Traits (a Fire Elemental is immune to Fire because it IS fire), powerful Spells (a Tier 5 ward), or Legendary Item Traits (artifacts of divine protection).

Immunity is rare by design. It removes an entire damage category from play. When a creature is immune to something, every character who relies on that damage type needs a new plan. Use that power carefully in content design.

### Immunity Is Not Healing

Standing in fire while immune means zero damage. It does not mean you heal. Converting damage into health is a separate and more powerful mechanic.

## Absorption

Absorption converts incoming damage of a specific type into healing.

### Formula

```
Absorbed HP  = Typed Damage × Absorption%
Remaining    = Typed Damage × (1 - Absorption%)
```

At 100% absorption, all damage heals and none gets through. At lower percentages, the entity heals a portion and takes the rest as damage.

### Examples

```
FIRE ELEMENTAL (GREATER)
Trait: Fire Absorption (100%)

Incoming: 30 Fire → Heals 30 HP, takes 0 damage
Feed it fire. It thanks you.
```

```
FIRE-ATTUNED ARMOR
Grants Trait: Partial Fire Absorption (50%)

Incoming: 30 Fire → Heals 15 HP, takes 15 damage
Half the fire feeds you. The other half still burns.
```

```
FLAME DANCER
Trait: Minor Fire Absorption (25%)

Incoming: 40 Fire → Heals 10 HP, takes 30 damage
A small edge, not invincibility. Still hurts, but you heal while you burn.
```

### Absorption at 100% Implies Immunity

An entity with 100% absorption of a Damage Type is effectively immune to it. All damage converts to healing, nothing reaches HP. At less than 100%, the entity still takes the unabsorbed portion as damage. Only full absorption grants effective immunity.

### Healing Cap

Healing from absorption cannot exceed the entity's maximum HP. You can't stockpile health beyond your ceiling. Excess is wasted.

### Absorption Is Rare

This is the strongest possible interaction with a Damage Type. Content should reserve it for entities with a deep thematic connection to that damage category. Fire elementals. Divine beings attuned to their domain. Ancient constructs powered by the very energy you're throwing at them. Not random soldiers with enchanted cloaks.

## Multi-Type Damage

Some effects deal damage of multiple types simultaneously.

### Split Damage

When an effect deals damage of multiple types, each type is evaluated separately through the pipeline.

```
ENCHANTED FLAME SWORD
Grants Traits: Slashing Weapon (+3), Flame Enchantment (+1d4 Fire)

Against a target with 50% Fire Resistance and 0% Slashing Resistance:
  Slashing: 3 → 3 (no resistance)
  Fire: 1d4 (say 3) → 1.5, rounded to 2 (50% resistance)
  Total bonus damage: 5
```

Resistance to one type does not affect the other. A creature resistant to Fire still takes full Slashing from an enchanted flame sword.

### Rounding

When resistance or vulnerability produces a fractional result, round down. Always round down. Consistent with all TDGS rounding.

## The Damage Pipeline

Document 8 defines how damage flows from attack to HP. Damage Types extend this pipeline. The updated pipeline has two phases.

### Phase 1: Flat Reduction

```
1. Calculate raw damage (stat + bonus, per Document 8)
2. Ablative armor absorbs (pool reduced by raw amount)
   → Remaining damage continues to Phase 2
```

Ablative absorption is a flat subtraction. The shield takes the hit before anything else. Order matters here because subtraction and multiplication don't commute.

### Phase 2: Percentage Reductions

```
3. Apply all percentage modifiers multiplicatively:
   - Deflection armor (percentage, per Document 8)
   - Resistance or Vulnerability (percentage, by Damage Type, this document)
4. Minimum 1 damage if the attack hit (unless Immune or fully Absorbed)
```

All percentage modifiers in Phase 2 compound multiplicatively. Because multiplication is commutative, the order between deflection, resistance, and vulnerability does not matter. The math produces the same result regardless of sequence.

### Pipeline Examples

**Fire damage against an armored, resistant target:**

```
Incoming: 40 Fire damage

Phase 1:
  Ablative Shield absorbs 10 → 30 remaining

Phase 2:
  Deflection Armor: 50% → 30 × 0.50 = 15
  Fire Resistance (Trait): 25% → 15 × 0.75 = 11.25 → 11 (round down)

Result: 11 Fire damage to HP
```

**Piercing damage against the same target:**

```
Incoming: 40 Piercing damage

Phase 1:
  Ablative Shield absorbs 10 → 30 remaining

Phase 2:
  Deflection Armor: 50% → 30 × 0.50 = 15
  Fire Resistance: does not apply (wrong type)

Result: 15 Piercing damage to HP
```

Armor reduces everything. Resistance only cares about its matching type.

**Cold damage against a vulnerable target:**

```
Incoming: 40 Cold damage

Phase 1:
  No ablative armor → 40 remaining

Phase 2:
  Deflection Armor: 50% → 40 × 0.50 = 20
  Cold Vulnerability (Trait): 50% → 20 × 1.50 = 30

Result: 30 Cold damage to HP
```

Finding the weakness matters even through armor.

## Conditions and Damage Types

Document 8 defines conditions (Burning, Bleeding, Poisoned, etc.). Damage Types formalize the connection between conditions and damage categories.

### Condition Damage Types

Conditions that deal damage over time should specify a Damage Type when the category is meaningful.

```
BURNING:    Fire damage per round
BLEEDING:   Untyped (blood loss, not an elemental category)
POISONED:   Poison damage over time (if the poison deals ongoing damage)
```

Whether a condition's damage is typed or untyped is a content decision. Bleeding is a good example of a condition where typing adds nothing. What type is blood loss? It's just HP leaving the body.

### Conditions and Immunity

If an entity is immune to a Damage Type, it is immune to conditions whose damage is entirely of that type.

A fire-immune entity cannot be set Burning by fire effects. The condition deals Fire damage per round. Fire damage against an immune entity is zero. A condition that deals zero damage per round has no meaningful effect, so it does not apply.

However, immunity to Fire does not protect against conditions caused by other means. A fire-immune entity can still be grappled by a burning creature. The grapple works. The fire doesn't.

### Gaining Immunity to an Active Condition

If an entity is already Burning and then gains Fire Immunity (from a Spell, an Item, or any other ability source), the Burning condition remains but deals zero damage for its remaining duration. The condition is not retroactively removed. It simply has no effect while immunity persists.

If the immunity expires before the condition does, the condition resumes dealing damage normally.

Content may define specific abilities that explicitly cleanse conditions on application. "Fire Shield: grants Fire Immunity and removes all active Fire conditions." That's a content decision layered on top of the base mechanic.

## Weapons and Default Damage Types

Weapons deal physical damage through Traits they grant while equipped. Content defines which physical Damage Types exist.

A typical fantasy setting:

```
Slashing:    Swords, axes, claws
Piercing:    Spears, arrows, daggers, bites
Bludgeoning: Hammers, maces, fists
```

Content can combine these into a single "Physical" type if the distinction doesn't matter for the setting. A horror game where the difference between a sword and a hammer is irrelevant might define:

```
Physical:    All mundane damage
Supernatural: All non-mundane damage
```

Two types instead of twelve. Same framework. The granularity is a content decision. TDGS provides the mechanism. Content chooses the resolution.

## Summary Tables

### Damage Interaction Types

| Interaction | Effect | Cap | Stacking | Delivered By |
|-------------|--------|-----|----------|-------------|
| Resistance | Reduces typed damage by X% | 75% | Additive | Traits, Spells, Skills |
| Vulnerability | Increases typed damage by X% | None | Additive | Traits, Spells, Skills |
| Immunity | Negates typed damage entirely | N/A | Binary | Traits, Spells, Skills |
| Absorption | Heals X%, remaining (1-X%) dealt as damage | Max HP | N/A | Traits, Spells, Skills |

### Damage Pipeline

| Phase | Step | Applies To | Source |
|-------|------|-----------|--------|
| 1 | Calculate raw damage | All | Stat + Bonus (Doc 8) |
| 1 | Ablative armor absorbs | All | Ablative pool (Doc 8) |
| 2 | Deflection armor reduces | All | Deflection % (Doc 8) |
| 2 | Resistance/Vulnerability | Typed only | Abilities (this doc) |
| - | Minimum 1 damage | All except Immune/Absorbed | Core rule (Doc 8) |

### Interaction Priority

| Situation | Resolution |
|-----------|-----------|
| Resistance + Vulnerability (same type) | Offset: net percentage applied |
| Immunity + Vulnerability (same type) | Immunity wins |
| Absorption + any (same type) | Absorption wins |
| Absorption < 100% (same type) | Heal X%, take remainder |
| Multiple resistances (same type) | Additive, capped at 75% |
| Multiple vulnerabilities (same type) | Additive, no cap |

## Document Status

> **Status:** Canonical

This document defines the Damage Type framework for TDGS. All typed damage, resistance, vulnerability, immunity, and absorption in the system conform to the rules established here.

All damage interactions are delivered through the Ability system (Document 7). This document defines no new entity-level structures.

Specific Damage Type lists are defined in content documents (setting guides, bestiaries, etc.), not in this core rules document.

---
