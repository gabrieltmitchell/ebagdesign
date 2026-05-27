---
pattern: gallery-layout
tags: [layout, navigation, sidebar, grid, cards]
---

# Sidebar + Gallery Tile Layout

A two-pane workspace layout: a narrow, dense navigation sidebar paired with a generous main area that displays content as a row of large preview tiles.

## Layout & Structure

- Two columns, fixed-width sidebar on the left + flexible main area on the right
- Sidebar width: ~220–240px, full viewport height, separated from the main area by a single hairline vertical divider
- Sidebar internal structure (top to bottom):
  1. Workspace switcher with logo mark + workspace name + chevron (dropdown affordance)
  2. Search input (full-width, filled neutral background)
  3. Grouped nav sections, each with a small uppercase-ish label and a list of items
  4. Bottom-pinned utility row with two buttons ("invite teammates" + "copy link" style)
- Main area internal structure:
  1. Top bar: large page title on the left, filter dropdown + primary CTA on the right
  2. Content region: horizontal row of 3 preview tiles, equal width, equal gaps
  3. Below tiles: empty vertical space — the grid does not stretch to fill height

## Spacing & Sizing

- Sidebar internal padding: ~12–16px horizontal, ~12px vertical between groups
- Sidebar list items: ~28–32px tall, ~6–8px vertical padding, full clickable row
- Gap between sidebar groups: a thin divider line + ~16–20px vertical breathing room
- Main area padding: ~32–40px on all sides; top padding tighter, bottom open
- Tile grid: 3 columns, equal-width tiles, gap between tiles ~24–28px
- Tile aspect ratio: roughly 4:5 (portrait), preview surface taller than wide
- Tile preview height: ~280–320px on a desktop viewport
- Below-tile metadata block: ~48–56px tall, sits flush-left under the tile with no card chrome around it
- Top bar height: ~56–64px, vertically centered title and right-side controls

## Typography

- Workspace name (sidebar header): ~14px, medium weight, near-black
- Section labels in sidebar ("Domains", "Projects"): ~12–13px, semibold, slightly darker neutral, generous letter-spacing feel
- Sidebar item labels: ~13–14px, regular weight
- Sidebar item count badges (right-aligned numbers): ~12px, light gray, regular
- Main area page title ("All"): ~22–26px, semibold, near-black
- Filter dropdown label: ~13–14px regular
- Primary CTA button label: ~13–14px medium, white on filled background
- Tile title (below preview): ~15–16px, medium/semibold, near-black
- Tile subtitle ("Viewed Xh ago"): ~13px, regular, medium gray
- Tile status tag (e.g. "BASIC", "PRO", "FREE"): ~11–12px, bold, all caps, accent color (blue) — sits to the right of the subtitle

## Colors & Surfaces

- App background: very light gray / off-white (~#FAFAFA)
- Sidebar background: same as app background OR a touch lighter — no strong contrast, separation is via divider line only
- Main area background: white or same off-white as sidebar — the divide is purely structural, not tonal
- Hairline dividers: 1px, very light gray (~#EAEAEA), used for sidebar/main split and between sidebar groups
- Search input: filled with a soft neutral (~#F0F0F2), no border, rounded ~8px
- Tile preview surface: each tile has its own background color drawn from its content (dark navy, warm cream, light gray) — tiles are NOT uniformly white; they take on the personality of their preview
- Tile corners: rounded ~10–12px
- Tile shadow: none or extremely subtle — separation is via gap + the colored preview itself
- No outer card border around the preview; the colored fill IS the card
- Primary CTA: solid blue/indigo fill (~#3D63F5 feel), white text, rounded ~8px, ~32–36px tall
- Filter dropdown: white fill, 1px light border, rounded ~8px, chevron on the right

## Interaction & Behaviour

- Sidebar items: full-row hit area; hover applies a light gray background fill, active/selected state uses a slightly darker fill plus an icon shift (e.g. filled vs outline)
- "All" item in Projects appears selected — selection is shown by a subtle filled background, not a left border or accent bar
- Workspace switcher chevron and filter dropdown both open menus on click
- Tiles are clickable as a whole (entire tile + metadata block is one target); hovering likely raises a very subtle shadow or shifts the cursor only
- Tile preview content (the inner artwork) is non-interactive decoration — clicks go to the project
- Status tags ("BASIC", "PRO", "FREE") are display-only labels, not interactive
- Search filters the sidebar lists in place (does not navigate)
- Bottom-pinned utility row stays fixed to sidebar bottom regardless of scroll

## Animation

- Hover transitions on sidebar items: ~120–150ms ease, background-color only
- Tile hover: subtle and optional — at most a 1–2px lift or a very faint shadow fade-in over ~150ms; no scale, no rotation
- Dropdown menus open with a quick fade + 4–8px downward translate, ~150ms
- No skeleton shimmer visible — tiles likely fade in on load
- Sidebar selection change is instant on the indicator, with the hover-bg crossfade providing the smoothness

## Key Principles

- Tiles ARE the cards — there is no outer card chrome wrapping the preview and metadata. The colored preview surface provides containment; the metadata sits naked below it. This is what makes the gallery feel like a portfolio rather than a dashboard.
- Tonal restraint in the chrome lets the content tiles carry all the color. Sidebar, dividers, and main background sit in a tight neutral range so the varied tile backgrounds pop.
- Sidebar uses density without clutter: small type, tight row heights, light dividers, and right-aligned count badges keep a lot of information legible in a narrow column.
- Generous bottom whitespace below the tile row signals "this is a gallery, scroll for more if there's more" without forcing the grid to fill the viewport — content dictates height, not the layout.
- Selection and grouping in the sidebar rely on filled backgrounds and dividers, never on accent-colored left borders or rails — keeping the visual vocabulary calm.
- The single primary CTA (top-right, solid color) is the only saturated UI element above the fold; everything else defers to it and to the tile artwork.
