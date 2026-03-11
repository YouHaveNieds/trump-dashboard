# Fix: Bottom Navigation Button Styling

**File:** `index.html`
**Lines changed:** `.tab-item` CSS rule (~line 735)

## Problem

The Command and History tab buttons had white/light backgrounds because `<button>` elements carry browser-default styles (`background`, `border`, `appearance`) that were never reset. The `.tab-item` rule styled color and layout but never explicitly cleared the defaults, so the browser applied its native button appearance — white background, visible border, platform-specific styling.

## Fix

Added three properties to `.tab-item`:

```css
background: none;
border: none;
appearance: none;
-webkit-appearance: none;
```

## Result

- Buttons are now fully transparent, inheriting the dark glassmorphism `.tab-bar` background (`rgba(18, 18, 18, 0.92)` with `backdrop-filter: blur(20px)`)
- Inactive tabs: muted text (`#888888`), no background
- Active tab: white text + green-blue gradient indicator bar (`#006aff` to `#00ff99`) with glow — unchanged, already correct
- No visual changes to layout, spacing, or any other element
