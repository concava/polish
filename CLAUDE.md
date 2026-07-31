# Repo conventions for polish

This file is for anyone (human or agent) editing this repo — it is not the
skill itself. The skill Claude runs when auditing a design lives at
[skills/design-system-audit/SKILL.md](skills/design-system-audit/SKILL.md).

## What this repo is

A single-plugin, zero-dependency Claude Code plugin. There is no application
code, no build step, and no test suite — the entire product is two markdown
files (`SKILL.md` and `references/checklist.md`) plus the plugin/marketplace
manifests that make it installable.

## Keep these in sync

- `skills/design-system-audit/SKILL.md` ("The 14 categories" list) and
  `skills/design-system-audit/references/checklist.md` (the numbered
  sections) must list the exact same categories, in the same order.
- `README.md`'s category list mirrors both of the above.
- The category count is stated in three places in prose (`SKILL.md`,
  `README.md` ×2) — grep for the number before changing category count.
- `.claude-plugin/plugin.json`'s `description` should stay a shorter
  paraphrase of the README's "Why it exists" / "What it does" sections, not
  drift into a different framing.

## Versioning

Bump `.claude-plugin/plugin.json`'s `version` (semver) for any change to
`SKILL.md` or `checklist.md` that changes what the audit checks for or how
it reports — new/removed category, changed report structure, changed
severity or effort semantics. Add a matching entry to `CHANGELOG.md`. Typo
fixes and prose clarifications that don't change behavior don't need a bump.

## Style

Checklist entries follow a fixed shape: what "good" looks like, the specific
failure to watch for, and the fix — stated concretely enough that a
developer could act on it without asking a follow-up question. Mark
AI-generated-UI-specific failures with `⚠️ AI tell`. Avoid restating generic
design-textbook advice that isn't tied to a concrete, checkable symptom.
