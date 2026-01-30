---
title: Amplitude Implementation Guide
---

# Amplitude Implementation Guide

This guide documents how Amplitude is implemented in the `usercentrics-replica` static site.

## Where the Implementation Lives

- `index.html` contains the Amplitude scripts near the end of the file.
- Two script tags are used:
  - Amplitude loader script
  - Session Replay plugin script

## Scripts Included

1. **Amplitude loader**
   - `https://cdn.amplitude.com/script/0dfd933e176deec9a5634f8acf98b0f0.js`
2. **Session Replay plugin**
   - `https://cdn.amplitude.com/libs/plugin-session-replay-browser-1.13.10-min.js.gz`

## Initialization Flow

1. Check that `window.amplitude` exists.
2. If available, add the Session Replay plugin:
   - `window.amplitude.add(window.sessionReplay.plugin({ sampleRate: 1 }))`
3. Initialize Amplitude:
   - `window.amplitude.init('0dfd933e176deec9a5634f8acf98b0f0', { fetchRemoteConfig: true, autocapture: true })`
4. Errors are caught and logged to console as `Amplitude init:`.

## Event Tracking

- The form with id `scanner-form` is tracked on submit.
- Default submit is prevented to keep the site static.
- Event tracked: `Scan Started` with payload `{ url }`.

## How to Modify

- **Change the API key**
  - Update the key passed to `window.amplitude.init(...)`.
- **Adjust session replay sampling**
  - Edit `sampleRate` in the session replay plugin.
- **Add custom events**
  - Call `inst.track('Event Name', { ...props })` where needed.

## Troubleshooting

- If events don’t appear, confirm the scripts load in the browser.
- If `window.amplitude` is undefined, the loader script is blocked or failed to load.
- If the form event is missing, confirm the `scanner-form` id matches in HTML.
