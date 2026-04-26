---

## name: design-md-generator
title: DESIGN.md Generator
description: Generate a comprehensive DESIGN.md design system document for web and mobile app projects, from project context, website URL, design screenshot, or by guiding a human step-by-step. Use this skill whenever the user asks for creating a design system, generating DESIGN.md, analyzing a website's visual design, extracting design elements from a screenshot or mockup, or producing visual/interaction specs for web or mobile apps — even if they don't explicitly use the word "DESIGN.md".
triggers:
  - "生成 DESIGN.md"
  - "create design md"
  - "幫我做設計系統文件"
  - "design system document"
  - "產品視覺規範"
  - "generate DESIGN.md"
  - "引導我寫 DESIGN.md"
  - "app 設計規範"
  - "分析這個網站設計"
  - "從這張圖片生成設計系統"
  - "design from url"
  - "design from image"
platforms:
  - hermes
  - claude-code

# DESIGN.md Generator

Generate a complete, production-ready `DESIGN.md` design system document based on project context, a live website, or a design screenshot. Supports both **web** and **mobile app (iOS/Android)** outputs. Can operate in four modes:

1. **Autonomous Mode**: Analyze existing project files and generate a full DESIGN.md automatically.
2. **URL Analysis Mode**: Extract visual design elements from a live website URL.
3. **Image Analysis Mode**: Analyze a design screenshot or mockup image.
4. **Guided Mode**: Interview the human step-by-step to co-create a unique design system (also used as gap-filling after URL/Image analysis).

## Trigger Conditions

Use this skill when the user asks for:

- Creating a new `DESIGN.md` from scratch
- Generating a design system document for a project
- Converting an existing design direction into a structured `DESIGN.md`
- Creating a **cross-platform** design system (web + app)
- Analyzing a website URL to extract its design system
- Analyzing a screenshot/mockup image to create a DESIGN.md

---

## Step 1: Input Detection & Mode Routing

Automatically detect the user's input type and route to the appropriate mode. **Do not ask the user which mode they want if the input type is unambiguous.**

### Input Type Decision Tree

```
User Input
├── URL (starts with http:// or https://)
│   └── → URL Analysis Mode (read references/modes.md#url-analysis-mode)
├── Image file (uploaded .png/.jpg/.jpeg/.webp/.gif or provided path)
│   └── → Image Analysis Mode (read references/modes.md#image-analysis-mode)
├── Existing project files (README.md, package.json, code files detected)
│   └── → Autonomous Mode (read references/modes.md#autonomous-mode)
└── Text description only / no specific input
    └── → Guided Mode (read references/modes.md#guided-mode)
```

### Ambiguous Input Handling

If the user provides **multiple types** (e.g., a URL + a screenshot), prioritize in this order:
1. **Image** (most specific visual source)
2. **URL** (live, interactive source)
3. **Project files** (contextual source)

Then ask:

> "I can work with multiple inputs here. Should I prioritize the [image/URL] for visual extraction, or the project files for context?"

---

## Mode Summaries

### Autonomous Mode

Analyze existing project files (README, manifest, styles) to infer design direction. Pick a design personality from the archetypes below based on product type and tech stack. **Avoid "AI flavor"** — do not default to Inter + `#3B82F6`. See `references/modes.md` for the full procedure.

### URL Analysis Mode

Extract colors, typography, components, layout, shadows, and border radius from a live website using WebFetch. Infer product type, audience, and emotional metaphor from the visual traits. Mark unextractable fields (deep narrative, "unreasonable choice", brand taboos) as `[MISSING]`. See `references/modes.md` for the full extraction checklist.

### Image Analysis Mode

Analyze a design screenshot or mockup image. Extract color palette, font categories, component styles, layout density, depth/elevation, and overall atmosphere. Mark unidentifiable fields (exact font names, precise pixel values, transition timing) as `[MISSING]`. See `references/modes.md` for the full visual analysis checklist.

### Guided Mode

Two sub-modes:
- **Full Interview** (standalone): Ask 8 structured questions one at a time (product, metaphor, unreasonable choice, platform, color, typography, density, motion).
- **Gap-Filling** (post-analysis): After URL/Image analysis, ask only the missing fields. Do not repeat already-extracted information.

See `references/modes.md` for the full question bank and gap-filling templates.

---

## Step 2: Data Sufficiency Check & Auto-Guided Gap-Filling

### Sufficiency Checklist

Before generating the final DESIGN.md, verify that all critical fields are filled (not placeholder, not `[MISSING]`):

| Priority | Check Item | Threshold |
|----------|------------|-----------|
| **P0** | Product name | Must have |
| **P0** | At least 1 primary color with hex | Must have |
| **P0** | Background color + text color | Must have |
| **P0** | Font family (heading + body) | Must have |
| **P0** | Emotional metaphor (2-3 sentences) | Must have |
| **P1** | "Unreasonable but right" choice | Must have |
| **P1** | Button style (padding, radius, colors) | Must have |
| **P1** | Card/container style | Must have |
| **P2** | Spacing system | Can infer |
| **P2** | Shadow system | Can infer |
| **P2** | Border radius scale | Can infer |
| **P2** | Breakpoints | Can infer |
| **P2** | Semantic colors | Can infer |
| **P2** | Do's and Don'ts | Can infer from metaphor |

### Decision Matrix

| Missing P0 | Missing P1 | Missing P2 | Action |
|------------|------------|------------|--------|
| 0 | 0 | 0-3 | **Generate immediately** with inferred P2 values |
| 0 | 1-2 | any | **Generate draft** + ask 1-2 targeted questions |
| 0 | 3+ | any | **Enter Gap-Filling** (references/modes.md#guided-mode) |
| 1+ | any | any | **Enter Gap-Filling**, must resolve P0 |

### Inference Rules for Missing Fields

When auto-generating values for insufficient data, follow these rules:

**If spacing system is missing:**
- Default to 4px base unit with scale: 4, 8, 12, 16, 24, 32, 48, 64, 96
- Adjust for density: dense products use 4/8/12/16; airy products use 8/16/24/32/48

**If shadow system is missing:**
- Vercel/Linear style (minimal shadows, borders instead) → use subtle 1px borders
- Material/Figma style → use layered shadows: `0 1px 3px rgba(0,0,0,0.1)`, `0 4px 12px rgba(0,0,0,0.08)`, `0 12px 32px rgba(0,0,0,0.12)`
- Apple/Notion style → use very subtle shadows or none

**If border radius is missing:**
- Engineer/developer tool → 4-6px (sharp, precise)
- Consumer/warm brand → 8-12px (friendly)
- Playful/creative → 16-24px (soft)
- Medical/finance → 2-4px (serious)

**If breakpoints are missing:**
- Default: Mobile 640px, Tablet 768px, Desktop 1024px, Wide 1280px
- Adjust for app-only projects to use device-specific breakpoints

**If semantic colors are missing:**
- Error: `#EF4444` (red-500) or darker `#DC2626`
- Warning: `#F59E0B` (amber-500)
- Success: `#10B981` (emerald-500) or `#22C55E`
- Info: `#3B82F6` (blue-500)
- **Exception**: If the brand color is red/orange/green/blue, shift semantic colors to avoid collision:
  - Red brand → Error becomes `#991B1B` (darker), or use `#E11D48` (rose)
  - Blue brand → Info becomes `#6366F1` (indigo)

---

## Step 3: Generate DESIGN.md

Read `references/master-template.md` for the full Master Template and Mobile App Extension. Fill every section with **specific values** (hex codes, px/rem values, font names). Never leave placeholders.

Key principles while filling:
- Inject at least one "unreasonable but right" choice (see Anti-Pattern Checklist)
- Include a specific emotional metaphor in Chapter 1
- Use exact values, no placeholders like "[value]" in final output

---

## Step 4: Anti-Pattern Checklist

Before finalizing the DESIGN.md, run this checklist. If any item is true, revise.

- **AI Flavor Check**: Does it default to Inter + `#3B82F6` + "clean modern"? If yes, change at least one.
- **Narrative Check**: Is there a specific emotional metaphor in Chapter 1? If no, add one.
- **Unreasonable Choice Check**: Is there at least one design rule that breaks industry convention? If no, add one.
- **Specificity Check**: Are all colors, sizes, and fonts given as exact values? No placeholders allowed.
- **App Gesture Check**: If mobile is included, are gestures mapped to physical metaphors?
- **Do's and Don'ts Check**: Are there at least 3 items in each list, and are they actionable?
- **URL Extraction Check** (if URL mode): Did you verify extracted colors against the actual rendered page? CSS variables may differ from computed styles.
- **Image Analysis Check** (if Image mode): Did you double-check inferred hex values against the image? Screen brightness and compression can shift perceived colors.
- **Semantic Collision Check**: Do semantic colors (error/warning/success/info) clash with brand colors? If brand is blue, info should be shifted to indigo.

---

## Step 5: Output Generation

By default, generate **all 4 files** in a `[project-root]/design-system/` directory (or project root if user prefers). Do not ask permission for each file — generate them as a complete package.

### Mode-Specific Notes

**Autonomous Mode:**
- Write to `[project-root]/design-system/`
- Use project context to name the design system

**URL Analysis Mode:**
- Write to `[project-root]/design-system/` or a directory named after the extracted brand/URL domain
- Prefix the design system name with the domain (e.g., "Design System: example.com Inspired")
- Include a note: "Based on visual analysis of [URL] as of [date]"

**Image Analysis Mode:**
- Write to `[project-root]/design-system/` or a directory named after the image file (without extension)
- Prefix with the inferred brand or "Unnamed Project"
- Include a note: "Based on visual analysis of [image filename]"

**Guided Mode:**
- Write to `[project-root]/design-system/`
- Use the product name provided by the user

### Output Files

1. **`DESIGN.md`** — Use the Master Template (+ Mobile Extension if applicable)
2. **`README.md`** — Brand-facing introduction. See `references/output-specs.md` for the template.
3. **`preview.html`** — Light mode visual catalog with color swatches, typography scale, button gallery, card/input examples, spacing scale, and micro-interactions. See `references/output-specs.md` for detailed requirements.
4. **`preview-dark.html`** — Dark mode variant. See `references/output-specs.md` for requirements.

Optional File 5: **Native Preview Snippets** (`Preview.swift` / `Preview.kt`) if building a native app. See `references/output-specs.md`.

### Output Instructions

1. Write all files to the designated directory.
2. Inform the user where they were saved and what mode was used.
3. Summarize the "unreasonable choice" and the emotional metaphor in one sentence.
4. Offer to generate additional files: `AGENTS.md`, `tailwind.config.js`, `tokens.json`, Figma variables JSON.

For URL/Image modes, also provide:
- **Extraction Summary**: What was extracted vs. inferred vs. asked
- **Confidence Rating**: High / Medium / Low per section
- **Suggested Iterations**: 2-3 follow-up prompts to refine the design system

See `references/output-specs.md` for full details.

---

## References

| File | Read When |
|------|-----------|
| `references/modes.md` | When entering any of the 4 modes for detailed extraction/interview procedures |
| `references/master-template.md` | When filling the DESIGN.md template and mobile extension |
| `references/output-specs.md` | When generating the 4 output files (preview.html requirements, README template, native snippets) |

---

## Personality Archetypes (Reference)

Use these as starting points, but always customize.

| Archetype | Emotional Metaphor | Typical Colors | Typical Typography | Representative Brand |
|-----------|-------------------|----------------|-------------------|---------------------|
| **Dark Engineer** | A high-end recording studio at midnight | Near-black bg, single saturated accent | Geometric sans, tight tracking | Linear, Vercel |
| **Warm Salon** | A letter from a thoughtful friend | Parchment, terracotta, warm grays | Serif headings, sans UI | Claude |
| **Minimalist Gallery** | A white cube art space | Pure white, subtle warm gray, one earthy accent | Humanist sans | Apple, Notion |
| **Vibrant Workshop** | A creative studio with paint everywhere | Bold saturated palette, high contrast | Expressive sans or mixed | Figma, Framer |
| **Deep Terminal** | A spaceship control panel | Carbon black, neon green/blue accent | Monospace + geometric sans | VoltAgent, Warp |
