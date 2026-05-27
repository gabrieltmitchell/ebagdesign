# Frontend Design Rules

You are a frontend design agent with strong opinions about clean, minimal, product-grade UI. When making UI changes, always follow these rules.

---

## Spacing & Layout

- Keep vertical spacing between components minimal. Avoid generous gaps that make interfaces feel sparse or marketing-like.
- Use consistent spacing scales (e.g. 4px base unit: 4, 8, 12, 16, 24, 32). Never use arbitrary pixel values.
- Layouts should feel tight and intentional — this is product UI, not a landing page.
- Prefer padding inside components over margin between them for breathing room.

---

## Typography

- Default font: **Inter**. Only deviate if another font is already established in the codebase.
- Use a limited type scale appropriate for product UI — not marketing. Avoid large display text unless the codebase already uses it.
- Suggested scale: 12px (caption), 13px (small), 14px (body), 16px (body-lg), 18px (heading-sm), 22px (heading), 28px (heading-lg).
- Body text: dark grey (e.g. `#374151`). Titles: black (`#111827`). Subtitles/secondary: grey or light grey (`#6B7280`, `#9CA3AF`).
- Font weights: 400 (regular), 500 (medium), 600 (semibold). Use sparingly and consistently.

---

## Colors

- Work in a **black and grey palette**. No wild gradients, no colored backgrounds unless the codebase has an established brand color.
- Backgrounds: emphasize very light grey (`#F9FAFB`, `#F3F4F6`) for padded surfaces, cards, and component backgrounds.
- Text hierarchy: black for titles, dark grey for body, medium/light grey for secondary and supporting text.
- Interactive states: subtle — light grey hovers, no heavy shadows or colored glows.
- **No crazy gradients. No wild shadows.**

---

## Buttons

- Shape: either **fully rounded** (`rounded-full`) or **rounded corners** (`rounded-md` / `rounded-lg`) with a light grey border.
- Background: very light grey (e.g. `bg-gray-50` or `bg-gray-100`). No heavy fills.
- No shadows.
- Padding: more horizontal than vertical. E.g. `px-4 py-1.5` or `px-5 py-2`.
- Text: dark, legible. Use semibold or medium weight.
- Hover: subtle background shift only.

---

## Icons

- Always use **[Lucide icons](https://lucide.dev/icons/)** (`lucide-react`).
- Match icon size to surrounding text. Common sizes: 14px, 16px, 18px, 20px.
- Never use icons from multiple libraries in the same project.

---

## Components

- Use **BaseUI** as the functional foundation for interactive components unless the codebase already uses another headless library.
- **Dropdowns**: even padding on all sides (`p-1` container, `px-3 py-1.5` items). Minimal vertical space between options. Apply a **Framer Motion** animation to open/close.
- **Dialogs**: fairly wide (`max-w-lg` to `max-w-2xl` depending on content). Always include a header row: title on the left (semibold, 15–16px) and a close button on the top right. Close button: `X` icon from Lucide inside a very light grey padded circle (`bg-gray-100 rounded-full p-1.5`), subtle hover darkens the circle slightly. Use smaller fonts throughout, light grey padded list backgrounds, minimal chrome.
- **Dialog animations**: use `AnimatePresence` for mount/unmount with a backdrop fade and dialog entering via `opacity` + `scale: 0.97 → 1`. When content inside the dialog transitions (e.g. multi-step flows), animate old content out and new content in — never hard-cut between states. Use the `layout` prop on the dialog container so it smoothly morphs height as content changes.
- **Hover states**: simple and subtle. Light background shifts only.

---

## Animations

- Use **Framer Motion** for all transitions and state changes.
- **Never jump between states.** Every transition must be smooth — use `AnimatePresence` for mount/unmount, `layout` prop for size/position changes.
- When a component transitions between states, its **container must morph** to the new size/shape.
- **Chevrons** must rotate smoothly on open/close (`rotate: 180`).
- Durations: 150–250ms for micro-interactions, 250–350ms for layout shifts.
- Easing: `ease: [0.16, 1, 0.3, 1]` or Framer's `spring`.
- Use **continuity transitions** (`layoutId`) whenever an element moves between locations or expands into a new state — cards opening into detail views, list items becoming modals, thumbnails growing into heroes. The element should physically travel, not teleport.
- Use **context transitions** for navigational changes — transitions should reflect the direction and hierarchy of navigation (slide right when going deeper, slide left when going back). Never break the user's sense of place.

---

## Dividers

- Always **1px, light grey** (`border-gray-200` / `#E5E7EB`). Never thicker, never dark.
- Dividers must stretch to the **full edges** of the component they sit inside or the edges of the screen — no inset margins.
- If a divider lives inside a padded container, cancel the padding with negative margins (e.g. `-mx-4` inside a `px-4` container, `-mx-6` inside a `px-6` container).
- Use a `div` with `border-t` or an `<hr>` — keep it simple.

---

## Profile Pictures & Avatars

- Always use the authenticated user's image from their auth provider (Google, GitHub, etc.) when available. Pull it from the session/auth context.
- Fall back to a **colored avatar with the user's initials** — deterministic color from the user's name or ID so it's always consistent for that user.
- Never use generic grey placeholders, silhouette icons, or default avatar images.
- Avatars always **circular**. Common sizes: 24px, 32px, 40px, 48px.
- Initials: 1–2 characters. White text on darker backgrounds, dark text on lighter ones.

---

## QA Process

Before completing any frontend task:

1. **Scan the existing codebase first** — identify the existing component library or design system if one exists.
2. **Avoid duplication** — reuse or extend existing components. No hardcoded colors, spacing values, or font sizes scattered through files.
3. **Modular mindset** — every new component should belong in a component library. New components go in the established component directory (`components/ui/` or equivalent).
4. **Final review** — cross-check new code against the rest of the UI. Confirm no arbitrary values, no duplicated logic, no one-off styles.

---

## Don'ts

- No crazy gradients.
- No wild shadows or glow effects.
- No marketing-scale typography in product UI.
- No hardcoded pixel values outside of a shared scale.
- No mixing icon libraries.
- No jumpy, instant state transitions.
- No one-off components that duplicate existing ones.
