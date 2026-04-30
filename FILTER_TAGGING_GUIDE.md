# Dynamic Filter Tagging Guide for SON OF ADAM

## Overview
The collection page filters are now **dynamically generated** from product tags. This means filters automatically populate based on the tags assigned to products in your Shopify store.

## How It Works

### Tag Naming Convention
Filters use a **prefix-based tagging system**:

```
prefix:value
```

**Important:** Tags must include the colon (`:`) with no spaces before or after it. The system uses Shopify's `filter.p.tag` parameter for tag-based filtering.

### Supported Filter Types

#### 1. Category Filter
**Tag Format:** `category:VALUE`

**Examples:**
- `category:Face`
- `category:Beard`
- `category:Body`
- `category:Shaving`
- `category:Hair`

**How to Use:**
1. Go to Shopify Admin → Products
2. Select a product
3. Add tags like `category:Face Care`
4. The filter will automatically show "Face Care" with the product count

#### 2. Skin Type Filter
**Tag Format:** `skin-type:VALUE`

**Examples:**
- `skin-type:Normal`
- `skin-type:Dry`
- `skin-type:Oily`
- `skin-type:Combination`
- `skin-type:Sensitive`

**How to Use:**
1. Go to Shopify Admin → Products
2. Select a product
3. Add tags like `skin-type:Oily`
4. The filter will automatically show "Oily" with the product count

#### 3. Price Filter
The price filter uses Shopify's built-in price range filtering and doesn't require tags.

## Important Notes

### Automatic Product Counting
- The system automatically counts how many products have each tag
- Only tags with at least 1 product are displayed
- Product counts update automatically when products are added/removed

### Fallback Behavior
If no tags with the correct prefix are found, the system shows default options with (0) counts. This ensures the filter UI doesn't break.

### Tag Display
- Tags are automatically formatted for display
- `category:Face Care` displays as "Face Care"
- `skin-type:Oily` displays as "Oily"
- Capitalization from your tags is preserved

## Best Practices

### 1. Consistent Naming
Use consistent capitalization and spelling:
- ✅ `category:Face Care`
- ✅ `skin-type:Oily`
- ❌ `category: Face Care` (space after colon)
- ❌ `category :Face Care` (space before colon)
- ❌ `Category:Face Care` (wrong prefix capitalization)

### 2. Multiple Tags Per Product
Products can have multiple filter tags:
```
Product: "Hydrating Face Serum"
Tags: category:Face Care, skin-type:Dry, skin-type:Normal
```

### 3. Avoid Duplicate Prefixes
Don't use the filter prefixes for other purposes:
- ✅ `category:Face Care` (filter tag)
- ✅ `bestseller` (regular tag)
- ❌ `category:New Arrival` (confusing - use regular tag instead)

### 4. Tag Organization
Keep filter tags separate from other tags:
```
Filter Tags: category:Face Care, skin-type:Oily
Other Tags: bestseller, new-arrival, gift-set
```

## Adding New Filter Categories

To add a new filter type (e.g., "Concern"):

1. Add products with tags like `concern:Anti-Aging`, `concern:Acne`, etc.
2. Edit `sections/collection.liquid`
3. Copy the Category or Skin Type filter dropdown structure
4. Change the prefix from `category:` or `skin-type:` to `concern:`
5. Update the filter name and data attributes

## Testing Your Filters

1. **Add Tags to Products:**
   - Go to Products in Shopify Admin
   - Add tags like `category:Face Care` to several products

2. **View Collection Page:**
   - Navigate to any collection
   - The Category filter should show "Face Care" with the correct count

3. **Test Filtering:**
   - Click the filter checkbox
   - Products should filter correctly
   - URL should update with filter parameters

## Troubleshooting

### Filter Shows (0) Products
- Check that products have the correct tag format: `prefix:value`
- Verify products are in the collection you're viewing
- Check for typos in tag names

### Filter Not Appearing
- Ensure at least one product has a tag with the correct prefix
- Check that the tag format matches exactly: `category:` not `Category:` or `category-` or `category :`
- Verify there are no spaces around the colon

### Products Not Filtering
- Verify the JavaScript is working (check browser console for errors)
- Ensure tag values match between the filter and products exactly
- Check that URL parameters are being generated correctly (should be `filter.p.tag=category:Face%20Care`)
- Verify products are actually tagged with the full tag including prefix (e.g., `category:Face Care`)
- Clear browser cache and reload the page

## Example Product Setup

**Product: "Charcoal Face Wash"**
```
Tags:
- category:Face Care
- skin-type:Oily
- skin-type:Combination
- bestseller
- new-arrival
```

**Result:**
- Appears in "Face Care" category filter
- Appears in "Oily" skin type filter
- Appears in "Combination" skin type filter
- Can be filtered by any combination of these

## Support

For questions or issues with the dynamic filter system, refer to:
- `sections/collection.liquid` (lines 42-100 for filter implementation)
- Shopify's tag documentation
- This guide