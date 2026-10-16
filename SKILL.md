---
name: sleekslide
description: "Plan, build, or edit interactive HTML slide decks with a contents sidebar, one screen per slide, and editable content."
---

# SleekSlide

Create editable HTML presentations. Preserve explicit instructions, existing conventions, supplied facts, and requested slide counts, including the cover. Keep native Figma, PPTX, and video work in their own workflows.

## Plan first

Before building or substantially restructuring, share a numbered rundown of every slide: message/source content, composition, interaction and purpose (including none), and editable fields. Usually 2–4 sentences per slide suffice. Identify assumptions and distinguish illustrative behavior from real capabilities or evidence.

Describe theme and navigation once. For a new visual system, include palette values/roles, harmony rationale, checked color pairs, fonts, and type hierarchy with its reference canvas size. Fonts/colors are optional inputs: prefer supplied branding, existing product styling, a chosen reference, then suitable defaults. Borrowing an interaction does not imply copying branding.

Proceed after sharing unless the user requested review or a plan-only response. For small edits, state the affected slides/controls and changes instead of replanning everything.

## Build

- Prefer semantic HTML/CSS/JavaScript; retain an existing framework. Use CSS/Web Animations for simple effects, GSAP for coordinated motion. ScrollTrigger and Lottie need a specific purpose.
- Separate content, theme, layout, and motion data. Use stable slide IDs and one model for sidebar, controls, hashes, and browser history. Centralize theme roles in CSS variables; keep text, metrics, and labels editable.
- Fit one slide beside the sidebar within the viewport, reserving control space. Recompose or reduce density before shrinking type; never crop active content. Preserve slide count. Collapse the sidebar on mobile; disclose any necessary reading/scrolling fallback.
- Use one presentation bar for previous/next, replay, editor, fullscreen, and mobile contents as needed. Keep branding, titles, and active-slide context in the sidebar; avoid duplicate progress/count displays.
- Provide buttons and keyboard navigation. Finish staged reveals before advancing slides. Ignore shortcuts in interactive/editable fields and dialogs.
- Include edit mode unless declined or already provided: text, sidebar labels, numeric targets, images/timing where present, and slide duplicate/delete/reorder. Write changes to the model. Freeze effects while editing; offer a static state and separate preview.
- Stop outgoing animations and stale callbacks; pause offscreen loops and choose reset/resume deliberately. Under reduced motion, retain complete content and usable controls. Provide keyboard/touch alternatives to hover.

## Read only what applies

| Need | Reference |
| --- | --- |
| New/changed palette or typography | [Design system](references/design-system.md) |
| Counters, live controls, or specialized effects | [Interactions](references/interaction-patterns.md) |
| Upward covering panels retaining keywords | [Stacked panels](references/stacked-panels.md) |
| Diagrams within slides | [Diagrams](references/diagrams.md) |
| Editor, drafts, or export | [Editing and saving](references/editing-and-sharing.md) |
| Requested hosting or protected sharing | [Hosting](references/hosting.md) |

The [HTML gallery](assets/pattern-gallery.html) is optional implementation material. Inspect only relevant portions when useful; do not load every reference or the gallery by default. Keep private presets outside this public skill and its releases.

## Verify and deliver locally

Inspect distinct layouts and the longest content at desktop, shorter laptop, and mobile sizes. Check navigation/history, staged reveals, rapid switching, final metric values, reduced motion, fonts/assets, and actual color contrast. Exercise representative edits, reordering, draft reload, and reopening/re-editing an export. Report concrete verification limits.

Deliver local HTML/source/assets with editing and saving instructions. Use a loopback-only localhost preview when useful. Remote projects, repositories, deployments, tunnels, and shareable links require a user request; discussing sharing options alone is insufficient. Honor the chosen host when requested and follow its workflow. State only features actually implemented. Updating this skill does not require creating or deploying a deck.
