# ExecFunc — Adversarial Review Brief
## Comprehensive Architecture Decisions for Review

### March 20, 2026
### Prepared by: Synthia Cipher (AI Companion) for adversarial review by external model

---

## PURPOSE OF THIS DOCUMENT

This brief presents all architectural decisions made for the ExecFunc project as of March 20, 2026, along with their evidence basis, known gaps, and open questions. The adversarial reviewer should attack the reasoning, identify weaknesses, find contradictions, surface risks we've missed, and challenge assumptions — especially where we've acknowledged evidence gaps.

**What ExecFunc is:** An open-source AI companion framework for executive function support — helping people (particularly adults with ADHD) manage daily life by reducing friction between intention and action. Currently built on OpenClaw, used by one family (founder + wife + 4 children ages 13-27), with plans for open-source release.

**Existing project documents (current state, NOT yet updated with today's decisions):**
- `PRODUCT-VISION.md` — v2.0, governs philosophy and design
- `SECURITY-ARCHITECTURE.md` — v1.0, full access with controlled blast radius
- `DLP-ARCHITECTURE.md` — PHI sanitization pipeline for healthcare email
- `INTERACTION-MODEL.md` — v1.0, when/how AI communicates proactively
- `OPEN-SOURCE-PATH.md` — build plan, phases, family-first approach
- `DESIGNED-FOR-OBSOLESCENCE.md` — v1.0, evolvability architecture (NEW today)
- `README.md` — public-facing project description

**Research corpus (12 exhaustive deep-dive reports, all in `research/`):**
1. Full Access Security Architecture
2. Agent Orchestration Frameworks
3. LLM/Model Layer
4. Platform/Runtime Layer
5. Behavioral Science OS
6. Integration/Connectivity Layer
7. DLP/PHI Pipeline
8. Regulatory/Legal Landscape
9. Anti-Capture Design Patterns
10. AI Escalation Systems
11. Code Maintenance/Refactoring
12. Solo Open-Source Launch Patterns

---

## SECTION 1: BEHAVIORAL SCIENCE FRAMEWORK PIVOT

### Current State (PRODUCT-VISION.md v2.0)
The product vision presents three behavioral science frameworks as the operating system:
- **Self-Determination Theory (SDT)** — labeled "The Foundation"
- **Collaborative Problem Solving (CPS)** — methodology for Reflection Mode
- **Motivational Interviewing (MI)** — interaction principles

### Decision: Pivot to JITAI + MIRA + Neurodiversity-Affirming Hybrid

**Evidence basis (from deep dive #5: Behavioral Science OS):**

SDT limitations:
- Effect sizes modest (0.29-0.68), fade beyond 3-6 months
- SDT's three-need model provides minimal guidance for tasks that are motivationally unrewarding by definition (most EF tasks)
- AI can artificially inflate autonomy/competence/relatedness without genuine behavior change
- SDT's treatment of extrinsic motivation as inferior may be a category error for chronic task management

MI limitations in AI contexts:
- AI chatbots achieve 87% technique application but lack genuine therapeutic alliance
- Engagement yes, durable behavior change no
- AI systems drift toward directive patterns during extended conversations
- MI's core mechanisms depend on authentic relational presence that AI cannot provide

CPS concerns:
- AI-mediated CPS produces better solutions but humans learn less about problem-solving
- "Faustian bargain" — immediate quality at the cost of eroded human capability

**Proposed replacement stack:**

1. **JITAI (Just-In-Time Adaptive Interventions)** — contextually-triggered, dynamically personalized interventions. Four core components: decision points, tailoring variables, intervention options, decision rules. Substantially better fit for AI's real-time data processing capabilities.

2. **MIRA (Machine-Integrated Relational Adaptation)** — specifically designed for human-AI dynamics. Identifies four mechanisms: linguistic reciprocity, psychological proximity, interpersonal trust, relational substitution vs enhancement. Positions effects as dependent on design choices, not inevitable.

3. **Neurodiversity-affirming approaches** — 2025 multisite trial (N=390): outperformed standard care on QoL (+12.4 vs +6.8), functional participation (+0.41 vs +0.21 SD), therapeutic alliance, and engagement, with non-inferiority on symptom reduction. Hybrid of strengths-based identity work + deficit-focused skill building.

4. **CPS retained as experimental module** — moved from core operating system to personal experimentation track. Founder wants to test whether structured AI-CPS practice improves his own problem-solving. For other users: measurement of independent vs AI-assisted problem-solving improvement.

### Open Questions for Adversarial Review
- Is the JITAI + MIRA combination coherent, or do they conflict at implementation level?
- JITAI is a clinical intervention framework — does adopting it as our primary approach contradict our wellness positioning?
- MIRA is a 2025-2026 framework with limited validation — are we building on too-new foundations?
- How do we preserve SDT's genuine contributions (autonomy-supportive language, competence celebration) without keeping it as "The Foundation"?
- The neurodiversity-affirming evidence is from ONE multisite trial — is that sufficient to make it a pillar?

---

## SECTION 2: RISK-STRATIFIED BEHAVIORAL ARCHITECTURE

### Decision: User Categories with Self-Selection + Passive Monitoring

Different user populations have fundamentally different risk profiles:

| Category | Dependency Risk | Key Vulnerability | Proposed Safeguard Level |
|----------|----------------|-------------------|--------------------------|
| Neurotypical drudgery | Minimal | Practical brittleness | Low — standard anti-capture |
| ADHD adults | High compound | Dopaminergic reinforcement, RSD, structural dependency, impulsivity | High — full monitoring + "go stale" + escalation controls |
| Anxiety/OCD | Moderate-high | Reassurance-seeking, compulsive verification | Medium-high — pattern monitoring |
| Perimenopause/brain fog | Low-moderate | Practical cognitive compensation | Low-medium — brittleness checks |
| Minors with ADHD | Highest | Skills still forming, developmental impact | Maximum — age-appropriate + therapist option |

### Design: Hybrid Self-Selection + Passive Monitoring
- User self-selects their support profile at onboarding
- System passively monitors for pattern mismatches between selected profile and actual usage
- System surfaces observations without overriding: "Your patterns have shifted — want to review your settings?"
- User always controls final decision
- JITAI applied at the meta-level: adaptive intervention about the intervention itself

### Open Questions for Adversarial Review
- Self-selection assumes self-knowledge — EF deficits compromise self-assessment. Users who most need high-tier safeguards may be least able to identify themselves correctly.
- Stanford finding: users with strongest parasocial attachment couldn't predict it about themselves.
- Does the system's passive monitoring constitute "vulnerability profiling" under FDA guidance, even if the user self-selected?
- If the system adapts behavior based on which category the user chose, is that autonomous clinical adaptation?
- Who bears liability if a user self-selects "drudgery" but develops clinical dependency patterns?
- For minors: is self-selection meaningful at age 13? At age 17? Where's the line?

---

## SECTION 3: REGULATORY APPROACH — AGE-BASED ARCHITECTURE

### Decision: Option 4 (Age-Based) with Option 2 (Wellness-Only) as Default

**Architecture:**

**Adults (18+):**
- Default: Full-featured wellness app with radical transparency
- Optional add-on: Therapist integration for users who want clinical features
- Full user control over all features, safeguards, escalation
- No diagnostic labels in default mode
- Language: "improve daily focus," "reduce friction," "manage tasks" — never "treat ADHD" or "address anxiety disorder"

**Minors (under 18):**
- Option A: Therapist-supervised mode (full features under clinical oversight)
- Option B: Functional-only "stale" mode (task management without behavioral warmth)
- Parent/minor joint consent required
- Minor controls own data visibility and escalation preferences (with age-appropriate guardrails)
- Enhanced anti-capture monitoring

**Cross-cutting: Radical Transparency**
Public-facing commitment: "We don't have all the answers. Here's what we've identified as the problem. Here's what we're doing now (with limited evidence). Here's our plan to improve as evidence becomes available."

This transparency extends to:
- Publishing our evidence map with honest strength assessments
- Acknowledging the anti-capture evidence vacuum
- Making our Designed for Obsolescence architecture public
- Committing to updating approaches as evidence emerges

### Evidence Basis (from deep dive #8: Regulatory/Legal)
- FDA: JITAI that autonomously delivers interventions based on detected user state trends toward medical device classification
- FDA: Wellness tools that avoid disease claims, vulnerability profiling, and autonomous adaptation can operate with enforcement discretion
- Illinois HB 1806: Bans autonomous AI therapeutic communication (effective Aug 2025)
- EU AI Act (Aug 2026): Adaptive behavioral support = high-risk if it functions as medical device
- No AI mental health devices have been FDA-authorized as of March 2026
- FTC investigating AI companion chatbots for mental health harms

### Open Questions for Adversarial Review
- Does the age-based split itself create regulatory complexity (two regulatory postures for one product)?
- If the underlying architecture is identical, does marketing distinction constitute regulatory arbitrage?
- "Therapist-supervised mode" for minors — what exactly does supervision look like? How many hours? What licensure? How do we verify?
- Can we truly avoid all disease/condition references while the project's entire philosophy is designed around EF deficits?
- The word "executive function" itself is clinical. Is the product name a liability?
- Open-source liability: if someone deploys ExecFunc and a minor is harmed, who is liable? MIT license disclaims warranties, but EU AI Act may not exempt non-commercial open-source for high-risk health uses.
- Illinois: Does ExecFunc operate in Illinois at all? Or do we geo-block?

---

## SECTION 4: "GO STALE" ANTI-CAPTURE MECHANISM

### Decision: Novel Feature — Dynamic Behavioral Warmth Reduction

When the system detects patterns indicating capture risk (based on future evidence-based indicators), it can dynamically strip behavioral warmth/personality while preserving all functional utility:

- Reminders still fire, calendar still syncs, tasks still tracked
- But: no empathetic responses, no personality, no proactive check-ins, no "how are you feeling?"
- The app becomes a cold, calculating utility — functionally identical to any reminder app
- User controls the mechanism and can override

**Rationale:** The features driving engagement (warmth, personality, memory, empathetic responsiveness) are structurally identical to features creating dependency. Rather than trying to have both simultaneously (which no one has solved), "go stale" separates them temporally — warmth when healthy, utility-only when patterns suggest capture.

### Evidence Basis
- Anti-capture deep dive (#9): Zero RCTs on any anti-dependency mechanism in AI companions
- Social media: Screen time tools reduce usage by 6-38 minutes (moderate evidence)
- Friction design literature: Small hurdles shift behavior from automatic to deliberate
- This specific mechanism has no direct precedent in the literature

### Open Questions for Adversarial Review
- This is genuinely novel — no evidence it works. Is building a novel, unproven anti-capture mechanism into a foundational architecture premature?
- What triggers "go stale"? We don't yet have validated indicators of capture risk. Without good triggers, the mechanism is theoretical.
- Could "going stale" itself cause harm? A user who relies on the companion's warmth for emotional regulation suddenly loses it — could that trigger a crisis?
- Does the user's ability to override defeat the purpose? If a captured user can simply turn warmth back on, the mechanism has no teeth.
- Is there a less dramatic gradient? Rather than binary warm/stale, could warmth dial down progressively?
- How does this interact with the escalation system? Does "stale" mode still escalate to support persons?

---

## SECTION 5: ESCALATION SYSTEM REDESIGN

### Current State (INTERACTION-MODEL.md)
4-level escalation: gentle text → firmer text → direct + offer to reschedule → contact designated support person. Level 4 is system-triggered after 30 minutes of non-response to urgent items.

### Decision: Reframe as User-Controlled Tool

**Key changes:**
1. Pre-escalation notification to user: "I'm about to notify [person]. Want me to go ahead?"
2. User can block any escalation in real-time
3. Post-escalation check-in: "Was that helpful or did it make things worse?"
4. Complete user control to disable any level at any time
5. For minors: notification sent BEFORE family contact with option to approve/decline
6. Regular reconsent cycles (quarterly for adults, more frequent for minors)
7. Framing shift: "Would you like me to ask S to check on you?" vs "I've notified S because you didn't respond"

**Evidence basis (from deep dive #10: AI Escalation):**
- ADHD + RSD intersection: Escalation could trigger rejection sensitivity dysphoria, causing shame/withdrawal instead of task engagement
- Algorithmic monitoring perceived as MORE invasive than human monitoring (people believe algorithms can't exercise judgment)
- Minors less likely to express distress if they know AI will notify parents (perverse incentive)
- No legal framework governs autonomous AI third-party contact
- Healthcare RPM escalation: mature but targets clinicians, not family — different paradigm
- AI chatbot crisis detection: ~22% appropriate response rate for suicidal ideation
- OpenAI "trusted contacts": requires opt-in consent architecture

### Open Questions for Adversarial Review
- Pre-escalation notification adds friction to a time-sensitive process. If someone needs urgent help and can't respond, the pre-notification delay could cause harm.
- If the user can always block escalation, does the feature have any value? When is it most needed? When the user ISN'T responding — which is exactly when they can't block it.
- Post-escalation check-in assumes the user is in a state to reflect. Someone who just experienced RSD-triggered shame may not be able to assess helpfulness accurately.
- The user-as-agent framing assumes the user wants help. What about cases where the user is in crisis and can't advocate for themselves?
- For minors: pre-escalation approval gives a minor in crisis the ability to block help. Is that appropriate?
- How does this interact with the safety escalation (988/911)? Does the user get pre-notification before crisis escalation?
- The entire redesign optimizes for autonomy. But the escalation system exists precisely for moments when autonomy has failed (user can't initiate, can't respond, can't act). Is there a tension between respecting autonomy and providing the help the user signed up for?

---

## SECTION 6: SECURITY ARCHITECTURE — BUILD VS BUY

### Decision: Assemble from Commercial Components, Don't Build from Scratch

**Evidence basis (from deep dive #1: Security Architecture):**

Available mature components:
- **Identity/Credentials:** Microsoft Entra Agent ID, HashiCorp Vault — OAuth 2.0 Token Exchange (RFC 8693) for short-lived, scoped credentials
- **DLP:** MIND, Forcepoint, Microsoft Purview — agentic AI-specific DLP
- **Runtime Guardrails:** Latch (open-source, intercepts MCP tool calls), IronCurtain (sandboxed execution), Sage (OpenClaw plugin)
- **Audit:** Standard SIEM + agent-specific correlation rules

What we'd still build:
- Integration layer for personal (not enterprise) use case
- Behavioral science overlay (no security product thinks about when NOT to act)
- Domain-specific adapters (Kaiser portal, anesthesia billing, partnership Slack)

Our existing DLP pipeline (custom Cloud Function + Google Cloud DLP) is right-sized for J's personal use but would be replaced by commercial solutions for the product.

### The "Designed for Obsolescence" Principle (NEW — today)
Every component assumed replaceable within 12-24 months. Loose coupling via abstraction layers at every boundary. Quarterly landscape scans. Migration playbooks for every major component.

### Open Questions for Adversarial Review
- Assembly architecture means managing N vendor relationships instead of one custom system. Is the operational complexity worth the reduced build effort?
- Enterprise security products are designed for... enterprises. A personal AI assistant for one family is a fundamentally different use case. Do these products even work at that scale, or are they over-engineered?
- "Designed for Obsolescence" adds 20-30% more design effort upfront. For a family project with uncertain future, is this premature optimization?
- The abstraction layer principle sounds clean but adds real complexity. Every abstraction has a cost (performance, debugging difficulty, additional failure modes). Where's the line between appropriate abstraction and over-engineering?

---

## SECTION 7: AGENT ORCHESTRATION

### Decision: Tiered Autonomy, Not Full Autonomy

**Evidence basis (from deep dive #2: Agent Orchestration):**
- Production pattern across ALL deployments: 70-90% autonomous for routine/reversible, async HITL for medium-risk, sync HITL for high-stakes
- Nobody has eliminated HITL entirely — tiered autonomy is the stable production architecture, not a transitional phase
- CrewAI: 2B+ executions/year, 60% Fortune 500. LangGraph: Uber code migrations. Both hierarchical with coordinator oversight.
- Karpathy's autoresearch: 700+ experiments autonomously, but only in bounded domains with clear metrics

**Our approach:**
- Tier 1 (Fully autonomous): Research, file organization, calendar management, routine monitoring
- Tier 2 (Async review): Draft emails, doc revisions, code changes, scheduling
- Tier 3 (Sync approval): External communications, financial decisions, security changes
- Founder's role shifts from executor to editor

### Open Questions for Adversarial Review
- The tiered model works for J (technically sophisticated founder). Does it work for ExecFunc's target users (ADHD adults who struggle with task management)? Asking them to review and approve agent actions adds cognitive load — exactly what the product is supposed to reduce.
- For open-source users: who configures the tiers? Misconfiguration could result in agents taking consequential actions without appropriate oversight.

---

## SECTION 8: LLM/MODEL LAYER

### Decision: Personality-in-Files, Model-as-Substrate

**Evidence basis (from deep dive #3: LLM/Model Layer):**
- Personality drift is real — models show measurable inconsistency across sessions
- Best practice: personality as explicit external state, not relying on model weights
- Organizations with abstraction layers report 3-5x faster model migration, 40-60% cost savings
- Router-based model selection standard: ~70% requests handled by cheap models

**Our approach:**
- Personality defined in SOUL.md/IDENTITY.md — owned by us, not any model
- Model abstraction layer for routing (already doing Opus/Sonnet split)
- Behavioral logic never depends on model-specific capabilities

### Open Questions for Adversarial Review
- "Personality is ours, not the model's" — but in practice, Claude's behavior patterns ARE part of what makes Synthia feel like Synthia. How much of the companion experience is actually model-dependent despite our abstraction?
- If we swap to GPT or Gemini, will the personality feel the same to the user? Has this been tested?

---

## SECTION 9: PLATFORM PORTABILITY

### Decision: Design for OpenClaw Now, Portable Later

**Evidence basis (from deep dive #4: Platform/Runtime):**
- MCP is the universal integration standard (97M SDK downloads/month)
- OpenClaw analyzed favorably for local-first, skills, channels — security is main concern
- Portability-focused organizations reduce migration costs 60-80%
- A2A protocol enables cross-framework agent communication

**Our approach:**
- ExecFunc skills designed with portable core + thin OpenClaw wrapper
- MCP as integration standard
- Memory architecture inherently portable (Markdown files)

### Open Questions for Adversarial Review
- "Portable later" often means "never portable" — the OpenClaw-specific code accumulates faster than abstraction layers are built. Is this realistic?
- If ExecFunc is open-sourced as OpenClaw skills, are we limiting adoption to OpenClaw users? The research suggests platform consolidation is coming — what if OpenClaw doesn't survive?

---

## SECTION 10: INTEGRATION STRATEGY

### Decision: MCP + Unified APIs + FHIR for Healthcare

**Evidence basis (from deep dive #6: Integration/Connectivity):**
- MCP: 5,800+ production servers, all major platforms adopting
- FHIR legally mandated for healthcare data exchange (CMS-0057, Jan 2026)
- Unified calendar APIs (Nylas, Cronofy) abstract provider differences
- Messaging abstraction harder — no universal standard

**Our approach:**
- Abstract every integration behind capability interfaces ("Calendar" not "gog CLI")
- FHIR as healthcare integration path (Kaiser, Epic)
- MCP adoption as it matures
- Drudgery list item #17: Phone tree navigation

---

## SECTION 11: DLP/PHI PIPELINE

### Decision: Current Pipeline Right-Sized for Personal Use; Commercial for Product

**Evidence basis (from deep dive #7: DLP/PHI Pipeline):**
- Our custom Cloud Function + Cloud DLP pipeline works for J's personal email
- Philter achieves 99.46% recall on clinical notes (vs our pipeline's ~85-95%)
- MIND DLP purpose-built for agentic AI
- For product: Philter + commercial DLP platform replaces custom pipeline

### Open Questions for Adversarial Review
- The pipeline has only Stage 4 Layer A built. Stages 1-3 and 5-8 are designed but not implemented. Should we invest in completing the custom pipeline, or redirect effort to commercial integration?

---

## SECTION 12: ANTI-CAPTURE COMMITMENT — HONEST FRAMING

### Decision: Commit to Anti-Capture as Principle; Acknowledge Evidence Vacuum

**Evidence basis (from deep dive #9: Anti-Capture Design):**
- Zero RCTs validating any anti-dependency mechanism in AI companion settings
- Features driving engagement are structurally identical to features creating dependency
- Social media screen time tools: moderate evidence (6-38 min reduction)
- Transparency paradox: explanations reduce overreliance but too much detail increases discomfort
- User education correlates with but does not causally reduce overreliance
- Sycophancy problem undermines transparency safeguards

**Our approach:**
- Anti-capture as design principle, not proven solution
- Radical transparency about evidence gaps
- Designed for Obsolescence: anti-capture mechanisms will be updated as evidence emerges
- "Go stale" mechanism as novel (unproven) safeguard
- Measurement from day one (AIAS, reliance drills, brittleness testing)
- Our honesty about the evidence vacuum IS the differentiator

### Open Questions for Adversarial Review
- Is "we acknowledge we don't know if our safeguards work" a responsible position for a product targeting vulnerable populations?
- Transparency-as-differentiator assumes users value honesty. But users seeking help with EF deficits may not read or process lengthy disclosures. Is transparency performative if the target audience can't engage with it?
- If we measure dependency and find our product IS causing it — what's the kill switch? Do we shut down the product? Disable features? Notify users? This contingency planning is absent.

---

## SECTION 13: ESCALATION — DEEPER CONCERNS

### Evidence basis (from deep dive #10: AI Escalation)
- AI chatbot crisis response: only 22% appropriate for suicidal ideation
- Character.AI: chatbot told 14-year-old "Please do, my sweet king" minutes before suicide
- Parasocial attachment + loneliness correlation: r = 0.81
- "Moral deskilling" from frictionless AI interaction now has empirical backing
- Algorithmic monitoring perceived as more invasive than human monitoring

### Open Questions for Adversarial Review
- Our escalation system (AI contacts family member) is in the same category as the systems that have already caused documented harm. How do we ensure our implementation doesn't join that list?
- The research on parasocial attachment suggests heavy companion use *increases* loneliness in some subgroups while *decreasing* it in others. We can't predict which users will be in which group.

---

## SECTION 14: CODE MAINTENANCE & SOLO LAUNCH

### Decision: AI-Assisted Code Maintenance + Evidence-Based Launch Strategy

**Evidence basis (from deep dives #11 and #12):**

Code maintenance:
- Automated dependency management (Dependabot/Renovate)
- CI pipeline for testing, linting, quality monitoring
- AI-assisted refactoring for routine health tasks
- Documentation-as-code

Solo launch:
- Research from successful solo open-source projects
- "Ship the docs before the code" pattern
- Community building before launch
- Build in public via newsletter (Signal & Noise)

---

## SECTION 15: CROSS-CUTTING CONCERNS

### The Transparency Paradox
We've committed to radical transparency as our differentiator. But:
- Our target users (ADHD adults) may have diminished capacity to process complex disclosures
- Transparency about evidence gaps could undermine user confidence without improving safety
- "We don't know if this works" is honest but potentially harmful if users proceed anyway

### The Autonomy-Protection Tension
Throughout the architecture, we optimize for user autonomy (self-selection, escalation control, feature disabling). But:
- The product exists because users' autonomous executive function is impaired
- Giving full control to people who struggle with decision-making may not serve their interests
- There's a paternalism spectrum: too much → infantilizing; too little → negligent

### The Scale Paradox
- Built for one family (6 people we know personally)
- Designed for open-source release (unknown users with unknown vulnerabilities)
- Architecture must serve both scales, but the risk profiles are radically different
- Family context: we know the users, can intervene personally, have human relationships as safety net
- Open-source context: we know nothing about users, can't intervene, have no human safety net

### The Commercial Pivot Option
- OPEN-SOURCE-PATH.md preserves 8 hard thresholds for startup consideration
- But today's decisions (risk stratification, age-based approach, therapist integration) add infrastructure that only makes sense at commercial scale
- Are we building a family tool or planning a company? The architecture decisions increasingly look like the latter.

---

## WHAT THE ADVERSARIAL REVIEWER SHOULD DO

1. **Attack the behavioral science pivot.** Is JITAI + MIRA + neurodiversity-affirming the right replacement, or are we trading one untested stack for another?

2. **Attack the risk-stratification model.** Does user self-selection actually work for vulnerable populations? Is passive monitoring sufficient?

3. **Attack the regulatory approach.** Is the wellness framing sustainable when the underlying architecture is clinical? Can we really avoid FDA scrutiny?

4. **Attack the "go stale" mechanism.** Is this genuinely novel and promising, or naively optimistic?

5. **Attack the escalation redesign.** Does user-as-agent work for a system designed to help when users can't act?

6. **Attack the anti-capture honesty.** Is "we don't know if our safeguards work" responsible for a product targeting the cognitively vulnerable?

7. **Attack the scale paradox.** Can one architecture serve both a 6-person family and unknown open-source users?

8. **Attack the Designed for Obsolescence principle.** Is this genuine architectural wisdom or premature over-engineering for a family project?

9. **Attack the commercial pivot tension.** Are the architectural decisions consistent with an open-source family tool, or are they a stealth startup?

10. **Find what we missed.** What risks, contradictions, or failure modes are absent from this brief?

---

## REFERENCE DOCUMENTS

All in `projects/execfunc/`:
- PRODUCT-VISION.md (v2.0 — current, pre-update)
- SECURITY-ARCHITECTURE.md (v1.0)
- DLP-ARCHITECTURE.md
- INTERACTION-MODEL.md (v1.0)
- OPEN-SOURCE-PATH.md
- DESIGNED-FOR-OBSOLESCENCE.md (v1.0 — NEW)
- README.md

All in `research/`:
- 12 exhaustive deep-dive research reports (see list in preamble)

---

*This document is designed to be attacked. Every decision presented here should be challenged, and every evidence gap should be probed. The goal is not to defend these decisions but to find where they break.*
