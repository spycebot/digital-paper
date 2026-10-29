# digital-paper — Design Language System

Oct 28, 2026 · @Shannon Ware · Draft 0.1

## 1. Purpose and scope

digital-paper is a design language for rendering technical and didactic content as if it were printed, typed or plotted onto paper by computing machinery of roughly 1940–1995, while remaining a screen medium that can animate.

**In scope**

- Didactic plates explaining statistical and machine-learning concepts (e.g. Figures 4.3–4.7: threshold sweeps, ROC curves, confusion matrices, k-fold rotation)
- Code listings, manual pages and photographic plates
- Still and animated social output, by default 1080 × 1350 px (4:5) at 25 fps
- Web surfaces styled through the `--sw-font-*` and related CSS tokens

**Out of scope (for now)**

- Faithful facsimile or forgery of real publications, logos or trade dress
- Interactive application UI beyond static or lightly animated pages
- Colour printing processes other than a single spot accent (see open questions)

## 2. Design philosophy and principles

The language rests on a three-step argument:

1. **Old computer manuals are cool.** Their authority comes from plain typography, numbered structure and diagrams that explain machines rather than sell them.
2. **Circuits drawn on paper actually work.** Copper tape and graphite pencil make functional circuits, so paper is not only a record of a machine; it can be part of one.
3. **Ink can behave like pixels.** If marks on paper may conduct, they may also update: dots can be added, removed and animated as on a screen.

From this argument follow five working principles.

1. **Plausible marks.** Every mark must be one a named marking engine could make: a pin strike, a toner dot, a typebar impression or a pencil line. Effects with no physical cause (gradients, drop shadows, glows, anti-aliased vectors at device scale) are excluded.
2. **Paper is a substrate, not a texture.** Paper has stock, age, fibre and damage; it is modelled, not overlaid as a photograph of grain.
3. **The page is a live circuit.** Motion is expressed as printing, erasure and re-striking on the page: a raster band descending, a threshold rule sweeping, a readout re-typed. The page never scrolls, zooms or fades like a screen.
4. **Explanation before nostalgia.** Period character is permitted only where it leaves the figure readable and correct. A defect that obscures data is removed.
5. **Numbered authority.** Content is organised as a manual: sections, figures, plates, listings and folios, each numbered and cross-referenced.

**Anachronism policy.** Mixing eras is allowed within one page only when each element is consistent with a single plausible document history, for example a 1980s laser page annotated in pencil. A laser-printed plate set in a 2020s geometric typeface is a deliberate liberty and must be recorded as such (see Section 5).

## 3. Visual references

Three references define the register: the typed engineering handbook, the corporate hardware manual, and the printed technical article.

| Reference | Period and engine | What digital-paper takes from it |
| --- | --- | --- |
| `user-manual-z.jpg` — ETH Zürich, *Bedienungsanweisung Z4* | c. 1950; typewriter on cream stock | Monospaced typed body; rules of `=` and `*` under headings; box-and-arrow block diagrams typed or ruled by hand; `§` numbering; bound edge visible at the margin |
| `vt382-thai-display-terminal-manual-cover.png` — Digital VT382 manual cover | c. 1990; offset print | Generous negative space; right-aligned geometric sans title stack; document number top right (`EK-…`); line-art hardware illustration; manufacturer mark bottom right |
| `Defence-forces-mag-article-Comp-in-O-june-1987_001.jpg` — *An Cosantóir*, June 1987 | 1987; phototypeset magazine | Heavy display headline across the full measure; three justified columns; bold run-in section heads; lettered and numbered lists; halftone-free line drawing set into the columns; folio and masthead at the foot |

**Shared traits to preserve:** warm, slightly yellowed stock; black as the only ink; structure carried by numbering and rules rather than colour; illustrations drawn as line work rather than photographs.

The reference images should be attached to this section when the document is next edited, so that each trait can be shown beside its source.

## 4. Media model: substrates and marking engines

Every page declares one substrate and one primary marking engine; secondary engines (e.g. pencil annotation) are optional.

### 4.1 Substrates

| Token | Base RGB | Character | Used in |
| --- | --- | --- | --- |
| `paper.fanfold` | 236, 229, 210 | Tractor-feed holes every 48 px, dotted perforation, vignette, 14 foxing spots | `dotmatrix.py` |
| `paper.bond` | 243, 241, 234 | Near-white, faint cloud and fibre | `laser_photo.py` (plain) |
| `paper.aged` | 234, 224, 200 | Browned margins, vignette, 18 foxing spots, one horizontal fold at 47 % height | `laser_listing.py` |
| `paper.ruled` | scanned stock | Pale blue feint rules; supplied as an image | laser plates via `PAPER` argument |
| `paper.typed` (proposed) | cream | Bound edge, typewriter stock as in the Z4 manual | not yet built |

### 4.2 Marking engines

| Engine | Resolution and screen | Signature defects | Reference script |
| --- | --- | --- | --- |
| Dot-matrix, 9-pin | Pin pitch 5 × 6 px; Floyd–Steinberg dither | Per-pass ribbon density, pass misregistration (σ 0.6 px), pin jitter (σ 0.25 px), ink bleed | `dotmatrix.py` |
| Laser, 300 dpi | 53 lpi at 45°, Euclidean spot, about 33 grey levels | Dot gain, drum banding (periods H/7.3 and H/31), weak highlight dots dropping out (35–45 %), toner scatter near edges, low toner at one edge | `laser_photo.py`, `laser_listing.py` |
| Laser, plate variant | Supersampled ×2; 5.5 px dot screen and 7 px hatch | Toner halo scatter (0.6 % of edge pixels) | `laser_threshold.py`, `laser_roc.py`, etc. |
| Typewriter (proposed) | Fixed pitch | Uneven strike weight, ribbon fade, misaligned characters | not yet built |
| Pencil / copper tape (proposed) | Vector, hand-drawn | Graphite sheen, tape edges, solder blobs | not yet built |

### 4.3 Fidelity rules

- Device pixels are binary: each is toner or paper, ink or not. Tone is made only by screening, dithering or hatching.
- Type on laser pages is rasterised without anti-aliasing at device resolution; smoothing comes only from the toner model.
- Ink and toner are never pure black: toner is RGB 22, 21, 24 (plates) or 20, 19, 22 (photos) at 0.95–0.96 coverage.
- Defects are seeded (`default_rng(<year>)`) so every render is reproducible.

## 5. Foundations

Foundations are expressed as named tokens with the `--sw-` prefix, so that web pages and Python renderers share one vocabulary.

### 5.1 Typography

| Token | Family | Role | Period fit | Notes |
| --- | --- | --- | --- | --- |
| `--sw-font-display` | Orbitron (400–900) | Display, plate titles, pull quotes | Liberty: a 2009 geometric face evoking terminal-era futurism | Wide and capital-led; use at 24 px and above, short strings only |
| `--sw-font-heading` | Rubik Dirt | Section heads, accents | Liberty: a pre-distressed face | Already carries texture, so do not pass it through a marking engine as well |
| `--sw-font-body` | Special Elite | Body, captions, meta, legal, interface | Strong: matches the typed Z4 manual | Single weight, no italic; uneven by design, so keep passages short |
| `--sw-font-mono` | JetBrains Mono (100–800, italic) | Code, readouts, data | Liberty: modern programming face | Carries the monochrome syntax convention: bold keywords, italic strings |
| (unassigned) | Outfit (100–900) | Imported but not yet used | Close to the VT382 cover sans | Candidate for small UI text and dense captions |

The supplied stylesheet, with syntax corrected and assignments unchanged:

```css
@import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400..900&family=Outfit:wght@100..900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Rubik+Dirt&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Special+Elite&display=swap');
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:ital,wght@0,100..800;1,100..800&display=swap');

:root {
  /* Core families */
  --sw-font-display: 'Orbitron', sans-serif;      /* Display titles and quotes */
  --sw-font-heading: 'Rubik Dirt', sans-serif;    /* Distressed section heads */
  --sw-font-body:    'Special Elite', serif;      /* Typewriter body layer */
  --sw-font-mono:    'JetBrains Mono', monospace; /* Code and data */
  /* --sw-font-ui:   'Outfit', sans-serif;  imported; not yet assigned */

  /* Functional assignments */
  --sw-font-interface:  var(--sw-font-body);
  --sw-font-meta:       var(--sw-font-body);
  --sw-font-caption:    var(--sw-font-body);
  --sw-font-print-edge: var(--sw-font-interface);
  --sw-font-quote:      var(--sw-font-display);
  --sw-font-accent:     var(--sw-font-heading);
  --sw-font-legal:      var(--sw-font-body);
}
```

Corrections made: `:css:root` became `:root`; the closing brace was added; the comments on Rubik Dirt and Special Elite were reworded, since neither face is "clean" or "highly legible" in the usual sense.

### 5.2 Colour

| Token | Value | Use |
| --- | --- | --- |
| `--sw-ink-toner` | #161518 (22, 21, 24) | All laser marks |
| `--sw-ink-ribbon` | #222126 (34, 33, 38) | Dot-matrix strikes |
| `--sw-paper-fanfold` | #ECE5D2 | Fanfold substrate |
| `--sw-paper-bond` | #F3F1EA | Bond substrate |
| `--sw-paper-aged` | #EAE0C8 | Aged substrate |
| `--sw-rule-perforation` | #C4BCAA | Perforations and faint furniture |

No other colours appear in print. A single spot accent (for instance copper for paper-circuit traces) is an open question.

### 5.3 Tone and pattern

Tone carries meaning, so each pattern has one semantic role.

| Token | Definition | Meaning |
| --- | --- | --- |
| `tone.dots` | 45° dot screen, 5.5 px period, 25–30 % cover | Gain, numerator, area of interest |
| `tone.dots-fine` | 4.5 px period, 18 % cover | Secondary area (e.g. AUC) |
| `tone.hatch` | 45° lines, 7–9 px period | Shortfall, remainder of denominator, held-out fold |
| `tone.tint` | 53 lpi screen, 7 % (cell) or 22 % (fill) | Backgrounds and neutral fills |

### 5.4 Grid and page furniture

- Canvas: 1080 × 1350 px (4:5); plates may use 1088 × 1372 when supersampled panels require it.
- Text block: left 95 px, right 985–993 px.
- Running head at y ≈ 70–92 px: section name in italic at left, folio at right, a 2 px rule beneath.
- Colophon at y ≈ 1250–1300 px: hairline rule, then `300 dpi · 53 lpi @ 45° · PostScript Level 2` at left and the folio at right.
- Folios are hyphenated with an en dash (`4–7`); supplementary plates take a letter suffix (`4–7a`).

## 6. Editorial conventions

All content is addressed as parts of one manual.

| Unit | Form | Example |
| --- | --- | --- |
| Section | `Section n · Title` in the running head | Section 4 · Model Calibration |
| Figure | `Figure n.m` + title in bold | Figure 4.4 Error rates and the ROC curve |
| Supplementary figure | Letter suffix | Figure 4.3a |
| Panel | `(a)`, `(b)` in bold italic | (b) Receiver operating characteristic |
| Listing | `Listing n.m` | Listing 4.1 |
| Plate (dot-matrix) | `FIG. n-m` in capitals | FIG. 4-3 |
| Notebook cell | `In [n]:` / `Out[n]:` in mono | In \[47\]: |

**Captions.** Captions are written in the present tense and in plain declarative sentences. The first sentence states what the figure shows; later sentences state what to notice. Four lines is the norm, five the maximum.

**Numbers.** Rates and scores are reported to three decimals in readouts and two in prose; thousands take a comma (1,410). Mathematical minus (−) and multiplication (×) signs are used, not hyphens or the letter x.

**Cross-reference.** A figure that serves as a baseline names the figure it is compared with (e.g. Figure 4.5 refers to J\* = 0.56 and AUC = 0.86 in Figure 4.4).

**Proofreading.** Titles are checked before render, since a typo in a rasterised plate cannot be corrected in place. The current title of Listing 4.1 reads *Tain the model and evaluate it* and should read *Train*.

## 7. Components

Each component is specified by its anatomy, permitted variants and one governing rule.

| Component | Anatomy | Variants | Rule |
| --- | --- | --- | --- |
| Axes frame | 1.6 px box, 7–8 px outward ticks, sans tick labels, italic serif axis titles, rotated y-title | Single panel; stacked (a)/(b) panels | Ticks outward only; no gridlines |
| Data line | 2.6 px solid; 2.2 px dashed (9 on, 6 off) for the second series | Solid, dashed, dotted chance line (3 on, 5 off) | Series are distinguished by stroke pattern, never colour |
| Marker | Open circle (positive / TPR), open square (negative / FPR), filled when "called positive" | Radius 5–7 px | Filled versus open always means predicted state |
| Threshold rule | Vertical dotted line (4 on, 4 off) sweeping with t | Extends into score strips | One per panel, synchronised across panels |
| Readout box | Ruled box, mono text, `name = value` lines aligned on `=` | 3–4 lines | Knocks out everything beneath it |
| Callout | Ruled or unruled box, bold sans head, small sans detail, 1.3 px leader, optional arrowhead | Boxed (key result), unboxed (side note) | Leader ends at the datum, never on text |
| Dimension bracket | Vertical line with end ticks, bold label (J, J\*) | Left or right label | Marks a difference that also appears in another panel |
| Best-so-far mark | Filled downward triangle above the point | — | Moves only when the maximum improves |
| Score strip | Ruled band beneath (a), one row per class | Sample of 18–46 marks per row | Marks use the marker rule above |
| Confusion matrix | 2 × 2 ruled grid, cell code (TP) bold, name small, count right-aligned mono; mark field 15 per row | Each mark = 10 cases | Numerator dotted, rest of denominator hatched |
| Code cell | `In [n]:` label, 7 % tint box, mono text | With or without output | Syntax by weight and slant only |
| Running head and colophon | See Section 5.4 | — | Present on every page |

A dot-matrix variant of each component is drawn at pin pitch: rules become rows of pin strikes, and text uses 5 × 7-style glyphs.

## 8. Motion

Motion depicts the page being printed and then operated, never a camera moving over it. At 25 fps, a standard plate runs for about 13–15 s.

1. **Print-in, 60 frames (2.4 s).** A raster band descends from top to bottom with a 6 px soft edge, revealing the static plate.
2. **Settle, 10–12 frames.** The finished page holds still.
3. **Operate, 160–200 frames.** The governing parameter (usually a threshold t) sweeps from 0 to 1 with cosine easing; lines, tints, markers and readouts update together.
4. **Annotate.** On completion, the result callouts are struck in.
5. **Hold, 90–110 frames.** The annotated page holds for reading.

**Build-up variant.** Tabular plates (e.g. Figure 4.3a) fill marks in a random order over about 70 frames, then strike formulas part by part. Each part is wiped in over 7 frames and held for 22 frames, and the last part of each formula for 34.

**Rules**

- Every frame must be a valid printed page: no cross-fades, scaling, blur or camera motion.
- Text is struck or wiped in by scan line, never typed letter by letter, unless the engine is a typewriter or teletype.
- Annotations appear only once the state they describe is reached.

## 9. Accessibility and legibility

Period defects may never cost the reader the content, so each rule below overrides the media model.

- **Feed-size test.** Every plate is checked at 360 px wide, roughly a phone feed. Text below 14 px at 1080 px width fails, as does a callout that cannot be read at that size.
- **Contrast.** After ageing, toner on paper must stay at or above 7:1 for body text and 4.5:1 for annotations. Foxing and browning are kept out of the text block.
- **Distressed faces.** Rubik Dirt and Orbitron are limited to headings of six words or fewer. Special Elite is limited to passages of about 60 words; longer copy needs a cleaner body face (see open questions).
- **Defect placement.** Banding, scatter and dropout are never allowed to break a digit, a minus sign or a decimal point.
- **Non-visual access.** Each published plate carries alt text stating the figure's finding with its key number. Animated output carries the same text in the post body.
- **Motion.** No flashing above 3 Hz. The final frame must stand alone as a complete still.

## 10. Implementation

The system is currently implemented as seven standalone Python scripts that share code by copying it; the first task is to consolidate them into one library.

| Script | Produces | Engine |
| --- | --- | --- |
| `dotmatrix.py` | Photographic plate on fanfold | Dot-matrix |
| `laser_photo.py` | Photographic plate | Laser 300 dpi |
| `laser_listing.py` | Code listing with schematic | Laser 300 dpi |
| `laser_threshold.py` | Figure 4.3 animation | Laser plate |
| `laser_metrics.py` | Figure 4.3a animation | Laser plate |
| `laser_roc.py` | Figure 4.4 animation | Laser plate |
| `laser_random.py`, `laser_ideal.py` | Figures 4.5 and 4.6 animations | Laser plate |

**Proposed package structure (`digitalpaper/`)**

- `tokens.py`: colours, screens, page geometry and font paths, mirrored from the CSS tokens
- `paper.py`: substrate generators (fanfold, bond, aged, typed)
- `engines/`: `laser.py` (screen, dot gain, banding, `tonerise`, `compose`), `dotmatrix.py` (dither, `strike`), `typewriter.py`
- `components.py`: axes, readout, callout, bracket, marker, score strip, matrix
- `motion.py`: print-in, sweep, wipe and hold timelines
- `export.py`: frame sequences to MP4 (H.264, `-preset veryfast`) and stills

**Fonts in the renderers.** The scripts currently use Liberation and DejaVu. To adopt the chosen families, download the TTF files of Orbitron, Rubik Dirt, Special Elite, JetBrains Mono and Outfit from Google Fonts into a `fonts/` folder and reference them only through `tokens.py`.

**Reproducibility.** Each render records its script version, seed and inputs in the file metadata.

## 11. Do and don't

| Do | Don't |
| --- | --- |
| Make tone with screens, dither or hatching | Use smooth gradients or transparency |
| Separate series by dash pattern and marker shape | Separate series by colour |
| Seed every random defect | Let a re-render change the defects |
| Keep defects out of digits and signs | Let banding or dropout break a number |
| Let one engine distress the type | Run Rubik Dirt through the laser or dot-matrix model as well |
| Number every figure and cross-reference its comparison | Publish an unnumbered or orphaned plate |
| Animate as printing and re-striking | Cross-fade, zoom, pan or blur |
| Draw illustrations as line work | Paste photographs without screening them |
| Evoke the references' registers | Reproduce a real manufacturer's logo, document number or trade dress |

Each row should gain a pair of example images, correct and incorrect, rendered from the reference scripts.

## 12. Governance and open questions

The system is versioned semantically: a new token or component is a minor version, and a change to an existing token's value or meaning is a major version. Changes are recorded in a changelog, newest first.

**Admission of a new engine or component** requires a reference script, a seeded example render, its token entries and a do-and-don't pair.

**Open questions**

- [ ] Should Outfit be assigned (e.g. as `--sw-font-ui` for dense captions), or removed from the import?
- [ ] Is Special Elite acceptable for long body copy, or should long passages fall back to a quieter face?
- [ ] Should quotes use Orbitron, whose wide capitals suit titles more than sentences?
- [ ] Is a single copper spot colour admitted for paper-circuit traces (principle 2)?
- [ ] How are copper tape and graphite rendered: as a new engine, or as an overlay on existing pages?
- [ ] Does the system extend to web pages as live, interactive "paper", and if so, which motion rules apply?
- [ ] Should the Z4 typewriter register become its own engine and substrate?
