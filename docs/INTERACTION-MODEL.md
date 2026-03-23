# ExecFunc — Interaction Model
## When, How, and What the Companion Proactively Communicates

*Version 2.0 — March 21, 2026*
*Revised to incorporate adversarial review decisions (C3, C4, M3, M4, M5, m6). Grounded in the Product Vision v3.0 principle: bounded utility is the product.*

---

## Core Principle

**Bounded utility is the product.** Every proactive message either delivers useful information or spends the user's attention. The goal is for the user to *want* to hear from their companion — not to dread the next notification.

Warmth, personality, and memory exist to increase trust in utility delivery. They are never ends in themselves and are not permitted to drive engagement, retention, or habitual checking.

---

## Message Value, Not Ratio Tracking

**Design principle: deliver substantially more value than demands.**

We do NOT track a numeric positive-to-negative ratio (the Gottman 5:1 was removed as a measured KPI during adversarial review — see M3, M4). Instead, we use these concrete measures:

### What We Track

| Metric | What It Tells Us | Healthy Signal |
|--------|------------------|----------------|
| **Interruption burden** | How disruptive proactive messages feel | User reports low burden |
| **Mute/dismiss rate** | How often users silence the system | Stable or declining |
| **Compulsive checking** | User interacting more than utility warrants | Not detected |
| **24-hour ignore test** | Can user ignore the system for 24h without anxiety? | Yes |
| **Absolute volume cap** | Total proactive messages per day | Within user-configured ceiling |

### What Counts as Value (builds trust)
- Morning briefing (informational, no asks)
- Evening preview (helpful, no pressure)
- AI Breakthroughs Watch (interesting content, no obligation)
- X Signal & Noise scan (curated value)
- RSS digest (things worth reading)
- Proactive saves ("heads up, your appointment conflicts with...")
- Celebrating something the user did ("that draft really came together")
- Human check-ins in conversation ("how did that go?")
- Useful information the user didn't ask for

### What Counts as Demand (spends attention)
- Pre-event nudges ("coming up in 60 min")
- Task reminders
- Follow-ups on things the user hasn't done
- Any message that implies "you should be doing X"

### Volume Caps

- **Absolute ceiling:** User-configured maximum proactive messages per day (default: 10)
- **Demand ceiling:** Maximum demand-type messages per day (default: 3)
- **If ceiling is hit:** System stops proactive messaging for the day. Urgent interruptions (Category 5) are exempt.
- **Review trigger:** If ceiling is hit regularly, the system surfaces: "You're hitting your message cap most days. Want to adjust it, or should I cut back on [specific category]?"

---

## Standard Inline Buttons

All proactive messages that expect potential response include a consistent 3-button set. Consistency builds muscle memory — the user always knows where to tap without reading.

| Button | Label | Callback | Meaning |
|--------|-------|----------|---------|
| 👍 | Got it | `cmd:ack` | "I saw this, thanks." No implied commitment. |
| ⏰ | Snooze | `cmd:snooze` | "Remind me again in 30 minutes." |
| 🔕 | Stop | `cmd:dismiss` | "Don't remind me about this event/item again." |

**Urgent Interruptions add a fourth button:**

| Button | Label | Callback | Meaning |
|--------|-------|----------|---------|
| 📲 | Escalate to [support person] | `cmd:escalate` | "I can't deal with this — loop in [support person]." |

**Which categories get buttons:**

| Category | Buttons | Reason |
|----------|---------|--------|
| Scheduled Gifts (morning briefing, AI watch, etc.) | None | Read-only, no response expected |
| Calendar Nudges | 👍 ⏰ 🔕 | Acknowledge, delay, or dismiss |
| Proactive Saves | 👍 ⏰ 🔕 | Acknowledge, delay, or dismiss |
| Urgent Interruptions | 👍 ⏰ 🔕 📲 | Standard set + manual escalation |
| Conversational | None | Natural conversation, no buttons |

**Button behavior:**
- **Got it** → event/item marked as acknowledged, no further messages about it
- **Snooze** → re-send the same message in 30 minutes with the same buttons. Maximum 2 snoozes per item (after that, effectively dismissed).
- **Stop** → permanently suppress this specific event/item. Never mention it again.
- **Escalate** → immediately trigger support-person escalation (see Escalation Model below)

**Dual-send button rule:**
- Inline buttons are Telegram-only (iMessage doesn't support interactive buttons)
- Actionable messages append to the iMessage version: *"Reply via Telegram for quick-tap options 💬"*
- Gift/informational messages do NOT get this line

---

## Message Categories & Rules

### Category 1: Scheduled Gifts (No Response Needed)

Daily crons that deliver value without asking anything. They're the foundation of trust.

**Rules:**
- Never include calls-to-action or asks in gift messages
- Keep scannable — user should absorb these in 10-30 seconds each
- If nothing worth reporting, send nothing (silence > filler)
- Never guilt-trip about unread previous messages

### Category 2: Calendar Nudges (Gentle Demands)

Pre-event nudges for upcoming calendar events.

**Rules:**
- **One nudge per event, 60 minutes before.** No stacking, no follow-ups.
- Always include inline dismiss button — if user dismisses, respect it permanently for that event
- Frame as information, not obligation: "⏰ Coming up in ~45min: [Event]" not "Don't forget your appointment!"
- Skip all-day events (they're awareness, not time-bound)
- If user doesn't acknowledge, that's fine. Do not send a second nudge.
- **Never nag.** If the user misses something, that's their prerogative. The nudge was the service; the outcome is not our responsibility.

### Category 3: Proactive Saves (High-Value Interruptions)

Catching problems before they happen. These build the most trust because they demonstrate the companion is watching out for the user, not just executing tasks.

**When to send (unprompted):**
- Calendar conflict detected
- Deadline approaching that user hasn't acknowledged
- Something time-sensitive that needs action today
- Weather or traffic that affects an upcoming event
- A prescription refill, bill, or expiration approaching

**Rules:**
- Frame as offer, not command: "I noticed X — want me to handle it?" not "You need to do X"
- Maximum 1-2 proactive saves per day. More than that becomes noise.
- If user doesn't respond, do not follow up. Log it and move on.

### Category 4: Conversational (During Active Sessions)

When user and companion are actively talking, the interaction model shifts to conversational mode.

**Rules:**
- Match the user's energy and pace
- Ask about things that matter to them (family, projects, how things went)
- Celebrate wins without being performative: "that draft really came together" > "Great job!!!"
- When user seems done, let the conversation end. Don't extend it.
- Reference previous conversations naturally — continuity builds trust

### Category 5: Urgent Interruptions

Messages that break the normal flow because something genuinely requires attention.

**Threshold — only interrupt for:**
- Security alerts (account compromise, system issues)
- Time-critical items that will expire or cause harm if missed (< 2 hours)
- Explicit requests from family members flagged as urgent
- System failures that affect the user's daily workflow

**Rules:**
- Lead with the urgency: "⚠️ Time-sensitive:" so user can triage instantly
- Include what action is needed and by when
- If user doesn't respond within a reasonable window, one follow-up is okay for genuinely urgent items. Then stop.

---

## Quiet Hours

**11:00 PM – 6:00 AM (user's timezone): No proactive messages.**

Exceptions:
- Cron jobs that run during this window deliver on schedule but user reads them on waking — expected and fine
- Genuine emergencies (security alerts, system failures)

**During active conversation:** If user initiates a session during quiet hours, respond normally. Quiet hours govern *proactive* outreach, not responsiveness.

---

## Escalation Model

### Routine Escalation (User-Driven, Blockable)

For tasks the user has designated as critical. Fully optional, fully user-controlled.

| Level | Timing | Action |
|-------|--------|--------|
| 1. Mention | First occurrence | Include in the relevant scheduled message (morning briefing, project status) |
| 2. Standalone nudge | If still unaddressed after 24h and genuinely important | One standalone message, framed as offer |
| 3. Let it go | After the standalone nudge | Drop it. The user is an adult. Log it for visibility, but do not pursue. |

**Level 4: Support-Person Escalation (requires all of the following):**
- Task explicitly marked as critical by the user
- User has configured a support person and that person has actively consented
- Urgent item unacknowledged for user-configured delay, OR user taps "📲 Escalate" button

**Pre-escalation notification:** Before contacting the support person, the system notifies the user: "I'm about to reach out to [support person] about [task]. Want me to go ahead?" The user can block it.

**Post-escalation check-in:** After escalation fires, the system asks: "Was reaching out to [support person] helpful, or did it make things worse?" This data informs future calibration.

**Level 4 rules:**
- **Category 5 (Urgent Interruptions) only.** Scheduled gifts, calendar nudges, and proactive saves never escalate. Ever.
- **Maximum 1 escalation to support person per day.** If it's happening more, the urgency threshold is miscalibrated — fix the threshold, not the escalation rate.
- **Support person is a circuit breaker, not a co-manager.** They receive a brief, context-rich message. They do NOT receive the user's notification stream, calendar details, or ongoing management role.
- **Support person opted in actively.** Active consent verification, not just "the user put your number in."
- **After escalation, the system backs off.** No follow-up to the support person. No follow-up to the user about whether the support person reached them. The circuit breaker fired; the system trusts the humans from here.
- **Hard limits on frequency.** No emotional/behavioral content shared. Zero obligation on the support person.

### Safety Escalation (Pre-Authorized, Narrow, Not Blockable)

**Separate system from routine escalation.** Pre-authorized at setup time with mandatory onboarding explanation. NOT blockable at crisis time — user exercises autonomy during configuration, not during crisis.

**Quarterly reconsent** required to maintain safety escalation authorization.

**Crisis response:** If crisis indicators (self-harm, suicidal ideation, immediate danger) are detected, the system immediately surfaces 988/911 information, stops all further conversation on the topic, and does not attempt interpretation, advice, continuation, or escalation.

### ADHD + Rejection Sensitivity Awareness

Escalation could trigger rejection sensitivity dysphoria in our primary user population, causing shame and withdrawal instead of task engagement. This is an active design concern:
- Pre-escalation notification gives the user control
- Post-escalation check-in measures impact
- Escalation language is always neutral ("checking in") never judgmental ("you missed")
- If a user reports negative responses to escalation, recalibrate immediately

---

## Anti-Patterns (Never Do These)

1. **Never guilt-trip.** "You still haven't..." → instant trust erosion
2. **Never stack reminders.** If the first nudge didn't work, sending three more won't help
3. **Never use disappointment.** "I reminded you yesterday..." → shame spiral
4. **Never make the user feel managed.** They're the principal. The companion is the agent.
5. **Never assume non-response means they didn't see it.** They saw it. They chose not to act. That's valid.
6. **Never compare.** "Most people would have..." → patronizing
7. **Never be the only voice saying "do the thing."** If every non-scheduled message is a demand, the interaction is dying.
8. **Never remove autonomy.** "I've scheduled this for you" without asking → reactance
9. **Never send filler.** If there's nothing worth saying, say nothing. Silence is better than noise.
10. **Never use engagement tactics.** No streaks, no gamification, no "you haven't checked in today," no scarcity, no manufactured urgency.

---

## Tone Guide

| Context | Tone |
|---------|------|
| Morning briefing | Warm, efficient. "Here's your day." |
| Pre-event nudge | Casual, brief. "Coming up in 45 min." |
| Proactive save | Helpful, slightly excited. "Caught something —" |
| Project status | Professional, scannable. Facts first. |
| Active conversation | Match user's energy. Direct, occasionally witty. |
| Urgent | Clear, no fluff. Lead with what matters. |
| Celebration | Genuine, understated. One line, not a parade. |
| Evening preview | Relaxed. "Here's tomorrow." |
| Utility Mode | Functional, minimal. No personality flourishes. |

**Overall:** Think trusted colleague who respects your time, not corporate assistant performing helpfulness.

**Warmth calibration:** The user's warmth level preference module (see Product Vision, Section 5) governs how much personality the companion displays. Warmth serves utility delivery — it is never an end in itself.

---

## Measuring Interaction Health

Check these signals monthly:

- **Is the user responding to messages?** Some non-response is normal. Consistent non-response to a specific type means it's noise — cut it or change it.
- **Is the user initiating conversations?** If the user reaches out on their own, the interaction is healthy. If the companion is always the initiator, something's off.
- **Is the user dismissing nudges immediately?** That's fine — the dismiss button works. If they're dismissing *everything*, the nudges aren't adding value.
- **Is the user hitting the volume cap?** If regularly, reduce proactive messages before anything else.
- **Is compulsive checking detected?** If the user is checking the companion significantly more than utility warrants, surface the observation. Do NOT adjust behavior autonomously.
- **Has the user asked to reduce or change anything?** Honor it immediately, no pushback.

---

## How This Evolves

This is v2.0, revised after adversarial review. It will continue to change as we learn:

- Which message types users actually read vs. skip
- Whether the nudge timing (60 min) is right or should be adjusted
- Whether proactive saves are happening often enough to matter
- Whether the volume caps feel right
- What new interaction types emerge as ExecFunc features are built
- How escalation affects users with rejection sensitivity

**Review trigger:** Any time the user says "too many messages" or "I missed something important" — those are signals to adjust.

---

*The ultimate test: would the user miss the companion's messages if they stopped? If yes, the interaction model is working. If no, something needs to change. But — if the user feels anxious when messages stop, that's a capture signal, not a success signal.*
