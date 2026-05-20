# Design Tokens — Virtual Ambassador QR Solution Admin
> Source: Figma file `SUbO7gaqt5ElgmTKszGHqh` | Generated: 2026-05-20

---

## Color

### Primitive

| Token | Value |
|---|---|
| `--color-white` | `#ffffff` |

### Semantic — Text

| Token | Value | Usage |
|---|---|---|
| `--color-text-primary` | `#e7e9ea` | 본문 주요 텍스트 |
| `--color-text-secondary` | `#aebbcc` | 보조 텍스트, 레이블 |
| `--color-text-muted` | `#91a3c5` | 비활성 / 힌트 텍스트 |
| `--color-text-btn-primary` | `#006bea` | 텍스트 버튼 강조색 |

### Semantic — Icon

| Token | Value | Usage |
|---|---|---|
| `--color-icon-primary` | `#e7e9ea` | 기본 아이콘 |
| `--color-icon-subtle` | `#aebbcc` | 보조 아이콘 |
| `--color-icon-muted` | `#91a3c5` | 비활성 아이콘 |

### Semantic — Border

| Token | Value | Usage |
|---|---|---|
| `--color-border-default` | `#4b5e7c` | 일반 보더 |
| `--color-border-subtle` | `#37486c` | 연한 보더 (구분선) |

### Semantic — Background

| Token | Value | Usage |
|---|---|---|
| `--color-bg-primary` | `#151d2b` | 가장 어두운 배경 (페이지) |
| `--color-bg-secondary` | `#1d273b` | 카드 / 패널 배경 |
| `--color-bg-tertiary` | `#26324c` | hover, 선택 행 배경 |

### Semantic — Role / Avatar

| Token | Value | Usage |
|---|---|---|
| `--color-role-pm-bg` | `#0d2d7d` | Product Manager GNB 배경 |
| `--color-avatar-blue` | `#264f7a` | 아바타 파란 배경 |

---

## Border Width

### Primitive

| Token | Value |
|---|---|
| `border-width-0` | `0px` |
| `border-width-sm` | `1px` |

### Semantic

| Token | Value (→ Primitive) |
|---|---|
| `border-width-default` | `border-width-sm` (1px) |

---

## Radius

### Primitive

| Token | Value |
|---|---|
| `radius-none` | `0px` |
| `radius-xs` | `2px` |
| `radius-sm` | `4px` |
| `radius-md` | `6px` |
| `radius-lg` | `8px` |
| `radius-full` | `9999px` |

### Semantic

| Token | Value (→ Primitive) | Usage |
|---|---|---|
| `radius-tag` | `radius-xs` (2px) | 태그, 작은 배지 |
| `radius-component` | `radius-sm` (4px) | 기본 버튼, 인풋, 드롭다운 |
| `radius-hit-area` | `radius-md` (6px) | 텍스트 버튼 hit-area |
| `radius-card` | `radius-lg` (8px) | 모달, 카드 |
| `radius-pill` | `radius-full` (9999px) | 원형 아이콘 버튼, 아바타 |

---

## Size (spacing + sizing 공용 scale)

### Primitive

| Token | Value |
|---|---|
| `size-0` | `0px` |
| `size-2` | `2px` |
| `size-4` | `4px` |
| `size-6` | `6px` |
| `size-8` | `8px` |
| `size-10` | `10px` |
| `size-12` | `12px` |
| `size-14` | `14px` |
| `size-16` | `16px` |
| `size-20` | `20px` |
| `size-24` | `24px` |
| `size-26` | `26px` |
| `size-30` | `30px` |
| `size-32` | `32px` |
| `size-40` | `40px` |
| `size-46` | `46px` |
| `size-60` | `60px` |
| `size-80` | `80px` |

---

## Sizing (컴포넌트 전용 — scale 외 값)

### Primitive

| Token | Value | Usage |
|---|---|---|
| `sizing-icon-sm` | `16px` | 보조 아이콘 |
| `sizing-icon-md` | `20px` | 기본 아이콘 |
| `sizing-icon-lg` | `24px` | GNB 아이콘 |
| `sizing-icon-xl` | `40px` | 그래픽 배지 내부 |
| `sizing-avatar-md` | `32px` | GNB 아바타 |
| `sizing-avatar-lg` | `60px` | 성공/실패 대형 배지 |
| `sizing-control-sm` | `36px` | 소형 버튼 높이 |
| `sizing-control-md` | `42px` | 중형 버튼 높이 |
| `sizing-control-lg` | `45px` | 기본 인풋/버튼 |
| `sizing-control-xl` | `54px` | 대형 인터랙션 |
| `sizing-modal-md` | `560px` | 알럿/다이얼로그 너비 |
| `sizing-layout-max` | `1440px` | 페이지 최대 너비 |

---

## Spacing

> Primitive 직접 사용 + layout만 Semantic  
> 버튼 padding, gap 등은 `size-4`, `size-8`, `size-12`, `size-16`을 직접 사용

### Semantic (layout 전용)

| Token | Value | Usage |
|---|---|---|
| `spacing-page-section` | `80px` | 페이지 상하 여유 |
| `spacing-page-gutter` | `40px` | 페이지 좌우 여유 |
| `spacing-gnb-padding-x` | `24px` | GNB 가로 padding |
| `spacing-modal-inset` | `40px` | 모달 내부 padding·gap |

---

## Typography

### Primitive

| Token | Value |
|---|---|
| `font-family-base` | `SamsungOne` |
| `font-weight-regular` | `400` |
| `font-weight-bold` | `700` |
| `font-size-11` | `11px` |
| `font-size-12` | `12px` |
| `font-size-13` | `13px` |
| `font-size-14` | `14px` |
| `font-size-15` | `15px` |
| `font-size-16` | `16px` |
| `font-size-20` | `20px` |
| `font-size-22` | `22px` |
| `font-size-24` | `24px` |
| `font-size-28` | `28px` |
| `line-height-tight` | `1.0` |
| `line-height-snug` | `1.3` |
| `line-height-base` | `1.4` |

### Semantic — Composite Styles

| Token | Family | Weight | Size | Line-height |
|---|---|---|---|---|
| `title-xl` | font-family-base | bold (700) | 28px | 1.3 |
| `title-lg` | font-family-base | bold (700) | 24px | 1.3 |
| `subtitle-lg` | font-family-base | bold (700) | 20px | 1.3 |
| `subtitle-md` | font-family-base | bold (700) | 16px | 1.3 |
| `superscrip` | font-family-base | regular (400) | 22px | 1.0 |
| `body-lg` | font-family-base | regular (400) | 16px | 1.4 |
| `body-md` | font-family-base | regular (400) | 14px | 1.4 |
| `label-lg` | font-family-base | bold (700) | 16px | 1.3 |
| `label-md` | font-family-base | bold (700) | 14px | 1.3 |
| `label-sm` | font-family-base | bold (700) | 12px | 1.0 |
| `caption-md` | font-family-base | regular (400) | 13px | 1.4 |
| `caption-sm` | font-family-base | regular (400) | 11px | 1.4 |
| `filled-btn-lg` | font-family-base | bold (700) | 16px | 1.3 |
| `filled-btn-md` | font-family-base | bold (700) | 12px | 1.3 |
| `filled-btn-sm` | font-family-base | bold (700) | 10px | 1.3 |
| `text-btn-sm` | font-family-base | bold (700) | 10px | 1.3 |
| `menu-md` | font-family-base | regular (400) | 13px | 1.4 |
