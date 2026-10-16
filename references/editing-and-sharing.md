# Editing and local saving

Read for editors, drafts, and export. Deliver locally by default; preview through loopback-only localhost when useful. Localhost runs on the user's machine, not a sharing service. Read [hosting](hosting.md) only when remote delivery, collaboration, or access control is requested.

## Model and editor

Use a versioned model with stable slide IDs; separate content/theme/assets/layout/motion from transient animation/selection/dialog state. Render from the model and write edits back to it. Keep meaningful text/numbers outside flattened media and retain replaceable asset references.

Use plain text for ordinary fields. Treat imports/pasted content as data; never evaluate imported JavaScript or insert arbitrary HTML. Sanitize explicitly supported rich text.

Keep presentation/edit modes distinct. Expose independent sidebar labels when needed. Duplication creates IDs, reordering preserves them, and deletion selects a valid remaining slide; keep hashes/navigation synchronized. Provide reversible drafts/undo where practical. Routine editing does not imply a freeform canvas.

## Saving modes

| Mode | Contract |
| --- | --- |
| Browser draft | localStorage/IndexedDB, deck-specific key and schema. Handle quota/storage failures visibly. Stays in that profile/origin; file-URL behavior is not portable. |
| Portable export | Complete HTML or HTML/assets package plus current editable model. Reopen with latest content/theme/assets and continued editing. JSON alone is a backup, not the presentation. |
| Hosted updates | Only if requested; use authenticated persistence/publishing per [hosting](hosting.md). Browser storage does not update the hosted file or another device. |

Label controls precisely, e.g. “Save draft in this browser” and “Download updated deck.” Avoid a backend for local editing/re-export.

## Export

Serialize the current model into a known template, not transient animated DOM. Escape `<` in embedded JSON so `</script>` cannot end its script block. Preserve final metric targets, not intermediate counters; exclude selection wrappers, open editor state, measurement nodes, and unrelated drafts.

Package assets/dependencies for promised offline use; replace temporary blob URLs. Reopen the export and edit it again. State where files/edits live, how to preview/download, and any concrete unimplemented behavior. Hosted publishing/access instructions belong only in a requested hosting workflow.
