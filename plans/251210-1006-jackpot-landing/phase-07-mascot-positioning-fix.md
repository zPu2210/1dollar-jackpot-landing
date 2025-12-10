# Phase 07: Mascot Positioning Fix (Visual Feedback Revision)

## Context Links
- [Main Plan](./plan.md)
- [Dependency: Phase 06 Hero Mascot Optimization](./phase-06-hero-mascot-optimization.md)

## Overview

| Field | Value |
|-------|-------|
| **Date** | 2025-12-10 |
| **Description** | Fix mascot positioning based on visual feedback - mascots incorrectly placed inside carousel instead of outside |
| **Priority** | Critical |
| **Status** | Pending |
| **Estimated Lines** | ~4 lines modified |
| **Target File** | `index.html` lines 194, 204 |
| **Type** | Revision/Bugfix |

## Visual Feedback Summary

### Screenshot #1: Desktop (1440px)
- **Red square** = Couple rabbit mascot current position
- **Yellow line** = Bottom edge of video carousel
- **Problem:** Mascot inside carousel, not touching left edge from outside
- **Expected:** Mascot OUTSIDE left edge, touching/overlapping by ~10%, feet on yellow line

### Screenshot #2: Mobile (375px)
- **Red square** = Gold rabbit mascot current position
- **Yellow line** = Top edge of video carousel
- **Problem:** Mascot positioned inside/over video content
- **Expected:** Mascot "sitting" ON yellow line (top edge), ~5% overlap

## Root Cause Analysis

### Desktop Issue (Couple Rabbit)

**Problem:** `-left-[10%]` positions mascot 10% INWARD from container left edge.

**Mental Model Error:** Negative percentage was interpreted as "outside" but actually moves element inward when combined with absolute positioning.

**Correct Approach:**
1. Position at container edge: `left-0`
2. Translate OUTSIDE container: `-translate-x-[90%]`
3. Result: 90% outside, 10% overlapping INTO container

### Mobile Issue (Gold Rabbit)

**Problem:** `-top-6` (24px above) doesn't account for mascot element height.

**Mental Model Error:** Assumed negative top positions entire mascot above, but absolute positioning anchors TOP of element, so mascot body extends DOWNWARD into carousel.

**Correct Approach:**
1. Position top of element above by its own height: `-top-full` (top: -100%)
2. Pull down for sitting effect: `translate-y-[5%]`
3. Result: Bottom of mascot sits ON top edge, 5% overlap

## Current Implementation (Phase 06)

### Mobile Mascot (Line 194)
```html
<div class="absolute -top-6 left-1/2 -translate-x-1/2 w-[40%] max-w-[160px] opacity-90 md:opacity-100 z-20 md:hidden pointer-events-none">
    <picture>
        <source srcset="images/rabbit-gold.webp" type="image/webp">
        <img src="images/rabbit-gold.png" alt="" class="w-full h-auto object-contain drop-shadow-2xl filter brightness-110">
    </picture>
</div>
```

### Desktop Mascot (Line 204)
```html
<div class="absolute bottom-0 -left-[10%] h-[65%] max-h-[400px] z-20 hidden md:block pointer-events-none">
    <picture>
        <source srcset="images/couple-rabbit.webp" type="image/webp">
        <img src="images/couple-rabbit.png" alt="" class="h-full w-auto object-contain drop-shadow-2xl">
    </picture>
</div>
```

## Implementation Steps

### Step 1: Desktop Mascot Positioning Fix

**File:** `index.html` line 204

**Current Classes:**
```
absolute bottom-0 -left-[10%] h-[65%] max-h-[400px] z-20 hidden md:block pointer-events-none
```

**Fixed Classes:**
```
absolute bottom-0 left-0 -translate-x-[90%] h-[65%] max-h-[400px] z-20 hidden md:block pointer-events-none
```

**Changes:**
| Remove | Add | Purpose |
|--------|-----|---------|
| `-left-[10%]` | `left-0` | Align mascot to container left edge |
| - | `-translate-x-[90%]` | Move 90% of mascot width to LEFT (outside container) |

**Transform Calculation:**
```
Container left edge = 0
Mascot at left-0 = left edge of mascot at container left edge
-translate-x-[90%] = move left by 90% of MASCOT width (not container)
Result: 10% of mascot visible inside, 90% outside
```

**Visual Result:**
- Mascot positioned OUTSIDE container on left side
- 10% of mascot width overlaps INTO container (touches edge)
- Feet align with `bottom-0` (yellow line from feedback)

### Step 2: Mobile Mascot Positioning Fix

**File:** `index.html` line 194

**Current Classes:**
```
absolute -top-6 left-1/2 -translate-x-1/2 w-[40%] max-w-[160px] opacity-90 md:opacity-100 z-20 md:hidden pointer-events-none
```

**Fixed Classes:**
```
absolute -top-full left-1/2 -translate-x-1/2 translate-y-[5%] w-[40%] max-w-[160px] opacity-90 md:opacity-100 z-20 md:hidden pointer-events-none
```

**Changes:**
| Remove | Add | Purpose |
|--------|-----|---------|
| `-top-6` | `-top-full` | Position mascot ABOVE container (top: -100%) |
| - | `translate-y-[5%]` | Pull down 5% of mascot height for sitting effect |

**Transform Calculation:**
```
Container top edge = 0
Mascot at -top-full = bottom of mascot aligns with container top (top: -100% of mascot height)
translate-y-[5%] = move down by 5% of MASCOT height
Result: Bottom of mascot sits ON top edge, 5% extends into carousel
```

**Visual Result:**
- Mascot positioned ABOVE carousel
- Bottom of mascot aligns with top of carousel (yellow line)
- 5% overlap creates "sitting on top" effect

## Testing & Validation

### Desktop Tests

| Viewport | Test | Expected Result |
|----------|------|-----------------|
| 1024px | Mascot position | Outside left edge, 10% overlap visible |
| 1440px | Mascot position | Outside left edge, 10% overlap visible |
| 1024px | Feet alignment | Aligned with bottom of carousel |
| 1440px | Feet alignment | Aligned with bottom of carousel |
| 1024px+ | Controls | Carousel buttons not obstructed |
| 1024px+ | Drop shadow | Renders naturally toward right |

### Mobile Tests

| Viewport | Test | Expected Result |
|----------|------|-----------------|
| 375px | Mascot position | Above carousel, sitting on top edge |
| 390px | Mascot position | Above carousel, sitting on top edge |
| 428px | Mascot position | Above carousel, sitting on top edge |
| 375px | Bottom alignment | Mascot bottom ON yellow line (top edge) |
| 375px | Overlap | ~5% of mascot extends into carousel |
| All mobile | Centering | Horizontally centered via translate-x-1/2 |
| All mobile | Opacity | opacity-90 applied correctly |

### Validation Procedure

1. Open Chrome DevTools
2. Toggle device toolbar (Ctrl+Shift+M)
3. Test each viewport size listed above
4. Screenshot before/after comparison
5. Use ruler tool to measure overlap percentages
6. Click test all carousel controls

## Success Criteria

| # | Criterion | Validation Method |
|---|-----------|-------------------|
| 1 | Desktop: Mascot outside left edge, touching | Visual inspection + DevTools |
| 2 | Desktop: 10% overlap into carousel | Measure with DevTools ruler |
| 3 | Desktop: Feet align with bottom (yellow line) | Screenshot comparison |
| 4 | Mobile: Mascot sits ON yellow line (top edge) | Visual inspection |
| 5 | Mobile: 5% overlap (bottom extends in) | Screenshot comparison |
| 6 | Mobile: Centered horizontally | DevTools computed center |
| 7 | No carousel control obstruction | Click test all buttons |
| 8 | Visual balance at all breakpoints | Manual review 5 viewports |
| 9 | Drop shadow renders naturally | Visual inspection |

## Todo List

- [ ] Update desktop mascot classes (line 204)
- [ ] Update mobile mascot classes (line 194)
- [ ] Test desktop at 1024px - verify positioning
- [ ] Test desktop at 1440px - verify positioning
- [ ] Test mobile at 375px - verify positioning
- [ ] Test mobile at 390px - verify positioning
- [ ] Test mobile at 428px - verify positioning
- [ ] Capture before/after screenshots
- [ ] Verify carousel controls work
- [ ] Check drop-shadow rendering

## Risk Assessment

| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| Mascot too far outside | Medium | Low | Adjust translate-x from 90% to 85% |
| Mobile mascot too high | Low | Low | Increase translate-y from 5% to 8% |
| Transform conflicts | Low | Low | Test transform order in DevTools |
| Responsive breakpoints | Medium | Low | Test all target viewports |
| Overflow hidden clips mascot | Medium | Low | Check parent container overflow setting |

## Fallback Values

If initial values don't match visual expectation:

### Desktop Alternatives
```css
/* More visible (20% overlap) */
-translate-x-[80%]

/* Less visible (5% overlap) */
-translate-x-[95%]
```

### Mobile Alternatives
```css
/* Higher position (3% overlap) */
translate-y-[3%]

/* Lower position (8% overlap) */
translate-y-[8%]
```

## Dependencies

- Phase 06 must be implemented (provides base positioning structure)
- Images exist at correct paths:
  - `images/couple-rabbit.webp`
  - `images/couple-rabbit.png`
  - `images/rabbit-gold.webp`
  - `images/rabbit-gold.png`

## Performance Notes

- CSS-only changes (no performance impact)
- No additional HTTP requests
- No JavaScript modifications
- Transform properties are GPU-accelerated

## Overflow Consideration

**Important:** Parent container must NOT have `overflow: hidden` on X-axis for desktop mascot to be visible outside container.

Check parent element for:
```css
/* Bad - will clip mascot */
overflow: hidden;
overflow-x: hidden;

/* Good - allows mascot outside */
overflow: visible;
overflow-x: visible;
```

If overflow is hidden, may need to:
1. Move mascot to parent level (outside video container)
2. Or adjust overflow-x to visible

## Code Changes Summary

### Line 194 (Mobile Mascot)

**Before:**
```html
<div class="absolute -top-6 left-1/2 -translate-x-1/2 w-[40%] max-w-[160px] opacity-90 md:opacity-100 z-20 md:hidden pointer-events-none">
```

**After:**
```html
<div class="absolute -top-full left-1/2 -translate-x-1/2 translate-y-[5%] w-[40%] max-w-[160px] opacity-90 md:opacity-100 z-20 md:hidden pointer-events-none">
```

### Line 204 (Desktop Mascot)

**Before:**
```html
<div class="absolute bottom-0 -left-[10%] h-[65%] max-h-[400px] z-20 hidden md:block pointer-events-none">
```

**After:**
```html
<div class="absolute bottom-0 left-0 -translate-x-[90%] h-[65%] max-h-[400px] z-20 hidden md:block pointer-events-none">
```

## Next Steps

After Phase 07 implementation:
1. Capture screenshots at 375px, 1440px
2. Compare with user feedback screenshots
3. Get user confirmation positioning is correct
4. If adjustments needed, iterate on translate percentages
5. Document final values for future reference

## Lessons Learned

1. **Negative percentage positioning** (e.g., `-left-[10%]`) moves element INWARD relative to parent, not outside
2. **Translate transforms** operate on element's own dimensions, not parent
3. **Absolute positioning top** anchors element's top edge, body extends downward
4. **Use `translate` for outside positioning** - more predictable than negative position values
5. **Visual feedback loops** critical for pixel-perfect decorative positioning
