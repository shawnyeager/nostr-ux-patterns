# References & Bibliography

This document contains all sources cited throughout the Nostr UX Research Study, organized by category.

---

## Citation Key

Citations in pattern documents use this format:
- **[Data:1]** = Data & Analytics (section 1)
- **[Research:12]** = Academic & UX Research (section 2)
- **[Example:5]** = Case Studies & Examples (section 3)
- **[Protocol:3]** = Nostr Protocol Documentation (section 4)
- **[User:8]** = User Feedback & Quotes (section 5)

---

## 1. Data & Analytics Sources

### Nostr Usage & Retention Data

**[Data:1]** Nostr.band Analytics
- **Source:** https://nostr.band/stats
- **Data:** DAU trends, retention cohorts, network growth metrics
- **Date accessed:** November 2025
- **Key findings:** 30-day retention trending to 0% for recent cohorts, DAU stable at 10,000-12,000 trusted pubkeys

**[Data:2]** Nostr Content Discovery and Retention Crisis
- **Source:** Multiple 2024-2025 analyses including nostr.band statistics
- **Date:** 2024-2025
- **Key findings:**
  - Only ~36,000 weekly active users as of October 2024; less than 15,000 daily active
  - Adoption spikes (X ban in Brazil, Reddit/TikTok events) show poor retention
  - Post-viral-event retention failure demonstrates discovery/content problems
- **Relevance:** Pattern 2 (Content Discovery) - Quantifies the retention impact of poor content discovery

**[Data:5]** Nostr Spam Crisis
- **Source:** Web research on spam mitigation discussions
- **Date:** February 2024
- **Key findings:**
  - Nostr hit with approximately 500,000 daily spam messages in mid-February 2024
  - Spam consisted of ads for spam services, scams, and NSFW content
  - Global feed became unusable without filtering
- **Relevance:** Pattern 2 (Content Discovery) - Feed quality problems at scale

### Mainstream App Benchmarks

**[Data:3]** Andreessen Horowitz (a16z) Social App Retention Benchmarks (2023)
- **Source:** a16z Consumer Team
- **URL:** https://a16z.com/do-you-have-lightning-in-a-bottle-how-to-benchmark-your-social-app/
- **Publication:** March 2023
- **Data:** N-day retention benchmarks for social apps (D1/D7/D30)
- **Key findings:**
  - **OK:** D1: 50%, D7: 35%, D30: 20%
  - **Good:** D1: 60%, D7: 40%, D30: 25%
  - **Great:** D1: 70%, D7: 50%, D30: 30%
  - Retention curves typically flatten between D7-D14 and plateau by D20
  - More users reaching "aha moment" in onboarding correlates with better retention across all time periods
- **Relevance:** Nostr's ~0% D30 retention for recent cohorts falls far below even the "OK" threshold (20%)

**[Data:4]** AppsFlyer Mobile App Retention Benchmarks (2024)
- **Source:** AppsFlyer
- **URL:** https://www.appsflyer.com/resources/reports/app-retention-benchmarks/
- **Publication:** 2024 Edition
- **Data:** Global mobile app retention rates by category
- **Key findings:**
  - Social media apps: D1: 26.3%, D7: 9.3%, D30: 3.11%
  - Social media showed +23% YoY growth in retention (Android)
  - iOS retention rates 46% higher than Android across categories
  - Industry baseline shows most apps lose 80% of users in first days
- **Relevance:** Even AppsFlyer's lower benchmarks (3.11% D30) exceed Nostr's near-zero retention, indicating fundamental onboarding/retention failures

---

## 2. Academic & UX Research

### Onboarding & First-Run Experience

**[Research:1]** Time to First Value (TTFV) in Product Onboarding
- **Citation:** Multiple industry sources (UserGuiding, Sixteenventures, MarTech)
- **URLs:**
  - https://sixteenventures.com/customer-onboarding-ttfv
  - https://martech.org/time-to-first-value-the-cx-metric-you-cant-afford-to-ignore/
- **Key findings:**
  - TTFV measures how long it takes for users to experience first meaningful benefit from a product
  - 40% of users abandon products after their first interaction if experience isn't seamless
  - Journey mapping reveals the "true value event" is when customer says "OK, this is worth it"
  - Not about first login or completing setup, but when users realize the outcome aligned with why they tried the product
  - Shorter TTFV correlates with higher user satisfaction and retention
- **Relevance:** Pattern 1 (Onboarding) - Nostr's 15-20 minute setup process massively exceeds acceptable TTFV thresholds

**[Research:2]** Progressive Disclosure in Human-Computer Interaction
- **Citation:** Nielsen, J. (1995). Progressive Disclosure. Nielsen Norman Group.
- **URL:** https://www.nngroup.com/articles/progressive-disclosure/
- **Key findings:**
  - Progressive disclosure defers advanced/rarely used features to secondary screens
  - First introduced by Jakob Nielsen in 1995 to minimize user errors in complex programs
  - Improves 3 of 5 usability components: learnability, efficiency, and error rate
  - Helps novices avoid mistakes and saves time scanning features they don't need
  - Helps advanced users by reducing initial cognitive load
  - Common patterns: accordions, tabs, tooltips, modal dialogs, hypertext
- **Academic extension:** Springer, A., & Whittaker, S. (2019). "Progressive Disclosure: Designing for Effective Transparency." ACM Transactions on Interactive Intelligent Systems.
  - arXiv preprint: https://arxiv.org/pdf/1811.02164
  - Extends progressive disclosure principles to algorithmic transparency
  - Users benefit from initially simplified feedback to build working heuristics
- **Relevance:** Pattern 1 (Onboarding), Pattern 5 (Progressive Complexity) - Nostr clients should hide relay/signer complexity for new users

**[Research:3]** Commitment & Consistency in User Onboarding
- **Citation:** Cialdini, R. B. (2006). *Influence: Science and Practice* (5th ed.). Pearson Education.
- **NN/g Application:** Kate Moran (Nielsen Norman Group). "The Principle of Commitment and Behavioral Consistency."
  - URL: https://www.nngroup.com/articles/commitment-consistency-ux/
- **Key findings:**
  - Behavioral consistency: people tend to behave in manner matching past decisions/behaviors
  - "Once we make a choice or take a stand, we encounter personal and interpersonal pressures to behave consistently with that commitment" (Cialdini)
  - "Foot-in-the-door" technique: small commitments build to larger ones
  - Start with small, low-cost commitments rather than all-or-nothing approaches
  - Examples: Yelp asks for review first, then account creation (leveraging aversion to data loss); Fitbit asks users to state fitness goals early
  - Gradual commitment more effective than immediate large asks
- **Related:** Luke Wroblewski's "Gradual Engagement" principle
  - Showcase product value before requiring information/commitment
  - Duolingo example: experience value before full account creation
- **Relevance:** Pattern 1 (Onboarding) - Nostr should allow browsing/reading before requiring key generation and account setup

### Content Discovery & Feed Algorithms

**[Research:4]** Bluesky Starter Packs Solve Cold Start Problem
- **Citation:** "Bootstrapping Social Networks: Lessons from Bluesky Starter Packs" - Lancaster University, TU Darmstadt, City St George's University of London
- **URL:** https://arxiv.org/pdf/2501.11605
- **Date:** January 2025
- **Key findings:**
  - Starter packs (curated lists of accounts users can follow with one click) accounted for 43% of follow actions during peak periods
  - 20% of all follow relationships during first 6 months came from starter packs
  - Users included in starter packs received 85% more followers and posted 60% more than similar users not included
  - Over 335,000 starter packs were created in the first six months
- **Relevance:** Pattern 2 (Content Discovery) - Research-backed solution to cold start problem directly applicable to Nostr

**[Research:5]** Cold Start Problem in Recommendation Systems (Academic)
- **Citations:**
  - "A social importance and category enhanced cold-start user recommendation system" - Expert Systems with Applications, ScienceDirect
    - URL: https://www.sciencedirect.com/science/article/abs/pii/S0957417425007523
  - "Recruitment From Social Networks for the Cold Start Problem in Mobile Crowdsourcing" - IEEE Internet of Things Journal
    - URL: https://pureportal.coventry.ac.uk/en/publications/recruitment-from-social-networks-for-the-cold-start-problem-in-mo
- **Date:** 2024
- **Key strategies identified:**
  - Using social network information from existing platforms
  - Leveraging collaborative filtering based on similar user behavior
  - Hybrid models combining content-based and collaborative filtering
  - Incorporating user demographics and stated preferences
  - Using community detection to identify similar users
- **Relevance:** Pattern 2 (Content Discovery) - Academic research backing for Web of Trust and social graph-based discovery

**[Research:6]** Algorithmic vs Chronological Feeds: Impact on Engagement ("Better Feeds" Report)
- **Citation:** Georgetown University Knight-Georgetown Institute. "Better Feeds: Algorithms That Put People First"
- **URL:** https://kgi.georgetown.edu/wp-content/uploads/2025/02/Better-Feeds_-Algorithms-That-Put-People-First.pdf
- **Date:** March 2025
- **Key findings:**
  - Moving users from algorithmic to reverse-chronological feeds decreased time spent on platform and user activity over 3 months
  - Chronological feeds did NOT significantly alter levels of polarization, political knowledge, or other attitudes (contrary to common belief)
  - Users compensated by increasing usage on other platforms: Instagram users → TikTok (+36%), YouTube (+20%); Facebook users → Reddit (+52%), YouTube (+21%)
  - Chronological feeds may increase exposure to abuse, amplify untrustworthy content, and create recency bias
  - Suggests false choice between engagement-optimized vs chronological feeds - algorithms can be designed for long-term user value
- **Relevance:** Pattern 2 (Content Discovery) - Critical evidence that pure chronological feeds won't solve retention problems; users will leave for more engaging alternatives

**[Research:7]** Engagement-Based Algorithms Amplify Divisive Content
- **Citation:** "Engagement, user satisfaction, and the amplification of divisive content on social media" - PNAS Nexus, Oxford Academic
- **URLs:**
  - https://academic.oup.com/pnasnexus/article/4/3/pgaf062/8052060
  - https://pmc.ncbi.nlm.nih.gov/articles/PMC11894805/
- **Date:** 2024-2025
- **Key findings:**
  - Preregistered algorithmic audit of Twitter/X found engagement-based ranking amplifies emotionally charged, out-group hostile political content
  - Users report this content makes them feel worse
  - Users do not prefer the political tweets selected by algorithm, suggesting algorithm underperforms in satisfying stated preferences
  - Item-level satisfaction surveys correlate with integrity metrics and can improve retention when used in ranking
- **Relevance:** Pattern 2 (Content Discovery) - WARNING: optimizing purely for engagement (likes, replies, reposts) amplifies divisive content. Nostr algorithms should incorporate user satisfaction signals (muting, reporting, feedback) alongside engagement

**[Research:8]** Social Media as Search Engine for Gen Z
- **Citation:** Multiple 2024-2025 sources including Sked Social "Social search: How to Optimize for Discoverability on TikTok and Instagram (2025)"
- **URL:** https://skedsocial.com/blog/social-search-how-to-optimize-for-discoverability-on-tiktok-and-instagram-2025/
- **Date:** 2024-2025
- **Key findings:**
  - Two in five Americans currently use TikTok as a search engine
  - Over 50% of Gen Z and Millennials prefer social media for product discovery, recommendations, and research over traditional search engines
  - TikTok introduced "Creator Search Insights Tool" in 2024 to help creators optimize for search behavior
  - Platforms are no longer just for scrolling—they're where consumers look for information
- **Relevance:** Pattern 2 (Content Discovery) - Search functionality is now table stakes, not an afterthought. Users expect to search for topics, hashtags, and people as primary discovery mechanism

### Performance & Perceived Speed

**[Research:9]** Perceived Performance vs Actual Performance
- **Citation:** [UX research - to be found]
- **Key finding:** Users perceive apps as faster with skeleton screens and optimistic UI
- **Relevance:** Pattern 4 (Performance)

**[Research:10]** Mobile App Performance Budgets
- **Citation:** [To be researched - Google Web Fundamentals or similar]
- **Key finding:** [Summary]
- **Relevance:** Pattern 4 (Performance)

**[Research:11]** Optimistic UI Patterns
- **Citation:** [To be researched]
- **Key finding:** [Summary]
- **Relevance:** Pattern 3 (Core Interactions), Pattern 4 (Performance)

### Progressive Complexity & Feature Discovery

**[Research:12]** The 80/20 Rule in Feature Usage
- **Citation:** [Product design research - to be found]
- **Key finding:** 80% of users use only 20% of features
- **Relevance:** Pattern 5 (Progressive Complexity)

**[Research:13]** Settings Hierarchy and Configuration Burden
- **Citation:** [UX research - to be researched]
- **Key finding:** [Summary]
- **Relevance:** Pattern 5 (Progressive Complexity)

### Data Consistency & Trust

**[Research:14]** User Trust in Distributed Systems
- **Citation:** [HCI research - to be found]
- **Key finding:** [Summary]
- **Relevance:** Pattern 6 (Cross-Client Consistency)

**[Research:15]** Eventual Consistency and User Experience
- **Citation:** [Distributed systems + UX research]
- **Key finding:** [Summary]
- **Relevance:** Pattern 6 (Cross-Client Consistency)

---

## 3. Case Studies & Examples

### Mainstream App Onboarding

**[Example:1]** TikTok Onboarding Teardown & UX Analysis
- **Sources:**
  - Appcues: "TikTok's addictive, activation-focused user onboarding" - https://goodux.appcues.com/blog/tiktok-user-onboarding
  - UX Planet: Dulenko, V. "How TikTok Design Hooks You Up" - https://uxplanet.org/how-tiktok-design-hooks-you-up-6c889522c7ed
  - Medium: Srivastava, R. "Decoding TikTok's peerless onboarding and curation process" - https://medium.com/@rishdotblog/decoding-tiktoks-peerless-onboarding-and-curation-process-d520f3d17600
  - App Fuel: TikTok Onboarding Flow - https://www.theappfuel.com/examples/tiktok_onboarding
- **Key patterns:**
  - **No-signup browsing:** Core feed accessible without account, no personal info required
  - **Immediate value:** Users see entertaining videos as soon as they open app
  - **Minimal friction:** No annoying screens asking preferences or setup
  - **No traditional onboarding:** No profile picture, interest selection, or forced follows
  - **Algorithm-first approach:** AI automatically sources content users will love without explicit preferences
  - **Variable rewards:** Slot machine psychology - users don't know what's next, keep swiping
  - **Auto-play + short clips:** Instant engagement, low commitment per video
- **Comparison:** Instagram requires minimum 8 clicks before viewing first post (username, profile picture, birthday, follow suggestions)
- **Relevance:** Pattern 1 (Onboarding), Pattern 2 (Content Discovery) - Gold standard for time-to-value and gradual commitment

**[Example:2]** Samuel Hulick - User Onboarding Philosophy
- **Source:** UserOnboard.com, various interviews and analyses
  - Heavybit: "Elements of User Onboarding's Samuel Hulick" - https://www.heavybit.com/library/article/samuel-hulick-elements-of-user-onboarding
  - Intercom: "Samuel Hulick on building better onboarding" - https://www.intercom.com/blog/podcasts/podcast-samuel-hulick-onboarding/
  - Appcues: "Onboarding new users—an interview with Samuel Hulick" - https://www.appcues.com/blog/onboarding-new-users-an-interview-with-samuel-hulick
- **Key philosophy:**
  - "The single biggest mistake is not focusing on delivering value to users"
  - "What's the shortest path to get a user to think this product will make them more awesome at a specific task?"
  - Success = when users come back and actively engage, not when they complete setup
  - Focus on "meaningful wins" as early as possible
  - Give users "a taste of why the product improves their lives"
- **Best known for:** UX teardowns on UserOnboard.com analyzing onboarding flows of popular apps
- **Relevance:** Pattern 1 (Onboarding) - Framework for evaluating Nostr onboarding against time-to-value principles

**[Example:3]** Instagram Onboarding Flow Comparison
- **Source:** Various product analyses (referenced in TikTok comparisons)
- **Key pattern:** Multi-step required setup before value
  - Username creation (required)
  - Profile picture upload (encouraged)
  - Birthday entry (required)
  - Follow suggested accounts (encouraged)
  - Minimum 8 clicks before viewing first content
- **Relevance:** Pattern 1 (Onboarding) - Example of higher friction approach that still works due to network effects (friends are already there)

### Feed Design & Discovery

**[Example:4]** TikTok's For You Algorithm - Solving Cold Start Without Followers
- **Sources:** Multiple 2024-2025 analyses including:
  - Sprout Social: "How the TikTok Algorithm Works in 2025" - https://sproutsocial.com/insights/tiktok-algorithm/
  - Buffer: "TikTok Algorithm Guide 2026" - https://buffer.com/resources/tiktok-algorithm/
  - Jackson Mohsenin: "The algorithm isn't everything: TikTok's virtuous cycle" - https://jmohsenin.com/tiktok-strategy
- **Date:** 2024-2025
- **Key patterns:**
  - For You Page algorithm prioritizes content relevance over creator popularity
  - Users with zero followers can reach large audiences if content aligns with viewer interests
  - Algorithm analyzes user interactions (watch time, likes, comments), video information (captions, hashtags, sounds), and device settings
  - Accounts with fewer followers receive more than 75% of impressions from "For You" feed, confirming balanced content distribution
  - Short-form video provides rich signal - users can watch many quickly, algorithm learns preferences rapidly
  - 55% of TikTok users create content, ensuring sufficient content supply even for new users
  - 2024 updates: Analyzes emotional tone, gives exposure to positive/supportive/"feel-good" content
  - Community alignment: Rewards content that aligns with specific communities (#BookTok, #SportsOnTikTok)
  - STEM feed introduced late 2024, contributing to 45% increase in #Science hashtag posts
- **Relevance:** Pattern 2 (Content Discovery) - Demonstrates that algorithmic content discovery solves "need followers to get reach" chicken-and-egg problem. Nostr clients could implement similar "For You" feeds surfacing quality content from unknown npubs

**[Example:5]** Instagram Algorithm Updates (2024-2025) & Multiple Specialized Algorithms
- **Sources:**
  - Later: "How the Instagram Algorithm Works in 2025" - https://later.com/blog/how-instagram-algorithm-works/
  - Sprout Social: "How the Instagram Algorithm Works [Updated 2025]" - https://sproutsocial.com/insights/instagram-algorithm/
  - Shopify: "Instagram Algorithm: How It Works and Tips for 2025" - https://www.shopify.com/blog/instagram-algorithm
  - Buffer: "How the Instagram Algorithm Works: Your 2025 Guide" - https://buffer.com/library/instagram-feed-algorithm/
- **Date:** 2024-2025
- **Key patterns:**
  - **April 2024 update:** Rewards original content creation; heavily weights "shares per reach" (content sent via DMs) as deeper engagement than likes
  - **December 2024:** "Trial Reels" allows creators to test content with non-followers before sharing to audience
  - **Summer 2024:** Shift to views-focused analytics announced by Adam Mosseri
  - **Multiple specialized algorithms:** Feed algorithm prioritizes content from close connections; Reels algorithm focuses on entertainment value and gives newcomers viral potential regardless of follower count; Explore algorithm helps users discover new content using similar signals
  - Each algorithm optimizes for different user goals (staying connected vs discovering new content)
- **Relevance:** Pattern 2 (Content Discovery) - Nostr should prioritize original content and deep engagement signals like zaps over simple likes. Multiple specialized algorithms for different use cases improves user experience

**[Example:6]** Bluesky Starter Packs in Practice
- **Source:** Bluesky blog announcement, June 26, 2024
- **Key pattern:** "Personalized invites that allow you to bring friends directly into your slice of Bluesky!" - helps users joining the social network find interesting content right out of the gate. Existing users can add accounts and custom feeds to create a starter pack and share the link or QR code. Can recommend up to 150 people and up to 3 custom feeds.
- **Research backing:** Lancaster University study (January 2025) found 43% of follows during peak periods came from starter packs
- **Relevance:** Pattern 2 (Content Discovery) - Competitive threat showing what's possible. NIP-51 starter packs exist in Nostr but clients haven't widely implemented. Multiple sources cite Bluesky's better onboarding/discovery as why it grew bigger than Nostr

**[Example:7]** Mastodon Discovery Mechanisms (Federated Timeline Model)
- **Source:** [Decentralized social comparison - to be researched]
- **Key pattern:** Local/Federated timeline structure provides instant content discovery; Hashtag-based discovery
- **Relevance:** Pattern 2 (Content Discovery)

### Performance Optimization

**[Example:8]** Twitter/X Performance Optimization
- **Source:** [Engineering blog - to be found]
- **Key pattern:** [Summary]
- **Relevance:** Pattern 4 (Performance)

**[Example:9]** Facebook Mobile Performance Budgets
- **Source:** [Engineering blog]
- **Key pattern:** [Summary]
- **Relevance:** Pattern 4 (Performance)

### Progressive Disclosure

**[Example:10]** Slack Settings Hierarchy
- **Source:** [Product analysis]
- **Key pattern:** [Summary]
- **Relevance:** Pattern 5 (Progressive Complexity)

**[Example:11]** Apple iOS Progressive Feature Education
- **Source:** [iOS design patterns]
- **Key pattern:** [Summary]
- **Relevance:** Pattern 5 (Progressive Complexity)

---

## 4. Nostr Protocol Documentation

### NIPs (Nostr Implementation Possibilities)

**[Protocol:1]** NIP-01: Basic Protocol Flow
- **Source:** https://github.com/nostr-protocol/nips/blob/master/01.md
- **Relevance:** All patterns (foundational)

**[Protocol:2]** NIP-02: Contact List and Petnames
- **Source:** https://github.com/nostr-protocol/nips/blob/master/02.md
- **Relevance:** Pattern 6 (Cross-Client Consistency)

**[Protocol:3]** NIP-46: Nostr Connect (Signers)
- **Source:** https://github.com/nostr-protocol/nips/blob/master/46.md
- **Relevance:** Pattern 1 (Onboarding), Pattern 5 (Progressive Complexity)

**[Protocol:4]** NIP-65: Relay List Metadata (Outbox Model)
- **Source:** https://github.com/nostr-protocol/nips/blob/master/65.md
- **Relevance:** Pattern 5 (Progressive Complexity), Pattern 6 (Cross-Client Consistency)

**[Protocol:5]** NIP-57: Lightning Zaps
- **Source:** https://github.com/nostr-protocol/nips/blob/master/57.md
- **Relevance:** Pattern 2 (Content Discovery - quality signal)

**[Protocol:6]** Event Kinds Reference
- **Source:** [NIPs repository]
- **Key kinds:** Kind 0 (metadata), Kind 1 (notes), Kind 3 (contacts)
- **Relevance:** Multiple patterns

### Nostr Design Resources

**[Protocol:7]** Nostr Design - UX Guidelines
- **Source:** https://nostrdesign.org/
- **Relevance:** All patterns (community design resource)

**[Protocol:8]** Nostr Protocol Specification
- **Source:** [Official docs]
- **Relevance:** All patterns (foundational)

---

## 5. User Feedback & Quotes

### Onboarding Pain Points

**[User:1]** "15-20 minute setup process overwhelms new users"
- **Source:** [User feedback - to be specifically cited]
- **Context:** [Where this was observed]
- **Relevance:** Pattern 1 (Onboarding)

**[User:2]** "Key management is terrifying - losing nsec = losing identity forever"
- **Source:** [User feedback - to be cited]
- **Context:** [Where this was observed]
- **Relevance:** Pattern 1 (Onboarding)

**[User:3]** "Empty feed after signup - no idea what to do"
- **Source:** [User feedback - to be cited]
- **Context:** [Where this was observed]
- **Relevance:** Pattern 1 (Onboarding), Pattern 2 (Content Discovery)

### Reliability & Core Interactions

**[User:4]** "Posts disappear seconds after posting"
- **Source:** [User complaint - to be cited]
- **Context:** [Client and circumstances]
- **Relevance:** Pattern 3 (Core Interactions), Pattern 6 (Cross-Client Consistency)

**[User:5]** "Notifications are missing or delayed"
- **Source:** [User feedback]
- **Context:** [Where this was observed]
- **Relevance:** Pattern 3 (Core Interactions)

### Content Discovery Issues

**[User:6]** "Traditional apps win by having much better content selection"
- **Source:** [User observation - to be cited]
- **Context:** [Discussion context]
- **Relevance:** Pattern 2 (Content Discovery)

**[User:7]** "Need 5-6 different clients to work around bugs"
- **Source:** [User feedback - to be cited]
- **Context:** [Where this was observed]
- **Relevance:** All patterns (systemic UX failure)

### Cross-Client Consistency

**[User:8]** "Lost all followers when switching from Primal → Damus → Snort"
- **Source:** [User complaint - to be cited with GitHub issue or Nostr post]
- **Context:** [Specific circumstances]
- **Relevance:** Pattern 6 (Cross-Client Consistency)

**[User:9]** "Profile changes don't sync across apps"
- **Source:** [User feedback - to be cited]
- **Context:** [Where observed]
- **Relevance:** Pattern 6 (Cross-Client Consistency)

### Performance & Reliability

**[User:10]** "Apps hang/buffer constantly"
- **Source:** [User complaint - to be cited]
- **Context:** [Client and device]
- **Relevance:** Pattern 4 (Performance)

**[User:11]** "After 15-20 minutes of messing around, I was able to create a NOSTR account"
- **Source:** Stacker News discussion thread #222205
- **URL:** https://stacker.news/items/222205
- **Date:** 2024
- **Context:** User describing first-time Nostr experience; thread titled "NOSTR is not going to fix anything :("
- **Relevance:** Pattern 1 (Onboarding) - Demonstrates excessive onboarding time

**[User:12]** "If you lose the private key the account is lost forever"
- **Source:** Iris (Nostr client) FAQ documentation
- **URL:** https://github.com/irislib/faq
- **Context:** Official warning presented to users about key management
- **Relevance:** Pattern 1 (Onboarding) - Illustrates the terror of permanent account loss

**[User:17]** Key management remains a blocker for adoption
- **Source:** "Managing Nostr Keys and Signing Devices" (Substack)
- **URL:** https://onnostr.substack.com/p/managing-nostr-keys-and-signing-devices
- **Date:** March 2025
- **Quote:** "A protocol based entirely on public/private key pairs being used as identities cannot gain traction and adoption if people are burning their accounts by accident or handing it over to scammers"
- **Key findings:**
  - Hardware signers: "Non-technical users aren't going to onboard by buying or building a device"
  - Extension signers create friction when moving between desktop and mobile
  - "Nostr has a very tight complexity budget when onboarding new users"
- **Relevance:** Pattern 1 (Onboarding) - March 2025 analysis confirms key management is STILL a blocker

**[User:18]** Nostr Design onboarding guidance
- **Source:** Nostr Design reference documentation
- **URL:** https://nostrdesign.org/docs/reference-designs/onboarding/
- **Date:** 2024 (actively maintained)
- **Quote:** Relay selection is "high friction" that should be minimized during onboarding
- **Guidance provided:**
  - Defer key management for a time convenient to user rather than overwhelming upfront
  - Customize feeds based on users' preferred interests instead of throwing into Global
  - Segment recommendations based on chosen interests
- **Relevance:** Pattern 1 (Onboarding), Pattern 5 (Progressive Complexity) - Ecosystem recognition of widespread onboarding problems

**[User:19]** Damus onboarding improvements tracker (ACTIVE)
- **Source:** GitHub Issue #2642, Damus repository
- **URL:** https://github.com/damus-io/damus/issues/2642
- **Date:** Opened November 6, 2024; Last updated February 4, 2025
- **Status:** Open, actively maintained
- **Problems identified:**
  - Profile pre-caching needed to reduce loading states
  - Cold start optimization still pending
  - Development mode cold start listed as technical priority
- **Relevance:** Pattern 1 (Onboarding) - Active work in Feb 2025 proves problems persist

**[User:20]** Damus considering removing account creation step
- **Source:** GitHub Issue #3207, Damus repository
- **URL:** https://github.com/damus-io/damus/issues/3207
- **Date:** Opened August 22, 2025
- **Status:** Open
- **Quote:** "Remove the 'create account' step during new app installation's onboarding sequence, based on the hypothesis that lower friction improves first-time user experience"
- **Relevance:** Pattern 1 (Onboarding) - Aug 2025 shows account creation friction remains critical enough to consider eliminating entirely

**[User:21]** Nstart standalone onboarding tool
- **Source:** Hacker News Show HN post / https://start.njump.me
- **URL:** https://news.ycombinator.com/item?id=43001303
- **Date:** February 2025
- **Description:** A standalone Nostr onboarding tool where users can be "automagically logged into the app, without needing to touch their keys/bunker"
- **Relevance:** Pattern 1 (Onboarding) - Creation of separate onboarding service in Feb 2025 proves client-level onboarding is too complex

**[User:15]** "Traditional apps win by having much better content selection"
- **Source:** "The State of Nostr Clients" analysis by karnage
- **URL:** https://karnage.npub.pro/post/1711761836895/
- **Date:** March 29, 2024
- **Full quote:** "Traditional apps win simply by having much better content selection - you get to see a variety of interesting things that Nostr simply can't match"
- **Additional data:** DAU stuck at 10-12k trusted pubkeys, users need 5-6 different clients
- **Relevance:** Pattern 2 (Content Discovery) - Direct comparison showing Nostr's content discovery deficit

**[User:22]** "Nostr is lacking in content, which could be the primary reason people are not sticking around"
- **Source:** Multiple user discussions, 2024
- **Context:** Analysis of retention crisis
- **Relevance:** Pattern 2 (Content Discovery) - Content scarcity as primary retention killer

**[User:23]** "Nostr suffers from the chicken/egg problem where new users are needed to generate more content, and more content is needed to retain new users"
- **Source:** UX retention problem discussions
- **Date:** 2024
- **Context:** Cold start problem where empty feeds drive users away before they contribute content
- **Relevance:** Pattern 2 (Content Discovery) - The fundamental chicken-egg problem

**[User:24]** "Nostr does not seem to have any external growth loops, such as the ability to invite people by email with a single click"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** March 2024
- **Context:** No mechanisms to help users discover or invite others
- **Relevance:** Pattern 2 (Content Discovery) - No growth loops for network effects

**[User:25]** "Users are not notified when tagged, and people have to have a habit of opening the app to know if something is happening"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** March 2024
- **Context:** Discovery problem - users miss interactions
- **Relevance:** Pattern 2 (Content Discovery), Pattern 3 (Core Interactions) - Notification failures affect discovery

**[User:26]** "Habit formation of using a new app is important in the early usage phase and Nostr seems to have a weak spot here"
- **Source:** "The State of Nostr Clients" by karnage
- **Date:** March 2024
- **Context:** No triggers to bring users back, related to discovery
- **Relevance:** Pattern 2 (Content Discovery) - Weak habit formation due to poor discovery

**[User:27]** "The main problem of decentralized alternatives like Nostr is content discovery"
- **Source:** General Nostr UX discussions
- **Date:** 2024
- **Context:** Recognized as a core architectural challenge
- **Relevance:** Pattern 2 (Content Discovery) - Protocol-level discovery challenge acknowledged

**[User:28]** "It's only possible to search on what you have seen, so search engines will always have to crawl some parts of the network they chose to and index those to enable public search"
- **Source:** Hashtag discovery discussions
- **Date:** 2024
- **Context:** Search is limited by relay coverage
- **Relevance:** Pattern 2 (Content Discovery) - Search limitations in decentralized architecture

**[User:29]** Nostr spam crisis - "500,000 daily spam messages in mid-February"
- **Source:** Spam filter discussions, web research
- **Date:** February 2024
- **Full quote:** "Nostr was hit with approximately 500,000 daily spam messages in mid-February, consisting of ads for spam services, scams, and NSFW content"
- **Context:** Global feed usability severely impacted by spam
- **Relevance:** Pattern 2 (Content Discovery) - Feed quality crisis requiring spam filtering

**[User:30]** "There can't be a 'global' view of the network, as it would be full of spam, so indexers have to choose what to display"
- **Source:** Global feed discussions
- **Date:** 2024
- **Context:** Architecture limitation affects discovery
- **Relevance:** Pattern 2 (Content Discovery) - No true global discovery feed possible

**[User:31]** Primal 2.0 addressing discovery problems
- **Source:** NoBS Bitcoin announcement / Primal 2.0 launch
- **URL:** [To be added]
- **Date:** November 21, 2024
- **Quote:** "Primal 2.0 was announced by miljan, founder and CEO of Primal, after the team worked for many months to reach this milestone. Primal now offers a much more comprehensive view of Nostr on its web and mobile apps, with the following additions: a Reads tab, an Explore tab, a Feed Marketplace, comprehensive Advanced Search options, and multiple performance improvements."
- **Context:** Major discovery innovation launched late 2024
- **Relevance:** Pattern 2 (Content Discovery) - Ecosystem response to discovery crisis

**[User:32]** Nstart onboarding wizard with auto-follow
- **Source:** Nstart announcement (https://www.nobsbitcoin.com/nstart-nostr-onboarding-wizard/)
- **Date:** January 2025
- **Quote:** "Nstart aims to simplify onboarding for new users to the Nostr protocol with an easy-to-use wizard that provides helpful hints about the protocol and exclusive features... Auto follow the contacts list of some old and trusted Nostr users"
- **Context:** Solves cold start by auto-following curated lists
- **Relevance:** Pattern 2 (Content Discovery) - Solution to empty feed problem launched January 2025

**[User:33]** Derek Ross on user-controlled discovery
- **Source:** Derek Ross Nostr post
- **Date:** January 2025
- **Quote:** "Content discovery on Nostr keeps improving, but I believe we still need to act as our own algorithms most of the time—and I actually prefer it that way"
- **Context:** Philosophy on discovery vs algorithms
- **Relevance:** Pattern 2 (Content Discovery) - Developer perspective on algorithmic vs manual discovery

**[User:16]** "Nostr is weird and hard to use"
- **Source:** Jack Dorsey interview with Mike Solana, Founders Fund
- **Date:** May 2024
- **Coverage:** Washington Post, TechTimes, Engadget
- **Full context:** Dorsey emphasized "those who truly believe in censorship resistance and free speech need to use technologies that enable those values" but admitted UX is "rough around the edges"
- **Relevance:** Pattern 1 (Onboarding), All patterns - Validation from Nostr's most prominent backer

---

## 6. Industry Design Systems

**[Design:1]** Apple Human Interface Guidelines
- **Source:** https://developer.apple.com/design/human-interface-guidelines/
- **Relevance:** All patterns (iOS design standards)

**[Design:2]** Google Material Design
- **Source:** https://material.io/design
- **Relevance:** All patterns (Android design standards)

**[Design:3]** Microsoft Fluent Design System
- **Source:** https://www.microsoft.com/design/fluent/
- **Relevance:** Pattern 5 (Progressive Complexity)

---

## 7. Developer Resources

### Client Repositories (for implementation analysis)

**[Code:1]** Damus (iOS)
- **Source:** https://github.com/damus-io/damus
- **Relevance:** Implementation examples (iOS patterns)

**[Code:2]** Amethyst (Android)
- **Source:** https://github.com/vitorpamplona/amethyst
- **Relevance:** Implementation examples (Android patterns)

**[Code:3]** Primal (Web/Mobile)
- **Source:** [Repository link]
- **Relevance:** Implementation examples

**[Code:4]** Snort (Web)
- **Source:** https://github.com/v0l/snort
- **Relevance:** Implementation examples (web patterns)

---

## Research Gaps (To Be Filled)

### High Priority
- [ ] Academic HCI papers on social media onboarding
- [ ] Quantitative retention data for mainstream apps (benchmarks)
- [ ] TikTok algorithm research (published analyses)
- [ ] Formal user studies of Nostr clients
- [ ] Performance benchmarks for social apps

### Medium Priority
- [ ] Case studies: successful social app launches
- [ ] Research on trust in decentralized systems
- [ ] Feed algorithm comparison studies
- [ ] Progressive disclosure best practices

### Low Priority (Nice to Have)
- [ ] Developer interviews with Nostr client builders
- [ ] Formal usability testing reports
- [ ] Accessibility research for social apps

---

## How to Cite This Work

**APA Style:**
Yeager, S. (2025). *Nostr UX Research Study: Design Patterns for Consumer Applications*. GitHub. https://github.com/shawnyeager/nostr-ux-research

**MLA Style:**
Yeager, Shawn. "Nostr UX Research Study: Design Patterns for Consumer Applications." *GitHub*, 2025, https://github.com/shawnyeager/nostr-ux-research.

---

*Last updated: November 2025*

**Note:** This is a living document. Citations are added as patterns are developed. Placeholders marked with [To be researched] will be filled during the writing process.
