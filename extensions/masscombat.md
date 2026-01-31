*Extension*

# Mass Combat

*Rules for armies, units, commanders, orders, and morale. Scales TDGS from individual heroes to clashing battalions.*

## Purpose

This document extends TDGS to handle warfare. It defines how groups of soldiers function as single game entities, how commanders issue orders and inspire troops, and how morale can break an army faster than steel.

Mass combat uses the same core resolution (d20 + (Stat - Stat) >= 11) as everything else in TDGS. Units are entities with stats. Commanders provide bonuses. The math scales seamlessly from duels to sieges.

## Core Concept

**Units are Entities.** A squad, company, or battalion is a single Entity with Race (unit type), Class (training), nine stats, HP, and abilities. The rules don't change; the scale does.

**Commanders provide CHA bonuses to morale.** Units without commanders can still fight, but they crumble faster under pressure.

**Orders shape behavior.** Attack, Hold, Charge, Retreat—each order modifies how a unit acts in combat.

**Morale determines survival.** Most armies break before they die. Routing spreads like fire.

## Units

### Unit Stats

Units have the same nine stats as any Entity. Physical stats represent collective soldier quality; mental stats represent training, doctrine, and unit properties.

| Stat | Represents |
|------|------------|
| STR | Collective fighting power |
| DEX | Coordination, formation precision |
| REF | Reaction speed as a group |
| CON | Staying power, discipline under fire |
| MOV | March speed, tactical mobility |
| INT | Tactical adaptability |
| WIS | Situational awareness |
| CHA | Unit cohesion, esprit de corps |
| LUK | Fortune as a group |

### Unit HP

Units calculate HP the same way as any Entity: **HP = CON × 5**. A unit with CON 50 has 250 HP. This represents the unit's ability to sustain casualties and keep fighting.

### Unit Scale

Unit race defines approximate soldier count and stat ranges. Larger formations have higher stats but move slower.

| Unit Type | Approx. Size | Typical Stat Range |
|-----------|--------------|-------------------|
| Squad | 5–12 | 10–30 |
| Platoon | 25–50 | 25–45 |
| Company | 100–200 | 35–60 |
| Battalion | 500–1000 | 50–80 |
| Regiment | 2000–5000 | 65–100 |

### Unit Creation

Units are created like any Entity: Race + Class. Race defines base stats and formation type; Class defines training and abilities. Content provides unit races (Infantry Company, Cavalry Squadron) and classes (Veteran, Elite Guard).

### Unit Progression

Units earn XP from battle per standard Entity rules (Document 12). They can also earn XP from training during downtime. Units that survive battles together become more effective.

## Command

### Commanders

A commander is any Entity (hero, NPC, or even another unit) that issues orders to units. Commanders provide CHA bonuses to morale checks for units they command.

### CHA Bonus

**Formula:** CHA ÷ 10 (minimum +1)

| CHA | Bonus |
|-----|-------|
| 1–10 | +1 |
| 11–20 | +2 |
| 21–30 | +3 |
| 31–40 | +4 |
| 50 | +5 |

### Command Structure

**Direct Command:** One unit receives full CHA bonus. This is the commander's personal attention.

**Extended Command:** Additional units equal to CHA bonus receive half CHA bonus (rounded down). A CHA 30 commander (+3) can extend command to 3 more units at +1 each.

**Command Range:** CHA in squares. A CHA 30 commander has a 30-square command radius.

### Lieutenants

Lieutenants are just other commanders. An army can have multiple commanders, each with their own units under direct and extended command. There is no special lieutenant mechanic—it's commanders all the way down.

### Chain of Command

**Commander Lost:** When a commander is killed or incapacitated, their units must make immediate morale checks. Units then become uncontrolled until claimed by another commander.

**Claiming Units:** Release costs Free Action. Claiming a unit costs an Action.

**Uncontrolled Units:** No CHA bonus to morale. Morale check becomes: d20 + (CON − Threat) ≥ 11.

**Exposed Commander:** When a commander's directly commanded unit is destroyed, the entity that destroyed it gets one free attack on the commander. Extended command units do NOT trigger this—only the single unit under direct command.

## Orders

### Issuing Orders

Commanders issue orders on their turn. Orders are executed when the unit acts (on the unit's REF turn).

- **Standing Order:** Free Action (no change from current order)
- **New Order:** Action (changes unit behavior)

### Order Types

| Order | Effect |
|-------|--------|
| Attack | Engage nearest enemy. Standard combat. |
| Hold | +10% REF. No movement. Can attack enemies that enter range. |
| Take Cover | +10% REF vs ranged. Limited movement. |
| Charge | +10% STR, −10% REF until start of next turn. Move toward enemy, stop when adjacent. |
| Retreat | Move away from nearest enemy. No opportunity attacks suffered. Cannot use if surrounded. |

### Percentage Bonuses

**Formula:** Stat ÷ 10 (minimum +1)

A unit with STR 50 receiving +10% STR gains +5 STR. A unit with REF 35 receiving +10% REF gains +3 REF (minimum +1).

## Morale

### Morale Checks

**Formula:** d20 + (Unit CON − Threat Value) + Commander CHA Bonus ≥ 11

Luck applies per Document 4. This is a d20 resolution roll.

### Morale Triggers

| Trigger | Threat Value |
|---------|--------------|
| 50% HP | 10 |
| 25% HP | 14 |
| Commander Lost | 12 |
| Adjacent Friendly Breaks | 10 |
| Surrounded | 12 |
| Terrifying Enemy | Enemy's full CHA |

Each trigger fires once when the condition first occurs (the shock of the moment).

### Terrifying Trait

Content may assign the Terrifying trait to entities of overwhelming power or dread (dragons, undead hordes, legendary warriors). When a unit first engages a Terrifying entity (attacks, is attacked, or is targeted by an ability), it must check morale with Threat Value equal to the Terrifying entity's full CHA.

### Morale Cascade

When a unit breaks, adjacent friendly units must check morale (Threat Value 10). Adjacent follows Document 14's adjacency rules.

**Resolution Order:** Lowest CON to highest. Weakest units check first. If they break, this may trigger additional cascades before stronger units have rolled.

> **Note:** One weak unit crumbles, neighbors check, rout spreads through an army. Position your commander to prevent this. Target the enemy's weak point to start a cascade.

## Breaking and Routing

### Failed Morale Check = Routed

The unit flees toward safety. They can be rallied.

### 0 HP = Destroyed

The unit is gone. Too many casualties, survivors scattered beyond recovery. Cannot be rallied.

### Routed Units

A routed unit:

- Moves full MOV toward safety each turn
- Cannot attack
- Cannot receive orders
- Triggers opportunity attacks when fleeing past enemies (per Document 14)

**Safety Priority:**

1. Friendly board edge (if one exists)
2. Toward nearest friendly commander
3. Directly away from the threat that caused the rout

**Reaching Safety:** A routed unit that reaches the friendly board edge is removed from the battle but not destroyed. They cannot return this engagement.

## Cornered Units

When a routed unit has no escape route, they make a second morale check:

```
d20 + (Unit CON - Original Threat Value) + Commander CHA Bonus (if in range) >= 11
```

**Pass:** Last stand. The unit is no longer routed. They can receive orders and act normally, retaining a +10% STR bonus from desperation until no longer cornered.

**Fail:** Surrender or destroyed (based on enemy—honorable foes take prisoners, monsters don't).

> **Note:** Cornering a routed unit isn't automatically winning. Historically, trapped units sometimes fight with desperate ferocity. Do you pursue and corner, or leave them an escape route?

## Rally

Commanders can attempt to recover routed units.

- **Cost:** Action
- **Range:** Commander's CHA in squares
- **Roll:** d20 + (Commander CHA − Threat Value that caused rout) ≥ 11
- **Success:** Unit stops fleeing, no longer routed. Defaults to Attack order. Can act next round at current HP.
- **Failure:** Unit continues fleeing. Try again next round.

**Why Rally Uses Full CHA:** Rally is the commander's raw force of will directly opposing the fear that broke the unit. Luck applies per Document 4.

## Combat

### Unit vs Unit

Standard TDGS resolution:

```
d20 + (Attacker STR - Defender REF) + modifiers >= 11
```

Units are Entities. Entities attack Entities. The formula works.

### Hero vs Unit

Heroes can attack units directly. Normal damage—no special rules. The unit's HP already scales with its size. A level 80 wizard CAN devastate a conscript army. That's Gandalf at Helm's Deep.

### Unit vs Hero

Units can attack heroes. Standard resolution. Unit stats scale with formation size. A battalion has STR 65. That's terrifying. A hero facing a battalion alone is in serious danger—as they should be.

### Turn Order

All Entities (units and heroes) act in REF order, per core rules. Units use their own REF. Commanders use their own REF. Higher REF acts first.

## Positioning

Document 14 covers positioning mechanics. All rules apply to units:

- Flanking
- Cover
- Difficult terrain
- Opportunity attacks

**Unit Facing:** Units have facing like any Entity. A unit attacked from the rear or flank suffers the same consequences as any other Entity would.

**Surrounded:** Enemies on 3+ sides of a unit (four cardinal directions). Triggers morale check (Threat Value 12).

**Unit Size:** Unit race defines grid footprint. A squad might occupy 2×2; a battalion might occupy 6×6.

## Creating Units (Content Guidance)

### Unit Race Template

```
Race: [Name]
Size: [Grid footprint]
Type: [Infantry/Cavalry/Archer/etc.]
Scale: [Approximate soldier count]
Base Stats:
  STR: [Value]
  DEX: [Value]
  REF: [Value]
  CON: [Value]
  MOV: [Value]
  INT: [Value]
  WIS: [Value]
  CHA: [Value]
  LUK: [Value]
Innate Traits: [List]
```

### Unit Class Template

```
Class: [Name]
Description: [What this training represents]
Levels: [Max level]
Progression:
  Level 1: [Abilities gained]
  Level 2: [Abilities gained]
  ...
Stat Bonuses: [Per level]
```

### Example: Infantry Company

```
Race: Infantry Company
Size: 3x3
Type: Infantry
Scale: ~100 soldiers
Base Stats:
  STR: 40, DEX: 35, REF: 38, CON: 42, MOV: 6
  INT: 30, WIS: 32, CHA: 28, LUK: 10
Innate Traits: Formation Fighting
```

### Example: Veteran Class

```
Class: Veteran
Description: Battle-hardened survivors
Levels: 5
Progression:
  Level 1: Steady (+2 CON)
  Level 2: Disciplined Fire (ranged attacks ignore partial cover)
  Level 3: Hold the Line (+2 REF when using Hold order)
  Level 4: Battle Sense (+2 WIS)
  Level 5: Unbreakable (reroll one failed morale check per battle)
Stat Bonuses: +1 CON per level
```

## XP and Mass Combat

### No XP for Commanders

Commanding units does not award XP to the commander. TDGS awards XP for facing danger. A commander directing troops from behind the lines is not personally at risk. The units earn XP. The commander earns victory.

**However:** A commander who fights personally earns XP for that combat. Leading a charge, dueling the enemy commander, casting fireballs into the enemy formation—that's danger. That earns XP.

### Unit XP

Units earn XP from battle per standard Entity rules (Document 12). They also earn XP from training during downtime. The unit faced danger, survived, and learned.

## Summary

| Concept | Rule |
|---------|------|
| Units | Entities with Race + Class |
| Unit Stats | Physical = soldier quality, Mental = training/unit properties |
| Unit HP | CON × 5 (standard Entity calculation) |
| CHA Bonus | CHA ÷ 10 (minimum +1) |
| Direct Command | 1 unit, full CHA bonus |
| Extended Command | CHA bonus units, half CHA bonus each |
| Command Range | CHA in squares |
| New Order | Action cost |
| Standing Order | Free Action |
| Morale Check | d20 + (CON − Threat) + CHA Bonus ≥ 11 |
| Morale Cascade | Adjacent units check when one breaks |
| Routed | Flees toward safety, can be rallied |
| Rally | Action, d20 + (CHA − Threat) ≥ 11 |
| Cornered | Second check: pass = last stand, fail = surrender/destroyed |
| Commander XP | None from commanding; yes from personal combat |

## Status

> **Status:** Canonical

This extension builds on core TDGS rules. It does not redefine them.

**Core documents referenced:** Document 3, Document 4, Document 12, Document 14

---
