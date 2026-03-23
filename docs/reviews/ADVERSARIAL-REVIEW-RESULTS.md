# ExecFunc — Adversarial Review Results

## Executive Summary

The architecture is not merely "ambitious." It is currently internally inconsistent at the level of product category, safety model, and deployment scope. It tries to be all of the following at once:

- a wellness tool
- a clinically-adjacent adaptive intervention system
- a family coordination layer
- an emotionally coherent companion
- an anti-capture experiment
- an open-source framework for unknown users
- a possible future regulated product

Those modes have different duties of care, different failure modes, and different acceptable defaults. The brief repeatedly attempts to solve category conflicts with transparency, user control, or future evidence generation. That is not enough. Transparency is not a control. User choice is not a substitute for safe defaults. Future evidence does not justify present exposure of vulnerable users.

My bottom-line judgment: the current architecture is not launch-ready for minors, not ready for broad open-source release to vulnerable users, and not coherent enough to defend as a "wellness" product if the actual behavior includes adaptive intervention, passive monitoring, vulnerability segmentation, and support-network escalation. The only credible near-term path is to cut scope hard: founder-only or consenting adult utility assistance, no minors, no passive risk profiling, no dynamic warmth modulation, no safety-positioned escalation, and one authoritative security posture.

## Critical Findings

### 1. The "wellness" posture does not survive the actual capability set
Severity: CRITICAL

The brief wants the legal and reputational advantages of a wellness tool while adopting the behavioral machinery of a clinical intervention system: JITAI, passive monitoring, adaptive decision rules, vulnerability-linked support profiles, therapist-supervised modes, and age-based safeguards. That is a capability mismatch, not just a messaging risk.

The core contradiction is explicit. The brief proposes JITAI as the primary operating framework and applies it "at the meta-level" to adapt the intervention itself. It then notes that FDA treats autonomously delivered interventions based on detected user-state trends as trending toward medical-device classification. It simultaneously wants adults to get a "full-featured wellness app" and minors to get therapist-supervised or behaviorally modified modes. That is not a stable category boundary. It is regulatory arbitrage by wording.

This also conflicts with the current public posture. `PRODUCT-VISION.md` and `README.md` say ExecFunc is not a medical device and does not make clinical inferences. But risk-stratified support profiles for ADHD, OCD/anxiety, perimenopause/brain fog, and minors are exactly condition-linked inferences, even if the user self-selects first.

Resolution / question: pick one architecture. Either:

- a true wellness/utility tool with fixed behavior, no passive vulnerability profiling, no adaptive behavioral intervention rules, and no minors

or

- a clinical-adjacent product with an explicit regulatory strategy, bounded claims, and real governance.

Trying to keep the adaptive stack while hiding behind wellness language is the least defensible option.

### 2. The minors architecture is unsafe, incoherent, and likely ungovernable
Severity: CRITICAL

The minor design combines the highest-risk user group with the weakest operational clarity. The brief gives minors their own data-visibility control and escalation preferences, allows pre-escalation approval/decline, proposes therapist-supervised mode or "stale" mode, and requires parent/minor joint consent. `OPEN-SOURCE-PATH.md` goes further: each minor controls what parents can see, parents cannot override for non-safety tasks, and the system never shares reflection content or emotional state with parents.

This creates an impossible governance triangle:

- minors are high-risk and developmentally still forming habits
- parents retain legal and practical responsibility
- the system is supposed to help exactly when self-regulation is failing

At 13, "self-selection" is not a meaningful safeguard. At 17, it is still unstable in high-distress situations. The architecture has not defined age bands, emergency exceptions, mandated supervision standards, parental override boundaries, or how to handle conflict between assent, privacy, and duty of care.

Worse, the brief uses minors as a core design case before resolving whether the product is even wellness or clinical. That is upside-down prioritization. You do not use minors to pressure-test an unresolved adult architecture.

Resolution / question: remove minors from the product scope entirely until there is:

- an age-banded policy model
- a clinician-governance model
- an abuse/coercion threat model
- a sharply defined emergency exception matrix
- jurisdiction-specific legal review

Without that, "family-first" becomes a justification for testing the hardest safety case with the weakest guardrails.

### 3. The escalation redesign removes the one thing escalation is for
Severity: CRITICAL

The redesign reframes escalation as a user-controlled tool: pre-escalation notification, real-time blocking, post-escalation feedback, full disablement, reconsent cycles, and, for minors, notification before family contact with approval/decline. That maximizes autonomy precisely where the architecture previously assumed autonomy had failed.

This is not a small design tension. It invalidates the safety logic of the feature.

If a user is able to evaluate a pre-escalation notice and decide whether to block it, then the system is no longer acting as a fallback for non-response or impaired action. It is simply offering another prompt. If the user is not able to respond, the system either waits and risks harm or proceeds and violates the autonomy framing it just promised. The redesign tries to have both non-authoritarian legitimacy and last-resort efficacy. It does not get both.

The contradiction with the existing `INTERACTION-MODEL.md` is stark. The current model treats Level 4 as a circuit breaker for urgent items after 30 minutes of non-response. The redesign turns that circuit breaker into a permission dialog.

Resolution / question: split escalation into distinct systems.

- Routine accountability/logistics escalation: fully optional, non-safety, user-driven.
- Welfare/safety escalation: either remove it entirely from ExecFunc, or restrict it to extremely narrow, pre-authorized cases with rules that are not blockable at the moment of crisis.

Do not pretend one mechanism can simultaneously be autonomy-maximizing and failure-of-autonomy fallback.

### 4. "Go stale" is a speculative anti-capture intervention built from the same mechanisms that create capture
Severity: CRITICAL

The architecture intentionally builds warmth, memory, consistency, relational trust, and personality. It then proposes a novel anti-capture safeguard that dynamically removes warmth/personality when capture risk is detected. This is not just unvalidated. It may be directionally dangerous.

The same brief that proposes MIRA also notes mechanisms like psychological proximity, interpersonal trust, and relational substitution vs. enhancement. `INTERACTION-MODEL.md` says "the relationship is the product." `PRODUCT-VISION.md` says the relationship is a trust mechanism. The system is therefore deliberately cultivating the relational substrate, then proposing to withdraw it when the user's attachment patterns become concerning.

That can look and feel like withdrawal, punishment, abandonment, or sudden coldness from a trusted entity. For anxious, rejection-sensitive, or attachment-vulnerable users, that may worsen exactly the harms the safeguard claims to prevent. The brief even asks whether a user who relies on warmth for emotional regulation could be destabilized. Yes. That is not a side question. That is the central failure mode.

Resolution / question: do not ship dynamic warmth modulation as a foundational safety feature. Replace it with static constraints:

- limits on proactive volume
- hard bans on intimate/possessive language
- session boundaries
- clear offboarding/export paths
- friction against compulsive checking
- explicit human-connection nudges

If "go stale" is studied at all, it should be manual, gradual, reversible, and clearly framed as a user-selected mode change, not an automated behavioral intervention.

### 5. The security posture is split across incompatible realities
Severity: CRITICAL

There is no single authoritative answer to what data ExecFunc actually touches.

`README.md`, `PRODUCT-VISION.md`, and `OPEN-SOURCE-PATH.md` present the family/open-source posture as manual forwarding of non-sensitive email, calendar as primary data source, and no direct inbox access. `SECURITY-ARCHITECTURE.md` argues the vision requires deep integration with email, medical records, financial accounts, insurance, and legal docs, and says the AI only solves ~20% of drudgery without full access and ~90%+ with it. `DLP-ARCHITECTURE.md` says the current system already pulls work email through a Cloud Function and that only Stage 4 Layer A is implemented.

That is not just documentation drift. It is a safety-critical inconsistency about the actual attack surface.

The most dangerous version is that aspirational full-access docs normalize behavior that the safer public docs explicitly reject. The second-most dangerous version is that public docs understate what the current private system already does. Both are bad. Users, contributors, and future maintainers need one truth.

Resolution / question: establish one canonical current-state deployment boundary and demote everything else to clearly labeled future-state docs. Add a rule: no public or internal "current state" doc may advertise access or protections that do not actually exist in the implementation.

### 6. The family-to-open-source generalization is methodologically invalid and ethically risky
Severity: CRITICAL

The brief repeatedly treats the family build as evidence-generating groundwork for open-source release. That leap is much larger than the documents admit.

The family environment has safety properties that unknown users will not have:

- preexisting trust and context
- an established relationship with Synthia
- real humans who already care and can intervene
- technical sophistication
- founder oversight
- shared norms and implicit knowledge

Those conditions are doing enormous hidden safety work. They reduce misinterpretation, shorten feedback loops, and make escalation socially legible. None of that transfers automatically to an unknown adult self-hoster, much less an anxious user, an isolated user, or a minor deployed by a parent.

Open-sourcing this before the architecture is segmented is not neutral "sharing." It exports a safety model that depends on invisible founder/family context.

Resolution / question: split the project into separate artifacts with separate claims:

- private family operating system
- adult self-hosted utility framework
- future high-risk/clinical exploration

Do not present one as proving the safety of the others.

### 7. There is no credible harm-containment plan if the system starts causing the harms it is worried about
Severity: CRITICAL

The brief explicitly raises the question of what happens if dependency metrics show the product is causing harm. It admits the contingency planning is absent. That is not a minor gap. For a system aimed at people with ADHD, anxiety/OCD, and minors, it is a stop-ship issue.

Current safety responses are mostly observational:

- self-report QoL
- social connectedness checks
- quiet-day brittleness tests
- post-escalation feedback
- future measurement tools

None of those specify thresholds, mandatory interventions, feature shutdown conditions, user notification protocols, support-person notification protocols, or rollout rollback. Transparency about the evidence vacuum does not compensate for the absence of a concrete response plan.

Resolution / question: define before any broader deployment:

- adverse-event taxonomy
- escalation-harm thresholds
- dependency-harm thresholds
- automatic and manual feature disablement rules
- user communication templates
- offboarding/export flow
- who decides and on what evidence

If you cannot answer "what do we do when the safeguard fails?" then the safeguard is not operational.

## Major Findings

### 1. The behavioral-science pivot lacks a coherent causal model
Severity: MAJOR

The brief replaces SDT/CPS/MI with JITAI + MIRA + neurodiversity-affirming approaches, but it never cleanly states what causal work each framework is doing, how they interact, or what happens when they disagree.

JITAI is a timing/adaptation framework. MIRA is a human-AI relational dynamics framework. Neurodiversity-affirming practice is an orientation toward identity, strengths, and support. Those are not interchangeable levels of abstraction. They can be combined, but only if you have a causal model that says:

- which outcomes matter
- what mechanism each framework controls
- what optimization target is primary when they conflict

Right now the pivot reads less like a coherent operating system and more like selecting the newest or most AI-relevant frameworks because the current stack feels insufficient.

Resolution / question: produce a one-page causal model before implementation. Define:

- outcome variables
- mechanism variables
- framework-to-mechanism mapping
- failure modes
- which framework has veto power when objectives conflict

### 2. Risk stratification by user category is quasi-diagnostic profiling in all but name
Severity: MAJOR

The proposed categories are explicitly condition-linked: ADHD adults, anxiety/OCD, perimenopause/brain fog, minors with ADHD, neurotypical drudgery. The system then adapts safeguard intensity based on those categories and passive monitoring. That is vulnerability profiling, even if users self-select first.

This directly conflicts with current claims in `PRODUCT-VISION.md` that ExecFunc does not make mental-health inferences and is not a medical device. It also increases stigma, misclassification, and path dependence: once a user is in a category, the architecture starts interpreting behavior through that lens.

Resolution / question: replace diagnosis-like support profiles with capability-and-preference modules:

- desired reminder intensity
- impulse-protection features
- reassurance-limiting features
- support-network preferences
- warmth level

Do not bake condition labels into the control plane.

### 3. The interaction model uses engagement optimization logic that undermines anti-capture claims
Severity: MAJOR

`INTERACTION-MODEL.md` opens with "The relationship is the product" and grounds itself in Gottman 5:1, Cialdini, and BJ Fogg. It explicitly aims for J to want to hear from Synthia. That is engagement-optimization language. It may be well-intentioned, but it is structurally the same class of design logic used to increase attachment and habitual return.

This clashes with `PRODUCT-VISION.md`, which says the relationship is a trust mechanism, not a growth lever, and that the AI is a coach, not a friend. It also clashes with the anti-capture posture that treats relational substitution as a harm vector.

The risk is not only philosophical hypocrisy. It is practical incentive drift. Once the system starts treating positive message volume and desire-to-hear-from-the-AI as markers of health, it is already optimizing the wrong thing.

Resolution / question: rewrite the interaction model around bounded utility, not relationship maintenance. Remove persuasion frameworks unless you can state hard, testable negative constraints on how they may be used.

### 4. The "value surplus" ratio is easy to game and may incentivize attention capture
Severity: MAJOR

The 5:1 ratio sounds prudent, but the implementation creates a bad control target. The system can improve the ratio simply by adding more "gifts" like briefings, digests, and proactive informational content. That does not necessarily mean it is less demanding. It may just mean it is more present.

This is especially problematic for anti-capture. A system that wants to preserve a positive/demand ratio can flood the user with low-stakes value content, increasing notification salience, habitual checking, and emotional presence. The metric then rewards the very thing you claim to fear.

Resolution / question: stop using message-count ratio as a primary health indicator. Track user-reported interruption burden, compulsive checking behavior, mute/dismiss behavior, and whether the user can ignore the system without distress.

### 5. The anti-capture metrics confuse legitimate accommodation with harmful capture
Severity: MAJOR

`PRODUCT-VISION.md` rightly argues that assistive support is legitimate and that permanent support can be a success. But the anti-capture plan relies on "AI goes quiet" tests, brittleness checks, and reliance drills. Those are not obviously compatible with the assistive-tech analogy.

A person with glasses is worse off without glasses. That alone does not prove pathological dependency. An ADHD support system that externalizes working memory will, by design, create some meaningful reliance. Treating service interruption as the core diagnostic for harm risks pathologizing legitimate accommodation.

This matters because it feeds directly into "go stale" and other support-reduction ideas. The architecture has not drawn a rigorous line between:

- acceptable tool dependence
- harmful agency erosion
- harmful social displacement

Resolution / question: define anti-capture against the right harms: coercion, shame, social replacement, narrowing of decision ownership, compulsive reassurance loops, inability to stop using the tool by choice. Do not use mere decrement-without-tool as the primary indicator.

### 6. Tiered autonomy is founder-compatible, not obviously user-compatible
Severity: MAJOR

The brief says the founder's role shifts from executor to editor and proposes async review for medium-risk work. That makes sense for a technically sophisticated builder. It is not obvious that it makes sense for the target population of adults who already struggle with initiation, review, follow-through, and task switching.

The danger is offloading executive overhead from execution to supervision. You have not removed the burden; you have changed its shape. Reviewing queued actions, drafts, thresholds, consent states, and escalation settings is still executive work.

Resolution / question: define a maximum acceptable review burden for non-founder users. If the product requires users to be good editors, it is solving the wrong user's problem.

### 7. Designed for Obsolescence is overbuilt relative to the available human bandwidth
Severity: MAJOR

Quarterly deep dives across multiple system domains, annual behavioral reviews, monthly scans, migration playbooks for every major component, and agent-maintained architecture reports are plausible inside a staffed company. They are much less plausible inside a family side project with 5-10 hours/week.

The risk is not merely fatigue. It is displacement of the core work:

- building daily-use utility
- validating whether the product actually helps
- tightening one or two critical safety boundaries

There is a real chance this becomes architecture theater: elegant abstractions and review cadences around a product whose core use loop is still unproven.

Resolution / question: downgrade the process to trigger-based reviews for now. Only add abstraction where there is a demonstrated replacement horizon and real migration cost.

### 8. The build-vs-buy security plan ignores operational fit for self-hosters and family scale
Severity: MAJOR

The security plan names enterprise-grade tools such as Entra, Vault, SIEM, Forcepoint/Purview/MIND, and runtime guardrails, but the project is positioned as family-first and later open-source. There is no serious discussion of:

- cost
- maintenance burden
- complexity for self-hosters
- false-positive operational load
- vendor lock-in

This is a pattern throughout the docs: borrowing institutional security language to support a consumer/family project without proving the operational path exists for the actual deployment model.

Resolution / question: define separate security baselines for:

- founder/private use
- advanced self-hosters
- hypothetical commercial deployment

Do not write one blended architecture that only enterprises can realistically operate.

### 9. Personality portability is asserted, not demonstrated
Severity: MAJOR

The brief says personality lives in files and the model is a substrate. That is partly true and still materially incomplete. In practice, the user-visible personality is co-produced by:

- model priors
- tool use quality
- memory retrieval quality
- phrasing style
- refusal style
- latency and turn-taking feel

The docs themselves admit Synthia already exists as a relationship and that Claude-specific behavior patterns are part of what makes her feel like Synthia. That means model migration is not a backend refactor. It is a user-facing relational and safety event.

Resolution / question: treat model swaps like product changes requiring user testing and safety verification. Do not rely on abstraction-layer language to hide the experiential break.

### 10. Platform portability is likely wishful unless enforced immediately
Severity: MAJOR

The project is explicitly being built as OpenClaw skills on OpenClaw infrastructure with cron, memory files, Telegram integration, and OpenClaw-specific capabilities. Saying "portable core, thin wrapper" is easy. Keeping it true while shipping fast is hard.

Portability usually fails because local convenience wins. By the time portability matters, the OpenClaw assumptions are everywhere.

Resolution / question: if portability matters, enforce it in code now with a shared core library and explicit adapter boundaries. Otherwise stop claiming it as a near-term architectural property.

### 11. Therapist integration is treated as a feature flag, but it is actually an operating model
Severity: MAJOR

The brief proposes therapist-supervised mode for minors and optional therapist integration for adults who want clinical features. That sounds modular. It is not.

Therapist integration raises unaddressed questions:

- what counts as supervision
- how frequently the therapist reviews
- how the therapist receives context
- what licensure is acceptable
- who is liable when the therapist does not respond
- whether the therapist is treating the user or merely consulting on software behavior

This is not a UI option. It is a care-delivery model.

Resolution / question: remove therapist integration from the architecture until there is a concrete workflow, scope-of-practice model, and liability analysis.

### 12. The DLP roadmap is strategically confused
Severity: MAJOR

The documents simultaneously say:

- automated inbox scanning is deferred because no viable solution exists for the family/open-source build
- the current DLP pipeline works for J's personal use
- only Stage 4 Layer A exists
- the full pipeline could be built in months
- commercial DLP will probably replace it anyway

That is four different strategic postures at once: defer, use, build, replace. The result is predictable: unclear current risk, unclear investment priority, and unclear public message.

Resolution / question: choose one near-term stance. The cleanest answer is:

- no healthcare email integration for public release
- private pipeline stays private and explicitly experimental
- revisit build-vs-buy only if the project becomes commercial or healthcare use becomes unavoidable

### 13. The naming and public framing still read as clinically suggestive
Severity: MAJOR

The product is called `ExecFunc`. The README centers executive-function challenges and specifically adults with ADHD. The architecture is full of behavioral scaffolding, escalation, support profiles, and therapist options. Saying "we never say treat ADHD" does not erase the surrounding context.

This may matter for users, regulators, journalists, platform reviewers, and potential critics. Language does not exist in isolation from function and audience.

Resolution / question: either embrace the assistive/clinical-adjacent framing and build accordingly, or rename/reframe the public artifact around mundane personal operations.

### 14. The measurement plan is too weak to support public claims
Severity: MAJOR

The proposed evidence generation relies heavily on family self-report, weekly check-ins, usage metrics, and qualitative observation. That may be enough for internal learning. It is not enough to support stronger claims or open-source advocacy about what "works."

The biases are obvious:

- founder as builder and participant
- family social pressure
- novelty effects
- no comparator
- no blinded interpretation

If this gets written up publicly as evidence that persistent AI companions improve executive function, the methodological weakness will be an easy target.

Resolution / question: sharply limit claims from family data. If public evidence matters, define minimal evaluation rigor now, including baselines, adverse-event logging, and external review of interpretations.

### 15. The integration strategy assumes standards will remove the hardest work
Severity: MAJOR

The brief points to MCP, unified APIs, and FHIR as the integration strategy. That is directionally sensible and still under-argued. Standards reduce some friction. They do not remove the hardest problems in this product:

- provider-specific workflow differences
- brittle auth and token-refresh behavior
- incomplete or delayed healthcare data
- lack of universal messaging standards
- deeply human tasks like phone-tree navigation and exception handling

FHIR in particular is easy to invoke as the healthcare answer and much harder to use as the operational answer for a personal executive-function companion. Availability, scope, write permissions, latency, and data completeness vary widely by provider and use case. The brief treats the abstraction layer as more mature than the real-world integration surface.

Resolution / question: prove the architecture on a tiny number of concrete end-to-end integrations before generalizing. One calendar stack and one low-risk healthcare read path are more valuable than a generic integration story.

### 16. The solo-launch and AI-assisted maintenance plan is not operationally credible as written
Severity: MAJOR

The brief and surrounding docs assume all of the following can coexist on 5-10 hours/week:

- core product development
- family onboarding and retrospectives
- security hardening
- quarterly architecture reviews
- evidence tracking
- documentation for open source
- community building
- newsletter/public writing
- AI-assisted refactoring and code maintenance

That is not a side-project roadmap. It is a small program office. The likely result is partial implementation everywhere and validated safety nowhere.

AI-assisted maintenance also does not remove the need for review. In a safety-sensitive project, automated refactors without strong test coverage can silently widen the blast radius.

Resolution / question: pick a ruthless sequence. Build the narrow adult utility loop first, add tests before relying on AI maintenance, and defer publication/community work until the core system is stable and the safety boundary is real.

## Minor Findings

### 1. Reconsent cadence appears arbitrary rather than evidence-based
Severity: MINOR

Quarterly for adults and "more frequent for minors" sounds thoughtful but currently looks invented. Too infrequent and consent drifts. Too frequent and the process becomes wallpaper.

Resolution / question: tie reconsent to material changes in capability, support-person configuration, or risk posture, not just the calendar.

### 2. "Stale mode" is a poor user-facing concept
Severity: MINOR

The label reads as punitive, degraded, or emotionally withholding. If the mode is meant to be a neutral low-warmth utility setting, the name works against that goal.

Resolution / question: rename it to something descriptive and non-judgmental, or keep it as an internal research label only.

### 3. The current interaction examples normalize a high proactive message volume
Severity: MINOR

The interaction model counts multiple early-morning informational pushes as positives and treats that as health. Even if the ratio is favorable, the absolute message volume may still be irritating or habit-forming.

Resolution / question: track absolute proactive volume and mute behavior, not only the positive/demand ratio.

### 4. The project already has serious version-skew between canonical docs
Severity: MINOR

The brief explicitly says the underlying documents are not yet updated with today's decisions, and the contradictions are already significant. This is governance debt, not just editorial debt.

Resolution / question: designate one canonical architecture index and mark any superseded doc as superseded immediately, not after a later cleanup pass.

### 5. The security-disclosure and governance signals are more mature than the actual operating model
Severity: MINOR

The repo presents a security disclosure email and governance posture that imply a more stabilized public project than the architecture supports today. That creates credibility risk if the public surface outpaces the real safety story.

Resolution / question: keep public governance modest until there is a stable release boundary and an actual response process.

### 6. Crisis language is under-specified
Severity: MINOR

The docs say crisis situations go to 988/911 and that the AI is not crisis support, but they do not define what the system does when users mention self-harm, domestic abuse, medication misuse, or acute panic in the middle of otherwise ordinary workflows.

Resolution / question: add a narrow crisis-handling protocol or explicitly declare that the system does not attempt crisis interpretation at all.

## Cross-Cutting Concerns

- The project repeatedly tries to solve capability risk with language. That will not hold. Regulators, critics, and harmed users look at what the system does, not what it calls itself.
- The project repeatedly tries to solve safety risk with user choice. That is especially weak for people whose core problem is inconsistent self-regulation.
- The anti-capture strategy repeatedly adds new adaptive control loops to solve risks created by the existing adaptive control loops.
- The architecture depends heavily on founder context, prior relationship, and family dynamics while describing itself as a portable framework.
- The documents oscillate between "assistive reliance is fine" and "meaningful degradation without the AI is a warning sign." That philosophical contradiction infects the metrics, escalation design, and anti-capture proposals.

## What's Missing

These are not side issues. They are absent design areas that should exist before broader deployment.

1. Exclusion criteria. Who should explicitly not use ExecFunc in its current form?
2. Abuse/coercion threat model. What if a parent, spouse, or support person uses the system for surveillance or control?
3. Adverse-event taxonomy. What counts as a psychological, social, or relational safety incident?
4. Stop-ship and rollback criteria. What exact findings would pause rollout or remove a feature?
5. Offboarding/export plan. How does a user safely leave without abrupt relational rupture or data loss?
6. Consent-comprehension design. How do you confirm that cognitively overloaded users or minors actually understand what they are enabling?
7. Family-systems risk model. What happens when one companion identity mediates multiple family relationships and conflicts?
8. Support-person operating model. What training, burden limits, and opt-out rights do support persons have?
9. External-oversight plan. Who outside the founder/family reviews high-risk design changes before rollout?
10. Model-failure protocol. What happens when the provider changes behavior, memory fails, or the identity feels "off"?
11. Jurisdiction-gating strategy. Illinois is mentioned; there is no actual launch/no-launch matrix by geography.
12. Secure defaults for self-hosters. Which features are off by default, and what warnings gate high-risk capabilities?
13. Prompt-injection and social-engineering threat model for convenience data. The security docs mention it only indirectly.
14. Evidence publication standard. What claims will you refuse to make from family data, even if the results look good?

## Final Verdict

The current architecture is not defensible as a single coherent product. It is a stack of partially incompatible ambitions held together by honesty, future research, and user control. Honesty is valuable. It is not enough.

The highest-risk problems are not small implementation gaps. They are category errors:

- wellness language over clinical-style adaptation
- autonomy framing over fallback/safety logic
- anti-capture goals pursued through relational optimization
- family evidence stretched toward public deployment
- public safety claims built on contradictory security realities

If you want the safest credible path forward, narrow the system aggressively:

1. Adult founder-only or consenting adult utility mode only.
2. No minors.
3. No passive vulnerability profiling by condition category.
4. No automated "go stale."
5. No safety-positioned support-person escalation beyond narrow logistical use.
6. One canonical security posture: manual forwarding and low-risk integrations only.
7. Public release only after the project is explicitly segmented into low-risk public framework vs. high-risk private/experimental components.

Until those changes are made, broad launch would be irresponsible, and minors deployment would be especially hard to defend.
