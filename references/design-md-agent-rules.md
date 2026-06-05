# DESIGN.md Agent Rules

Source: https://github.com/google-labs-code/design.md

DESIGN.md is a structured, plain-text design system format for coding agents. It does not replace these rules; it gives agents a persistent source of truth for the exact design tokens and the rationale behind them.

## Core idea

A strong design handoff has two layers:

1. **Machine-readable tokens** in YAML front matter: exact colors, typography, spacing, radius, and component values.
2. **Human-readable prose** in Markdown: the design intent, constraints, references, and reasoning that explain how to apply the tokens.

Tokens give the agent precise values. Prose tells the agent what kind of product it is building and why the values exist.

## Use prose as the design brain

The most important part of a DESIGN.md file is the prose. Token values alone do not create taste.

- Prefer a specific reference over generic adjectives. "Austere graduate lecture handout" gives a clearer design target than "modern, clean, premium."
- Describe the product's substrate, density, rhythm, and restraint. Is it a dense tool, a quiet dashboard, a printed-object metaphor, or a friendly consumer workflow?
- Explain what the design must avoid. Negative constraints define the character as much as positive rules.
- Keep the prose compact enough that an agent can actually follow it during implementation.

## Canonical DESIGN.md structure

When a project has or needs a DESIGN.md, use this order for the main sections:

1. Overview
2. Colors
3. Typography
4. Layout
5. Elevation & Depth
6. Shapes
7. Components
8. Do's and Don'ts

Unknown project-specific sections are fine, but duplicate sections create confusion and should be avoided.

## Token guidance

Use tokens for stable, reusable decisions:

- `colors`: semantic palette values such as `primary`, `surface`, `on-surface`, `border`, `muted`, and `accent`.
- `typography`: named levels such as `body-md`, `label-sm`, `heading-sm`, and `heading-lg`.
- `spacing`: the actual spacing scale used by the project.
- `rounded`: the corner-radius scale.
- `components`: canonical component styling such as `button-primary`, `button-primary-hover`, `input-field`, `card`, and `badge`.

Use token references instead of duplicating values:

```yaml
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.label-md}"
    rounded: "{rounded.md}"
    padding: "{spacing.sm}"
```

Represent hover, active, pressed, disabled, and selected states as separate sibling component entries. Do not bury important state guidance in an unstructured paragraph if it should be reused.

## Agent workflow

Before changing UI code:

1. Look for `DESIGN.md`, `design.md`, `tokens.json`, Tailwind config, CSS variables, or Figma-exported tokens.
2. Treat DESIGN.md tokens as the exact values to use unless the user explicitly asks to change the design system.
3. Treat DESIGN.md prose as the design intent. When a local implementation rule conflicts with the prose, preserve the intent and update the local pattern to match.
4. If a project has no design source of truth, create a small DESIGN.md instead of scattering one-off values through components.
5. Keep these ebagdesign rules as implementation guardrails: minimal product UI, tight spacing, Lucide icons, BaseUI primitives, Framer Motion, and modular reusable components.

## Validation and exports

When a project uses DESIGN.md, validate it before relying on it:

```bash
npx @google/design.md lint DESIGN.md
```

The linter catches broken token references, missing primary colors, missing typography, low color contrast, orphaned tokens, section-order issues, and likely typos in top-level keys.

Use the CLI to compare or export the design system when needed:

```bash
npx @google/design.md diff DESIGN.md DESIGN-v2.md
npx @google/design.md export --format json-tailwind DESIGN.md > tailwind.theme.json
npx @google/design.md export --format css-tailwind DESIGN.md > theme.css
npx @google/design.md export --format dtcg DESIGN.md > tokens.json
```

## Practical rule for ebagdesign

DESIGN.md should become the project-level memory for brand and design-system decisions. ebagdesign remains the agent behavior layer: how to inspect a codebase, avoid duplication, choose components, implement motion, and keep product UI restrained.

In other words: DESIGN.md says what this product should feel like; ebagdesign says how the coding agent should execute that taste in code.
