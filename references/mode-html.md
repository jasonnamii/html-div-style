# MODE: HTML 단독 파일

단독 .html 파일로 출력할 때의 규칙. .md 렌더링 규칙(obsidian-rules.md)과 무관하게 풀 HTML/CSS를 사용할 수 있다.

---

## 기본 구조

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>{문서 제목}</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Noto+Sans+KR:wght@300;400;500;700;900&display=swap');
  * { margin: 0; padding: 0; box-sizing: border-box; }
  body { font-family: 'Inter', 'Noto Sans KR', sans-serif; }
  /* 스타일별 CSS 여기 */
</style>
</head>
<body>
  <!-- 콘텐츠 -->
</body>
</html>
```

## 폰트 CDN

| 스타일 | 추가 폰트 |
|--------|-----------|
| 기본 (모든 스타일) | Inter + Noto Sans KR |
| Style 2 (Warm Paper) | + Playfair Display |
| Style 6 (Blueprint) | + JetBrains Mono |

```
https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&family=Noto+Sans+KR:wght@300;400;500;700;900&family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=JetBrains+Mono:wght@400;500&display=swap
```

## .md와의 차이점

| 항목 | .md | .html |
|------|-----|-------|
| `<style>` 태그 | 금지 | 사용 |
| CSS class | 금지 | 사용 |
| font-family | 지정 금지 | 필수 |
| flex/grid | 리딩뷰 전용 | 자유 |
| 빈줄 | div 내부 금지 | 자유 |
| 마크다운 혼용 | 금지 | 해당 없음 |
| 중첩 div | 최대 2단 | 자유 |
| rgba/투명도 | 불투명 대체 | 자유 |
| backdrop-filter | 미지원 | 사용 |

## 반응형 가이드

```css
@media (max-width: 768px) {
  .parties { grid-template-columns: 1fr !important; }
  .header h2 { font-size: 24px !important; }
}
```

## 저장 위치

.html 파일은 mnt/_inbox/ (Cowork 출력 폴더)에 저장하여 computer:// 링크로 제공한다.
