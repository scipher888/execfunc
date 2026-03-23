# ExecFunc — Designed for Obsolescence
## Foundational Evolvability Architecture

### Version 1.1 — March 21, 2026 (originally 1.0, March 20, 2026)

*Every component in this system will be replaced. The question is whether we designed for that, or whether replacement requires rebuilding from scratch.*

---

## 1. THE PRINCIPLE

**Evolvability is a load-bearing requirement — not a nice-to-have, not a phase-two concern, but a foundational architectural constraint equal in importance to security, privacy, and reliability.**

The AI landscape is moving faster than any technology cycle in history. Models, platforms, protocols, integrations, security tools, and even behavioral science frameworks are evolving on quarterly timescales. Any system that works excellently at launch but has no built-in mechanism for systematic self-assessment and strategic upgrade becomes technical debt within 6-12 months.

**The design assumption:** Every component in ExecFunc will be superseded by something meaningfully better within 12-24 months. Our architecture must make component replacement a routine maintenance operation, not an emergency rebuild.

**Scale-appropriate cadences (M7):** The review cadences in this document describe two tiers: (1) **current-scale** cadences appropriate for a solo builder with a family build, and (2) **scaled-operations** cadences for when/if the project grows. At current scale, reviews are primarily **trigger-based** (something changed that matters) rather than calendar-based. Comprehensive health checks target every 18-24 months, not annually.

**What this means in practice:**
- Every component connects through **abstraction layers with defined interface contracts**
- If we can swap a component without touching anything else, the architecture is correct
- If swapping a component requires changing 6 other things, the architecture has failed this principle
- We invest upfront in interfaces and contracts specifically to reduce future migration cost

---

## 2. THE SEVEN FOUNDATIONAL SYSTEMS

ExecFunc rests on seven load-bearing foundational systems. Each requires its own evolvability strategy.

### System 1: Security Architecture (Full Access + Industrial-Grade Protection)
**Current state:** SECURITY-ARCHITECTURE.md v1.0 — tiered trust zones, scoped credentials, defense in depth, kill switches.

**Why it must evolve:**
- The security product landscape is shifting quarterly (new entrants, new capabilities, new standards)
- OAuth patterns, credential vaulting, DLP services, runtime guardrails — all improving rapidly
- Emerging standards (NIST AI Agent Standards, MITRE ATLAS agentic techniques, SAIL Framework) will reshape best practices
- Our current architecture is largely custom-built; mature commercial components may replace much of it

**Evolvability strategy:**
- Abstraction: Security controls accessed through defined interfaces, not hard-wired to specific vendors
- Each security layer (identity, DLP, audit, guardrails) independently replaceable
- Quarterly landscape scan for new products, standards, and threat vectors
- Annual adversarial review of the complete security architecture

**Review cadence:** Quarterly deep dive + annual adversarial review

---

### System 2: Agent Orchestration
**Current state:** Single-agent (Synthia on OpenClaw) with one-shot sub-agents for specific tasks (Codex for adversarial review).

**Why it must evolve:**
- Multi-agent orchestration frameworks are maturing rapidly (CrewAI, LangGraph, AutoGen, Google ADK)
- Persistent specialized agent teams with coordinator oversight are emerging as production patterns
- Trust infrastructure for agent swarms (verification, auditing, drift prevention) is being built now
- Our current "me-supervised, single-task, one-shot" sub-agent pattern will be obsolete

**Evolvability strategy:**
- Abstraction: Agent task definitions separated from orchestration framework
- Task descriptions, success criteria, and escalation rules defined in portable formats (not framework-specific code)
- Coordinator logic (what to delegate, when to escalate to human) expressed as declarative policies, not imperative code
- Human-in-the-loop gates expressed as configuration, swappable between frameworks

**Review cadence:** Quarterly deep dive

---

### System 3: LLM / Model Layer
**Current state:** Claude-centric (Opus for main, Sonnet for routine) with identity consistency tied to Claude's personality characteristics.

**Why it must evolve:**
- Model capabilities are the fastest-moving component in the entire system
- Context windows, tool use, reasoning, persistent memory, multimodal capabilities — all changing quarterly
- New models could render our workaround architectures unnecessary (e.g., native persistent memory could replace our file-based system)
- Pricing shifts could make our current model routing economics irrelevant
- Open-source models approaching frontier quality could enable self-hosting for data sovereignty
- Fine-tuning and customization options evolving rapidly

**Evolvability strategy:**
- **Personality is ours; the model is a substrate.** Synthia's identity, voice, behavioral patterns, and relationship memory exist in our files and design docs — not in any model's weights
- Prompt architecture uses model-agnostic patterns where possible; model-specific optimizations isolated in adapter layers
- Behavioral logic (escalation rules, anti-capture checks, value surplus tracking) never depends on model-specific capabilities
- Multi-model testing: periodically evaluate new models against our interaction quality standards before switching
- Model abstraction layer: all model calls go through a routing layer that can redirect to different providers without changing application logic

**Review cadence:** Quarterly deep dive (fastest-moving domain)

---

### System 4: Platform / Runtime Layer (Currently OpenClaw)
**Current state:** OpenClaw handles everything — memory, messaging, cron, tools, multi-channel presence, personality persistence.

**Why it must evolve:**
- The agent platform landscape is exploding (Anthropic, Google ADK, OpenAI Agents SDK, plus orchestration frameworks)
- Platform consolidation is likely within 12-24 months — some platforms will survive, others will merge or die
- OpenClaw's architecture could shift in ways that break our skills
- Our open-source release assumes users run OpenClaw — the landscape may consolidate around something else

**Evolvability strategy:**
- **Separate ExecFunc logic from OpenClaw runtime.** The behavioral science engine, escalation chains, friction detection, anti-capture monitoring — these are ExecFunc's intellectual property. They should be expressible independently of any runtime.
- ExecFunc skills designed with a portable core: logic in standard code/config, OpenClaw-specific integration as a thin wrapper
- Memory architecture: our Markdown-based memory system is inherently portable (plain text files), which is an advantage — but the *retrieval and update patterns* should be abstracted
- Multi-channel presence logic separated from channel-specific implementation
- If we had to rebuild on a different platform in 12 months, target: 80%+ of logic transfers without rewrite

**Review cadence:** Semi-annual deep dive (more stable but high-consequence if it shifts)

---

### System 5: Behavioral Science Operating System
**Current state:** SDT (Ryan & Deci), CPS (Ablon), MI principles, Gottman's ratio, EF frameworks (Dawson & Guare, Diamond).

**Why it must evolve:**
- The application of behavioral science to AI-mediated interventions is a brand-new field with minimal long-term evidence
- Core theories themselves can be challenged, refined, or superseded as new research emerges
- SDT was formalized in the 1980s; it may not be the optimal framework for human-AI interaction in the 2030s
- CPS has predominantly pediatric evidence; adult AI-mediated CPS is uncharted
- MI shows weak evidence for durable behavior change in AI chatbot contexts
- The optimal "value surplus ratio" for human-AI interaction is unknown — 5:1 is borrowed from human relationships
- Entirely new frameworks may emerge that are specifically designed for AI companion behavioral dynamics
- Neurodiversity-affirming approaches are evolving rapidly and may reshape how we think about EF support
- Emerging research on parasocial relationships, AI anthropomorphism, and dependency patterns could change our anti-capture design

**Evolvability strategy:**
- **No framework is sacred.** Our commitment is to evidence-based design, not to any specific theory. If a better framework emerges, we adopt it.
- Implementation parameters (ratios, timing, language patterns, escalation thresholds) treated as configurable hypotheses, not fixed constants
- Behavioral logic expressed declaratively (rules and parameters) not imperatively (hard-coded patterns) — making it possible to swap underlying frameworks without rewriting interaction logic
- Annual deep dive on new behavioral science + AI interaction research, with specific focus on:
  - New frameworks designed for AI-mediated behavioral support
  - Updated evidence on existing frameworks (SDT, CPS, MI) in AI contexts
  - Emerging research on human-AI relationship dynamics and dependency patterns
  - Neurodiversity-affirming alternatives to deficit-based models
  - New evidence on anti-capture and anti-dependency design
- Maintain an explicit **evidence ledger** (see Evidence Map in PRODUCT-VISION.md) tracking what we've confirmed, what we've modified, and what we've rejected based on our own data and external research
- When theory conflicts with observed family outcomes, observed outcomes take precedence

**Review cadence:** Annual deep dive + continuous informal monitoring of key publications

**Critical note:** The behavioral science OS is the *soul* of ExecFunc — what makes it more than a reminder app. Changing it is higher-stakes than swapping a DLP provider. Changes here require careful transition planning, not just a component swap. But the willingness to change it when evidence demands it is exactly what makes the project honest.

---

### System 6: Integration / Connectivity Layer
**Current state:** Direct integrations via CLIs and APIs — gog (Google Workspace), remindctl (Apple Reminders), imsg (iMessage), Telegram Bot API, DLP Cloud Function.

**Why it must evolve:**
- MCP (Model Context Protocol) is rapidly becoming the universal integration standard — and it's still maturing
- APIs deprecate, change, and evolve (Google APIs, Telegram Bot API, financial aggregation APIs)
- Healthcare portal integration patterns are shifting as FHIR adoption expands
- Financial aggregation (Plaid, open banking) is in regulatory flux
- Smart home protocols are consolidating (Matter)
- New integration protocols beyond MCP may emerge

**Evolvability strategy:**
- **Abstract every integration behind a capability interface.** "Calendar" not "Google Calendar via gog." "Messaging" not "Telegram Bot API." "Financial Data" not "Plaid API."
- Each integration implemented as a pluggable adapter conforming to the capability interface
- Integration adapters are the thinnest possible layer — translate between our interface and the external API
- When an API changes or a better provider emerges, only the adapter changes
- MCP adoption as it matures, but not MCP-dependent — MCP servers are one type of adapter
- Integration health monitoring: detect when an integration is degrading (API errors, deprecation warnings, rate limit changes)

**Review cadence:** Quarterly per integration domain (healthcare APIs may shift on different timelines than messaging APIs)

---

### System 7: DLP / PHI Pipeline
**Current state:** Custom Cloud Function + Google Cloud DLP pipeline for healthcare email (DLP-ARCHITECTURE.md). Only Stage 4 Layer A built; Stages 1-3 and 5-8 designed but not implemented.

**Why it must evolve:**
- Commercial DLP-as-a-service for agentic AI is shipping now (MIND, Forcepoint, Cyera AI Guardian)
- PHI detection NLP/NER models improving rapidly (better accuracy, lower false positive rates)
- Document layout-preserving redaction tools maturing
- Our custom pipeline requires ongoing maintenance and security updates
- The pipeline may be partially or fully replaceable by commercial solutions within 6-12 months

**Evolvability strategy:**
- **Subsumed under Security Architecture** as a high-churn component — reviewed as part of quarterly security deep dive
- Pipeline stages designed as independently replaceable modules (swap Stage 4 PHI detection without touching Stage 5 redaction)
- Evaluate build-vs-buy at each quarterly review: is our custom pipeline still the best approach, or has a commercial solution caught up?
- Input/output contracts defined for each stage — any PHI detector that meets the contract can be plugged in
- Maintain the "fail closed on uncertainty" principle regardless of which implementation powers each stage

**Review cadence:** Quarterly (as part of Security Architecture review)

---

### System 8: Regulatory / Legal Landscape
**Current state:** Product vision says "not therapy, not a medical device." No formal regulatory analysis until March 2026 deep dive.

**Why it must evolve:**
- FDA classification criteria for AI/ML SaMD are actively shifting
- State-level AI regulation is diverging rapidly (Illinois bans autonomous therapeutic AI; Colorado requires bias testing; California mandates chatbot safety protocols)
- EU AI Act (August 2026) classifies adaptive health AI as high-risk
- FTC investigating AI companion mental health harms
- The wellness/clinical boundary depends on our design choices — small changes can shift classification

**Evolvability strategy:**
- Maintain a living regulatory tracker by jurisdiction
- All user-facing language reviewed quarterly against current FDA/FTC/state guidance
- Product features designed with regulatory "escape valves" — any feature that risks clinical classification can be disabled or reframed without architectural change
- Legal review before any new jurisdiction launch

**Review cadence:** Quarterly (fastest-shifting regulatory environment in decades)

---

### System 9: Anti-Capture / Anti-Dependency Design
**Current state:** Anti-capture principle established in Product Vision. Evidence base: theoretical + adjacent (social media screen time). Zero RCTs validating any anti-dependency mechanism in AI companion settings.

**Why it must evolve:**
- This is an evidence vacuum that will fill rapidly as AI companion research matures
- Regulatory bodies (FTC, EU) are beginning to scrutinize engagement-driven design
- The features that drive engagement are structurally identical to those creating dependency
- New measurement frameworks (AIAS, AIDep-22) are enabling quantitative dependency assessment for the first time
- The "go stale" concept (dynamically stripping behavioral warmth when capture patterns detected) needs validation

**Evolvability strategy:**
- Commit to radical transparency: publish what we know, what we don't, and what we're doing about it
- Anti-capture parameters treated as testable hypotheses, not fixed design
- Incorporate new measurement tools (AIAS, reliance drills) as they mature
- "Designed for Obsolescence" applies here — current anti-capture mechanisms will be replaced when better evidence-based alternatives emerge
- Track our own longitudinal data as a research contribution

**Review cadence:** Annual deep dive + continuous monitoring of new publications + immediate review when significant research publishes

---

### System 10: Escalation System Design
**Current state:** INTERACTION-MODEL.md defines 4-level escalation. Level 4 contacts designated support person. Consent architecture designed but implementation-specific safeguards incomplete.

**Why it must evolve:**
- No legal framework governs autonomous AI third-party contact — we're in a regulatory gap that will be filled
- ADHD + rejection sensitivity dysphoria intersection is unexplored — escalation could cause harm in our primary user population
- Algorithmic monitoring perceived as more invasive than human monitoring
- Minors less likely to express distress if they know AI will notify parents (perverse incentive)
- OpenAI's "trusted contacts" and California's Parents & Kids Safe AI Act are setting new norms

**Evolvability strategy:**
- Escalation as user-controlled tool, not system-imposed consequence
- Pre-escalation notification to user with option to block
- Post-escalation check-in to measure helpfulness vs. harm
- Age-appropriate consent and disclosure architecture
- Regular reconsent cycles
- Complete user control to disable any level at any time
- Track escalation outcomes as research data to inform future design

**Review cadence:** Semi-annual + immediate review when relevant legislation passes

---

### System 11: Code Maintenance / Refactoring
**Current state:** No formal code maintenance architecture. Codebase growing across multiple skills, integrations, tools, and configurations.

**Why it must evolve:**
- Solo developer (J + AI) cannot manually maintain a growing codebase indefinitely
- Dependencies, APIs, and frameworks change constantly
- Security vulnerabilities in dependencies require continuous monitoring
- Technical debt accumulates faster than manual review can address
- AI-powered code maintenance tools are maturing rapidly

**Evolvability strategy:**
- Automated dependency management (Dependabot/Renovate for version bumps and security patches)
- CI pipeline for automated testing, linting, and code quality monitoring
- AI-assisted refactoring agents for routine code health tasks
- Documentation-as-code to keep docs synchronized with implementation
- Code health dashboard tracking coverage, dependency freshness, security posture
- Quarterly "maintenance sprint" dedicated to debt reduction

**Review cadence:** Quarterly

---

## 3. THE CONTINUOUS ARCHITECTURE REVIEW SYSTEM

Evolvability isn't just a design principle — it requires a structured, recurring process.

### 3.1 Quarterly Deep Dive (**Scaled-Operations Goal**)

> **At current scale:** These reviews are trigger-based, not calendar-based. Run a deep dive when something meaningful changes (new model release, security incident, API deprecation, regulatory shift), not on a fixed quarterly schedule. The quarterly cadence applies when the project has enough users and complexity to justify regular scheduled reviews.

**Scope:** Security Architecture, Agent Orchestration, LLM/Model Layer, Integration Layer, DLP/PHI Pipeline

**Process:**
1. **Landscape Scan** — Exhaustive deep-dive research on each domain's current state (products, frameworks, standards, pricing, capabilities)
2. **Gap Assessment** — Compare current architecture against landscape: What's changed? What new options exist? Where are we falling behind?
3. **Severity Classification** — For each gap:
   - **Cosmetic** — Nice to have, no urgency (log for future consideration)
   - **Incremental** — Meaningful improvement, can be scheduled (next quarter)
   - **Architectural** — Significant change needed, requires planning (next 2 quarters)
   - **Paradigm Shift** — Fundamental rethink required, initiate adversarial review immediately
4. **Upgrade Plan** — For Incremental and above: migration plan, risk assessment, rollback strategy
5. **Adversarial Review** — For Architectural and Paradigm Shift changes: full adversarial review before implementation

**Output:** Quarterly Architecture Review Report with findings, classifications, and recommended actions.

### 3.2 Annual Behavioral Science Review

**Scope:** Behavioral Science Operating System — core theories, implementation parameters, evidence updates

**Process:**
1. **Literature Scan** — New research on SDT, CPS, MI, and alternatives in AI-mediated contexts
2. **Evidence Ledger Update** — What have we confirmed, modified, or rejected from our own data?
3. **Framework Audit** — Are our core theories still the best available? What new frameworks have emerged?
4. **Parameter Review** — Are our implementation parameters (ratios, timing, language) supported by evidence?
5. **Neurodiversity & Ethics Review** — Are we still aligned with neurodiversity-affirming best practices?

**Output:** Annual Behavioral Science Review Report with updated evidence map and any recommended framework changes.

### 3.3 Monthly Lightweight Scan (**Scaled-Operations Goal**)

> **At current scale:** Folded into regular awareness — Synthia monitors AI news and flags developments that matter. Formal monthly scans begin when the project has a Tier 2 release.

**Scope:** All systems — quick check for urgent developments

**Process:**
1. Scan major AI news sources, research publications, and industry announcements
2. Flag anything that could trigger an out-of-cycle review
3. Brief summary (5-10 bullet points) of notable developments

**Output:** Monthly Architecture Pulse — brief notes in project memory, flagging anything requiring deeper attention.

### 3.4 Migration Playbooks

For every major component, maintain a migration playbook that answers:
- What does this component do? (capability description, not vendor description)
- What interface contracts does it conform to?
- What depends on it? (upstream and downstream)
- What would we need to do to replace it? (estimated effort, risk, downtime)
- What are the leading alternative candidates today?
- What's the rollback plan if migration fails?

**Update cadence:** Refreshed at each quarterly review.

---

## 4. THE META-PRINCIPLE: USE THE SYSTEM TO MAINTAIN THE SYSTEM

The agent orchestration capabilities we're building can (and should) be used to maintain the architecture itself:

- **Architecture Review Agent** — A specialized agent that runs quarterly landscape scans, compares findings against current architecture, and produces gap reports
- **Integration Health Monitor** — An agent that continuously monitors integration endpoints for deprecation warnings, error rate changes, and capability shifts
- **Evidence Tracker** — An agent that monitors behavioral science publications and flags relevant new research

This is not a future aspiration — it's a practical application of the agent orchestration system to reduce J's bottleneck role in architecture maintenance. The agents scan and report; J reviews and decides.

---

## 5. WHAT THIS COSTS

Evolvability isn't free. The costs are:

- **Upfront:** More time designing abstraction layers and interface contracts (estimated: 20-30% more initial design effort)
- **Ongoing:** Quarterly deep dives (~4-8 hours research + synthesis per quarter), monthly scans (~1 hour), annual behavioral science review (~4-6 hours)
- **Per-migration:** Each component swap requires planning, testing, and validation (highly variable — from hours to weeks depending on scope)

**What it saves:**
- Emergency rebuilds when a critical dependency changes without warning
- Vendor lock-in that prevents adopting better solutions
- Gradual degradation as the system falls behind the state of the art
- The "everything works but nothing is current" failure mode that kills products slowly

**The ROI argument:** A quarterly deep dive costs ~8 hours. An emergency rebuild of a tightly-coupled component costs weeks. The math is straightforward.

---

## 6. RELATIONSHIP TO OTHER DOCUMENTS

This document is a **cross-cutting architectural principle** that applies to every other ExecFunc document:

| Document | How Designed for Obsolescence Applies |
|----------|--------------------------------------|
| PRODUCT-VISION.md | Behavioral science framework treated as evolvable hypothesis, not permanent truth |
| SECURITY-ARCHITECTURE.md | Every security component independently replaceable; quarterly review cycle |
| DLP-ARCHITECTURE.md | Pipeline stages modular; build-vs-buy reassessed quarterly |
| INTERACTION-MODEL.md | Interaction parameters (timing, ratios, tone) treated as testable hypotheses |
| OPEN-SOURCE-PATH.md | Platform portability as design constraint; framework usable beyond OpenClaw |

---

## DOCUMENT HISTORY

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-03-20 | Initial architecture. Establishes evolvability as load-bearing requirement. Identifies 7 foundational systems (expanded to 11). Defines Continuous Architecture Review System. |
| 1.1 | 2026-03-21 | Added scale-appropriate cadence notes per M7. Quarterly cadences labeled "scaled-operations goal." Current-scale reviews are trigger-based. Comprehensive health check every 18-24 months (not annual). |

---

*The strongest systems aren't the ones that never change. They're the ones that were designed to change gracefully.*
