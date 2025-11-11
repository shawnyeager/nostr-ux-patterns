---
linkTitle: "Introduction"
title: Introduction
weight: 1
---

**Evidence-informed UX patterns for building Nostr clients that people actually use.**

## The Problem

Nostr has a working, censorship-resistant protocol. The critical bottleneck is user experience.

**Current metrics:**

- **30-day retention trending to 0%** for recent cohorts
- **Daily active users stuck at 10,000-12,000** despite viral adoption spikes
- Users often need **multiple clients** to access different features

This is a retention crisis---but it's solvable. Traditional social apps achieve better retention not through centralization, but through better content discovery, reliable core interactions, and streamlined onboarding. All of these are implementable on Nostr.

---

## The Solution

**Six evidence-informed UX patterns** addressing the highest-impact UX problems:

1. **[Onboarding & First-Run Experience](../patterns/01-onboarding)** - Get users to value in under 2 minutes
2. **[Content Discovery & Feed Quality](../patterns/02-content-discovery)** - Solve the empty feed problem
3. **[Core Interaction Loops](../patterns/03-core-interactions)** - Make basic actions reliable
4. **[Performance & Perceived Speed](../patterns/04-performance)** - Feel fast even when slow
5. **[Progressive Complexity](../patterns/05-progressive-complexity)** - Hide advanced features from beginners
6. **[Cross-Client Consistency](../patterns/06-cross-client-consistency)** - Don't lose data when switching apps

Each pattern includes: research-backed problem statements, universal UX principles (70%) + Nostr-specific considerations (30%), concrete implementation examples, anti-patterns to avoid, and validation checklists with measurable metrics.

---

## Who This Is For

- **Nostr developers** building consumer social apps (mobile, web, desktop)
- **Product designers** working on Nostr clients
- **Mainstream developers** evaluating whether to build on Nostr

**Assumed knowledge:** Basics of Nostr protocols (relays, events, NIPs)

---

## Core Principle

**Great UX is the gateway to the protocol's power.**

Ship working experiences, then add features.

---

## How This Was Built

Patterns were identified through analysis of user feedback, usage data, and developer discussions, then solutions were developed by applying established UX principles to Nostr's specific challenges. Draws on industry design systems (Apple HIG, Material Design), available HCI research, Nostr-specific data (retention metrics, user complaints, GitHub issues), and mainstream app practices (TikTok, Instagram, Bluesky, Discord). 100+ sources cited throughout.

**Content balance:** 70% universal principles (applicable to any social app) + 30% Nostr-specific considerations (relays, keys, decentralization)

**[View complete approach and references →](../research/methodology)**

This project was developed by [Shawn Yeager](https://github.com/shawnyeager).

---

## Next Steps

{{< cards >}}
  {{< card link="quick-start/" title="Quick Start" subtitle="Get up to speed in 5-30 minutes" icon="lightning-bolt" >}}
  {{< card link="../foundation/" title="Foundation" subtitle="Learn the validation framework" icon="academic-cap" >}}
  {{< card link="../patterns/" title="View Patterns" subtitle="Dive into the 6 critical patterns" icon="collection" >}}
{{< /cards >}}
