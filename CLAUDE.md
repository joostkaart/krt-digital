# KRT Digital — Project Guide

## What is this?
Corporate website for KRT Digital (Joost Kaart) — interim, fractional, and freelance management/strategy in Digital Marketing & E-commerce. Dutch language. Editorial/magazine design aesthetic.

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
└── styles/          # global.css (theme, fonts, base styles)
public/
├── joost-kaart.jpeg # Professional headshot
├── favicon.svg      # KRT logo favicon
└── robots.txt
```

## Design system

### Fonts
- **Headings:** DM Serif Display (weight 400, line-height 1.15)
- **Body:** Inter (weights 300–600, line-height 1.7)

### Colors
| Token | Value | Usage |
|-------|-------|-------|
| `navy` | `#0f1923` | Primary dark, footer bg, dark sections |
| `accent` | `#d4622a` | Orange CTA, highlights, hover states |
| `text` | `#1a1a1a` | Body text |
| `text-light` | `#555555` | Secondary text |
| `text-lighter` | `#999999` | Tertiary, labels |
| `bg` | `#fefefe` | Page background |
| `bg-alt` | `#f7f5f2` | Alternate section background |
| `border` | `#e0dcd5` | Dividers, borders |

Teal variant available via `.theme-teal` on `<html>` (accent becomes `#0ea5a0`).

### Editorial patterns
- **Micro-labels:** `text-[11px] uppercase tracking-[0.25em] font-sans font-medium`
- **Section spacing:** `py-24 md:py-32`
- **Container:** `max-w-[80rem] mx-auto px-8 md:px-12`
- **Asymmetric grids:** 12-column with 4/7, 3/9, 5/7 splits
- **Expanding-line CTA:** border-bottom that grows on hover via `after:` pseudo-element
- **Numbered lists:** Large serif numbers with editorial dividers

### SVG illustrations
All illustrations are inline SVGs (no external files). They use:
- Existing color palette (`#0f1923`, `#d4622a`)
- Very low opacity for backgrounds (`opacity-[0.04]` to `opacity-[0.06]`)
- Refined line weights (0.5–2px strokes)

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
