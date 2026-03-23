# ExecFunc — Adversarial Review Decision Log
## All Decisions Locked March 20, 2026

*This log captures every decision from the adversarial review triage (Passes 1-3). Use this as the canonical reference for the comprehensive document revision.*

---

## CRITICAL DECISIONS (7)

### C1: Wellness vs Clinical Architecture
**Decision:** Accept with modification
- Replace condition-linked categories with capability/preference modules (reminder intensity, impulse protection, warmth level, support network preferences)
- JITAI for timing/context only — NOT autonomous clinical intervention
- MIRA informs design constraints, not runtime adaptation
- Neurodiversity-affirming as philosophical orientation, not clinical methodology
- **Hard guardrail (Grok tweak):** "ExecFunc MUST NOT adapt behavior based on inferred psychological or emotional state. Timing and context adaptation only. Any proposed feature that crosses this line requires full adversarial review before implementation." Add to architecture index + code-review checklist.

### C2: Minors Architecture Unsafe
**Decision:** Accept
- Phase 1: J only
- Phase 1B: S, M (consenting adults). L (19, legally adult) with appropriate consent.
- E (17) and T (13): DEFERRED until governance framework exists (age-banded policies, clinician governance, abuse threat model, emergency exception matrix, jurisdiction-specific legal review)
- Informal family coordination (reminders, shared calendar) still allowed
- Individual EF profiles with escalation/behavioral features for minors: NOT until adult architecture proven + additional governance built

### C3: Escalation Paradox
**Decision:** Accept
- **Split into two systems:**
  - **Routine escalation:** Optional, user-driven, blockable, dismissable. Pre-escalation notification works here. Covers 95%+ of use cases.
  - **Safety escalation:** Narrow, pre-authorized at setup time, NOT blockable at crisis time. User exercises autonomy during configuration, not during crisis. Quarterly reconsent.
- **Tier 2 (public release):** Includes narrow pre-authorized safety escalation between consenting adults, with: mandatory onboarding explanation, active contact-person consent verification, hard limits on frequency, no emotional/behavioral content shared, no minors.

### C4: "Go Stale" Dangerous
**Decision:** Accept with modification
- Renamed to **"Utility Mode"** — user-selectable preference, NOT automated safety mechanism
- **Never automated.** System can surface observation; user decides.
- Gradual warmth dial, not binary switch
- **Static constraints are the real anti-capture work:** proactive volume limits, no intimate/possessive language, session boundaries, human-connection nudges, clear offboarding/export
- **Grok tweak:** Use neutral name ("Utility Mode") and explicitly document in architecture index + user settings that this is NOT an anti-capture safety mechanism — purely user preference. Prevents regulator/reviewer misinterpretation.

### C5: Security Posture Split
**Decision:** Accept
- One canonical current-state deployment boundary
- SECURITY-ARCHITECTURE.md relabeled as "FUTURE VISION"
- Public docs (README, OPEN-SOURCE-PATH) reflect only current-state capabilities
- **Rule:** No document may advertise access or protections that don't exist in the implementation

### C6: Family ≠ Open-Source
**Decision:** Accept with modification
- **Three deployment tiers, one codebase:**
  - **Tier 1 (Family/Private):** Full features, experimental capabilities, personal integrations. No public safety claims.
  - **Tier 2 (Public/Open-Source):** Utility features only + narrow pre-authorized safety escalation between consenting adults. Conservative defaults. All high-risk features OFF by default.
  - **Tier 3 (Future/Research):** Clinical-adjacent features (therapist integration, adaptive behavioral support). Only with governance framework.
- Open-source release = Tier 2 only
- Family evidence = "what we learned" not "proof it works for you"
- **Grok tweaks:**
  - Feature flags + automated tests so Tier 1 capabilities CANNOT ship in Tier 2
  - Tier 2 public messaging: "This is a personal operations utility framework, not an emotional companion or behavioral support system."

### C7: No Harm-Containment Plan
**Decision:** Accept (stop-ship item)
- Before any broader deployment, define:
  1. Adverse-event taxonomy
  2. Harm thresholds (specific, measurable)
  3. Response protocol (graduated: surface observation → recommend changes → feature restriction → offboarding support)
  4. Offboarding/export flow (clean exit, no guilt, no friction)
  5. Who decides (family: J. Open-source: user, with system observations)

---

## MAJOR DECISIONS (16)

### M1: No causal model for behavioral pivot
**Decision:** Accept
- Produce one-page causal model: JITAI = when/how, MIRA = relational design constraints, Neurodiversity-affirming = philosophical orientation
- Conflict resolution: MIRA has veto power on relational safety

### M2: Risk categories are diagnostic profiling
**Decision:** Resolved by C1 (preference modules replace condition labels)

### M3: Engagement optimization undermines anti-capture
**Decision:** Accept with modification
- Drop Cialdini and BJ Fogg entirely
- Reframe Gottman 5:1 as max-demand threshold, not engagement target
- Replace "the relationship is the product" with "bounded utility is the product"
- **Grok tweak:** Add to interaction model + architecture index: "Warmth, personality, and memory exist only to increase trust in utility delivery; they are never ends in themselves and are not permitted to drive engagement, retention, or habitual checking."

### M4: Value surplus ratio gameable
**Decision:** Accept
- Replace message-count ratio with: interruption burden, mute/dismiss rate, compulsive checking detection, 24-hour ignore test, absolute volume caps
- 5:1 stays as design principle, not measured metric

### M5: Anti-capture confuses accommodation with capture
**Decision:** Accept
- Measure right harms: social isolation, compulsive checking, decision-ownership narrowing, inability to stop by choice, relationship damage
- DON'T measure: whether user functions worse without tool (expected for assistive tech)
- Brittleness testing reframed: testing for catastrophic fragility beyond intended support, not testing for dependence

### M6: Tiered autonomy not user-compatible
**Decision:** Accept
- Max review burden for non-founder users (2-3 approval decisions/day)
- Conservative automation defaults with minimal review required
- Heavy-review mode opt-in for power users
- Simple one-tap approve/reject for confirmations

### M7: Designed for Obsolescence overbuilt
**Decision:** Accept with modification
- Trigger-based reviews instead of calendar-based at current scale
- **Grok tweak:** Comprehensive health check every 18-24 months (not annual). Quarterly cadence explicitly labeled "scaled-operations goal only."

### M8: Security plan ignores operational fit
**Decision:** Accept
- Tier 1: Lightweight (OS keychain, file-based logs, manual token rotation)
- Tier 2: Security docs + secure-defaults guide, no enterprise tools required
- Tier 3: Enterprise security evaluated only if commercial deployment is real
- Stop referencing enterprise products as current architecture

### M9: Personality portability undemonstrated
**Decision:** Accept
- Model swaps are product changes requiring user testing + safety verification
- Personality portability = design goal being incrementally achieved, not current capability
- Don't claim model-agnosticism until tested

### M10: Platform portability wishful
**Decision:** Accept with modification
- Acknowledge OpenClaw dependency explicitly
- New ExecFunc skills: separate logic from OpenClaw integration
- Don't retroactively refactor existing work
- **Grok tweak:** "Portability is not claimed in public documentation or Tier 2 release materials until migration has been demonstrated on at least one component."

### M11: Therapist integration is operating model
**Decision:** Resolved by C2 + C6 (deferred to Tier 3)

### M12: DLP roadmap confused
**Decision:** Accept
- No healthcare email integration for Tier 2 (public release)
- J's private DLP pipeline stays private and explicitly experimental (Tier 1)
- Don't invest in Stages 1-3/5-8 unless project goes commercial
- Build-vs-buy reassessed only if healthcare integration becomes unavoidable

### M13: Naming clinically suggestive
**Decision:** Accept with modification
- Tier 2 public: Frame as personal operations and daily task management
- Tier 1 private + newsletter: Open EF/ADHD/neurodiversity discussion
- Name "ExecFunc" retained (ambiguous enough)
- **Grok tweak:** Prominent disclaimer in all Tier 2 docs/README: "ExecFunc is a personal operations and task-management framework. It is not designed or intended as a tool for executive dysfunction, ADHD support, mental health, or clinical use."

### M14: Measurement too weak for claims
**Decision:** Accept
- Family data = narrative ("what we learned"), never evidence ("this works")
- Never claim "ExecFunc improves executive function" from family data
- Stronger claims require proper methodology (baselines, adverse-event logging, external review)

### M15: Integration over-assumes standards
**Decision:** Accept
- Prove on concrete end-to-end integrations first (calendar, Telegram, one healthcare read path)
- Don't generalize integration architecture until proven on real integrations

### M16: Solo-launch plan not credible
**Decision:** Accept
- Ruthless sequencing:
  1. Build narrow adult utility loop for J
  2. Expand to S, M, L (consenting adults)
  3. Add tests + docs sufficient for Tier 2
  4. Open-source Tier 2 with conservative scope
  5. Defer: community building, newsletter ExecFunc content, quarterly reviews, Tier 3
- Each phase completes before next begins

---

## MINOR DECISIONS (6)

### m1: Reconsent cadence arbitrary
**Decision:** Accept — event-triggered + quarterly fallback maximum

### m2: "Stale mode" poor name
**Decision:** Resolved by C4 — "Utility Mode"

### m3: High proactive volume normalized
**Decision:** Resolved by M4 — volume caps + interruption burden

### m4: Version-skew between docs
**Decision:** Accept with modification
- Create ARCHITECTURE-INDEX.md as single source of truth
- Superseded docs get header stamp
- **Grok tweak:** Add "Open / Deferred Decisions" section to prevent items falling through cracks

### m5: Governance signals too mature
**Decision:** Accept — scale back public governance posture until Tier 2 is stable

### m6: Crisis language under-specified
**Decision:** Accept with modification
- **Grok tweak (strengthened wording):** "If crisis indicators (self-harm, suicidal ideation, immediate danger) are detected, the system immediately surfaces 988/911 information, stops all further conversation on the topic, and does not attempt interpretation, advice, continuation, or escalation."

---

## MISSING AREA DECISIONS (14)

### X1: Exclusion criteria
**Decision:** Accept — define before Tier 2. Not for active crisis, clinical treatment, minors, or substitute for professional care.

### X2: Abuse/coercion threat model
**Decision:** Accept with modification — before Tier 2
- Instant revoke, narrow info sharing, detect external control
- **Grok tweak:** "Support-person escalation access can only be configured by the primary user during an authenticated session. No proxy setup allowed, and no memory/conversation history from one user ever influences another user's profile unless explicitly and knowingly shared by the first user."

### X3: Adverse-event taxonomy
**Decision:** Accept — before Tier 2 (part of C7 deliverables)

### X4: Stop-ship criteria
**Decision:** Accept — before Tier 2 (part of C7 deliverables)

### X5: Offboarding/export plan
**Decision:** Accept — before Tier 2. Clean exit, data export, no guilt, no friction.

### X6: Consent-comprehension design
**Decision:** Accept with modification — Tier 2 design phase
- Short, simple, plain language consent flows
- **Grok tweak:** For high-risk features, add "explain-back": "In your own words, tell me what you are enabling and what risks are involved."

### X7: Family-systems risk model
**Decision:** Accept — NOW (Tier 1). Explicit rule: no family member's data/conversations/patterns influence interactions with another unless explicitly shared.

### X8: Support-person operating model
**Decision:** Accept — before Tier 2. Clear explanation, active consent verification, opt-out, burden cap, zero obligation.

### X9: External oversight plan
**Decision:** Accept with modification — before Tier 2
- Current: adversarial review via Codex
- Future: advisory reviewer for safety-critical decisions
- **Grok tweak:** Make it recurring: "Adversarial safety review by an external party before every major release or when adding any new high-risk capability."

### X10: Model-failure protocol
**Decision:** Accept — NOW (Tier 1). Notify user, fall back to conservative behavior, investigate before resuming.

### X11: Jurisdiction-gating strategy
**Decision:** Accept — before Tier 2. Document restrictive jurisdictions, warn users, don't require geo-blocking.

### X12: Secure defaults for self-hosters
**Decision:** Accept — before Tier 2. All high-risk features OFF by default. Feature flags enforce (per C6).

### X13: Prompt-injection threat model
**Decision:** Accept with modification — before Tier 2
- **Grok tweak:** Treat as both documentation AND implementation: input sanitization + prompt-hardening on all user-submitted content before model processing. Document threat model AND apply technical controls.

### X14: Evidence publication standard
**Decision:** Accept — NOW (incorporate into doc revision)
- Never claim ExecFunc treats/improves/addresses ADHD from family data
- Never publish individual outcomes without consent + review
- Never present family experience as generalizable evidence
- Any quantitative claims require peer-review-survivable methodology

---

## IMMEDIATE ACTION ITEMS (for doc revision)

### Do NOW (before/during doc revision):
1. ☐ X7: Add family-systems isolation rule to safety docs
2. ☐ X10: Add model-failure protocol
3. ☐ X14: Add evidence publication standard
4. ☐ m4: Create ARCHITECTURE-INDEX.md with Open/Deferred section
5. ☐ Comprehensive document revision incorporating all 43 decisions

### Do BEFORE TIER 2 RELEASE:
6. ☐ X1: Exclusion criteria
7. ☐ X2: Abuse/coercion threat model
8. ☐ C7: Harm-containment plan (X3 adverse taxonomy + X4 stop-ship + X5 offboarding)
9. ☐ X6: Consent-comprehension design
10. ☐ X8: Support-person operating model
11. ☐ X9: Recurring external oversight process
12. ☐ X11: Jurisdiction-gating documentation
13. ☐ X12: Secure defaults + feature flags
14. ☐ X13: Prompt-injection threat model + technical controls

---

## STATS

- **Total findings reviewed:** 43
- **Accepted as-is:** 27
- **Accepted with modification:** 14
- **Resolved by prior decisions:** 2
- **Pushed back:** 0
- **Research corpus:** 12 exhaustive deep-dive reports (~$17 total)
- **Adversarial review model:** Codex GPT (100K tokens consumed)
- **External validation:** Grok (all 3 passes)
- **Review duration:** ~15 hours (7:22 AM – 10:12 PM PST)
- **Total session cost (research + review):** ~$20

---

*This decision log is the canonical reference for the document revision. Every decision here is locked unless reopened through a new adversarial review.*
