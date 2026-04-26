# design-md-generator

**Languages:** English (this page) · [繁體中文](./README.zh-Hant.md)

A **Claude Code / Cursor Agent Skill** that produces a full design-system package—aligned with the spirit of [Google Stitch DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/)—from your project context, a website URL, a design screenshot, or a guided human interview. Includes preview assets and built-in real-world examples.

## What is DESIGN.md?

[DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) is a **plain Markdown** design-system document: visual and interaction rules so AI coding agents or tools can build consistent UIs without Figma exports or an extra schema.


| File        | Read by              | Defines                          |
| ----------- | -------------------- | -------------------------------- |
| `AGENTS.md` | Coding agents        | How to build the project         |
| `DESIGN.md` | Design / coding agents | How the product should look and feel |


**This repo** provides **generation from scratch** (autonomous/guided modes) and **58 built-in anonymized examples** (`examples/brand-01` ~ `brand-58`) for format reference. You can also point the skill at any live website URL or design screenshot to extract a design system automatically.

## Four Generation Modes

The skill automatically detects your input type and picks the right mode:

| Mode | Input | What it does |
|------|-------|-------------|
| **Autonomous** | Existing project files (`README.md`, `package.json`, styles) | Analyzes context and auto-generates a DESIGN.md |
| **URL Analysis** | A website URL (`https://...`) | Extracts colors, typography, components, and layout from the live site |
| **Image Analysis** | A screenshot or mockup image | Identifies visual elements from a design image |
| **Guided** | Text description or no input | Step-by-step interview about product personality and constraints |

If data from URL/Image analysis is incomplete, the skill automatically enters **Guided Gap-Filling**—asking only the missing questions, not the full interview.

## Repository Structure

```
design-md-generator/
├── SKILL.md                    # Core skill orchestrator (< 500 lines)
├── references/
│   ├── modes.md                # Detailed extraction procedures for all 4 modes
│   ├── master-template.md      # DESIGN.md template (9 chapters) + Mobile extension
│   └── output-specs.md         # Preview HTML specs, README template, native snippets
└── examples/                   # 58 anonymized DESIGN.md references from real-world brands
    ├── brand-01/
    ├── brand-02/
    ├── brand-03/
    └── ... (brand-01 ~ brand-58, each contains one DESIGN.md)
```

### Built-in Examples (`examples/`)

The `examples/` directory contains **58 anonymized design system references** originally derived from real-world websites. Each subdirectory (`brand-01` ~ `brand-58`) contains one `DESIGN.md` with brand identifiers removed. These serve as:

- **Format references** — See what a well-structured DESIGN.md looks like
- **Starting points** — Adapt the structure for your own product
- **Training material** — Build intuition for color, typography, and component specifications

> **Note:** These files are observational analyses of publicly visible design patterns, not official brand design systems. All brand names have been anonymized to avoid trademark implications.

## Usage

1. Install or reference this repo's `SKILL.md` per your agent's skill system (path depends on your skills directory).
2. Use trigger phrases in chat:
   - **"generate DESIGN.md"**
   - **"分析這個網站設計"** / **"design from url"**
   - **"從這張圖片生成設計系統"** / **"design from image"**
   - **"產品視覺規範"** / **"design system document"**
   (full list in the `triggers` field at the top of `SKILL.md`)
3. The skill auto-detects your input type and enters the appropriate mode.
4. By default, get `DESIGN.md`, brand-facing `README.md`, `preview.html`, and `preview-dark.html` under `design-system/` in the target project.

## Further reading

- [Stitch: DESIGN.md overview](https://stitch.withgoogle.com/docs/design-md/overview/)
- [Stitch: DESIGN.md format](https://stitch.withgoogle.com/docs/design-md/format/)
- [Custom DESIGN.md request (getdesign.md)](https://getdesign.md/request)

## License

This repository is licensed under the [MIT License](./LICENSE). When using community templates or third-party `DESIGN.md` files, follow each source's terms.
