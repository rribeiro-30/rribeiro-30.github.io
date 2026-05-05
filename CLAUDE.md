# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page portfolio website for Rogério Salomão Ribeiro (.NET developer). No build system, no package manager, no framework — just three files: `index.html`, `style.css`, `script.js`.

## Development

No build step. Serve directly:

```bash
python -m http.server 8000
# then open http://localhost:8000
```

Or open `index.html` directly in a browser.

No linting, testing, or CI configuration exists.

## Architecture

### File roles
- `index.html` — All markup. Six sections: `#hero`, `#sobre`, `#experiencia`, `#formacao`, `#skills`, `#contato`.
- `style.css` — All styling (~950 lines). Dark GitHub-like theme.
- `script.js` — Four IntersectionObserver instances (`.reveal` fade-ins with stagger, `.stat-num` animated counters, `.skill-fill` bar animations, scroll-triggered nav `.scrolled` class / `#back-to-top` visibility), plus mobile hamburger toggle and smooth-scroll for `a[href^="#"]` links.
- `foto.jpeg` — Profile photo used in the hero avatar.

### CSS variables system
All colors and core sizing are CSS custom properties on `:root`. Change the theme by editing variables there rather than hunting individual rules. Key tokens: `--bg`, `--bg-alt`, `--surface`, `--border`, `--accent`, `--accent-glow`, `--text`, `--text-muted`, `--green`, `--radius`, `--nav-h`.

### Responsive breakpoints
Three tiers defined in `style.css`:
- **≤900px** — hero stacks vertically, single-column about section
- **≤640px** — hamburger mobile nav, compact cards, smaller fonts
- **≤430px** — iPhone-specific: floating badges hidden, single-column skills, `100svh` viewport, ultra-compact spacing

### External dependencies (CDN only)
- Google Fonts — Inter (weights 300–800)
- Font Awesome 6.5.0 — icons

No npm packages or runtime dependencies.
