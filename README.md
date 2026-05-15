# Travel Guide — Singapore Explorer

A single-page travel guide web app for Singapore-based travellers exploring 12 Asian destinations.

## Features
- City guides with 7-tab modal detail (overview, itinerary, food, transport, costs, safety, photo spots)
- Budget calculator, packing checklist, itinerary planner, currency converter
- Weather widget (requires OpenWeatherMap API key — see CLAUDE.md)
- Enquiry form with localStorage persistence

## Tech Stack
Plain HTML / CSS / JavaScript — no build step, no dependencies.

## Run Locally
```bash
python -m http.server 3000
# open http://localhost:3000
```

## Deploy
GitHub Pages — push to `main`; the `gh-pages.yml` workflow publishes automatically.

## Images
All images are served from Unsplash CDN. No assets are stored in this repo.

## License
MIT
