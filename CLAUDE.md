# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Yakov Altman Timer Site - A personal portfolio/tracking website featuring an interactive timer displaying time until/since birth with dynamic weather-based sky animations and glassmorphism UI. Deployed to GitHub Pages at levaltman.com.

## Architecture

**Single-file vanilla web application** - All HTML, CSS, and JavaScript contained in `index.html` with no build tools or external dependencies.

- **CSS** (lines 47-911): Inline styles with CSS custom properties for theming, glassmorphism effects, sky gradient presets, responsive breakpoints at 320px, 480px, 734px, 900px, 1200px
- **JavaScript** (lines 978-2237): Timer logic, weather API integration, canvas-based weather animations, sky gradient calculations

## Key Configuration Points

When modifying timer behavior:
- Birth date: line 981 (`BIRTH_DATE: '2026-01-26T17:51:00.000Z'`)
- Eighteen-year date: line 982 (`EIGHTEEN_YEARS_DATE`)
- Weather location: lines 991-993 (Haifa coordinates and timezone)
- Milestone messages: lines 1814-1835 (age-based messages)
- Phase messages: lines 1842-1849 (life stage descriptions)

## Weather System

The site displays real-time weather for Haifa, Israel using the Open-Meteo API (no API key required):
- Weather widget shows temperature, wind, humidity, WMO code
- Sky gradient dynamically adjusts based on temperature, time of day, and weather conditions
- Canvas-based particle animations for rain, snow, fog, clouds, wind
- Lightning effects for thunderstorms

## Development

No build process required. Open `index.html` directly in a browser or serve with any static file server:

```bash
python3 -m http.server 8000
```

Console commands for testing sky effects:
- `testSky('sunset', 'thunderstorm')` - Test specific time/weather combination
- `testAllSkies()` - Cycle through all combinations

## Deployment

Direct GitHub Pages deployment - push changes to main branch. Custom domain configured via CNAME file.

## Technical Notes

- Timer updates every second via `setInterval`
- Weather data fetched every 10 minutes from Open-Meteo API
- Sky colors interpolate smoothly between weather updates over 60 seconds
- Canvas weather animations use `requestAnimationFrame` for 60fps rendering
- Glassmorphism UI with `backdrop-filter: blur()` for frosted glass effect
- Uses CSS `font-feature-settings: "tnum"` for monospaced numerals
- Accessibility: screen reader support, reduced motion preference, high contrast mode
