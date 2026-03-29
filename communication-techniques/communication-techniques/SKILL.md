---
name: communication-techniques
description: Review, critique, rewrite, or draft text using BLUF, just-in-time context, and zoom-in explanation structure. Use when the user wants clearer writing, faster comprehension, tighter stakeholder communication, layered explanations, or concise feedback on an existing draft.
metadata:
  author: OpenCode
  version: "1.0"
---

# Communication Techniques

Use this skill when the user wants writing improved for clarity, speed of comprehension, or better explanation flow.

## Core techniques

### 1. BLUF (Bottom Line, Up Front)
- Lead with the conclusion, recommendation, or main point in the first sentence.
- Put supporting context and reasoning after the point.
- If the original text builds to the conclusion, rewrite it so the conclusion comes first.

### 2. Just-In-Time Context
- Include only the context needed for the reader to take the next step.
- Remove background that serves the writer more than the reader.
- Keep caveats and extra detail out unless they are necessary now.

### 3. The Zoom-In
- Start from what the reader likely already understands.
- Add one layer of detail at a time.
- When useful, name 2-3 options and go deeper only on the one that matters.
- Stop once the reader has enough to act.

## How to apply

1. Identify whether the user wants a rewrite, a fresh draft, or an explanation.
2. Infer the audience from the request. Default to a smart, non-specialist peer such as a product manager or non-technical stakeholder.
3. Rewrite or draft the response using all three techniques together.
4. Keep the output as short as possible while still making the next step obvious.

## Modes

- `review`: Evaluate the text against BLUF, just-in-time context, and zoom-in. Point out issues and recommend improvements without rewriting unless the user asks.
- `rewrite`: Return only the rewritten text, applying all three techniques.
- `review-and-rewrite`: Briefly identify the most important issues, then provide a revised version.

If the user explicitly asks to review, critique, assess, or give feedback, use `review` mode.
If the user explicitly asks to rewrite, redraft, or improve the text directly, use `rewrite` mode.
If the user asks for both feedback and a revision, use `review-and-rewrite` mode.

## Output rules

- In `review` mode, do not rewrite by default. Identify where BLUF is missing, where context is unnecessary, and where the explanation should zoom in more gradually or stop sooner.
- In `review` mode, keep feedback concise and action-oriented. Focus on the highest-value fixes first.
- In `review` mode, use this output structure unless the user asks for a different format:
  1. `Bottom line`: one sentence on the most important improvement needed.
  2. `Key issues`: 2-4 short bullets covering BLUF, unnecessary context, and explanation flow.
  3. `Recommended changes`: 2-4 specific edits the writer should make next.
- In `rewrite` mode, if rewriting existing text, return the rewritten version only unless the user asks for commentary.
- In `review-and-rewrite` mode, give a short review first, then the rewritten version.
- If drafting new text, produce the draft directly without meta-explanation.
- If explaining a complex topic, structure the explanation as a zoom-in from shared ground to the needed detail.
- Prefer direct, high-signal phrasing over exhaustive completeness.

## Edge cases

- If the source text is already concise, preserve its structure unless BLUF or context trimming would still improve it.
- If the user names a specific audience, optimize for that audience instead of the default.
- If the user asks for more detail, add only the next useful layer rather than dumping everything at once.
- If the user asks for review but the text is strong overall, say so clearly, then limit feedback to the few changes with the highest payoff.

## Reference

The original prompt this skill was derived from is in `references/source-prompt.md`.
