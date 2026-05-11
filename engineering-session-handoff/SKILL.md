---
name: engineering-session-handoff
description: Compact an engineering or coding agent session into a clean handoff document that preserves implementation state, files changed, commands run, decisions, blockers, and the next coding action. Use when another agent or engineer must resume without rereading the whole session.
compatibility: opencode; best for coding sessions involving files, commands, tests, reviews, debugging, or iterative implementation work
metadata:
  author: opencode
  version: 1.0.0
  audience: agents-and-software-engineers
  scope: engineering-coding-session-handoff
---

## What this skill does

Use this skill to turn a coding or engineering session into a compact handoff document for the next agent or engineer.

This skill is stricter than a general handoff. It assumes the reader needs to continue implementation, debugging, review, or verification work, not just understand the discussion.

## Default stance

- Optimize for immediate continuation of engineering work.
- Preserve concrete implementation state: files, commands, outputs, tests, and pending edits.
- Distinguish verified results from assumptions or intended work.
- Preserve decision rationale so the next person does not undo deliberate tradeoffs.
- Point to exact files and paths whenever artifacts exist.

## When to use

Use this skill when the session involved one or more of:

- code changes or planned code changes
- file creation, cleanup, or restructuring
- test runs, validation steps, or failed verification
- debugging or triage
- architecture or implementation decisions
- command outputs that matter for the next step

Do not use this skill for non-engineering discussions unless the next person still needs a code-focused handoff.

## Required input gathering

Before writing the handoff, identify:

- current engineering goal and sub-goals
- what is implemented, changed, cleaned up, or still pending
- exact artifacts produced so far with paths
- commands run and what mattered from their output
- validation already performed and its outcome
- decisions made and why
- blockers, failed attempts, or known dead ends
- recommended next coding action

If anything is missing, state `Unknown` rather than guessing.

## Engineering handoff structure

Use this structure by default:

```md
# Engineering Handoff

## Current goal
- ...

## Sub-goals
- ...

## Current status
- ...

## Code / artifact state
- `path` — what exists or changed

## Commands run
- `command` — result / why it matters

## Validation status
- ...

## Decisions made
- Decision: ...
  - Why: ...

## Open questions / assumptions
- ...

## Blockers / failed attempts
- ...

## Risks / caveats
- ...

## Recommended next coding step
- ...
```

Add `Recent edits` only if there were multiple file changes and listing them separately helps resume work faster.

## Writing rules

- Keep it compact, but never omit actionable engineering state.
- Prefer bullets and exact paths.
- Include commands only when they materially affect what happens next.
- Summarize command outputs; do not paste large raw logs unless the exact text matters.
- Mark validation clearly: passed, failed, not run, or partially run.
- If the next step depends on a user answer, say that explicitly.
- If a branch, archive, or generated artifact exists, include the exact path.

## What to exclude

Do not include:

- full conversation transcript
- speculative implementation details presented as facts
- repeated summaries that do not change the engineering state
- sensitive credentials or secrets
- long raw logs unless essential to the blocker

## Quality bar

A good engineering handoff lets the next person answer these quickly:

1. What are we building or fixing?
2. What files or outputs already exist?
3. What commands or validation already ran?
4. What decisions should not be undone casually?
5. What should I edit, run, or check first?

## Best-practice guidance encoded here

- preserve implementation state, not just intent
- preserve verification state, not just claims of completion
- capture failed paths so they are not retried blindly
- prefer exact files, commands, and outputs over vague prose
- end with one concrete next coding action

## Output contract

Return the handoff document directly.

If work is blocked on user input, say exactly what answer is required before coding can continue.

## Supporting files

- [references/engineering-handoff-best-practices.md](references/engineering-handoff-best-practices.md)
- [references/engineering-handoff-template.md](references/engineering-handoff-template.md)
- [examples/feature-implementation-handoff.md](examples/feature-implementation-handoff.md)
- [examples/debugging-handoff.md](examples/debugging-handoff.md)
