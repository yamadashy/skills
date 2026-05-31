---
name: claude-review-loop
description: Iterative Claude review-and-fix loop
---

Repeat the following cycle on the current branch's changes against `main` (max 3 iterations):

1. **Review** — Spawn a read-only Claude Code reviewer sub-agent over the diff (see the `claude-exec` skill for flag details):
   ```bash
   claude -p --no-session-persistence --permission-mode default \
     --disallowedTools Bash,Edit,Write \
     -- "Review the current branch's diff against main (git diff main...HEAD). Report only real defects — bugs, security issues, broken logic, missing edge cases. For each finding give file:line, severity, and a one-line fix. Skip style nitpicks and scope creep."
   ```
2. **Triage** — Review agent findings and keep only what you also deem noteworthy. Classify each as **Fix** (clear defects, must fix) or **Skip** (style, nitpicks, scope creep). Show a brief table before changing anything.
3. **Fix** only the "Fix" items. Keep changes minimal.
4. **Verify** with `npm run lint` and `npm run test`. Fix any regressions and repeat this step until all checks pass before continuing.
5. **Re-review** only the newly changed lines. Do not re-raise skipped items.

Stop when no "Fix" items remain or 3 iterations are reached. Print a summary of what was fixed and what was skipped.
