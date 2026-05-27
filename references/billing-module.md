---
pattern: billing-settings-modal
tags: overlay, settings, billing, modal, two-pane
---

# Billing Settings Modal

A centered, two-pane modal dialog for managing account/workspace settings with a persistent left rail of sections and a right content pane that swaps based on selection.

## Layout & Structure

- Centered floating card overlay on a dimmed/blurred app background. The underlying app (sidebar + project grid) stays visible but de-emphasized.
- Modal is roughly 640px wide by 420px tall with generously rounded corners (~14–16px radius).
- Two-pane internal split:
  - Left rail: ~180px wide, light surface, holds the section list.
  - Right pane: fills the remainder, white surface, holds section content.
- Header strip spans the full modal width: title left-aligned, a segmented toggle (e.g. two top-level scopes) center-right, and a close (×) icon at the far right.
- A subtle hairline divider separates the header from the body and the two panes from each other.

## Spacing & Sizing

- Modal outer padding to viewport: centered with at least 80px of breathing room top/bottom.
- Header height: ~52px. Header horizontal padding: ~20px.
- Left rail item height: ~32px. Vertical gap between items: ~2px. Items have ~10px horizontal padding inset from the rail edge.
- Icon-to-label gap in nav items: ~10px. Icon size: 16px.
- Right pane padding: ~24px top, ~28px left/right, ~24px bottom.
- Section heading ("Overview", "Workspace") gets ~24px of space above and ~10px below.
- Vertical rhythm inside the content pane:
  - Heading to first line of body text: ~8px.
  - Caption / fine-print line (e.g. tax note with an inline link): immediately under heading with ~6px gap.
  - Block-level gap between meta block and price: ~14px.
  - Price to button row: ~16px.
  - Button row to next section ("Workspace"): ~32px.
- Button row: two buttons side by side with ~8px gap; each ~32px tall, ~14px horizontal padding.
- Footer-like row at the bottom (workspace/plan summary with price): full-width line with the label group on the left and price group right-aligned, ~16px vertical padding.
- Segmented toggle in header: two pills inside a ~28px tall track with ~3px inner padding; selected pill has a white surface and soft shadow, unselected is transparent.

## Typography

- Modal title: 15–16px, medium weight, near-black.
- Left rail items: 13–14px, regular weight, dark gray; selected item uses the same size with slightly heavier weight (medium) and darker tone.
- Section heading: 16–17px, semibold, near-black.
- Body/explanatory copy: 13px, regular, mid-gray (~#6B7280-ish).
- Inline links: same size as body, underlined, same mid-gray (not a bright accent — link affordance comes from underline, not color).
- Primary price: 22–24px, semibold, near-black. Sits on its own line.
- Sub-price meta (e.g. renewal date): 12–13px, light gray.
- Right-aligned price in list row: price 14px medium, billing cadence ("monthly", "yearly") 12px light gray on the line below, right-aligned.
- Segmented toggle labels: 13px, medium.

## Colors & Surfaces

- App backdrop: very light warm gray (~#F4F4F2) with the modal casting a soft drop shadow rather than a dark scrim.
- Modal surface: pure white (#FFFFFF) for the right pane.
- Left rail surface: subtle off-white / light gray (~#F7F7F6), about 2–3% darker than the right pane, creating a soft inset feel without a hard border.
- Selected nav item: white pill background that matches the right pane, ~6–8px corner radius, with a hairline border or very subtle shadow so it reads as "lifted out" of the rail.
- Primary action button: near-black fill (#111) with white label, ~8px radius.
- Secondary button: white fill with a 1px light gray border, dark label, ~8px radius.
- Dividers: 1px hairlines at ~#ECECEC, used between header and body, and between rail and pane.
- Text colors: primary ~#111, secondary ~#6B7280, tertiary/meta ~#9CA3AF.

## Interaction & Behaviour

- Modal is dismissed via the × icon, Escape key, or clicking outside the card.
- Header segmented toggle swaps the whole content scope; the left rail items stay the same but their contents differ.
- Left rail items are single-select; the selected item shows the white "lifted" pill. Hover state for non-selected items is a very subtle gray fill (~#EFEFEE) without the lift/shadow.
- Inline links open external info inline or in a new pane.
- Primary button is always the rightmost in a row; it is the highest-contrast element in the pane and acts as the visual anchor.
- Right pane scrolls independently if content overflows; left rail stays fixed.

## Animation

- Modal enters with a quick fade + slight scale-up from ~0.96 to 1.0 over ~150–200ms, ease-out.
- Backdrop fades in over the same duration.
- Section swaps in the right pane cross-fade (~120ms) with no layout jump — heights settle smoothly.
- Selected-pill movement in the left rail can use a soft spring (or a 120ms ease) so the highlight slides between items rather than hard-cutting.
- Button hover: background darkens ~6–8% over 80–120ms; no scale change.

## Key Principles

- The two-pane split inside a single floating card is what makes this feel like a focused "settings surface" rather than a full page — preserve the contained, compact footprint (~640×420) instead of letting it grow.
- Hierarchy comes from typographic weight and a single high-contrast primary button, not from color. Links are underlined-gray, not blue.
- The selected nav item visually "punches through" the rail by matching the right pane's surface color — this single trick ties the two panes into one continuous reading surface and should be preserved.
- Money and dates get their own line and breathing room; never inline a price with body copy. Right-aligned prices in list rows always pair a bold figure with a small lowercase cadence word ("monthly", "yearly").
- Keep the backdrop a soft light tone (no dark scrim) so the modal feels like a layer of the app, not a heavy interruption.
