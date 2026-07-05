# skills

A personal collection of [Agent Skills](https://www.anthropic.com/news/skills) maintained by [@yamadashy](https://github.com/yamadashy).

## Installation

```bash
npx skills add yamadashy/skills
```

## Skills

Bundled in this repository — installed together by the command above.

| Category | Skill | Description |
| --- | --- | --- |
| Sub-agent | [claude-exec](skills/claude-exec/SKILL.md) | Delegate a task to the Claude Code CLI as a sub-agent. |
| Sub-agent | [codex-exec](skills/codex-exec/SKILL.md) | Delegate a task to the OpenAI Codex CLI as a sub-agent. |
| Sub-agent | [antigravity-exec](skills/antigravity-exec/SKILL.md) | Delegate a task to the [Antigravity CLI](https://antigravity.google/docs/cli-getting-started) (`agy`) as a sub-agent. |
| Code review | [claude-review-loop](skills/claude-review-loop/SKILL.md) | Run an iterative Claude review-and-fix loop over a change. |
| Code review | [codex-review-loop](skills/codex-review-loop/SKILL.md) | Run an iterative Codex review-and-fix loop over a change. |
| Pull request | [pr-fix](skills/pr-fix/SKILL.md) | Drive a PR to mergeable — address review feedback and fix failing CI, then reply and resolve threads. |
| Pull request | [pr-vet](skills/pr-vet/SKILL.md) | Vet a PR and its author for supply-chain risk — runs isolated in a sub-agent, resists prompt-injection and hidden-Unicode smuggling, checks account reputation, scans the diff, and maps it to current attack techniques. |
| Pull request | [renovate-merge](skills/renovate-merge/SKILL.md) | Batch-merge Renovate dependency PRs safely — gates each on GitHub-verified bot commits, non-major scope, a confined diff + supply-chain scan, release cooldown, green CI, and mergeable state, then auto-approves and merges only the ones that clear every gate. |
| Insight | [only-you](skills/only-you/SKILL.md) | Surface the insights about a repository that only a frontier-tier model can produce — scouts with cheap subagents, judges itself, and discards anything a routine review would also have found. |
| Writing | [readable-japanese](skills/readable-japanese/SKILL.md) | Tune Japanese prose into a readable rhythm — checks phonological clashes, prosody/syntax alignment, and end-of-sentence monotony, without altering meaning. (Japanese content — see CLAUDE.md.) |

Each bundled skill lives under [`skills/<name>/`](skills) with its own `SKILL.md`.

## Skills in their own repositories

These have their own home repository — install each directly:

| Repository | Skills | Install |
| --- | --- | --- |
| [agent-carnet](https://github.com/yamadashy/agent-carnet) | Persistent file-based notebook for AI agents and humans. | `npx skills add yamadashy/agent-carnet` |
| [pdfvision](https://github.com/yamadashy/pdfvision) | Extract text, metadata, layout, OCR, and rendered page PNGs from a PDF. | `npx skills add yamadashy/pdfvision` |
| [agent-readable](https://github.com/yamadashy/agent-readable) | Fetch clean, readable web content (arXiv, GitHub, MDN, PDF, SpeakerDeck, spec, Stack Overflow). | `npx skills add yamadashy/agent-readable` |
