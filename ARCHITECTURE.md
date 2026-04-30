# SON OF ADAM - Theme Architecture

## System Architecture Diagram

```mermaid
graph TD
    A[Theme Root] --> B[Configuration Layer]
    A --> C[Layout Layer]
    A --> D[Section Layer]
    A --> E[Component Layer]
    A --> F[Template Layer]
    
    B --> B1[settings_schema.json<br/>Brand Colors, Fonts, Spacing]
    B --> B2[settings_data.json<br/>Store-specific Settings]
    
    C --> C1[theme.liquid<br/>Main Layout Wrapper]
    C --> C2[CSS Variables<br/>Design System Tokens]
    C --> C3[critical.css<br/>Base Styles & Typography]
    
    D --> D1[Header Section<br/>Premium Navigation]
    D --> D2[Footer Section<br/>Oxford Blue Footer]
    D --> D3[Editorial Hero<br/>Full-width Hero]
    D --> D4[Featured Collection<br/>Product Grid]
    D --> D5[Image with Text<br/>50/50 Split]
    D --> D6[Multicolumn Categories<br/>Category Grid]
    D --> D7[Newsletter Signup<br/>Email Capture]
    D --> D8[Product Section<br/>PDP Layout]
    
    E --> E1[Button Snippet<br/>Primary & Secondary CTAs]
    E --> E2[Product Card Snippet<br/>Minimalist Cards]
    E --> E3[Badge Snippet<br/>New/Limited Labels]
    E --> E4[Accordion Snippet<br/>Expandable Content]
    
    F --> F1[index.json<br/>Homepage Template]
    F --> F2[product.json<br/>Product Page Template]
    F --> F3[collection.json<br/>Collection Template]
    
    D3 -.uses.-> E1
    D4 -.uses.-> E2
    D7 -.uses.-> E1
    D8 -.uses.-> E1
    D8 -.uses.-> E2
    D8 -.uses.-> E3
    D8 -.uses.-> E4
    
    F1 -.includes.-> D1
    F1 -.includes.-> D3
    F1 -.includes.-> D4
    F1 -.includes.-> D5
    F1 -.includes.-> D6
    F1 -.includes.-> D7
    F1 -.includes.-> D2
    
    F2 -.includes.-> D1
    F2 -.includes.-> D8
    F2 -.includes.-> D2
    
    style B1 fill:#D6B93D
    style C2 fill:#D6B93D
    style E1 fill:#CAE0FF
    style E2 fill:#CAE0FF
    style D3 fill:#0D1C31,color:#fff
    style D7 fill:#0D1C31,color:#fff
```

## Design System Token Flow

```mermaid
graph LR
    A[Design Document] --> B[settings_schema.json]
    B --> C[css-variables.liquid]
    C --> D[CSS Custom Properties]
    D --> E1[Sections]
    D --> E2[Snippets]
    D --> E3[critical.css]
    
    style A fill:#F9F9F9
    style B fill:#D6B93D
    style C fill:#D6B93D
    style D fill:#CAE0FF
```

## Component Hierarchy

```mermaid
graph TD
    A[Page Template] --> B[Header Group]
    A --> C[Main Content]
    A --> D[Footer Group]
    
    B --> B1[Header Section]
    
    C --> C1[Editorial Hero]
    C --> C2[Featured Collection]
    C --> C3[Image with Text]
    C --> C4[Multicolumn Categories]
    C --> C5[Newsletter Signup]
    
    D --> D1[Footer Section]
    
    C2 --> E1[Product Card x4]
    C4 --> E2[Category Card x3]
    
    E1 --> F1[Button: Add to Bag]
    E1 --> F2[Badge: New]
    
    C5 --> F3[Button: Subscribe]
    
    style A fill:#F9F9F9
    style B1 fill:#0D1C31,color:#fff
    style D1 fill:#0D1C31,color:#fff
    style F1 fill:#D6B93D
    style F3 fill:#D6B93D
```

## Responsive Layout Strategy

```mermaid
graph LR
    A[Mobile First<br/>375px+] --> B[Tablet<br/>768px+]
    B --> C[Desktop<br/>1024px+]
    C --> D[Wide Desktop<br/>1440px+]
    
    A --> A1[1 Column<br/>60px Spacing]
    B --> B1[2 Columns<br/>80px Spacing]
    C --> C1[3-4 Columns<br/>120px Spacing]
    D --> D1[Max 1200px Container<br/>120px Spacing]
    
    style A fill:#CAE0FF
    style B fill:#CAE0FF
    style C fill:#CAE0FF
    style D fill:#CAE0FF
```

## Data Flow: Product Display

```mermaid
sequenceDiagram
    participant Store as Shopify Store
    participant Template as product.json
    participant Section as product.liquid
    participant Snippet as product-card.liquid
    participant User as Customer
    
    Store->>Template: Product Data
    Template->>Section: Render Product Section
    Section->>Section: Display Main Product
    Section->>Snippet: Render Related Products
    Snippet->>Snippet: Apply Minimalist Styling
    Snippet->>User: Display Product Cards
    User->>Snippet: Hover on Card
    Snippet->>User: Show "Add to Bag" Button
```

## Typography Hierarchy

```mermaid
graph TD
    A[Typography System] --> B[Display Font: Cinzel]
    A --> C[Header Font: Oswald]
    A --> D[Body Font: Inter]
    
    B --> B1[Hero Titles<br/>80px / 1.1]
    B --> B2[Large Headlines<br/>60px / 1.1]
    
    C --> C1[Section Titles<br/>42px / 1.2 / UPPERCASE]
    C --> C2[Subheadings<br/>24px / 1.4]
    C --> C3[Navigation<br/>16px / UPPERCASE]
    
    D --> D1[Body Text<br/>16px / 1.6]
    D --> D2[Captions<br/>12px / 1.4 / UPPERCASE]
    
    style B fill:#0D1C31,color:#fff
    style C fill:#D6B93D
    style D fill:#636363,color:#fff
```

## Color Application Map

```mermaid
graph TD
    A[Color System] --> B[Backgrounds]
    A --> C[Text Colors]
    A --> D[Interactive Elements]
    A --> E[Accents]
    
    B --> B1[Sea Salt #F9F9F9<br/>Primary Background]
    B --> B2[Oxford Blue #0D1C31<br/>Header/Footer/Newsletter]
    B --> B3[White #FFFFFF<br/>Cards/Overlays]
    
    C --> C1[Oxford Blue #0D1C31<br/>Primary Text]
    C --> C2[Dim Grey #636363<br/>Secondary Text]
    C --> C3[White #FFFFFF<br/>Text on Dark BG]
    
    D --> D1[Harvest Gold #D6B93D<br/>Primary CTA]
    D --> D2[Oxford Blue #0D1C31<br/>Secondary CTA Border]
    
    E --> E1[Silver #B7B7B9<br/>Badges/Dividers]
    E --> E2[California Blue #CAE0FF<br/>Highlights/Info]
    
    style B2 fill:#0D1C31,color:#fff
    style D1 fill:#D6B93D
    style E2 fill:#CAE0FF
```

## Section Schema Pattern

```mermaid
graph TD
    A[Section Schema] --> B[Content Settings]
    A --> C[Layout Settings]
    A --> D[Style Settings]
    A --> E[Blocks]
    
    B --> B1[Text Fields]
    B --> B2[Image Pickers]
    B --> B3[Rich Text]
    B --> B4[URL Fields]
    
    C --> C1[Alignment Options]
    C --> C2[Column Count]
    C --> C3[Spacing Controls]
    C --> C4[Container Width]
    
    D --> D1[Color Pickers]
    D --> D2[Font Selectors]
    D --> D3[Border Options]
    D --> D4[Background Options]
    
    E --> E1[Repeatable Content]
    E --> E2[Drag & Drop Order]
    E --> E3[Individual Settings]
    
    style A fill:#D6B93D
```

## Performance Optimization Strategy

```mermaid
graph LR
    A[Performance] --> B[Image Optimization]
    A --> C[Font Loading]
    A --> D[CSS Strategy]
    A --> E[JavaScript]
    
    B --> B1[Lazy Loading]
    B --> B2[Responsive Images]
    B --> B3[WebP Format]
    
    C --> C1[Font Display Swap]
    C --> C2[Preload Critical Fonts]
    C --> C3[Subset Fonts]
    
    D --> D1[Critical CSS Inline]
    D --> D2[Component-level CSS]
    D --> D3[CSS Variables]
    
    E --> E1[Minimal JS]
    E --> E2[Defer Non-critical]
    E --> E3[Native Web Components]
    
    style A fill:#CAE0FF
```

---

## Key Architectural Decisions

### 1. **Mobile-First Responsive Design**
All sections built with mobile as the baseline, progressively enhancing for larger screens.

### 2. **Component-Based Architecture**
Reusable snippets (buttons, product cards, badges) used across multiple sections for consistency and maintainability.

### 3. **Schema-Driven Customization**
Every section includes comprehensive schema settings, allowing merchants to customize without code.

### 4. **CSS Variables for Design Tokens**
All design system values (colors, spacing, typography) defined as CSS custom properties for easy theming.

### 5. **Performance-First Approach**
Critical CSS inlined, lazy loading for images, optimized font loading strategy.

### 6. **Accessibility by Default**
Semantic HTML, proper ARIA labels, keyboard navigation, color contrast compliance.

### 7. **Modular Section System**
Each section is self-contained with its own styles and logic, making it easy to add, remove, or reorder.

---

## File Dependencies

### Critical Path
1. `settings_schema.json` → Defines available settings
2. `css-variables.liquid` → Converts settings to CSS variables
3. `critical.css` → Base styles using CSS variables
4. Sections → Use CSS variables for styling
5. Templates → Compose sections into pages

### Component Dependencies
- All sections depend on `css-variables.liquid`
- Product sections depend on `product-card.liquid`
- Interactive sections depend on `button.liquid`
- Product details depend on `accordion.liquid`

---

## Development Environment Setup

### Required Tools
- Shopify CLI (latest version)
- Node.js (for any build tools if needed)
- Git for version control
- VS Code with Shopify Liquid extension

### Local Development Workflow
```bash
# Start development server
shopify theme dev

# Push changes to development theme
shopify theme push --development

# Pull latest from store
shopify theme pull --development
```

---

This architecture ensures a scalable, maintainable, and performant Shopify theme that embodies the premium SON OF ADAM brand aesthetic while remaining flexible for future enhancements.