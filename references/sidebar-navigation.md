---
pattern: sidebar-navigation
tags: navigation, layout, sidebar, density
---

# Sidebar Navigation

A dense, mono-chrome sidebar for a productivity / project management tool. The whole point is that it reads like a structured outline of the product — sections, items, sub-items — rather than a styled menu. The lack of decoration is the design.

## Layout & Structure

- Fixed width ~220–240px, full viewport height
- Single 1px vertical hairline divider on the right edge (no shadow, no gradient) separates it from the content area
- Background is a very faintly warm off-white (`#FAFAFA`–`#F7F7F7`), one shade darker than the white chat surface to its right — this differentiation matters
- Vertical stack with no internal scroll bar visible; sections are stacked top-to-bottom:
  1. **Workspace header** (top): small square brand mark + workspace name + dropdown chevron on the left; two icon-only actions (search, compose/new) right-aligned
  2. **Pinned top-level items** (e.g. primary queue, personal view, activity feed) — no section label, sits directly under the header
  3. **Collapsible section groups** (Workspace, Favorites, Your teams) — each with a small label + chevron that toggles visibility
  4. **Team blocks** — each team is itself a collapsible parent with sub-items (channels/views) nested under it, often with a small lock or status glyph trailing
  5. **Footer item** ("Try" or similar) at the very bottom, dimmed and small
- A single inline badge (e.g. `67`) sits flush right on the same line as its item, no pill, no background — just dimmed numeric text
- Team rows use a tiny colored square favicon/avatar (~14px, rounded ~3px) instead of a line icon — this is the only chromatic element in the entire sidebar

## Spacing & Sizing

- Row height: **24–26px** (extremely tight — this is the signature)
- Vertical gap between rows: **0px** (rows are flush, only the text leading provides separation)
- Section label margin-top: **12–14px** above the label, **2–4px** between label and first item
- Left padding of items: **8px** from the sidebar edge
- Gap between icon and label: **8px**
- Icon size: **14–15px** stroke icons for top-level items; team color-square is **12–14px**
- Nested team sub-items are indented an extra **14–16px** from the team row
- Workspace header total height: ~36–40px, with ~8px vertical padding
- Right edge has a ~4–6px gutter before the divider so icons never crowd it

## Typography

- All nav item labels: **13px**, weight 400–450, color `#3F3F46`–`#52525B` (warm dark grey, not pure black)
- Workspace name in header: **13px**, weight 500–550, slightly darker than items
- Section labels ("Workspace", "Favorites", "Your teams"): **12px**, weight 450–500, color `#A1A1AA` (mid-grey), sentence case (not uppercase, not tracked) — they read as quiet headings, not screaming labels
- Item count badge: **12px**, weight 400, color `#A1A1AA`, no background
- Footer "Try": **12px**, color `#A1A1AA`
- Letter spacing: default / 0 — no tracking applied anywhere

## Colors & Surfaces

- Sidebar background: `#FAFAFA` (warm off-white)
- Divider: `#EAEAEA` 1px solid right border
- Text default: `#3F3F46`
- Text muted (sections, counts, footer): `#A1A1AA`
- Icon stroke: `#71717A` at rest, matches text on hover
- Hover background on a row: `#F0F0F0` / `rgba(0,0,0,0.04)`, rounded `4px`, inset by ~4px from the sidebar edges so it doesn't touch the divider
- Active/selected row: `#E8E8E8` / `rgba(0,0,0,0.06)`, same rounding and inset
- Team color squares are saturated but small enough to read as accents, not focal points (greens, blues, purples ~14px squares with rounded 3px corners)

## Interaction & Behaviour

- Hover background appears instantly (no transition delay), opacity transitions ~80ms ease-out
- Section labels are clickable — clicking the label OR the chevron collapses the whole group
- Chevron is a tiny **8–10px** triangle/caret, positioned to the right of the label, rotated 0° collapsed / 90° expanded
- Each team row is independently collapsible with its own chevron
- Trailing glyphs on team sub-items (lock icon, status dot) appear only when relevant; they're `#A1A1AA` and ~11px
- Search and compose icons in the header are buttons with no background until hover, then `#F0F0F0` circle
- Workspace name chevron opens a workspace switcher popover (see `sidebar-popover.md`)
- No tooltips on hover — labels are always visible, so tooltips would be redundant

## Animation

- Section expand/collapse uses height + opacity, **150–180ms** ease-out — fast enough to feel instant, slow enough to read as motion
- Chevron rotation matches the height animation duration so they feel mechanically linked
- No staggered child reveal — children fade in as a block, not one-by-one (staggering would feel slow at this density)
- No entrance animation on initial mount — the sidebar is persistent furniture, not a drawer

## Key Principles

- **Density is the brand.** 24–26px rows with 0px gaps signal "professional tool". If you space these out, it stops feeling like this product.
- **One accent surface, one accent type.** The only color in the sidebar is the small team-square avatars. Every other element is greyscale. Don't add status colors, gradients, or hover accents.
- **Hover/active states are inset, not full-bleed.** The selection background never touches the sidebar's right divider — it's a floating pill with ~4px horizontal margin. This is what makes the list feel composed rather than tabular.
- **Section labels are quiet, not loud.** They are NOT uppercase and NOT tracked. They sit just slightly heavier than the items they label, which is enough hierarchy at this density.
- **The sidebar background is warmer/darker than the main content.** That 1-shade difference is what gives the content area presence — don't make both surfaces the same white.
- **Trailing metadata (counts, locks) sits flush-right with no decoration.** Pills, badges with backgrounds, or colored numerics would shatter the calm.
