# Contributing to TDGS

TDGS is meant to be grown, not owned.

We welcome contributions from game designers, developers, GMs, players, and AI enthusiasts. This document explains how to contribute effectively.

By contributing, you agree to abide by our [Code of Conduct](CODE_OF_CONDUCT.md).

## The Golden Rules

Before contributing anything, internalize these:

1. **Core is immutable from downstream.** Extensions cannot change Core. Content cannot change Core. If your contribution requires Core to be different, that is a high bar, carefully considered, and rarely accepted.

2. **Extensions extend. They never override.** An extension that redefines Core mechanics is not an extension. It is a fork.

3. **ForAI documentation is required.** Every specification document needs a ForAI companion. If you submit a new extension, you must submit both versions.

4. **Three constituencies, always.** Every mechanic must work for humans at tables, computers running software, and AI. If any constituency cannot use it, the design needs work.

## What We Welcome

- Errata and bug fixes
- Clarifications to existing documentation
- New Extensions that complement Core
- Improvements to ForAI documentation
- Tooling, implementations, and integrations
- Translations (with ForAI versions)

## What Belongs Elsewhere

- **Content** (bestiaries, classes, items, adventures): Build this in your own project using TDGS. Content is downstream, not part of this repo.
- **Game Layer** (VTTs, character builders, apps): Same. Build it, release it, tell us about it. We would love to see it.
- **Forks and alternate interpretations**: The MIT License permits this. Fork away. Just do not call it official TDGS.

## Contribution Process

### Small Fixes

Typos, broken links, minor clarifications, formatting fixes.

**Process:** Submit a PR directly. No issue needed.

### Larger Changes

Significant rewrites, new sections, mechanical clarifications that change meaning.

**Process:**
1. Open an issue describing the change and why it matters
2. Discussion happens
3. If there is consensus, submit a PR referencing the issue

### New Extensions

Extensions are significant work. Discuss before building.

**Process:**
1. Open an issue with the extension concept
2. Include: purpose, scope, which Core documents it builds on, why it belongs in the official repo vs. a community extension
3. Discussion happens (community input welcome)
4. If the concept is viable, write the extension
5. Submit a PR with both the human-readable and ForAI versions
6. PR must reference the original issue

**Note:** Not every extension belongs in the official repo. Community Extensions are valuable and encouraged. The official repo maintains a curated scope focused on general utility and broad applicability.

### Core Change Proposals

This is the high bar.

Core is the foundation. Everything rests on it. Changes to Core ripple through every extension, every implementation, every game built on TDGS.

**Process:**
1. Open an issue labeled "Core Change Proposal"
2. Explain: what change, why it is necessary, what breaks if we do not change it, what breaks if we do
3. Extended discussion happens
4. The Tactical Dice team makes the final call
5. If accepted, we will coordinate the change and version bump

Most Core change proposals will be declined. This is not gatekeeping. It is structural integrity. The answer to "Core should work differently" is usually "build an extension" or "fork the project."

## Documentation Standards

### Follow Existing Patterns

Look at how existing documents are structured. Match that structure.

- Same heading hierarchy
- Same use of tables vs. prose
- Same level of detail
- Same voice and tone

### Normative Language

TDGS uses precise language. Use it correctly.

| Term | Meaning |
|------|---------|
| **SHALL / SHALL NOT** | Absolute requirement or prohibition. No exceptions. |
| **SHOULD / SHOULD NOT** | Strong recommendation. Deviation permitted with good justification. |
| **MAY / MAY NOT** | Permission granted or not granted. Freedom, not obligation. |

### ForAI Documentation

Every specification needs a ForAI version. These are not summaries. They are reformatted for AI comprehension:

- More explicit structure
- Less narrative flow
- Clearer cross-references
- Same mechanical content, different presentation

If you are unsure how to write ForAI documentation, study the existing pairs in `/core` and `/core/forai`.

## Document Numbering

**Only Core documents receive document numbers.**

**Only the Tactical Dice team assigns document numbers.**

If you propose a new Core document (rare), do not assign it a number. Submit it unnumbered. If accepted, we assign the number. This keeps document numbers stable as permanent references.

## Review Process

The Tactical Dice team reviews all contributions.

We aim to:
- Acknowledge PRs within a few days
- Provide substantive feedback within two weeks
- Be clear about why something is accepted or declined

We aspire to broader community governance as TDGS grows. For now, the team makes final calls, but community input genuinely shapes decisions. The Discord is a good place for early discussion before formal proposals.

## Licensing

By submitting a contribution, you agree that your contribution is licensed under the MIT License, the same as the rest of TDGS.

You retain copyright on your contribution. You are granting permission for it to be included in TDGS under MIT terms.

## Questions?

- **Discord:** [Join the conversation](https://discord.gg/tTpjN4hQVs)
- **Issues:** Open an issue labeled "Question"

---

Thank you for helping TDGS grow.
