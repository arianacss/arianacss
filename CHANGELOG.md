# Changelog

All notable changes to ArianaCSS will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2026-06-28

### Added

#### Framework Foundation
- **Complete token system** (`tokens.css`) with 147 tokens across 17 sections:
  - 25 color primitives (5 hues × 5 stops)
  - Semantic color roles (primary, success, warning, danger, info, layer, text, state, border)
  - Typography scale (10 sizes, 6 line heights, 5 tracking values, 5 weights)
  - Spacing scale (17 steps from 0 to 96px)
  - Border radius scale (6 steps)
  - Shadow system (6 levels with multi-layer shadows)
  - Motion system (3 durations, 3 easing curves)
  - Focus ring system (3px ring, 2px offset, 3 color variants)
  - Z-index system (7 named layers)
  - Layout tokens (container widths, grid configuration)

#### Base Layer
- **reset.css**: Targeted browser normalization (no token references)
- **motion.css**: `prefers-reduced-motion` global override for accessibility
- **base.css**: Document foundation (font stack, body styles, link styles, scrollbar styling)
- **focus.css**: `:focus-visible` ring system with three color variants (default, danger, success)

#### Layout Layer
- **container.css**: Responsive container with max-widths at all breakpoints
- **grid.css**: 12-column CSS Grid layout system with:
  - Column spans (1-12) at all breakpoints
  - Gap variants (sm, lg)
  - 7 pre-composed layout patterns (sidebar-left, thirds, quarters, etc.)

#### Typography Layer
- **scale.css**: Heading styles and pattern classes:
  - Element selectors for h1–h6
  - Pattern classes `.ar-h1` through `.ar-h6` (decouple semantics from appearance)
  - `.ar-display` for hero sections
  - `.ar-eyebrow` for pre-heading labels
  - Mobile overrides (h1: 60→36px, h2: 48→30px, h3: 36→24px)
- **utils.css**: Prose utilities (`.ar-prose`, `.ar-lead`, `.ar-text-small`, `.ar-text-muted`, etc.)

#### Utility Layer (1,207 classes)
- **display.css**: Display values, responsive variants, sr-only utilities
- **shadow.css**: 6 shadow classes (0–4 + inset)
- **color.css**: Semantic background utilities with hover variants
- **typography.css**: Font size, alignment, color, weight, family, leading, tracking, transforms
- **border.css**: Border presence, sides, colors, styles, and radius with responsive variants
- **ratio.css**: 6 aspect ratios (square, video, photo, portrait, wide, golden) with responsive variants
- **spacing.css**: Margin, padding, and gap utilities with responsive variants
- **flex.css**: Complete flexbox system with responsive variants
- **grid.css**: Grid utilities (col spans, start/end, rows, templates) with responsive variants

#### Component Layer (5 components)
- **indicators.css**:
  - Badge component (surface, filled, outline, dot, interactive variants)
  - Avatar component (sizes, shapes, initials, status dot, groups)
- **alert.css**: 4 semantic variants (success, warning, danger, info) with titles and messages
- **button.css**: 7 variants (primary, secondary, ghost, danger, danger-ghost, link, inverse) with sizes and states
- **input.css**: Form inputs with states (error, success, disabled) and field wrapper pattern
- **card.css**: Card with header, body, footer, and variants (flat, bordered, interactive)

#### Distribution Builds
- **ariana.min.css**: Complete framework (components + utilities)
- **ariana-core.min.css**: Core only (components, no utilities) — Bootstrap-style usage
- **ariana-utilities.min.css**: Utilities only — add-on for existing projects

#### Governance & Documentation
- `TOKEN-STANDARD.md`: Complete token naming grammar
- `CONTRIBUTING.md`: Contribution guidelines and standards
- `LAYER-CONTRACT.md`: CSS `@layer` architecture documentation
- `README.md`: Project overview and quick start guide
- Full documentation website with examples

#### Design System
- **Unique visual identity** distinct from Bootstrap, Tailwind, and Material Design
- **Afghan-inspired color palette**: Lapis lazuli blue, saffron gold, cedar green, ember red, warm stone gray
- **Professional, accessible design** with geometric balance and clean whitespace
- **8-point spacing scale** with 4px micro-step for precise control
- **6px default border radius** (not Bootstrap's 4px, not 8px — the perceptual sweet spot)
- **Warm, realistic multi-layer shadows** (ambient + direct layers)

#### Accessibility
- **WCAG 2.1 AA compliant** contrast ratios for all semantic color pairs
- **`:focus-visible`** exclusively (no bare `:focus` to prevent mouse-click rings)
- **Keyboard navigable** all interactive components
- **Screen reader ready** with proper ARIA attributes
- **`prefers-reduced-motion`** global override for vestibular disorders
- **Windows High Contrast Mode** (`forced-colors`) support in all components
- **200% font size** tested (WCAG 1.4.4 compliance)
- **RTL support** via CSS logical properties (Dari, Pashto, Arabic)

#### Performance
- **Zero JavaScript dependencies** — pure CSS only
- **No build tools required** — drop a single CSS file into any HTML
- **Core bundle under 15 KB** minified and gzipped
- **CSS `@layer` system** eliminates specificity wars without `!important`
- **Token depth limit** (max 2 levels) ensures maintainable theming

### Changed
- N/A (initial release)

### Deprecated
- N/A (initial release)

### Removed
- N/A (initial release)

### Fixed
- N/A (initial release)

### Security
- No known security issues

---

## [Unreleased]

### Planned for v2.0
- Dark mode with `[data-theme="dark"]` support
- Full RTL module for Dari/Pashto special cases
- Fluid typography with `clamp()` for responsive type
- Perceptual 9-stop color scale (advanced palette)
- More components: modal, dropdown, tabs, tooltip, breadcrumb, table, divider
- Visual regression test suite with screenshot comparison
- `ariana.config.css` formal theming contract

---

## Legend

- **Added**: New features
- **Changed**: Changes to existing functionality
- **Deprecated**: Features that will be removed in the next major release
- **Removed**: Features removed in this version
- **Fixed**: Bug fixes
- **Security**: Security vulnerability fixes

---

**ArianaCSS v1.0.0** — _Ship less. Ship right. Ship on time._