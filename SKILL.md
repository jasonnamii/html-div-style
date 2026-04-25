---
name: html-div-style
description: |
  옵시디언 .md 전용 HTML div 래퍼. 8가지 스타일(디폴트: 1번 Corporate Minimal). 옵시디언 렌더링 깨짐 방지 14대 금칙 내장. .md 안에서 div 태그를 안전하게 쓰기 위한 스킬.
  P1: HTML div, div 스타일, div 디자인, 박스 디자인, 카드 디자인, 옵시디언 div.
  P2: 적용해줘, 만들어줘, 래핑해줘, apply, create, wrap.
  P3: HTML div style, card design, box design, obsidian div wrapper.
  P5: .md로.
  NOT: HTML 전체 페이지 디자인(→design-skill), 애플디자인스타일(→design-skill), 일반 옵시디언 문서(→obsidian-markdown), UI설계 프로세스(→ui-action-designer).
"@uses":
  - references/tokens.md
  - references/snippets.md
  - references/forbidden.md
  - references/qc.md
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

옵시디언 .md 안에서 HTML div 태그로 구조화된 시각 요소(카드, 헤더, 배지, 노트박스)를 **깨지지 않게** 삽입하는 스킬. 렌더링 안전성 + 8스타일 스펙 구현만 담당.

**범위:** 옵시디언 .md 내 div 래핑 **단 하나의 타겟**. HTML 전체 페이지(.html)는 design-skill.

**디자인 종속:** design-skill CORE(3색 시스템·여백 철학)와 톤 준수. 이 스킬은 2층(HTML div) 전용.

---

## 4블록 참조 구조

| 블록 | 파일 | 역할 |
|---|---|---|
| 토큰 | `references/tokens.md` | 옵시디언 안전 값 화이트리스트 |
| 스니펫 | `references/snippets.md` | 8스타일 인덱스·공통 프리미티브 (→ style-corporate·style-catalog) |
| 금칙 | `references/forbidden.md` | 전역 금지 + 옵시디언 14금칙 + 치트시트 |
| QC | `references/qc.md` | 6계층 스코어카드·합격선 ≥80 & Layer1~4 ≥85% |

공통 스파인: `VAULT/_skills research/html-skill-refactor/spine.md`.

---

## 라우팅

### 스타일 선택

| 조건 | 적용 | 로드 |
|---|---|---|
| 스타일 미지정 | **1번 Corporate Minimal** (디폴트, N6 RECOGNITION) | `snippets.md` + `style-corporate.md` |
| "1번 스타일로" | Corporate Minimal | `snippets.md` + `style-corporate.md` |
| "N번 스타일로" (2~8) | 해당 스타일 | `snippets.md` + `style-catalog.md` §해당 |

### 로드 최소화

| 상황 | 로드 순서 |
|---|---|
| 스타일만 적용 | snippets.md → 해당 스펙 파일 |
| 검증까지 | + forbidden.md → qc.md |
| 신규 값 정의 | + tokens.md (금지 토큰 확인) |

---

## 8스타일 목록

| # | 이름 | 톤 | 적합 용도 |
|---|---|---|---|
| 1 | **Corporate Minimal** (디폴트) | 절제·신뢰 | 비즈니스 보고서·분석·범용 |
| 2 | Warm Paper | 품격·따뜻함 | 제안서·계약 요약 |
| 3 | Notion-like Clean | 명료·효율 | 내부 메모·정리 |
| 4 | Soft Glass | 세련·부드러움 | 프레젠·프로토타입 |
| 5 | Dark Executive | 무게감·권위 | 경영진 브리핑 |
| 6 | Blueprint | 분석·구조 | 기술문서·목업·와이어프레임 |
| 7 | Swiss Typography | 단호·강렬 | 의사결정 문서 |
| 8 | Soft Pastel | 친근·캐주얼 | 내부 공유·브레인스톰 |

고정 스펙 요약: `→ snippets.md §스타일별 고정 스펙 요약`.

---

## 레이어링 (1층·2층)

| 층 | 역할 | 담당 |
|---|---|---|
| 1층 | 콜아웃·테이블·볼드·헤딩·접힘·수평선 — 구조·가독성·위계 | **design-skill** 이쁘니 |
| 2층 | 카드 배경·flex·색상 강조 — 시각적 특수효과 | **이 스킬** |

**규칙:** 1층 먼저 확인 → 2층 적용. 1층 부재 시 "1층 이쁘니 먼저 깔까요?" 확인. "HTML div only" 명시 요청 시 1층 스킵 허용.

---

## 워크플로우

```
0. 1층 확인 (design-skill 이쁘니 적용 여부) — HTML div only 요청 시 스킵
1. 출력 대상 = 옵시디언 .md (유일 타겟)
2. 스타일 선택 (미지정 → 1번 디폴트)
3. 로드: snippets.md + 해당 스펙 파일 (필요 시 tokens/forbidden/qc)
4. 콘텐츠 구조 파악 → 박스 타입 조합
5. 스펙 고정값 확인 (radius·보더·배지·제목size — 변형 금지, N4)
6. 코드 생성 (인라인 style만, 고정 스펙값만)
7. QC 검증 (forbidden 14금칙 전수 + qc.md 6계층)
```

---

## 핵심 제약 (가장 자주 실수하는 7가지)

| 실수 | 결과 | 금칙 |
|---|---|---|
| div 내부 빈줄 | 레이아웃 붕괴 | ❶ |
| div 안 `**볼드**` | 태그 노출 | ❷ |
| 다크 div color 미지정 | 텍스트 안 보임 | ❸ |
| 연한 보더·배경 (`#eee`·`#fafafa`) | 카드 투명화 | ❿ |
| 제목 font-size 미지정 | 본문과 구분 없음 | tokens §타이포 |
| 카드 사이 빈줄만 | 간격 0으로 붙음 | ⓫ |
| `<br>` 뒤 블록 태그 같은 줄 | div 스타일 무시 | ⓮ |

전수: `→ forbidden.md §옵시디언 14금칙`.

---

## UX 원리 적용

이 스킬은 N4·N6·N8 코어 3원리 적용.

| 원리 | 반영 |
|---|---|
| N4 CONSISTENCY | 8스타일 고정 스펙 · 임의 변형 금지 |
| N6 RECOGNITION | radius·보더·배지 색상 고정값 |
| N8 MINIMAL | 3색 준수 · font-family 미지정 |

허브: `→ references/ux-principles.md#A-N4,N6,N8`.

**충돌 규칙:** design-skill CORE와 UX 원리 충돌 → design-skill CORE 우선.

---

## 검증 역할 분리

이 스킬 = 스타일 **생성**. 렌더 **검증**은 qc.md 6계층 + UP §C.QC 파이프라인.

---


## §INV NO_WORK_LABEL (산출물·대화 본질 보호)

| 항목 | 정의 |
|------|------|
| RULE | 산출물·대화 = 인간 언어. 작업 라벨 ZERO. (1만 페이지 1단어 = FAIL) |
| 판정 | "이 단어, 이 대화 밖 사람이 사전 없이 읽을 수 있나?" NO → 작업 라벨 → 금지 |
| ALLOW | 업계 전문용어(HTML·CSS·div·span·flexbox·grid) · 고유명사(Obsidian) |
| CONVERT | 라벨 발견 → 실명·평문 풀어쓰기. 예) "8가지 스타일·14대 금칙·1번 Corporate Minimal" → 스타일 결과만 노출(코드 라벨 ✗) |
| SELF_CHECK | .md 출력 직전에서 자체 스캔. 1개라도 발견 = 차단·재작성. paper-engine cascade 경유 시 INV 13 자동 적용 |

---

## Gotchas

- **디폴트 혼동:** 스타일 번호 없이 "HTML div로" → 반드시 1번. 임의 선택 금지.
- **.html 파일로 오인:** 이 스킬 = .md 전용. .html은 design-skill.
- **margin 사용:** 옵시디언 div서 예측 불가. padding만, 간격은 `<br>`. → forbidden ⑨.
- **font-family 지정:** 옵시디언 기본폰트 충돌. 금지. → forbidden ⑧.
- **Style 5 rgba 투명도:** .md에서 불안정. style-catalog의 .md용 불투명 대체값 필수.
- **연한 색 함정:** `.html용` 값을 .md에 쓰면 흐려짐. 기준선 이상만. → tokens §색.
- **스타일 ≠ 콘텐츠 제한:** 어떤 스타일이든 카드·테이블·관계도 전부 표현 가능.
- **스타일 임의 변형:** "이번만 radius 16px" = N4 위반. 변형 필요 시 새 스타일 정의.
- **`<details>` 접기 실패:** 내부 빈줄·마크다운 0 — HTML only. → forbidden ⓬.
- **`<summary>` 삼각형:** 네이티브 토글과 중복. ▶/►/▸/▹/◀/◄/◂/◃ 금지. → forbidden ⓭.
