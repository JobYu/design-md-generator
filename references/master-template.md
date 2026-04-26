# Master Template

Reference file containing the DESIGN.md template and mobile app extension. Read this when you are ready to generate the DESIGN.md content.

## Table of Contents

- [DESIGN.md Master Template](#designmd-master-template)
- [Mobile App Extension](#mobile-app-extension)

---

## DESIGN.md Master Template

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

## Mobile App Extension

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
