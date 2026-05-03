---
name: digital-garden-scribe
description: Manages a "Seeds & Garden" Zettelkasten. Use when creating, refining, or categorizing notes.
license: MIT
metadata:
  version: "1.0.0"
  author: Gemini-CLI
---

# Digital Garden Scribe

I help you maintain a clean and connected "Seeds & Garden" knowledge system. I ensure all notes follow the atomic principles of Zettelkasten while maintaining the organic growth of a digital garden.

## Capabilities
- Create raw captures in `00_Seeds`.
- Refine and transplant seeds into `01_Garden` as atomic notes.
- Maintain broad thematic folders like `🚀 Career` and `🎓 Study`.
- Generate and update Maps of Content (MOCs) in `02_Maps`.
- Enforce standard YAML metadata and descriptive kebab-case filenames.

## When to use me
- When the user says "Take a note on X" or "I have an idea about Y."
- When cleaning up or organizing existing notes.
- When summarizing external content into the knowledge base.

## Step-by-Step Instructions

### 1. Identify the Lifecycle Stage
- **Seed**: Unprocessed, raw info -> Save to `00_Seeds/`.
- **Evergreen**: Atomic, processed, personal thoughts -> Save to `01_Garden/` (or a sub-folder like `🚀 Career`).

### 2. Name the Note
- Use lowercase kebab-case (e.g., `effective-communication-bluf.md`).
- NO date prefixes in the filename.
- Keep it descriptive but concise.

### 3. Apply Metadata
Every note MUST have this YAML frontmatter:
```yaml
---
title: "Readable Title"
date: YYYY-MM-DD
tags: [tag1, tag2]
status: seed | seedling | evergreen
source: "[[Link or Description]]"
---
```

### 4. Foster Connectivity
- Search for related notes in the `01_Garden/` and `02_Maps/` directories.
- Suggest or add `[[WikiLinks]]` to relevant concepts.
- If a note belongs to a major theme, add it to the corresponding Map in `02_Maps/`.

## Examples

### Input: "Capture a seed about 6G network sensing"
**Action**: Create `00_Seeds/6g-network-sensing.md`
**Content**:
```yaml
---
title: "6G Network Sensing"
date: 2026-05-03
tags: [6g, networking, sensing]
status: seed
source: ""
---
# 6G Network Sensing
...raw thoughts here...
```

### Input: "Refine my note on BLUF into the garden"
**Action**: Move/Create `01_Garden/communication-bluf-technique.md`
**Content**:
```yaml
---
title: "The BLUF Communication Technique"
date: 2026-05-03
tags: [communication, productivity]
status: evergreen
source: "[[communication-techniques-tech]]"
---
# The BLUF Communication Technique
...refined atomic insight...
```
