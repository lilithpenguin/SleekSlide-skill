# SleekSlide

SleekSlide is a Codex skill for turning a brief, existing content, or a webpage into a polished, editable HTML presentation. It starts with a slide-by-slide content and interaction plan, then builds a deck that fits one slide to each screen.

A contents sidebar keeps the story easy to navigate. One presentation bar holds the controls. An in-page editor lets you update text, metric values, images, and slide order without touching the source code. Animations and interactive examples are chosen to explain the content, with quieter treatment where the message speaks for itself.

Fonts and colors can follow your brand or be chosen for the project. The technical foundation stays small: HTML, CSS, and JavaScript, with GSAP when coordinated motion is useful.

## What the skill does

- Shares a numbered rundown of each slide's content and interactions before implementation.
- Derives a coordinated palette from an optional primary color and defines a reusable type hierarchy, with checked contrast pairings.
- Builds responsive, single-screen slides with a contents sidebar and one set of presentation controls.
- Adds useful counters, chart reveals, sliders, toggles, or product examples where appropriate.
- Includes an editing mode for routine content changes and slide organization.
- Distinguishes browser-local drafts, downloadable HTML, and hosted updates.
- Supports keyboard navigation and reduced-motion preferences.

## Install

For a new installation in the default Codex skills directory:

```sh
git clone https://github.com/lilithpenguin/SleekSlide-skill.git ~/.codex/skills/sleekslide
```

If you use a custom Codex home directory, install the skill under its `skills/sleekslide` directory instead.

## Use

Start with a topic, document, or webpage. Include the audience and any required slide count or brand guidelines.

> Use $sleekslide to turn https://example.com into a nine-slide product presentation. First share the content and interaction rundown for each slide. Keep the existing branding and include one interactive product example.

If you want to review the plan before implementation, add:

> Stop after the rundown so I can review it before you build.

You can also request changes to an existing HTML deck:

> Use $sleekslide to simplify this deck's navigation and add an editable number counter to slide 4.

## Color and typography

Supply a primary color to use as the theme seed. SleekSlide can derive supporting tints, neutrals, and an optional accent using a monochromatic, analogous, or complementary direction. It preserves the supplied primary and checks the text/background pairs used in the deck.

The plan includes palette roles, actual color values, and a type hierarchy with font families, sizes, weights, and line heights. Existing brand guidelines take precedence. Personal brand presets can stay in a separate private companion skill.

> Use $sleekslide to create a product deck with #6750A4 as the primary color. Generate a restrained analogous palette and a clear type hierarchy. Include the theme specification in the slide plan before building.

## Interaction and diagram examples

Open [the pattern gallery](assets/pattern-gallery.html) in a browser. It includes three upward covering-panel templates—features, process, and design principles—and two inline SVG diagram examples. Scroll over the panel body, use the controls, or revisit an earlier keyword header. Change the primary color to see all examples update together.

> Use $sleekslide with stacked feature panels that slide up over each other, keeping earlier keywords visible. Add a process diagram using my deck's theme colors and typography.

The diagram guidance references [Cathryn Lavery's Diagram Design](https://github.com/cathrynlavery/diagram-design). The bundled examples are original and inherit the deck theme; they do not require installing that skill or adopting its default palette.

## Editing and sharing

Generated decks can include an editor for changing content and downloading an updated copy. A browser draft stays in that browser; publishing changes to a hosted deck requires a supported hosting workflow.

If a deck needs password protection, access controls belong on its host or server. The skill includes guidance for that setup; a password embedded in downloadable page code does not protect private content.

## Scope

This repository contains reusable authoring instructions and supporting references. Each generated deck receives its own presentation source and dependencies. Native Figma decks, PowerPoint authoring, and video production use separate workflows.

## Files

- [SKILL.md](SKILL.md): planning, authoring, editing, and validation guidance.
- [Interaction patterns](references/interaction-patterns.md): adaptable effects and implementation choices.
- [Design system guidance](references/design-system.md): palette generation, contrast checks, and type hierarchy.
- [Stacked panels](references/stacked-panels.md): upward reveals with persistent keyword headers.
- [Diagram guidance](references/diagrams.md): themed SVG diagrams for slides.
- [Pattern gallery](assets/pattern-gallery.html): three panel templates and two diagram examples.
- [Editing and sharing](references/editing-and-sharing.md): persistence, export, and access controls.
- [Codex interface metadata](agents/openai.yaml): display name and example invocation.
