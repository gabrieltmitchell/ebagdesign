---
pattern: chat-input
tags: input, chat, ai, overlay
---

# Chat Input

A centered, floating-style chat input for AI or search interactions. Sits in a light grey content area and feels like a calm, open invitation rather than a form field.

## Layout & Structure

- Centered horizontally in the content area, with generous left/right margin (~20% each side — roughly `max-w-2xl` centered)
- White rounded rectangle container with a subtle border (`border-gray-200`)
- Two distinct rows inside the input:
  - Top: the text input area (plain, no label, placeholder text only)
  - Bottom: a toolbar row with actions on the left and right
- Toolbar left: a contextual action button (e.g. "Skills" with a small icon and dropdown chevron) — small, pill-shaped, light grey
- Toolbar right: secondary action icon (attachment) + primary send icon — both small (~16px), right-aligned
- Send button: small rounded arrow icon, not a full button — contained, subtle

## Spacing & Sizing

- Container padding: `px-4 pt-4 pb-3`
- Input area: minimum height ~40px, grows with content
- Toolbar height: ~32px
- Gap between input and toolbar: ~8px
- Corner radius: `rounded-xl` or `rounded-2xl` — noticeably rounded but not pill

## Typography

- Placeholder text: 14–15px, light grey (`#9CA3AF`), regular weight
- Input text: 14–15px, dark (`#111827`)

## Colors & Surfaces

- Container background: white
- Container border: `border border-gray-200`
- No shadow — the white card on light grey background provides natural contrast
- Toolbar button (Skills): very light grey background (`#F3F4F6`), 12–13px text, rounded-full
- Icon buttons: grey (`#6B7280`), no background at rest, very light grey circle on hover

## Interaction & Behaviour

- Input expands vertically as content grows — container morphs with it
- Toolbar actions are always visible (not hidden until focus)
- Send button activates when input has content — subtle opacity change or color shift
- Dropdown (Skills) opens a small floating menu below with `AnimatePresence`

## Animation

- Container height morphs smoothly as text grows — use `layout` prop on the container
- On page load, input can gently fade + slide up into position (`opacity: 0→1`, `y: 8→0`)
- No bounce or overshoot — calm, functional entrance

## Key Principles

- The input looks like a card, not a form field — it floats in the space rather than being anchored to a grid
- Toolbar actions feel like they belong to the input, not outside it — keep them inside the container
- The background of the page (light grey) is what makes the white card feel premium — don't use this pattern on a white page background
- Simplicity of the send button (just an arrow icon) keeps the UI from feeling like a chat app — it reads as a tool
