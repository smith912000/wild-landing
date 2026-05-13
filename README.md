# WILD Landing

Public-facing landing pages for the **WILD Programme** (Wake-Induced Lucid Dreaming).

**Live URL**: https://smith912000.github.io/wild-landing/

## What this repo is

Public marketing surface only:
- `index.html` — main landing hub
- `pages/landing_page.html` — primary sales page
- `pages/landing_spiritual.html` — alternative angle for spiritual audience
- `pages/tier1.html` `tier2.html` `tier3.html` — per-tier explanation pages
- `pages/community.html` — Discord community info
- `pages/thankyou.html` — post-signup confirmation
- `pages/purchase-confirmed.html` — post-purchase confirmation
- `pages/legal.html` — privacy + terms

## What this repo is NOT

- Paid course content (lessons, modules) — lives in private `smith912000/wild-programme`
- Lead magnet PDFs — delivered via Kit email automation, not hosted here
- wild-os app (PWA) — separate `smith912000/wild-os` (to be deployed)

## Whop gating roadmap

Currently the landing pages are open. When ready to gate:

1. **Buy / subscribe flow** routes through Whop checkout (£47 / £67 / £77 / £13-month)
2. **On purchase, Whop webhook** assigns a role/tier to the buyer
3. **Discord** gets role-synced from Whop
4. **Course portal** (private repo) deployed at a gated subdomain (e.g. `course.wildprogramme.com`) with Whop SSO check on each page load
5. **wild-os** PWA reads the Whop session to unlock tier-specific features

Until then, only the landing pages here are public. Course content stays in the private repo and is **never** pushed to a public deploy.

## Local dev

Static site — open any HTML file directly in a browser or run:

` bash
python -m http.server 8000
# then visit http://localhost:8000
`

## Deployment

GitHub Pages, `main` branch root. Any push to `main` redeploys within 1-2 minutes.

## Integrations to wire up

- [ ] **Google Analytics** — replace `G-XXXXXXXXXX` placeholder with real GA4 measurement ID
- [ ] **Kit (email)** — embed form on landing pages for lead magnet capture
- [ ] **Whop** — link buy buttons to live product pages (3 tiers + 1 sub)
- [ ] **Discord invite** — replace placeholder invite link on community page