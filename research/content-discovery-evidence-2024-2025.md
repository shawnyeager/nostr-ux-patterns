# Content Discovery Evidence: 2024-2025

Research findings on content discovery problems in Nostr apps, compiled November 2024.

**Sources:** Verified web sources with URLs only. All findings without verifiable URLs have been removed.

---

## 1. RETENTION & COLD START CRISIS

### Finding 1.1: Retention Crisis
- **Quote:** "According to nostr.band, retention of trusted users 30 days after signups trends to 0 for recent cohorts. Daily active users averaging in the 10,000-12,000 range for 'trusted' pub keys. As of October 2024, there are only ~36,000 weekly active users on Nostr right now, and less than 15,000 daily active users."
- **Source:** https://stats.nostr.band/
- **Date:** October 2024
- **Context:** Nostr.band tracks retention metrics and DAU/WAU. Despite growth in total signups, active user numbers remain flat. Post-viral-event retention failure after Brazil Twitter ban and other spikes.
- **Category:** Retention / Empty feed

### Finding 1.2: Content Scarcity & Chicken-Egg Problem
- **Quote:** "Nostr is lacking in content, which could be the primary reason people are not sticking around after trying it. Nostr suffers from the chicken/egg problem where new users are needed to generate more content, and more content is needed to retain new users. Traditional apps win simply by having much better content selection - you get to see a variety of interesting things that Nostr simply can't match."
- **Source:** https://karnage.npub.pro/post/1711761836895/ ("The State of Nostr Clients" by karnage)
- **Date:** March 30, 2024
- **Context:** Cold start problem where empty feeds drive users away before they contribute content. Direct comparison showing Nostr's content discovery deficit compared to mainstream platforms.
- **Category:** Empty feed / Feed quality / Cold start

---

## 2. DISCOVERY MECHANISMS

### Finding 2.1: No External Growth Loops
- **Quote:** "Nostr does not seem to have any external growth loops, such as the ability to invite people by email with a single click"
- **Source:** https://karnage.npub.pro/post/1711761836895/ ("The State of Nostr Clients" by karnage)
- **Date:** March 30, 2024
- **Context:** No mechanisms to help users discover or invite others
- **Category:** Discovery

### Finding 2.2: No Tag Notifications
- **Quote:** "Users are not notified when tagged, and people have to have a habit of opening the app to know if something is happening"
- **Source:** https://karnage.npub.pro/post/1711761836895/ ("The State of Nostr Clients" by karnage)
- **Date:** March 30, 2024
- **Context:** Discovery problem - users miss interactions
- **Category:** Discovery / Core interactions

### Finding 2.3: Weak Habit Formation
- **Quote:** "Habit formation of using a new app is important in the early usage phase and Nostr seems to have a weak spot here"
- **Source:** https://karnage.npub.pro/post/1711761836895/ ("The State of Nostr Clients" by karnage)
- **Date:** March 30, 2024
- **Context:** No triggers to bring users back, related to discovery
- **Category:** Discovery / Retention

---

## 3. ONBOARDING & FIRST-RUN EXPERIENCE

### Finding 3.1: Unknown Recommendations Add Confusion
- **Quote:** "Unknown people recommendations could add to confusion during onboarding – it's better to present well known accounts or publications (e.g. news feeds)"
- **Source:** https://nostrdesign.org/docs/how-to/onboarding/ (Nostr Design onboarding guidelines)
- **Date:** 2024
- **Context:** Design recommendation for solving cold start
- **Category:** Discovery / Onboarding

### Finding 3.2: Progressive Disclosure & Content Discovery Priority
- **Quote:** "The primary recommendation is to use the progressive disclosure design principle, which emphasizes step-by-step discovery of essential information instead of showing everything at once. The goal is to minimize information disclosed to users to avoid overwhelming them. Key areas to review include onboarding, navigation, content and user discovery, search, profile, settings, and other UI"
- **Source:** https://nostrdesign.org/ (Nostr Design guidelines)
- **Date:** 2024
- **Context:** Recommended approach for onboarding to improve discovery. Design community prioritizes content and user discovery as a key area.
- **Category:** Discovery / Onboarding

---

## 4. SOLUTIONS & INNOVATIONS (2024-2025)

### Finding 4.1: Nstart Onboarding Wizard
- **Quote:** "Nstart aims to simplify onboarding for new users to the Nostr protocol with an easy-to-use wizard that provides helpful hints about the protocol and exclusive features... Auto follow the contacts list of some old and trusted Nostr users"
- **Source:** https://www.nobsbitcoin.com/nstart-nostr-onboarding-wizard/
- **Date:** January 2025
- **Context:** Solves cold start by auto-following curated lists
- **Category:** Discovery / Solution / Onboarding

---

## SUMMARY OF KEY THEMES

### Empty Feed / Cold Start Problems:
1. **Retention crisis:** 30-day retention trends to 0% for new cohorts (nostr.band, Oct 2024)
2. **DAU stagnation:** Stuck at 10-12K daily active users despite viral spikes (nostr.band, Oct 2024)
3. **Content scarcity:** Primary reason people don't stick around (karnage, March 2024)
4. **Chicken-egg problem:** Need users for content, need content for users (karnage, March 2024)

### Discovery Mechanism Problems:
1. **No external growth loops:** No email invites or viral mechanisms (karnage, March 2024)
2. **No tag notifications:** Users miss when they're mentioned (karnage, March 2024)
3. **Weak habit formation:** No triggers to bring users back to app (karnage, March 2024)

### Solutions Emerging (2024-2025):
1. **Nstart onboarding wizard** (Jan 2025): Auto-follow trusted users, email backup, simplified key management
2. **Nostr Design guidelines**: Prioritizes progressive disclosure and content/user discovery in onboarding recommendations

### Design Community Acknowledgment:
1. **Nostr Design:** Prioritizes "content and user discovery" as key areas for improvement
2. **karnage:** "The State of Nostr Clients" report documenting UX gaps and retention failures
3. **Progressive disclosure:** Recommended principle to avoid overwhelming users during onboarding

---

## KEY QUOTES FOR PATTERN 2 (CONTENT DISCOVERY)

**On the retention crisis:**
> "According to nostr.band, retention of trusted users 30 days after signups trends to 0 for recent cohorts"

**On content quality:**
> "Traditional apps win simply by having much better content selection - you get to see a variety of interesting things that Nostr simply can't match"

**On the cold start problem:**
> "Nostr is lacking in content, which could be the primary reason people are not sticking around after trying it"

**On the chicken-egg problem:**
> "Nostr suffers from the chicken/egg problem where new users are needed to generate more content, and more content is needed to retain new users"

**On no growth loops:**
> "Nostr does not seem to have any external growth loops, such as the ability to invite people by email with a single click"

**On onboarding recommendations:**
> "Unknown people recommendations could add to confusion during onboarding – it's better to present well known accounts or publications"

---

**Research completed:** November 7, 2025
**Cleaned:** November 8, 2025
**Methodology:** Removed all findings without verifiable URLs. Consolidated findings from the same source where appropriate.
**Total findings with verified sources:** 8 findings from 4 distinct sources
