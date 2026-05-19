# Semantic Color Token Guideline

เอกสารนี้อธิบายวิธีใช้ Semantic Color Tokens ใน Design System โดยยึด token name และ mapping จาก Figma Variables ปัจจุบัน

## Core Rules

- ใช้ semantic color tokens เท่านั้นใน UI components
- Primitive colors ใช้เป็น source layer เท่านั้น ไม่ใช้ตรงใน component
- Token naming ใช้ slash format เช่น `color/brand/primary/surface/default`
- ใช้ `content` สำหรับทั้ง text และ icons
- ไม่ใช้คำว่า `foreground`
- ไม่แยก text token กับ icon token
- ไม่สร้าง component-specific token เช่น `button/primary/bg`
- ใช้ `color/accent/*` ได้เฉพาะ non-semantic decorative accent เช่น chart, avatar, tag, illustration หรือ visual grouping ที่ไม่ใช่ brand/status
- ไม่ใช้ `danger` group แล้ว ให้ใช้ `color/status/error/*` สำหรับ destructive/error meaning
- Status border tokens have been removed เพื่อไม่ให้สับสนกับ field/control borders
- `bg` ใช้เฉพาะ page-level background ชั้นล่างสุด เช่น page, subtle page, inverse page
- `surface` ใช้กับพื้นที่ UI ที่เป็น component/container/action surface

## Naming Meaning

| Term | Meaning |
|---|---|
| `bg` | Page-level background ชั้นล่างสุดของหน้าหรือ app shell |
| `surface` | Component/container/action background เช่น card, input, menu, selected state, filled button |
| `content` | Text/icon/readable content |
| `border` | Stroke, divider, outline |
| `default` | Normal state |
| `hover` | Hover state |
| `pressed` | Pressed/active state |
| `subtle` | Low-emphasis surface |
| `muted` | Stronger low-emphasis surface |
| `strong` | Higher-emphasis content/border |
| `disabled` | Disabled state using explicit colors, not opacity only |

## Important Usage Rules

### Brand content is brand-colored content

`color/brand/*/content/*` means brand-colored text/icon on neutral or light/dark surfaces.

Do not use brand content tokens as white text on filled brand buttons.

Primary filled button:

| Part | Token |
|---|---|
| Background | `color/brand/primary/surface/default` |
| Hover | `color/brand/primary/surface/hover` |
| Pressed | `color/brand/primary/surface/pressed` |
| Text/Icon | `color/content/inverse` |

Primary brand text/icon:

| Part | Token |
|---|---|
| Default | `color/brand/primary/content/default` |
| Strong | `color/brand/primary/content/strong` |

### Destructive actions use status error

Component variants may still use the word `Destructive`, but color mapping should use `color/status/error/*`.

Destructive filled button:

| Part | Token |
|---|---|
| Background | `color/status/error/surface/default` |
| Hover | `color/status/error/surface/hover` |
| Pressed | `color/status/error/surface/pressed` |
| Text/Icon | `color/content/inverse` |

Destructive text/icon:

| Part | Token |
|---|---|
| Default | `color/status/error/content/default` |
| Strong | `color/status/error/content/strong` |

### Form-like UI without field tokens

| Field Part | Token |
|---|---|
| Background | `color/surface/default` |
| Hover background | `color/surface/action/hover` |
| Disabled background | `color/surface/action/disabled` |
| Border | `color/border/default` |
| Hover border | `color/border/strong` |
| System active border | `color/border/system` |
| Error/destructive focus border | `color/border/error` |
| Text/Icon | `color/content/primary` |
| Placeholder | `color/content/placeholder` |
| Disabled text/icon | `color/content/disabled` |
| Error helper/icon | `color/status/error/content/default` |


## Color Samples

ตัวอย่างสีด้านล่างช่วยให้คนอ่านเห็นภาพเร็วขึ้นว่าแต่ละ semantic group map ไปที่สีประมาณไหนใน Light และ Dark Theme

### Brand Samples

| Group | Light Theme | Dark Theme |
|---|---|---|
| Primary brand | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#155DFC;border:1px solid #E2E8F0;"></span> blue.600 `#155DFC` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#2B7FFF;border:1px solid #314158;"></span> blue.500 `#2B7FFF` |
| Primary subtle | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#EFF6FF;border:1px solid #E2E8F0;"></span> blue.50 `#EFF6FF` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#162456;border:1px solid #314158;"></span> blue.950 `#162456` |
| Secondary brand | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#007A55;border:1px solid #E2E8F0;"></span> emerald.700 `#007A55` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#00BC7D;border:1px solid #314158;"></span> emerald.500 `#00BC7D` |
| Secondary subtle | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#ECFDF5;border:1px solid #E2E8F0;"></span> emerald.50 `#ECFDF5` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#002C22;border:1px solid #314158;"></span> emerald.950 `#002C22` |

### Neutral Samples

| Group | Light Theme | Dark Theme |
|---|---|---|
| Page background | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#F8FAFC;border:1px solid #E2E8F0;"></span> slate.50 `#F8FAFC` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#020618;border:1px solid #314158;"></span> slate.950 `#020618` |
| Surface default | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#FFFFFF;border:1px solid #E2E8F0;"></span> white `#FFFFFF` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#0F172B;border:1px solid #314158;"></span> slate.900 `#0F172B` |
| Content primary | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#020618;border:1px solid #E2E8F0;"></span> slate.950 `#020618` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#F8FAFC;border:1px solid #314158;"></span> slate.50 `#F8FAFC` |
| Border default | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#E2E8F0;border:1px solid #CBD5E1;"></span> slate.200 `#E2E8F0` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#314158;border:1px solid #64748B;"></span> slate.700 `#314158` |

### Status Samples

| Status | Light Theme | Dark Theme |
|---|---|---|
| Success | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#009966;border:1px solid #E2E8F0;"></span> emerald.600 `#009966` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#00BC7D;border:1px solid #314158;"></span> emerald.500 `#00BC7D` |
| Warning | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#E17100;border:1px solid #E2E8F0;"></span> amber.600 `#E17100` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#FD9A00;border:1px solid #314158;"></span> amber.500 `#FD9A00` |
| Error / Destructive | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#E7000B;border:1px solid #E2E8F0;"></span> red.600 `#E7000B` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#FB2C36;border:1px solid #314158;"></span> red.500 `#FB2C36` |
| Info | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#0084D1;border:1px solid #E2E8F0;"></span> sky.600 `#0084D1` | <span style="display:inline-block;width:40px;height:16px;border-radius:4px;background:#00A6F4;border:1px solid #314158;"></span> sky.500 `#00A6F4` |

## Token Reference

### Brand

Use Brand tokens for brand identity, primary/secondary actions, active brand states, and brand emphasis.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/brand/primary/surface/default` | Primary filled action surface | blue.600 `#155DFC` | blue.500 `#2B7FFF` |
| `color/brand/primary/surface/hover` | Hover state for primary filled action | blue.700 `#1447E6` | blue.400 `#51A2FF` |
| `color/brand/primary/surface/pressed` | Pressed state for primary filled action | blue.800 `#193CB8` | blue.300 `#8EC5FF` |
| `color/brand/primary/surface/subtle` | Subtle selected/active brand surface | blue.50 `#EFF6FF` | blue.950 `#162456` |
| `color/brand/primary/surface/muted` | Stronger soft brand surface, badge/chip | blue.100 `#DBEAFE` | blue.900 `#1C398E` |
| `color/brand/primary/content/default` | Primary brand text/icon | blue.600 `#155DFC` | blue.300 `#8EC5FF` |
| `color/brand/primary/content/strong` | Strong primary brand text/icon | blue.700 `#1447E6` | blue.200 `#BEDBFF` |
| `color/brand/primary/border/default` | Soft primary brand border | blue.300 `#8EC5FF` | blue.700 `#1447E6` |
| `color/brand/primary/border/strong` | Strong primary brand border | blue.500 `#2B7FFF` | blue.500 `#2B7FFF` |
| `color/brand/secondary/surface/default` | Secondary filled action surface | emerald.700 `#007A55` | emerald.500 `#00BC7D` |
| `color/brand/secondary/surface/hover` | Hover state for secondary filled action | emerald.800 `#006045` | emerald.400 `#00D492` |
| `color/brand/secondary/surface/pressed` | Pressed state for secondary filled action | emerald.900 `#004F3B` | emerald.300 `#5EE9B5` |
| `color/brand/secondary/surface/subtle` | Subtle secondary brand surface | emerald.50 `#ECFDF5` | emerald.950 `#002C22` |
| `color/brand/secondary/surface/muted` | Stronger soft secondary brand surface | emerald.100 `#D0FAE5` | emerald.900 `#004F3B` |
| `color/brand/secondary/content/default` | Secondary brand text/icon | emerald.600 `#009966` | emerald.300 `#5EE9B5` |
| `color/brand/secondary/content/strong` | Strong secondary brand text/icon | emerald.700 `#007A55` | emerald.200 `#A4F4CF` |
| `color/brand/secondary/border/default` | Soft secondary brand border | emerald.300 `#5EE9B5` | emerald.700 `#007A55` |
| `color/brand/secondary/border/strong` | Strong secondary brand border | emerald.500 `#00BC7D` | emerald.500 `#00BC7D` |

### Content

Use Content tokens for readable text/icons, labels, helper text, menu items, table text, and links.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/content/primary` | Highest-emphasis readable content | slate.950 `#020618` | slate.50 `#F8FAFC` |
| `color/content/secondary` | Supporting text/icon | slate.700 `#314158` | slate.300 `#CAD5E2` |
| `color/content/muted` | Low-emphasis readable content | slate.500 `#62748E` | slate.400 `#90A1B9` |
| `color/content/placeholder` | Placeholder and empty input hint | slate.500 `#62748E` | slate.400 `#90A1B9` |
| `color/content/disabled` | Disabled text/icon | slate.400 `#90A1B9` | slate.400 `#90A1B9` |
| `color/content/inverse` | Text/icon on filled or inverse surfaces | white `#FFFFFF` | slate.950 `#020618` |
| `color/content/link/default` | Default link | blue.600 `#155DFC` | blue.400 `#51A2FF` |
| `color/content/link/hover` | Link hover | blue.700 `#1447E6` | blue.300 `#8EC5FF` |
| `color/content/link/pressed` | Link pressed | blue.800 `#193CB8` | blue.200 `#BEDBFF` |
| `color/content/link/disabled` | Disabled link | slate.600 `#45556C` | slate.400 `#90A1B9` |

### Background

Use `bg` only for page-level backgrounds, not component action surfaces.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/bg/page` | Main page/app background | slate.50 `#F8FAFC` | slate.950 `#020618` |
| `color/bg/subtle` | Subtle page/app shell background | slate.100 `#F1F5F9` | slate.900 `#0F172B` |
| `color/bg/inverse` | Inverse page/background area | slate.950 `#020618` | white `#FFFFFF` |

### Surface

Use Surface tokens for cards, panels, inputs, popovers, rows, menus, selected areas, and neutral action states.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/surface/default` | Default component/container surface | white `#FFFFFF` | slate.900 `#0F172B` |
| `color/surface/subtle` | Softer neutral surface | slate.50 `#F8FAFC` | slate.800 `#1D293D` |
| `color/surface/elevated` | Dropdown, popover, floating panel | white `#FFFFFF` | slate.800 `#1D293D` |
| `color/surface/sunken` | Recessed/inset surface | slate.100 `#F1F5F9` | slate.950 `#020618` |
| `color/surface/overlay` | Modal/dialog/popover surface | white `#FFFFFF` | slate.900 `#0F172B` |
| `color/surface/action/hover` | Neutral hover surface | slate.100 `#F1F5F9` | slate.800 `#1D293D` |
| `color/surface/action/pressed` | Neutral pressed surface | slate.200 `#E2E8F0` | slate.700 `#314158` |
| `color/surface/action/selected` | Selected neutral/brand-tinted surface | blue.50 `#EFF6FF` | blue.950 `#162456` |
| `color/surface/action/disabled` | Disabled neutral surface | slate.100 `#F1F5F9` | slate.800 `#1D293D` |

### Border

Use Border tokens for neutral strokes, outlines, dividers, and component borders.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/border/default` | Default neutral border/divider | slate.200 `#E2E8F0` | slate.700 `#314158` |
| `color/border/strong` | Stronger neutral border/hover border | slate.300 `#CAD5E2` | slate.600 `#45556C` |
| `color/border/disabled` | Disabled border | slate.200 `#E2E8F0` | slate.800 `#1D293D` |

### Status

Use Status tokens for feedback, alerts, validation messages, helper states, badges, toast, and alert surfaces. Status tokens use surface/content only. Status border tokens have been removed.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/status/success/surface/default` | Filled success surface | emerald.600 `#009966` | emerald.500 `#00BC7D` |
| `color/status/success/surface/hover` | Success hover surface | emerald.700 `#007A55` | emerald.400 `#00D492` |
| `color/status/success/surface/pressed` | Success pressed surface | emerald.800 `#006045` | emerald.300 `#5EE9B5` |
| `color/status/success/surface/subtle` | Success alert background | emerald.50 `#ECFDF5` | emerald.950 `#002C22` |
| `color/status/success/surface/muted` | Success badge/chip background | emerald.100 `#D0FAE5` | emerald.900 `#004F3B` |
| `color/status/success/content/default` | Success text/icon | emerald.600 `#009966` | emerald.300 `#5EE9B5` |
| `color/status/success/content/strong` | Strong success text/icon | emerald.700 `#007A55` | emerald.200 `#A4F4CF` |
| `color/status/warning/surface/default` | Filled warning surface | amber.600 `#E17100` | amber.500 `#FD9A00` |
| `color/status/warning/surface/hover` | Warning hover surface | amber.700 `#BB4D00` | amber.400 `#FFBA00` |
| `color/status/warning/surface/pressed` | Warning pressed surface | amber.800 `#973C00` | amber.300 `#FFD230` |
| `color/status/warning/surface/subtle` | Warning alert background | amber.50 `#FFFBEB` | amber.950 `#461901` |
| `color/status/warning/surface/muted` | Warning badge/chip background | amber.100 `#FEF3C6` | amber.900 `#7B3306` |
| `color/status/warning/content/default` | Warning text/icon | amber.600 `#E17100` | amber.300 `#FFD230` |
| `color/status/warning/content/strong` | Strong warning text/icon | amber.700 `#BB4D00` | amber.200 `#FEE685` |
| `color/status/error/surface/default` | Filled error/destructive surface | red.600 `#E7000B` | red.500 `#FB2C36` |
| `color/status/error/surface/hover` | Error/destructive hover surface | red.700 `#C10007` | red.400 `#FF6467` |
| `color/status/error/surface/pressed` | Error/destructive pressed surface | red.800 `#9F0712` | red.300 `#FFA2A2` |
| `color/status/error/surface/subtle` | Error alert background | red.50 `#FEF2F2` | red.950 `#460809` |
| `color/status/error/surface/muted` | Error badge/chip background | red.100 `#FFE2E2` | red.900 `#82181A` |
| `color/status/error/content/default` | Error/destructive text/icon | red.600 `#E7000B` | red.300 `#FFA2A2` |
| `color/status/error/content/strong` | Strong error/destructive text/icon | red.700 `#C10007` | red.200 `#FFC9C9` |
| `color/status/info/surface/default` | Filled info surface | sky.600 `#0084D1` | sky.500 `#00A6F4` |
| `color/status/info/surface/hover` | Info hover surface | sky.700 `#0069A8` | sky.400 `#00BCFF` |
| `color/status/info/surface/pressed` | Info pressed surface | sky.800 `#00598A` | sky.300 `#74D4FF` |
| `color/status/info/surface/subtle` | Info alert background | sky.50 `#F0F9FF` | sky.950 `#052F4A` |
| `color/status/info/surface/muted` | Info badge/chip background | sky.100 `#DFF2FE` | sky.900 `#024A70` |
| `color/status/info/content/default` | Info text/icon | sky.600 `#0084D1` | sky.300 `#74D4FF` |
| `color/status/info/content/strong` | Strong info text/icon | sky.700 `#0069A8` | sky.200 `#B8E6FE` |

### Accent

Use Accent tokens for non-semantic decorative color grouping, data visualization, avatars, tags, illustrations, and product UI accents that are not brand and not status. Accent tokens are semantic utility tokens that alias to primitive Tailwind colors.

Rules:

- Use accent only when the color does not communicate success, warning, error, or info.
- Do not use accent for primary brand actions; use `color/brand/*` instead.
- Each accent family has exactly two token depths.
- `/200` is the soft accent: Light Theme maps to shade 200; Dark Theme maps to shade 900.
- `/600` is the strong accent: Light Theme maps to shade 600; Dark Theme maps to shade 300.

| Family | Soft token | Light | Dark | Strong token | Light | Dark |
|---|---|---|---|---|---|---|
| red | `color/accent/red/200` | red.200 `#FFC9C9` | red.900 `#82181A` | `color/accent/red/600` | red.600 `#E7000B` | red.300 `#FFA2A2` |
| orange | `color/accent/orange/200` | orange.200 `#FFD6A8` | orange.900 `#7E2A0C` | `color/accent/orange/600` | orange.600 `#F54A00` | orange.300 `#FFB86A` |
| amber | `color/accent/amber/200` | amber.200 `#FEE685` | amber.900 `#7B3306` | `color/accent/amber/600` | amber.600 `#E17100` | amber.300 `#FFD230` |
| yellow | `color/accent/yellow/200` | yellow.200 `#FFF085` | yellow.900 `#733E0A` | `color/accent/yellow/600` | yellow.600 `#D08700` | yellow.300 `#FFDF20` |
| lime | `color/accent/lime/200` | lime.200 `#D8F999` | lime.900 `#35530E` | `color/accent/lime/600` | lime.600 `#5EA500` | lime.300 `#BBF451` |
| green | `color/accent/green/200` | green.200 `#B9F8CF` | green.900 `#0D542B` | `color/accent/green/600` | green.600 `#00A63E` | green.300 `#7BF1A8` |
| emerald | `color/accent/emerald/200` | emerald.200 `#A4F4CF` | emerald.900 `#004F3B` | `color/accent/emerald/600` | emerald.600 `#009966` | emerald.300 `#5EE9B5` |
| teal | `color/accent/teal/200` | teal.200 `#96F7E4` | teal.900 `#0B4F4A` | `color/accent/teal/600` | teal.600 `#009689` | teal.300 `#46ECD5` |
| cyan | `color/accent/cyan/200` | cyan.200 `#A2F4FD` | cyan.900 `#104E64` | `color/accent/cyan/600` | cyan.600 `#0092B8` | cyan.300 `#53EAFD` |
| sky | `color/accent/sky/200` | sky.200 `#B8E6FE` | sky.900 `#024A70` | `color/accent/sky/600` | sky.600 `#0084D1` | sky.300 `#74D4FF` |
| blue | `color/accent/blue/200` | blue.200 `#BEDBFF` | blue.900 `#1C398E` | `color/accent/blue/600` | blue.600 `#155DFC` | blue.300 `#8EC5FF` |
| indigo | `color/accent/indigo/200` | indigo.200 `#C6D2FF` | indigo.900 `#312C85` | `color/accent/indigo/600` | indigo.600 `#4F39F6` | indigo.300 `#A3B3FF` |
| violet | `color/accent/violet/200` | violet.200 `#DDD6FF` | violet.900 `#4D179A` | `color/accent/violet/600` | violet.600 `#7F22FE` | violet.300 `#C4B4FF` |
| purple | `color/accent/purple/200` | purple.200 `#E9D4FF` | purple.900 `#59168B` | `color/accent/purple/600` | purple.600 `#9810FA` | purple.300 `#DAB2FF` |
| fuchsia | `color/accent/fuchsia/200` | fuchsia.200 `#F6CFFF` | fuchsia.900 `#721378` | `color/accent/fuchsia/600` | fuchsia.600 `#C800DE` | fuchsia.300 `#F4A8FF` |
| pink | `color/accent/pink/200` | pink.200 `#FCCEE8` | pink.900 `#861043` | `color/accent/pink/600` | pink.600 `#E60076` | pink.300 `#FDA5D5` |
| rose | `color/accent/rose/200` | rose.200 `#FFCCD3` | rose.900 `#8B0836` | `color/accent/rose/600` | rose.600 `#EC003F` | rose.300 `#FFA1AD` |

### Border

Use Border tokens for neutral, system active, and error component borders. System active states use `color/border/system`; error or destructive states use `color/border/error`.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/border/system` | System active field/component border | blue.600 `#155DFC` | blue.400 `#51A2FF` |
| `color/border/error` | Error/destructive field/component border | red.600 `#E7000B` | red.400 `#FF6467` |

### Effect Styles

Use effect styles for reusable visual effects. System ring should use the shared `system` effect style instead of local drop shadows.

| Style | Usage | Token binding | Notes |
|---|---|---|---|
| `system` | Outer keyboard-visible interaction ring for interactive controls | `color/border/system` | Use together with system active border. Error/destructive states use `color/border/error` for the field/control stroke. |

### Overlay

Use Overlay tokens for modal backdrops, drawer backdrops, and scrims.

| Token | Usage | Light | Dark |
|---|---|---|---|
| `color/overlay/backdrop` | Normal modal/drawer backdrop | black / 40% `#000000 / 40%` | black / 60% `#000000 / 60%` |
| `color/overlay/backdrop/strong` | Stronger backdrop for critical or high-emphasis flows | black / 60% `#000000 / 60%` | black / 80% `#000000 / 80%` |
| `color/overlay/scrim` | Light scrim over image or content | black / 20% `#000000 / 20%` | black / 40% `#000000 / 40%` |

## Accessibility Notes

- Normal readable text should meet WCAG AA 4.5:1 where possible
- Large text and large icons should meet at least 3:1
- Focus indicators must be visually clear
- Disabled state should use explicit disabled tokens and should not rely on opacity alone
- Do not use color alone to communicate status; pair color with text, icon, or label
- If a token pairing fails contrast in real component usage, adjust the semantic mapping while keeping the token name stable
