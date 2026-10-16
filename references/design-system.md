# Color and type

Read for a new/changed visual system. Existing branding wins. A primary color alone is sufficient; infer optional tone, light/dark treatment, harmony, and fonts, then state choices in the plan. A palette-only request need not produce a deck.

## Generate a palette

1. Preserve the exact supplied `primary` seed. Choose one restrained harmony: monochromatic; analogous (roughly 25–35° apart); or complementary (roughly 180°). Angles are starting points, not aesthetic or accessibility guarantees. Near-neutral seeds usually suit neutral support.
2. Derive tints, shades, and neutrals with perceptual lightness/chroma, preferably OKLCH. Equal HSL lightness does not mean equal brightness. For sRGB portability, gamut-map by reducing chroma and test serialized fallbacks; avoid unchecked channel clipping.
3. Assign only needed roles and measure their actual pairings. Choose readable `onPrimary`; use a separate `primaryText` variant if the seed fails on the canvas. Keep locked brand colors and adjust the foreground/surface instead.

| Roles | Use |
| --- | --- |
| `primary`, `onPrimary` | Seed fill and its readable foreground |
| `primaryText`, `primarySoft` | Brand-related text and supporting fill |
| `background`, `surface` | Canvas and containers |
| `text`, `textMuted` | Main and secondary text |
| `border` | Decorative rules |
| `controlBorder`, `focus` | Meaningful boundaries and focus |
| Optional `accent/onAccent`, `inverse/onInverse` | Supporting emphasis or contrasting sections |

Pair each foreground with its intended background; do not reuse `onPrimary` indiscriminately. Use labels/shape/position as well as color. Add semantic/chart colors only when needed.

## Measure contrast

- Ordinary text: ≥4.5:1. Large text: ≥3:1 at rendered sizes ≥24 CSS px regular or ≈18.67 CSS px bold.
- Essential non-text graphics and control boundaries: generally ≥3:1 against adjacent colors; decorative lines are different.
- Measure exact serialized colors after gamut mapping/quantization. Composite opacity first; inspect image/gradient regions or add a reliable backing. Check muted text, links, labels, buttons, focus, and dark/inverse surfaces. Record pairs/ratios without rounding failures into passes.

For normalized sRGB channel `c`, linearize as `c/12.92` when `c <= 0.04045`, otherwise `((c+0.055)/1.055)^2.4`. Luminance is `0.2126R + 0.7152G + 0.0722B`; contrast is `(lighter+0.05)/(darker+0.05)`. Contrast checks do not establish full accessibility conformance; inspect visually too.

## Type hierarchy

Use available, licensed fonts with verified loading, weights, language coverage, and fallback stacks. One family may suffice; use a second deliberately. Set the canvas size and base body before choosing a modular scale such as 1.20 or 1.25. Reuse named roles rather than inventing sizes per text box.

Example defaults for a ~1280 px-wide slide canvas, body 20 px, ratio 1.25:

| Role | px | Line height | Weight |
| --- | --- | --- | --- |
| Display | 76 | 1.04 | 500–600 |
| Slide title | 61 | 1.10 | 500–600 |
| Subheading | 39 | 1.20 | 500–600 |
| Lead | 25 | 1.40 | 400–500 |
| Body | 20 | 1.50 | 400 |
| Caption | 16 | 1.40 | 400–500 |

These are starting values, not accessibility requirements. Refine using actual font proportions. Avoid blanket negative tracking, excessive uppercase, and thin small text; use tabular figures for changing metrics. The canvas excludes navigation. Recompose at smaller sizes rather than uniformly scaling text down; check longest copy with loaded fonts.

## Model and plan

Store seed, harmony, locked overrides, font roles, type scale, and reference canvas separately from derived CSS tokens. If primary editing is offered, regenerate dependent roles across slides, controls, and diagrams; preserve overrides and recheck contrast. Persist inputs/tokens in drafts and exports. Do not describe a basic accent picker as full palette generation.

In the slide plan, show palette values/roles, harmony rationale, checked pairs, type roles (family/size/weight/line height), reference size, and material constraints. Keep spacing, radii, and stroke treatment consistent. Keep personal presets private.

Sources: [OKLCH](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/color_value/oklch), [CSS color conversions](https://www.w3.org/TR/css-color-4/#color-conversion-code), [text contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html), [non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).
