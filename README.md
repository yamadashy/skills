# skills

A personal collection of [Agent Skills](https://www.anthropic.com/news/skills) maintained by [@yamadashy](https://github.com/yamadashy).

## Installation

```bash
npx skills add yamadashy/skills
```

## Skills

| Category | Skill | Description |
| --- | --- | --- |
| Sub-agent | [claude-exec](skills/claude-exec/SKILL.md) | Delegate a task to the Claude Code CLI as a sub-agent. |
| Sub-agent | [codex-exec](skills/codex-exec/SKILL.md) | Delegate a task to the OpenAI Codex CLI as a sub-agent. |
| Sub-agent | [antigravity-exec](skills/antigravity-exec/SKILL.md) | Delegate a task to the [Antigravity CLI](https://antigravity.google/docs/cli-getting-started) (`agy`) as a sub-agent. |
| Code review | [codex-review-loop](skills/codex-review-loop/SKILL.md) | Run an iterative Codex review-and-fix loop over a change. |
| Pull request | [pr-fix](skills/pr-fix/SKILL.md) | Drive a PR to mergeable — address review feedback and fix failing CI, then reply and resolve threads. |
| Document | [pdfvision](skills/pdfvision/SKILL.md) | Extract text, metadata, layout, image boxes, OCR, and rendered page PNGs from a PDF via the [pdfvision](https://github.com/yamadashy/pdfvision) CLI. |
| Memory | [agent-carnet](skills/agent-carnet/SKILL.md) | Persistent file-based notebook for AI agents and humans — save, recall, and organize notes across sessions, backed by [agent-carnet](https://github.com/yamadashy/agent-carnet). |

Each skill lives under [`skills/<name>/`](skills) with its own `SKILL.md`.
