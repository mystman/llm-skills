# Example: feature implementation handoff

```md
# Engineering Handoff

## Current goal
- Create a session handoff skill for Opencode.

## Sub-goals
- Write `SKILL.md`
- Add references and examples
- Keep package manifest+docs only

## Current status
- Core skill files are written.
- Package structure exists.
- No additional validation tooling was added by design.

## Code / artifact state
- `/home/example/session/session-handoff/SKILL.md` — main skill instructions
- `/home/example/session/session-handoff/README.md` — package overview
- `/home/example/session/session-handoff/references/handoff-template.md` — reusable handoff template

## Commands run
- `mkdir -p /home/example/session/session-handoff/...` — created package directories

## Validation status
- Manual structure review only

## Decisions made
- Decision: keep the skill manifest+docs only
  - Why: the user did not want helper code or extra tooling

## Open questions / assumptions
- Assumption: general-purpose handoff is acceptable unless the user asks for a narrower variant

## Blockers / failed attempts
- None currently

## Risks / caveats
- Avoid drifting into transcript-style output; the skill must stay compact and action-oriented

## Recommended next coding step
- Add an engineering-session-only variant if the user wants a stricter technical handoff skill.
```
