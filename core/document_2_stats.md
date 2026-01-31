*Document 2*

# Core Attributes (Stats)

*The foundational attributes that define capability in the Tactical Dice Game System*

## Purpose

This document defines the foundational attributes of the Tactical Dice Game System. They describe capability, permission, and constraints. They exist to support play by both humans and machines without collapsing into ambiguity or hand-waving.

## Unit Policy

TDGS uses abstract units for game mechanics. Distance is measured in **squares**. Weight is measured in **WU (Weight Units)**. The engine calculates using these abstract units and is agnostic to real-world measurement systems.

Content creators define what these units represent in their world:

- 1 square = 5 feet, 1.5 meters, or any scale you choose
- 1 WU = 1 pound, 0.5 kg, or any scale you choose

> **Note:** Examples in TDGS documentation may use feet or pounds for familiarity. These are content examples, not engine requirements. See Document 15 (Equipment & Slots) and Document 14 (Movement) for more on measurement units.

## Strength (STR)

Strength is the most intuitively understood attribute, and also the easiest to misuse.

In TDGS, **Strength represents raw physical force**. It answers a single question: "How much force can this entity meaningfully exert against resistance?"

Strength is not technique. It is not coordination. It is not endurance. It is the ability to apply force, abstracted from leverage, biomechanics, and cleverness.

### Representation and Scale

Strength uses a shared absolute scale from 0 to 100.

- **STR 0** means no meaningful force can be applied.
- **STR 10** represents the strongest human, as in world record holder level.
- **STR 100** represents planetary-scale force.

This scale is intentionally non-linear. Human-scale play lives near the bottom, while mythic and cosmic play occupies the upper extremes without compressing the lower range.

### Meaningful Force Threshold

Some entities are simply too small to meaningfully register on the Strength scale. Insects, microbes, and particulate entities are treated as STR 0 individually.

This does not make them irrelevant. They matter through swarms, counts, traits, and narrative effects. Strength measures *individual* force, not collective danger.

### Strength Band Anchors

Strength determines Carrying Capacity using a simple formula:

```
Carrying Capacity = STR × 10 (in Weight Units)
```

Weight Units (WU) are abstract. Content defines the scale (1 WU = 1 pound, 0.5 kg, or setting-specific).

| STR | Carrying Capacity (WU) | Interpretation |
|-----|------------------------|----------------|
| 0 | 0 | No meaningful force (insects, swarms) |
| 5 | 50 | Child, small creature |
| 10 | 100 | Average adult |
| 15 | 150 | Trained, athletic |
| 20 | 200 | Elite athlete, strongman |
| 25 | 250 | Peak mortal |
| 30 | 300 | Superhuman begins |
| 40 | 400 | Heroic, legendary |
| 50 | 500 | Titanic, monstrous |
| 75 | 750 | Mythic, godlike |
| 100 | 1000 | Cosmic, world-shaping |

See Document 15: Equipment & Slots for full equipment and carrying rules.

### What Strength Does Not Do

- Guarantee success
- Define damage on its own
- Override narrative consequence
- Replace decision making

> **Most Play Lives Here:** STR 3-15. Above 25, characters leave mortal competition and enter heroic or mythic territory.

## Dexterity (DEX)

Dexterity represents **precision and coordination**, not speed or reliability.

DEX answers the question: "What degree of precise control is possible if everything goes right?"

A high Dexterity character can thread needles, disarm traps, and perform delicate actions. Whether they succeed consistently depends on training, circumstance, and chance.

### Scale Philosophy

DEX uses the same 0-100 scale but behaves linearly. Improvements at high levels represent refinement, not transformation.

### Dexterity Lookup Table

| DEX | Interpretation | Example Entities |
|-----|----------------|------------------|
| 0 | No coordination | Inanimate |
| 3 | Poor control | Clumsy beings |
| 5 | Average | Adult human |
| 8 | Exceptional | Surgeons |
| 10 | Peak human | World-class |
| 20 | Superhuman | Mythic heroes |
| 40 | Inhuman | Constructs |
| 100 | Absolute | Divine |

### What Dexterity Does Not Do

DEX does not determine speed, reaction time, or success on its own.

> **Most Play Lives Here:** DEX 4-10. Precision is meaningful, but never guaranteed.

## Reflex (REF)

Reflex represents **reaction time**.

It answers: "How quickly does this entity notice something and begin to act?"

### Scale

REF uses the shared 0-100 scale with diminishing returns. Early improvements matter enormously. Later improvements compress toward theoretical limits.

### Reflex Lookup Table

| REF | Interpretation | Example Entities |
|-----|----------------|------------------|
| 0 | No reaction | Objects |
| 5 | Average | Adult human |
| 10 | Peak human | Elite athlete |
| 20 | Superhuman | Enhanced |
| 60 | Near instant | Legendary |
| 100 | Absolute | Conceptual |

> **Most Play Lives Here:** REF 4-10.

## Constitution (CON)

Constitution represents **endurance and pain tolerance**.

CON answers: "How much stress, injury, and pain can be endured before failure?"

This includes the ability to function while injured. It does not include healing or damage reduction.

### Scale

CON uses a 0-100 scale. Higher values represent survivability, not invulnerability.

### Constitution Lookup Table

| CON | Interpretation | Example Entities |
|-----|----------------|------------------|
| 0 | Cannot endure | Fragile matter |
| 5 | Average | Adult human |
| 10 | Peak human | Extreme survivor |
| 20 | Superhuman | Enhanced |
| 60 | Extreme | Colossal |
| 100 | Absolute | Divine |

> **Most Play Lives Here:** CON 4-10.

## Movement (MOV)

Movement represents **speed**.

MOV answers: "How fast can this entity move through space under its own power?"

It does not measure reaction time, precision, or stamina.

### Movement Lookup Table

MOV determines how many squares an entity can move per Move action.

| MOV | Interpretation |
|-----|----------------|
| 0 | Immobile (objects, rooted) |
| 3 | Slow (heavily encumbered, crawling) |
| 5 | Average adult |
| 6 | Standard humanoid baseline |
| 8 | Quick, athletic |
| 10 | Fast, trained runner |
| 12 | Very fast, cavalry |
| 15 | Exceptional speed |
| 20 | Superhuman |
| 30+ | Heroic, mythic |

See Document 14: Movement & Positioning for movement rules, terrain, and positioning.

> **Most Play Lives Here:** MOV 4-10. Above 15, entities outpace normal creatures significantly.

## Intelligence (INT)

Intelligence represents **reasoning, abstraction, and learning**.

INT answers: "How complex a problem can this entity understand?"

It does not answer whether the entity makes good decisions.

### Intelligence Lookup Table

| INT | Interpretation | Example Entities |
|-----|----------------|------------------|
| 0 | No cognition | Object |
| 5 | Average | Adult human |
| 10 | Peak human | Genius |
| 20 | Superhuman | AI |
| 100 | Absolute | Conceptual |

> **Most Play Lives Here:** INT 4-10.

## Wisdom (WIS)

Wisdom represents **judgment and consequence awareness**.

WIS answers: "Is this a good idea?"

A wise character may be slow. A foolish character may be brilliant.

### Wisdom Lookup Table

| WIS | Interpretation | Example Entities |
|-----|----------------|------------------|
| 0 | No judgment | Object |
| 5 | Average | Adult human |
| 10 | Peak human | Sage |
| 20 | Superhuman | Ancient |
| 100 | Absolute | Divine |

> **Most Play Lives Here:** WIS 4-10.

## Charisma (CHA)

Charisma represents **presence and influence**.

CHA is not beauty. It is the ability to shape social outcomes through force of personality.

### Charisma Lookup Table

| CHA | Interpretation | Example Entities |
|-----|----------------|------------------|
| 0 | No influence | Object |
| 5 | Average | Adult human |
| 10 | Peak human | Leader |
| 20 | Superhuman | Mythic |
| 100 | Absolute | Divine |

> **Most Play Lives Here:** CHA 4-10.

## Luck (LUK)

Luck represents an **abnormal relationship with probability**.

Luck is permanent. Luck is rare. Luck is powerful.

It modifies probability through dice interaction, not narrative fiat.

### Representation

Range: **-10 to +10**. This is the only attribute allowing negative values.

### Luck Effects

- Adds modifiers
- Adds or subtracts dice
- Influences rerolls
- Affects success or failure
- **Never affects magnitude**

### Luck Lookup Table

| LUK | Interpretation |
|-----|----------------|
| -10 | Catastrophic misfortune |
| -5 | Severe bad luck |
| -1 | Unlucky |
| 0 | Normal |
| +1 | Lucky |
| +5 | Strong good luck |
| +7 | Exceptional fortune |
| +10 | Mythic fortune |

> **Most Play Lives Here:** LUK -1 to +1.
> 
> **MOST ENTITIES HAVE A LUK OF 0**
> 
> Entities with LUK >= 3 or <= -3 are generally for narrative purposes.

## Document Status

> **Status:** Canonical

All nine attributes defined in this document are finalized and form the complete stat block for TDGS. Future documents may add derived stats or secondary attributes, but these nine core stats are immutable.

---

