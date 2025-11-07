# Pattern 3: Core Interaction Loops

**Status:** 🚧 Work in Progress
**Last Updated:** November 2025

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

**Core interactions failing:**
- [CITATION NEEDED] Posts disappear seconds after posting
- [CITATION NEEDED] Reactions (likes/zaps) don't appear consistently
- [CITATION NEEDED] Replies sometimes vanish
- [CITATION NEEDED] Following/unfollowing unreliable across clients
- [CITATION NEEDED] Missing or delayed notifications

**Trust erosion:**
- Users lose confidence when basic actions don't work
- "Did my post actually send?" uncertainty
- Cross-client inconsistency destroys trust
- No feedback when actions fail

**The retention impact:**
- Users abandon apps that feel "broken"
- Unreliable core interactions more damaging than missing features
- Trust lost is hard to rebuild

### Root Causes

1. **Multi-relay coordination failures**: Events not propagating to all necessary relays
2. **No publish confirmation**: Apps don't verify events were actually accepted by relays
3. **Race conditions**: Rapid actions cause conflicts
4. **Missing error handling**: Silent failures leave users confused
5. **Optimistic UI without validation**: Shows success before confirming
6. **Cross-client event conflicts**: Different clients make conflicting updates

### Why This Matters

> "If posting doesn't work reliably, nothing else matters." [CITATION NEEDED]

**Trust threshold**: Users tolerate 1-2 failures before abandoning. Core interactions must be >99% reliable.

---

## Universal Principles (70%)

These principles apply to any social application, regardless of underlying architecture.

### 1. Perceived Reliability Trumps Actual Speed

**Research backing:** [Research:NEEDED - cite perceived performance studies]

**Core principle:** Users prefer slower, reliable interactions over fast but unreliable ones.

**Key insight:** A 200ms delay with clear feedback feels better than instant action that might have failed.

**Mainstream approaches:**
- **Twitter/X:** Shows "Sending..." state, confirms when tweet is live
- **Instagram:** Upload progress bar, "Posted" confirmation
- **Discord:** Message appears with "Sending..." then checkmark when delivered
- **Slack:** Pending indicator, retry on failure

**What users need:**
1. Immediate visual feedback that action was received
2. Loading/processing state
3. Clear success/failure indication
4. Easy retry on failure

### 2. Optimistic UI with Validation

**Research backing:** [Research:NEEDED - cite optimistic UI studies]

**The pattern:**
1. Show the change immediately (optimistic)
2. Send the request in background
3. Validate the response
4. Rollback or show error if failed

**When to use optimistic UI:**
- ✅ Actions users expect to succeed (like, follow, post)
- ✅ When you can easily rollback
- ✅ When instant feedback improves experience
- ❌ Critical actions that can't be undone
- ❌ When failure rate is high
- ❌ When rollback is confusing

**Example: Liking a post**
```
User clicks like
→ Heart turns red immediately (optimistic)
→ Send like event to server
→ If success: keep heart red
→ If failure: revert to gray + show error toast
```

### 3. Progressive Feedback States

**Research backing:** [Research:NEEDED - cite loading states research]

**States every interaction needs:**
1. **Idle** - Ready for action
2. **Initiated** - User clicked/tapped
3. **Processing** - Request in flight
4. **Success** - Confirmed complete
5. **Error** - Failed with explanation

**Visual indicators:**
- Initiated: Button state change (pressed)
- Processing: Spinner, progress bar, or animated indicator
- Success: Checkmark, color change, brief confirmation
- Error: Red indicator, error message, retry button

### 4. Error Messages That Help

**Research backing:** [Research:NEEDED - cite error messaging best practices]

**Bad error messages:**
- "Error occurred" (no information)
- "Network error" (too vague)
- "Failed to post event" (what do I do?)

**Good error messages:**
- "Your post couldn't be sent. Check your connection and try again."
- "Follow action failed. The user's profile might not be available right now."
- "Like wasn't saved. Tap to retry."

**Error message checklist:**
- Explains what happened in plain language
- Suggests what user can do
- Provides easy retry mechanism
- Doesn't expose technical jargon

### 5. Idempotency: Allow Retries Safely

**Research backing:** [Research:NEEDED - cite distributed systems patterns]

**Core principle:** Users should be able to retry actions without creating duplicates or causing problems.

**Implementation:**
- Use unique IDs for actions
- Server checks if action already completed
- Retry produces same result as initial request
- UI prevents accidental double-taps

**Example: Publishing a post**
```
Generate unique post ID client-side
User clicks "Post"
→ Send event with ID
→ If network fails, user retries
→ Server sees duplicate ID, returns success without creating duplicate
→ User sees their post (not duplicate)
```

---

## Nostr-Specific Considerations (30%)

### Challenge 1: Multi-Relay Publishing & Verification

**The protocol reality:**
- Events must be published to multiple relays
- Different users read from different relays
- No guarantee all relays will accept the event
- Some relays may be slow or offline

**Current failures:**
- Post to 3 relays, only 2 accept it
- Other users don't see your post (they use the 3rd relay)
- No way to know which relays failed

**Solution patterns:**
- Publish to user's write relays + common relays
- Wait for confirmation from at least N relays before showing success
- Retry failed relays in background
- Show partial success: "Posted to 4 of 5 relays"

### Challenge 2: Event ID vs Relay Confirmation

**The issue:** Nostr clients can create the event and event ID locally, but that doesn't mean relays accepted it.

**Bad pattern:**
```typescript
const event = createEvent(content)
// Event has ID, but hasn't been sent!
showInFeed(event) // Optimistic UI
await publishToRelays(event) // Might fail, but post already shown
```

**Good pattern:**
```typescript
const event = createEvent(content)
showAsPending(event) // Show as "sending"
const results = await publishToRelays(event)
if (results.successCount >= MIN_RELAYS) {
  showAsPublished(event)
} else {
  showAsPartiallyPublished(event, results)
  retryFailedRelays(event, results.failed)
}
```

### Challenge 3: Following/Unfollowing Consistency

**The problem:** Kind 3 (contact list) events replace the entire list. Race conditions cause lost follows.

**Current failures:**
- User follows Alice in Client A
- User follows Bob in Client B (doesn't know about Alice yet)
- Client B publishes contact list without Alice
- Alice is now unfollowed

**Solutions:**
- Lock: Don't allow simultaneous follow/unfollow in same client
- Read-before-write: Always fetch latest contact list before modifying
- Conflict detection: Check if contact list changed since we read it
- Merge strategy: Combine follows from multiple sources

**NIP considerations:**
- [Protocol:NEEDED - NIP-02 contact lists]
- [Protocol:NEEDED - NIP-65 relay lists]

### Challenge 4: Reaction/Like Propagation

**The problem:** Reactions (Kind 7) need to propagate to where the original post's author can see them.

**Where to publish reactions:**
- User's write relays (so their followers see they liked something)
- Original post author's relays (so author sees the reaction)
- Relays where the original post was found

**Current failures:**
- Publish reaction only to your relays
- Author never sees it (they don't read your relays)
- Reaction count appears inconsistent across clients

### Challenge 5: Zap Workflow Complexity

**The multi-step process:**
1. Get author's Lightning address (from Kind 0 metadata)
2. Request invoice from author's Lightning service
3. Pay invoice via Lightning wallet
4. Lightning service publishes Kind 9735 zap receipt to relays
5. Client detects zap receipt and shows it

**Failure points:**
- Author has no Lightning address
- Lightning service is offline
- User's wallet can't pay invoice
- Zap receipt not published
- Client doesn't poll for receipts

**Current UX:**
- User clicks zap
- Wallet opens... then nothing
- No confirmation if zap went through
- Zap count doesn't update

**Better patterns:**
- Check for Lightning address before showing zap option
- Show clear steps: "Requesting invoice..." → "Opening wallet..." → "Confirming..."
- Poll for zap receipts after payment
- Show "Zapped! Receipt pending..." state
- Fallback if receipt never arrives

---

## Pattern Library: Concrete Solutions

### Pattern A: Reliable Post Publishing

**Problem:** Posts don't reliably appear for all users across relays.

**Solution:** Multi-phase publish with confirmation.

**Implementation:**

```typescript
async function publishPost(content: string): Promise<PublishResult> {
  const event = await createSignedEvent(content)

  // Phase 1: Show optimistic UI
  showPostAsPending(event)

  // Phase 2: Publish to relays in parallel
  const targetRelays = [
    ...getUserWriteRelays(),
    ...getCommonRelays() // High-traffic relays
  ]

  const results = await Promise.allSettled(
    targetRelays.map(relay => relay.publish(event, { timeout: 5000 }))
  )

  const successful = results.filter(r => r.status === 'fulfilled')
  const failed = results.filter(r => r.status === 'rejected')

  // Phase 3: Evaluate results
  if (successful.length >= 3) {
    showPostAsPublished(event)
    // Retry failed relays in background
    if (failed.length > 0) {
      retryInBackground(event, failed)
    }
    return { status: 'success', published: successful.length }
  } else if (successful.length > 0) {
    showPostAsPartial(event, successful.length, targetRelays.length)
    return { status: 'partial', published: successful.length }
  } else {
    showPostAsFailed(event)
    return { status: 'failed', published: 0 }
  }
}
```

**UI states:**
```
Pending:  [•••] Publishing...
Success:  [✓] Posted (4/4 relays)
Partial:  [!] Posted (2/4 relays) [Retry]
Failed:   [✗] Failed to post [Retry]
```

**Validation:**
- Track: % of posts that reach ≥3 relays
- Measure: Time from click to confirmation
- Survey: "Did your post publish reliably?"

---

### Pattern B: Optimistic Reactions with Rollback

**Problem:** Likes/reactions feel laggy or don't register.

**Solution:** Instant visual feedback with background confirmation and rollback on failure.

**Implementation:**

```typescript
async function reactToPost(postId: string, reaction: string = '+') {
  const reactionEvent = createReactionEvent(postId, reaction)

  // Immediate UI update
  addReactionToUI(postId, reaction)
  incrementReactionCount(postId)

  try {
    // Publish to relevant relays
    await publishReaction(reactionEvent, {
      userRelays: getUserWriteRelays(),
      postAuthorRelays: getPostAuthorRelays(postId)
    })

    // Success - already shown in UI

  } catch (error) {
    // Rollback UI changes
    removeReactionFromUI(postId, reaction)
    decrementReactionCount(postId)

    // Show error
    showToast('Reaction failed. Tap to retry.')
  }
}
```

**Visual feedback:**
```
Before: 👍 42   [tap]
During: 👍 43   (your reaction appears instantly)
Success: 👍 43  (stays)
Failure: 👍 42  (reverts) + error toast
```

---

### Pattern C: Reliable Follow/Unfollow

**Problem:** Following someone in one client, they disappear in another.

**Solution:** Read-modify-write pattern with conflict detection.

**Implementation:**

```typescript
async function followUser(pubkey: string) {
  // Step 1: Lock to prevent concurrent modifications
  if (contactListLock.isLocked()) {
    showToast('Please wait, processing previous action')
    return
  }
  contactListLock.acquire()

  try {
    // Step 2: Fetch latest contact list from relays
    const currentContacts = await fetchLatestContactList()

    // Step 3: Check if already following
    if (currentContacts.includes(pubkey)) {
      showToast('Already following')
      return
    }

    // Step 4: Add new follow
    const updatedContacts = [...currentContacts, pubkey]
    const contactListEvent = createContactListEvent(updatedContacts)

    // Step 5: Optimistic UI
    addToFollowingList(pubkey)

    // Step 6: Publish
    const result = await publishToRelays(contactListEvent)

    if (!result.success) {
      // Rollback
      removeFromFollowingList(pubkey)
      showError('Failed to follow. Try again.')
    }

  } finally {
    contactListLock.release()
  }
}
```

**Safety checks:**
- Lock prevents race conditions within same client
- Read-before-write prevents conflicts with other clients
- Verify event created_at is newer than current

---

### Pattern D: Clear Action Feedback System

**Problem:** Users don't know if their actions worked.

**Solution:** Standardized feedback states across all interactions.

**UI Component:**

```typescript
interface ActionFeedback {
  state: 'idle' | 'processing' | 'success' | 'error'
  message?: string
  retryAction?: () => void
}

function ActionButton({
  label,
  action,
  icon
}: ActionButtonProps) {
  const [feedback, setFeedback] = useState<ActionFeedback>({ state: 'idle' })

  async function handleAction() {
    setFeedback({ state: 'processing' })

    try {
      await action()
      setFeedback({ state: 'success' })
      setTimeout(() => setFeedback({ state: 'idle' }), 2000)
    } catch (error) {
      setFeedback({
        state: 'error',
        message: error.message,
        retryAction: handleAction
      })
    }
  }

  return (
    <button onClick={handleAction} disabled={feedback.state === 'processing'}>
      {feedback.state === 'idle' && <>{icon} {label}</>}
      {feedback.state === 'processing' && <>⏳ Processing...</>}
      {feedback.state === 'success' && <>✓ Done</>}
      {feedback.state === 'error' && (
        <>
          ✗ {feedback.message}
          <RetryButton onClick={feedback.retryAction} />
        </>
      )}
    </button>
  )
}
```

**Visual examples:**

```
Post button:
[ Post ]  →  [ ⏳ Posting... ]  →  [ ✓ Posted! ]  →  [ Post ]
                                  ↘ [ ✗ Failed. Retry? ]

Follow button:
[ Follow ]  →  [ ⏳ Following... ]  →  [ ✓ Following ]
                                     ↘ [ ✗ Error. Retry? ]

Like button:
[ ♡ Like ]  →  [ ♡ ]  →  [ ♥ Liked ]
                       ↘ [ ♡ Error: Tap to retry ]
```

---

### Pattern E: Batch Operations for Efficiency

**Problem:** Performing many actions individually is slow and unreliable.

**Solution:** Batch related operations and publish as group.

**Use cases:**
- Publishing a post + uploading attached images
- Following multiple users from starter pack
- Deleting multiple posts
- Broadcasting updates to multiple relays

**Implementation:**

```typescript
async function batchFollowUsers(pubkeys: string[]) {
  // Fetch current contact list once
  const currentContacts = await fetchLatestContactList()

  // Add all new follows
  const newFollows = pubkeys.filter(pk => !currentContacts.includes(pk))
  const updatedContacts = [...currentContacts, ...newFollows]

  // Single contact list update
  const event = createContactListEvent(updatedContacts)

  // Show progress
  showProgress(`Following ${newFollows.length} users...`)

  // Publish once
  await publishToRelays(event)

  // Update UI
  updateFollowingList(updatedContacts)
  showSuccess(`Following ${newFollows.length} new users!`)
}
```

**Benefits:**
- Reduces network requests
- Prevents race conditions
- Faster UX
- Lower chance of conflicts

---

## Anti-Patterns: What Not To Do

### Anti-Pattern 1: Silent Failures

**What it looks like:**
```typescript
async function publishPost(content) {
  const event = createEvent(content)
  try {
    await publishToRelays(event)
  } catch (error) {
    // Do nothing - silent failure
  }
  // User thinks post published, but it failed
}
```

**Why it fails:**
- User has no idea action failed
- No way to retry
- Post appears in local UI but not on network
- Destroys trust

**What to do instead:**
- Always show error state
- Provide retry mechanism
- Explain what went wrong
- Give user control

---

### Anti-Pattern 2: Fake Optimistic UI

**What it looks like:**
```typescript
function likePost(postId) {
  // Just update UI, never actually send
  incrementLikeCount(postId)
  showAsLiked(postId)
  // No network request!
}
```

**Why it fails:**
- Like isn't persisted
- Disappears on refresh
- Other users don't see it
- Completely breaks trust

**What to do instead:**
- Optimistic UI must be followed by actual request
- Validate and rollback on failure
- Never fake data

---

### Anti-Pattern 3: No Confirmation After Critical Actions

**What it looks like:**
- User deletes post, no confirmation shown
- User zaps 10000 sats, no receipt
- User unfollows account, no feedback

**Why it fails:**
- User unsure if action worked
- Anxiously checks multiple times
- May retry and create problems

**What to do instead:**
- Always confirm critical actions
- Show clear success state
- Provide undo if possible

---

### Anti-Pattern 4: Spinner Forever (No Timeout)

**What it looks like:**
```typescript
async function followUser(pubkey) {
  showSpinner()
  await publishFollow(pubkey) // Might hang forever
  // Spinner never stops if this hangs
}
```

**Why it fails:**
- User stuck waiting
- Can't cancel or retry
- App feels frozen

**What to do instead:**
- Set reasonable timeouts (5-10 seconds)
- Show timeout error
- Allow cancellation
- Provide retry option

---

### Anti-Pattern 5: Publishing to Only One Relay

**What it looks like:**
```typescript
async function publishPost(event) {
  const relay = getUserPreferredRelay()
  await relay.publish(event)
  // Only published to one relay!
}
```

**Why it fails:**
- Single point of failure
- Other users won't see post
- Defeats purpose of decentralization

**What to do instead:**
- Publish to multiple relays
- Include common/popular relays
- Verify multiple confirmations

---

## Validation Checklist

### Reliability Metrics

**Core interactions to measure:**
- [ ] **Post success rate:** >99% of posts reach ≥3 relays
- [ ] **Reaction success rate:** >99% of likes/reactions persist
- [ ] **Follow/unfollow success rate:** >99% without data loss
- [ ] **Time to confirmation:** <3 seconds for most actions
- [ ] **Error rate:** <1% of actions fail
- [ ] **Retry success rate:** >90% of retries succeed

### User Experience Metrics

- [ ] **Perceived reliability:** "Actions feel reliable" (user survey)
- [ ] **Trust score:** "I trust the app to save my actions" (user survey)
- [ ] **Confusion rate:** <5% of users report "not sure if action worked"
- [ ] **Error recovery rate:** % of users who successfully retry after error
- [ ] **Completion rate:** % of initiated actions that complete

### Technical Metrics

- [ ] **Relay publish success:** Average # of relays that accept events
- [ ] **Network failure handling:** % of network errors that show proper feedback
- [ ] **Rollback correctness:** Optimistic UI rollbacks work 100% of time
- [ ] **Lock contention:** Minimal race conditions in contact list updates
- [ ] **Timeout adherence:** No operations hang indefinitely

### User Research Questions

**Reliability perception:**
- "Do your posts reliably appear?"
- "When you like/react to something, does it always register?"
- "Have you lost follows/followers when switching clients?"

**Feedback clarity:**
- "When you post, is it clear when it's done?"
- "If something fails, do you know what happened?"
- "Can you easily retry failed actions?"

**Comparison to other platforms:**
- "How does reliability compare to Twitter/Instagram?"
- "Do you trust Nostr apps as much as mainstream apps?"
- "What makes you lose trust in an app?"

### A/B Testing Opportunities

Test different approaches:
- Optimistic vs confirmed UI
- Spinner duration before timeout
- Number of relays required for "success"
- Error message phrasing
- Retry button placement

**Measure impact on:**
- Perceived reliability
- User trust scores
- Action completion rates
- Retry rates
- Session length

---

## Citations & Sources

**Note:** This section will be populated with citations as research is conducted. All sources will be from 2024-2025 to ensure currency for this fast-moving technology.

### Data & Analytics

[Data:X] - Citations will be added for:
- Core interaction success rates from Nostr clients
- User complaints about reliability
- Retention impact of interaction failures

### Academic & UX Research

[Research:X] - Citations will be added for:
- Perceived performance vs actual performance
- Optimistic UI patterns
- Loading states and user expectations
- Error messaging best practices
- Trust and reliability in social apps

### Case Studies & Examples

[Example:X] - Citations will be added for:
- Twitter/X post publishing flow
- Instagram upload confirmation
- Discord message delivery
- Slack retry mechanisms

### Nostr Protocol Documentation

[Protocol:X] - Citations will be added for:
- NIP-01: Basic protocol flow
- NIP-02: Contact lists
- NIP-07: window.nostr capability
- NIP-65: Relay list metadata
- Other relevant NIPs for interaction reliability

### User Feedback & Quotes

[User:X] - Citations will be added for:
- "Posts disappear seconds after posting"
- "Lost all followers when switching clients"
- Missing notification complaints
- Reliability pain points from GitHub issues

---

**See [References & Bibliography](../appendices/references.md) for full citation details.**

---

*This pattern is part of the [Nostr UX Research Study](../README.md). See [OUTLINE.md](../OUTLINE.md) for the complete study structure.*

---

**Next Pattern:** [Pattern 4: Performance & Perceived Speed](04-performance.md) 🚧 Coming Soon
