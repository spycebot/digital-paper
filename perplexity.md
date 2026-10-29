Prompt:
I want to formalise my **digital-paper** design language system (DLS). When writing up a design vocabulary (or whatever professional designers call it), what things should I be writing about? What are the required document headings, and suggested topics to address?


Response:
For a **digital-paper design language system (DLS)**, formalise it as a layered documentation system: principles and vocabulary first, then foundations/tokens, components, patterns, content, accessibility, and governance. Professional designers usually call this a **design system documentation** or **design language specification**; the “vocabulary” is one section within it—your shared names for visual elements, states, and concepts. [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/)

## Recommended document structure

| Heading | What to write | Why it matters |
|---|---|---|
| **1. Overview** | Purpose, scope, intended users, products/platforms covered, version, status, and a short “how to use this document” guide. | Establishes the system as a single source of truth.  [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/) |
| **2. Design principles** | 4–8 decision-making rules, e.g. “paper feels calm,” “ink hierarchy before decoration,” “one focal action per page.” | Explains the *why* behind visual and interaction choices.  [aem](https://aem.design/manual/dls/) |
| **3. Brand & experience vision** | Brand attributes, emotional qualities, audience, product personality, and the intended “digital paper” experience. | Connects the DLS to brand and product strategy.  [aem](https://aem.design/manual/dls/) |
| **4. Design vocabulary** | Canonical names and definitions: page, sheet, canvas, margin, note, annotation, layer, ink, highlight, folio, spread, etc. Include synonyms to avoid and preferred terms. | Prevents teams from using inconsistent names for the same concept.  [uxpin](https://www.uxpin.com/studio/blog/design-system-documentation-guide/) |
| **5. Foundations** | Color/ink, typography, spacing, grid/layout, elevation, borders, radii, iconography, imagery, texture, and motion. | Defines the reusable visual building blocks.  [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/) |
| **6. Design tokens** | Named values for color, type, space, radius, shadow, motion duration, z-index, etc.; include semantic names and usage intent. | Makes design decisions reusable and implementable across tools and code.  [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/) |
| **7. Components** | Each reusable UI element: purpose, anatomy, variants, states, content rules, accessibility, tokens, code/design references, and do/don’t examples. | Helps someone correctly use an element in under a minute.  [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/) |
| **8. Patterns** | Multi-component solutions: reading view, note-taking, annotation, search, export, onboarding, empty states, errors, and settings. | Shows how components combine for recurring product tasks.  [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/) |
| **9. Content & voice** | Voice, tone, terminology, microcopy, error messages, empty states, alt text, and localization rules. | Ensures written language matches the visual language.  [uxpin](https://www.uxpin.com/studio/blog/design-system-documentation-guide/) |
| **10. Accessibility** | Contrast, focus, keyboard operation, screen-reader semantics, reduced motion, touch targets, and inclusive language. | Makes accessibility a system requirement rather than a late fix.  [uxpin](https://www.uxpin.com/studio/blog/creating-context-design-systems-comprehensive-approach-documentation/) |
| **11. Platform & responsive rules** | Rules for desktop, tablet, mobile, print/PDF export, dark mode, RTL languages, and input methods such as stylus, touch, keyboard, and mouse. | Digital-paper products often vary substantially by device and input.  [uxpin](https://www.uxpin.com/studio/blog/creating-context-design-systems-comprehensive-approach-documentation/) |
| **12. Governance** | How to propose, review, approve, version, deprecate, and release changes; ownership and contribution workflow. | Keeps the system coherent as it grows.  [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/) |
| **13. Getting started** | Separate quick-start paths for designers, engineers, writers, and researchers; include setup, tools, and first examples. | Reduces onboarding friction.  [aem](https://aem.design/manual/dls/) |
| **14. Changelog & roadmap** | Version history, known gaps, upcoming changes, deprecated items, and migration notes. | Communicates system maturity and change over time.  [thedesignsystem](https://thedesignsystem.guide/documentation) |

## What “design vocabulary” should contain

Your vocabulary section should be more than a glossary. Include:

- **Canonical terms:** the approved name for every concept, such as `sheet`, `canvas`, `note`, `annotation`, `ink layer`, `margin`, and `reading mode`.
- **Definitions:** one clear sentence for each term, plus a visual example where useful.
- **Preferred and forbidden synonyms:** for example, choose `sheet` over “page,” “document,” or “canvas” if `sheet` is the system term.
- **Naming conventions:** token naming, component naming, file naming, state naming, and event naming.
- **Concept map:** how terms relate—e.g. a `document` contains `sheets`; a `sheet` contains `ink layers`, `annotations`, and `media`.
- **Terminology for states:** default, hover, active, focus, selected, disabled, loading, error, empty, and read-only. [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/)
- **Terminology for roles:** author, reader, collaborator, reviewer, viewer, owner—especially important if permissions affect the interface.

## Required headings for each component

For every component—such as a note card, toolbar, page navigator, annotation pin, or ink brush—use the same template:

1. **Name**
2. **Purpose**
3. **When to use / when not to use**
4. **Anatomy**
5. **Variants**
6. **States**
7. **Content rules**
8. **Accessibility**
9. **Design tokens**
10. **Interaction and motion**
11. **Responsive/platform behavior**
12. **Do and don’t**
13. **Code or design-tool reference**
14. **Related components and patterns** [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/)

## Digital-paper-specific topics

Because your product is digital paper rather than a conventional app, add explicit guidance for:

- **Paper metaphor:** how literally the interface should imitate physical paper; where realism helps and where it becomes noise.
- **Canvas model:** infinite canvas versus fixed sheets; scrolling, zooming, panning, and page boundaries.
- **Ink and input:** pen, highlighter, eraser, pressure sensitivity, palm rejection, lasso selection, and stylus versus finger behavior.
- **Layering:** background paper, content, annotations, collaboration cursors, and UI overlays.
- **Reading ergonomics:** line length, margins, type scale, contrast, and low-glare or dark-paper modes.
- **Persistence and export:** autosave, version history, PDF export, print fidelity, and offline behavior.
- **Collaboration:** presence, cursors, comments, annotations, conflict handling, and permissions.
- **Motion restraint:** subtle transitions for page turns, tool changes, and overlays; respect reduced-motion preferences. [aem](https://aem.design/manual/dls/)

## Practical minimum viable version

If you want to start formalising immediately, create these seven documents first:

1. `00-overview.md`
2. `01-principles.md`
3. `02-vocabulary.md`
4. `03-foundations-and-tokens.md`
5. `04-components.md`
6. `05-patterns.md`
7. `06-accessibility-and-governance.md`

A strong rule: every visual decision should be traceable to a **principle**, expressed as a **token or component**, and explained with **usage guidance**. That structure turns a mood board or visual style into a maintainable design language system. [storybook.js](https://storybook.js.org/blog/how-to-document-your-design-system-best-practices-tools/)


Follow-up prompt:
Examples of design tokens for a paper aesthetic


Follow-up response:
Here are practical **paper-aesthetic design tokens** you can adapt directly into your DLS. The key idea is to avoid pure black/white and cool grays: use warm “paper” surfaces, warm “ink” text, hairline rules, restrained shadows, and low-opacity grain. [github](https://github.com/nexu-io/open-design/blob/main/design-systems/paper/DESIGN.md)

## Core color tokens

Use **primitive tokens** for raw values, then **semantic tokens** for roles such as surface, text, border, and accent. This lets you later add dark “ink” or “night reading” themes without changing component code. [paper](https://paper.design/docs/tokens)

### Primitive palette

| Token | Value | Use |
|---|---:|---|
| `paper.50` | `#FDFBF6` | Brightest paper surface |
| `paper.100` | `#F7F2E7` | Default warm paper canvas |
| `paper.200` | `#EFE7D6` | Secondary surface / subtle wells |
| `paper.300` | `#E3D8C2` | Cards on cards, recessed panels |
| `ink.900` | `#1B1915` | Primary warm-black ink |
| `ink.700` | `#3E3A33` | Strong secondary text |
| `ink.500` | `#6B6355` | Muted text, captions |
| `ink.300` | `#A79C89` | Disabled text, faint metadata |
| `rule.200` | `#D9CFBB` | Hairline rules and dividers |
| `accent.sienna` | `#A4501F` | Selection, links, key actions |
| `accent.moss` | `#5F6F4A` | Success / confirmation |
| `accent.ochre` | `#B7791F` | Warning |
| `accent.brick` | `#A63A2E` | Error / destructive |

These values follow the common paper-system pattern of cream/ivory backgrounds, warm-black text, cream-tinted borders, and one restrained accent. [github](https://github.com/NylasDev/hermes-mythic-design)

### Semantic tokens

| Semantic token | Maps to | Purpose |
|---|---|---|
| `surface.page` | `paper.100` | Main reading/document background |
| `surface.sheet` | `paper.50` | A sheet, card, modal, or elevated panel |
| `surface.well` | `paper.300` | Input fields, code blocks, empty trays |
| `text.primary` | `ink.900` | Body copy and headings |
| `text.secondary` | `ink.700` | Supporting copy |
| `text.muted` | `ink.500` | Metadata, timestamps, placeholders |
| `border.subtle` | `rule.200` | Hairlines, table rules, dividers |
| `border.strong` | `ink.700` | Emphasized outlines or selected edges |
| `interactive.default` | `accent.sienna` | Links, selected tools, primary actions |
| `interactive.hover` | `#8A3F17` | Hover state for interactive ink |
| `status.success` | `accent.moss` | Saved, synced, completed |
| `status.warning` | `accent.ochre` | Unsaved changes, sync issues |
| `status.danger` | `accent.brick` | Deletion, errors, destructive actions |

A useful rule: **paper is the background, ink is the content, and accent ink is scarce.** Paper-inspired systems commonly reserve a single accent color for interaction and emphasis. [github](https://github.com/NylasDev/hermes-mythic-design)

## Typography tokens

For a digital-paper feel, pair a readable serif for reading content with a quiet sans for UI, plus a mono face for metadata or technical labels. [github](https://github.com/nexu-io/open-design/blob/main/design-systems/paper/DESIGN.md)

| Token | Example value | Use |
|---|---|---|
| `font.family.reading` | `"Source Serif 4", Georgia, serif` | Long-form document text |
| `font.family.display` | `"Playfair Display", Georgia, serif` | Titles, section headers |
| `font.family.ui` | `"Inter", system-ui, sans-serif` | Buttons, menus, labels |
| `font.family.mono` | `"IBM Plex Mono", ui-monospace, monospace` | Metadata, coordinates, code |
| `font.size.display.xl` | `40px / 2.5rem` | Document title |
| `font.size.heading.lg` | `28px / 1.75rem` | Section heading |
| `font.size.heading.md` | `22px / 1.375rem` | Subheading |
| `font.size.body.lg` | `18px / 1.125rem` | Comfortable reading text |
| `font.size.body.md` | `16px / 1rem` | Default UI and body text |
| `font.size.caption` | `13px / 0.8125rem` | Footnotes, metadata |
| `font.lineHeight.reading` | `1.6` | Long-form reading |
| `font.lineHeight.ui` | `1.35` | UI labels and controls |
| `font.weight.reading` | `400` | Body ink |
| `font.weight.emphasis` | `600` | Headings and selected labels |

Keep body leading generous—around `1.55` to `1.65`—because it reinforces the calm, printed-page reading experience. [open-design](https://open-design.ai/plugins/design-system-atelier-zero/)

## Spacing and layout tokens

Use a consistent base unit, then derive larger spacing values from it. Paper layouts benefit from generous margins, clear column rhythm, and hairline rules rather than heavy boxes. [github](https://github.com/nexu-io/open-design/blob/main/design-systems/paper/DESIGN.md)

| Token | Value | Use |
|---|---:|---|
| `space.unit` | `4px` | Base spacing unit |
| `space.1` | `4px` | Icon-to-label gap |
| `space.2` | `8px` | Tight component padding |
| `space.3` | `12px` | Default control padding |
| `space.4` | `16px` | Card padding |
| `space.6` | `24px` | Section spacing |
| `space.8` | `32px` | Block spacing |
| `space.12` | `48px` | Major section separation |
| `space.page.margin` | `clamp(24px, 5vw, 80px)` | Outer document margin |
| `space.reading.measure` | `65ch` | Maximum comfortable text width |
| `radius.none` | `0px` | Print-like cards, sheets, buttons |
| `radius.subtle` | `2px` | Optional softened controls |
| `radius.pill` | `999px` | Tags, chips, avatars |

For a more editorial or letterpress feel, favor `radius.none` or `radius.subtle`; for a friendlier notebook feel, use slightly larger radii. [github](https://github.com/NylasDev/hermes-mythic-design)

## Elevation and shadow tokens

Paper usually reads best with **flat layers, hairline borders, and very soft shadows** rather than glossy material elevation. [github](https://github.com/NylasDev/hermes-mythic-design)

| Token | Value | Use |
|---|---|---|
| `elevation.flat` | `none` | Inline content on the page |
| `elevation.sheet` | `0 0 0 1px var(--border-subtle)` | Card defined by a hairline rule |
| `elevation.raised` | `0 1px 2px rgba(27, 25, 21, 0.06)` | Menus, tooltips |
| `elevation.floating` | `0 8px 24px rgba(27, 25, 21, 0.10)` | Modals, popovers, dragged sheets |
| `elevation.press` | `0 2px 0 rgba(27, 25, 21, 0.18)` | Optional letterpress button effect |
| `border.width.hairline` | `1px` | Rules, dividers, outlines |
| `border.width.emphasis` | `2px` | Focus rings and selected states |

## Texture tokens

Texture should be a controlled overlay, not a busy background image. Implement grain as a low-opacity procedural noise layer or SVG turbulence filter, and ensure it never reduces text contrast. [typeui](https://www.typeui.sh/design-skills/riso)

| Token | Example value | Use |
|---|---|---|
| `texture.paper.grain` | `url("paper-grain.svg")` | Global paper surface texture |
| `texture.paper.opacity` | `0.04` | Default grain strength |
| `texture.paper.opacity.strong` | `0.07` | Hero, cover, or decorative areas |
| `texture.paper.blend` | `multiply` | How grain interacts with surface color |
| `texture.rule.style` | `solid` | Horizontal ruled-paper lines |
| `texture.rule.gap` | `28px` | Ruled-paper line spacing |
| `texture.grid.dot` | `1px` | Dot-grid notebook background |
| `texture.grid.gap` | `24px` | Dot-grid spacing |
| `texture.noise.enabled` | `true` | Global toggle for accessibility/performance |

## Motion tokens

Keep motion subtle and tactile: quick feedback for controls, slightly slower transitions for sheets and overlays. [brainy](https://brainy.ink/paper/design-tokens/ja)

| Token | Value | Use |
|---|---:|---|
| `motion.duration.instant` | `80ms` | Ink feedback, hover |
| `motion.duration.fast` | `150ms` | Buttons, menus, selection |
| `motion.duration.base` | `240ms` | Panels, sheets, drawers |
| `motion.duration.slow` | `360ms` | Page transitions, modal entrance |
| `motion.easing.standard` | `cubic-bezier(0.2, 0, 0, 1)` | General transitions |
| `motion.easing.paper` | `cubic-bezier(0.22, 0.61, 0.36, 1)` | Sheet reveal, page turn |
| `motion.distance.pageTurn` | `24px` | Subtle page-turn travel |

## Example token block

```css
:root {
  /* Paper surfaces */
  --paper-50: #FDFBF6;
  --paper-100: #F7F2E7;
  --paper-200: #EFE7D6;
  --paper-300: #E3D8C2;

  /* Ink */
  --ink-900: #1B1915;
  --ink-700: #3E3A33;
  --ink-500: #6B6355;
  --rule-200: #D9CFBB;

  /* Accents */
  --accent-sienna: #A4501F;
  --accent-moss: #5F6F4A;
  --accent-brick: #A63A2E;

  /* Semantic roles */
  --surface-page: var(--paper-100);
  --surface-sheet: var(--paper-50);
  --text-primary: var(--ink-900);
  --text-muted: var(--ink-500);
  --border-subtle: var(--rule-200);
  --interactive-default: var(--accent-sienna);

  /* Typography */
  --font-reading: "Source Serif 4", Georgia, serif;
  --font-ui: "Inter", system-ui, sans-serif;
  --font-mono: "IBM Plex Mono", ui-monospace, monospace;
  --text-body: 1rem;
  --leading-reading: 1.6;

  /* Texture and elevation */
  --texture-paper-opacity: 0.04;
  --elevation-sheet: 0 0 0 1px var(--border-subtle);
  --elevation-floating: 0 8px 24px rgba(27, 25, 21, 0.10);

  /* Motion */
  --motion-fast: 150ms;
  --motion-base: 240ms;
  --easing-paper: cubic-bezier(0.22, 0.61, 0.36, 1);
}
```

## Documentation fields per token

For each token in your DLS, record:

- **Name:** e.g. `surface.sheet`
- **Category:** color, typography, spacing, elevation, texture, or motion
- **Value:** e.g. `#FDFBF6`
- **Intent:** “elevated sheet or card on the paper canvas”
- **Allowed uses:** cards, modals, floating toolbars
- **Forbidden uses:** page background, body text color
- **Theme variants:** light paper, aged paper, dark ink mode
- **Accessibility note:** contrast ratio, focus visibility, reduced-texture behavior
- **Platform mapping:** CSS variable, Figma variable, iOS/Android equivalent [paper](https://paper.design/docs/tokens)

A good starting principle for your DLS: **no pure white, no pure black, no cool gray, and no more than one dominant accent.** That constraint alone will make most interfaces feel more like paper. [github](https://github.com/NylasDev/hermes-mythic-design)