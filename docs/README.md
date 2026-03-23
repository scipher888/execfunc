# ExecFunc Documentation

## Document Hierarchy

```
ARCHITECTURE-INDEX.md ← Master index (start here)
    │
    ├── PRODUCT-VISION.md ← What we build and why
    │       │
    │       ├── INTERACTION-MODEL.md ← How we communicate with users
    │       └── OPEN-SOURCE-PATH.md ← How we build and for whom
    │
    ├── DESIGNED-FOR-OBSOLESCENCE.md ← Evolvability architecture
    │
    ├── DECISION-LOG-2026-03-20.md ← Adversarial review decisions (locked)
    │
    └── reviews/ ← Adversarial review artifacts
            ├── ADVERSARIAL-REVIEW-BRIEF.md
            ├── ADVERSARIAL-REVIEW-RESULTS.md
            └── REVIEW-{1,2,3}-CODEX.md
```

## Reading Order

If you're new to ExecFunc:

1. Start with the project [README](../README.md) for the overview
2. Read [PRODUCT-VISION.md](PRODUCT-VISION.md) for the design philosophy
3. Read [OPEN-SOURCE-PATH.md](OPEN-SOURCE-PATH.md) for how we're building it
4. Read [INTERACTION-MODEL.md](INTERACTION-MODEL.md) for how the AI communicates
5. Browse the [reviews/](reviews/) folder to see the adversarial review process

## About the Adversarial Review

Every foundational document went through multi-pass adversarial review using an external model (Codex GPT 5.4). The reviewer was instructed to attack reasoning, find contradictions, surface risks, and challenge assumptions. The results are published unedited in `reviews/`.

This process is documented in [DECISION-LOG-2026-03-20.md](DECISION-LOG-2026-03-20.md), which contains every decision made during the review triage — including what we accepted, what we modified, and what we deferred.

We publish the review artifacts because we believe transparent design processes matter, especially for software that touches people's daily lives.
