# Editing, persistence, and protected sharing

Read before implementing the deck's editor, saving/export, or a protected link.

## Content ownership and model

Use a versioned deck model with stable slide IDs. Keep theme tokens, content fields, chart data, asset references, and per-slide animation settings distinct. Render from this model; write editor changes back to it. Store transient animation progress, selected elements, and open dialogs separately from the saved content.

Ordinary fields should use plain text. Treat imported JSON, pasted content, titles, and asset references as data. Do not evaluate imported JavaScript or blindly insert arbitrary HTML. If limited rich text is required, define its supported structure and sanitize it consistently.

Provide an understandable distinction between presentation mode and edit mode. Changing a title should update the contents label when they share the same field. If navigation labels differ intentionally, expose both. Duplicating a slide creates new IDs; reordering preserves IDs. Deleting a slide selects a sensible remaining slide and keeps hashes/navigation valid. Preserve an undo path or a reversible draft for destructive editing actions where practical.

For slide-level illustration and screenshots, retain references to replaceable assets. Keep meaningful text and numbers outside a raster image or pre-rendered animation whenever routine editing is expected. Freeform layout authoring is additional scope, not implied by an edit mode.

## Three kinds of saving

1. **Browser-local draft:** Save the model to localStorage or IndexedDB with a deck-specific key and schema version. Handle unavailable storage and quota failures visibly. A browser draft stays in that browser/profile/origin; it does not update the hosted deck or another device. Do not rely on file-URL storage behavior for portability.
2. **Portable export:** Export a complete HTML file or an HTML-and-assets package plus the editable content model. JSON export/import is useful for backup, but JSON alone is not the finished presentation. Reopening an exported deck must reproduce the latest edits, theme, and assets. If single-file offline output is promised, include its runtime dependencies and local images/fonts appropriately. Do not call the original static file 'updated' after merely writing browser storage.
3. **Hosted editing:** Persist through an authenticated backend or the host's supported publishing workflow. An edit saved in the browser only is not a publication. Handle validation, revisions or concurrent edits, failed saves, and durable asset storage in proportion to the requested collaboration features. Avoid introducing a backend for a deck that only needs local editing and re-export.

Choose a model that fits the requested hosting and editing workflow, and label its controls precisely, such as 'Save draft in this browser' and 'Download updated deck'.

## Export correctness

Serialize current model data safely. If embedding JSON in an HTML script block, escape characters such as `<` so user text containing `</script>` cannot terminate the block. Prefer serializing a model into a known template over copying transient animated DOM. Preserve genuine target values rather than a counter's intermediate display.

Avoid exporting stale content, temporary text-selection wrappers, hidden measurement nodes, animation progress, browser drafts from another deck, or a visibly open editor. Keep editing capability available in the exported source if promised, with presentation view as the initial state. Verify an exported copy by reopening it and editing again. Package local assets rather than retaining temporary blob URLs.

## Viewer and editor access

A public static file can be downloaded, and a hidden editor button is not an authorization boundary. If viewers must be unable to change the canonical hosted deck, enforce write permissions on the server and give the owner separate authenticated access. Explain that a recipient can still modify their own downloaded copy.

For protected viewing, use hosting/server/edge authentication over HTTPS before sending the private deck, JSON, images, videos, and other private assets. A password comparison inside downloadable HTML/JavaScript is not access control. Do not embed shared passwords, backend credentials, or authentication secrets in the deck or its source. Collect secrets through the host's supported secret mechanism.

Scope protection to the intended path or subdomain and its assets. Check alternate deployment/origin addresses and caches for bypasses when relevant. Use current provider documentation rather than assuming every plan supports the same controls. Examples of provider approaches include a host's shared-password feature, HTTP authentication on a server, or an identity gateway such as Cloudflare Access. Email-code/identity login is a different experience from a single shared password; do not substitute it silently.

Preserve the user's requested audience, host, and existing website. If the host is unknown and implementation depends on it, finish independent source work and ask for the host. Do not imply a password-protected URL exists until deployed and verified. For Sites or another installed hosting integration, follow that workflow's access and deployment requirements.

## Handoff

State where edits are saved, how to download or publish them, and who can view versus change the hosted version. If persistence, access controls, or browser verification remain unimplemented, describe that concrete limitation rather than presenting a mock control as functional.
