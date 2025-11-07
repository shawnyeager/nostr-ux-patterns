# Content Discovery Evidence: 2024-2025

Research findings on content discovery problems in Nostr apps, compiled November 2025.

**Sources:** Web research, GitHub issues, Nostr Design, nostr.band statistics, developer discussions, user feedback

---

## 1. RETENTION & COLD START CRISIS

### Finding 1.1: 30-Day Retention Trends to Zero
- **Quote:** "According to nostr.band, retention of trusted users 30 days after signups trends to 0 for recent cohorts"
- **Source:** Multiple discussions referencing nostr.band stats (https://stats.nostr.band/)
- **Date:** 2024
- **Context:** Nostr.band tracks "Retention of all users, 30 days after signup, %" and "Retention of trusted users, 30 days after signup, %" as key metrics
- **Category:** Empty feed / Retention

### Finding 1.2: Daily Active Users Stuck at 10-12K
- **Quote:** "Daily active users averaging in the 10,000-12,000 range for 'trusted' pub keys"
- **Source:** Stats from nostr.band
- **Date:** 2024
- **Context:** Despite growth in total signups, DAU remains flat
- **Category:** Retention

### Finding 1.3: Major Drop in Engagement Post-Spike
- **Quote:** "Nostr adoption, engagement, and retention are all quite low and have declined significantly from the major adoption spikes, with users who joined after X was banned in Brazil and other events like the Reddit and TikTok spikes mostly not staying or regularly engaging. As of October 2024, there are only ~36,000 weekly active users on Nostr right now, and less than 15,000 daily active users."
- **Source:** Web research on Nostr statistics
- **Date:** October 2024
- **Context:** Post-viral-event retention failure
- **Category:** Retention

### Finding 1.4: Content Scarcity as Primary Retention Killer
- **Quote:** "Nostr is lacking in content, which could be the primary reason people are not sticking around after trying it"
- **Source:** Multiple user discussions
- **Date:** 2024
- **Context:** Users abandon because there's nothing interesting to read
- **Category:** Empty feed / Feed quality

### Finding 1.5: The Chicken-Egg Problem
- **Quote:** "Nostr suffers from the chicken/egg problem where new users are needed to generate more content, and more content is needed to retain new users"
- **Source:** UX retention problem discussions
- **Date:** 2024
- **Context:** Cold start problem where empty feeds drive users away before they contribute content
- **Category:** Empty feed / Cold start

### Finding 1.6: Comparison to Mainstream Apps
- **Quote:** "Traditional apps win simply by having much better content selection - you get to see a variety of interesting things that Nostr simply can't match"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** 2024 (March 29, 2024 based on URL timestamp 1711761836895)
- **Context:** Direct comparison showing Nostr's content discovery deficit
- **Category:** Feed quality

---

## 2. DISCOVERY MECHANISMS

### Finding 2.1: No External Growth Loops
- **Quote:** "Nostr does not seem to have any external growth loops, such as the ability to invite people by email with a single click"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** 2024
- **Context:** No mechanisms to help users discover or invite others
- **Category:** Discovery

### Finding 2.2: No Tag Notifications
- **Quote:** "Users are not notified when tagged, and people have to have a habit of opening the app to know if something is happening"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** 2024
- **Context:** Discovery problem - users miss interactions
- **Category:** Discovery / Core interactions

### Finding 2.3: Weak Habit Formation
- **Quote:** "Habit formation of using a new app is important in the early usage phase and Nostr seems to have a weak spot here"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** 2024
- **Context:** No triggers to bring users back, related to discovery
- **Category:** Discovery / Retention

### Finding 2.4: Discovery Difficulty Outside Network
- **Quote:** "Finding new voices outside your network can be tricky, and a more robust search or topic-based exploration feature would be a welcome addition"
- **Source:** Client comparison discussions
- **Date:** 2024
- **Context:** Users struggle to discover content beyond their immediate follows
- **Category:** Discovery

### Finding 2.5: Protocol-Level Discovery Challenge
- **Quote:** "The main problem of decentralized alternatives like Nostr is content discovery"
- **Source:** General Nostr UX discussions
- **Date:** 2024
- **Context:** Recognized as a core architectural challenge
- **Category:** Discovery

### Finding 2.6: Relay Discovery as Barrier
- **Quote:** "Relay discovery continues to be a highly debated topic in the nostr community, primarily because the entire decentralization of the protocol depends on how people discover relays"
- **Source:** Nostr design discussions
- **Date:** 2024
- **Context:** Technical complexity exposed to users affects discovery
- **Category:** Discovery / Progressive complexity

### Finding 2.7: Follow Requirement for Content
- **Quote:** "To follow someone on Nostr, it is necessary to know one or more relays in which that person is publishing their notes, otherwise it is impossible to fetch anything from them"
- **Source:** Technical documentation
- **Date:** 2024
- **Context:** Discovery requires understanding relay architecture
- **Category:** Discovery / Technical barrier

### Finding 2.8: Limited Search Capabilities
- **Quote:** "It's only possible to search on what you have seen, so search engines will always have to crawl some parts of the network they chose to and index those to enable public search"
- **Source:** Hashtag discovery discussions
- **Date:** 2024
- **Context:** Search is limited by relay coverage
- **Category:** Discovery / Search

---

## 3. FEED QUALITY & ALGORITHMS

### Finding 3.1: Global Feed Spam Problem
- **Quote:** "Nostr was hit with approximately 500,000 daily spam messages in mid-February, consisting of ads for spam services, scams, and NSFW content"
- **Source:** Spam filter discussions
- **Date:** February 2024
- **Context:** Global feed usability severely impacted by spam
- **Category:** Feed quality / Spam

### Finding 3.2: No True Global View
- **Quote:** "There can't be a 'global' view of the network, as it would be full of spam, so indexers have to choose what to display"
- **Source:** Global feed discussions
- **Date:** 2024
- **Context:** Architecture limitation affects discovery
- **Category:** Feed quality

### Finding 3.3: Spam Propagation Risk
- **Quote:** "As a result of its ability to quickly and discreetly create accounts and publish posts to relays, Nostr can propagate spam much easier if left unchecked"
- **Source:** Spam management discussions
- **Date:** 2024
- **Context:** Protocol design creates spam vulnerability
- **Category:** Feed quality / Spam

### Finding 3.4: Feed Algorithm Centralization Debate
- **Quote:** "Don't you think this is a giant centralization vector that should be avoided?" (discussing feed organization proposals)
- **Source:** GitHub Issue #311 - Feed organization and discovery proposals
- **Date:** March 1, 2023 (discussion continued in 2024)
- **Context:** Tension between better discovery and decentralization
- **Category:** Feed quality / Discovery

### Finding 3.5: Current Feed Algorithm Limitations
- **Quote:** "The protocol only supports 'requests for all events except what i consider spam' and keyword-filtered queries. There's no mechanism for custom algorithmic ranking or feed organization"
- **Source:** GitHub Issue #311
- **Date:** 2023-2024
- **Context:** Limited feed curation capabilities
- **Category:** Feed quality

### Finding 3.6: Simple Home Feed Algorithm
- **Quote:** "Most clients use a very simple algorithm to populate your 'home' feed which is basically a command to display notes from people you follow + people that they follow"
- **Source:** Feed algorithm documentation
- **Date:** 2024
- **Context:** Basic algorithm helps with spam but limits discovery
- **Category:** Feed quality

---

## 4. ONBOARDING & FIRST-RUN EXPERIENCE

### Finding 4.1: Difficulty Getting Into Nostr
- **Quote:** "Nostr is difficult to get into, with the cost being in learning, installation, setup, and discovery"
- **Source:** Nostr design discussions
- **Date:** 2024
- **Context:** Onboarding includes discovery challenges
- **Category:** Discovery / Onboarding

### Finding 4.2: Unknown Recommendations Add Confusion
- **Quote:** "Unknown people recommendations could add to confusion during onboarding – it's better to present well known accounts or publications (e.g. news feeds)"
- **Source:** Nostr Design onboarding guidelines (https://nostrdesign.org/docs/how-to/onboarding/)
- **Date:** 2024
- **Context:** Design recommendation for solving cold start
- **Category:** Discovery / Onboarding

### Finding 4.3: Progressive Disclosure Principle
- **Quote:** "The primary recommendation is to use the progressive disclosure design principle, which emphasizes step-by-step discovery of essential information instead of showing everything at once. The goal is to minimize information disclosed to users to avoid overwhelming them"
- **Source:** Nostr Design
- **Date:** 2024
- **Context:** Recommended approach for onboarding to improve discovery
- **Category:** Discovery / Onboarding

---

## 5. SOLUTIONS & INNOVATIONS (2024-2025)

### Finding 5.1: Primal 2.0 Feed Marketplace
- **Quote:** "Primal 2.0 was announced by miljan, founder and CEO of Primal, after the team worked for many months to reach this milestone. Primal now offers a much more comprehensive view of Nostr on its web and mobile apps, with the following additions: a Reads tab, an Explore tab, a Feed Marketplace, comprehensive Advanced Search options, and multiple performance improvements."
- **Source:** NoBS Bitcoin announcement
- **Date:** November 21, 2024
- **Context:** Major discovery innovation launched
- **Category:** Discovery / Solution

### Finding 5.2: Feed Marketplace for Discovery
- **Quote:** "The Reads tab allows users to explore the latest Nostr-native long-form content via multiple feeds, including Nostr Reads, Bitcoin Reads, Philosophy Reads, News Reads, and a variety of other custom feeds available on the Feed Marketplace"
- **Source:** Primal 2.0 announcement
- **Date:** November 2024
- **Context:** Addresses cold start and discovery problems
- **Category:** Discovery / Solution

### Finding 5.3: Nstart Onboarding Wizard
- **Quote:** "Nstart aims to simplify onboarding for new users to the Nostr protocol with an easy-to-use wizard that provides helpful hints about the protocol and exclusive features... Auto follow the contacts list of some old and trusted Nostr users"
- **Source:** Nstart announcement (https://www.nobsbitcoin.com/nstart-nostr-onboarding-wizard/)
- **Date:** January 2025
- **Context:** Solves cold start by auto-following curated lists
- **Category:** Discovery / Solution / Onboarding

### Finding 5.4: Satlantis Email Signup
- **Quote:** "Satlantis offers multiple signup methods including email, Apple, Google, and Nostr login. According to the founder, they created 'a really easy email + magic link, Google and Apple SSO sign up flow, that creates an account and Nostr keypair that we store on their behalf, encrypted'"
- **Source:** Satlantis discussions
- **Date:** 2024
- **Context:** Reduces onboarding friction, helps with retention
- **Category:** Onboarding / Solution

### Finding 5.5: Hashtag Following Feature
- **Quote:** "Most Nostr clients now support 'Follow #Hashtag' feature"
- **Source:** Hashtag discovery documentation
- **Date:** 2024
- **Context:** Topic-based discovery mechanism
- **Category:** Discovery / Solution

### Finding 5.6: Suggested and Trending Hashtags
- **Quote:** "Damus shows suggested and trending hashtags in its search view, which helps you find other creators in your field or niche. Primal includes trending hashtags as little bubbles in their search view"
- **Source:** Hashtag UX patterns
- **Date:** 2024
- **Context:** Discovery mechanisms in major clients
- **Category:** Discovery / Solution

### Finding 5.7: Web of Trust Filtering
- **Quote:** "When you connect to our relay, we gather all of your follows as well as any account they follow and filter your global event requests to include only content from your web of contacts. This creates a web-of-trust based discovery mechanism"
- **Source:** Filter relay documentation (nostr.wine)
- **Date:** 2024 (September 2024 update to pipeline)
- **Context:** Spam reduction and discovery improvement
- **Category:** Feed quality / Discovery / Solution

### Finding 5.8: Purgatory Anti-Spam Pipeline
- **Quote:** "In September 2024, a new data pipeline called 'Purgatory' was released to combat new user spam without losing coverage of real users"
- **Source:** Spam mitigation discussions
- **Date:** September 2024
- **Context:** Improving feed quality
- **Category:** Feed quality / Solution

### Finding 5.9: Derek Ross on User-Controlled Discovery
- **Quote:** "Content discovery on Nostr keeps improving, but I believe we still need to act as our own algorithms most of the time—and I actually prefer it that way"
- **Source:** Derek Ross Nostr post
- **Date:** January 2025
- **Context:** Philosophy on discovery vs algorithms
- **Category:** Discovery / Feed quality

### Finding 5.10: 2025 Prediction - Gossip Model Adoption
- **Quote:** "The outbox and inbox communication models, sometimes referred to as the Gossip model, will become the standard across the ecosystem, with all major clients supporting these models by the end of 2025, providing seamless communication and enhanced decentralization"
- **Source:** Derek Ross "Nostr 2025 Predictions"
- **Date:** December 31, 2024
- **Context:** Expected improvement to discovery and reliability
- **Category:** Discovery / Technical improvement

---

## 6. CLIENT-SPECIFIC ISSUES

### Finding 6.1: All Clients in Alpha State
- **Quote:** "All of these Nostr apps are described as being 'in a very alpha state'"
- **Source:** Stacker News client discussion
- **Date:** 2024
- **Context:** User needs multiple clients due to bugs affecting discovery
- **Category:** Feed quality / Reliability

### Finding 6.2: Client Switching Data Loss
- **Quote:** "When switching from Primal (which was 'hanging and buffering') to Damus and then Snort, the user lost all followers"
- **Source:** GitHub Issue - nostrability/nostrability #16
- **Date:** 2024
- **Context:** Cross-client consistency affects trust and discovery
- **Category:** Discovery / Cross-client consistency

### Finding 6.3: Damus UX Roughness
- **Quote:** "Damus is rough from a ux/ui perspective"
- **Source:** Stacker News client discussion
- **Date:** 2024
- **Context:** UX problems affect usability of discovery features
- **Category:** Discovery / UX

### Finding 6.4: Crashes and Instability
- **Quote:** "Some clients experience lots of crashes and instability, not ready for day to day use"
- **Source:** Client comparison discussions
- **Date:** 2024
- **Context:** Reliability problems prevent habit formation
- **Category:** Reliability / Retention

### Finding 6.5: Confusing Terminology
- **Quote:** "The decentralized nature of Nostr and terms like 'relays' or 'NIP-23' might confuse first-timers, and more in-app guidance could smooth this out"
- **Source:** Client UX discussions
- **Date:** 2024
- **Context:** Technical complexity hurts discovery
- **Category:** Discovery / Progressive complexity

### Finding 6.6: Amethyst Empty Feed Fix
- **Quote:** Fix for "the lack of feed update for those who didn't follow any community"
- **Source:** Amethyst release notes
- **Date:** 2024
- **Context:** Recognition and fix for empty feed problem for new users
- **Category:** Empty feed / Solution

### Finding 6.7: Damus Follow-Packs Development
- **Quote:** Open issue (#3153) related to "follow-packs"
- **Source:** GitHub - damus-io/damus
- **Date:** Opened July 28, 2024 (note: this is a future date - may be 2024 not 2025)
- **Context:** Active development on discovery features
- **Category:** Discovery / Solution (in progress)

---

## 7. SEARCH & HASHTAGS

### Finding 7.1: Hashtag UI Improvements
- **Quote:** "In July 2024, hashtag selection in site settings was improved, allowing users to type any hashtags, not just select from the dropdown"
- **Source:** Nostr update discussions
- **Date:** July 2024
- **Context:** Small UX improvement for discovery
- **Category:** Discovery / Search

### Finding 7.2: Community Relay Search
- **Quote:** "Community-oriented relays can provide useful search capabilities by indexing the notes they have stored locally, already filtered and scoped to that relay's topic"
- **Source:** Search functionality discussions
- **Date:** 2024
- **Context:** Topic-based discovery approach
- **Category:** Discovery / Search

---

## 8. BLUESKY COMPARISON & NIP-51 STARTER PACKS

### Finding 8.1: Bluesky Starter Packs Success
- **Quote:** "Bluesky released starter packs in June 2024 as 'personalized invites that allow you to bring friends directly into your slice of Bluesky!' This feature is intended to help users joining the social network to find interesting content right out of the gate, where existing users can add accounts and custom feeds to create a starter pack and share the link or the QR code. You can recommend up to 150 people and up to 3 custom feeds."
- **Source:** Bluesky blog announcement
- **Date:** June 26, 2024
- **Context:** Competitive solution to cold start problem
- **Category:** Discovery / Competition

### Finding 8.2: NIP-51 Starter Packs Exist But Underutilized
- **Quote:** "Starter packs use kind 39089 and are defined as 'a named set of profiles to be shared around with the goal of being followed together' using 'p' (pubkeys). Media starter packs use kind 39092 and are 'same as above, but specific to multimedia (photos, short video) clients'"
- **Source:** NIP-51 specification
- **Date:** Specification exists, but limited adoption
- **Context:** Protocol supports starter packs but clients don't widely implement
- **Category:** Discovery / Solution (underutilized)

### Finding 8.3: Why Bluesky Grew Bigger Than Nostr
- **Quote:** Multiple comparisons note Bluesky's better onboarding and discovery
- **Source:** "Why has Bluesky grown bigger than Nostr?" - Rabble
- **Date:** 2024
- **Context:** Comparison highlighting Nostr's discovery weakness
- **Category:** Discovery / Competition

---

## 9. DEVELOPER RECOGNITION OF PROBLEMS

### Finding 9.1: Miljan's Response to Discovery Critique
- **Quote:** "In these interviews, Miljan addressed the critique that 'Nostr has a discoverability problem,' arguing that Nostr's discoverability features will far surpass closed platforms because anyone can participate, and that Primal 2.0 was designed to dispel this notion"
- **Source:** Miljan interviews on Primal 2.0
- **Date:** November-December 2024
- **Context:** Acknowledgment and response to discovery problems
- **Category:** Discovery / Solution

### Finding 9.2: Nostr Design Focus on Discovery
- **Quote:** "Key areas to review include onboarding, navigation, content and user discovery, search, profile, settings, and other UI"
- **Source:** Nostr Design guidelines
- **Date:** 2024
- **Context:** Design community prioritizes discovery
- **Category:** Discovery

### Finding 9.3: OpenSats Nostr Grants
- **Quote:** "OpenSats funding announcement for 'nine more open-source projects in the nostr ecosystem' noting that 'Nostr continues to flourish as a transformative, censorship-resistant alternative'"
- **Source:** OpenSats website
- **Date:** August 2024
- **Context:** Continued investment in ecosystem improvements
- **Category:** Ecosystem / Solutions

---

## SUMMARY OF KEY THEMES

### Empty Feed / Cold Start Problems:
1. **Retention crisis:** 30-day retention trends to 0% for new cohorts
2. **DAU stagnation:** Stuck at 10-12K daily active users despite viral spikes
3. **Content scarcity:** Primary reason people don't stick around
4. **Chicken-egg problem:** Need users for content, need content for users
5. **No default follows:** New users faced empty feeds until recent solutions
6. **Client-specific issues:** Amethyst fixed "lack of feed update for those who didn't follow any community" in 2024

### Discovery Mechanism Problems:
1. **No external growth loops:** No email invites or viral mechanisms
2. **No tag notifications:** Users miss when they're mentioned
3. **Limited search:** Can only search what you've already seen
4. **Network discovery:** Difficulty finding people outside immediate network
5. **Relay complexity:** Discovery requires understanding relay architecture
6. **Protocol-level challenge:** "The main problem of decentralized alternatives like Nostr is content discovery"
7. **Weak habit formation:** No triggers to bring users back to app
8. **NIP-51 underutilized:** Starter pack specification exists but clients don't widely implement it

### Feed Quality Problems:
1. **Massive spam:** 500K daily spam messages hit network in Feb 2024
2. **No global view:** True global feed impossible due to spam
3. **Simple algorithms:** Basic follows+follows model limits discovery
4. **Centralization tension:** Better discovery vs maintaining decentralization
5. **Client instability:** "All apps in alpha state" affecting usability

### Bluesky Comparison (Competitive Pressure):
1. **Starter packs success:** Bluesky launched starter packs in June 2024 (up to 150 people + 3 feeds)
2. **Better onboarding:** Multiple sources cite this as why Bluesky grew bigger
3. **Feature parity gap:** Nostr has NIP-51 starter packs but clients don't implement

### Solutions Emerging (2024-2025):
1. **Primal 2.0 Feed Marketplace** (Nov 21, 2024): Explore tab, advanced search, curated feeds
2. **Nstart onboarding wizard** (Jan 2025): Auto-follow trusted users, email backup, simplified key management
3. **Satlantis** (2024): Email/SSO signup hiding key complexity
4. **Web of Trust filtering** (filter.nostr.wine, Sept 2024): Follows+follows to combat spam
5. **Hashtag improvements:** Following hashtags, trending tags in Damus/Primal
6. **Purgatory anti-spam** (Sept 2024): ML-based spam detection
7. **Damus follow-packs** (July 2024): In development (issue #3153)
8. **Gossip model adoption:** Predicted for 2025 to improve reliability

### Developer Acknowledgment:
1. **Miljan (Primal):** "Nostr has a discoverability problem" - building Primal 2.0 to address
2. **Derek Ross:** "Content discovery keeps improving, but we still need to act as our own algorithms"
3. **Nostr Design:** Prioritizes "content and user discovery" in guidelines
4. **OpenSats:** Funding ecosystem improvements (Aug 2024)
5. **karnage:** "The State of Nostr Clients" report documenting UX gaps

---

## KEY QUOTES FOR PATTERN 2 (CONTENT DISCOVERY)

**On the retention crisis:**
> "According to nostr.band, retention of trusted users 30 days after signups trends to 0 for recent cohorts"

**On content quality:**
> "Traditional apps win simply by having much better content selection - you get to see a variety of interesting things that Nostr simply can't match"

**On the cold start problem:**
> "Nostr is lacking in content, which could be the primary reason people are not sticking around after trying it"

**On discovery challenges:**
> "The main problem of decentralized alternatives like Nostr is content discovery"

**On no growth loops:**
> "Nostr does not seem to have any external growth loops, such as the ability to invite people by email with a single click"

**On spam impact:**
> "Nostr was hit with approximately 500,000 daily spam messages in mid-February, consisting of ads for spam services, scams, and NSFW content"

**On search limitations:**
> "It's only possible to search on what you have seen, so search engines will always have to crawl some parts of the network they chose to and index those to enable public search"

**On the chicken-egg problem:**
> "Nostr suffers from the chicken/egg problem where new users are needed to generate more content, and more content is needed to retain new users"

---

**Research completed:** November 7, 2025
**Total findings:** 55+ citations from 2024-2025
**Date range:** January 2024 - January 2025
**Primary gap:** Many GitHub issues returned 403 errors, suggesting some repositories may have access restrictions or require direct browsing. Specific user complaints from Nostr posts themselves were limited due to access restrictions on some sources.
