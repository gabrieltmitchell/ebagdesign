---
pattern: dropdown-menu
tags: overlay, navigation, input, menu
---

# Dropdown Menu

A floating panel of selectable actions or destinations, anchored to a trigger, used for navigation switching (Variant A) or contextual actions on an object (Variant B).

## Layout & Structure

- Vertically stacked list of items inside a rounded rectangular surface, anchored just below (or beside) its trigger with a small gap (~4–6px).
- Surface is a single column; items span the full inner width.
- Items are grouped using thin horizontal divider lines that span edge-to-edge inside the panel, optionally with a small uppercase section label introducing a group (Variant A: "Favorited Views").
- Variant A (navigation switcher): text-only rows, one trailing checkmark on the active row, no icons, no shortcuts. Use when the menu represents mutually exclusive destinations or a current selection.
- Variant B (action menu): each row has a leading 16px monochrome icon, the action label, and a right-aligned meta column for keyboard shortcuts or a submenu chevron (▸). Use when the menu represents actions performed on a target object.
- Right-edge meta column in Variant B is right-aligned and vertically centered; shortcuts render as faint glyphs (⌘, ⇧, ⌥, "Ctrl") followed by the key, with consistent spacing between modifier and key.
- Submenu indicator is a small filled right-pointing triangle at the far right edge, replacing or following the shortcut.

## Spacing & Sizing

- Panel width: ~220–260px (Variant A, tighter) to ~300–340px (Variant B, wider to fit shortcuts). Width is content-driven, not fixed — sized to the longest row plus padding.
- Panel inner padding: ~6–8px top/bottom, ~6px left/right (items get their own horizontal padding so they can extend to the panel edges minus a small inset).
- Item height: ~34–38px. Tall enough to feel comfortable on a trackpad but compact enough that 8–10 items read as a single object.
- Item horizontal padding: ~12px left, ~12px right. Items sit inset from the panel edge by ~4–6px so the hover/active pill has visible breathing room on both sides.
- Vertical gap between items: 0 (rows are flush); separation comes from row height and dividers, not gaps.
- Icon-to-label gap (Variant B): ~10–12px. Icons are 16px square, optically aligned with the cap height of the label.
- Label-to-shortcut gap: a flexible spacer — shortcuts always pin to the right edge of the row.
- Group divider: 1px hairline, full inner width, with ~6–8px of vertical breathing room on each side.
- Section label (Variant A "Favorited Views"): ~13px, uppercase or sentence case, with ~12px top padding and ~4px bottom padding before the first item under it.
- Corner radius of panel: ~10–12px (noticeably rounded but not pill-soft).
- Corner radius of hover/active pill: ~6–8px, smaller than the panel itself.

## Typography

- Item label: ~14–15px, regular weight (400–450), near-black on light surface.
- Section label / group header: ~12–13px, medium weight (500), muted gray (~50–60% black).
- Keyboard shortcut text: ~12–13px, regular weight, muted gray. Modifier glyphs (⌘ ⇧ ⌥ ⌃) render in the same color and weight as the key character.
- Line-height inside items is tight (~1.2) — the row height does the spacing work, not leading.
- All text is left-aligned within its column; no centering anywhere except inside icon bounds.
- Truncation: long labels truncate with an ellipsis ("Make recurring…", "Add customer request…") rather than wrapping. Trailing ellipsis is part of the label string itself when it indicates a follow-on dialog.

## Colors & Surfaces

- Panel background: pure white or very near-white (~#FFFFFF to #FCFCFC).
- Panel border: 1px hairline at ~6–8% black, OR no visible border with a soft elevation shadow doing the lifting (Variant B leans on shadow more than border).
- Shadow: a layered drop shadow — a tight 1px shadow at ~8% black for crispness plus a softer ~20–30px blur at ~6–10% black offset down by ~8–12px. The result reads as "floating just above the page," not "deep modal."
- Hover / active item background: very light neutral gray (~#F4F4F5 / 4–6% black). No color tint, no border on the highlight — just a flat fill.
- Active/selected text color: same as default text — selection is communicated by background fill and (in Variant A) the trailing checkmark glyph, not by changing the text color.
- Icons (Variant B): single-weight line icons, ~1.5px stroke, in a mid-gray (~50% black). They do not change color on hover — only the row background changes.
- Dividers and section labels share a muted gray so the eye groups them as "structural, not interactive."
- Behind the menu: the page beneath remains fully visible and un-dimmed. No scrim, no backdrop blur. The shadow alone separates the menu from content.

## Interaction & Behaviour

- Triggered by clicking a trigger control (a button, a "more" affordance like the three-dot icon in Variant B, or a header label in Variant A). Also openable via keyboard focus + Enter/Space.
- Anchored to its trigger. Panel opens below by default; if there is not enough room below, it flips above. Horizontal alignment matches the trigger's leading edge unless that would clip — then it snaps to the opposite edge.
- One item shows hover state at a time. Moving the pointer or pressing arrow keys moves the highlight; the highlight is the same visual in both cases (a coding agent should not style keyboard focus differently from pointer hover).
- Dismissal: click outside, press Escape, select an item, or Tab away. Selecting an item closes the menu immediately (no animation delay).
- Variant A behavior: selecting an item navigates and persists the selection — the next time the menu opens, the new row carries the checkmark.
- Variant B behavior: rows with a trailing "…" open a follow-up dialog; rows with a trailing ▸ open a submenu to the side, which inherits the same visual treatment.
- Submenus open to the right with a small overlap on the parent panel's edge so the connection reads clearly. Hovering the parent row should open the submenu after a short hover delay (~120–180ms) to avoid accidental opens while traversing.
- Keyboard: Up/Down moves between items (skipping dividers and section labels), Enter activates, Right opens a submenu, Left closes the submenu and returns focus to the parent row, Escape closes the whole stack.
- Shortcuts shown on the right are live — pressing them while the menu is open (or even with it closed, if global) fires the action.

## Animation

- Enter: ~120–160ms ease-out. Two things move together — opacity 0→1 and a small Y translate of ~4–6px from above the resting position down into place. A very subtle scale (0.98→1) anchored to the trigger edge can be layered in, but it should be barely perceptible.
- Exit: ~80–100ms ease-in, opacity to 0 with the same small Y translate reversed. Exit is noticeably faster than enter — the menu should feel like it gets out of the way.
- Hover state on items: instant, no transition. A 50–80ms background fade is acceptable but anything longer makes the menu feel laggy when scrubbing through items with the pointer.
- Submenu open: same enter animation, but translated from the parent row's edge rather than from the trigger.
- No bounce, no spring overshoot. The motion language is "crisp and quiet" — this is a utility surface, not a hero element.
- Respect prefers-reduced-motion: drop the translate, keep only the opacity fade.

## Key Principles

- Selection vs. action is communicated by structure, not color. Variant A uses a trailing checkmark on text-only rows; Variant B uses leading icons and trailing shortcuts. Mixing the two languages in one menu muddies the model — pick one per surface.
- The hover/active pill is inset from the panel edge and uses a flat neutral gray, never a brand tint. This keeps the menu feeling like a tool rather than a decision-point, and lets the actual content (labels, icons, shortcuts) carry the weight.
- Width is content-driven and shortcuts pin right. Never center a label, never let the shortcut column float in the middle — the right-edge alignment is what makes a menu scan as "tabular and trustworthy" instead of "list of buttons."
- Elevation comes from a soft, layered shadow on a near-white surface — not from a heavy border or a backdrop dim. The page behind stays visible because dropdowns are transient, not modal.
- Section labels and dividers exist to chunk the list into ~3–6 item groups. If the menu has more than ~10 items with no grouping, it is the wrong pattern — reach for a command palette or a sub-navigation instead.
- Animation duration asymmetry (slower in, faster out) is small but load-bearing for feel. Equal-duration in/out animations read as "sluggish on dismiss."
