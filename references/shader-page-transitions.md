---
pattern: shader-page-transitions
tags: [shader, webgl, route-transitions, motion, performance, nextjs]
source: https://glimm.dev/
---

# Shader Page Transitions

A single GPU-composited shader band sweeps across the screen during navigation or a meaningful state change, revealing the next view underneath without making the app feel heavy or decorative.

## Layout & Structure

- Treat the shader as a page-level transition layer, not a component decoration. Mount it once at the app shell/root so it can cover the viewport without changing page layout.
- Keep the outgoing and incoming views structurally stable underneath the sweep. The shader should mask the transition; it should not be responsible for reflow, height changes, or content positioning.
- Use the effect for route changes or deliberate state changes where continuity matters. Do not attach it to small component toggles, hover states, menu opens, or every click.
- Prefer automatic internal-link interception only when the app's navigation model is simple and consistent. Use explicit transition links or a transition router when the destination, direction, or timing needs to communicate hierarchy.

## Motion Model

- The band is one continuous sweep with a soft gaussian falloff. Lower tightness creates a wider, softer wash; higher tightness creates a focused beam. Choose the narrowest band that still feels smooth at the target speed.
- Match direction to navigation semantics: left-to-right or top-to-bottom for forward/progressive movement, the reverse for back/return flows when the product has a clear spatial model.
- Keep traversal fast enough to feel responsive. A route transition can be expressive, but it should never make the user wait for decoration before seeing the next state.
- Use front-loaded easing for snappy user-initiated navigation, symmetric ease-in-out for calmer scene changes, and avoid linear motion unless the design intentionally needs a mechanical scan.

## Color & Palette

- Use shader color sparingly in otherwise quiet product UI. The sweep can be the one expressive moment; the resting interface should still follow the black/grey system.
- Prefer restrained palettes that echo existing brand accents. If using cosine palettes, tune the RGB triplets against real UI backgrounds instead of accepting random saturated results.
- Ensure the sweep preserves text legibility while it passes. It should reveal and soften, not wash the whole viewport in high-chroma glare.
- Do not use shader palettes as a reason to introduce gradients, glows, or colored shadows into static surfaces.

## Implementation Guardrails

- Lazy-initialize expensive WebGL work. A route transition system should be idle until the first sweep, and an app with no transition should pay essentially no setup cost.
- Keep the shader dependency small and isolated. Route-transition code belongs in the app shell, not scattered through individual screens.
- Provide a non-WebGL fallback: instant navigation, opacity/transform transition, or no effect. Broken GPU support must not block routing.
- Respect `prefers-reduced-motion`: reduce distance, duration, and chroma, or disable shader sweeps while preserving state feedback.
- Avoid multiple simultaneous WebGL contexts for UI polish. One transition layer is enough.

## QA Checklist

- Trigger a normal forward navigation, a back navigation, a programmatic redirect, and a rapid double-click. The page should not flash, tear, or get stuck mid-sweep.
- Test on a low-power laptop or throttled browser. The transition should stay GPU-composited and avoid layout thrash.
- Verify the first transition does not feel delayed by shader setup; if it does, prewarm only when intentional and safe.
- Confirm keyboard navigation and reduced-motion settings still produce understandable route changes.
- Check dark and light surfaces. The sweep should feel integrated on both, not like a pasted-on gradient.

## Anti-patterns

- No shader effects for micro-interactions that only need opacity, scale, or a simple transform.
- No full-screen color blasts that obscure the destination view.
- No per-component WebGL instances for isolated cards, menus, or buttons.
- No transition that hides slow routing, loading, or data fetching problems. Fix the wait state; do not mask it with spectacle.
