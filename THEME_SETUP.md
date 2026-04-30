# SON OF ADAM - Theme Setup Guide

## 🎉 Implementation Complete!

The SON OF ADAM premium grooming theme has been successfully built based on the design specifications. This guide will help you set up and customize the theme.

---

## 📦 What's Been Built

### ✅ Core Components
- **Design System**: Complete color palette, typography scale, and spacing system
- **Header**: Premium navigation with sticky header, search, account, and cart
- **Footer**: Multi-column layout with social links and payment icons
- **Reusable Components**: Button and product card snippets

### ✅ Homepage Sections
1. **Editorial Hero** - Full-width hero with background image/video support
2. **Featured Collection** - Product grid with minimalist cards
3. **Image with Text** - 50/50 split layout for lifestyle content
4. **Multicolumn Categories** - Browse categories grid
5. **Newsletter Signup** - Email capture with testimonial
6. **Additional Image with Text** - Secondary content section

### ✅ Design System Features
- **Colors**: Sea Salt, Oxford Blue, Harvest Gold, Silver, Dim Grey
- **Typography**: Cinzel (display), Oswald (headers), Inter (body)
- **Responsive**: Mobile-first design with tablet and desktop breakpoints
- **Accessibility**: WCAG AA compliant with proper focus states

---

## 🚀 Getting Started

### 1. Install Shopify CLI
```bash
npm install -g @shopify/cli @shopify/theme
```

### 2. Connect to Your Store
```bash
cd son-of-adam
shopify theme dev
```

### 3. Preview the Theme
The CLI will provide a preview URL. Open it in your browser to see the theme.

---

## 🎨 Customization Guide

### Theme Settings
Navigate to **Online Store > Themes > Customize** in your Shopify admin.

#### Global Settings
1. **Typography**
   - Display Font: Cinzel (for hero headlines)
   - Header Font: Oswald (for navigation and titles)
   - Body Font: Inter (for content)

2. **Colors**
   - Sea Salt: `#F9F9F9` (Primary Background)
   - Oxford Blue: `#0D1C31` (Secondary Background)
   - Harvest Gold: `#D6B93D` (Primary CTA)
   - Silver: `#B7B7B9` (Secondary Accent)
   - Dim Grey: `#636363` (Secondary Text)

3. **Layout**
   - Max Container Width: 1200px
   - Section Spacing: 120px (desktop), 80px (tablet), 60px (mobile)
   - Grid Gutter: 24px

### Header Customization
- Upload your logo (recommended: 300px wide)
- Configure navigation menu
- Enable/disable sticky header
- Enable/disable search

### Footer Customization
- Upload footer logo
- Add tagline
- Configure social media links (Facebook, Instagram, Twitter)
- Set up three menu columns: Shop, About, Support
- Enable/disable payment icons

---

## 📄 Section Configuration

### Editorial Hero
**Location**: Homepage top section

**Settings**:
- Background Image: 1920x1080px recommended
- Video URL: Optional MP4 video
- Overlay Opacity: 0-80%
- Heading: Use `[gold]text[/gold]` to highlight in gold
- Primary & Secondary CTAs

**Example**:
```
Heading: GROOMING AS [gold]TIMELESS[/gold] AS MAN
```

### Featured Collection
**Settings**:
- Select a collection
- Products to show: 2-12
- Products per row: 2, 3, or 4
- View all link text

### Image with Text
**Settings**:
- Image position: Left or Right
- Background color: None, Sea Salt, or Oxford Blue
- Subheading, Heading, Description
- Button style: Primary or Secondary

**Use Cases**:
- Brand story
- Product features
- Sustainability message
- Craftsmanship details

### Multicolumn Categories
**Settings**:
- Heading
- Columns: 2, 3, or 4
- Add category blocks with:
  - Square images (800x800px)
  - Title and description
  - Overlay text (shown on hover)
  - Link to collection

### Newsletter Signup
**Settings**:
- Optional testimonial section
- Heading and description
- Email placeholder text
- Success message
- Privacy notice

---

## 🖼️ Image Guidelines

### Recommended Sizes
- **Hero Background**: 1920x1080px (16:9)
- **Product Images**: 800x1067px (3:4 portrait)
- **Category Images**: 800x800px (1:1 square)
- **Lifestyle Images**: 1200x800px (3:2)
- **Logo**: 300px wide, transparent background

### Image Optimization
- Use WebP format when possible
- Keep file sizes under 200KB
- Use descriptive alt text for accessibility
- Compress images before uploading

---

## 🎯 Content Strategy

### Homepage Flow
1. **Hero**: Capture attention with bold statement
2. **Featured Products**: Showcase bestsellers
3. **Brand Story**: Build trust with philosophy
4. **Categories**: Guide discovery
5. **Testimonial**: Social proof
6. **Newsletter**: Capture leads

### Writing Guidelines
- **Headlines**: Bold, masculine, confident
- **Body Copy**: Clear, honest, benefit-focused
- **CTAs**: Action-oriented ("Shop Essentials", "Discover", "Join Now")
- **Tone**: Premium but approachable, editorial style

---

## 📱 Responsive Behavior

### Breakpoints
- **Mobile**: 0-767px (1 column)
- **Tablet**: 768-1023px (2 columns)
- **Desktop**: 1024-1439px (3-4 columns)
- **Wide**: 1440px+ (max 1200px container)

### Mobile Optimizations
- Hamburger menu for navigation
- Stacked layouts for image-with-text
- Full-width buttons
- Touch-friendly 44px minimum targets
- Optimized font sizes

---

## 🔧 Advanced Customization

### Adding Custom CSS
Edit `assets/critical.css` for global styles or add CSS within section files using `{% stylesheet %}` tags.

### Modifying Colors
Update `config/settings_schema.json` and adjust in theme customizer, or directly edit CSS variables in `snippets/css-variables.liquid`.

### Creating New Sections
1. Create new file in `sections/` directory
2. Follow existing section structure
3. Include `{% schema %}` for customization
4. Add to templates as needed

### Font Alternatives
If you have custom fonts:
1. Upload to `assets/` directory
2. Update `snippets/css-variables.liquid`
3. Modify font-face declarations

---

## ✅ Pre-Launch Checklist

### Content
- [ ] Upload all product images
- [ ] Write product descriptions
- [ ] Create collections
- [ ] Add brand story page
- [ ] Set up navigation menus
- [ ] Configure footer links

### Settings
- [ ] Upload logo
- [ ] Set brand colors
- [ ] Configure fonts
- [ ] Add social media links
- [ ] Set up payment methods
- [ ] Configure shipping

### Testing
- [ ] Test on mobile devices
- [ ] Test on tablets
- [ ] Test on desktop
- [ ] Check all links
- [ ] Test checkout process
- [ ] Verify newsletter signup
- [ ] Test search functionality

### SEO
- [ ] Add meta descriptions
- [ ] Optimize image alt text
- [ ] Set up Google Analytics
- [ ] Submit sitemap
- [ ] Configure social sharing

---

## 🐛 Troubleshooting

### Images Not Displaying
- Check file paths in section settings
- Verify images are uploaded to Shopify
- Ensure correct image picker settings

### Fonts Not Loading
- Verify font selections in theme settings
- Check browser console for errors
- Clear browser cache

### Layout Issues
- Check responsive breakpoints
- Verify CSS grid settings
- Test in different browsers

### Section Not Appearing
- Ensure section is added to template
- Check section visibility settings
- Verify block order in JSON

---

## 📚 Resources

### Shopify Documentation
- [Theme Development](https://shopify.dev/docs/themes)
- [Liquid Reference](https://shopify.dev/docs/api/liquid)
- [Section Schema](https://shopify.dev/docs/themes/architecture/sections/section-schema)

### Design Inspiration
- Tom Ford Grooming
- Aesop
- Horace
- Haeckels

### Support
- Shopify Community Forums
- Theme Check for validation
- Shopify CLI documentation

---

## 🎨 Design Tokens Reference

### Colors
```css
--color-sea-salt: #F9F9F9
--color-oxford-blue: #0D1C31
--color-harvest-gold: #D6B93D
--color-silver: #B7B7B9
--color-dim-grey: #636363
--color-california-blue: #CAE0FF
--color-white: #FFFFFF
```

### Typography
```css
--font-display: 'Cinzel', serif
--font-header: 'Oswald', sans-serif
--font-body: 'Inter', sans-serif
```

### Spacing
```css
--spacing-xs: 8px
--spacing-sm: 16px
--spacing-md: 24px
--spacing-lg: 32px
--spacing-xl: 48px
--spacing-2xl: 64px
--spacing-3xl: 80px
--spacing-4xl: 120px
```

---

## 🚀 Next Steps

1. **Upload Content**: Add your products, images, and copy
2. **Customize Settings**: Adjust colors, fonts, and layout in theme editor
3. **Test Thoroughly**: Check all pages and functionality
4. **Launch**: Publish your theme and go live!

---

## 📞 Need Help?

For questions or issues:
1. Check this documentation
2. Review Shopify's theme documentation
3. Use Shopify CLI's built-in help: `shopify theme --help`
4. Consult Shopify Community Forums

---

**Built with ❤️ for SON OF ADAM**

*Grooming as timeless as man.*