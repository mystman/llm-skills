# Example: debugging handoff

```md
# Engineering Handoff

## Current goal
- Fix validation failures in the generated skill package.

## Sub-goals
- identify missing references
- update `SKILL.md`
- re-run validation

## Current status
- Validation failed because `SKILL.md` referenced files that did not exist.
- File list has been corrected in draft but not yet rechecked.

## Code / artifact state
- `/home/example/project/my-skill/SKILL.md` — edited locally, not revalidated yet
- `/home/example/project/my-skill/references/guide.md` — exists

## Commands run
- `python3 scripts/validate_skill.py .` — failed due to missing referenced files

## Validation status
- Failed: missing file references in `SKILL.md`

## Decisions made
- Decision: remove stale references instead of creating placeholder files
  - Why: keep the package lean and truthful

## Open questions / assumptions
- Unknown whether additional missing references remain after the latest edit

## Blockers / failed attempts
- Previous attempt assumed all referenced example files existed; that assumption was wrong

## Risks / caveats
- Do not claim the package is valid until validation is rerun

## Recommended next coding step
- Re-run the validator and check `SKILL.md` for any remaining nonexistent references.
```
