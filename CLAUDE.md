# KRT Digital — Project Guide

## What is this?
Corporate website for KRT Digital (Joost Kaart) — interim, fractional, and freelance management/strategy in Digital Marketing & E-commerce. Dutch language. **"Sovereign Editorial"** design aesthetic: deep Midnight Navy canvas with luminous Champagne Gold accents, tonal layering instead of borders, generous whitespace. The full design spec lives in `DESIGN.md` at the repo root.

## Tech stack
- **Astro 5** static site generator
- **Tailwind CSS v4** via `@tailwindcss/vite` plugin (NOT the Astro integration)
- **@astrojs/sitemap** for sitemap.xml
- **Netlify** hosting with auto-deploy from GitHub `main` branch
- **Node.js v22** — requires `source ~/.nvm/nvm.sh` before running commands

## Commands
```bash
npm run dev      # Dev server (default port 4321)
npm run build    # Build to dist/
npm run preview  # Preview production build
netlify deploy --prod  # Manual deploy (auto-deploy is also active)
```

## Project structure
```
src/
├── pages/           # Routes (index, diensten, over-mij, contact, contact/bedankt, 404)
├── components/      # Header, Footer, Logo, CTASection, SEOHead
├── layouts/         # BaseLayout (wraps all pages)
└── styles/          # global.css (theme, fonts, base styles, utilities)
public/
├── joost-kaart.jpeg # Professional headshot
├── krt-logo.png     # Logo used in Header/Footer (via Logo.astro)
├── favicon.ico + favicon-16/32/192/512.png, apple-touch-icon.png # KRT logo-mark favicons (generated from public/krt-logo.png)
└── robots.txt
```
- `Logo.astro` accepts an `imgClass` prop to size the logo per placement (header uses `h-16 md:h-20`; footer uses the default `h-10`).

## Design system
Theme tokens, fonts, and utilities are all defined in `src/styles/global.css` via Tailwind v4's `@theme`. See `DESIGN.md` for the full rationale and rules.

### Fonts (Power & Grace pairing)
- **Display & headings:** Space Grotesk — `--font-display`. Tight tracking (`-0.02em`).
- **Body & narrative:** Newsreader (serif) — `--font-serif`. This is the `<body>` default.
- **Labels & nav:** Manrope — `--font-label`. Used for micro-labels, metadata, buttons.

### Colors
| Token | Value | Usage |
|-------|-------|-------|
| `primary` | `#e6c185` | Champagne Gold — CTAs, accents, active states |
| `primary-container` | `#c5a36a` | Darker gold, bottom of button gradient |
| `on-primary` | `#422c00` | Text on gold buttons |
| `surface` | `#0e141d` | Midnight Navy — page background |
| `surface-low` | `#161c25` | Alternate/recessed sections |
| `surface-mid` | `#1b2230` | — |
| `surface-high` | `#242a34` | Lifted cards |
| `surface-highest` | `#2f353f` | Highest layer / glass base |
| `on-surface` | `#dde2f0` | Primary text (never pure `#ffffff`) |
| `on-surface-variant` | `#9da3b0` | Secondary text |
| `on-surface-muted` | `#6b7280` | Labels, tertiary text |
| `outline-variant` | `#4e463a` | Ghost borders (inputs only) |

### Patterns & utilities
- **The No-Line Rule:** no `1px solid` borders for sectioning. Separate content with tonal shifts (`surface-low` vs `surface`) or lifted cards. (Two legacy exceptions remain: old `index-v*.astro` and the Footer copyright bar.)
- **Micro-labels:** `font-[var(--font-label)] text-[0.6875rem] uppercase tracking-[0.25em] text-on-surface-muted font-medium`
- **Section spacing:** `py-24 md:py-32`
- **Container:** `max-w-[var(--container-max)] mx-auto px-8 md:px-12` (`--container-max` = 80rem)
- **Asymmetric grids:** 12-column with offset splits (e.g. `md:col-span-6` + `md:col-start-9`)
- **`.card`:** lifted surface — pair with `bg-surface-high`/`bg-surface-low rounded-[0.25rem]` + `hover:-translate-y-1`. Depth via ambient shadow + subtle gold hover ring.
- **`.btn-primary`:** gold gradient (135deg) button. **`.btn-ghost`:** transparent w/ ghost border.
- **`.glass`:** glassmorphism (backdrop-blur) — used by the fixed Header nav.
- **`.field-underline`:** ghost bottom-border for inputs; transitions to gold on `:focus`.

### SVG illustrations
All illustrations are inline SVGs (no external files). They use:
- The theme palette — gold `#e6c185` and light `#dde2f0`
- Very low opacity for backgrounds (`opacity-[0.04]` to `opacity-[0.06]`)
- Refined line weights (0.5–2px strokes)

> Note: the headshot (`/joost-kaart.jpeg`) is a bright/light-background portrait, integrated into the navy via a gradient scrim + reduced brightness on the homepage hero and over-mij. A darker studio portrait would integrate more naturally.

## Key details
- **Domain:** krtdigital.nl (DNS via Strato, hosting via Netlify)
- **Email:** info@krtdigital.nl (via Strato mail — MX records must not change)
- **KvK:** 80708293
- **Contact form:** Netlify Forms (`data-netlify="true"`, honeypot spam filter)
- **GA4:** Placeholder `G-XXXXXXXXXX` in SEOHead.astro — needs real ID
- **JSON-LD:** Structured data in SEOHead (ProfessionalService, Person, Service, ContactPage)
- **GitHub:** github.com/joostkaart/krt-digital (public repo)

## Deployment
Push to `main` → Netlify auto-builds and deploys. SSL is automatic.
Manual deploy: `npm run build && netlify deploy --prod`

## Content notes
- All content is in Dutch
- Bio text on over-mij page is placeholder — needs personalization
- Client logos (NS, Sunweb, Pricewise) are text-only, no actual logos yet
