# TDGS Intent (ForAI)

**Foundation Document** | AI-Optimized Reference

---

## What TDGS Is

- A foundational RPG engine, not a game
- Genre-agnostic, setting-agnostic
- Designed for humans, computers, or both
- Open source under MIT License

---

## What TDGS Is Not

| Not This | That's For |
|----------|------------|
| A finished game | Games built on TDGS |
| A genre simulator | Content layer |
| A balance-obsessed skirmish engine | Different design goals |
| A narrative freeform framework | Different design goals |
| Classes, spells, equipment | Content layer |

---

## Core Identity Features

These define TDGS. Removing them breaks compatibility.

### 1. Resolution vs Magnitude Separation

| Concept | Determines | Governed By |
|---------|------------|-------------|
| Resolution | Whether something happens | d20, Luck, modifiers, crits |
| Magnitude | How much happens | Stats, abilities, explicit mechanics |

Hard boundary. Never conflated.

### 2. Dice Have Explicit Roles

| Role | Examples |
|------|----------|
| Resolve truth | d20 |
| Resolve quantity | Damage dice |
| Select outcomes | d100 tables |
| Represent extremes | Critical ranges |

No die does all roles at once.

### 3. Luck as Permanent Probability Distortion

| Property | Value |
|----------|-------|
| Permanent | Yes |
| Resource | No |
| Reroll | No |
| Flat modifier | No |
| Affects | Critical threshold ranges |
| Symmetric | Blessing and curse mirror |

Luck distorts how often extremes occur, not base success chance.

### 4. Extremes Permitted

System allows:
- Overwhelming advantage
- Catastrophic failure
- Cursed existence
- Improbable victory

No flattening for balance. Difficult to reach, difficult to escape, but real.

### 5. No Hidden Ceilings

Progression constrained only by:
- Effort
- Survival
- Opportunity
- Circumstance

No artificial caps. Supports short arcs and generational play.

### 6. Computable by Design

| Requirement | Meaning |
|-------------|---------|
| Human-readable | Natural language rules |
| Deterministic | No narrative ambiguity in mechanics |
| Dual-context | Same rules work for human GM and computer |

Human may interpret. Computer never has to.

---

## Design Priorities

| Priority | Meaning |
|----------|---------|
| Fun over correctness | Unfun but correct = bad rule |
| Memorable over balanced | Edge case stories = feature |
| Open over controlled | MIT License, cultural attribution only |
| Computable over interpretive | No ambiguity in mechanics |

---

## Success Criteria

TDGS succeeds if:

- Lucky nobody can occasionally defeat stronger foe
- Cursed hero can fail repeatedly despite competence
- Powerful being remains powerful at any scale
- Growth feels earned
- Same rules work at small and absurd scales
- People enjoy it

---

## Canonical Game

TDGS has an optional canonical game/setting.

| Property | Value |
|----------|-------|
| Required | No |
| Purpose | Reference implementation, shared content |
| Remixable | Yes |
| Expandable | Yes |
| Ignorable | Yes |

No engine rule depends on canonical content.

---

## License

MIT License.

| Permission | Granted |
|------------|---------|
| Use | Yes |
| Modify | Yes |
| Redistribute | Yes |
| Commercial use | Yes |
| Viral obligations | None |

Cultural expectation: say it's TDGS-based.

---

## Document Role

This is the foundational intent document. All other TDGS documents build on this.

Changes should be:
- Rare
- Deliberate
- Backward compatible when possible
