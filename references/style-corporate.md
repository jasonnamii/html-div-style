# Style 1: Corporate Minimal (디폴트)

뉴트럴 그레이 기반, 테마 저항성 높은 보더와 충분한 명암비로 옵시디언 .md에서도 선명하게 렌더링된다. 비즈니스 문서·분석 보고서·일반 문서에 범용 적합.

---

## 색상 팔레트

| 역할 | .md용 | .html용 |
|------|-------|---------|
| 배경 (페이지) | 투명 (마크다운 기본) | `#ffffff` |
| 카드 배경 | `#efefef` | `#efefef` |
| 카드 보더 | `1.5px solid #b0b0b0` | `1.5px solid #b0b0b0` |
| 카드 radius | `8px` | `8px` |
| 텍스트 기본 | `#111` | `#111` |
| 텍스트 보조 | `#555` | `#555` |
| 레이블 (role) | `#666` | `#666` |
| 배지 배경 | `#ddd` | `#ddd` |
| 배지 텍스트 | `#333` | `#333` |
| 배지 보더 | `1px solid #999` | `1px solid #999` |
| 강조선 (노트박스) | `border-left: 3px solid #777` | `border-left: 3px solid #777` |
| 노트박스 배경 | `#e8e8e8` | `#e8e8e8` |
| 노트박스 텍스트 | `#444` | `#444` |
| 구분선 | `border-bottom: 1px solid #ccc` | `border-bottom: 1px solid #ccc` |

## 타이포그래피

| 요소 | .md용 | .html용 |
|------|-------|---------|
| 폰트 | 옵시디언 기본 (지정 금지) | `'Inter', 'Noto Sans KR', sans-serif` |
| 제목 | `font-size: 22px`, `font-weight: 700` | `24px`, `font-weight: 700` |
| 본문 | 기본 크기 | `14px`, `font-weight: 400` |
| 레이블 | `font-size: 12px` | `11px`, `font-weight: 600`, `text-transform: uppercase`, `letter-spacing: 1px` |
| 보조텍스트 | `font-size: 13px` | `12px` |
| 배지 | `font-size: 12px` | `11px`, `font-weight: 600` |

---

## 박스 타입 (.md용)

### ① 기본 카드

```html
<div style="background: #efefef; border: 1.5px solid #b0b0b0; border-radius: 8px; padding: 24px;">
<div style="font-size: 11px; font-weight: 600; color: #666; text-transform: uppercase; letter-spacing: 1px; margin-bottom: 8px;">레이블</div>
<div style="font-size: 22px; font-weight: 700; color: #111; margin-bottom: 4px;">제목</div>
<div style="font-size: 12px; color: #555; line-height: 1.4;">설명 텍스트</div>
<span style="display: inline-block; margin-top: 12px; font-size: 11px; font-weight: 600; padding: 4px 12px; border-radius: 4px; background: #ddd; border: 1px solid #999; color: #333;">배지</span>
</div>
```

### ② 헤더 (제목 + 날짜)

```html
<div style="display: flex; justify-content: space-between; align-items: center; padding-bottom: 16px; border-bottom: 1px solid #ccc; margin-bottom: 24px;">
<span style="font-size: 22px; font-weight: 700; color: #111;">문서 제목</span>
<span style="font-size: 13px; color: #666;">2026.04.05</span>
</div>
```

### ③ 노트 박스 (경고/참고)

```html
<div style="background: #e8e8e8; border-left: 3px solid #777; padding: 16px 20px; border-radius: 0 8px 8px 0;">
<p style="font-size: 13px; color: #444; line-height: 1.6; margin: 0;">참고 내용</p>
</div>
```

### ④ 커넥터 (관계 표시)

```html
<div style="text-align: center; font-size: 13px; font-weight: 600; color: #888; padding: 8px 0;">◀ MOU ▶</div>
```

### ⑤ 2컬럼 레이아웃 (리딩뷰 전용)

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

### ⑥ 3컬럼 레이아웃 (리딩뷰 전용)

```html
<div style="display: flex; gap: 16px;">
<div style="flex: 1; background: #efefef; border: 1.5px solid #b0b0b0; border-radius: 8px; padding: 24px;">
<p style="color: #111; margin: 0;">좌</p>
</div>
<div style="text-align: center; font-size: 13px; font-weight: 600; color: #888; display: flex; align-items: center;">◀ ▶</div>
<div style="flex: 1; background: #efefef; border: 1.5px solid #b0b0b0; border-radius: 8px; padding: 24px;">
<p style="color: #111; margin: 0;">우</p>
</div>
</div>
```

---

## 조합 원칙

| 원칙 | 설명 |
|------|------|
| 카드 내부 요소 순서 | 레이블 → 제목 → 설명 → 배지 (고정) |
| 여백 | 카드 간 gap 16px, 카드 내 padding 24px |
| 밀도 | 텍스트 밀도 중간. 카드당 4~6줄 적정 |
| 다크 카드 | 이 스타일에서는 사용하지 않는다. 밝은 톤 유지 |
| 테이블 | div 바깥에 마크다운 테이블 사용. div 내부 테이블은 HTML `<table>` |
| 배지 삼중 단서 | 배경색 + 보더 + 텍스트색 3요소 모두 적용. 단일 요소만으로는 옵시디언 테마에 따라 소실 가능 |

---

## Gotchas

- .md에서 `font-family` 지정하면 옵시디언 기본 폰트와 충돌하여 어색해진다. .md에서는 font-family 지정 금지
- radius 값을 크게 잡으면(16px+) 옵시디언에서 카드가 둥글어 보이는데, 작은 카드에서는 내용이 잘린다. 8px 고정
- `margin`은 옵시디언 div에서 예측 불가. `padding`만 사용하고 간격은 div 사이 빈줄로 조절
- 카드 배경·보더가 너무 연하면(`#fafafa`, `#eee` 수준) 옵시디언 라이트 테마에서 카드가 투명처럼 보인다. 배경 `#efefef` / 보더 `#b0b0b0` 이상을 유지한다
- 제목(헤더) font-size를 기본값으로 두면 옵시디언에서 본문과 시각적 구분이 약해진다. .md에서 최소 `22px`, .html에서 최소 `24px`를 명시한다
