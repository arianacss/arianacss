# ArianaCSS Token Standard

**Version:** 1.0.0
**Status:** Approved & Locked
**Last Updated:** 2026-06-28

This document defines the non-negotiable naming grammar for all CSS Custom Properties (tokens) used within the ArianaCSS framework. Adherence to this standard is mandatory for all contributions and ensures the system remains scalable, predictable, and self-documenting.

---

## 1. Core Philosophy

- **Single Source of Truth:** The file `src/1-tokens/tokens.css` is the exclusive source for all visual decisions. No component, utility, or layout file may contain a hard-coded visual value.
- **Semantic Over Implementation:** Tokens are named by their *purpose* (e.g., `--ar-color-primary-base`), not by their raw value (e.g., `--ar-color-blue-500`). This allows for easy theming and shields the rest of the framework from changes in the primitive palette.
- **Clarity and Discoverability:** Token names are structured to be self-explanatory, making the system easy to learn for beginners and intuitive to use for experts.

## 2. The Token Naming Grammar

All tokens must strictly conform to the following pattern:

`--ar-[category]-[subcategory]?-[variant]`

### Grammar Components

| Component | Description | Constraint | Example |
| :--- | :--- | :--- | :--- |
| `--ar-` | **Namespace Prefix** | Mandatory for all tokens. Prevents conflicts with third-party code. | `--ar-` |
| `[category]` | **The Token Category** | Defines the high-level group. Must be one of the allowed categories listed in Section 3. | `color`, `text`, `space` |
| `[subcategory]?` | **The Token Subcategory** | Optional. Provides further context and specificity for the category. Should be used to create logical groupings. | `layer`, `primary`, `size` |
| `[variant]` | **The Token Variant** | Defines the specific role or variation of the token. This is the final, most granular descriptor. | `base`, `surface`, `hover`, `4` |

### Key Rules

- **Lowercase Only:** All token names must be in lowercase.
- **Hyphens as Separators:** Use hyphens (`-`) to separate all components of the token name.
- **Meaningful Names:** Names must clearly describe the token's purpose. Avoid abbreviations. `--ar-color-primary-base` is preferred over `--ar-c-pri-b`.
- **No Hard-Coded Units:** Token names must not contain units (e.g., `--ar-space-16px` is forbidden). The unit is defined in the token's value within `tokens.css`.
- **No Underscores:** Use hyphens only. Underscores (`_`) are prohibited.
- **Private/Internal Tokens:** For values used only within a specific component's CSS to avoid repetition (e.g., size calculations), use a double underscore prefix: `--_ar-[component]-[property]`. These are never referenced outside the component file. Example: `--_ar-btn-height`.

## 3. Allowed Categories and Subcategories

The following is the exhaustive list of categories and their valid subcategories. Any deviation from this list must be proposed as a formal change to the architecture.

| Category | Description | Valid Subcategories | Valid Variants (Examples) |
| :--- | :--- | :--- | :--- |
| **`color`** | All color-related decisions. | `primary`, `success`, `warning`, `danger`, `info`, `layer`, `text`, `state`, `border`, `selection`, `backdrop`, `scrollbar` | `base`, `hover`, `active`, `surface`, `emphasis`, `muted`, `default`, `strong`, `focus` |
| **`text`** | All typography-related decisions. | `font`, `size`, `leading`, `tracking`, `weight` | `sans`, `mono`, `xs`, `sm`, `base`, `normal`, `tight`, `normal`, `bold` |
| **`space`** | All spacing (margin, padding, gap) decisions. | (None) | `0`, `micro`, `1`, `1h`, `2`, `3`, `4`, `5`, `6`, `7`, `8`, `10`, `12`, `16`, `20`, `24`, `hairline` |
| **`radius`** | All border-radius decisions. | (None) | `none`, `sm`, `base`, `lg`, `xl`, `full` |
| **`shadow`** | All box-shadow decisions. | (None) | `0`, `1`, `2`, `3`, `4`, `inset` |
| **`duration`** | All animation/transition duration decisions. | (None) | `fast`, `base`, `slow` |
| **`ease`** | All animation/transition easing curve decisions. | (None) | `standard`, `decelerate`, `accelerate` |
| **`focus`** | All focus ring decisions. | `ring` | `width`, `offset`, `style`, `color-default`, `color-danger`, `color-success` |
| **`z`** | All z-index decisions. | (None) | `base`, `raised`, `dropdown`, `sticky`, `overlay`, `modal`, `toast` |
| **`grid`** | All grid-specific layout decisions. | (None) | `columns`, `gap`, `gap-sm`, `gap-lg` |
| **`container`** | All container-specific layout decisions. | (None) | `sm`, `md`, `lg`, `xl`, `padding-x` |

## 4. Category-Specific Standards

### 4.1 The `color` Category

- **Subcategory Rule:** Use subcategories to separate roles.
    - `--ar-color-primary-base`
    - `--ar-color-success-text`
    - `--ar-color-layer-base`
- **Value Rule:** All color token values must be expressed in modern CSS `hsl()` syntax.

### 4.2 The `text` Category

- **Subcategory Rule:** This is the only category where a strict subcategory is always required.
    - `--ar-text-size-base`
    - `--ar-text-weight-bold`
    - `--ar-text-font-sans`
- **Rule:** The `text` subcategory ensures all typography tokens are discoverable under the `--ar-text-` prefix.

### 4.3 The `space` Category

- **Variant Rule:** Variants must be numeric scale steps derived from the 4px base unit (e.g., `4` for `16px`), with special variants for precision tools (`hairline`) and half-steps (`1h` for `6px`).
- **Rule:** Spacing is defined by the `--ar-space-*` scale, not by arbitrary pixel values.

## 5. The Prohibited Patterns

The following patterns are strictly prohibited in token names:

1.  **Direct Color Names:** Tokens must never be named by their raw color (e.g., `--ar-blue-500`). Use semantic names.
    - **Prohibited:** `--ar-button-blue`
    - **Correct:** `--ar-color-primary-base`
2.  **Implementation Details:** Tokens must not reference CSS properties (e.g., `background-color`, `padding`).
    - **Prohibited:** `--ar-button-background`
    - **Correct:** `--ar-color-primary-base` (The component is responsible for applying the color to `background-color`.)
3.  **Unclear Abbreviations:** Avoid abbreviations that are not universally understood.
    - **Prohibited:** `--ar-c-brdr-def`
    - **Correct:** `--ar-color-border-default`

## 6. Token Depth & Chaining

To ensure performance and maintainability, a strict depth limit is enforced.

- **Maximum Depth:** A semantic token may reference a primitive token (1 level of indirection) or a raw value. The chain of `var()` lookups within the `tokens.css` file must not exceed **two (2) levels**.
- **Enforcement:**
    - **Correct:** `--ar-color-primary-base: var(--ar-lapis-600);` (1 level)
    - **Correct:** `--ar-color-primary-base: hsl(226, 72%, 46%);` (0 levels)
    - **Incorrect:** `--ar-color-x: var(--ar-color-primary-base);` (Chaining a semantic token to another semantic token is 2+ levels and is prohibited).
- **Exception for Theming:** If a user overrides a token with another `var()`, this depth is outside the framework's control and may exceed the 2-level limit. This is permitted as an advanced theming feature.

## 7. The Theming Entry Point

The token system provides two distinct, non-conflicting entry points for theming:

1.  **Override Primitives:** To completely change a color palette (e.g., replace Lapis with a corporate blue), the user overrides the primitive tokens (e.g., `--ar-lapis-600`). This automatically updates all semantic tokens that reference it.
2.  **Override Semantic Tokens:** To make a targeted change (e.g., changing a primary button hover state without affecting the rest of the primary color), the user overrides the semantic token directly (e.g., `--ar-color-primary-hover`).

**Important:** Users should choose one entry point to avoid conflicting overrides. If they override `--ar-lapis-600` and `--ar-color-primary-base`, the `--ar-color-primary-base` override will take precedence.

## 8. Governance

- **Adding a Token:** New tokens cannot be added directly. A formal proposal must be submitted, which includes an update to this document, `LAYER-CONTRACT.md`, and `CONTRIBUTING.md`.
- **Renaming/Removing a Token:** This is a breaking change that requires a major version bump and must follow the formal deprecation process.
- **Enforcement:** All tokens, in every file, will be audited against this standard as part of the code review process. Any violation will block the PR from being merged.
