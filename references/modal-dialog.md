---
pattern: modal-dialog
tags: [overlay, dialog, settings, form]
---

# Modal Dialog

A centered, full-attention overlay panel for settings, multi-section forms, or workflows that need their own dedicated context. Use when the task is complex enough to warrant a sidebar of sub-sections but light enough not to deserve a full route.

## Layout & Structure

- Rounded rectangle, horizontally and vertically centered in the viewport
- Three-zone structure: top header bar, left vertical nav rail, right content pane
- Header spans full width and contains: title (far left), segmented tab control (centered), close icon (far right)
- Left rail is a fixed-width column with vertical list of section items, each with leading icon + label
- Right pane is the active section: stacked form groups separated by generous vertical whitespace, each group has a small label above its input row
- Selected nav item gets a subtle filled background; non-selected items are transparent
- Bottom of the content pane can host a muted helper sentence (e.g. empty state line) centered horizontally

## Spacing & Sizing

- Dialog width feels like ~640–720px, height auto-fits content with comfortable bottom padding
- Header bar height ~48–56px, separated from body by a hairline divider
- Left rail width ~180–200px, also separated from content by a hairline
- Nav item height ~32–36px, icon-to-label gap ~8px, internal horizontal padding ~10–12px
- Content pane padding ~24px top/right/bottom, ~28px from the rail edge
- Vertical gap between form groups (e.g. "Invite via Link" → "Invite via Email") ~28–32px
- Input rows are ~36–40px tall; trailing controls (role selector, refresh, primary button) sit inline at the same height
- Inline button group gap ~6–8px

## Typography

- Dialog title: ~15–16px, semibold, near-black
- Segmented tab labels: ~13px, medium weight; active tab has a thin rounded border + slightly stronger weight, inactive is muted gray
- Left nav labels: ~13–14px, medium weight, dark when selected, mid-gray when idle
- Section labels ("Invite via Link", "Invite via Email"): ~13–14px, semibold
- Input text and placeholders: ~13px, regular; placeholder is light gray
- Trailing inline meta (e.g. "Editor" role): ~12–13px, muted
- Empty state line: ~13px, regular, mid-gray, centered

## Colors & Surfaces

- Dialog surface: pure white
- Backdrop: page behind is visible but desaturated/dimmed — a soft scrim rather than a heavy black overlay; objects behind remain partially recognizable
- Dividers: 1px hairlines in a very light neutral (~#ECECEC / 6% black)
- Inputs: white fill with a 1px light-gray border, rounded ~6–8px corners
- Selected nav item: very light gray fill (~#F4F4F5), no border
- Active segmented tab: white fill with thin border in brand blue, label color shifts to near-black
- Primary button: saturated blue, white label, rounded ~6–8px, no shadow
- Secondary/icon buttons (refresh, close): square-ish, light gray fill on hover, no fill at rest
- No drop shadow on inputs or nav items; only the dialog itself carries a soft, diffuse shadow to lift it off the backdrop

## Interaction & Behaviour

- Opens from a settings/account trigger; dismisses via the top-right close icon, Escape key, or clicking the backdrop
- Left rail clicks swap the right pane content with no layout shift
- Segmented tabs in the header switch between top-level scopes (e.g. personal vs. shared) — independent from the left rail
- Focusing an input gives it a subtle ring in the brand color; no heavy glow
- Primary actions stay disabled-looking (lower opacity blue) until their input has content, then snap to full saturation
- Body scroll on the page behind is locked while open; focus is trapped inside the dialog
- Tab order: header tabs → left rail → content inputs → primary action → close

## Animation

- Enter: backdrop fades in (~150ms ease-out) while the dialog scales from ~96% to 100% and fades in simultaneously (~180–220ms, ease-out cubic)
- Exit: reverse, slightly faster (~120–150ms)
- Section swaps inside the dialog are instant or use a 80–100ms crossfade — never slide, to avoid drawing attention away from the content
- Nav item hover/selection transitions are ~120ms on background-color only
- No bouncing, no spring — the motion reads as crisp and utilitarian

## Key Principles

- Hairline dividers, not heavy borders — the structure should be felt, not seen
- The dialog earns elegance by keeping every surface flat: no nested shadows, no gradient fills, no busy iconography
- Header carries three responsibilities (identity, scope switch, dismiss) without any of them dominating — equal visual weight via spacing, not size
- Left rail items use icon + label with consistent icon stroke weight; selected state is a fill, never an underline or accent bar
- Empty states sit centered in the content area as a quiet helper line, not a full illustration — keeps the dialog from feeling sparse
