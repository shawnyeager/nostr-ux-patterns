# Pattern 5: Progressive Complexity

**Status:** ✅ Complete
**Last Updated:** November 8, 2025
**Research Currency:** All sources from 2024-2025

---

## Table of Contents

1. [Problem Statement](#problem-statement)
2. [Universal Principles (70%)](#universal-principles-70)
3. [Nostr-Specific Considerations (30%)](#nostr-specific-considerations-30)
4. [Pattern Library: Concrete Solutions](#pattern-library-concrete-solutions)
5. [Anti-Patterns: What Not To Do](#anti-patterns-what-not-to-do)
6. [Validation Checklist](#validation-checklist)
7. [Citations & Sources](#citations--sources)

---

## Problem Statement

### Current State

**Overwhelming complexity killing adoption:**
- [[User:12]](#user-12) New users exposed to relay selection, key management, and NIP configurations immediately during onboarding
- [[Data:28]](#data-28) Nostr clients showing 50+ relay pickers, signer app setup (NIP-46), and read/write relay splits before users understand basic posting
- [[Data:29]](#data-29) Settings pages with technical jargon: "Outbox model (NIP-65)", "Relay list metadata", "Event signature verification"
- [[User:13]](#user-13) Users report feeling "overwhelmed" and "confused" by protocol complexity exposed in UI
- [[Data:30]](#data-30) Power user features (relay health indicators, custom feeds, mute lists) presented as essential setup steps

**The perception problem:**
Nostr apps feel like developer tools, not consumer apps. Users compare to Twitter/Instagram's "it just works" simplicity and abandon when faced with:
- Relay management decisions on first launch
- Key signer configuration requirements
- Technical error messages referencing NIPs
- No sensible defaults—everything requires user configuration

**The retention impact:**
- Users abandon during onboarding when faced with unfamiliar technical concepts
- "Too complicated" cited as top reason for not adopting Nostr
- Power users love the control, but they represent <5% of potential audience
- Missing the mainstream market by optimizing for protocol purists

### Root Causes

1. **Protocol complexity exposed directly to users**: Relays, NIPs, and cryptographic concepts in user-facing UI
2. **No smart defaults**: Apps require configuration instead of working great out-of-box
3. **Power user features treated as essential**: Relay selection, signer apps shown to all users upfront
4. **Developer-first design**: Built for people who understand Nostr protocol, not mainstream users
5. **Feature bloat without hierarchy**: All features given equal prominence regardless of usage frequency
6. **Poor feature discovery**: Advanced features either hidden completely or overwhelming beginners

### Why This Matters

> "80% of users will only use 20% of features. Design for that 80% first." [[Research:54]](#research-54)

**Research shows:** [[Research:55]](#research-55) [[Research:56]](#research-56) [[Research:57]](#research-57)
- **30-40% reduction in cognitive load** through progressive disclosure during onboarding [[Research:55]](#research-55)
- **25% fewer interactions** needed when interfaces apply smart defaults (Airbnb case study) [[Research:57]](#research-57)
- **24% reduction in cognitive load** from minimal layouts with decluttered designs (Figma research) [[Research:57]](#research-57)
- Progressive disclosure reduces decision fatigue by revealing information in stages [[Research:56]](#research-56)
- Users abandon apps with >10-15 settings on a single screen [[Research:58]](#research-58)

**The Pareto Principle in UX:** [[Research:54]](#research-54)
- Focus on the 20% of features that deliver 80% of user value
- Most users never explore advanced settings
- Complexity should be optional, not mandatory

---

## Universal Principles (70%)

These principles apply to any application managing feature complexity and user experience.

### 1. The Pareto Principle (80/20 Rule)

**Research backing:** [[Research:54]](#research-54) [[Research:59]](#research-59)

**Core insight:** 80% of users will use only 20% of features. Design should optimize for the majority, not the power user minority.

**Application to interface design:**
- **Feature prioritization:** Identify which 20% of features meet 80% of users' needs [[Research:59]](#research-59)
- **Design focus:** 20% of design decisions drive 80% of impact—focus there [[Research:59]](#research-59)
- **MVP development:** Minimum viable products are Pareto Principle in action [[Research:59]](#research-59)

**Key strategies:**
- Default to the 20% of features that deliver 80% of value
- Make power features discoverable, not prominent
- Measure feature usage—if <20% use it, it shouldn't be in primary UI
- Reduce cognitive load by simplifying design elements [[Research:59]](#research-59)

**Examples from mainstream apps:**
- **Email clients:** Compose/Read/Archive visible; filters/labels/rules in settings
- **Social apps:** Post/Like/Comment primary; mute lists/quality filters advanced
- **Photo apps:** Basic filters prominent; curves/levels/masking for pros

### 2. Progressive Disclosure

**Research backing:** [[Research:55]](#research-55) [[Research:56]](#research-56) [[Research:60]](#research-60)

**Core insight:** Defer advanced features and information to secondary UI components. Keep essential content in primary UI, reveal advanced content upon request. [[Research:60]](#research-60)

**Why it works:**
- **30-40% reduction in cognitive load** during onboarding [[Research:55]](#research-55)
- Reduces decision fatigue by revealing information in stages [[Research:56]](#research-56)
- Breaks complex processes into manageable steps [[Research:55]](#research-55)
- Eliminates friction points that cause abandonment [[Research:55]](#research-55)

**Common implementations:** [[Research:56]](#research-56) [[Research:60]](#research-60)
- **Collapsible menus:** Hide advanced options until clicked
- **Tooltips/contextual help:** Information appears on hover or interaction
- **Hover-based actions:** Secondary actions revealed on hover
- **Toggles:** Reveal or hide advanced settings, letting users control interface complexity [[Research:60]](#research-60)
- **Step-by-step flows:** Multi-page wizards instead of one overwhelming screen

**When to use:** [[Research:60]](#research-60)
- Designing for novice users
- Complex tasks with many options
- Limited screen space (mobile)
- High cognitive load scenarios

**Design methods:** [[Research:60]](#research-60)
Define essential vs. advanced content through user research using card sorting and task analysis.

### 3. Smart Defaults That Work for 80%

**Research backing:** [[Research:57]](#research-57) [[Research:61]](#research-61)

**Core insight:** Great UX isn't about hiding features—it's about organizing them so users can find, understand, and use them without frustration. [[Research:61]](#research-61)

**The default experience should:**
- Work excellently without any configuration
- Serve 80% of users' needs immediately
- Allow customization for the 20% who need it
- Never force decisions users aren't ready to make

**Airbnb case study:** [[Research:57]](#research-57)
- Smart defaults led to **25% fewer interactions** needed to complete bookings
- Higher conversion rate with less cognitive effort
- Users could still customize, but most didn't need to

**Best practices:**
- Research what most users actually need (not what power users want)
- Test defaults with non-technical users
- Make changing defaults easy, but unnecessary for most
- Provide "Reset to default" option for users who customize

**Examples:**
- **Notification settings:** Defaults that balance engagement without spam
- **Privacy settings:** Sensible privacy by default, opt-in for sharing
- **Display settings:** Auto dark mode, readable font sizes, standard layouts

### 4. Settings Hierarchy: Basic → Advanced → Expert

**Research backing:** [[Research:58]](#research-58) [[Research:61]](#research-61)

**Core insight:** Limit settings on one screen to 10-15 items—more becomes overwhelming. [[Research:58]](#research-58) Create intuitive menus by moving additional settings to separate screens. [[Research:58]](#research-58)

**Three-tier hierarchy:**

**Tier 1: Basic (Visible to all)**
- Frequently used settings (top of screen) [[Research:58]](#research-58)
- Core functionality toggles
- Account/profile settings
- <10 items maximum

**Tier 2: Advanced (Behind "Advanced Settings" section)**
- Features used by 20-40% of users
- Customization options
- Performance tweaks
- Grouped logically by category

**Tier 3: Expert (Hidden in debug/developer/power user mode)**
- Experimental features
- Technical configurations
- Developer tools
- Risk: Can break things if misused

**Android design guidelines:** [[Research:58]](#research-58)
- Place frequently used settings at top
- Users should glance at settings and understand all individual settings and their values
- Limit items per screen to avoid overwhelming users

**Visual hierarchy principles:** [[Research:61]](#research-61)
- Prioritize important information
- Ensure content aligns with user needs and goals
- Use shared traits (color, shape, size) for quick understanding
- Apply visual consistency

### 5. Contextual Help Over Upfront Tutorials

**Research backing:** [[Research:62]](#research-62) [[Research:63]](#research-63)

**Core insight:** Show help content alongside each step to minimize cognitive load, rather than overwhelming users upfront. [[Research:62]](#research-62)

**Pull revelations vs. Push tutorials:** [[Research:62]](#research-62)
- **Pull revelations:** Help triggered when user would benefit from that information at that moment
- **Push tutorials:** Upfront product tours that users skip or forget

**Nielsen Norman Group (February 2024):** [[Research:62]](#research-62)
Progressive and contextual delivery introduces actions, steps, and features gradually as they become relevant to avoid cognitive overload.

**Best practices:** [[Research:63]](#research-63)
- **Tooltips:** Concise, context-sensitive pop-ups that give information without interrupting flow
- **Contextual hints:** Explain features only when first used
- **Progressive guidance:** Interactive tutorials, tooltips, step-by-step guides
- **AI-enhanced personalization:** Tailor onboarding to each user's goals and behavior [[Research:62]](#research-62)

**Implementation tools:** [[Research:62]](#research-62)
Pendo, Appcues, and Userpilot enable contextual help implementation without coding.

**Design principle:** [[Research:63]](#research-63)
Tooltips provide subtle, contextual guidance; pop-ups or modals are more disruptive—choose appropriately.

### 6. Feature Discovery for Power Users

**Research backing:** [[Research:61]](#research-61) [[Research:64]](#research-64)

**The challenge:** Power users need to find advanced features without overwhelming beginners.

**Discovery patterns:**

**Pattern A: Keyboard shortcuts**
- Display hints in tooltips (e.g., "⌘K to search")
- Provide shortcuts panel (? key)
- Allow customization for power users

**Pattern B: Search within settings**
- Filter settings by keyword
- Jump to specific configurations
- Avoids endless scrolling

**Pattern C: "Advanced" toggle or mode**
- Switch between simplified and full interfaces
- Remember user preference
- Clearly labeled entry point

**Pattern D: Contextual upsells**
- "Looking for more options? Try Advanced Mode"
- Shown after user demonstrates proficiency
- Not intrusive to beginners

**2024-2025 trends:** [[Research:64]](#research-64)
- **"Choose your own UX adventure" settings** for power users
- **Smart defaults** with behavior-based interfaces
- **Dashboards that feel personalized**
- **Adaptive interfaces:** Dark mode at night, simplified UI when fatigued

### 7. Minimize Cognitive Load

**Research backing:** [[Research:57]](#research-57) [[Research:65]](#research-65)

**Core insight:** Reduce cognitive load by simplifying visual information, creating clear interaction design, and applying psychological principles. [[Research:65]](#research-65)

**Proven techniques:** [[Research:65]](#research-65)

**Progressive disclosure:**
Accordions, tooltips, or step-by-step flows reveal content only when needed, keeping interface clean.

**Simplification strategies:**
- Consistent patterns across interface
- Clear layouts with minimal distractions
- Group related items logically
- Improve navigation with clear menus and visual hierarchies

**Mobile-specific:**
Bottom navigation bars and gesture-based controls streamline user journeys. [[Research:65]](#research-65)

**Measurable impact:** [[Research:57]](#research-57)
- **Airbnb:** Higher conversion, 25% fewer interactions with smart defaults
- **Figma:** 24% reduction in cognitive load with minimal layouts
- **Adobe (2024):** 30% increase in engagement with decluttered designs

**Key principle:** [[Research:61]](#research-61)
Great UX isn't about hiding features—it's about organizing them so users can find, understand, and use without frustration.

---

## Nostr-Specific Considerations (30%)

### Challenge 1: Relay Management Complexity

**The problem:** Nostr's multi-relay architecture is powerful but overwhelming for new users.

**Current failures:**
- [[Data:28]](#data-28) Apps showing 50+ relay pickers during onboarding
- [[Data:31]](#data-31) Users setting relay preferences in one client (Nostrudel) find other clients (Coracle, Nostter) pulling relay lists incorrectly
- [[Data:31]](#data-31) Manual relay additions multiply unexpectedly, causing confusion
- Read/write relay splits exposed to beginners who don't understand the concept
- No explanation of what relays are or why they matter

**NIP-65 (Relay List Metadata) challenges:** [[Data:32]](#data-32)
- Uses kind:10002 events to advertise user's write relays (OUTBOX) and read relays (INBOX)
- Clients should guide users to keep lists small (2-4 relays) [[Data:32]](#data-32)
- Users switching clients experience relay list confusion due to incomplete NIP implementations [[Data:31]](#data-31)

**What 80% of users need:**
- App works perfectly with zero relay configuration
- Smart default relays chosen based on:
  - Geographic location (latency)
  - Reliability metrics
  - Community recommendations
- No relay UI during onboarding

**What 20% of power users need:**
- Relay health indicators (uptime, latency, event coverage)
- Custom relay management
- Read/write relay separation
- Relay analytics and debugging tools

**Progressive disclosure approach:**

**Level 1: Invisible (Default)**
```
No relay UI at all. App chooses optimal relays automatically:
- 2-3 well-connected, reliable relays
- Geographic proximity for low latency
- Automatic failover if relay goes down
```

**Level 2: Basic (Settings → Advanced)**
```
"Network Settings" (not "Relay Management")
- [✓] Automatic relay selection (recommended)
- [ ] Custom relay configuration

Tooltip: "Nostr uses multiple servers (relays) to store your posts.
Automatic mode works great for most people."
```

**Level 3: Power User (Settings → Advanced → Relay Management)**
```
Full relay management interface:
- Add/remove relays manually
- Read/write relay separation
- Relay health monitoring
- NIP-65 outbox model controls
- Import/export relay lists
```

**Implementation example:**
```typescript
// Smart default relays based on user location
function getDefaultRelays(userLocation: string): string[] {
  const globalRelays = [
    'wss://relay.damus.io',
    'wss://nos.lol',
    'wss://relay.nostr.band'
  ]

  const regionalRelays = {
    'NA': ['wss://nostr.mom', 'wss://relay.current.fyi'],
    'EU': ['wss://nostr.wine', 'wss://relay.orangepill.dev'],
    'APAC': ['wss://relay.nostr.wirednet.jp']
  }

  // Combine 2 global + 1-2 regional for optimal coverage
  return [...globalRelays.slice(0, 2), ...regionalRelays[userLocation].slice(0, 2)]
}

// Only show relay UI if user explicitly requests it
function shouldShowRelayUI(user: User): boolean {
  return user.settings.advancedMode === true || user.relayOverrides.length > 0
}
```

### Challenge 2: Key Signer Apps (NIP-46) Complexity

**The problem:** Remote signers enhance security but add significant complexity.

**Current state:** [[Data:33]](#data-33)
- NIP-46 specification unclear and constantly changing
- Incompatibilities between apps and signers
- No signer apps in traditional app stores (requires Obtanium or zap.store)
- Clients don't handle latency well (need better loading states, debouncing, optimistic updates)
- Push notification support incomplete

**Available signers:** [[Data:34]](#data-34)
- **Amber (Android):** Offline signing, multiple accounts, granular permissions
- **Nostr Signer (Alby):** Remote signing via push notifications

**User experience challenges:** [[Data:33]](#data-33)
While NIP-46 is best practice for key security, "it doesn't currently work very well at all" due to spec instability and poor UX.

**What 80% of users need:**
- Simple, secure key storage in-app
- Optional passphrase/biometric protection
- Clear backup instructions

**What 20% of power users need:**
- Remote signer integration (NIP-46)
- Hardware wallet support
- Multiple key/identity management
- Granular permission controls

**Progressive disclosure approach:**

**Level 1: Simple & Secure (Default)**
```
Onboarding:
"Your account is secured with a private key, safely stored on your device"
- Biometric unlock (Face ID/Touch ID)
- Optional passphrase
- Clear backup flow (12-word seed phrase or encrypted file)

NO mention of:
- nsec/npub distinction
- Remote signers
- NIP-46
- Cryptographic details
```

**Level 2: Backup Awareness (After 1 week or first post)**
```
Non-intrusive reminder:
"💡 Secure your account with a backup"
[Set up backup] [Later]

Backup flow:
"Save your recovery phrase. You'll need it if you switch devices."
[Show 12 words] → [Confirm] → [✓ Backed up]
```

**Level 3: Advanced Security (Settings → Security → Advanced)**
```
"Advanced Key Management"
- [ ] Use remote signer app (NIP-46)
  ℹ️ Store keys in a separate app for extra security
  [Connect Signer App]

- [ ] Export private key (nsec)
  ⚠️ Only do this if you know what you're doing
  [Show Private Key]
```

**When to introduce signer apps:**
- NEVER during onboarding
- Only in advanced security settings
- With clear explanation of benefits
- After user has successfully used app for 1+ week

### Challenge 3: Protocol Terminology in UI

**The problem:** Nostr-specific jargon (NIPs, relays, events, kinds) exposed in user-facing UI.

**Current failures:** [[Data:29]](#data-29)
- Error messages: "Failed to publish kind:1 event to relay"
- Settings: "Enable NIP-65 Outbox Model"
- Features: "Import NIP-05 identifier"
- Help text: "This is defined in NIP-46"

**Translation guide for user-facing UI:**

| Technical Term | User-Facing Label | Context |
|----------------|-------------------|---------|
| Relay | Server, Network | "Your posts are stored on multiple servers" |
| Event | Post, Message, Update | "Your post was published successfully" |
| Kind:1 | Post | Never mention kind numbers |
| Kind:3 | Following list | "Your following list" |
| NIP-05 | Username, Verified name | "Get a username like alice@example.com" |
| NIP-46 | Remote signer | "Use a separate app to manage your keys" |
| NIP-65 | Network preferences | "Choose your preferred servers" |
| nsec/npub | Private key/Public key | Only in advanced settings |
| Outbox model | (no direct equivalent) | Feature should be invisible |

**Pattern: Hide protocol, show benefit**

**Bad:**
```
⚠️ Failed to publish kind:1 event to wss://relay.example.com
NIP-01 signature verification failed
```

**Good:**
```
⚠️ Couldn't post right now
We'll try again automatically, or you can retry
[Retry] [Cancel]
```

**Bad:**
```
Settings
☐ Enable NIP-65 Outbox Model
☐ Verify NIP-01 Signatures
☐ Support NIP-46 Remote Signers
```

**Good:**
```
Settings
☐ Optimize network performance (recommended)
☐ Verify post authenticity (recommended)

Advanced →
  ☐ Use external key manager
```

### Challenge 4: When to Introduce Advanced Nostr Features

**The progressive rollout:**

**Week 1: Core social experience**
- Post, read, like, reply
- Follow/unfollow
- Profile editing
- Notifications
- Zero Nostr-specific concepts

**Week 2-4: Light customization**
- Mute/block users (no "Web of Trust" jargon)
- Notification preferences
- Display preferences
- Content filters

**Month 2+: Power user features (opt-in)**
- Network settings (relay management)
- Advanced security (remote signers)
- Data portability (export/import)
- Custom feeds
- Zap configuration

**Power user detection signals:**
- User explores settings multiple times
- User asks support about advanced features
- User follows >100 accounts
- User posts >10 times/week
- User has been active >30 days

**Contextual feature discovery:**
```typescript
// Show power user hints based on behavior
if (user.daysActive > 30 && user.postsCount > 50) {
  showContextualHint(
    "💡 Did you know?",
    "You can optimize your network settings for better performance",
    "Settings → Advanced → Network"
  )
}

// Only show once, never intrusive
```

### Challenge 5: Settings Organization for Nostr Apps

**Applying 10-15 items limit to Nostr settings:** [[Research:58]](#research-58)

**Basic Settings (Visible to all, <10 items)**
```
Profile & Account
  • Edit profile
  • Username (NIP-05)
  • Privacy settings

Notifications
  • Enable notifications
  • Sound & badges

Display
  • Theme (Light/Dark/Auto)
  • Text size

Security
  • Require biometric unlock
  • Backup account
```

**Advanced Settings (Collapsed by default)**
```
Advanced →
  Network
    • Network optimization (auto/manual)
    • Connection status

  Security
    • Key management
    • Remote signer setup

  Data & Storage
    • Cache management
    • Import/export

  Experimental
    • Beta features
    • Debug mode
```

**Developer/Debug (Hidden, requires code/gesture)**
```
Hold settings icon for 3 seconds →

Developer Options
  • Relay management (full control)
  • Event inspector
  • NIP feature flags
  • Performance monitoring
  • Protocol diagnostics
```

---

## Pattern Library: Concrete Solutions

### Pattern A: Collapsible Advanced Settings

**Problem:** Settings page with 30+ options overwhelming users.

**Solution:** Group related settings, collapse advanced sections by default.

**Implementation:**

```tsx
function SettingsScreen() {
  const [showAdvanced, setShowAdvanced] = useState(false)
  const [showDeveloper, setShowDeveloper] = useState(false)

  return (
    <div className="settings">
      {/* Basic Settings - Always Visible */}
      <Section title="Profile & Account">
        <Setting label="Edit profile" onClick={editProfile} />
        <Setting label="Username" value={user.nip05} />
        <Setting label="Privacy settings" onClick={showPrivacy} />
      </Section>

      <Section title="Notifications">
        <Toggle label="Enable notifications" checked={notificationsEnabled} />
        <Toggle label="Sound & badges" checked={soundEnabled} />
      </Section>

      <Section title="Display">
        <Select label="Theme" options={['Light', 'Dark', 'Auto']} value={theme} />
        <Slider label="Text size" value={textSize} min={12} max={24} />
      </Section>

      <Section title="Security">
        <Toggle label="Require biometric unlock" checked={biometricEnabled} />
        <Setting label="Backup account" onClick={showBackup} />
      </Section>

      {/* Advanced Settings - Collapsed by Default */}
      <CollapsibleSection
        title="Advanced"
        isOpen={showAdvanced}
        onToggle={() => setShowAdvanced(!showAdvanced)}
        itemCount={8}
      >
        <Subsection title="Network">
          <Toggle label="Network optimization" checked={autoNetwork} />
          <Setting label="Connection status" onClick={showNetworkStatus} />
        </Subsection>

        <Subsection title="Security">
          <Setting label="Key management" onClick={showKeyManagement} />
          <Setting label="Remote signer setup" onClick={showSignerSetup} />
        </Subsection>

        <Subsection title="Data & Storage">
          <Setting label="Cache management" onClick={showCacheSettings} />
          <Setting label="Import/export" onClick={showDataPortability} />
        </Subsection>

        <Subsection title="Experimental">
          <Toggle label="Beta features" checked={betaEnabled} />
          <Setting label="Debug mode" onClick={enableDebugMode} />
        </Subsection>
      </CollapsibleSection>

      {/* Developer Settings - Hidden */}
      {showDeveloper && (
        <CollapsibleSection title="Developer Options" isDangerous>
          <Setting label="Relay management" onClick={showRelayManager} />
          <Setting label="Event inspector" onClick={showEventInspector} />
          <Setting label="NIP feature flags" onClick={showNIPFlags} />
        </CollapsibleSection>
      )}
    </div>
  )
}

// Collapsible section component
function CollapsibleSection({ title, isOpen, onToggle, itemCount, isDangerous, children }) {
  return (
    <div className={`collapsible-section ${isDangerous ? 'dangerous' : ''}`}>
      <button onClick={onToggle} className="section-header">
        <span>{title}</span>
        {!isOpen && itemCount && <span className="badge">{itemCount}</span>}
        <ChevronIcon direction={isOpen ? 'up' : 'down'} />
      </button>
      {isOpen && <div className="section-content">{children}</div>}
    </div>
  )
}
```

**Validation:**
- Basic settings: 8 items (under 10 limit)
- Advanced settings: 8 items (collapsed by default)
- Clear visual hierarchy
- Item count badge shows what's hidden

---

### Pattern B: Contextual Feature Introduction

**Problem:** Users don't know about advanced features that could help them.

**Solution:** Show contextual hints based on user behavior, never intrusive.

**Implementation:**

```typescript
// Track user behavior to detect power user patterns
interface UserBehaviorTracker {
  daysActive: number
  postsCount: number
  followingCount: number
  settingsVisits: number
  hasSeenHint: Set<string>
}

function shouldShowHint(
  hintId: string,
  user: UserBehaviorTracker,
  condition: () => boolean
): boolean {
  // Never show same hint twice
  if (user.hasSeenHint.has(hintId)) return false

  // Check condition
  return condition()
}

// Contextual hint system
function useContextualHints(user: UserBehaviorTracker) {
  const [currentHint, setCurrentHint] = useState<ContextualHint | null>(null)

  useEffect(() => {
    // Power user detection: Show relay optimization hint
    if (shouldShowHint('relay-optimization', user, () =>
      user.daysActive > 30 && user.postsCount > 50
    )) {
      setCurrentHint({
        id: 'relay-optimization',
        title: '💡 Did you know?',
        message: 'You can optimize your network settings for better performance',
        action: {
          label: 'Learn more',
          onClick: () => navigate('/settings/advanced/network')
        }
      })
    }

    // Frequent poster: Show backup reminder
    if (shouldShowHint('backup-reminder', user, () =>
      user.postsCount > 10 && !user.hasBackup
    )) {
      setCurrentHint({
        id: 'backup-reminder',
        title: '🔒 Secure your account',
        message: 'You\'ve posted 10 times! Consider backing up your account',
        action: {
          label: 'Set up backup',
          onClick: () => navigate('/settings/security/backup')
        }
      })
    }

    // Heavy follower: Show custom feed hint
    if (shouldShowHint('custom-feeds', user, () =>
      user.followingCount > 100
    )) {
      setCurrentHint({
        id: 'custom-feeds',
        title: '📋 Organize your feed',
        message: 'You follow 100+ people. Try creating custom feeds to organize content',
        action: {
          label: 'Create feed',
          onClick: () => navigate('/feeds/create')
        }
      })
    }
  }, [user])

  const dismissHint = (hintId: string) => {
    user.hasSeenHint.add(hintId)
    setCurrentHint(null)
    // Persist to storage
    saveDismissedHints(user.hasSeenHint)
  }

  return { currentHint, dismissHint }
}

// UI Component
function ContextualHintBanner({ hint, onDismiss }) {
  if (!hint) return null

  return (
    <div className="contextual-hint">
      <div className="hint-content">
        <h4>{hint.title}</h4>
        <p>{hint.message}</p>
      </div>
      <div className="hint-actions">
        <button onClick={hint.action.onClick} className="primary">
          {hint.action.label}
        </button>
        <button onClick={() => onDismiss(hint.id)} className="secondary">
          Dismiss
        </button>
      </div>
    </div>
  )
}
```

---

### Pattern C: Progressive Relay Configuration

**Problem:** Relay selection too complex for beginners, but essential for power users.

**Solution:** Three-tier progressive disclosure (invisible → basic → advanced).

**Implementation:**

```typescript
// Level 1: Automatic relay selection (invisible to user)
class AutomaticRelayManager {
  private userLocation: string
  private relayStats: Map<string, RelayStats>

  async getOptimalRelays(): Promise<string[]> {
    const location = await this.getUserLocation()
    const defaults = this.getDefaultRelays(location)
    const tested = await this.testRelayLatency(defaults)

    // Return 3-4 fastest, most reliable relays
    return tested
      .sort((a, b) => a.latency - b.latency)
      .slice(0, 4)
      .map(r => r.url)
  }

  private getDefaultRelays(location: string): string[] {
    const globalRelays = [
      'wss://relay.damus.io',
      'wss://nos.lol',
      'wss://relay.nostr.band'
    ]

    const regionalRelays = {
      'NA': ['wss://nostr.mom', 'wss://relay.current.fyi'],
      'EU': ['wss://nostr.wine', 'wss://relay.orangepill.dev'],
      'APAC': ['wss://relay.nostr.wirednet.jp', 'wss://relay.nostr.moctane.com']
    }

    return [...globalRelays, ...(regionalRelays[location] || [])]
  }

  private async testRelayLatency(relays: string[]): Promise<RelayTestResult[]> {
    const results = await Promise.all(
      relays.map(async url => {
        const start = Date.now()
        try {
          await this.pingRelay(url)
          return { url, latency: Date.now() - start, online: true }
        } catch {
          return { url, latency: Infinity, online: false }
        }
      })
    )
    return results.filter(r => r.online)
  }
}

// Level 2: Basic toggle (Settings → Advanced)
function NetworkSettings() {
  const [mode, setMode] = useState<'auto' | 'custom'>('auto')
  const [customRelays, setCustomRelays] = useState<string[]>([])

  return (
    <div>
      <h2>Network Settings</h2>

      <RadioGroup value={mode} onChange={setMode}>
        <Radio value="auto">
          <strong>Automatic (Recommended)</strong>
          <p>We'll choose the best servers for you</p>
          <Tooltip>
            Nostr uses multiple servers (relays) to store your posts.
            Automatic mode works great for most people.
          </Tooltip>
        </Radio>

        <Radio value="custom">
          <strong>Custom configuration</strong>
          <p>Manually choose your servers</p>
        </Radio>
      </RadioGroup>

      {mode === 'custom' && (
        <button onClick={() => navigate('/settings/advanced/relays')}>
          Manage relays →
        </button>
      )}
    </div>
  )
}

// Level 3: Full relay management (Settings → Advanced → Relay Management)
function RelayManagementScreen() {
  const [relays, setRelays] = useState<Relay[]>([])
  const [showAddRelay, setShowAddRelay] = useState(false)

  return (
    <div className="relay-manager">
      <h2>Relay Management</h2>
      <p className="description">
        Advanced users: Customize which servers store and relay your posts
      </p>

      {/* Relay List */}
      <div className="relay-list">
        {relays.map(relay => (
          <RelayCard
            key={relay.url}
            relay={relay}
            onRemove={() => removeRelay(relay.url)}
            onToggleRead={() => toggleRelayRead(relay.url)}
            onToggleWrite={() => toggleRelayWrite(relay.url)}
          />
        ))}
      </div>

      {/* Add Relay */}
      <button onClick={() => setShowAddRelay(true)}>
        + Add relay
      </button>

      {/* Advanced Options */}
      <CollapsibleSection title="Advanced Options">
        <Toggle
          label="Enable NIP-65 Outbox Model"
          tooltip="Use your relay preferences when others fetch your posts"
          checked={nip65Enabled}
          onChange={setNip65Enabled}
        />
        <Setting
          label="Import relay list"
          onClick={importRelayList}
        />
        <Setting
          label="Export relay list"
          onClick={exportRelayList}
        />
      </CollapsibleSection>

      {/* Relay Health Monitoring */}
      <Section title="Relay Health">
        <RelayHealthDashboard relays={relays} />
      </Section>
    </div>
  )
}

function RelayCard({ relay, onRemove, onToggleRead, onToggleWrite }) {
  return (
    <div className="relay-card">
      <div className="relay-info">
        <StatusIndicator status={relay.status} />
        <span className="relay-url">{relay.url}</span>
        <span className="relay-latency">{relay.latency}ms</span>
      </div>

      <div className="relay-controls">
        <Toggle
          label="Read"
          size="small"
          checked={relay.read}
          onChange={onToggleRead}
        />
        <Toggle
          label="Write"
          size="small"
          checked={relay.write}
          onChange={onToggleWrite}
        />
        <button onClick={onRemove} className="icon-button">
          <TrashIcon />
        </button>
      </div>
    </div>
  )
}
```

---

### Pattern D: Smart Feature Gating

**Problem:** Advanced features visible to all users, causing confusion.

**Solution:** Gate features based on user proficiency level, with clear upgrade path.

**Implementation:**

```typescript
// User proficiency detection
enum UserLevel {
  BEGINNER = 'beginner',      // 0-7 days, <10 posts
  INTERMEDIATE = 'intermediate', // 7-30 days, 10-50 posts
  ADVANCED = 'advanced',        // 30+ days, 50+ posts
  POWER_USER = 'power_user'     // Explicitly enabled advanced mode
}

function getUserLevel(user: User): UserLevel {
  // Explicit power user mode
  if (user.settings.advancedMode) {
    return UserLevel.POWER_USER
  }

  // Based on activity
  const { daysActive, postsCount, followingCount } = user.stats

  if (daysActive > 30 && postsCount > 50) {
    return UserLevel.ADVANCED
  }

  if (daysActive > 7 && postsCount > 10) {
    return UserLevel.INTERMEDIATE
  }

  return UserLevel.BEGINNER
}

// Feature gating component
function FeatureGate({
  requiredLevel,
  feature,
  fallback,
  children
}: {
  requiredLevel: UserLevel
  feature: string
  fallback?: React.ReactNode
  children: React.ReactNode
}) {
  const user = useUser()
  const userLevel = getUserLevel(user)

  const levels = [
    UserLevel.BEGINNER,
    UserLevel.INTERMEDIATE,
    UserLevel.ADVANCED,
    UserLevel.POWER_USER
  ]

  const hasAccess = levels.indexOf(userLevel) >= levels.indexOf(requiredLevel)

  if (hasAccess) {
    return <>{children}</>
  }

  // Show upgrade prompt for intermediate/advanced users
  if (userLevel >= UserLevel.INTERMEDIATE && fallback) {
    return <>{fallback}</>
  }

  // Hide completely for beginners
  return null
}

// Usage examples
function ComposerToolbar() {
  return (
    <div className="composer-toolbar">
      {/* Always visible */}
      <button>Bold</button>
      <button>Italic</button>
      <button>Link</button>

      {/* Intermediate+ */}
      <FeatureGate requiredLevel={UserLevel.INTERMEDIATE} feature="markdown">
        <button>Code</button>
        <button>Quote</button>
      </FeatureGate>

      {/* Advanced+ */}
      <FeatureGate
        requiredLevel={UserLevel.ADVANCED}
        feature="custom-relays"
        fallback={
          <Tooltip>
            Unlock custom relay selection after 30 days of activity
          </Tooltip>
        }
      >
        <button onClick={openRelaySelector}>
          Choose relays for this post
        </button>
      </FeatureGate>

      {/* Power users only */}
      <FeatureGate requiredLevel={UserLevel.POWER_USER} feature="raw-event">
        <button onClick={editRawEvent}>Edit raw event</button>
      </FeatureGate>
    </div>
  )
}

function SettingsMenu() {
  const userLevel = getUserLevel(useUser())

  return (
    <div>
      {/* Basic settings - always visible */}
      <MenuItem to="/settings/profile">Profile</MenuItem>
      <MenuItem to="/settings/notifications">Notifications</MenuItem>
      <MenuItem to="/settings/display">Display</MenuItem>

      {/* Advanced settings - gated */}
      <FeatureGate requiredLevel={UserLevel.INTERMEDIATE} feature="advanced-settings">
        <MenuItem to="/settings/advanced">Advanced</MenuItem>
      </FeatureGate>

      {/* Power user prompt */}
      {userLevel === UserLevel.ADVANCED && (
        <MenuItem onClick={enablePowerUserMode}>
          <span>Enable Power User Mode</span>
          <Badge>Unlock all features</Badge>
        </MenuItem>
      )}
    </div>
  )
}
```

---

### Pattern E: In-App Feature Education

**Problem:** Users don't understand what advanced features do or when to use them.

**Solution:** Contextual tooltips and progressive education.

**Implementation:**

```tsx
// Educational tooltip system
function EducationalTooltip({
  feature,
  title,
  description,
  learnMoreUrl,
  children
}: {
  feature: string
  title: string
  description: string
  learnMoreUrl?: string
  children: React.ReactNode
}) {
  const [hasSeenTooltip, setHasSeenTooltip] = useState(
    () => localStorage.getItem(`tooltip-seen-${feature}`) === 'true'
  )
  const [isOpen, setIsOpen] = useState(false)

  const markAsSeen = () => {
    localStorage.setItem(`tooltip-seen-${feature}`, 'true')
    setHasSeenTooltip(true)
    setIsOpen(false)
  }

  return (
    <Tooltip
      isOpen={isOpen}
      onOpenChange={setIsOpen}
      content={
        <div className="educational-tooltip">
          <h4>{title}</h4>
          <p>{description}</p>
          <div className="tooltip-actions">
            {learnMoreUrl && (
              <a href={learnMoreUrl} target="_blank">
                Learn more →
              </a>
            )}
            <button onClick={markAsSeen}>Got it</button>
          </div>
        </div>
      }
      badge={!hasSeenTooltip ? '!' : undefined}
    >
      {children}
    </Tooltip>
  )
}

// Usage in advanced settings
function AdvancedNetworkSettings() {
  return (
    <div>
      <EducationalTooltip
        feature="relay-read-write-split"
        title="Read/Write Relay Split"
        description="Choose different servers for reading posts (read) and publishing your posts (write). This can improve performance and privacy."
      >
        <Toggle
          label="Separate read and write relays"
          checked={splitRelays}
          onChange={setSplitRelays}
        />
      </EducationalTooltip>

      <EducationalTooltip
        feature="outbox-model"
        title="Outbox Model (NIP-65)"
        description="Tell other users which servers to check for your posts. This helps your posts reach more people reliably."
        learnMoreUrl="https://github.com/nostr-protocol/nips/blob/master/65.md"
      >
        <Toggle
          label="Enable outbox model"
          checked={outboxEnabled}
          onChange={setOutboxEnabled}
        />
      </EducationalTooltip>

      <EducationalTooltip
        feature="relay-auth"
        title="Relay Authentication"
        description="Some relays require authentication to prevent spam. This lets you connect to authenticated relays."
      >
        <Toggle
          label="Allow relay authentication (NIP-42)"
          checked={authEnabled}
          onChange={setAuthEnabled}
        />
      </EducationalTooltip>
    </div>
  )
}
```

---
