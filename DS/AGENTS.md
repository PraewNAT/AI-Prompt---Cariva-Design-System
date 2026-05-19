# Cariva Design System - AGENTS.md

## Stack
- UI Library: MUI v5, Wrapper pattern
- Font: IBM Plex Sans Thai (sans), IBM Plex Sans Thai Looped (serif)
- Figma: https://www.figma.com/design/XgxprkSY5mGbzIIwlmscCt/Cariva-Core-Design-System
- Handoff doc: design-system-ai-handoff.md
- Color doc: semantic-color-token-guideline.md

## Naming Convention
Figma ใช้ kebab-case -> Code ใช้ PascalCase แปลงให้อัตโนมัติ

cv-button-icon        ->  CvButtonIcon
cv-input-horizontal   ->  CvInputHorizontal
cv-ai-bubble-user     ->  CvAiBubbleUser

## Wrapper Rules
component ที่ wrap MUI:
cv-button-*    ->  wrap MuiButton
cv-input-*     ->  wrap MuiTextField
cv-select-*    ->  wrap MuiSelect
cv-checkbox-*  ->  wrap MuiCheckbox
cv-badge-*     ->  wrap MuiBadge
cv-chip-*      ->  wrap MuiChip

component ที่สร้างใหม่ ไม่ wrap:
cv-ai-bubble-*      ->  custom
cv-ai-streaming-*   ->  custom
cv-ai-suggest-*     ->  custom

## Token Rules
ใช้ semantic tokens เท่านั้น ห้ามใช้ raw Tailwind colors ใน component

ห้ามสร้าง:
- primitive tokens
- component-specific tokens
- color/danger/*
- color/field/*
- color/foreground/*
- color/border/invalid
- status border tokens
- color/content/success, warning, error, info
- tertiary tokens

ใช้ content สำหรับทั้ง text และ icon:
- color/content/primary       <- main text/icon
- color/content/secondary     <- supporting
- color/content/muted         <- low-emphasis
- color/content/placeholder   <- placeholder
- color/content/disabled      <- disabled
- color/content/inverse       <- text บน filled/dark bg

ใช้ status/error สำหรับ destructive และ error:
- color/status/error/surface/default   <- error bg
- color/status/error/content/default   <- error text/icon

ใช้ accent เฉพาะ non-semantic decorative (chart, avatar, tag):
- color/accent/{family}/200   <- soft surface
- color/accent/{family}/600   <- strong mark

## Border Rules
- color/border/system   <- system active field/component
- color/border/error    <- error/destructive field
- color/border/default  <- default border
- color/border/strong   <- hover border
- color/border/disabled <- disabled border

ห้ามใช้ชื่อเก่า:
- color/focus/ring/default
- color/focus/ring/error

## Brand Rules
Primary = blue -> color/brand/primary/*
Secondary = green -> color/brand/secondary/*

text/icon บน filled brand bg ใช้ color/content/inverse เสมอ

## Typography Rules
ใช้ text style เท่านั้น ห้าม override typography local

Display  -> landing/hero เท่านั้น
Heading  -> page/section/card hierarchy
Body     -> readable content, helper text
Label    -> button, tab, menu, form label
Caption  -> metadata, timestamp

Current text styles:
- typography/display/large, typography/display/medium, typography/display/small
- typography/heading/large, typography/heading/medium, typography/heading/small
- typography/body/large, typography/body/medium, typography/body/small
- typography/label/large, typography/label/medium, typography/label/small
- typography/caption/caption

Current Body / Label scale:

| Style | Desktop | Mobile | Weight |
|---|---:|---:|---|
| typography/body/large | 16 / 24 | 14 / 22 | Regular 400 |
| typography/body/medium | 14 / 22 | 13 / 20 | Regular 400 |
| typography/body/small | 12 / 18 | 12 / 16 | Regular 400 |
| typography/label/large | 16 / 20 | 14 / 20 | Medium 500 |
| typography/label/medium | 14 / 20 | 13 / 18 | Medium 500 |
| typography/label/small | 12 / 16 | 12 / 16 | Medium 500 |

Label ใช้ size rhythm ใกล้ Body แต่ line-height กระชับกว่าและ weight หนักกว่า

ตัวอย่าง:
- typography/label/medium <- button label default
- typography/body/medium  <- input content, help text
- typography/body/small <- small helper/detail

ห้ามสร้าง code typography style
ห้ามใช้ชื่อเก่า typography/display/xl, typography/display/lg, typography/display/md, typography/display/sm, typography/heading/xl, typography/heading/lg, typography/heading/md, typography/heading/sm, typography/body/lg, typography/body/md, typography/body/sm, typography/label/lg, typography/label/md, typography/label/sm, typography/caption/md
Mobile ให้เปลี่ยน Typography variable mode -> อย่าสร้าง style ซ้ำ

## Button Component
Component sets: button-standard, button-icon, button-loading
Variant pattern: Type=Filled, State=Default, Size=Default

Layer names:
- button-standard: icon/leading, label, icon/trailing
- button-icon: icon/only
- button-loading: loading/icon, loading/label

Filled brand button ใช้ color/content/inverse สำหรับ text/icon
Destructive button ใช้ color/status/error/surface/* และ color/content/inverse

## Input Component
Component sets: input/standard, input/horizontal
States: Default, Hover, Filled, Focused, Focused-Filled, Error, Disabled
Sizes: Default, Small

Layer names: Field, label, label/secondary, content, help-text, error-message

System active border -> color/border/system
Error border -> color/border/error
Error helper text -> color/status/error/content/default

## Accessibility
- Normal text: WCAG AA 4.5:1
- Large text/icon: 3:1
- ห้ามใช้สีอย่างเดียวสื่อความหมาย
- Error state ต้องมี message, icon หรือ label ประกอบ
- Disabled ต้องดูไม่ active แต่ยังอ่านได้

## AI Rules
1. ใช้ existing variants ก่อนสร้าง UI ใหม่
2. ใช้ semantic tokens เท่านั้น
3. ห้ามใช้ raw Tailwind colors ใน component
4. ใช้ typography/... text styles เสมอ
5. preserve layer names และ variant properties
6. ถ้า token หรือ state ที่ต้องการไม่มี ให้ถามก่อน อย่าสร้างเอง
