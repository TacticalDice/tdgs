*Document 5*

# Action Taxonomy

*What you can do, and what it costs*

## Purpose

This document defines the base actions available in TDGS.

It establishes:

- The categories of actions (Physical, Mental, Magical, Utility, Defensive)
- The stat pairings for each action
- The cost of each action (Action, Free, or Interrupt)
- Optional expansions for Technology and Psionics
- The foundation that Skills and Abilities build upon

This document builds upon Document 3 (Resolution Mechanics) and Document 4 (Luck). All actions use the core resolution formula defined in those documents.

## What Is an Action?

An action is any discrete thing an entity does that requires resolution.

Actions have three properties:

- **TYPE:** What category (Physical, Mental, Magical, Utility, Defensive)
- **STATS:** What you roll (Your Stat vs Their Stat, or Your Stat vs Difficulty)
- **COST:** What it takes (Action, Free, or Interrupt)

When an action targets another entity, you roll against their stat. When an action targets the environment, an object, or a challenge with no defender, you roll against a **Difficulty**, which is a virtual stat assigned by the GM (or defined by the object/challenge itself).

The resolution formula remains constant:

```
d20 + (Your Stat - Opposing Stat) + Modifiers >= 11
```

Whether the opposing stat belongs to a creature or is a Difficulty assigned to a lock, a cliff, or a computer system, the math works the same way.

## Action Costs

Every action has a cost.

### Action

The default cost. You get one Action per turn. Using it consumes your turn's primary activity.

Most things that matter cost an Action: attacking, casting spells, complex maneuvers, focused mental effort.

### Free

Costs nothing. Can be performed alongside your Action.

Free actions are limited or restricted in some way. A Step is free but limited to once per turn and adjacent movement only. Simple interactions are free but require no resolution.

### Interrupt

Special timing. Fires in response to something else, outside normal turn order.

Interrupts are never free. They come from Skills, Abilities, Spells, or Readied actions. A character with no relevant abilities has no Interrupts available.

## Difficulty as Virtual Stat

When an action has no defender, the GM assigns a **Difficulty**, which functions as a virtual stat.

The core formula remains unchanged:

```
d20 + (Your Stat - Difficulty) + Modifiers >= 11
```

### Standard Difficulty Scale

| Challenge Level | Virtual Stat | Success at Stat 10 |
|-----------------|--------------|-------------------|
| Trivial | 0 | 95% |
| Easy | 5 | 70% |
| Moderate | 10 | 50% |
| Hard | 15 | 30% |
| Very Hard | 20 | 5% (nat 20 only) |
| Legendary | 25+ | 5% (nat 20 only) |

A character with a stat of 10 attempting a Moderate (10) challenge has a 50% success rate, exactly as if they were facing an opponent with the same stat.

### Objects and Challenges Have Stats

Some objects and challenges have predefined virtual stats:

- A **simple lock** might have DEX 5
- A **quality lock** might have DEX 10
- A **masterwork lock** might have DEX 15
- A **legendary vault** might have DEX 25

This allows the same formula to handle both opposed actions (fighting a goblin) and non-opposed actions (picking a lock). The goblin has REF. The lock has virtual DEX. The math is identical.

## Physical Actions

Actions involving the body: combat, movement, stealth, pursuit.

| Action | Attacker Stat | Defender Stat | Cost |
|--------|---------------|---------------|------|
| Melee Attack | STR | REF | Action |
| Ranged Attack | DEX | REF | Action |
| Grapple | STR | STR | Action |
| Shove | STR | STR | Action |
| Hide | DEX | WIS | Action |
| Search | WIS | DEX | Action |
| Chase | MOV | MOV | Action |
| Flee | MOV | MOV | Action |
| Move | — | — | Action |
| Step | — | — | Free (once per turn) |

**Melee Attack:** Strike an adjacent target with a weapon or body part. Your STR versus their REF.

**Ranged Attack:** Strike a distant target with a projectile or thrown weapon. Your DEX versus their REF.

**Grapple:** Attempt to grab and restrain a target. Your STR versus their STR. Success means they are grappled (effects defined in Combat document).

**Shove:** Attempt to push a target away or knock them down. Your STR versus their STR. Success moves them or knocks them prone.

**Hide:** Attempt to become unseen. Your DEX versus the WIS of anyone who might notice. Success means you are hidden until you reveal yourself or they Search.

**Search:** Attempt to find something hidden—a creature, object, or detail. Your WIS versus the DEX of anything hidden (or a Difficulty for objects).

**Chase:** Pursue a fleeing target. Your MOV versus their MOV. Success means you close distance or catch them.

**Flee:** Escape from a pursuer. Your MOV versus their MOV. Success means you create distance or escape.

**Move:** Relocate any distance you are capable of. Costs your Action. Use this for significant repositioning: crossing a room, climbing to a vantage point, sprinting across a battlefield.

**Step:** Relocate to an adjacent position. Free, once per turn. Use this for minor repositioning during combat without sacrificing your Action.

## Mental Actions

Actions involving the mind: persuasion, deception, insight, knowledge.

| Action | Attacker Stat | Defender Stat | Cost |
|--------|---------------|---------------|------|
| Persuade | CHA | WIS | Action |
| Intimidate | CHA | WIS | Action |
| Deceive | CHA | INT | Action |
| Insight | WIS | CHA | Action |
| Recall Knowledge | INT | Difficulty | Action |
| Concentrate | — | — | Action |

**Persuade:** Convince someone through logic, charm, or appeal. Your CHA versus their WIS. Success means they are inclined to agree or cooperate.

**Intimidate:** Frighten or coerce someone through threat or presence. Your CHA versus their WIS. Success means they are cowed, hesitant, or compliant.

**Deceive:** Make someone believe something false. Your CHA versus their INT. Success means they accept the lie (for now).

**Insight:** Determine if someone is lying or hiding something. Your WIS versus their CHA. Success reveals deception or hidden intent.

**Recall Knowledge:** Remember something relevant from training or experience. Your INT versus a Difficulty (virtual stat) set by obscurity.

| Knowledge Type | Virtual Stat |
|----------------|--------------|
| Common | 5 |
| Uncommon | 10 |
| Rare | 15 |
| Legendary | 20 |

**Concentrate:** Maintain focus on an ongoing effect. Some spells and abilities require Concentration to persist.

### Breaking Concentration

When you take damage while concentrating, you must make a Concentration check:

```
d20 + (CON - Damage Taken) >= 11

Success: You maintain concentration.
Failure: The effect ends immediately.

- Natural 1 always fails (concentration broken)
- Natural 20 always succeeds (concentration maintained)
- Luck applies normally
```

Small damage can be shrugged off. Large damage overwhelms focus.

| Damage | CON 10 Success Rate |
|--------|---------------------|
| 5 | 75% |
| 10 | 50% |
| 15 | 25% |
| 20 | 5% (nat 20 only) |

### Voluntary End

You may end your own concentration at any time (free action, no roll required).

### Multiple Concentrations

By default, an entity can only concentrate on one effect at a time. Starting concentration on a new effect ends the previous one. Abilities MAY override this limit.

## Magical Actions

Actions involving supernatural power: casting, countering, identifying.

| Action | Attacker Stat | Defender Stat | Cost |
|--------|---------------|---------------|------|
| Cast Spell (Arcane) | INT | WIS | Action |
| Cast Spell (Divine) | WIS | WIS | Action |
| Dispel (Arcane) | INT | Caster's INT | Action |
| Dispel (Divine) | WIS | Caster's WIS | Action |
| Identify | INT | Difficulty | Action |

**Cast Spell (Arcane):** Channel magical energy through knowledge and will. Your INT versus target's WIS. Arcane magic is learned, studied, and precise. Wizards, sorcerers, and artificers use Arcane casting.

**Cast Spell (Divine):** Channel magical energy through faith and wisdom. Your WIS versus target's WIS. Divine magic is granted, intuited, and purposeful. Clerics, druids, and paladins use Divine casting.

**Dispel (Arcane):** Attempt to end an active Arcane spell. Your INT versus the original caster's INT. Success ends the spell. Failure means it persists.

**Dispel (Divine):** Attempt to end an active Divine spell. Your WIS versus the original caster's WIS. Success ends the spell. Failure means it persists.

**Identify:** Attempt to recognize a magical effect. Your INT versus a Difficulty (virtual stat) based on the spell's rarity. Success reveals the spell's nature, effects, and (possibly) its caster.

| Spell Rarity | Virtual Stat |
|--------------|--------------|
| Common | 5 |
| Uncommon | 10 |
| Rare | 15 |
| Legendary | 20 |

## Utility Actions

Actions that support, prepare, or interact with the environment.

| Action | Effect | Cost |
|--------|--------|------|
| Use Item | Activate an item's effect | Action |
| Interact (Simple) | Open door, pull lever, pick up object | Free |
| Interact (Complex) | Pick lock, disable trap, operate machinery | Action |
| Ready | Prepare conditional action | Action |
| Delay | Act later in initiative | Free |
| Help | Grant +2 to ally's next roll | Action |

**Use Item:** Activate an item that requires deliberate use: drink a potion, activate a wand, throw a bomb. The item's description determines any resolution required.

**Interact (Simple):** Engage with the environment in a trivial way: open an unlocked door, pull a lever, pick up a dropped weapon. No resolution required. Free.

**Interact (Complex):** Engage with the environment in a meaningful way: pick a lock (DEX vs Difficulty), disable a trap (INT vs Difficulty), operate unfamiliar machinery (INT vs Difficulty). Requires resolution. Costs Action.

**Ready:** Prepare to act when a specific trigger occurs. Declare your trigger condition and your held action. If the trigger occurs before your next turn, your held action executes immediately as an Interrupt, even in the middle of another entity's action. If the trigger does not occur, your action is lost.

**Delay:** Choose to act later in initiative order. You may move to any later position in the current round's initiative. You cannot delay past the start of the next round. Your position resets to your natural order (based on REF) at the start of each round.

**Help:** Assist another entity with their next action. Grant +2 to one ally's next roll, which must occur before your next turn. The assistance must be narratively plausible: you must be adjacent for physical help, able to communicate for mental help, etc.

## Defensive Actions

Actions that protect you from harm. Unlike other categories, Defensive Actions are never available by default. They require Skills, Abilities, or Spells.

| Action | Effect | Cost |
|--------|--------|------|
| Dodge | Avoid an incoming attack | Interrupt |
| Block | Absorb an incoming attack | Interrupt |
| Parry | Deflect an incoming attack | Interrupt |

### Base Defense

By default, your REF IS your defense. Attackers roll against it. You do not roll.

This is not an action. It is simply how defense works. A peasant with no combat training still has REF, and attackers must overcome it.

### Active Defense (Requires Ability)

Characters with defensive Skills or Abilities may use Interrupts to enhance their defense when attacked.

- **Dodge:** Use an Interrupt to add a bonus to your effective REF for one attack. The specific bonus depends on your Dodge skill level.
- **Block:** Use an Interrupt to reduce damage from one attack. The specific reduction depends on your Block skill level and shield.
- **Parry:** Use an Interrupt to deflect an attack and potentially counter. The specific effect depends on your Parry skill level.

These are not base actions. They are granted by the Skills system (Document 7: Abilities).

## Technology Actions (Optional Expansion)

Actions involving advanced technology. Include these if your setting features computers, networks, or complex machinery.

| Action | Attacker Stat | Defender Stat | Cost |
|--------|---------------|---------------|------|
| Hack | INT | INT or Difficulty | Action |
| Interface | INT | Difficulty | Action |
| Scan | WIS | Difficulty | Action |
| Repair | INT or DEX | Difficulty | Action |
| Override | INT | System Difficulty | Action |

**Hack:** Breach a secured system—whether a computer network, electronic lock, or AI. Your INT versus the system's Difficulty (for passive security) or the defending operator's INT (if actively defended). Success grants access.

**Interface:** Operate unfamiliar technology. Your INT versus a Difficulty (virtual stat) based on the technology's complexity.

| Technology | Virtual Stat |
|------------|--------------|
| Consumer-grade | 5 |
| Professional | 10 |
| Military/Research | 15 |
| Alien/Ancient | 20 |

**Scan:** Use sensors or detection equipment to gather information. Your WIS versus a Difficulty based on what you're scanning for.

**Repair:** Fix damaged equipment or machinery. Your INT (for understanding) or DEX (for precision work) versus a Difficulty based on damage severity and complexity.

**Override:** Force control of a system against its programming or operator. Your INT versus the system's security Difficulty. Success gives temporary control. Failure may trigger alarms or lockouts.

## Psionic Actions (Optional Expansion)

Actions involving mental powers. Include these if your setting features psychics, telepaths, or mind-based abilities.

| Action | Attacker Stat | Defender Stat | Cost |
|--------|---------------|---------------|------|
| Mind Probe | WIS | WIS | Action |
| Telepathy | WIS | WIS or willing | Action |
| Telekinesis | INT | Difficulty | Action |
| Dominate | CHA | WIS | Action |
| Psi Sense | WIS | Difficulty | Action |

**Mind Probe:** Attempt to read a target's thoughts. Your WIS versus their WIS. Success reveals surface thoughts. Critical success may reveal deeper memories or secrets. The target knows they are being probed (unless a Skill says otherwise).

**Telepathy:** Communicate mentally with a target. Your WIS versus their WIS (if unwilling) or no roll (if willing). Willing targets can be contacted freely. Unwilling targets may resist.

**Telekinesis:** Move an object with mental force. Your INT versus a Difficulty based on weight and distance. Using telekinesis as an attack uses INT versus target's REF.

| Task | Virtual Stat |
|------|--------------|
| Light object, close (book, cup) | 5 |
| Medium object, close (chair, weapon) | 10 |
| Heavy object or medium distant | 15 |
| Massive object or fine manipulation | 20 |

**Dominate:** Attempt to control a target's actions. Your CHA versus their WIS. Success gives you control over the target's next action. They are aware they are being controlled (and will likely be hostile afterward). This is typically considered hostile and evil in most settings.

**Psi Sense:** Detect minds, emotions, or psionic activity. Your WIS versus a Difficulty based on what you're sensing.

## Extending the Taxonomy

This document defines the base actions available in TDGS, plus optional expansions for Technology and Psionics. It is not exhaustive.

Game Masters may create additional actions appropriate to their setting, following the patterns established in the Technology and Psionics sections:

- **Nautical settings:** Navigate (WIS vs Difficulty), Command Crew (CHA vs Difficulty)
- **Political intrigue:** Scheme (INT vs INT), Rally (CHA vs Difficulty)
- **Horror settings:** Resist Fear (WIS vs Difficulty), Banish (WIS vs Entity's WIS)
- **Superhero settings:** Power Stunt (varies), Monologue (CHA vs WIS)

When creating new actions, follow this pattern:

1. Name the action
2. Assign the Action Type (Physical, Mental, Magical, Utility)
3. Determine the stat pairing (Attacker vs Defender, or Attacker vs Difficulty)
4. Set the cost (Action, Free with limits, or Interrupt with requirements)

The resolution formula remains constant:

```
d20 + (Your Stat - Their Stat) + Modifiers >= 11
```

## Summary Tables

### By Cost

**Actions (1 per turn):**
- *Physical:* Melee Attack, Ranged Attack, Grapple, Shove, Hide, Search, Chase, Flee, Move
- *Mental:* Persuade, Intimidate, Deceive, Insight, Recall Knowledge, Concentrate
- *Magical:* Cast Spell, Dispel, Identify
- *Utility:* Use Item, Interact (Complex), Ready, Help
- *Technology:* Hack, Interface, Scan, Repair, Override
- *Psionics:* Mind Probe, Telepathy, Telekinesis, Dominate, Psi Sense

**Free:**
- Step (once per turn)
- Interact (Simple)
- Delay
- Telepathy (willing target)

**Interrupt (Requires Ability):**
- Dodge, Block, Parry
- Readied actions (when triggered)

### By Stat Used

| Stat | Attacks With | Defends Against |
|------|--------------|-----------------|
| STR | Melee Attack, Grapple, Shove | Grapple, Shove |
| DEX | Ranged Attack, Hide, Repair (precision) | Search |
| REF | — | Melee Attack, Ranged Attack, TK attack |
| CON | — | Concentration checks |
| MOV | Chase, Flee | Chase, Flee |
| INT | Cast (Arcane), Dispel (Arcane), Identify, Recall, Hack, Interface, Repair, Override, Telekinesis | Deceive, Hack (defended) |
| WIS | Search, Cast (Divine), Dispel (Divine), Insight, Scan, Mind Probe, Telepathy, Psi Sense | Persuade, Intimidate, Cast, Mind Probe, Telepathy, Dominate |
| CHA | Persuade, Intimidate, Deceive, Dominate | Insight |
| LUK | (Tiebreaker only) | (Tiebreaker only) |

## Status

> **Status:** Canonical

This document defines the base action taxonomy for TDGS. All actions in the system either appear in this document or extend from it using the patterns defined here.

Skills, Abilities, Spells, and Traits may create new actions or modify existing ones. Those modifications are defined in their respective documents.

---
