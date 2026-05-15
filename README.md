# Travel Explorer

**We went, so you know where to go.**

A premium single-page travel discovery website for curated Asia–Pacific city guides, built with pure HTML, CSS, and JavaScript — no frameworks, no backend, no build step.

![Travel Explorer](https://images.unsplash.com/photo-1476514525535-07fb3b4ae5f1?w=1200&q=80)

## Live Demo

Open `index.html` directly in a browser, or serve it locally:

```bash
python -m http.server 3000
# → http://localhost:3000
```

## Features

### 12 Destination Guides
Seoul · Singapore · Bali · Tokyo · Bangkok · Hong Kong · Kuala Lumpur · Maldives · Phuket & Krabi · Sydney · Taipei · Hanoi

Each guide includes a full modal with:
- 3-day suggested itinerary
- Must-try food & drink
- Transport tips (airport → city + local)
- Cost breakdown in SGD
- Safety tips
- Best photo spots

### Travel Tools
| Tool | Description |
|---|---|
| Budget Calculator | Estimates total trip cost including flights, based on destination and party size |
| Packing Checklist | 5-category pre-filled checklist with progress bar; state saved in `localStorage` |
| Itinerary Planner | Add/sort/clear day-by-day activities; persisted in `localStorage` |
| Currency Converter | Live SGD conversion to USD, EUR, JPY, THB, IDR, MYR, AUD, HKD |

### Other Sections
- **Enquiry forms** — validated, stored in `localStorage` (no backend required)
- **Safety guide** — regional tips for Southeast Asia, East Asia, Pacific & Oceania, and general travel
- **Weather section** — ready to connect to OpenWeather API (see below)

## Adding Live Weather

1. Get a free API key at [openweathermap.org/api](https://openweathermap.org/api)
2. In `index.html`, find the comment `YOUR_API_KEY_HERE` in the `<script>` block
3. Add a `checkWeather()` function calling:
   ```
   https://api.openweathermap.org/data/2.5/weather?q={city}&appid={key}&units=metric
   ```
The HTML input and result card are already in place — one function and it's live.

## Tech Stack

- **HTML5** — semantic single-page structure with anchor navigation
- **CSS3** — custom properties, CSS Grid, Flexbox, smooth transitions
- **Vanilla JS** — no libraries or frameworks
- **Fonts** — Playfair Display (headings) + Inter (body) via Google Fonts
- **Images** — Unsplash (direct CDN URLs)
- **Persistence** — browser `localStorage` only

## Destinations at a Glance

| City | Country | Budget/day (SGD) | Flight from SG | Best Season |
|---|---|---|---|---|
| Seoul | South Korea | $120 | 6h | Mar–May, Sep–Nov |
| Singapore | Singapore | $150 | — | Nov–Jan |
| Bali | Indonesia | $80 | 2.5h | Apr–Oct |
| Tokyo | Japan | $160 | 7h | Mar–May, Oct–Nov |
| Bangkok | Thailand | $70 | 2h | Nov–Feb |
| Hong Kong | China SAR | $140 | 3.5h | Oct–Dec |
| Kuala Lumpur | Malaysia | $90 | 1h | May–Jul |
| Maldives | Maldives | $300 | 4h | Nov–Apr |
| Phuket & Krabi | Thailand | $100 | 2h | Nov–Apr |
| Sydney | Australia | $200 | 8h | Sep–Nov |
| Taipei | Taiwan | $110 | 4.5h | Sep–Nov |
| Hanoi | Vietnam | $60 | 3h | Oct–Apr |

## Project Structure

```
Travel_Class/
├── index.html   # Entire app: HTML + CSS + JS in one file
├── CLAUDE.md    # Codebase guide for Claude Code
└── README.md    # This file
```

## License

For educational and personal use.
