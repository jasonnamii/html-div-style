# snippets.md — html-div-style 8스타일 스니펫 라이브러리

이 스킬의 **유일한 고유물**. 공통 참조(tokens/forbidden/qc)는 모든 html-* 스킬 공용이지만, 스니펫은 스킬마다 다름.

> 각 스타일의 **풀 스펙 + 코드 예시**는 기존 spec 파일에 유지(하위호환):
> - Style 1 Corporate Minimal: `→ style-corporate.md`
> - Style 2~8: `→ style-catalog.md`

---

## 8스타일 인덱스

| # | 이름 | 디폴트 | 톤 | 적합 | 스펙 파일 |
|---|---|---|---|---|---|
| 1 | **Corporate Minimal** | ✅ | 절제·신뢰 | 비즈니스·분석·범용 | `style-corporate.md` |
| 2 | Warm Paper | | 품격·따뜻함 | 제안서·계약 요약 | `style-catalog.md §Style 2` |
| 3 | Notion-like Clean | | 명료·효율 | 내부 메모·정리 | `style-catalog.md §Style 3` |
| 4 | Soft Glass | | 세련·부드러움 | 프레젠·프로토타입 | `style-catalog.md §Style 4` |
| 5 | Dark Executive | | 무게감·권위 | 경영진 브리핑 | `style-catalog.md §Style 5` |
| 6 | Blueprint | | 분석·구조 | 기술문서·목업 | `style-catalog.md §Style 6` |
| 7 | Swiss Typography | | 단호·강렬 | 의사결정 문서 | `style-catalog.md §Style 7` |
| 8 | Soft Pastel | | 친근·캐주얼 | 내부공유·브레인스톰 | `style-catalog.md §Style 8` |

---

## 로딩 규칙

| 조건 | 로드 |
|---|---|
| 스타일 미지정 | `style-corporate.md` (디폴트 1번) |
| "1번 스타일로" | `style-corporate.md` |
| "N번 스타일로" (2~8) | `style-catalog.md` 해당 섹션 |

같은 문서 내 스타일 섞지 말 것(Layer 5 Design, N4 CONSISTENCY).

---

## 공통 프리미티브 (모든 스타일 공유)

### 카드 기본 골격

```html
<div style="padding:20px;border:1px solid #b0b0b0;border-radius:6px;background:#fff;">
<p style="color:#333;font-size:15px;line-height:1.6;">본문 내용</p>
</div>
```

### 다크 카드 (color 하위 전파 금지 → 각 태그 명시)

```html
<div style="padding:20px;border-radius:6px;background:#002147;">
<p style="color:#fff;font-size:15px;line-height:1.6;">본문</p>
<strong style="color:#fff;">강조</strong>
</div>
```

### 연속 카드 사이 (⓫ 스페이서)

```html
<div style="...">카드 A</div>

<br>

<div style="...">카드 B</div>
```

### `<details>` 토글 (⓬·⓭)

```html
<details>
<summary>제목만 (삼각형 문자 금지)</summary>
<div style="padding:12px;">
<p style="color:#333;">내용 — 내부 빈줄·마크다운 금지</p>
</div>
</details>
```

### 배지·레이블

```html
<span style="display:inline-block;padding:2px 8px;border:1px solid #666;border-radius:3px;font-size:12px;color:#333;">BADGE</span>
```

---

## 스타일별 고정 스펙 요약 (변형 금지, N4)

| # | radius | 보더 | 배지 | 제목 size |
|---|---|---|---|---|
| 1 Corporate | `4px` | `1px solid #b0b0b0` | `border 1px solid #666` | `22px/700` |
| 2 Warm Paper | `2px` | `1px solid #e0d4c4` | `border 1px solid #c4a880` | `22px/700` |
| 3 Notion | (없음) | 외곽 `1.5px solid #c0b8a8` | `bg #ddd8d0` | `22px/600` |
| 4 Soft Glass | `12px` | `1px solid #d0d0d0` | `bg #f0f0f5` | `22px/600` |
| 5 Dark Exec | `4px` | `1px solid #2a2a3e` | `bg #3a3a4e` (color `#fff`) | `22px/700` |
| 6 Blueprint | `0px` | `1px solid #4a6b8a` | `border 1px solid #4a6b8a` | `22px/600` |
| 7 Swiss | `0px` | 굵은 `3px solid #000` | `bg #000 color #fff` | `22px/700` |
| 8 Soft Pastel | `16px` | `1px solid #e5d6e8` | `bg #f5e6f8` | `22px/600` |

**풀 스펙**(텍스트색·배지 패딩·레이블 등): 각 스타일 스펙 파일 참조.

---

## 1층·2층 레이어링

이 스킬은 **2층(HTML div)**. 1층(md 네이티브: 콜아웃·테이블·볼드·헤딩)은 **design-skill 이쁘니** 담당.

| 층 | 담당 | 내용 |
|---|---|---|
| 1층 | design-skill 이쁘니 | 콜아웃·위계·여백 |
| 2층 | **이 스킬** | 카드 배경·flex·색상 강조 |

일반 문서: 1층 먼저, 2층 얹음. "이 스타일로만" 명시 요청 = 1층 스킵 허용.

---

## UX 원리 준수 (snippets 레벨)

| 원리 | 스니펫 반영 |
|---|---|
| N4 CONSISTENCY | 위 표의 고정 스펙 = 재인 기반 |
| N6 RECOGNITION | radius·보더·배지 색상 고정값 |
| N8 MINIMAL | 3색 준수·font-family 미지정 |

상세: `→ ux-principles.md §A N4·N6·N8`
