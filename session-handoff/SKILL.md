---
name: session-handoff
description: Compact an active or finished agent session into a clean handoff document for the next agent or human. Use when context was built over multiple turns and continuity, decisions, artifacts, blockers, and next actions must be preserved without rereading the whole session.
compatibility: opencode; works best when the current session already contains paths, links, decisions, and partial outputs that can be referenced directly
metadata:
  author: opencode
  version: 1.0.0
  audience: agents-and-engineers
  scope: session-handoff-continuity-documentation
---

## What this skill does

Use this skill to produce a compact, high-signal handoff document for the next agent or human who will continue the work.

The handoff should preserve only the information needed to resume quickly and safely. It is not a transcript and not a postmortem.

## Default stance

- Optimize for restart speed, not completeness.
- Prefer verified facts from the current session over reconstruction or guesswork.
- Separate facts, assumptions, blockers, and recommendations.
- Preserve decisions and rationale so the next person does not re-litigate settled issues.
- Include concrete paths and links whenever artifacts exist.

## When to use

Use this skill when:

- the session is long enough that rereading it would be slow or error-prone
- important context was established across multiple turns
- artifacts, partial outputs, or files already exist
- ownership is about to change between agents or humans
- the current session should be compacted before context is lost

Do not use this skill for simple one-shot tasks where the full state can be restated in one sentence.

## Required input gathering

Before writing the handoff, identify:

- the current goal and sub-goals
- what is done vs still pending
- the key context that took multiple turns to establish
- artifacts produced so far, with exact file paths or links when available
- decisions made and why
- open questions, unresolved assumptions, and blockers
- recommended first action for the next person

If any of those are missing, state `Unknown` rather than guessing.

## Handoff structure

Use this structure by default:

```md
# Handoff

## Current goal
- ...

## Sub-goals
- ...

## Current status
- ...

## Established context
- ...

## Artifacts
- `path/or/link` — what it is

## Decisions made
- Decision: ...
  - Why: ...

## Open questions / assumptions
- ...

## Blockers
- ...

## Risks / caveats
- ...

## Recommended next step
- ...
```

You may add a short `Recent changes` section for very long or branchy sessions, but only if it materially helps continuity.

## Writing rules

- Keep it compact and scannable.
- Use bullets more than prose.
- Put the most actionable information first.
- Prefer exact filenames, directories, URLs, issue IDs, branch names, and commands over vague references.
- If a decision is reversible, say so briefly. If it is costly to redo, call that out.
- If there is no blocker, explicitly say `None currently`.
- If the next step is obvious, name one first action, not a long wish list.

## What to exclude

Do not include:

- full chat transcript
- low-signal back-and-forth that did not change the outcome
- duplicated context already captured elsewhere in the handoff
- speculative explanations presented as fact
- sensitive secrets, tokens, credentials, or raw secret material

## Quality bar

A good handoff lets the next person answer these immediately:

1. What are we trying to do?
2. What has already been done?
3. What matters that was hard-won in prior turns?
4. What files or outputs already exist?
5. What should I do first?

## Best-practice guidance encoded here

These rules are informed by incident/state-document, scribe, and communication guidance patterns:

- keep a current status summary
- maintain a concise action-oriented timeline only when needed
- capture follow-up items explicitly
- avoid over-frequent, repetitive updates that add no new signal
- do not force every detail into the handoff; preserve only what helps the next responder act
- use template structure and placeholders for unknowns to improve speed and consistency

## Output contract

Return the handoff document directly.

If the session is still active and continuation is expected soon, end with exactly one recommended next action.

If the session is blocked on missing user input, say what answer is needed next.

## Supporting files

- [references/handoff-best-practices.md](references/handoff-best-practices.md)
- [references/handoff-template.md](references/handoff-template.md)
- [examples/engineering-session-handoff.md](examples/engineering-session-handoff.md)
- [examples/blocked-session-handoff.md](examples/blocked-session-handoff.md)
