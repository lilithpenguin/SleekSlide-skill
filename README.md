# SleekSlide

A Codex skill for turning a brief, document, or webpage into an editable HTML deck. It starts with a slide-by-slide content and interaction plan, then builds one screen per slide with a contents sidebar and one control bar.

- Brand-aware palettes from an optional primary color, checked contrast, and reusable type hierarchy.
- Selective motion: counters, reveals, live controls, and upward covering panels with persistent keyword headers.
- In-page editing for text, metrics, images, and slide organization; browser drafts and portable export.
- Keyboard/touch controls, responsive layouts, and reduced-motion support.

HTML/CSS/JavaScript are the baseline; GSAP is optional. Native Figma, PPTX, and video use separate workflows.

## Install

For a new installation:

```sh
git clone https://github.com/lilithpenguin/SleekSlide-skill.git ~/.codex/skills/sleekslide
```

With a custom Codex home, use its `skills/sleekslide` directory.

## Use

> Use $sleekslide to turn https://example.com into a nine-slide product deck. Keep its branding and include one interactive example.

> Use $sleekslide with #6750A4 as primary, a restrained analogous palette, and a clear type hierarchy.

> Use $sleekslide to add covering feature panels that slide upward while earlier keywords stay visible.

Add “Stop after the rundown so I can review it” when you want plan approval before building. Existing brand guidelines take priority; personal storytelling/brand presets can remain in a separate private skill.

## Preview and sharing

Delivery defaults to local HTML with localhost preview when useful. Remote previews, hosting, and shareable links require a request. Browser drafts stay in that browser; exported files carry edits elsewhere. Requested password protection belongs on the host/server, not in downloadable JavaScript.

## Resources

[SKILL.md](SKILL.md) contains the core workflow and loads only relevant references: [theme](references/design-system.md), [interactions](references/interaction-patterns.md), [stacked panels](references/stacked-panels.md), [diagrams](references/diagrams.md), [editing/saving](references/editing-and-sharing.md), and [hosting](references/hosting.md).

The optional [HTML gallery](assets/pattern-gallery.html) demonstrates three panel variants and two themed SVG diagrams. It is implementation material, not mandatory context or a complete deck editor. [Interface metadata](agents/openai.yaml) supplies the Codex display and example prompt.

Diagram guidance credits [Cathryn Lavery's Diagram Design](https://github.com/cathrynlavery/diagram-design). Bundled examples are original; no installation or default palette is inherited.
