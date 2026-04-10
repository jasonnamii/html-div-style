# html-div-style

> 🇰🇷 [한국어 README](./README.ko.md)

**HTML div design system with 8 visual styles, Obsidian compatibility, and rendering stability rules.**

## Prerequisites

- **Obsidian Vault** — required when outputting `.md` files (14 rendering rules enforce Obsidian compatibility)
- **Claude Cowork or Claude Code** environment
- For standalone `.html` output, Obsidian is not required

## Goal

html-div-style provides a unified design system with 8 predefined visual styles (default: Corporate Minimal) that work across standalone HTML, Obsidian markdown, and mixed environments. Includes 14 anti-break rules for Obsidian rendering and markdown readability correction principles.

## When & How to Use

Deploy when producing HTML documents, styling markdown for Obsidian, or creating documents that render consistently across platforms. Select a style (1-8); the system applies div-based design patterns, color palettes, typography, and spacing rules automatically.

## Use Cases

| Scenario | Prompt | What Happens |
|---|---|---|
| Business report in HTML | `"Apply Corporate Minimal style to this report"` | Semantic divs→typography hierarchy→professional color palette→anti-break safeguards |
| Obsidian vault docs | `"Style documentation for Obsidian. Style 3."` | Div styling Obsidian renders cleanly→14 anti-break rules applied |
| Multi-platform document | `"Create doc that looks good in both HTML and Obsidian"` | Div-safe markdown→HTML styling + Obsidian syntax→readability correction |

## Key Features

- 8 visual styles: Corporate Minimal, Modern Minimal, Dark Professional, Warm Accessible, Minimalist Data, Creative Bold, Academic Formal, Startup Energetic
- Dual-platform: .html and Obsidian .md rendering without compromise
- 14 anti-break rules for Obsidian rendering stability
- Markdown readability correction principles
- Typography + color systems with 5-scale font weight hierarchy

## Works With

- **[deliverable-engine](https://github.com/jasonnamii/deliverable-engine)** — visual styling after structure
- **[obsidian-markdown](https://github.com/jasonnamii/obsidian-markdown)** — Obsidian-native syntax + rendering safety
- **[apple-design-style](https://github.com/jasonnamii/apple-design-style)** — minimalist alternative

## Installation

```bash
git clone https://github.com/jasonnamii/html-div-style.git ~/.claude/skills/html-div-style
```

## Update

```bash
cd ~/.claude/skills/html-div-style && git pull
```

Skills placed in `~/.claude/skills/` are automatically available in Claude Code and Cowork sessions.

## Part of Cowork Skills

This is one of 25+ custom skills. See the full catalog: [github.com/jasonnamii/cowork-skills](https://github.com/jasonnamii/cowork-skills)

## License

MIT License — feel free to use, modify, and share.
