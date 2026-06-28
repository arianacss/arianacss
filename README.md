


# ArianaCSS

**A modern, lightweight, pure CSS framework. ~15KB. No JavaScript. Mobile-first. Accessible.**

---

## Quick Start

Download `ariana.min.css` from the `dist/` folder and include it in your HTML:

```html
<link rel="stylesheet" href="path/to/ariana.min.css">
```

---

Hello World

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ArianaCSS</title>
  <link rel="stylesheet" href="ariana.min.css">
</head>
<body>
  <div class="ar-container">
    <h1>Hello, ArianaCSS!</h1>
    <button class="ar-btn ar-btn--primary">Get Started</button>
  </div>
</body>
</html>
```

---

Why ArianaCSS?

Feature ArianaCSS
Pure CSS ✅
No JavaScript ✅
No build tools ✅
Components + Utilities ✅
Mobile-first ✅
Accessible (WCAG AA) ✅
RTL ready ✅
~15 KB gzipped ✅

---

Framework Structure

```
arianacss/
├── src/
│   ├── 1-tokens/       # Single source of truth (147 tokens)
│   ├── 2-base/         # Reset, base, focus, motion
│   ├── 3-layout/       # Container + 12-column grid
│   ├── 4-typography/   # Type scale + prose utilities
│   ├── 5-utilities/    # 1,200+ utility classes
│   └── 6-components/   # Button, card, alert, input, indicators
└── dist/
    ├── ariana.min.css          # Full framework
    ├── ariana-core.min.css     # Components only
    └── ariana-utilities.min.css # Utilities only
```

---

Components

Button

Primary interactive element. 7 variants, 3 sizes, all states.

```html
<button class="ar-btn ar-btn--primary">Primary</button>
<button class="ar-btn ar-btn--secondary">Secondary</button>
<button class="ar-btn ar-btn--ghost">Ghost</button>
<button class="ar-btn ar-btn--danger">Danger</button>
```

Card

Versatile container. Optional header, body, footer, media.

```html
<div class="ar-card">
  <div class="ar-card__header">
    <h3 class="ar-card__title">Card Title</h3>
  </div>
  <div class="ar-card__body">
    <p>Card content goes here.</p>
  </div>
  <div class="ar-card__footer">
    <button class="ar-btn ar-btn--primary">Action</button>
  </div>
</div>
```

Alert

Contextual feedback. 5 color variants, filled, dismissible.

```html
<div class="ar-alert ar-alert--success" role="alert">
  Your changes have been saved.
</div>
```

Badge

Small status labels. Surface, filled, outline, dot.

```html
<span class="ar-badge ar-badge--primary">New</span>
<span class="ar-badge ar-badge--success ar-badge--pill">Active</span>
```

Avatar

User/entity avatars. Images, initials, 6 sizes, groups.

```html
<div class="ar-avatar ar-avatar--initials ar-avatar--primary">
  <span>JD</span>
</div>
```

Input

Form inputs. Text, email, password, number, textarea.

```html
<div class="ar-field">
  <label class="ar-label" for="email">Email</label>
  <input class="ar-input" type="email" id="email" placeholder="you@example.com">
</div>
```

---

Utilities

Spacing

Margin, padding, gap. 17 steps from 0 to 96px.

```html
<div class="ar-mt-4">Margin top 16px</div>
<div class="ar-p-4">Padding 16px all sides</div>
<div class="ar-mx-auto">Horizontally centered</div>
```

Display

Show/hide, responsive variants, sr-only.

```html
<div class="ar-hidden ar-md:flex">Visible on tablet+</div>
<div class="ar-flex ar-md:hidden">Visible on mobile only</div>
```

Flexbox

Complete flex system. Direction, alignment, grow/shrink.

```html
<div class="ar-flex ar-flex-row ar-justify-between ar-items-center">
  <span>Left</span>
  <span>Center</span>
  <span>Right</span>
</div>
```

Grid

Custom grid layouts. 1, 2, 3, 4, 6, 12 columns.

```html
<div class="ar-grid ar-grid-cols-3 ar-gap-4">
  <div>Column 1</div>
  <div>Column 2</div>
  <div>Column 3</div>
</div>
```

Typography

Font size, weight, alignment, color, transforms.

```html
<p class="ar-text-lg ar-font-bold ar-text-center">Large bold centered text</p>
<p class="ar-text-muted">Muted text</p>
<p class="ar-text-primary">Primary color text</p>
```

Border

Border presence, sides, colors, radius.

```html
<div class="ar-border ar-border-primary ar-rounded-lg">Bordered card</div>
<img class="ar-rounded-full" src="avatar.jpg" alt="Avatar">
```

Shadow

6 elevation levels. Resting, hover, floating, modal.

```html
<div class="ar-shadow-1">Resting card</div>
<div class="ar-shadow-4">Modal dialog</div>
```

Ratio

Aspect ratios. Square, video, photo, portrait, wide, golden.

```html
<div class="ar-ratio-video">16:9 video container</div>
<div class="ar-ratio-square">1:1 square container</div>
```

---

Grid System

12-column CSS Grid layout. Mobile-first, responsive.

```html
<div class="ar-container">
  <div class="ar-grid">
    <!-- Full on mobile, half on tablet, third on desktop -->
    <div class="ar-col-12 ar-md:col-6 ar-lg:col-4">Column 1</div>
    <div class="ar-col-12 ar-md:col-6 ar-lg:col-4">Column 2</div>
    <div class="ar-col-12 ar-md:col-6 ar-lg:col-4">Column 3</div>
  </div>
</div>
```

Layout Patterns

```html
<!-- Sidebar + content -->
<div class="ar-layout-sidebar-left">
  <nav>Sidebar</nav>
  <main>Content</main>
</div>

<!-- 3-column equal grid -->
<div class="ar-layout-thirds">
  <div>1/3</div>
  <div>1/3</div>
  <div>1/3</div>
</div>
```

---

Typography

Semantic headings, pattern classes, display, lead, eyebrow.

```html
<!-- Heading elements (no classes needed) -->
<h1>This is an h1 heading</h1>
<h2>This is an h2 heading</h2>

<!-- Pattern classes (semantic vs visual) -->
<h2 class="ar-h4">This h2 looks like an h4</h2>
<p class="ar-h3">A paragraph that looks like an h3</p>

<!-- Display heading -->
<h1 class="ar-display">Building the Future</h1>

<!-- Lead paragraph -->
<p class="ar-lead">Introductory paragraph.</p>

<!-- Eyebrow label -->
<p class="ar-eyebrow">New Feature</p>
```

---

Breakpoints

Prefix Value Device
sm: 480px Standard phone
md: 768px Tablet
lg: 1024px Laptop
xl: 1280px Wide desktop

```html
<div class="ar-hidden ar-md:flex">Visible on tablet+</div>
<div class="ar-text-base ar-lg:text-xl">Responsive text</div>
```

---

Theming

Override CSS custom properties in your stylesheet:

```css
:root {
  /* Change primary color */
  --ar-lapis-600: hsl(280, 70%, 46%);
  --ar-lapis-700: hsl(280, 75%, 38%);
  
  /* Change spacing scale */
  --ar-space-4: 1.5rem;
}
```

---

Browser Support

Browser Version
Chrome / Edge 90+
Firefox 90+
Safari 14+
Mobile Safari 14+
Chrome for Android 90+

---

License

MIT License. See LICENSE for details.

---

Built With ❤️ in Afghanistan

ArianaCSS is a university design systems project. Open source. Free to use. Free to modify.

---

ArianaCSS v1.0.0 — Ship less. Ship right. Ship on time.

```
