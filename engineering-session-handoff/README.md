# Engineering Session Handoff Skill

Strictly engineering-focused handoff skill for coding, debugging, review, and implementation sessions.

## Purpose

This skill is for sessions where the next person needs to continue technical work immediately. It emphasizes files, commands, validation, failed attempts, and the next coding action.

## Design goals

- resume implementation quickly
- preserve concrete technical state
- distinguish verified results from assumptions
- avoid repeated investigation or rework

## How it differs from the general handoff skill

This version is narrower and more technical. It requires explicit coverage of:

- code or artifact state
- commands run
- validation status
- blockers and failed attempts
- exact next coding step

## Package layout

```text
engineering-session-handoff/
├── SKILL.md
├── README.md
├── references/
│   ├── engineering-handoff-best-practices.md
│   └── engineering-handoff-template.md
└── examples/
    ├── debugging-handoff.md
    └── feature-implementation-handoff.md
```

## Changelog

- `1.0.0`: initial engineering-session-only variant derived from the general session handoff skill
