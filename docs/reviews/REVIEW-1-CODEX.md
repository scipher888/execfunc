# ExecFunc Founding Docs Adversarial Review

Overall verdict: the three documents mostly tell the same high-level story, but they are not yet tight enough to serve as durable founding documents for an open-source EF project. The Product Vision is the strongest document. The README is materially less careful than the Vision, and the Open Source Path still carries unresolved document-control, governance, safety, and commercialization assumptions.

## Findings

### 1. Critical — The README expands the user/clinical surface area while omitting the project's own safety boundaries

Evidence:
- `README.md:8` says ExecFunc is for "adults with ADHD, brain fog, TBI, or anyone who knows what they need to do but can't reliably make it happen."
- `PRODUCT-VISION.md:80-82` says ExecFunc is "Not a therapist," "Not a medical device," and "Not a safety monitor."
- `PRODUCT-VISION.md:179` says emergency/safety situations go to "988/911, never handled by AI."

Why this matters:
The public-facing entry point is the least careful document. "Brain fog" and especially "TBI" pull the project toward medically adjacent use cases, but the README does not surface any of the hard boundaries that the Product Vision relies on to stay honest and safe. A newcomer could reasonably infer broader clinical applicability than the project actually supports.

Recommendations:
- Add a short, explicit boundary box near the top of the README: not therapy, not crisis support, not a medical device, not for emergency use.
- Either remove "TBI" from the README for now or explain the narrow non-clinical sense in which the framework may still be useful.
- Add one sentence that the framework is evidence-informed but not clinically validated.

### 2. Critical — The family-first plan involves a minor and publishable family data, but the documents do not define consent, assent, or publication ethics

Evidence:
- `OPEN-SOURCE-PATH.md:58-60` includes "E (17)" as a planned user.
- `OPEN-SOURCE-PATH.md:75-78` describes parent/family escalation flows.
- `OPEN-SOURCE-PATH.md:123-127` promises results by family member, including "what worked and what didn't for each family member."
- `OPEN-SOURCE-PATH.md:143` promises "Results and evidence (anonymized)."
- `PRODUCT-VISION.md:336-337` covers profile isolation and escalation-message content, but not publication consent or minor-specific governance.

Why this matters:
This is not just a product-design issue. It is a household power-dynamics issue. A 17-year-old subject plus parent escalation plus public write-ups creates obvious risks around assent, surveillance, coercion, embarrassment, and future regret. "Anonymized" is not a sufficient policy, especially in a family-origin story where contextual clues can re-identify people.

Recommendations:
- Add a family data and publication policy before any public release.
- Define who can consent, who must assent, who can revoke, and what happens to already-collected data after revocation.
- State whether minors' data or stories will ever be published, even anonymously. A defensible default is: no minor case studies without explicit contemporaneous assent and a very high redaction bar.
- Define what parents can and cannot see by default, and how conflicts are resolved when "support" feels like surveillance.

### 3. Major — The core governing document is unclear because the Open Source Path keeps pointing to Product Vision v1.1 while the repo now has v2.0

Evidence:
- `OPEN-SOURCE-PATH.md:6` says "The Product Vision (v1.1) still governs what we build and why."
- `OPEN-SOURCE-PATH.md:25` says "Everything in the Product Vision v1.1 still applies."
- `OPEN-SOURCE-PATH.md:118` calls out "Product Vision v1.1."
- `OPEN-SOURCE-PATH.md:270` says the startup would inherit "The Product Vision v1.1."
- `OPEN-SOURCE-PATH.md:306` then says `PRODUCT-VISION.md` is "Product Vision v2.0 (open-source edition, governs all design)."
- `PRODUCT-VISION.md:501` says v2.0 was specifically "Adapted for open-source path."

Why this matters:
This is basic document control, and it currently fails. A reader cannot tell whether the authoritative philosophy is the archived startup-era document or the edited open-source edition. That weakens trust in every other claim about what changed and what did not.

Recommendations:
- Replace every governing reference to v1.1 with v2.0 unless the text is intentionally referring to the archived startup document.
- Add a one-line rule in both `README.md` and `OPEN-SOURCE-PATH.md`: "`PRODUCT-VISION.md` v2.0 is the active governing design document; v1.1 is archived for lineage only."
- Remove any remaining "v1.1 still governs" language.

### 4. Major — Foundational open-source decisions are still unresolved: license, governance, security reporting, and maintainer expectations

Evidence:
- `OPEN-SOURCE-PATH.md:133` says the project will be "Licensed permissively (MIT or Apache 2.0)."
- `README.md:86` says "MIT (planned)."
- `OPEN-SOURCE-PATH.md:161-163` assumes contributions and ongoing maintenance.
- `README.md:74-82` says contributions are not yet open, but gestures at future contribution areas.

Why this matters:
For an open-source project, these are not implementation details. They are founding-document basics. Right now the documents describe an open-source future without stating who governs the repo, how decisions get made, how security issues are reported, what support burden maintainers accept, or even what license the code will ship under.

Recommendations:
- Decide the license now and make all documents match.
- Add a minimal governance section: maintainer(s), decision-making authority, contribution-opening criteria, and support expectations.
- Add a security disclosure path and a statement about how vulnerability reports for integrations/secrets will be handled.
- If the answer is "family project first, public contributions later," say exactly what event opens that gate.

### 5. Major — The implementation plan does not yet operationalize the Product Vision's most important safeguards

Evidence:
- `PRODUCT-VISION.md:94-99` requires "minimum effective support," user choice, no pressure, and no brittleness.
- `PRODUCT-VISION.md:154` says Reflection mode must operate in "a separate conversational context."
- `PRODUCT-VISION.md:175-188` defines detailed escalation safeguards: user-configured levels, criticality set by the user, frequency caps, re-consent, revocation, and recalibration after bad escalations.
- `PRODUCT-VISION.md:178` requires a "Full audit trail of all escalations."
- `OPEN-SOURCE-PATH.md:176-185` lists skills, but does not say how these safeguards become concrete product requirements or release blockers.

Why this matters:
The philosophy is unusually careful. The roadmap is much looser. That creates the classic failure mode where the values remain in the vision doc while the shipped system follows whatever is easiest to build.

Recommendations:
- Add a "principle to mechanism" table to `OPEN-SOURCE-PATH.md`.
- For each core safeguard, specify the concrete enforcement mechanism and the release gate. Example: "No support-person escalation until revocation, re-consent, quiet hours, and audit logging exist."
- Separate "nice to have" skills from "non-negotiable safety/agency controls."

### 6. Major — Action-taking scope is ambiguous even though the Product Vision defines high-risk behavior that requires much stronger controls

Evidence:
- `PRODUCT-VISION.md:300-316` defines Tiers 3-5, including scheduling, orders, payments, cancellations, allowlists, receipts, and undo windows.
- `OPEN-SOURCE-PATH.md:80-84` says Phase 1 includes "Task execution" via calendar, reminders, email awareness, and deep links.
- `README.md:10` says ExecFunc makes an AI "actually useful for executive function," but does not state what action tiers are or are not in scope.

Why this matters:
The docs currently leave too much room for interpretation about what the early system can do. That is risky for both builders and future users. The Product Vision is explicit that not all actions are equal; the implementation plan should be equally explicit about what is disabled until stronger controls exist.

Recommendations:
- Declare the action-tier scope for Phase 1 and the first public release.
- A sensible default is: public v1 supports Tiers 1-3, selected Tier 4 scheduling with confirmations, and excludes Tier 5 entirely.
- Add a release checklist for any feature that can send, book, pay, cancel, or contact third parties.

### 7. Major — The pivot section still reads partly like startup wish-casting rather than a hard decision framework

Evidence:
- `OPEN-SOURCE-PATH.md:263` uses "open-source adoption, newsletter audience asking 'can I pay for this?', inbound interest from ADHD community" as demand signals.
- `OPEN-SOURCE-PATH.md:169-170` says "The open-source community becomes the initial user base" and "The newsletter audience becomes the launch list."
- `OPEN-SOURCE-PATH.md:272-273` says the startup inherits "The newsletter audience" and "The brand and story."
- `OPEN-SOURCE-PATH.md:264` makes the startup case partly contingent on whether "Apple/Google/OpenAI ship an EF-specific companion."

Why this matters:
Those are soft signals, not a real commercialization test. Open-source usage is not willingness to pay. Newsletter interest is not retention, supportability, regulatory feasibility, or distribution durability. And "big platform competitor exists or not" is not a sufficient decision criterion for whether a niche product should exist.

Recommendations:
- Rewrite Section 6 as a gated decision memo, not a narrative option.
- Define hard thresholds: repeated external setup success, retention, user outcomes outside the founding family, support burden, security maturity, and some credible signal of willingness to pay.
- Add a "do not start a company if..." list. Example: if the open-source project is useful only with founder-level handholding, if high-risk integrations remain brittle, or if the values cannot survive commercialization.

### 8. Major — The open-source security and privacy model is too thin for the capabilities being proposed

Evidence:
- `PRODUCT-VISION.md:334-345` describes local files, DLP redaction, profile isolation, and some open-source privacy guidance.
- `OPEN-SOURCE-PATH.md:97-98` says data lives in workspace files and structured JSON, with "No external database needed."
- `OPEN-SOURCE-PATH.md:192-195` relies on Gmail/Calendar, reminders, memory files, and a DLP pipeline.
- `README.md:52-58` lists only high-level requirements.

Why this matters:
An EF companion that touches email, calendars, reminders, messaging, and potentially escalation contacts is a secrets-and-integrations project. The current documents talk about privacy philosophy, but not operational security: token scoping, secret storage, host hardening, backup/retention, audit access, incident response, or safe defaults for contributors and self-hosters.

Recommendations:
- Add a minimum safe deployment guide for open-source users.
- Define secret-handling requirements, least-privilege scopes, logging boundaries, retention, and recommended host assumptions.
- Add a threat-model appendix for the first public release.

### 9. Minor — The README is understandable at a high level, but it is not yet strong enough as a first touchpoint

Evidence:
- `README.md:10` says "It is not an app" and frames the project as a framework on OpenClaw.
- `README.md:33-41` lists six skills under "OpenClaw Skills (Building)."
- `README.md:61` says the project is "Early development."

Why this matters:
A newcomer can understand the general idea, but the README still leaves three basic questions fuzzy: what is in this repository today, what a user interaction actually looks like, and who should not use this. Right now it reads more like a prospectus than a concrete repo landing page.

Recommendations:
- Add a 30-second example flow: a missed appointment, escalating texts, optional support-person contact.
- Add a "Current contents" section that says this repo currently contains founding docs and planned skills, not a finished package.
- Move the most important safety/scope disclaimers above the philosophy section.

### 10. Minor — Residual startup language weakens the credibility of the open-source pivot

Evidence:
- `OPEN-SOURCE-PATH.md:156` says "This is the content strategy that the startup plan never had."
- `OPEN-SOURCE-PATH.md:170` says "The newsletter audience becomes the launch list."
- `OPEN-SOURCE-PATH.md:273` says the startup inherits "The brand and story (the credibility)."
- `OPEN-SOURCE-PATH.md:288-289` spends energy arguing this path is "Not a lesser version of the startup" and "Not permanent."

Why this matters:
The documents say "family-first, open-source" but parts of the roadmap still read like a pre-startup staging area. That may be true strategically, but if so, say it more plainly. Otherwise the pivot can look emotionally unresolved.

Recommendations:
- Strip or soften marketing language unless the real intent is explicitly "open-source first, possibly commercial later."
- Reframe the newsletter as documentation and public learning, not distribution.
- Decide whether open-source is a destination with optional commercialization, or a temporary proving ground. The current documents want both.

## Consistency Summary

The good news: the central philosophical story is mostly consistent across all three files. They agree that ExecFunc is an assistive, anti-capture, family-first AI companion framework rather than a reminder app or therapeutic product.

The weak points are structural, not thematic:
- the Open Source Path still references the wrong governing version of the Product Vision;
- the README is less bounded and less cautious than the Product Vision;
- several open-source fundamentals are still aspirational rather than decided.

## Missing Pieces

The documents should add, at minimum:
- an explicit README safety/scope section;
- a family consent, assent, and publication policy;
- a real open-source governance and license decision;
- a security disclosure and safe-deployment posture;
- a principle-to-implementation matrix tying anti-capture and escalation safeguards to concrete release gates;
- a harder, more falsifiable pivot rubric.

## Bottom Line

This is close to a coherent founding set, but not yet publish-ready as-is. The Product Vision has done the hardest intellectual work. The next step is to make the README and Open Source Path as disciplined as the Vision, especially around scope control, minor/family data ethics, OSS governance, and commercialization realism.
