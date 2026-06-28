# Contributing to ArianaCSS

**Version:** 1.0.0
**Status:** Approved & Locked
**Last Updated:** 2026-06-28

Thank you for your interest in contributing to ArianaCSS! This document outlines the standards, processes, and expectations for all contributors. Adherence to these guidelines is mandatory for all pull requests.

---

## 1. Code of Conduct

ArianaCSS is an open-source project built for a university environment in Afghanistan. We are committed to providing a welcoming, respectful, and harassment-free experience for everyone, regardless of background, identity, or experience level.

- Be respectful and inclusive.
- Provide constructive feedback.
- Assume good intentions.
- Focus on the code, not the person.

Unacceptable behavior will not be tolerated and may result in immediate removal from the project.

---

## 2. Getting Started

### Prerequisites

- A code editor (VS Code recommended)
- Basic knowledge of CSS, CSS Custom Properties, and CSS Layers
- Familiarity with the ArianaCSS philosophy and architecture (see `README.md` and `LAYER-CONTRACT.md`)
- Access to modern browsers for testing (Chrome 90+, Firefox 90+, Safari 14+)

### Project Setup

1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/arianacss.git
    cd arianacss
    ```

2.  **Development Environment:**
    - ArianaCSS requires no build tools for development. All source files are pure CSS.
    - Use a local development server (e.g., Live Server extension in VS Code) to preview changes.
    - The development master file is `src/ariana.css`. It imports all other source files via `@import`.

3.  **Directory Structure:**
    ```
    arianacss/
    ├── src/
    │   ├── 1-tokens/          # tokens.css (The single source of truth)
    │   ├── 2-base/            # reset, motion, base, focus
    │   ├── 3-layout/          # container, grid (12-column layout system)
    │   ├── 4-typography/      # scale, utils (heading classes, prose utilities)
    │   ├── 5-utilities/       # display, shadow, color, typography, border, ratio, spacing, flex, grid
    │   ├── 6-components/      # indicators, alert, button, input, card
    │   └── ariana.css         # Master development import file
    ├── dist/                  # Production builds (generated, do not edit manually)
    ├── docs/                  # Documentation (generated, do not edit manually)
    └── [Governance Files]     # TOKEN-STANDARD.md, CONTRIBUTING.md, LAYER-CONTRACT.md, etc.
    ```

### Development Workflow

1.  **Fork the Repository** and create your branch from `main`.
2.  **Make your changes** following the standards defined in this document.
3.  **Test your changes** thoroughly in all target browsers.
4.  **Commit your changes** with a descriptive commit message following the commit format (Section 5.4).
5.  **Open a Pull Request (PR)** against the `main` branch.
6.  **Complete the PR checklist** (Section 6) in the PR description.
7.  **Address review feedback** promptly and respectfully.

---

## 3. CSS Coding Standards

These standards apply to every file in the `src/` directory. Adherence is non-negotiable and enforced during code review.

### 3.1 File Structure

Every CSS source file must follow this exact structure:

```css
/* ============================================================
   [FILE NAME] — [Brief Description]
   File:    [path/to/file.css]
   Layer:   @layer [layer-name]
   Version: 1.0.0

   Token dependencies:
   [List of all --ar-* tokens consumed by this file]
   [e.g., --ar-color-primary-base, --ar-space-4, etc.]

   Responsive variants: [yes/no and which ones]
   Hover variants: [yes/no and which ones]

   ──────────────────────────────────────────────────────────────
   [Any additional file-specific notes or implementation
    decisions that are critical for maintainers to understand.]
   ============================================================ */

@layer [layer-name] {
  /* All CSS rules must be placed inside this @layer block. */
}