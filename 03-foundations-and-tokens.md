# digital-paper Foundations and Tokens

Created 29 OCT 2026

Updated 06 NOV 2026

This document will contain canonical foundations and tokens for the **digital-paper** Design Language System.

## Colour and Ink

The primary colour couices are contained in the following "Neutrals" and "Accents"


**Neutrals**:
Dark: `#141413` for primary text and dark backgrounds; 

Light: `#faf9f5` for light backgrounds and text on dark;

Mid Gray: `#b0aea5` for secondary elements; 

Light Gray: `#e8e6dc` for subtle backgrounds

Please render the abover colours.


For additional, content rich applications, the following colour tokens can be used.

| Token         | Value   | Use                              |
| ------------- | ------- | -------------------------------- |
| paper.50      | #FDFBF6 | Brightest paper surface          |
| paper.100     | #F7F2E7 | Default warm paper canvas        |
| paper.200     | #EFE7D6 | Secondary surface / subtle wells |
| paper.300     | #E3D8C2 | Cards on cards, recessed panels  |
| ink.900       | #1B1915 | Primary warm-black ink           |
| ink.700       | #3E3A33 | Strong secondary text            |
| ink.500       | #6B6355 | Muted text, captions             |
| ink.300       | #A79C89 | Disabled text, faint metadata    |
| rule.200      | #D9CFBB | Hairline rules and dividers      |
| accent.sienna | #A4501F | Selection, links, key actions    |
| accent.moss   | #5F6F4A | Success / confirmation           |
| accent.ochre  | #B7791F | Warning                          |
| accent.brick  | #A63A2E | Error / destructive              |


Therefore the following **semantic tokens** apply.

| Semantic token      | Maps to       | Purpose                                 |
| ------------------- | ------------- | --------------------------------------- |
| surface.page        | paper.100     | Main reading/document background        |
| surface.sheet       | paper.50      | A sheet, card, modal, or elevated panel |
| surface.well        | paper.300     | Input fields, code blocks, empty trays  |
| text.primary        | ink.900       | Body copy and headings                  |
| text.secondary      | ink.700       | Supporting copy                         |
| text.muted          | ink.500       | Metadata, timestamps, placeholders      |
| border.subtle       | rule.200      | Hairlines, table rules, dividers        |
| border.strong       | ink.700       | Emphasized outlines or selected edges   |
| interactive.default | accent.sienna | Links, selected tools, primary actions  |
| interactive.hover   | #8A3F17       | Hover state for interactive ink         |
| status.success      | accent.moss   | Saved, synced, completed                |
| status.warning      | accent.ochre  | Unsaved changes, sync issues            |
| status.danger       | accent.brick  | Deletion, errors, destructive actions   |


**Accents**: 
Red: `#B5332A` (vermillion-brick)

Blue: `#6a9bcc` as the secondary accent 

Green: `#788c5d` as the tertiary accent

### Typography

  {
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400..900&family=Outfit:wght@100..900&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Rubik+Dirt&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Rubik+Dirt&family=Special+Elite&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');
  
  :css:root {
    /* Core Google Font Pairings */
    --sw-font-display:   'Orbitron', sans-serif; /* Editorial headings */
    --sw-font-heading:   'Special Elite', sans-serif;  /* Clean web/print headers */
    --sw-font-body:      'Faustina', serif;        /* Highly legible body layer */
    --sw-font-mono:      'JetBrains Mono', monospace;/* Technical data & code */
  
    /* Structural & Functional Assignments */
    --sw-font-interface:  var(--sw-font-body);
    --sw-font-meta:       var(--sw-font-body);
    --sw-font-caption:    var(--sw-font-body);
    --sw-font-print-edge: var(--sw-font-interface);
    --sw-font-quote:      var(--sw-font-display);
    --sw-font-accent:     var(--sw-font-heading);
    --sw-font-legal:      var(--sw-font-body);
  }

### Spacing


### Grid and layout


### Elevation


### Borders


### Radii


### Iconography


### Imagery


### Texture


### Motion.
