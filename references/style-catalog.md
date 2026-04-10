# Style Catalog (2~8번)

디폴트(1번 Corporate Minimal) 외 7개 스타일의 핵심 스펙. 형이 "N번 스타일로"라고 지정하면 해당 섹션을 참조한다.

---

## Style 2: Warm Paper · 따뜻한 종이

| 항목 | 값 |
|------|-----|
| 배경 | `#fdf8f3` (아이보리) |
| 카드 배경 | `#fff9f2` |
| 카드 보더 | `1px solid #e0d4c4` |
| radius | `2px` (직각에 가까움) |
| 텍스트 기본 | `#3d2e1f` |
| 텍스트 보조 | `#8a7560` |
| 레이블 | `#886644` |
| 배지 | 보더 `1px solid #c4a880`, 배경 투명, 색 `#6a5540` |
| 구분선 | `#c8b090`, 40px 너비, 센터 |
| 제목 (.md) | `font-size: 22px`, `font-weight: 700` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 700` |
| 폰트 (.html) | `'Playfair Display'` (제목), `'Noto Sans KR'` (본문) |
| 톤 | 품격, 따뜻함, 전통 |
| 적합 | 제안서, 계약 요약, 인문적 콘텐츠 |

---

## Style 3: Notion-like Clean · 노션 스타일

| 항목 | 값 |
|------|-----|
| 배경 | `#ffffff` |
| 외곽 보더 | `1.5px solid #c0b8a8` |
| 레이아웃 | 클린 레이아웃 (카드·테이블·관계도 등 모든 구조 지원) |
| 행 구분 | `border-bottom: 1px solid #c0b8a8` |
| 텍스트 기본 | `#37352f` |
| 텍스트 보조 | `#787774` |
| 레이블 | `#9b9a97` |
| 배지 | 배경 `#ddd8d0`, 색 `#444`, radius `3px` |
| 콜아웃 (노트) | 배경 `#e8e5df`, radius `3px`, 좌측 이모지 |
| 제목 (.md) | `font-size: 24px`, `font-weight: 700`, `#37352f` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 700`, `#37352f` |
| 톤 | 명료, 효율, 현대적 |
| 적합 | 내부 메모, 정리 문서, 범용 클린 레이아웃 |

---

## Style 4: Soft Glass · 소프트 글래스

| 항목 | 값 |
|------|-----|
| 외곽 | 그라디언트 `linear-gradient(135deg, #667eea, #764ba2)`, 3px 패딩 |
| 카드 배경 | `rgba(255,255,255,0.92)` + `backdrop-filter: blur(20px)` |
| 내부 카드 | `rgba(255,255,255,0.6)`, 보더 `rgba(102,126,234,0.15)` |
| radius | `12~14px` |
| 텍스트 기본 | `#2d2b55` |
| 텍스트 보조 | `#7777aa` |
| 레이블 | `#667eea` |
| 배지 | 그라디언트 배경, 색 `#667eea`, radius `100px` |
| 제목 (.md) | `font-size: 22px`, `font-weight: 700` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 700` |
| 톤 | 세련, 부드러움, 현대적 고급감 |
| 적합 | 프레젠테이션 보조 자료 |
| .md 제한 | `backdrop-filter` 미지원 → 불투명 배경으로 대체 |

---

## Style 5: Dark Executive · 다크 이그제큐티브

| 항목 | 값 |
|------|-----|
| 배경 | `#1a1a2e` |
| 카드 배경 | `rgba(255,255,255,0.04)`, 보더 `rgba(255,255,255,0.08)` |
| radius | `10px` |
| 텍스트 기본 | `#e8e6e3` |
| 텍스트 보조 | `rgba(255,255,255,0.4)` |
| 레이블 | `rgba(255,255,255,0.35)` |
| 배지 | 배경 `rgba(255,255,255,0.06)`, 보더 `rgba(255,255,255,0.08)` |
| 노트 | 배경 `rgba(255,200,100,0.04)`, 보더 `rgba(255,200,100,0.1)`, 색 `rgba(255,200,100,0.7)` |
| 제목 (.md) | `font-size: 22px`, `font-weight: 700` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 700` |
| 톤 | 무게감, 권위, 프리미엄 |
| 적합 | 경영진 브리핑 |
| .md 제한 | `rgba` 투명도 → 옵시디언에서 불투명 색상으로 대체 필수. 카드: `#252540`, 텍스트: `#e8e6e3`, 보조: `#888899` |

---

## Style 6: Blueprint · 블루프린트

| 항목 | 값 |
|------|-----|
| 배경 | `#f0f4f8` (모눈 패턴 — .html만. .md에서는 단색) |
| 외곽 보더 | `2px solid #c4d5e8` |
| 카드 배경 | `rgba(255,255,255,0.7)` → .md: `#f8fafc` |
| 카드 보더 | `1px solid #a0b8d0` |
| radius | `0px` (직각) |
| 텍스트 기본 | `#1a365d` |
| 텍스트 보조 | `#4a6785` |
| 레이블 | `#2c5282`, uppercase, `letter-spacing: 2px` |
| 배지 | 보더 `1px dashed #a0b8d0`, 배경 투명 |
| 폰트 (.html) | `'JetBrains Mono'` (레이블), `'Inter'` (제목/본문) |
| 제목 (.md) | `font-size: 22px`, `font-weight: 700` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 700` |
| 톤 | 분석적, 구조적, 엔지니어링 |
| 적합 | 기술 문서, 구조 분석 |

---

## Style 7: Swiss Typography · 스위스 타이포

| 항목 | 값 |
|------|-----|
| 배경 | `#ffffff` |
| 상단 악센트 | `border-top: 8px solid #e00` |
| 카드 구분 | `border-top: 2px solid #000` (보더, 카드 배경 없음) |
| radius | `0px` (직각) |
| 텍스트 기본 | `#000` |
| 텍스트 보조 | `#888` |
| 레이블 | `#e00`, `10px`, `font-weight: 700`, uppercase, `letter-spacing: 2px` |
| 배지 | 보더 `2px solid #000`, 배경 투명, uppercase |
| 제목 (.md) | `font-size: 22px`, `font-weight: 900` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 900` |
| 날짜 (.md) | `font-size: 16px`, `font-weight: 300`, `#bbb` |
| 날짜 (.html) | `font-size: 16px`, `font-weight: 300`, `#ddd` |
| 톤 | 단호, 강렬, 권위적 명료 |
| 적합 | 의사결정 문서, 경영 보고 |

---

## Style 8: Soft Pastel · 소프트 파스텔

| 항목 | 값 |
|------|-----|
| 배경 | `#f8f7ff` (연한 라벤더) |
| 카드 배경 | `#ffffff` |
| 카드 보더 | `1px solid #ece9f8` |
| 카드 상단 악센트 | 카드1: `3px solid #a8d8ea`, 카드2: `3px solid #e8a8c8` (교차) |
| radius | `16px` (큰 라운딩) |
| 텍스트 기본 | `#3d3870` |
| 텍스트 보조 | `#7a75a0` |
| 레이블 | `#9994c4` |
| 배지 | 카드1: 배경 `#e8f4f8`, 카드2: 배경 `#fce8f0`, 색 `#8a85b0` |
| 노트 | 배경 `#fff`, 보더 `1px solid #ece9f8`, radius `12px` |
| 제목 (.md) | `font-size: 22px`, `font-weight: 700` |
| 제목 (.html) | `font-size: 24px`, `font-weight: 700` |
| 톤 | 친근, 부드러움, 캐주얼 |
| 적합 | 내부 공유, 브레인스톰 |
