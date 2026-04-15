---

## name: design-md-generator
title: DESIGN.md Generator
description: Generate a comprehensive DESIGN.md design system document for web and mobile app projects, either autonomously from project context or by guiding a human step-by-step.
triggers:
  - "生成 DESIGN.md"
  - "create design md"
  - "幫我做設計系統文件"
  - "design system document"
  - "產品視覺規範"
  - "generate DESIGN.md"
  - "引導我寫 DESIGN.md"
  - "app 設計規範"
platforms:
  - hermes
  - claude-code

# DESIGN.md Generator

Generate a complete, production-ready `DESIGN.md` design system document based on project context. Supports both **web** and **mobile app (iOS/Android)** outputs. Can operate in two modes:

1. **Autonomous Mode**: Analyze existing project files and generate a full DESIGN.md automatically.
2. **Guided Mode**: Interview the human step-by-step to co-create a unique design system.

## Trigger Conditions

Use this skill when the user asks for:

- Creating a new `DESIGN.md` from scratch
- Generating a design system document for a project
- Converting an existing design direction into a structured `DESIGN.md`
- Creating a **cross-platform** design system (web + app)

## Step 1: Determine Mode

Ask the user (or infer from context):

> "I can generate the DESIGN.md in two ways:
>
> 1. **Autonomous Mode** — I analyze your existing project files (README, tech stack, screenshots, code) and generate a complete DESIGN.md.
> 2. **Guided Mode** — I ask you 8-10 focused questions about your product's personality and audience, then write the document together.
>
> Which mode do you prefer?"

If they choose **Autonomous Mode**, proceed to Step 2A.  
If they choose **Guided Mode**, proceed to Step 2B.

---

## Step 2A: Autonomous Mode — Project Analysis

1. **Inspect project context**:
  - Read `README.md`, `package.json`, `Cargo.toml`, or equivalent manifest files.
  - Look for any existing UI screenshots, Figma links, or style files (`globals.css`, `theme.ts`, `tailwind.config.js`).
  - Identify the product type: SaaS dashboard, AI chat, e-commerce, developer tool, content app, etc.
2. **Infer design direction**:
  - Based on the product type and tech stack, pick a "design personality" (see Personality Archetypes below).
  - If the project is B2B developer tool → lean toward dark engineering aesthetic (Linear/Vercel inspired).
  - If the project is consumer AI companion → lean toward warm literary salon (Claude inspired).
  - If the project is creative tool → lean toward vibrant, expressive system (Figma/Framer inspired).
3. **Generate DESIGN.md** using the **Master Template** in Step 3.
  - Fill in all sections with specific hex colors, font families, spacing scales, and component rules.
  - **Avoid "AI flavor"**: Do not default to Inter + `#3B82F6` + "clean modern interface". Inject at least one "unreasonable but right" choice (see Section 1.3 in the template).
4. **Output**:
  - Follow **Step 6** and **Output Instructions** at the end of this skill (default: write the package under `[project-root]/design-system/`, not the repo root alone).

---

## Step 2B: Guided Mode — Human Interview

Conduct a structured interview. Ask **one question at a time** and build upon previous answers.

### Questionnaire (ask in order)

**Q1. Product & Audience**

> "用一句話描述你的產品是什麼，以及核心用戶是誰？"
> (e.g., "A note-taking app for nighttime programmers")

**Q2. Emotional Metaphor**

> 「如果你的產品是一個『場所』，它會是什麼？請用具體的類比描述氛圍。」
> (e.g., "a 24-hour convenience store at 3 AM — lonely but warm, with neon glow")

**Q3. One Unreasonable Choice**

> 「市面上同類產品都在用什麼設計慣例？你想故意打破哪一條？」
> (e.g., "All dev tools are dark mode. I want mine to be aggressively light.")

**Q4. Platform Scope**

> 「這個設計系統要覆蓋哪些平台？」
>
> - Web only
> - Mobile App only (iOS/Android)
> - Both Web + Mobile App

**Q5. Color Constraint**

> 「有沒有一個對你有特殊意義的顏色？（如工作室牆面顏色、家鄉土壤顏色）如果沒有，給我一個情緒詞，我來幫你轉譯。」

**Q6. Typography Personality**

> 「你的產品『說話』的聲音是什麼樣的？選一個最接近的：
>
> - 冷靜的工程師（等寬/幾何無襯線）
> - 溫暖的編輯（襯線體）
> - 前衛的藝術家（實驗字體）
> - 可靠的管家（經典人文主義無襯線）」

**Q7. Density Preference**

> 「介面應該感覺『擁擠但強大』還是『寬鬆但從容』？」
> (Information-dense like Bloomberg Terminal vs. breathable like Aesop website)

**Q8. Motion & Interaction**

> 「當用戶完成一個重要操作時，你希望產品給出什麼樣的反饋？選一個：
>
> - 精確的機械咔噠聲
> - 溫柔的彈性回饋
> - 華麗的慶祝動效
> - 幾乎無聲的沈默確認」

After Q8, synthesize all answers and generate the `DESIGN.md` using the Master Template in Step 3.

---

## Step 3: Master Template

Use this exact structure. Fill every section with **specific values** (hex codes, px/rem values, font names). Never leave placeholders.

```markdown
# Design System: [Product Name]

## 1. Visual Theme & Atmosphere

[2-3 paragraphs describing the emotional and philosophical core of the design.]

**Key Characteristics:**
- [Distinctive trait 1 with specific value]
- [Distinctive trait 2 with specific value]
- [Distinctive trait 3 with specific value]
- [At least one "unreasonable but right" choice]

## 2. Color Palette & Roles

### Primary
- **[Color Name]** (`#HEXCODE`): [Role and emotional meaning]

### Secondary & Accent
- **[Color Name]** (`#HEXCODE`): [Role]

### Surface & Background
- **[Color Name]** (`#HEXCODE`): [Role]

### Neutrals & Text
- **[Color Name]** (`#HEXCODE`): [Role]

### Semantic Colors (Error, Warning, Success, Info)
- **Error** (`#HEXCODE`)
- **Warning** (`#HEXCODE`)
- **Success** (`#HEXCODE`)
- **Info** (`#HEXCODE`)

## 3. Typography Rules

### Font Family
- **Headings**: [Font name, fallback stack]
- **Body**: [Font name, fallback stack]
- **Code/Mono**: [Font name, fallback stack]

### Hierarchy
| Level | Size | Weight | Line-Height | Letter-Spacing | Use Case |
|-------|------|--------|-------------|----------------|----------|
| Display | [px/rem] | [weight] | [ratio] | [px] | Hero headlines |
| H1 | [px/rem] | [weight] | [ratio] | [px] | Page titles |
| H2 | [px/rem] | [weight] | [ratio] | [px] | Section headers |
| H3 | [px/rem] | [weight] | [ratio] | [px] | Sub-sections |
| Body | [px/rem] | [weight] | [ratio] | [px] | Paragraphs |
| Caption | [px/rem] | [weight] | [ratio] | [px] | Labels, metadata |
| Code | [px/rem] | [weight] | [ratio] | [px] | Inline code |

### Principles
- [Principle 1]
- [Principle 2]
- [Principle 3]

## 4. Component Stylings

### Buttons

**Primary Button**
- Background: `[color]` (`#HEX`)
- Text: `[color]` (`#HEX`)
- Padding: `[value]`
- Radius: `[value]`
- Hover/Active: [specific state rules]

**Secondary Button**
- Background: `[color]` (`#HEX`)
- Text: `[color]` (`#HEX`)
- Padding: `[value]`
- Radius: `[value]`
- Hover/Active: [specific state rules]

**Danger Button**
- Background: `[color]` (`#HEX`)
- Text: `[color]` (`#HEX`)
- Padding: `[value]`
- Radius: `[value]`

### Cards & Containers
- Background: `[color]` (`#HEX`)
- Border: `[value] solid [color]`
- Radius: `[value]`
- Shadow: `[shadow values]`

### Inputs & Forms
- Background: `[color]`
- Text: `[color]`
- Border: `[value] solid [color]`
- Focus ring: `[value] [color]`
- Radius: `[value]`
- Padding: `[value]`

### Navigation
- Background: `[color]`
- Link color: `[color]`
- Active link: `[color]`
- CTA treatment: [button style reference]

### Links
- Default: `[color]`
- Hover: `[color]`
- Visited: `[color]` (if applicable)

### Distinctive Components
[Describe 1-3 components unique to this product.]

## 5. Layout Principles

### Spacing System
- Base unit: `[px/rem]`
- Scale: `[list of values]`

### Grid & Container
- Max container width: `[value]`
- Gutter: `[value]`
- Columns: `[number]`

### Whitespace Philosophy
[1-2 sentences on how space is used meaningfully.]

### Border Radius Scale
- Small: `[value]` — inputs, badges
- Medium: `[value]` — cards, buttons
- Large: `[value]` — modals, featured sections
- Full: `[value]` — pills, avatars

## 6. Depth & Elevation

### Shadow System
| Level | Shadow Value | Use Case |
|-------|--------------|----------|
| Flat | `none` | Base surfaces |
| Subtle | `[value]` | Cards, inputs |
| Elevated | `[value]` | Dropdowns, popovers |
| Floating | `[value]` | Modals, toasts |

### Elevation Philosophy
[Describe whether the product uses shadows for depth, borders for structure, or a hybrid approach like Vercel's "shadow-as-border" technique.]

## 7. Do's and Don'ts

### Do
- [Specific, actionable rule 1]
- [Specific, actionable rule 2]
- [Specific, actionable rule 3]
- [At least one rule that enforces the "unreasonable choice"]

### Don't
- [Specific anti-pattern 1]
- [Specific anti-pattern 2]
- [Specific anti-pattern 3]
- [At least one rule that explicitly forbids a common cliché]

## 8. Responsive Behavior

### Breakpoints
- Mobile: `[px]`
- Tablet: `[px]`
- Desktop: `[px]`
- Wide: `[px]`

### Touch Targets
- Web minimum: `[px] x [px]`
- App minimum (iOS): `44px x 44px`
- App minimum (Android): `48px x 48px`

### Collapsing Strategy
- Navigation: [how it transforms]
- Grids: [how columns collapse]
- Typography: [how sizes scale]
- Spacing: [how padding adjusts]

### Image Behavior
[How media scales, aspect ratios, art direction if any.]

## 9. Agent Prompt Guide

### Quick Color Reference
- Brand CTA: "[Color Name] (#HEX)"
- Page Background: "[Color Name] (#HEX)"
- Card Surface: "[Color Name] (#HEX)"
- Primary Text: "[Color Name] (#HEX)"
- Secondary Text: "[Color Name] (#HEX)"
- Border: "[Color Name] (#HEX)"

### Example Component Prompts
- "Create a hero section on [Background] (#HEX) with a [size] [font] headline..."
- "Design a feature card on [Surface] (#HEX) with a [border] border and [radius] radius..."
- "Build a [state] button in [color] (#HEX) with [text color] text..."

### Iteration Guide
1. Focus on ONE component at a time
2. Reference specific color names with hex values
3. Always specify the background surface for context
4. Use exact typography specs (font, size, weight, line-height)
5. Follow the Do's and Don'ts strictly
```

---

## Step 4: Mobile App Extension (If Applicable)

If the project includes **mobile app**, append these three chapters to the DESIGN.md **after** Chapter 9.

```markdown
## 10. Platform Adaptation

### iOS
- Safe Area compliance: all content respects top/bottom safe area insets
- System font: SF Pro (do not use Android fonts on iOS)
- Navigation pattern: [Tab Bar / Navigation Stack / Modal Sheets]
- Haptic feedback: [light / medium / heavy] for [specific actions]

### Android
- System font: Roboto / Noto Sans CJK
- Navigation pattern: [Bottom Navigation / Navigation Drawer / Floating Action Button]
- Dynamic color: [enabled / disabled]
- Back button behavior: [specific rule]

### Cross-Platform Taboos
- Never use hamburger menu as primary navigation on iOS
- Never use iOS-style back chevrons on Android
- Never use pure black `#000000` as dark mode background (use `#0f0f11` or `#121212`)

## 11. Gesture Semantics

| Intent | Gesture | Physical Metaphor |
|--------|---------|-------------------|
| Delete | Swipe left + haptic | Tearing a paper note |
| Reorder | Long-press + drag | Picking up a Lego block |
| Go back | Edge swipe right | Turning a book page |
| Refresh | Pull down + elastic snap | Pulling a rubber band |
| Quick actions | Long-press bubble | Peeling a sticker |
| Dismiss modal | Swipe down | Sliding a card off the table |

## 12. System Component Mapping

| Web Component | iOS Native | Android Native |
|---------------|------------|----------------|
| Primary Button | UIButton (filled) | Material Button (filled) |
| Modal Dialog | UIAlertController / UISheetPresentationController | AlertDialog / BottomSheet |
| Dropdown | UIPickerView / UIActionSheet | Exposed Dropdown Menu |
| Toast / Snackbar | Custom UIKit overlay | Snackbar |
| Toggle | UISwitch | Material Switch |
| Text Field | UITextField | TextInputLayout |
| Card | UICollectionViewCell | Material Card |
```

---

## Step 5: Anti-Pattern Checklist

Before finalizing the DESIGN.md, run this checklist. If any item is true, revise.

- **AI Flavor Check**: Does it default to Inter + `#3B82F6` + "clean modern"? If yes, change at least one.
- **Narrative Check**: Is there a specific emotional metaphor in Chapter 1? If no, add one.
- **Unreasonable Choice Check**: Is there at least one design rule that breaks industry convention? If no, add one.
- **Specificity Check**: Are all colors, sizes, and fonts given as exact values? No placeholders allowed.
- **App Gesture Check**: If mobile is included, are gestures mapped to physical metaphors?
- **Do's and Don'ts Check**: Are there at least 3 items in each list, and are they actionable?

---

## Personality Archetypes (Reference)

Use these as starting points, but always customize.


| Archetype              | Emotional Metaphor                      | Typical Colors                                  | Typical Typography             | Representative Brand |
| ---------------------- | --------------------------------------- | ----------------------------------------------- | ------------------------------ | -------------------- |
| **Dark Engineer**      | A high-end recording studio at midnight | Near-black bg, single saturated accent          | Geometric sans, tight tracking | Linear, Vercel       |
| **Warm Salon**         | A letter from a thoughtful friend       | Parchment, terracotta, warm grays               | Serif headings, sans UI        | Claude               |
| **Minimalist Gallery** | A white cube art space                  | Pure white, subtle warm gray, one earthy accent | Humanist sans                  | Apple, Notion        |
| **Vibrant Workshop**   | A creative studio with paint everywhere | Bold saturated palette, high contrast           | Expressive sans or mixed       | Figma, Framer        |
| **Deep Terminal**      | A spaceship control panel               | Carbon black, neon green/blue accent            | Monospace + geometric sans     | VoltAgent, Warp      |


---

## Step 6: Complete Design System Package (4 Files)

By default, generate **all 4 files** in a `[project-root]/design-system/` directory (or project root if user prefers). Do not ask permission for each file — generate them as a complete package.

### File 1: `DESIGN.md`

Use the Master Template from Step 3 (+ Step 4 App extension if applicable).

### File 2: `README.md` (Brand Introduction)

A concise brand-facing document that introduces the design system without technical implementation details.

```markdown
# [Product Name] Design System

## Design Philosophy

[1-paragraph summary of the emotional metaphor and core idea from DESIGN.md Chapter 1.]

## Key Principles

- **[Principle 1]**: [One-sentence explanation]
- **[Principle 2]**: [One-sentence explanation]
- **[Principle 3]**: [One-sentence explanation]

## Color Essence

| Role | Color | Hex | Meaning |
|------|-------|-----|---------|
| Primary | [Name] | `#HEX` | [Emotional meaning] |
| Background | [Name] | `#HEX` | [Atmosphere role] |
| Accent | [Name] | `#HEX` | [Highlight role] |

## Typography Voice

- **Headings**: [Font] — [personality description]
- **Body**: [Font] — [personality description]

## What's Included

- `DESIGN.md` — Complete design system specification for AI agents and developers
- `preview.html` — Light mode visual component catalog
- `preview-dark.html` — Dark mode visual component catalog

## Usage

Drop `DESIGN.md` into your project root and reference it when prompting AI coding agents.
```

### File 3: `preview.html` (Light Mode Visual Catalog)

A self-contained HTML page that renders the design system as a visual catalog. Must include:

1. **Color Swatches**: All primary, secondary, surface, neutral, and semantic colors with hex labels
2. **Typography Scale**: Display, H1, H2, H3, Body, Caption samples with actual font stack
3. **Button Gallery**: Primary, Secondary, Danger, Disabled states
4. **Card Example**: A sample card using the actual shadow, border, radius, and background values
5. **Input Example**: Form input with focus state
6. **Spacing Scale**: Visual bars showing spacing increments
7. **Micro-Interactions Section**: A dedicated area demonstrating motion language

#### Micro-Interactions Requirements

The preview must include live, interactive examples of:

- **Button States**: Hover transitions (scale 1.02, shadow lift, color shift), active press (scale 0.98), and loading spinner state
- **Input Focus**: Soft glow/focus ring fade-in (200-300ms ease-out), placeholder fade behavior
- **Card Hover**: Elevation lift with shadow deepening and subtle Y-axis translate (-2px to -4px)
- **Toggle/Switch**: Elastic spring animation when toggled (use CSS `transition` with `cubic-bezier(0.34, 1.56, 0.64, 1)`)
- **Feedback Pulse**: A success/checkmark micro-animation or gentle pulse on a CTA element
- **Stagger Reveal**: If showing a list or group, optional stagger fade-in on load (0.1s delay increments)

#### App Simulation Mode (if project includes mobile app)

Within the same `preview.html`, add a **"Mobile Simulation"** section that mimics app interactions using CSS/JS:

- **Phone Frame Container**: A ~375px × 812px rounded container representing an iPhone/Android screen
- **Touch Target Rings**: Visual 44px/48px radius circles appearing briefly on tap to demonstrate compliance
- **Gesture Hints**: Swipe arrows and instructional overlays for edge-swipe-back, pull-to-refresh, long-press menus
- **Bottom Navigation Bar**: Rendered inside the phone frame using the app-safe-area bottom padding
- **Haptic Visualizer**: A small ripple or screen flash on tap to simulate haptic feedback visually
- **Page Transition Simulation**: A push/pop slide animation between two dummy screens when tapping navigation items

Technical requirements:

- Single-file, no external JS dependencies (pure CSS transitions + optional lightweight inline JS for click states)
- Use CSS custom properties (variables) for colors to keep `DESIGN.md` and `preview.html` in sync
- Embed all CSS in `<style>` and any JS in `<script>`
- Use the exact hex colors, fonts, easing curves, and spacing from `DESIGN.md`
- Load web fonts via Google Fonts or jsDelivr CDN if needed
- Responsive container (~900px max-width, centered)

### File 4: `preview-dark.html` (Dark Mode Visual Catalog)

Same structure as `preview.html`, but:

- Background uses the dark mode surface color from `DESIGN.md`
- Text uses the corresponding dark mode text colors
- Components render their dark variants (dark cards, dark inputs, dark buttons)
- Micro-interactions adapt to dark mode (e.g., focus glow should use the accent color with lower opacity, shadows may become inner-glows or border-glows)
- App simulation phone frame uses dark mode surfaces and OLED-safe background colors
- If `DESIGN.md` does not define explicit dark mode colors, derive them by inverting the background/text pairs and keeping accent colors unchanged

### File 5: Native Preview Snippets (Optional, if project includes mobile app)

If the user confirms they are building a native app, also generate lightweight preview snippets that developers can paste into Xcode or Android Studio to see real native micro-interactions:

`**Preview.swift`** (SwiftUI Preview for iOS)

```swift
import SwiftUI

struct DesignSystemPreview: View {
    var body: some View {
        // Renders primary button, card, toggle, and input
        // with the exact colors and corner radius from DESIGN.md
    }
}

#Preview {
    DesignSystemPreview()
}
```

`**Preview.kt**` (Jetpack Compose Preview for Android)

```kotlin
@Preview
@Composable
fun DesignSystemPreview() {
    // Renders primary button, card, switch, and text field
    // with the exact colors and shapes from DESIGN.md
}
```

Requirements:

- Use hardcoded hex values from `DESIGN.md` (do not use Material dynamic theming unless explicitly requested)
- Include a basic `@State` toggle demo to show the switch/check animation
- Include a `Button` with ripple enabled/disabled per the design system's preference
- Show a `Card` with the exact elevation/shadow values

Note: Native previews are optional quick-starts, not production code. They help bridge the gap between `DESIGN.md` specs and actual platform implementation.

---

## Output Instructions

1. **Write all 4 files** to `[project-root]/design-system/`:
  - `DESIGN.md`
  - `README.md`
  - `preview.html`
  - `preview-dark.html`
2. **Inform the user** where they were saved and what mode was used.
3. **Summarize** the "unreasonable choice" and the emotional metaphor in one sentence.
4. **Offer** to generate additional files if needed:
  - `AGENTS.md` (coding agent instructions)
  - `tailwind.config.js` or `tokens.json` export
  - Figma variables JSON

