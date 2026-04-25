# Changelog — The Tonsorium

All notable changes to this project are documented in this file.

Follows [Semantic Versioning](https://semver.org/): `MAJOR.MINOR.PATCH`
Format inspired by [Keep a Changelog](https://keepachangelog.com/).

---

## [v0.4.5] — CSS Audit & Bug Fixes

### Summary
Full audit of all CSS files against HTML structure. Fixed 5 bugs and 1 missing style
that would have caused visual and behavioral inconsistencies across sections.

### Fixed

#### reset.css
- Removed `line-height: 1.6` from `body` — design tokens belong in `components.css`, not reset

#### components.css
- **Button hover bug** — `.button:hover { background: var(--gold-light) }` was applying to ALL
  button variants. Moved to `.button--primary:hover` only, preventing override of WhatsApp
  and secondary buttons
- **Secondary button invalid CSS** — `box-shadow: var(--white-pure)` used a color token as a
  shadow value (invalid). Replaced with correct transparent + gold border style per `branding.md`
- **Button missing font-family** — `.button` base had no `font-family`, relying on accidental
  inheritance. Added `font-family: var(--font-body)` explicitly
- **`.hero__eyebrow` missing** — class present in HTML but had zero CSS. Added full styling
- **Navbar logo gap wrong token** — `gap: var(--ls-widest)` used a letter-spacing value (`0.25em`)
  as a gap. Replaced with `gap: var(--space-xs)`

---

## [v0.4.0] — Phase 5–13 CSS Complete

### Summary
Full visual styling for all remaining sections: About, Services, Gallery, Contact, and Footer.
CSS split cleanly into `layout.css`, `components.css`, and `responsive.css`.

### Added

#### Shared

- `.eyebrow` component — gold uppercase label with decorative horizontal rule,
  used consistently across About, Services, Gallery, and Contact sections

#### About (Phase 5)

- Two-column grid layout (text + image)
- `about__image-placeholder` with `aspect-ratio: 4/5`, gold border, hover zoom
- `about__image-accent` — decorative offset box behind photo
- Responsive: single column on mobile, photo stacked above text

#### Services (Phase 6)

- 3-column card grid with `card--service` component
- Service cards: dark surface, gold shimmer `::before` line on hover, lift animation
- `card__footer` with price (gold) and duration (muted gray), separated by border
- Responsive: 2-column tablet → 1-column mobile

#### Gallery (Phase 7)

- 3-column CSS Grid with `gallery__item--tall` spanning 2 rows
- Hover: image zoom + caption slide-up from bottom
- Responsive: 2-column tablet → 1-column mobile, tall items flattened

#### Contact (Phase 8)

- Two-column layout: info column + hours column
- `button--whatsapp` — green WhatsApp button with matching glow shadow
- `hours__list` — table with gold time values, hover row highlight, closed day muted
- Google Maps embed with grayscale filter, color on hover

#### Footer (Phase 9)

- 3-column grid: brand · quick links · social
- Footer social links with `→` arrow animation on hover
- Bottom bar with copyright + credits, separated by border

#### Responsive (Phase 13)

- All sections covered across `1024px`, `768px`, `480px` breakpoints
- Restructured `responsive.css`: sections ordered top → bottom within each breakpoint block

---

## [v0.3.5] — Hero Background & Responsive Polish

### Summary
Added background image overlay and responsive improvements for the hero section.

### Added

#### Hero
- Background image overlay with directional gradient
- Responsive adjustments for better visual on all devices

---

## [v0.3.0] — Phase 3 & 4 Navbar and Hero Styling

### Summary
Basic styling and layout structure for Navbar and Hero Section. Hamburger menu structure
prepared for future JavaScript implementation.

### Added

#### Navbar
- Logo / brand text: The Tonsorium
- Navigation links: About, Services, Gallery, Contact
- CTA booking button with gold background
- Sticky position
- Smooth hover states
- Active link underline style
- Spacing alignment
- Hamburger toggle structure (JS pending)

#### Hero
- Eyebrow tagline
- Premium headline with gold accent
- Supporting paragraph
- Primary and secondary CTA buttons
- Centered layout with premium spacing

---

## [v0.2.0] — HTML Structure Complete

### Summary
Full semantic HTML skeleton built. No styles applied, structure only.

### Added
- HTML5 boilerplate: `<!DOCTYPE html>`, `lang="en"`, charset, viewport meta tags
- Page `<title>`: *"The Tonsorium — Precision Cuts. Timeless Ritual."*
- `<link>` for `styles/index.css`
- Google Fonts import: Playfair Display (400, 700) + Montserrat (400, 500, 700)
- Semantic layout: `<nav>`, `<header>`, `<main>`, all `<section>` blocks, `<footer>`
- All section `id` attributes for anchor navigation
- `.container` wrapper divs within each section
- HTML comments marking section boundaries for readability

### Notes
- Deliberate choice: build the full skeleton first, style second
- Avoids early over-styling of incomplete structure

---

## [v0.1.0] — Project Initialized

### Summary
Project scaffolded. All folders, core files, and documentation structure created.

### Added
- Root project folder: `the-tonsorium/`
- `index.html` — empty HTML entry point
- `README.md` — project overview stub
- `TODO.md` — full development roadmap (20 phases)
- `styles/index.css` — empty main stylesheet
- `assets/` directory (empty, structure prepared)
- `docs/` directory
- `docs/branding.md` — complete design system and visual identity guide
- `docs/changelog.md` — this file
- `docs/screenshots/` — empty, reserved for final screenshots
- `docs/progress/` — empty, reserved for section-by-section progress shots
- `docs/wireframes/` — empty, reserved for layout planning assets
- `scripts/` — empty, reserved for future JavaScript files

### Notes
- Git repository initialized with initial commit
- `.gitignore` added (excludes `.DS_Store`, `node_modules/`, `*.env`)

---

*The Tonsorium — Changelog*