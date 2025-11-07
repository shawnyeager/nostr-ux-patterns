# CLAUDE.md

This file provides guidance to Claude Code when working with this Nostr UX research study repository.

---

## Project Overview

**Repository:** nostr-ux-research
**Purpose:** Meta research study on UX best practices for Nostr consumer applications
**Owner:** Shawn Yeager (@shawnyeager)
**Target Audience:** Nostr developers building consumer apps (social clients)

**Core Thesis:** Good UX beats protocol purity. Ship working experiences, then add features.

---

## Project Goals & Context

### Primary Goal
Help existing Nostr developers improve their UX, while being useful enough for mainstream developers to understand Nostr app development.

### Target Frustrations Being Addressed
1. **Naive feature bloat:** Piling on features without user validation
2. **Protocol purism:** Thinking that protocol purity will somehow win when the UX is poor

### Success Criteria
We'll know this is valuable based on **the discussion it generates on Nostr** itself.

---

## Scope & Approach (From Initial Interview)

### Depth vs Breadth
- **Deep dive on 5-7 critical patterns** (not broad coverage of 15-20)
- Patterns chosen based on research of Nostr apps' typical weaknesses
- Each pattern: thorough treatment with examples, anti-patterns, validation

### Content Balance
- **70%:** Universal social app UX principles (applicable to any platform)
- **30%:** Nostr-specific considerations (relays, keys, zaps, censorship-resistance)

### Audience Profile
- **Mix:** Mobile developers (iOS/Android) + Web developers (React, Vue, etc.)
- **Level:** Mid to senior developers (junior devs have bigger problems)
- **Nostr Knowledge:** Assume they know basics of Nostr protocols

### Tone & Style
- **Balanced:** Principles + rationale (not purely academic, not purely prescriptive)
- Evidence-based with citations where useful
- Opinionated where it helps ("just do this" when appropriate)
- Practical over theoretical

### Length Target
"Just make it good" - no specific page count constraints

---

## Research Findings (Foundation for the 6 Patterns)

### Primary Issues Identified

**Retention Crisis:**
- 30-day retention trends to 0% for recent cohorts
- Daily active users stuck at 10,000-12,000 "trusted" pubkeys
- Users need 5-6 different clients to work around bugs
- All apps described as "alpha state"

**Onboarding Failure:**
- 15-20 minute setup process
- Key management overwhelming and terrifying (loss = permanent identity loss)
- Relay selection too complex for new users
- Users abandon before reaching value

**Content Discovery Problems:**
- "Traditional apps win by having much better content selection"
- Cold start problem: empty feeds after signup
- No effective discovery mechanisms
- Chicken/egg: need users for content, need content for users

**Core Reliability Issues:**
- Posts disappearing seconds after posting
- Cross-client data loss (following/followers disappear when switching apps)
- Missing notifications
- Apps hanging/buffering
- Crashes and performance problems

**Complexity Exposure:**
- Protocol complexity exposed to end users
- Relay management shown to beginners
- Signer setup (NIP-46) too complex for onboarding
- Tech jargon in user-facing UI

**No Growth Loops:**
- No email invites
- Users not notified when tagged
- No habit formation triggers

### Root Causes
- Feature bloat without validating core UX works
- Protocol complexity exposed to end users
- Shipping features before core interactions are reliable
- Multi-relay coordination without optimization
- Power user features treated as essential
- Poor relay coordination and data validation

---

## The 6 Critical Patterns

Based on research findings, these patterns address the highest-impact UX problems:

1. **Onboarding & First-Run Experience**
   - Problem: 15-20 min setup, key management overwhelming
   - Impact: Users abandon before reaching value

2. **Content Discovery & Feed Quality**
   - Problem: "Traditional apps win by having much better content selection"
   - Impact: Users bounce because feed is boring/empty

3. **Core Interaction Loops**
   - Problem: Posts disappear, notifications missing, basic actions unreliable
   - Impact: Users lose trust, abandon platform

4. **Performance & Perceived Speed**
   - Problem: Apps hang/buffer, crashes, slow loads
   - Impact: Users perceive app as broken

5. **Progressive Complexity**
   - Problem: Exposing relay management, key signers, NIPs to all users
   - Impact: Overwhelming, users ignore or leave

6. **Cross-Client Consistency & Data Integrity**
   - Problem: "Lost all followers when switching from Primal → Damus → Snort"
   - Impact: Users don't trust the platform

---

## Structure & Format

### Pattern Documentation Structure
Each pattern follows this format:
1. **Problem Statement** (research-backed)
2. **Universal Principles** (70% - applicable to any social app)
3. **Nostr-Specific Considerations** (30%)
4. **Pattern Library** (concrete examples)
5. **Anti-Patterns** (what not to do)
6. **Validation Checklist** (how to measure if it's working)

### Key Sections
- **Part 0:** Introduction, context, and the Validation Framework (meta-pattern)
- **Parts 1-6:** The 6 critical patterns
- **Part 7:** Implementation guide (where to start, how to measure, common traps)
- **Part 8:** Appendices (case studies, resources, glossary, methodology)

### Delivery Format
- **Primary:** GitHub repository (markdown)
- Each pattern = detailed markdown file
- Code examples where relevant
- Visual diagrams for complex flows
- Links to reference implementations

**Supplementary:**
- Summary version (TL;DR for each pattern)
- Discussion thread on Nostr
- Video walkthrough (optional)

---

## The Validation Framework (Meta-Pattern)

A central theme woven throughout all patterns to address "features without validation" problem.

**The Three-Question Filter:**
1. Does this help users accomplish their core goal?
2. Have we validated this solves a real problem?
3. Can we measure if it's working?

**Principles:**
- Evidence-based design: Metrics that matter for social apps
- When to ship vs when to validate first
- Ship small, validate fast
- Core interactions before new features

**Common Traps to Avoid:**
- "We need feature X because competitor has it"
- "Protocol purity over pragmatic UX"
- "Power users will configure it themselves"
- "We'll fix UX after we add more features"

---

## Development Workflow

### File Organization
```
nostr-ux-research/
├── CLAUDE.md              # This file
├── OUTLINE.md             # Complete structure (created)
├── README.md              # Public-facing intro (to create)
├── patterns/
│   ├── 01-onboarding.md
│   ├── 02-content-discovery.md
│   ├── 03-core-interactions.md
│   ├── 04-performance.md
│   ├── 05-progressive-complexity.md
│   └── 06-cross-client-consistency.md
├── validation-framework.md
├── implementation-guide.md
└── appendices/
    ├── case-studies.md
    ├── resources.md
    ├── glossary.md
    └── methodology.md
```

### Next Steps (Where We Left Off)
1. ✅ Created OUTLINE.md with full structure
2. ✅ Committed to local repo
3. ⏳ **PENDING:** Push to GitHub (waiting for explicit permission per git rules)
4. **TODO:** Get feedback on outline from Shawn
5. **TODO:** Create README.md (public-facing introduction)
6. **TODO:** Begin detailed pattern documentation (start with Pattern 1: Onboarding)
7. **TODO:** Gather examples and case studies
8. **TODO:** Iterative refinement based on feedback

### Git Workflow
- **Branch:** master (or main, depending on repo setup)
- **Commit style:** Descriptive messages explaining changes
- **Push policy:** NEVER push without explicit permission ("ship it" or direct request)

---

## Research Sources & Methodology

### Sources Used
- Web research on Nostr client UX problems (2024-2025)
- User complaints and feedback (Damus, Amethyst, Primal, Snort)
- Nostr Design website (nostrdesign.org)
- Developer discussions on UX challenges
- Retention and usage data (nostr.band)

### What Still Needs Research
- Academic HCI literature on social media UX
- Industry design systems (Apple HIG, Material Design)
- Detailed audit of 10-15 popular Nostr clients
- Developer interviews/surveys
- Specific NIPs with UX implications
- Case studies from successful social apps (TikTok, Instagram, Mastodon, Discord)

---

## Writing Guidelines

### Voice & Tone
- Direct and practical
- Balanced (not preachy, not academic)
- Opinionated where it helps decision-making
- Evidence-based with research citations
- Respectful of Nostr developers' work while being honest about problems

### What to Emphasize
- **Pragmatism over purity:** UX wins matter more than protocol elegance
- **Validation before features:** Measure, don't guess
- **User empathy:** Think like a mainstream user, not a power user
- **Concrete examples:** Show, don't just tell
- **Anti-patterns:** Learn from what doesn't work

### What to Avoid
- Condescension toward Nostr developers
- Pure theory without practical application
- Feature checklists without rationale
- Mainstream app apologetics (acknowledge Nostr's unique strengths)
- Over-emphasis on what's broken (balance with solutions)

---

## Key Nostr Concepts (Quick Reference)

For context when writing:

- **NIPs:** Nostr Implementation Possibilities (protocol specs)
- **Relays:** Servers that store and relay events
- **Events:** The basic unit of Nostr data
- **npub/nsec:** Public/private keys (hex encoded differently)
- **Kind 0:** Metadata (profile info)
- **Kind 1:** Short text notes (tweets)
- **Kind 3:** Contact lists (following)
- **Zaps:** Lightning payments integrated into Nostr
- **Web of Trust (WoT):** Trust network based on social graph
- **Signer apps (NIP-46):** Separate key management apps
- **Outbox model (NIP-65):** User-defined relay preferences

---

## Questions to Ask Shawn for Clarification

If you need guidance while building out content:

1. Specific Nostr clients to highlight (positive or negative examples)?
2. Are there Nostr developers you want to collaborate with or get feedback from?
3. Should we reach out to nostrdesign.org team for coordination?
4. Timeline expectations for completion?
5. Where will this be promoted (specific Nostr communities, events)?
6. Any sensitive topics to avoid (specific clients, developers, drama)?

---

## Communication Preferences

Based on CLAUDE.md patterns from other repos:

- Be concise and clear
- Don't push to GitHub without explicit permission
- Ask before creating new files if unsure
- Provide options rather than assuming preferences
- Focus on the work, not the process

---

## Success Metrics (How We'll Know This Works)

### Short-term (0-3 months)
- Generates substantive discussion on Nostr
- Developers reference it in client changelogs
- Nostr Design website links to it
- Other researchers/designers cite it

### Medium-term (3-6 months)
- Measurable UX improvements in Nostr clients
- Cross-client coordination on core patterns emerges
- New clients launch using these principles

### Long-term (6-12 months)
- Retention metrics improve across ecosystem
- User complaints shift from "UX is broken" to feature requests
- Mainstream developers start building on Nostr

---

## Current State Summary

**Files Created:**
- OUTLINE.md - Complete structure and outline (committed locally, not pushed)
- CLAUDE.md - This file (not yet committed)

**Status:**
- Structure validated ✓
- Ready for Shawn's feedback on outline
- Ready to begin pattern documentation once approved
- Waiting for push permission

**Last Context:**
- User asked if we should start a new chat with the repo selected to avoid working directory issues
- Decision: Create this CLAUDE.md so we can start fresh without losing context
- This file enables Claude to pick up exactly where we left off

---

## For Claude: How to Resume Work

When continuing this project in a new session:

1. **Read this file first** to understand the full context
2. **Read OUTLINE.md** to see the complete structure
3. **Check git status** to see what's been committed/pushed
4. **Ask Shawn** what phase we're in:
   - Still refining outline?
   - Ready to build pattern documentation?
   - Gathering examples and case studies?
   - Editing and refining existing content?
5. **Use the TodoWrite tool** to track progress on multi-step work
6. **Reference the Validation Framework** when making UX recommendations
7. **Remember:** Never push without explicit permission

---

Last updated: November 7, 2025
