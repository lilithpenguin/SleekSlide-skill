# Interaction choices

Read for counters, live controls, or specialized effects. Choose effects that explain content; this is not a checklist.

| Effect | Implementation / invariant |
| --- | --- |
| Entrance | CSS/Web Animations; GSAP for coordinated sequences. Animate containers so text edits remain robust. |
| Covering panels | Bounded state + transforms; see [stacked panels](stacked-panels.md). |
| Numeric change | GSAP or requestAnimationFrame over numeric state; separate units, precision, target, and timing. |
| Chart/process reveal | Data-driven HTML/SVG; keep labels/evidence editable. See [diagrams](diagrams.md). |
| Product setting | Labeled native range/button, bounded state, meaningful presets; label hypothetical results. |
| Before/after | Toggle or labeled range; retain both views and keyboard access. |
| Word/line reveal | Split only when needed; re-split after edits/fonts/layout changes, not every frame. |
| Scramble | Decorative clone; preserve correct semantic text and reduced-motion fallback. |
| Font morph | Verify actual axes/ranges; prefer standard font properties. Avoid reflowing body text or faking width by stretching it. |
| Looping illustration | Optional supplied/authored Lottie; pause offscreen and keep primary metrics separate. |

## Numeric and live state

Interpolate numbers, then format for locale/units. Support descending/decimal values, clamp ranges, and set exact final values. Keep accessible final text without announcing every frame. Cancel an existing tween before starting another. Graphs and metrics share state; editing updates model/final preview without launching presentation loops.

Controls should explain a real setting or clearly labeled scenario. Do not invent capabilities or a business model to justify a slider. Font effects depend on the chosen font, not vice versa; inspect axes such as `wght`, `wdth`, `opsz`, and `slnt` before using them.

## Sequencing

Useful starting durations: 200–600 ms for moves; 800–1400 ms for counters. Adapt to content and presenter pacing. Provide enter/leave, next reveal, replay, and reduced-motion states as needed. Avoid multiple controllers animating one property.

Use the deck's active-slide state; IntersectionObserver only when it matches navigation. Do not add document scrolling just to trigger effects. Lazy-load optional assets and supply static fallbacks; bundle dependencies for promised offline output. Tailwind is optional styling, not a motion engine.

Long pinned sequences, mouse-follow effects, custom cursors, continuous scrambling, WebGL, and bespoke Lottie need a clear reason. The optional [gallery](../assets/pattern-gallery.html) provides implementation examples; inspect only the selected pattern.

## Inspiration and documentation

[GT Mechanik](https://gt-mechanik.com/) and [GT Standard](https://gt-standard.com/), inspected 2026-10-16, informed paper/panel reveals, live controls, variable-type effects, and chapter navigation. Their observed GSAP/Lottie/Tailwind implementations are dated references, not dependencies. Reinspect for fresh technical research; use original visuals and legitimate fonts.

Docs: [GSAP](https://gsap.com/docs/v3/GSAP/), [Web Animations](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API), [variable fonts](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Fonts/Variable_fonts).
