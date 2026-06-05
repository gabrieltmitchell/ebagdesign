# References

Pattern-level breakdowns of specific UI interactions and layouts worth replicating. No app names or brand assets — just the pattern, distilled.

Each file captures a single pattern: its structure, spacing, animation, and the non-obvious things that make it feel good. These are meant to be read by a coding agent alongside the main design rules.

## How to use

When invoking the design skill, point the agent at a relevant reference:

```
/design build a command palette — see references/command-palette.md for the interaction pattern
```

## How new patterns are added

1. Drop a screenshot into this conversation
2. The agent breaks it down using `_template.md`
3. The output is saved as a new `.md` file here
4. Brand names and identifying details are removed

## Patterns

- [Animation Vocabulary & Best Practices](animation-vocabulary.md) — shared motion language: entrances/exits, sequencing, transforms, state transitions, feedback, easing, springs, ambient motion, reduced motion, and performance QA
- [Agent Layout Alignment Specs](agent-layout-alignment.md) — draw alignment rails, bounding boxes, padding boxes, hit areas, anchors, and stable/changing regions so coding agents understand structure
- [DESIGN.md Agent Rules](design-md-agent-rules.md) — use Google's DESIGN.md pattern as project memory: tokens for exact values, prose for rationale, linting/export for agent-safe design systems
- [Sidebar Navigation](sidebar-navigation.md) — 24–26px rows, 0px gaps, warm off-white bg, inset hover pills, only color is team avatars
- [Chat Input](chat-input.md) — white card composer on warm grey canvas, border not shadow, oversized placeholder, toolbar inside the card
- [Sidebar Popover](sidebar-popover.md) — settings mode overlay in the sidebar column, larger rows signal mode switch, pinned back action
- [Dropdown Menu](dropdown-menu.md) — two variants: navigation switcher with trailing checkmark vs. action menu with leading icons + keyboard shortcuts
- [Modal Dialog](modal-dialog.md) — centered settings dialog, hairline dividers, desaturated backdrop, structure felt through spacing not borders
- [Popover](popover.md) — no backdrop, single card with wide soft shadow, title+description as one writing surface, attribute pills not form fields
- [Callout Notification](callout-notification.md) — announces change already made, equal weight across message/actions, shape carries hierarchy not bold
- [Gallery Layout](gallery-layout.md) — tiles are the cards, colored preview surface IS the container, no outer chrome
- [Billing Module](billing-module.md) — two-pane modal, selected nav item surface punches through to match content pane
- [Settings & Preferences](settings-preferences.md) — section headers outside the card, all controls aligned to one vertical gridline, blue only for active toggles
