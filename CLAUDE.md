# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal academic portfolio website for Danya Li, hosted on GitHub Pages (danyayay.github.io). It is a **pure static site** — no build tools, no npm, no frameworks. All files are served directly to the browser.

## Development

No build step is required. Open `index.html` directly in a browser, or serve locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

There are no lint, test, or CI commands.

## Architecture

The site is a single HTML page (`index.html`) with all sections rendered inline. Content is structured into four visible sections plus an Easter egg:

1. **Navigation** — fixed header with responsive hamburger menu (JS-driven toggle)
2. **Hero/About** — bio, photo, contact links, research interest tags
3. **Publications** — 2-column card grid; each card has a colored left-accent stripe, figure thumbnail, and collapsible abstract
4. **Experience** — vertical timeline layout (timeline dots + connector line via CSS)
5. **Duck Pond** — interactive canvas Easter egg at the bottom; ducks are spawned on click, physics-simulated (gravity, waypoint movement, collision), and a special animation fires when >180 ducks are active

### Key files

| File | Purpose |
|------|---------|
| `index.html` | Entire site — markup, inline `<style>` overrides, and all JavaScript |
| `style.css` | All styles — CSS variables, layout, animations, responsive breakpoints |
| `figures/` | Profile photo and publication figure images |
| `CV_danya.pdf` | Linked CV document |
| `.gitignore` | Ignores `papers/` directory and `.DS_Store` |

### Styling conventions

- Color palette defined as CSS variables at `:root` in `style.css` — use these rather than hardcoded values
- Each publication card has a unique gradient accent stripe applied via an inline `style` attribute on the `.pub-accent` element
- Fonts loaded from Google Fonts: **Playfair Display** (headings), **Nunito** (body), **Space Mono** (metadata/labels)
- Responsive breakpoints: 768px (tablet — hamburger nav, hero stacks) and 480px (mobile — font size reductions)
- Scroll-reveal animations use `IntersectionObserver` in `index.html`

### Adding a publication

1. Copy an existing `.pub-card` block in `index.html`
2. Add the figure image to `figures/`
3. Update the `.pub-accent` gradient to a new color scheme
4. Update title, authors, venue, abstract, and links
5. Publication cards appear in source order (newest first by convention)
