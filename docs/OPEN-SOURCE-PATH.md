# ExecFunc — Open Source Path
## Building an AI Executive Function Companion for Family First, Then the World

### Version 2.0 — March 21, 2026

*Revised from v1.0 (March 14, 2026) incorporating adversarial review decisions (C2, C6, M6, M16, m5, X12). See DECISION-LOG-2026-03-20.md for the canonical decision record.*

---

## 1. WHY THIS PATH

### The Honest Assessment

J is a practicing health care provider with a family and a genuine belief that AI can meaningfully improve executive function for people who struggle with it. The startup path — fundraising, hiring, regulatory counsel, board meetings — is a commitment that competes with a career, a family, and a life.

The open-source path lets us:

- **Build the thing we actually want to build** — a working EF companion for J's family
- **Test every hypothesis in the Product Vision** with real people we know and care about
- **Share what we learn** without the obligations of a commercial product
- **Preserve the option** to pivot to a startup later if the evidence is compelling and the timing is right

### What We Keep From the Startup Plan

Everything in the **[Product Vision v3.0](PRODUCT-VISION.md)** still applies:
- The core insight (assistive support is a legitimate outcome)
- The three operating modes (Utility, Reflection, Escalation)
- The behavioral science framework (JITAI, MIRA, neurodiversity-affirming orientation)
- The anti-capture design principles
- The evidence map and honest evidence standards
- The action architecture (tiered risk levels)
- The identity consistency architecture
- The escalation framework (routine + safety, split design)

What changes is the **vehicle**, not the **vision**.

### What We Drop

- Fundraising, investor relations, board governance
- Hiring a team (it's J + Synthia + open-source contributors)
- Regulatory counsel for commercial launch (we're not selling a health product)
- Revenue model, pricing tiers, unit economics
- Go-to-market strategy, CAC, LTV
- Enterprise/clinical expansion roadmap
- HIPAA compliance, SOC 2, FDA pathway
- The pressure to scale before the product actually works

---

## 2. THREE DEPLOYMENT TIERS

All features, documentation, and claims must be explicit about which tier they belong to. See Product Vision v3.0, Section 2 for full tier definitions.

| Tier | Scope | Users | What Ships |
|------|-------|-------|------------|
| **Tier 1 (Family/Private)** | Full features, experimental capabilities, personal integrations | J → S, M, L (consenting adults). E and T deferred. | No public safety claims. |
| **Tier 2 (Public/Open-Source)** | Utility features only + narrow safety escalation between consenting adults | Self-hosters | Conservative defaults. All high-risk features OFF by default. |
| **Tier 3 (Future/Research)** | Clinical-adjacent features | Only with governance framework | Not on current roadmap. |

**Feature flag enforcement (C6):** Tier 1 experimental capabilities CANNOT ship in a Tier 2 release. Automated tests verify the boundary.

**Tier 2 public messaging:** "ExecFunc is a personal operations and task-management framework. It is not designed or intended as a tool for executive dysfunction, ADHD support, mental health, or clinical use."

---

## 3. THE PLAN

### Phase 1: Build It for J (Months 1-3)

**The goal:** A working AI EF companion running on OpenClaw that demonstrably helps J with daily executive function challenges.

**User: J only.** This is the builder and first user. Experiencing your own product is the most honest feedback loop.

**What we build (on OpenClaw):**

1. **Personified AI companion** — Synthia already exists. Extend her with EF-specific capabilities:
   - Proactive friction detection ("You have 3 things due this week and haven't started any — want to pick one?")
   - Morning briefings tailored to J's context
   - Calendar awareness with conflict detection
   - Task management with voice input

2. **Escalating text reminders** — Levels 1-3 via Telegram:
   - Gentle → firmer → direct + offer to reschedule
   - User-configured per-task criticality
   - Quiet hours, frequency caps, volume ceilings

3. **Task execution** — Using tools we already have:
   - Calendar integration (gog CLI for Google Calendar)
   - Reminder integration (Apple Reminders via remindctl)
   - Email awareness (manual forwarding of non-PHI emails; calendar is primary data source)
   - Deep links to apps

4. **Anti-capture measurement from day one:**
   - Track supported task completion
   - Monitor interruption burden and dismiss rates
   - Watch for compulsive checking patterns
   - 24-hour ignore test periodically

5. **Preference modules configured** — reminder intensity, impulse protection, warmth level, support network, proactive volume (see Product Vision Section 5)

### Phase 1B: Expand to Consenting Adults (Months 3-6)

**Users: S, M, L** — all legally consenting adults.

- S: Household coordination, appointment management
- M (27): Participation at his discretion
- L (19): Participation at his discretion — legally adult with appropriate consent

Each person gets their own:
- Preference module configuration
- Escalation preferences (which levels, which support persons, quiet hours)
- Domain spectrum classification (compensate/scaffold/their choice per domain)
- Communication style preferences
- Metrics tracking

**Level 4 (support-person) escalation** available between consenting adults only, with:
- Active consent verification from the support person (not just "user put your number in")
- Pre-escalation notification to user
- Post-escalation check-in
- Hard frequency limits

### E (17) and T (13): Deferred

Individual EF profiles with escalation and behavioral features for E and T are NOT deployed until:
- Age-banded policies are designed and reviewed
- Abuse/coercion threat model is complete (X2)
- Emergency exception matrix is defined
- Jurisdiction-specific legal review for minors
- Clinician governance framework exists (if applicable)

**What IS allowed now:** Informal family coordination — shared reminders, shared calendar events, group messages. Nothing that constitutes an individual EF profile with behavioral adaptation or escalation.

### Family Data, Consent, and Publication Policy

**Consent and Assent:**
- Every family member opts in voluntarily. No one is enrolled by default.
- **E (17, minor) and T (13, minor):** Each requires explicit assent before any future enrollment. J's parental consent is necessary but not sufficient.
- Any family member can withdraw at any time. Withdrawal = escalation stops immediately, profile archived, no new data collected.
- Already-collected data after withdrawal: retained for project metrics only in anonymized/aggregated form. Raw data deleted within 7 days.

**Family-systems isolation rule (X7):**
- No family member's data, conversations, or patterns influence interactions with another member unless explicitly shared by the first member.
- This applies even within a family. Each person's relationship with the companion is their own.

**Evidence publication standard (X14):**
- Never claim ExecFunc treats/improves/addresses any condition from family data
- Never publish individual outcomes without consent + review of the draft
- Never present family experience as generalizable evidence
- Family data = narrative ("what we learned"), never evidence ("this works")
- Any quantitative claims require peer-review-survivable methodology

**Escalation-specific safeguards for minors (when eventually deployed):**
- Each minor chooses which tasks are eligible for Level 4 escalation to parents
- Safety-related exceptions discussed and agreed in advance, not imposed
- The system never sends a minor's reflection mode content, emotional state, or private conversations to parents

### Action-Tier Scope

Per the Product Vision's action architecture:

| Tier | Phase 1 Scope | Status |
|---|---|---|
| **Tier 1: Information** (briefings, summaries) | ✅ Full | No restrictions needed |
| **Tier 2: Suggestions** (conflict detection, prioritization) | ✅ Full | No restrictions needed |
| **Tier 3: Staged Actions** (draft emails, call scripts) | ✅ Full | User reviews before execution |
| **Tier 4: Reversible Actions** (scheduling, reminders) | ⚠️ Limited | Calendar events and reminders only. Explicit confirmation. No purchases, no orders. |
| **Tier 5: Irreversible Actions** (payments, cancellations) | ❌ Not in Phase 1 | Requires dollar caps, merchant allowlists, audit logging |
| **Tier 6: Human Fallback** | ✅ Full | AI-prepared context + support-person handoff |

**Release gate:** No action tier above 3 ships without the corresponding confirmation/audit mechanism.

### Safeguard-to-Mechanism Matrix

| Product Vision Safeguard | Mechanism | Release Blocker? |
|---|---|---|
| Escalation levels are user-configured | Per-user config with defaults-off for Level 4 | ✅ Yes |
| Routine escalation is blockable | Pre-escalation notification with block option | ✅ Yes |
| Post-escalation check-in | "Was that helpful or did it make things worse?" | ✅ Yes |
| Task criticality set by user, not AI | Task creation includes criticality field; AI cannot override | ✅ Yes |
| Quiet hours respected | Time-window config per user; checked before sending | ✅ Yes |
| Volume caps enforced | User-configured daily maximum; hard stop at ceiling | ✅ Yes |
| Frequency caps on escalation | Configurable max escalations/week; hard-coded absolute ceiling | ✅ Yes |
| Recurring re-consent | Event-triggered + quarterly fallback maximum | ✅ Yes |
| Support-person active consent | Consent verification before first escalation delivery | ✅ Yes |
| Support-person revocation | Immediate effect; all pending escalations cancelled | ✅ Yes |
| Full audit trail of escalations | Structured log: time, level, recipient, content, response | ✅ Yes |
| Reflection mode in separate context | Reflection conversations stored separately; never surfaced in Utility mode | ✅ Yes |
| Family-systems isolation | Per-member data isolation; no cross-pollination | ✅ Yes |
| Anti-capture monitoring | Interruption burden, dismiss rates, compulsive checking, 24h ignore test | No — tracked, not gated |
| Social connectedness monitoring | Monthly self-report per family member | No — tracked, not gated |

**Rule:** No feature ships until all its ✅ release blockers are implemented and tested.

### Phase 2: Document Everything (Months 3-9, overlapping)

**The goal:** Comprehensive, honest guide for anyone who wants to build their own.

**What we document:**

1. **The Setup Guide** — How to configure an AI system for EF support (on OpenClaw or adaptable)
2. **The Design Principles** — Product Vision v3.0, preference modules, escalation framework, anti-capture design
3. **The Results** — What worked and what didn't. Honest about failures. Family data as narrative, never evidence.
4. **The Evidence Map** — Updated with our own observations: what hypotheses did we confirm, modify, or reject?

**Format:** GitHub repository with markdown docs, OpenClaw skill packages, configuration templates. MIT licensed.

### Phase 3: Open-Source Release (Months 6-12)

**The goal:** Share the framework and tell the story.

**GitHub Release — Tier 2 scope only:**
- OpenClaw skills for EF support (task management, escalation, friction detection, morning briefings)
- Configuration templates and setup guide
- Design principles documentation
- Results and observations (anonymized)
- Example prompt architectures
- Secure defaults (all high-risk features OFF by default)
- Feature flags enforcing Tier 1/Tier 2 boundary

**Before Tier 2 release, ALL of the following must be complete (deferred decisions from adversarial review):**
- Exclusion criteria defined (D2/X1)
- Abuse/coercion threat model (D3/X2)
- Harm-containment plan including adverse-event taxonomy, stop-ship criteria, offboarding/export (D4-D6/C7)
- Consent-comprehension design with explain-back for high-risk features (D7/X6)
- Support-person operating model (D8/X8)
- Recurring external oversight process (D9/X9)
- Jurisdiction-gating documentation (D10/X11)
- Secure defaults + feature flag enforcement (D11/X12)
- Prompt-injection threat model + technical controls (D12/X13)

**Signal & Noise (Newsletter):**
- "We built an AI assistant for our family — here's what happened"
- The philosophy — anti-capture design, assistive support, bounded utility
- Technical deep dives — escalation, privacy, measurement
- The results — honest, data-informed, including failures
- The bigger picture — AI + executive function + assistive technology

### Phase 4: Community + Iteration (Ongoing, only if Phase 3 succeeds)

**Ruthless sequencing (M16):** Each phase completes before the next begins. No premature community-building, no newsletter ExecFunc content before the framework works for our family.

---

## 4. WHAT WE BUILD ON OPENCLAW

### New Skills Needed

| Skill | Purpose | Complexity | Priority |
|---|---|---|---|
| **ef-task-tracker** | Structured task management with EF-aware features (energy levels, step breakdown) | Medium | High — core product |
| **ef-escalation** | Multi-level escalation with user-configured thresholds, pre-notification, post-check-in | Medium | High — key differentiator |
| **ef-morning-briefing** | Personalized daily briefing (calendar, tasks, weather, proactive friction detection) | Low-Medium | High — daily value delivery |
| **ef-friction-detector** | Pattern recognition for task avoidance, deadline proximity, administrative pile-up | Medium-High | Medium — requires usage data first |
| **ef-reflection** | CPS-based reflection mode (experimental — see Product Vision Section 5) | Medium | Lower — Phase 1B after core works |
| **ef-metrics** | Track supported task completion, escalation patterns, anti-capture metrics | Low-Medium | High — measurement from day one |

### Leveraging Existing Infrastructure

| Already Have | How It's Used |
|---|---|
| Telegram integration | Primary communication channel, group + individual DMs |
| gog CLI (Gmail/Calendar) | Calendar sync, email awareness, appointment extraction |
| Manual email forwarding | Non-PHI emails only. Calendar is primary data source. |
| remindctl | Apple Reminders integration |
| Memory system (MEMORY.md + daily files) | Persistent relationship memory per family member |
| Heartbeat/cron system | Scheduled check-ins, morning briefings |
| Synthia's personality | Identity consistency — already established |

### Per-Family-Member Configuration

Each family member gets their own:
- Preference modules (reminder intensity, warmth level, etc.)
- Escalation preferences (which levels, which support persons, quiet hours)
- Domain spectrum classification (compensate/scaffold/their choice per domain)
- Communication style preferences
- Metrics tracking

Stored in workspace files (e.g., `ef-profiles/j.md`). No database needed.

---

## 5. METRICS — FAMILY SCALE

See Product Vision v3.0, Section 10 for the full metrics framework. Adapted for family scale:

### What We Measure

| Metric | How | Frequency |
|---|---|---|
| Supported task completion rate | Task tracker data | Weekly |
| Escalation frequency and appropriateness | Escalation logs + family feedback | Weekly |
| Self-reported quality of life | Simple 1-5 scale | Weekly |
| Self-reported helpfulness | "Was the companion helpful this week?" per person | Weekly |
| Interruption burden | User-reported | Weekly |
| Mute/dismiss rate | Automated tracking | Continuous |
| Compulsive checking | Pattern detection | Continuous |
| 24-hour ignore test | Periodic silent day — not on days with critical tasks | Monthly |
| Social connectedness | Family self-report | Monthly |
| Support-person burden | Support person feedback | Monthly |

### What Success Looks Like

**For J:** Fewer missed administrative tasks. Less anxiety about schedule management. More mental bandwidth for medicine and family.

**For the project:** Honest observations about whether a persistent AI companion actually improves daily functioning for real people. Family data is narrative, never evidence.

---

## 6. TIMELINE

| Month | Focus | Deliverables |
|---|---|---|
| 1-3 | Core skills + J as first user | ef-task-tracker, ef-morning-briefing, ef-escalation (Levels 1-3). J uses daily. Anti-capture metrics active. |
| 3-6 | Expand to S, M, L (consenting adults) | Profiles configured per individual needs. Level 4 escalation available. All participation voluntary. |
| 3-9 | Document everything | Setup guide, design principles, results documentation. |
| 6-9 | Pre-release requirements | Complete ALL Tier 2 prerequisites (Section 3, Phase 3 list). |
| 6-12 | GitHub release (Tier 2) | Open-source skills, templates, guides, secure defaults. |

**This is not a sprint.** J has a full-time career and a family. 5-10 hours/week is the realistic time budget. Some weeks will be zero.

---

## 7. THE PIVOT OPTION

We're not closing the startup door. We're choosing not to walk through it yet.

**Hard thresholds — ALL must be met before the startup conversation is real:**

| Criterion | Threshold | Why It Matters |
|---|---|---|
| Family usage duration | 6+ months of continuous daily use | Proves it survives novelty wear-off |
| Family outcomes | Measurable improvement in supported task completion (>70%) and self-reported QoL for at least 2 family members | The product actually works |
| External setup success | 5+ non-family users set up and used for 30+ days without handholding | Proves transferability |
| External retention | 30-day return rate >30% among non-family users | People come back unprompted |
| Willingness to pay | At least 10 people independently express WTP (unprompted) | Real demand signal |
| Security maturity | Threat model documented, no unresolved high-severity issues, secret handling validated | Can't commercialize insecure product |
| Anti-capture metrics stable | No compulsive checking signals, social connectedness stable, no escalation backlash | Values survive real-world use |
| J's personal readiness | Career stage, financial position, family support, genuine desire | Not something a spreadsheet decides |

**Do NOT start a company if:**
- The framework only works with founder-level handholding
- High-risk integrations remain brittle or poorly controlled
- Anti-capture metrics show concerning trends
- The values in the Product Vision cannot survive commercialization pressures
- J doesn't genuinely want to do it

---

## 8. SECURITY AND DEPLOYMENT POSTURE

### Current State (Tier 1 — What Actually Exists)

| Concern | Approach |
|---|---|
| **API keys and tokens** | OS keychain, file-based logs, manual token rotation |
| **Work email (PHI)** | No automated scanning. Manual forwarding of non-PHI only. Calendar is primary data source. |
| **DLP pipeline** | J's private experimental pipeline (Tier 1 only). See DLP-ARCHITECTURE.md. NOT part of any public release. |
| **Escalation contacts** | Stored in EF profiles. Not logged in conversation history. |
| **LLM API exposure** | All prompts may be sent to LLM providers. No PHI, passwords, or financial account numbers in prompt-accessible data. |
| **Host security** | Mac mini with standard macOS security. OpenClaw workspace permissions restricted. |
| **Backup** | Existing Dropbox sync of OpenClaw workspace (encrypted at rest). |

**Rule (C5):** No document may advertise access or protections that don't exist in the implementation. The SECURITY-ARCHITECTURE.md document is labeled as "FUTURE VISION" — it describes aspirational architecture, not current state.

### For Tier 2 Release

- Minimum safe deployment guide
- Secret-handling requirements (env vars or secret managers, never in config templates)
- Least-privilege scopes (calendar read-only by default, write only for specific skills)
- Logging boundaries (what to log vs. what not to log)
- Threat model published with first release
- Secure defaults: all high-risk features OFF by default
- Feature flags enforcing Tier 1/Tier 2 boundary
- Prompt-injection threat model + technical controls (X13)
- No enterprise security tools required (M8) — appropriate to the scale

### Security Disclosure

Security vulnerabilities reported privately via email to security@execfunc.ai, not via public issues.

---

## 9. GOVERNANCE

### Current Scale

This project is maintained by one family. Decisions are made by J. Governance posture is scaled to current reality — not performatively mature (m5).

- **License:** MIT
- **External oversight:** Adversarial review via Codex before major releases. Advisory reviewer for safety-critical decisions before Tier 2 (X9).
- **Recurring:** Adversarial safety review by an external party before every major release or when adding any new high-risk capability.
- **Contributions:** Not yet open. Framework needs to stabilize first.

### Platform Dependency

ExecFunc currently depends on OpenClaw. We acknowledge this dependency explicitly (M10). ExecFunc skills are designed with separable logic where practical, but we do NOT claim platform portability until migration has been demonstrated on at least one component.

---

## DOCUMENT LINEAGE

**Active documents (this folder: `projects/execfunc/`):**
- `ARCHITECTURE-INDEX.md` — Master index, document hierarchy, open/deferred decisions
- `PRODUCT-VISION.md` — Product Vision v3.0 (governs all design)
- `OPEN-SOURCE-PATH.md` — This document (how we build it)
- `INTERACTION-MODEL.md` — Communication model v2.0
- `SECURITY-ARCHITECTURE.md` — Future vision for full-access security (labeled as such)
- `DLP-ARCHITECTURE.md` — PHI pipeline design (Tier 1 experimental)
- `DESIGNED-FOR-OBSOLESCENCE.md` — Evolvability architecture
- `DECISION-LOG-2026-03-20.md` — Canonical adversarial review decisions
- `README.md` — Public-facing overview (Tier 2 framing)

**Archived (startup path: `projects/Old/exec-function-pre-open-source/`):**
- All previous versions and startup-context documents

---

*"Build it for your family. Use it. Refine it. Write about it. If it's genuinely transformative — that's the evidence that makes the startup decision for you."*
