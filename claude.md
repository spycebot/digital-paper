Prompt:
I want to formalise my **digital-paper** design language system (DLS). When writing up a design vocabulary (or whatever professional designers call it), what things should I be writing about? What are the required document headings, and suggested topics to address?


Response:
**Terminology:** professionals call the whole artefact a **design system** and its expressive core a **design language** or **visual language**. Your document sits between a **style guide**, which covers how things look, and a **specification**, which covers how they are produced. Because your system is generative and code-driven, it should be both.

Below is a conventional heading structure. Under each heading I suggest topics specific to the digital-paper idiom.

**1. Purpose and Scope**
- What the system is for (didactic ML plates, carousels, manual pages) and what it is not for
- Intended outputs and channels, e.g. 1080 × 1350 (4:5) stills and 25 fps animations

**2. Principles**
- Three to five governing tenets, such as "every mark is plausible for its machine" and "the artefact must still teach"
- A policy on anachronism: what period liberties are permitted, and why

**3. Media Model (Substrates and Marking Engines)**

This is the section unique to your system, and arguably its centre.
- *Substrates:* paper stocks such as fanfold, laser bond, aged and ruled paper, with base colours, fibre, foxing, browning and fold parameters
- *Engines:* dot-matrix (9-pin passes, ribbon density), 300 dpi laser (53 lpi at 45°, about 33 grey levels, dot gain, drum banding, toner scatter), and possibly typewriter or CRT
- *Fidelity rules:* binary device pixels, un-anti-aliased type at device resolution, and which defects are mandatory, optional or forbidden

**4. Foundations (Design Tokens)**
- *Colour:* toner and ink RGB values, paper bases, opacity (for example, 0.95 coverage)
- *Tone:* named halftone screens, hatch patterns and tint levels, with the semantic meaning of each (for example, dots for a numerator and hatching for the remainder)
- *Typography:* serif, sans and mono roles; sizes; bold for keywords and italic for strings in monochrome listings
- *Grid and page furniture:* margins, running heads, folios, rules and the colophon line

**5. Editorial Conventions**
- Section, figure, plate and listing numbering; caption voice and length
- Notebook cell framing (`In [n]:`), how equations are set, and how numbers are reported

**6. Components**
- Axes, legends, readout boxes, callouts with leaders, brackets, markers, score strips and confusion matrices
- For each component: its anatomy, permitted variants, and usage rules such as knock-out behaviour

**7. Motion**
- A canonical timeline (print-in raster wipe, pause, parameter sweep, annotated hold)
- Easing, frame counts and the rule for when annotations appear

**8. Accessibility and Legibility**
- Minimum contrast once paper ageing is applied, mobile legibility at feed size, and alt-text and caption obligations

**9. Implementation**
- Reference scripts, shared helpers to factor out (`tonerise`, `compose`, `dot_screen`), seeding for reproducibility, and supersampling factors
- A file and naming scheme, and the export pipeline

**10. Do's and Don'ts**
- Annotated correct and incorrect examples. This section usually does the most to keep a system consistent.

**11. Governance**
- Versioning, a changelog, how new engines or components are admitted, and who approves them

If it would help, I can draft this as a document seeded with the actual values from your scripts, which are already consistent enough to serve as the first token set.

-----

Follow-up prompt:
Yes, and please use the following fonts and visual references.

My inputs are as follows:
1. Design Philosophy
2. Visual Reference
3. Chosen Fonts


Design Philosophy
The logic of digital-paper flows as follows:
(1) Old computer manuals are cool
(2) There are circuits drawn on paper that actually work: functional paper circuits using copper tape and graphite pencil
(3) What if the ink on the page could  be manipulated like pixels on a screen


Visual References
1. user-manual-z.jpg
2. vt382-thai-display-terminal-manual-cover.png
3. Defence-forces-mag-article-Comp-in-O-june-1987_001.jpg



Chosen Fonts
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400..900&family=Outfit:wght@100..900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Rubik+Dirt&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Special+Elite&display=swap'); 
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');

:css:root {
  /* Core Google Font Pairings */
  --sw-font-display:   'Orbitron', sans-serif; /* Editorial headings */
  --sw-font-heading:   'Rubik Dirt', sans-serif;  /* Clean web/print headers */
  --sw-font-body:      'Special Elite', serif;        /* Highly legible body layer */
  --sw-font-mono:      'JetBrains Mono', monospace;/* Technical data & code */

  /* Structural & Functional Assignments */
  --sw-font-interface:  var(--sw-font-body);
  --sw-font-meta:       var(--sw-font-body);
  --sw-font-caption:    var(--sw-font-body);
  --sw-font-print-edge: var(--sw-font-interface);
  --sw-font-quote:      var(--sw-font-display);
  --sw-font-accent:     var(--sw-font-heading);
  --sw-font-legal:      var(--sw-font-body);


  Follow-up response:
  I'll draft the design-language document now, seeding it with your philosophy, references, fonts and the values already set in your scripts.

Outline up; now writing the purpose and philosophy sections.

Now the philosophy and principles.

Next, the media model drawn from your rendering scripts.

Now the foundations, including your font tokens.

Editorial conventions next.

Components next.

I've drafted [digital-paper — Design Language System](https://claude.ai/artifact/JVzS7YZXwp1i1r9onLvMch). Read it over, edit inline, or comment and I'll revise.

Your stylesheet had a few problems, which I've corrected in the document:
- **Syntax:** `:css:root` is not a valid selector, so it should be `:root`. The block was also missing its closing brace.
- **Unused font:** Outfit is imported but never assigned to a token.
- **Comments:** I reworded two, since Rubik Dirt is a distressed face rather than "clean", and Special Elite is a typewriter face rather than "highly legible".

I couldn't attach your reference images because the files aren't available to me. I've described them in a table in Section 3 instead.