---
pattern: liquid-glass-web
tags: [glass, refraction, motion, surfaces, components, performance]
source: https://aave.com/design/building-glass-for-the-web
---

# Liquid Glass for the Web

A tactile glass surface pattern for web UI: a live-content lens that bends what is inside it, adds rim/specular light, and stays portable across modern browsers.

## Layout & Structure

- Treat glass as a component wrapper around real rendered content, not as a decorative overlay pasted above the UI.
- Keep the refracted region small and intentional: switch thumbs, slider handles, selected pills, QR-code tap states, video controls, or compact floating controls.
- Let the rest of the content render normally outside the lens so the interface remains readable, clickable, scrollable, and selectable.
- For component families, reuse the same lens behavior across switches, sliders, toggle groups, media controls, and special interactive surfaces so the effect feels like one material system.
- Do not rely on the glass alone for state. Pair it with a clear selected track, fill, rim light, or highlighted pill so state remains legible behind the distortion.

## Spacing & Sizing

- Keep glass lenses compact. Large refracted DOM regions are fragile and expensive, especially in Safari.
- Add an explicit hit area around small lenses so tactile controls are easy to drag without making the visible glass bulky.
- For switches and sliders, keep the lens aligned to the control track and move the lens region rather than regenerating the full effect on every drag frame.
- Let the lens overhang the underlying track slightly so the edge highlight and distortion have room to read.

## Typography

- Text may pass under the lens, but it should not be the only way to read the control state.
- Preserve text selection and links by bending the element’s own rendered pixels instead of replacing the DOM with a screenshot or canvas copy.
- Use a softer bend when values or labels must stay readable through the glass; use stronger refraction only when the highlight is mostly decorative.

## Colors & Surfaces

- The core effect is displacement: red and green channels in a generated map push pixels horizontally and vertically.
- Add a subtle color fringe at the lens edge and a specular highlight so the glass remains visible against both bright and busy backgrounds.
- For controls, refract a purpose-built highlight/fill layer when needed instead of distorting important labels directly.
- On moving or busy backgrounds, strengthen the rim/highlight enough for controls to stay crisp without adding heavy shadows.

## Interaction & Behaviour

- Use glass where the interaction benefits from tactility: dragging, toggling, selecting, tapping, scrubbing, or controlling media.
- Animate position cheaply. When the glass moves without changing shape, shift the filter region and reuse the same displacement map.
- Regenerate the map only when the lens changes size, radius, or squish/shape.
- For toggle groups, let the glass selection indicator glide with spring easing and settle into place instead of snapping linearly.
- For tap responses, briefly bend/squish the surface to make the component feel physical.

## Animation

- Prefer spring motion for selected pills, switch thumbs, and slider handles so the lens feels material rather than mechanical.
- Keep drag animations frame-safe: the displacement map should remain stable while only the lens position changes.
- For resize or squish animations, generate maps quickly enough to stay inside the frame budget.
- Respect reduced-motion settings by reducing squish, glide distance, and ambient movement while preserving the static glass treatment.

## Browser & Rendering Notes

- SVG `feDisplacementMap` can drive the effect for ordinary DOM content across modern browsers.
- Use a generated PNG displacement map: neutral outside the lens, directional red/green offsets inside it.
- Safari may cache SVG filter output by filter ID; use fresh filter IDs when the displacement map changes so motion does not freeze.
- Safari also has practical limits on how much source graphic a filter can process. Keep refracted DOM regions conservative.
- For non-DOM or unsupported surfaces, such as canvas-rendered QR codes or live video in Safari, feed the same displacement map into a WebGL shader instead.
- Optimize map generation with symmetry where possible: a rounded lens can compute one quadrant and mirror it with inverted X/Y displacement.

## Key Principles

- Glass is a live-content lens, not a blur overlay.
- The displacement map is the portable core; the renderer can switch between SVG filters and WebGL depending on the surface.
- Make glass part of the component language, not a one-off flourish.
- Preserve readability and interactivity first; refraction is only successful when the UI remains usable.
- Browser compatibility and performance are design constraints, not implementation afterthoughts.
