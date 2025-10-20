# Luigol Hub - Personal Landing Page

A modern, single-page personal website with glassmorphism design, interactive identity boxes, and integrated Bitcoin tracker. Built with vanilla HTML, CSS, and JavaScript.

## 🚀 Quick Start

### Option 1: Direct File Opening
Simply open `index.html` in your web browser. This works for basic functionality but may have CORS issues with the Bitcoin API.

### Option 2: Local Server (Recommended)
Run the included Python server for full functionality:

```bash
python start_server.py
```

Then open `http://localhost:8000` in your browser.

## 🎨 Customization Guide

### 1. Replacing Icons and Images

#### Identity Box Icons
**Location**: Each identity box has an icon in the `.box-icon` div
**File**: `index.html`
**Selectors**: 
- `.identity-box:nth-child(1) .box-icon img` (Bitcoin icon)
- `.identity-box:nth-child(2) .box-icon img` (Education icon)
- `.identity-box:nth-child(3) .box-icon img` (YouTube icon)
- `.identity-box:nth-child(4) .box-icon img` (Developer icon)
- `.identity-box:nth-child(5) .box-icon img` (Languages icon)
- `.identity-box:nth-child(6) .box-icon img` (Sports icon)

**Recommended size**: 64x64px square icons with `border-radius: 8px`
**Format**: PNG with transparent background
**Example**:
```html
<img src="path/to/bitcoin-icon.png" alt="Bitcoin icon" />
```

#### Social Media Icons
**Location**: Social links section
**File**: `index.html`
**Selectors**:
- `.social-btn:nth-child(1) img` (YouTube)
- `.social-btn:nth-child(2) img` (GitHub)
- `.social-btn:nth-child(3) img` (LinkedIn)
- `.social-btn:nth-child(4) img` (Bitcoin)

**Recommended size**: 24x24px
**Format**: PNG with transparent background
**Note**: Icons are automatically inverted to white (`filter: brightness(0) invert(1)`)

#### Profile Avatar
**Location**: Header section
**File**: `index.html`
**Selector**: `.avatar` CSS background-image property
**Current**: `background-image: url("IMG_3044.jpg");`
**Recommended size**: 168x168px (will be cropped to circle)

### 2. Editing Box Content

#### Box Titles
**File**: `index.html`
**Elements**: Elements with IDs ending in `-title`
- `#bitcoin-title`
- `#student-title`
- `#youtube-title`
- `#developer-title`
- `#languages-title`
- `#sports-title`

**Example**:
```html
<div class="box-title" id="bitcoin-title">Your Custom Title</div>
```

#### Box Descriptions
**File**: `index.html`
**Elements**: Elements with IDs ending in `-description`
- `#bitcoin-description`
- `#student-description`
- `#youtube-description`
- `#developer-description`
- `#languages-description`
- `#sports-description`

**Example**:
```html
<p class="box-description" id="bitcoin-description">
  Your custom description text here...
</p>
```

#### Box Button Labels and Links
**File**: `index.html`
**Elements**: Elements with IDs ending in `-button`
- `#bitcoin-button`
- `#student-button`
- `#youtube-button`
- `#developer-button`
- `#languages-button`
- `#sports-button`

**Example**:
```html
<a href="https://your-link.com" class="box-button" id="youtube-button" target="_blank" rel="noopener">
  Visit My Channel
</a>
```

### 3. Adding/Removing Identity Boxes

#### Adding a New Box
Use this template and insert it in the `.identity-boxes` section:

```html
<!-- Box Template -->
<div class="identity-box" tabindex="0" role="button" aria-expanded="false" aria-describedby="newbox-desc">
  <div class="box-header">
    <div class="box-icon">
      <img src="" alt="Your icon description" />
    </div>
    <div class="box-title" id="newbox-title">Your Box Title</div>
  </div>
  <div class="box-content" id="newbox-desc">
    <p class="box-description" id="newbox-description">
      Your box description text here...
    </p>
    <a href="#" class="box-button" id="newbox-button">Learn more</a>
  </div>
</div>
```

#### Required Steps for New Boxes:
1. Add the HTML structure above
2. Add translations in the `translations` object in JavaScript
3. Update the `boxTypes` array in the `updateContent()` function
4. Add hover effects in CSS if needed (optional)

#### Removing Boxes:
1. Delete the HTML structure
2. Remove translations from JavaScript
3. Update the `boxTypes` array
4. Remove any custom CSS hover effects

### 4. Modifying Social Links Section

#### Changing Icons and URLs
**File**: `index.html`
**Location**: `.social-links` section

**Current structure**:
```html
<a href="https://www.youtube.com/@oluigol" class="social-btn" aria-label="YouTube" target="_blank" rel="noopener">
  <img src="" alt="YouTube" />
  <div class="tooltip" id="youtube-tooltip">@oluigol</div>
</a>
```

**To modify**:
1. Change the `href` attribute to your URL
2. Update the `aria-label` for accessibility
3. Replace the `src` attribute in the `img` tag
4. Update the tooltip text

#### Adding New Social Links
```html
<a href="https://your-platform.com/username" class="social-btn" aria-label="Platform Name" target="_blank" rel="noopener">
  <img src="path/to/icon.png" alt="Platform Name" />
  <div class="tooltip" id="platform-tooltip">@username</div>
</a>
```

#### Custom Hover Effects
**File**: `index.html` (CSS section)
**Location**: Social button hover effects

Add new hover effects:
```css
.social-btn:nth-child(5):hover { /* Your new platform */
  background: rgba(r, g, b, 0.15);
  border-color: rgba(r, g, b, 0.4);
}
```

### 5. Bitcoin Section Customization

#### Section Title
**File**: `index.html`
**Element**: `#bitcoinTitle`
**JavaScript**: Update translations object

#### Disabling Bitcoin Section
**File**: `index.html`
**Method 1**: Hide with CSS
```css
.bitcoin-section {
  display: none;
}
```

**Method 2**: Remove HTML structure
Delete the entire `.bitcoin-section` div

#### Modifying Chart Data
**File**: `index.html`
**Function**: `generateChartData()`
**Location**: JavaScript section

Update the `csvData` array with your own data:
```javascript
const csvData = [
  { date: '2024-08-31', price: 63329.50 },
  { date: '2024-09-30', price: 70215.19 },
  // Add your data points here
];
```

#### Changing Start Date and Price
**File**: `index.html`
**Variables**: 
- `START_DATE = '2024-09-01'`
- `START_PRICE = 57430.34`
- `CURRENT_PRICE = 112391.38`

### 6. Language Support

#### Adding New Languages
**File**: `index.html`
**Location**: `translations` object

1. Add new language object:
```javascript
fr: {
  title: "Luigol",
  subtitle: "Luigi • São Paulo / Maceió • 21 Ans",
  // ... add all translations
}
```

2. Add flag to flags object:
```javascript
const flags = { pt: '🇧🇷', en: '🇺🇸', es: '🇪🇸', fr: '🇫🇷' };
```

3. Add language option to HTML:
```html
<a href="#" class="lang-option" data-lang="fr">🇫🇷 Français</a>
```

#### Updating Existing Translations
**File**: `index.html`
**Location**: `translations` object

Each language object contains:
- Basic info (title, subtitle, footer, footerQuote)
- Identity box content (titles, descriptions, button labels)
- Bitcoin section content
- Tooltip content

### 7. Styling Customization

#### Color Scheme
**File**: `index.html`
**Location**: `:root` CSS variables

```css
:root {
  --bg: #0a0a0a;                    /* Background color */
  --text: #f5f5f5;                 /* Main text color */
  --muted: #b3b3b3;                /* Secondary text color */
  --glass-border: rgba(255, 255, 255, 0.15); /* Glass border */
  --glass-bg: rgba(255, 255, 255, 0.05);     /* Glass background */
  --ring: rgba(255, 255, 255, 0.12);        /* Focus ring */
  --shadow: 0 10px 30px rgba(0, 0, 0, 0.35); /* Shadow */
  --radius: 18px;                   /* Border radius */
  --space: clamp(16px, 2.5vmin, 28px);       /* Spacing */
  --maxw: 860px;                    /* Max content width */
  --bitcoin-orange: #f7931a;        /* Bitcoin orange */
}
```

#### Glassmorphism Effects
**File**: `index.html`
**Key properties**:
- `backdrop-filter: blur(16px) saturate(160%);`
- `background: rgba(255, 255, 255, 0.05);`
- `border: 1px solid rgba(255, 255, 255, 0.15);`
- `border-radius: 18px;`

#### Responsive Breakpoints
**File**: `index.html`
**Location**: `@media (max-width: 768px)` section

Modify breakpoints and responsive behavior as needed.

### 8. Accessibility Features

#### Keyboard Navigation
- All identity boxes support Enter/Space key activation
- Language selector is fully keyboard accessible
- Focus indicators are visible for all interactive elements

#### Screen Reader Support
- Proper ARIA labels and roles
- Semantic HTML structure
- Alt text for all images

#### Motion Preferences
**File**: `index.html`
**Location**: `@media (prefers-reduced-motion: reduce)` section

Respects user's motion preferences by disabling animations.

### 9. Performance Optimization

#### Image Optimization
- Use WebP format when possible
- Compress images before adding
- Consider lazy loading for large images

#### JavaScript Optimization
- Bitcoin API calls are cached
- Chart.js is loaded from CDN
- Minimal JavaScript footprint

### 10. Deployment

#### Static Hosting
Upload `index.html` to any static hosting service:
- GitHub Pages
- Netlify
- Vercel
- Firebase Hosting

#### Custom Domain
Update any hardcoded URLs in the code to match your domain.

## 🛠️ Technical Details

### Dependencies
- **Chart.js**: For Bitcoin price chart (loaded from CDN)
- **Inter Font**: Google Fonts (loaded from CDN)
- **CoinGecko API**: For live Bitcoin prices

### Browser Support
- Modern browsers with CSS Grid and Flexbox support
- ES6+ JavaScript features
- CSS Custom Properties (CSS Variables)

### File Structure
```
luigol-hub/
├── index.html          # Main website file
├── start_server.py     # Local development server
├── README.md          # This file
└── IMG_3044.jpg       # Profile photo (replace as needed)
```

## 🐛 Troubleshooting

### Bitcoin API Issues
If the Bitcoin tracker shows errors:
1. Check internet connection
2. Verify CoinGecko API is accessible
3. The site will fallback to static data if API fails

### CORS Issues
If you see CORS errors:
1. Use the local server (`python start_server.py`)
2. Or deploy to a web server instead of opening file directly

### Styling Issues
If glassmorphism effects don't work:
1. Check browser support for `backdrop-filter`
2. Ensure CSS variables are properly defined
3. Verify no conflicting CSS rules

## 📝 License

This project is open source. Feel free to use and modify as needed.

## 🤝 Contributing

To contribute:
1. Fork the repository
2. Make your changes
3. Test thoroughly
4. Submit a pull request

---

**Need help?** Check the code comments in `index.html` for additional implementation details.