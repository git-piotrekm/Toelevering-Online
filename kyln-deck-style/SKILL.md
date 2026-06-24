---
name: kyln-deck-style
description: Style HTML slide decks with the Kyln visual system — Onest typeface, vivid indigo (#5b4ee6) accent, alternating white / soft-lavender / indigo / dark card variants, 24px rounded radii, pill components, keyboard-navigable single-file HTML. Use whenever the user asks for slides, a deck, a presentation, an HTML deck, or any slide-based visual content in this look. Triggers on Kyln, Onest, indigo decks, or requests for modern, editorial slides. Includes image patterns — full-bleed backgrounds, split layouts, hero-with-image-below, and showcase — supporting URLs and uploaded files inlined as base64. Ships the Kyln and Amsterdam Standard logos as monochrome SVGs (assets/logos.html) for title, chrome, and closing slides. Provides the full visual system plus a base template demonstrating every pattern. Use proactively for any deck request unless the user specifies a different aesthetic.
---

# Kyln Deck Style

A purely visual skill. It does not care what's on the slides — it cares that they look right.

The skill produces single-file HTML presentations with a consistent visual language: Onest typeface, vivid indigo accent, four background variants in rotation, pill components, large rounded cards, and image patterns that fit the system. Apply it to any deck content: pitch, status update, training, manifesto, recipe collection, anything.

## When to use

- Any HTML slide deck where the user wants this look
- Any time the user references Kyln, Onest, the indigo aesthetic, or "that style you used before"
- Default to this skill for "make me slides" / "build a deck" requests unless the user specifies otherwise

## How to use

1. **Fetch the extras file first** — before anything else, fetch `https://raw.githubusercontent.com/amsdard/tools-public-assets/main/kyln-deck-extras.md` and hold it in context. This is a required prerequisite for every build and edit session.
2. Read `assets/base.html` to see every layout pattern rendered together.
3. Copy `assets/base.html` to the working directory as the starting scaffold.
4. Keep the entire `<style>` block intact.
5. Replace slide content with the user's content, picking layout patterns from the base file as needed.
6. Update the slide count in `chrome-num` elements and the `data-slide` attributes.
7. For image patterns, see the dedicated section below.
8. To brand a slide, copy a logo SVG from `assets/logos.html` — see the Logos section below.
9. Save and deliver as a single self-contained HTML file.

Do not modify the CSS variables, fonts, or component class names. The look depends on these being consistent.

## Extras

An additional, frequently-updated reference lives at:
https://raw.githubusercontent.com/amsdard/tools-public-assets/main/kyln-deck-extras.md

The full public assets repo (browse for additional images, files, or future extras):
https://github.com/amsdard/tools-public-assets

**Always fetch the extras at the start of every build or edit session** — treat it as a prerequisite, not an optional lookup. When editing an existing deck, check the extras first; fall back to this SKILL.md only if the extras don't cover the requested pattern or component.

Apply any relevant instructions, patterns, or overrides it contains — treating it as an extension of this skill. If the fetch fails or the file has nothing relevant, fall back to this SKILL.md and tell the user the extras didn't cover it.

Instructions in the extras file are additive; they do not override the hard visual rules (palette, fonts, radii, logo color) unless the user explicitly confirms.

## The palette

```css
--bg: #ffffff /* main slide background */ --bg-soft: #f1f1f7
  /* soft lavender — secondary slide background */ --bg-card: #ffffff
  --indigo: #5b4ee6 /* primary accent */ --indigo-dark: #4a3fd1
  --indigo-soft: #ede9fe /* tinted background for indigo pills */
  --indigo-glow: #8b85f0 /* lighter indigo for accents on dark cards */
  --ink: #1a1a2e /* near-black with cool undertone */ --ink-mute: #6b6987
  /* cool grey-purple for secondary text */ --ink-soft: #a4a3bd --rule: #e6e5ee
  --rule-strong: #d4d3e0 --dark-card: #1a1a2e;
```

## Typography

- **Onest** (Google Fonts, variable 100–900) — everything visible
- **JetBrains Mono** — chrome only (slide numbers, dates, technical labels)

Weight conventions:

- `font-weight: 700` — display headings (`.h-display`)
- `font-weight: 600` — sub-display, blockquotes (`.h-display-md`)
- `font-weight: 500` — pills, emphasis, lists
- `font-weight: 400` — body

Tight letter-spacing on big type (`-0.035em` on `.h-display`, `-0.025em` on `.h-display-md`, `-0.06em` on `.stat-num`).

## Four slide backgrounds (use them in rotation)

| Class        | Background           | When                                                    |
| ------------ | -------------------- | ------------------------------------------------------- |
| (default)    | `#ffffff`            | Primary content slides                                  |
| `.bg-soft`   | `#f1f1f7` lavender   | Secondary content slides, breaks up the rhythm          |
| `.bg-indigo` | `#5b4ee6` indigo     | One big statement, max once or twice per deck           |
| `.bg-dark`   | `#1a1a2e` near-black | Quote slides, closing slides, anywhere you want gravity |
| `.bg-image`  | image                | Full-bleed image background (see Image patterns below)  |

Alternating backgrounds give the deck visual rhythm. Don't put three white slides in a row.

## Four card variants

| Class            | Background          | Text  | When                                     |
| ---------------- | ------------------- | ----- | ---------------------------------------- |
| `.card`          | white, bordered     | dark  | Default card                             |
| `.card-soft`     | lavender, no border | dark  | Subtle differentiation                   |
| `.card-ind`      | indigo              | white | Emphasis, "the recommended one"          |
| `.card-dark`     | near-black          | white | Contrast, gravity                        |
| `.card-elevated` | white with shadow   | dark  | Hero cards (big stats, important tables) |

All cards use `border-radius: 24px` and `padding: 2rem`. Do not change this.

On grids with 3–4 cards, rotate through the variants (e.g. white → soft → indigo → dark). This is the deck's signature visual move.

## Pills (always fully rounded, always with a leading dot)

```html
<span class="pill pill-ind">Label</span>
<!-- indigo on lavender, primary -->
<span class="pill pill-ink">Label</span>
<!-- dark on lavender, neutral -->
<span class="pill pill-on-dark">Label</span>
<!-- white on translucent, for dark slides -->
<span class="pill pill-on-indigo">Label</span
><!-- white on translucent, for indigo slides -->
<span class="pill pill-ind pill-lg">Label</span
><!-- bigger pill, for pill-row visuals (Pattern 13) -->
```

Use pills as section labels at the top of slides, or as inline tags in headers. Each pill auto-renders a leading dot via `::before`. Don't add it manually. Add `.pill-lg` for larger pills used in tag-row visuals.

## Heading emphasis pattern

The signature move: bold heading with 1–2 words in indigo.

```html
<h2 class="h-display text-6xl">
  [Sentence with one] <span class="ind">[accent word]</span> [or two].
</h2>
```

Rules: never accent more than half the words in a heading. Never accent every heading on a slide. The indigo should feel earned.

## Strikethrough for "removed / dying / cancelled"

```html
<span class="strike">item</span>
```

Uses a 2px indigo line, slightly rotated (-1.5°). For dark/indigo backgrounds, use `.strike-on-dark` instead.

This replaces a red "warning" color. The deck's palette has no red. Use strikethrough for negation.

## Highlight a single key phrase

```html
... the real thing is <span class="hl">[key phrase]</span> ...
```

Renders a lavender-tinted underline behind the text. Use **once per deck**, on the single most important phrase. More than that and it loses meaning.

## Stat numerals (for big numbers)

```html
<div class="stat-num ind">75<span class="text-4xl">%+</span></div>
<div class="stat-sub mt-5">
  [Three-line caption<br />describing the<br />stat]
</div>
```

Combine with any card variant. The numeral itself can be indigo (`.ind`), white (default on dark/indigo cards), or `--indigo-glow` for dark cards.

## Quote treatment

```html
<div class="quote-mark">"</div>
<blockquote class="h-display-md text-4xl leading-tight">
  [The quote, with one phrase] <span class="hl">[highlighted]</span>.
</blockquote>
<p class="mono text-xs uppercase tracking-[0.15em] ink-mute">[Attribution]</p>
```

On dark slides, the `.quote-mark` shifts to `--indigo-glow`. On dark/indigo slides, swap `.hl` for an inline gradient with `rgba(139,133,240,0.4)` (see base.html for the exact pattern).

## Slide chrome (top of every slide)

```html
<div class="chrome-top">
  <div class="chrome-tag">
    <span class="chrome-tag-dot"></span> [Section label]
  </div>
  <div class="chrome-num">[NN] / [TOTAL]</div>
</div>
```

Tag on the left, slide number on the right. Auto-adjusts contrast for dark/indigo backgrounds via the `.slide.bg-dark` and `.slide.bg-indigo` cascades. The `.bg-image` slides need the same contrast treatment (use `pill-on-dark` and inline white styling for chrome).

## Layout patterns (see base.html for each)

Pick the pattern that fits the content, not the other way around. Each is demonstrated as one slide in `assets/base.html`.

| #      | Pattern                          | When                                                                        |
| ------ | -------------------------------- | --------------------------------------------------------------------------- |
| 1      | Title                            | Opening slide. Big heading, subtitle, accent words.                         |
| 2      | Single-statement                 | One big claim with rule-of-N structure.                                     |
| 3      | Two-column split                 | Compare two sides. Often `.card-soft` + `.card-ind`.                        |
| 4      | Three-column grid                | Audit-style. Mix three card variants.                                       |
| 5      | Four-card row                    | Funnel/process. Full white→soft→indigo→dark rotation.                       |
| 6      | Big stats grid                   | Three large numbers, one per card.                                          |
| 7      | Quote (dark)                     | Pull quote with attribution. Dark slide background.                         |
| 8      | Block + cards                    | Dark card with quote on one side, three small cards on the other.           |
| 9      | Indigo statement                 | Single big claim on full indigo background. Use sparingly.                  |
| 10     | 2×2 options                      | Four cards in a grid, one highlighted as `.card-ind`.                       |
| 11     | Pricing/data table               | Elevated card with header row and data rows.                                |
| 12     | Numbered closing (list)          | Dark slide with 3–4 numbered items, big indigo-glow numbers, list-style.    |
| **13** | **Pill row visual**              | **Heading + a row of large indigo pills as the visual element.**            |
| **14** | **Single-takeaway closing**      | **One big number, one heading, one subtitle. Use as a trilogy at the end.** |
| **15** | **Image A · Full-bleed**         | **Image fills the slide, text overlays via dark gradient.**                 |
| **16** | **Image B · Split**              | **Half text, half contained image (24px corners).**                         |
| **17** | **Image C · Hero + image below** | **Top section with text, bottom section with full-bleed image.**            |
| **18** | **Image D · Showcase**           | **One image, contained, centered with text alongside. Good for portraits.** |

### Variations of existing patterns (no new pattern needed)

These come up often but don't need their own slide — they're tighter forms of patterns above:

- **3-card flow.** Same as four-card row (Pattern 5) but with 3 cards. Rotate white → indigo → dark, skip the soft variant. Used for short sequences.
- **2-card pricing/feature compare.** Same as two-column split (Pattern 3) but with two cards (elevated + indigo) instead of two equal columns. Used when comparing two options/tiers.
- **Confession / context slide.** Same as single-statement (Pattern 2) but with a two-line headline (one ink, one indigo) and two short body paragraphs underneath. Used for vulnerable / honest moments ("we tried this, too early").
- **Numbered card grid 2×2.** Same as 2×2 options (Pattern 10) but with a leading number (`01`, `02`...) on each card in monospace. Used for "what you get" / "4 key benefits" slides.

## Numbered closing — two variants

Pattern 12 (the list form) puts all takeaways on one slide. Pattern 14 (single-takeaway) gives each takeaway its own slide.

**Use Pattern 12** when:

- Closing a short deck (under 10 slides)
- Items are short and read well as a list
- You want fewer total slides

**Use Pattern 14 (×3 in a row)** when:

- Closing a longer deck (15+ slides) where each takeaway deserves its own beat
- For impact in a spoken presentation — each click is a new beat
- The takeaways are the speech's main thesis

When using Pattern 14 as a trilogy, alternate backgrounds for rhythm:

```
20 · bg-dark
21 · bg-indigo  (callback to slide 6 or earlier indigo)
22 · bg-dark
```

Or all-dark for a uniform chant. Same layout pattern, different bg.

## Logos

Two brand logos ship with this skill in `assets/logos.html`: the **Kyln** logo (mark + wordmark) and the **Amsterdam Standard** wordmark. They are defined **once** as reusable SVG symbols and referenced anywhere via `<use>` — never paste the full SVG path data more than once.

**Define once, reference many.** The `base.html` scaffold already includes the logo defs block at the top of `<body>`. As long as you start from `base.html`, the symbols are present — just reference them. If you ever build a deck from scratch, copy the `<svg style="display:none">…<defs>…</defs></svg>` block from `assets/logos.html` once into the top of `<body>`.

Reference a logo with a one-liner (no path data):

```html
<svg style="height:100%;width:auto;fill:currentColor;"><use href="#logo-kyln"/></svg>
```

Available symbol IDs:

| ID                | Logo                                              |
| ----------------- | ------------------------------------------------- |
| `#logo-kyln`      | Kyln mark + wordmark                              |
| `#logo-kyln-mark` | Kyln gear mark only (no wordmark)                 |
| `#logo-ams`       | Amsterdam Standard wordmark (in its rounded box)  |

**Both logos are monochrome and inherit `currentColor`. Render them in white OR near-black only — never indigo, never any other palette color.**

| Slide background                        | Logo color | How                     |
| --------------------------------------- | ---------- | ----------------------- |
| white / `.bg-soft`                      | near-black | set `color: var(--ink)` |
| `.bg-dark` / `.bg-indigo` / `.bg-image` | white      | set `color: #fff`       |

Set color on a wrapping element and the logo follows it. Set a `height` on the wrapper and let `width: auto` keep the aspect ratio — the viewBox handles the rest.

```html
<!-- on a light slide -->
<div class="deck-logo" style="color: var(--ink); height: 32px;">
  <svg style="height:100%;width:auto;fill:currentColor;"><use href="#logo-kyln"/></svg>
</div>

<!-- on a dark or indigo slide -->
<div class="deck-logo" style="color: #fff; height: 32px;">
  <svg style="height:100%;width:auto;fill:currentColor;"><use href="#logo-kyln"/></svg>
</div>
```

### Where to use them

- **Title slide** — Kyln logo large (60–120px tall), top-left or centered above the heading.
- **Closing slide** — Kyln logo or a co-brand lockup, centered, on a dark or indigo background in white.
- **Chrome** — a small logo (~28px) can sit in the corner. Use the `.chrome-logo` helper, or place it inside `.chrome-top`. Don't put it on every slide — title and closing are usually enough.
- **Co-brand lockup** — Kyln + Amsterdam Standard side by side with a thin divider, when the deck represents both brands. Use the `.logo-lockup` wrapper from `assets/logos.html`.

### Logo rules

- **White or black only.** This is the one hard rule. The logos are never indigo, never tinted, never gradient-filled.
- **Pick the variant for contrast.** Dark/indigo/image slides → white. Light slides → near-black (`--ink`), not pure `#000`.
- **Kyln mark alone.** To show just the gear mark without the "kyln" wordmark, reference `#logo-kyln-mark` instead of `#logo-kyln`.
- **Amsterdam Standard box.** The wordmark ships inside its rounded rule frame (the original lockup). To drop the box and show the wordmark alone, delete the first `<path>` (the frame) inside the `#logo-ams` symbol in the defs block.
- **Don't stretch or recolor.** Keep the aspect ratio (height + `width: auto`). No drop shadows on the logo itself.
- **Restraint.** A logo per deck on the title, optionally one on the close, is plenty. Don't stamp it on every slide.

## Image patterns

Four ways to put an image into a slide. Each supports both URL and base64 sources.

### Source options

| Source     | Use when                                                                              | How                                                                                                         |
| ---------- | ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **URL**    | Image lives on the web. Public images, hosted assets, live case studies.              | `background-image: url('https://...')` or `<img src="https://...">`. HTML stays small.                      |
| **base64** | Image is uploaded locally. Internal screenshots, NDA images, anything not on the web. | Read the file, base64-encode, inline as `data:image/jpeg;base64,...`. HTML becomes one self-contained file. |

For uploaded images, **compress first** before inlining. A typical workflow with PIL:

```python
from PIL import Image; import base64
img = Image.open('/mnt/user-data/uploads/photo.jpg')
# Downscale long edge to 1200px, save at quality 80
img.thumbnail((1200, 1200), Image.LANCZOS)
img.save('/tmp/img.jpg', 'JPEG', quality=80, optimize=True)
with open('/tmp/img.jpg', 'rb') as f:
    b64 = base64.b64encode(f.read()).decode()
# Now embed as: data:image/jpeg;base64,{b64}
```

Target a final HTML file under ~500KB per inlined image. If the user uploads multiple large images, downscale aggressively (720–900px long edge is plenty for web display).

### Pattern 15 · Full-bleed (image as background)

```html
<section
  class="slide bg-image"
  data-slide="N"
  style="background-image: url('IMAGE_URL_OR_DATA_URI');"
>
  <div class="image-gradient-bottom"></div>
  <!-- dark fade for text contrast -->
  <div class="chrome-top">
    <div class="chrome-tag"><span class="chrome-tag-dot"></span> [Label]</div>
    <div class="chrome-num">[NN] / [TOTAL]</div>
  </div>
  <div
    class="flex-1 flex flex-col justify-end max-w-6xl w-full relative"
    style="z-index: 2;"
  >
    <span class="pill pill-on-dark mb-6 w-fit">[Section label]</span>
    <h2 class="h-display text-6xl mb-4" style="color: #fff;">
      [Heading] <span style="color: var(--indigo-glow);">[accent]</span>.
    </h2>
    <p class="text-2xl" style="color: rgba(255,255,255,0.85);">[Subtitle]</p>
  </div>
</section>
```

Use `.image-gradient-bottom` (bottom-up fade) when text sits at the bottom. Use `.image-gradient-full` when text sits anywhere or you want to mute the whole image.

### Pattern 16 · Split (image + text)

```html
<section class="slide bg-soft" data-slide="N">
  <div class="chrome-top">...</div>
  <div
    class="flex-1 grid grid-cols-1 md:grid-cols-2 gap-10 items-center max-w-7xl mx-auto w-full"
  >
    <div>[text content — pill, heading, body]</div>
    <div class="image-card" style="height: 70vh; max-height: 600px;">
      <img src="IMAGE_URL_OR_DATA_URI" alt="..." />
    </div>
  </div>
</section>
```

Image gets 24px corners and fills the right column. Use `object-fit: cover` (default in `.image-card img`).

### Pattern 17 · Hero + image below

```html
<section class="slide" data-slide="N">
  <div class="hero-split">
    <div class="hero-split-top">
      <div class="chrome-top">...</div>
      <!-- chrome inside top half -->
      [eyebrow + big heading]
    </div>
    <div class="hero-split-bottom">
      <img src="IMAGE_URL_OR_DATA_URI" alt="..." />
    </div>
  </div>
</section>
```

Top 58% is a colored panel (indigo by default — change to dark or soft as needed). Bottom 42% is a full-width image. The chrome lives inside `.hero-split-top` so it sits on the colored panel, not the image.

To change top-panel color: edit `.hero-split-top { background: ... }` in the CSS, or override inline.

### Pattern 18 · Showcase (single image with text alongside)

```html
<section class="slide bg-soft" data-slide="N">
  <div class="chrome-top">...</div>
  <div
    class="flex-1 grid grid-cols-1 md:grid-cols-5 gap-10 items-center max-w-7xl mx-auto w-full"
  >
    <div class="md:col-span-3">[text content]</div>
    <div class="md:col-span-2 flex justify-center">
      <img
        src="IMAGE_URL_OR_DATA_URI"
        alt="..."
        class="image-card"
        style="max-height: 78vh; width: auto;
                  box-shadow: 0 20px 50px rgba(26, 26, 46, 0.15);"
      />
    </div>
  </div>
</section>
```

Use for a single hero image that needs to land. Portrait or landscape both work — the image keeps its aspect ratio, gets 24px corners, and a soft drop shadow. Text gets 60% of the width, image 40%.

### Image-pattern rules

- **24px corner radius on contained images** (Patterns 16, 18). No corners on full-bleed (15) or hero-below (17 bottom panel).
- **Always include a dark gradient overlay** when text sits on top of a full-bleed image. Use `.image-gradient-bottom` or `.image-gradient-full`.
- **Chrome contrast**: on `.bg-image` slides, the chrome dot is `--indigo-glow` and the chrome text is white-translucent. The CSS handles this via the `.slide.bg-image .chrome-tag` cascade (already in base.html).
- **Don't stack image slides**. Two in a row feels like a slideshow, not a deck. Break them up with text slides.
- **Compress before inlining**. See the Python snippet above. Aim for ~200KB or less per inlined image.

## Animation

Each slide fades in with a staggered rise (12px translateY, 700ms). Attach `.fade-in` to a section that already has `.active`:

```html
<section class="slide active fade-in" data-slide="1">...</section>
```

Children animate in sequence with staggered delays (already defined for the first 7 children — add more `:nth-child()` rules if you need more).

## Navigation

The base template includes JS for:

- `→` / `space` / `PageDown` — next slide
- `←` / `PageUp` — previous slide
- `Home` / `End` — first / last
- `Escape` — reset to slide 1
- Click — right 70% of screen advances, left 30% goes back

A progress bar runs along the top. A nav hint pill sits at the bottom centre.

Don't change these unless the user asks.

## Design principles to maintain

- **No gradients on flat slides.** Solid colors only for `.bg-soft`, `.bg-indigo`, `.bg-dark`. Gradients are only allowed for image overlays (`.image-gradient-bottom`, `.image-gradient-full`).
- **No additional colors.** The palette is white + soft lavender + indigo + near-black. Don't add green, red, orange, etc.
- **Generous whitespace.** Slide padding scales: `clamp(2rem, 5vw, 5rem)`.
- **Large type.** Headings scale up aggressively. `clamp(2.5rem, 6.5vw, 6.5rem)` is normal for an H2.
- **One accent per heading.** 1–2 indigo words max.
- **Card radius 24px. Pill radius 999px. Image corners 24px.** Always.
- **Logos are white or black only.** The Kyln and Amsterdam Standard logos (`assets/logos.html`) inherit `currentColor` — render them in `--ink` on light slides, `#fff` on dark/indigo/image slides. Never indigo or any other color.
- **Onest only** (with JetBrains Mono for tiny chrome text). Don't swap fonts.

If the user asks to break any of these (different font, gradients, more colors, etc.), gently note that these choices define the aesthetic — then do what they ask if they confirm.
