# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Single-file static portfolio for Nguyen Minh Hoang Duong (Senior Flutter Developer). No build step, no dependencies, no framework — the entire site is `index.html`. The PDF [text](resources/files/CV_Nguyen_Minh_Hoang_Duong.pdf) and [text](resources/files/CV_Nguyen_Minh_Hoang_Duong_2.pdf) is the source-of-truth for content.

## Running locally

```bash
open index.html
# or serve with a local server
python3 -m http.server 8080
```

## Architecture

Everything lives in `index.html`:

- **`<style>`** — all CSS using CSS custom properties (design tokens defined in `:root`). Three font families: Sora (display), Inter (body), JetBrains Mono (code/accents).
- **Sections** (find by HTML comments): `<!-- hero -->`, experience `<details class="commit">` blocks, skills as `import` statements, education as a `pubspec.yaml` block.
- **`<script>`** at the bottom — vanilla JS only, no libraries.

Design motif: Flutter/Dart "code editor" aesthetic — dark theme (`--bg: #11141b`), blue/amber/teal accent palette.

## Updating content

All content is inline in `index.html`. Search for the section comments to jump to the right place. No CMS, no data file, no template engine.

## Deployment

GitHub Pages from the `main` branch root. Target URL: `https://hoangduongit1997.github.io/portfolio/`
