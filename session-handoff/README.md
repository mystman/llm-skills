# Session Handoff Skill

Skill for compressing an active or completed agent session into a clean, restart-friendly handoff document.

## Purpose

This skill helps an agent preserve continuity without dumping the whole conversation into the handoff. It is intended for general-purpose sessions, with a bias toward coding, engineering, and multi-step agent work.

## Design goals

- compact, high-signal handoff output
- clear separation of facts, assumptions, blockers, and next steps
- restart speed for the next agent or human
- exact paths and links when artifacts exist

## Primary references used for design

- Google SRE — Communication and Collaboration in SRE: https://sre.google/sre-book/communication-and-collaboration/
- Google SRE — Example Incident State Document: https://sre.google/sre-book/incident-document/
- PagerDuty — Different Roles: https://response.pagerduty.com/before/different_roles/
- PagerDuty — During an Incident: https://response.pagerduty.com/during/during_an_incident/
- PagerDuty — Scribe: https://response.pagerduty.com/training/scribe/
- PagerDuty Stakeholder Comms — Templatizing communications: https://stakeholders.pagerduty.com/considerations/templates/
- PagerDuty Stakeholder Comms — Frequency of communication: https://stakeholders.pagerduty.com/considerations/frequency/
- PagerDuty — Anti-Patterns: https://response.pagerduty.com/resources/anti_patterns/

## Package layout

```text
session-handoff/
├── SKILL.md
├── README.md
├── references/
│   ├── handoff-best-practices.md
│   └── handoff-template.md
└── examples/
    ├── blocked-session-handoff.md
    └── engineering-session-handoff.md
```

## Key ideas

- summarize current state, not the whole transcript
- preserve costly-to-recover context
- make the next action obvious
- explicitly mark unknowns and blockers

## Changelog

- `1.0.0`: initial general-purpose session handoff skill, biased toward coding and multi-step agent sessions
