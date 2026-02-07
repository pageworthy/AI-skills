# Component Patterns Reference

Ready-to-use section blueprints for landing pages. Each pattern includes HTML structure with Tailwind classes, animations, and responsive behavior.

---

## Navigation — Sticky Glassmorphism

```html
<nav class="fixed top-0 w-full z-50 backdrop-blur-xl bg-[#0a0a0a]/80 border-b border-white/[0.06]">
  <div class="max-w-7xl mx-auto px-5 md:px-8 flex items-center justify-between h-16">
    <!-- Logo -->
    <a href="#" class="flex items-center gap-2 text-white font-semibold tracking-tight">
      <span class="iconify text-lg text-primary" data-icon="solar:star-bold"></span>
      Brand Name
    </a>

    <!-- Desktop Links -->
    <div class="hidden md:flex items-center gap-8 text-sm text-white/50">
      <a href="#" class="hover:text-white transition-colors duration-200">Services</a>
      <a href="#" class="hover:text-white transition-colors duration-200">Case Studies</a>
      <a href="#" class="hover:text-white transition-colors duration-200">About</a>
    </div>

    <!-- CTA -->
    <div class="hidden md:flex items-center gap-4">
      <a href="#" class="text-sm text-white/50 hover:text-white transition-colors">Sign in</a>
      <a href="#" class="text-sm px-4 py-2 border border-white/[0.15] text-white rounded-full hover:bg-white/[0.05] transition-all duration-300 tracking-wide uppercase text-xs font-medium">
        Get Started →
      </a>
    </div>

    <!-- Mobile Menu Button -->
    <button class="md:hidden text-white" onclick="document.getElementById('mobile-menu').classList.toggle('hidden')">
      <span class="iconify text-xl" data-icon="solar:hamburger-menu-linear"></span>
    </button>
  </div>

  <!-- Mobile Menu -->
  <div id="mobile-menu" class="hidden md:hidden border-t border-white/[0.06] px-5 py-6 space-y-4">
    <a href="#" class="block text-white/70 hover:text-white text-sm">Services</a>
    <a href="#" class="block text-white/70 hover:text-white text-sm">Case Studies</a>
    <a href="#" class="block text-white/70 hover:text-white text-sm">About</a>
    <a href="#" class="block text-sm px-4 py-2 bg-primary text-white rounded-full text-center mt-4">Get Started</a>
  </div>
</nav>
```

---

## Hero — Editorial with Background Effects

```html
<section class="relative min-h-screen flex items-center pt-24 pb-16 overflow-hidden">
  <!-- Background layer -->
  <div class="absolute inset-0 bg-grid opacity-40"></div>
  <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[600px] h-[600px] bg-primary/10 rounded-full blur-[120px] pointer-events-none"></div>

  <!-- Content -->
  <div class="relative z-10 max-w-7xl mx-auto px-5 md:px-8 w-full">
    <div class="max-w-3xl">
      <!-- Badge -->
      <div class="anim-intro d1 inline-flex items-center gap-2 px-3 py-1.5 rounded-full border border-white/[0.08] text-xs tracking-[0.15em] uppercase text-white/60 mb-8">
        <span class="w-1.5 h-1.5 rounded-full bg-primary status-dot"></span>
        Advisory Firm
      </div>

      <!-- Headline -->
      <h1 class="anim-intro d2 text-4xl md:text-6xl lg:text-7xl leading-[1.05] tracking-tight mb-6">
        <span class="font-body font-light text-white/80">Deploy Strategic</span><br>
        <span class="font-heading italic text-white">Artificial Intelligence.</span>
      </h1>

      <!-- Subheadline -->
      <p class="anim-intro d3 text-base md:text-lg text-white/45 leading-relaxed max-w-xl mb-10">
        We bridge the gap between emerging models and enterprise value. Architecting custom neural infrastructure for the Fortune 500.
      </p>

      <!-- CTAs -->
      <div class="anim-intro d4 flex flex-wrap gap-4">
        <a href="#" class="inline-flex items-center gap-2 px-6 py-3 bg-primary text-white rounded-full font-medium text-sm hover:brightness-110 transition-all duration-300">
          Book Consultation
          <span class="iconify" data-icon="solar:arrow-right-linear"></span>
        </a>
        <a href="#" class="inline-flex items-center gap-2 px-6 py-3 border border-white/[0.12] text-white/60 rounded-full text-sm hover:bg-white/[0.04] hover:border-white/[0.2] transition-all duration-300">
          View Framework
        </a>
      </div>
    </div>

    <!-- Stats (right side on desktop) -->
    <div class="anim-intro d5 mt-12 lg:mt-0 lg:absolute lg:right-8 lg:top-1/2 lg:-translate-y-1/2 space-y-8">
      <div>
        <span class="text-[0.65rem] tracking-[0.2em] uppercase text-white/30 block mb-1">Efficiency Gain</span>
        <span class="font-heading italic text-5xl text-white">40</span>
        <span class="text-xl text-white/40">%</span>
      </div>
      <div>
        <span class="text-[0.65rem] tracking-[0.2em] uppercase text-white/30 block mb-1">Implementation</span>
        <span class="font-heading italic text-5xl text-white">6</span>
        <span class="text-sm text-white/40 uppercase tracking-wider ml-1">Weeks</span>
      </div>
    </div>
  </div>
</section>
```

---

## Hero — Light Editorial (Sixtine / Interior Design style)

Oversized serif typography spanning the full width, asymmetric layout, decorative horizontal lines, metadata labels at the bottom.

```html
<section class="relative min-h-screen flex flex-col justify-center pt-20 pb-16" style="background: var(--bg);">
  <div class="max-w-7xl mx-auto px-5 md:px-8 w-full">
    <div class="grid grid-cols-1 lg:grid-cols-12 gap-4 items-end">
      <!-- Left: Oversized heading -->
      <div class="lg:col-span-7">
        <h1 class="anim-intro d1 text-5xl md:text-7xl lg:text-[7rem] leading-[0.92] tracking-tight font-heading">
          <span style="color: var(--text);">Timeless</span><br>
          <span class="italic" style="color: var(--text-muted);">Spatial</span>
        </h1>
      </div>

      <!-- Right: image + CTA -->
      <div class="lg:col-span-5 anim-intro d3">
        <span class="text-xs tracking-[0.12em] uppercase block mb-3" style="color: var(--text-dim);">Start the Dialogue</span>
        <div class="rounded-xl overflow-hidden aspect-[4/3]" style="background: var(--bg-raised);">
          <img src="hero-image.jpg" alt="" class="w-full h-full object-cover" loading="eager">
        </div>
      </div>
    </div>

    <!-- Decorative line spanning between text and right column -->
    <div class="hidden lg:block anim-intro d2 mx-auto my-4" style="width: 40%; height: 1px; background: var(--border-strong);"></div>

    <!-- Large right-aligned word -->
    <div class="text-right anim-intro d2">
      <span class="text-5xl md:text-7xl lg:text-[7rem] font-heading font-bold leading-[0.92]" style="color: var(--text);">Design</span>
    </div>

    <!-- Bottom metadata row -->
    <div class="anim-intro d4 flex items-center justify-between mt-10 pt-4" style="border-top: 1px solid var(--divider);">
      <span class="text-xs tracking-[0.12em] uppercase" style="color: var(--text-dim);">The Studio</span>
      <span class="text-xs" style="color: var(--text-dim);">2025</span>
      <span class="text-xs tracking-[0.12em] uppercase" style="color: var(--text-dim);">Private Collection</span>
    </div>
  </div>
</section>
```

---

## Hero — Light Centered (Vitalis / Wellness style)

Clean centered layout, logo bar above headline, single prominent CTA, photography below.

```html
<section class="relative pt-28 pb-16 text-center" style="background: var(--bg);">
  <!-- Trust logos -->
  <div class="anim-intro d1 flex items-center justify-center gap-8 mb-14">
    <span class="text-sm font-medium tracking-wider" style="color: var(--text-dim);">Uber</span>
    <span class="text-sm font-medium tracking-wider" style="color: var(--text-dim);">NASA</span>
    <span class="text-sm font-medium tracking-wider" style="color: var(--text-dim);">VISA</span>
  </div>

  <!-- Headline -->
  <h1 class="anim-intro d2 text-4xl md:text-6xl lg:text-7xl font-heading leading-[1.08] tracking-tight max-w-4xl mx-auto px-5 mb-6" style="color: var(--text);">
    Engineered Nutrition for Systemic Wellness
  </h1>

  <!-- Description -->
  <p class="anim-intro d3 text-base md:text-lg max-w-2xl mx-auto px-5 mb-10 leading-relaxed" style="color: var(--text-muted);">
    Whole-food formulations designed to optimize microbiome diversity and metabolic flexibility. No prep. No fillers.
  </p>

  <!-- CTA -->
  <div class="anim-intro d4 mb-16">
    <a href="#" class="inline-flex items-center gap-2 px-8 py-3.5 rounded-full text-sm font-medium transition-all hover:brightness-90" style="background: var(--btn-primary-bg); color: var(--btn-primary-text);">
      View Menu
    </a>
  </div>

  <!-- Image grid -->
  <div class="anim-intro d5 max-w-6xl mx-auto px-5 md:px-8 grid grid-cols-1 md:grid-cols-3 gap-4">
    <div class="rounded-2xl overflow-hidden aspect-[4/5]" style="box-shadow: var(--shadow-lg);">
      <img src="image1.jpg" alt="" class="w-full h-full object-cover" loading="lazy">
    </div>
    <div class="rounded-2xl overflow-hidden aspect-[4/5]" style="background: var(--bg-raised); box-shadow: var(--shadow);">
      <!-- Icon + minimal content card -->
    </div>
    <div class="rounded-2xl overflow-hidden aspect-[4/5]" style="box-shadow: var(--shadow-lg);">
      <img src="image2.jpg" alt="" class="w-full h-full object-cover" loading="lazy">
    </div>
  </div>
</section>
```

---

## Statement Text — Full Width Editorial Quote

Large italic serif text spanning most of the viewport width. Works beautifully on both light and dark themes.

```html
<section class="py-24 md:py-36" style="background: var(--bg);">
  <div class="max-w-5xl mx-auto px-5 md:px-8" data-animate="up">
    <p class="text-2xl md:text-3xl lg:text-[2.75rem] font-heading italic leading-[1.35] tracking-tight" style="color: var(--text-secondary);">
      At Sixtine, we believe space is an emotion. We curate environments that transcend utility to become lasting expressions of identity.
    </p>
  </div>
</section>
```

---

## Project Card — Light Editorial (Portfolio)

```html
<div data-animate="up" class="group cursor-pointer">
  <!-- Image -->
  <div class="rounded-2xl overflow-hidden mb-4 transition-transform duration-500 group-hover:scale-[1.01]" style="box-shadow: var(--shadow);">
    <img src="project.jpg" alt="" class="w-full aspect-[16/10] object-cover">
  </div>
  <!-- Info row -->
  <div class="flex items-center justify-between">
    <div>
      <span class="text-xs block mb-1" style="color: var(--text-dim);">Featured Work</span>
      <span class="font-heading text-lg" style="color: var(--text);">Azure Coast Villa</span>
    </div>
    <a href="#" class="text-xs tracking-[0.12em] uppercase flex items-center gap-1 opacity-0 group-hover:opacity-100 transition-opacity" style="color: var(--text);">
      View Project
      <span class="iconify" data-icon="solar:arrow-right-linear"></span>
    </a>
  </div>
</div>
```

---

## Logo Ticker — Marquee with Icons

```html
<section class="py-6 border-y border-white/[0.04] overflow-hidden">
  <div class="marquee-container">
    <div class="marquee-track">
      <!-- SET 1 (original) -->
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:bolt-circle-bold"></span> Process Automation
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:shield-check-bold"></span> Data Governance
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:tuning-2-bold"></span> LLM Fine-Tuning
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:graph-up-bold"></span> Predictive Analytics
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:verified-check-bold"></span> Ethical Compliance
      </div>

      <!-- SET 2 (duplicate for seamless loop) -->
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:bolt-circle-bold"></span> Process Automation
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:shield-check-bold"></span> Data Governance
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:tuning-2-bold"></span> LLM Fine-Tuning
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:graph-up-bold"></span> Predictive Analytics
      </div>
      <div class="flex items-center gap-2 text-white/25 text-xs tracking-[0.15em] uppercase whitespace-nowrap px-6">
        <span class="iconify" data-icon="solar:verified-check-bold"></span> Ethical Compliance
      </div>
    </div>
  </div>
</section>
```

---

## Features — Numbered Cards with Icons

```html
<section class="py-24 md:py-32">
  <div class="max-w-7xl mx-auto px-5 md:px-8">
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 stagger">

      <!-- Card 1 -->
      <div data-animate="up" class="relative border border-white/[0.06] rounded-2xl p-7 bg-[#111]/60 hover:bg-[#161616] hover:border-white/[0.1] transition-all duration-300 group">
        <span class="absolute top-5 right-5 text-[0.6rem] text-white/15 font-mono">01</span>
        <div class="w-11 h-11 rounded-lg bg-white/[0.03] border border-white/[0.06] flex items-center justify-center mb-6 group-hover:border-primary/30 transition-colors">
          <span class="iconify text-lg text-primary/70" data-icon="solar:magnifer-bold"></span>
        </div>
        <h3 class="font-heading italic text-lg text-white mb-2">Infrastructure Audit</h3>
        <p class="text-sm text-white/40 leading-relaxed">Deep-dive analysis of your current data stack to identify readiness for vectorization and RAG implementation.</p>
      </div>

      <!-- Card 2 -->
      <div data-animate="up" class="relative border border-white/[0.06] rounded-2xl p-7 bg-[#111]/60 hover:bg-[#161616] hover:border-white/[0.1] transition-all duration-300 group">
        <span class="absolute top-5 right-5 text-[0.6rem] text-white/15 font-mono">02</span>
        <div class="w-11 h-11 rounded-lg bg-white/[0.03] border border-white/[0.06] flex items-center justify-center mb-6 group-hover:border-primary/30 transition-colors">
          <span class="iconify text-lg text-primary/70" data-icon="solar:code-square-bold"></span>
        </div>
        <h3 class="font-heading italic text-lg text-white mb-2">Model Integration</h3>
        <p class="text-sm text-white/40 leading-relaxed">Seamless API orchestration connecting proprietary data with foundational models (GPT-4, Claude, Llama).</p>
      </div>

      <!-- Card 3 -->
      <div data-animate="up" class="relative border border-white/[0.06] rounded-2xl p-7 bg-[#111]/60 hover:bg-[#161616] hover:border-white/[0.1] transition-all duration-300 group">
        <span class="absolute top-5 right-5 text-[0.6rem] text-white/15 font-mono">03</span>
        <div class="w-11 h-11 rounded-lg bg-white/[0.03] border border-white/[0.06] flex items-center justify-center mb-6 group-hover:border-primary/30 transition-colors">
          <span class="iconify text-lg text-primary/70" data-icon="solar:chart-bold"></span>
        </div>
        <h3 class="font-heading italic text-lg text-white mb-2">Strategic Roadmapping</h3>
        <p class="text-sm text-white/40 leading-relaxed">Quarterly execution plans that align AI capabilities with core business KPIs and competitive positioning.</p>
      </div>

    </div>
  </div>
</section>
```

---

## Bento Grid — Asymmetric Feature Showcase

```html
<section class="py-24 md:py-32">
  <div class="max-w-7xl mx-auto px-5 md:px-8">
    <!-- Section heading -->
    <div class="mb-16" data-animate="up">
      <h2 class="text-3xl md:text-5xl leading-tight">
        <span class="font-heading italic text-white/60">Operational</span>
        <span class="font-heading italic font-bold text-white"> System Metrics</span>
      </h2>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 stagger">
      <!-- Large card (image + label) -->
      <div data-animate="up" class="relative rounded-2xl border border-white/[0.06] bg-[#111]/60 overflow-hidden min-h-[360px]">
        <span class="absolute top-5 left-5 text-xs text-primary/60 font-mono">{001}</span>
        <div class="absolute bottom-5 left-5 right-5">
          <span class="text-[0.6rem] tracking-[0.15em] uppercase text-white/30">Neural Core V4.0</span>
        </div>
        <!-- Placeholder for image or visual -->
        <div class="absolute inset-0 bg-gradient-to-b from-primary/5 to-transparent"></div>
      </div>

      <!-- Right side: text + metrics -->
      <div data-animate="up" class="rounded-2xl border border-white/[0.06] bg-[#111]/60 p-8 flex flex-col justify-between">
        <div>
          <div class="flex items-center justify-between mb-6">
            <h3 class="text-2xl md:text-3xl font-heading">
              Scalable <span class="italic text-primary/70">Inference</span> Architecture
            </h3>
            <span class="text-xs text-white/20 tracking-wider">[LIVE MONITOR]</span>
          </div>
          <p class="text-sm text-white/40 uppercase tracking-wide leading-relaxed">
            Deploying adaptive neural networks for enterprise-grade decisioning and real-time data synthesis.
          </p>
        </div>

        <!-- Metric row -->
        <div class="grid grid-cols-3 gap-3 mt-8">
          <div class="rounded-xl border border-white/[0.06] bg-white/[0.02] p-4">
            <span class="text-[0.6rem] tracking-[0.15em] uppercase text-white/30 block mb-1">Latency</span>
            <span class="text-2xl font-heading text-white">12<span class="text-sm text-white/40">ms</span></span>
          </div>
          <div class="rounded-xl border border-white/[0.06] bg-white/[0.02] p-4">
            <span class="text-[0.6rem] tracking-[0.15em] uppercase text-white/30 block mb-1">Uptime</span>
            <span class="text-2xl font-heading text-white">99.99<span class="text-sm text-white/40">%</span></span>
          </div>
          <div class="rounded-xl border border-white/[0.06] bg-white/[0.02] p-4">
            <span class="text-[0.6rem] tracking-[0.15em] uppercase text-white/30 block mb-1">Throughput</span>
            <span class="text-2xl font-heading text-white">850<span class="text-sm text-white/40">T</span></span>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
```

---

## Testimonial — Minimal Quote Card

```html
<section class="py-24 md:py-32 border-t border-white/[0.04]">
  <div class="max-w-4xl mx-auto px-5 md:px-8 text-center" data-animate="up">
    <span class="text-6xl text-white/10 font-heading italic block mb-6">"</span>
    <blockquote class="text-xl md:text-2xl text-white/70 leading-relaxed font-heading italic mb-8">
      Their AI implementation cut our processing time by 60% and uncovered revenue streams we didn't know existed.
    </blockquote>
    <div class="flex items-center justify-center gap-3">
      <div class="w-10 h-10 rounded-full bg-white/[0.06] border border-white/[0.08]"></div>
      <div class="text-left">
        <span class="text-sm text-white/80 block">Sarah Chen</span>
        <span class="text-xs text-white/30">CTO, Meridian Systems</span>
      </div>
    </div>
  </div>
</section>
```

---

## Pricing — Three-Tier Cards

```html
<section class="py-24 md:py-32">
  <div class="max-w-7xl mx-auto px-5 md:px-8">
    <div class="text-center mb-16" data-animate="up">
      <h2 class="text-3xl md:text-5xl font-heading italic text-white mb-4">Simple Pricing</h2>
      <p class="text-white/40">Choose the plan that scales with you.</p>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 max-w-5xl mx-auto stagger">
      <!-- Starter -->
      <div data-animate="up" class="rounded-2xl border border-white/[0.06] bg-[#111]/60 p-7">
        <span class="text-xs tracking-[0.15em] uppercase text-white/30">Starter</span>
        <div class="mt-4 mb-6">
          <span class="text-4xl font-heading text-white">$49</span>
          <span class="text-sm text-white/30">/mo</span>
        </div>
        <ul class="space-y-3 text-sm text-white/50 mb-8">
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> Feature one</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> Feature two</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> Feature three</li>
        </ul>
        <a href="#" class="block text-center py-2.5 rounded-full border border-white/[0.1] text-sm text-white/60 hover:bg-white/[0.04] transition-all">Get Started</a>
      </div>

      <!-- Pro (highlighted) -->
      <div data-animate="up" class="rounded-2xl border border-primary/30 bg-[#111]/80 p-7 relative card-beam">
        <span class="absolute -top-3 left-1/2 -translate-x-1/2 text-[0.6rem] px-3 py-0.5 bg-primary text-white rounded-full tracking-wider uppercase">Popular</span>
        <span class="text-xs tracking-[0.15em] uppercase text-white/30">Professional</span>
        <div class="mt-4 mb-6">
          <span class="text-4xl font-heading text-white">$149</span>
          <span class="text-sm text-white/30">/mo</span>
        </div>
        <ul class="space-y-3 text-sm text-white/50 mb-8">
          <li class="flex items-center gap-2"><span class="iconify text-primary" data-icon="solar:check-circle-bold"></span> Everything in Starter</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary" data-icon="solar:check-circle-bold"></span> Advanced feature</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary" data-icon="solar:check-circle-bold"></span> Priority support</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary" data-icon="solar:check-circle-bold"></span> Team access</li>
        </ul>
        <a href="#" class="block text-center py-2.5 rounded-full bg-primary text-white text-sm font-medium hover:brightness-110 transition-all">Get Started →</a>
      </div>

      <!-- Enterprise -->
      <div data-animate="up" class="rounded-2xl border border-white/[0.06] bg-[#111]/60 p-7">
        <span class="text-xs tracking-[0.15em] uppercase text-white/30">Enterprise</span>
        <div class="mt-4 mb-6">
          <span class="text-4xl font-heading text-white">Custom</span>
        </div>
        <ul class="space-y-3 text-sm text-white/50 mb-8">
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> Everything in Pro</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> Dedicated support</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> Custom integrations</li>
          <li class="flex items-center gap-2"><span class="iconify text-primary/60" data-icon="solar:check-circle-bold"></span> SLA guarantee</li>
        </ul>
        <a href="#" class="block text-center py-2.5 rounded-full border border-white/[0.1] text-sm text-white/60 hover:bg-white/[0.04] transition-all">Contact Sales</a>
      </div>
    </div>
  </div>
</section>
```

---

## CTA Section — Full Width with Glow

```html
<section class="py-24 md:py-32 relative overflow-hidden">
  <!-- Background glow -->
  <div class="absolute inset-0 flex items-center justify-center pointer-events-none">
    <div class="w-[500px] h-[500px] bg-primary/10 rounded-full blur-[120px]"></div>
  </div>

  <div class="relative z-10 max-w-3xl mx-auto px-5 md:px-8 text-center" data-animate="up">
    <h2 class="text-3xl md:text-5xl font-heading italic text-white mb-4">Ready to get started?</h2>
    <p class="text-white/40 mb-10 text-lg">Join hundreds of companies already using our platform.</p>
    <div class="flex flex-wrap justify-center gap-4">
      <a href="#" class="inline-flex items-center gap-2 px-8 py-3.5 bg-primary text-white rounded-full font-medium hover:brightness-110 transition-all border-beam">
        Start Free Trial
        <span class="iconify" data-icon="solar:arrow-right-linear"></span>
      </a>
      <a href="#" class="inline-flex items-center gap-2 px-8 py-3.5 border border-white/[0.12] text-white/60 rounded-full hover:bg-white/[0.04] transition-all">
        Talk to Sales
      </a>
    </div>
  </div>
</section>
```

---

## Footer — Minimal Dark

```html
<footer class="border-t border-white/[0.04] py-16">
  <div class="max-w-7xl mx-auto px-5 md:px-8">
    <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-12">
      <!-- Column 1 -->
      <div>
        <a href="#" class="flex items-center gap-2 text-white font-semibold mb-6">
          <span class="iconify text-primary" data-icon="solar:star-bold"></span>
          Brand
        </a>
        <p class="text-xs text-white/30 leading-relaxed">Building the future of intelligent systems.</p>
      </div>

      <!-- Column 2 -->
      <div>
        <h4 class="text-xs tracking-[0.15em] uppercase text-white/40 mb-4">Product</h4>
        <ul class="space-y-2 text-sm text-white/30">
          <li><a href="#" class="hover:text-white/60 transition-colors">Features</a></li>
          <li><a href="#" class="hover:text-white/60 transition-colors">Pricing</a></li>
          <li><a href="#" class="hover:text-white/60 transition-colors">Docs</a></li>
        </ul>
      </div>

      <!-- Column 3 -->
      <div>
        <h4 class="text-xs tracking-[0.15em] uppercase text-white/40 mb-4">Company</h4>
        <ul class="space-y-2 text-sm text-white/30">
          <li><a href="#" class="hover:text-white/60 transition-colors">About</a></li>
          <li><a href="#" class="hover:text-white/60 transition-colors">Blog</a></li>
          <li><a href="#" class="hover:text-white/60 transition-colors">Careers</a></li>
        </ul>
      </div>

      <!-- Column 4 -->
      <div>
        <h4 class="text-xs tracking-[0.15em] uppercase text-white/40 mb-4">Legal</h4>
        <ul class="space-y-2 text-sm text-white/30">
          <li><a href="#" class="hover:text-white/60 transition-colors">Privacy</a></li>
          <li><a href="#" class="hover:text-white/60 transition-colors">Terms</a></li>
        </ul>
      </div>
    </div>

    <!-- Bottom bar -->
    <div class="pt-8 border-t border-white/[0.04] flex flex-col md:flex-row items-center justify-between gap-4">
      <span class="text-xs text-white/20">© 2025 Brand Name. All rights reserved.</span>
      <div class="flex items-center gap-4 text-white/20">
        <a href="#" class="hover:text-white/40 transition-colors"><span class="iconify text-lg" data-icon="mdi:twitter"></span></a>
        <a href="#" class="hover:text-white/40 transition-colors"><span class="iconify text-lg" data-icon="mdi:linkedin"></span></a>
        <a href="#" class="hover:text-white/40 transition-colors"><span class="iconify text-lg" data-icon="mdi:github"></span></a>
      </div>
    </div>
  </div>
</footer>
```

---

## Code Block / Developer Section

For SaaS/developer-facing products, include a code preview panel.

```html
<div class="rounded-xl border border-white/[0.06] bg-[#0d0d0d] overflow-hidden">
  <!-- Terminal dots -->
  <div class="flex items-center gap-1.5 px-4 py-3 border-b border-white/[0.04]">
    <span class="w-2.5 h-2.5 rounded-full bg-white/[0.08]"></span>
    <span class="w-2.5 h-2.5 rounded-full bg-white/[0.08]"></span>
    <span class="w-2.5 h-2.5 rounded-full bg-white/[0.08]"></span>
  </div>
  <!-- Code content -->
  <pre class="p-5 text-sm leading-relaxed font-mono overflow-x-auto"><code><span class="text-purple-400">import</span> { Nebula } <span class="text-purple-400">from</span> <span class="text-green-400">"@nebula/api"</span>;

<span class="text-purple-400">const</span> client = <span class="text-purple-400">new</span> <span class="text-blue-400">Nebula</span>({
  <span class="text-white/40">apiKey:</span> process.env.<span class="text-amber-300">NEBULA_KEY</span>,
});</code></pre>
</div>
```

---

## Vertical Container Lines (Decorative)

Add to any section's container for premium detail:

```html
<div class="relative container-lines">
  <!-- Your section content here -->

  <!-- Optional: inner vertical lines at grid columns -->
  <div class="hidden lg:block absolute top-0 bottom-0 left-1/3 w-px bg-white/[0.03]"></div>
  <div class="hidden lg:block absolute top-0 bottom-0 left-2/3 w-px bg-white/[0.03]"></div>
</div>
```
