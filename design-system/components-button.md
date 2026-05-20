# Button Components
> Figma node: `11032:101212` | File: `SUbO7gaqt5ElgmTKszGHqh`

---

## 1. button/default

filled 버튼. 사이트 주요 액션에 사용.

### Variants
- **importance**: `primary` | `secondary`
- **size**: `large` | `medium` | `small`
- **state**: `default` | `hover` | `disabled`

### 시각 스펙

#### Size

| Size | Height | Padding X | Padding Y | Font token | Font size |
|---|---|---|---|---|---|
| large | 48px | 16px | 14px | `filled-btn-lg` | 16px / bold |
| medium | 32px | 12px | 7px | `filled-btn-md` | 12px / bold |
| small | 26px | 10px | 6px top / 5px bottom | `filled-btn-sm` | 10px / bold |

- **Border radius**: `radius-component` (4px)
- **Icon**: left 선택. large → 20px, medium/small → 16px
- **Text color**: `#ffffff` (color/text/on-btn)

#### Color — Primary

| State | Background |
|---|---|
| default | `#006bea` (color/brand/brand-primary) |
| hover | `#2189ff` (color/brand/brand-primary-hover) |
| disabled | `#006bea` + `opacity: 0.5` |

#### Color — Secondary

| State | Background |
|---|---|
| default | `#37486c` (color/background/interactive) |
| hover | `#4b5e7c` (color/background/interactive-hover) |
| disabled | `#37486c` + `opacity: 0.5` |

---

## 2. button/text-button

배경 없는 텍스트 전용 버튼. 부가 액션, 링크성 액션에 사용.

### Variants
- **importance**: `primary` | `secondary` | `tertiary`
- **state**: `default` | `hover` | `disabled`
- **icon**: left / right 각각 선택 가능

### 시각 스펙

- **Padding**: 4px (x) / 2px (y)
- **Border radius**: `radius-hit-area` (6px) — hover 시 배경에 적용
- **Font**: `label-md` — 14px / bold / line-height 1.3
- **Icon**: 16px (left / right 선택)

#### Color

| Importance | Text color | Hover background | Disabled |
|---|---|---|---|
| primary | `#006bea` (color/text/btn-primary) | `#2e3d5c` (color/background/btn-text-hover) | opacity 0.5 |
| secondary | `#e7e9ea` (color/text/btn-secondary) | `#2e3d5c` | opacity 0.5 |
| tertiary | `#91a3c5` (color/text/muted) | 없음 | 없음 |

---

## 3. button/icon-button

아이콘만 있는 버튼. 툴바, 테이블 액션 등에 사용.

### Variants
- **size**: `large` | `small`
- **style**: `solid` | `ghost`
- **state**: `default` | `hover` | `disabled`

### 시각 스펙

| Size | 전체 크기 | Padding (solid) | Padding (ghost) | Icon |
|---|---|---|---|---|
| large | 48 × 48px | 12px | — | 24px |
| small | 26 × 26px | 1px | 4px | 24px |

- **Border radius**: `radius-component` (4px)

#### Color

| Style | State | Background |
|---|---|---|
| solid | default | `#37486c` (color/background/interactive) |
| solid | hover | `#4b5e7c` (color/background/interactive-hover) |
| solid | disabled | `#37486c` + `opacity: 0.5` |
| ghost | default | transparent |
| ghost | hover | `#37486c` (color/background/interactive) |
| ghost | disabled | `opacity: 0.5` |

---

## 4. button/mlp-card

MLP 카드 내부 전용 네비게이션 버튼. chevron-right 아이콘 고정.

### Variants
- **status**: `default` | `hover`

### 시각 스펙

| Property | Value |
|---|---|
| 크기 | 24 × 24px |
| Border radius | 120px (`radius-pill`) |
| Icon | `icon=chevron_right.svg` (20px) |
| default background | transparent |
| hover background | `#4b5e7c` (color/background/interactive-hover) |

---

## 공통 색상 값 정리

| Token (Figma 내부) | Hex | 역할 |
|---|---|---|
| color/brand/brand-primary | `#006bea` | primary 버튼 배경 |
| color/brand/brand-primary-hover | `#2189ff` | primary 버튼 hover 배경 |
| color/background/interactive | `#37486c` | secondary/icon 버튼 배경 |
| color/background/interactive-hover | `#4b5e7c` | secondary/icon 버튼 hover 배경 |
| color/background/btn-text-hover | `#2e3d5c` | text-button hover 배경 |
| color/text/on-btn | `#ffffff` | 버튼 위 텍스트 |
| color/text/btn-primary | `#006bea` | text-button primary 텍스트 |
| color/text/btn-secondary | `#e7e9ea` | text-button secondary 텍스트 |
| color/text/muted | `#91a3c5` | text-button tertiary 텍스트 |
| opacity-disabled | `0.5` | 비활성 상태 투명도 |
