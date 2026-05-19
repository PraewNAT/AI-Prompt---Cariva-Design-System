---
name: cariva-design-system-docs
description: Write or update Cariva Core Design System documentation in the established AI-readable style. Use when documenting Figma design system foundations, semantic tokens, typography, components, variants, states, usage guidelines, accessibility, or AI implementation rules for Cariva. Also use when the user asks to create docs beside a Figma component or keep docs consistent with existing Button/Input/Semantic Color documentation.
---

# Cariva Design System Docs

Use this skill to write or update Cariva Core Design System documentation in a consistent format for both humans and AI.

## Required Context

Before writing, read the handoff doc when available:

```text
design-system-ai-handoff.md
```

If the task is about color tokens, semantic color, contrast, or token mapping, also read:

```text
semantic-color-token-guideline.md
```

If these files are not available in the current workspace, ask the user to provide them or inspect the relevant Figma documentation nodes instead.

Important Figma source nodes:

| Area | Node ID |
|---|---:|
| Semantic Color Token Guideline | `3791:2` |
| Border Colors frame | `3791:722` |
| Typography Guideline | `3814:1454` |
| Button section | `3646:404` |
| Button Documentation | `3803:553` |
| Input section | `3760:5504` |
| Input Documentation | `3800:99` |

## Writing Style

- Write Thai mixed with English design-system terms.
- Keep language simple, practical, and scannable.
- Prefer sections and tables over long paragraphs.
- Explain what each token/component/state is for.
- Include concrete usage examples.
- Make the doc readable by both humans and AI.
- Use slash token names in examples, because Figma variables use slash naming.
- Do not invent new design-system decisions. Follow the handoff doc and Figma source.

## Documentation Structure

For component docs, use this structure unless the user asks otherwise:

```text
# Component Name

## Overview
## Anatomy
## Variants
## Sizes
## States
## Typography
## Color Tokens
## Usage Guidelines
## Accessibility
## AI Implementation Rules
```

For foundation docs, adapt the structure:

```text
# Foundation Name

## Overview
## Core Rules
## Naming Pattern
## Token Groups or Styles
## Usage
## Examples
## Accessibility
## AI Implementation Rules
```

## Required Doc Content

Every component doc should include:

- Source component name and Figma node ID when known.
- Component variants and allowed values.
- States and when each state is used.
- Layer/anatomy names when relevant.
- Typography styles to use.
- Semantic color tokens to use.
- What not to do.
- Accessibility notes.
- AI implementation rules.

## Token Rules

Use semantic tokens only.

Do not use raw Tailwind colors directly in component docs except when documenting token mappings or color samples.

`color/accent/*` tokens are allowed only for non-semantic decorative accents such as charts, avatars, tags, illustrations, and visual grouping. They must not be used for brand, status, destructive, or validation meaning.

Do not create or recommend:

- primitive tokens
- component-specific color tokens
- `color/danger/*`
- `color/field/*`
- `color/foreground/*`
- `color/border/invalid`
- status border tokens
- separate text and icon token groups
- `color/content/success`
- `color/content/warning`
- `color/content/error`
- `color/content/info`

Use `content` for both text and icons.

Use `status/error` for destructive, risky, error, and validation meanings.

Use `color/border/system` for system active component borders. Use `color/border/error` only for error/destructive field/control borders. Status border tokens have been removed; do not recreate them.

Do not use old focus token names:

- `color/focus/ring/default`
- `color/focus/ring/error`
- `color.focus.ring.default`
- `color.focus.ring.error`

## Typography Rules

Use `typography/...` text styles and Typography variables.

Main font:

| Variable | Value |
|---|---|
| `typography/font-family/sans` | IBM Plex Sans Thai |
| `typography/font-family/serif` | IBM Plex Sans Thai Looped |

Do not create a `code` typography style.

Role guidance:

| Role | Use for |
|---|---|
| Display | Landing page, hero, marketing headline |
| Heading | Page, section, modal, card hierarchy |
| Body | Readable content, descriptions, table text, helper content |
| Label | Buttons, tabs, menus, form labels, controls |
| Caption | Metadata, timestamp, low-emphasis note |

Current text styles:

| Role | Styles |
|---|---|
| Display | `typography/display/large`, `typography/display/medium`, `typography/display/small` |
| Heading | `typography/heading/large`, `typography/heading/medium`, `typography/heading/small` |
| Body | `typography/body/large`, `typography/body/medium`, `typography/body/small` |
| Label | `typography/label/large`, `typography/label/medium`, `typography/label/small` |
| Caption | `typography/caption/caption` |

Current Body / Label scale:

| Style | Desktop | Mobile | Weight |
|---|---:|---:|---|
| `typography/body/large` | 16 / 24 | 14 / 22 | Regular 400 |
| `typography/body/medium` | 14 / 22 | 13 / 20 | Regular 400 |
| `typography/body/small` | 12 / 18 | 12 / 16 | Regular 400 |
| `typography/label/large` | 16 / 20 | 14 / 20 | Medium 500 |
| `typography/label/medium` | 14 / 20 | 13 / 18 | Medium 500 |
| `typography/label/small` | 12 / 16 | 12 / 16 | Medium 500 |

Label should follow a similar size rhythm to Body, but use tighter line-height and Medium weight.

Do not use deprecated style aliases:

- `typography/display/xl`
- `typography/display/lg`
- `typography/display/md`
- `typography/display/sm`
- `typography/heading/xl`
- `typography/heading/lg`
- `typography/heading/md`
- `typography/heading/sm`
- `typography/body/lg`
- `typography/body/md`
- `typography/body/sm`
- `typography/label/lg`
- `typography/label/md`
- `typography/label/sm`
- `typography/caption/md`

## Component Doc Rules

For Button docs:

- Use `button-standard`, `button-icon`, and `button-loading`.
- Use variant naming like `Type=Filled, State=Default, Size=Default`.
- Use layer names like `icon/leading`, `label`, `icon/trailing`, `icon/only`, `loading/icon`, `loading/label`.
- Use `typography/label/small`, `typography/label/medium`, or `typography/label/large` for button labels by size.
- Filled brand button text/icon uses `color/content/inverse`.
- Destructive/error filled button uses `color/status/error/surface/*` and `color/content/inverse`.

For Input docs:

- Use `input/standard` and `input/horizontal`.
- Valid states: `Default`, `Hover`, `Filled`, `Focused`, `Focused - Filled`, `Error`, `Disabled`.
- Valid sizes: `Default`, `Small`.
- Use layer names like `Field`, `label`, `label/secondary`, `content`, `help-text`, `error-message`.
- Use `typography/label/medium` or `typography/label/small` for labels.
- Use `typography/body/medium` or `typography/body/small` for content, placeholders, helper text, and error messages.
- System active border uses `color/border/system`.
- Error/destructive border uses `color/border/error`.
- Error helper text/icon uses `color/status/error/content/default`.

## Figma Writing Workflow

When writing docs into Figma:

1. Use the `figma-use` skill before any `use_figma` call.
2. Inspect the target node first.
3. Place new documentation beside the source component or requested frame.
4. Match the established documentation style: large title, short description, section cards, tables, and AI rules.
5. Use auto-layout or stable sizing where possible.
6. Keep text frames readable and avoid overflow.
7. Return created or updated node IDs.
8. Validate with screenshot or metadata after writing.

## Markdown Writing Workflow

When writing `.md` docs:

1. Use the same terminology as Figma docs.
2. Include Figma node links or node IDs.
3. Use markdown tables for tokens, variants, states, and usage.
4. Include an `AI Implementation Rules` section.
5. Keep examples concrete.
6. Avoid long abstract explanation.

## AI Implementation Rules Template

Use or adapt this section in docs:

```text
## AI Implementation Rules

1. Use existing component variants before creating new UI.
2. Use semantic tokens only.
3. Do not use raw Tailwind colors directly in components.
4. Use typography/... text styles instead of local text overrides.
5. Preserve layer names and variant properties.
6. Do not create deprecated token groups.
7. If a needed state or token is missing, ask before inventing one.
```

## Validation Checklist

Before finishing, check:

- The doc follows Cariva naming and token rules.
- Deprecated token names are not present except in explicit "do not use" sections.
- Slash token names are used.
- Component states and variants match the actual Figma component.
- Typography guidance uses `typography/...`.
- System active border uses `color/border/system`; error/destructive border uses `color/border/error`.
- The final answer tells the user where the doc was created or updated.
