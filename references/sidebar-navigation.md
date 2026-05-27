---
pattern: sidebar-navigation
tags: navigation, layout, sidebar
---

# Sidebar Navigation

A compact, icon-and-text sidebar for product navigation. Feels dense without being cramped — items are small and close together, giving the impression of a professional tool rather than a consumer app.

## Layout & Structure

- Fixed width, approximately 240px
- White background, separated from the main content by a single 1px light grey border (no shadow)
- Top bar: workspace selector on the left (logo + name + chevron), icon actions on the far right (search, compose — ~18px icons)
- Nav items organized into labeled sections (section labels are small, grey, lowercase or sentence case)
- Items are left-aligned with a small icon (16px) followed by text
- Nested items indented ~12–16px with smaller icons, sometimes with secondary indicators (lock icon, expand arrow) on the right
- Bottom of sidebar: a persistent utility item (e.g. help) at the very bottom left, small and unobtrusive

## Spacing & Sizing

- Nav item height: approximately 28–30px (very tight)
- Vertical gap between items: 0–2px — items are nearly flush
- Section label margin-top: ~16px to create breathing room between groups
- Icon size: 16px for primary nav, 14px for nested items
- Left padding on items: ~12px
- Right padding: ~8px

## Typography

- Nav item text: 13px, regular weight (400)
- Section labels: 11–12px, medium weight (500), grey (`#9CA3AF`)
- Badge counts (e.g. inbox count): 11px, grey pill, no background fill — just text

## Colors & Surfaces

- Sidebar background: white (`#FFFFFF`)
- Hovered item: very light grey background (`#F3F4F6`), rounded (`rounded-md`)
- Active/selected item: slightly darker light grey (`#E5E7EB`), same rounding
- Section label color: `#9CA3AF` (light grey)
- Icon color: `#6B7280` (medium grey), slightly darker on active
- No colored accents in the nav — everything is grey-scale

## Interaction & Behaviour

- Hover reveals background immediately (no delay)
- Collapsible sections toggle with a chevron — chevron rotates on open/close
- Nested items revealed on parent expand, not on hover
- Badge counts are static — no animation on update needed unless real-time

## Animation

- Section expand/collapse: smooth height animation with `AnimatePresence` + `layout`
- Chevron rotates 90° on expand
- No dramatic entrance animations — sidebar is persistent, not a drawer

## Key Principles

- Items feel like a list of text links, not styled buttons — the background only appears on hover/active, not by default
- The tightness of the spacing is intentional — it communicates density of functionality, like a pro tool
- Icon and text are treated as a single unit — consistent left alignment creates a clean vertical rhythm
- Nested items feel subordinate through indentation + smaller icons, not through color or opacity changes
