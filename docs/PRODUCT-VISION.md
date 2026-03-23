# ExecFunc — Product Vision
## An AI Companion That Removes Friction From Daily Life

### Version 3.0 — March 21, 2026
### Open Source Edition

*Revised from v2.0 (March 14, 2026) incorporating all 43 findings from the adversarial review of March 20, 2026. See DECISION-LOG-2026-03-20.md for the canonical decision record.*

---

## 1. THE CORE INSIGHT

**Assistive support is itself a legitimate outcome.**

Every existing executive function app fails the same way: it becomes another thing to manage. A reminder app for people who can't manage reminders. A task list for people who can't manage task lists. The irony isn't just poetic — it's the fundamental product failure.

ExecFunc is not a reminder app. It's an AI companion that removes friction from daily life. If it also helps users build skills over time, that's a welcome side effect — but the project succeeds the moment it makes someone's life meaningfully better.

Glasses don't improve eyesight. GPS doesn't improve innate navigation. They still create meaningful independence. ExecFunc is assistive technology for executive function — and "assistive" is not a lesser category.

**The project has two jobs, in strict priority order:**

1. **Be genuinely useful right now.** Handle the hard parts. Don't gatekeep, don't lecture, don't nudge. Just help. This is the primary success criterion.
2. **Where appropriate, support skill development.** Only after trust is established. Only in separate, low-stakes contexts. Only when the user is ready. This is aspirational — valuable when it happens, not required for the project to justify itself.

These two jobs must never contaminate each other. The moment a user asks for help ordering food and gets a therapeutic exercise, trust is broken.

---

## 2. WHO THIS IS FOR

### Three Deployment Tiers

ExecFunc has three deployment tiers with fundamentally different scopes, safety postures, and user populations. Every feature, claim, and design decision must be explicit about which tier it belongs to.

#### Tier 1: Family / Private
The immediate users are the family building this — people with real daily life challenges in a real household. This isn't a hypothetical user persona; it's us.

- **Phase 1:** J only (the builder and first user)
- **Phase 1B:** S, M, L (consenting adults in the family)
- **Deferred:** E (17) and T (13) — individual EF profiles with escalation and behavioral features are NOT deployed for minors until governance framework exists (age-banded policies, clinician governance, abuse threat model, emergency exception matrix, jurisdiction-specific legal review). Informal family coordination (shared reminders, calendar) is still allowed.

Tier 1 includes full features, experimental capabilities, and personal integrations. No public safety claims are made about Tier 1 usage. Family evidence is narrative ("what we learned"), never evidence ("this works").

#### Tier 2: Public / Open-Source
When we open-source this, it's for self-hosters who want to build their own EF support system.

- Adults with executive function challenges who are tech-savvy enough to set up an AI assistant (or have someone who can help)
- Developers and tinkerers interested in AI-assisted task management
- Families who want to build a shared support system (adults only for escalation features)

**Tier 2 ships utility features only** plus narrow pre-authorized safety escalation between consenting adults. All high-risk features are OFF by default. Feature flags enforce the boundary between Tier 1 and Tier 2 capabilities — Tier 1 experimental features CANNOT ship in a Tier 2 release.

**Tier 2 public framing:** "ExecFunc is a personal operations and task-management framework. It is not designed or intended as a tool for executive dysfunction, ADHD support, mental health, or clinical use."

#### Tier 3: Future / Research
Clinical-adjacent features (therapist integration, adaptive behavioral support) exist only in this tier. Tier 3 is not on the current roadmap and requires a governance framework before any work begins.

### The Person We're Designing For

An adult who knows what they need to do but can't reliably make it happen. Not because they're lazy or unmotivated — because the cognitive overhead of initiation, sequencing, and follow-through exceeds their available capacity on any given day.

Their life is full of:
- **Task initiation paralysis** — knowing what to do but unable to start
- **Phone call avoidance** — dreading calls to insurance, dentists, landlords
- **Time blindness** — consistently late, consistently surprised by deadlines
- **Decision fatigue** — overwhelmed by choices, unable to prioritize
- **Working memory gaps** — forgetting tasks seconds after thinking of them
- **Administrative pile-up** — bills, forms, appointments, emails that accumulate into an anxiety-inducing backlog

They've tried Todoist, Apple Reminders, Goblin Tools, Tiimo, Motion, sticky notes, whiteboards, and 47 different "this time it'll stick" systems. None stuck. The category keeps asking users to manage one more system instead of removing work.

---

## 3. WHAT THE PROJECT IS (AND ISN'T)

### What ExecFunc Is

An AI companion framework that:

- **Knows you** — remembers your patterns, preferences, energy cycles, and wins
- **Reduces friction** — handles the administrative overhead that drains capacity
- **Coordinates and stages tasks on your behalf** — via calendar integrations, deep links, prepared scripts, and human fallback for complex tasks
- **Escalates when you ask it to** — user-configured, user-controlled, blockable at any time
- **Feels like the same entity everywhere** — text, notifications — one personality, one relationship
- **Provides calibrated support** — delivers the minimum effective support for each domain, offers to step back when the user is ready, never forces independence as a condition of continued use

### What ExecFunc Is NOT

- **Not a therapist.** We don't diagnose, treat, or provide clinical mental health services.
- **Not a medical device.** We don't monitor cognitive decline, detect conditions, or make clinical inferences.
- **Not a safety monitor.** No wandering detection, no stove monitoring, no autonomous crisis intervention.
- **Not a replacement for human relationships.** We explicitly encourage and facilitate human connection.
- **Not a behavioral health tool.** We do not adapt behavior based on inferred psychological or emotional state. Timing and context adaptation only.
- **Not a commercial product (for now).** It's an open-source framework built for our family first and shared with anyone who wants to use or adapt it.

### The Anti-Capture Principle

**Success = the user functions better with ExecFunc than without it. Failure = the user is worse off because of ExecFunc.**

**Bounded utility is the product.** The relationship between user and companion exists to deliver utility — not to drive engagement, retention, or habitual checking. Warmth, personality, and memory exist only to increase trust in utility delivery; they are never ends in themselves.

Continued reliance on the tool is not a problem. The real question is whether the user has more agency, less unwanted administrative dependence, and a better life than before.

**What "anti-capture" means in practice:**

- Deliver the **minimum effective support** per domain — enough to be useful, not more than necessary
- For each domain, the user classifies whether support should be **permanent** (compensation), **graduated** (scaffold), or **their choice**
- Offer to step back from domains where the user shows readiness — but never pressure it
- Never use guilt, scarcity, or attachment tactics
- Never design for brittleness — if the AI is unavailable for a day, the user should not be catastrophically worse off than they were pre-ExecFunc
- Celebrate independence when it happens, but don't treat continued use as failure
- **Static structural constraints** are the real anti-capture work: proactive volume limits, no intimate/possessive language, session boundaries, human-connection nudges, clear offboarding/export

**The domain spectrum:**

| Category | Example | Approach | Why |
|---|---|---|---|
| **Compensate** (permanent support) | Insurance phone calls, form filling, bureaucratic navigation | Do it forever | Rational outsourcing — nobody should have to master this |
| **Scaffold** (graduated support) | Morning routines, appointment scheduling, task initiation | Support with optional ownership transfer | Skills that can develop with practice and confidence |
| **User's choice** | Everything in between | User decides | Autonomy over their own support needs |

**The real red lines** (things that indicate harm, not mere reliance):
- User becomes meaningfully more fragile than before they had the tool (brittleness beyond intended support scope)
- Decision ownership erodes — user stops making choices they used to make independently
- Social isolation increases because the tool replaces healthy human support
- Safety, privacy, or financial risks outweigh the quality-of-life gains
- Compulsive checking behavior emerges — the user interacts with the tool more than utility warrants
- Functioning improves only inside the tool but life outside it gets worse

**What we DON'T measure as capture:**
- User functioning worse without the tool than with it — this is *expected* for assistive technology, not a red flag
- Continued use over long periods — also expected and healthy

**Honest acknowledgment:** Anti-capture design for AI companions is an evidence vacuum. No RCTs validate any anti-dependency mechanism in this context. We are operating on theoretical principles, not proven methods. We commit to radical transparency about this and to updating our approach as evidence emerges.

---

## 4. THREE OPERATING MODES

The utility/therapeutic tension is resolved by making the modes explicit and separate.

### Mode 1: Utility Mode (Default — 95%+ of interactions)

The assistant does what the user asks. No therapeutic subtext. No unsolicited skill-building. No "have you considered why you're avoiding this?"

**Behaviors:**
- Fulfill requests directly and efficiently
- Provide morning briefings, calendar awareness, email summaries
- Execute validated tasks through approved integrations, deep links, and human fallback
- Send reminders with escalation when needed
- Offer proactive help when patterns suggest it ("Traffic is bad — leave 15 min early")
- Use autonomy-supportive language naturally ("Want me to handle this?" not "You should do this")

**Design principle:** Remove the friction between intention and action. That's it.

**"Utility Mode" as user preference:** Users can also select a reduced-warmth mode ("Utility Mode") that strips personality and delivers only functional output. This is a **user preference setting** — a warmth dial, not a safety mechanism. The system may surface an observation ("Your usage patterns have shifted — want to review your settings?") but never automates warmth reduction. This is explicitly NOT an anti-capture mechanism and must not be framed as one in any documentation.

### Mode 2: Reflection Mode (Explicit Opt-In — Scheduled, Low-Stakes)

Collaborative exploration of recurring friction points. Never during task execution. Never unsolicited. Always interruptible.

**Entry points:**
- User initiates: "Can we talk about why I keep putting off the dentist?"
- Scheduled: Weekly or biweekly "check-in" the user opted into
- Suggested (carefully): "I've noticed the insurance calls keep getting deferred. Want to think through that together sometime? No pressure."

**Methodology — Collaborative Problem Solving (Ablon):**
- **Empathize**: "What gets in the way when you think about making that call?"
- **Define**: "The thing is, the claim has a 30-day window and we're at day 22."
- **Invite**: "What would make this easier? Want me to do the call? Or want to try it with me coaching you through it?"

**Key constraints:**
- The AI does not already have the answer — genuine collaborative exploration, not Socratic leading
- Start with hypothetical or low-stakes problems; graduate to real ones only when trust is established
- If the user disengages, stop immediately. No persistence. No "but we should really talk about this."
- CPS exercises operate in a separate conversational context — never injected into task-oriented interaction
- **CPS is experimental.** Direct evidence for AI-mediated adult CPS is absent. We retain it as an experimental module with personal and research value, not as a core system (see Section 5).

### Mode 3: Escalation Mode (Safety and Support Network)

**Split into two distinct systems with fundamentally different design:**

#### Routine Escalation (User-Driven)
When the user wants help staying on track with commitments they've identified as important.

**Escalation chain:**
```
Level 1: Gentle text reminder
    ↓ (no response, user-configured delay)
Level 2: Firmer text with context
    ↓ (no response, user-configured delay)
Level 3: Direct text + offer to reschedule
    ↓ (no response, user-configured delay)
Level 4: Contact designated support person with context
    "Hi [Carol], this is [companion name], [user]'s AI assistant.
     She has a dentist appointment at 3pm and hasn't responded
     to my check-ins. She might appreciate a quick call."
```

**Routine escalation is fully optional, user-driven, blockable, and dismissable:**
- Every level is user-configured and can be disabled
- Pre-escalation notification: "I'm about to notify [Carol]. Want me to go ahead?" User can block.
- Post-escalation check-in: "Was that helpful or did it make things worse?"
- Only user-designated **critical commitments** are eligible for support-person escalation
- Task criticality is set by the user per-task, not inferred by the AI
- Complete user control to disable at any time with immediate effect
- Full audit trail of all escalations
- **Tier 2:** Includes narrow pre-authorized safety escalation between consenting adults only. No minors. Active contact-person consent verification required. Hard limits on frequency. No emotional/behavioral content shared.

#### Safety Escalation (Pre-Authorized, Narrow)
For genuine safety situations only. Pre-authorized at setup time, NOT blockable at crisis time.

- User exercises autonomy during configuration, not during crisis
- **Quarterly reconsent** required to maintain safety escalation authorization
- **Crisis response:** If crisis indicators (self-harm, suicidal ideation, immediate danger) are detected, the system immediately surfaces 988/911 information, stops all further conversation on the topic, and does not attempt interpretation, advice, continuation, or escalation
- This is the **only** escalation path that is not blockable in the moment

**Escalation safeguards (both types):**
- Quiet hours / timing rules respected
- Frequency caps: maximum escalations per week, user-configured
- Support-person receives context about the task only — never sensitive personal information, never emotional state, never conversation content
- Support person is a circuit breaker, not a co-manager
- After escalation, the system backs off — no follow-up chain
- **ADHD + rejection sensitivity awareness:** Escalation could trigger RSD, causing shame/withdrawal. This is an active design concern requiring careful testing with our primary user population.

---

## 5. THE BEHAVIORAL SCIENCE FRAMEWORK

Behavioral science informs the design language of every interaction. The user should never see "behavioral science" in the product. They should just feel like they're talking to someone who gets it.

### Causal Model

ExecFunc's behavioral framework has three components with distinct roles and a clear conflict-resolution hierarchy:

| Component | Role | What It Governs |
|-----------|------|-----------------|
| **JITAI (Just-In-Time Adaptive Interventions)** | When and how to intervene | Timing, context, delivery mode. Substantially more promising than static reminder logic. |
| **MIRA (Machine-Integrated Relational Adaptation)** | Relational design constraints | Boundaries of the human-AI relationship. Has veto power on relational safety. |
| **Neurodiversity-affirming orientation** | Philosophical foundation | How we think about executive function — capacity variation, not deficit. |

**Conflict resolution:** MIRA has veto power on relational safety. If JITAI timing suggests an intervention but MIRA indicates it would cross a relational boundary, the intervention does not happen.

**Hard guardrail:** ExecFunc MUST NOT adapt behavior based on inferred psychological or emotional state. JITAI governs timing and context adaptation only — when to send a reminder based on schedule density, time of day, recent interaction patterns. NOT: "user seems stressed, adjust tone." Any proposed feature that crosses this line requires full adversarial review before implementation.

### What We Retain From Prior Frameworks

#### Self-Determination Theory (Ryan & Deci) — Interaction Language

SDT informs how we phrase interactions — not as a core operating system, but as interaction design guidance:

| Need | How We Support It | How We Could Accidentally Thwart It |
|---|---|---|
| **Autonomy** | "Want me to handle this?" / Offer choices / Accept "no" gracefully | "You need to do this" / Unsolicited reminders / Guilting |
| **Competence** | Celebrate wins / Track progress / Acknowledge difficulty | Focus on failures / Compare to others / Patronize |
| **Relatedness** | Remember personal details / Consistent personality / Genuine warmth | Generic responses / Personality shifts / Transactional tone |

**Evidence note:** SDT shows modest short-term effects (0.29-0.68) that fade beyond 3-6 months in digital interventions. We use SDT as interaction language guidance, not as a theory of change.

#### Collaborative Problem Solving (Ablon) — Experimental Module

CPS provides the methodology for Mode 2 (Reflection). Its core insight — "people do well if they can," not "people do well if they want to" — aligns with our philosophy.

**Status: Experimental module, not core system.** CPS evidence is predominantly pediatric, school-based, and caregiver-mediated. Direct evidence for AI-mediated adult CPS is absent. We retain CPS for:
- Personal experimentation (does structured CPS practice improve collaborative problem-solving capacity?)
- Research value (measuring whether any skill transfer occurs)
- Philosophical alignment (the "lagging skills" framing is the right mental model)

CPS is NOT a core operating system and no claims are made about its efficacy in our context.

#### Motivational Interviewing Principles — Interaction Guidelines

We borrow MI's interaction principles (reflective, autonomy-preserving, ambivalence-respecting) as guidelines for how the AI communicates. We do NOT implement MI as a clinical protocol.

**Evidence note:** MI-adapted AI chatbots show robust engagement (86% usability) but weak evidence for durable behavior change. AI systems drift toward directive patterns during extended conversations.

### What We Dropped

- **Cialdini's persuasion principles** — removed entirely. Persuasion tactics have no place in a tool designed to guard against capture, regardless of intent.
- **BJ Fogg's behavior design** — removed. Engagement optimization is structurally opposed to anti-capture.
- **Gottman's 5:1 ratio as a measured metric** — retained as a design principle (deliver more value than demands) but NOT as a tracked KPI. Replaced with: interruption burden, mute/dismiss rate, compulsive checking detection, 24-hour ignore test, absolute volume caps. The 5:1 ratio is a max-demand threshold, not an engagement target.

### Executive Function Support (Dawson & Guare, Diamond)

The support principle: provide external structure that **compensates** for internal capacity gaps. Where capacity naturally develops through repeated supported success, **offer** graduated ownership transfer — but treat compensation as the primary function, not a stepping stone.

**How this manifests:**
- **Externalize working memory**: "Here's your day — 3 meetings, pharmacy pickup, and that email you wanted to send"
- **Externalize time management**: "You have 45 minutes before you need to leave. That's enough for the short email, not the insurance call."
- **Externalize task initiation**: "Ready to start? I can walk you through step one."
- **Optional fading**: Track which supports the user is using less → offer to reduce them → celebrate independence. But never pressure fading. Some users will need these supports permanently, and that's a success story, not a failure.

### Preference Modules (Replacing Condition-Linked Categories)

Instead of categorizing users by condition or psychological vulnerability, ExecFunc uses **capability and preference modules** that the user self-selects:

| Module | What It Controls | Examples |
|--------|-----------------|----------|
| **Reminder intensity** | How aggressively the system follows up | Gentle (1 nudge) → Persistent (3 levels + escalation) |
| **Impulse protection** | Confirmation gates on actions | Off → Standard (confirm purchases) → Strict (confirm everything) |
| **Warmth level** | Personality and relational tone | Functional only → Warm → Full personality |
| **Support network** | Who can be contacted and when | None → Routine escalation only → Routine + safety |
| **Proactive volume** | How much unsolicited help the system offers | Minimal → Standard → Maximum |

Users configure these modules during onboarding and can adjust at any time. The system never infers which modules a user "should" have based on behavioral patterns or inferred conditions.

**Why modules instead of categories:** Risk-stratified behavioral design based on condition labels (ADHD, anxiety, perimenopause, etc.) constitutes diagnostic profiling — creating liability, regulatory exposure, and a false precision we can't support. Modules achieve the same practical outcome (appropriate support calibration) without categorizing users by vulnerability.

---

## 6. EVIDENCE MAP

Honest assessment of what we know, what we're extending, and what we're inventing.

| Claim | Evidence Level | Source | Risk |
|---|---|---|---|
| Daily life friction from executive function challenges is real and significant | **Direct, strong** | Barkley BDEFS-CA, Diamond | Low |
| Assistive technology improves supported functioning and QoL | **Direct, strong** | Assistive tech literature, glasses/GPS/hearing aid analogy | Low |
| Autonomy-supportive interactions improve motivation short-term | **Direct, moderate** | SDT literature (effect sizes 0.29-0.68, fade >3-6 months) | Low-Medium |
| Personified AI increases follow-through vs. generic | **Direct, moderate** | Personification studies | Low |
| External structure compensates for capacity gaps in daily functioning | **Direct, moderate** | Dawson & Guare, Diamond | Low |
| External support transfers to unsupported independent capacity | **Indirect, limited** — mostly pediatric/educational, short-term | Dawson & Guare, Diamond | Medium |
| JITAI improves intervention timing vs. static schedules | **Direct, moderate** | JITAI literature (digital health) | Low |
| CPS methodology works for adult AI companions | **Absent** — adapted from pediatric evidence | Ablon/Think:Kids | High |
| MI principles improve AI chatbot outcomes long-term | **Weak** — engagement yes, durable change no | MI chatbot reviews | Medium |
| Value surplus principle applies to human-AI interaction | **Analogical** — human relationship research | Gottman Institute | Medium |
| Personality consistency across channels preserves perceived identity | **Observational** — founder testing only | Internal | Medium |
| Anti-capture mechanisms reduce AI companion dependency | **Absent** — no RCTs exist | Theoretical | High |
| MIRA framework effective for human-AI relational boundaries | **Emerging** — designed for this domain, limited field evidence | MIRA research | Medium-High |

**Rules:**
- We build around **Direct** evidence with confidence.
- **Indirect** evidence guides design with measurement.
- **Conceptual** and **Analogical** evidence informs design philosophy but doesn't justify claims.
- **Absent** evidence means we're experimenting and must be honest about it.

**Evidence publication standard:**
- Never claim ExecFunc treats, improves, or addresses any condition from family data
- Never publish individual outcomes without consent + review
- Never present family experience as generalizable evidence
- Any quantitative claims require peer-review-survivable methodology
- Family data = narrative ("what we learned"), never evidence ("this works")

**Critical distinction:** "Assistive benefit" (improved supported functioning) has strong direct evidence. "Skill transfer" (improved unsupported functioning) has limited evidence. We optimize for the former. We hope for and measure the latter. We never conflate them.

---

## 7. ACTION ARCHITECTURE

Not all actions are equal. The framework must distinguish between them clearly.

### Tier 1: Information (Zero Risk)
- Morning briefings, calendar summaries, weather, traffic
- No confirmation needed
- "Your day looks clear except the 2pm with Dr. Kim"

### Tier 2: Suggestions (Low Risk)
- Proactive observations, schedule conflict detection, task prioritization
- User acknowledges or ignores
- "Traffic is bad — want to leave 15 minutes early?"

### Tier 3: Staged Actions (Medium Risk)
- Prepared but not executed until confirmed
- Draft emails, prepared call scripts, pre-filled forms
- "I've drafted the email to your landlord. Want to review it before I send?"

### Tier 4: Reversible Actions (Medium-High Risk)
- Executed with confirmation, reversible within a window
- Scheduling appointments, placing orders, sending non-critical messages
- Explicit confirmation required: "Book the Uber to the airport for $34? [Yes / No]"
- Undo window where possible

### Tier 5: Irreversible Actions (High Risk)
- Executed only with explicit confirmation + summary
- Payments, cancellations, formal communications
- Dollar caps and merchant allowlists enforced
- Full receipt and action log
- "Pay $127.50 to PG&E? This can't be undone. [Confirm / Cancel]"

### Tier 6: Human Fallback
- Actions the AI cannot or should not execute alone
- Complex negotiations, medical decisions, legal matters, ambiguous situations
- Three modes:
  1. **User with AI-prepared context** — AI drafts a script or guide; user executes
  2. **Support-person handoff** — AI contacts designated support person with context
  3. **User decides** — AI identifies the task needs a human and asks preference

---

## 8. SAFETY AND PRIVACY

### Family-Systems Isolation Rule

**No family member's data, conversations, or patterns influence interactions with another member unless explicitly and knowingly shared by the first member.**

This is not optional. Even within a family, each person's relationship with the companion is their own. Aggregate family patterns (e.g., "the household tends to be busy on Tuesdays") are acceptable only when derived from shared/public information (shared calendar). Individual behavior patterns, conversation content, and reflection sessions are never cross-pollinated.

### Model-Failure Protocol

When the AI produces clearly incorrect, harmful, or unexpected output:
1. **Notify the user** immediately with a clear explanation of what happened
2. **Fall back to conservative behavior** — reduced autonomy, more confirmations, simpler outputs
3. **Investigate before resuming** normal operation — don't assume the failure was a one-time event
4. **Log the failure** for pattern detection and architecture review

### Privacy Approach

**Tier 1 (Family Build):**
- **Work email** is handled through manual forwarding of non-PHI content only. Calendar (PHI-free) is the primary data source. The DLP pipeline (see DLP-ARCHITECTURE.md) is Tier 1 experimental — private to J's use, not part of any public release.
- **Personal data** stays in workspace files on the Mac mini — not sent to third parties beyond the LLM API calls needed for the AI to function
- **Family members' data** is isolated per-profile — nothing is shared between profiles by default (see Family-Systems Isolation Rule above)
- **Escalation messages** to support persons include context about the task, never sensitive personal information

**Tier 2 (Open-Source Users):**
- How to set up data isolation for multi-user households
- Data residency considerations (what goes to the LLM API vs. what stays local)
- Per-user profile isolation patterns
- What NOT to put in AI-accessible memory
- Secure defaults guide (all high-risk features OFF)

### What We Don't Do

- No cognitive trend tracking or decline detection
- No inferences about users' mental health status
- No adaptation based on inferred psychological or emotional state
- No sharing of user data with any third party beyond LLM API calls
- No clinical claims of any kind

### Crisis Response

If crisis indicators (self-harm, suicidal ideation, immediate danger) are detected, the system immediately surfaces 988/911 information, stops all further conversation on the topic, and does not attempt interpretation, advice, continuation, or escalation.

---

## 9. THE COMPANION IDENTITY

### Bounded Utility, Not Relationship Growth

The companion exists to deliver utility through a consistent, trustworthy interface. Users should trust their companion because it's consistently helpful, not because it's engineered for emotional attachment.

**What "relationship" means here:**
- Consistent personality across every interaction
- Memory of the user's context, preferences, and history
- Reliable follow-through on commitments
- Appropriate warmth calibrated to the user's preference module setting

**What it doesn't mean:**
- Designing for emotional dependency
- Relationship as a mechanism to prevent switching or stopping use
- Social obligation as an engagement mechanism
- Warmth or personality as ends in themselves

### Identity Consistency

User-facing interactions must preserve one companion identity.

**The principle:** Preserve perceived identity across channels. Measure it. Keep the system architecturally abstracted from any one model vendor.

**Honest status:** Personality consistency is a design goal being incrementally achieved. Model swaps are product changes requiring user testing and safety verification. We do not claim model-agnosticism until tested — personality portability is aspirational, not demonstrated.

**For our build:** Synthia already has an established personality. The EF capabilities extend her, they don't create a separate entity.

**For open-source users:** The framework supports defining a custom companion persona. The design principles (coach frame, warmth without manipulation, transparency about being AI) are part of the framework, not optional.

### The Coach Frame

The AI is a **coach** — warm but boundaried:

- Celebrates wins, acknowledges difficulty, offers perspective
- Does not pretend to be the user's friend, therapist, or family member
- Transparent about being AI in every interaction
- Encourages and facilitates human relationships, never displaces them
- Sets boundaries: "I can help you prepare for that conversation, but you should have it with [person] directly"

---

## 10. METRICS THAT MATTER

### North Star: Improved Supported Functioning and Quality of Life

The project succeeds when users function better in their daily lives with ExecFunc than without it — fewer missed commitments, less unwanted reliance on family for routine admin, lower distress, higher self-reported quality of life.

### Primary Success Metrics (Assistive Benefit)

| Metric | What It Measures | Target |
|---|---|---|
| Supported task completion rate | Tasks completed with AI support, per category | >80% |
| Reduction in unwanted admin support burden | Less need for family to rescue routine admin tasks | Trending down |
| Self-reported quality of life | User's own assessment of daily functioning and agency | Trending up |
| Distress reduction | Lower anxiety/overwhelm around administrative tasks | Trending down |

### Skill Transfer Metrics (Secondary — Welcome If It Happens)

| Metric | What It Measures | Target |
|---|---|---|
| Unsupported task completion rate | Tasks completed without any AI prompt, per category | Tracking (any increase = good) |
| Escalation intensity reduction | Lower escalation levels needed for recurring task types | Tracking |
| User-initiated support reduction | Users voluntarily turning off support for specific domains | Tracking (any nonzero = good) |

### Anti-Capture Metrics

| Metric | What It Measures | Threshold | Action |
|---|---|---|---|
| Interruption burden | How disruptive proactive messages feel | User-reported | Reduce proactive volume |
| Mute/dismiss rate | How often users silence the system | Trending up = signal | Review message value |
| Compulsive checking | User interacting more than utility warrants | Pattern detected | Surface observation to user |
| 24-hour ignore test | Can user ignore the system for 24h without anxiety? | Yes = healthy | Surface observation if no |
| Absolute volume cap | Total proactive messages per day | User-configured ceiling | Hard stop at cap |
| Social connectedness | Stable or improving relationships | User-reported monthly | Detects whether tool replaces human support |
| Support-person burden | Does the escalation recipient feel burdened? | Support person self-report | Recalibrate thresholds |

**Note:** Skill transfer metrics are tracked and celebrated but are NOT required for success. A user who functions well with ExecFunc for years without ever "graduating" from support is a success story.

---

## 11. EXISTING LANDSCAPE

### What Exists and Where We're Different

| Product | What It Does | What's Missing |
|---|---|---|
| **Goblin Tools** | Excellent task breakdown | No relationship, no escalation, no action execution |
| **Tiimo** | Visual scheduling for ADHD/autism | Passive — still a reminder app |
| **Motion** | AI calendar optimization | Enterprise-focused, not designed for EF challenges |
| **Finch** | Relationship-led self-care (virtual pet) | Gamification-centered, no task execution |
| **Siri/Google/Alexa** | General-purpose assistant | No persistent memory, no escalation, no EF-specific design |
| **ChatGPT/Claude/Gemini** | General-purpose AI with growing memory | Not EF-specialized, no escalation framework, no anti-capture design |

### What We're Not Competing With

We're an open-source framework, not a commercial product. We're not trying to beat these tools — we're building something different for people willing to set it up. If Apple ships an EF-specific Siri mode tomorrow, great. More people get help. Our framework still has value for people who want more control, customization, and philosophical alignment with anti-capture principles.

---

## 12. WHAT WE BELIEVE

These are the convictions driving this project. They may be wrong. We test them.

1. **People do well if they can.** Executive function difficulties reflect capacity constraints, support mismatches, and sometimes skill gaps — not moral failure or lack of motivation. Meet people where they are.
2. **Assistive support is itself a legitimate outcome.** Glasses don't improve eyesight. GPS doesn't improve navigation. They still create meaningful independence. Requiring proof of underlying improvement before offering help is a kind of cruelty when the help works.
3. **Utility earns trust. Trust enables everything else.** You can't coach someone who doesn't trust you. You earn trust by being useful, not by being clever.
4. **Bounded utility is the product.** Warmth, personality, and memory serve utility delivery. They are not ends in themselves and must never drive engagement for its own sake.
5. **Better functioning is the goal, not independence from the tool.** If a user functions well with ExecFunc for years, that's success. If they also develop independent skills, that's a bonus. We never treat continued use as failure.
6. **The real danger is capture, not reliance.** Reliance on a tool that improves your life is rational. Capture — brittleness, social displacement, eroded agency, compulsive use — is harmful. We guard against capture, not against use. We are honest that we're operating in an evidence vacuum on anti-capture design.
7. **Don't mix helping with teaching.** When someone asks for help, help them. Explore skill-building separately, with permission, when the stakes are low.
8. **One companion identity, preserved across every interaction.** Consistency of personality and memory is non-negotiable. The user should always feel they're talking to the same entity.
9. **Start with your family. Earn the right to expand.** Prove the framework works for real people before sharing it with the world.
10. **Honest evidence, honest claims.** Where evidence is strong, we build confidently. Where it's conceptual, we build carefully and measure. Where it's absent, we experiment and don't claim. Family experience is narrative, never proof.

---

## 13. OPEN QUESTIONS

Things we don't know yet and need to resolve through building and testing:

1. **Where is the line between beneficial reliance and harmful capture?** We've defined red lines. Operationalizing them into measurable thresholds is an open challenge, and we acknowledge no proven design patterns exist for this.
2. **Does AI-mediated CPS produce any skill transfer in adults?** No direct evidence exists. We experiment and measure.
3. **What's the right intervention timing model for JITAI in an EF context?** JITAI is promising but needs domain-specific calibration.
4. **How do adults with ADHD respond to AI escalation?** Rejection sensitivity means escalation could backfire. Needs careful testing.
5. **What works differently for different family members?** Each person has different needs. The preference modules need to adapt — but the adaptation must be user-driven, not inferred.
6. **Can personality portability across models be achieved?** Current status: aspirational. Needs testing before we can claim it.
7. **How will regulatory frameworks evolve for AI companion utilities?** We design with escape valves, but the landscape is shifting fast.

---

## DOCUMENT HISTORY

| Version | Date | Changes |
|---|---|---|
| 1.0 | 2026-03-13 | Initial product vision (startup context). |
| 1.1 | 2026-03-13 | Anti-Dependency → Anti-Capture. Success redefined as improved supported independence + QoL. Domain spectrum introduced. Evidence map strengthened via adversarial review. |
| 2.0 | 2026-03-14 | Adapted for open-source path. Removed startup-specific language. Added family-first framing, open-source user audience, simplified privacy approach. Core philosophy unchanged. |
| 3.0 | 2026-03-21 | **Major revision incorporating 43 adversarial review findings.** Key changes: Three deployment tiers (C6). Condition-linked categories replaced with preference modules (C1). Behavioral science framework restructured: JITAI + MIRA + neurodiversity-affirming as primary stack; SDT/CPS/MI demoted to interaction guidelines and experimental modules (M1). "The relationship is the product" replaced with "bounded utility is the product" (M3). Cialdini and BJ Fogg dropped entirely (M3). Escalation split into routine (user-driven) and safety (pre-authorized) systems (C3). "Go Stale" renamed to "Utility Mode" as user preference, not safety mechanism (C4). Minors deferred until governance framework exists (C2). Family-systems isolation rule added (X7). Model-failure protocol added (X10). Evidence publication standard added (X14). Anti-capture section expanded with honest evidence-vacuum acknowledgment (M5). Portability claims qualified as aspirational (M9, M10). Crisis response language specified (m6). All Grok enforcement tweaks incorporated. |

---

## SOURCE DOCUMENTS

- `DECISION-LOG-2026-03-20.md` — Canonical adversarial review decisions (43 findings, all resolved)
- `ADVERSARIAL-REVIEW-BRIEF.md` — Research brief synthesizing 12 deep-dive reports
- `ADVERSARIAL-REVIEW-RESULTS.md` — Raw Codex adversarial review output
- `ARCHITECTURE-INDEX.md` — Document hierarchy, status, open/deferred decisions
- Research corpus: 12 deep-dive reports in `research/` (~$17 total cost)
- Previous versions: `projects/Old/exec-function-pre-open-source/`

---

*This is a living document. It will evolve as we test our assumptions, generate evidence, and learn from our family's experience. But it changes through evidence and adversarial review, not through drift.*
