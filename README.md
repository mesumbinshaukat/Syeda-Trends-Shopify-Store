# Syeda Trends - Shopify Theme

A modern, responsive Shopify theme with custom blocks and advanced features for an enhanced e-commerce experience.

## Features

### 🎨 Custom Blocks

#### Fixed Header (`ai_gen_block_8659d54.liquid`)
- **Fixed positioning** - Stays at the top of the page (full width)
- **Responsive design** - Adapts seamlessly to all screen sizes
- **Centered logo/site name** with customizable height and styling
- **Navigation menu** with collection exclusion options
- **Cart drawer** - Slides in from the right with real-time updates
- **Mobile hamburger menu** - Full-screen navigation drawer
- **Search modal** - Overlay search functionality
- **Account access** - Quick login/register link
- **Asynchronous cart updates** - No page reload required

**Key Features:**
- Full-width fixed header with no spacing
- Dynamic body padding to prevent content overlap
- Customizable colors, shadows, and padding
- Cart badge with item count
- Quantity controls in cart drawer
- Empty cart state handling

#### Product Display (`ai_gen_block_b127068.liquid`)
- Product image gallery with thumbnails
- Variant selection
- Quantity selector
- Add to Cart button with loading states
- Buy Now button (direct checkout)
- Expandable product description
- Image modal/lightbox
- **Asynchronous cart integration** - Dispatches `cart:updated` event

#### Shuffle Grid (`ai_gen_block_9273ecf.liquid`)
- Randomized product grid display
- Quick add-to-cart from grid
- Quick view functionality
- Hover effects and animations
- **Asynchronous cart integration**

## Installation

1. Clone or download this theme to your Shopify store
2. Upload to your Shopify admin under **Online Store > Themes**
3. Customize the theme settings as needed

## Configuration

### Header Settings

Navigate to **Theme Customizer > Sections** and configure:

- **Logo**: Upload your logo or set a site name
- **Logo Height**: 20-100px (default: 40px)
- **Navigation Menu**: Select which menu to display
- **Collection Exclusions**: Exclude up to 3 collections from navigation
- **Colors**: Header background, text, links, cart badge
- **Drawer Colors**: Background and text for cart/mobile drawers
- **Checkout Button**: Customize button colors

### Asynchronous Cart System

The theme includes a fully asynchronous cart system:

1. **Add to Cart** - Products can be added without page reload
2. **Cart Updates** - Header cart drawer updates automatically
3. **Event System** - Uses `cart:updated` event for synchronization

**How it works:**
```javascript
// When a product is added to cart
window.dispatchEvent(new Event('cart:updated'));

// Header listens and refreshes cart data
window.addEventListener('cart:updated', () => {
  this.refreshCart();
});
```

## Technical Details

### Cart API Endpoints

- `/cart/add.js` - Add items to cart
- `/cart/change.js` - Update item quantities
- `/cart.js` - Get current cart state

### Custom Events

- `cart:updated` - Triggered when cart contents change

### Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile responsive (iOS Safari, Chrome Mobile)
- Progressive enhancement approach

## Customization

### Adding New Products

Products automatically work with the asynchronous cart system. Ensure your product forms dispatch the `cart:updated` event:

```javascript
window.dispatchEvent(new Event('cart:updated'));
```

### Styling

All blocks use scoped CSS with unique IDs to prevent conflicts. Customize colors and spacing through the theme customizer or by editing the liquid files directly.

### Localization

Edit locale files in `/locales/` directory for multi-language support.

## File Structure

```
blocks/
├── ai_gen_block_8659d54.liquid  # Fixed Header
├── ai_gen_block_b127068.liquid  # Product Display
└── ai_gen_block_9273ecf.liquid  # Shuffle Grid

locales/
└── en.default.json              # English translations
```

## Development

### Prerequisites

- Shopify CLI (optional, for local development)
- Basic knowledge of Liquid, HTML, CSS, JavaScript

### Best Practices

1. Test all changes in a development theme first
2. Clear browser cache when testing JavaScript changes
3. Use browser DevTools to debug cart functionality
4. Monitor console for any errors

## Troubleshooting

### Cart not updating asynchronously

1. Check browser console for JavaScript errors
2. Verify `cart:updated` event is being dispatched
3. Ensure header block is present on the page
4. Clear browser cache and reload

### Header overlapping content

- Body padding is automatically calculated based on header height
- If issues persist, check for conflicting CSS

### Mobile menu not working

- Ensure JavaScript is enabled
- Check z-index values aren't being overridden
- Verify drawer overlay is present in DOM

## Support

For issues or questions:
1. Check browser console for errors
2. Verify all blocks are properly configured
3. Test in incognito/private mode to rule out cache issues

## Credits

Built with modern web standards and Shopify best practices.

## License

Proprietary - All rights reserved.
