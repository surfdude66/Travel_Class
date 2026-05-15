# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the App

No build step. Serve the single file with Python:

```bash
python -m http.server 3000
# open http://localhost:3000
```

## Architecture

Everything lives in `index.html` — one file, three blocks in order:

1. **`<style>`** — all CSS, organised with `/* ── SECTION ── */` comment banners
2. **`<body>`** — HTML sections in anchor order: `#home` → `#home-form-section` → `#guides` → `#cities` → `#tools` → `#weather` → `#safety` → `#enquiry` → `<footer>`
3. **`<script>`** — all JS at the bottom, no modules

## Design Tokens (CSS Variables)

| Variable | Value | Use |
|---|---|---|
| `--primary` | `#1a1a2e` | Deep navy — headings, buttons, nav |
| `--accent` | `#e8b86d` | Warm gold — highlights, CTAs |
| `--bg` | `#f8f7f4` | Off-white — alternating section backgrounds |
| `--heading` | Playfair Display | Serif font for all headings |
| `--body` | Inter | Sans-serif for body copy |

## Key JS Objects & Functions

**`cityGuides` object** — the single source of truth for all 12 destinations. Each key (e.g. `'seoul'`, `'tokyo'`) holds: `name`, `country`, `image` (Unsplash URL), `budget` (SGD/day), `flight`, `season`, `desc`, `overview`, `itinerary` (3 days), `food[]`, `transport`, `costs{}`, `safety[]`, `photoSpots[]`.

**Adding a new city:** add an entry to `cityGuides` — `renderCityCards()` and `openModal()` pick it up automatically.

| Function | What it does |
|---|---|
| `renderCityCards()` | Generates all 12 city cards from `cityGuides` into `#cityCardsGrid` |
| `openModal(key)` | Renders and opens the 7-tab guide modal for a given city key |
| `switchTab(el, tabId)` | Switches active tab inside the open modal |
| `setupForm(formId, successId)` | Wires up enquiry form: validates, saves entry to `localStorage['enquiries']`, shows success banner |
| `calculateBudget()` | Reads budget tool inputs; uses `budgetDefaults` and `flightEst` lookup maps |
| `renderChecklist()` / `togglePackItem(id)` | Packing checklist backed by `localStorage['packingList']` |
| `addItineraryItem()` / `renderItinerary()` | Itinerary planner backed by `localStorage['itinerary']` |
| `convertCurrency()` | Static SGD→8-currency conversion using `fxRates` map |

## Images

All images are Unsplash direct URLs (`https://images.unsplash.com/photo-{id}?w=900&q=85`). Photo IDs are hardcoded in `cityGuides[key].image`. To change a city's image, replace the photo ID — use `?w=600&q=80` for cards and `?w=900&q=85` for hero/modal sizes.

## Persistence

`localStorage` keys used:
- `enquiries` — array of enquiry form submissions
- `packingList` — `{ [checkboxId]: boolean }` map for checklist state
- `itinerary` — array of `{ day, time, activity, notes }` objects

## Weather Section

The weather widget HTML structure is present but the live fetch is intentionally removed. To enable: get a free key from `openweathermap.org/api` and add a `checkWeather()` function that calls `https://api.openweathermap.org/data/2.5/weather?q={city}&appid={key}&units=metric`.
