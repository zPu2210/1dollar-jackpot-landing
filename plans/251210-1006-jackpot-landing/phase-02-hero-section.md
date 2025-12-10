# Phase 02: Hero Section

## Context Links
- [Main Plan](./plan.md)
- [Previous: Design System](./phase-01-design-system.md)
- [Next: Conversion Sections](./phase-03-conversion-sections.md)

## Overview

| Field | Value |
|-------|-------|
| **Date** | 2025-12-10 |
| **Description** | Hero section with logo, headline, YouTube embed, demo placeholder, CTA |
| **Priority** | High |
| **Status** | Pending |
| **Estimated Lines** | ~120 |

## Key Design Intelligence

### Hero Structure
- Logo at top (centered)
- Primary headline: "A Single Dollar Spin Can Change Everything"
- Secondary copy: "The Web3 Game Engineered for Fun..."
- Embedded YouTube video (responsive 16:9)
- Demo video placeholder below
- Primary CTA button → Telegram

### Visual Treatment
- Full viewport height on desktop
- Aurora gradient accent (subtle)
- Glassmorphism card for video container
- Logo with subtle glow effect

### YouTube Embed
- Video ID: `OWKZ3EDD_gw`
- Full URL: `https://www.youtube.com/embed/OWKZ3EDD_gw?si=o7D8fF9enJJP9Q_F`
- Responsive: 16:9 aspect ratio container

## Requirements

1. Logo image with alt text
2. H1 headline with gradient text effect
3. Subheadline paragraph
4. Responsive YouTube iframe embed
5. Demo video placeholder with "Coming Soon" overlay
6. Primary CTA button (Telegram link)
7. Scroll indicator (optional)
8. Mobile-first responsive design

## Architecture

```html
<section id="hero" class="...">
  <!-- Logo -->
  <img src="..." alt="..." />

  <!-- Headlines -->
  <h1>...</h1>
  <p>...</p>

  <!-- YouTube Embed -->
  <div class="video-container">
    <iframe>...</iframe>
  </div>

  <!-- Demo Placeholder -->
  <div class="demo-placeholder">...</div>

  <!-- CTA Button -->
  <a href="..." class="cta-button">...</a>
</section>
```

## Related Code Files

| File | Section | Lines (approx) |
|------|---------|----------------|
| `index.html` | Hero section | 81-200 |

## Implementation Steps

### Step 1: Hero Container
```html
<!-- Hero Section -->
<section id="hero" class="relative min-h-screen flex flex-col items-center justify-center px-4 md:px-6 lg:px-8 py-12 overflow-hidden">
  <!-- Aurora background effect -->
  <div class="absolute inset-0 overflow-hidden pointer-events-none" aria-hidden="true">
    <div class="absolute -top-1/2 -left-1/2 w-full h-full bg-gradient-to-br from-primary/20 via-transparent to-transparent rounded-full blur-3xl"></div>
    <div class="absolute -bottom-1/2 -right-1/2 w-full h-full bg-gradient-to-tl from-secondary/20 via-transparent to-transparent rounded-full blur-3xl"></div>
  </div>
```

### Step 2: Logo
```html
  <!-- Logo -->
  <div class="relative z-10 mb-8">
    <img
      src="1$ Jackpot logo.png"
      alt="$1 Jackpot Logo - Web3 Gaming"
      class="w-32 h-32 md:w-40 md:h-40 object-contain drop-shadow-[0_0_30px_rgba(124,58,237,0.5)]"
      width="160"
      height="160"
    >
  </div>
```

### Step 3: Headlines
```html
  <!-- Headlines -->
  <div class="relative z-10 text-center max-w-4xl mx-auto mb-10">
    <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold font-display mb-6 bg-gradient-to-r from-white via-accent to-gold bg-clip-text text-transparent">
      A Single Dollar Spin Can Change Everything
    </h1>
    <p class="text-lg md:text-xl text-slate-300 max-w-2xl mx-auto leading-relaxed">
      The Web3 Game Engineered for Fun. Play Big with Small Stakes and Control Your Thrill.
    </p>
  </div>
```

### Step 4: YouTube Embed (Responsive)
```html
  <!-- YouTube Video -->
  <div class="relative z-10 w-full max-w-3xl mx-auto mb-8">
    <div class="glass rounded-2xl p-2 md:p-3">
      <div class="relative w-full pt-[56.25%]"> <!-- 16:9 Aspect Ratio -->
        <iframe
          class="absolute inset-0 w-full h-full rounded-xl"
          src="https://www.youtube.com/embed/OWKZ3EDD_gw?si=o7D8fF9enJJP9Q_F"
          title="$1 Jackpot - How It Works"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          referrerpolicy="strict-origin-when-cross-origin"
          allowfullscreen
          loading="lazy"
        ></iframe>
      </div>
    </div>
  </div>
```

### Step 5: Demo Video Placeholder
```html
  <!-- Demo Video Placeholder -->
  <div class="relative z-10 w-full max-w-2xl mx-auto mb-10">
    <div class="glass rounded-2xl p-4 md:p-6">
      <div class="relative w-full pt-[56.25%] bg-dark-card rounded-xl overflow-hidden">
        <!-- Placeholder content -->
        <div class="absolute inset-0 flex flex-col items-center justify-center">
          <svg class="w-16 h-16 text-slate-500 mb-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
          </svg>
          <p class="text-slate-400 text-sm font-medium">Demo Video Coming Soon</p>
        </div>
        <!-- Replace this div with actual video when ready:
        <video class="absolute inset-0 w-full h-full object-cover" controls poster="demo-poster.jpg">
          <source src="demo.mp4" type="video/mp4">
        </video>
        -->
      </div>
    </div>
  </div>
```

### Step 6: Primary CTA Button
```html
  <!-- Primary CTA -->
  <div class="relative z-10">
    <a
      href="https://t.me/OneJackpotOfficial"
      target="_blank"
      rel="noopener noreferrer"
      class="group inline-flex items-center gap-3 bg-cta hover:bg-cta-hover text-white font-semibold text-lg px-8 py-4 rounded-full shadow-lg shadow-cta/30 transition-all duration-300 hover:scale-105 hover:shadow-xl hover:shadow-cta/40"
    >
      <!-- Telegram Icon -->
      <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
        <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
      </svg>
      <span>Play $1 Jackpot Now</span>
      <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24" aria-hidden="true">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
      </svg>
    </a>
  </div>

  <!-- Scroll Indicator (optional) -->
  <div class="absolute bottom-8 left-1/2 -translate-x-1/2 animate-bounce hidden md:block" aria-hidden="true">
    <svg class="w-6 h-6 text-slate-500" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
    </svg>
  </div>
</section>
```

## Todo List

- [ ] Create hero section container with aurora background
- [ ] Add logo with glow effect and proper alt text
- [ ] Implement gradient headline (H1)
- [ ] Add subheadline paragraph
- [ ] Create responsive YouTube embed with 16:9 ratio
- [ ] Add glassmorphism container around video
- [ ] Create demo video placeholder with "Coming Soon"
- [ ] Implement primary CTA button with Telegram icon
- [ ] Add hover animations to CTA
- [ ] Optional: Add scroll indicator
- [ ] Test responsiveness 320px → 1440px

## Success Criteria

1. Hero takes full viewport on desktop
2. Logo displays with purple glow
3. Headline has gradient text effect
4. YouTube video embeds and plays correctly
5. Demo placeholder shows "Coming Soon" state
6. CTA button links to Telegram, has hover animation
7. Layout is responsive across breakpoints
8. All images have alt text

## Risk Assessment

| Risk | Impact | Mitigation |
|------|--------|------------|
| YouTube embed blocked | Medium | Fallback thumbnail with link |
| Large logo file (1.8MB) | High | Compress/optimize before production |
| Gradient text not supported | Low | Falls back to solid color |

## Security Considerations

- External Telegram link opens in new tab with `rel="noopener noreferrer"`
- YouTube iframe has `referrerpolicy="strict-origin-when-cross-origin"`
- No inline scripts with user data

## Next Steps

After completing Phase 02:
1. Test YouTube embed on mobile devices
2. Verify CTA button accessibility (focus states)
3. Check logo loading performance
4. Proceed to [Phase 03: Conversion Sections](./phase-03-conversion-sections.md)
