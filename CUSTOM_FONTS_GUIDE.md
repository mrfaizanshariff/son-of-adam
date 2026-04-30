# Custom Fonts Integration Guide - SON OF ADAM

## 📦 Font Files You Have
1. **Old London** - Display font for hero headlines
2. **Flama Condensed** - Header font for navigation and titles
3. **Mosvita** - Body font for content

## 🚀 Step-by-Step Integration

### Step 1: Upload Font Files to Shopify

1. **Prepare Your Font Files**
   - Ensure you have `.woff` and `.woff2` formats (best for web)
   - If you only have `.ttf` or `.otf`, you'll need to convert them
   - Recommended converter: https://transfonter.org/

2. **Upload to Shopify Assets**
   ```bash
   # Using Shopify CLI
   cd son-of-adam/assets
   
   # Copy your font files here with these names:
   # - old-london.woff2
   # - old-london.woff
   # - flama-condensed.woff2
   # - flama-condensed.woff
   # - mosvita-regular.woff2
   # - mosvita-regular.woff
   # - mosvita-bold.woff2
   # - mosvita-bold.woff
   ```

3. **Upload via Shopify Admin** (Alternative)
   - Go to **Online Store > Themes > Actions > Edit code**
   - Click **Assets** folder
   - Click **Add a new asset**
   - Upload each font file

### Step 2: Update CSS Variables

Once fonts are uploaded, I'll update the `snippets/css-variables.liquid` file to load them.

### Step 3: Remove Google Fonts

I'll remove the Google Fonts references and use your custom fonts instead.

## 📝 Font File Naming Convention

Please name your font files as follows when uploading:

### Old London (Display Font)
- `old-london-regular.woff2`
- `old-london-regular.woff`

### Flama Condensed (Header Font)
- `flama-condensed-regular.woff2`
- `flama-condensed-regular.woff`
- `flama-condensed-bold.woff2`
- `flama-condensed-bold.woff`

### Mosvita (Body Font)
- `mosvita-regular.woff2`
- `mosvita-regular.woff`
- `mosvita-bold.woff2`
- `mosvita-bold.woff`
- `mosvita-italic.woff2` (if available)
- `mosvita-italic.woff` (if available)

## 🔧 What I'll Update

After you upload the fonts, I'll modify:

1. **`snippets/css-variables.liquid`**
   - Add @font-face declarations
   - Update font-family variables

2. **`config/settings_schema.json`**
   - Remove Google Font pickers
   - Add custom font options

## ⚡ Quick Start

1. Upload all font files to `son-of-adam/assets/` folder
2. Let me know when they're uploaded
3. I'll update the code to use them

## 📋 Font Formats Priority

The theme will load fonts in this order:
1. `.woff2` (best compression, modern browsers)
2. `.woff` (fallback for older browsers)

## 🎯 Expected Result

After integration:
- **Hero Headlines**: Old London font
- **Navigation & Titles**: Flama Condensed font
- **Body Content**: Mosvita font
- **Faster loading**: No external Google Fonts requests
- **Better brand consistency**: Exact fonts from design

## 📞 Ready to Proceed?

Once you've uploaded the font files to the `assets` folder, let me know and I'll:
1. Create the @font-face declarations
2. Update all font references
3. Test the implementation
4. Provide fallback fonts for safety

---

**Note**: Make sure you have the legal rights to use these fonts on your website. Custom fonts should be properly licensed for web use.