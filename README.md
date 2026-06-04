# ebagdesign

Frontend design rules for clean, minimal, product-grade UI. Works with Claude Code, Cursor, and OpenAI Codex.

Covers spacing, typography, colors, buttons, icons, components, animations, motion vocabulary, and a QA process for keeping codebases clean and modular.

---

## Install

Pick your tool below and follow the one-liner.

### Claude Code

Installs globally — available as `/design` in every project.

```bash
curl -o ~/.claude/commands/design.md https://raw.githubusercontent.com/gabrieltmitchell/ebagdesign/main/claude/design.md
```

Then in any project, type `/design` and describe what you want to build or review.

---

### Cursor

Adds the rules to a specific project. Run this from your project root:

```bash
mkdir -p .cursor/rules && curl -o .cursor/rules/design.mdc https://raw.githubusercontent.com/gabrieltmitchell/ebagdesign/main/cursor/design.mdc
```

Cursor will automatically apply the rules to all `.ts`, `.tsx`, `.css`, and `.scss` files.

---

### OpenAI Codex

Adds the rules to a specific project. Run this from your project root:

```bash
curl -o AGENTS.md https://raw.githubusercontent.com/gabrieltmitchell/ebagdesign/main/codex/AGENTS.md
```

For global rules, place the file at `~/.codex/AGENTS.md`.

---

## What's covered

| Section | Summary |
|---|---|
| Spacing & Layout | Tight, intentional spacing. 4px scale. Minimal vertical gaps. Agent-readable alignment boxes for handoff. |
| Typography | Inter font, product-grade type scale, strict text hierarchy. |
| Colors | Black and grey palette. Light grey surfaces. No gradients or shadows. |
| Buttons | Rounded, light grey, no shadows. More horizontal padding than vertical. |
| Icons | Lucide only. Consistent sizing. Never mix libraries. |
| Components | BaseUI foundation. Animated dropdowns and dialogs. Subtle hover states. |
| Animations | Framer Motion everywhere. Smooth morphing containers. Animation vocabulary, easing, springs, reduced motion, and performance QA. |
| Agent Handoff | Draw the invisible layout boxes: rails, bounds, padding, hit areas, anchors, and stable vs. changing regions. |
| QA Process | Scan before building. No duplication. Modular component library mindset. |

---

## Animation vocabulary

The animation rules now include a shared vocabulary distilled from [animations.dev/vocabulary](https://animations.dev/vocabulary): entrances/exits, sequencing, transforms, continuity transitions, scroll motion, interaction feedback, easing, springs, ambient motion, polish effects, and performance. See [`references/animation-vocabulary.md`](references/animation-vocabulary.md) for the full checklist.

## Agent-readable layout specs

When handing designs to coding agents, make the invisible structure visible: alignment rails, bounding boxes, padding boxes, hit areas, anchors, and stable vs. changing regions. See [`references/agent-layout-alignment.md`](references/agent-layout-alignment.md) for the principle and QA checklist.

---

## Customizing

The rules are plain markdown — edit any file directly to match your project's conventions. The structure is intentionally opinionated but easy to override.

---

## Contributing

Open a PR. Keep it focused on product UI patterns — this isn't for marketing or landing page design.
