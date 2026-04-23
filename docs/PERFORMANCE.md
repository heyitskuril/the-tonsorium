# Performance Guide — The Tonsorium

Performance strategy, optimization checklist, and Lighthouse targets for The Tonsorium landing page.

---

## Performance Goals

| Metric | Target | Why |
|---|---|---|
| Lighthouse Performance | **90+** | Portfolio standard |
| Lighthouse Accessibility | **95+** | Inclusive design |
| Lighthouse SEO | **95+** | Discoverability |
| Lighthouse Best Practices | **95+** | Professional quality |
| First Contentful Paint (FCP) | **< 1.5s** | First impression |
| Largest Contentful Paint (LCP) | **< 2.5s** | WCAG Core Web Vital |
| Cumulative Layout Shift (CLS) | **< 0.1** | Stable layout |
| Total Blocking Time (TBT) | **< 200ms** | Interactivity |

---

## 1. Image Optimization

Images are typically the largest performance bottleneck on landing pages.

### Compression

Run all images through compression before adding to the project:

| Tool | Use Case | Free |
|---|---|---|
| [Squoosh](https://squoosh.app) | Full control, great WebP output | ✅ |
| [TinyPNG](https://tinypng.com) | Quick PNG/JPG compression | ✅ |
| [ImageOptim](https://imageoptim.com) | macOS bulk compression | ✅ |

**Target:** Hero image < 200KB · Gallery images < 80KB each

### Modern Formats

Use WebP for all photos (40–60% smaller than JPEG at same quality):

```html
<picture>
  <source srcset="assets/images/hero/hero-bg.webp" type="image/webp">
  <img src="assets/images/hero/hero-bg.jpg" alt="The Tonsorium barbershop interior" loading="eager">
</picture>
```

### Explicit Dimensions

Always declare `width` and `height` attributes to prevent layout shift (CLS):

```html
<img 
  src="assets/images/gallery/gallery-01.webp" 
  alt="Classic fade haircut"
  width="400" 
  height="400"
  loading="lazy"
>
```

### Lazy Loading

Apply `loading="lazy"` to all images below the fold:

```html
<!-- Hero image: loading="eager" (above fold) -->
<img src="hero-bg.webp" loading="eager" alt="...">

<!-- All other images: loading="lazy" -->
<img src="gallery-01.webp" loading="lazy" alt="...">
```

---

## 2. Font Loading

Google Fonts can block rendering if loaded incorrectly.

### Optimized Font Import

```html
<head>
  <!-- Preconnect to Google Fonts servers -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  
  <!-- Load fonts with display=swap to prevent FOIT -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Montserrat:wght@400;500;700&display=swap" rel="stylesheet">
</head>
```

### Font Fallback Stack

Defined in CSS variables — ensures readable text even before fonts load:

```css
--font-heading: 'Playfair Display', Georgia, 'Times New Roman', serif;
--font-body: 'Montserrat', 'Helvetica Neue', Arial, sans-serif;
```

### Load Only What You Use

Only load the exact weights needed:
- Playfair Display: `400`, `700`
- Montserrat: `400`, `500`, `700`

Do not load entire font families.

---

## 3. CSS Optimization

### Avoid Render-Blocking CSS

The main stylesheet is linked in `<head>` — this is correct. No CSS should be loaded via JavaScript.

### CSS Variable Benefits

Design tokens defined once in `:root` reduce redundant declarations throughout the stylesheet, keeping file size lean.

### Unused CSS

Before launch, audit for and remove:
- Unused class declarations
- Commented-out blocks
- Duplicate property declarations

Tool: Chrome DevTools → Coverage tab

### Critical CSS *(Advanced, Optional)*

For maximum performance, inline the CSS required for above-the-fold content directly in `<head>`:

```html
<head>
  <style>
    /* Inlined critical CSS here: reset, variables, navbar, hero */
  </style>
  <link rel="stylesheet" href="styles/index.css" media="print" onload="this.media='all'">
</head>
```

---

## 4. HTML Optimization

### Minimize HTTP Requests

The Tonsorium target: **≤ 5 requests** on initial load:
1. `index.html`
2. `styles/index.css`
3. Google Fonts CSS
4. Playfair Display font file
5. Montserrat font file

### Defer Non-Critical Scripts

When JavaScript is added:

```html
<!-- At end of <body> or with defer -->
<script src="scripts/main.js" defer></script>
```

Never place `<script>` tags without `defer` or `async` in `<head>`.

---

## 5. Hosting & CDN

### CDN Benefits

Serving from a CDN reduces latency for global users. All recommended hosting platforms (Netlify, Vercel, Cloudflare Pages) include CDN automatically.

### Gzip / Brotli Compression

All recommended platforms compress text assets automatically. No configuration needed.

### HTTP/2

All recommended platforms serve over HTTP/2 automatically, enabling multiplexed requests.

---

## 6. Core Web Vitals

### Largest Contentful Paint (LCP)

The hero image or headline is likely the LCP element.

Optimization:
- Preload the hero background image

```html
<head>
  <link rel="preload" as="image" href="assets/images/hero/hero-bg.webp">
</head>
```

### Cumulative Layout Shift (CLS)

Caused by: images without dimensions, fonts swapping, late-loading elements shifting content.

Prevention:
- Always declare `width` and `height` on images
- Use `font-display: swap` with fallback fonts that closely match loaded fonts
- Reserve space for dynamic elements

### First Input Delay / Interaction to Next Paint (INP)

Not applicable until JavaScript is added. When JS is introduced:
- Keep event listeners lightweight
- Debounce scroll and resize handlers
- Use `requestAnimationFrame` for visual updates

---

## 7. Performance Audit Process

### How to Run Lighthouse

1. Open the deployed site in Chrome
2. Open DevTools (F12)
3. Go to **Lighthouse** tab
4. Check: Performance, Accessibility, Best Practices, SEO
5. Device: run both Mobile and Desktop
6. Click **Analyze page load**

### How to Interpret Results

| Score | Rating | Action |
|---|---|---|
| 90–100 | Green / Good | Ship it |
| 50–89 | Orange / Needs Improvement | Optimize before launch |
| 0–49 | Red / Poor | Do not launch |

### Other Tools

| Tool | URL | Use |
|---|---|---|
| PageSpeed Insights | [pagespeed.web.dev](https://pagespeed.web.dev) | Production URL testing |
| WebPageTest | [webpagetest.org](https://webpagetest.org) | Detailed waterfall analysis |
| GTmetrix | [gtmetrix.com](https://gtmetrix.com) | Alternative scoring |

---

## 8. Performance Log

Track Lighthouse scores over time:

| Version | LCP | CLS | TBT | Performance | Date |
|---|---|---|---|---|---|
| v0.5.0 | — | — | — | — | *pending* |
| v1.0.0 | — | — | — | — | *pending* |

---

*The Tonsorium — Performance Guide*