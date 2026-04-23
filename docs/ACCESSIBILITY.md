# Accessibility Guide — The Tonsorium

Accessibility decisions, checklist, and implementation notes for WCAG 2.1 AA compliance.

---

## Why Accessibility Matters

Accessibility is not a bonus feature — it is a baseline requirement for any professional web project.

For The Tonsorium specifically:
- Customers of all abilities should be able to book a haircut
- Screen reader users should be able to navigate and understand every section
- Keyboard-only users should be able to reach all interactive elements

---

## Target Standard

**WCAG 2.1 Level AA** — the industry-standard accessibility requirement for professional websites.

---

## 1. Semantic HTML

Using the correct HTML element is the foundation of accessibility.

### Implementation

```html
<!-- Correct semantic structure -->
<nav class="navbar" aria-label="Main navigation">
<header class="hero">
<main>
  <section id="about" aria-labelledby="about-title">
    <h2 id="about-title">About The Tonsorium</h2>
  </section>
  <section id="services" aria-labelledby="services-title">
    <h2 id="services-title">Our Services</h2>
  </section>
</main>
<footer>
```

### Rules Applied

- ✅ One `<h1>` per page (hero headline)
- ✅ `<nav>` for navigation, not a `<div>`
- ✅ `<header>` for the hero, `<footer>` for the footer
- ✅ `<main>` wraps page content
- ✅ `<section>` elements have accessible names via `aria-labelledby`
- ✅ `<button>` used for actions, `<a>` for navigation

---

## 2. Color Contrast

All text must meet minimum contrast ratios against their backgrounds.

### Contrast Ratios

| Foreground | Background | Ratio | Passes AA |
|---|---|---|---|
| Off White `#F5F5F5` | Obsidian Black `#1A1A1A` | 16.5:1 | ✅ |
| Gray 300 `#bdbdbd` | Obsidian Black `#1A1A1A` | 8.6:1 | ✅ |
| Metallic Gold `#D4AF37` | Obsidian Black `#1A1A1A` | 7.2:1 | ✅ |
| Black `#1A1A1A` | Gold `#D4AF37` | 7.2:1 | ✅ (button text) |
| Gray 500 `#8c8c8c` | Obsidian Black `#1A1A1A` | 4.6:1 | ✅ |

> WCAG AA requires 4.5:1 for normal text, 3:1 for large text (18px+ or bold 14px+).

### Tools Used

- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- Chrome DevTools → Accessibility tab

---

## 3. Keyboard Navigation

All interactive elements must be reachable and operable by keyboard alone.

### Tab Order

The natural DOM order defines tab sequence. Follow this structure:

1. Skip to main content link *(recommended)*
2. Navbar logo
3. Nav links (About, Services, Gallery, Contact)
4. Navbar CTA button (Book Now)
5. Hero CTA buttons
6. Section content (read-only)
7. Contact links (phone, WhatsApp)
8. Footer links

### Focus Styles

Default browser focus outlines are sometimes removed by CSS resets. Explicit focus styles are required:

```css
/* Applied to all interactive elements */
:focus-visible {
  outline: 2px solid var(--gold);
  outline-offset: 3px;
  border-radius: 3px;
}

/* Do NOT use: */
/* *:focus { outline: none; } — this destroys keyboard navigation */
```

### Skip Navigation Link *(recommended)*

```html
<!-- First element in <body> -->
<a href="#main" class="skip-link">Skip to main content</a>
```

```css
.skip-link {
  position: absolute;
  top: -100%;
  left: 1rem;
  background: var(--gold);
  color: var(--black);
  padding: 0.5rem 1rem;
  border-radius: var(--radius);
  font-weight: 700;
  z-index: 9999;
}

.skip-link:focus {
  top: 1rem;
}
```

---

## 4. Images

Every image must have meaningful `alt` text.

### Rules

| Image Type | Alt Text Rule |
|---|---|
| Content image (haircut photo) | Descriptive: `alt="Barber trimming a fade haircut"` |
| Decorative image (background texture) | Empty: `alt=""` |
| Logo image | Brand name: `alt="The Tonsorium logo"` |
| Gallery placeholder | Contextual: `alt="Gallery image placeholder"` |

### Implementation

```html
<!-- Content image -->
<img src="assets/images/gallery/gallery-01.jpg" 
     alt="Sharp fade haircut with clean line up by The Tonsorium barbers">

<!-- Decorative -->
<img src="assets/images/hero/overlay.png" alt="" role="presentation">

<!-- Logo -->
<img src="assets/images/logos/logo-light.png" alt="The Tonsorium">
```

---

## 5. Forms

Contact and booking forms must be fully accessible.

### Checklist

- [ ] Every `<input>` has an associated `<label>` (via `for`/`id`)
- [ ] Required fields marked with `aria-required="true"`
- [ ] Error messages associated with fields via `aria-describedby`
- [ ] Success/error states announced to screen readers via `aria-live`

```html
<div class="form-field">
  <label for="name">Full Name <span aria-label="required">*</span></label>
  <input 
    type="text" 
    id="name" 
    name="name" 
    aria-required="true"
    autocomplete="name"
  >
</div>
```

---

## 6. ARIA Landmarks

ARIA landmark roles help screen reader users navigate page regions:

```html
<nav role="navigation" aria-label="Main">
<header role="banner">
<main role="main">
<footer role="contentinfo">
```

> Note: Semantic HTML5 elements already carry implicit ARIA roles. The above attributes are redundant but harmless — use them for maximum compatibility.

---

## 7. Interactive States

All interactive elements need clear state communication:

```html
<!-- Hamburger menu (future JS) -->
<button 
  class="nav-toggle" 
  aria-expanded="false" 
  aria-controls="nav-menu"
  aria-label="Toggle navigation menu"
>
  <span class="sr-only">Menu</span>
</button>

<ul id="nav-menu" class="nav-links" aria-hidden="true">
  <!-- links -->
</ul>
```

When JS opens the menu, toggle `aria-expanded="true"` and `aria-hidden="false"`.

---

## 8. Screen Reader Utilities

```css
/* Visually hidden but screen-reader accessible */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

Use for: icon-only buttons (add label), skip links when visually hidden, supplementary context.

---

## 9. Motion & Animation

Some users prefer reduced motion (vestibular disorders, epilepsy, preference).

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

---

## 10. Testing Checklist

### Manual Tests

- [ ] Tab through entire page — every interactive element reachable
- [ ] No focus trap outside of intentional modals
- [ ] Skip link appears on first Tab press
- [ ] All images have appropriate alt text
- [ ] Heading hierarchy is logical (H1 → H2 → H3, no skips)
- [ ] Color contrast passes for all text

### Automated Tests

- [ ] Run [axe DevTools](https://www.deque.com/axe/) browser extension
- [ ] Run Lighthouse Accessibility audit (target: 95+)
- [ ] Run [WAVE Web Accessibility Evaluation Tool](https://wave.webaim.org/)

### Screen Reader Tests

- [ ] NVDA + Chrome (Windows)
- [ ] VoiceOver + Safari (macOS / iOS)
- [ ] TalkBack + Chrome (Android)

---

## Current Accessibility Score

| Audit Tool | Score | Date |
|---|---|---|
| Lighthouse | — | *pending* |
| axe DevTools | — | *pending* |
| WAVE | — | *pending* |

---

*The Tonsorium — Accessibility Guide*