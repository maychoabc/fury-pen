# FuryPen (怒笔)

> AI Long-Form Novel Consistency Writing System — A skill that actually wrote a 34-chapter novel.

**FuryPen** is a long-form novel writing system built on the WorkBuddy Skill + Memory architecture. It's not a "help you write a paragraph" tool — it's a system designed to make AI capable of writing a complete novel without contradicting itself.

Core problems it solves:

- **Context window can't hold a full novel** → Bible on-demand injection, each chapter only loads what it needs
- **AI has no persistent state** → run-state.md state machine + S4 fact extraction and writeback
- **No consistency gate** → genre-config type-customized validation + S5 layered review + S8 global audit

## Architecture Overview

```
Bible (Persistence Layer)  →  Loop (Execution Layer)  →  Gate (Control Layer)
   meta.md                       S2 Context Injection       genre-config
   characters/                   S3 Chapter Writing          check_priority
   worldbuilding/                S4 Fact Extraction          HARD/SOFT grading
   foreshadowing.md              S5 Consistency Review
   lorebook.md                   S6 Scene Expansion
   progression.md                S7 Revision & Rewrite
                                 S8 Global Final Audit (10 dimensions)
```

## The 8 Skills at a Glance

| Skill | Function | Trigger |
|-------|----------|---------|
| S1 | Novel initialization: hot menu → Q&A → generate bible | One-time |
| S2 | Context injection: load on-demand → assemble prompt | Per chapter auto |
| S3 | Write chapter: self-check → draft → finalize | Per chapter |
| S4 | Fact extraction: 8 dimensions → write back to bible | Per chapter / batch |
| S5 | Consistency review: HARD block → SOFT release | Per chapter auto |
| S6 | Scene expansion: locate → inject → expand → replace | On demand |
| S7 | Revision & rewrite: locate → inject → rewrite → verify | Auto / manual |
| S8 | Global final audit: 10-dimension cross-chapter scan | Novel complete |

## Key Features

- **Genre-Customized Consistency Gate (Original)**: Rule Horror / Post-Apocalyptic / Urban Supernatural / Mystery / General — each genre has its own check_priority configuration
- **Fast Batch Mode**: Skip per-chapter review, write the whole book first, revise later
- **Two-Pass Draft/Polish**: Draft mode prioritizes speed, Polish mode prioritizes quality
- **Adaptive Chapter Length**: Weight coefficient auto-adjusts word count based on suspense level
- **Bulk Foreshadowing Scan**: Auto-detect planted/recovered foreshadowing from text after completion
- **S8 10-Dimension Global Audit**: Orphan foreshadowing / information leaks / rule drift / character absence / naming consistency

## Real-World Validation

FuryPen has written a complete 34-chapter sci-fi novel **"Scrap Number 007"** (also known as **"Fury"**), approximately 80,000 Chinese characters across 5 volumes.

- Full fast batch mode, zero human intervention during writing
- S8 global audit results: 0 cross-chapter information leaks, 0 rule drifts, 0 broken foreshadowing
- 3 iterations (v1→v3) all driven by real writing feedback

## Quick Start

1. Make sure [WorkBuddy](https://www.codebuddy.cn) is installed
2. Copy this skill directory to `~/.workbuddy/skills/fury-pen/`
3. Type `写小说` (or "start novel" in Chinese mode) to trigger S1 initialization
4. Follow the Q&A prompts — the system generates the full bible
5. Type `写第1章` → auto-enter S2→S3→S4→S5 writing loop

## Project Structure

```
~/.workbuddy/skills/fury-pen/
├── SKILL.md                          # Main workflow (S1-S8 complete)
├── README_CN.md                      # Chinese documentation
├── references/
│   ├── hot-directions.md             # Hot direction menu (4 categories × 4)
│   ├── context-assembly-template.md  # S2 context template
│   ├── extraction-rules.md           # S4 8-dimension extraction rules
│   ├── consistency-check-rules.md    # S5 validation methods
│   ├── self-check-rules.md           # S3 pre-write checklist
│   ├── global-audit-rules.md         # S8 10-dimension audit rules
│   ├── outline-extension.md          # Auto-outline extension
│   ├── foreshadowing-auto-extract.md # Bulk foreshadowing auto-extraction
│   └── genre-config/                 # 5 genre configurations
│       ├── rule-horror.md
│       ├── post-apocalyptic.md
│       ├── urban-supernatural.md
│       ├── mystery.md
│       └── general.md
├── assets/
│   ├── bible-templates/              # 20 bible file templates
│   └── tracking-templates/           # 4 tracking templates
├── novel/                            # Full novel "Scrap Number 007"
│   ├── bible/                        # Novel world-building (13 files)
│   ├── chapters/                     # 35 chapter files (prologue + 34)
│   └── 废品编号007_全书.txt           # Complete TXT (~80K chars)
└── 怒笔FuryPen_深度拆解.html          # Deep-dive technical article (Chinese)
```

## Design Lineage

Borrowed from five existing systems:

- **Waqu Pingwen** — 8-module structure + foreshadowing tracking + character growth arcs
- **NovelCrafter** — Codex (structured wiki) + scene hook on-demand injection
- **NovelAI** — Lorebook keyword-triggered auto injection
- **Sudowrite** — Scene expansion / revision rewriting
- **AI_NovelGenerator** — Multi-stage generation + auto consistency check

**Original innovations**: Hot direction selection menu + staged Q&A guided initialization + genre-customized consistency gate

## License

MIT License
