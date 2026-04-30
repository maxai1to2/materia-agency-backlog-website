# Software & Dependency Log — materia-agency-backlog-website mirror project
# ============================================================

## Installed during this session

1. playwright (Python package)
   - pip install playwright
   - Reason: headless browser for rendering JS-heavy Squarespace pages
   - Version: 1.59.0
   - Status: installed

2. chromium-headless-shell (via playwright install)
   - playwright install chromium
   - Reason: browser engine for page rendering
   - Version: chromium-headless-shell v1217
   - Path: ~/Library/Caches/ms-playwright/chromium_headless_shell-1217/
   - Status: installed

## NOT installed (decided against)

- Node.js / nvm / npm
  - Would be needed for: mavis-team MCP orchestration, some website mirroring tools
  - Decision: not needed for Playwright-based rendering approach
  - Can be installed later if needed: brew install node

## Scripts written

1. capture_rendered.py — captures fully-rendered DOM via Playwright, rewrites CDN
   URLs to local asset references, saves static HTML files
   (replaces the original curl-fetched HTML files)

## Approach

- Use Playwright (Python) to load each page, execute all JS, wait for networkidle
- Extract all image URLs loaded via network requests
- Rewrite rendered DOM: replace all CDN image URLs with local file references
- Save as static HTML — visually identical to what a browser would render
- Images stored as external files in /assets/images/ (not base64)
