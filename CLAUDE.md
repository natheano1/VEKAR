# Gold Coast DJ Hire — Claude Code Project Context

## Project Overview
This is the website for **Gold Coast DJ Hire**, a professional DJ service based on the Gold Coast, Queensland, Australia. The live site is at **https://www.goldcoastdjhire.com.au**.

The site is hosted on **GitHub Pages** via the repository `natheano1/VEKAR` on the `main` branch.

---

## Business Details
- **Business name:** Gold Coast DJ Hire
- **Owner:** Solo trader (1 person)
- **Email:** hello@goldcoastdjhire.com.au
- **Location:** Gold Coast, QLD, Australia
- **Service area:** All of South East Queensland (Gold Coast, Brisbane, Sunshine Coast)
- **Services:** Weddings, Corporate Events, Ceremony & Cocktail Hour, Private Events
- **Gigs played:** 100+
- **Google Analytics ID:** G-BTVRRJVSGC

---

## Tech Stack
- Pure HTML + CSS + Vanilla JavaScript (no frameworks)
- Anime.js for animations (loaded via CDN)
- Shared stylesheet: `style.css` in root
- No build process — files are served directly by GitHub Pages
- Domain connected via GoDaddy DNS → GitHub Pages

---

## File Structure
```
VEKAR/
├── index.html              ← Home page
├── style.css               ← Shared stylesheet (used by all subpages)
├── logo.svg                ← Site logo
├── about-photo.jpg         ← DJ controller photo used in About section
├── 12548280-hd_1920_1080_30fps.mp4  ← Hero video on home page
├── CNAME                   ← goldcoastdjhire.com.au
├── _config.yml             ← Jekyll config (permalink: pretty)
├── about/
│   └── index.html          ← /about page
├── services/
│   └── index.html          ← /services page
├── corporate/
│   └── index.html          ← /corporate service page
├── wedding/
│   └── index.html          ← /wedding service page
├── ceremony-cocktail/
│   └── index.html          ← /ceremony-cocktail service page
├── private/
│   └── index.html          ← /private service page
├── contact/
│   └── index.html          ← /contact page
├── blog/
│   └── index.html          ← /blog index page
└── privacy-policy/
    └── index.html          ← /privacy-policy page
```

---

## Design System
### Colour Palette
- Background: `#0D0D0D` (near black)
- Dark surfaces: `#141414`
- Card background: `#1A1A1A`
- Border: `rgba(255,255,255,0.08)`
- Text: `#FFFFFF`
- Text muted: `rgba(255,255,255,0.6)`
- Gradient: `linear-gradient(135deg, #FF2D8B 0%, #A020F0 50%, #2060FF 100%)`
- Gradient text: `linear-gradient(90deg, #FF2D8B, #A020F0, #2060FF)`

### Typography
- Headings: Georgia (serif), font-weight normal
- Body/UI: Arial (sans-serif)
- Font sizes use `clamp()` for responsive scaling

### Key CSS Classes
- `.grad-text` — pink-to-blue gradient text effect
- `.btn-primary` — gradient filled button
- `.btn-outline` — transparent border button
- `.section-inner` — max-width 1100px centred container
- `.section-label` — small uppercase tracking label above headings
- `.divider` — 40px gradient horizontal rule

---

## Important Rules When Making Changes

### Email addresses
NEVER write `hello@goldcoastdjhire.com.au` as a plain `mailto:` href.
GoDaddy/Cloudflare obfuscates plain email addresses automatically.
Always use this JS pattern instead:
```javascript
var u = 'hello', d = 'goldcoastdjhire.com.au';
var ml = 'mailto:' + u + '\x40' + d;
document.getElementById('emailElementId').href = ml;
```
And in HTML use: `hello&#64;goldcoastdjhire.com.au` for display text.

### External stylesheet
`index.html` has ALL CSS inlined (no external stylesheet dependency).
All subpages (`about/`, `services/`, etc.) link to `../style.css`.
When adding new styles to subpages always add to `style.css` too.

### No .html in links
All internal links use clean paths: `/about`, `/services`, `/corporate` etc.
Never use `.html` extensions in href attributes.

### Cloudflare interference
GoDaddy routes traffic through Cloudflare automatically.
Cloudflare injects script tags and obfuscates emails.
Always test email links after pushing. If broken, rebuild using the JS pattern above.

### Mobile menu
Every page must have:
1. `<div class="mobile-menu" id="mobileMenu">` overlay before `<nav>`
2. Hamburger button `<button class="hamburger" id="hamburger">` inside `<nav>`
3. The shared hamburger JS (see any subpage for reference)

### GA4
Every page must include the GA4 tag in `<head>`:
```html
<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-BTVRRJVSGC"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'G-BTVRRJVSGC');
</script>
```

---

## Service Pages — Image URLs
Each service uses a consistent Unsplash image across home, services overview, and subpage hero:
- **Corporate:** `https://images.unsplash.com/photo-1540575467063-178a50c2df87?w=1200&q=80`
- **Wedding:** `https://images.unsplash.com/photo-1519741497674-611481863552?w=1200&q=80`
- **Ceremony & Cocktail:** `https://images.unsplash.com/photo-1515934751635-c81c6bc9a2d8?w=1200&q=80`
- **Private Events:** `https://images.unsplash.com/photo-1533174072545-7a4b6ad7a6c3?w=1200&q=80`

---

## SEO
- Canonical URLs set on every page
- Local Business schema JSON-LD on home page
- Meta descriptions targeting Gold Coast DJ keywords
- Clean URLs via folder/index.html structure
- GA4 tracking on all pages (G-BTVRRJVSGC)

---

## Git Workflow
After making any changes always:
```
git add .
git commit -m "brief description of change"
git push
```
GitHub Pages deploys within 1-2 minutes of pushing.

---

## Common Tasks & How To Do Them

### Adding a new blog post
1. Create folder: `blog/post-name/`
2. Create `blog/post-name/index.html` using existing page as template
3. Add link to `blog/index.html`
4. Push to GitHub

### Adding a testimonial
Edit the testimonial carousel in `index.html` — add a new `.testimonial-slide` div following the existing pattern.

### Updating service content
Edit the relevant subpage: `corporate/index.html`, `wedding/index.html`, etc.

### Adding a new page
1. Create folder with page name
2. Create `index.html` inside it using an existing subpage as template
3. Add nav link to `style.css` mobile menu and all page navs
4. Push to GitHub
