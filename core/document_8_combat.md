*Document 8*

# Combat

*How damage is dealt, absorbed, and survived*

## Purpose

This document defines the combat mechanics of TDGS: how entities take damage, resist damage, and ultimately live or die.

It establishes:

- Hit Points and death
- Damage calculation
- Armor systems (Ablative and Deflection)
- Healing and recovery
- Conditions (buffs and debuffs)

This document builds upon Document 3 (Resolution), Document 5 (Action Taxonomy), Document 6 (Action Economy), and Document 7 (Abilities). Resolution determines if you hit. This document determines what happens when you do.

## The Combat Truth

In TDGS, damage is absolute. One point of damage to a dragon is one point of damage to a peasant. The dragon simply has more hit points to lose.

This means a peasant CAN hurt a dragon. Not easily. They probably can't even land a hit given the stat differential. But if that desperate spear thrust lands? The dragon bleeds. Every hit matters. Even gods bleed.

What separates heroes from peasants isn't magical durability. It's:

- **Higher stats** (from training, items, investment)
- **Better armor** (evasion to avoid, absorption to reduce)
- **Better skills** (active defense, damage mitigation)

Catch a hero sleeping naked? They're just as tender as anyone else.

## Hit Points

Hit Points (HP) represent how much punishment an entity can sustain before death.

### HP Formula

```
HP = Apparent CON × 5
```

**Apparent CON** is your base Constitution plus all bonuses from items, gear, skills, effects, and narrative sources.

| Entity | Base CON | Bonuses | Apparent CON | HP |
|--------|----------|---------|--------------|-----|
| Peasant | 8 | +0 | 8 | 40 |
| Peasant with Amulet | 8 | +4 | 12 | 60 |
| Soldier | 12 | +0 | 12 | 60 |
| Barbarian | 18 | +5 | 23 | 115 |
| Dragon | 40 | +10 | 50 | 250 |
| God | 80 | +20 | 100 | 500 |

### HP Does Not Scale With Level

A Level 50 warrior with CON 12 has the same HP as a Level 1 peasant with CON 12: 60 HP.

Experience doesn't make you physically tougher. Training might increase your CON. Gear might add CON bonuses. But your body is your body. Level doesn't magically create more blood.

Veterans survive longer because they hit harder, dodge better, and wear superior armor. Not because they have inflated hit point pools.

### Knockout Threshold

When an entity reaches **5% of their maximum HP** (rounded down), they fall unconscious.

| Max HP | Knockout At |
|--------|-------------|
| 40 | 2 HP |
| 60 | 3 HP |
| 100 | 5 HP |
| 200 | 10 HP |
| 500 | 25 HP |

Knockout is a warning. The next hit might kill.

### Death

When an entity reaches **0 HP**, they die.

No death saves. No bleeding out timers. No dramatic last words while the cleric scrambles for a heal. Zero is zero. Dead is dead.

This is intentional. TDGS combat is lethal. When HP gets low, the stakes are real. Every hit in that danger zone between knockout and death could be the last.

## Damage

When an attack hits, it deals damage. Damage reduces the target's HP.

### Damage Formula

**Melee:**
```
Damage = Apparent STR + Weapon Damage Bonus
```

**Ranged:**
```
Damage = Apparent DEX + Weapon Damage Bonus
```

**Spells:**
```
Damage = Apparent INT (Arcane) or WIS (Divine) + Spell Damage Bonus
```

### Examples

| Attacker | Stat | Weapon | Bonus | Damage |
|----------|------|--------|-------|--------|
| Peasant | STR 8 | Fists | +0 | 8 |
| Soldier | STR 12 | Sword | +2 | 14 |
| Barbarian | STR 18 | Greatsword | +5 | 23 |
| Archer | DEX 14 | Longbow | +3 | 17 |
| Wizard | INT 15 | Fire Bolt | +3 | 18 |
| Dragon | STR 40 | Claws | +5 | 45 |
| God | STR 80 | Divine Fist | +10 | 90 |

### Damage Scales With Power

At parity (similar-powered entities fighting each other), combat takes roughly 4-5 hits to kill. This remains consistent across all power tiers because both HP and damage scale with stats.

| Fight | Damage | HP | Hits to Kill |
|-------|--------|-----|--------------|
| Peasant vs Peasant | ~8 | ~40 | 5 |
| Soldier vs Soldier | ~14 | ~60 | 4-5 |
| Dragon vs Dragon | ~45 | ~250 | 5-6 |
| God vs God | ~90 | ~500 | 5-6 |

Lethality is consistent. Scale is different.

### Damage Variance

The damage bonus from weapons, spells, and abilities can be:

- **Flat:** +5 (always adds 5)
- **Dice:** +1d6 (adds 1-6, rolled each time)
- **Both:** +2 + 1d6 (adds 2 + 1-6)

Content defines which format each effect uses. A simple dagger might be +1. A volatile magic sword might be +1d8.

This applies to ALL damaging effects: weapons, spells, natural weapons, abilities, traps, environmental hazards. If it deals damage, the bonus can include dice.

Flat bonuses are predictable. Dice add drama. Choose based on the feel you want.

### Minimum Damage

Every hit that lands deals **at least 1 damage**, regardless of armor.

You hit? You scratch the paint. No attack is completely negated. Even the peasant poking a god with a pointy stick draws a single drop of divine blood.

## Weapon Properties

Weapons have two separate properties that affect combat. For full item structure including slot costs and carrying rules, see Document 15 (Equipment & Slots).

### Hit Bonus

Adds to the resolution roll (d20 + mods). Each +1 equals approximately 5% better chance to hit.

### Damage Bonus

Adds to damage dealt on a successful hit. Can be flat (+3), dice-based (+1d6), or both (+2 + 1d4). Content defines which.

### Range

Weapons have a range band indicating optimal engagement distance.

| Range Type | Optimal Band | Extended (-2) | Maximum |
|------------|--------------|---------------|---------|
| Melee | Adjacent | — | Adjacent |
| Reach | Adjacent, Near | — | Near |
| Thrown | Near | Far | Far |
| Ranged | Far | Distant | Distant |
| Long Range | Distant | — | Distant |

- **Optimal:** No penalty. This is where the weapon is designed to work.
- **Extended:** -2 to hit. One band beyond optimal. Pushing the weapon's limits.
- **Beyond Maximum:** Cannot hit. Out of range entirely.

Melee weapons have no extended range. You're in arm's reach or you're not.

Reach weapons threaten both Adjacent AND Near ranges. This is their advantage—zone control without sacrificing close combat. Opportunity attacks trigger from either range for reach weapons.

See Document 14 (Movement & Positioning) for range band definitions: Adjacent (0-1 squares), Near (2-4 squares), Far (5-10 squares), Distant (11+ squares).

### Example Weapons

These properties are **completely separate**. A weapon can have any combination:

| Weapon | Hit Bonus | Damage Bonus | Range | Notes |
|--------|-----------|--------------|-------|-------|
| Dagger | +0 | +2 | Melee | Simple, concealable |
| Longsword | +1 | +4 | Melee | Balanced, reliable |
| Spear | +0 | +3 | Reach | Keeps enemies at distance |
| Throwing Knife | +0 | +2 | Thrown | Expendable |
| Shortbow | +1 | +3 | Ranged | Quick, accurate |
| Longbow | +0 | +4 | Long Range | Powerful, slow |
| Chaotic Blade | +1 | +2d4 | Melee | Unpredictable but exciting |

This separation honors our principle: **Resolution and Magnitude Never Mix**. What makes you more likely to hit is independent of what makes you hit harder.

## Armor

Armor protects you from damage. TDGS has two types of armor absorption: **Ablative** and **Deflection**. For armor as equipment (slot costs, wearing rules), see Document 15 (Equipment & Slots).

### Ablative Armor (Pool-Based)

Ablative armor has a damage pool. It absorbs incoming damage until depleted.

```
ABLATIVE ARMOR:
  Has a pool of HP
  Absorbs damage until pool is empty
  Once depleted: no protection until restored/replaced
```

**Example: Energy Shield (Pool: 100)**

```
Hit for 30 damage → Shield absorbs 30, pool now 70. You take 0.
Hit for 30 damage → Shield absorbs 30, pool now 40. You take 0.
Hit for 60 damage → Shield absorbs 40, depleted. You take 20.
Shield is now empty.
```

Ablative armor is your buffer. It takes the hits so you don't have to. Until it runs out.

**Durability:** Each ablative item defines whether it:

- **Destroyed when depleted** (consumable barriers, one-use shields)
- **Recharges between scenes** (energy shields, regenerating barriers)

This is a property of the item, not a universal rule.

**Cap:** There is no cap on ablative pool values. A divine barrier could have 10,000 HP. Content defines what exists; the engine defines how it works.

### Deflection Armor (Percentage-Based)

Deflection armor reduces incoming damage by a percentage. It persists until destroyed or removed.

```
DEFLECTION ARMOR:
  Reduces damage by a percentage
  Always active while worn
  Degrades only on critical magnitude (rare)
```

**Example: Plate Armor (50% Deflection)**

```
Hit for 30 damage → Reduced by 50% to 15. You take 15.
Hit for 30 damage → Reduced by 50% to 15. You take 15.
Hit for 100 damage → Reduced by 50% to 50. You take 50.
Armor still works.
```

Deflection armor is reliable. It always helps. But it never fully protects you.

### Deflection Cap: 75%

No matter how much deflection you stack, you always take at least 25% of incoming damage. True invincibility doesn't exist in TDGS.

> **Note:** GMs can override this cap for their setting. Want 100% deflection armor in your world? Your game, your rules. But understand: true invincibility breaks combat math. If nothing can hurt someone, why roll? We provide the physics. You decide if you want to break them.

### Deflection Degradation

Deflection armor degrades when hit by a critical hit (natural 20) with maximum magnitude (4 on the magnitude die).

```
Trigger: Crit (nat 20) + Magnitude 4
Effect: -10% deflection for rest of scene
Resets between scenes (assumed repaired/maintained)
Probability: ~1.25% per attack
```

Most crits don't damage armor. Only the most devastating blows (mag 4) punch through. When they do, your armor is compromised. But only until you can tend to it.

### Stacking: Ablative First

When you have both ablative and deflection armor, **ablative absorbs first**, then deflection reduces the remainder.

**Example: Shield (Ablative 50) + Plate (Deflection 50%)**

```
Hit for 80 damage:
  → Shield absorbs 50, depleted
  → 30 remains, plate reduces by 50%
  → You take 15

Next hit for 80 damage:
  → Shield depleted, no ablative
  → Plate reduces 80 by 50%
  → You take 40
```

Your ablative buffer goes first. Once it's gone, you're down to base armor.

### Evasion

Some armor also provides **Evasion**: a bonus to REF that makes you harder to hit in the first place.

```
EVASION: Adds to Apparent REF for defense

Light Leather: +2 Evasion, 10% Deflection
Chain Mail: +0 Evasion, 30% Deflection  
Full Plate: -2 Evasion, 50% Deflection
```

Light armor helps you dodge. Heavy armor helps you tank. Choose your survival strategy.

## The Three Layers of Survival

Survival in TDGS has three layers:

| Layer | What It Does | Source |
|-------|--------------|--------|
| 1. REF (Avoid) | Determines if hit lands at all | Base REF + Evasion |
| 2. Absorption (Reduce) | Reduces damage taken | Ablative pools, Deflection % |
| 3. HP (Survive) | How much you can take | Apparent CON × 5 |

A hit must pass through all three layers:

- Does it beat your REF? (Resolution)
- How much gets through armor? (Ablative → Deflection → Minimum 1)
- Can your HP absorb what's left? (HP)

Master all three and you're hard to kill. Neglect any one and you have a weakness to exploit.

## Healing

HP can be restored through rest and healing effects.

### Rest

**Short Rest (minutes):**
```
Recover 25% of maximum HP
Requires: Brief pause, no combat, catching breath
```

**Long Rest (hours/sleep):**
```
Recover to full HP
Requires: Extended rest, typically overnight
```

### Healing Effects

Spells, potions, and abilities that restore HP use **percentages**, not flat amounts.

```
Heal Spell: Restore 20% HP
Greater Heal: Restore 40% HP
Healing Potion: Restore 15% HP
```

**Why percentages?** They scale automatically across power tiers.

| Target | Max HP | 20% Heal |
|--------|--------|----------|
| Peasant | 40 | +8 HP |
| Soldier | 60 | +12 HP |
| Dragon | 250 | +50 HP |
| God | 500 | +100 HP |

The same spell works for everyone. No need for tiered healing lists.

## Conditions

Conditions are temporary states that affect an entity's capabilities. They include both **Debuffs** (negative effects) and **Buffs** (positive effects).

### Condition Framework

Every condition follows this structure:

```
NAME:       What it's called
TYPE:       Buff or Debuff
EFFECT:     What it does mechanically
DURATION:   Rounds / Scene / Day / Until Removed
STACKING:   Yes or No
SOURCE:     What can apply it
```

### Applying and Removing Conditions

Conditions can be applied by:

- Weapons (poison blade causes Poisoned)
- Spells (fear spell causes Frightened)
- Abilities (grapple action causes Grappled)
- Narrative (GM applies Burning when you fall in lava)

Conditions can be removed by:

- Duration expiring
- Specific actions (standing removes Prone)
- Healing/cleansing effects
- Narrative resolution

## Core Debuffs

These are the standard negative conditions in TDGS.

### Grappled

```
Type:       Debuff
Effect:     Cannot move. Actions limited to: Attack grappler,
            Attempt escape (STR vs STR)
Duration:   Until escaped or grappler releases
Stacking:   No
Source:     Grapple action, certain abilities
```

### Prone

```
Type:       Debuff
Effect:     -2 to REF vs melee (easier to hit up close)
            +2 to REF vs ranged (smaller profile)
            Standing up costs your Action
Duration:   Until you stand (costs Action)
Stacking:   No
Source:     Shove action, knockdown effects, voluntary
```

### Stunned

```
Type:       Debuff
Effect:     Cannot take Actions, Instants, or Interrupts
            REF reduced to 0 (auto-hit on anything but nat 1)
Duration:   Rounds (defined by source)
Stacking:   No (duration refreshes)
Source:     Massive damage, head trauma, certain spells/abilities
```

### Frightened

```
Type:       Debuff
Effect:     -2 to all rolls while source of fear is visible
            Cannot willingly move closer to source of fear
Duration:   Scene or Until source removed/defeated
Stacking:   No
Source:     Intimidate action, terror abilities, narrative
```

### Poisoned

```
Type:       Debuff
Effect:     -2 to STR, DEX, and REF (body weakened)
            May deal damage over time (defined by poison source)
Duration:   Scene or Until treated
Stacking:   No (but different poisons can stack)
Source:     Poison weapons, venomous creatures, traps, ingested
```

### Bleeding

```
Type:       Debuff
Effect:     Lose X HP at start of each round (X defined by source)
Duration:   Until treated or Scene ends
Stacking:   Yes (multiple bleeds add together)
Source:     Slashing/piercing crits, certain weapons, abilities
```

### Blinded

```
Type:       Debuff
Effect:     -4 to attacks and REF (can't see incoming)
            Auto-fail sight-based WIS checks
Duration:   Rounds or Until removed
Stacking:   No
Source:     Darkness, flash effects, eye damage, spells
```

### Deafened

```
Type:       Debuff
Effect:     Auto-fail hearing-based WIS checks
            Cannot benefit from verbal commands/warnings
Duration:   Rounds or Until removed
Stacking:   No
Source:     Loud explosions, ear damage, spells
```

### Unconscious

```
Type:       Debuff
Effect:     Cannot take any actions
            REF reduced to 0 (auto-hit on anything but nat 1)
            Unaware of surroundings
Duration:   Until awakened (damage, allies, time)
Stacking:   No
Source:     Knockout (5% HP), sleep effects, head trauma, spells
```

### Paralyzed

```
Type:       Debuff
Effect:     Cannot move or take physical actions
            REF reduced to 0 (auto-hit on anything but nat 1)
            Mental actions still possible (if any)
Duration:   Rounds or Until removed
Stacking:   No
Source:     Paralysis poison, certain spells, nerve damage
```

### Slowed

```
Type:       Debuff
Effect:     MOV halved
            Cannot take Step as free action (must use Move action)
            -2 to REF
Duration:   Rounds or Until removed
Stacking:   No
Source:     Encumbrance, cold effects, certain spells, exhaustion
```

### Burning

```
Type:       Debuff
Effect:     Lose X HP at start of each round (X defined by source)
            Can spread to flammable materials
            Extinguish: Action + method (water, roll on ground, etc.)
Duration:   Until extinguished
Stacking:   Yes (multiple fire sources add together)
Source:     Fire attacks, spells, environmental hazards
```

### Charmed

```
Type:       Debuff
Effect:     Cannot attack or harm the charmer
            Charmer has +4 to CHA-based actions against you
            May follow suggestions (WIS to resist harmful ones)
Duration:   Scene or Until broken (damage from charmer, allies intervene)
Stacking:   No
Source:     Charm spells, seduction abilities, certain creatures
```

## Core Buffs

These are the standard positive conditions in TDGS.

### Invisible

```
Type:       Buff
Effect:     Cannot be seen (auto-succeed Hide vs sight)
            +4 to attacks against targets unaware of you
            Attackers who can't see you have -4 to hit you
            Broken: When you attack or interact physically
Duration:   Rounds / Scene / Until broken
Stacking:   No
Source:     Spells, potions, abilities, certain gear
```

### Hasted

```
Type:       Buff
Effect:     +2 to REF
            Can take two Actions per turn instead of one
Duration:   Rounds (defined by source)
Stacking:   No
Source:     Spells, potions, certain abilities
```

### Protected

```
Type:       Buff
Effect:     +2 to REF
            +10% deflection (stacks with armor, respects 75% cap)
Duration:   Rounds / Scene (defined by source)
Stacking:   No
Source:     Spells, abilities, shields of faith
```

### Regenerating

```
Type:       Buff
Effect:     Recover X% HP at start of each round (X defined by source)
Duration:   Rounds / Scene (defined by source)
Stacking:   No (highest value wins)
Source:     Spells, potions, abilities, certain creatures (innate)
```

### Stat Buffs

Any stat can have a buff following this pattern:

```
Type:       Buff
Effect:     +2 to [STAT]
Duration:   Rounds / Scene (defined by source)
Stacking:   No (highest value wins)
Source:     Spells, potions, abilities
```

| Name | Stat |
|------|------|
| Strengthened | +2 STR |
| Quickened | +2 DEX |
| Fortified | +2 CON |
| Sharpened | +2 INT |
| Enlightened | +2 WIS |
| Emboldened | +2 CHA |
| Accelerated | +2 MOV |
| Attuned | +2 REF |

## Summary Tables

### HP and Death

| Threshold | Effect |
|-----------|--------|
| 5% HP | Knockout (Unconscious) |
| 0 HP | Death |

### Damage Formula

| Attack Type | Formula |
|-------------|---------|
| Melee | Apparent STR + Weapon Damage Bonus |
| Ranged | Apparent DEX + Weapon Damage Bonus |
| Spell (Arcane) | Apparent INT + Spell Damage Bonus |
| Spell (Divine) | Apparent WIS + Spell Damage Bonus |

### Armor Types

| Type | How It Works | Cap |
|------|--------------|-----|
| Ablative | Pool absorbs damage until depleted | None |
| Deflection | Percentage reduces all damage | 75% |

### Healing

| Method | Recovery |
|--------|----------|
| Short Rest | 25% HP |
| Long Rest | 100% HP |
| Effects | Percentage-based (varies) |

### Core Conditions Quick Reference

**Debuffs:**

| Condition | Key Effect |
|-----------|------------|
| Grappled | Cannot move, limited actions |
| Prone | -2 REF melee, +2 REF ranged |
| Stunned | No actions, REF 0 |
| Frightened | -2 all rolls, can't approach source |
| Poisoned | -2 STR/DEX/REF |
| Bleeding | X damage per round, stacks |
| Blinded | -4 attacks/REF |
| Deafened | Fail hearing checks |
| Unconscious | No actions, REF 0, unaware |
| Paralyzed | No physical actions, REF 0 |
| Slowed | Half MOV, no Step, -2 REF |
| Burning | X damage per round, stacks |
| Charmed | Can't harm charmer |

**Buffs:**

| Condition | Key Effect |
|-----------|------------|
| Invisible | Can't be seen, +4 attack, -4 to be hit |
| Hasted | +2 REF, two Actions |
| Protected | +2 REF, +10% deflection |
| Regenerating | X% HP per round |
| [Stat] Buff | +2 to specific stat |

## Document Status

> **Status:** Canonical

This document defines the combat mechanics for TDGS. All damage, armor, healing, and conditions in the system conform to the rules established here.

---

