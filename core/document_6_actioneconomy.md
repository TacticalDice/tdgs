*Document 6*

# Action Economy

*When you act, how often, and in what order*

## Purpose

This document defines the action economy of TDGS: the structure of time, turns, and actions in tactical situations.

It establishes:

- The Scene (a tactical situation) and Round structure
- Initiative and turn order
- How many actions you get and when
- The difference between Instants and Interrupts
- How simultaneous events resolve

This document builds upon Document 5 (Action Taxonomy). It defines **WHEN** actions happen; Document 5 defines **WHAT** actions exist.

## The Scene

A **Scene** is a continuous tactical situation: a combat, a chase, a tense negotiation. Scenes contain Rounds. When the Scene ends, certain effects reset (armor durability, some abilities).

A Scene ends when the tactical situation resolves:

- Combat concludes (victory, defeat, surrender, escape)
- Chase ends (caught, escaped, abandoned)
- Negotiation finishes (agreement, breakdown, interruption)

Between Scenes, entities are assumed to catch their breath, reset their stance, and prepare for whatever comes next.

## The Round

A **Round** is one complete cycle where every entity gets a chance to act. Scenes are made of Rounds.

Rounds have two phases:

```
SCENE
└── ROUND (repeats until Scene ends)
    ├── 1. INSTANT PHASE
    │   └── All Instants resolve (ordered by Instant REF)
    └── 2. ACTION PHASE
        └── All entities act in initiative order
```

Rounds repeat until the Scene ends.

## Initiative

Initiative determines the order entities act during the Action Phase.

### Determining Initiative

Initiative is **not rolled**. It is determined by stats.

```
ORDER: REF → LUK → d2
```

1. Higher REF acts first
2. If REF is tied, higher LUK acts first
3. If both are tied, flip d2 (coin flip)

This order is typically determined once at the start of combat and persists unless something changes an entity's REF or LUK.

### Why No Initiative Roll?

Stats are truth. A character with REF 10 **IS** faster than a character with REF 8. Not "probably faster" or "usually faster." *Faster.*

Rolling for initiative introduces randomness where none is needed. The faster character acts first. The die confirms reality only when reality is ambiguous (ties).

### Resolving Ties

When two entities have identical REF and LUK, flip a d2 (coin flip) to determine who acts first.

When three or more entities are tied after REF and LUK comparison:

1. All tied entities flip d2 simultaneously
2. Higher results act before lower results
3. Any remaining ties flip again
4. Repeat until order is fully resolved

**Example: Four goblins, all REF 6, LUK 0**

```
First flip:
  Goblin A: 2, Goblin B: 1, Goblin C: 2, Goblin D: 1
  
  A and C (both 2) act before B and D (both 1)

Second flip (A vs C):
  A: 1, C: 2 → C acts before A

Third flip (B vs D):
  B: 2, D: 1 → B acts before D

Final order: C, A, B, D
```

## The Instant Phase

The Instant Phase occurs at the start of each round, before anyone takes their normal action.

### What Are Instants?

Instants are abilities with special timing. They fire **BEFORE** the Action Phase, allowing entities to act pre-emptively.

Instants are:

- Granted by Skills, Spells, or Traits
- Declared at the start of the round
- Resolved before any normal actions

**Examples of Instants:**

- Quick Draw (ready a weapon before combat begins)
- Battle Cry (buff allies before they act)
- Flash Step (reposition before anyone else moves)
- Premonition (gain information before deciding your action)

### Instant Ordering

When multiple Instants are declared, they resolve in order of the **Instant's REF stat**, not the entity's REF.

```
INSTANT ORDER: Instant's REF → Entity's LUK → d2
```

Each Instant ability has its own REF value defined in its description. Faster Instants resolve before slower ones.

**Example:**

```
Fighter declares "Battle Cry" (Instant REF 8)
Rogue declares "Quick Draw" (Instant REF 12)
Wizard declares "Premonition" (Instant REF 5)

Resolution order:
  1. Rogue's Quick Draw (REF 12)
  2. Fighter's Battle Cry (REF 8)
  3. Wizard's Premonition (REF 5)
```

If two Instants have the same REF, use the declaring entity's LUK as tiebreaker, then d2.

### Instant REF Source

Each Instant ability SHOULD define its own REF value. This represents how fast the ability itself activates, independent of who uses it.

**Example:**

```
Battle Cry (Instant)
Instant REF: 8
Effect: Allies within Near range gain +2 to their next attack
```

If an Instant ability does not define its own REF, it defaults to the declaring entity's REF.

**Why Instants Have Their Own REF:** Some abilities are inherently fast or slow regardless of the user. A "Flash Step" is fast because it's a Flash Step, not because the user is fast. A "Battle Meditation" is slow because centering oneself takes time.

This allows content creators to design Instants that fire in predictable order relative to each other, independent of who learns them.

### Instants Are Not Interrupts

Instants and Interrupts are different timing mechanisms:

| Instants | Interrupts |
|----------|------------|
| Fire at round start | Fire in response to something |
| Pre-emptive | Reactive |
| Declared before Action Phase | Declared when trigger occurs |
| Ordered by Instant's REF | Resolve immediately when triggered |
| Unlimited declarations | Limited by skill |

## The Action Phase

After all Instants resolve, the Action Phase begins. Entities act in initiative order.

### Your Turn

On your turn, you may:

1. Take one **ACTION** (attack, cast, move, etc.)
2. Take one **STEP** (free, adjacent movement)
3. Take any number of **FREE ACTIONS** (simple interactions, etc.)

You choose the order. You can Step before your Action, or after. Not both.

### Unused Actions

If you do not use your Action, it is lost. There is no banking, no conversion to defense, no carry-over.

**Use it or lose it.**

### The Anatomy of an Action

When you take an Action:

1. **DECLARE:** State what you're doing and your target
2. **INTERRUPT CHECK:** Opponents may use Interrupts (if available)
3. **RESOLUTION:** Roll d20 + modifiers against threshold
4. **MAGNITUDE:** If successful, determine how much (damage, duration, etc.)

This sequence applies to all Actions, whether attacking, casting, persuading, or anything else.

## Interrupts

Interrupts are reactive abilities that fire in response to something else.

### What Are Interrupts?

Interrupts allow an entity to act outside their normal turn, in direct response to another entity's action or event.

Interrupts are:

- Granted by Skills, Spells, or Traits
- Triggered by specific conditions
- Resolved immediately when triggered

**Examples of Interrupts:**

- Parry (when attacked in melee, deflect the blow)
- Counterspell (when a spell is cast, attempt to negate it)
- Opportunity Attack (when an enemy moves away, strike them)
- Dodge Roll (when targeted by an attack, evade)

### No Free Interrupts

You do not get Interrupts by default. An entity with no relevant Skills or Abilities has no Interrupts available.

When attacked, your REF **IS** your defense. If you want to parry, dodge, or counter, you need to learn how.

### Interrupt Limits

Each Interrupt-granting ability specifies how many times it can be used. Limits are typically:

- **Per round:** Resets each round
- **Per scene:** Resets when the Scene ends
- **Per day:** Resets after long rest

**Illustrative Examples:**

```
Parry (Level 1): Use once per round
Parry (Level 5): Use twice per round
Dodge Roll: Use once per round
Counterspell: Use once per scene
Divine Intervention: Use once per day
```

There is no base Interrupt pool. Your limits are defined entirely by your abilities.

### Interrupt Timing

When an Interrupt is triggered, it resolves immediately, before the triggering action completes (if relevant).

**Example: Parry**

```
1. Enemy declares Melee Attack against you
2. You declare Parry (your Interrupt)
3. Your Parry resolves (you roll)
4. If Parry succeeds, attack is deflected
5. If Parry fails, enemy's attack continues normally
```

### Interrupt vs Interrupt

If an Interrupt triggers another Interrupt, resolve them in order declared (defender's Interrupt first, since they're responding).

**Example: Counterspell Chain**

```
1. Wizard A casts Fireball
2. Wizard B uses Counterspell (Interrupt)
3. Wizard A uses Counter-Counterspell (Interrupt to the Interrupt)
4. Resolve: Counter-Counterspell first, then Counterspell, then Fireball (if it survives)
```

## Readied Actions

The Ready action (from Document 5) creates a special case: an Action that becomes an Interrupt.

### How Ready Works

1. On your turn, declare Ready (costs your Action)
2. State your trigger and your held action
3. If trigger occurs before your next turn, your held action fires as an Interrupt and resolves immediately
4. If trigger does not occur, your action is lost

**Example:**

```
Fighter's turn: "I Ready. When the goblin comes through the door, I attack."
Later: Goblin opens door.
Trigger fires: Fighter's attack resolves immediately as an Interrupt.
```

Readied actions are the primary way for characters **WITHOUT** Interrupt-granting skills to still react to events.

## Delay

The Delay action allows you to act later in initiative order.

### How Delay Works

1. When your turn comes, declare Delay (free)
2. Specify when you want to act ("after the wizard" or "at the end")
3. Your turn moves to that position this round
4. At the start of next round, your position resets to your natural REF order

You cannot delay past the start of the next round. If you keep delaying, eventually the round ends and you lose your action.

## Step Timing

You get one Step per turn, free. You choose when to take it.

**VALID:**

```
Step, then Action
Action, then Step
Step, then free actions, then Action
Action, then free actions, then Step
```

**INVALID:**

```
Step, Action, Step (only one Step per turn)
```

If you need to move further than one adjacent position, use the Move action instead.

## Simultaneous Events

Sometimes multiple things happen "at the same time." TDGS resolves these in order.

### Same Phase, Different REF

If two events happen in the same phase but from entities with different REF, higher REF resolves first.

### Same Phase, Same REF

If two events happen at exactly the same time from entities with the same REF:

1. Compare LUK
2. If still tied, flip d2

### Mutual Destruction

If two events would each prevent the other (both attacks would kill both combatants), resolve in REF order. The faster entity's action completes first.

There is no "mutual kill" unless both have identical REF and LUK, in which case flip d2 to see whose action completes first. The other may not get to complete theirs.

## Summary Tables

### Scene and Round Structure

```
SCENE (combat, chase, negotiation, etc.)
└── ROUND (repeats until Scene ends)
    ├── INSTANT PHASE
    │   └── All declared Instants resolve (by Instant REF)
    └── ACTION PHASE
        └── Each entity acts in initiative order (by Entity REF)
            ├── Declare Action
            ├── Opponents may Interrupt
            ├── Resolution
            └── Magnitude

SCENE ENDS → Some effects reset (armor durability, per-scene abilities)
```

### Turn Structure

```
YOUR TURN
├── STEP (free, once, choose timing)
├── ACTION (one, use or lose)
└── FREE ACTIONS (unlimited simple interactions)
```

### Timing Types

| Type | When | Limit | Source |
|------|------|-------|--------|
| Action | Your turn | 1 per turn | Everyone |
| Free | Your turn | Varies | Everyone |
| Step | Your turn | 1 per turn | Everyone |
| Instant | Round start | Per ability* | Skills/Abilities |
| Interrupt | Response | Per ability* | Skills/Abilities |
| Readied | On trigger | 1 (from Ready) | Ready action |

*Each ability specifies its own limits: per round, per scene, or per day.

## Document Status

> **Status:** Canonical

This document defines the action economy for TDGS. All timing, turn structure, and action sequencing in the system conform to the rules established here.

---
