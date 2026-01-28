# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Lev Altman Timer Site - A personal portfolio/tracking website featuring an interactive timer displaying time since birth with dynamic animations and seasonal color theming. Deployed to GitHub Pages at levaltman.com.

## Architecture

**Single-file vanilla web application** - All HTML, CSS, and JavaScript contained in `index.html` with no build tools or external dependencies.

- **CSS** (lines 14-307): Inline styles with CSS custom properties for theming, responsive breakpoints at 480px, 734px, 900px, 1200px
- **JavaScript** (lines 322-644): Timer logic, seasonal color calculations, wave animation with mouse tracking

## Key Configuration Points

When modifying timer behavior:
- Birth date: line 323 (`new Date('2026-01-26T21:30:00-08:00')`)
- Eighteen-year date: line 324 (target for water fill animation)
- Milestone messages: lines 336-357 (age-based messages like "1 week old")
- Phase messages: lines 364-371 (life stage descriptions)

## Development

No build process required. Open `index.html` directly in a browser or serve with any static file server:

```bash
python3 -m http.server 8000
```

## Deployment

Direct GitHub Pages deployment - push changes to main branch. Custom domain configured via CNAME file.

## Technical Notes

- Timer updates every second via `setInterval`
- Seasonal colors transition smoothly using color interpolation, updating hourly
- Wave animations use `requestAnimationFrame` for 60fps mouse tracking
- Uses CSS `font-feature-settings: "tnum"` for monospaced numerals in timer display
