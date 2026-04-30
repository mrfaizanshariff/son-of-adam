# SON OF ADAM - Shopify Theme Implementation Plan

## Project Overview
Transform the Shopify Skeleton theme into a premium grooming brand theme for "SON OF ADAM" following the provided design system specifications.

---

## Design System Summary

### Brand Identity
- **Brand:** SON OF ADAM
- **Tagline:** "Grooming as timeless as man."
- **Aesthetic:** Premium, Masculine, Minimal, Editorial
- **Inspiration:** Tom Ford Grooming, Aesop, Horace, Haeckels

### Color Palette
```css
--color-sea-salt: #F9F9F9;           /* Primary Background */
--color-oxford-blue: #0D1C31;        /* Secondary Background */
--color-harvest-gold: #D6B93D;       /* Primary CTA */
--color-silver: #B7B7B9;             /* Secondary Accent */
--color-dim-grey: #636363;           /* Secondary Text/Borders */
--color-california-blue: #CAE0FF;    /* Highlight/Info */
--color-white: #FFFFFF;              /* Pure White */
```

### Typography System
- **Hero Display:** Cinzel (Google Font alternative to Old London)
- **Headers/Navigation:** Oswald (Google Font alternative to Flama Condensed)
- **Body Copy:** Inter (Google Font alternative to Mosvita)

### Typography Scale (Desktop)
- Hero Title: 80px / 1.1 line-height
- Section Title: 42px / 1.2 line-height (uppercase)
- Subheading: 24px / 1.4 line-height
- Body Text: 16px / 1.6 line-height
- Caption/Label: 12px / 1.4 line-height (uppercase, letter-spacing: 0.05em)

### Spacing System
- Max Container Width: 1200px
- Grid: 12-column responsive (Gutter: 24px desktop, 16px mobile)
- Section Spacing: 120px (desktop), 80px (tablet), 60px (mobile)
- Component Spacing: 8px, 16px, 24px, 32px, 48px increments

---

## Implementation Architecture

### Phase 1: Foundation & Configuration
**Files to Modify:**
1. [`config/settings_schema.json`](son-of-adam/config/settings_schema.json)
   - Add SON OF ADAM color system
   - Configure typography settings for 3 font families
   - Add spacing/layout controls
   - Set max width to 1200px

2. [`snippets/css-variables.liquid`](son-of-adam/snippets/css-variables.liquid)
   - Define all design system CSS variables
   - Load Google Fonts (Cinzel, Oswald, Inter)
   - Set up responsive spacing variables

3. [`assets/critical.css`](son-of-adam/assets/critical.css)
   - Add typography scale classes
   - Create button base styles
   - Add utility classes for spacing
   - Implement luxury spacing system

### Phase 2: Core Layout Components

#### Header Section
**File:** [`sections/header.liquid`](son-of-adam/sections/header.liquid)
- Premium navigation with Oswald font
- Minimalist design with proper spacing
- Account and cart icons
- Sticky header behavior
- Mobile hamburger menu

#### Footer Section
**File:** [`sections/footer.liquid`](son-of-adam/sections/footer.liquid)
- Oxford Blue background (#0D1C31)
- Multi-column layout
- Newsletter signup integration
- Social media links
- Payment icons

### Phase 3: Homepage Sections

#### 1. Editorial Hero Section
**File:** `sections/editorial-hero.liquid`
- Full-width background image/video support
- Centered Cinzel headline (80px)
- Harvest Gold CTA button
- Overlay opacity control
- Text alignment options
- Mobile responsive (60px font)

#### 2. Featured Collection Section
**File:** `sections/featured-collection.liquid`
- Horizontal scroll or 4-column grid
- Minimalist product cards (80% image, 20% info)
- "Add to Bag" button on hover
- Collection selector in schema
- Responsive: 2 columns tablet, 1 column mobile

#### 3. Image with Text Section
**File:** `sections/image-with-text.liquid`
- 50/50 split layout
- High-quality image on one side
- Oswald headers + Inter body text
- Image position toggle (left/right)
- Background color options
- Responsive: stacks on mobile

#### 4. Multicolumn Categories Section
**File:** `sections/multicolumn-categories.liquid`
- 3-4 column layout
- Square images/icons for categories
- Oswald category names
- Hover effects
- Link to collection pages
- Responsive: 2 columns tablet, 1 column mobile

#### 5. Newsletter Signup Section
**File:** `sections/newsletter-signup.liquid`
- Oxford Blue background
- Centered layout
- Email input field
- Harvest Gold submit button
- Success/error messaging
- GDPR compliance checkbox

### Phase 4: Product Page Components

#### Product Detail Page (PDP)
**File:** [`sections/product.liquid`](son-of-adam/sections/product.liquid)
- Large image gallery (left side, 60% width)
- Product info/buy box (right side, 40% width)
- Variant selector with custom styling
- Quantity selector
- Primary CTA button (Harvest Gold)
- Product description with accordions
- Related products section below

#### Product Card Snippet
**File:** `snippets/product-card.liquid`
- Minimalist design
- 80% image height
- Oswald font for product name
- Price in Harvest Gold
- "Add to Bag" hover state
- Badge support (New, Limited)
- Quick view option

### Phase 5: Reusable Components

#### Button Snippets
**File:** `snippets/button.liquid`
- Primary CTA: Harvest Gold fill, Oxford Blue text, rectangular
- Secondary CTA: Oxford Blue outline, 1px solid
- Hover states
- Size variants (small, medium, large)
- Full-width option

#### Badge Component
**File:** `snippets/badge.liquid`
- Small rectangular badges
- Oxford Blue background
- Silver text
- Types: "New", "Limited", "Sale"

#### Accordion Component
**File:** `snippets/accordion.liquid`
- Minimalist +/- icons
- Thin Dim Grey dividers
- Smooth transitions
- Used for product details, FAQs

### Phase 6: Template Configuration

#### Homepage Template
**File:** [`templates/index.json`](son-of-adam/templates/index.json)
```json
{
  "sections": {
    "editorial-hero": { "type": "editorial-hero" },
    "featured-collection": { "type": "featured-collection" },
    "image-with-text-1": { "type": "image-with-text" },
    "multicolumn-categories": { "type": "multicolumn-categories" },
    "image-with-text-2": { "type": "image-with-text" },
    "newsletter-signup": { "type": "newsletter-signup" }
  },
  "order": [...]
}
```

#### Product Template
**File:** [`templates/product.json`](son-of-adam/templates/product.json)
- Main product section
- Related products
- Recently viewed (optional)

---

## Responsive Breakpoints

```css
/* Mobile First Approach */
--breakpoint-mobile: 0px;
--breakpoint-tablet: 768px;
--breakpoint-desktop: 1024px;
--breakpoint-wide: 1440px;

/* Section Spacing */
--section-spacing-mobile: 60px;
--section-spacing-tablet: 80px;
--section-spacing-desktop: 120px;
```

---

## Schema Settings Strategy

Each section will include comprehensive schema settings:
- **Content Settings:** Text, images, links
- **Layout Settings:** Alignment, spacing, columns
- **Style Settings:** Colors, fonts, borders
- **Visibility Settings:** Show/hide elements
- **Responsive Settings:** Mobile-specific options

---

## File Structure Overview

```
son-of-adam/
├── assets/
│   ├── critical.css (updated)
│   ├── icon-account.svg
│   ├── icon-cart.svg
│   └── [new icons as needed]
├── config/
│   ├── settings_schema.json (updated)
│   └── settings_data.json
├── layout/
│   └── theme.liquid (minimal updates)
├── sections/
│   ├── header.liquid (redesigned)
│   ├── footer.liquid (redesigned)
│   ├── editorial-hero.liquid (new)
│   ├── featured-collection.liquid (new)
│   ├── image-with-text.liquid (new)
│   ├── multicolumn-categories.liquid (new)
│   ├── newsletter-signup.liquid (new)
│   └── product.liquid (updated)
├── snippets/
│   ├── css-variables.liquid (updated)
│   ├── product-card.liquid (new)
│   ├── button.liquid (new)
│   ├── badge.liquid (new)
│   └── accordion.liquid (new)
└── templates/
    ├── index.json (updated)
    └── product.json (updated)
```

---

## Development Workflow

### Step-by-Step Implementation Order:

1. **Foundation Setup** (Tasks 1-3)
   - Update settings schema with brand colors and fonts
   - Create CSS variables system
   - Update critical.css with base styles

2. **Layout Components** (Tasks 4-5)
   - Redesign header with premium styling
   - Redesign footer with Oxford Blue background

3. **Reusable Components** (Tasks 12-13)
   - Create button snippets (Primary/Secondary CTA)
   - Create product card snippet
   - Create badge and accordion snippets

4. **Homepage Sections** (Tasks 6-10)
   - Editorial Hero
   - Featured Collection
   - Image with Text
   - Multicolumn Categories
   - Newsletter Signup

5. **Product Page** (Task 11)
   - Update PDP with image gallery and buy box
   - Integrate product card snippet

6. **Template Configuration** (Task 14)
   - Update index.json with new sections
   - Configure product.json

7. **Testing & Refinement** (Task 15)
   - Test responsive behavior
   - Cross-browser testing
   - Performance optimization

---

## Key Technical Considerations

### Performance
- Use lazy loading for images
- Optimize font loading with `font-display: swap`
- Minimize CSS/JS bundle size
- Use Shopify's image CDN with proper sizing

### Accessibility
- Proper heading hierarchy
- ARIA labels for interactive elements
- Keyboard navigation support
- Color contrast compliance (WCAG AA)

### SEO
- Semantic HTML structure
- Proper meta tags
- Schema.org markup for products
- Alt text for all images

### Browser Support
- Modern browsers (last 2 versions)
- Progressive enhancement approach
- Graceful degradation for older browsers

---

## Testing Checklist

- [ ] Desktop layout (1440px, 1920px)
- [ ] Tablet layout (768px, 1024px)
- [ ] Mobile layout (375px, 414px)
- [ ] Header navigation functionality
- [ ] Product card hover states
- [ ] CTA button interactions
- [ ] Form submissions (newsletter)
- [ ] Product variant selection
- [ ] Add to cart functionality
- [ ] Image gallery navigation
- [ ] Accordion expand/collapse
- [ ] Cross-browser compatibility
- [ ] Performance metrics (Lighthouse)
- [ ] Accessibility audit

---

## Next Steps

Once this plan is approved, we'll switch to **Code mode** to implement each component systematically, following the todo list order. Each section will be built with:
- Clean, maintainable Liquid code
- Comprehensive schema settings
- Responsive CSS using the design system
- Proper documentation in comments

The implementation will prioritize the homepage and product page as requested, ensuring a premium, editorial aesthetic that matches the SON OF ADAM brand identity.