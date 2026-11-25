# GhumoCo

Custom India trip planning: a fast static website, and an optional API for enquiries, free Day 1 previews, payments and WhatsApp replies.

| Folder | What it is |
|---|---|
| `travel-site/` | The website (plain HTML/CSS/JS, no framework), the brand kit (`brand/`), and the build, launch and test tooling. Start with `travel-site/LAUNCH.md`. |
| `travel-backend/` | FastAPI service: leads, AI-drafted previews checked against real plans, PDFs, Razorpay payments, Telegram alerts, WhatsApp Cloud API webhook, leads console. See `travel-backend/README.md`. |
| `.github/workflows/` | CI: backend tests, site tests (end-to-end, accessibility, launch build) and a dependency audit. |

## Quick start
```
cd travel-site
npm install
npm run preview        # builds a preview with placeholder contact details and serves http://localhost:8080
npm test               # needs Playwright's Chromium: npx playwright install chromium
```
Backend: `cd travel-backend`, `pip install -r requirements.txt pytest`, `python -m pytest -q`.

## Going live
1. Fill in your own details (`travel-site/tools/brand.example.json` to `brand.json`, never committed), read the legal pages, set `legal_reviewed`.
2. Deploy the site: `travel-site/DEPLOY-VERCEL.md` (or Cloudflare Pages: `npm run build`, upload `dist/`).
3. Optional later: deploy the API, then set `api_base`.

## Rules this project keeps
- No invented numbers, ratings, traveller counts or "vetted/verified" claims; tests fail if they come back.
- No prices on the site except where a written quote exists.
- Reviews and photos of people only with their written yes.
- Your phone number, address and keys stay out of git (`brand.json`, `.env`, `brand/kit.json` are ignored).
