---
pattern: chat-input
tags: input, chat, ai, composer, surface
---

# Chat Input

A centered composer for an AI assistant embedded inside a productivity tool. Reads as a calm, oversized text card floating in a soft canvas — deliberately not a form field, not a chat bubble, not a search bar.

## Layout & Structure

- Horizontally centered in the content column with comfortable side gutters — composer width is roughly **560–620px** (`max-w-2xl`-ish), regardless of viewport width above that threshold
- Vertically positioned in the **upper-middle third** of the canvas, not dead-center — leaves space for example cards / response content to flow underneath without feeling bottom-loaded
- Sits on a very light warm-grey canvas (`#F4F4F5`-ish), which is what gives the white composer card its lift
- The composer itself is a single rounded white card with two stacked zones:
  1. **Input zone** (top, taller): the editable textarea region with placeholder
  2. **Toolbar zone** (bottom, shorter): a single row with left-aligned context controls and right-aligned action icons
- Below the composer, a smaller secondary surface holds **example prompt cards** (3 across) with a tiny dismiss `×` aligned to the top-right of that group — this is the "empty state helper" layer, visually subordinate to the composer
- The whole page has a faint centered watermark/logo behind the composer (~15% opacity) — subtle, never competes
- A small fixed "Ask <product>" pill lives in the **bottom-right corner of the viewport** as a persistent re-entry point when the composer isn't focused

## Spacing & Sizing

- Composer corner radius: **12px** (`rounded-xl`) — rounded enough to feel friendly, not so much it looks like a pill
- Composer outer padding: **14–16px** on all sides
- Input zone minimum height: **~56px** (enough for ~2 lines visible before growing)
- Toolbar zone height: **~32px**
- Vertical gap between input zone baseline and toolbar: **10–12px**
- Toolbar left pill ("Skills" with chevron + globe icon): height **24px**, padding `0 8px 0 6px`, icon-to-text gap **4px**, corner radius **6px**
- Toolbar right icons (attachment, send arrow): **16px** glyphs, ~24×24px hit targets, gap between them ~6px
- Example cards row: 3 columns, ~12px column gap, each card ~180px wide × ~96px tall
- Example card internal padding: **14px**, with the icon in the top-left and 2 lines of text below
- Gap between composer card and example cards container: **8–10px**

## Typography

- Placeholder text: **15px**, weight 400, color `#A1A1AA` (warm light grey) — sized larger than typical inputs to feel like a prompt invitation, not a field label
- Input text (when typed): **15px**, weight 400, color `#18181B`
- Toolbar pill text ("Skills"): **12.5–13px**, weight 450, color `#52525B`
- Example card title: **13px**, weight 500, color `#18181B`
- Example card description: **12.5px**, weight 400, color `#71717A`, ~1.4 line-height
- "Get started with some examples" helper label: **12px**, weight 400, color `#71717A`
- Bottom-right "Ask <product>" pill: **12px**, weight 450

## Colors & Surfaces

- Canvas background: `#F4F4F5` (warm light grey, slightly warmer than the sidebar)
- Composer card: pure white `#FFFFFF`, **1px border `#E4E4E7`**, **no drop shadow** — the border + canvas contrast does all the work
- Toolbar left pill: very light grey fill `#F4F4F5` or `#F0F0F0`, no border
- Toolbar icon buttons: transparent at rest; on hover get a `#F4F4F5` circular background
- Example cards: white `#FFFFFF` with the same 1px `#E4E4E7` border, same 12px radius
- The icon inside each example card sits in a tiny **light-grey rounded square** (~22×22, radius 6px, fill `#F4F4F5`) — a quiet "chip" rather than a colored badge
- Send arrow icon: `#71717A` at rest, darkens to `#18181B` only when input has content
- No focus ring on the composer itself — focus is communicated by the cursor in the input, not a border change

## Interaction & Behaviour

- The textarea grows vertically as the user types; the whole card grows with it (no internal scroll until many lines)
- Toolbar controls remain visible at all times — they are not gated behind focus
- "Skills" pill opens a popover with a list of capabilities; chevron rotates ~180° while open
- Attachment icon opens a file picker
- Send button is enabled-looking only when there's content; otherwise its arrow is muted (`#A1A1AA`)
- `Enter` submits, `Shift+Enter` newlines (standard chat composer behavior)
- Example cards are clickable: clicking one inserts the prompt template into the input and focuses the textarea
- The `×` on the examples row dismisses the empty-state helper; it should NOT reappear on the same session
- Bottom-right "Ask <product>" pill is a re-focus shortcut — clicking it scrolls/focuses the composer

## Animation

- The composer card itself has no entrance animation in steady state; it's already there when the canvas opens
- The empty-state row (helper text + example cards + dismiss) fades + slides up **8px** on mount, **200ms ease-out**
- Dismissing the example row: fade + slide **down 4px**, **150ms ease-in**, then the surrounding layout reflows
- Textarea height growth: use Framer Motion `layout` on the card so height changes interpolate smoothly (~120ms)
- "Skills" popover opens with `opacity 0→1` + `y: -4→0`, **140ms ease-out**
- Send arrow on submit: brief scale `1→0.9→1` (~120ms) provides tactile feedback
- No bouncy springs anywhere — motion is short and damped to match the calm tone

## Key Principles

- **The composer is a card, not an input.** Generous padding, large placeholder, two distinct zones — it reads as a surface you compose on, not a field you fill.
- **Border, not shadow.** A 1px border on a slightly-warm canvas is what makes this feel like a high-end tool. A drop shadow would push it toward a consumer chat app.
- **Toolbar controls live inside the card, not below it.** The "Skills" pill and the send arrow are part of the composer's footer — there is no detached action bar.
- **The placeholder is oversized.** At 15px, it invites a thought, not a query. Don't shrink it to 13–14px or it stops feeling premium.
- **The empty-state helper is a separate, dismissible layer.** It uses the same card vocabulary (white, 12px radius, 1px border) so it feels related — but its smaller scale and quiet header make it clearly secondary. When dismissed, the composer should not move.
- **The watermark behind the composer matters.** A faint centered glyph at ~15% opacity gives the canvas a sense of place without ever competing. Don't omit it; don't make it visible.
- **Warm greys, not cool greys.** Everything trends toward zinc/stone rather than slate. Cool greys here would make the surface feel sterile.
