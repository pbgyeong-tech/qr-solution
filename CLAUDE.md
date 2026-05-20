# QR Solution Admin - 로컬 재구현 프로젝트

## 프로젝트 목적
운영 서버(sha-virtual.com)의 Admin UI를 Figma 디자인 토큰 기반으로 재구현.
기존 코드는 토큰 체계 없이 하드코딩 → 이번에 토큰 기반 설계로 개선.

## 참고 운영 서버
- URL: https://admin.sha-virtual.com
- 스택: Vue 3 + Vuetify 3 + Vite + AWS

## 로컬 구현 스택
- Vue 3 (Composition API)
- Vuetify 3
- Vite
- TypeScript (선택)
- CSS 변수 기반 디자인 토큰 (Figma 토큰과 1:1 매핑)
- Pinia (role 상태 관리)

## Figma 디자인 파일
- 파일 키: `SUbO7gaqt5ElgmTKszGHqh`
- 파일명: (ttf) 2026 Virtual Promoter Platform Admin
- 컴포넌트 라이브러리 노드: `11097:101165`
- 버튼 컴포넌트 노드: `11032:101212`

---

## 디자인 토큰 원칙
- 모든 색상은 `var(--color-*)` 형태로만 사용, 하드코딩 금지
- 간격/폰트/사이즈도 토큰으로 관리
- 토큰 파일 위치: `/tokens.css` (프로젝트 루트)
- Vuetify 테마도 토큰 기반으로 오버라이드
- 실제 토큰 예시:
  ```
  --color-bg-primary:   #151d2b   /* 페이지 배경 */
  --color-bg-secondary: #1d273b   /* 카드/패널 배경 */
  --color-brand-primary: #006bea  /* primary 버튼 */
  --color-text-primary: #e7e9ea   /* 본문 텍스트 */
  --size-16: 16px
  --spacing-page-gutter: 40px
  ```
- 전체 토큰 정의: `design-system/design-tokens.md`

## 레이아웃 제약
- PC only (모바일 미지원)
- 최소 브라우저 너비: 1440px (`--sizing-layout-max: 1440px`)

---

## 디자인 시스템 파일 구조
```
/tokens.css                          ← CSS 변수 (색상/타이포/간격/사이즈 전체)
/design-system/
  design-tokens.md                   ← 전체 토큰 명세 (color/radius/size/spacing/typography)
  components-button.md               ← 버튼 컴포넌트 스펙
/icons/
  ui/                                ← UI 아이콘 SVG (icon=*.svg)
  product/                           ← 제품 카테고리 아이콘 SVG (category=*.svg)
  smarththings/                      ← SmartThings 카테고리 아이콘 PNG (category=*.png)
```

## 메뉴별 아이콘 매핑
| 메뉴 | 아이콘 파일 |
|---|---|
| Home | `icons/ui/icon=home.svg` |
| Dashboard / Analytics | `icons/ui/icon=analytics.svg` |
| Content Library | `icons/ui/icon=cnt library.svg` |
| Product MLP | `icons/ui/icon=product-mlp.svg` |

---

## 권한(Role) 구조
총 4가지 권한. 로그인 후 상단 role selector로 전환 가능.

| Role | 표시명 | 코드값 |
|------|--------|--------|
| ADMIN | System Manager Mode | ADMIN |
| GRM | Regional Manager Mode | GRM |
| LM | Local Manager Mode | LM |
| GPM | Product Manager Mode | GPM |

---

## 권한별 레이아웃 상세

### ADMIN (System Manager)
- 상단: role selector 1개만 노출
- 사이드 메뉴: Home, User Access History, System 메뉴 그룹
  - System 하위: Product Category Setting / SmartThings Explore Category Setting / QR Code Setting / Language Setting / User Management / Privacy Policy
- 홈 콘텐츠: Monitoring 카드 3개 + MLP Requests 테이블 + Member Requests 테이블

### GRM (Regional Manager)
- 상단: role selector + region selector (Europe 등) 노출
- 사이드 메뉴 상단: region selector
- 사이드 메뉴: Home, User Access History, Country selector (드롭다운) + 워크스페이스 목록
- 워크스페이스 하단에 Add Workspace 버튼 있음
- 워크스페이스 선택 시 상세 편집 뷰 (탭: MLP Requests / About / Members)
  - MLP Requests 테이블 컬럼: Category / Product Code / Summary / Status / Requested / Action
- GRM 홈: "Home: All Workspaces" 테이블 뷰
  - 컬럼: Name / URL / Country / Language / Status / Created / Action
  - 필터: Language selector, Status selector, Search input
  - 페이지네이션 있음 (예: 1-9 of 59)

### LM (Local Manager)
- 상단: role selector + region selector 노출
- 사이드 메뉴: Workspace selector (예: "all (de-DE)") + 메뉴 그룹
  - Workspace 그룹: Workspace, Content Library (하위: System Message)
  - Product MLP 그룹
  - Add Workspace 버튼 + Copy Superscript 유틸리티 (⁰¹²³...)
- 워크스페이스 선택 시 상세 편집 뷰 (탭: MLP Requests / About / Members)
  - MLP Requests 테이블 컬럼: Category / Product Code / Summary / Status / Requested / Action
- LM 홈: "All Workspaces" 테이블 뷰 (GRM 홈과 동일 구조)

### GPM (Product Manager / Global Product Manager)
- 상단: role selector 1개만 노출 (ADMIN과 동일)
- 사이드 메뉴: Home, User Access History, Content Library (하위: SmartThings Explore / System Message), Product MLP
  - Copy Superscript 유틸리티 (⁰¹²³...)
- 주요 화면: Product MLP (카드 리스트)
  - 필터: Year selector / Visibility selector / Status multi-selector / Search input
  - 우측 상단 Add 버튼
  - 카드 구성: 썸네일 이미지 / 상태(Published·Draft) / Product Code / Category / Year / Published날짜 / Updated날짜 / Visibility(Public·Private) / QR코드 이미지
  - 페이지네이션 있음 (예: 1-9 of 37)

---

## 공통 상태값

### Publish Status
- `published` / `draft` / `pending_approval`

### Approve Status
- `approved` / `rejected` / `pending_approval`

### Visibility
- `public` / `private`

> **state vs status 구분**
> - `state`: UI 인터랙션 상태 — `hover` / `selected` / `disabled` / `focused`
> - `status`: 데이터·비즈니스 상태 — `active` / `deleted` / `published` / `rejected`

---

## 공통 컴포넌트 목록 (운영서버 분석 기반)

| 컴포넌트 | 설명 |
|---|---|
| AppHeader | 타이틀 + role selector (+ region selector) + 우측 버튼 (help/notice/alarm/계정) |
| AppSidebar | 메뉴 + 권한별 selector |
| AppFooter | © Samsung + Terms of Use / Privacy Notice / 버전 |
| CInput | text / selector / selector-multiple / search-icon 타입 |
| CButton | btn / text 타입, status(active/normal), size(medium/large) |
| ContentTable | 헤더 정렬 / 페이지네이션 포함 |
| InfoPublishStatus | published / draft / pending_approval 뱃지 |
| InfoApproveStatus | approved / rejected / pending_approval 뱃지 |
| InfoPublicStatus | public / private 아이콘+텍스트 |
| AccountPanel | 슬라이드 패널 (이름/비밀번호 수정, Delete Account) |
| ProductCard | GPM의 Product MLP 카드 |
| ContentPaging | 페이지 텍스트 + 이전/다음 버튼 |
| SuperscriptCopier | ⁰¹²³... 복사 유틸리티 (LM/GPM 사이드바 하단) |

---

## 화면 구현 범위

### 공통
- [ ] 로그인
- [ ] 공통 레이아웃 (Header + Sidebar + Content + Footer)

### ADMIN
- [ ] Home (Monitoring 카드 3개 + MLP Requests 테이블 + Member Requests 테이블)
- [ ] User Access History
- [ ] Product Category Setting
- [ ] SmartThings Explore Category Setting
- [ ] QR Code Setting
- [ ] Language Setting
- [ ] User Management
- [ ] Privacy Policy

### GRM
- [ ] Home: All Workspaces (테이블, Region/Country/Language/Status 필터)
- [ ] User Access History
- [ ] Workspace 상세 (MLP Requests / About / Members 탭)

### LM
- [ ] Home: All Workspaces (테이블)
- [ ] Workspace 상세 (MLP Requests / About / Members 탭)
- [ ] Content Library > System Message
- [ ] Product MLP (카드 리스트 + 상세)

### GPM
- [ ] Home
- [ ] User Access History
- [ ] Content Library > SmartThings Explore
- [ ] Content Library > System Message
- [ ] Product MLP (카드 리스트 + 상세)

## 현재 구현 중인 화면
(작업할 때마다 업데이트)

---

## 코딩 규칙
- 컴포넌트는 `/components` 폴더에 분리
- 토큰은 `/tokens.css` 에서 중앙 관리
- 하드코딩된 색상값 발견 시 반드시 토큰으로 교체
- 권한 분기는 role store (Pinia)로 관리
- 컴포넌트명 PascalCase, 함수명 camelCase

---

## 네이밍 컨벤션

### 레이어 네이밍 (Figma)
- 형식: `domain/component-name` (소문자 + 하이픈)
- `auth`: 로그인·회원가입·비밀번호 찾기 등 인증 관련 화면 (`auth/login-form`)
- 도메인 예시: `page/`, `modal/`, `table/`, `section/`, `edit/`, `form/`, `navigation/`

### wrapper vs container
- `wrapper`: 아이콘 정렬·크기 맞춤·spacing 역할 (예: `icon-wrapper > icon/ui`)
- `container`: 의미 있는 콘텐츠 영역 (예: `page-container`, `modal-container`)

### 토큰 네이밍
- `muted`: 덜 강조된 텍스트, 비활성·보조 정보에 사용 (예: `--color-text-muted`)

---

## Git 커밋 규칙

### 커밋 메시지 형식
```
<타입>(<범위>): <제목>

<본문> (선택)
```

### 타입 종류
| 타입 | 설명 |
|------|------|
| feat | 새로운 기능 추가 |
| fix | 버그 수정 |
| refactor | 코드 리팩토링 |
| style | UI/스타일 변경 |
| docs | 문서 수정 |
| chore | 설정, 패키지 등 기타 |

### 예시
```
feat(layout): ADMIN role 레이아웃 구현
feat(home): GRM All Workspaces 테이블 구현
feat(mlp): GPM Product MLP 카드 리스트 구현
fix(auth): 로그인 토큰 만료 오류 수정
style(token): primary 색상 토큰 Figma값으로 업데이트
feat(component): InfoPublishStatus 뱃지 컴포넌트 추가
```

### 규칙
- 제목은 한국어로, 50자 이내
- 현재형으로 작성 ("추가했다" ❌ → "추가" ✅)
- 작은 단위로 자주 커밋
- 본문에는 왜 변경했는지 기록
