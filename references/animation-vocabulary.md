# Animation Vocabulary & Best Practices

Source distilled from [animations.dev/vocabulary](https://animations.dev/vocabulary). Use this as the shared language for UI motion in this repo.

## Purpose first

- Animate to orient the user, give feedback, preserve continuity, or improve perceived performance.
- Do not animate just to decorate. The more often a user sees the motion, the shorter and quieter it should be.
- Respect `prefers-reduced-motion`: reduce distance, remove parallax/looping motion, and keep essential state feedback.

## Entrances, exits, and reveals

- Use fade, slide, scale, pop, or reveal intentionally based on what changed.
- Pair scale with opacity for most entrances; avoid elements appearing fully opaque before they settle.
- Use `AnimatePresence` for enter/exit so removed elements fade/scale/collapse instead of disappearing instantly.
- Reveal content with masks, `clip-path`, or height expansion only when it helps explain where content came from.

## Sequencing and timing

- Coordinate related motion with orchestration, not independent one-off transitions.
- Stagger related lists sparingly; use a small delay so the cascade feels instant, not theatrical.
- Use short durations: 150–250ms for micro-interactions, 250–350ms for larger layout/view transitions.
- Use fill modes deliberately when an animation needs to keep its first or last visual state.

## Movement and transforms

- Prefer transform and opacity for smooth composited motion: `translate`, `scale`, `rotate`, and `opacity`.
- Avoid animating layout-heavy properties like `width`, `height`, `top`, and `left` every frame unless Framer Motion is handling layout projection.
- Set `transform-origin` to match the trigger or anchor: popovers grow from the button, rows expand from the top, menus open from their edge.
- Use 3D tilt/flip and perspective rarely; only when depth clarifies the interaction.

## Transitions between states

- Preserve spatial consistency. Elements should feel like they travel, resize, or morph — not teleport.
- Use shared element transitions (`layoutId`) when a card, thumbnail, row, or selected state becomes another surface.
- Use layout animation for size and position changes so surrounding content glides instead of snapping.
- Use direction-aware page transitions: forward navigation moves one way; back navigation reverses it.
- Accordions/collapses should animate height with an inner padded wrapper to avoid flash and measurement glitches.

## Feedback and interaction

- Hover effects are subtle background or opacity shifts; avoid loud color changes, shadows, or glow.
- Press/tap feedback should be physical and quick, usually a small scale-down that springs back.
- Drag, swipe-to-dismiss, and reorder interactions should carry momentum and let neighboring elements make room.
- Use shake/wiggle only for errors or rejected actions.
- Use ripple only when the design language already supports it; otherwise prefer restrained press feedback.

## Easing and springs

- Default UI response: ease-out, e.g. `cubic-bezier(0.16, 1, 0.3, 1)`.
- Use ease-in-out for elements already on screen moving from A to B.
- Avoid ease-in for user-triggered UI because it starts sluggish.
- Use linear only for spinners, progress indicators, marquees, and other constant-speed loops.
- Use springs for interruption-friendly, physics-like movement. Tune stiffness/tension for snap, damping for settle, and mass for perceived weight.
- Carry velocity through interrupted motion so flicks, drags, and redirected animations feel continuous.

## Ambient and polish motion

- Looping/ambient motion must be quiet: pulses, floats, marquees, and idle animations should not compete with primary content.
- Skeleton/shimmer communicates loading; keep it subtle and stop it as soon as real content appears.
- Number tickers need tabular numbers so digits do not shift horizontally.
- Blur, masks, line drawing, typewriter, and text morph effects are polish tools; use them only when they clarify change.

## Performance checklist

- Target 60fps minimum; 120fps should still feel clean on high-refresh displays.
- Watch for jank, dropped frames, layout thrashing, and accidental repaint-heavy effects.
- Use `will-change` only shortly before expensive motion; remove it or keep usage narrow so layers do not pile up.
- Keep animated layers small and avoid animating large blurred surfaces when possible.
- QA reduced motion, fast repeated clicks, interrupted transitions, and slow devices before shipping.
