# skills

A personal collection of [Agent Skills](https://www.anthropic.com/news/skills) maintained by [@yamadashy](https://github.com/yamadashy).

## Installation

```bash
npx skills add yamadashy/skills
```

## Skills

| Skill | Description |
| --- | --- |
| [carnet](skills/carnet/SKILL.md) | Persistent file-based notebook for AI agents and humans — save, recall, and organize notes across sessions. |
| [claude-exec](skills/claude-exec/SKILL.md) | Delegate a task to the Claude Code CLI as a sub-agent. |
| [codex-exec](skills/codex-exec/SKILL.md) | Delegate a task to the OpenAI Codex CLI as a sub-agent. |
| [codex-review-loop](skills/codex-review-loop/SKILL.md) | Run an iterative Codex review-and-fix loop over a change. |
| [pdfvision](skills/pdfvision/SKILL.md) | Extract text, metadata, layout, image boxes, OCR, and rendered page PNGs from a PDF via the pdfvision CLI. |

Each skill lives under [`skills/<name>/`](skills) with its own `SKILL.md`.
