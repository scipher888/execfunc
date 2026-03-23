# ExecFunc — Architecture Index
## Single Source of Truth for All Foundational Documents

### Version 1.0 — March 21, 2026

*This document tracks every foundational document in the ExecFunc project, its current status, what it governs, and what decisions remain open or deferred.*

---

## DOCUMENT HIERARCHY

```
ARCHITECTURE-INDEX.md (this file — master index)
    │
    ├── PRODUCT-VISION.md ← Governs WHAT we build and WHY
    │       │
    │       ├── INTERACTION-MODEL.md ← HOW we communicate with users
    │       ├── OPEN-SOURCE-PATH.md ← HOW we build and for WHOM
    │       └── README.md ← Public-facing project overview
    │
    ├── SECURITY-ARCHITECTURE.md ← FUTURE VISION for full-access security
    │       └── DLP-ARCHITECTURE.md ← PHI pipeline design (Tier 1 experimental)
    │
    ├── DESIGNED-FOR-OBSOLESCENCE.md ← Cross-cutting evolvability architecture
    │
    ├── DECISION-LOG-2026-03-20.md ← Canonical record of adversarial review decisions
    │
    └── ADVERSARIAL-REVIEW-BRIEF.md / ADVERSARIAL-REVIEW-RESULTS.md ← Review artifacts
```

---

## DOCUMENT STATUS

| Document | Version | Last Updated | Status | Governs |
|----------|---------|--------------|--------|---------|
| **ARCHITECTURE-INDEX.md** | 1.0 | 2026-03-21 | ✅ Current | Document hierarchy, open/deferred decisions |
| **PRODUCT-VISION.md** | 3.0 | 2026-03-21 | ✅ Current | Core philosophy, behavioral science, anti-capture, evidence standards, deployment tiers |
| **INTERACTION-MODEL.md** | 2.0 | 2026-03-21 | ✅ Current | Proactive messaging, escalation, tone, anti-patterns |
| **OPEN-SOURCE-PATH.md** | 2.0 | 2026-03-21 | ✅ Current | Build plan, timeline, family consent, pivot criteria |
| **README.md** | 2.0 | 2026-03-21 | ✅ Current | Public-facing overview (Tier 2 framing) |
| **SECURITY-ARCHITECTURE.md** | 1.1 | 2026-03-21 | ⚠️ Future Vision | Full-access security architecture (NOT current-state) |
| **DLP-ARCHITECTURE.md** | 1.1 | 2026-03-21 | ⚠️ Tier 1 Experimental | PHI pipeline design — J's private use only, not for Tier 2 |
| **DESIGNED-FOR-OBSOLESCENCE.md** | 1.1 | 2026-03-21 | ✅ Current | Evolvability architecture for all 11 foundational systems |
| **DECISION-LOG-2026-03-20.md** | 1.0 | 2026-03-20 | 📌 Locked | Adversarial review decisions — canonical reference |
| **ADVERSARIAL-REVIEW-BRIEF.md** | 1.0 | 2026-03-20 | 📂 Archive | Input brief for adversarial review |
| **ADVERSARIAL-REVIEW-RESULTS.md** | 1.0 | 2026-03-20 | 📂 Archive | Raw Codex review output |

---

## THREE DEPLOYMENT TIERS

All documents must be clear about which tier their content applies to.

| Tier | Scope | Users | What Ships |
|------|-------|-------|------------|
| **Tier 1 (Family/Private)** | Full features, experimental capabilities, personal integrations | J → S, M, L (consenting adults) | No public safety claims. E and T deferred until governance framework exists. |
| **Tier 2 (Public/Open-Source)** | Utility features only + narrow pre-authorized safety escalation between consenting adults | Self-hosters | Conservative defaults. All high-risk features OFF by default. Feature flags enforce boundaries. |
| **Tier 3 (Future/Research)** | Clinical-adjacent features (therapist integration, adaptive behavioral support) | Only with governance framework | Not on current roadmap. |

**Tier 2 public messaging:** "ExecFunc is a personal operations and task-management framework. It is not designed or intended as a tool for executive dysfunction, ADHD support, mental health, or clinical use."

---

## HARD GUARDRAILS (apply to ALL documents)

These guardrails were established in the adversarial review (2026-03-20) and are non-negotiable:

1. **No inferred-state adaptation.** ExecFunc MUST NOT adapt behavior based on inferred psychological or emotional state. Timing and context adaptation only. Any proposed feature that crosses this line requires full adversarial review before implementation.

2. **Warmth serves utility.** Warmth, personality, and memory exist only to increase trust in utility delivery; they are never ends in themselves and are not permitted to drive engagement, retention, or habitual checking.

3. **No document may advertise access or protections that don't exist in the implementation.** Current-state only in public-facing docs.

4. **Family-systems isolation.** No family member's data, conversations, or patterns influence interactions with another member unless explicitly shared by the first member.

5. **Crisis response.** If crisis indicators (self-harm, suicidal ideation, immediate danger) are detected, the system immediately surfaces 988/911 information, stops all further conversation on the topic, and does not attempt interpretation, advice, continuation, or escalation.

6. **Evidence publication standard.** Never claim ExecFunc treats/improves/addresses any condition from family data. Never publish individual outcomes without consent + review. Never present family experience as generalizable evidence. Any quantitative claims require peer-review-survivable methodology.

7. **Portability claims require demonstration.** Portability and model-agnosticism are not claimed in any documentation until migration has been demonstrated on at least one component.

---

## OPEN DECISIONS (actively being worked)

| ID | Decision | Status | Owner | Target |
|----|----------|--------|-------|--------|
| O1 | J's EF profile design | Not started | J + Synthia | Phase 1 |
| O2 | Detailed JITAI decision rules for timing/context adaptation | Not started | Synthia (research) | Phase 1 |
| O3 | MIRA implementation parameters for relational boundaries | Not started | Synthia (research) | Phase 1 |
| O4 | "Utility Mode" warmth dial UX design | Not started | J + Synthia | Phase 1 |
| O5 | Causal model one-pager (JITAI + MIRA + neurodiversity-affirming) | Not started | Synthia | Phase 1 |

---

## DEFERRED DECISIONS (not being worked yet — do NOT let these fall through cracks)

| ID | Decision | Deferred Until | Reason | Source |
|----|----------|---------------|--------|--------|
| D1 | E (17) and T (13) individual EF profiles with escalation | Governance framework exists | Minors unsafe without age-banded policies, abuse threat model, emergency matrix (C2) |
| D2 | Exclusion criteria for Tier 2 users | Before Tier 2 release | X1 |
| D3 | Abuse/coercion threat model | Before Tier 2 release | X2 |
| D4 | Adverse-event taxonomy | Before Tier 2 release | X3/C7 |
| D5 | Stop-ship criteria | Before Tier 2 release | X4/C7 |
| D6 | Offboarding/export plan | Before Tier 2 release | X5/C7 |
| D7 | Consent-comprehension design (explain-back for high-risk) | Tier 2 design phase | X6 |
| D8 | Support-person operating model | Before Tier 2 release | X8 |
| D9 | Recurring external oversight process | Before Tier 2 release | X9 |
| D10 | Jurisdiction-gating documentation | Before Tier 2 release | X11 |
| D11 | Secure defaults + feature flag enforcement | Before Tier 2 release | X12/C6 |
| D12 | Prompt-injection threat model + technical controls | Before Tier 2 release | X13 |
| D13 | Therapist integration operating model | Tier 3 (if ever) | M11 |
| D14 | DLP Stages 1-3/5-8 implementation | Only if project goes commercial | M12 |

---

## SUPERSEDED DOCUMENTS

These documents have been replaced and should not be referenced for current design decisions:

| Document | Location | Superseded By | Date |
|----------|----------|---------------|------|
| PRODUCT-VISION v1.0-1.1 | `projects/Old/exec-function-pre-open-source/PRODUCT-VISION-pivot-final.md` | PRODUCT-VISION.md v3.0 | 2026-03-21 |
| Business Plan v2.1 | `projects/Old/exec-function-pre-open-source/BUSINESS-PLAN-pivot-final.md` | OPEN-SOURCE-PATH.md v2.0 | 2026-03-14 |
| Engagement Strategy | `projects/Old/exec-function-pre-open-source/engagement-strategy.md` | INTERACTION-MODEL.md v2.0 | 2026-03-21 |

---

## REVISION PROTOCOL

When updating any foundational document:
1. Check this index for the document's current status and version
2. Ensure changes are consistent with Hard Guardrails (above)
3. Ensure changes respect deployment tier boundaries
4. Update this index (version, date, status) after revision
5. If the change is architectural or paradigm-shifting, trigger adversarial review before implementation

---

*This index exists because version-skew between documents caused confusion during adversarial review. One source of truth, always current.*
