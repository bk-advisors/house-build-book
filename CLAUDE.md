# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A Quarto book project about building a modern house in Africa, authored by Matthew Kuch. The site is hosted on GitHub Pages. The book contains 9 chapters across 3 parts, plus a preface, introduction, and about page.

## Build Commands

```bash
# Render entire book (output goes to _book/)
quarto render

# Preview with live reload
quarto preview

# Render a single chapter
quarto render 1-imagination/index.qmd
```

Quarto is the only build dependency. There are no test suites, linters, or package managers.

## Architecture

**Quarto book project:** Configured via `_quarto.yml` at the root. This file defines the book structure, chapter ordering, and shared HTML format options (theme, TOC, banner style). The output directory is `_book/`.

**Book structure (3 parts, 9 chapters):**

- `index.qmd` — book landing/welcome page
- `13-preface/index.qmd` — Preface
- `14-intro/index.qmd` — Introduction
- Part 1 "The Vision": `1-imagination/`, `2-research/`, `3-resources/`
- Part 2 "The Money": `4-savings/`, `5-loans/`, `6-family/`
- Part 3 "The Building": `7-sub/`, `8-super/`, `9-finishings/`
- `15-about/index.qmd` — About the Author

**Styling:**

- `custom.scss` — SCSS theme overrides (extends Cosmo theme). Defines primary colour `#69b3a2`, title banner styles, TOC active-link colour, callout styling, and utility classes (`.chapter-illustration`, `.practical-tips`, `.part-page`).
- `custom.css` — additional CSS for blockquotes, image captions, and responsive images.
- Per-chapter `style.css` files exist in older chapter directories but are superseded by the shared theme.

**Per-chapter directory layout:**

- `index.qmd` — source content (Quarto Markdown)
- `assets/` — chapter-specific images (mind maps, flowcharts, diagrams)
- `fonts/` — custom fonts (legacy; Chivo, Cocon, Font Awesome)
- `.Rproj` — RStudio project file (legacy; not actively used)

**Images:** Chapters use a mix of local images in `assets/` folders and Unsplash URLs for illustrative photographs. Local images are diagrams/flowcharts created by the author; Unsplash images are decorative illustrations.

## Key Conventions

- Chapter `.qmd` files use simplified YAML front matter (title, subtitle, author, date). Global settings like `toc`, `toc-location`, `title-block-banner`, and `number-sections` are set in `_quarto.yml`.
- Title banners use black background with white text. The primary accent colour is `#69b3a2` (teal).
- Each chapter ends with a `Practical Tips` section using `::: {.callout-tip}` Quarto callout blocks.
- Recurring characters (Vincent, Uncle Mo, Auntie Barbara) appear across chapters as narrative devices to illustrate real-world scenarios.
- The `source-material/` directory contains the original PDF manuscript used as reference.
- R code infrastructure (`.Rproj`, `R/` directories) exists in some chapter folders but is not actively used — chapters are prose-only.
