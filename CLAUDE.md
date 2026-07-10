# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Static landing page for KEEPY.MX (keepy.mx) — a private AI assistant for company documents, delivered through Telegram. Spanish-language (es-MX) marketing site deployed via GitHub Pages (the `CNAME` file maps the custom domain).

## Structure

The entire site is a single self-contained file: `index.html`. All CSS lives in a `<style>` block in the head and all JavaScript in a `<script>` block at the end of the body. There is no build step, no package manager, no framework, and no tests — edits to `index.html` are the deployment artifact. Preview by opening `index.html` directly in a browser or serving the folder with any static server.

The only external dependency is Font Awesome loaded from cdnjs; everything else (fonts fall back to system stacks, images in `assets/`) is local.

## Architecture of index.html

- **Design tokens**: colors, spacing, and easing are defined as CSS custom properties in `:root` (dark theme, cyan accent `--cyan`/`--cyan-2`). Use these variables rather than hard-coding colors.
- **Sections** are anchored by ids referenced from the fixed nav: `#problema`, `#solucion`, `#proceso`, `#diferencia`, `#control`, `#precios` — keep nav links and section ids in sync.
- **Responsive breakpoints** at 980px and 680px; every layout grid collapses there, so new multi-column layouts need corresponding rules in both media queries.
- **JavaScript** handles three things: logo load-failure fallback (`.brand.is-fallback`), card hover glow via `--mx`/`--my` custom properties, and the animated particle canvas in the hero (`.radar__canvas`). All animation respects `prefers-reduced-motion`.
- **CTA links** point to `https://cal.com/keepy` (demo booking) — they appear in the nav, hero, and final section.
