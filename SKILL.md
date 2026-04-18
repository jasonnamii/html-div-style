---
name: html-div-style
description: |
  옵시디언 .md 전용 HTML div 래퍼. 8가지 스타일(디폴트: 1번 Corporate Minimal). 옵시디언 렌더링 깨짐 방지 14대 규칙 내장. .md 안에서 div 태그를 안전하게 쓰기 위한 스킬.
  P1: HTML div, div 스타일, div 디자인, 박스 디자인, 카드 디자인, 옵시디언 div.
  P2: 적용해줘, 만들어줘, 래핑해줘, apply, create, wrap.
  P3: HTML div style, card design, box design, obsidian div wrapper.
  P5: .md로.
  NOT: HTML 전체 페이지 디자인(→design-skill), 애플디자인스타일(→design-skill), 일반 옵시디언 문서(→obsidian-markdown), UI설계 프로세스(→ui-action-designer).
"@uses":
  - references/obsidian-rules.md
  - references/style-corporate.md
  - references/style-catalog.md
vault_dependency: HARD
---

<!-- Trigger Conditions
P1: HTML div, div 스타일, div 디자인, 박스 디자인, 카드 디자인, 옵시디언 div.
P2: 적용해줘, 만들어줘, 래핑해줘, apply, create, wrap.
P3: HTML div style, card design, box design, obsidian div wrapper.
P4: 옵시디언 .md 안에서 HTML div 시각요소 삽입 필요 시.
P5: .md로.
NOT: HTML 전체 페이지 디자인(→design-skill), 애플디자인스타일(→design-skill), 일반 옵시디언 문서(→obsidian-markdown), UI설계 프로세스(→ui-action-designer).
-->

# HTML div Style — 옵시디언 .md 전용

옵시디언 .md 안에서 HTML div 태그로 구조화된 시각 요소(카드, 헤더, 배지, 노트박스)를 안전하게 삽입하는 스킬. 렌더링 깨짐 방지가 최우선.

**범위:** 옵시디언 .md 내 div 래핑만. HTML 전체 페이지(.html) 디자인은 design-skill이 전담한다.

**디자인 종속:** design-skill의 CORE(3색 시스템, 여백 철학 등)와 톤을 따른다. 이 스킬은 div 렌더링 안전성 + 스타일 스펙 구현만 담당.

**등록 액센트 팔레트 (공통 variant):** design-skill cascade로 상속. 8스타일 어디에서도 형 명시 요청 시 아래 팔레트를 CTA·강조 보더·다크 박스 배경으로 사용 가능.

| 이름 | HEX | 적용 |
|------|-----|------|
| Oxford Blue | `#002147` | 다크 박스 배경, 강조 보더, 배지. 텍스트 `#fff` 강제 (❸ 다크 div color 필수 규칙 적용) |

---

## 라우팅

### 출력 대상

| 출력 대상 | 로드 | 이유 |
|-----------|------|------|
| 옵시디언 .md | `references/style-catalog.md` (통합 참조) | .md는 렌더링 제약이 많아 반드시 규칙을 먼저 로드해야 깨짐을 방지한다. obsidian-rules.md의 14대 규칙은 style-catalog.md §공통규칙 섹션에 통합됨 |

**통합 참조:** obsidian-rules.md의 14대 규칙은 style-catalog.md §공통규칙 섹션에 통합. 별도 로드 불필요 — style-catalog.md 1회 로드로 공통규칙+스타일 카탈로그 동시 획득.

### 스타일 선택

| 조건 | 적용 스타일 | 로드 대상 |
|------|-------------|-----------|
| 스타일 미지정 | **1번 Corporate Minimal** (디폴트) | `references/style-corporate.md` |
| "1번 스타일로" | Corporate Minimal | `references/style-corporate.md` |
| "N번 스타일로" (2~8) | 해당 스타일 | `references/style-catalog.md` 내 해당 섹션 |

---

## 8개 스타일 목록

| # | 이름 | 핵심 톤 | 적합 용도 |
|---|------|---------|-----------|
| 1 | **Corporate Minimal** (디폴트) | 절제·신뢰 | 비즈니스 보고서, 분석, 범용 |
| 2 | Warm Paper | 품격·따뜻함 | 제안서, 계약 요약 |
| 3 | Notion-like Clean | 명료·효율 | 내부 메모, 정리 |
| 4 | Soft Glass | 세련·부드러움 | 프레젠테이션 보조, 프로토타입 미리보기 |
| 5 | Dark Executive | 무게감·권위 | 경영진 브리핑 |
| 6 | Blueprint | 분석적·구조적 | 기술 문서, 구조 분석, UI 비교표, 목업, 와이어프레임 |
| 7 | Swiss Typography | 단호·강렬 | 의사결정 문서 |
| 8 | Soft Pastel | 친근·캐주얼 | 내부 공유, 브레인스톰 |

---

## 레이어링 원칙

이 스킬은 **2층(HTML div)**을 담당한다. 문서의 1층(md 네이티브)이 먼저 깔려 있어야 한다.

| 층 | 역할 | 담당 |
|---|------|------|
| 1층 | 콜아웃·테이블·볼드·헤딩·접힘·수평선으로 구조·가독성·정보 위계 완성 | **design-skill** (이쁘니 프로토콜 = design-skill/references/protocol-pretty.md) |
| 2층 | 카드 배경, flex 레이아웃, 색상 강조 등 시각적 특수효과 | **이 스킬** |

**적용 규칙:**
- 일반 문서: 1층(design-skill 이쁘니) 존재 확인 → 2층(HTML div) 적용. 1층 없이 2층만 쌓기 ✗
- 형이 "이 스타일로" 등 HTML div only 명시 요청: 1층 없이 2층만 허용

---

## 워크플로우

```
0. 1층 확인: design-skill 이쁘니(콜아웃·위계·여백 등) 적용 여부 확인. 없으면 → 형에게 "1층 이쁘니를 먼저 깔까요?" 확인 (형 명시 HTML div only 요청 시 스킵)
1. 출력 대상: 옵시디언 .md (이 스킬의 유일한 대상)
2. 스타일 선택 (미지정 → 1번 디폴트)
3. 해당 스포크 로드 (obsidian-rules + 스타일)
4. 콘텐츠 구조 파악 → 적합한 박스 타입 조합
5. 스펙 값 확인 (코드 작성 전 필수):
   - 스포크에서 해당 스타일의 radius, 보더(카드 vs 외곽), badge/label 색상을 읽는다
   - font-family 지정 금지 재확인
   - 스펙에 명시된 정확한 값만 사용한다. 임의 변형·보간·추정 금지
6. 코드 생성 (스포크의 코드 패턴 + step 5에서 확인한 스펙 값 사용)
7. 검증 (obsidian-rules 체크리스트)
```

---

## UX 원리 연결

**허브:** `@ref: references/ux-principles.md#A-N4,N6,N8`. 이 스킬은 N4·N6·N8 코어 3원리 적용.

| 원리 | 14규칙 연결 | 의미 |
|------|-----------|------|
| N4 CONSISTENCY | 전 스타일 스펙값 고정·임의 변형 금지 | 8스타일 내부 일관성 = 사용자 재인 가능 |
| N6 RECOGNITION | radius·보더·배지 색상 고정값 | 학습된 패턴 재사용, 외우게 하지 않음 |
| N8 MINIMAL | 3색 준수·font-family 지정 금지 | 시각 노이즈 차단, 주 정보 가시성 확보 |

**충돌:** design-skill의 CORE와 UX 원리가 충돌시 → design-skill CORE 우선 (이 스킬은 2층 담당, 1층 규칙 준수).

---

## .md 적용 시 핵심 제약 (요약)

자세한 규칙은 `references/obsidian-rules.md`에 있다. 가장 자주 실수하는 7가지:

| 실수 | 결과 | 규칙 |
|------|------|------|
| div 내부 빈줄 | HTML 블록 끊김 → 레이아웃 붕괴 | ❶ 빈줄 0개 |
| div 안에 `**볼드**` | 마크다운으로 재해석 → 태그 노출 | ❷ HTML 태그만 |
| 다크 div에 color 미지정 | 텍스트 안 보임 | ❸ 개별 color 필수 |
| 연한 보더/배경 (`#eee`, `#fafafa`) | 옵시디언 테마에 흡수 → 카드 투명화 | 보더 `#b0b0b0`↑, 배경 `#efefef`↑ |
| 제목 font-size 미지정 | 본문과 시각적 구분 없음 | 최소 22px |
| 연속 div 카드 사이 빈줄만 | 카드가 간격 0으로 붙음 | ⓫ `<br>` 스페이서 필수 |
| `<details>` 내부 빈줄/마크다운 | 토글은 되나 내용 안 접힘 | ⓬ 내부 빈줄 금지 + HTML only |
| `<summary>` 내 삼각형 문자 | 옵시디언 토글 삼각형과 중복 | ⓭ ▶/►/▸/▹/◀/◄/◂/◃ 금지 |
| `<br>` 뒤 블록 태그 같은 줄 | div 스타일 전부 무시 | ⓮ `<br>` 단독 줄 + 빈줄 + 블록 태그 새 줄 |

---

## 검증 역할 분리

이 스킬은 스타일 생성만 담당한다. .md 파일의 렌더링 검증은 UP §C.QC 파이프라인이 수행한다.

---

## Gotchas

- **디폴트 혼동:** 스타일 번호 없이 "HTML div로 해줘"라고 하면 반드시 1번(Corporate Minimal)을 적용한다. 임의 스타일 선택 금지.
- **HTML 전체 페이지를 이 스킬로 처리:** 이 스킬은 옵시디언 .md 전용. .html 파일 디자인은 design-skill이 전담한다.
- **.md에서 margin 사용:** 옵시디언 div에서 margin은 예측 불가하다. padding만 사용하고 간격은 div 사이 빈줄로 조절한다.
- **.md에서 font-family 지정:** 옵시디언 기본 폰트와 충돌한다. .md에서는 font-family 지정 금지. font-size는 제목(`22px`)과 레이블(`12px`) 등 필수 위계용만 허용.
- **Style 5 다크의 .md 적용:** rgba 투명도가 옵시디언에서 불안정하다. .md용 불투명 대체값(style-catalog.md에 명시)을 반드시 사용한다.
- **연한 색상 함정:** `#fafafa`(배경), `#eee`(보더), `#999`(레이블)는 옵시디언 라이트 테마에서 거의 보이지 않는다. 스타일 스포크의 `.md용` 값을 반드시 사용한다. `.html용` 값을 .md에 그대로 적용하면 흐려진다.
- **스타일 ≠ 콘텐츠 제한:** 각 스타일은 시각 표현 시스템이다. 어떤 스타일이든 카드·테이블·관계도 등 모든 구조를 표현할 수 있다.
- **연속 div 카드 간격 소실:** 빈줄 1개만으로는 옵시디언이 div 카드 사이 간격을 렌더링하지 않는다. 반드시 `<br>` 스페이서를 빈줄 사이에 넣어야 시각적 분리가 된다.
- **`<details>` 접기 실패:** `<details>` 내부에 빈줄이나 마크다운(`**볼드**`)이 있으면 옵시디언이 HTML 블록을 끊어서 콘텐츠가 details 바깥으로 빠진다.
- **`<summary>` 내 수동 삼각형:** 옵시디언이 네이티브 렌더링하는 토글 삼각형과 겹쳐서 중복된다. `<summary>` 안에는 삼각형 문자 절대 금지.
- **`<br>` 뒤 블록 태그:** `<br>`과 블록 레벨 태그가 같은 줄에 있으면 div의 모든 스타일이 무시된다. 반드시 `<br>` 단독 줄 + 빈줄 + `<div>` 새 줄 형태로 분리.
- **스타일 임의 변형 (N4 위반):** "이번만 radius 12px 대신 16px로" = N4 CONSISTENCY FAIL. 8스타일의 고정 스펙은 재인(N6) 기반. 변형시 사용자가 매번 새로 학습.
