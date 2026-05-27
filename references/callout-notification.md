---
pattern: callout-notification
tags: [feedback, overlay, toast, pill]
---

# Callout Notification

A low-profile, pill-shaped callout that informs the user of a system-level change and offers a binary confirm/undo choice without blocking the underlying UI.

## Layout & Structure

- Single horizontal row, fully pill-shaped (border-radius equal to half its height, ~999px)
- Three slots from left to right: message text, secondary action (text-only), primary action (outlined pill button)
- Anchored to the top of the viewport, horizontally centered, floating above the app content with a subtle drop shadow
- Sits as an overlay above a rounded content surface — the rounded corners of the surface peek out below the callout, reinforcing the floating relationship
- Width is content-driven (hugs message + actions); not full-width, not a banner

## Spacing & Sizing

- Pill height roughly 44–48px
- Horizontal padding inside the pill ~20–24px on the outer edges
- Gap between message and "Change" action: large, ~48–64px (acts as a visual separator instead of a divider line)
- Gap between "Change" text action and "Keep" outlined button: ~16px
- Inner button ("Keep") has its own pill shape with ~12–16px horizontal padding and ~6–8px vertical padding
- No icon prefix — text alone carries the meaning

## Typography

- Single weight throughout: regular / 400–450
- Message text and both actions use the same size (~14–15px) and the same color
- No bolding on the primary action — emphasis comes purely from the button outline, not type weight
- Sentence case for the message; title case for the actions

## Colors & Surfaces

- Background: pure white (or near-white) pill on a light page background
- Shadow: soft, diffuse, low-opacity drop shadow (large blur radius, minimal vertical offset) — gives lift without a hard edge
- No border on the outer pill — the shadow does the work
- "Keep" button: 1px hairline border in a light neutral gray, transparent fill, same text color as the message
- Text color: near-black / very dark gray (~#111–#222), uniform across all three text elements

## Interaction & Behaviour

- Auto-appears after the system makes a default change on the user's behalf — it does not ask permission, it announces a fait accompli and offers an out
- "Change" = revert / pick a different option (text-only de-emphasized action)
- "Keep" = confirm and dismiss (outlined button, the implied-default path)
- Either action dismisses the callout; likely also auto-dismisses after a timeout (~6–10s) since the default is already applied
- Non-blocking: the page behind remains fully interactive; no scrim or backdrop
- No close (×) affordance — dismissal happens via the actions or timeout

## Animation

- Enter: slide down from just above the viewport edge combined with a fade-in, ~200–300ms with an ease-out curve
- Exit: fade + slight upward translate, slightly faster (~150–200ms)
- Hover on actions: very subtle background tint shift (no scale, no shadow change) to keep it calm
- Shadow stays static — no lift on hover, since the callout is already presented as floating

## Key Principles

- Announce, don't interrupt: the action has already been taken, so the UI is informational with an undo, not a confirmation dialog
- Equal typographic weight across message and actions keeps the tone neutral; hierarchy comes from shape (outlined pill) not from type
- The generous gap between message and actions replaces a divider — whitespace is the separator
- The pill shape, soft shadow, and lack of border make it read as a floating object rather than a banner welded to the chrome
- Keep it short: one line, two actions, no icons, no secondary text — if it needs more, it's not a callout anymore
