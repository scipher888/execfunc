# ExecFunc Founding Docs Final Review

## Bottom Line

The revision closed most of the first-pass issues. These documents are now close to credible founding docs. What still matters is document discipline, not philosophy: resolve the license/security placeholders, align the minor-privacy rules across docs, and remove a few lines that still read like a private memo instead of a public project charter.

## Original Findings Status

| # | Status | Assessment |
|---|---|---|
| 1 | **Adequately addressed** | README now opens with hard safety boundaries and an "evidence-informed, not clinically validated" disclaimer, and the broader `TBI` language is gone (`README.md:6-17`). |
| 2 | **Adequately addressed** | A real family consent/assent/publication policy now exists, including withdrawal handling, parent visibility rules, and minor-specific escalation safeguards (`OPEN-SOURCE-PATH.md:105-130`). |
| 3 | **Adequately addressed** | `OPEN-SOURCE-PATH.md` now consistently treats `PRODUCT-VISION.md` v2.0 as the governing document and isolates v1.1 to lineage/archive references (`OPEN-SOURCE-PATH.md:6`, `OPEN-SOURCE-PATH.md:25`, `OPEN-SOURCE-PATH.md:406-415`). |
| 4 | **Partially addressed** | Governance is much clearer and README now says MIT, but the Path still says `MIT or Apache 2.0`, and the security disclosure path is still `TBD` (`README.md:103-110`, `OPEN-SOURCE-PATH.md:195`, `OPEN-SOURCE-PATH.md:380-382`). |
| 5 | **Adequately addressed** | The safeguard-to-mechanism matrix and release-blocker rule now operationalize the Product Vision instead of leaving it aspirational (`OPEN-SOURCE-PATH.md:147-165`). |
| 6 | **Adequately addressed** | Phase 1 action scope is now explicit: Tiers 1-3 full, limited Tier 4, Tier 5 excluded (`OPEN-SOURCE-PATH.md:132-145`). |
| 7 | **Adequately addressed** | The pivot section is now a real decision framework with hard thresholds and a `Do NOT start a company if:` list (`OPEN-SOURCE-PATH.md:317-353`). |
| 8 | **Partially addressed** | Security/privacy posture is materially better, but it is still partly future-tense for public users and leaves disclosure/contact unresolved (`OPEN-SOURCE-PATH.md:357-382`, `README.md:109`). |
| 9 | **Adequately addressed** | README now shows the safety boundary, an interaction example, and what is actually in the repo today (`README.md:6-9`, `README.md:32-61`, `README.md:71-101`). |
| 10 | **Adequately addressed** | Most residual startup language is now bounded by the threshold framework. The remaining commercial option reads controlled, not wish-casting (`OPEN-SOURCE-PATH.md:317-353`, `OPEN-SOURCE-PATH.md:386-389`). |

## New Problems / Contradictions

1. **Minor privacy rules are now in tension across documents.** `PRODUCT-VISION.md` says J cannot see E's task completion without E's consent (`PRODUCT-VISION.md:336`), while `OPEN-SOURCE-PATH.md` says parents can see aggregate trend data for minors by default (`OPEN-SOURCE-PATH.md:116`) and then says E controls visibility (`OPEN-SOURCE-PATH.md:117`). That needs one clean rule.
2. **The anti-brittleness "quiet day" test is too blunt as written.** It appears in both the safeguard matrix and metrics (`OPEN-SOURCE-PATH.md:161`, `OPEN-SOURCE-PATH.md:285`, `PRODUCT-VISION.md:425`). Without constraints like "never on critical days/tasks," it creates an avoidable self-inflicted failure mode.
3. **A few lines still read like an internal memo rather than public founding docs.** The exact founder asset disclosure (`OPEN-SOURCE-PATH.md:14`) is unnecessary and weakens the tone more than it helps.

## Remaining Issues That Still Matter

- **Publishability gap:** the docs still do not finish the basics on license/security reporting. A public README cannot point security reports to `TBD`.
- **Privacy governance gap:** the family/minor visibility model is thoughtful but not yet internally consistent.
- **Operational security gap:** the security section is much improved, but important public-user guidance remains promised rather than stated. Acceptable for a draft, not ideal for "founding docs complete."

## Top 3 Improvements

1. **Resolve the publishability placeholders.** Choose one license everywhere, replace the `TBD` security contact with a real path, and make README and Path match exactly.
2. **Unify the minor privacy model.** State one explicit rule for what parents can see by default, what requires assent/consent, and how aggregate metrics interact with "E controls visibility."
3. **Tighten the public tone.** Remove private-decision details that do not help builders, especially the founder net-worth line, and keep the docs in project-charter mode rather than personal-memo mode.

The philosophical core is now strong, the README is materially better, and the roadmap is finally concrete. The remaining problems are governance/privacy discipline, not product thinking.
