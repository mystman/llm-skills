# Communication Techniques for Tech Professionals
**Source:** *Why Most Tech Professionals Are Terrible Communicators* (YouTube)

> The core insight: your career stalls not because of weak technical skills, but because of how you communicate. Most people build up to their point — they should lead with it.

---

## Technique 1 — BLUF (Bottom Line, Up Front)
**Timestamp: 00:29**

**The problem:** Most people explain in chronological order — the journey first, the conclusion last. By the time the point arrives, the audience has lost the thread.

**The fix:** State your point *first*. Everything else is support. Think of it as an inverted pyramid: the conclusion sits at the top, context underneath.

**Framework:**
- Ask yourself: *"What is my point?"*
- Say that first.
- If you catch yourself saying *"so basically what I'm trying to say is..."* — you went bottom-up. Flip it.

**Example — Bottom-up (don't do this):**
> "So we've been dealing with a lot of accumulated shortcuts in the code base... the auth module was a prototype three years ago... so the reason features are taking longer is we're fighting the codebase."

The VP still has to ask: *"Okay, but why are features taking longer?"*

**Example — BLUF (do this):**
> "Feature delivery slowed because of technical debt, especially in the authentication module. We need six weeks of dedicated cleanup. I'd like to propose pausing one feature track next quarter."

Now the VP can *choose* to go deeper — on their terms.

**Practice tip:** Write the next email with your ask or conclusion as the very first sentence. It will feel abrupt at first. It isn't.

---

## Technique 2 — Just-In-Time Context
**Timestamp: 5:24**

**The problem:** Deep experts over-explain because leaving things out *feels* wrong. But a complete explanation and a useful explanation are almost never the same thing.

**The fix:** Give people exactly enough context to do what they need to do *right now* — nothing more.

**Before explaining anything, ask:**
> *"What does this person need to **do** with this information?"*

Write it down: *"The thing this person needs to do with this information is ______."* Then filter everything through that sentence. If a detail doesn't serve that need, cut it.

**Example — Over-explained:**
> Explaining three types of technical debt (deliberate, accidental, bit rot) to a PM who just needs to talk about it in a planning meeting.

**Example — Just-in-time:**
> "We took shortcuts to ship faster, and now they're slowing us down. The biggest problem is the auth module — features that should take weeks now take months. That's the main thing worth bringing up."

Same knowledge, completely different filter. The first version communicates what *you* understand. The second gives them what *they* need.

---

## Technique 3 — The Zoom-In
**Timestamp: 8:15**

**The problem:** "If I simplify, I'm dumbing things down." Cutting context can feel like cutting substance.

**The fix:** Start from *shared understanding* and go one layer deeper at a time. You're not dumbing it down — you're building up from where they already are.

**How it works:**
1. Identify what the other person already knows → that's your **starting point**
2. Go one layer deeper
3. Break that layer into 2–3 categories
4. Pick the one that matters most
5. Go deeper into just that one
6. Stop when they can take the next step

**Example — Explaining "tensor" to a front-end engineer:**
- *Layer 1:* "You know what a vector is — a list of numbers. A matrix is vectors stacked together. Rows and columns."
- *Layer 2:* "A tensor is what happens when you keep going — add a third dimension and you have a cube of numbers. Add a fourth, a fifth."
- *Layer 3:* "When PyTorch calls your data a tensor, that's all it means — a multi-dimensional array."

Three zooms. They went from confused → working mental model they can use on Monday.

**Example — Explaining velocity drop to a new engineering manager:**
- *Zoom 1:* "Velocity dropped because of accumulated tech debt."
- *Zoom 2:* "The debt sits in three systems. Auth is the one hurting us."
- *Zoom 3:* "Auth was built as a temporary prototype. Six services depend on it now. Changes require coordinating across all six — a one-week feature takes three."

**Key difference vs. bottom-up:** Bottom-up starts from the beginning and tries to build the whole picture. The zoom-in starts from *shared understanding* and only goes deeper where it matters.

---

## Summary Table

| Technique | Fixes | Key Question |
|---|---|---|
| **BLUF** | Wrong *order* — burying the point | *"What is my point?"* — say it first |
| **Just-In-Time Context** | Too much *volume* — unnecessary detail | *"What does this person need to **do** with this?"* |
| **Zoom-In** | Going too deep *too fast* — losing people | *"What does this person already know?"* — start there |

---

## Key Takeaway

> "You need to start communicating the way that people listen. Lead with the point. Give them just enough context. Go deeper by starting where they are."
