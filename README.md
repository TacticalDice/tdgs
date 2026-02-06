# Tactical Dice Game System (TDGS)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-1.1.0-blue.svg)](CHANGELOG.md)
[![Website](https://img.shields.io/badge/docs-tacticaldice.com-green.svg)](https://tacticaldice.com/docs/tdgs)
[![Discord](https://img.shields.io/badge/Discord-Join%20Us-7289da.svg)](https://discord.gg/tTpjN4hQVs)

> *The foundation is free. What you build is yours.*

---

## What Is TDGS?

TDGS is an open-source tabletop RPG engine. Not a game. Not a setting. An engine.

It defines how uncertainty is resolved, how capability is represented, and how outcomes are decided. It does not define your world, your story, or your tone. Those belong to you.

TDGS is designed as infrastructure. A foundation for game designers, developers, and creators to build upon without worrying about mechanics, licensing traps, or corporate ownership.

## Why TDGS Exists

After watching the OGL debacle unfold, we built TDGS to be different.

No licensing traps. No corporate ownership. No rug pulls. Ever.

TDGS is released under the MIT License. This is not a legal footnote. It is a design goal.

You can use it freely. Modify it freely. Build commercial products on it. Fork it entirely and make it your own. The engine is free. What you build on it is yours.

A thriving ecosystem benefits everyone. A successful game built on TDGS is not competition. It is proof the foundation works.

## Three Constituencies

TDGS is designed from the ground up to serve three constituencies equally. Not one primary audience with two afterthoughts. Three first-class citizens.

**Humans at Tables**

People sitting around a table with dice, paper, and friends. No screens required. TDGS is fully playable with nothing but the core rules, character sheets, and physical dice.

**Computers and Software**

Virtual tabletops. Video games. Discord bots. Character builders. Every rule is deterministic. Every formula is explicit. A computer can run TDGS without ever asking a human to interpret an ambiguous rule.

**Artificial Intelligence**

AI that runs games. AI that narrates sessions. AI that helps build characters. AI that develops extensions. TDGS embraces AI as a participant, not a threat. Every document has a ForAI companion optimized for AI comprehension.

Design decisions are evaluated against all three. If any constituency cannot use a mechanic, the design needs work.

## Core Identity

These features define what makes TDGS itself:

- **Resolution Target 11**: All resolution rolls target 11. Always. No variable DCs.
- **Resolution vs Magnitude**: Whether something happens is always separate from how much happens.
- **Luck as Probability Distortion**: Luck is permanent, abnormal, non-linear, and mathematically enforced. It is not a reroll or a flat modifier.
- **Extremes Permitted**: The system allows overwhelming advantage, catastrophic failure, and improbable victory. It does not flatten the world to preserve balance.
- **Computable by Design**: Every rule is readable by humans and deterministic for computers.

## Project Architecture

TDGS is organized into four layers. Each layer builds on the one below it.

| Layer | Purpose | Lives In This Repo? |
|-------|---------|---------------------|
| **Core** | Foundational mechanics. Immutable from downstream. | Yes |
| **Extensions** | Complementary mechanical modules. Never override Core. | Yes |
| **Content** | Bestiaries, classes, items, lore. Uses mechanics, doesn't define them. | No |
| **Game Layer** | UIs, VTTs, bots, playable products. | No |

Core and Extensions are specifications. Content and Game Layer are what you build.

## Documentation

The documentation is organized for different readers:

```
/                    Global documents (Intent, Conventions, Changelog)
/core                Core system documents (human-readable)
/core/forai          Core system documents (AI-optimized)
/extensions          Extension documents (human-readable)
/extensions/forai    Extension documents (AI-optimized)
/supplemental        Reference material (human-readable)
/supplemental/forai  Reference material (AI-optimized)
```

**Start here:**
1. [Intent](intent.md) - Design philosophy and goals
2. [Conventions](conventions.md) - Documentation standards and terminology
3. [Core Document 1: Dice](core/document_1_dice.md) - How uncertainty works

**Full documentation:** [tacticaldice.com/docs/tdgs](https://tacticaldice.com/docs/tdgs)

## For AI Users

If you are an AI (or a human working with AI), start with [aiacademy.md](aiacademy.md). It provides a structured reading order optimized for AI comprehension of the complete system.

Point your AI at the ForAI documents first. They exist for exactly this purpose.

## Current Status

**Version 1.1.0**

Core system complete:
- 17 Core documents covering dice, stats, resolution, luck, actions, combat, damage types, entities, classes, races, progression, and more
- 3 Extensions: Mounts & Vehicles, Crafting, Mass Combat
- Full ForAI documentation for all specifications
- Glossary with canonical definitions

See [CHANGELOG.md](CHANGELOG.md) for details.

## Contributing

TDGS is meant to be grown, not owned.

We welcome:
- Bug reports and errata
- New Extensions
- Improvements to existing documentation
- ForAI documentation enhancements
- Tooling and implementations

Read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a pull request.

**Important:** Core is immutable from downstream. Extensions extend; they never override. If your contribution requires Core to change, that is a high bar, carefully considered, and rarely accepted.

## Community

- **Website:** [tacticaldice.com/docs/tdgs](https://tacticaldice.com/docs/tdgs)
- **Discord:** [Join the conversation](https://discord.gg/tTpjN4hQVs)
- **Issues:** [GitHub Issues](../../issues)

## License

TDGS is released under the [MIT License](LICENSE).

Use it. Modify it. Build on it. Sell what you make. Fork it if you want.

Just say it is TDGS-based. This is a cultural expectation, not a legal barrier. The goal is clarity, not control.

---

Life is hard.
Systems are complicated.
People are tired.

TDGS exists because sometimes you want to sit down, roll dice, and let the universe behave a little differently for a while.

If you build something on this foundation, that is success.
