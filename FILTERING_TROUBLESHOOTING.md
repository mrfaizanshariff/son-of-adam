# Collection Filtering Troubleshooting Guide

## Current Issue
Tag-based filters (Category and Skin Type) are not filtering products, while Price filters work correctly.

## Root Cause Analysis

### Why Price Filtering Works
Price filtering uses Shopify's native `filter.v.price.gte` and `filter.v.price.lte` parameters, which are automatically supported by Shopify's collection filtering system.

### Why Tag Filtering Doesn't Work
Tag filtering using `filter.p.tag` requires specific setup in Shopify:

1. **Shopify's Storefront Filtering API**: Modern Shopify themes use the Storefront Filtering API which requires:
   - Collection filters to be enabled in theme settings
   - Proper filter configuration in the collection template
   - Ajax-based filtering or full page reloads with filter parameters

2. **Tag Format**: Tags must match exactly what's in Shopify, including the prefix (e.g., `category:Face Care`)

3. **Collection Object**: The `collection.products` object should automatically be filtered when URL parameters are present, BUT this only works if:
   - The theme is using Shopify 2.0+ architecture
   - The collection template properly handles filter parameters
   - The filters are configured correctly

## Solution Options

### Option 1: Use Shopify's Native Filtering (Recommended)
Shopify 2.0+ themes should use the `collection.filters` object instead of manual URL parameter handling.

**Implementation:**
```liquid
{% for filter in collection.filters %}
  {% case filter.type %}
    {% when 'list' %}
      {%- comment -%} For tag-based filters {%- endcomment -%}
      {% for value in filter.values %}
        <input type="checkbox" 
               name="{{ filter.param_name }}" 
               value="{{ value.value }}"
               {% if value.active %}checked{% endif %}>
        {{ value.label }} ({{ value.count }})
      {% endfor %}
    {% when 'price_range' %}
      {%- comment -%} For price filters {%- endcomment -%}
  {% endcase %}
{% endfor %}
```

### Option 2: Client-Side Filtering (Current Approach - Needs Fix)
If using client-side filtering with URL parameters, the issue is that `collection.products` returns ALL products, not filtered ones.

**Fix Required:**
1. Check if Shopify is actually filtering the collection
2. Verify the URL parameters are in the correct format
3. Ensure the collection template supports filtering

### Option 3: Ajax-Based Filtering
Use Shopify's Section Rendering API to reload just the product grid:

```javascript
fetch(`/collections/${collectionHandle}?section_id=collection&${filterParams}`)
  .then(response => response.text())
  .then(html => {
    // Update product grid with filtered results
  });
```

## Immediate Debugging Steps

### 1. Check if Shopify is Filtering
Add this debug code to see if Shopify is actually filtering:

```liquid
{%- comment -%} DEBUG: Check if filtering is working {%- endcomment -%}
<div style="background: yellow; padding: 10px; margin: 10px 0;">
  <strong>DEBUG INFO:</strong><br>
  Total products in collection: {{ collection.all_products_count }}<br>
  Products being displayed: {{ collection.products.size }}<br>
  Current URL: {{ request.path }}?{{ request.query_string }}<br>
  
  {% if collection.filters.size > 0 %}
    <br><strong>Available Filters:</strong><br>
    {% for filter in collection.filters %}
      - {{ filter.label }} ({{ filter.type }})<br>
    {% endfor %}
  {% else %}
    <br><strong>No filters available</strong> - This means Shopify filtering is not enabled
  {% endif %}
</div>
```

### 2. Verify Tag Format
Check that product tags in Shopify admin match exactly:
- ✅ `category:Face Care`
- ❌ `category: Face Care` (space after colon)
- ❌ `Category:Face Care` (wrong capitalization)

### 3. Check URL Parameters
When a filter is selected, the URL should look like:
```
/collections/all-products?filter.p.tag=category:face-care
```

Note: Shopify URL-encodes spaces, so "Face Care" becomes "face-care" or "Face%20Care"

### 4. Verify Collection Template
Check `templates/collection.json` to ensure it's using the correct section and settings.

## Recommended Fix

The most reliable solution is to use Shopify's native `collection.filters` object. This requires:

1. **Enable Filtering in Theme Settings**
2. **Update Collection Template** to use `collection.filters`
3. **Modify JavaScript** to work with Shopify's filter format

This approach ensures:
- Automatic product counting
- Proper URL parameter handling
- Server-side filtering (faster, more reliable)
- SEO-friendly filter URLs

## Alternative: Manual Client-Side Filtering

If Shopify's native filtering isn't available, implement true client-side filtering:

```javascript
function filterProducts() {
  const selectedCategories = getSelectedFilters('category');
  const selectedSkinTypes = getSelectedFilters('skin-type');
  
  document.querySelectorAll('.product-card').forEach(card => {
    const productTags = card.dataset.tags.split(',');
    let show = true;
    
    // Check category filter
    if (selectedCategories.length > 0) {
      show = selectedCategories.some(cat => 
        productTags.includes(`category:${cat}`)
      );
    }
    
    // Check skin type filter
    if (show && selectedSkinTypes.length > 0) {
      show = selectedSkinTypes.some(type => 
        productTags.includes(`skin-type:${type}`)
      );
    }
    
    card.style.display = show ? 'block' : 'none';
  });
}
```

This requires adding `data-tags` attribute to each product card:
```liquid
<div class="product-card" data-tags="{{ product.tags | join: ',' }}">
```

## Next Steps

1. Add debug code to determine if Shopify filtering is working
2. Check if `collection.filters` object is available
3. Based on findings, implement either:
   - Native Shopify filtering (preferred)
   - Client-side filtering with product data attributes
   - Ajax-based filtering with Section Rendering API

## Testing Checklist

- [ ] Add debug code to collection page
- [ ] Check browser console for JavaScript errors
- [ ] Verify URL parameters are being generated correctly
- [ ] Check if `collection.products.size` changes when filters are applied
- [ ] Test with different tag combinations
- [ ] Verify product tags in Shopify admin match expected format
- [ ] Check if `collection.filters` object exists and has data