# Adaptable interaction patterns

Read when choosing motion, evaluating a reference, or implementing an effect. Use the smallest technique that supports the content. These are options, not a checklist to include in every deck.

## Reference findings

Inspected on 2026-10-16:

- [GT Mechanik](https://gt-mechanik.com/) combines Tailwind CSS, GSAP/ScrollTrigger, SplitText/ScrambleText, SVG-rendered Lottie illustrations, and custom variable-font interaction. Its scroll-linked paper reveals and mechanical art are more specialized than ordinary presentation transitions. Evidence: [public JavaScript](https://gt-mechanik.com/assets/index-BloRPNPN.js), [stylesheet](https://gt-mechanik.com/assets/index-vzwSAYox.css).
- [GT Standard](https://gt-standard.com/) combines Tailwind CSS, GSAP/ScrollTrigger, SVG-rendered Lottie, and CSS variables controlling variable-font axes. Its live font sliders, state toggles, active chapter navigation, and panel transitions are useful interaction references. Some Lottie frames are linked to scroll progress; animation JSON is embedded in the inspected JavaScript bundle. Evidence: [public JavaScript](https://gt-standard.com/source.41b3788d.js), [stylesheet](https://gt-standard.com/source.90a60e7d.css).

Treat these as dated implementation observations. Hashed asset URLs can change; inspect the current HTML before relying on them for fresh research. Borrow interaction principles with original content and visuals. These sites are inspiration, not runtime dependencies or a source of bundled proprietary fonts/artwork.

## Select effects

| Effect | Preferred technique | Editing implications |
| --- | --- | --- |
| Contents/sidebar progress | Semantic links/buttons, a single active-slide state, CSS transition | Generate labels and order from the content model |
| Slide or section entrance | CSS/Web Animations for a simple move/fade; GSAP for coordinated sequences | Apply to a container so text edits do not break timing |
| Upward covering panels with keyword headers | Bounded panel state and CSS transforms; see [stacked panels](stacked-panels.md) | Keep stable point IDs, keyword, body, and visual as data; reuse the deck controls |
| Count-up metric | A numeric state interpolated by GSAP or a small requestAnimationFrame loop | Keep target, units, precision, and timing as separate fields |
| Chart or process reveal | Native SVG/HTML with data-driven drawing and short transitions | Keep the evidence and labels editable |
| Product slider/toggle | Native range input or button updating a bounded state model | Expose presets/default values; label illustrative outcomes |
| Before/after comparison | Toggle states or a labeled range-controlled reveal | Keep both views in source and support keyboard input |
| Word/line reveal | Animate semantic containers; split text only when justified | Re-split after edits or font/layout changes, not on every frame |
| Scramble title | Optional short effect on a decorative text clone | Keep the correct semantic title stable; use the original under reduced motion |
| Variable-font morph | CSS font properties/axes driven by GSAP or direct input | Inspect available axes/ranges; contain layout changes and verify fallback |
| Looping product illustration | Lottie with an appropriate supplied/authored asset | Easy to integrate, potentially costly to redesign; keep primary metrics separate |

Default to HTML/CSS/JavaScript plus GSAP core when rich sequencing warrants it. Tailwind is a styling option, not an interaction engine. Preserve it when already in the project rather than adding it solely to match a reference's stack.

The optional [pattern gallery](../assets/pattern-gallery.html) contains three covering-panel variants and two theme-aware SVG examples. Inspect only the relevant implementation when needed. Read [diagram guidance](diagrams.md) when a slide benefits from a process or relationship diagram. Adapt content and tokens; the gallery is a component reference, not a complete deck editor.

## Numeric changes

Interpolate actual numbers, then format for display. Do not count by repeatedly parsing a string containing currency signs, separators, or units. Clamp to the intended range, handle descending and decimal values, and set the exact final value on completion. Use a formatting function appropriate to the requested locale and units. Keep the textual final value accessible without announcing every intermediate frame.

Kill the previous tween before starting another on the same target. Changing an editor value updates the model and final preview immediately; it should not create a new running presentation loop. Link a graph and displayed metric to the same state so they cannot disagree.

## Live controls and typography

GT Standard's direct manipulation is particularly transferable: moving a labeled slider changes a visible result immediately. For a product deck, map that pattern to a meaningful product setting, comparison, or an explicitly labeled hypothetical scenario. Do not fabricate a business model merely to justify an interactive slider.

Variable-font axes belong to specific fonts. Inspect their supported ranges before using `wght`, `wdth`, `opsz`, `slnt`, or custom axes. Prefer high-level CSS font properties for standard axes when they suffice. Animate a decorative heading rather than body copy if changing glyph width causes distracting reflow. Do not fake a missing width axis by stretching important body text.

## Timing and portability

Short movements commonly fit within 200–600 ms; allow around 800–1400 ms for a count-up when legibility benefits. These are starting points, not fixed rules. Match the content, reference, and presenter pacing.

Keep one scene's sequencing controllable through enter, leave, reveal-next, replay, and reduced-motion states as applicable. Use a scene controller or an IntersectionObserver only when it corresponds to the navigation model. Avoid adding continuous document scroll just to trigger a slide effect.

Lazy-load optional animation assets and pause them when inactive. Do not embed a large illustration library in the initial JavaScript simply because the reference did so. Prefer static final-state fallbacks if optional animation fails to load. Portable/offline exports must bundle the dependencies they claim to support.

Useful primary documentation:

- [GSAP tweens and timelines](https://gsap.com/docs/v3/GSAP/)
- [Web Animations API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API)
- [Variable fonts](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Fonts/Variable_fonts)

## Effects requiring a specific reason

Long pinned scroll choreography, mouse-following content, constant text scrambling, custom cursors, WebGL scenes, and complex bespoke Lottie artwork are not the baseline for an editable deck. Use them when requested or when a clear explanatory benefit justifies the additional authoring, mobile adaptation, and maintenance. A normal product deck does not require them to feel responsive.
