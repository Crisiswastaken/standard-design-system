# Standard Design System

Quiet, monochromatic UI kit for any product. Hierarchy comes from type, spacing, and contrast — never from accent color.

## Contents

```
├── design-system/     Spec + interactive HTML reference
├── icons/nucleo/      180 Nucleo Micro Bold Essential SVGs
└── fonts/sf-pro/      SF Pro setup (download fonts separately)
```

| Asset | Path | Notes |
| --- | --- | --- |
| Spec | [`design-system/DESIGN_SYSTEM.md`](design-system/DESIGN_SYSTEM.md) | Tokens, components, patterns |
| Preview | [`design-system/index.html`](design-system/index.html) | Open in a browser |
| Icons | [`icons/nucleo/micro-bold/`](icons/nucleo/micro-bold/) | 20px SVGs, `currentColor` |
| Icon gallery | [`icons/nucleo/index.html`](icons/nucleo/index.html) | Browse all icons |
| Fonts | [`fonts/sf-pro/`](fonts/sf-pro/) | Apple SF Pro (Text / Display / Rounded) |

## Quick start

1. **Preview** — open `design-system/index.html` in a browser (fonts load from `fonts/sf-pro/`).
2. **Icons** — open `icons/nucleo/index.html`, or inline any SVG from `icons/nucleo/micro-bold/`.

```html
<img src="icons/nucleo/micro-bold/check.svg" width="20" height="20" alt="" />
```

## Principles

1. **Monochrome only** — seven grays; emphasis is weight or darker gray.
2. **Every value is a token** — color, size, space, radius.
3. **40px control height** — buttons, inputs, nav items, icon buttons.
4. **Borders, not shadows** — 1px `#F2F2F2` separators by default.
5. **Two UI weights** — Regular 400 and Medium 500.

## Stack

- **Type:** SF Pro (variable) + Text / Display / Rounded statics  
- **Icons:** [Nucleo Micro Bold Essential](https://www.npmjs.com/package/nucleo-micro-bold-essential)  
- **Theme:** light only

## License

Design tokens, documentation, and Nucleo icon SVGs in this repo are available for use in projects.

**SF Pro** remains Apple proprietary — use under [Apple’s font license](https://developer.apple.com/fonts/).
