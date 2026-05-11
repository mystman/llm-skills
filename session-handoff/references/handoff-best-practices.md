# Handoff best practices

This skill is based on a few durable communication patterns that transfer well from incident response and operational coordination into agent session handoff.

## 1. Keep a current state summary

A useful handoff starts with current state, not historical buildup. The reader should understand the present goal and status in seconds.

## 2. Record only key events and decisions

Like a good incident timeline or scribe log, capture:

- meaningful actions taken
- important findings
- decisions and follow-up items

Do not reproduce every exchange.

## 3. Preserve rationale, not just conclusions

If a decision was made after multiple turns, preserve the reason so the next person does not reopen it unnecessarily.

## 4. Use explicit placeholders for unknowns

If a detail is unknown, mark it clearly rather than inferring it. This keeps the handoff trustworthy.

Recommended forms:

- `Unknown`
- `None currently`
- `Waiting on user input: ...`

## 5. Prefer templates

Template structure increases speed and consistency. Repeated headings also help the next person scan for exactly what they need.

## 6. Set expectations for the next step

The handoff should end with one recommended first move. Avoid large undifferentiated task lists when one next action is enough.

## 7. Avoid noisy updates

Repeated status lines with no new signal reduce confidence and waste attention. If nothing changed, say so briefly and add only the next relevant detail.

## 8. Keep artifacts concrete

When files, links, branches, or outputs exist, reference them exactly. This reduces rediscovery work.

## 9. Separate blockers from open questions

- A blocker stops progress now.
- An open question matters, but may not prevent progress.

Keep them distinct.

## 10. Do not leak sensitive information

Never include secrets or raw credentials in the handoff. Preserve references to secure locations instead.

## Common anti-patterns

- transcript disguised as handoff
- vague references like “the file we edited earlier”
- missing current status
- no recommended next action
- facts and assumptions mixed together
- rehashing all discussion instead of preserving only the useful output
