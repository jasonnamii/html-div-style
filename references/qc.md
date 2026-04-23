# qc.md — html-div-style 품질 체크리스트

옵시디언 .md HTML div 산출물을 **리딩뷰에서 점검**하는 6계층 스코어카드. 합격선 ≥80 AND Layer 1-4 ≥85%.

> 공통 QC 근거: `VAULT/_skills research/html-skill-refactor/spine.md §공통 QC`
> 축5 상세: `VAULT/_skills research/html-skill-refactor/axis5-qc-checklist.md`

---

## 6계층 스코어카드

| Layer | 항목 | 배점 | 자동화 |
|---|---|---|---|
| 1 Syntax | HTML 유효성 | 8 | 100% |
| 2 A11y | 대비·구조·시맨틱 | 20 | 70% |
| 3 Perf | 렌더 경량·리소스 | 20 | 100% |
| 4 Semantic | 태그 의미 정합 | 15 | 50% |
| 5 Design | 스타일·일관성 | 25 | 0% |
| 6 Brand | 톤·팔레트 고정 | 12 | 0% |

---

## Layer 1. Syntax (8점)

- [ ] 모든 `<div>` 짝 맞음
- [ ] 인용부호·속성 따옴표 안 깨짐
- [ ] 태그 겹침 없음 (`<p><div>...</p></div>` 금지)

## Layer 2. A11y (20점)

- [ ] 본문 대비 ≥4.5 (제목 ≥3.0)
- [ ] 다크 박스 내부 모든 텍스트 `color` 명시 (❸)
- [ ] 링크는 `<a href>` + 식별 가능한 텍스트
- [ ] heading 위계가 문서 흐름과 일치 (임의 점프 없음)

## Layer 3. Perf (20점) — 옵시디언 렌더 경량

- [ ] `<style>`·`<link>`·class 속성 없음 (G4)
- [ ] 외부 리소스(이미지·폰트 CDN) 없음 또는 캐시됨
- [ ] div 깊이 3단 이하
- [ ] `<script>` 없음 (G3)

## Layer 4. Semantic (15점)

- [ ] 카드는 `<div>`, 본문은 `<p>`, 리스트는 `<ul><li>`
- [ ] 배지·레이블은 `<span>` 또는 `<small>`
- [ ] `<details><summary>` 짝·상호 위치 올바름

## Layer 5. Design (25점) — 스킬 특화

- [ ] **스타일 미지정 = 1번 Corporate Minimal** 자동 적용 (N6 RECOGNITION)
- [ ] 해당 스타일의 **radius·보더·배지 색 고정값** 그대로 사용 (변형 금지, N4)
- [ ] 8스타일 내부 일관성 (한 문서 내 스타일 섞지 않음)
- [ ] 3색 이내 (N8 MINIMAL) — 액센트 팔레트 포함

## Layer 6. Brand (12점) — 스킬 특화

- [ ] font-family 지정 없음 (G/⑧)
- [ ] 등록 팔레트(Oxford Blue 등)는 지정 용도에서만
- [ ] design-skill CORE(3색 시스템·여백 철학)과 충돌 없음

---

## 옵시디언 렌더 실측 체크 (forbidden 기반 전수)

QC 통과 전 반드시 체크:

- [ ] ❶ div 내부 빈줄 0개
- [ ] ❷ div 내부 마크다운 문법 0개
- [ ] ❸ 다크 div의 모든 텍스트 태그 `color` 명시
- [ ] ❹ 다크 div 내부 마크다운 테이블 없음
- [ ] ❺ div 블록 전후 빈줄 1개씩
- [ ] ❻ 인라인 style만 사용
- [ ] ❼ flex/grid 사용 시 리딩뷰 확인 완료
- [ ] ❽ font-family 미지정
- [ ] ❾ margin 미사용 (외부 간격은 `<br>`/빈줄)
- [ ] ❿ 보더/배경/레이블 기준선 이상
- [ ] ⓫ 연속 카드 사이 `<br>` 스페이서
- [ ] ⓬ `<details>` 내부 빈줄/마크다운 없음
- [ ] ⓭ `<summary>` 수동 삼각형 없음
- [ ] ⓮ `<br>` 다음 블록 태그 같은 줄 없음

## 합격 판정

- Total ≥80 점 **AND** Layer 1~4 ≥85%
- 14금칙 전수 PASS (하나라도 FAIL 시 산출 중단, 재작성)

## 불합격 처방

| 주 실패 Layer | 처방 포인터 |
|---|---|
| Layer 1 Syntax | → forbidden.md §대응 치트시트 |
| Layer 2 A11y | → tokens.md §색 안전 기준선, ❸ |
| Layer 5 Design | → snippets.md 해당 스타일 고정 스펙 재확인 |
| Layer 6 Brand | → tokens.md §액센트 팔레트, 1층 design-skill 확인 |
