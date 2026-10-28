# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Placeholder site for yakovaltman.com, kept until Yakov turns 18. It shows Yakov's age as a live clock over a sky that follows the real sun and weather in Haifa. Deployed with GitHub Pages; the custom domain is set in `CNAME`.

The sister site, leonidaltman/ilyaaltman.com, uses the same `index.html`. Only the `<head>` tags, the `<h1>`, the footer text and the `SITE` constant differ, so mirror any other change to both repos.

## Architecture

Everything is in `index.html`: HTML, CSS and JavaScript, no build step and no dependencies apart from Google Fonts.

- `SITE`: name and birth date (UTC). The 18th birthday is derived from it.
- Age: `addMonths` and `ageAt` count calendar months in UTC, clamping to month ends.
- Sky: `sunPosition` gives the sun's altitude and azimuth for Haifa; `SKY_KEYS` maps altitude to zenith, middle and horizon colours; weather dulls and darkens them. The canvas draws stars, sun, moon phase, clouds, rain, snow, fog and lightning. Text colour flips between light and dark from the sky's brightness.
- Weather: Open-Meteo current conditions (no API key), refreshed every 10 minutes. If the request fails the sky still follows the sun.
- `prefers-reduced-motion` stops all animation.

## Development

```bash
python3 -m http.server 8000
```

Try other skies with URL parameters: `?time=dawn|noon|sunset|night` and `?weather=clear|clouds|rain|storm|fog`, for example `http://localhost:8000/?time=sunset&weather=storm`.

## Deployment

Pushing to `main` deploys to the live site.
