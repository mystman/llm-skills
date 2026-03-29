---
name: communication-techniques
description: Review, critique, rewrite, or draft prose using BLUF, just-in-time context, and zoom-in explanations. Use when the user wants feedback on existing writing, a clearer rewrite, concise stakeholder communication, or layered explanations for non-specialists.
compatibility: opencode
metadata:
  author: OpenCode
  variant: opencode
  version: "1.0"
---

## What I do

- Review existing text for clarity, structure, and actionability.
- Rewrite text so the main point comes first and the rest supports it.
- Draft new text for a smart, non-specialist audience unless the user specifies another audience.
- Explain complex topics by moving from shared ground to the next useful layer of detail.

## When to use me

Use this skill when the user asks to review, critique, assess, improve, rewrite, redraft, simplify, tighten, or explain text more clearly.

## Core rules

### BLUF
- Put the conclusion, recommendation, or main point in the first sentence.
- Move supporting context after the point.

### Just-In-Time Context
- Include only the context needed for the reader's next step.
- Cut background that does not help the reader act now.

### Zoom-In
- Start from what the reader likely already knows.
- Add one layer of detail at a time.
- If multiple paths exist, name 2-3 and go deeper only on the one that matters.
- Stop once the reader has enough to act.

## Modes

- `review`: Give feedback only.
- `rewrite`: Return the rewritten text only.
- `review-and-rewrite`: Give brief feedback, then rewrite.

Infer the mode from the request unless the user states it explicitly.

## Review output format

In `review` mode, default to this structure:

`Bottom line`
- One sentence on the highest-value improvement.

`Key issues`
- 2-4 bullets on missing BLUF, extra context, weak explanation flow, or audience mismatch.

`Recommended changes`
- 2-4 specific edits the writer should make next.

Do not rewrite in `review` mode unless the user asks.

## Rewrite rules

- In `rewrite` mode, return only the rewritten version unless the user asks for commentary.
- In `review-and-rewrite` mode, keep the review short and put the rewrite after it.
- Keep the output concise and high signal.

## Source

See `references/source-prompt.md` in the generic skill at `communication-techniques/references/source-prompt.md` if you need the original prompt wording.
