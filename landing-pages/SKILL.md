---
name: landing-pages
description: Create high-performance, visually stunning landing pages and full websites using HTML, Tailwind CSS, and vanilla CSS animations. Produces premium "vibe-coded" designs inspired by top design studios — dark luxury aesthetics, scroll-triggered animations, beam effects, gradient text, marquee logos, glassmorphism cards, and cinematic page loads. Use when the user asks to build a landing page, website, marketing page, SaaS page, portfolio, agency site, or any web page that needs to look premium and load fast. Also use when enhancing existing pages with animations, effects, or visual polish. Outputs single-file HTML by default with optional multi-file structure.
---

# Landing Page Builder — Premium Vibe-Coded Sites

Build stunning, fast-loading landing pages and websites with cinematic visual quality. This skill produces sites that look like they were designed by a top agency — not generic AI output.

## Core Philosophy

1. **Single-file HTML by default** — Everything in one file (HTML, CSS, JS). Easy to deploy anywhere. Optional multi-file for larger sites.
2. **Tailwind CSS via CDN** — Fast utility-first styling with custom config for brand colors and fonts.
3. **CSS-first animations** — No heavy JS libraries. Use `@keyframes`, `IntersectionObserver` for scroll triggers, and hardware-accelerated properties (`transform`, `opacity`, `filter`) for 60fps.
4. **Premium by default** — Dark themes, serif/sans-serif font pairing, generous whitespace, subtle grid patterns, and numbered details that make layouts feel designed, not generated.

---

## Before You Start

Read `references/animation-library.md` for the full catalog of copy-paste animation patterns.
Read `references/component-patterns.md` for section-by-section component blueprints.
Read `references/theme-system.md` for light/dark theme palettes, toggle, and system preference detection.

---

## Intake Questions — Ask Before Building

When a user requests a landing page, **always ask these 5 questions first** before generating any code. These map to MengTo's "Formula": Style → Layout → Motion → Function → Reference. Present them as a quick brief the user can answer in one message.

### The 5 Questions

**1. Style — What's the vibe?**
Pick one (or describe your own):
- **Dark Futuristic** — Black bg, glass blur, neon/glow accents (tech, SaaS, crypto)
- **Premium Serif** — Dark with warm undertones, elegant serif headings, gold/amber accents (finance, consulting)
- **Editorial** — Light bg, oversized serif headlines, generous white space, minimal color (portfolios, agencies)
- **Soft Minimal** — Light bg, rounded shapes, neutral/earth tones, gentle shadows (wellness, consumer brands)
- **Brutalist** — High contrast, raw grid, loud type, bold color (creative, disruptive brands)
- **Mixed** — Dark hero section transitioning to light content sections (versatile, modern)

**2. Theme Mode — Light, dark, or both?**
- **Dark only** (default for tech/SaaS)
- **Light only** (default for wellness, editorial, portfolios)
- **Both with toggle** — User can switch via button, defaults to system preference
- **Mixed** — Dark hero/nav, light body sections (like Etheria)

**3. Layout — How should content flow?**
- **Centered** — Content centered, symmetrical (most common for SaaS/product)
- **Split 50/50** — Hero with text left, visual right
- **Sidebar** — Content with persistent sidebar element
- **Editorial/Asymmetric** — Oversized headlines, offset elements, magazine-like flow
- **Bento Grid** — Mixed card sizes in an asymmetric grid layout

**4. Motion — How should things move?**
- **Subtle** — Fade-in on scroll only, minimal hover effects
- **Polished** — Staggered intro animation, scroll reveals, hover lifts (recommended default)
- **Cinematic** — Full intro sequence, blur-in, parallax, beam animations, spotlight cards
- **Minimal** — Almost no animation, let typography and space do the work

**5. Reference — Any existing sites, brand colors, or content to match?**
- Paste a URL to match the feel of
- Share brand colors (hex codes or descriptions)
- Paste existing copy/content to adapt
- Share logo or icon preferences

### If the user skips questions or says "just build it"

Use these smart defaults:
- Style: **Dark Futuristic** for tech/SaaS, **Soft Minimal** for anything consumer-facing
- Theme: **Dark only** unless the industry suggests otherwise
- Layout: **Centered** with split hero
- Motion: **Polished** (staggered intro + scroll reveals)
- Font: **Instrument Serif** + **DM Sans** (dark) or **Newsreader** + **Plus Jakarta Sans** (light)

---

## Architecture: Single-File HTML Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{{page_title}}</title>

  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Google Fonts — ALWAYS use distinctive pairings -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family={{heading_font}}:ital,wght@0,400;0,700;1,400&family={{body_font}}:wght@300;400;500;600&display=swap" rel="stylesheet">

  <!-- Iconify CDN for icons -->
  <script src="https://code.iconify.design/3/3.1.0/iconify.min.js"></script>

  <!-- Tailwind Config -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            heading: ['{{heading_font}}', 'serif'],
            body: ['{{body_font}}', 'sans-serif'],
          },
          colors: {
            primary: { DEFAULT: '{{primary_color}}', light: '{{primary_light}}', dark: '{{primary_dark}}' },
            surface: { DEFAULT: '#0a0a0a', raised: '#111111', border: '#1a1a1a' },
          },
        },
      },
    }
  </script>

  <style>
    /* === BASE RESETS === */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      font-family: '{{body_font}}', sans-serif;
      background: #0a0a0a;
      color: #e0e0e0;
      overflow-x: hidden;
    }

    /* === CUSTOM CSS GOES HERE === */
    /* Animation keyframes, backgrounds, effects */
  </style>
</head>
<body>
  <!-- NAV -->
  <!-- HERO -->
  <!-- SECTIONS -->
  <!-- FOOTER -->

  <script>
    /* === IntersectionObserver for scroll animations === */
    /* === Any interactive JS === */
  </script>
</body>
</html>
```

### Multi-File Option

When the user requests multi-file or the site exceeds ~800 lines, split into:
```
project/
├── index.html
├── css/
│   ├── tailwind-config.js
│   ├── animations.css      # All @keyframes and animation utilities
│   └── components.css      # Section-specific styles
├── js/
│   └── main.js             # IntersectionObserver, interactions
└── assets/                 # Images, fonts if self-hosted
```

---

## Design System Defaults

### Font Pairings (pick one pair per site — NEVER use Inter, Roboto, or Arial)

| Heading Font | Body Font | Vibe | Best For |
|---|---|---|---|
| **Playfair Display** (italic) | DM Sans | Luxury, editorial | Dark premium, consulting |
| **Newsreader** (italic) | Plus Jakarta Sans | Upscale agency | Light editorial, mixed themes |
| **Instrument Serif** | Geist / Satoshi (self-host) | Modern premium | Dark tech, SaaS |
| **Fraunces** | Work Sans | Warm sophistication | Light wellness, D2C |
| **Cormorant Garamond** | Nunito Sans | Classic elegance | Light editorial, interior design |
| **Syne** | Outfit | Bold, modern | Dark futuristic, crypto |
| **Bricolage Grotesque** | Source Sans 3 | Fresh, contemporary | Light SaaS, consumer |
| **DM Serif Display** | DM Sans | Refined contrast | Both light and dark |
| **Libre Baskerville** | Karla | Warm editorial | Light portfolios, agencies |
| **Noto Serif Display** | Noto Sans | Versatile premium | Both, esp. international |

**Rule for DARK themes**: Headings use serif/italic font. Body uses clean sans-serif. The italic serif heading is the signature move that separates premium from generic.

**Rule for LIGHT themes**: Can use either serif or bold sans-serif headings. For editorial, use large serif (Cormorant, Newsreader). For minimal, use a geometric sans (Outfit, Plus Jakarta Sans) with generous letter-spacing. Body text should have excellent readability at 16-18px with `leading-relaxed`.

### Color Strategies

| Strategy | Description | When to Use |
|---|---|---|
| **Monotone dark** | Black/charcoal bg, white text, single accent | Default for tech/SaaS. Always works. |
| **Monotone + accent** | As above + one vibrant color (blue, violet, amber) | SaaS, tech, agencies |
| **Warm dark** | Dark with warm undertones (#0d0a07), amber/copper accents | Consulting, luxury, finance |
| **Cool dark** | Deep navy/slate bg, ice blue accents | Finance, enterprise |
| **Warm light (editorial)** | Warm off-white bg (#f5f0ea), dark serif text, minimal color | Interior design, luxury, editorial |
| **Soft light (minimal)** | Clean off-white (#f8f7f4), earth tone accents, gentle shadows | Wellness, consumer, D2C brands |
| **Crisp light** | Pure white bg, dark text, single bold accent color | Portfolios, clean SaaS |
| **Mixed (dark hero → light body)** | Dark hero/nav with light content sections | Versatile, modern feel |

**Default DARK palette** (use for dark themes):
```css
--bg: #0a0a0a;
--bg-surface: #111111;
--bg-raised: #161616;
--border: rgba(255,255,255,0.06);
--border-hover: rgba(255,255,255,0.12);
--text: #e8e8e8;
--text-muted: #888888;
--text-dim: #555555;
--primary: #6366f1;       /* Override per project */
--primary-glow: rgba(99,102,241,0.15);
```

**Default LIGHT palette** (use for light themes):
```css
--bg: #f8f7f4;
--bg-surface: #ffffff;
--bg-raised: #f0eeea;
--border: rgba(0,0,0,0.08);
--border-hover: rgba(0,0,0,0.15);
--text: #1a1a1a;
--text-muted: #6b6b6b;
--text-dim: #999999;
--primary: #1a1a1a;       /* Override per project — often dark on light */
--primary-glow: rgba(0,0,0,0.05);
```

**WARM LIGHT palette** (Sixtine/editorial style):
```css
--bg: #f5f0ea;
--bg-surface: #ece7df;
--bg-raised: #e5dfd6;
--border: rgba(0,0,0,0.06);
--text: #1a1714;
--text-muted: #8a8279;
--primary: #c45a3c;       /* Warm terracotta accent */
```

**SOFT GREEN LIGHT palette** (Vitalis/wellness style):
```css
--bg: #f9f7f3;
--bg-surface: #ffffff;
--bg-raised: #f0ede8;
--border: rgba(0,0,0,0.06);
--text: #1a2e1a;
--text-muted: #6b7a6b;
--primary: #2d4a2d;       /* Deep forest green */
```

### Dark/Light Theme Toggle — See `references/theme-system.md`

When the user requests both themes with a toggle, or "follow system preference", implement the full theme system from the reference file. This uses CSS custom properties on `[data-theme]` attributes, a toggle button in the nav, and `prefers-color-scheme` media query detection.

### Icons

Use Iconify CDN with curated icon sets. Prompt pattern: `Use Iconify {set_name} icons`.

Recommended sets (NOT Lucide — too common):
- **Solar** — Clean, modern line icons
- **Phosphor** — Versatile, multiple weights
- **Iconoir** — Elegant, minimal
- **Heroicons** — Solid + outline variants
- **Tabler** — Comprehensive, consistent stroke

Usage: `<span class="iconify" data-icon="solar:shield-check-bold"></span>`

---

## Animation System

**CRITICAL**: All animations must use hardware-accelerated properties ONLY: `transform`, `opacity`, `filter`. NEVER animate `width`, `height`, `margin`, `padding`, `top`, `left`.

### Page Load Animations (Intro)

Apply to hero elements on page load. Stagger with `animation-delay` for cinematic reveal.

```css
/* Base intro animation — fade + slide + blur */
@keyframes fadeInUp {
  from {
    opacity: 0.01;  /* NOT opacity: 0 — avoids Flash of Invisible Content */
    transform: translateY(20px);
    filter: blur(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

.animate-intro {
  animation: fadeInUp 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
}

/* Stagger delays for element-by-element reveal */
.delay-1 { animation-delay: 0.1s; }
.delay-2 { animation-delay: 0.2s; }
.delay-3 { animation-delay: 0.3s; }
.delay-4 { animation-delay: 0.4s; }
.delay-5 { animation-delay: 0.5s; }
.delay-6 { animation-delay: 0.6s; }
```

**IMPORTANT**: Use `both` (not `forwards`) for `animation-fill-mode`. Use `opacity: 0.01` (not `0`) to prevent elements from being invisible before JS loads.

### Scroll-Triggered Animations

Use `IntersectionObserver` — NO external libraries.

```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('in-view');
    }
  });
}, {
  threshold: 0.15,
  rootMargin: '0px 0px -50px 0px'
});

document.querySelectorAll('.animate-on-scroll').forEach(el => observer.observe(el));
```

```css
.animate-on-scroll {
  opacity: 0.01;
  transform: translateY(30px);
  filter: blur(6px);
  transition: opacity 0.7s ease, transform 0.7s ease, filter 0.7s ease;
}

.animate-on-scroll.in-view {
  opacity: 1;
  transform: translateY(0);
  filter: blur(0);
}

/* Stagger children */
.stagger-children .animate-on-scroll:nth-child(1) { transition-delay: 0.0s; }
.stagger-children .animate-on-scroll:nth-child(2) { transition-delay: 0.1s; }
.stagger-children .animate-on-scroll:nth-child(3) { transition-delay: 0.15s; }
.stagger-children .animate-on-scroll:nth-child(4) { transition-delay: 0.2s; }
.stagger-children .animate-on-scroll:nth-child(5) { transition-delay: 0.25s; }
.stagger-children .animate-on-scroll:nth-child(6) { transition-delay: 0.3s; }
```

### Decorative Animations (See references/animation-library.md for full catalog)

These are the effects that make sites feel premium:

- **Border beam** — Animated gradient border that travels around a card or button
- **Sonar pulse** — Expanding rings from a point (great on icons or status dots)
- **Marquee ticker** — Infinite horizontal scroll for logos or text
- **Grid background** — Subtle CSS grid pattern with fade-to-edges
- **Dot matrix** — Background dot pattern with radial gradient mask
- **Gradient text** — Animated gradient on heading text
- **Noodle/beam lines** — Animated connecting lines between elements
- **Glow effects** — Pulsing ambient glow behind elements
- **Noise texture** — SVG noise overlay for grain/texture

---

## Section-by-Section Build Guide

Build pages section by section, top to bottom. Each section should be independently styled and animated.

### 1. Navigation

```
Fixed/sticky top bar with backdrop-blur
Logo left, links center or right, CTA button right
Pill-shaped or bordered CTA with hover effect
Mobile: hamburger menu with slide-in overlay
```

Key CSS:
```css
nav {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 50;
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  background: rgba(10, 10, 10, 0.8);
  border-bottom: 1px solid rgba(255,255,255,0.06);
}
```

### 2. Hero Section

The most important section. This is where you establish the premium feel.

**Structure**:
```
[Badge/label]           ← Small pill badge ("• ADVISORY FIRM")
[Headline]              ← Large serif/italic heading, 2-3 lines
[Subheadline]           ← 1-2 line description in body font
[CTAs]                  ← Primary + Secondary buttons
[Stats/metrics]         ← Optional: "40% efficiency" "6 weeks"
[Background animation]  ← Grid, dots, gradient glow, or embedded canvas
```

**Typography scale for hero headings**:
- Desktop: `text-5xl` to `text-7xl` (48px–72px), sometimes larger
- Mobile: `text-3xl` to `text-4xl`
- Use `font-heading italic` for serif headings
- Mix weights: light italic serif + bold sans-serif in same heading

**Background techniques — DARK themes** (pick one):
```css
/* 1. Subtle grid */
.hero-bg-grid {
  background-image:
    linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 60px 60px;
}

/* 2. Dot matrix */
.hero-bg-dots {
  background-image: radial-gradient(circle, rgba(255,255,255,0.08) 1px, transparent 1px);
  background-size: 24px 24px;
}

/* 3. Radial gradient glow (behind hero) */
.hero-glow {
  position: absolute;
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, var(--primary-glow) 0%, transparent 70%);
  filter: blur(80px);
  top: -200px;
  left: 50%;
  transform: translateX(-50%);
  pointer-events: none;
}

/* 4. Animated grid mesh glow (like Aura Financial — premium dark effect) */
.hero-grid-glow {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(rgba(255,255,255,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.04) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse 70% 50% at 60% 40%, black 20%, transparent 80%);
  -webkit-mask-image: radial-gradient(ellipse 70% 50% at 60% 40%, black 20%, transparent 80%);
}
.hero-grid-glow::after {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 50% 50% at 60% 40%, var(--primary-glow) 0%, transparent 70%);
  filter: blur(60px);
  animation: grid-glow-pulse 8s ease-in-out infinite alternate;
}
@keyframes grid-glow-pulse {
  0% { opacity: 0.4; transform: scale(1); }
  100% { opacity: 0.7; transform: scale(1.1); }
}

/* 5. Orbital decoration (circles + lines like Aura Financial) */
.hero-orbital {
  position: absolute;
  width: 400px;
  height: 400px;
  right: 10%;
  top: 20%;
  pointer-events: none;
}
.hero-orbital .ring {
  position: absolute;
  inset: 0;
  border: 1px solid rgba(255,255,255,0.06);
  border-radius: 50%;
  animation: orbital-spin 30s linear infinite;
}
.hero-orbital .ring:nth-child(2) {
  inset: 40px;
  animation-duration: 25s;
  animation-direction: reverse;
}
.hero-orbital .dot {
  position: absolute;
  width: 8px;
  height: 8px;
  background: var(--primary);
  border-radius: 50%;
  top: 50%;
  left: 0;
  box-shadow: 0 0 12px var(--primary-glow);
}
@keyframes orbital-spin {
  to { transform: rotate(360deg); }
}
```

**Background techniques — LIGHT themes** (pick one):
```css
/* 1. Soft warm gradient */
.hero-bg-warm {
  background: linear-gradient(180deg, #f5f0ea 0%, #ece7df 100%);
}

/* 2. Subtle noise texture */
.hero-bg-texture {
  background-color: var(--bg);
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.02'/%3E%3C/svg%3E");
}

/* 3. Soft radial highlight (centered, like Vitalis) */
.hero-bg-soft-glow {
  background: radial-gradient(ellipse 80% 50% at 50% 30%, rgba(255,255,255,0.8) 0%, var(--bg) 70%);
}

/* 4. Decorative horizontal lines (editorial like Sixtine) */
.hero-line-accent {
  position: relative;
}
.hero-line-accent::after {
  content: '';
  position: absolute;
  left: 20%;
  right: 20%;
  top: 55%;
  height: 1px;
  background: rgba(0,0,0,0.12);
}

/* 5. Light dot grid (very subtle, premium feel) */
.hero-bg-dots-light {
  background-image: radial-gradient(circle, rgba(0,0,0,0.04) 1px, transparent 1px);
  background-size: 28px 28px;
}
```

### 3. Logo Ticker / Social Proof

Infinite scrolling marquee with client logos or trust badges.

```css
.marquee-track {
  display: flex;
  width: max-content;
  animation: marquee 30s linear infinite;
}

@keyframes marquee {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

/* Fade edges */
.marquee-container {
  mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
  -webkit-mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
  overflow: hidden;
}
```

**Rule**: Always duplicate the logo set so the animation loops seamlessly.

### 4. Features/Services Cards

Use the numbered detail pattern (01, 02, 03) in the corner of each card.

```html
<div class="relative border border-white/[0.06] rounded-xl p-8 bg-surface-raised">
  <span class="absolute top-4 right-4 text-xs text-white/20 font-mono">01</span>
  <div class="w-12 h-12 rounded-lg bg-white/[0.04] border border-white/[0.06] flex items-center justify-center mb-6">
    <span class="iconify text-xl text-primary" data-icon="solar:magnifer-bold"></span>
  </div>
  <h3 class="font-heading italic text-xl mb-3">Infrastructure Audit</h3>
  <p class="text-sm text-white/50 leading-relaxed">Description text here.</p>
</div>
```

### 5. Metrics/Stats Section

Large typography with mixed fonts for visual interest.

```html
<div>
  <span class="text-xs tracking-[0.2em] uppercase text-white/40 block mb-2">EFFICIENCY GAIN</span>
  <span class="font-heading italic text-6xl text-white">40</span>
  <span class="text-2xl text-white/60">%</span>
</div>
```

### 6. Feature Showcase (Bento Grid)

Asymmetric grid with mixed card sizes. Some cards full-width, some half, some third.

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  <div class="lg:col-span-2 bg-surface-raised border border-white/[0.06] rounded-2xl p-8">
    <!-- Large feature card -->
  </div>
  <div class="bg-surface-raised border border-white/[0.06] rounded-2xl p-8">
    <!-- Standard card -->
  </div>
</div>
```

### 7. Testimonials

Quote with attribution, subtle left border or quotation marks.

### 8. Pricing (if applicable)

Cards with hover lift, highlighted "recommended" tier with border beam or glow.

### 9. CTA Section

Full-width dark section with centered text and prominent button. Often includes a background glow effect.

### 10. Footer

Minimal, dark. Logo + columns of links + bottom bar with copyright.

---

## Button Recipes

### Primary CTA
```html
<a href="#" class="inline-flex items-center gap-2 px-6 py-3 bg-primary text-white rounded-full font-medium text-sm hover:brightness-110 transition-all duration-300">
  Book Consultation
  <span class="iconify" data-icon="solar:arrow-right-linear"></span>
</a>
```

### Ghost/Secondary Button
```html
<a href="#" class="inline-flex items-center gap-2 px-6 py-3 border border-white/[0.12] text-white/70 rounded-full font-medium text-sm hover:bg-white/[0.04] hover:border-white/[0.2] transition-all duration-300">
  View Framework
</a>
```

### Button with Border Beam Animation
```css
.btn-beam {
  position: relative;
  overflow: hidden;
}
.btn-beam::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: conic-gradient(from var(--beam-angle, 0deg), transparent 60%, var(--primary) 100%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: beam-rotate 3s linear infinite;
}

@keyframes beam-rotate {
  to { --beam-angle: 360deg; }
}

/* Register the custom property for animation */
@property --beam-angle {
  syntax: '<angle>';
  initial-value: 0deg;
  inherits: false;
}
```

---

## Detail Enhancers (The "Human Touch")

These small details separate premium from generic:

1. **Vertical container lines** — Thin vertical lines at grid column edges
```css
.container-lines {
  position: relative;
}
.container-lines::before,
.container-lines::after {
  content: '';
  position: absolute;
  top: 0;
  bottom: 0;
  width: 1px;
  background: rgba(255,255,255,0.04);
}
.container-lines::before { left: 0; }
.container-lines::after { right: 0; }
```

2. **Numbered section labels** — `01`, `02`, `03` in monospace at card corners or section starts

3. **Status dots** — Small colored dots before labels (`• ADVISORY FIRM`)
```html
<span class="inline-flex items-center gap-2 px-3 py-1 rounded-full border border-white/[0.08] text-xs tracking-widest uppercase text-white/60">
  <span class="w-1.5 h-1.5 rounded-full bg-primary animate-pulse"></span>
  Advisory Firm
</span>
```

4. **Subtle grain/noise overlay**
```css
body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 9999;
  opacity: 0.4;
}
```

5. **Edge fade masks** on scrollable containers (logos, testimonials)

6. **Bracket/tag labels** — `[LIVE MONITOR]`, `{001}` as decorative metadata

---

## Responsive Rules

- **Mobile-first** Tailwind breakpoints: `sm:`, `md:`, `lg:`, `xl:`
- Hero heading: `text-3xl md:text-5xl lg:text-7xl`
- Card grids: `grid-cols-1 md:grid-cols-2 lg:grid-cols-3`
- Padding: `px-5 md:px-8 lg:px-16`
- Max container width: `max-w-7xl mx-auto`
- Hide decorative elements on mobile: `hidden lg:block`
- Hamburger menu for mobile navigation
- Reduce animation intensity on mobile (use `prefers-reduced-motion`)

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

---

## Performance Rules

1. **No external JS animation libraries** — CSS keyframes + IntersectionObserver only
2. **Only animate compositable properties** — `transform`, `opacity`, `filter`
3. **Lazy-load images** — `loading="lazy"` on all images below the fold
4. **Use `will-change` sparingly** — Only on elements that are actively animating
5. **SVG for icons** (via Iconify CDN) — Never use icon font files or large image sprites
6. **Preconnect** to Google Fonts and CDNs
7. **Inline critical CSS** in `<style>` tag — No render-blocking external stylesheets except Tailwind CDN
8. **Image formats** — Use WebP/AVIF where possible, with fallbacks

---

## Prompt-Driven Customization

The skill supports natural language customization after initial generation:

| User Says | Action |
|---|---|
| "Use {font} for headings" | Swap heading font in Google Fonts link + Tailwind config |
| "Change primary to blue" | Update color variables throughout |
| "Make it monotone" | Remove accent colors, go grayscale with single pop |
| "Animate on scroll" | Add IntersectionObserver + `.animate-on-scroll` classes |
| "Add beam animation to button" | Apply border-beam CSS from button recipes |
| "Add marquee logos" | Insert logo ticker section with marquee animation |
| "Make more upscale" | Switch to tall serif font, increase whitespace, B&W palette |
| "Add grid background" | Apply `.hero-bg-grid` CSS pattern |
| "Make outlines subtle" | Reduce border opacity to `white/[0.04]` |
| "Add 01 02 03 details" | Insert numbered labels on cards/sections |
| "Add vertical lines" | Apply `.container-lines` pattern |

---

## Output Checklist

Before delivering the final HTML file, verify:

- [ ] Page loads with smooth intro animation (staggered fade+slide+blur)
- [ ] Scroll animations trigger element-by-element with IntersectionObserver
- [ ] Navigation is fixed with backdrop-blur, works on mobile (hamburger menu)
- [ ] Font pairing is distinctive (not generic sans-serif)
- [ ] Colors use CSS custom properties on `[data-theme]`, easily swappable
- [ ] All interactive elements have hover states with transitions
- [ ] Responsive at all breakpoints (test 375px, 768px, 1024px, 1440px)
- [ ] `prefers-reduced-motion` is respected
- [ ] No layout shift from animations (no `opacity: 0` before load)
- [ ] Images are lazy-loaded
- [ ] Page weight < 500KB without images
- [ ] Background has atmosphere (grid, dots, glow, gradient, or texture — not flat solid)
- [ ] At least 2 decorative detail types used (numbers, dots, lines, brackets, grain)
- [ ] **If light theme**: borders use `rgba(0,0,0,0.06-0.12)`, not white-based; buttons are dark on light; text hierarchy uses weight/opacity, not just color
- [ ] **If both themes**: toggle button works; system preference detected on first load; no flash of wrong theme (script in `<head>`)
- [ ] **If mixed theme**: dark-to-light transition is smooth (gradient or hard section break with border)
