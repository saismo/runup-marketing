# runup-marketing — Claude Code Guide

## What this project is

Static marketing one-pager for **Runup** — a mobile-first flight checklist app for private pilots.
Hosted at `runup.saismo.at`. Built with Astro + Tailwind CSS v4, static output only.

The app itself lives in a separate repo (`/Coding/Checky`). This is a single `index.astro` page.

---

## The product

**Name:** Runup (internal/codebase name: Checky)
**Tagline direction:** "The checklist app pilots trust. Built for the cockpit, synced everywhere."

**What it does:**

- Mobile-first PWA for managing and executing per-aircraft flight checklists
- Covers all 10 standard flight phases: Pre-flight → Engine Start → Taxi → Before Takeoff → Takeoff → Climb → Cruise → Descent → Landing → Shutdown
- Offline-first (works without a connection, syncs when back online)
- Cloud sync across devices via Supabase
- Custom checklists per aircraft (tail number + optional photo)
- CSV import for existing checklists

**Target user:** Private pilots (VFR/IFR), primarily flying singles. Used on iPhone and iPad Mini in the cockpit.

**Pricing:**

- Free tier: single aircraft
- Pro tier: unlimited aircraft (not yet live)

**Demo content:** A pre-loaded Cessna 172S checklist ships with the app so new users understand the workflow immediately.

---

## Safety framing (important)

Runup is a supplementary tool. The official disclaimer:

> "Runup is a supplementary tool only. You, as pilot-in-command, are solely responsible for the safe conduct of each flight and for verifying all checklist items against the official POH/AFM."

**On the marketing page:** Lean into "trusted aide, not a replacement" positioning. Never imply the app substitutes for the POH/AFM. This is both legally important and builds credibility with pilots, who are skeptical by training.

---

## Page sections

Single scrolling one-pager — all content lives in `src/pages/index.astro`:

1. **Hero** — headline, subheadline, CTA button → links to the app
2. **Features** — key differentiators (offline, per-plane, phase structure, sync)
3. **Demo** — placeholder until screenshots or screen recording are ready
4. **Pricing** — Free vs. Pro comparison (no payment integration yet)
5. **CTA** — repeat app link
6. **Footer** — legal note, safety disclaimer, copyright

**Signup:** CTA button links to the app. No embedded auth form — deferred until Pro tier launches.

---

## Design system

### Colors


| Token           | Value     | Use                         |
| --------------- | --------- | --------------------------- |
| Primary blue    | `#026BFE` | Buttons, accents, links     |
| Background      | `#EAEDF8` | Page background             |
| Card background | `#FFFFFF` | White cards                 |
| Divider         | `#dee2ed` | Row separators inside cards |


### Typography

- **Font:** Inter (Variable) — load from Google Fonts or bundle
- Operational and trustworthy feel; no novelty display fonts

### Card shadow

```css
box-shadow:
  0px 2px 10px rgba(53,64,92,0.16),
  0px 0.836px 4.178px rgba(53,64,92,0.12),
  0px 0.447px 2.234px rgba(53,64,92,0.1),
  0px 0.25px 1.252px rgba(53,64,92,0.08),
  0px 0.133px 0.665px rgba(53,64,92,0.06),
  0px 0.055px 0.277px rgba(53,64,92,0.05);
```

### Border radius

Cards and buttons: ~8px

### Icons

Lucide icons (same as app) for visual consistency. Install via `npm install lucide-react` or use SVGs inline.

### Assets available from the app repo

- `../Checky/src/assets/logo.svg` — 84×22px logo
- `../Checky/src/assets/sky.jpg` — sky background image used in the app

---

## Stack

- **Framework:** Astro (minimal template, static output)
- **Styles:** Tailwind CSS v4 via `@tailwindcss/vite`
- **Stylesheet entry:** `src/styles/global.css` — import this in any layout
- **TypeScript:** strict mode
- No SSR, no server endpoints, no subpages — everything lives in `index.astro`

---

## Rules

1. **One page only** — all content in `src/pages/index.astro`, no subpages
2. **Static only** — no SSR, no API routes, no server functions
3. **No embedded auth** — CTA buttons link to the app, no signup form on this site
4. **Mobile-first** — the product's users are on iPhones; the marketing page should look sharp there too
5. **No framework migrations** — do not propose switching away from Astro

---

## Commands

```bash
npm run dev       # local dev server
npm run build     # production build → ./dist/
npm run preview   # preview the production build
```

