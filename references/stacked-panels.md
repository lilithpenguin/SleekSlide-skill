# Upward covering panels

Use for a few features, stages, or design principles within one slide. Each incoming panel slides over the previous body, leaving its keyword header clickable above. Inspired by the user's GT Standard reference; use the deck's own theme and artwork.

Optional [gallery](../assets/pattern-gallery.html) variants:

| Variant | Editable content |
| --- | --- |
| Features | Keyword, benefit, explanation, visual |
| Process | Stage, action, output, sequence visual |
| Principles | Keyword, rationale, design implication |

Prefer 3–4 panels, fewer for dense copy/small screens. Use simultaneous views for direct comparisons. These templates do not supply private storytelling guidance.

## Geometry and model

Keep slide/sidebar stationary. In a stage of height `H`, rail height `R`, panel `i` settles at `i*R` with height `H-i*R`. Later panels paint above earlier ones, starting below the stage. Incoming opaque bodies cover earlier content while retaining keyword rails. Ensure the last body fits.

Store stable point IDs, keyword/title/body/visual, and `activePanelId`; rebuild geometry after edits/reordering. Clip offstage motion only, never active content. On narrow/short screens, simplify/reflow or use a keyword selector with one body. Disclose any reading fallback instead of shrinking type excessively.

## Input and accessibility

- Reuse the deck bar: forward/back handles panels before slides. Return whether the panel controller consumed the action; never change both from one event.
- Optional wheel handling belongs over the stage. Normalize delta modes, accumulate a threshold, accept one step per gesture, and require a quiet interval to reject inertia. Ignore horizontal/pinch gestures and interactive/editable fields; preserve input outside the stage.
- Provide buttons, keyboard alternatives, touch-reachable controls, and clickable prior headers. Follow the main skill's shortcut guards.
- Future panels are inert and hidden from assistive technology. Covered bodies are also inert/hidden; earlier keyword buttons remain available. Move focus before it becomes covered and announce the selected keyword once.
- Clear gesture timers on leave and choose reset/resume on entry. Freeze motion while editing; expose all point fields. Reduced motion changes panels immediately without losing content or controls.

Use approved `surface/text`, `primarySoft/text`, or `primary/onPrimary` pairs. Update rails, visuals, controls, and focus with theme changes; do not copy the reference's palette.

Check first/middle/last states, forward/back, header revisits, sustained wheel gestures, rapid input, reduced motion, focus, and longest copy at desktop/laptop/mobile sizes. Full-deck integration also needs boundary handoff and edit/save/export verification. The gallery is a component reference, not a complete deck editor.
