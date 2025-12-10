# Phase 06: Hero Section Mascot Positioning Optimization

## Context Links
- [Main Plan](./plan.md)
- [Dependency: Phase 02 Hero Section](./phase-02-hero-section.md)

## Overview

| Field | Value |
|-------|-------|
| **Date** | 2025-12-10 |
| **Description** | Optimize mascot positioning for desktop/mobile UX, fix above-fold visibility |
| **Priority** | High |
| **Status** | Pending |
| **Estimated Lines** | ~20 lines modified |
| **Target File** | `index.html` lines 160-271 |

## Key Insights

### Current Implementation Issues

1. **Desktop Mascot (couple-rabbit.png)**
   - Position: `bottom-[-10%] -left-[15%]` - too far left, outside viewport
   - Height: `h-[85%]` - too large, obscures video content
   - Result: Excessive overlap, poor visual balance

2. **Mobile Mascot (rabbit-gold.png)**
   - Position: `-top-12` (48px gap) - creates visual disconnect
   - Width: `w-[60%]` - too large for above-fold view
   - Result: Pushes CTA below fold on iPhone SE (375x667)

3. **Hero Container**
   - `min-h-screen` forces CTA below fold on small mobile devices
   - Content spacing not optimized for mobile viewport constraints

### UX Standards Reference

| Standard | Desktop | Mobile |
|----------|---------|--------|
| Decorative sizing | 15-25% container width | 30-40% viewport width |
| Max dimension | 400px height | 180px width |
| Overlap ratio | 10-15% subtle touch | 5-10% minimal overlap |
| Above-fold | N/A | Must fit 667px height |

## Requirements

### Desktop Requirements (768px+)
- Couple rabbit "lightly touches" video with ~10% overlap
- Position naturally at left edge of video container
- Reduce height to 60-70% (max 400px) for proportion
- Must not obstruct video controls or carousel buttons
- Maintain: `pointer-events-none`, `drop-shadow-2xl`, `z-20`

### Mobile Requirements (<768px)
- Gold rabbit overlaps video by ~5% (20-30px overlap)
- Entire hero (logo, headline, video, CTA) visible in first viewport
- Reduce width to 35-45% for content focus
- Support viewports: 375x667, 390x844, 428x926
- CTA visible without scrolling on iPhone SE

## Architecture

### Current Structure (index.html)
```
<section id="hero" min-h-screen>
  ├── Aurora background (absolute)
  ├── Logo (z-10, mb-2/mb-8)
  ├── Headlines (z-10, mb-4/mb-10)
  ├── Video Container (z-10, mb-6/mb-16)
  │   ├── Mobile Mascot (absolute, -top-12, z-20, md:hidden)
  │   ├── Desktop Mascot (absolute, bottom-[-10%], z-20, hidden md:block)
  │   └── Glass card with iframe
  ├── CTA Button (z-10)
  └── Scroll Indicator (absolute, bottom-8, hidden md:block)
</section>
```

### Target Structure (optimized)
```
<section id="hero" min-h-[auto] md:min-h-screen>
  ├── Aurora background (unchanged)
  ├── Logo (z-10, mb-3/mb-8)
  ├── Headlines (z-10, mb-6/mb-10)
  ├── Video Container (z-10, mb-8/mb-16)
  │   ├── Mobile Mascot (absolute, -top-6, w-[40%], z-20, md:hidden)
  │   ├── Desktop Mascot (absolute, bottom-0, -left-[10%], h-[65%], z-20, hidden md:block)
  │   └── Glass card with iframe
  ├── CTA Button (z-10)
  └── Scroll Indicator (unchanged)
</section>
```

## Related Code Files

| File | Section | Lines |
|------|---------|-------|
| `index.html` | Hero section | 161-271 |
| `index.html` | Mobile mascot | 194-197 |
| `index.html` | Desktop mascot | 199-202 |

## Implementation Steps

### Step 1: Desktop Mascot Positioning

**File:** `index.html` line 200

**Current:**
```html
<div class="absolute bottom-[-10%] -left-[15%] h-[85%] z-20 hidden md:block pointer-events-none">
```

**Target:**
```html
<div class="absolute bottom-0 -left-[10%] h-[65%] max-h-[400px] z-20 hidden md:block pointer-events-none">
```

**Changes:**
- `bottom-[-10%]` -> `bottom-0` (align to container bottom)
- `-left-[15%]` -> `-left-[10%]` (10% overlap into video area)
- `h-[85%]` -> `h-[65%] max-h-[400px]` (proportional height with cap)

### Step 2: Mobile Mascot Positioning

**File:** `index.html` line 194

**Current:**
```html
<div class="absolute -top-12 left-1/2 -translate-x-1/2 w-[60%] z-20 md:hidden pointer-events-none">
```

**Target:**
```html
<div class="absolute -top-6 left-1/2 -translate-x-1/2 w-[40%] max-w-[160px] opacity-90 md:opacity-100 z-20 md:hidden pointer-events-none">
```

**Changes:**
- `-top-12` (48px) -> `-top-6` (24px) - closer overlap (~5% of 400px video)
- `w-[60%]` -> `w-[40%] max-w-[160px]` - smaller, proportional
- Added `opacity-90 md:opacity-100` - reduced opacity on mobile for better content hierarchy

### Step 3: Hero Height Optimization

**File:** `index.html` line 162

**Current:**
```html
<section id="hero" class="relative min-h-screen flex flex-col items-center justify-center px-4 md:px-6 lg:px-8 py-4 md:py-12 overflow-hidden">
```

**Target:**
```html
<section id="hero" class="relative min-h-[auto] md:min-h-screen flex flex-col items-center justify-center px-4 md:px-6 lg:px-8 py-8 md:py-12 overflow-hidden">
```

**Changes:**
- `min-h-screen` -> `min-h-[auto] md:min-h-screen` (natural height on mobile)
- `py-4` -> `py-8` (better mobile vertical rhythm)

### Step 4: Content Spacing Mobile

**File:** `index.html` lines 174, 181, 192

**Logo (line 174):**
```html
<!-- Current --> mb-2 md:mb-8
<!-- Target --> mb-3 md:mb-8
```

**Headlines (line 181):**
```html
<!-- Current --> mb-4 md:mb-10
<!-- Target --> mb-6 md:mb-10
```

**Video container (line 192):**
```html
<!-- Current --> mb-6 md:mb-16
<!-- Target --> mb-8 md:mb-16
```

### Step 5: Testing & Validation

**Chrome DevTools Emulation:**
1. iPhone SE: 375x667 - verify CTA above fold
2. iPhone 12: 390x844 - verify proportions
3. iPhone Pro Max: 428x926 - verify balance
4. iPad: 768x1024 - verify desktop mascot triggers at md breakpoint
5. Desktop: 1024x768, 1440x900 - verify 10% overlap looks natural

**Validation Checklist:**
- [ ] Desktop mascot overlaps video by ~10%
- [ ] Desktop mascot height is proportional (65%, max 400px)
- [ ] Mobile mascot overlaps video by ~5% (24px)
- [ ] Mobile mascot width is controlled (40%, max 160px)
- [ ] Entire hero fits in 667px viewport (iPhone SE)
- [ ] CTA visible without scrolling on all mobile sizes
- [ ] No pointer interference (controls work)
- [ ] No layout shift (CLS < 0.1)

### Step 6: Image Optimization (Required)

**Priority:** High - must complete before production deploy

**Current State:**
- `couple-rabbit.png`: 816KB
- `rabbit-gold.png`: 958KB
- **Total:** 1.7MB (excessive for decorative content)

**Target:**
- `couple-rabbit.webp`: <120KB
- `rabbit-gold.webp`: <130KB
- **Total:** <250KB (85% reduction)

**Tools:**
- Squoosh.app (online, free)
- ImageOptim (Mac)
- TinyPNG (online)

**Process:**

1. **Optimize couple-rabbit.png:**
   - Upload to Squoosh.app
   - Convert to WebP format
   - Quality: 80%
   - Target: <120KB
   - Save as: `characters/couple-rabbit.webp`

2. **Optimize rabbit-gold.png:**
   - Upload to Squoosh.app
   - Convert to WebP format
   - Quality: 80%
   - Target: <130KB
   - Save as: `characters/rabbit-gold.webp`

3. **Update HTML with `<picture>` elements:**

**Desktop Mascot (line ~200):**
```html
<picture>
  <source srcset="characters/couple-rabbit.webp" type="image/webp">
  <img src="characters/couple-rabbit.png" alt="" class="h-full w-auto object-contain drop-shadow-2xl">
</picture>
```

**Mobile Mascot (line ~194):**
```html
<picture>
  <source srcset="characters/rabbit-gold.webp" type="image/webp">
  <img src="characters/rabbit-gold.png" alt="" class="w-full h-auto object-contain drop-shadow-2xl filter brightness-110">
</picture>
```

**Performance Impact:**
| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Image payload | 1.7MB | ~250KB | 85% reduction |
| LCP on 3G | ~5s | ~2s | 2-3s faster |
| Mobile experience | Poor | Good | Significant |

**Browser Support:**
- WebP: Chrome, Firefox, Edge, Safari 14+
- PNG fallback: All browsers via `<picture>` element

## Todo List

- [ ] Modify desktop mascot positioning (line 200)
- [ ] Modify mobile mascot positioning (line 194)
- [ ] Add opacity-90 to mobile mascot for better content hierarchy
- [ ] Update hero section height (line 162)
- [ ] Adjust logo margin (line 174)
- [ ] Adjust headlines margin (line 181)
- [ ] Adjust video container margin (line 192)
- [ ] Optimize couple-rabbit.png -> WebP (<120KB)
- [ ] Optimize rabbit-gold.png -> WebP (<130KB)
- [ ] Update HTML with `<picture>` elements for WebP support
- [ ] Test on Chrome DevTools mobile emulation
- [ ] Verify CTA above-fold on iPhone SE
- [ ] Verify overlap percentages visually
- [ ] Check carousel controls accessibility
- [ ] Verify WebP loads in Chrome/Firefox, PNG fallback in Safari

## Success Criteria

| # | Criterion | Validation Method |
|---|-----------|-------------------|
| 1 | Desktop: Couple rabbit overlaps video by ~10% | Visual inspection at 1024px+ |
| 2 | Desktop: Mascot height proportional (65%, max 400px) | DevTools computed styles |
| 3 | Mobile: Gold rabbit overlaps video by ~5% (20-30px) | DevTools measurement |
| 4 | Mobile: Entire hero fits in 667px viewport | iPhone SE emulation |
| 5 | Mobile: CTA visible without scrolling | iPhone SE emulation |
| 6 | No pointer interference | Click test on carousel controls |
| 7 | Visual balance across breakpoints | Manual review at 5 viewports |
| 8 | CLS < 0.1 | Lighthouse performance audit |
| 9 | Image payload optimized (<300KB total for both mascots) | File size check after WebP conversion |

## Risk Assessment

| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| Layout shift on resize | Medium | Low | Use max-h/max-w constraints |
| Mobile overflow | High | Medium | Test all target viewports |
| Desktop mascot clipped | Low | Low | Adjust -left value if needed |
| CTA still below fold | High | Low | Further reduce min-h or spacing |

## Security Considerations

N/A - cosmetic CSS changes only, no external resources or scripts modified.

## Dependencies

- Phase 02 (Hero Section) must be implemented
- Images must exist:
  - `images/couple-rabbit.png` (desktop mascot)
  - `images/rabbit-gold.png` (mobile mascot)

## Performance Notes

- No additional HTTP requests
- No JavaScript changes
- CSS-only modifications (except `<picture>` element addition)
- Image optimization required: 1.7MB -> ~250KB (85% reduction)
- WebP with PNG fallback ensures broad browser support
- LCP improvement: 2-3 seconds faster on 3G connections

## Next Steps

After completing Phase 06:
1. Capture screenshots at all 5 target viewports
2. Run Lighthouse mobile performance audit
3. Verify on actual iOS device if available
4. Gather user feedback on mascot visibility
5. Consider A/B testing different overlap percentages

## Design Decisions

| Question | Decision | Rationale |
|----------|----------|-----------|
| Mascot opacity on mobile? | YES - reduce to `opacity-90` | Improves content hierarchy, better readability on small screens. Standard practice for decorative elements on mobile. |
| Desktop parallax effect? | NO | Keep simple per KISS principle. Page already has animations (winner notifications, aurora gradients). Parallax requires JS complexity and performance overhead. Can A/B test later if engagement data supports it. |
| Optimize image sizes? | YES - target <150KB each | Current 1.7MB excessive for decorative content. Industry standard is <150KB for decorative assets. Mobile users on 3G/4G will experience significant load time improvements. |
