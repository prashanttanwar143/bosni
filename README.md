# Bsoni Jewellers Website - README

## Overview
This is a static HTML/CSS/JavaScript website for Bsoni Jewellers, built with Tailwind CSS and featuring a responsive design for showcasing jewelry products.

## File Structure
- `demo.html` - Main homepage with product showcase, categories, and contact information
- `product-detail.html` - Individual product detail pages

## How to Add Products

### Step 1: Add Product Data
Edit `product-detail.html` and locate the `products` JavaScript object (around line 280). Add a new entry:

```javascript
'7': {
  name: 'Your Product Name',
  category: 'Necklaces', // or 'Earrings', 'Rings', 'Bangles', 'Bridal Sets'
  price: '₹1,25,000',
  originalPrice: '₹1,50,000', // optional, leave empty string if no discount
  description: 'Detailed description of your product...',
  length: '16 inches',
  weight: '35 grams',
  material: 'Gold & Diamonds',
  purity: '22K Gold',
  images: [
    'path/to/image1.jpg',
    'path/to/image2.jpg',
    'path/to/image3.jpg',
    'path/to/image4.jpg'
  ]
}
```

### Step 2: Add Product Card to Homepage
Edit `demo.html` and find the products carousel section (around line 450). Add a new product card:

```html
<div id="product-7" class="product-card flex-shrink-0 w-[260px] sm:w-[280px] md:w-[300px] bg-white/5 backdrop-blur-sm rounded-2xl overflow-hidden border border-white/10 group cursor-pointer" data-category="necklaces" onclick="viewProduct('7')">
  <div class="relative overflow-hidden aspect-[3/4]">
    <img src="path/to/main-image.jpg" alt="Your Product Name" class="product-image w-full h-full object-cover">
    <!-- Optional: Add badge -->
    <span class="absolute top-3 left-3 bg-gold-400 text-maroon-900 text-[10px] font-semibold px-2.5 py-1 rounded-full">NEW</span>
    <!-- Wishlist button -->
    <button class="absolute top-3 right-3 w-8 h-8 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center text-white hover:bg-gold-400 hover:text-maroon-900 transition-all opacity-0 group-hover:opacity-100">
      <i data-lucide="heart" class="w-4 h-4"></i>
    </button>
  </div>
  <div class="p-4 sm:p-5">
    <p class="font-inter text-gold-400 text-[10px] tracking-widest uppercase">Necklaces</p>
    <h3 class="font-cinzel text-white text-base sm:text-lg font-semibold mt-1">Your Product Name</h3>
    <div class="flex items-center gap-1 mt-1.5">
      <!-- Star ratings -->
      <i data-lucide="star" class="w-3.5 h-3.5 text-gold-400 fill-gold-400"></i>
      <!-- Add 4 more stars -->
      <span class="font-inter text-white/50 text-xs ml-1">(42)</span>
    </div>
    <div class="flex items-center gap-2 mt-3">
      <span class="font-cinzel text-gold-400 text-lg sm:text-xl font-bold">₹1,25,000</span>
      <span class="font-inter text-white/40 text-sm line-through">₹1,50,000</span> <!-- optional -->
    </div>
  </div>
</div>
```

## How to Set Prices
1. In the product data object, set the `price` field to your desired price (e.g., '₹1,25,000')
2. Optionally set `originalPrice` for showing discounts
3. Update the price display in the product card HTML

## How to Add Product Details
Product details are automatically populated from the product data object. To modify:
- **Description**: Edit the `description` field
- **Specifications**: Update `length`, `weight`, `material`, `purity` fields
- **Care Instructions**: These are hardcoded in the HTML, edit the `<ul>` in product-detail.html

## How to Change Icons
The website uses Lucide icons. To change an icon:
1. Find the icon element: `<i data-lucide="icon-name" class="..."></i>`
2. Replace `icon-name` with any Lucide icon name from https://lucide.dev/
3. The icons are automatically rendered by the Lucide script

Common icons used:
- `heart` - Wishlist
- `star` - Ratings
- `shopping-cart` - Cart
- `user` - Account
- `search` - Search
- `menu` - Mobile menu
- `instagram` - Social media

## How to Add Product Pictures
1. **Host your images**: Upload images to your web server or use a service like Cloudinary, AWS S3, etc.
2. **Update image paths**: Replace placeholder URLs with your actual image URLs
3. **Image requirements**:
   - Main product image: High quality, square aspect ratio recommended
   - Gallery images: 4 images per product, same product from different angles
   - Format: JPG, PNG, or WebP
   - Size: Optimize for web (under 500KB per image)

Example:
```javascript
images: [
  'https://your-domain.com/products/necklace-1.jpg',
  'https://your-domain.com/products/necklace-2.jpg',
  'https://your-domain.com/products/necklace-3.jpg',
  'https://your-domain.com/products/necklace-4.jpg'
]
```

## How to Add New Sections
To add a new section to the homepage:

### Step 1: Choose Location
Decide where to place the section in `demo.html`. Common locations:
- After the hero section
- Before the bestsellers
- Before the footer

### Step 2: Create Section HTML
Use this template structure:

```html
<!-- ============ YOUR SECTION NAME ============ -->
<section class="py-16 sm:py-20 md:py-28 bg-gradient-to-b from-maroon-900 via-maroon-800 to-maroon-900 relative overflow-hidden">
  <!-- Optional: Decorative background -->
  <div class="absolute inset-0 opacity-5">
    <div class="absolute top-10 left-10 w-72 h-72 rounded-full border border-gold-400"></div>
  </div>

  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
    <!-- Section Header -->
    <div class="text-center mb-12 md:mb-16 reveal">
      <span class="font-inter text-gold-400 text-xs tracking-[0.4em] uppercase">Section Subtitle</span>
      <h2 class="font-cinzel text-3xl sm:text-4xl md:text-5xl font-bold text-white mt-3">Section Title</h2>
      <div class="ornament-divider mt-4">
        <span class="text-gold-400 text-xl">◆</span>
      </div>
    </div>

    <!-- Section Content -->
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
      <!-- Your content here -->
    </div>
  </div>
</section>
```

### Step 3: Add Navigation (if needed)
If you want the section to be accessible from the navigation menu:
1. Add an id to the section: `<section id="your-section">`
2. Add to the navigation: `<a href="#your-section" class="nav-link ...">Your Section</a>`

### Step 4: Styling Tips
- Use Tailwind classes for responsive design
- Follow the color scheme: maroon, gold, royal, emerald
- Use the existing CSS classes like `.ornament-divider`, `.gold-shimmer`
- Add animations with `.animate-fade-in-up` and delay classes

## Customization Tips
- **Colors**: Modify the Tailwind config in the `<script>` tag at the top of each file
- **Fonts**: Currently using Cinzel and Inter from Google Fonts
- **Animations**: Custom CSS animations are defined in the `<style>` section
- **Responsive**: Use Tailwind's responsive prefixes (sm:, md:, lg:) for mobile-first design

## Deployment
1. Upload all files to your web server
2. Ensure images are accessible via the URLs you specified
3. Test all links and functionality
4. For production, consider minifying CSS/JS and optimizing images

## Support
If you need help with specific customizations, refer to:
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Lucide Icons](https://lucide.dev/)
- [MDN Web Docs](https://developer.mozilla.org/)