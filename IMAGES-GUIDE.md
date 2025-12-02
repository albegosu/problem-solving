# Images Guide for Landing Page

## 📁 Where to Add Images

Add your images to: `/src/assets/`

## 🎨 Recommended Images

### 1. **Hero Image** (Optional)
- **Filename**: `hero-illustration.svg` or `hero-illustration.png`
- **Size**: 800x600px (or similar ratio)
- **Purpose**: Main illustration for the hero section
- **Ideas**: Abstract problem-solving visual, methodology diagram, team collaboration

### 2. **Methodology Image** (Optional)
- **Filename**: `methodology.svg` or `methodology.png`
- **Size**: 1200x600px (landscape)
- **Purpose**: Visual representation of design thinking process
- **Ideas**: Flowchart, process diagram, design thinking stages

### 3. **Einstein Image** (Creativity Section)
- **Filename**: `einstein.jpg` or `einstein.png`
- **Size**: 600x800px (portrait)
- **Purpose**: Einstein portrait for the creativity section
- **Ideas**: Black and white Einstein photo, positioned at right edge
- **Note**: Already configured in the code!

### 4. **Munari Method Image** (Optional)
- **Filename**: `munari-method.svg` or `munari-method.png`
- **Size**: 1200x800px
- **Purpose**: Visual representation of the 6-step Munari method
- **Ideas**: Numbered steps diagram, process flow, methodology visualization

## 🚀 How to Add Images

### Step 1: Add Image Files
Place your images in the `src/assets/` folder:
```
src/
  assets/
    hero-illustration.svg
    methodology.svg
    creativity.svg
    munari-method.svg
```

### Step 2: Update CSS Variable for Hero Background (Already Done!)
The hero image is loaded as a background via CSS variable in `src/style.css`:

```css
--hero-bg-image: url('./assets/hero-illustration.jpg');
```

Just update the filename to match your image:
```css
--hero-bg-image: url('./assets/your-hero-image.jpg');
```

### Step 3: Add Section Images
In `src/App.vue`, the following images are already imported:

```javascript
import methodologyImage from './assets/methodology.png'  // ✅ Already active
import einsteinImage from './assets/einstein.jpg'        // ✅ Already active
// import munariImage from './assets/munari-method.svg'  // Optional
```

Just add your image files to `/src/assets/` with the correct filenames!

### Step 3: Uncomment Image Containers
In the template section of `App.vue`, uncomment the image divs:

**Hero Section** (around line 30):
```vue
<!-- FROM: -->
<!-- <div class="hero-image">
  <img :src="heroImage" alt="Problem solving illustration" />
</div> -->

<!-- TO: -->
<div class="hero-image">
  <img :src="heroImage" alt="Problem solving illustration" />
</div>
```

**Methodology Section** (around line 75):
```vue
<div class="section-image">
  <img :src="methodologyImage" alt="Design methodology" />
</div>
```

**Munari Section** (around line 135):
```vue
<div class="section-image">
  <img :src="munariImage" alt="Munari method" />
</div>
```

## 🎨 Image Specifications

### File Formats
- **SVG**: Preferred for illustrations, diagrams, icons (scalable, small file size)
- **PNG**: Good for photos or complex graphics with transparency
- **JPG**: For photos without transparency (smaller file size)

### Recommended Sizes
- **Hero Image**: 1920x1080px (16:9 ratio) - used as background
- **Section Images**: 1200x800px or 1200x600px (landscape)
- **File Size**: Keep under 500KB for fast loading

### Image Styling (Already Applied!)
**Hero Image:**
- Used as background image with color overlay
- Grayscale filter applied (100%)
- Low opacity (15%) to blend with dark background
- Matches `var(--color-background)` color scheme

**Section Images:**
- Grayscale filter (100%) - black and white effect
- 90% opacity for subtle appearance
- Rounded corners (8px border-radius)
- Dark theme compatible containers

### Color Scheme
Match your brand colors:
- Strong/Accent: `#c27a9f` (Pink)
- Basic/Primary: `#36464f` (Dark Blue)
- Background: Dark theme
- Text: White-smoke `#f5f5f5`

## 💡 Image Resources

### Free Illustration Sources:
- **unDraw**: https://undraw.co/ (customizable illustrations)
- **DrawKit**: https://www.drawkit.io/
- **Storyset**: https://storyset.com/
- **Blush**: https://blush.design/

### Icon & Diagram Tools:
- **Excalidraw**: https://excalidraw.com/ (hand-drawn style)
- **Figma**: https://figma.com/ (professional design)
- **Canva**: https://canva.com/ (templates)

## 🔍 Example: Changing Hero Background Image

1. Download or create an illustration (JPG/PNG recommended)
2. Name it: `my-hero-image.jpg`
3. Place in: `/src/assets/my-hero-image.jpg`
4. In `src/style.css`, update the CSS variable (line 11):
   ```css
   --hero-bg-image: url('./assets/my-hero-image.jpg');
   ```
5. Save and refresh browser!

The image will automatically:
- Display as a background with grayscale filter
- Blend with the dark blue background at 15% opacity
- Cover the entire hero section

## ✨ Styling Already Applied

Images are already styled with:
- ✅ Rounded corners (border-radius)
- ✅ Responsive sizing
- ✅ Proper spacing and margins
- ✅ Background containers with borders
- ✅ Float animation for hero image
- ✅ Dark theme compatible

## 📝 Notes

- **All images are optional** - the page works perfectly without them
- **Start with one image** to test the setup
- **Optimize images** before adding (compress them)
- **Use alt text** for accessibility
- Images will be centered and responsive automatically

---

Need help? The code is ready - just add your images and uncomment the sections! 🚀

