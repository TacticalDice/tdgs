*Extension*

# Mounts & Vehicles

*Rules for mounts (creatures you ride) and vehicles (conveyances you operate)*

## Purpose

This extension defines rules for mounts (creatures you ride) and vehicles (conveyances you operate). It builds on core TDGS documents and does not redefine any core rules.

**Provide unified mechanics for:**

- Riding creatures (horses, wolves, dragons, etc.)
- Operating vehicles (wagons, chariots, ships, etc.)
- Combat while mounted or aboard vehicles
- Progression for mounts and upgrades for vehicles

## Core Distinction: Mount vs Vehicle

| Aspect | Mount | Vehicle |
|--------|-------|---------|
| **Entity Type** | Full Entity (has mind) | Inert Entity (no mind) |
| **Stats** | All 9 stats are its own | Physical stats own, mental stats borrowed from driver |
| **Agency** | Can act independently, resist, panic | Cannot act without driver |
| **Race** | Creature type (Horse, Wolf, Griffin) | Vehicle template (Wagon, Chariot, Ship) |
| **Class** | Trained abilities (War Mount, Tracker) | Inert (always Level 1, no progression) |
| **Progression** | XP from adventuring AND training | Upgrades (gold) or replacement |

> **Note:** The Trade-Off: Mounts offer more capability (independent action, progression, senses) but less reliability (can panic, resist, disobey). Vehicles offer total reliability (no panic, no resistance) but no independent capability (requires driver for everything).

## Creating Mounts

1. Select race (creature type defines base stats and innate traits)
2. Select class (if trained) or leave classless (wild)
3. Apply class abilities

**Race** defines what the creature *is*: a Horse has base stats, size Large, and innate traits like Kick.

**Class** defines what it's *trained to do*: War Mount grants War-Trained, Trample, and Charge abilities.

**Wild vs Trained:** A wild horse has the Horse race but no class levels. A trained warhorse has Horse race plus War Mount class levels. Same creature, different training.

## Creating Vehicles

1. Select race (vehicle template defines stats and traits)
2. Class is always Inert (Level 1, no progression)
3. Apply upgrades if desired

**Race (Template):** "Wagon" is a race. "War Chariot" is a race. The template defines what the vehicle *is*.

### Inert Class

- **Name:** Inert
- **Description:** For entities without agency or progression
- **Max Level:** 1
- **Abilities:** None
- **Progression:** None (cannot gain XP, cannot level)

> **Note:** The Inert class exists to satisfy the entity framework. All entities have race and class. Vehicles are entities. Therefore vehicles have class, but it is an empty one.

## Progression: Mounts

Mounts are entities. Entities that participate in challenges earn XP. Standard progression rules apply (Document 12).

### Adventuring XP

Mounts earn XP from participating in challenges. Both rider and mount receive XP. Participation is not divided. They were there, they faced danger, they get XP.

### Training XP

Downtime training is an additional XP source for mounts. Content defines costs (gold, time, trainer requirements) and XP awarded. This lets mounts progress even between adventures.

### Spending XP

Mounts spend XP on class levels and stat increases using standard progression rules.

## Progression: Vehicles

**No XP.** Vehicles cannot gain XP. The Inert class has no levels beyond 1.

**Upgrades:** Modifications, repairs, and enchantments can improve stats or add traits. Content defines costs. This is gold-based, not XP-based.

**Replacement:** Buy a better vehicle outright. Content defines vehicle catalogs and prices.

### Progression: Draft Animals

Draft animals are entities. All non-inert entities earn XP per core progression rules.

**Adventuring XP:** Draft animals pulling a vehicle through combat earn XP from challenges. If the chariot tramples goblins, the horses faced danger and survived. They earn XP.

> **Note:** A draft animal is not equipment. It is an entity with a job. The job does not remove its right to progress.

## Combat: Action Economy

### Rider and Operator

Your Action is occupied with controlling the mount or vehicle. Everything else works normally.

| Timing Type | Available? |
|-------------|------------|
| Action | Restricted to mount/vehicle operation and its abilities |
| Step | N/A (mount/vehicle provides movement) |
| Free Actions | Yes |
| Instants | Yes |
| Interrupts | Yes |

Using mount/vehicle abilities (Trample, Ram, etc.) uses your Action.

### Passengers

Passengers are not controlling the conveyance. They have nearly full action economy.

| Timing Type | Available? |
|-------------|------------|
| Action | Yes (full) |
| Step | No (moving with conveyance) |
| Free Actions | Yes |
| Instants | Yes |
| Interrupts | Yes |

**Why no Step?** Step is movement across the battlefield. Passengers are moving with the conveyance, not independently. Dismount to get your Step back.

### Mounts (While Ridden)

The rider directs. The mount responds.

| Timing Type | Available? |
|-------------|------------|
| Action | No (rider directs) |
| Step | N/A (mount IS the movement) |
| Free Actions | Yes |
| Instants | Yes (if any) |
| Interrupts | Yes (kick, bite, buck) |

## Attacking While Mounted or Operating

### Default (no special training)

- Use mount/vehicle abilities (Trample, Ram) with your Action
- Use your Interrupts (Parry, Counterspell, etc.)
- Use your Instants at round start
- Use Free Actions (shout commands, drop items)
- **CANNOT** use personal attack Actions (swing sword, cast spell)

### With appropriate Skill or Ability

- Rider with "Mounted Archery" can make ranged attacks while riding
- Charioteer with "Combat Driver" can attack while operating
- Content defines these Skills and Abilities

> **Note:** A Hunnic horse archer fires arrows at full gallop because they trained for it. An untrained rider holding the reins cannot.

**Passengers have no such restriction.** They can attack normally without special training.

> **Note:** TDGS is multiclass by design. A character who wants to excel at mounted combat or vehicle operation should consider taking a class that grants relevant Skills. A Fighter on a warhorse is a Fighter who happens to be riding. A Fighter/Cavalier on a warhorse is a mounted warrior with trained capabilities: combat Actions while riding, bonuses to mount control, charge synergies. Content should provide classes or class options for: Mounted melee combat (Cavalier, Knight), Mounted ranged combat (Horse Archer, Skirmisher), Vehicle operation (Charioteer, Pilot, Captain), Beast mastery (bonding, training, control).

## Being Attacked (Target Choice)

Attacker chooses target freely. Mount/vehicle and rider/passenger are both valid targets. No penalty for choosing either.

**Tactical options:**

- Kill the mount to strand the rider
- Kill the rider to claim the mount
- Destroy the vehicle to halt everyone
- Target the driver to leave the vehicle uncontrolled

### Driver Incapacitation

If a vehicle's driver is killed or incapacitated mid-movement:

1. Vehicle completes declared movement in a straight line
2. Vehicle stops

**Seizing control mid-movement:** Requires a relevant Interrupt ability (content-defined). Without such ability, occupants cannot react until the vehicle stops.

**Seizing control after movement:** Any occupant may take control using their Action on their turn.

## Trample

Trample applies to any mount or vehicle with the Trample trait. The physics are the same whether hooves or wheels.

**Trigger:** Trampler enters a smaller creature's square during movement.

**Resolution:** Trampler STR vs Target REF (standard resolution)

### On Success

- Target takes trample damage (defined by Trample trait)
- Target is knocked prone
- Trampler continues in direction of travel

### On Failure

- Trampler's movement ends in the square before the target
- The target braced and held the line

### Trample Distance

**Formula:** MOV / 4 (rounded down) squares in direction of travel

| Mount/Vehicle | MOV | Trample Distance |
|---------------|-----|------------------|
| Riding Horse | 10 | 2 squares |
| Warhorse | 12 | 3 squares |
| War Elephant | 8 | 2 squares |
| Dragon | 16 | 4 squares |
| War Chariot | 10 | 2 squares |

**Chain Effect:** Each creature in the trample path gets their own opposed roll. Trample continues until maximum trample distance is reached OR a creature wins the opposed roll (stopping the trampler).

### Restrictions

- Cannot trample creatures of equal or larger size
- Cannot trample the same target twice in one turn
- Target does not get an Interrupt (this is being run over, not an attack)
- Trample is part of movement, no extra Action cost

### Charge

Mounts with the Charge trait deal bonus damage after straight-line movement.

**Trigger:** 4+ squares of straight-line movement immediately before attack.

**Effect:** Bonus damage as defined by trait (e.g., "Charge: +1d6 damage").

## Mount Rules

### Any Entity Can Be a Mount

**Rule:** Any entity can be mounted by an entity at least one size smaller. Must have carrying capacity. Physics does not require a trait. Control is the question.

### Control States

| State | Behavior | Action Required |
|-------|----------|-----------------|
| Trained | Obeys commands | None |
| Untrained | Does not obey, acts on own will | Action to attempt control |
| Hostile | Actively tries to throw rider | Check each round or dismounted |

**Control Check:** Rider CHA vs Mount WIS (standard resolution)

### Mount Stats

Mounts are full Entities. All 9 stats are the mount's own. A mount can be targeted by any effect that targets entities. Fireball uses the mount's CON. Charm uses the mount's WIS.

### Mounted Movement

Use mount's MOV. Rider's MOV is irrelevant while riding.

- **Mounting:** Costs an Action
- **Dismounting:** Costs an Action

Traits MAY grant faster mounting (e.g., "Cavalry Training: Mount as a Free Action").

### Mount Damage and Death

Mount has its own health pool. Damage to mount does not affect rider.

**When mount dies or is incapacitated:**

- Rider lands prone in adjacent square (rider's choice which)
- Standing from prone costs an Action

**Airborne Mount Death:** If mount dies or is incapacitated mid-air, rider falls. Falling damage applies per Document 14: 1d6 per 2 squares, capped at 10d6 (20 squares).

### Size Compatibility (Mounts)

Mount must be at least one size category larger than the rider.

| Rider Size | Minimum Mount Size |
|------------|-------------------|
| Tiny | Small |
| Small | Medium |
| Medium | Large |
| Large | Huge |
| Huge | Gargantuan |

### Multiple Riders

Multiple riders are allowed if the mount has carrying capacity for all of them.

**Carrying Capacity:** STR x 10 x Size Multiplier (WU)

One rider controls. Additional riders are passengers. Passengers can use their full Action but have no Step.

## Vehicle Rules

### Vehicle Stats

Vehicles are Inert Entities. Physical stats are the vehicle's own. Mental stats are borrowed from the driver.

| Stat | Source |
|------|--------|
| STR | Vehicle |
| DEX | Vehicle |
| CON | Vehicle |
| MOV | Vehicle (or motive source) |
| REF | Driver |
| INT | Driver |
| WIS | Driver |
| CHA | Driver |
| LUK | Driver |

**Occupied Vehicle:** Physical attacks target the vehicle's stats. Mental attacks target the driver's stats.

**Unoccupied Vehicle:** Physical attacks target the vehicle's stats. Mental attacks auto-succeed (no resistance). Exception: Traits may grant resistance (e.g., "Warded").

### Vehicle Operation

**Basic operation:** No check required. You can drive a wagon.

**Difficult maneuvers:** Standard resolution vs terrain's virtual DEX.

**Vehicle Maneuvers Roll:** d20 + (Driver DEX - Terrain DEX) + Handling + Modifiers >= 11

**Handling** is a vehicle trait. Positive = nimble. Negative = clunky.

### Passengers and Crew

**Passengers** MAY use their full Action while aboard (they're not controlling).

**Crew Requirement (X):** Need X people or the vehicle does not move.

**Crew are passengers with jobs.** Additional crew beyond the driver are passengers. They use normal action economy for their crew tasks.

- A rower uses their Action to row
- A siege engineer uses their Action to fire the ballista
- No new mechanics; action economy applied to vehicle context

### Cover

Cover is NOT inherent to vehicles. It is defined per vehicle via the Cover trait.

| Cover Type | Effect |
|------------|--------|
| None | No cover bonus |
| Partial | +2 REF vs ranged attacks |
| Half | +4 REF vs ranged attacks |
| Full | Cannot be targeted directly |

### Vehicle Damage

Vehicles have their own health pool: **HP = CON × 5** (per standard entity rules).

**At 0 HP:** Vehicle is destroyed or disabled. Occupants must disembark or are trapped (content-defined).

### Motive Sources

**Requires Motive Source:** Vehicle has no inherent MOV. Needs draft animals, crew rowing, wind, magic, etc.

**Self-Propelled:** Vehicle has its own MOV (magical carriages, clockwork wagons, etc.). Self-propelled is exotic; most vehicles require motive sources.

### Draft Animals

Draft animals pull vehicles. Their STR and carrying capacity determine load limits.

**Draft Animal Carrying Capacity:** STR × 10 × Size Multiplier (WU)

**Load Calculation:** Total load = vehicle weight + cargo + passengers

| Condition | Effect |
|-----------|--------|
| At or under capacity | Full MOV |
| Over capacity, under 2x | Half MOV |
| Over 2x capacity | Cannot move |

**Multiple Draft Animals:** Add carrying capacities together.

## Common Mount Traits

| Trait | Description |
|-------|-------------|
| Trained | Obeys commands without check |
| War-Trained | Immune to mundane panic, +2 vs magical fear, can use offensive Interrupts |
| Skittish | -2 to rider's CHA when reasserting control |
| Loyal | +2 to rider's CHA when reasserting control |
| Aggressive | Attacks adjacent enemies without command |
| Flight | Can fly using MOV |
| Aquatic | Full MOV in water |
| Amphibious | Full MOV on land and in water |
| Burrowing | Can move through earth/sand |
| Climbing | Can scale vertical surfaces |
| Trample (XdY) | Can trample smaller creatures for XdY damage |
| Charge | Bonus damage after 4+ squares straight-line movement |
| Mount (Size) | Specifies valid rider sizes |

## Common Vehicle Traits

| Trait | Description |
|-------|-------------|
| Passenger Capacity (X) | Number of passengers, size restrictions, action restrictions |
| Crew Requirement (X) | Minimum operators needed |
| Handling (+/-X) | Modifier to maneuver checks |
| Cover (Type) | None, Partial (+2), Half (+4), Full |
| Cargo Capacity (X WU) | Weight capacity beyond passengers |
| Terrain Restriction | Cannot traverse specified terrain types |
| Terrain Specialization | Bonus in specific terrain |
| Enclosed | Full cover, but limited visibility and actions |
| Open | No cover, full visibility and actions |
| Fuel/Feed | Requires resource to operate |
| Magical | Operates via magical power |
| Requires Motive Source | Has no inherent MOV |
| Self-Propelled | Has own MOV |
| Ram Damage (X or XdY) | Damage dealt on basic collision |
| Trample (XdY) | Can trample smaller creatures for XdY damage |

## Examples

### Horse (Mount Race)

```
Name: Horse
Size: Large
Base Stats:
  STR: 10, DEX: 10, REF: 8, CON: 8, MOV: 10
  INT: 3, WIS: 6, CHA: 4, LUK: 0
Innate Traits: Trained, Skittish
Mount: Medium or smaller
Carrying Capacity: 200 WU
```

### War Mount (Mount Class)

| Level | XP Cost | Abilities Gained |
|-------|---------|------------------|
| 1 | 50 | War-Trained, removes Skittish |
| 2 | 100 | Trample (1d6) |
| 3 | 200 | Charge (+1d6) |
| 4 | 400 | Trample improves to 1d8 |

### Warhorse (Horse + War Mount 4)

```
Name: Warhorse
Race: Horse
Class: War Mount (Level 4)
Size: Large
Stats: STR: 12, DEX: 8, REF: 6, CON: 10, MOV: 12
       INT: 3, WIS: 6, CHA: 4, LUK: 0
Traits: Trained, War-Trained, Trample (1d8), Charge (+1d6)
Mount: Medium or smaller
Carrying Capacity: 240 WU
Trample Distance: 3 squares
```

### Wagon (Vehicle Race)

```
Name: Wagon
Size: Large
Class: Inert (Level 1)
Stats: STR: 15, DEX: 4, CON: 12, MOV: - (requires motive source)
Weight: 50 WU
Traits:
  - Requires Motive Source
  - Passenger Capacity (4, Medium or smaller)
  - Cargo Capacity (200 WU)
  - Open
  - Handling (-2)
  - Crew Requirement (1)
```

### War Chariot (Vehicle Race)

```
Name: War Chariot
Size: Large
Class: Inert (Level 1)
Stats: STR: 10, DEX: 8, CON: 8, MOV: - (requires motive source)
Weight: 30 WU
Traits:
  - Requires Motive Source
  - Passenger Capacity (2, Medium or smaller)
  - Cargo Capacity (20 WU)
  - Open
  - Handling (+1)
  - Crew Requirement (1)
  - Trample (2d6)
  - Cover (Partial)
```

## Summary

| Concept | Rule |
|---------|------|
| Mount vs Vehicle | Mount = Entity (has mind). Vehicle = Inert Entity (no mind). |
| Any Entity as Mount | Yes, if size allows. Control state determines behavior. |
| Mount Creation | Race (creature type) + Class (trained abilities) |
| Mount Progression | XP from adventuring AND training (downtime) |
| Vehicle Creation | Race (template) + Inert class (no progression) |
| Vehicle Progression | Upgrades (gold) or replacement. Not XP-based. |
| Rider/Operator Action | Restricted to mount/vehicle operation unless Skill/Ability grants combat Actions |
| Passenger Action | Full Action (no Step) |
| Mount Action (Ridden) | No Action; Instants/Interrupts/Free work |
| Mounted Movement | Mount's MOV |
| Mount/Dismount | Action each |
| Mount Control | Trained = obeys. Reassert = CHA vs WIS. |
| Mount Death | Rider lands prone adjacent; falling damage if airborne (Doc 14) |
| Vehicle Stats | Physical own, mental borrowed from driver |
| Trample | STR vs REF, MOV / 4 distance, chain until stopped |
| Target Choice | Attacker picks mount/vehicle or rider/passenger |

## Status

> **Status:** Canonical Extension v1.0

This extension builds on core TDGS rules. It does not redefine them.

**Core documents referenced:** Document 5, Document 6, Document 8, Document 9, Document 12, Document 13, Document 14, Document 15

---
