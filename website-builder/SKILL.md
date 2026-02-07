---
name: website-builder
description: Extract brand identity and download assets from existing client websites. Use this skill BEFORE building any website, landing page, or marketing page that needs to match an existing brand. Handles logo extraction, color palette identification, font detection, and local asset downloading. Pair with landing-pages skill for the actual build.
---

# Website Builder — Brand Extraction & Asset Collection

Extract everything needed to match an existing brand before building anything.

## When To Use This Skill

- Before building a landing page for an existing client
- When you need to match a company's visual identity
- Any project that requires using the client's real logo, colors, and imagery
- **Use this first, then use landing-pages skill for the actual build**

## Core Workflow

### Phase 1: Brand Extraction (CRITICAL)

Before writing ANY code, extract the complete brand identity from the client's website.

**Use browser tool to:**
1. Open client website
2. Screenshot the homepage
3. Extract via JavaScript:
   - Logo URL
   - Color palette (primary, secondary, accent, text, background)
   - Font families (headings + body)
   - Navigation structure
   - Phone number, address
   - Footer content

**Example extraction script:**
```javascript
(() => {
  const imgs = Array.from(document.querySelectorAll('img'));
  const logo = imgs.find(i => 
    i.alt?.toLowerCase().includes('logo') || 
    i.src?.includes('logo')
  )?.src;
  
  const styles = getComputedStyle(document.body);
  
  return {
    logo,
    fonts: {
      body: styles.fontFamily,
    },
    colors: {
      text: styles.color,
      background: styles.backgroundColor,
    },
    images: imgs.slice(0, 30).map(i => ({src: i.src, alt: i.alt})),
    nav: Array.from(document.querySelectorAll('nav a, header a'))
      .map(a => ({label: a.textContent.trim(), href: a.href}))
      .filter(n => n.label)
  };
})()
```

### Phase 2: Asset Download (MANDATORY)

**NEVER use placeholder images.** Download ALL assets locally:

```bash
mkdir -p images
curl -sL "LOGO_URL" -o images/logo.png
curl -sL "HERO_IMAGE_URL" -o images/hero.jpg
# ... download all needed images
```

**Download these:**
- Logo (PNG/SVG preferred)
- Hero images
- Product/service images
- Team photos
- Any lifestyle imagery from the site
- Icons if custom

### Phase 3: Document the Brand

Create a `brand.md` file in the project directory:

```markdown
# Brand Identity — [Client Name]

## Logo
- Path: `images/logo.png`
- Source: [original URL]

## Colors
- Primary: #XXXXXX
- Secondary: #XXXXXX
- Accent: #XXXXXX
- Text: #XXXXXX
- Background: #XXXXXX

## Typography
- Headings: [Font Name]
- Body: [Font Name]

## Contact
- Phone: XXX-XXX-XXXX
- Address: [if found]
- Email: [if found]

## Navigation Structure
- [Link labels found]

## Downloaded Assets
- images/logo.png
- images/hero.jpg
- [list all]
```

## Rules

1. **Only use images from the client's actual website** — no stock photos
2. **Download assets locally** — never hotlink to their server
3. **Extract exact hex values** — don't approximate colors
4. **Match their typography** — use the same fonts or close matches from Google Fonts

## File Structure

After extraction, you should have:

```
project/
├── brand.md
└── images/
    ├── logo.png
    ├── hero.jpg
    └── ... (all extracted images)
```

## Next Steps

After brand extraction and asset download:
1. Use the **landing-pages** skill for building landing/marketing pages
2. Pass the extracted brand info (colors, fonts) into the design

## References

See `references/` folder for:
- `copywriting-frameworks.md` — AIDA, PAS, and other frameworks
- `conversion-psychology.md` — Psychological triggers for conversions
