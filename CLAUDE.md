# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-file static portfolio for Nguyen Minh Hoang Duong (Senior Flutter Developer). No build step, no dependencies, no framework — the entire site is `index.html` (1232 lines). The PDFs in `resources/files/` are the source-of-truth for content.

## Running locally

```bash
open index.html
# or serve with a local server
python3 -m http.server 8080
```

## Architecture

Everything lives in `index.html`:

- **`<style>`** (lines ~20–600) — all CSS using CSS custom properties. Design tokens in `:root`: `--bg`, `--blue`, `--amber`, `--teal`, `--purple` plus `-soft`/`-glow` variants. Three font families: Sora (display), Inter (body), JetBrains Mono (code/accents). Max content width: `--maxw: 1080px` via `.wrap`.
- **HTML sections** — find by comment or `id`:
  - `<!-- hero -->` — `<header class="hero">` with photo, stats, highlights, CTAs
  - `<!-- about -->` — `<section id="about">` with summary blockquote and industry cards
  - `<section id="experience">` — accordion of `<details class="commit">` blocks, one open at a time
  - `<section id="skills">` — skills styled as Dart `import` statements
  - `<section id="education">` — education styled as `pubspec.yaml` block
  - `<section id="contact">` — contact card
- **`<script>`** (lines ~1060–1229) — vanilla JS only; handles scroll-reveal, counters, accordion, hamburger nav, typing animation, footer year.

Design motif: Flutter/Dart "code editor" aesthetic — dark theme (`--bg: #11141b`), blue/amber/teal accent palette.

## Resources

```
resources/
  files/
    CV_Nguyen_Minh_Hoang_Duong.pdf    ← downloadable CV (linked in nav)
    CV_Nguyen_Minh_Hoang_Duong_2.pdf
  images/
    avatar.jpg   ← hero photo
    og.svg       ← Open Graph / social preview image
```

## Key JS patterns

**Scroll-reveal:** Add `class="reveal"` to any element — JS adds `class="in"` when it enters the viewport (threshold 0.08). CSS handles the fade/slide transition.

**Animated counters:** On `<b data-target="14" data-suffix="+">` inside `.stat-row` — JS counts up on first scroll into view.

**Accordion (experience):** `<details class="commit">` elements are mutually exclusive — opening one closes others with a smooth max-height animation. The `.commit-body` child is the animated container.

**Typing animation:** `<span id="heroTyping">` cycles through the `phrases` array defined at line ~1128. Edit that array to change the rotating titles.

## Deployment

GitHub Pages from the `main` branch root. Target URL: `https://github.com/hoangduongit1997/hoangduongit1997.github.io.git`
