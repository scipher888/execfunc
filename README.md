# ExecFunc
### An Open-Source Personal Operations and Task-Management Framework

---

> ⚠️ **ExecFunc is a personal operations and task-management framework. It is not designed or intended as a tool for executive dysfunction, ADHD support, mental health, or clinical use.**
>
> It does not diagnose, treat, or monitor any condition. It does not detect cognitive decline. It is not a substitute for professional mental health care. If you or someone you know is in crisis, contact [988 Suicide & Crisis Lifeline](https://988lifeline.org/) or call 911.
>
> This is an evidence-*informed* but not clinically *validated* framework for AI-assisted daily task management. It makes no clinical claims.

---

## What Is This?

ExecFunc is an open-source framework for building an AI companion that helps people manage daily life — particularly adults who know what they need to do but can't reliably make it happen.

**It is not an app.** It's a set of skills, configuration templates, and design principles built on [OpenClaw](https://github.com/openclaw/openclaw) — a platform for persistent AI agents. You bring your own AI, your own messaging app, and your own integrations. ExecFunc provides the framework for making that AI actually useful for daily task management.

## The Philosophy

**Assistive support is itself a legitimate outcome.**

Most task-management tools fail the same way: they become another thing to manage. A reminder app for people who can't manage reminders. ExecFunc takes a different approach:

- **Be useful first.** Remove friction between intention and action. No lectures, no gamification, no unsolicited coaching.
- **Escalate when asked.** When a critical commitment is at risk, escalate from gentle text to firmer reminders to (optionally) contacting a designated support person. Every level is user-controlled and blockable.
- **Respect autonomy.** The user decides what support looks like — permanent assistance, graduated scaffolding, or anything in between.
- **Guard against capture.** The goal is better functioning, not dependency. Bounded utility is the product — not engagement, not relationship, not habit formation.

Read the full philosophy: [Product Vision](PRODUCT-VISION.md)

## What It Looks Like

A real interaction flow:

```
8:00 AM  — "Good morning. You have 3 things today: dentist at 2pm,
            pharmacy pickup, and that insurance email you've been
            putting off for 6 days. Energy check — how are you feeling?"

8:01 AM  — User: "tired"

8:01 AM  — "Got it. I'd skip the insurance email today and handle the
            two time-bound things. Want me to set a reminder for the
            dentist at 1:15 so you have time to get ready?"

1:15 PM  — "Dentist in 45 minutes. Keys, wallet, insurance card."

1:50 PM  — (no response)
            "Hey — dentist is at 2. You haven't left yet. Want me to
            check if they can push it 15 minutes?"

2:10 PM  — (no response, task marked critical by user)
            "I'm about to reach out to Carol about the dentist.
            Want me to go ahead? [Yes / Block]"

2:12 PM  — [User approves]
            [To support person]: "Hi Carol, [user] has a dentist
            appointment that started at 2 and hasn't responded to
            check-ins. A quick call might help."
```

The escalation chain is fully user-configured. Every level can be turned off. Support-person contact only happens for tasks the user explicitly marked as critical, and the user gets a pre-notification with the option to block.

## Origin Story

This started as a startup business plan. After adversarial review and honest self-assessment, the founder (J — a practicing health care provider with a family) realized the right move was to build it for his own family first, prove it works, and share it with anyone who wants it.

The startup option isn't closed. But the evidence needs to come first.

Read the full story: [Open Source Path](OPEN-SOURCE-PATH.md)

## What's in This Repo Today

**This project is in early development.** The repo currently contains founding documents and design principles. Skills and code are being built and tested with one family before public release.

### Design Documents (Available Now)
- [Architecture Index](ARCHITECTURE-INDEX.md) — Document hierarchy, status, open/deferred decisions
- [Product Vision](PRODUCT-VISION.md) — Governing design philosophy, behavioral science framework, evidence map
- [Open Source Path](OPEN-SOURCE-PATH.md) — How we're building this and why
- [Interaction Model](INTERACTION-MODEL.md) — Communication design and escalation framework
- [Designed for Obsolescence](DESIGNED-FOR-OBSOLESCENCE.md) — Evolvability architecture

### OpenClaw Skills (Building — Not Yet Published)
- `ef-task-tracker` — Task management with EF-aware features (energy levels, step breakdown)
- `ef-escalation` — Multi-level escalation with user-configured thresholds, pre-notification, post-check-in
- `ef-morning-briefing` — Personalized daily briefing (calendar, tasks, weather, friction detection)
- `ef-friction-detector` — Pattern recognition for task avoidance and administrative pile-up
- `ef-reflection` — CPS-based reflection mode for opt-in check-ins (experimental)
- `ef-metrics` — Track supported task completion, escalation patterns, anti-capture metrics

### Configuration Templates (Coming)
- Per-user preference modules (reminder intensity, warmth level, support network, etc.)
- Escalation preferences (which levels, which support persons, quiet hours)
- Domain spectrum classification (compensate / scaffold / your choice)

## Requirements

- [OpenClaw](https://github.com/openclaw/openclaw) — the AI agent platform
- An LLM API (Anthropic Claude, OpenAI, etc.)
- A messaging channel (Telegram, Discord, Signal, etc.)
- Calendar integration (Google Calendar, Apple Calendar)

## ⚠️ Email & Sensitive Data

ExecFunc does **not** automatically scan your email inbox. If your email contains sensitive data (PHI, financial records, legal documents), do not connect it directly to the AI.

**How it works instead:**
- **Calendar** is the primary data source (typically PHI-free)
- **Email:** Users manually forward relevant, non-sensitive emails to the AI
- **The AI never has direct inbox access** — you control what it sees

## Safety Defaults

ExecFunc ships with **conservative defaults:**
- All high-risk features are OFF by default
- Support-person escalation requires active opt-in AND active consent from the support person
- No behavioral adaptation based on inferred psychological state
- No condition-specific categorization or profiling
- Crisis indicators → immediate 988/911 information, full stop

## Status

**Early development.** We're building this for one family right now. Skills and documentation will be published as they're tested and refined. Watch this repo for updates.

## Governance

This project is maintained by one family. Decisions are made by the project founder (J).

- **License:** MIT
- **Contributions:** Not yet open. The framework needs to stabilize first. Star the repo to follow progress.
- **Security issues:** [Open a private security advisory](https://github.com/scipher888/execfunc/security/advisories/new) or email security@execfunc.ai — please don't open a public issue.
- **Support:** This is a side project maintained by a working parent. No SLA, no guarantees.

## Behavioral Science Foundation

ExecFunc's design is informed by behavioral science research, adapted for a non-clinical context:

- **JITAI (Just-In-Time Adaptive Interventions)** — timing and context for when to offer support
- **MIRA (Machine-Integrated Relational Adaptation)** — relational design constraints
- **Neurodiversity-affirming orientation** — capacity variation, not deficit
- **Self-Determination Theory** (Ryan & Deci) — interaction language (autonomy, competence, relatedness)
- **Collaborative Problem Solving** (Ablon) — experimental reflection mode
- **Executive Function frameworks** (Dawson & Guare, Diamond) — externalize, compensate, optionally scaffold

See the [Evidence Map](PRODUCT-VISION.md#6-evidence-map) for honest assessment of what we know vs. what we're hypothesizing. We are transparent about the evidence gaps — particularly in anti-capture design, where no RCTs exist.

## Contributing

Not yet accepting contributions — the framework needs to stabilize first. When we're ready, contributions in these areas would be most valuable:

- Additional OpenClaw skills for task management
- Integration patterns for different calendars, messaging apps, and tools
- Accessibility improvements
- Evidence and research pointers
- Translations

## License

MIT

---

*Built by a family, for families. Shared with anyone who needs it.*
