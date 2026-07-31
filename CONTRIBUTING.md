# Contributing to polish

`polish` is a multi-harness agent plugin (Claude Code, Codex, Cursor, Gemini
CLI, Kimi Code), not a code library — its entire behavior lives in the two
markdown files under `skills/design-system-audit/`. Contributing means
editing prose and criteria, not shipping code.

## Project structure

```
.claude-plugin/plugin.json       # Claude Code plugin manifest
.claude-plugin/marketplace.json  # lets this repo be added via `claude plugin marketplace add`
.codex-plugin/plugin.json        # Codex plugin manifest
.cursor-plugin/plugin.json       # Cursor plugin manifest
.kimi-plugin/plugin.json         # Kimi Code plugin manifest
gemini-extension.json            # Gemini CLI extension manifest
GEMINI.md                        # imports SKILL.md into Gemini's context
skills/design-system-audit/
  SKILL.md                       # the audit process, report template, severity/effort guidance
  references/checklist.md        # the 14 categories: criteria, failures, fixes
```

All five manifests point at the same `skills/` directory — there is one
skill, described once. If you change `name`, `version`, or `description`,
update it in all five (see [CLAUDE.md](CLAUDE.md)'s "Keep these in sync"
section).

`SKILL.md` and `checklist.md` must stay in sync: every category listed in
`SKILL.md`'s "The 14 categories" section must have a matching, numbered
section in `checklist.md`, and vice versa. If you add, remove, or reorder a
category, update both files and the category list in `README.md`.

## What belongs here

- Corrections or additions to the UI/UX criteria in `checklist.md` —
  especially ones grounded in a specific design failure you actually hit,
  not a generic principle restated from a textbook.
- New AI/vibe-coded tells (⚠️ AI tell) — patterns you've seen repeatedly in
  AI-generated UI that aren't already covered.
- Clarity fixes to `SKILL.md`'s process, report template, or severity/effort
  guidance.

## What doesn't belong here

- Framework-specific or tool-specific advice (e.g. "how to fix this in
  Tailwind" vs. a general CSS principle) — keep criteria tool-agnostic.
- Personal taste that isn't backed by a recognized UI/UX principle. Every
  checklist item should cite *why* it matters, not just assert a preference.

## Proposing a change

1. Open an issue first for anything beyond a typo fix — describe the
   specific case that motivated it (a screenshot or example is ideal).
2. Keep PRs scoped to one category or concern at a time.
3. Since there's no test suite, "validation" means running the updated
   skill against a real screen or codebase and checking the finding reads
   as specific and actionable — not vague or generic.
4. Update `README.md` and `CHANGELOG.md` if the change is user-visible
   (new category, changed report structure, etc.).

## Reporting issues

Use the issue templates under `.github/ISSUE_TEMPLATE/`. A concrete example
of a design the audit got wrong (missed an issue, flagged a non-issue, or
gave vague/non-actionable advice) is the most useful thing you can include.
