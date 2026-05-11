# Engineering handoff best practices

## 1. Preserve implementation state

The next engineer should know what already exists on disk and what has changed. Exact paths matter.

## 2. Preserve verification state

Do not just say “done” or “working.” Record whether validation passed, failed, was partial, or was not run.

## 3. Include commands only when useful

The command history is useful only when it affects the next step. Summarize what mattered.

## 4. Record failed attempts

Failed approaches and dead ends save time when documented clearly. Preserve them briefly if they affected direction.

## 5. Separate facts from intended work

- Fact: file exists, command ran, test failed, patch applied
- Intended work: next edit, planned refactor, expected fix

Keep these separate.

## 6. End with one next coding action

The handoff should reduce hesitation. Prefer one first move over many possible moves.

## 7. Prefer exact artifacts

Use exact file paths, directories, archives, PR links, issue links, or command names.

## Common anti-patterns

- “implemented” without naming the file or validation status
- listing many commands with no outcome
- omitting blockers or failed attempts
- restating the conversation instead of the code state
- saying “tests passed” without saying which tests
