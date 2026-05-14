# WILD Landing

Public-facing landing pages for the **WILD Programme** (Wake-Induced Lucid Dreaming).

**Live URL**: https://smith912000.github.io/wild-landing/

## Structure — two-track gateway

The landing is a gateway that splits into two themed tracks (the Linktree is retired — both paths live here).

```
index.html              ← GATEWAY: "Choose your way in" button → reveals two doors
science/
  index.html            ← Oneirology hub (research-grounded track)
  pages/
    landing_page.html       ← primary sales page
    tier1/2/3.html          ← per-tier explanation pages
    community.html          ← community info
    thankyou.html           ← post-signup
    purchase-confirmed.html ← post-purchase
    legal.html              ← privacy + terms
spiritual/
  index.html            ← The Dreaming Path hub (contemplative track)
  pages/
    landing_spiritual.html  ← spiritual sales page
    legal.html              ← privacy + terms (shared copy)
og-image.svg            ← shared social card
```

**Two brands, one programme:**
- **Oneirology** — the science track. Sleep science, metacognition, dream-awareness research. Deliberately avoids "biohacking" / pseudoscience framing. "Oneirology" is the formal academic word for the scientific study of dreams.
- **The Dreaming Path** — the contemplative track. Dream yoga, the witness, conscious awareness.

## What this repo is NOT

- Paid course content (lessons, modules) — lives in private `smith912000/wild-programme`
- Lead magnet PDFs — delivered via Kit email automation, not hosted here
- wild-os app (PWA) — separate `smith912000/wild-os`, deployed at https://smith912000.github.io/wild-os/

## Social accounts — placeholder swap

Both hub pages have a "Socials & more" section with **5 placeholder cards** each (X, Instagram, YouTube, TikTok, Reddit). They're marked:
- `href="#"` and `class="...disabled"` and a `badge-soon` span
- `data-social="science-x"` / `data-social="spiritual-instagram"` etc. — stable hooks for the swap

**To activate a social account once it exists:**
1. Find the `<a>` with the matching `data-social` attribute
2. Replace `href="#"` with the real profile URL
3. Update the `card-title` text with the real handle
4. Remove the `disabled` class and delete the `<span class="card-badge badge-soon">Soon</span>`

See `SOCIAL_ACCOUNTS.md` (in `Negotiorum Master Folder/`) for the full account plan, naming, and creation sequence.

## Whop gating roadmap

Currently both tracks are fully open. When ready to gate:

1. **Buy / subscribe flow** routes through Whop checkout (£47 / £67 / £77 / £13-month)
2. **On purchase, Whop webhook** assigns a role/tier to the buyer
3. **Discord** gets role-synced from Whop
4. **Course portal** (private repo) deployed at a gated path with a Whop SSO check on each page load
5. **wild-os** PWA reads the Whop session to unlock tier-specific features

The course-content links in `purchase-confirmed.html` are currently `href="#" data-course-link="pending-deploy"` — swap these once the gated course portal is live.

## Local dev

Static site — open any HTML file in a browser, or:
```bash
python -m http.server 8000   # then visit http://localhost:8000
```

## Deployment

GitHub Pages, `main` branch root. Any push to `main` redeploys within 1-2 minutes.

## Integrations to wire up

- [ ] **Google Analytics** — replace `G-XXXXXXXXXX` placeholder with real GA4 ID (in all 3 hub files + sub-pages)
- [ ] **Contact email** — replace `CONTACT_EMAIL_PLACEHOLDER` with the new Google Workspace sub-email
- [ ] **Kit (email)** — embed form on both landing pages for lead-magnet capture
- [ ] **Whop** — link buy buttons to live product pages (3 tiers + 1 sub)
- [ ] **Discord invite** — replace placeholder on both community sections
- [ ] **Social accounts** — swap the 10 `data-social` placeholders (5 science + 5 spiritual)

## Encoding note

These files contain emoji. Always edit with UTF-8 **no BOM**. Do NOT use PowerShell `Set-Content -Encoding UTF8` (adds BOM + reads with system codepage = double-encodes emoji). Use `[System.IO.File]::ReadAllText/WriteAllText` with `UTF8Encoding($false)`, or the Edit tool.
