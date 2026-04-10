# HTML div 디자인 시스템

> 🇺🇸 [English README](./README.md)

**8가지 비주얼 스타일, Obsidian 호환성, 렌더링 안정성 규칙을 갖춘 HTML div 디자인 시스템입니다.**

## 사전 요구사항

- **Obsidian Vault** — `.md` 파일을 출력할 때 필수 (14개 렌더링 규칙이 Obsidian 호환성을 보장)
- **Claude Cowork 또는 Claude Code** 환경
- 독립형 `.html` 출력의 경우 Obsidian은 필수 아님

## 목적

html-div-style은 8개의 사전 정의된 비주얼 스타일(기본값: Corporate Minimal)을 제공하는 통합 디자인 시스템입니다. 독립형 HTML, Obsidian markdown, 혼합 환경에서 모두 작동합니다. Obsidian 렌더링을 위한 14개의 방지 규칙과 markdown 가독성 개선 원칙을 포함합니다.

## 사용 시점 및 방법

HTML 문서를 생성할 때, Obsidian용 markdown을 스타일링할 때, 또는 플랫폼 전반에 걸쳐 일관되게 렌더링되는 문서를 만들 때 배포합니다. 스타일을 선택(1~8)하면 시스템이 div 기반 디자인 패턴, 색상 팔레트, 타이포그래피, 간격 규칙을 자동으로 적용합니다.

## 사용 예시

| 상황 | 프롬프트 | 결과 |
|---|---|---|
| HTML 비즈니스 보고서 | `"이 보고서에 Corporate Minimal 스타일을 적용해줘"` | 시맨틱 div→타이포그래피 계층→전문적 색상 팔레트→방지 규칙 적용 |
| Obsidian vault 문서 | `"문서를 Obsidian용으로 스타일링해줘. 스타일 3."` | div 스타일링 Obsidian 깔끔하게 렌더→14개 방지 규칙 적용 |
| 멀티플랫폼 문서 | `"HTML과 Obsidian 모두에서 잘 보이는 문서를 만들어줘"` | div-안전 markdown→HTML 스타일 + Obsidian 문법→가독성 개선 |

## 핵심 기능

- 8가지 비주얼 스타일: Corporate Minimal, Modern Minimal, Dark Professional, Warm Accessible, Minimalist Data, Creative Bold, Academic Formal, Startup Energetic
- 듀얼 플랫폼: .html과 Obsidian .md 렌더링 모두 완벽 지원
- Obsidian 렌더링 안정성을 위한 14개 방지 규칙
- Markdown 가독성 개선 원칙
- 5단계 글꼴 굵기 계층을 가진 타이포그래피 + 색상 시스템

## 연관 스킬

- **[deliverable-engine](https://github.com/jasonnamii/deliverable-engine)** — 구조 후 비주얼 스타일링
- **[obsidian-markdown](https://github.com/jasonnamii/obsidian-markdown)** — Obsidian 네이티브 문법 + 렌더링 안전성
- **[apple-design-style](https://github.com/jasonnamii/apple-design-style)** — 미니멀 대안

## 설치

```bash
git clone https://github.com/jasonnamii/html-div-style.git ~/.claude/skills/html-div-style
```

## 업데이트

```bash
cd ~/.claude/skills/html-div-style && git pull
```

`~/.claude/skills/`에 배치된 스킬은 Claude Code 및 Cowork 세션에서 자동으로 사용할 수 있습니다.

## Cowork 스킬 생태계

25개 이상의 커스텀 스킬 중 하나입니다. 전체 카탈로그: [github.com/jasonnamii/cowork-skills](https://github.com/jasonnamii/cowork-skills)

## 라이선스

MIT 라이선스 — 자유롭게 사용, 수정, 공유하세요.