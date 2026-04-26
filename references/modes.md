# Mode Instructions

Reference file for the detailed instructions of each generation mode. Read the section corresponding to the mode selected in Step 1.

## Table of Contents

- [Autonomous Mode](#autonomous-mode)
- [URL Analysis Mode](#url-analysis-mode)
- [Image Analysis Mode](#image-analysis-mode)
- [Guided Mode](#guided-mode)

---

## Autonomous Mode

1. **Inspect project context**:
  - Read `README.md`, `package.json`, `Cargo.toml`, or equivalent manifest files.
  - Look for any existing UI screenshots, Figma links, or style files (`globals.css`, `theme.ts`, `tailwind.config.js`).
  - Identify the product type: SaaS dashboard, AI chat, e-commerce, developer tool, content app, etc.
2. **Infer design direction**:
  - Based on the product type and tech stack, pick a "design personality" (see Personality Archetypes in the main SKILL.md).
  - If the project is B2B developer tool → lean toward dark engineering aesthetic (Linear/Vercel inspired).
  - If the project is consumer AI companion → lean toward warm literary salon (Claude inspired).
  - If the project is creative tool → lean toward vibrant, expressive system (Figma/Framer inspired).
3. **Generate DESIGN.md** using the **Master Template** from `references/master-template.md`.
  - Fill in all sections with specific hex colors, font families, spacing scales, and component rules.
  - **Avoid "AI flavor"**: Do not default to Inter + `#3B82F6` + "clean modern interface". Inject at least one "unreasonable but right" choice.
4. **Execute Data Sufficiency Check** (Step 2.5 in main SKILL.md):
  - If critical fields are missing, enter **Guided Gap-Filling** before final generation.
5. **Output**: Follow Step 6 in the main SKILL.md.

---

## URL Analysis Mode

Use this mode when the user provides a website URL. Extract the design system directly from the live site.

### Fetch Website Content

Use WebFetch to retrieve the target URL. Fetch both:
- The main page HTML (for structure and content)
- The rendered visual output (for accurate color and layout analysis)

If the site uses client-side rendering (React/Vue/SPA), note that some dynamic styles may not be fully captured. In that case, infer missing values from visible elements.

### Extract Visual Elements

Analyze the fetched content systematically. Document your findings in a structured extraction note.

**Color Extraction:**
- **Primary/Brand**: Extract from `--primary`, `--brand`, `--color-primary` CSS variables; CTA button backgrounds; active navigation links.
- **Accent**: Extract from secondary CTAs, hover states, highlight badges, links.
- **Background**: Extract from `body`, `main`, `.container`, card backgrounds. Note both light and dark mode if detected.
- **Text**: Extract from `body`, `h1-h6`, `.text-primary`, `.text-secondary`.
- **Surface/Border**: Extract from card backgrounds, input borders, dividers.
- **Semantic**: Extract from error messages (red), success states (green), warnings (yellow/amber), info (blue).
- **Neutrals**: Extract gray scale from text, borders, disabled states.

**Typography Extraction:**
- **Heading font**: From `h1-h6` `font-family`, weight, and size hierarchy.
- **Body font**: From `body`/`p` `font-family`, size, line-height.
- **Code font**: From `code`, `pre` elements.
- **Hierarchy**: Document the actual pixel/rem sizes for H1, H2, H3, Body, Caption as used on the site.
- **Letter-spacing**: Note any tight or loose tracking (e.g., uppercase labels with wide tracking).

**Component Style Extraction:**
- **Buttons**: padding, border-radius, background color, text color, hover/active states, font-weight.
- **Cards/Containers**: background, border (width, color, style), border-radius, box-shadow, padding.
- **Inputs/Forms**: background, border, focus ring style, border-radius, padding, placeholder color.
- **Navigation**: background color, link color, active/hover link treatment, height.
- **Links**: default color, hover color, underline behavior.
- **Badges/Tags**: background, text color, border-radius, padding.

**Layout Extraction:**
- **Container max-width**: From `.container`, `.wrapper`, `.max-w-*` classes.
- **Grid system**: Columns, gutters, gap values.
- **Spacing**: Base unit and scale (e.g., 4px, 8px, 16px, 24px, 32px, 48px, 64px).
- **Breakpoints**: From `@media` queries in CSS.

**Shadow & Depth Extraction:**
- **Box-shadow values**: From cards, dropdowns, modals, buttons.
- **Depth philosophy**: Does the site use shadows for elevation (Material) or borders for structure (Vercel/Linear)?

**Border Radius Extraction:**
- Small (inputs, badges)
- Medium (cards, buttons)
- Large (modals, featured sections)
- Full (pills, avatars)

### Infer Design Personality

Based on extracted elements, infer:
- **Product type**: SaaS, e-commerce, developer tool, content platform, social app, etc.
- **Target audience**: Developers, consumers, enterprise, creatives.
- **Emotional metaphor**: Map visual traits to a place/feeling:
  - Dark + neon accents → "spaceship control panel" (Deep Terminal)
  - Warm + serif fonts → "a letter from a thoughtful friend" (Warm Salon)
  - White + minimal → "white cube art gallery" (Minimalist Gallery)
  - Bold + saturated → "creative studio with paint everywhere" (Vibrant Workshop)
  - Near-black + single accent → "high-end recording studio at midnight" (Dark Engineer)
- **Density preference**: Information-dense (Bloomberg Terminal) vs. breathable (Aesop website).
- **Motion language**: From any visible animations or transitions in CSS.

### Fill the Master Template

Populate the Master Template from `references/master-template.md` with extracted values. Use `[MISSING: description]` placeholders for fields that cannot be extracted.

**Common unextractable fields (mark as MISSING):**
- Deep emotional narrative in Chapter 1 (beyond surface-level visual inference)
- The "unreasonable but right" choice (requires user intent)
- Specific brand-origin color meanings (e.g., "studio wall color")
- Mobile-specific gesture mappings (unless the URL is a mobile app web view)
- Explicit Do's and Don'ts rooted in brand values

### Execute Data Sufficiency Check

Run Step 2.5 from the main SKILL.md. If gaps are found, enter **Guided Gap-Filling** before generating the final DESIGN.md.

---

## Image Analysis Mode

Use this mode when the user provides an image file (screenshot, Figma export, design mockup, mood board).

### Read the Image

Use the Read tool to load the image file. The image may be:
- A full-page website screenshot
- A mobile app screen
- A Figma/Sketch design export
- A mood board or style reference
- A partial component collage

### Visual Analysis Checklist

Analyze the image comprehensively. Document findings in a structured extraction note.

**Color Palette Analysis:**
- **Dominant color**: The most visually prominent color (usually brand/primary).
- **Background colors**: Page background, card surfaces, section backgrounds.
- **Text colors**: Primary text, secondary text (labels, metadata), inverted text on dark backgrounds.
- **Accent colors**: CTA buttons, links, highlights, status indicators.
- **Neutral palette**: Grays used for borders, dividers, disabled states.
- **Dark mode colors**: If the image shows dark mode, document those separately.
- For each color, provide the hex value if clearly identifiable, or a close approximation.

**Typography Analysis:**
- **Font style category**:
  - Sans-serif (geometric, humanist, grotesque)
  - Serif (modern, transitional, slab)
  - Monospace
  - Display/experimental
- **Heading characteristics**: Size relative to body, weight (light/regular/bold), letter-spacing, casing (sentence/uppercase/title).
- **Body characteristics**: Size, weight, line-height perception (tight/normal/loose).
- **Hierarchy levels**: Count distinct text sizes visible (e.g., 5 levels: hero, heading, subheading, body, caption).
- **Code/technical text**: If present, note the style.

**Component Recognition:**
- **Buttons**: Identify all button styles (primary, secondary, ghost, danger). Note shape (pill, rounded, square), shadow, and size.
- **Cards/Containers**: Note background treatment (solid, translucent, gradient), border, shadow, corner radius.
- **Input fields**: Border style, focus indication, background, placeholder visibility.
- **Navigation**: Top bar, sidebar, tab bar, bottom nav — note style, height, background treatment.
- **Tags/Badges/Chips**: Small label elements, note shape, color, and size.
- **Tables/Lists**: If present, note row separators, hover states, selection states.
- **Modals/Overlays**: Note backdrop treatment, shadow, and border.

**Layout & Spacing Analysis:**
- **Density**: Crowded vs. airy. Count approximate elements per screen area.
- **Alignment**: Left-aligned, center-aligned, or mixed.
- **Whitespace**: Generous margins/padding vs. edge-to-edge content.
- **Grid**: Visible columns, card arrangements, or asymmetric layouts.
- **Safe area**: If mobile, note top/bottom spacing for system bars.

**Depth & Elevation:**
- **Shadow usage**: Soft diffused shadows, sharp drop shadows, or no shadows (flat).
- **Border usage**: 1px hairlines, thick borders, or borderless.
- **Layering**: Overlapping elements, floating action buttons, sticky headers.

**Motion & Interaction Clues (if visible):**
- Hover states captured in the image (e.g., button with different background).
- Active/selected states (tab underlines, list selections).
- Loading states or skeletons if visible.

**Overall Atmosphere:**
- Describe the mood in 3-5 adjectives (e.g., "clinical, precise, premium, subdued").
- Match to the closest **Personality Archetype** (see main SKILL.md).
- Note any reference brand the design resembles.

### Fill the Master Template

Same as URL Analysis. Use `[MISSING: description]` for unidentifiable fields.

**Common unextractable fields from images:**
- Exact font names (unless clearly identifiable from letterforms)
- Exact pixel values for spacing (estimate with "approx. Xpx")
- Hover/active transition timing and easing curves
- Responsive breakpoint behavior
- Deep brand narrative and emotional metaphor
- "Unreasonable but right" design choices
- Brand constraints and taboos

### Execute Data Sufficiency Check

Run Step 2.5 from the main SKILL.md. If gaps are found, enter **Guided Gap-Filling**.

---

## Guided Mode

### Full Interview (standalone mode)

Use this when the user starts with no specific input, or explicitly asks for guided mode.

Conduct a structured interview. Ask **one question at a time** and build upon previous answers.

#### Questionnaire (ask in order)

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

After Q8, synthesize all answers and generate the `DESIGN.md` using the Master Template from `references/master-template.md`.

### Guided Gap-Filling (post-analysis mode)

Use this after URL or Image analysis when the Data Sufficiency Check detects missing fields. **Do not repeat questions for fields already extracted.** Only ask about missing information.

**Opening statement:**

> "我已經從 [URL/圖片] 分析了你的設計方向。以下是提取到的關鍵元素：
>
> - 主色：[顏色]（#[hex]）
> - 字體風格：[推斷的字體類型]
> - 整體氛圍：[推斷的氣氛描述]
> - 產品類型：[推斷的類型]
>
> 為了讓設計系統更完整，我還需要確認幾個細節："

**Missing-field Question Bank** (ask only for fields marked MISSING):

**If Product Name/Audience is missing:**
> "這個設計是為什麼產品服務的？核心用戶是誰？"

**If Emotional Metaphor is missing or weak:**
> "從 [提取的顏色/字體/布局] 來看，這個設計給人的感覺是 [推斷的情感]。你會怎麼用具體的場所或場景來描述這個產品的氛圍？"

**If "Unreasonable Choice" is missing:**
> 「市面上同類產品通常 [行業慣例觀察]。你想故意打破哪一條規則來讓自己的產品與眾不同？」

**If Color Meaning is missing:**
> "主色 [hex] 對你的品牌有什麼特殊意義嗎？（如來自 logo、團隊文化、或純粹的美學選擇）"

**If Typography is unconfirmed:**
> "從圖片中我推斷標題使用 [推斷字體類型]，正文使用 [推斷字體類型]。這個判斷正確嗎？有沒有指定的字體名稱？"

**If Brand Taboos/Constraints are unknown:**
> "有沒有什麼顏色、字體或設計元素是這個品牌絕對不能用的？"

**If Mobile App scope is unclear:**
> 「這個設計系統需要覆蓋手機 App（iOS/Android）嗎？還是僅限 Web？」

**If Density is unclear:**
> 「你希望介面感覺『資訊密集但強大』還是『寬鬆但從容』？」

After collecting answers, fill the remaining `[MISSING]` placeholders and proceed to generation.
