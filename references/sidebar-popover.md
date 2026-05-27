---
pattern: sidebar-popover
tags: navigation, overlay, popover, settings, menu
---

# Sidebar Popover (Settings / Navigation Drawer)

A full-height popover that slides over the existing sidebar to reveal a deep, categorized navigation tree — used for settings and other multi-section secondary navigation. It replaces the sidebar contextually rather than opening a separate modal.

## Layout & Structure

- Occupies the same column as the main sidebar (same left edge, same width ~240px), creating the illusion that the sidebar's *contents* swapped out rather than a panel opening on top
- Full viewport height; the right edge is a 1px hairline divider matching the main sidebar's divider
- The main canvas to the right is dimmed/desaturated slightly so the popover commands focus without being a hard modal
- Top of the popover: a **"Back to app" pill button** with a left-chevron icon — this is the primary affordance to dismiss
- Just below "Back to app": a **tooltip / keyboard hint chip** showing the label + `⌘` + `Esc` keys — this is part of the steady-state UI in this screenshot (likely surfaced on hover/focus of the back button, then auto-dismissed)
- Below that, a **flat scrollable list** of items grouped into labeled sections:
  - Personal/account group (Notifications, Security & access, Connected accounts, Agent personalization) — no visible section header above this group
  - **Issues** section — label, then items (Labels, Templates, SLAs)
  - **Projects** section — label, then items (Labels, Templates, Statuses, Updates)
  - **Features** section — label, then items (AI & Agents, Initiatives, Documents, Customer requests, Releases, Pulse, Asks, Emojis, Integrations)
- All items use a **line icon + text** pattern, identical structure to the main sidebar (consistency across layers)
- Items are flat (no nesting in this view) — depth is created by section labels, not indentation

## Spacing & Sizing

- "Back to app" pill: height **32px**, horizontal padding **14px** (left icon → 8px → label), corner radius full (pill / `rounded-full`), positioned with **12px top margin** and **12px left margin** from the popover edge
- Keyboard hint chip: height **28px**, padding `4px 8px`, corner radius **6px**, sits **4–6px below** the back button, slightly inset from the left edge — looks like a tooltip pinned in place
- The `⌘` and `Esc` keys inside the chip are individual **mini key caps** with **1px border**, **4px radius**, **~22×20px**, each with a tiny inset shadow — they read as physical keys
- Nav item row height: **32–34px** (slightly taller than the main sidebar's 24–26px to give a settings-context feel of "more space to breathe")
- Vertical gap between items: **2px**
- Section label: **14–16px top margin**, **6px bottom margin** before first item
- Icon size: **16px** (slightly larger than main sidebar's 14–15px)
- Icon-to-label gap: **10px**
- Left padding of items: **16px** from the popover edge

## Typography

- "Back to app" label: **14px**, weight 500, color `#18181B`
- Nav item labels: **15px**, weight 450, color `#27272A` — noticeably larger than main sidebar (13px) to signal a different mode
- Section labels ("Issues", "Projects", "Features"): **13px**, weight 500, color `#71717A`, sentence case, no tracking, no uppercase
- Keyboard hint chip label: **12px**, weight 450
- Key cap glyphs (`⌘`, `Esc`): **11px**, weight 500, centered

## Colors & Surfaces

- Popover background: pure white `#FFFFFF` (lighter than the main sidebar's `#FAFAFA`) — the slight color swap reinforces that this is a different surface
- Right edge divider: `#EAEAEA` 1px
- "Back to app" pill background: `#F0F0F0` (warm light grey), no border
- Keyboard hint chip: white `#FFFFFF` with a 1px `#E4E4E7` border, very faint shadow `0 1px 2px rgba(0,0,0,0.04)` — it floats above the popover
- Key cap fill: `#FAFAFA` with `#E4E4E7` border
- Icon stroke: `#52525B` at rest, `#18181B` on hover/active
- Hover row background: `#F4F4F5`, inset 8px from popover edges, radius **6px**
- No active/selected state is shown for items in this screenshot — when applied, use `#E8E8E8` with the same inset/radius

## Interaction & Behaviour

- Triggered by clicking a settings entry point (likely from the workspace dropdown in the main sidebar header)
- Replaces the sidebar's content in place — the workspace header is hidden while this is open
- Dismiss via:
  - Clicking "Back to app"
  - Pressing `⌘ + Esc` (the chip is teaching this shortcut)
  - Pressing `Esc` alone (likely also supported)
- The chip appearing pinned suggests it shows on first hover of the back button and persists for ~2–3 seconds, OR it's a permanent onboarding tooltip until dismissed
- Hover state on rows is identical to the main sidebar's pattern (inset pill background)
- The popover itself is scrollable internally when content exceeds viewport — scrollbar is overlay style, no visible track
- The main canvas to the right is non-interactive while open (pointer-events: none) but visible/faded, not blacked out — this is what differentiates this pattern from a modal

## Animation

- Enter: the popover slides in **from the left** by ~12–16px while fading from `opacity 0→1`, **220ms ease-out** — the main sidebar's content fades out underneath on the same timing so they feel like a crossfade in the same column
- Main canvas dim: opacity of canvas drops to ~60–70% over the same 220ms; no blur (a blur would be too heavy for this calm pattern)
- Exit: reverse — slide left **8px** + fade `1→0`, **180ms ease-in**, canvas brightens back simultaneously
- The keyboard hint chip enters with a slight delay (~150ms after the popover settles) and a tiny `y: -4→0` + fade — it's the last thing to arrive
- No spring physics — short, damped, calm

## Key Principles

- **It's not a modal, it's a sidebar mode-switch.** Stay in the same column, same width, same item vocabulary as the main sidebar. The user should feel they navigated *into* a section, not opened a new window.
- **Slightly larger rows + slightly larger type signal a different mental mode.** Settings ≠ navigation. Bumping rows from 24px → 32px and text from 13px → 15px gives a "stop and configure" feel without changing the visual language.
- **The keyboard shortcut chip is the premium touch.** Showing `⌘ + Esc` as real-looking key caps near the back button teaches power-user behavior without an onboarding tour. Don't omit this — it's a signature detail.
- **Section labels carry hierarchy alone.** No indentation, no dividers, no boxes — just generous top margin and a mid-grey label. The list stays flat and scannable.
- **The right canvas stays visible but quiet.** Dimming (not blurring, not overlaying) preserves spatial context — the user knows where they came from and can see they can return.
- **Icons match the main sidebar's icon family.** Line weight, corner style, and size step all read as the same set. Switching icon styles between sidebar modes would feel like two different apps.
- **The "Back to app" pill is the only filled control.** Everything else is text + icon. That single pill is what tells the eye "this is how you leave."
