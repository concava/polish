# Repo conventions for polish

This file is for anyone (human or agent) editing this repo — it is not the
skill itself. The skill your agent runs when auditing a design lives at
[skills/design-system-audit/SKILL.md](skills/design-system-audit/SKILL.md).

## What this repo is

A single-skill, zero-dependency plugin, published for five agent harnesses
(Claude Code, Codex, Cursor, Gemini CLI, Kimi Code) from one shared
`skills/` directory. There is no application code, no build step, and no
test suite — the audit logic is two markdown files (`SKILL.md` and
`references/checklist.md`); everything else is per-harness manifest
plumbing that points at them.

## Keep these in sync

- `skills/design-system-audit/SKILL.md` ("The 14 categories" list) and
  `skills/design-system-audit/references/checklist.md` (the numbered
  sections) must list the exact same categories, in the same order.
- `README.md`'s category list mirrors both of the above.
- The category count is stated in three places in prose (`SKILL.md`,
  `README.md` ×2) — grep for the number before changing category count.
- `name`, `version`, and `description` must match across all five
  manifests: `.claude-plugin/plugin.json`, `.claude-plugin/marketplace.json`,
  `.codex-plugin/plugin.json`, `.cursor-plugin/plugin.json`,
  `.kimi-plugin/plugin.json`, and `gemini-extension.json`. Grep for the
  current version string before bumping — one miss leaves a harness on a
  stale description.
- Each manifest's `description` should stay a shorter paraphrase of the
  README's "Why it exists" / "What it does" sections, not drift into a
  different framing per harness.
- `GEMINI.md` must keep importing `skills/design-system-audit/SKILL.md` via
  the `@./path` syntax — it's how Gemini CLI (which has no native "skills"
  concept) gets the audit process into context, since `gemini-extension.json`
  points `contextFileName` at it.

## Versioning

Bump the `version` field in **all five manifests** (see above) for any
change to `SKILL.md` or `checklist.md` that changes what the audit checks
for or how it reports — new/removed category, changed report structure,
changed severity or effort semantics. Add a matching entry to
`CHANGELOG.md`. Typo fixes and prose clarifications that don't change
behavior don't need a bump.

## Style

Checklist entries follow a fixed shape: what "good" looks like, the specific
failure to watch for, and the fix — stated concretely enough that a
developer could act on it without asking a follow-up question. Mark
AI-generated-UI-specific failures with `⚠️ AI tell`. Avoid restating generic
design-textbook advice that isn't tied to a concrete, checkable symptom.
