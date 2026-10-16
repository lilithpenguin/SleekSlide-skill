---
name: sleekslide
description: "Plan, create, or edit interactive HTML presentation decks with a contents sidebar, one screen per slide, reusable motion, and an editing mode for routine content changes. Use for browser-based pitch decks, product presentations, and animated HTML slides. Keep ordinary websites, native Figma decks, PPTX authoring, and video production in their own workflows."
---

# SleekSlide

Build a presentation the user can present, navigate, and update without editing code. Defaults reflect this user's preferences: a contents sidebar, one screen per slide, selective rich interaction, and editable text and numbers. Explicit instructions and an existing deck's conventions take precedence.

## Brief and theme

Use the conversation and supplied materials to establish the subject, audience, required content, and slide count. Ask only for missing information that materially affects the result. Do not invent company metrics or product capabilities. Keep requested slide counts, including the cover.

Fonts and colors are optional inputs, not prerequisites. In order of preference, use supplied brand guidelines, the existing product's design language, an explicitly selected reference, or a coherent theme chosen for the subject. A request to borrow interactions does not imply copying a reference's branding.

Centralize typography, spacing, and named color roles in one theme configuration and CSS custom properties. Include background, foreground, muted text, accent, border, and inverse colors. Provide a font fallback stack and verify actual font loading and language coverage before measuring layouts. Use legitimately supplied or available fonts. Variable-font effects are optional and depend on the selected font's actual axes; they must not dictate the font choice. Theme changes should not require editing each slide.

## Plan before building

Before writing presentation code for a new deck or substantially restructuring an existing deck, share a numbered text rundown covering every slide, including the cover. Describe each slide's main message and source content, its composition in plain spatial terms, and the interaction to use and why it helps. State explicitly when a slide only needs a simple reveal or no animation. Include relevant editable values and distinguish illustrative examples from real product behavior or evidence.

Keep the rundown concise enough to review: usually two to four sentences per slide, with content and interaction clearly identifiable. Summarize the intended theme and navigation once rather than repeating them for every slide. Identify material assumptions or missing sources. Do not replace this step with a generic implementation checklist or keep the plan only in private reasoning.

Share the rundown before moving into implementation. Then proceed within the authorized scope unless the user requested a plan-only response or a chance to review or approve it first. Do not add a routine approval gate. For a bounded edit, state the affected slides or shared controls and the intended change; a full deck plan is unnecessary.

## Choose a small technical foundation

For a new standalone deck, prefer semantic HTML, CSS, and JavaScript. Keep an existing application's framework when integrating. React, Tailwind, and a build tool are not prerequisites.

Use CSS transitions or the Web Animations API for simple fades, hover states, and short moves. Add GSAP core when the deck needs coordinated sequences, counters, or interactive interpolation. Prefer one motion controller for each animated property rather than overlapping CSS and JavaScript animations. Keep animation dependencies local to the deliverable when portable/offline use is requested.

Drive motion from entering or advancing a slide. ScrollTrigger is optional for an explicitly requested scrolling story; long pinned scroll sequences are a poor default for a one-screen slide deck. Lottie is optional for a supplied or purpose-built illustration, not a dependency for normal text, counters, charts, or navigation. Read [interaction patterns](references/interaction-patterns.md) when choosing effects or adapting the reference sites.

Use applicable installed presentation and website/hosting skills for their specialized workflows when relevant. Honor the requested local-file, existing-website, or hosted destination. This skill does not itself authorize publishing, changing access, or sending material to an external service.

## Screen and navigation contract

- Keep the presentation stage within the available viewport beside the sidebar, with one slide visible and no internal vertical scrolling at the intended desktop presentation sizes. Use dynamic viewport units where appropriate and reserve space for navigation controls.
- Use responsive layout and bounded type sizes. Inspect long content and short laptop viewports. If content overflows, improve composition or shorten it with the user's meaning intact. Do not conceal content with clipping or shrink the entire slide until text becomes unreadable. Add slides only when the requested count permits it.
- Give slides stable IDs independent of order. Generate the contents sidebar and any active markers, progress indicators, or counters from the same slide model. Keep URL links and browser back/forward synchronized without replay loops.
- Use one presentation control bar alongside the contents sidebar. Combine previous/next, replay, editing, fullscreen, and the mobile contents toggle there as applicable. Do not create separate top and bottom bars for the same navigation. Keep titles, section labels, brand identity, and active-slide context in the sidebar rather than repeating them in the control bar. Add a progress or count display only when it contributes information that the sidebar does not already convey.
- Provide previous/next buttons and keyboard navigation. Arrow and space shortcuts must not steal input from text fields, sliders, editable regions, dialogs, or the editor. If a slide has staged reveals, finish its intended sequence before advancing.
- On small screens, collapse the contents sidebar and recompose the slide. Preserve readable content and reachable controls. Explicitly explain any mobile reading/scrolling fallback if full-screen fit cannot coexist with the required content; do not silently crop or make text tiny.

## Editable source and editor

Separate content, theme, slide layout, and motion settings. Keep headings and paragraphs as real text, required chart values as data, and labels outside flattened illustration assets. A useful slide model includes a stable ID, section/title, layout name, content fields, and optional motion settings.

Include an unobtrusive edit mode for new decks unless the user opts out or an existing editing system already provides it. Support editing text, sidebar labels, and numeric targets without code. For multi-slide decks, support duplicate, delete, and reorder through understandable controls. Keep timing and image replacement configurable when those features are present. Do not promise a freeform Figma-like canvas unless implementing it was requested.

Editing must update the underlying model, not only the rendered DOM. Preserve stable IDs and meaningful sidebar links after reordering or duplication. Freeze presentation effects during editing so counters and text animations do not overwrite user input. Provide a static final state and a separate preview action.

Read [editing and sharing](references/editing-and-sharing.md) before implementing saving, downloadable decks, remote persistence, or password protection. Distinguish browser-local drafts, portable export, and server-persisted changes in both implementation and handoff.

## Motion and interaction

Choose effects for their explanatory value and maintainability. Useful defaults are short section/title reveals, metric count-ups, chart reveals, restrained state transitions, and a bounded product control such as a slider or toggle when it helps explain the content. Keep a clear hierarchy instead of animating everything simultaneously.

Treat settings such as start/target values, numeric formatting, duration, delay, and replay policy as data. Reusable layouts should still work after wording or values change. Leave the real final text available to assistive technology when using split letters or scrambling. Use tabular figures for changing metrics when supported.

Manage active-slide animation lifecycles: stop outgoing timelines, cancel stale callbacks, and reset or resume deliberately on re-entry. Pause offscreen decorative loops. Never let hidden slides or background timers modify the active slide's values. Under reduced-motion preferences, show final states and retain all content and controls. Hover interactions need a touch and keyboard alternative.

## Validate and deliver

Use browser tooling available in the environment to inspect representative slides at a normal desktop size, a shorter laptop viewport, and a mobile size. Report concrete verification limits when tooling is unavailable. Check the longest slide and every distinct layout for readable fit, not just the cover.

Exercise navigation, staged sequences, URL/back behavior, and controls. Edit a heading and numeric target, reorder a slide, reload a saved draft, and reopen an exported result to verify persistence and continued editability. Check final counter values, fast slide switching, reduced-motion behavior, and any image/font dependencies. When access control is requested, verify denied access for the deck data and assets as well as the visible page.

Deliver the usable result and editable source in the requested format, with a concise explanation of editing and saving. State which sharing/access features actually exist. Preserve project conventions for existing work. Skill creation alone does not require making or deploying an example deck.
