# Output File Specifications

Reference file for the detailed specifications of each output file in the design system package. Read this when you are ready to generate the output files (Step 6).

## Table of Contents

- [File 1: DESIGN.md](#file-1-designmd)
- [File 2: README.md](#file-2-readmemd)
- [File 3: preview.html](#file-3-previewhtml)
- [File 4: preview-dark.html](#file-4-preview-darkhtml)
- [File 5: Native Preview Snippets](#file-5-native-preview-snippets)
- [URL/Image Mode Additional Output](#urlimage-mode-additional-output)

---

## File 1: DESIGN.md

Use the Master Template from `references/master-template.md` (+ Mobile App Extension if applicable).

---

## File 2: README.md (Brand Introduction)

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

---

## File 3: preview.html (Light Mode Visual Catalog)

A self-contained HTML page that renders the design system as a visual catalog. Must include:

1. **Color Swatches**: All primary, secondary, surface, neutral, and semantic colors with hex labels
2. **Typography Scale**: Display, H1, H2, H3, Body, Caption samples with actual font stack
3. **Button Gallery**: Primary, Secondary, Danger, Disabled states
4. **Card Example**: A sample card using the actual shadow, border, radius, and background values
5. **Input Example**: Form input with focus state
6. **Spacing Scale**: Visual bars showing spacing increments
7. **Micro-Interactions Section**: A dedicated area demonstrating motion language

### Micro-Interactions Requirements

The preview must include live, interactive examples of:

- **Button States**: Hover transitions (scale 1.02, shadow lift, color shift), active press (scale 0.98), and loading spinner state
- **Input Focus**: Soft glow/focus ring fade-in (200-300ms ease-out), placeholder fade behavior
- **Card Hover**: Elevation lift with shadow deepening and subtle Y-axis translate (-2px to -4px)
- **Toggle/Switch**: Elastic spring animation when toggled (use CSS `transition` with `cubic-bezier(0.34, 1.56, 0.64, 1)`)
- **Feedback Pulse**: A success/checkmark micro-animation or gentle pulse on a CTA element
- **Stagger Reveal**: If showing a list or group, optional stagger fade-in on load (0.1s delay increments)

### App Simulation Mode (if project includes mobile app)

Within the same `preview.html`, add a **"Mobile Simulation"** section that mimics app interactions using CSS/JS:

- **Phone Frame Container**: A ~375px x 812px rounded container representing an iPhone/Android screen
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

---

## File 4: preview-dark.html (Dark Mode Visual Catalog)

Same structure as `preview.html`, but:

- Background uses the dark mode surface color from `DESIGN.md`
- Text uses the corresponding dark mode text colors
- Components render their dark variants (dark cards, dark inputs, dark buttons)
- Micro-interactions adapt to dark mode (e.g., focus glow should use the accent color with lower opacity, shadows may become inner-glows or border-glows)
- App simulation phone frame uses dark mode surfaces and OLED-safe background colors
- If `DESIGN.md` does not define explicit dark mode colors, derive them by inverting the background/text pairs and keeping accent colors unchanged

---

## File 5: Native Preview Snippets (Optional, if project includes mobile app)

If the user confirms they are building a native app, also generate lightweight preview snippets that developers can paste into Xcode or Android Studio to see real native micro-interactions:

**`Preview.swift`** (SwiftUI Preview for iOS)

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

**`Preview.kt`** (Jetpack Compose Preview for Android)

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

## URL/Image Mode Additional Output

When generating from a URL or image, also provide:

1. **Extraction Summary**: A brief summary of what was extracted vs. what was inferred:
  > "From [URL/image], I extracted: primary color `#3B82F6`, heading font 'Inter', button radius 8px. I inferred: spacing scale (4px base), shadow system (subtle layered). I asked you about: emotional metaphor, unreasonable choice."

2. **Confidence Rating**: For each major section, indicate confidence:
  - **High**: Directly extracted from the source (e.g., exact hex from CSS)
  - **Medium**: Inferred from visual analysis (e.g., font category from letterforms)
  - **Low**: Defaulted or heavily estimated (e.g., motion language from static image)

3. **Suggested Iterations**: List 2-3 specific follow-up prompts the user can use to refine the design system:
  > "To refine: try 'make the buttons more rounded' or 'add a secondary accent color in coral'"
