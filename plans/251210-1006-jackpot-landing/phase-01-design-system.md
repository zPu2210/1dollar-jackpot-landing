# Phase 01: Design System

## Context Links
- [Main Plan](./plan.md)
- [Next Phase: Hero Section](./phase-02-hero-section.md)

## Overview

| Field | Value |
|-------|-------|
| **Date** | 2025-12-10 |
| **Description** | HTML head, CSS custom properties, base styles, Tailwind config |
| **Priority** | High |
| **Status** | Pending |
| **Estimated Lines** | ~80 |

## Key Design Intelligence

### Color System (Gaming + Fintech Merge)
| Token | Hex | Usage |
|-------|-----|-------|
| `--color-primary` | #7C3AED | Brand purple, headings |
| `--color-secondary` | #F59E0B | Amber accents, energy |
| `--color-cta` | #F43F5E | Rose, action buttons |
| `--color-cta-hover` | #E11D48 | Darker rose on hover |
| `--color-bg` | #0A0E27 | OLED midnight base |
| `--color-bg-card` | #0F172A | Card backgrounds |
| `--color-accent` | #A78BFA | Light purple highlights |
| `--color-gold` | #FBBF24 | Winner highlights |
| `--color-text` | #F8FAFC | Primary text |
| `--color-text-muted` | #94A3B8 | Secondary text |

### Typography
- Fredoka: Display/headings (wght 400-700)
- Nunito: Body text (wght 300-700)

### Glassmorphism Recipe
```css
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 16px;
}
```

Tailwind equivalent: `bg-white/10 backdrop-blur-md border border-white/20 rounded-2xl`

## Requirements

1. HTML5 doctype with lang="en"
2. Meta tags: viewport, description, charset
3. Open Graph tags for social sharing
4. Google Fonts import (Fredoka + Nunito)
5. Tailwind CDN script
6. CSS custom properties for colors
7. Base body styles (dark bg, default font)
8. Utility classes for glassmorphism
9. Animation keyframes for winner notification
10. Prefers-reduced-motion respect

## Architecture

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <!-- Meta tags -->
  <!-- Open Graph -->
  <!-- Google Fonts -->
  <!-- Tailwind CDN -->
  <style>
    /* Custom properties */
    /* Base styles */
    /* Animation keyframes */
    /* Utility classes */
  </style>
</head>
<body class="...">
  <!-- Content from subsequent phases -->
</body>
</html>
```

## Related Code Files

| File | Section | Lines |
|------|---------|-------|
| `index.html` | `<head>` | 1-80 |

## Implementation Steps

### Step 1: HTML Skeleton (Lines 1-10)
```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="$1 Jackpot - Web3 gaming with $1 spins, 95% prize pool, blockchain transparency. Play big with small stakes.">
  <title>$1 Jackpot | Web3 Gaming - Spin to Win</title>
```

### Step 2: Open Graph Tags (Lines 11-20)
```html
  <!-- Open Graph -->
  <meta property="og:title" content="$1 Jackpot | Web3 Gaming">
  <meta property="og:description" content="The Web3 Game Engineered for Fun. $1 spins, 95% prize pool, blockchain transparency.">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://t.me/OneJackpotOfficial">
  <meta property="og:image" content="1$ Jackpot logo.png">

  <!-- Twitter Card -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="$1 Jackpot | Web3 Gaming">
```

### Step 3: External Resources (Lines 21-30)
```html
  <!-- Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Nunito:wght@300;400;500;600;700&display=swap" rel="stylesheet">

  <!-- Tailwind CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
```

### Step 4: Tailwind Config (Lines 31-50)
```html
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: '#7C3AED',
            secondary: '#F59E0B',
            cta: '#F43F5E',
            'cta-hover': '#E11D48',
            dark: '#0A0E27',
            'dark-card': '#0F172A',
            accent: '#A78BFA',
            gold: '#FBBF24',
          },
          fontFamily: {
            display: ['Fredoka', 'sans-serif'],
            body: ['Nunito', 'sans-serif'],
          },
        },
      },
    }
  </script>
```

### Step 5: Custom Styles (Lines 51-80)
```html
  <style>
    /* Base styles */
    body {
      font-family: 'Nunito', sans-serif;
      background-color: #0A0E27;
      color: #F8FAFC;
    }

    h1, h2, h3, h4, h5, h6 {
      font-family: 'Fredoka', sans-serif;
    }

    /* Glassmorphism utility */
    .glass {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
      border: 1px solid rgba(255, 255, 255, 0.2);
    }

    /* Winner notification animation */
    @keyframes slideIn {
      from { transform: translateX(100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }

    @keyframes slideOut {
      from { transform: translateX(0); opacity: 1; }
      to { transform: translateX(100%); opacity: 0; }
    }

    .winner-notification {
      animation: slideIn 0.5s ease-out, slideOut 0.5s ease-in 4.5s forwards;
    }

    /* Aurora gradient */
    .aurora-gradient {
      background: linear-gradient(135deg, #7C3AED 0%, #F59E0B 50%, #F43F5E 100%);
    }

    /* Reduced motion */
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: 0.01ms !important;
        animation-iteration-count: 1 !important;
        transition-duration: 0.01ms !important;
      }
    }
  </style>
</head>
```

### Step 6: Body Opening
```html
<body class="bg-dark min-h-screen antialiased">
```

## Todo List

- [ ] Create HTML5 skeleton with lang attribute
- [ ] Add meta tags (viewport, description, charset)
- [ ] Add Open Graph and Twitter Card tags
- [ ] Import Google Fonts with preconnect
- [ ] Add Tailwind CDN script
- [ ] Configure Tailwind with custom colors and fonts
- [ ] Write base CSS styles
- [ ] Create glassmorphism utility class
- [ ] Add animation keyframes for winner notification
- [ ] Add aurora gradient utility
- [ ] Implement prefers-reduced-motion

## Success Criteria

1. Page loads with correct fonts (Fredoka headings, Nunito body)
2. Custom Tailwind colors available (e.g., `bg-primary`, `text-cta`)
3. `.glass` class renders glassmorphism effect
4. Background is OLED dark (#0A0E27)
5. No FOUC (flash of unstyled content)
6. Animations disabled when prefers-reduced-motion is set

## Risk Assessment

| Risk | Impact | Mitigation |
|------|--------|------------|
| Tailwind CDN fails | High | Fallback inline styles (not implemented for MVP) |
| Font loading slow | Medium | preconnect hints, font-display: swap (default) |
| Backdrop-filter unsupported | Low | Graceful degradation (solid bg fallback) |

## Security Considerations

- External CDNs (Google Fonts, Tailwind) - trusted sources
- No user input handling in this phase
- CSP headers recommended for production (server config)

## Next Steps

After completing Phase 01:
1. Verify design system renders correctly in browser
2. Test responsive behavior of base styles
3. Proceed to [Phase 02: Hero Section](./phase-02-hero-section.md)
