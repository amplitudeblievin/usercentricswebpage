---
title: User Guide
---

# User Guide

This guide documents the implementation workflow for the `usercentrics-replica` static site.

## Project Overview

- Single-page static site built in `index.html`
- Styles live in the `<style>` block in `index.html`
- No build step or framework required

## Local Setup

1. Start a local server from the project folder:
   - `python -m http.server 8000`
2. Open the site:
   - `http://localhost:8000/index.html`

## Implementation Workflow

1. **Edit content or layout**
   - Update HTML in `index.html` (sections, copy, links, CTA text).
2. **Adjust styling**
   - Update CSS in the `<style>` block in `index.html`.
   - Primary buttons use `.btn-primary`.
3. **Preview changes**
   - Refresh the browser tab running `http://localhost:8000/index.html`.

## Styling Conventions

- Design tokens are defined under `:root` in `index.html`.
- Primary buttons are green:
  - Use `--uc-green` for normal state.
  - Use `--uc-green-dark` for hover state.

## Common Tasks

- **Change the header CTA text**
  - Edit the “Start free” link in the `<header>` navigation.
- **Add a new section**
  - Copy an existing `<section>` block and adjust headings/content.
- **Update CTA colors**
  - Modify `.btn-primary` or add a new button class.

## Troubleshooting

- If the page doesn’t load, confirm the server is running and the URL is correct.
- If styles don’t apply, check for typos in class names or CSS selectors.
