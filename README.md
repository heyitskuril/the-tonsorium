# The Tonsorium

> *Precision Cuts. Timeless Ritual.*

A premium, responsive landing page for a modern-classic Latin-inspired barbershop brand — built as a professional frontend learning project using pure HTML5 and CSS3.

---

## Overview

**The Tonsorium** is a portfolio-grade frontend project designed to simulate a real-world client deliverable. It focuses on semantic HTML architecture, scalable CSS systems, responsive design, and a polished visual identity.

The name *Tonsorium* is derived from Latin: *tonsor* (barber) — a nod to the ancient tradition of the craft.

---

## Project Goals

- Practice semantic, accessible HTML5 structure
- Build a maintainable CSS architecture using custom properties (variables)
- Apply CSS Grid and Flexbox for modern layout systems
- Implement a consistent design system (colors, typography, spacing, shadows)
- Deliver a mobile-first responsive experience
- Prepare a scalable foundation for future JavaScript enhancements
- Create a portfolio-quality project demonstrating professional frontend workflow

---

## Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 |
| Typography | Google Fonts — Playfair Display + Montserrat |
| Icons | SVG (custom minimal line icons) |
| Scripts | Vanilla JS |

> No frameworks. No build tools. No dependencies. Pure web standards.

---

## Folder Structure

```
the-tonsorium/
│
├── index.html               # Main entry point
├── README.md                # Project overview (this file)
├── TODO.md                  # Development roadmap
│
├── assets/
│   ├── images/
│   │   ├── hero/            # Hero background images
│   │   ├── gallery/         # Haircut + atmosphere gallery
│   │   ├── about/           # Barber / shop photos
│   │   ├── logos/           # Light + dark logo variants
│   │   └── placeholders/    # Development placeholder
│   └── icons/               # SVG icon set
│
├── styles/
│   ├── index.css            # Main stylesheet (imports all partials)
│   ├── reset.css            # CSS normalization
│   ├── variables.css        # Design token definitions
│   ├── layout.css           # Container + grid systems
│   ├── components.css       # Reusable UI components
│   └── responsive.css       # Breakpoint overrides
│
├── scripts/
│   ├── main.js              # Entry point (future)
│   ├── navbar.js            # Hamburger + sticky scroll (future)
│   ├── modal.js             # Booking modal (future)
│   └── gallery.js           # Lightbox + filters (future)
│
└── docs/
    ├── branding.md          # Full design system
    ├── changelog.md         # Version history
    ├── accessibility.md     # A11y checklist + decisions
    ├── performance.md       # Performance strategy
    ├── roadmap.md           # Future feature roadmap
    ├── screenshots/         # Final desktop/tablet/mobile
    ├── progress/            # Section-by-section progress shots
    └── wireframes/          # Layout planning sketches
```

---

## Brand Identity

### Color Palette

| Name | Hex | Role |
|---|---|---|
| Obsidian Black | `#1A1A1A` | Background, navbar, footer |
| Metallic Gold | `#D4AF37` | Accents, CTAs, highlights |
| Off White | `#F5F5F5` | Headings, body text |
| Gray 300 | `#bdbdbd` | Muted paragraph text |
| Gray 700 | `#444444` | Dark borders, separators |

**Color Ratio:** 70% Black · 20% White/Gray · 10% Gold

### Typography

| Role | Font | Usage |
|---|---|---|
| Headings | Playfair Display | Logo, hero, section titles |
| Body | Montserrat | Nav, paragraphs, buttons, UI |

### Design Personality

> Modern · Classic · Masculine · Premium · Elegant · Timeless

---

## Page Sections

1. **Navbar** — Sticky, premium, minimal with brand logo + CTA
2. **Hero** — Full-height with headline, tagline, and booking CTA
3. **About** — Brand story and philosophy (two-column layout)
4. **Services** — 6 service cards in a responsive grid with pricing
5. **Gallery** — 6-image responsive grid with hover effects
6. **Contact** — Address, hours, phone, WhatsApp CTA, optional map
7. **Footer** — Brand name, slogan, links, social, copyright

---

## Responsive Strategy

| Breakpoint | Layout |
|---|---|
| `> 1024px` | Full desktop — multi-column grids, 1200px container |
| `768px–1024px` | Tablet — 2-column grids, reduced spacing |
| `< 768px` | Mobile — single column stack, centered CTAs |
| `< 480px` | Small mobile — larger tap targets, reduced font scale |

Mobile-first approach: base styles target mobile, enhanced with `min-width` breakpoints.
