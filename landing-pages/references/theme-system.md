# Theme System Reference

Complete implementation for light themes, dark themes, dark/light toggle, and system preference detection. All theme-aware CSS uses custom properties on `[data-theme]` attributes.

---

## 1. Theme Architecture

All colors are defined as CSS custom properties. Components reference variables, NEVER hardcode colors. This makes themes instantly swappable.

### CSS Custom Properties Setup

Place this in your `<style>` block before any component styles:

```css
/* === THEME VARIABLES === */

/* Dark theme (default for dark-first sites) */
[data-theme="dark"], :root {
  --bg: #0a0a0a;
  --bg-surface: #111111;
  --bg-raised: #161616;
  --bg-overlay: rgba(0,0,0,0.6);

  --border: rgba(255,255,255,0.06);
  --border-hover: rgba(255,255,255,0.12);
  --border-strong: rgba(255,255,255,0.2);

  --text: #e8e8e8;
  --text-secondary: #aaaaaa;
  --text-muted: #777777;
  --text-dim: #444444;

  --primary: #6366f1;
  --primary-hover: #818cf8;
  --primary-glow: rgba(99,102,241,0.15);
  --primary-text: #ffffff;

  --nav-bg: rgba(10,10,10,0.85);
  --card-bg: rgba(17,17,17,0.6);
  --card-border: rgba(255,255,255,0.06);
  --card-hover-bg: #161616;
  --card-hover-border: rgba(255,255,255,0.1);

  --btn-primary-bg: var(--primary);
  --btn-primary-text: #ffffff;
  --btn-ghost-border: rgba(255,255,255,0.12);
  --btn-ghost-text: rgba(255,255,255,0.6);
  --btn-ghost-hover-bg: rgba(255,255,255,0.04);

  --badge-bg: transparent;
  --badge-border: rgba(255,255,255,0.08);
  --badge-text: rgba(255,255,255,0.6);

  --divider: rgba(255,255,255,0.04);
  --grid-line: rgba(255,255,255,0.03);
  --dot-color: rgba(255,255,255,0.07);
  --number-color: rgba(255,255,255,0.12);
  --grain-opacity: 0.35;
  --shadow: none;
  --shadow-lg: none;
}

/* Light theme */
[data-theme="light"] {
  --bg: #f8f7f4;
  --bg-surface: #ffffff;
  --bg-raised: #f0eeea;
  --bg-overlay: rgba(255,255,255,0.7);

  --border: rgba(0,0,0,0.08);
  --border-hover: rgba(0,0,0,0.15);
  --border-strong: rgba(0,0,0,0.25);

  --text: #1a1a1a;
  --text-secondary: #4a4a4a;
  --text-muted: #888888;
  --text-dim: #bbbbbb;

  --primary: #1a1a1a;
  --primary-hover: #333333;
  --primary-glow: rgba(0,0,0,0.05);
  --primary-text: #ffffff;

  --nav-bg: rgba(248,247,244,0.85);
  --card-bg: #ffffff;
  --card-border: rgba(0,0,0,0.06);
  --card-hover-bg: #f5f3ef;
  --card-hover-border: rgba(0,0,0,0.12);

  --btn-primary-bg: #1a1a1a;
  --btn-primary-text: #ffffff;
  --btn-ghost-border: rgba(0,0,0,0.12);
  --btn-ghost-text: rgba(0,0,0,0.5);
  --btn-ghost-hover-bg: rgba(0,0,0,0.03);

  --badge-bg: transparent;
  --badge-border: rgba(0,0,0,0.08);
  --badge-text: rgba(0,0,0,0.5);

  --divider: rgba(0,0,0,0.06);
  --grid-line: rgba(0,0,0,0.04);
  --dot-color: rgba(0,0,0,0.06);
  --number-color: rgba(0,0,0,0.1);
  --grain-opacity: 0.15;
  --shadow: 0 1px 3px rgba(0,0,0,0.06);
  --shadow-lg: 0 8px 30px rgba(0,0,0,0.08);
}
```

### Light Theme Accent Variants

Override `--primary` for different industries:

```css
/* Warm editorial (Sixtine-style) */
[data-theme="light"].theme-warm {
  --bg: #f5f0ea;
  --bg-surface: #ece7df;
  --bg-raised: #e5dfd6;
  --primary: #c45a3c;
  --primary-hover: #d4684a;
  --primary-text: #ffffff;
}

/* Forest green (Vitalis-style wellness) */
[data-theme="light"].theme-green {
  --bg: #f9f7f3;
  --primary: #2d4a2d;
  --primary-hover: #3d5e3d;
  --primary-text: #ffffff;
  --btn-primary-bg: #2d4a2d;
}

/* Cool blue (fintech) */
[data-theme="light"].theme-blue {
  --primary: #1e40af;
  --primary-hover: #2563eb;
  --primary-glow: rgba(30,64,175,0.08);
}

/* Neutral luxury (black accent on light) */
[data-theme="light"].theme-luxury {
  --primary: #000000;
  --primary-hover: #222222;
}
```

---

## 2. Theme-Aware Component CSS

Replace ALL hardcoded colors in component styles with variables:

```css
/* === THEME-AWARE BASE STYLES === */
body {
  background: var(--bg);
  color: var(--text);
}

/* Navigation */
nav {
  background: var(--nav-bg);
  border-bottom: 1px solid var(--divider);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
}

nav a { color: var(--text-muted); }
nav a:hover { color: var(--text); }

/* Cards */
.card {
  background: var(--card-bg);
  border: 1px solid var(--card-border);
  box-shadow: var(--shadow);
  transition: all 0.3s ease;
}

.card:hover {
  background: var(--card-hover-bg);
  border-color: var(--card-hover-border);
  box-shadow: var(--shadow-lg);
}

/* Numbered detail labels */
.card .number-label {
  color: var(--number-color);
}

/* Primary button */
.btn-primary {
  background: var(--btn-primary-bg);
  color: var(--btn-primary-text);
}

/* Ghost button */
.btn-ghost {
  border: 1px solid var(--btn-ghost-border);
  color: var(--btn-ghost-text);
}
.btn-ghost:hover {
  background: var(--btn-ghost-hover-bg);
  border-color: var(--border-hover);
}

/* Badge/pill */
.badge {
  border: 1px solid var(--badge-border);
  color: var(--badge-text);
}

/* Text classes */
.text-primary { color: var(--text); }
.text-secondary { color: var(--text-secondary); }
.text-muted { color: var(--text-muted); }
.text-dim { color: var(--text-dim); }

/* Dividers */
.divider { border-color: var(--divider); }
hr { border-color: var(--divider); }

/* Background patterns */
.bg-grid {
  background-image:
    linear-gradient(var(--grid-line) 1px, transparent 1px),
    linear-gradient(90deg, var(--grid-line) 1px, transparent 1px);
  background-size: 60px 60px;
}

.bg-dots {
  background-image: radial-gradient(circle, var(--dot-color) 1px, transparent 1px);
  background-size: 24px 24px;
}

/* Grain overlay adapts to theme */
body::after {
  opacity: var(--grain-opacity);
}
```

---

## 3. Dark/Light Toggle Button

### Toggle Component (place in nav)

```html
<!-- Theme toggle button -->
<button id="theme-toggle" class="relative w-9 h-9 rounded-full border border-[--border] bg-[--bg-surface] flex items-center justify-center hover:border-[--border-hover] transition-all" aria-label="Toggle theme">
  <!-- Sun icon (shown in dark mode) -->
  <svg class="w-4 h-4 theme-icon-sun absolute transition-all" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
    <circle cx="12" cy="12" r="5"/><path d="M12 1v2m0 18v2M4.22 4.22l1.42 1.42m12.72 12.72l1.42 1.42M1 12h2m18 0h2M4.22 19.78l1.42-1.42M18.36 5.64l1.42-1.42"/>
  </svg>
  <!-- Moon icon (shown in light mode) -->
  <svg class="w-4 h-4 theme-icon-moon absolute transition-all" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
    <path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/>
  </svg>
</button>
```

### Toggle CSS

```css
/* Icon visibility based on theme */
[data-theme="dark"] .theme-icon-sun { opacity: 1; transform: rotate(0deg); }
[data-theme="dark"] .theme-icon-moon { opacity: 0; transform: rotate(-90deg); }
[data-theme="light"] .theme-icon-sun { opacity: 0; transform: rotate(90deg); }
[data-theme="light"] .theme-icon-moon { opacity: 1; transform: rotate(0deg); }

/* Smooth theme transition */
body,
body *,
body *::before,
body *::after {
  transition: background-color 0.3s ease, color 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
}
```

### Toggle JavaScript

**CRITICAL**: Place theme detection script in `<head>` (before body renders) to prevent flash of wrong theme (FOWT).

```html
<head>
  <!-- ... other head content ... -->

  <!-- ANTI-FOWT: Detect theme before page renders -->
  <script>
    (function() {
      const stored = localStorage.getItem('theme');
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      const theme = stored || (prefersDark ? 'dark' : 'light');
      document.documentElement.setAttribute('data-theme', theme);
    })();
  </script>
</head>
```

```javascript
// Toggle logic (place at bottom of page with other scripts)
const toggle = document.getElementById('theme-toggle');
const html = document.documentElement;

toggle?.addEventListener('click', () => {
  const current = html.getAttribute('data-theme');
  const next = current === 'dark' ? 'light' : 'dark';
  html.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
});

// Listen for system preference changes
window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', (e) => {
  if (!localStorage.getItem('theme')) {
    html.setAttribute('data-theme', e.matches ? 'dark' : 'light');
  }
});
```

---

## 4. Light Theme Component Patterns

### Light Nav (Editorial Style)

```html
<nav class="fixed top-0 w-full z-50" style="background: var(--nav-bg); backdrop-filter: blur(12px); border-bottom: 1px solid var(--divider);">
  <div class="max-w-7xl mx-auto px-5 md:px-8 flex items-center justify-between h-16">
    <a href="#" class="font-heading text-lg italic" style="color: var(--text);">Sixtine</a>
    <div class="hidden md:flex items-center gap-8 text-sm" style="color: var(--text-muted);">
      <a href="#" class="hover:opacity-100 transition-opacity" style="opacity: 0.6;">Studio</a>
      <span class="text-xs opacity-30">/</span>
      <a href="#" class="hover:opacity-100 transition-opacity" style="opacity: 0.6;">Expertise</a>
      <span class="text-xs opacity-30">/</span>
      <a href="#" class="hover:opacity-100 transition-opacity" style="opacity: 0.6;">Portfolio</a>
    </div>
    <div class="flex items-center gap-4">
      <button id="theme-toggle" class="w-9 h-9 rounded-full flex items-center justify-center" style="border: 1px solid var(--border);" aria-label="Toggle theme">
        <!-- icons -->
      </button>
      <a href="#" class="w-10 h-10 rounded-full flex items-center justify-center" style="border: 1px solid var(--border); color: var(--primary);">
        <span class="iconify text-sm" data-icon="solar:hamburger-menu-linear"></span>
      </a>
    </div>
  </div>
</nav>
```

### Light Hero — Editorial (Sixtine-style)

```html
<section class="relative min-h-screen flex flex-col justify-center pt-20 pb-16" style="background: var(--bg);">
  <div class="max-w-7xl mx-auto px-5 md:px-8 w-full">
    <!-- Oversized headline spanning full width -->
    <h1 class="anim-intro d1 text-5xl md:text-7xl lg:text-[8rem] leading-[0.95] tracking-tight font-heading">
      <span style="color: var(--text);">Timeless</span><br>
      <span class="italic" style="color: var(--text-muted);">Spatial</span>
      <!-- Decorative horizontal line -->
      <span class="hidden md:inline-block w-32 h-px mx-6 align-middle" style="background: var(--border-strong);"></span>
      <span class="font-bold" style="color: var(--text);">Design</span>
    </h1>

    <!-- Metadata row -->
    <div class="anim-intro d3 flex items-center justify-between mt-8 pt-4" style="border-top: 1px solid var(--divider);">
      <span class="text-xs tracking-[0.15em] uppercase" style="color: var(--text-dim);">The Sixtine Residence</span>
      <span class="text-xs" style="color: var(--text-dim);">2024</span>
      <span class="text-xs tracking-[0.15em] uppercase" style="color: var(--text-dim);">Private Estate</span>
    </div>
  </div>
</section>
```

### Light Hero — Centered (Vitalis-style)

```html
<section class="relative pt-32 pb-20 text-center" style="background: var(--bg);">
  <!-- Social proof logos -->
  <div class="anim-intro d1 flex items-center justify-center gap-8 mb-12 opacity-30">
    <span class="text-sm font-medium tracking-wider">Uber</span>
    <span class="text-sm font-medium tracking-wider">NASA</span>
    <span class="text-sm font-medium tracking-wider">VISA</span>
  </div>

  <!-- Headline -->
  <h1 class="anim-intro d2 text-4xl md:text-6xl lg:text-7xl font-heading leading-[1.1] tracking-tight max-w-4xl mx-auto px-5 mb-6" style="color: var(--text);">
    Engineered Nutrition for Systemic Wellness
  </h1>

  <!-- Description -->
  <p class="anim-intro d3 text-base md:text-lg max-w-2xl mx-auto px-5 mb-10 leading-relaxed" style="color: var(--text-muted);">
    Whole-food formulations designed to optimize microbiome diversity and metabolic flexibility.
    No prep. No fillers. Pure biological signal.
  </p>

  <!-- CTA -->
  <div class="anim-intro d4">
    <a href="#" class="inline-flex items-center gap-2 px-8 py-3.5 rounded-full text-sm font-medium transition-all duration-300 hover:brightness-110" style="background: var(--btn-primary-bg); color: var(--btn-primary-text);">
      View Menu
    </a>
  </div>
</section>
```

### Light Cards — Soft Shadow (replaces border-heavy dark style)

```html
<div class="rounded-2xl p-7 transition-all duration-300 group"
     style="background: var(--card-bg); border: 1px solid var(--card-border); box-shadow: var(--shadow);"
     onmouseover="this.style.boxShadow='var(--shadow-lg)'; this.style.borderColor='var(--card-hover-border)'"
     onmouseout="this.style.boxShadow='var(--shadow)'; this.style.borderColor='var(--card-border)'">
  <span class="absolute top-5 right-5 text-[0.6rem] font-mono" style="color: var(--number-color);">01</span>
  <div class="w-11 h-11 rounded-lg flex items-center justify-center mb-6" style="background: var(--bg-raised); border: 1px solid var(--card-border);">
    <span class="iconify text-lg" data-icon="solar:magnifer-bold" style="color: var(--primary);"></span>
  </div>
  <h3 class="font-heading italic text-lg mb-2" style="color: var(--text);">Infrastructure Audit</h3>
  <p class="text-sm leading-relaxed" style="color: var(--text-muted);">Description text here.</p>
</div>
```

### Light Statement Text (large editorial block — Sixtine/Etheria style)

```html
<section class="py-24 md:py-32" style="background: var(--bg);">
  <div class="max-w-5xl mx-auto px-5 md:px-8">
    <p class="text-2xl md:text-4xl lg:text-5xl font-heading italic leading-[1.3]" style="color: var(--text-secondary);" data-animate="up">
      At Sixtine, we believe space is an emotion. We curate environments that transcend utility to become lasting expressions of identity.
    </p>
  </div>
</section>
```

### Light Buttons

```html
<!-- Primary (dark on light) -->
<a href="#" class="inline-flex items-center gap-2 px-6 py-3 rounded-full text-sm font-medium transition-all hover:brightness-90" style="background: var(--btn-primary-bg); color: var(--btn-primary-text);">
  Get Started →
</a>

<!-- Ghost (subtle border) -->
<a href="#" class="inline-flex items-center gap-2 px-6 py-3 rounded-full text-sm transition-all" style="border: 1px solid var(--btn-ghost-border); color: var(--btn-ghost-text);">
  Learn More
</a>

<!-- Text link (editorial style) -->
<a href="#" class="text-xs tracking-[0.15em] uppercase flex items-center gap-2 group" style="color: var(--text);">
  View Project
  <span class="iconify group-hover:translate-x-1 transition-transform" data-icon="solar:arrow-right-linear"></span>
</a>
```

---

## 5. Mixed Theme (Dark Hero → Light Body)

Some sites use a dark hero/nav with light content sections. This is the "Etheria" pattern.

### Implementation

```css
/* The hero stays dark regardless of theme */
.hero-always-dark {
  --bg: #0a0a0a;
  --text: #e8e8e8;
  --text-muted: #888888;
  --border: rgba(255,255,255,0.06);
  --primary-glow: rgba(99,102,241,0.15);
  background: #0a0a0a;
  color: #e8e8e8;
}

/* Transition between dark hero and light body */
.section-transition {
  background: linear-gradient(180deg, #0a0a0a 0%, var(--bg) 100%);
  height: 120px;
  margin-top: -1px; /* prevent gap */
}
```

```html
<!-- Dark hero (forced dark) -->
<section class="hero-always-dark relative min-h-screen ...">
  <!-- Hero content -->
</section>

<!-- Gradient transition -->
<div class="section-transition"></div>

<!-- Light body sections (follow data-theme) -->
<section style="background: var(--bg);">
  <!-- Content -->
</section>
```

---

## 6. Adapting Animations for Light Themes

Most animations work on both themes if they reference CSS variables. Key differences:

### Marquee on Light
```css
/* Dark theme: white text, fade to dark edges */
[data-theme="dark"] .marquee-container {
  mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
}

/* Light theme: dark text, same mask works */
[data-theme="light"] .marquee-container {
  mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
}
```

### Card Hover on Light (shadows instead of border glow)
```css
[data-theme="light"] .card:hover {
  box-shadow: 0 8px 30px rgba(0,0,0,0.08);
  transform: translateY(-2px);
}
```

### Background Glow on Light (softer, warmer)
```css
[data-theme="light"] .hero-glow {
  background: radial-gradient(circle, rgba(0,0,0,0.03) 0%, transparent 70%);
  filter: blur(100px);
}
```

### Status Dots on Light
```css
[data-theme="light"] .status-dot {
  background: var(--primary);
  box-shadow: 0 0 0 3px rgba(0,0,0,0.05);
}
```

---

## 7. Light Theme Design Principles

These rules apply when building light pages:

1. **Hierarchy through weight, not color**: Use font-weight 300/400/500/600/700 and opacity to create text hierarchy, not drastically different colors.

2. **Shadows replace borders**: On light themes, soft `box-shadow` creates depth better than borders. Use `var(--shadow)` and `var(--shadow-lg)` instead of thick borders.

3. **Warm over cool whites**: `#f8f7f4` (warm off-white) feels premium. `#ffffff` feels sterile unless used for cards on a slightly tinted background.

4. **Dark accents, not colored accents**: Many premium light sites use black or near-black as the primary accent (buttons, links) rather than a brand color. The brand color becomes a subtle accent (status dots, highlights).

5. **Generous whitespace**: Light themes need MORE whitespace than dark. Increase `py-24` to `py-32`, increase card padding, increase line-height.

6. **Serif headings are even more important on light**: A serif heading on a light background immediately reads as "designed" vs "template". Use italic for extra editorial feel.

7. **Reduce decorative noise**: Light themes look better with FEWER decorative effects. Skip the grain overlay, reduce grid/dot intensity, rely on typography and space.

8. **Image treatment**: On dark themes, images have dark surrounds. On light themes, use `rounded-xl overflow-hidden` with subtle shadows, or full-bleed with no border.
