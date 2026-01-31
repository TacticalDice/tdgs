# Conventions and Concepts

How TDGS is organized and how to speak its language

## Purpose

This document defines the organizational structure, terminology standards, and conventions that govern the TDGS project. It exists to ensure that contributors, creators, and implementers understand how the project is structured and how to maintain consistency as it grows.

TDGS is a carefully organized system. That organization is not accidental. This document explains the rules that keep it coherent.

If you're building on TDGS, extending it, or contributing to it, start here.

## The Three Constituencies

TDGS is designed from the ground up to serve three constituencies equally. Not one primary audience with two afterthoughts. Three first-class citizens.

### Humans at Tables

People sitting around a table with dice, paper, and friends. No screens required.

TDGS must be fully playable with nothing but the core rules, character sheets, and physical dice. The canonical game being developed on this system will translate completely to tabletop play. If you can play it on a computer, you can play it with pencils.

This constituency has existed for decades. It isn't going anywhere.

### Computers and Software

Virtual tabletops. Video games. Discord bots. Character builders. Console RPGs. Anything with a processor.

TDGS is designed to be computable. Every rule is deterministic. Every formula is explicit. There is no "GM discretion required" baked into Core mechanics. A computer can run TDGS without ever asking a human to interpret an ambiguous rule.

This constituency is growing. TDGS is ready for it.

### Artificial Intelligence

AI that runs games. AI that narrates sessions. AI that helps build characters. AI that develops extensions. AI that creates content.

TDGS embraces AI as a participant, not a threat. The ForAI documentation requirement exists because AI is a real constituency, not a novelty. Someone should be able to point an AI at the ForAI documents and have it run a game, assist with worldbuilding, or help develop new content.

The future includes AI at the table. TDGS is designed for that future.

### Equal Access by Design

These three constituencies are not ranked. TDGS does not favor humans over computers or computers over AI.

Design decisions are evaluated against all three:

- Can a human calculate this at the table? 
- Can a computer execute this deterministically?
- Can an AI learn and apply this from documentation?

If the answer to any of these is "no," the design needs work.

This is why TDGS uses fixed thresholds instead of variable DCs. This is why the resolution formula is one formula, not a table of exceptions. This is why every document has a ForAI companion. Equal access is not a feature. It is a design constraint.

### Mechanical Transparency

TDGS mechanics are intentionally transparent.

The resolution formula is visible. The math is explicit. Outcomes follow from mechanics, not from hidden judgment calls. When a player rolls, they know what they need. When they succeed or fail, they know why.

This transparency serves all three constituencies:

- Humans can trust that the dice mean what the dice say
- Computers can execute rules without ambiguity
- AI can model the system without hidden variables

GMs at their own tables can absolutely make house rules. That's their right. But the default contract in TDGS is: mechanics are honest. Players can see the math. The system doesn't hide the odds.

Extensions SHOULD maintain this transparency. An extension that introduces hidden modifiers, secret rolls, or GM-fiat mechanics is departing from the spirit of TDGS. It may still be valid, but it's swimming against the current.

## Open Source and the Ecosystem

TDGS is released under the MIT License. This is not a legal footnote. It is a core design goal.

The MIT License means:

- You can use TDGS freely
- You can modify TDGS freely
- You can redistribute TDGS freely
- You can build commercial products on TDGS
- You can fork TDGS entirely and take it in a new direction

We actively encourage all of this.

Build a game on TDGS and sell it. Create a VTT implementation and charge subscriptions. Write a bestiary and put it on DriveThruRPG. Fork the engine, rename it, and make it your own.

A thriving ecosystem benefits everyone. A successful game built on TDGS isn't competition-it's proof the foundation works. The more people building on this system, the more robust, tested, and valuable it becomes.

The engine is free. What you build on it is yours.

## Normative Language

TDGS documents use precise language to distinguish between requirements, recommendations, and permissions.

| Term | Meaning |
|------|---------|
| **SHALL / SHALL NOT** | Absolute requirement or prohibition. No exceptions. Violating this means you're no longer following TDGS. |
| **SHOULD / SHOULD NOT** | Strong recommendation or discouragement. Deviation permitted but requires good justification. |
| **MAY / MAY NOT** | Permission granted or not granted. Freedom, not obligation. |
| **WILL / WILL NOT** | Statement of fact or consequence, not a command. "Your extension WILL break" is physics, not a rule. |


## Project Architecture

TDGS is organized into four layers. Each layer builds on the one below it. Higher layers depend on lower layers. Lower layers never depend on higher layers.

### Layer 1: Core

Core is the foundation. It defines the mechanics that everything else depends on.

Core includes:

- Resolution mechanics
- The nine attributes
- Dice roles and usage
- Action economy
- Combat fundamentals
- Progression systems
- Entity structure

Core documents are numbered (Document 1, Document 2, etc.) and carry the **Core** badge.

**Core is immutable from the perspective of all other layers.**

Extensions cannot change Core. Content cannot change Core. Games cannot change Core. If something downstream needs Core to be different, either Core receives a pull request (high bar, carefully considered, rarely accepted) or the downstream thing changes.

This isn't gatekeeping. It's load-bearing architecture. Everything rests on Core. If Core shifts, everything shifts.

### Layer 2: Extensions

Extensions add new mechanical modules that complement Core. They are still specifications, not implementations. Examples: Mounts and Vehicles, Mass Combat, Naval Warfare, Crafting Systems.

Extensions operate under strict constraints:

- Extensions SHALL NOT redefine or override Core mechanics
- Extensions MAY NOT contradict Core mechanics
- Extensions SHOULD provide new capabilities, not replacements

An extension that requires Core to change is not an extension. It's a fork. **Extensions extend. They never override.**

#### Official vs Community Extensions

**Official Extensions** live in the TDGS repository, carry the **Extension** badge, and are released under MIT License. They are produced by TacticalDice or accepted via pull request.

**Community Extensions** are created outside the main repository. They're valid TDGS extensions but aren't part of the official repo. Community Extensions can use any license, including proprietary.

Community Extensions can become Official through pull request. TacticalDice curates the official repo for general utility, Core compliance, quality, and ForAI documentation. Not every extension belongs in the official repo-Community Extensions are valuable and encouraged. The official repo simply maintains a curated scope.

Extension documents are never numbered.

### Layer 3: Content

Content is the "stuff" that uses the mechanics-bestiaries, class definitions, races, lore, items, spells. It's concrete rather than abstract.

Content follows Core and Extension mechanics. It doesn't define new ones. A Content document might say "The Fire Drake has STR 22 and the Flame Breath trait." It would not say "Fire Drakes use d12 for resolution instead of d20."

**Content is downstream.** The TDGS repository contains Core, Extensions, and Foundational/Supplemental documents. Content is what studios, developers, and creators build using those specifications.

### Layer 4: Game Layer

The Game Layer is where implementation lives-user interfaces, character builders, VTTs, bots, the actual playable product.

The Game Layer consumes Core, Extensions, and Content. It may make UX decisions, but it SHALL NOT alter the underlying mechanics. A character builder can hide options or reorder stats. It cannot change how stats work.

**The Game Layer is downstream.** Like Content, it's not part of the TDGS repository. It's what people build on the engine.

## Document Classification

TDGS documents are classified by badge and, for Core documents only, by number.

### Badges

| Badge | Meaning |
|-------|---------|
| **Foundational** | Defines project philosophy, structure, or conventions. Not mechanical. Governs how the project operates. |
| **Core** | Defines foundational mechanics. Immutable from downstream. Numbered. |
| **Extension** | Defines complementary mechanical modules. Not numbered. |
| **Supplemental** | Supports the project with reference material. Not mechanical. Not numbered. |

**Foundational vs Supplemental:** Both are non-mechanical, but Foundational documents govern project structure and philosophy (like Intent and this document). Supplemental documents provide reference material (like the Glossary).

### Document Numbering

**ONLY Core documents receive document numbers.**

If a document has "Document #:" in its title, it is Core. If it doesn't, it isn't.

This is a quick visual indicator. Numbered means Core. Unnumbered means everything else.

**TacticalDice assigns document numbers.** A pull request can propose a new Core document, but the document number is assigned upon acceptance. This ensures that document numbers are stable references. Document 2 will always be Document 2, covering the same subject. References to numbered documents never break.

Numbers are assigned sequentially as Core documents are canonized. Numbers are never reused. If Document 7 is deprecated, there will never be a new Document 7.

### Document Deprecation

Deprecated documents are marked as deprecated but retained for historical reference. They remain accessible but are clearly labeled as no longer canonical.

**Deprecating a Core document triggers a Major version change.** This is a significant event. If a numbered Core document is deprecated, the engine has fundamentally changed, and downstream implementations should expect breaking changes. Previous versions of the engine (with the document still active) remain available.

### Badge Assignment

Badges are assigned based on what the document actually does, not what it aspires to be.

When in doubt, Supplemental is the safe default. Promotion to Foundational, Core, or Extension requires deliberate decision and review.

## Documentation Standards

All TDGS documents follow consistent standards to maintain quality and interoperability.

### Canonical Source

**The documents at https://tacticaldice.com/docs/tdgs are ALWAYS the canonical documentation.**

The GitHub repository contains the same information, but TacticalDice.com always displays the latest canonical version. When linking to TDGS documentation, link to TacticalDice.com, not to the repository.

### ForAI Requirement

**Every TDGS document SHALL have a companion ForAI version.**

ForAI versions use the naming convention `{documentname}forai` and contain the same canonical information, restructured for machine parseability. They remove flavor text and narrative framing, use consistent structure, front-load key information, and minimize ambiguity.

The goal: an AI system can ingest ForAI documents and accurately model TDGS mechanics without human interpretation. Reference existing ForAI documents in the repository for patterns. When in doubt, optimize for: "Can an AI read this and correctly implement the mechanic?"

### JSON as Default Portable Format

TDGS targets JSON as the default format for portable data.

This includes:

- Character sheets
- Entity definitions
- Exported game state
- Interoperable data exchange

JSON is chosen because it is:

- Human-readable
- Machine-parseable
- Language-agnostic
- Widely supported

This applies to data interchange, not to code files, documentation, or production content systems. Your game can store data however it wants internally. When data leaves your system for another, JSON is the expected format.

### Cross-Reference Standards

When one document references another:

- Use the document title or number (for Core)
- Link to the canonical source
- Do not duplicate definitions-reference them

If the Glossary defines a term, other documents reference the Glossary. They do not redefine the term locally.

Note: The Glossary compiles definitions FROM the Core and Extension documents. It is a reference that aggregates, not a source that dictates. This is why it carries the Supplemental badge rather than Core.

## Versioning

TDGS uses semantic versioning: `{Major}.{Minor}.{Revision}`

| Component | Meaning | Example Triggers |
|-----------|---------|------------------|
| **Major** | Breaking change. Extremely rare. | Core mechanics reimagined, Core document deprecated, Extensions break |
| **Minor** | Non-breaking changes to Core, Extensions, or Foundational/Supplemental | New mechanics, new Official Extensions, refinements |
| **Revision** | Minor fixes that don't affect mechanics | Spelling, grammar, formatting, wording clarifications |

If the Major version changes, everything built on the previous Major version MAY break. Major version changes represent a new era for the engine and are not taken lightly.

A changelog will be maintained starting with version 1.0.

## Character Callout Policy

The official TDGS website (tacticaldice.com) features character callouts-the dice characters who comment on rules throughout the documentation.

**Character callouts are reserved for the official TDGS website.**

**The characters are NOT covered by the MIT License.** The TDGS engine is open source. The characters (Sir Critsalot, Decimancer, Flamey Eight-ball, Tetrahex the Obscure, Nyxara Tidelight, Hundröd the Uncountable, Plushmaw the Unrollable, Flippity Cent, His Rolliness the Sixth) are the intellectual property of TacticalDice.com and are not released to the public domain.

Documents in the GitHub repository:

- SHALL NOT include character callouts
- SHALL NOT include character images
- SHALL NOT reference the characters as if they were present

This separation is intentional. The engine specification is clean, neutral, and open. The characters add personality to the official site and remain proprietary to TacticalDice.com.

## Contributing to TDGS

Contributors to TDGS are expected to maintain these conventions.

### Before Contributing

1. Read this document
2. Read the Intent document
3. Understand which layer your contribution targets
4. Understand which badge your contribution would carry

### When Contributing

1. Follow normative language conventions (shall/should/may)
2. Respect layer boundaries (especially Core immutability)
3. Create both human-readable and ForAI versions
4. Use JSON for any portable data formats
5. Do not include character callouts in repository documents

### Pull Requests to Core

Pull requests that modify Core face a high bar.

Core changes are considered when:

- A genuine gap exists that Extensions cannot address
- The change is backward compatible or has a clear migration path
- The change has been discussed and vetted
- The mathematical and systemic implications are understood

"I want it to work differently" is not sufficient justification. Core is stable because Core must be stable.

## Document Status

**Status:** Canonical

**Badge:** Foundational

This document defines the organizational conventions for TDGS. All contributors, creators, and implementers should follow the standards established here.
