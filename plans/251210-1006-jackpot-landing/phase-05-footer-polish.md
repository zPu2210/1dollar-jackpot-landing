# Phase 05: Footer & Polish

## Context Links
- [Main Plan](./plan.md)
- [Previous: Trust & Social Proof](./phase-04-trust-social-proof.md)

## Overview

| Field | Value |
|-------|-------|
| **Date** | 2025-12-10 |
| **Description** | Footer section, accessibility audit, performance optimization, final HTML closure |
| **Priority** | Medium |
| **Status** | Pending |
| **Estimated Lines** | ~100 |

## Key Design Intelligence

### Footer Content
- Logo (smaller version)
- Age compliance: "18+ (or 19+ where applicable)"
- Legal links: Terms of Service, Privacy Policy
- Social links: Telegram (primary), Twitter/X (optional)
- Copyright notice

### Polish Tasks
- Accessibility audit (WCAG 2.1 AA)
- Focus states for interactive elements
- Skip to content link
- Performance: lazy loading, image optimization notes
- Final HTML validation

### Visual Treatment
- Subtle glassmorphism or solid dark background
- Muted text colors for legal copy
- Centered layout
- Social icons with hover effects

## Requirements

1. Footer container with logo
2. Age compliance notice (prominent)
3. Legal links (Terms, Privacy)
4. Social media links
5. Copyright notice
6. Skip to main content link (accessibility)
7. Focus visible states for all interactive elements
8. Closing HTML tags
9. Performance notes/comments

## Architecture

```html
<!-- Skip Link (at top of body) -->
<a href="#main-content" class="skip-link">Skip to main content</a>

<!-- Main Content Wrapper -->
<main id="main-content">
  <!-- All sections from Phases 2-4 -->
</main>

<!-- Footer -->
<footer class="...">
  <logo />
  <nav>Legal links</nav>
  <social-links />
  <age-notice />
  <copyright />
</footer>

</body>
</html>
```

## Related Code Files

| File | Section | Lines (approx) |
|------|---------|----------------|
| `index.html` | Skip link (after body open) | 82-85 |
| `index.html` | Main wrapper | 86, end of sec 5 |
| `index.html` | Footer | 531-600 |
| `index.html` | Closing tags | 601-605 |

## Implementation Steps

### Step 1: Add Skip Link (After Body Open Tag)
```html
<body class="bg-dark min-h-screen antialiased">
  <!-- Skip to main content link (Accessibility) -->
  <a
    href="#main-content"
    class="sr-only focus:not-sr-only focus:absolute focus:top-4 focus:left-4 focus:z-50 focus:bg-primary focus:text-white focus:px-4 focus:py-2 focus:rounded-lg focus:outline-none"
  >
    Skip to main content
  </a>

  <!-- Main Content -->
  <main id="main-content">
```

### Step 2: Close Main Tag (After Social Proof Section)
```html
  </main>
  <!-- End Main Content -->
```

### Step 3: Footer Container
```html
<!-- Footer -->
<footer class="relative py-12 md:py-16 px-4 md:px-6 lg:px-8 bg-[#070A1A]">
  <!-- Top border decoration -->
  <div class="absolute top-0 left-0 w-full h-px bg-gradient-to-r from-transparent via-slate-700/50 to-transparent"></div>

  <div class="max-w-6xl mx-auto">
    <!-- Footer Grid -->
    <div class="grid grid-cols-1 md:grid-cols-3 gap-8 md:gap-12 mb-10">
```

### Step 4: Footer Logo & Tagline
```html
      <!-- Column 1: Logo & Tagline -->
      <div class="text-center md:text-left">
        <img
          src="1$ Jackpot logo.png"
          alt="$1 Jackpot Logo"
          class="w-16 h-16 mx-auto md:mx-0 mb-4 object-contain"
          width="64"
          height="64"
          loading="lazy"
        >
        <p class="text-slate-400 text-sm">
          The Web3 Game Engineered for Fun.
          <br>Play Big with Small Stakes.
        </p>
      </div>
```

### Step 5: Legal Links
```html
      <!-- Column 2: Legal Links -->
      <div class="text-center">
        <h4 class="text-white font-semibold font-display mb-4">Legal</h4>
        <nav aria-label="Legal links">
          <ul class="space-y-2">
            <li>
              <a
                href="#terms"
                class="text-slate-400 hover:text-white transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2 focus:ring-offset-dark rounded"
              >
                Terms of Service
              </a>
            </li>
            <li>
              <a
                href="#privacy"
                class="text-slate-400 hover:text-white transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2 focus:ring-offset-dark rounded"
              >
                Privacy Policy
              </a>
            </li>
            <li>
              <a
                href="#responsible"
                class="text-slate-400 hover:text-white transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2 focus:ring-offset-dark rounded"
              >
                Responsible Gaming
              </a>
            </li>
          </ul>
        </nav>
      </div>
```

### Step 6: Social Links & CTA
```html
      <!-- Column 3: Social & CTA -->
      <div class="text-center md:text-right">
        <h4 class="text-white font-semibold font-display mb-4">Connect</h4>
        <div class="flex items-center justify-center md:justify-end gap-4 mb-6">
          <!-- Telegram -->
          <a
            href="https://t.me/OneJackpotOfficial"
            target="_blank"
            rel="noopener noreferrer"
            class="w-10 h-10 bg-slate-800 hover:bg-primary rounded-full flex items-center justify-center transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2 focus:ring-offset-dark"
            aria-label="Join us on Telegram"
          >
            <svg class="w-5 h-5 text-white" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
              <path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/>
            </svg>
          </a>

          <!-- Twitter/X (Optional - uncomment if needed)
          <a
            href="https://twitter.com/1DollarJackpot"
            target="_blank"
            rel="noopener noreferrer"
            class="w-10 h-10 bg-slate-800 hover:bg-slate-700 rounded-full flex items-center justify-center transition-colors focus:outline-none focus:ring-2 focus:ring-primary focus:ring-offset-2 focus:ring-offset-dark"
            aria-label="Follow us on X (Twitter)"
          >
            <svg class="w-5 h-5 text-white" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
              <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
            </svg>
          </a>
          -->
        </div>

        <!-- Mini CTA -->
        <a
          href="https://t.me/OneJackpotOfficial"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-2 text-cta hover:text-white font-semibold transition-colors focus:outline-none focus:underline"
        >
          <span>Play Now</span>
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 6H6a2 2 0 00-2 2v10a2 2 0 002 2h10a2 2 0 002-2v-4M14 4h6m0 0v6m0-6L10 14" />
          </svg>
        </a>
      </div>
    </div>
```

### Step 7: Age Compliance & Copyright
```html
    <!-- Age Compliance Notice -->
    <div class="border-t border-slate-800 pt-8 mb-6">
      <div class="glass rounded-xl px-6 py-4 text-center max-w-2xl mx-auto">
        <p class="text-amber-400 font-semibold text-sm mb-2">
          <svg class="w-5 h-5 inline-block mr-1 -mt-0.5" fill="none" stroke="currentColor" viewBox="0 0 24 24" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z" />
          </svg>
          18+ Only (19+ where applicable)
        </p>
        <p class="text-slate-500 text-xs">
          Gambling can be addictive. Please play responsibly.
          If you need help, visit <a href="https://www.begambleaware.org" target="_blank" rel="noopener noreferrer" class="underline hover:text-slate-300">BeGambleAware.org</a>
        </p>
      </div>
    </div>

    <!-- Copyright -->
    <div class="text-center">
      <p class="text-slate-600 text-sm">
        &copy; 2024 $1 Jackpot. All rights reserved.
      </p>
    </div>
  </div>
</footer>
```

### Step 8: Closing Tags
```html
</body>
</html>
```

### Step 9: Add Focus Styles to Head (Phase 01 Addition)
```css
/* Add to <style> in head */
/* Focus visible styles for accessibility */
:focus-visible {
  outline: 2px solid #7C3AED;
  outline-offset: 2px;
}

/* Screen reader only utility */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

## Accessibility Checklist

- [ ] Skip to main content link present and functional
- [ ] All images have alt text
- [ ] All links have descriptive text or aria-label
- [ ] Color contrast meets WCAG AA (checked)
- [ ] Focus states visible on all interactive elements
- [ ] aria-hidden on decorative elements
- [ ] aria-live on winner notification container
- [ ] Landmark elements used (main, footer, nav)
- [ ] Reduced motion respected for animations
- [ ] Form elements labeled (N/A - no forms)

## Performance Checklist

- [ ] Logo image optimized (note: 1.8MB is too large)
- [ ] YouTube iframe has loading="lazy"
- [ ] Footer logo has loading="lazy"
- [ ] Google Fonts has preconnect hints
- [ ] CSS animations use transform/opacity (GPU accelerated)
- [ ] JavaScript is minimal and at end of body
- [ ] No blocking resources

## Performance Notes (Add as HTML Comment)
```html
<!--
  PERFORMANCE OPTIMIZATION NOTES:

  Before deploying to production:
  1. Optimize logo image (1.8MB -> ~100KB)
     - Use TinyPNG or Squoosh
     - Consider WebP with PNG fallback
     - Add srcset for responsive images

  2. Consider self-hosting fonts
     - Download Google Fonts
     - Use font-display: swap

  3. Add meta tags for social:
     - Update og:image with full URL
     - Add og:image:width and og:image:height

  4. Add favicon
     - favicon.ico
     - apple-touch-icon.png
     - manifest.json for PWA (optional)
-->
```

## Todo List

- [ ] Add skip to main content link after body tag
- [ ] Wrap all sections in main element
- [ ] Create footer container
- [ ] Add footer logo with lazy loading
- [ ] Create legal links navigation
- [ ] Add social links (Telegram icon)
- [ ] Create age compliance notice (prominent)
- [ ] Add responsible gambling link
- [ ] Add copyright notice
- [ ] Close all HTML tags properly
- [ ] Add focus-visible CSS to head
- [ ] Add screen reader utility class
- [ ] Run accessibility checklist
- [ ] Add performance notes comment

## Success Criteria

1. Skip link works (visible on focus, jumps to main)
2. Footer displays with all required elements
3. Age compliance notice is prominent
4. All links have visible focus states
5. Social icons have aria-labels
6. Copyright displays correctly
7. HTML validates (no errors)
8. Page loads without console errors

## Risk Assessment

| Risk | Impact | Mitigation |
|------|--------|------------|
| Legal links point to #hash | Low | Placeholder - update with real URLs |
| Logo not optimized | Medium | Add comment note for production |
| Missing favicon | Low | Add as enhancement |

## Security Considerations

- External responsible gambling link uses `rel="noopener noreferrer"`
- No user data collection
- Legal page links are placeholders (update before launch)
- Copyright year should be dynamic in production

## Final File Structure

After all phases complete:
```
/Users/pu/Documents/Playground/1dollarlandingpage/
├── index.html          # ~600 lines, production-ready
├── 1$ Jackpot logo.png # (optimize before deploy)
└── plans/
    └── 251210-1006-jackpot-landing/
        ├── plan.md
        ├── phase-01-design-system.md
        ├── phase-02-hero-section.md
        ├── phase-03-conversion-sections.md
        ├── phase-04-trust-social-proof.md
        └── phase-05-footer-polish.md
```

## Next Steps (Post-Implementation)

1. Test in multiple browsers (Chrome, Firefox, Safari, Edge)
2. Test on real mobile devices
3. Run Lighthouse audit (target: 90+ all categories)
4. Validate HTML at validator.w3.org
5. Test with screen reader (VoiceOver/NVDA)
6. Optimize logo image before deployment
7. Update legal links with real URLs
8. Add favicon and social images
9. Deploy to hosting (Vercel, Netlify, etc.)
