# $1 Jackpot Web3 Gaming Landing Page

## Overview

| Field | Value |
|-------|-------|
| **Date** | 2025-12-10 |
| **Priority** | High |
| **Status** | Planning |
| **Type** | New Project |
| **Deliverable** | Single `index.html` with Tailwind CDN |

## Project Summary

Web3 gaming landing page for $1 Jackpot Telegram Mini App. Target: crypto users seeking low-stake gaming excitement. Single HTML file, no build process, production-ready.

## Key Product Details

- **Platform:** Telegram Mini App (Web3)
- **USP:** $1 spins, 95% prize pool, $3 daily limit, blockchain transparency
- **CTA Target:** https://t.me/OneJackpotOfficial
- **Asset:** `1$ Jackpot logo.png` (exists in root)

## Design System Summary

### Color Palette (Gaming + Fintech Merge)
```
Primary:     #7C3AED (purple) - brand identity
Secondary:   #F59E0B (amber) - energy/excitement
CTA:         #F43F5E (rose) - action buttons
Background:  #0A0E27 (midnight blue OLED)
Accent:      #A78BFA (light purple)
Gold:        #FBBF24 (winner highlights)
```

### Typography
- **Heading:** Fredoka (playful, energetic)
- **Body:** Nunito (friendly, readable)
- **CDN:** `@import url('https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Nunito:wght@300;400;500;600;700&display=swap');`

### Style Effects
- Glassmorphism: `backdrop-blur-md bg-white/10 border border-white/20`
- Dark OLED base: `bg-[#0A0E27]`
- Aurora gradients: purple-amber complementary

## Phase Overview

| Phase | Name | Priority | Status | Est. Lines |
|-------|------|----------|--------|------------|
| 01 | Design System | High | Pending | ~80 |
| 02 | Hero Section | High | Pending | ~120 |
| 03 | Conversion Sections | High | Pending | ~150 |
| 04 | Trust & Social Proof | Medium | Pending | ~130 |
| 05 | Footer & Polish | Medium | Pending | ~100 |
| 06 | Hero Mascot Optimization | High | Implemented | ~20 |
| 07 | Mascot Positioning Fix | Critical | Pending | ~4 |

## Progress Tracking

- [ ] Phase 01: Design System (HTML head, CSS variables, base styles)
- [ ] Phase 02: Hero Section (headline, YouTube embed, CTA)
- [ ] Phase 03: Conversion Sections (zero-friction, humor feature)
- [ ] Phase 04: Trust & Social Proof (blockchain, winners animation)
- [ ] Phase 05: Footer & Polish (compliance, links, accessibility audit)
- [x] Phase 06: Hero Mascot Optimization (positioning, above-fold visibility)
- [ ] Phase 07: Mascot Positioning Fix (visual feedback revision)

## Technical Stack

| Component | Choice |
|-----------|--------|
| Framework | None (vanilla HTML) |
| CSS | Tailwind CDN v3.x |
| Fonts | Google Fonts CDN |
| Build | None required |
| Responsive | 320px → 1440px+ |

## File Structure (Final)

```
/
├── index.html          # Single deliverable
├── 1$ Jackpot logo.png # Existing asset
└── plans/              # Planning docs
```

## Success Criteria

1. Single HTML file loads in <3s on 3G
2. Responsive across all breakpoints
3. All CTAs link to Telegram
4. YouTube embed loads responsively
5. Winner notification animation works
6. WCAG 2.1 AA accessible
7. No console errors
8. Glassmorphism renders correctly

## Phase Files

- [Phase 01: Design System](./phase-01-design-system.md)
- [Phase 02: Hero Section](./phase-02-hero-section.md)
- [Phase 03: Conversion Sections](./phase-03-conversion-sections.md)
- [Phase 04: Trust & Social Proof](./phase-04-trust-social-proof.md)
- [Phase 05: Footer & Polish](./phase-05-footer-polish.md)
- [Phase 06: Hero Mascot Optimization](./phase-06-hero-mascot-optimization.md)
- [Phase 07: Mascot Positioning Fix](./phase-07-mascot-positioning-fix.md)

## Unresolved Questions

None - all design intelligence provided upfront.
