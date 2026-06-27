# CLAUDE.md

Guidance for AI agents (and humans) working in this repository.

## What this repo is

A curated, version-controlled collection of [Agent Skills](https://www.anthropic.com/news/skills),
installable in one step via `npx skills add yamadashy/skills`. Skills that used
to live scattered across `~/.agents/skills` and per-project `.agents/skills`
directories are centralized here so they are portable and reproducible.

It holds two kinds of skill:

- **Bundled** — small, general skills with no home of their own, vendored under
  `skills/<name>/` and installed together by the command above.
- **Referenced** — skills that ship from their own repository (e.g. a CLI's repo).
  These are *not* copied in; the README lists them with their own
  `npx skills add <owner>/<repo>` command so each stays the single source of truth.

## Philosophy

- **One home, one command.** A skill is only worth having if it's findable and
  installable later. Centralize it here instead of re-deriving the same setup on
  every machine or in every project.
- **Skills stay thin and composable.** Each skill does one thing and stays
  small. Prefer wrapping an existing tool over reimplementing its behavior.
- **Document only verified behavior.** Before writing a flag or a claim into a
  `SKILL.md`, run the tool and confirm it. Untested instructions are worse than
  none — they fail silently inside an agent. (For example, `agy`'s `-p`
  rejecting stdin was documented only after testing it.)
- **Self-contained.** Each bundled skill is a full folder — `skills/<name>/SKILL.md`
  plus any `references/` — copied in, not symlinked, so it travels intact.
- **Don't vendor what has its own repo.** If a skill ships from its own
  repository, reference it (README + `npx skills add <owner>/<repo>`) instead of
  copying it here — one source of truth, no drift between two copies.

## The `*-exec` family

Skills named `<tool>-exec` (`claude-exec`, `codex-exec`, `antigravity-exec`) all
do the same thing: delegate a task to an external agent CLI as a non-interactive
sub-agent. Keep them structurally parallel so they stay predictable:

1. Prerequisites
2. How to run (non-interactive / print mode)
3. Flags table
4. Long-prompt handling
5. Notes (timeouts, permissions, context is not carried over, summarize back)

When a new agent CLI appears, add it as `<tool>-exec` following this same shape.

## Conventions

- **Layout:** one folder per skill under `skills/`, each with a `SKILL.md` whose
  frontmatter `name` matches the folder name.
- **English only.** All skill content — frontmatter, body, and trigger phrases —
  is written in English, because this repo is public. *Exception:* a skill whose
  subject is a specific natural language (e.g. `readable-japanese`, about Japanese
  prose) may be written in that target language, since its examples and trigger
  phrases only work there.
- **README:** keep both tables in sync — the bundled-skills table (each name
  links to its `SKILL.md`) and the "Skills in their own repositories" table
  (repo link + one-line summary + `npx skills add` command).
