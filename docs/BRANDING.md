# Branding & Design System — The Tonsorium

Complete visual identity guide for **The Tonsorium** — a modern-classic Latin-inspired barbershop brand.

---

## Brand Overview

**Name:** The Tonsorium
**Etymology:** From Latin *tonsor* — meaning barber, one who cuts hair
**Tagline:** *Precision Cuts. Timeless Ritual.*

### Brand Personality

| Trait | Expression |
|---|---|
| Modern | Clean layouts, contemporary grid systems |
| Classic | Serif headings, heritage-inspired details |
| Masculine | Dark palette, structured composition, confident copy |
| Premium | Generous spacing, gold accents, refined typography |
| Elegant | Restraint over decoration, quality over quantity |
| Timeless | No trendy effects, no dated gimmicks |

### Emotional Direction

The brand should feel like walking into a shop that charges more than average and is worth every cent. Not intimidating — **assured**. Like someone who doesn't need to prove anything.

---

## 1. Color System

### Primary Palette

#### Obsidian Black — `#1A1A1A`

The dominant color. Deep, rich, near-black.

```css
--black: #1A1A1A;
```

Use for: page background · navbar · footer · hero overlay · dark sections · premium surfaces

---

#### Metallic Gold — `#D4AF37`

The accent color. Warm, refined, restrained.

```css
--gold: #D4AF37;
```

Use for: buttons · hover states · pricing text · icon highlights · dividers · borders · active nav states

---

#### Off White — `#F5F5F5`

The contrast color. Soft, readable, premium.

```css
--white: #F5F5F5;
```

Use for: headings · primary body text · light contrast surfaces

---

### Neutral Palette

| Token | Hex | Use |
|---|---|---|
| `--gray-100` | `#e7e7e7` | Soft backgrounds, subtle borders |
| `--gray-300` | `#bdbdbd` | Muted paragraph text |
| `--gray-500` | `#8c8c8c` | Secondary labels, captions |
| `--gray-700` | `#444444` | Dark borders, subtle separators |

### Semantic Tokens

```css
--overlay-dark: rgba(0, 0, 0, 0.65);     /* Hero image overlay */
--border-light: rgba(255, 255, 255, 0.08); /* Subtle section dividers */
--border-gold: rgba(212, 175, 55, 0.28);   /* Card and component borders */
```

### Color Usage Rule: 70 / 20 / 10

| Proportion | Color | Role |
|---|---|---|
| 70% | Black | Dominant background and surface |
| 20% | White + Gray | Text, content, light elements |
| 10% | Gold | Accent, highlight, CTA |

> Gold must never dominate. Its power comes from restraint.

### Color Avoid List

- No neon or fluorescent colors
- No gold backgrounds at large scale
- No colorful shadows or glows
- No random accent colors outside the defined palette

---

## 2. Typography System

### Heading Font: Playfair Display

```css
--font-heading: 'Playfair Display', Georgia, serif;
```

**Tone:** Elegant · Heritage · Premium · Authoritative

Use for: logo · hero headline · section titles · premium pullquotes · callout text

**Google Fonts import:**

```html
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&display=swap" rel="stylesheet">
```

---

### Body Font: Montserrat

```css
--font-body: 'Montserrat', 'Helvetica Neue', sans-serif;
```

**Tone:** Clean · Modern · Geometric · Readable

Use for: nav links · body paragraphs · buttons · pricing · labels · all UI text

**Google Fonts import:**

```html
<link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&display=swap" rel="stylesheet">
```

---

### Typography Hierarchy

| Element | Font | Weight | Size Token | Use |
|---|---|---|---|---|
| `h1` | Playfair Display | 700 | `--fs-hero` | Hero headline only |
| `h2` | Playfair Display | 700 | `--fs-2xl` | Section titles |
| `h3` | Playfair Display | 600 | `--fs-xl` | Card titles, service names |
| `p` | Montserrat | 400 | `--fs-md` | Body text |
| `label` / `nav` | Montserrat | 500 | `--fs-sm` | UI labels, nav links |
| `button` | Montserrat | 700 | `--fs-md` | CTA buttons |
| Eyebrow | Montserrat | 500 | `--fs-xs` | Taglines, categories |

### Font Scale

```css
  --fs-xs:              1.2rem;   /* 12px */
  --fs-sm:              1.4rem;   /* 14px */
  --fs-md:              1.6rem;   /* 16px */
  --fs-lg:              1.8rem;   /* 18px */
  --fs-xl:              2.4rem;   /* 24px */
  --fs-2xl:             3.2rem;   /* 32px */
  --fs-3xl:             4.4rem;   /* 44px */

  --fs-hero:            clamp(3.6rem, 6vw, 6.4rem);

```

### Typography Rules

- **Line height:** Headings `1.2` · Body `1.6`
- **Eyebrow tags:** letter-spacing `2–3px`, uppercase, `--fs-xs`
- **Long paragraphs:** max-width `65ch` for readability
- **Avoid:** centered long paragraphs · all-caps body text · too many font weights on one page

---

## 3. Spacing System

### Scale

```css
  --space-xs:           0.8rem;   /* 8px */
  --space-sm:           1.2rem;   /* 12px */
  --space-md:           2.4rem;   /* 24px */
  --space-lg:           4.8rem;   /* 48px */
  --space-xl:           8rem;     /* 80px */
  --space-2xl:          11.2rem;  /* 112px */
  --space-3xl:          16rem;    /* 160px */
```

### Usage Guide

| Token | Use |
|---|---|
| `--space-xs` | Icon gaps, button icon spacing |
| `--space-sm` | Inline label spacing, tight stacks |
| `--space-md` | Card padding, content gaps, nav spacing |
| `--space-lg` | Grid gaps, section internal spacing |
| `--space-xl` | Section vertical padding |
| `--space-2xl` | Hero breathing room, major breaks |

### Whitespace Philosophy

> Luxury brands use generous spacing. When in doubt — more space, not less.

Cramped layouts signal low confidence. Open layouts signal authority.

---

## 4. Layout System

### Container

```css
.container {
  width: min(1200px, 90%);
  margin: 0 auto;
}
```

### Section Padding

```css
.section {
  padding: var(--space-xl) 0; /* Desktop: ~80px */
}

@media (max-width: 768px) {
  .section {
    padding: var(--space-lg) 0; /* Mobile: ~48px */
  }
}
```

### Grid Systems

**Services Grid**
```css
.services-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Desktop */
  gap: var(--space-md);
}
/* Tablet: 2 columns */
/* Mobile: 1 column */
```

**Gallery Grid**
```css
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* Desktop */
  gap: 1rem;
}
/* Tablet: 2 columns */
/* Mobile: 1 column */
```

**Contact Grid**
```css
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1fr; /* Desktop */
  gap: var(--space-lg);
}
/* Mobile: 1 column */
```

---

## 5. Border Radius

```css
--radius-sm:   6px;
--radius:      10px;
--radius-lg:   18px;
--radius-full: 999px;
```

| Token | Use |
|---|---|
| `--radius-sm` | Small inputs, tight elements |
| `--radius` | Buttons, cards, form fields |
| `--radius-lg` | Gallery items, featured cards |
| `--radius-full` | Pill badges, round tags |

---

## 6. Shadow System

```css
--shadow-sm: 0 6px 20px rgba(0, 0, 0, 0.15);
--shadow-md: 0 12px 30px rgba(0, 0, 0, 0.20);
--shadow-lg: 0 20px 50px rgba(0, 0, 0, 0.35);
```

| Token | Use |
|---|---|
| `--shadow-sm` | Cards at rest |
| `--shadow-md` | Buttons on hover, cards on hover |
| `--shadow-lg` | Hero elements, elevated modals |

### Shadow Rules

- Use shadows to add depth — not decoration
- Never use colored shadows
- Never use glow effects
- Consistent blur per layer: small/medium/large

---

## 7. Motion System

### Timing

```css
--transition-fast: 0.2s ease;
--transition:      0.3s ease;
--transition-slow: 0.45s ease;
```

### Motion Use Cases

| Trigger | Duration | Property |
|---|---|---|
| Button hover | `0.3s ease` | `transform`, `opacity`, `box-shadow` |
| Nav link hover | `0.2s ease` | `color`, `opacity` |
| Card hover | `0.3s ease` | `transform`, `box-shadow` |
| Scroll reveal | `0.45s ease` | `opacity`, `translateY` |
| Mobile menu | `0.3s ease` | `max-height`, `opacity` |

### Motion Rules

- Motion should feel natural, not performative
- `ease` over `linear` for all UI transitions
- Avoid: `bounce`, `elastic`, `spin`
- Never animate layout-affecting properties (width, height) — use `transform` and `opacity` only

---

## 8. Button System

### Primary Button

```css
.btn-primary {
  background: var(--gold);
  color: var(--black);
  font-family: var(--font-body);
  font-weight: 700;
  padding: 0.85rem 1.75rem;
  border-radius: var(--radius);
  border: none;
  transition: var(--transition);
  cursor: pointer;
}

.btn-primary:hover {
  transform: translateY(-2px);
  opacity: 0.92;
  box-shadow: var(--shadow-md);
}

.btn-primary:focus-visible {
  outline: 2px solid var(--gold);
  outline-offset: 3px;
}

.btn-primary:disabled {
  opacity: 0.6;
  pointer-events: none;
  cursor: not-allowed;
}
```

Use for: Book Now · Submit · Main CTA

### Secondary Button

```css
.btn-secondary {
  background: transparent;
  color: var(--white);
  border: 1px solid var(--gold);
  font-family: var(--font-body);
  font-weight: 500;
  padding: 0.85rem 1.75rem;
  border-radius: var(--radius);
  transition: var(--transition);
  cursor: pointer;
}

.btn-secondary:hover {
  background: rgba(212, 175, 55, 0.1);
  transform: translateY(-2px);
}
```

Use for: View Services · Learn More · Secondary actions

---

## 9. Card Component

```css
.card {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid var(--border-gold);
  border-radius: var(--radius);
  padding: var(--space-md);
  transition: var(--transition);
}

.card:hover {
  border-color: rgba(212, 175, 55, 0.5);
  box-shadow: var(--shadow-sm);
  transform: translateY(-3px);
}
```

Use for: service cards · testimonials · feature highlights

---

## 10. Icon Style

- **Style:** Thin line icons (stroke-based SVG)
- **Size:** 20–24px default · 32px for feature icons
- **Color:** `var(--gold)` for decorative · `var(--white)` for functional

Recommended icons:
- `scissors` — services
- `razor` — grooming
- `calendar` — booking
- `phone` — contact
- `map-pin` — location
- `clock` — hours

---

## 11. Navigation Rules

```
Sticky top → z-index: 1000
Background: rgba(26,26,26,0.95) with backdrop-filter: blur(10px)
Border-bottom: 1px solid rgba(212,175,55,0.2)
```

Navbar internal layout: Flexbox · `space-between` · `align-items: center`

Nav link hover: `color: var(--gold)` transition `0.2s ease`

---

## 12. Imagery Style

### Use Photos That Show:
- Sharp haircut detail and clean lines
- Rich contrast, warm lighting
- Confident masculine tone
- Luxury barbershop environment
- Tools and craft

### Avoid:
- Low resolution or over-filtered images
- Generic stock smile photos
- Cluttered, noisy backgrounds
- Cold or clinical lighting

---

## 13. Copywriting Tone

**Voice:** Confident · Premium · Concise · Masculine · Trustworthy

**Avoid:** Clichés · Filler words · Exclamation marks (rare) · Informal slang

### Examples

| ❌ Generic | ✓ The Tonsorium |
|---|---|
| "We cut hair great!" | "Crafted with precision." |
| "Come visit us!" | "Your ritual starts here." |
| "Book an appointment" | "Reserve your session." |
| "We're the best barbers" | "Where tradition meets mastery." |

---

## 14. Accessibility Standards

- Minimum contrast ratio: **4.5:1** for body text (WCAG AA)
- All images have descriptive `alt` text
- Keyboard navigation supported with visible focus states
- Semantic HTML structure (no div-soup)
- Form labels explicitly associated with inputs

---

## Final Brand Rule

> Every section should feel:
> **Clean enough** for modern users.
> **Rich enough** for premium clients.
> **Timeless enough** to trust.