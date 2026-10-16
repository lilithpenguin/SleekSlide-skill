# Upward covering panels

Use for a small set of features, process stages, or design principles that deserve separate attention within one slide. The incoming panel moves upward over the previous panel's body, leaving its keyword header exposed. The visible header remains a button for revisiting that point. This pattern is inspired by the user's GT Standard screenshot; it does not require that site's fonts, artwork, or colors.

## Three starting templates

The runnable [gallery](../assets/pattern-gallery.html) includes original sample content:

| Variant | Content per panel | Appropriate use |
| --- | --- | --- |
| Features | Short keyword, benefit, explanatory text, simple visual | Product capabilities with distinct benefits |
| Process | Stage keyword, action, output, sequence visual | A short ordered workflow |
| Principles | Principle keyword, rationale, concrete implication | Explaining design decisions; does not supply private storytelling guidance |

Prefer three or four panels; choose fewer when the viewport or wording needs more room. Do not turn every slide into a stack. Contrast or parallel comparison may be clearer with both items visible together.

## Geometry and state

Keep the outer slide and sidebar stationary. Within a bounded stage of height `H`, give each keyword rail height `R`. For panel index `i`, its settled top is `i * R`, and its height is `H - i * R`. Later panels paint above earlier ones and begin below the stage. When advancing, translate the next panel to its settled top. Earlier bodies remain behind the incoming opaque panel, while their rails stay visible. The last panel must still have enough room for its full content.

Store `activePanelId` independently of slide order. Keep `id`, `keyword`, `title`, `body`, and visual data separate from geometry. Use the model to rebuild after edits or reordering. Avoid raw HTML fields for routine text. The sample gallery uses an array of plain text and original SVG; it intentionally does not implement the full deck editor.

The stage clips moving offstage panels intentionally; verify that no active content is clipped. On short/mobile screens, reduce composition complexity and reflow the visual. If readable content cannot fit, use a keyword selector with a single active body, or disclose a reading-mode fallback. Do not reduce the whole slide to miniature type.

## Input and deck integration

- Reuse the deck's single previous/next bar. Forward advances the panel sequence before the next slide. Backward reverses panels before the previous slide. Expose whether the component handled the action to the parent deck controller; never advance a panel and slide from the same event.
- Wheel input is an optional enhancement over the stage. Normalize delta modes, ignore horizontal/pinch gestures and interactive fields, accumulate a threshold, and accept one step per gesture. Require a quiet interval so trackpad inertia does not skip several panels. Avoid document-wide wheel capture. Keep normal input behavior outside the stage.
- Provide buttons and keyboard alternatives, plus clickable earlier keyword headers. Touch users can use these controls without learning a gesture. Do not intercept space/arrows from inputs, sliders, buttons, or editable content.
- Future panels must be inert and absent from the accessibility tree. Covered bodies must also be inert and hidden from assistive technology; their keyword buttons remain available. If focus is about to become covered, move it to the appropriate visible keyword button. Announce the selected keyword once rather than every animation frame.
- Cancel pending gesture timers on leave, and reset gesture state on re-entry. Choose reset or resume deliberately. Freeze motion during editing and expose all panel fields in the editor. Under reduced motion, change panels immediately while retaining the same controls and all content.

## Theme and validation

Map panel backgrounds and foregrounds to approved theme role pairs: `surface/text`, `primarySoft/text`, and optionally `primary/onPrimary`. Supporting colors may distinguish chapters, but the reference's blue/pink/yellow scheme is not the default. Keyword rails, SVG fills, arrowheads, focus indicators, and controls must respond to the same theme change.

Check the first, intermediate, and final state; forward/backward movement; header revisits; a sustained wheel gesture; repeated fast input; reduced motion; focus after covering; and the longest editable copy at desktop, shorter laptop, and mobile sizes. Integration into a full deck additionally needs the boundary handoff and editor/persistence checks from SKILL.md.
