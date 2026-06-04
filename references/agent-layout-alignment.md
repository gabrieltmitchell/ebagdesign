# Agent Layout Alignment Specs

Source: inspired by Jordan Singer's note that "the new design spec is drawing alignment boxes for agent to understand layout" (https://x.com/jsngr/status/2062574606037164134).

## Principle

When a design spec is meant for an implementation agent, make the invisible structure visible. A screenshot shows what the UI looks like; alignment boxes explain how it is built.

Draw or describe the layout rails, bounding boxes, padding boxes, hit areas, component edges, anchor points, and spacing tokens that govern the composition. This gives the agent an implementation map instead of forcing it to infer structure from pixels.

## Use this when

- Translating a screenshot, Figma mock, or rough visual direction into code.
- Handing off dense product UI with multiple aligned regions, toolbars, cards, tables, rows, or overlays.
- Asking an agent to preserve a precise relationship between elements rather than merely approximate the look.
- Reviewing generated UI that looks close but feels misaligned, loose, or structurally wrong.

## What to specify

- **Outer frame:** page/container width, max width, safe area, and canvas background.
- **Alignment rails:** left/right edges that text, icons, controls, and cards should share.
- **Bounding boxes:** visible and invisible rectangles for cards, rows, popovers, hit areas, and content groups.
- **Spacing tokens:** exact gaps and padding from the 4px scale; call out repeated values.
- **Anchors:** where menus, popovers, tooltips, badges, and expanding content originate.
- **Stable vs. changing regions:** which boxes stay fixed and which boxes may resize, animate, or scroll.
- **Hierarchy through geometry:** use alignment, inset, scale, radius, and grouping before labels, borders, or heavy chrome.

## Implementation rules

- Before coding, identify the alignment boxes and name the major layout regions in plain language.
- Prefer shared grid/flex primitives and reusable spacing tokens over one-off pixel nudges.
- Keep related elements on the same alignment rail unless there is a deliberate hierarchy shift.
- If a component animates, keep its motion tied to its box: popovers grow from the trigger box, rows expand from their top edge, and shared elements travel between known rectangles.
- Do not add borders or wrappers just to make structure legible. The spec should expose the structure; the UI should remain quiet.

## QA checklist

- Can every major element be explained by a small set of boxes, rails, and spacing tokens?
- Do text, icons, controls, and cards snap to consistent left/right edges?
- Are hit areas larger than their visible glyphs where needed?
- Do animated elements preserve their origin, bounding box, and stable siblings?
- If the screenshot disappeared, would the written spec still give enough structure to rebuild the layout?
