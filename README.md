# Nostr UX Research Study

A meta research study on UX best practices and design patterns for Nostr consumer applications.

## Overview

This project synthesizes research on user experience design for social applications and applies it to the unique challenges of building Nostr clients. It's designed to help Nostr developers create better user experiences by learning from both mainstream social app patterns and Nostr-specific considerations.

**Core Thesis:** Good UX beats protocol purity. Ship working experiences, then add features.

## The Problem

Current state of Nostr apps (based on 2024-2025 data):
- **30-day user retention trending to 0%** for recent cohorts
- **15-20 minute onboarding** drives user abandonment
- **All clients in "alpha state"** with reliability issues
- Users need **5-6 different clients** to work around bugs
- Cross-client data loss and inconsistency
- DAU stuck at 10,000-12,000 trusted pubkeys

**Root causes:**
- Feature bloat without user validation
- Protocol complexity exposed to end users
- Core interactions shipped before they're reliable
- Power user features treated as essential

## Target Audience

This research is for:
- **Nostr developers** building consumer social apps (mobile, web, desktop)
- **Product designers** working on Nostr clients
- **Mainstream developers** evaluating whether to build on Nostr

**Assumed knowledge:** Basics of Nostr protocols (relays, events, NIPs)

## The 6 Critical Patterns

Based on research into Nostr apps' typical weaknesses, this study focuses on:

1. **Onboarding & First-Run Experience** - Get to value fast, defer complexity
2. **Content Discovery & Feed Quality** - Solve the cold start problem
3. **Core Interaction Loops** - Make posting/replying/reacting work perfectly
4. **Performance & Perceived Speed** - Optimistic UI, loading states, reliability
5. **Progressive Complexity** - Reveal power features gradually (relays, signers)
6. **Cross-Client Consistency** - Following/follower sync, data integrity

Each pattern includes:
- Problem statement (research-backed)
- Universal principles (70% - applicable to any social app)
- Nostr-specific considerations (30%)
- Pattern library (concrete examples)
- Anti-patterns (what not to do)
- Validation checklist (how to measure success)

## The Validation Framework

A meta-pattern addressing "features without validation" problem.

**Three-question filter before building features:**
1. Does this help users accomplish their core goal?
2. Have we validated this solves a real problem?
3. Can we measure if it's working?

**Core principle:** Ship small, validate fast. Core interactions before new features.

## Project Structure

```
nostr-ux-research/
├── README.md                    # This file
├── OUTLINE.md                   # Complete study structure
├── CLAUDE.md                    # Project context and guidelines
├── patterns/                    # Detailed pattern documentation
│   ├── 01-onboarding.md
│   ├── 02-content-discovery.md
│   ├── 03-core-interactions.md
│   ├── 04-performance.md
│   ├── 05-progressive-complexity.md
│   └── 06-cross-client-consistency.md
├── validation-framework.md      # Meta-pattern for feature validation
├── implementation-guide.md      # Where to start, how to measure
└── appendices/
    ├── case-studies.md          # Successful patterns from mainstream apps
    ├── resources.md             # Nostr Design, NIPs, design systems
    ├── glossary.md              # Terms for mainstream developers
    └── methodology.md           # How this research was conducted
```

## Content Balance

- **70%** - Universal UX principles (applicable to any social app)
- **30%** - Nostr-specific considerations (relays, keys, zaps, censorship-resistance)

This balance makes the research valuable for both existing Nostr developers and mainstream developers evaluating the platform.

## Status

🚧 **Work in Progress** - Currently in early development phase.

**Completed:**
- [x] Initial research on Nostr client UX problems
- [x] Pattern identification and prioritization
- [x] Complete study structure and outline

**In Progress:**
- [ ] Detailed pattern documentation
- [ ] Case studies and examples
- [ ] Visual diagrams and flows
- [ ] Code examples

**Planned:**
- [ ] Community feedback and iteration
- [ ] Video walkthrough
- [ ] Summary quick-start guide

## Research Methodology

This study synthesizes:
- Academic HCI literature on social media UX
- Industry design systems (Apple HIG, Material Design)
- User feedback from Nostr clients (Damus, Amethyst, Primal, Snort, etc.)
- Retention and usage data (nostr.band)
- Developer discussions on UX challenges
- Successful patterns from mainstream social apps

Full methodology documented in [appendices/methodology.md](appendices/methodology.md) (coming soon).

## Success Criteria

We'll know this is valuable when:
- It generates substantive discussion on Nostr
- Developers reference it in client changelogs
- Measurable UX improvements appear in Nostr clients
- Cross-client coordination on core patterns emerges
- Retention metrics improve across the ecosystem

## Contributing & Feedback

This research is being developed in the open. Feedback welcome via:
- GitHub Issues (questions, suggestions, corrections)
- Pull requests (examples, case studies, additional research)
- Nostr discussions (links will be posted when content is ready)

## Related Resources

- [Nostr Design](https://nostrdesign.org/) - Design patterns and guidelines for Nostr
- [Awesome Nostr](https://github.com/aljazceru/awesome-nostr) - Collection of Nostr projects
- [Nostr NIPs](https://github.com/nostr-protocol/nips) - Protocol specifications

## License

This research is shared openly for the benefit of the Nostr community.

## Author

**Shawn Yeager** ([@shawnyeager](https://github.com/shawnyeager))

---

*Last updated: November 2025*
