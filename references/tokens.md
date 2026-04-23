# tokens.md — html-div-style 전용 토큰

옵시디언 .md 안 HTML div에서 **안전하게 쓸 수 있는 값만**. 공통 토큰(html-skill-refactor 스파인)에서 옵시디언 제약으로 좁힌 하위집합.

> 원본 공통 토큰: `VAULT/_skills research/html-skill-refactor/spine.md §공통 토큰`
> 축1 디테일: `VAULT/_skills research/html-skill-refactor/axis1-css-tokens.md`

---

## 타이포 (옵시디언 하위집합)

| 용도 | 값 | 근거 |
|---|---|---|
| 제목 size | `22px` (고정) | ❻ 인라인 style만·제목/본문 시각차 확보 |
| 레이블 size | `12px` (고정) | 대비 유지 최소선 |
| 본문 size | 지정 금지 | 옵시디언 기본폰트 우선 (font-family 지정 금지와 동일 원칙) |
| weight | `400 / 600 / 700` 3단계만 | 중간값은 테마 흡수 |
| line-height | `1.4 / 1.5 / 1.6` | 공통 lh 교집합 |

**font-family 지정 금지** (→ forbidden.md ⑧).

## 간격

| 용도 | 값 |
|---|---|
| padding (카드) | `16 / 20 / 24` |
| padding (노트) | `12 / 16` |
| div 사이 간격 | `<br>` 스페이서 (margin 사용 금지 → forbidden.md ⑨) |

## radius

| 스타일 톤 | 값 |
|---|---|
| 절제·공식 | `0 / 2` |
| 기본 | `4 / 6 / 8` |
| 부드러움 | `12 / 16` |

## 색 (안전 기준선)

옵시디언 라이트/다크 테마 모두에서 **보이는** 최소 조건:

| 요소 | 기준 |
|---|---|
| 보더 | `#b0b0b0` 이상 진하게 (= `#eee`, `#ccc` 금지) |
| 배경 | `#efefef` 이상 진하게 (= `#fafafa`, `#f8f8f8` 금지) |
| 텍스트 본문 | `#333` 이상 진하게 |
| 레이블 | `#666` 이상 (= `#999` 금지 — 라이트 테마서 흐려짐) |

**다크 컨테이너:** 모든 하위 텍스트 태그에 개별 color 명시 필수(❸). → forbidden.md 참조.

## 액센트 팔레트 (등록)

| 이름 | HEX | 용도 |
|---|---|---|
| Oxford Blue | `#002147` | 다크 박스 배경, 강조 보더, 배지 |

다크 박스 배경으로 쓸 때 내부 텍스트는 `#fff` 강제.

---

## 스타일별 세부 토큰

8스타일 각각의 **고정 스펙값**(변형 금지, N4 CONSISTENCY):
→ `snippets.md` 및 기존 `style-corporate.md` · `style-catalog.md`

## 금지 토큰

| 토큰 | 이유 |
|---|---|
| `position: fixed` | 옵시디언 렌더 무시·레이아웃 붕괴 |
| viewport 단위 (`vw` / `vh`) | 리딩뷰서 예측 불가 |
| `margin` (div 외부 간격) | 옵시디언서 불안정 → `<br>` 스페이서로 대체 |
| `font-family` | 기본폰트 충돌 |
| `<style>`·`<link>`·CSS class | 옵시디언 미지원 → 인라인 style만 |

상세 금칙: `→ forbidden.md`
