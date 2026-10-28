# Shopify Theme Improvement Plan: Accessibility, Standards & Localization

## Top-Level Overview
This plan establishes a structured, prioritized path to elevate the custom **SON OF ADAM** Shopify theme into full compliance with **WCAG 2.2 Level AA Accessibility**, **Shopify Liquid & Web Component Standards**, and **Complete Theme Localization**. The work is sequenced into three distinct, reviewable phases:

1. **Phase 1: WCAG 2.2 Accessibility Hardening** — Keyboard navigation, focus states, screen reader context, live regions, and semantic roles.
2. **Phase 2: Liquid/HTML Standards, Progressive Enhancement & CSS Refactoring** — Native `<details>/<summary>` accordions, Web Component JS encapsulation, and CSS logical properties.
3. **Phase 3: Comprehensive Localization & Translation Architecture** — Replacement of hardcoded strings with `{{ '...' | t }}` filters and complete hierarchical keys in `locales/en.default.json`.

---

## Sub-Tasks

### Sub-Task 1: Global Accessibility Foundation & Focus Management
- **Intent**: Establish visible skip navigation, high contrast focus indicators, and reduced-motion user preference overrides at the global layout level.
- **Expected Outcomes**:
  - Skip link is fully visible and usable upon keyboard focus.
  - Global CSS handles reduced-motion preferences to disable/minimize transitions and animations.
  - High-contrast mode focus indicators meet WCAG 2.2 requirements.
- **Todo List**:
  - [x] Update `assets/critical.css` to add visible focus styles for `.skip-to-content:focus`.
  - [x] Add `@media (prefers-reduced-motion: reduce)` rules across `assets/critical.css` to neutralize animations.
  - [x] Add `@media (forced-colors: active)` focus overrides for high contrast modes.
  - [x] Verify `layout/theme.liquid` has proper main landmark linking and language tag output.
- **Relevant Context**: `assets/critical.css:557-580`, `layout/theme.liquid:41-48`.
- **Status**: [x] done

---

### Sub-Task 2: Product & Collection Accessibility Hardening
- **Intent**: Ensure product cards, image galleries, price displays, and collection filters provide rich screen reader context and proper keyboard navigation.
- **Expected Outcomes**:
  - Product cards use semantic `<article>` tags with `aria-labelledby` pointing to the title.
  - Price tags have descriptive screen reader labels distinguishing sale and regular prices.
  - Strike-through comparison prices are hidden from screen readers via `aria-hidden="true"`.
  - Product image gallery updates thumbnail active states with `aria-current="true"`.
  - Background media in the hero section provides accessible pause/play controls.
- **Todo List**:
  - [x] Refactor `snippets/product-card.liquid` to use `<article>`, single primary tab stop, and accessible price labels.
  - [x] Update `sections/product.liquid` price block to wrap strikethrough prices with `<s aria-hidden="true">` and provide `aria-label`.
  - [x] Update `snippets/product-gallery.liquid` to add `aria-current="true"` on the active thumbnail and link accessible labels.
  - [x] Update `sections/editorial-hero.liquid` to handle background video accessibility or pause options.
- **Relevant Context**: `snippets/product-card.liquid:34-90`, `sections/product.liquid:43-53`, `snippets/product-gallery.liquid:40-65`, `sections/editorial-hero.liquid:8-20`.
- **Status**: [x] done

---

### Sub-Task 3: Cart, Search, and Reviews Accessibility
- **Intent**: Ensure dynamic asynchronous updates (cart changes, review submissions, search results) are announced to assistive technologies via ARIA live regions and proper form labeling.
- **Expected Outcomes**:
  - Dynamic cart modifications and error messages announce status via `aria-live="polite"`.
  - Product reviews modal/form properly manages keyboard focus and field validations.
  - Filter drawer / dropdowns in collections manage `aria-expanded` and focus trap states correctly.
- **Todo List**:
  - [x] Add polite live regions for cart quantity updates and remove actions in `sections/cart.liquid`.
  - [x] Ensure `snippets/product-reviews.liquid` form fields link `aria-describedby` to error containers and manage focus on submit.
  - [x] Verify `sections/collection.liquid` filter buttons toggle `aria-expanded` and manage focus transitions.
- **Relevant Context**: `sections/cart.liquid:30-100`, `snippets/product-reviews.liquid:50-120`, `sections/collection.liquid:110-230`.
- **Status**: [x] done

---

### Sub-Task 4: Progressive Enhancement & Native HTML Refactoring
- **Intent**: Replace custom JS-dependent UI components with native HTML elements like `<details>/<summary>` for accordions, ensuring functionality without JavaScript.
- **Expected Outcomes**:
  - Accordion sections work natively with zero JavaScript dependency.
  - Clean LiquidDoc annotations at the top of snippets and blocks.
  - Removal of inline presentational styles in favor of CSS utility classes or CSS custom properties.
- **Todo List**:
  - [x] Refactor `snippets/product-accordion.liquid` to use native `<details>` and `<summary>` tags.
  - [x] Replace inline presentational styles in `sections/product.liquid`, `sections/editorial-hero.liquid`, and `sections/cart.liquid` with scoped classes.
  - [x] Add `{% doc %}` LiquidDoc headers to undocumented snippets.
- **Relevant Context**: `snippets/product-accordion.liquid:18-42`, `sections/product.liquid:98`, `sections/cart.liquid:44,117`.
- **Status**: [x] done

---

### Sub-Task 5: JavaScript Encapsulation & Web Component Patterns
- **Intent**: Encapsulate interactive behaviors into modular, maintainable Web Components or component-scoped `{% javascript %}` tags without global scope pollution.
- **Expected Outcomes**:
  - Eliminates inline `<script>` tags across snippets.
  - Product gallery, quantity selector, and header mobile menu are cleanly encapsulated.
  - Proper cleanup of event listeners and abort controllers on async fetch operations.
- **Todo List**:
  - [x] Migrate inline script in `snippets/product-gallery.liquid` to standard scoped JavaScript/Web Component.
  - [x] Modernize `snippets/quantity-selector.liquid` to use Custom Event dispatching and clean event delegation.
  - [x] Review `sections/header.liquid` and `sections/cart.liquid` scripts to ensure reliable DOM cleanup and event handling.
- **Relevant Context**: `snippets/product-gallery.liquid:66-80`, `snippets/quantity-selector.liquid:121-192`, `sections/header.liquid:372-420`.
- **Status**: [x] done

---

### Sub-Task 6: CSS Logical Properties & RTL Readiness
- **Intent**: Convert physical directional CSS rules to CSS logical properties to prepare the theme for internationalization and multi-directional layouts (RTL/LTR).
- **Expected Outcomes**:
  - Spacing, margins, padding, and alignments use logical properties (`margin-inline`, `padding-inline`, `inset-inline-start`, `text-align: start`).
- **Todo List**:
  - [x] Refactor physical margins and paddings in `assets/critical.css` to `margin-inline-start/end` and `padding-inline-start/end`.
  - [x] Refactor physical alignments and positionings in `snippets/breadcrumb.liquid`, `snippets/button.liquid`, and section stylesheets.
- **Relevant Context**: `assets/critical.css:120, 139, 156, 173, 360-363`, `snippets/breadcrumb.liquid:108-150`.
- **Status**: [x] done

---

### Sub-Task 7: Comprehensive Theme Localization & Translation Architecture
- **Intent**: Extract every user-facing string across all templates, sections, and snippets into standard hierarchical translation keys in `locales/en.default.json`.
- **Expected Outcomes**:
  - Zero hardcoded English text in Liquid templates, sections, or snippets.
  - Complete, structured `locales/en.default.json` covering navigation, product details, cart, collection filters, and error messages.
  - Proper string interpolation with variables (`{{ '...' | t: variable: value }}`).
- **Todo List**:
  - [x] Extract and replace hardcoded strings in `sections/product.liquid`, `snippets/product-card.liquid`, `sections/collection.liquid`, and `sections/cart.liquid` with `| t` filters.
  - [x] Extract strings from `sections/header.liquid`, `sections/footer.liquid`, `sections/search.liquid`, and `sections/editorial-hero.liquid`.
  - [x] Rebuild and organize `locales/en.default.json` with structured namespaces (`general`, `products`, `cart`, `collection`, `filters`, `accessibility`).
  - [x] Update `locales/en.default.schema.json` for theme editor setting translations where applicable.
- **Relevant Context**: `locales/en.default.json`, `sections/product.liquid`, `sections/collection.liquid:74`, `snippets/product-card.liquid:61-75`.
- **Status**: [x] done
