# SleekSlide

A Codex skill for creating editable, interactive HTML presentation decks.

SleekSlide guides the creation of browser-based presentations with a contents sidebar, one screen per slide, animated metrics, and an editing mode for routine content changes. It favors HTML, CSS, and JavaScript, with GSAP when coordinated motion is useful.

## Use

Install this repository as a skill named `sleekslide` in your Codex skills directory. For a new installation using the default directory:

```sh
git clone https://github.com/lilithpenguin/SleekSlide-skill.git ~/.codex/skills/sleekslide
```

Then request a deck:

> Use $sleekslide to create an editable 10-slide product deck about [topic], with a contents sidebar, animated metrics, and one interactive product demonstration.

Provide the audience, content, and any required slide count. Fonts and colors are optional: supply brand guidelines or let the skill choose a suitable theme.

## What it covers

- Responsive slide layouts, sidebar navigation, keyboard controls, and reusable motion.
- Editable text and numeric values, with clear saving and export behavior.
- Live sliders and toggles when they help explain the product.
- Accessible final states and reduced-motion behavior.
- Hosting and password-protection considerations when sharing is requested.

This repository contains authoring instructions, not a presentation runtime. Individual decks receive their own source and dependencies. Native Figma decks, PowerPoint authoring, and video production use separate workflows.

## Skill files

- [SKILL.md](SKILL.md): scope, workflow, and validation requirements.
- [Interaction patterns](references/interaction-patterns.md): adaptable effects and implementation choices.
- [Editing and sharing](references/editing-and-sharing.md): persistence, export, and access controls.
- [Codex interface metadata](agents/openai.yaml): display name and example invocation.
