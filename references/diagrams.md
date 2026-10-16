# Diagrams for slides

Read when relationships or ordered change need a diagram. Keep graph data/labels editable and bind visuals to the deck theme. Optional [gallery](../assets/pattern-gallery.html): process and architecture examples.

Credit: [Cathryn Lavery's Diagram Design](https://github.com/cathrynlavery/diagram-design) informed editorial restraint, selective emphasis, semantic tokens, and inline SVG. Consulted 2026-10-16: [skill](https://github.com/cathrynlavery/diagram-design/blob/main/skills/diagram-design/SKILL.md), [style guide](https://github.com/cathrynlavery/diagram-design/blob/main/skills/diagram-design/references/style-guide.md), [connectors](https://github.com/cathrynlavery/diagram-design/blob/main/skills/diagram-design/references/primitives-core.md). This independent adaptation bundles no upstream code/artwork and requires neither its installation nor its onboarding/default skin.

## Choose and theme

Use process for stages/outputs, architecture for components/connections, timeline for phases/dates, swimlanes for ownership/handoffs, and flowcharts for decisions/outcomes. Prefer tables for attribute comparisons. Explain one main relationship; simplify or split without silently dropping required information.

| Diagram role | Theme role |
| --- | --- |
| Paper / container | `background` / `surface` |
| Labels / secondary labels | `text` / `textMuted` |
| Decorative rules | `border` |
| Essential connections/boundaries | Checked `controlBorder`, `textMuted`, or `primaryText` |
| Focal fill/text | `primary` / `onPrimary` |
| Soft emphasis | `primarySoft` / checked foreground |
| Typography | Existing heading/body/technical roles |

Emphasize the central node/path, leaving most elements neutral. Use labels or dash patterns as well as color. Apply [contrast checks](design-system.md#measure-contrast), including markers and label backings. Preserve custom theme colors/fonts rather than adopting the reference's palette.

## Render and verify

Use inline SVG with unique per-instance title/description/marker/mask IDs. Informative SVGs need `role="img"` and resolving `aria-labelledby`; decorative SVGs may be hidden.

Route clear horizontal/vertical connections around unrelated nodes. Separate shared-edge attachment points and parallel paths. Keep labels clear of strokes/nodes, adding opaque backing where needed. Draw connections before opaque nodes; verify endpoints/direction after edits.

Use readable slide typography at actual rendered size. On narrow screens, recompose vertically or provide an equivalent labeled list. Motion should clarify real sequence/state; retain a complete static/textual equivalent and honor editing/reduced-motion behavior.

Inspect clipping, overlap, and contrast at target sizes. Standalone SVG export must resolve document CSS tokens and include styling/font fallbacks.
