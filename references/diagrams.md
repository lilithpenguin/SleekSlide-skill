# Diagrams inside a themed deck

Use a diagram when relationships or ordered change explain a slide better than prose. Keep it part of the deck's visual system and editable source. The [gallery](../assets/pattern-gallery.html) contains original, self-contained process and architecture examples.

## Reference and scope

[Cathryn Lavery's Diagram Design](https://github.com/cathrynlavery/diagram-design) is the reference for restrained editorial diagrams, selective emphasis, semantic tokens, and inline SVG. Its [skill](https://github.com/cathrynlavery/diagram-design/blob/main/skills/diagram-design/SKILL.md), [style guide](https://github.com/cathrynlavery/diagram-design/blob/main/skills/diagram-design/references/style-guide.md), and [connector guidance](https://github.com/cathrynlavery/diagram-design/blob/main/skills/diagram-design/references/primitives-core.md) were consulted on 2026-10-16. This is an independent SleekSlide adaptation, not an installation or vendored copy of that skill. No upstream code or artwork is bundled. Its onboarding prompts and default skin are not SleekSlide requirements.

## Select a structure

| Message | Starting composition |
| --- | --- |
| Steps that produce an outcome | Process: clearly ordered stages, connecting direction, named output |
| Components and their connections | Architecture: components grouped by real boundaries, named relationships |
| Change across dates or phases | Timeline: a common axis with meaningful spacing or explicit equal-stage spacing |
| Ownership and handoffs | Swimlanes: owners on one axis, stages on the other |
| A decision changes the path | Flowchart: labeled branches and explicit outcomes |

Choose one main relationship per diagram. Remove redundant elements; use a table for attribute comparisons. For slide readability, begin with a handful of nodes and split overview from detail when needed. Do not silently drop required relationships to meet a visual budget.

## Bind the active theme

Resolve the reference's roles to SleekSlide's current theme; do not import its tangerine color or font families:

| Diagram role | SleekSlide source |
| --- | --- |
| Paper / container | `background` or `surface`, according to actual placement |
| Ink / node labels | `text` |
| Secondary labels | `textMuted` |
| Decorative rules | `border` |
| Essential connections and boundaries | A checked `textMuted`, `controlBorder`, or `primaryText` pairing |
| Focal fill / foreground | `primary` / `onPrimary` |
| Soft focal fill / foreground | `primarySoft` / checked `primaryText` or `text` |
| Fonts | Existing heading, body, and optional technical-label font roles |

Emphasize the central node or path; most elements can remain neutral. Distinguish relationship types with labels or dash patterns as well as color. Apply the contrast checks in [design-system.md](design-system.md) to the actual SVG background. Include markers and label backings when changing themes. The gallery's color control regenerates a small monochromatic demo palette; custom deck palettes can supply the same role names directly.

## Author and animate

Use inline SVG for precise connectors and labels; use semantic HTML for accompanying explanation and controls. Keep graph content and relationships in data where edits are offered. Define unique IDs per diagram instance for accessible titles, descriptions, markers, and masks. Give informative SVGs a title and description via `role="img"` and resolving `aria-labelledby`.

Prefer clear horizontal/vertical routing, with bends around unrelated nodes. Separate parallel paths and attachment points so connections remain traceable. Put labels in open space, clear of strokes and nodes; use an opaque backing when needed. Draw connections before opaque nodes. Verify direction and endpoints after changing labels or layout.

Use slide-level type roles at the actual rendered size. Do not copy small document-diagram font sizes into a presentation. At narrow widths, recompose the graph vertically or replace it with an equivalent labeled list; enlarging an SVG viewBox alone does not preserve readable labels.

Motion can reveal an actual sequence or highlight the selected path. Keep an understandable static state and a complete textual equivalent; avoid a perpetual animated flow that implies unsupported behavior. Freeze effects in editing mode and disable travel/drawing animation under reduced motion.

Inspect all nodes and connector labels for clipping/overlap at target sizes. Recheck text and meaningful strokes after theme changes. If exporting a standalone SVG, resolve CSS tokens and include the needed styling and font fallback; document-scoped variables alone do not travel with an extracted SVG.
