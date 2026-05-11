# Handoff skill comparison

## Short version
- **`session-handoff`** = broad, general handoff for any multi-turn agent session
- **`engineering-session-handoff`** = narrower, technical handoff for coding/debugging/implementation work

---

## Core difference

### 1. Scope
**session-handoff**
- works for:
  - planning
  - research
  - writing
  - product/ops discussions
  - coding sessions too
- focuses on continuity in general

**engineering-session-handoff**
- works best for:
  - code changes
  - debugging
  - tests/validation
  - file edits
  - implementation state
- focuses on technical resumability

---

### 2. What they force you to preserve

**session-handoff**
asks for:
- current goal
- sub-goals
- status
- established context
- artifacts
- decisions
- open questions
- blockers
- risks
- next step

**engineering-session-handoff**
asks for all the above engineering-relevant pieces, but explicitly requires:
- **code / artifact state**
- **commands run**
- **validation status**
- **blockers / failed attempts**
- **recommended next coding step**

That’s the main difference.

---

### 3. Tone and output style
**session-handoff**
- more neutral
- more portable across domains
- more about “what matters next”

**engineering-session-handoff**
- more concrete
- more operational
- more about:
  - what files exist
  - what was run
  - what passed/failed
  - what should be edited/run next

---

## Side-by-side comparison

| Aspect | `session-handoff` | `engineering-session-handoff` |
|---|---|---|
| Best for | Any long multi-turn session | Coding/debugging/implementation sessions |
| Audience | Next agent or human generally | Next engineer / coding agent |
| Requires artifact paths | Yes | Yes, more strictly |
| Requires command history | Optional if relevant | Expected if relevant |
| Requires validation/test status | Not required by default | Explicitly required |
| Requires failed attempts | Optional | Explicitly important |
| Next step | General next step | Concrete next coding step |
| Good for research/writing handoff | Yes | Usually overkill |
| Good for debugging/code continuation | Good | Better |

---

## How I suggest using them

### Use `session-handoff` when:
- the work is mixed or ambiguous
- the session includes planning, discussion, design, and maybe some code
- the next person mainly needs orientation
- there may be no meaningful command/test state

Examples:
- “We discussed three approaches and settled on one”
- “User clarified requirements over many turns”
- “Need a clean summary for the next agent”
- “Research session with some draft files”

### Use `engineering-session-handoff` when:
- actual technical continuation matters
- files/commands/tests are central
- the next person will open files and continue coding immediately
- avoiding repeated debugging matters

Examples:
- “I changed these files, ran these commands, this test failed”
- “We cleaned up the package and now only final validation remains”
- “There was a failed attempt; don’t retry it blindly”
- “Next person should edit file X and rerun command Y”

---

## My recommendation
### Default workflow:
- Use **`session-handoff`** as the default
- Use **`engineering-session-handoff`** whenever the handoff is primarily for **continued implementation/debugging**

### Rule of thumb
Ask:
> “Will the next person mostly **read to understand**, or **open files and continue coding**?”

- **read to understand** → `session-handoff`
- **open files and continue coding** → `engineering-session-handoff`

---

## Even more practical recommendation
For your workflow:

- If the session ends in **docs / planning / skill design / requirement shaping**  
  → use **`session-handoff`**

- If the session ends in **code state / repo state / test state / bug-fix state**  
  → use **`engineering-session-handoff`**

---

## If you want the cleanest setup
I’d suggest:
1. keep both
2. treat `session-handoff` as the parent/general skill
3. treat `engineering-session-handoff` as the stricter specialist skill

If you want, I can also:
- refine the two so the distinction is even sharper, or
- make a **third** one for **git/PR/repo handoff** specifically.