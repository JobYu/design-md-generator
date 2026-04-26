# design-md-generator

A **Claude Code / Cursor Agent Skill** that produces a full design-system package — aligned with [Google Stitch DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) — from project context, a website URL, a design screenshot, or a guided human interview.

## Tech Stack

- Language: Markdown
- Format: Cursor Agent Skill (`SKILL.md`)
- No build step, no runtime dependencies

## Directory Structure

```
design-md-generator/
├── SKILL.md                    # Core skill definition (orchestrator + modes + template + output specs)
├── README.md                   # Project documentation (EN)
├── README.zh-Hant.md           # Project documentation (ZH-TW)
├── LICENSE                     # MIT License
├── .gitignore                  # Git ignore rules
├── _MANIFEST.md                # This file
└── examples/                   # 58 anonymized DESIGN.md references from real-world brands
    ├── brand-01/
    ├── brand-02/
    ├── brand-03/
    └── ... (brand-01 ~ brand-58, each contains one DESIGN.md)
```

## Key Modules

| File | Purpose |
|------|---------|
| `SKILL.md` | Single-file skill orchestrator. Contains: input detection, mode routing, Data Sufficiency Check, anti-patterns, 4 mode instructions (Autonomous/URL/Image/Guided), DESIGN.md Master Template + Mobile Extension, and output file specifications. |
| `examples/` | 58 anonymized DESIGN.md references from real-world brands. Each subdir (`brand-01` ~ `brand-58`) contains one `DESIGN.md` with brand names removed. |

## Modes

1. **Autonomous Mode**: Analyze existing project files (README, package.json, styles) and auto-generate.
2. **URL Analysis Mode**: Extract visual design elements from a live website URL.
3. **Image Analysis Mode**: Analyze a design screenshot/mockup image.
4. **Guided Mode**: Step-by-step interview to co-create a design system. Also used for gap-filling after URL/Image analysis.

## Output Package (4 files)

Generated under `[project-root]/design-system/`:

- `DESIGN.md` — Complete design system spec
- `README.md` — Brand-facing introduction
- `preview.html` — Light mode visual catalog
- `preview-dark.html` — Dark mode visual catalog

## How to Use

Install or reference `SKILL.md` per your agent's skill system, then use trigger phrases like:
- "generate DESIGN.md"
- "分析這個網站設計"
- "從這張圖片生成設計系統"

## Known Constraints

- URL Analysis relies on `WebFetch`; JavaScript-heavy SPAs may have incomplete style extraction.
- Image Analysis cannot extract exact font names or precise pixel values; these are inferred or left for gap-filling.
- Semantic colors default to standard Tailwind values unless brand collision requires shifting.

## External References

- [Google Stitch: DESIGN.md overview](https://stitch.withgoogle.com/docs/design-md/overview/)
- [Google Stitch: DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/format/)
