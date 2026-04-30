# SON OF ADAM - Design System Reference

Quick reference guide for implementing the SON OF ADAM brand aesthetic.

---

## 🎨 Color Palette

### Primary Colors
```css
/* Backgrounds */
--color-sea-salt: #F9F9F9;        /* Main background - light, clean */
--color-oxford-blue: #0D1C31;     /* Dark sections - header, footer, newsletter */
--color-white: #FFFFFF;           /* Pure white for cards and contrast */

/* Brand Colors */
--color-harvest-gold: #D6B93D;    /* Primary CTA, prices, highlights */
--color-silver: #B7B7B9;          /* Secondary accents, badges */

/* Text & UI */
--color-dim-grey: #636363;        /* Secondary text, borders, dividers */
--color-california-blue: #CAE0FF; /* Info highlights, hover states */
```

### Color Usage Guidelines

| Element | Color | Hex Code |
|---------|-------|----------|
| Page Background | Sea Salt | `#F9F9F9` |
| Header Background | Oxford Blue | `#0D1C31` |
| Footer Background | Oxford Blue | `#0D1C31` |
| Primary Button | Harvest Gold | `#D6B93D` |
| Primary Button Text | Oxford Blue | `#0D1C31` |
| Secondary Button Border | Oxford Blue | `#0D1C31` |
| Body Text | Oxford Blue | `#0D1C31` |
| Secondary Text | Dim Grey | `#636363` |
| Dividers | Dim Grey | `#636363` |
| Badges | Oxford Blue bg + Silver text | `#0D1C31` + `#B7B7B9` |
| Price | Harvest Gold | `#D6B93D` |

---

## 📝 Typography

### Font Families (Google Fonts)

```css
/* Display Font - for hero headlines */
--font-display: 'Cinzel', serif;

/* Header Font - for navigation, section titles, product names */
--font-header: 'Oswald', sans-serif;

/* Body Font - for descriptions, labels, general content */
--font-body: 'Inter', sans-serif;
```

### Typography Scale

| Element | Font | Size | Line Height | Transform | Letter Spacing |
|---------|------|------|-------------|-----------|----------------|
| Hero Title | Cinzel | 80px | 1.1 | - | - |
| Hero Title (Mobile) | Cinzel | 48px | 1.1 | - | - |
| Section Title | Oswald | 42px | 1.2 | UPPERCASE | - |
| Section Title (Mobile) | Oswald | 32px | 1.2 | UPPERCASE | - |
| Subheading | Oswald | 24px | 1.4 | - | - |
| Navigation | Oswald | 16px | 1.4 | UPPERCASE | 0.05em |
| Body Text | Inter | 16px | 1.6 | - | - |
| Product Name | Oswald | 18px | 1.3 | - | - |
| Price | Oswald | 20px | 1.2 | - | - |
| Caption/Label | Inter | 12px | 1.4 | UPPERCASE | 0.05em |
| Button Text | Oswald | 14px | 1.2 | UPPERCASE | 0.1em |

### CSS Classes

```css
.hero-title {
  font-family: var(--font-display);
  font-size: clamp(48px, 8vw, 80px);
  line-height: 1.1;
  font-weight: 400;
}

.section-title {
  font-family: var(--font-header);
  font-size: clamp(32px, 5vw, 42px);
  line-height: 1.2;
  text-transform: uppercase;
  font-weight: 700;
}

.subheading {
  font-family: var(--font-header);
  font-size: 24px;
  line-height: 1.4;
  font-weight: 500;
}

.body-text {
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 1.6;
  font-weight: 400;
}

.label {
  font-family: var(--font-body);
  font-size: 12px;
  line-height: 1.4;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  font-weight: 500;
}
```

---

## 📏 Spacing System

### Base Spacing Scale
```css
--spacing-xs: 8px;
--spacing-sm: 16px;
--spacing-md: 24px;
--spacing-lg: 32px;
--spacing-xl: 48px;
--spacing-2xl: 64px;
--spacing-3xl: 80px;
--spacing-4xl: 120px;
```

### Section Spacing (Vertical)
```css
/* Desktop */
--section-spacing-desktop: 120px;

/* Tablet */
--section-spacing-tablet: 80px;

/* Mobile */
--section-spacing-mobile: 60px;
```

### Container & Grid
```css
--container-max-width: 1200px;
--grid-columns: 12;
--grid-gutter-desktop: 24px;
--grid-gutter-mobile: 16px;
--page-margin-desktop: 40px;
--page-margin-mobile: 20px;
```

---

## 🔘 Buttons

### Primary CTA Button
```css
.btn-primary {
  background-color: var(--color-harvest-gold);
  color: var(--color-oxford-blue);
  font-family: var(--font-header);
  font-size: 14px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  padding: 16px 32px;
  border: none;
  border-radius: 0; /* Rectangular, no rounding */
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-primary:hover {
  background-color: #C4A735; /* Slightly darker gold */
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(214, 185, 61, 0.3);
}
```

### Secondary CTA Button
```css
.btn-secondary {
  background-color: transparent;
  color: var(--color-oxford-blue);
  font-family: var(--font-header);
  font-size: 14px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  padding: 16px 32px;
  border: 1px solid var(--color-oxford-blue);
  border-radius: 0;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-secondary:hover {
  background-color: var(--color-oxford-blue);
  color: var(--color-white);
}

/* On dark backgrounds */
.btn-secondary--dark {
  color: var(--color-white);
  border-color: var(--color-white);
}

.btn-secondary--dark:hover {
  background-color: var(--color-white);
  color: var(--color-oxford-blue);
}
```

---

## 🖼️ UI Components

### Product Card
```
┌─────────────────────┐
│                     │
│                     │
│   Product Image     │ 80% height
│   (Aspect 3:4)      │
│                     │
├─────────────────────┤
│ Product Name        │ 20% height
│ $XX.XX              │ Oswald font
│ [Add to Bag]        │ Hover state
└─────────────────────┘
```

**Specifications:**
- Image aspect ratio: 3:4 (portrait)
- Hover: Show "Add to Bag" button overlay
- Product name: Oswald, 18px
- Price: Harvest Gold, 20px, Oswald
- Minimal padding: 16px
- No border, clean edges

### Badge
```css
.badge {
  display: inline-block;
  background-color: var(--color-oxford-blue);
  color: var(--color-silver);
  font-family: var(--font-body);
  font-size: 10px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  padding: 4px 8px;
  border-radius: 0; /* Rectangular */
}
```

**Badge Types:**
- `NEW` - For new products
- `LIMITED` - For limited editions
- `SALE` - For discounted items

### Accordion
```
┌─────────────────────────────────┐
│ Title                        [+]│
├─────────────────────────────────┤
│ Title                        [-]│
│ Content goes here...            │
│ Multiple lines supported        │
├─────────────────────────────────┤
│ Title                        [+]│
└─────────────────────────────────┘
```

**Specifications:**
- Divider: 1px solid Dim Grey
- Icon: +/- symbols, 16px
- Smooth transition: 0.3s ease
- Padding: 24px vertical, 0 horizontal

---

## 📱 Responsive Breakpoints

```css
/* Mobile First Approach */
@media (min-width: 768px) {
  /* Tablet styles */
}

@media (min-width: 1024px) {
  /* Desktop styles */
}

@media (min-width: 1440px) {
  /* Wide desktop styles */
}
```

### Layout Adjustments

| Breakpoint | Columns | Section Spacing | Grid Gutter |
|------------|---------|-----------------|-------------|
| Mobile (0-767px) | 1 | 60px | 16px |
| Tablet (768-1023px) | 2 | 80px | 20px |
| Desktop (1024-1439px) | 3-4 | 120px | 24px |
| Wide (1440px+) | 4 | 120px | 24px |

---

## 🎯 Section Guidelines

### Editorial Hero
- **Height:** 80vh (desktop), 60vh (mobile)
- **Text Alignment:** Center
- **Overlay:** 40% opacity black overlay on image
- **CTA Position:** Below headline, centered
- **Spacing:** 48px between headline and CTA

### Featured Collection
- **Layout:** 4 columns (desktop), 2 (tablet), 1 (mobile)
- **Gap:** 24px
- **Card Style:** Minimalist product card
- **Scroll:** Horizontal scroll on mobile (optional)

### Image with Text
- **Split:** 50/50 (desktop), stacked (mobile)
- **Image:** Full height of container
- **Text Padding:** 48px (desktop), 32px (mobile)
- **Alignment:** Vertical center

### Multicolumn Categories
- **Columns:** 3-4 (desktop), 2 (tablet), 1 (mobile)
- **Image Shape:** Square (1:1 aspect ratio)
- **Hover Effect:** Slight zoom (1.05 scale)
- **Text:** Centered below image

### Newsletter Signup
- **Background:** Oxford Blue
- **Text Color:** White
- **Input Style:** White background, Oxford Blue text
- **Button:** Harvest Gold
- **Max Width:** 600px, centered

---

## ✨ Animation & Transitions

### Standard Transitions
```css
transition: all 0.3s ease;
```

### Hover Effects
- **Buttons:** Slight lift (translateY -2px) + shadow
- **Product Cards:** Show overlay with "Add to Bag"
- **Images:** Subtle zoom (scale 1.05)
- **Links:** Color change to Harvest Gold

### Loading States
- Use subtle fade-in animations
- Skeleton screens for product grids
- Smooth transitions between states

---

## ♿ Accessibility Requirements

### Color Contrast
- Text on Sea Salt: Use Oxford Blue (AAA)
- Text on Oxford Blue: Use White (AAA)
- Buttons: Ensure 4.5:1 minimum contrast

### Interactive Elements
- Minimum touch target: 44x44px
- Clear focus states (2px Harvest Gold outline)
- Keyboard navigation support
- ARIA labels for icons

### Semantic HTML
- Proper heading hierarchy (h1 → h2 → h3)
- Alt text for all images
- Form labels properly associated
- Landmark regions (header, main, footer)

---

## 🚀 Performance Guidelines

### Images
- Use WebP format with JPG fallback
- Lazy load below-the-fold images
- Responsive images with srcset
- Max file size: 200KB per image

### Fonts
- Preload critical fonts (Cinzel regular)
- Use font-display: swap
- Subset fonts to Latin characters only
- Load font weights on-demand

### CSS
- Critical CSS inlined in `<head>`
- Component-level CSS in sections
- Use CSS variables for theming
- Minimize specificity

---

## 📋 Component Checklist

When creating a new section, ensure:
- [ ] Responsive design (mobile, tablet, desktop)
- [ ] Schema settings for customization
- [ ] Proper color contrast
- [ ] Keyboard navigation support
- [ ] Loading states handled
- [ ] Error states handled
- [ ] Proper spacing using design tokens
- [ ] Typography follows scale
- [ ] Hover states defined
- [ ] Focus states visible
- [ ] Alt text for images
- [ ] Semantic HTML structure

---

This design system ensures consistency across the SON OF ADAM theme while maintaining the premium, editorial aesthetic that defines the brand.