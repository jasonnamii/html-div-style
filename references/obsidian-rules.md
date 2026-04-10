# Obsidian .md 렌더링 규칙

HTML div를 옵시디언 .md 파일에 삽입할 때 깨짐을 방지하는 규칙 모음. 이 규칙을 어기면 옵시디언이 HTML 블록을 마크다운으로 재해석하여 레이아웃이 붕괴한다.

---

## 14대 규칙

### ❶ div 내부 빈줄 절대 금지

`<div>` ~ `</div>` 사이에 빈 줄(empty line)이 1개라도 있으면, 옵시디언이 HTML 블록을 끊고 마크다운 파서로 전환한다.

```html
<!-- ❌ WRONG -->
<div style="padding: 24px;">

<p>텍스트</p>

</div>

<!-- ✅ CORRECT -->
<div style="padding: 24px;">
<p>텍스트</p>
</div>
```

### ❷ div 내부 마크다운 문법 금지

`<div>` 블록 안에서 `**볼드**`, `*이탤릭*`, `- 리스트`, `[[위키링크]]` 등 마크다운 문법을 쓰면 렌더링이 깨진다. HTML 태그만 사용한다.

| 마크다운 | HTML 대체 |
|----------|-----------|
| `**텍스트**` | `<strong>텍스트</strong>` |
| `*텍스트*` | `<em>텍스트</em>` |
| `- 항목` | `<ul><li>항목</li></ul>` |
| `[링크](url)` | `<a href="url">링크</a>` |
| `[[#헤딩]]` | div 바깥에서 사용 |

### ❸ 모든 텍스트 태그에 color 개별 지정

div의 `color` CSS는 하위 요소에 안정적으로 전파되지 않는다. 특히 다크 배경 div에서 `<p>`, `<strong>`, `<li>`, `<td>`, `<span>` 각각에 `style="color: ..."` 을 지정해야 한다.

```html
<!-- ❌ WRONG: div에만 color 지정 -->
<div style="background: #1a1a2e; color: #e8e6e3;">
<p>텍스트</p>
<strong>강조</strong>
</div>

<!-- ✅ CORRECT: 각 태그에 개별 지정 -->
<div style="background: #1a1a2e;">
<p style="color: #e8e6e3;">텍스트</p>
<strong style="color: #e8e6e3;">강조</strong>
</div>
```

### ❹ 다크 배경 div 내 마크다운 테이블 금지

옵시디언 테마의 행줄무늬(stripe)가 다크 배경을 override한다. 테이블이 필요하면 div 바깥에 배치하거나, HTML `<table>`을 사용하되 각 `<td>`에 `background-color`를 명시한다.

### ❺ div 블록 전후 빈줄 필수

div 블록 시작 전과 종료 후에 빈줄 1개씩. 없으면 전후 마크다운 콘텐츠가 div에 흡수된다.

```markdown
이전 마크다운 텍스트

<div style="padding: 20px;">
<p style="color: #333;">내용</p>
</div>

다음 마크다운 텍스트
```

### ❻ 인라인 style만 사용

옵시디언은 `<style>` 태그, `<link>` 태그, CSS class를 지원하지 않는다. 모든 스타일은 각 태그의 `style=""` 속성에 인라인으로 넣어야 한다.

### ❼ flex/grid 레이아웃: 리딩뷰 전용

`display: flex`와 `display: grid`는 옵시디언 리딩뷰(Reading View)에서는 작동하지만, 라이브프리뷰(Live Preview)에서 깨질 수 있다. 2컬럼 레이아웃 사용 시 반드시 라이브프리뷰 호환성을 고려하여 단일 컬럼 폴백을 제공하거나 "리딩뷰 권장" 안내를 문서 상단에 명시한다.

### ❽ 콜아웃 뒤 빈줄 필수

`> [!note]` 등 콜아웃 마지막 줄 뒤에 빈줄 1개. 없으면 후속 블록이 콜아웃에 흡수된다.

### ❾ 앵커링크 = 위키링크

div 바깥의 문서 내 링크는 `[text](#slug)` 대신 `[[#헤딩명]]` 위키링크를 사용한다. 옵시디언에서 앵커링크는 불안정하다.

### ❿ 중첩 div 최소화

div 안에 div를 3단 이상 중첩하면 옵시디언 라이브프리뷰에서 파싱이 불안정해진다. 최대 2단 중첩(외곽 + 내부 카드 1레벨)을 원칙으로 한다.

### ⓫ 연속 div 블록 사이 `<br>` 스페이서 필수

연속된 div 카드 사이에 빈줄 1개만 넣으면, 옵시디언이 카드를 붙여서 렌더링한다(간격 0). `<details>` 등 다른 블록이 끼어 있지 않은 순수 연속 div 카드는 반드시 `<br>` 스페이서를 넣어야 시각적 간격이 생긴다.

```html
<!-- ❌ WRONG: 빈줄만으로는 카드가 붙는다 -->
</div>

<div style="padding: 24px;">

<!-- ✅ CORRECT: <br> 스페이서 삽입 -->
</div>

<br>

<div style="padding: 24px;">
```

### ⓬ `<details>` 내부도 규칙 ❶❷ 동일 적용 (빈줄 금지 + HTML only)

`<details>` 블록은 옵시디언에서 `<div>`와 동일한 HTML 파싱 규칙을 따른다. 내부에 빈줄이 1개라도 있으면 옵시디언이 HTML 블록을 끊고 콘텐츠를 `<details>` 바깥으로 밀어낸다. 결과: 접기 토글(▶/▼)은 작동하지만 내용이 접히지 않는다.

**핵심 3규칙:**
1. `<details>` 내부 빈줄 절대 금지 (규칙 ❶과 동일)
2. `<details>` 내부 마크다운 문법 금지 — `<p>`, `<strong>` 등 HTML 태그만 (규칙 ❷와 동일)
3. 전후 여백은 `<br>` 스페이서로 제어 — 위(카드→details): `<br>` 1개, 아래(details→카드): `<br>` 2개

```html
<!-- ❌ WRONG: 빈줄 + 마크다운 → 접기 깨짐 (토글은 보이나 내용 안 접힘) -->
<details>
<summary><strong>제목</strong></summary>

**리서치 근거**: 내용...

**피디님 이점**: 내용...

</details>

<!-- ✅ CORRECT: 빈줄 없음 + HTML only → 접기 정상 작동 -->
</div>

<br>

<details>
<summary><strong>제목</strong></summary>
<p style="color: #555; font-size: 14px; margin: 0 0 8px 0;"><strong style="color: #111;">리서치 근거</strong>: 내용...</p>
<p style="color: #555; font-size: 14px; margin: 0 0 8px 0;"><strong style="color: #111;">피디님 이점</strong>: 내용...</p>
</details>

<br>

<br>

<div style="padding: 24px;">
```

**여백 비율:** details는 위 카드의 부속이므로 위 간격을 작게(br 1개), 아래 다음 카드와는 넓게(br 2개) 설정한다.

### ⓭ `<summary>` 내 수동 삼각형 문자 금지

`<details><summary>` 안에 `▶`, `►`, `▸`, `▹`, `◀`, `◄`, `◂`, `◃` 등 삼각형 유니코드 문자를 넣으면, 옵시디언이 자체적으로 렌더링하는 토글 삼각형과 중복되어 `▶ ▶ 제목` 형태로 보인다.

```html
<!-- ❌ WRONG: 삼각형 중복 -->
<summary><strong>▶ 상세 근거</strong></summary>

<!-- ✅ CORRECT: 삼각형 없이 -->
<summary><strong>상세 근거</strong></summary>
```

### ⓮ `<br>` 뒤 같은 줄에 블록 태그 금지

`<br><div ...>` 처럼 `<br>`과 블록 레벨 태그(`<div>`, `<table>`, `<details>`, `<section>`)가 같은 줄에 있으면, 옵시디언이 새 HTML 블록의 시작을 인식하지 못하고 이전 컨텍스트에서 마크다운 파서로 전환한다. 결과: div 내부 스타일이 전부 무시되고 마크다운으로 렌더링됨.

```html
<!-- ❌ WRONG: br과 div가 같은 줄 → 스타일 무시 -->
<br><div style="padding: 24px;">

<!-- ✅ CORRECT: br 단독 줄 + 빈줄 + div 새 줄 -->
<br>

<div style="padding: 24px;">
```

---

## .md용 가독성 보정 원칙

옵시디언 .md에서 HTML div를 렌더링하면 .html 대비 가독성이 떨어진다. 원인과 보정 전략:

| 축 | 원인 | 보정 |
|---|------|------|
| 시각 위계 | .md에서 font-size 제어가 제한적 → 공간·보더로 위계 표현 | 카드 간 gap, padding, 보더 두께·색으로 구분. 제목은 최소 `font-size: 22px` 명시 |
| 테마 저항성 | 옵시디언 테마가 연한 보더·배경을 흡수하여 카드가 투명해짐 | 보더를 1차 구분자로 사용. `#b0b0b0` 이상 명도. 배경은 `#efefef` 이상 |
| 색상 진화 | 옵시디언 라이트/다크 테마 모두에서 텍스트가 읽혀야 함 | .html 대비 색상값을 ~2단계 진하게 설정. 보조텍스트 `#555`, 레이블 `#666` |

**핵심:** 스타일 파일의 `.md용` 값은 `.html용`보다 항상 진해야 한다. 동일값 사용 시 .md에서 흐려 보인다.

---

## .md용 코드 패턴 (복사용)

### 기본 박스

```html
<div style="background: #efefef; border: 1.5px solid #b0b0b0; border-radius: 8px; padding: 24px;">
<p style="color: #111; font-size: 14px; margin: 0;">텍스트</p>
</div>
```

### 2컬럼 (리딩뷰 전용)

```html
<div style="display: flex; gap: 16px;">
<div style="flex: 1; background: #efefef; border: 1.5px solid #b0b0b0; border-radius: 8px; padding: 24px;">
<p style="color: #111; margin: 0;">좌측</p>
</div>
<div style="flex: 1; background: #efefef; border: 1.5px solid #b0b0b0; border-radius: 8px; padding: 24px;">
<p style="color: #111; margin: 0;">우측</p>
</div>
</div>
```

### 주의 박스

```html
<div style="background: #e8e8e8; border-left: 3px solid #777; padding: 16px 20px; border-radius: 0 8px 8px 0;">
<p style="color: #444; font-size: 13px; margin: 0;">주의 내용</p>
</div>
```

---

## 서브에이전트 전파 템플릿

이 스킬이 서브에이전트에 위임할 때 아래 규칙을 프롬프트에 포함한다:

```
## Obsidian 렌더링 규칙 (필수)
❶ div 내부 빈줄 금지: <div>~</div> 사이 빈줄 0개
❷ div 내부 마크다운 금지: **·*·-·[[]] 금지 → <strong>·<em>·<ul><li> 사용
❸ 모든 텍스트 태그에 color 개별 지정 (div color 미전파)
❹ 다크배경 div 내 마크다운 테이블 금지
❺ div 블록 전후 빈줄 1개씩
❻ 인라인 style만 (class·<style> 태그 금지)
❼ flex/grid는 리딩뷰 전용
❽ 콜아웃 뒤 빈줄 필수
❾ 앵커링크 = 위키링크
❿ 중첩 div 최대 2단
⓫ 연속 div 카드 사이 <br> 스페이서 필수 (빈줄만으로는 간격 0)
⓬ <details> 내부도 ❶❷ 동일: 빈줄 금지 + HTML only. 전후 여백은 <br> (위 1개, 아래 2개)
⓭ <summary> 내 수동 삼각형 문자 금지: ▶·►·▸·▹·◀·◄·◂·◃ 금지 (옵시디언 네이티브 삼각형과 중복)
⓮ <br> 뒤 같은 줄에 블록 태그 금지: <br><div>는 ✗. <br> 단독 줄 + 빈줄 + <div> 새 줄 필수
## 가독성 보정 (필수)
- 카드 보더: #b0b0b0 이상. 연한 보더(#eee)는 테마에 흡수됨
- 카드 배경: #efefef 이상. #fafafa는 흰 배경과 구분 불가
- 제목: font-size 22px 이상 명시. 기본값 사용 금지
- 배지: 배경+보더+텍스트 3요소 모두 지정
```

---

## 검증 체크리스트

.md 파일에 HTML div 삽입 후 아래 항목을 grep/목시로 확인:

- [ ] div 내부 빈줄 0개
- [ ] div 내부 마크다운 문법 0개
- [ ] 다크배경 div 내 모든 텍스트 태그에 color 지정
- [ ] div 블록 전후 빈줄 존재
- [ ] `<style>` 태그 0개, class 속성 0개
- [ ] div 중첩 3단 이상 0개
- [ ] 연속 div 카드 사이 `<br>` 스페이서 존재 (빈줄만 있는 곳 0개)
- [ ] `<details>` 내부 빈줄 0개 (규칙 ❶과 동일)
- [ ] `<details>` 내부 마크다운 문법 0개 (규칙 ❷와 동일)
- [ ] `<details>` 전에 `<br>` 1개, 후에 `<br>` 2개 존재
- [ ] `<summary>` 태그 내 삼각형 문자(▶/►/▸/▹/◀/◄/◂/◃) 0개 (규칙 ⓭)
- [ ] `<br>` 뒤 같은 줄에 블록 태그(`<div>`/`<table>`/`<details>`/`<section>`) 없음 (규칙 ⓮)
