---
pattern: popover
tags: [overlay, composer, floating-panel, quick-create]
---

# Popover (Floating Composer)

A lightweight, floating panel anchored over the current page for quick-entry tasks like creating an item, leaving a comment, or composing a short form. Use when the action is fast, single-purpose, and shouldn't pull the user out of their current context.

## Layout & Structure

- Single rounded card that floats above the page, not anchored to a viewport edge — it sits in the upper-middle area with the underlying page still visible around it
- Vertical stack inside the card: compact header row, large title input, multi-line description input, row of attribute pills, footer action row
- Header row contains a context chip on the left (icon + short workspace/scope label) followed by a chevron and the action name (e.g. "New item"); right side holds an expand-to-fullscreen icon and a close icon
- Attribute pills sit in a single horizontal row near the bottom of the content area, each a rounded outlined chip with leading icon + label; an overflow trigger ("…") closes the row
- Footer is split: left side has a small icon-only attachment button; right side has a toggle ("Create more") and the primary submit button

## Spacing & Sizing

- Card width feels generous, ~720–820px max, height grows with content but starts compact (~280–320px)
- Outer card padding: ~20–24px on all sides, slightly less on the bottom row
- Header row to title input gap: ~20–24px
- Title input to description input gap: ~8–12px (they read as one continuous editor)
- Description block to pill row gap: ~28–36px (deliberate breathing room)
- Pill height ~28–32px, internal horizontal padding ~10–12px, icon-to-label gap ~6px, gap between pills ~8px
- Footer row sits flush with the card's bottom padding, primary button height ~32–36px

## Typography

- Header context chip label: ~12–13px, semibold, uppercase or proper-case
- Header action title ("New item"): ~14–15px, semibold, near-black
- Title input: ~18–20px, semibold; placeholder uses the same size but a muted gray
- Description input: ~14–15px, regular; placeholder also muted gray
- Pill labels: ~13px, medium weight, mid-gray
- Toggle label ("Create more"): ~13px, regular, mid-gray
- Primary button label: ~13–14px, medium weight, white

## Colors & Surfaces

- Card surface: pure white
- Backdrop: none — the underlying page is fully visible and untinted; the popover relies entirely on its own elevation
- Card elevation: a soft, wide, low-opacity shadow (large blur radius, small y-offset) — it floats rather than punches forward
- Card corner radius: ~16–20px (noticeably softer than typical inputs)
- Pills: 1px border in a very light gray, transparent fill; icons in mid-gray
- Context chip in header: white pill with the same hairline border, small colored icon mark inside
- Primary button: saturated purple/indigo, white label, rounded ~8px, no shadow
- Toggle when off: light gray track, white knob, no shadow
- No internal dividers — the card is one continuous surface; structure comes from spacing alone

## Interaction & Behaviour

- Triggered by a keyboard shortcut or a "+ New" affordance; anchored to the viewport rather than to a specific button
- Dismissed by: close icon (top-right), Escape, clicking outside the card, or successful submit
- Expand icon (top-right, next to close) promotes the popover into a full-page view without losing input state
- Each pill opens its own nested popover for value selection (priority, assignee, project, label) — those nested popovers anchor directly to their pill
- "Create more" toggle, when on, keeps the popover open after submit and resets the inputs so the user can fire off several in a row
- Submit button stays in a low-saturation state until the title input has content
- Attachment icon (bottom-left) opens a file picker
- Title input is auto-focused on open; Tab moves through title → description → first pill → … → submit

## Animation

- Enter: card fades and scales from ~97% to 100% over ~160–200ms with an ease-out curve; no bounce
- Exit: ~120ms fade + slight scale-down to ~98%
- The lack of a backdrop fade is deliberate — the page stays static so the card reads as additive rather than blocking
- Pill popovers open with a small ~120ms fade + 4px upward translate from their anchor
- Toggle state change ~150ms ease, button color transitions ~120ms

## Key Principles

- No backdrop, no dimming — the floating card and its shadow do all the elevation work; this is what makes it feel light rather than modal
- Title and description read as one continuous writing surface (no border, no fill, no separator) so the composer feels like a document, not a form
- Attribute pills replace traditional labeled form fields — they collapse what would otherwise be five labeled rows into a single tidy strip
- The header doubles as a breadcrumb (scope → action), giving context without a heavy title bar
- Generous corner radius and a soft, wide shadow are doing more elegance work than any color or border treatment — preserve both
- Footer balances a quiet utility (attachment) on the left with the commit action on the right; never put both on the same side
