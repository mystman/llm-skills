# Example: engineering session handoff

```md
# Handoff

## Current goal
- Create a production-oriented Kubernetes expert skill for Opencode.

## Sub-goals
- Finalize `SKILL.md`
- Add reference files
- Remove unneeded assets from the package

## Current status
- `SKILL.md` and core references are complete.
- Cleanup is complete.
- Final review is still pending.

## Established context
- The user wanted a Kubernetes expert skill, then narrowed it to an opinionated platform-engineering variant.
- The user explicitly did not want helper Python files or bundled Helm skeleton assets.

## Artifacts
- `/home/example/session/kubernetes-expert/SKILL.md` — main skill definition
- `/home/example/session/kubernetes-expert/references/platform-guardrails.md` — platform defaults and caveats

## Decisions made
- Decision: remove validator scripts and extra assets
  - Why: the user wanted a lean manifest+docs style skill package
- Decision: bias the skill toward shared-cluster defaults
  - Why: the user said platform-engineering guidance was the real goal

## Open questions / assumptions
- Assumption: the skill should stay general enough for both humans and agents

## Blockers
- None currently

## Risks / caveats
- Do not reintroduce generated helper files unless the user asks
- Keep recommendations upstream-grounded and avoid controller-specific claims unless sourced

## Recommended next step
- Read `README.md` and do a final pass for tone and unnecessary verbosity.
```
