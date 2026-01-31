*Document 3*

# Resolution Mechanics

*How uncertain actions are resolved within the Tactical Dice Game System*

## Purpose

This document defines how uncertain actions are resolved in the Tactical Dice Game System.

It establishes:

- The core resolution formula
- How stats interact with resolution
- How opposed and non-opposed actions work
- How ties are resolved
- How critical outcomes function

> **Note:** This document assumes a Luck value of 0. Luck modifications to resolution are defined in Document 4: Luck.

## The Core Formula

All resolution in TDGS uses a single formula:

```
d20 + (Your Stat - Their Stat) + Modifiers >= 11
```

That's it.

- **d20**: The resolution die
- **Your Stat**: The relevant stat for your action
- **Their Stat**: The relevant stat for their defense (or a virtual stat for non-opposed actions)
- **Modifiers**: Equipment, temporary effects, situational bonuses
- **11**: The fixed threshold. Always.

### Why 11?

The threshold never changes. There are no difficulty classes to look up, no variable targets to calculate. The difficulty of an action is embedded in the stat delta, not a shifting goalpost.

Equal stats at zero modifiers = 50% success. The math is transparent.

## Natural 1 and Natural 20

**Natural 1 always fails.**

**Natural 20 always succeeds.**

Always. Regardless of math.

A peasant can strike a god. A god can fumble against a peasant.

The dice have final say.

## Stat Pairings

Each action type uses one attacking stat versus one defending stat.

### Physical Actions

| Action | Attacker Uses | Defender Uses |
|--------|---------------|---------------|
| Melee strike | STR | REF |
| Ranged attack | DEX | REF |
| Grapple / shove | STR | STR |
| Chase / flee | MOV | MOV |
| Hide / stealth | DEX | WIS |
| Spot hidden | WIS | DEX |

### Mental Actions

| Action | Attacker Uses | Defender Uses |
|--------|---------------|---------------|
| Persuade / intimidate | CHA | WIS |
| Deceive / bluff | CHA | INT |
| Resist fear / charm | — | WIS |

### Magical Actions

| Action | Attacker Uses | Defender Uses |
|--------|---------------|---------------|
| Arcane magic (learned) | INT | WIS |
| Divine magic (intuitive) | WIS | WIS |

### Resistance Actions

| Action | Defender Uses |
|--------|---------------|
| Resist poison / pain | CON |
| Endurance contest | CON vs CON |

### Knowledge Actions

| Action | Stat | Against |
|--------|------|---------|
| Recall knowledge | INT | Virtual Difficulty |


### Extending Stat Pairings

These pairings are defaults. Game Masters may create additional stat pairings appropriate to their setting—technology, psionics, specialized skills, or other systems.

The formula remains constant. Only the stats change.

## Non-Opposed Actions

When there is no defender, the GM assigns a **virtual stat** representing the difficulty of the task.

```
d20 + (Your Stat - Virtual Stat) + Modifiers >= 11
```

The virtual stat answers: "If this obstacle were an entity, what would its relevant stat be?"

### Examples

| Task | Stat Used | Virtual Stat | Interpretation |
|------|-----------|--------------|----------------|
| Pick a simple lock | DEX | 5 | Trivial mechanism |
| Pick a quality lock | DEX | 10 | Professional security |
| Pick a master lock | DEX | 15 | Expert craftsmanship |
| Climb a rough wall | STR | 6 | Easy handholds |
| Climb a sheer cliff | STR | 12 | Demanding terrain |
| Recall common lore | INT | 4 | Widely known |
| Recall obscure lore | INT | 14 | Specialist knowledge |

> **Future Note:** Items may have inherent difficulty stats defined within the item system. A lock might have a built-in DEX value rather than requiring GM assignment.

## Contested Resolution

When two entities directly oppose each other, both perform a resolution roll.

```
Entity A: d20 + (A's Stat - B's Stat) + A's Modifiers
Entity B: d20 + (B's Stat - A's Stat) + B's Modifiers
```

The higher total succeeds. The lower total fails.

If the action is **asymmetric** (attacker vs defender), only the attacker rolls. The defender's stat creates the delta.

If the action is **symmetric** (grapple vs grapple, chase vs chase), both entities roll.

## Contested Ties

When two contested rolls produce the same total, ties are resolved based on the type of contest.

### Physical Contests

Grapple, melee, chase, and other physical contests:

```
REF → LUK → d2
```

Higher Reflex wins. If Reflex is equal, higher Luck wins. If both are equal, flip a coin.


### Magical Contests

Spell vs spell, or any magical opposition:

```
LUK → d2
```
## Critical Outcomes

Critical outcomes occur only on natural 1 or natural 20.

Resolution and magnitude are always separate.

### Critical Success (Natural 20)

**Resolution:** Automatic success, regardless of the math.

**Magnitude:** Roll d4.

| d4 | Effect |
|----|--------|
| 1 | Normal success |
| 2 | Minor bonus |
| 3 | Notable bonus |
| 4 | Major bonus |

### Critical Failure (Natural 1)

**Resolution:** Automatic failure, regardless of the math.

**Magnitude:** Roll d4.

| d4 | Effect |
|----|--------|
| 1 | Normal failure |
| 2 | Minor consequence |
| 3 | Notable consequence |
| 4 | Major consequence |

For detailed critical effect examples (damage scaling, duration, area, healing), see Document 1: Dice & Uncertainty - Critical Effect Examples.

### Principle

```
d20 = Resolution (did it happen?)
d4 = Critical magnitude (how extreme?)
```

These are always separate rolls. The d20 never determines magnitude. The d4 never determines resolution.

The specific effects of minor, notable, and major outcomes are defined by the relevant system (combat, skills, GM discretion).

## Modifiers

Modifiers adjust the resolution roll. They come from multiple sources:

```
Final Roll = d20 + (Stat Delta) + Equipment + Temporary + Situational
```

### Modifier Sources

| Source | Type | Examples |
|--------|------|----------|
| Stat Delta | Your stat - Their stat | DEX 8 vs REF 5 = +3 |
| Equipment | Weapons, armor, tools | +2 sword, +1 lockpicks |
| Temporary | Buffs, debuffs, conditions | Potion +2, Blinded -4 |
| Situational | Positioning, environment | High ground +2, darkness -2 |

### Equipment Dice (Optional)

Equipment may grant modifier dice instead of flat bonuses:

| Quality | Modifier |
|---------|----------|
| Mundane | +1 or +2 (flat) |
| Quality | +d4 |
| Exceptional | +d6 |
| Legendary | +d8 or +d12 |

This makes gear feel variable and impactful without changing the core formula.

## Multi-Entity Situations

Numeric advantage is resolved through action economy, not roll bonuses. Six attackers against one defender means six separate resolution rolls, not one enhanced roll.

### Positional Modifiers

| Situation | Modifier |
|-----------|----------|
| Flanking (2 attackers, opposite sides) | +2 to attackers |
| Surrounded (3+ attackers, no escape route) | +4 to attackers |

These are situational modifiers and stack with normal resolution.

### Multi-Target Actions

Some skills allow a single action to affect multiple targets. Resolution for multi-target actions is defined in the Skills system.

## Success Rate Table

For reference, here is the relationship between delta and success rate:

| Delta | Need on d20 | Success Rate |
|-------|-------------|--------------|
| -9 or worse | 20 | 5% |
| -8 | 19+ | 10% |
| -7 | 18+ | 15% |
| -6 | 17+ | 20% |
| -5 | 16+ | 25% |
| -4 | 15+ | 30% |
| -3 | 14+ | 35% |
| -2 | 13+ | 40% |
| -1 | 12+ | 45% |
| 0 | 11+ | 50% |
| +1 | 10+ | 55% |
| +2 | 9+ | 60% |
| +3 | 8+ | 65% |
| +4 | 7+ | 70% |
| +5 | 6+ | 75% |
| +6 | 5+ | 80% |
| +7 | 4+ | 85% |
| +8 | 3+ | 90% |
| +9 or better | 2+ | 95% |

> **Note:** The system naturally bounds between 5% (nat 20 only) and 95% (only nat 1 fails).

## Deferrals and Dependencies

This document intentionally does not define:

- **Luck modifications:** How LUK -10 to +10 alters resolution (see Document 4: Luck)
- **Action economy:** How many actions per round, instants, interrupts (see Document 6: Action Economy)
- **Combat specifics:** Damage, armor, death states (see Document 8: Combat)
- **Skill specifics:** What specific skills do, skill levels (see Document 7: Abilities)
- **Item system:** Equipment stats, item creation (see future document)
- **Critical effect details:** What "minor bonus" means in combat vs persuasion (see relevant systems)

## Document Status

> **Status:** Canonical

This document defines the core resolution mechanics for TDGS. All resolution in the system uses the formula established here. Later systems (combat, skills, magic) build upon this foundation but do not alter it.

Changes to this document should be rare, deliberate, and backward compatible.

---
