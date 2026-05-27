---
pattern: preferences-list
tags: settings, list, form, layout
---

# Preferences List

A full-page settings/preferences screen organized as titled sections of horizontally laid-out rows, each row pairing a label + description on the left with a compact control (dropdown, toggle, or link button) on the right.

## Layout & Structure

- Single-column centered page on a light neutral background. Content column is ~640–720px wide, centered, with comfortable left/right margins.
- Top-level page title "Preferences" sits flush-left at the top of the column, no breadcrumb, no back arrow — this is a destination page.
- Content is grouped into sections, each with:
  - A small section header ("General", "Interface and theme") above
  - A single rounded white "card" containing all rows for that section, with internal hairline dividers between rows (no outer-most divider above the first or below the last row inside the card).
- Each row is a horizontal flex layout: left side stacked (label + description), right side a single control aligned to the vertical center.
- Generous vertical gap between sections so the eye treats them as distinct groupings.

## Spacing & Sizing

- Page top padding: ~64px from viewport top to "Preferences" title.
- Title to first section header: ~32px.
- Section header to its card: ~12px.
- Section-to-section gap (bottom of one card to top of next section header): ~48–56px.
- Card corner radius: ~10–12px.
- Row height: ~64–72px (taller than a typical list row because each row carries a two-line label+description on the left).
- Row horizontal padding: ~20px left and right.
- Row vertical padding: ~14–16px top and bottom.
- Internal divider between rows: 1px hairline, inset to align with the row's content (or full-bleed — both read clean; this design uses full-bleed inside the card).
- Label-to-description vertical gap: ~4px.
- Control sizing on the right:
  - Dropdown pill: ~28–30px tall, ~10–12px horizontal padding, ~6–8px radius, with a small chevron 6–8px from the right edge.
  - Toggle switch: ~28px wide × 16px tall track, ~12px circular knob.
  - Plain text action ("Customize"): no button chrome, just colored/weighted text.
- Card max-width matches the content column width; cards are never full-bleed to the viewport.

## Typography

- Page title "Preferences": ~28–32px, semibold, near-black.
- Section header ("General", "Interface and theme"): ~15–16px, semibold, near-black. Sits outside/above the card.
- Row label: 14px, medium weight, near-black.
- Row description: 13px, regular, mid-gray (~#6B7280). Single line, truncates if too long.
- Dropdown current value: 13px, medium, near-black.
- Toggle has no inline label — its meaning comes entirely from the row's left side.
- Plain text action ("Customize"): 13–14px, medium, near-black (no underline, no accent color — relies on hover for affordance).
- Keyboard shortcut display inside dropdown ("⌘+Enter"): same 13px medium, using the platform symbol glyph rather than spelled-out "Cmd".

## Colors & Surfaces

- Page background: very light warm gray (~#F5F5F3), nearly off-white.
- Card surface: pure white (#FFFFFF).
- Card border: either no border, or an ultra-faint 1px (~#ECECEC) — the lift comes from the surface contrast against the page bg, not from a stroke or shadow.
- Row dividers: 1px ~#EFEFEF, full-bleed across the card.
- Toggle (on): solid blue (~#3B82F6 / similar saturated mid-blue) — this is the ONLY accent color on the page; everything else is neutral.
- Toggle (off): light gray track (~#E5E7EB) with white knob.
- Dropdown background: white with a 1px light gray border (~#E5E7EB), darkens slightly on hover.
- Text: primary ~#111, secondary ~#6B7280.

## Interaction & Behaviour

- Dropdowns open a small popover menu directly below the trigger, matching its width or slightly wider, with the current value checkmarked.
- Toggles flip immediately on click with no confirmation; state persists optimistically.
- "Customize" text actions open a deeper configuration surface (likely a modal or drawer) — they read as "this row has more inside it" vs. the inline controls.
- Row hover: very subtle background tint (~#FAFAFA) across the full row width, or no hover at all on rows whose control is a toggle/dropdown (the control itself shows the hover state).
- Clicking anywhere on a row should activate its control where reasonable (especially for toggles) — extend the hit target across the whole row.
- Keyboard: Tab moves between controls; Space toggles switches; Enter/Space opens dropdowns; arrow keys navigate dropdown items.

## Animation

- Toggle animation: knob slides ~12px horizontally over ~150ms with an ease-out curve; track color cross-fades in the same window.
- Dropdown popover: fades + scales from ~0.97 to 1.0 from the top edge, ~120–150ms ease-out. Closes with a faster ~80ms fade.
- Row hover: background tint fades in over ~80ms; no transform.
- No section-level animations — the page is static; only individual controls move.

## Key Principles

- The combination of "section header outside the card" + "rounded white card containing rows" is the load-bearing pattern. The header sits in the page background, not on the card surface — preserve this separation; never put the section title inside the card.
- Each row is a label + description pair on the left, control on the right, vertically centered as a group. The description is never optional ornament — it tells you what the setting changes in plain language and is part of what makes the page feel calm and self-explanatory.
- Use exactly one accent color (blue) reserved for "on" toggle states. Every other interactive element is neutral. This is what keeps a dense settings page from feeling busy.
- Controls vary by row but all sit on the same right-edge gridline — the right edge of every dropdown, toggle, and text action aligns vertically down the card. This invisible alignment is what makes the list feel engineered rather than ad-hoc.
- Row height should breathe (64–72px) because of the two-line left side. Don't compress it to typical menu-row height (32–40px); the description needs the air.
