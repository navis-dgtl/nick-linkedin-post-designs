# Carousel Design System

This document defines Nick Prince's visual brand for LinkedIn carousels and any companion image content. Every visual produced under this skill must follow these rules. They are not suggestions.

---

## Brand Source

The visual language comes from Nick's LinkedIn banner: dotted texture grid, soft warm orange accent, dotted world map, near-black body text on a warm cream background. The full banner aesthetic is the reference. Carousels extend that look into a 4:5 slide format.

---

## Color System

Six tokens. Do not introduce additional colors. Do not substitute hex values.

| Token | Hex | Use |
|-------|------|-----|
| `--orange` | `#E07856` | Primary accent. Brand mark, CTAs, headline emphasis, progress fill, divider lines. |
| `--orange-soft` | `#EDA68C` | Secondary accent. Dot textures, tag labels on dark surfaces, soft edges. |
| `--orange-deep` | `#C25E3D` | Quote attributions, hover states, dense accent moments. |
| `--orange-tint` | `#FCEFE8` | Quote box backgrounds, callout panels, subtle warm fills. |
| `--bg-light` | `#F5F2EE` | Light slide background. Warm cream. Never pure white. |
| `--bg-card` | `#FAF7F3` | Card and panel surfaces on light slides. Slightly warmer than the page. |
| `--bg-dark` | `#1F1B18` | Dark slide background. Near-black with brown undertone. Never pure black. |
| `--bg-dark-card` | `#2A2520` | Card surfaces on dark slides. |
| `--ink` | `#1F1B18` | Primary text on light slides. Same value as dark background by design. |
| `--ink-soft` | `#6B635C` | Secondary text, descriptions, captions. |
| `--ink-faint` | `#A39B94` | Tertiary text, timestamps, disabled states. |
| `--line-light` | `#E8E2DA` | Borders and dividers on light slides. |
| `--line-dark` | `rgba(245, 242, 238, 0.08)` | Borders and dividers on dark slides. |

### Color Usage Rules

- Orange must cover less than 20% of any single slide's visible surface. It is an accent, not a fill.
- Headlines either use the ink color with one or two orange-emphasized words, or the orange color with the rest in ink. Never an entire headline in orange.
- Status colors (red, green, blue) are not part of this system. If a slide needs to indicate state, use weight, position, or pairing with the orange accent.
- Pure white (`#FFFFFF`) appears only on text inside the orange CTA button and the orange split-block. Never as a background.

---

## Typography

**Font family:** Plus Jakarta Sans. Loaded from Google Fonts. No fallback to Inter, Roboto, Arial, or system defaults.

**Weights used:**
- 500 (Medium) - body copy, descriptions, captions
- 600 (Semibold) - tag labels, progress counters, button text
- 700 (Bold) - subheadings within slides
- 800 (Extrabold) - hero headlines, statistic numbers, slide titles, CTA headlines

**Type scale (fluid sizing using clamp):**

| Element | Min | Preferred | Max |
|---------|-----|-----------|-----|
| Hero display | 38px | 6.5vh | 64px |
| Slide heading (h2) | 28px | 5vh | 48px |
| Stat number | 42px | 7vh | 72px |
| CTA headline | 30px | 5vh | 48px |
| Body copy | 14px | 2vh | 20px |
| Tag label | 10px | 1.4vh | 14px |
| Numbered list label | 14px | 2vh | 18px |
| Numbered list description | 12px | 1.7vh | 15px |
| Progress counter | 11px | 1.4vh | 13px |

**Letter-spacing rules:**
- Hero display: -1.2px (tight)
- Slide heading: -0.7px
- Stat numbers: -1.5px to -1.8px (tightest)
- Tag labels: 2.5px (widest, uppercase)
- Body copy: 0px

**Line-height rules:**
- Headlines: 1.05 to 1.15 (tight)
- Body copy: 1.45 to 1.55 (relaxed)
- Stat numbers: 1.0 (no extra leading)

---

## Textures

The textures are what make the brand feel like Nick's banner. Three options. One per slide. Do not combine on a single slide.

### Dotted grid (primary)

Subtle radial dot pattern across the entire slide. Used on most slides. Applied via `::before` pseudo-element.

**Light slide version:**
```css
background-image: radial-gradient(circle at center, rgba(224, 120, 86, 0.18) 1px, transparent 1.5px);
background-size: 16px 16px;
```

**Dark slide version:**
```css
background-image: radial-gradient(circle at center, rgba(224, 120, 86, 0.18) 1px, transparent 1.5px);
background-size: 18px 18px;
```

### Diagonal lines (variation)

Used on one or two slides per carousel for visual rhythm. Always 135deg angle.

```css
background-image: repeating-linear-gradient(
  135deg,
  transparent 0,
  transparent 12px,
  rgba(224, 120, 86, 0.05) 12px,
  rgba(224, 120, 86, 0.05) 13px
);
```

### Corner dot clusters (decorative)

Larger, denser dot fields that bleed off the edge of a slide. Used as accent moments. One or two per slide max. Never centered.

```css
.dot-cluster {
  position: absolute;
  width: 220px;
  height: 220px;
  background-image: radial-gradient(circle at center, var(--orange-soft) 1.5px, transparent 2px);
  background-size: 14px 14px;
  opacity: 0.5;
}
```

Position classes: `.tl` (top-left), `.tr` (top-right), `.br` (bottom-right). Always offset by -20px to -40px so the cluster fades off the canvas.

---

## Slide Layouts

Two main vertical alignments. Choose based on content density.

### Center alignment (`pad-center`)
Used for hero and CTA slides. Content sits centered vertically with breathing room above and below.

```css
padding: 8% 9%;
height: 100%;
display: flex;
flex-direction: column;
justify-content: center;
```

### Bottom alignment (`pad-bottom`)
Used for content-dense slides. Text sits at the bottom with negative space above. This is the primary layout for stat slides, numbered lists, and comparison slides.

```css
padding: 8% 9% 12%;
height: 100%;
display: flex;
flex-direction: column;
justify-content: flex-end;
```

The 12% bottom padding clears the progress bar.

---

## Components

These are the only pre-approved component patterns. Do not invent new ones without explicit instruction.

### Personal lockup (slide 1 hero)

Profile image circle + name stack. Sits at the top of the hero slide.

```html
<div class="lockup">
  <div class="mark"><img src="{PROFILE_IMAGE_URL}" alt="Nick Prince" /></div>
  <div class="name-stack">
    <div class="name">NICK PRINCE</div>
    <div class="role">AI Solutions</div>
  </div>
</div>
```

The `mark` div has a 2px orange border, full circle, image cropped with `object-fit: cover`.

### Tag label

Small uppercase label above each slide heading. Categorizes the slide.

```html
<span class="tag on-light">Three patterns</span>
<span class="tag on-dark">The 2026 numbers</span>
```

Color: `--orange` on light, `--orange-soft` on dark. Letter-spacing 2.5px. 10-14px font size.

### Stat row (data slide)

Big orange number + supporting label. Used on the stats slide.

```html
<div class="stat-row">
  <div class="stat-num">80%</div>
  <div class="stat-label">of AI projects fail to deliver intended business value.</div>
</div>
```

Stat number is 42-72px, weight 800, color `--orange`. Label is 12-16px, weight 500.

### Numbered row (patterns slide)

Two-digit orange number + bold label + muted description. Used for "three patterns" or "three principles" content.

```html
<div class="num-row">
  <span class="num">01</span>
  <div class="copy">
    <span class="label">Leadership buys the tool. The work stops there.</span>
    <span class="desc">Access alone changes nothing. Mindset and workflow have to move with it.</span>
  </div>
</div>
```

Always use `01`, `02`, `03` format. Not `1.` or `(1)`.

### Compare grid (mindset shift slide)

Two-column comparison. Old way vs new way. Used for mindset shifts or before/after framing.

```html
<div class="compare">
  <div class="col old">
    <div class="col-tag">Search mindset</div>
    <div class="col-text">Type a question. Hit enter. Scroll the results.</div>
  </div>
  <div class="col new">
    <div class="col-tag">Conversation</div>
    <div class="col-text">Give context. Iterate. Treat AI like a teammate.</div>
  </div>
</div>
```

Old column uses muted background. New column uses orange-tinted background. Always pair them. Never use one column alone.

### Quote box (insight slide)

Orange-bordered callout for the insight payload or key quote.

```html
<div class="quote-box">
  <div class="quote-text">[The core insight, one sentence]</div>
  <div class="quote-attr">[Attribution or framing label]</div>
</div>
```

Background: `--orange-tint`. Left border: 4px solid `--orange`. Attribution is uppercase, letter-spaced, in `--orange-deep`.

### 80/20 split (math slide)

Visual representation of an unequal split. Used when the post argues a percentage breakdown.

```html
<div class="split-row">
  <div class="split-tools">
    <div class="split-pct">20%</div>
    <div class="split-cap">Buying the tools</div>
  </div>
  <div class="split-enable">
    <div class="split-pct">80%</div>
    <div class="split-cap">Enabling your staff to actually use them</div>
  </div>
</div>
```

The smaller percentage uses the cream card background. The larger uses solid orange. Visual weight matches argument weight.

### CTA stack (final slide)

Profile mark + name + headline + subline + button.

```html
<div class="cta-stack">
  <div class="cta-mark"><img src="{PROFILE_IMAGE_URL}" /></div>
  <div class="cta-name">NICK PRINCE</div>
  <h2 class="cta-headline">[Closing verdict from the post]</h2>
  <p class="cta-sub">[One supporting line]</p>
  <div class="cta-btn">Follow for more →</div>
</div>
```

The CTA mark is larger than the lockup mark (64-96px vs 38-56px) with a 3px orange border.

---

## Required Slide Elements

Every slide except the last gets these two:

### Progress bar (bottom of every slide)

3px height, full-width track at the bottom. Fills proportionally to slide position.

- Position: absolute bottom, 18px-22px padding
- Track color: `rgba(31, 27, 24, 0.1)` on light, `rgba(245, 242, 238, 0.12)` on dark
- Fill color: `--orange` (both modes)
- Counter: "1/7" format, weight 600, faint

### Swipe arrow (right edge, every slide except last)

Subtle chevron indicating swipe direction. Removed on the final slide so the user knows they reached the end.

- 6% width, min 40px
- Gradient fade from transparent to subtle tint
- Chevron stroke: `rgba(31, 27, 24, 0.3)` on light, `rgba(224, 120, 86, 0.55)` on dark

### Floating dot indicator (top-right, fixed)

Small pill of dots showing carousel position. Not part of the slide image, sits over the viewport.

- Background: `rgba(0,0,0,0.4)` with `backdrop-filter: blur(8px)`
- Active dot: white, elongated to 14px width
- Inactive dots: `rgba(255,255,255,0.35)`

---

## Slide Sequence

The default 7-slide arc maps directly to a Nick Prince LinkedIn post structure.

| Slide | Background | Texture | Content from post |
|-------|-----------|---------|-------------------|
| 1 | Light | Dots | Hook line + reframe + lockup |
| 2 | Dark | Dots | Data block (3 stats) |
| 3 | Light | Lines | Three numbered patterns |
| 4 | Dark | Dots | Pivot / mindset shift (compare grid) |
| 5 | Light | Dots | Insight payload (quote box) |
| 6 | Dark | Dots | Math or proof (80/20 split, before/after) |
| 7 | Light | Dots | Closing verdict + CTA |

Light and dark slides alternate to create rhythm. The first and last are light to bookend the deck. Texture variation prevents pattern fatigue.

### Flex points

- A 5-slide deck cuts slides 4 and 6.
- A 9-slide deck adds a "consequence" slide after slide 3 and a "case study" slide after slide 5.
- Never exceed 10 slides. Instagram caps at 10.

---

## Hard Rules

These do not bend.

1. Plus Jakarta Sans only. No serif fonts. No system defaults.
2. The six-token color palette only. No introduced colors.
3. Orange covers less than 20% of any slide.
4. Backgrounds are warm cream or warm near-black. Never pure white. Never pure black.
5. Headlines use weight 800. Body copy uses weight 500. Tags use weight 600 with 2.5px letter-spacing.
6. Texture appears on every slide. Either dotted grid or diagonal lines. Never both on one slide.
7. The first and last slides are always light.
8. The last slide has no swipe arrow.
9. The progress bar fills to 100% on the last slide.
10. The personal lockup appears on slide 1 and slide 7. Not on intermediate slides.
11. Aspect ratio is 4:5. Always.
12. No emojis anywhere. Not in copy, not as decoration.
13. No drop shadows on cards or text. The texture and color contrast carry visual hierarchy.
14. No gradients on backgrounds. Only on the swipe arrow fade and the orange split-block dot overlay.

---

## Export Notes

The carousel HTML renders fullscreen at 4:5 in any modern browser. To export individual slide images for posting:

1. Open the HTML in Chrome or Safari
2. Set the viewport to 1080x1350 (use dev tools device emulation or resize the window)
3. Screenshot each slide using the OS screenshot tool or browser screenshot extension
4. Save as PNG, name them `slide-1.png` through `slide-7.png`

For batch export, request a "print-stacked" version of the carousel. That layout renders all slides vertically at exact 1080x1350 dimensions for one-shot capture.

---

## Failure Modes to Avoid

- Crowding a slide with body copy. If a slide has more than 60 words of body text outside headlines and labels, cut.
- Using orange for paragraph text. Orange is for accents and emphasis only.
- Centering all text on every slide. Only the hero and CTA use center alignment.
- Mixing texture types on a single slide.
- Adding decorative elements that are not in this document.
- Using stock icons or illustrations. The brand is type-led and texture-led.
- Generating slides that look like generic SaaS marketing. The dot textures and warm palette are the signature. Do not let them drift toward cool grays or blue accents.
