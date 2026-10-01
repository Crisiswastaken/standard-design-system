# Design System

Quiet, monochromatic UI language. Hierarchy comes from type, spacing, and contrast — never from accent color.

- **Visual reference:** `index.html` (same folder). Open it in a browser. It loads fonts from `../fonts/sf-pro` and has every icon built in.
- **Font:** SF Pro (variable) with SF Pro Text / Display / Rounded static files — `../fonts/sf-pro`
- **Icons:** Nucleo Micro Bold Essential, 180 icons — `../icons/nucleo/micro-bold`
- **Theme:** light only. No dark tokens are defined.
- **Source:** consolidated from the Paper exports `foundations.tsx`, `components.tsx`, `patterns-1.tsx`, `patterns-2.tsx`

---

## 1. Principles

1. **Monochrome only.** Seven grays. No accent color in UI chrome. Emphasis is a darker gray or a heavier weight.
2. **Every value is a token.** Color, size, space, radius — nothing hard-coded.
3. **40px is the control constant.** Buttons, inputs, nav items and icon buttons share one height.
4. **Borders, not shadows.** Surfaces separate with a 1px `#F2F2F2` line. No drop shadows by default.
5. **Two weights in UI.** Regular 400 for reading, Medium 500 for emphasis, labels and buttons.
6. **Pills are reserved.** Full radius only for buttons, badges and toggles.

---

## 2. Tokens (CSS)

Paste into the global stylesheet. `index.html` uses exactly this block.

```css
:root {
  /* Color — primitives */
  --gray-0:   #FFFFFF;
  --gray-25:  #FAFAFA;
  --gray-50:  #F5F5F5;
  --gray-75:  #F2F2F2;
  --gray-500: #7F7F7F;
  --gray-700: #5D5D5D;
  --gray-900: #292929;

  /* Color — semantic */
  --color-background:          var(--gray-0);
  --color-surface:             var(--gray-0);
  --color-surface-subtle:      var(--gray-25);
  --color-background-selected: var(--gray-50);
  --color-border:              var(--gray-75);
  --color-divider:             var(--gray-75);
  --color-text-subtle:         var(--gray-500);
  --color-text-default:        var(--gray-700);
  --color-text-strong:         var(--gray-900);
  --color-icon:                var(--gray-700);
  --color-icon-strong:         var(--gray-900);
  --color-inverse:             var(--gray-900);
  --color-on-inverse:          var(--gray-0);

  /* Typography */
  --font-sans:    "SF Pro", "SF Pro Text", -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
  --font-display: "SF Pro", "SF Pro Display", -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
  --font-rounded: "SF Pro Rounded", ui-rounded, -apple-system, system-ui, sans-serif;
  --font-mono:    ui-monospace, "SF Mono", Menlo, Consolas, monospace;
  --weight-ultralight: 100;
  --weight-thin:       200;
  --weight-light:      300;
  --weight-regular:    400;  /* product UI */
  --weight-medium:     500;  /* product UI */
  --weight-semibold:   600;
  --weight-bold:       700;
  --weight-heavy:      800;
  --weight-black:      900;
  --text-xs:   12px;  --leading-xs:   16px;
  --text-sm:   13px;  --leading-sm:   18px;
  --text-md:   14px;  --leading-md:   20px;
  --text-base: 16px;  --leading-base: 24px;
  --text-lg:   18px;  --leading-lg:   24px;
  --text-xl:   24px;  --leading-xl:   32px;
  --tracking-tight:   -0.02em;  /* 24px headings   */
  --tracking-default: -0.01em;  /* default         */
  --tracking-normal:   0em;     /* 12px UI / labels */

  /* Spacing — 4px base */
  --space-1: 4px;  --space-2: 8px;   --space-3: 12px;  --space-4: 16px;
  --space-5: 20px; --space-6: 24px;  --space-8: 32px;  --space-10: 40px;
  --space-12: 48px; --space-16: 64px;

  /* Radius */
  --radius-sm: 4px;     /* tiny chips  */
  --radius-md: 8px;     /* inputs      */
  --radius-lg: 12px;    /* nav items, icon buttons */
  --radius-xl: 16px;    /* cards       */
  --radius-2xl: 24px;   /* shells      */
  --radius-full: 9999px;/* pills only  */

  /* Border & elevation */
  --border-width: 1px;
  --shadow-none: none;

  /* Sizing */
  --size-control: 40px;
  --size-topbar: 76px;
  --size-sidebar: 256px;
  --size-content-max: 1200px;
  --icon-xs: 14px; --icon-sm: 16px; --icon-md: 18px; --icon-lg: 20px;

  /* Breakpoints (reference — use in media queries) */
  --bp-sm: 640px; --bp-md: 768px; --bp-lg: 1024px; --bp-xl: 1280px; --bp-2xl: 1536px;

  color-scheme: light;
}
```

### Tailwind v4 (`@theme`)

The Paper exports use Tailwind class names (`text-text-subtle`, `bg-background-selected`, `tracking-default`, `text-xs/xs`, `font-regular`, `w-sidebar`). This theme makes those classes resolve:

```css
@import "tailwindcss";

@theme {
  --font-sans: "SF Pro", "SF Pro Text", -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
  --font-display: "SF Pro", "SF Pro Display", -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
  --font-rounded: "SF Pro Rounded", ui-rounded, -apple-system, system-ui, sans-serif;

  --font-weight-ultralight: 100;
  --font-weight-thin: 200;
  --font-weight-light: 300;
  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
  --font-weight-heavy: 800;
  --font-weight-black: 900;

  --color-background: #FFFFFF;
  --color-surface: #FFFFFF;
  --color-surface-subtle: #FAFAFA;
  --color-background-selected: #F5F5F5;
  --color-border: #F2F2F2;
  --color-divider: #F2F2F2;
  --color-text-subtle: #7F7F7F;
  --color-text-default: #5D5D5D;
  --color-text-strong: #292929;
  --color-icon: #5D5D5D;
  --color-icon-strong: #292929;
  --color-inverse: #292929;
  --color-on-inverse: #FFFFFF;

  --text-xs: 12px;   --text-xs--line-height: 16px;
  --text-sm: 13px;   --text-sm--line-height: 18px;
  --text-md: 14px;   --text-md--line-height: 20px;
  --text-base: 16px; --text-base--line-height: 24px;
  --text-lg: 18px;   --text-lg--line-height: 24px;
  --text-xl: 24px;   --text-xl--line-height: 32px;
  --leading-xs: 16px; --leading-sm: 18px; --leading-md: 20px;
  --leading-base: 24px; --leading-xl: 32px;

  --tracking-tight: -0.02em;
  --tracking-default: -0.01em;
  --tracking-normal: 0em;

  --radius-sm: 4px; --radius-md: 8px; --radius-lg: 12px;
  --radius-xl: 16px; --radius-2xl: 24px;

  --spacing: 4px;
  --container-sidebar: 256px;
}
```

### Base body styles

```css
body {
  background: var(--color-background);
  color: var(--color-text-default);
  font-family: var(--font-sans);
  font-size: var(--text-sm);
  line-height: var(--leading-sm);
  letter-spacing: var(--tracking-default);
  font-synthesis: none;
  font-optical-sizing: auto;
  -webkit-font-smoothing: antialiased;
}
```

---

## 3. Color

| Token | Value | Use | Contrast on white |
|---|---|---|---|
| `--color-background` | #FFFFFF | Page canvas | — |
| `--color-surface` | #FFFFFF | Cards, inputs, top bar, sidebar | — |
| `--color-surface-subtle` | #FAFAFA | Quiet wells, nav hover | — |
| `--color-background-selected` | #F5F5F5 | Selected nav item, selected badge, toggle off | — |
| `--color-border` / `--color-divider` | #F2F2F2 | All 1px lines | 1.1 : 1 |
| `--color-text-subtle` | #7F7F7F | Metadata, overlines, placeholders | 4.0 : 1 |
| `--color-text-default` / `--color-icon` | #5D5D5D | Body text, default icons | 6.6 : 1 |
| `--color-text-strong` / `--color-icon-strong` / `--color-inverse` | #292929 | Headings, selected states, primary button fill | 14.5 : 1 |
| `--color-on-inverse` | #FFFFFF | Text and icons on inverse | 14.5 : 1 on #292929 |

**Accessibility.** `text-subtle` (#7F7F7F) is 4.0 : 1. That's fine for 18px+ text but below WCAG AA (4.5 : 1) for 12–13px, so keep it for non-essential metadata. Borders (#F2F2F2) don't reach 3 : 1 non-text contrast, so inputs rely on placeholder text and the focus border to read as fields.

---

## 4. Typography

**SF Pro · Regular 400 / Medium 500.** Tracking −0.01em default, −0.02em on 24px headings, 0em on 12px UI.

### Families

All files are in `../fonts/sf-pro` (47 files).

| Family | Files | Range | Token |
|---|---|---|---|
| **SF Pro** (variable, primary) | `SF-Pro.ttf`, `SF-Pro-Italic.ttf` | weight 1–1000, optical size 17–28 | `--font-sans`, `--font-display` |
| SF Pro Text | `SF-Pro-Text-*.otf` | 9 weights + italics | fallback in `--font-sans` |
| SF Pro Display | `SF-Pro-Display-*.otf` | 9 weights + italics | fallback in `--font-display` |
| SF Pro Rounded | `SF-Pro-Rounded-*.otf` | 9 weights, no italics | `--font-rounded` |

- **How Text vs Display works.** Apple's rule is SF Pro Text below 20px and SF Pro Display at 20px and up. The variable `SF Pro` does this by itself: with `font-optical-sizing: auto`, the browser sets the optical size from the font size. The 12–18px steps get the Text cut and 24px gets close to Display. The static Text / Display files are only fallbacks, which is why `.t-xl` uses `--font-display`.
- **Rounded** is available as `--font-rounded`. The Paper source doesn't use it anywhere.

### Weights

| Token | Value | Static file name |
|---|---|---|
| `--weight-ultralight` | 100 | Ultralight |
| `--weight-thin` | 200 | Thin |
| `--weight-light` | 300 | Light |
| `--weight-regular` | 400 | Regular — **UI** |
| `--weight-medium` | 500 | Medium — **UI** |
| `--weight-semibold` | 600 | Semibold |
| `--weight-bold` | 700 | Bold |
| `--weight-heavy` | 800 | Heavy |
| `--weight-black` | 900 | Black |

Product UI uses only 400 and 500. The other weights are there if you need them.

### Scale

| Step | Size / line | Tracking | Typical weight | Use |
|---|---|---|---|---|
| `xs` | 12 / 16 | 0em | Regular · Medium for overlines | Metadata, captions, secondary UI, badges |
| `sm` | 13 / 18 | −0.01em | Regular | Default UI text, inputs, descriptions |
| `md` | 14 / 20 | −0.01em | Regular · Medium when selected | Navigation, settings labels, card titles |
| `base` | 16 / 24 | −0.01em | Medium | Larger body, buttons |
| `lg` | 18 / 24 | −0.01em | Medium | Section-level text |
| `xl` | 24 / 32 | −0.02em | Medium | Page headings, empty-state titles |

- **Overline / section label:** `xs`, Medium, `text-subtle`, uppercase, 0em tracking.
- 24px is the largest size in the source spec.

### Font faces

Paths are relative to a stylesheet in `design-system/`. Change `../fonts/sf-pro/` to wherever the files live.

```css
@font-face { font-family: "SF Pro"; font-weight: 1 1000; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro.ttf") format("truetype"); }
@font-face { font-family: "SF Pro"; font-weight: 1 1000; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Italic.ttf") format("truetype"); }
```

<details>
<summary>Static faces (SF Pro Text, Display, Rounded — 45 rules)</summary>

```css
@font-face { font-family: "SF Pro Text"; font-weight: 100; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Ultralight.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 100; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-UltralightItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 200; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Thin.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 200; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-ThinItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 300; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Light.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 300; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-LightItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 400; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Regular.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 400; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-RegularItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 500; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Medium.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 500; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-MediumItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 600; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Semibold.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 600; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-SemiboldItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 700; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Bold.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 700; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-BoldItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 800; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Heavy.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 800; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-HeavyItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 900; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-Black.otf") format("opentype"); }
@font-face { font-family: "SF Pro Text"; font-weight: 900; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Text-BlackItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 100; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Ultralight.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 100; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-UltralightItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 200; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Thin.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 200; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-ThinItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 300; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Light.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 300; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-LightItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 400; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Regular.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 400; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-RegularItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 500; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Medium.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 500; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-MediumItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 600; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Semibold.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 600; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-SemiboldItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 700; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Bold.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 700; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-BoldItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 800; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Heavy.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 800; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-HeavyItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 900; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-Black.otf") format("opentype"); }
@font-face { font-family: "SF Pro Display"; font-weight: 900; font-style: italic; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Display-BlackItalic.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 100; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Ultralight.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 200; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Thin.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 300; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Light.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 400; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Regular.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 500; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Medium.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 600; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Semibold.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 700; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Bold.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 800; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Heavy.otf") format("opentype"); }
@font-face { font-family: "SF Pro Rounded"; font-weight: 900; font-style: normal; font-display: swap; src: url("../fonts/sf-pro/SF-Pro-Rounded-Black.otf") format("opentype"); }
```

</details>

Browsers only download the faces a page actually uses. A page set in the variable `SF Pro` loads one 6 MB file. The files aren't subset, so consider subsetting or converting to WOFF2 before production.

---

## 5. Spacing

4px base. Prefer **4 / 8 / 12 / 16 / 24 / 32**.

| Token | 1 | 2 | 3 | 4 | 5 | 6 | 8 | 10 | 12 | 16 |
|---|---|---|---|---|---|---|---|---|---|---|
| px | 4 | 8 | 12 | 16 | 20 | 24 | 32 | 40 | 48 | 64 |

Common uses: icon↔label 8 (buttons, tabs) or 12 (sidebar nav) · card padding 24 · section gap 48 · empty-state padding 64.

---

## 6. Radius

| Token | Value | Use |
|---|---|---|
| `sm` | 4px | Tiny chips |
| `md` | 8px | Inputs |
| `lg` | 12px | Nav items, icon buttons |
| `xl` | 16px | Cards, settings sections |
| `2xl` | 24px | App shells |
| `full` | 9999px | Pills only — buttons, badges, toggles |

---

## 7. Borders, elevation, layout

- **Borders:** 1px · `#F2F2F2`. Use `--color-border` for outlines and `--color-divider` for separators. **No shadows by default.**
- **Breakpoints:** sm 640 · md 768 · lg 1024 · xl 1280 · 2xl 1536.
- **Layout rules:** sidebar collapses below 768. Full desktop layout from 1024. Content max width 1200.

| Size token | Value | Use |
|---|---|---|
| `--size-control` | 40px | Button, input, nav item, icon button height |
| `--size-topbar` | 76px | App top bar height |
| `--size-sidebar` | 256px | App sidebar width |
| `--size-content-max` | 1200px | Max page content width |

---

## 8. Iconography

**Nucleo Micro Bold Essential** — 180 icons in `icons/nucleo/micro-bold/*.svg`.

- 20×20 grid, 2px round stroke, `currentColor`.
- Render sizes: **14** inline/dense · **16** default UI (buttons, nav, inputs, cards) · **18** top bar · **20** native · **40** empty states.
- Color: `--color-icon` by default, `--color-icon-strong` for selected/active, `--color-on-inverse` on dark fills.
- Use a `-filled` variant only when the state calls for it (selected, saved, active). Otherwise use outlines.

The SVGs use `currentColor`, so inline them (or use a sprite) to color them with CSS. An `<img>` tag can't inherit color.

```html
<!-- inline -->
<svg class="icon" width="16" height="16" viewBox="0 0 20 20" aria-hidden="true">…contents of check.svg…</svg>

<!-- sprite (how index.html does it) -->
<svg class="icon" width="16" height="16" aria-hidden="true"><use href="#i-check"/></svg>
```

```css
.icon { flex-shrink: 0; display: block; color: var(--color-icon); }
.icon-strong { color: var(--color-icon-strong); }
```

Icon-only controls need an `aria-label` on the button. Decorative icons get `aria-hidden="true"`.

**Coverage gap.** The free set has no search, plus, minus, close, ellipsis or chevron left/right/down. If you need them, take them from the full Nucleo library so the stroke and grid match.

### Full set (180)

`accessibility`, `alert-info`, `alert-question`, `alert-warning`, `anchor`, `app-stack`, `archive`, `archive-download`, `archive-export`, `arrow-door-in`, `arrow-door-out`, `arrow-down`, `arrow-down-left`, `arrow-down-right`, `arrow-left`, `arrow-right`, `arrow-rotate-anticlockwise`, `arrows-bold-opposite-direction`, `arrows-cross`, `arrows-expand-diagonal7`, `arrows-reduce-diagonal`, `arrow-trend-down`, `arrow-trend-up`, `arrow-up`, `arrow-up-left`, `arrow-up-right`, `at-sign`, `badge-check`, `bars-filter`, `basement`, `bed`, `bolt`, `bolt-filled`, `bookmark`, `bookmark-filled`, `box-archive`, `box-archive-download`, `brightness-increase`, `button`, `caret-expand-y`, `caret-up-right-down-left`, `chat-bot`, `check`, `check2`, `checkbox-checked`, `checkbox-checked-filled`, `checkbox-unchecked`, `chevron-expand-y`, `circle-check-plus`, `circle-half-dotted-check`, `circle-info`, `circle-question`, `circle-user-filled`, `circle-warning`, `clipboard`, `clock-rotate-clockwise`, `clone`, `clone-filled`, `cloud-refresh`, `compose2`, `desk-lamp`, `download`, `download4`, `envelope`, `envelope-filled`, `envelope-open-heart`, `expand`, `expand2`, `eye`, `eye-filled`, `face-expression`, `face-plus`, `face-search`, `feather`, `feather-filled`, `file`, `file-clip`, `file-clock`, `file-download`, `files`, `file-search`, `finder`, `folder`, `folder-open`, `folder-tree`, `forklift`, `full-screen4`, `gauge2`, `gear4`, `ghost-enraged`, `grid2`, `grid-check`, `grid-circle-plus`, `grid-filled`, `grid-layout`, `grid-plus`, `hammer2`, `hand2`, `hand-holding-heart`, `heart`, `heart-filled`, `hexagon-check`, `history`, `house2`, `house2-fill`, `house6`, `house6-fill`, `id-badge`, `label`, `label-filled`, `label-plus`, `language`, `laptop-video`, `layers2`, `layers2-filled`, `list-checkbox`, `mailbox`, `msg`, `msg-bubble-user`, `msg-filled`, `msg-smile2`, `office3`, `ordered-list`, `page`, `paperclip`, `paper-plane2`, `party`, `pen-nib2`, `pen-sparkle`, `pen-writing`, `pen-writing-filled`, `person-walking`, `person-wheelchair`, `photo`, `photo-filled`, `print`, `progress-bar`, `radio-checked`, `radio-unchecked`, `rect-layout-grid3-filled`, `refresh`, `refresh-anticlockwise`, `repeat2`, `rotate-obj-anticlockwise`, `rotate-obj-clockwise`, `saved-items`, `side-profile-heart`, `signature`, `skull`, `slider`, `sort-bottom-to-middle`, `sort-bottom-to-top2`, `sort-middle-to-top`, `sort-obj-bottom-to-top`, `square-kanban`, `square-layout-grid`, `square-layout-grid3`, `stack-filled`, `stack-perspective2`, `star`, `star-lock`, `storage`, `swap`, `tabs-minus`, `tabs-plus`, `thumbs-up`, `timeline-vertical2`, `toggle3`, `trash`, `trash-filled`, `triangle-warning`, `triangle-warning-filled`, `upload`, `user`, `user-filled`, `users`, `users-filled`, `view-all`, `window`, `window-code2`

---

## 9. Components

All heights reference `--size-control` (40px) unless noted. States marked *proposed* aren't in the Paper source. Remove them if you don't want them.

### Global states (proposed)

| State | Rule |
|---|---|
| Hover — ghost / secondary / icon button | background `background-selected` |
| Hover — primary button | opacity .88 |
| Hover — nav item | background `surface-subtle` |
| Focus-visible | 2px solid `text-strong` outline, 2px offset |
| Input focus | border becomes `text-subtle` |
| Disabled | opacity .4, `cursor: not-allowed` |

### Button

40px tall · pill (`radius-full`) · 16px horizontal padding · `base` 16/24 Medium · optional 16px leading icon, 8px gap.

| Variant | Fill | Text / icon | Border |
|---|---|---|---|
| Primary | `inverse` | `on-inverse` | — |
| Secondary | `surface` | `text-strong` | 1px `border` |
| Ghost | transparent | `text-default` | — |

Use one primary button per view.

```html
<button class="btn btn-primary">Primary</button>
<button class="btn btn-primary"><svg class="icon" width="16" height="16"><use href="#i-download"/></svg>With icon</button>
<button class="btn btn-secondary">Secondary</button>
<button class="btn btn-ghost">Ghost</button>
```

### Navigation item

40px · `radius-lg` (12) · 12px horizontal padding · `md` 14/20 · 16px icon · 12px gap (8px in top-bar tabs).

| State | Background | Text | Weight | Icon |
|---|---|---|---|---|
| Default | transparent | `text-default` | Regular | `icon` |
| Selected | `background-selected` | `text-strong` | Medium | `icon-strong` |

Mark the selected item with `aria-current="page"`.

### Input

40px · `radius-md` (8) · 12px horizontal padding · `surface` fill · 1px `border` · `sm` 13/18 · optional 16px leading icon, 8px gap. Placeholder `text-subtle`, value `text-strong`.

```html
<label class="input">
  <svg class="icon" width="16" height="16"><use href="#i-at-sign"/></svg>
  <span class="sr-only">Label</span>
  <input type="text" placeholder="Placeholder">
</label>
```

### Icon button

40×40 · `radius-lg` (12) · 16px icon in `icon`.

| Variant | Style |
|---|---|
| Default | transparent |
| Selected | `background-selected` |
| Outline | 1px `border` |

### Badge

24px tall · pill · 12px horizontal padding · `xs` 12/16, 0em.

| Variant | Background | Text | Weight |
|---|---|---|---|
| Selected | `background-selected` | `text-strong` | Medium |
| Default | transparent | `text-default` | Regular |

### Divider

1px line, `--color-divider`.

### Card

`surface` · 1px `border` · `radius-xl` (16) · 24px padding · 12px gap · no shadow.

- **Titled card:** 16px icon + `md` Medium `text-strong` title (8px gap), then `sm` `text-default` description.
- **Overline card:** overline (`xs` Medium `text-subtle`, uppercase) → `lg` Medium `text-strong` title → `sm` `text-default` metadata.

### Toggle

Track 36×20, 2px padding, pill. Knob 16×16, pill. Use `role="switch"` and `aria-checked`.

| State | Track | Knob | Knob position |
|---|---|---|---|
| Off | `background-selected` | `surface` + 1px `border` | left |
| On | `inverse` | `on-inverse` | right |

---

## 10. Patterns

### App shell

- **Shell:** `background`, 1px `border`, `radius-2xl` (24) when framed.
- **Top bar:** 76px tall · `surface` · 1px bottom `divider` · 24px horizontal padding · 24px gap. Logo slot at 18px in `icon-strong`, then tabs (nav items with an 8px icon gap) 4px apart.
- **Sidebar:** 256px wide · `surface` · 1px right `divider` · 16px padding · 4px between items. Section label: `xs` Regular `text-subtle`, padding 24 top / 8 bottom / 12 sides.
- **Main:** `surface`, fills the remaining space.
- **Responsive:** the sidebar hides below 768px.

### Content header

Flex row, bottom-aligned, space-between · 24px bottom padding · 1px bottom `divider`.
Left: `xl` Medium `text-strong` title + `sm` `text-default` description, 8px apart. Right: one primary button.

### Settings section

- **Container:** card shell (`surface`, 1px `border`, `radius-xl`, overflow clipped).
- **Row:** 16px vertical × 24px horizontal padding · 24px gap · 1px `divider` between rows (none after the last).
- **Row text:** `md` Medium `text-strong` label + `sm` `text-default` description, 4px apart.
- **Row control:** an input 220px wide, or a toggle.
- **Below 640px:** rows stack and inputs go full width.

### Empty state

Centered column · 64px padding · 24px gap.
40px glyph in `icon-strong` → `xl` Medium `text-strong` title + `base` `text-default` description (12px apart) → one primary button.

---

## 11. Notes

- **Icons differ from the Paper file.** Paper drew custom 16px icons with a 1.25px stroke. This system uses the Nucleo files: a 2px stroke on a 20px grid, which renders as about 1.6px at 16px. The Paper "Mobile" glyph is Nucleo `stack-filled`.
- **Values the source used but never defined:** `--color-surface`, `--color-icon-strong`, `--color-inverse` and the sidebar width (`w-sidebar`). They're set to #FFFFFF, #292929 (the source draws that glyph in rgb(40 40 40)), #292929 and 256px. Change them if you meant something else.
- **Not in the source:** dark theme, status colors, tables, select / checkbox / radio controls. They're not specced here.
- **Font licensing.** Apple's SF Pro license limits use to mockups of UI for Apple platforms. Check it before you ship SF Pro on a public website. The font stack falls back to `-apple-system` / `system-ui`, which gives SF on Apple devices without hosting the files.
