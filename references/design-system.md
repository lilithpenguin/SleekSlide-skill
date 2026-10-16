# Theme generation and type hierarchy

Read when creating a deck's visual system, deriving colors from a primary color, or changing typography. Apply supplied brand guidelines and an existing deck's conventions first. These are reusable defaults, not a fixed SleekSlide aesthetic.

## Inputs and scope

A primary color is enough to begin. Optional inputs include existing brand colors, a preferred harmony, light or dark treatment, heading/body fonts, desired tone, and a type scale. Infer reasonable missing choices from the subject and audience, and state them in the plan. Do not require the user to supply a complete design system.

When the user supplies a full brand palette or type system, preserve it and identify any necessary accessibility adaptations. If they supply only a primary color, generate a small coordinated palette. Keep personal presets in a separate private skill or user-selected private file; do not copy private instructions into a public skill, example, or release ZIP.

## Palette from one primary color

1. Preserve the exact supplied color as `primary`. Parse it consistently, normalize the representation, and record it in the theme model. A generated variant may be useful for a particular role, but must not silently replace the brand seed.
2. Choose one harmony suited to the deck. A restrained monochromatic palette is a good default for information-heavy work. Analogous hues, often around 25–35 degrees apart, can create a related supporting accent. A complementary hue, around 180 degrees away, can supply a contrasting highlight. These angles are starting heuristics; none guarantees an attractive or accessible result. Do not combine every harmony or introduce several competing accents by default.
3. Derive light and dark variants using perceptual lightness and chroma, preferably in OKLCH when tools support it. Avoid treating equal HSL lightness values as equally bright. For near-neutral seeds, hue is weakly defined; prefer neutral/monochromatic support unless another hue is requested or justified.
4. Make lightly tinted backgrounds and restrained neutrals, with dark and light text roles. Keep enough separation between text levels without making secondary information faint. Use a supporting hue sparingly for emphasis, illustration, or a chart distinction.
5. Keep generated colors within the target gamut. If an OKLCH color falls outside sRGB and broad portability matters, reduce chroma while preserving hue/lightness as far as practical; provide tested sRGB fallback values. Do not rely on unexamined channel clipping to preserve the intended relationship.
6. Calculate contrast for the exact serialized colors and the backgrounds where they will be used. Check colors after gamut mapping and quantization. Adjust role-specific lightness/chroma or the adjacent surface when a pair fails. Choose light or dark text on the primary according to the measured result. A bright primary may need a darker `primaryText` variant for links or headings on a light page.

Use hue relationships to organize the palette and numerical contrast to validate intended pairings. Visual inspection still matters, particularly for very thin type, projection, gradients, and color-vision differences.

## Named roles

Create only the roles the deck needs. A useful starting set is:

| Role | Purpose |
| --- | --- |
| `primary` | Exact supplied seed and prominent brand use |
| `onPrimary` | Verified readable text/icons on the primary fill |
| `primaryText` | A seed-related foreground that works on the main surface |
| `primarySoft` | Pale or muted supporting fill |
| `accent`, `onAccent` | Optional supporting emphasis and its readable foreground |
| `background`, `surface` | Main canvas and any distinct content surface |
| `text`, `textMuted` | Primary and secondary text |
| `border` | Decorative separators |
| `controlBorder`, `focus` | Necessary control boundaries and visible focus treatment |
| `inverse`, `onInverse` | Optional contrasting section treatment |

Pair foregrounds with their intended backgrounds explicitly. `onPrimary` is not a universal text color, and decorative `border` is not necessarily suitable as a control boundary. Add semantic or chart colors only when the content requires them. Use labels, markers, patterns, or position as well as color to convey meaning.

## Contrast checks

For ordinary text, target at least 4.5:1 against its actual background. The WCAG large-text minimum is 3:1 for at least 24 CSS px regular text or approximately 18.67 CSS px bold text. Apply these thresholds to the rendered size, not a large design-canvas size that was subsequently scaled down. Prefer stronger contrast when practical for presentation text. Necessary visual boundaries and meaningful non-text graphics generally need 3:1 against adjacent colors; assess the specific component rather than every decorative line.

Compute contrast from sRGB relative luminance, not differences in hue, OKLCH lightness, or a visual guess. Linearize each sRGB channel `c` in 0–1 as `c / 12.92` for `c <= 0.04045`, otherwise `((c + 0.055) / 1.055) ** 2.4`. Relative luminance is `0.2126 R + 0.7152 G + 0.0722 B`. Contrast is `(lighter + 0.05) / (darker + 0.05)`. Make pass/fail decisions with the full computed result, without rounding a failing value into a passing one.

Check primary/body/muted text on every used light or dark surface; button labels; links; focus treatment; and chart labels. Resolve transparency against the effective background. For text on images or gradients, inspect the relevant background region and add a solid backing if reliable contrast is difficult. Record the checked pairs and ratios in the theme plan or private validation record. This is a contrast check, not a claim of full WCAG conformance.

## Type hierarchy

Choose font families from the user's brand, the source product, or a deliberate pairing. One family with suitable weights is often sufficient. A second family may serve display text or a wordmark; do not add fonts just to fill roles. Verify availability, licensing, required glyphs, and actual weights. Use fallback stacks. Treat uppercase, tracking, weight, size, and spacing as a coordinated hierarchy.

Set the reference slide canvas and base body size before choosing the scale. A modular ratio such as 1.20 or 1.25 is a useful starting point. Assign sizes to named roles and reuse them across slides; do not invent a new size for each text box.

For an approximately 1280-pixel-wide slide canvas, a 20 px body size and 1.25 ratio can begin with this rounded scale. These are design defaults, not accessibility requirements or mandatory values:

| Role | Size | Line height | Typical weight |
| --- | --- | --- | --- |
| Display / cover | 76 px | 1.04 | 500–600 |
| Slide title | 61 px | 1.10 | 500–600 |
| Subheading | 39 px | 1.20 | 500–600 |
| Lead / short emphasis | 25 px | 1.40 | 400–500 |
| Body | 20 px | 1.50 | 400 |
| Caption / supporting label | 16 px | 1.40 | 400–500 |

Use the actual loaded font's proportions to refine the scale. Cover type can be larger if the composition supports it. Use moderately tighter tracking for large headings when the face benefits, and normal tracking for body copy. Avoid blanket negative tracking, excessive uppercase, and low-weight small text. Use tabular figures for changing numeric values when supported.

The slide canvas is the area remaining after navigation, not necessarily the full browser width. At smaller viewports, recompose content and adjust role sizes within readable bounds. Do not uniformly scale a desktop canvas until body text and captions become tiny. Check the longest title and body example with the actual fonts at desktop, shorter laptop, and mobile sizes. Edit density or composition before shrinking critical content. Preserve the requested slide count.

## Theme model and implementation

Separate inputs from derived tokens. Store the primary seed, harmony choice, optional locked overrides, font roles, reference canvas, and type scale in a theme model. Generate named CSS custom properties for all slides. Keep spacing, line thickness, radii, and emphasis treatment consistent with the same visual direction; a large UI component library is unnecessary for a deck.

When primary-color editing is offered, regenerate the derived roles that depend on the seed, preserve explicit overrides, and recheck affected contrast pairs. Update all relevant slides and controls. Merely changing one accent variable while leaving incompatible derived colors is not complete theme regeneration. Keep inputs and derived tokens in browser drafts and exports so reopening a deck preserves its visual system.

For existing decks, extend the theme model only as needed for the requested edit. Do not imply an existing basic color picker already performs palette generation. Keep a locked brand color intact and explain any failing pairing; use another foreground or surface instead of silently overriding the locked value.

## Plan output

Before building, show a compact specification alongside the slide rundown:

- The primary seed and chosen harmony, with a one-sentence reason.
- A palette table with actual values and intended roles, including readable foreground/background pairings.
- The heading/body font choices and named type scale, with the reference slide size.
- Any material constraints, such as an unavailable font or a brand color that needs a separate text variant.

No additional approval is required unless the user requested review before implementation. If the brief asks only for palette or typography exploration, provide that exploration without building a deck.

## Primary references

- [OKLCH color notation](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Values/color_value/oklch)
- [CSS Color 4 conversion examples](https://www.w3.org/TR/css-color-4/#color-conversion-code)
- [WCAG text contrast](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)
- [WCAG non-text contrast](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html)
