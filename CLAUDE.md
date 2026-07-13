# The Evolution of Digital Logic — Project Conventions

## Purpose

This is a structured notebook chronicling the evolution of digital logic — from mechanical switches, relays, and discrete gates through memory, programmable devices, and the integrated architectures that followed. The tone is exploratory and explanatory: recording concepts, tradeoffs, and the through-line that connects each generation of logic technology to the next. The emphasis is on *why* digital logic developed the way it did, not on cataloging devices.

This is one volume in a set of engineering notebooks (alongside `ee-notebook` and `embedded`). It shares their voice, structure, and Hugo setup.

## Repository Structure

- **Hugo static site** using the [hugo-book](https://github.com/alex-shpak/hugo-book) theme
- Content lives in `content/docs/` organized into L0 sections (chapters)
- Built with `make html` (runs `hugo --minify`)
- Local dev server with `make server`
- Deployed to GitHub Pages via `.github/workflows/hugo.yml` on push to `main`

## Central Argument

Everything on the site should reinforce one thesis: **digital design has evolved by moving functionality to higher levels of integration — not by making the lower levels disappear.** This is *not a nostalgia project*. The primitives (gates, latches, counters, muxes, buffers, comparators, analog switches) are the vocabulary practicing hardware engineers still reach for; integration changed the package and voltage, not the idea. The notebook aims to be the missing bridge between *NAND to Tetris* (build logic from first principles) and embedded/firmware work.

## Section Structure

Content uses a 3-level hierarchy: L0 (Parts) → L1 (subsections) → L2 (pages). The book is organized into six Parts, following the evolution from physical switches through the primitives and logic families to the integrated/programmable present.

| Weight | Directory | Title |
|--------|-----------|-------|
| 1 | `before-the-ic/` | Before the IC |
| 2 | `building-blocks/` | Primitive Building Blocks |
| 3 | `technology/` | The Technology |
| 4 | `glue-logic-toolbox/` | The Glue Logic Toolbox |
| 5 | `obsolete/` | What Became Obsolete? |
| 6 | `modern-world/` | The Modern World |
| 100 | `glossary/` | Glossary |

**Primitive Building Blocks** is the heart, split into six L1 subsections, each carrying a one-line mental model:

| Subsection | Mental model |
|-----------|--------------|
| `gates/` | Gates make decisions. |
| `storage/` | Gates remember. |
| `counting/` | Hardware can count without software. |
| `selection/` | Hardware routes information. |
| `moving-data/` | Hardware transports information. |
| `analog-helpers/` | Digital systems still touch the analog world. |

**The Glue Logic Toolbox** is organized by *problem* ("I need more outputs"), not by chip; its `_index.md` carries a problem→chip quick-reference table. **What Became Obsolete?** is a single reference page (obsolescence table), no leaf pages.

L0 and L1 directories use `bookCollapseSection: true` in their `_index.md` so they appear as collapsible items in the sidebar. L2 entries are leaf pages (`.md` files) inside the section/subsection directories. Most content pages are currently minimal stubs (`_This page is in progress._`); the structure is complete and prose is filled in over time.

## Adding a New Entry

Create a markdown file inside the appropriate section directory under `content/docs/`:

```
content/docs/<section>/<entry>.md
```

Frontmatter pattern:

```yaml
---
title: "Entry Title"
weight: 10
---
```

- **title**: Descriptive name for the entry
- **weight**: Controls ordering within the section; use increments of 10 to leave room for future entries

## Content Conventions

- **Evergreen entries**: Entries get revised and expanded over time; they are not dated posts
- **No chronological structure in filenames**: The subject matter is historical, but the files themselves are not dated posts — no dates in filenames or frontmatter
- **Neutral voice**: No first-person (*I*, *we*) or second-person (*you*, *your*) in body pages. Use neutral, observation-oriented phrasing. See `styleguide.md` for full voice rules. (The preface is the one signed, first-person exception.)
- **Why over what**: Prefer explaining the problem a technology solved and the tradeoff it accepted over restating how a device is wired
- **Standard L2 sections**: Tips, Caveats, In Practice — names and intent are fixed (see `styleguide.md`)
- **Entry types**: Concepts, historical context, patterns, comparisons — no formal taxonomy required, just pick what fits

## Diagrams & Math

- **Graphviz** — the `{{</* graphviz */>}}...{{</* /graphviz */>}}` shortcode renders DOT diagrams client-side. Useful for state machines, block diagrams, and logic flow.
- **Circuit figures** — the `{{</* circuit caption="..." */>}}...{{</* /circuit */>}}` shortcode wraps inline SVG/diagram markup in a captioned figure (styled by `static/css/circuit.css`).
- **Images** — the `{{</* img src="..." alt="..." width="..." */>}}` shortcode resizes page-bundle images to WebP.
- **KaTeX** — the hugo-book theme includes KaTeX but loads it only on pages that invoke the shortcode. Any page using `$$` or `\(` math delimiters must include `{{</* katex */>}}{{</* /katex */>}}` on the line immediately after the frontmatter.

## Glossary & Tooltip System

An automatic glossary tooltip system links terms on every page (except the glossary and preface) to their definitions.

**Key files:**
- `data/glossary.json` — single source of truth (term, definition, anchor, aliases)
- `content/docs/glossary/_index.md` — rendered glossary page (weight 100, last sidebar item)
- `static/js/glossary.js` — client-side auto-linking (first occurrence per term per page)
- `layouts/shortcodes/glossary-list.html` — renders the full list on the glossary page
- `layouts/partials/docs/inject/body.html` — injects glossary data + JS

The glossary is seeded with a few core terms; expand it as chapters are written.

## Build & Verify

```sh
make html      # Build the site (hugo --minify)
make server    # Local dev server with live reload
make clean     # Remove build artifacts
```
