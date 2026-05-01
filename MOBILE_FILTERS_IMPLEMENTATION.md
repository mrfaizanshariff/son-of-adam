# Mobile-Responsive Filter Implementation

## Overview

This document describes the mobile-responsive filter solution implemented for the collection page. The solution provides an optimal user experience across all device sizes with a slide-out sidebar for mobile devices and dropdown filters for desktop.

## Features

### Desktop (1024px and above)
- **Horizontal filter bar** with dropdown panels
- **Three filter categories**: Category, Skin Type, and Price
- **Inline sorting** dropdown
- **Product count** display
- **Active filters** display with remove functionality

### Tablet & Mobile (below 1024px)
- **Mobile toggle button** to open filter sidebar
- **Slide-out sidebar** from the left side
- **Backdrop overlay** with semi-transparent background
- **Touch-friendly** interactions with larger tap targets (48px minimum)
- **Smooth animations** using CSS transitions
- **Scroll prevention** on body when sidebar is open
- **Apply/Clear buttons** for filter management

## Implementation Details

### HTML Structure

#### Mobile Toggle Button
```liquid
<button type="button" class="filter-bar__mobile-toggle" id="mobileFilterToggle">
  <svg>...</svg>
  <span>FILTERS</span>
</button>
```

#### Mobile Sidebar
```liquid
<div class="mobile-filter-sidebar" id="mobileFilterSidebar">
  <div class="mobile-filter-sidebar__header">
    <h2>FILTERS</h2>
    <button class="mobile-filter-sidebar__close">×</button>
  </div>
  <div class="mobile-filter-sidebar__content">
    <!-- Filter sections -->
  </div>
  <div class="mobile-filter-sidebar__footer">
    <button class="mobile-filter-sidebar__clear">Clear All</button>
    <button class="mobile-filter-sidebar__apply">Apply Filters</button>
  </div>
</div>
```

#### Backdrop Overlay
```liquid
<div class="mobile-filter-backdrop" id="mobileFilterBackdrop"></div>
```

### CSS Architecture

#### Responsive Breakpoints
- **Desktop**: 1024px and above
- **Tablet**: 768px - 1023px
- **Mobile**: Below 768px

#### Key CSS Classes

**Mobile Toggle Button**
- Hidden on desktop (`display: none`)
- Full-width button with centered content
- Touch-friendly size (48px min-height)
- Hover states for better UX

**Mobile Sidebar**
- Fixed positioning with slide animation
- 85% width, max 400px
- Full viewport height
- Smooth cubic-bezier transition
- Z-index: 1000

**Backdrop**
- Fixed full-screen overlay
- Semi-transparent black (rgba(0, 0, 0, 0.5))
- Fade in/out animation
- Z-index: 999

**Filter Options**
- Minimum 48px height for touch targets
- Larger checkboxes (20px × 20px)
- Increased padding and spacing
- Active state feedback

### JavaScript Functionality

#### Core Functions

**openMobileSidebar()**
- Adds `is-open` class to sidebar
- Shows backdrop overlay
- Prevents body scroll
- Syncs checkboxes from desktop to mobile

**closeMobileSidebar()**
- Removes `is-open` class
- Hides backdrop
- Restores body scroll

**applyMobileFilters()**
- Syncs mobile checkboxes back to desktop
- Triggers main filter function
- Closes sidebar automatically

**clearMobileFilters()**
- Unchecks all mobile filter checkboxes

#### Event Listeners

1. **Toggle button click** → Opens sidebar
2. **Close button click** → Closes sidebar
3. **Backdrop click** → Closes sidebar
4. **Apply button click** → Applies filters and closes
5. **Clear button click** → Clears all filters
6. **Escape key** → Closes sidebar
7. **Touch move** → Prevents scroll propagation

### Accessibility Features

- **ARIA labels** on buttons
- **Keyboard navigation** support (Escape key)
- **Focus management** for better screen reader support
- **Semantic HTML** structure
- **Touch-friendly** tap targets (minimum 48px)

### Performance Optimizations

1. **CSS Transitions** instead of JavaScript animations
2. **Hardware acceleration** with transform properties
3. **Passive event listeners** for touch events
4. **Debounced filter application** (500ms delay)
5. **Efficient DOM queries** with cached selectors

## User Experience Flow

### Mobile Filter Flow

1. User taps "FILTERS" button
2. Sidebar slides in from left with backdrop
3. User selects/deselects filter options
4. User taps "Apply Filters"
5. Filters are applied, sidebar closes
6. Products update based on selections

### Alternative Actions

- **Clear All**: Removes all filter selections
- **Close (×)**: Closes without applying changes
- **Backdrop tap**: Closes without applying changes
- **Escape key**: Closes without applying changes

## Browser Compatibility

- **Modern browsers**: Full support
- **iOS Safari**: Optimized with `-webkit-overflow-scrolling: touch`
- **Android Chrome**: Full support
- **Edge/Firefox**: Full support

## Testing Checklist

- [ ] Mobile toggle button appears below 1024px
- [ ] Desktop dropdowns hidden below 1024px
- [ ] Sidebar slides in smoothly
- [ ] Backdrop appears with correct opacity
- [ ] Body scroll prevented when sidebar open
- [ ] Checkboxes sync between desktop and mobile
- [ ] Apply button triggers filter function
- [ ] Clear button resets all selections
- [ ] Close button works correctly
- [ ] Backdrop click closes sidebar
- [ ] Escape key closes sidebar
- [ ] Touch interactions feel responsive
- [ ] Animations are smooth (60fps)
- [ ] No layout shifts or jumps

## Customization

### Adjusting Sidebar Width

```css
.mobile-filter-sidebar {
  width: 85%; /* Change percentage */
  max-width: 400px; /* Change max width */
}
```

### Changing Animation Speed

```css
.mobile-filter-sidebar {
  transition: left 0.3s cubic-bezier(0.4, 0, 0.2, 1); /* Adjust duration */
}
```

### Modifying Backdrop Opacity

```css
.mobile-filter-backdrop {
  background: rgba(0, 0, 0, 0.5); /* Adjust opacity */
}
```

### Adjusting Touch Target Size

```css
.mobile-filter-option {
  min-height: 48px; /* Increase for larger targets */
}
```

## Future Enhancements

1. **Swipe gestures** to close sidebar
2. **Filter count badge** on toggle button
3. **Animated filter transitions**
4. **Saved filter presets**
5. **Filter history**
6. **Advanced price range slider**

## Troubleshooting

### Sidebar not opening
- Check if JavaScript is loaded
- Verify element IDs match
- Check console for errors

### Filters not applying
- Ensure checkbox sync is working
- Verify `applyFilters()` function exists
- Check network requests

### Scroll issues
- Verify body overflow is being set
- Check for conflicting CSS
- Test touch event listeners

### Animation stuttering
- Check for heavy JavaScript operations
- Verify CSS transitions are hardware-accelerated
- Test on actual devices, not just emulators

## Support

For issues or questions about this implementation, refer to:
- `sections/collection.liquid` - Main implementation file
- `AGENTS.md` - Development guidelines
- `ARCHITECTURE.md` - Theme architecture documentation