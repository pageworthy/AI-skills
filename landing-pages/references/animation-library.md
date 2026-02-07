# Animation Library Reference

Complete catalog of copy-paste CSS animation patterns for landing pages. All animations use hardware-accelerated properties only (`transform`, `opacity`, `filter`) for 60fps performance.

---

## 1. Page Load Intro Animations

### Fade + Slide + Blur (Default — use on every page)

```css
@keyframes fadeInUp {
  from {
    opacity: 0.01;
    transform: translateY(24px);
    filter: blur(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

@keyframes fadeInDown {
  from {
    opacity: 0.01;
    transform: translateY(-24px);
    filter: blur(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
    filter: blur(0);
  }
}

@keyframes fadeInLeft {
  from {
    opacity: 0.01;
    transform: translateX(-30px);
    filter: blur(6px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
    filter: blur(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0.01;
    transform: translateX(30px);
    filter: blur(6px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
    filter: blur(0);
  }
}

@keyframes fadeInScale {
  from {
    opacity: 0.01;
    transform: scale(0.95);
    filter: blur(6px);
  }
  to {
    opacity: 1;
    transform: scale(1);
    filter: blur(0);
  }
}

/* Apply classes with staggered delays */
.anim-intro     { animation: fadeInUp 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both; }
.anim-intro-down{ animation: fadeInDown 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both; }
.anim-intro-left{ animation: fadeInLeft 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both; }
.anim-intro-right{animation: fadeInRight 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both; }
.anim-intro-scale{animation: fadeInScale 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) both; }

/* Stagger delays — use on hero children */
.d1 { animation-delay: 0.05s; }
.d2 { animation-delay: 0.1s; }
.d3 { animation-delay: 0.15s; }
.d4 { animation-delay: 0.2s; }
.d5 { animation-delay: 0.25s; }
.d6 { animation-delay: 0.3s; }
.d7 { animation-delay: 0.4s; }
.d8 { animation-delay: 0.5s; }
.d9 { animation-delay: 0.6s; }
.d10 { animation-delay: 0.75s; }
```

---

## 2. Scroll-Triggered Animations

### JavaScript Observer (place once at bottom of page)

```javascript
// Scroll animation observer
const scrollObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('in-view');
      // Optional: unobserve after triggering (animate once)
      // scrollObserver.unobserve(entry.target);
    }
  });
}, {
  threshold: 0.12,
  rootMargin: '0px 0px -60px 0px'
});

document.querySelectorAll('[data-animate]').forEach(el => {
  scrollObserver.observe(el);
});
```

### CSS for scroll animations

```css
/* Base hidden state for scroll-animated elements */
[data-animate] {
  opacity: 0.01;
  transition: opacity 0.7s ease, transform 0.7s ease, filter 0.7s ease;
}

[data-animate="up"] {
  transform: translateY(30px);
  filter: blur(4px);
}

[data-animate="down"] {
  transform: translateY(-30px);
  filter: blur(4px);
}

[data-animate="left"] {
  transform: translateX(-30px);
  filter: blur(4px);
}

[data-animate="right"] {
  transform: translateX(30px);
  filter: blur(4px);
}

[data-animate="scale"] {
  transform: scale(0.92);
  filter: blur(4px);
}

[data-animate="fade"] {
  filter: blur(4px);
}

/* Visible state */
[data-animate].in-view {
  opacity: 1;
  transform: translateY(0) translateX(0) scale(1);
  filter: blur(0);
}

/* Stagger children inside a container */
.stagger > [data-animate]:nth-child(1) { transition-delay: 0s; }
.stagger > [data-animate]:nth-child(2) { transition-delay: 0.08s; }
.stagger > [data-animate]:nth-child(3) { transition-delay: 0.16s; }
.stagger > [data-animate]:nth-child(4) { transition-delay: 0.24s; }
.stagger > [data-animate]:nth-child(5) { transition-delay: 0.32s; }
.stagger > [data-animate]:nth-child(6) { transition-delay: 0.4s; }
.stagger > [data-animate]:nth-child(7) { transition-delay: 0.48s; }
.stagger > [data-animate]:nth-child(8) { transition-delay: 0.56s; }
```

### Usage in HTML

```html
<div class="stagger">
  <div data-animate="up">First item</div>
  <div data-animate="up">Second item (delayed)</div>
  <div data-animate="up">Third item (more delayed)</div>
</div>
```

---

## 3. Marquee / Infinite Ticker

### Logo Marquee

```css
.marquee-container {
  overflow: hidden;
  mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
  -webkit-mask-image: linear-gradient(90deg, transparent, black 10%, black 90%, transparent);
}

.marquee-track {
  display: flex;
  gap: 3rem;
  width: max-content;
  animation: marquee-scroll 35s linear infinite;
}

.marquee-track:hover {
  animation-play-state: paused;
}

@keyframes marquee-scroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

/* Reverse direction variant */
.marquee-track-reverse {
  animation-direction: reverse;
}
```

### HTML structure (items MUST be duplicated for seamless loop)

```html
<div class="marquee-container py-8 border-y border-white/[0.06]">
  <div class="marquee-track">
    <!-- Original set -->
    <div class="flex items-center gap-2 text-white/30 text-sm whitespace-nowrap">
      <span class="iconify" data-icon="solar:bolt-circle-bold"></span> PROCESS AUTOMATION
    </div>
    <!-- ... more items ... -->

    <!-- DUPLICATE the entire set for seamless loop -->
    <div class="flex items-center gap-2 text-white/30 text-sm whitespace-nowrap">
      <span class="iconify" data-icon="solar:bolt-circle-bold"></span> PROCESS AUTOMATION
    </div>
    <!-- ... duplicated items ... -->
  </div>
</div>
```

### Text Marquee (for testimonials or announcements)

```css
.text-marquee {
  animation: marquee-scroll 20s linear infinite;
  font-size: clamp(2rem, 5vw, 5rem);
  white-space: nowrap;
  color: rgba(255,255,255,0.06);
  font-family: var(--font-heading);
  font-style: italic;
}
```

---

## 4. Border Beam Animation

Animated gradient that travels around an element's border. Premium hover effect.

```css
/* Requires CSS @property for animation */
@property --beam-angle {
  syntax: '<angle>';
  initial-value: 0deg;
  inherits: false;
}

.border-beam {
  position: relative;
  overflow: hidden;
  border-radius: 9999px; /* or your border-radius */
}

.border-beam::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px; /* border width */
  background: conic-gradient(
    from var(--beam-angle),
    transparent 0%,
    transparent 70%,
    var(--primary, #6366f1) 85%,
    white 95%,
    transparent 100%
  );
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: beam-spin 4s linear infinite;
}

@keyframes beam-spin {
  to { --beam-angle: 360deg; }
}

/* Hover-only variant */
.border-beam-hover::before {
  opacity: 0;
  transition: opacity 0.3s ease;
}
.border-beam-hover:hover::before {
  opacity: 1;
}
```

### Card Border Beam (rectangular)
```css
.card-beam {
  position: relative;
  border-radius: 1rem;
}
.card-beam::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: conic-gradient(
    from var(--beam-angle),
    transparent 0%,
    transparent 75%,
    rgba(255,255,255,0.15) 90%,
    transparent 100%
  );
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  animation: beam-spin 6s linear infinite;
}
```

---

## 5. Sonar / Pulse Effects

### Sonar Rings (expanding circles)

```css
.sonar {
  position: relative;
}

.sonar::before,
.sonar::after {
  content: '';
  position: absolute;
  inset: -4px;
  border-radius: 50%;
  border: 1px solid var(--primary, #6366f1);
  opacity: 0;
  animation: sonar-ring 3s ease-out infinite;
}

.sonar::after {
  animation-delay: 1.5s;
}

@keyframes sonar-ring {
  0% {
    transform: scale(1);
    opacity: 0.4;
  }
  100% {
    transform: scale(2.5);
    opacity: 0;
  }
}
```

### Status Dot Pulse

```css
.status-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--primary, #6366f1);
  position: relative;
}

.status-dot::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 50%;
  background: inherit;
  animation: dot-pulse 2s ease-in-out infinite;
}

@keyframes dot-pulse {
  0%, 100% { transform: scale(1); opacity: 1; }
  50% { transform: scale(2.5); opacity: 0; }
}
```

---

## 6. Background Effects

### Gradient Mesh Glow

```css
.bg-glow {
  position: absolute;
  width: 100%;
  height: 100%;
  overflow: hidden;
  pointer-events: none;
}

.bg-glow .orb {
  position: absolute;
  border-radius: 50%;
  filter: blur(100px);
  opacity: 0.15;
  animation: float-orb 20s ease-in-out infinite;
}

.bg-glow .orb-1 {
  width: 500px;
  height: 500px;
  background: var(--primary, #6366f1);
  top: -20%;
  left: -10%;
}

.bg-glow .orb-2 {
  width: 400px;
  height: 400px;
  background: #8b5cf6;
  bottom: -15%;
  right: -5%;
  animation-delay: -7s;
  animation-direction: reverse;
}

@keyframes float-orb {
  0%, 100% { transform: translate(0, 0) scale(1); }
  33% { transform: translate(30px, -40px) scale(1.05); }
  66% { transform: translate(-20px, 20px) scale(0.95); }
}
```

### CSS Grid Background

```css
.bg-grid {
  background-image:
    linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse 50% 50% at 50% 50%, black 40%, transparent 100%);
  -webkit-mask-image: radial-gradient(ellipse 50% 50% at 50% 50%, black 40%, transparent 100%);
}
```

### Dot Matrix Background

```css
.bg-dots {
  background-image: radial-gradient(circle, rgba(255,255,255,0.07) 1px, transparent 1px);
  background-size: 20px 20px;
  mask-image: radial-gradient(ellipse 60% 50% at 50% 50%, black 30%, transparent 100%);
  -webkit-mask-image: radial-gradient(ellipse 60% 50% at 50% 50%, black 30%, transparent 100%);
}
```

### Noise/Grain Overlay (SVG-based, ultra lightweight)

```css
.grain::after {
  content: '';
  position: fixed;
  inset: 0;
  z-index: 9999;
  pointer-events: none;
  opacity: 0.35;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
}
```

### Vertical Light Beam

```css
.light-beam {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background: linear-gradient(180deg, var(--primary) 0%, transparent 100%);
  opacity: 0.3;
}

.light-beam::before {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 200px;
  height: 400px;
  background: radial-gradient(ellipse at center top, var(--primary-glow) 0%, transparent 70%);
  filter: blur(40px);
}
```

### Animated Grid Mesh with Glow (Aura Financial-style)

Premium dark background with a visible grid that has a pulsing color glow behind it. Creates a "holographic blueprint" feel.

```css
.bg-grid-glow {
  position: absolute;
  inset: 0;
  overflow: hidden;
  pointer-events: none;
}

/* The grid lines */
.bg-grid-glow .grid-lines {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(rgba(var(--primary-rgb, 99,102,241), 0.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(var(--primary-rgb, 99,102,241), 0.06) 1px, transparent 1px);
  background-size: 40px 40px;
  mask-image: radial-gradient(ellipse 70% 60% at 55% 40%, black 10%, transparent 70%);
  -webkit-mask-image: radial-gradient(ellipse 70% 60% at 55% 40%, black 10%, transparent 70%);
}

/* The ambient glow behind the grid */
.bg-grid-glow .glow {
  position: absolute;
  width: 80%;
  height: 80%;
  top: 10%;
  left: 10%;
  background: radial-gradient(
    ellipse 50% 40% at 55% 40%,
    rgba(var(--primary-rgb, 99,102,241), 0.12) 0%,
    rgba(var(--primary-rgb, 99,102,241), 0.04) 40%,
    transparent 70%
  );
  filter: blur(60px);
  animation: mesh-pulse 10s ease-in-out infinite alternate;
}

@keyframes mesh-pulse {
  0% { opacity: 0.5; transform: scale(1) translate(0, 0); }
  50% { opacity: 0.8; transform: scale(1.05) translate(10px, -10px); }
  100% { opacity: 0.5; transform: scale(0.98) translate(-5px, 5px); }
}
```

**HTML structure:**
```html
<div class="bg-grid-glow">
  <div class="grid-lines"></div>
  <div class="glow"></div>
</div>
```

### Orbital Rings Decoration

Animated concentric circles with a traveling dot. Perfect positioned in the right side of a hero. Purely CSS, no JS.

```css
.orbital-decoration {
  position: absolute;
  width: 350px;
  height: 350px;
  right: 8%;
  top: 25%;
  pointer-events: none;
}

.orbital-ring {
  position: absolute;
  border: 1px solid rgba(var(--primary-rgb, 99,102,241), 0.1);
  border-radius: 50%;
  animation: orbital-rotate 40s linear infinite;
}

.orbital-ring:nth-child(1) { inset: 0; }
.orbital-ring:nth-child(2) { inset: 30px; animation-duration: 30s; animation-direction: reverse; }
.orbital-ring:nth-child(3) { inset: 70px; animation-duration: 20s; border-style: dashed; opacity: 0.5; }

/* Traveling dot on the outer ring */
.orbital-dot {
  position: absolute;
  width: 10px;
  height: 10px;
  background: var(--primary, #6366f1);
  border-radius: 50%;
  top: 50%;
  left: -5px;
  box-shadow: 0 0 15px var(--primary-glow, rgba(99,102,241,0.4));
  animation: orbital-rotate 40s linear infinite;
}

/* Center point */
.orbital-center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 12px;
  height: 12px;
  border: 2px solid var(--primary, #6366f1);
  border-radius: 50%;
}
.orbital-center::after {
  content: '';
  position: absolute;
  inset: 3px;
  background: var(--primary, #6366f1);
  border-radius: 50%;
}

/* Connection lines (angled beams from center to edge) */
.orbital-beam {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 175px;
  height: 1px;
  background: linear-gradient(90deg, rgba(var(--primary-rgb, 99,102,241), 0.2) 0%, transparent 100%);
  transform-origin: left center;
}
.orbital-beam:nth-child(5) { transform: rotate(30deg); }
.orbital-beam:nth-child(6) { transform: rotate(150deg); }
.orbital-beam:nth-child(7) { transform: rotate(250deg); }

@keyframes orbital-rotate {
  to { transform: rotate(360deg); }
}
```

**HTML structure:**
```html
<div class="orbital-decoration">
  <div class="orbital-ring"></div>
  <div class="orbital-ring"></div>
  <div class="orbital-ring"></div>
  <div class="orbital-dot"></div>
  <div class="orbital-center"></div>
  <div class="orbital-beam"></div>
  <div class="orbital-beam"></div>
  <div class="orbital-beam"></div>
</div>
```

---

## 7. Text Effects

### Gradient Text

```css
.text-gradient {
  background: linear-gradient(135deg, #fff 0%, rgba(255,255,255,0.5) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.text-gradient-primary {
  background: linear-gradient(135deg, var(--primary) 0%, #c084fc 50%, var(--primary) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Animated shimmer text */
.text-shimmer {
  background: linear-gradient(
    90deg,
    rgba(255,255,255,0.5) 0%,
    #fff 25%,
    rgba(255,255,255,0.5) 50%,
    #fff 75%,
    rgba(255,255,255,0.5) 100%
  );
  background-size: 200% 100%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: text-shimmer 3s linear infinite;
}

@keyframes text-shimmer {
  0% { background-position: 200% center; }
  100% { background-position: -200% center; }
}
```

### Typewriter Effect

```css
.typewriter {
  overflow: hidden;
  white-space: nowrap;
  border-right: 2px solid var(--primary);
  animation:
    typing 2.5s steps(30, end) both,
    blink-caret 0.75s step-end infinite;
}

@keyframes typing {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-caret {
  50% { border-color: transparent; }
}
```

---

## 8. Card Hover Effects

### Lift + Glow

```css
.card-hover {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card-hover:hover {
  transform: translateY(-4px);
  box-shadow: 0 20px 40px -15px rgba(0,0,0,0.5), 0 0 0 1px rgba(255,255,255,0.08);
}
```

### Spotlight (mouse-following glow)

```javascript
document.querySelectorAll('.card-spotlight').forEach(card => {
  card.addEventListener('mousemove', (e) => {
    const rect = card.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;
    card.style.setProperty('--spot-x', x + 'px');
    card.style.setProperty('--spot-y', y + 'px');
  });
});
```

```css
.card-spotlight {
  position: relative;
  overflow: hidden;
}

.card-spotlight::before {
  content: '';
  position: absolute;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(255,255,255,0.06), transparent 70%);
  left: var(--spot-x, -999px);
  top: var(--spot-y, -999px);
  transform: translate(-50%, -50%);
  pointer-events: none;
  transition: opacity 0.3s;
  opacity: 0;
}

.card-spotlight:hover::before {
  opacity: 1;
}
```

### Tilt on Hover (3D perspective)

```javascript
document.querySelectorAll('.card-tilt').forEach(card => {
  card.addEventListener('mousemove', (e) => {
    const rect = card.getBoundingClientRect();
    const x = (e.clientX - rect.left) / rect.width - 0.5;
    const y = (e.clientY - rect.top) / rect.height - 0.5;
    card.style.transform = `perspective(600px) rotateY(${x * 8}deg) rotateX(${-y * 8}deg)`;
  });
  card.addEventListener('mouseleave', () => {
    card.style.transform = 'perspective(600px) rotateY(0deg) rotateX(0deg)';
  });
});
```

```css
.card-tilt {
  transition: transform 0.15s ease;
  transform-style: preserve-3d;
}
```

---

## 9. Noodle / Beam Connecting Lines

Animated SVG lines connecting two elements. Great for showing workflows or connections.

```html
<svg class="noodle-svg" viewBox="0 0 400 100" fill="none">
  <path
    d="M 0 50 C 100 50, 100 10, 200 10 S 300 50, 400 50"
    stroke="url(#beam-gradient)"
    stroke-width="2"
    stroke-dasharray="8 6"
    class="noodle-path"
  />
  <defs>
    <linearGradient id="beam-gradient" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="transparent" />
      <stop offset="50%" stop-color="var(--primary, #6366f1)" />
      <stop offset="100%" stop-color="transparent" />
    </linearGradient>
  </defs>
</svg>
```

```css
.noodle-path {
  stroke-dashoffset: 0;
  animation: noodle-flow 2s linear infinite;
}

@keyframes noodle-flow {
  to { stroke-dashoffset: -28; }
}
```

---

## 10. Number Counter Animation

For stats/metrics sections — count up from 0 to target number.

```javascript
function animateCounters() {
  document.querySelectorAll('[data-count]').forEach(el => {
    const target = parseInt(el.dataset.count);
    const duration = 2000;
    const start = performance.now();

    function update(now) {
      const progress = Math.min((now - start) / duration, 1);
      const eased = 1 - Math.pow(1 - progress, 3); // ease-out cubic
      el.textContent = Math.round(target * eased);
      if (progress < 1) requestAnimationFrame(update);
    }
    requestAnimationFrame(update);
  });
}

// Trigger on scroll into view
const counterObserver = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      animateCounters();
      counterObserver.disconnect();
    }
  });
}, { threshold: 0.3 });

document.querySelector('.stats-section')?.let(el => counterObserver.observe(el));
```

---

## 11. Reduced Motion Support

**ALWAYS include this at the end of your CSS:**

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }

  [data-animate] {
    opacity: 1 !important;
    transform: none !important;
    filter: none !important;
  }
}
```
