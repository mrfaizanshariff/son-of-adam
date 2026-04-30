# Essential Pages Implementation Plan - SON OF ADAM

## 📋 Overview

This document outlines the implementation plan for creating essential e-commerce pages based on the provided designs and SON OF ADAM brand aesthetic.

---

## 🎯 Pages to Build

### 1. **Collection Page** (Design Provided)
### 2. **Product Detail Page (PDP)** (Design Provided)
### 3. **Search Page** (Follow Theme)
### 4. **Cart Page** (Follow Theme)
### 5. **Checkout Page** (Shopify Plus Only - Style with CSS)

---

## 📐 Design Analysis

### Collection Page Design Elements:
- **Breadcrumb**: HOME / GROOMING ESSENTIALS
- **Page Title**: "Grooming Essentials" with mixed font (G in Old London, rest in Flama Condensed)
- **Description**: Body text in Mosvita below title
- **Filters Section**: Left sidebar with:
  - CATEGORY dropdown
  - SKIN TYPE dropdown
  - PRICE dropdown
- **Sort By**: Top right - "Featured" dropdown
- **Product Grid**: 4 columns on desktop
- **Product Cards**: Same minimalist style as homepage
- **Load More Button**: Centered at bottom
- **Footer**: Newsletter signup section

### Product Detail Page Design Elements:
- **Breadcrumb**: HOME / GROOMING / NOCTURNAL RECOVERY
- **Layout**: 50/50 split (Image left, Info right)
- **Image Gallery**: 
  - Large main image
  - 4 thumbnail images below
  - Product images with clean backgrounds
- **Product Info Section**:
  - Product title: "NOCTURNAL RECOVERY OIL"
  - Star rating: 5 stars with review count
  - Price: ₹850.00
  - Description paragraph
  - Quantity selector (- 1 +)
  - "ADD TO CART" button (Harvest Gold)
- **Accordions**:
  - BENEFITS (expandable)
  - INGREDIENTS (expandable)
  - HOW TO USE (expandable)
- **Brand Section**: Oxford Blue background
  - "THE RITUAL" label
  - "CRAFTED FOR THE DISCERNING FEW."
  - Description text
  - "EXPLORE OUR PHILOSOPHY" button
- **Related Products**: "YOU MAY ALSO LIKE" section
  - 4 product cards in a row
  - Same card style as collection page

---

## 🔨 Implementation Strategy

### Phase 1: Collection Page (Priority 1)
**File**: `sections/collection.liquid`

**Components Needed**:
1. **Collection Header**
   - Breadcrumb navigation
   - Collection title with mixed font
   - Collection description
   
2. **Filters Sidebar**
   - Category filter (dropdown/accordion)
   - Skin Type filter
   - Price range filter
   - Clear filters button
   
3. **Product Grid Header**
   - Product count display
   - Sort dropdown (Featured, Price Low-High, Price High-Low, Newest)
   
4. **Product Grid**
   - 4 columns desktop, 2 tablet, 1 mobile
   - Reuse existing product-card snippet
   - Pagination or "Load More" button
   
5. **Styling**
   - Sea Salt background
   - Proper spacing (120px sections)
   - Filter sidebar: 300px width
   - Main content: Remaining width

**Settings Schema**:
- Products per page
- Enable/disable filters
- Default sort order
- Show/hide collection description

---

### Phase 2: Product Detail Page (Priority 1)
**File**: `sections/product.liquid`

**Components Needed**:
1. **Product Gallery**
   - Main image display (zoom on hover)
   - Thumbnail navigation (4 images)
   - Image lightbox/modal
   
2. **Product Info**
   - Breadcrumb
   - Product title (mixed font)
   - Star rating + review count
   - Price display
   - Product description
   - Variant selector (if applicable)
   - Quantity selector
   - Add to Cart button
   - Buy Now button (optional)
   
3. **Product Details Accordions**
   - Benefits section
   - Ingredients list
   - How to Use instructions
   - Collapsible with +/- icons
   
4. **Brand Philosophy Section**
   - Oxford Blue background
   - "THE RITUAL" heading
   - Brand statement
   - CTA button
   
5. **Related Products**
   - "YOU MAY ALSO LIKE" heading
   - 4 product recommendations
   - Horizontal scroll on mobile

**New Snippets Needed**:
- `snippets/product-gallery.liquid`
- `snippets/product-accordion.liquid`
- `snippets/quantity-selector.liquid`
- `snippets/star-rating.liquid`

**Settings Schema**:
- Enable/disable sections
- Related products collection
- Accordion default states
- Gallery layout options

---

### Phase 3: Search Page (Priority 2)
**File**: `sections/search.liquid`

**Components Needed**:
1. **Search Header**
   - Search form (prominent)
   - Results count
   - Search term display
   
2. **Search Results**
   - Product grid (same as collection)
   - Article results (if applicable)
   - Page results (if applicable)
   - No results message
   
3. **Filters** (Optional)
   - Filter by type (Products, Articles, Pages)
   - Sort options

**Styling**:
- Clean, minimal design
- Same grid as collection page
- Prominent search bar
- Clear "No results" state

---

### Phase 4: Cart Page (Priority 2)
**File**: `sections/cart.liquid`

**Components Needed**:
1. **Cart Header**
   - "Your Cart" title
   - Item count
   
2. **Cart Items**
   - Product image
   - Product title + variant
   - Price per item
   - Quantity selector
   - Remove button
   - Line total
   
3. **Cart Summary**
   - Subtotal
   - Shipping estimate
   - Tax estimate (if applicable)
   - Total
   - Checkout button (Harvest Gold)
   - Continue Shopping link
   
4. **Empty Cart State**
   - Message
   - CTA to shop collections

**Styling**:
- Clean table/grid layout
- Prominent checkout button
- Clear pricing breakdown
- Mobile-optimized

---

### Phase 5: Checkout Styling (Priority 3)
**Note**: Full checkout customization requires Shopify Plus

**Approach**:
- Use `checkout.liquid` (if available)
- Apply brand colors via CSS
- Match typography
- Ensure mobile responsiveness

**Elements to Style**:
- Form fields
- Buttons
- Headers
- Progress indicators
- Payment icons

---

## 🎨 Design System Application

### Typography
- **Page Titles**: Mixed font (first letter Old London, rest Flama Condensed)
- **Section Headings**: Flama Condensed Bold, uppercase
- **Body Text**: Mosvita Regular
- **Labels**: Mosvita, uppercase, letter-spacing

### Colors
- **Background**: Sea Salt (#F9F9F9)
- **Text**: Oxford Blue (#0D1C31)
- **Accents**: Harvest Gold (#D6B93D)
- **Borders**: Dim Grey (#636363)
- **Highlights**: California Blue (#CAE0FF)

### Spacing
- **Section Spacing**: 120px desktop, 80px tablet, 60px mobile
- **Grid Gutter**: 24px
- **Component Spacing**: 8px, 16px, 24px, 32px, 48px

### Components
- **Buttons**: Rectangular, no border-radius
- **Inputs**: Minimal borders, clean styling
- **Dropdowns**: Custom styled with brand colors
- **Accordions**: +/- icons, thin dividers

---

## 📦 Reusable Components to Create

### 1. Product Gallery Snippet
```liquid
{% render 'product-gallery', 
  product: product,
  featured_image: product.featured_image,
  images: product.images
%}
```

### 2. Quantity Selector Snippet
```liquid
{% render 'quantity-selector',
  id: 'quantity',
  value: 1,
  min: 1
%}
```

### 3. Star Rating Snippet
```liquid
{% render 'star-rating',
  rating: product.metafields.reviews.rating,
  count: product.metafields.reviews.count
%}
```

### 4. Accordion Snippet
```liquid
{% render 'product-accordion',
  title: 'Benefits',
  content: product.metafields.custom.benefits,
  open: false
%}
```

### 5. Breadcrumb Snippet
```liquid
{% render 'breadcrumb',
  items: breadcrumb_items
%}
```

---

## 🔄 Implementation Order

### Week 1: Collection & Product Pages
1. ✅ Create breadcrumb snippet
2. ✅ Build Collection Page with filters
3. ✅ Create product gallery snippet
4. ✅ Create quantity selector snippet
5. ✅ Create star rating snippet
6. ✅ Create accordion snippet
7. ✅ Build Product Detail Page
8. ✅ Add related products section
9. ✅ Add brand philosophy section

### Week 2: Search & Cart Pages
1. ✅ Redesign Search Page
2. ✅ Redesign Cart Page
3. ✅ Create empty cart state
4. ✅ Add cart notifications/drawer (optional)
5. ✅ Style checkout (if Shopify Plus)

### Week 3: Testing & Refinement
1. ✅ Test all pages on mobile
2. ✅ Test all pages on tablet
3. ✅ Test all pages on desktop
4. ✅ Verify accessibility
5. ✅ Optimize performance
6. ✅ Cross-browser testing

---

## 📊 Success Criteria

### Collection Page
- [ ] Filters work correctly
- [ ] Sorting functions properly
- [ ] Product grid responsive
- [ ] Load more/pagination works
- [ ] Matches design aesthetic

### Product Page
- [ ] Image gallery functional
- [ ] Add to cart works
- [ ] Variant selection works
- [ ] Accordions expand/collapse
- [ ] Related products display
- [ ] Mobile-optimized

### Search Page
- [ ] Search returns accurate results
- [ ] Results display properly
- [ ] No results state clear
- [ ] Filters work (if implemented)

### Cart Page
- [ ] Items display correctly
- [ ] Quantity updates work
- [ ] Remove items works
- [ ] Totals calculate correctly
- [ ] Checkout button functional
- [ ] Empty state displays

---

## 🚀 Next Steps

1. **Start with Collection Page** - Most complex filtering logic
2. **Build Product Page** - Core conversion page
3. **Complete Search & Cart** - Essential functionality
4. **Test & Refine** - Ensure quality

---

**Last Updated**: 2026-04-29  
**Status**: 📝 Planning Complete - Ready for Implementation