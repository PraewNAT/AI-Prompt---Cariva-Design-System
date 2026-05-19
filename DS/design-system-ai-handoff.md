# Cariva Design System AI Handoff

เอกสารนี้ใช้ส่งต่อ context ให้ AI ตัวอื่น หรือใช้เริ่มแชทใหม่ เพื่อให้เข้าใจ Cariva Core Design System โดยไม่ต้องอ่านประวัติแชทเดิมทั้งหมด

## Source of Truth

Figma file:
https://www.figma.com/design/XgxprkSY5mGbzIIwlmscCt/Cariva-Core-Design-System

Important Figma nodes:

| Area | Node ID | Notes |
|---|---:|---|
| Semantic Color Token Guideline | `3791:2` | Main semantic color documentation |
| Border Colors frame | `3791:722` | Includes border colors, `color/border/system`, `color/border/error`, and `system` effect style guidance |
| Typography Guideline | `3814:1454` | Typography styles, variables, Desktop/Mobile modes |
| Button section | `3646:404` | Button components and documentation |
| Button Documentation | `3803:553` | AI-readable button usage doc |
| Input section | `3760:5504` | Input components and documentation |
| Input Documentation | `3800:99` | AI-readable input usage doc |

Local docs:

| File | Purpose |
|---|---|
| `semantic-color-token-guideline.md` | Semantic color token usage and samples |
| `design-system-ai-handoff.md` | This handoff summary |

## Global Rules

- Use semantic tokens only.
- Do not use raw Tailwind colors directly in UI components.
- Primitive Tailwind color variables already exist. Do not create primitive tokens.
- Do not create component-specific color tokens.
- Do not create tertiary tokens.
- Do not create `field` tokens.
- Create/use `color/accent/*` only for non-semantic decorative accents such as charts, avatars, tags, illustrations, and visual grouping.
- Do not create `danger` tokens.
- Do not use `foreground`.
- Use `content` for both text and icons.
- Do not create separate text and icon token groups.
- Do not create `color.content.success`, `color.content.warning`, `color.content.error`, or `color.content.info`.
- Use `color/status/*` for success, warning, error, and info meanings.
- Do not create or use status border tokens; they have been removed.
- Destructive or risky actions use `status/error`, not `danger`.
- Components should use semantic tokens and shared styles, not local raw values.

## Naming Style

Figma variables use slash naming:

```text
color/brand/primary/surface/default
color/content/primary
color/border/system
typography/body/medium/font-size
typography/font-family/sans
```

Documentation may also mention dot notation for readability:

```text
color.brand.primary.surface.default
color.content.primary
color.border.focus.default
```

When implementing or inspecting in Figma, use the actual slash variable names.

## Semantic Color Groups

Current semantic color groups:

- `color/bg/*`
- `color/surface/*`
- `color/surface/action/*`
- `color/content/*`
- `color/content/link/*`
- `color/border/*`
- `color/border/system`
- `color/border/error`
- `color/brand/primary/*`
- `color/brand/secondary/*`
- `color/status/success/*`
- `color/status/warning/*`
- `color/status/error/*`
- `color/status/info/*`
- `color/accent/*`
- `color/overlay/*`

Do not add:

- `color/danger/*`
- `color/field/*`
- `color/foreground/*`
- `color/border/invalid`

## Accent Rules

Accent tokens are allowed only for non-semantic decorative color grouping. They are useful for charts, avatars, tags, illustrations, and visual grouping where the color does not mean success, warning, error, info, destructive, or brand.

Accent variables live under `color/accent/{family}/{shade}` and are available in these families:

`red`, `orange`, `amber`, `yellow`, `lime`, `green`, `emerald`, `teal`, `cyan`, `sky`, `blue`, `indigo`, `violet`, `purple`, `fuchsia`, `pink`, `rose`.

Mapping rule:

| Token depth | Use for | Light Theme | Dark Theme |
|---|---|---|---|
| `color/accent/{family}/200` | Soft accent surface or subtle visual grouping | `{family}.200` | `{family}.900` |
| `color/accent/{family}/600` | Strong accent mark, icon, label, or chart series | `{family}.600` | `{family}.300` |

Do not use accent tokens for status meaning. Use `color/status/*` for success, warning, error, and info. Do not use accent tokens for primary/secondary brand actions; use `color/brand/*`.

## Brand Rules

Primary brand = blue.

Secondary brand = green.

Use brand tokens for:

- primary and secondary brand expression
- brand-colored text or icons
- selected or active brand states
- filled primary or secondary actions

Important rule:

- Text or icons on filled brand backgrounds should use `color/content/inverse`.
- Brand content tokens represent brand-colored text/icons, not white.

Examples:

| Usage | Token |
|---|---|
| Primary filled button background | `color/brand/primary/surface/default` |
| Primary filled button hover | `color/brand/primary/surface/hover` |
| Primary filled button pressed | `color/brand/primary/surface/pressed` |
| Text/icon on primary filled button | `color/content/inverse` |
| Primary brand text/icon | `color/brand/primary/content/default` |
| Strong primary brand text/icon | `color/brand/primary/content/strong` |
| Secondary filled button background | `color/brand/secondary/surface/default` |
| Text/icon on secondary filled button | `color/content/inverse` |

## Content Rules

Use `color/content/*` for general readable UI content:

- text
- icons
- labels
- helper text
- table text
- menu item content
- normal UI copy

Common usage:

| Usage | Token |
|---|---|
| Main readable content | `color/content/primary` |
| Supporting content | `color/content/secondary` |
| Low-emphasis readable content | `color/content/muted` |
| Placeholder | `color/content/placeholder` |
| Disabled text/icon | `color/content/disabled` |
| Text/icon on filled or dark backgrounds | `color/content/inverse` |
| Link default | `color/content/link/default` |
| Link hover | `color/content/link/hover` |
| Link pressed | `color/content/link/pressed` |

Do not use content tokens for success, warning, error, or info meaning. Use `color/status/*`.

## Border System Rules

System and error border tokens now live under `color/border/*`. System active field/control states use `color/border/system`; error or destructive field/control borders use `color/border/error`. The shared `system` effect style is used for keyboard-visible interaction rings.

Use:

| Usage | Token |
|---|---|
| System active field/component border | `color/border/system` |
| Error/destructive field/component border | `color/border/error` |
| System ring effect | `system` effect style |

Do not use old names:

- `color/focus/ring/default`
- `color/focus/ring/error`
- `color.focus.ring.default`
- `color.focus.ring.error`

For form-like UI:

| Field State | Token |
|---|---|
| Default border | `color/border/default` |
| Hover border | `color/border/strong` |
| System active border | `color/border/system` |
| Error/destructive border | `color/border/error` |
| Disabled border | `color/border/disabled` |

## Status Rules

Use status tokens for feedback and meaning:

- success
- warning
- error
- info

Use `status/error` for destructive or risky actions too.

Examples:

| Usage | Token |
|---|---|
| Error filled action background | `color/status/error/surface/default` |
| Error hover background | `color/status/error/surface/hover` |
| Error pressed background | `color/status/error/surface/pressed` |
| Error text/icon | `color/status/error/content/default` |
| Strong error text/icon | `color/status/error/content/strong` |
| Error helper text | `color/status/error/content/default` |

Important:

- Text/icon on filled error backgrounds should use `color/content/inverse`.
- Status content tokens represent status-colored text/icons, not white.
- Status border tokens have been removed. Use normal border tokens for neutral borders and `color/border/error` for error/destructive field/control borders.

## Form-like UI Without Field Tokens

There are no field tokens.

Input, select, textarea, combobox, search field, and date picker should use surface, border, border focus, content, and status content tokens for helper/error text.

| Field Part | Token |
|---|---|
| Background | `color/surface/default` |
| Hover background | `color/surface/action/hover` |
| Disabled background | `color/surface/action/disabled` |
| Default border | `color/border/default` |
| Hover border | `color/border/strong` |
| System active border | `color/border/system` |
| Error/destructive border | `color/border/error` |
| Text/icon | `color/content/primary` |
| Placeholder | `color/content/placeholder` |
| Disabled text/icon | `color/content/disabled` |
| Error helper/icon | `color/status/error/content/default` |

Important: system active fields use `color/border/system`; error/destructive fields use `color/border/error`. Status border tokens have been removed and must not be used for field/control borders.

## Typography

Typography variables and text styles exist in Figma.

Main font:

| Variable | Value |
|---|---|
| `typography/font-family/sans` | IBM Plex Sans Thai |
| `typography/font-family/serif` | IBM Plex Sans Thai Looped |

Global font weight variables:

| Variable | Value |
|---|---:|
| `typography/font-weight/regular` | 400 |
| `typography/font-weight/medium` | 500 |
| `typography/font-weight/semibold` | 600 |
| `typography/font-weight/bold` | 700 |

Use text styles instead of local typography overrides:

| Style | Desktop | Mobile | Weight | Usage |
|---|---|---|---|---|
| `typography/display/large` | 64 / 72 | 40 / 48 | 700 | Hero display, landing page headline, highest-impact title |
| `typography/display/medium` | 48 / 56 | 36 / 44 | 700 | Large marketing headline or high-emphasis display title |
| `typography/display/small` | 40 / 48 | 32 / 40 | 600 | Medium display title for landing sections |
| `typography/heading/large` | 28 / 36 | 24 / 32 | 600 | Section heading or modal title |
| `typography/heading/medium` | 24 / 32 | 20 / 28 | 600 | Card title, panel heading, grouped content title |
| `typography/heading/small` | 20 / 28 | 18 / 24 | 600 | Small section heading or compact component title |
| `typography/body/large` | 16 / 24 | 14 / 22 | 400 | Large body copy and high-readability long text |
| `typography/body/medium` | 14 / 22 | 13 / 20 | 400 | Default UI copy |
| `typography/body/small` | 12 / 18 | 12 / 16 | 400 | Small body text, helper detail, compact table content |
| `typography/label/large` | 16 / 20 | 14 / 20 | 500 | Large control labels |
| `typography/label/medium` | 14 / 20 | 13 / 18 | 500 | Default button/menu/field labels |
| `typography/label/small` | 12 / 16 | 12 / 16 | 500 | Small labels and badges |
| `typography/caption/caption` | 12 / 16 | 12 / 16 | 400 | Metadata, timestamp, caption |

Rules:

- Do not create a `code` typography style.
- Do not use deprecated style aliases such as `typography/display/xl`, `typography/display/lg`, `typography/display/md`, `typography/display/sm`, `typography/heading/xl`, `typography/heading/lg`, `typography/heading/md`, `typography/heading/sm`, `typography/body/lg`, `typography/body/md`, `typography/body/sm`, `typography/label/lg`, `typography/label/md`, `typography/label/sm`, or `typography/caption/md`.
- Use Display only for landing/hero content.
- Use Heading for page/section/card hierarchy.
- Use Body for readable content.
- Use Label for controls and actions. Label uses the same mobile size rhythm as Body, but with tighter line-height and Medium weight.
- Use Caption for low-emphasis metadata.
- For mobile, switch Typography variable mode to Mobile instead of creating duplicate mobile styles.

## Button Component

Source node:

```text
Button section: 3646:404
Button Documentation: 3803:553
```

Component sets:

| Component Set | Node ID | Notes |
|---|---:|---|
| `button-standard` | `3646:28000` | Text button variants |
| `button-icon` | `3730:5246` | Icon-only button variants |
| `button-loading` | `3730:5454` | Loading button variants |

Variant naming pattern:

```text
Type=Filled, State=Default, Size=Default
Type=Outline, State=Hover, Size=Small
Type=Destructive, State=Pressed, Size=Large
```

Button layer naming:

```text
button-standard
  Type=Filled, State=Default, Size=Default
    icon/leading
    label
    icon/trailing

button-icon
  Type=Filled, State=Default, Size=Default
    icon/only

button-loading
  Type=Filled, Size=Default
    loading/icon
    loading/label
```

Typography:

- `button-standard` labels use `typography/label/medium`.
- `button-loading` uses `typography/label/small`, `typography/label/medium`, or `typography/label/large` by size.
- `button-icon` has no text.

Button color usage:

| Button Type | Background | Text/Icon |
|---|---|---|
| Filled primary | `color/brand/primary/surface/default` | `color/content/inverse` |
| Filled primary hover | `color/brand/primary/surface/hover` | `color/content/inverse` |
| Filled primary pressed | `color/brand/primary/surface/pressed` | `color/content/inverse` |
| Outline | `color/surface/default` or transparent | `color/content/secondary` |
| Ghost | transparent | `color/brand/primary/content/default` |
| Link | transparent | `color/content/link/default` |
| Destructive/Error filled | `color/status/error/surface/default` | `color/content/inverse` |
| Disabled | `color/surface/action/disabled` | `color/content/disabled` |

## Input Component

Source node:

```text
Input section: 3760:5504
Input Documentation: 3800:99
```

Component sets:

| Component Set | Node ID | Notes |
|---|---:|---|
| `input/standard` | `3760:6623` | Vertical input layout |
| `input/horizontal` | `3760:6895` | Horizontal/inline input layout |

States:

```text
Default
Hover
Filled
Focused
Focused - Filled
Error
Disabled
```

Sizes:

```text
Default
Small
```

Input layer naming:

```text
Field
label
label/secondary
content
help-text
error-message
```

Typography:

- Label text uses `typography/label/medium` or `typography/label/small`.
- Content, placeholder, help text, and error message use `typography/body/medium` or `typography/body/small`.
- No Input component text should use Geist or old Tailwind text styles.

Input color usage:

| Part | Token |
|---|---|
| Field background | `color/surface/default` |
| Hover background | `color/surface/action/hover` |
| Disabled background | `color/surface/action/disabled` |
| Default border | `color/border/default` |
| Hover border | `color/border/strong` |
| System active border | `color/border/system` |
| Error/destructive border | `color/border/error` |
| Label | `color/content/primary` |
| Secondary label | `color/content/secondary` |
| Placeholder | `color/content/placeholder` |
| Value | `color/content/primary` |
| Help text | `color/content/muted` |
| Error message | `color/status/error/content/default` |
| Disabled content | `color/content/disabled` |

## Accessibility Rules

- Normal text should meet WCAG AA 4.5:1 where possible.
- Large text or large icons should meet at least 3:1.
- System active border must use `color/border/system`; error/destructive border must use `color/border/error`.
- Disabled state should look inactive but still be readable.
- Do not rely on opacity alone for disabled states.
- Do not use color alone to communicate meaning.
- Error states should include message, icon, label, or another non-color cue where needed.

## Current Audit Notes

Button and Input have been updated to use the new typography styles.

Known clean state:

- No `Geist` font remains inside Button/Input component text layers.
- No old text styles remain inside Button/Input component text layers.
- Input system active strokes use `color/border/system`; error/destructive strokes use `color/border/error`.
- Button layer names are AI-readable.
- Input `Conent` typo was corrected to `content`.
- Hidden raw black fills may still exist inside icon vector internals, but they are not effectively visible. Clean icon masters later if a perfectly clean audit is required.

## Prompt Starter for Another AI

Use this prompt when opening a new chat:

```text
You are helping with the Cariva Core Design System in Figma.

Use the Figma file and this handoff document as source of truth.
Use semantic tokens only. Do not use raw Tailwind colors in UI components.
Do not create primitive tokens, field tokens, danger tokens, foreground tokens, tertiary tokens, or component-specific color tokens. Accent tokens already exist; use `color/accent/*` only for non-semantic decorative accents.
Use content tokens for both text and icons.
Use status/error for destructive and error meanings.
Use color/border/system for system active component borders. Use color/border/error only for error/destructive field/control borders. Status border tokens have been removed; do not recreate them.
Use typography/... text styles and Typography variables. Main font is IBM Plex Sans Thai.
Do not create code typography style.

Before editing components, inspect existing variants and preserve component structure.
For Button and Input, use the documented component sets, semantic tokens, typography styles, and AI-readable layer names.
```
