# TDGS Conventions and Concepts - ForAI Version

## Document Metadata

- **Document**: Conventions and Concepts
- **Badge**: Foundational
- **Status**: Canonical
- **Purpose**: Defines organizational structure, terminology, and conventions for the TDGS project
- **Canonical URL**: https://tacticaldice.com/docs/tdgs/conventions

---

## Core Principle: Three Equal Constituencies

TDGS is designed for three constituencies with EQUAL priority:

| Constituency | Description | Design Implication |
|--------------|-------------|-------------------|
| Humans | Tabletop players with dice and paper | Must be calculable without computers |
| Computers | VTTs, video games, bots, software | Must be deterministic and unambiguous |
| AI | Game runners, narrators, content creators, assistants | Must be learnable from documentation alone |

**Design Test**: Every mechanic must pass ALL THREE:
1. Can a human calculate this at the table?
2. Can a computer execute this deterministically?
3. Can an AI learn and apply this from documentation?

If any answer is "no", the design needs revision.

---

## Normative Language Definitions

| Term | Meaning | Compliance |
|------|---------|------------|
| **SHALL** | Absolute requirement | Violating = not following TDGS |
| **SHALL NOT** | Absolute prohibition | Violating = not following TDGS |
| **SHOULD** | Strong recommendation | Deviation requires justification |
| **SHOULD NOT** | Strong discouragement | Deviation requires justification |
| **MAY** | Permission granted | Optional |
| **MAY NOT** | Permission not granted | Not forbidden, just not granted |
| **WILL** | Statement of fact/consequence | Not a command |

---

## Four-Layer Architecture

```
Layer 4: Game Layer      [DOWNSTREAM - not in repo]
         ↑ consumes
Layer 3: Content         [DOWNSTREAM - not in repo]
         ↑ consumes
Layer 2: Extensions      [IN REPO - MIT Licensed]
         ↑ consumes
Layer 1: Core            [IN REPO - MIT Licensed - IMMUTABLE]
```

### Layer 1: Core

**Definition**: Foundational mechanics everything depends on

**Contents**:
- Resolution mechanics
- Nine attributes
- Dice roles and usage
- Action economy
- Combat fundamentals
- Progression systems
- Entity structure

**Rules**:
- Core documents ARE numbered (Document 1, Document 2, etc.)
- Core documents carry the **Core** badge
- Core is IMMUTABLE from all other layers
- Changes require pull request (high bar, rarely accepted)

### Layer 2: Extensions

**Definition**: Mechanical modules that complement Core (specifications, not implementations)

**Examples**: Mounts and Vehicles, Mass Combat, Naval Warfare, Crafting Systems

**Rules**:
- Extensions SHALL NOT redefine Core mechanics
- Extensions SHALL NOT override Core mechanics
- Extensions MAY NOT contradict Core mechanics
- Extensions SHOULD provide new capabilities, not replacements
- Extension documents are NEVER numbered
- Extension documents carry the **Extension** badge

**Official vs Community**:

| Type | Location | License | Curation |
|------|----------|---------|----------|
| Official | TDGS repository | MIT (mandatory) | TacticalDice curated |
| Community | External | Any (including proprietary) | Self-published |

**Official Extension Acceptance Criteria**:
1. General utility (broad audience)
2. Core compliance (no override/contradiction)
3. Quality (well-documented, complete, mechanically sound)
4. ForAI companion included

### Layer 3: Content

**Definition**: Concrete implementations using mechanics

**Examples**: Bestiaries, class definitions, race definitions, lore, items, spells

**Rules**:
- Content follows Core and Extension mechanics
- Content does NOT define new mechanics
- Content is DOWNSTREAM (not in TDGS repository)

### Layer 4: Game Layer

**Definition**: Implementation and user-facing products

**Examples**: User interfaces, character builders, VTTs, bots, playable games

**Rules**:
- Game Layer consumes Core, Extensions, and Content
- Game Layer MAY make UX decisions
- Game Layer SHALL NOT alter underlying mechanics
- Game Layer is DOWNSTREAM (not in TDGS repository)

---

## Document Classification

### Badges

| Badge | Meaning | Numbered | In Repo |
|-------|---------|----------|---------|
| **Foundational** | Project philosophy, structure, conventions | No | Yes |
| **Core** | Foundational mechanics, immutable from downstream | Yes | Yes |
| **Extension** | Complementary mechanical modules | No | Yes |
| **Supplemental** | Reference material (e.g., Glossary) | No | Yes |

### Document Numbering Rules

- ONLY Core documents receive numbers
- Format: "Document #: Title"
- TacticalDice assigns numbers upon acceptance
- Numbers are sequential
- Numbers are NEVER reused
- Numbered = Core (visual indicator)

### Deprecation Rules

- Deprecated documents are marked but retained
- Deprecating a Core document triggers MAJOR version change
- Previous versions remain available

---

## Versioning

**Pattern**: `{Major}.{Minor}.{Revision}`

| Component | Meaning | Triggers |
|-----------|---------|----------|
| **Major** | Breaking change | Core reimagined, Core doc deprecated, Extensions break |
| **Minor** | Non-breaking change | New mechanics, new Official Extensions, refinements |
| **Revision** | Non-mechanical fix | Spelling, grammar, formatting, wording |

**Compatibility**:
- Major change: downstream MAY break
- Minor change: downstream SHOULD continue working
- Revision: no impact

---

## Documentation Standards

### Canonical Source

**https://tacticaldice.com/docs/tdgs is ALWAYS canonical.**

- Repository contains same information
- Always link to TacticalDice.com, not repository

### ForAI Requirement

**Every TDGS document SHALL have a ForAI companion.**

- Naming: `{documentname}forai`
- Same canonical information
- Restructured for machine parseability
- No flavor text or narrative framing
- Consistent structure
- Front-loaded key information
- Minimal ambiguity

### Data Interchange Format

**JSON is the default portable format.**

Applies to:
- Character sheets
- Entity definitions
- Exported game state
- Interoperable data exchange

Does NOT apply to:
- Code files
- Documentation
- Internal storage (use whatever you want internally)

### Cross-Reference Rules

- Use document title or number (for Core)
- Link to canonical source (TacticalDice.com)
- Do not duplicate definitions; reference them
- Glossary aggregates FROM other documents (not the reverse)

---

## Mechanical Transparency Principle

**TDGS mechanics are intentionally transparent.**

- Resolution formula is visible
- Math is explicit
- Outcomes follow from mechanics, not hidden judgment
- Players know what they need to roll
- Players know why they succeeded or failed

**Extensions SHOULD maintain transparency.**

Departing from transparency (hidden modifiers, secret rolls, GM-fiat mechanics) is valid but against TDGS spirit.

---

## Licensing

### Engine (Core, Extensions, Foundational, Supplemental)

**MIT License**

- Free to use, modify, redistribute
- Commercial use permitted
- Forking permitted
- No viral obligations

### Characters (dice mascots)

**NOT covered by MIT License**

- Intellectual property of TacticalDice.com
- NOT released to public domain
- Reserved for official website only

Characters: Sir Critsalot, Decimancer, Flamey Eight-ball, Tetrahex the Obscure, Nyxara Tidelight, Hundröd the Uncountable, Plushmaw the Unrollable, Flippity Cent, His Rolliness the Sixth

**Repository documents**:
- SHALL NOT include character callouts
- SHALL NOT include character images
- SHALL NOT reference characters as if present

---

## Contributing Rules

### Pre-Contribution Checklist

1. Read Conventions document (this document)
2. Read Intent document
3. Identify target layer
4. Identify appropriate badge

### Contribution Requirements

1. Follow normative language (SHALL/SHOULD/MAY)
2. Respect layer boundaries
3. Create both human-readable AND ForAI versions
4. Use JSON for portable data
5. No character callouts in repository

### Core Pull Request Criteria

Core PRs face HIGH bar. Accepted when:

1. Genuine gap exists that Extensions cannot address
2. Change is backward compatible OR has clear migration path
3. Change has been discussed and vetted
4. Mathematical and systemic implications are understood

"I want it different" is NOT sufficient justification.

---

## Quick Reference: What Goes Where

| If creating... | Layer | Badge | Numbered | Repo |
|----------------|-------|-------|----------|------|
| Fundamental mechanic | Core | Core | Yes | Yes |
| New mechanical module | Extension | Extension | No | Yes (if Official) |
| Project governance doc | N/A | Foundational | No | Yes |
| Reference material | N/A | Supplemental | No | Yes |
| Bestiary, classes, items | Content | N/A | No | No (downstream) |
| Character builder, VTT | Game Layer | N/A | No | No (downstream) |

---

## Quick Reference: Constraint Summary

**ABSOLUTE (SHALL/SHALL NOT)**:
- Extensions SHALL NOT redefine Core mechanics
- Extensions SHALL NOT override Core mechanics
- Game Layer SHALL NOT alter underlying mechanics
- Every document SHALL have ForAI companion
- Repository documents SHALL NOT include character callouts/images

**STRONG (SHOULD/SHOULD NOT)**:
- Extensions SHOULD provide new capabilities, not replacements
- Extensions SHOULD maintain mechanical transparency
- Downstream SHOULD continue working across Minor versions

**PERMITTED (MAY)**:
- Extensions MAY NOT contradict Core mechanics (prohibition)
- Game Layer MAY make UX decisions
- Downstream MAY break on Major version change
- Community Extensions MAY use any license

---

## End of Document
