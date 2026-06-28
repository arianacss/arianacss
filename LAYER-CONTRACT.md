# ArianaCSS Layer Contract

**Version:** 1.0.0
**Status:** Approved & Locked
**Last Updated:** 2026-06-28

This document defines the CSS cascade layer system for ArianaCSS. The layer order is the single most consequential architectural decision in the framework. Understanding and respecting this contract is mandatory for all contributors.

---

## Table of Contents

- [What Are CSS Layers?](#what-are-css-layers)
- [The Layer Order](#the-layer-order)
- [Layer Definitions](#layer-definitions)
- [Why This Order Is Correct](#why-this-order-is-correct)
- [Layer Assignment](#layer-assignment)
- [Special Cases & Exceptions](#special-cases--exceptions)
- [Common Mistakes](#common-mistakes)
- [Layer Contract Enforcement](#layer-contract-enforcement)

---

## What Are CSS Layers?

CSS `@layer` is a modern CSS feature that allows developers to control the cascade order of entire groups of styles. Unlike specificity (`!important`, ID selectors, nested selectors), which is a per-rule battle, layers provide a **global, predictable, and maintainable** priority system.

### How Layers Work

1.  **Layers are declared in order.** The order of declaration determines the priority:
    - **Later layers win** over earlier layers.
    - A rule in `@layer utilities` will always beat a rule in `@layer components`, regardless of specificity.

2.  **Layers don't fight specificity.** If a layer wins, all its rules win, even if they have lower specificity than a rule in a losing layer.

3.  **Unlayered styles** (styles written outside any `@layer` block) win over all layered styles. **This is why we never write styles outside layers.**

### Example

```css
/* Layer declaration */
@layer base, components, utilities;

/* Base layer */
@layer base {
  .btn { color: red; }
}

/* Components layer */
@layer components {
  .btn { color: blue; } /* Wins over base because components comes later */
}

/* Utilities layer */
@layer utilities {
  .btn { color: green; } /* Wins over both because utilities comes last */
}
