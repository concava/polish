# Changelog

All notable changes to this plugin are documented here. Versions follow
[Semantic Versioning](https://semver.org/).

## [0.3.1] - 2026-07-31

### Fixed
- Corrected the Codex and Cursor install instructions in `README.md` after
  verifying against official/community documentation: Codex needs its own
  repo-scoped marketplace manifest at `.agents/plugins/marketplace.json`
  (distinct from `.claude-plugin/marketplace.json`, which only Claude Code
  reads) for `/plugin marketplace add concava/polish` to work; Cursor
  installs via `cursor-agent plugin marketplace add <url>` followed by an
  interactive `/plugin` selection, since it has no non-interactive
  per-plugin install command yet.

### Added
- `.agents/plugins/marketplace.json`, the repo-scoped marketplace manifest
  Codex reads.

## [0.3.0] - 2026-07-31

### Added
- Plugin manifests for four additional agent harnesses, all pointing at
  the same `skills/design-system-audit/` directory: `.codex-plugin/plugin.json`,
  `.cursor-plugin/plugin.json`, `.kimi-plugin/plugin.json`, and
  `gemini-extension.json` (with `GEMINI.md` importing `SKILL.md` into
  Gemini CLI's context, since it has no native skills mechanism).
- Per-harness install instructions in `README.md`.

## [0.2.0] - 2026-07-31

### Added
- New 14th audit category: **Accessibility** — color contrast ratios,
  visible focus indicators, color-independent state signaling, touch
  target size, semantic markup/ARIA, keyboard reachability, and
  `prefers-reduced-motion`.
- Evidence-gathering guidance in the audit process that distinguishes
  auditing a codebase (grep tokens, markup, CSS) from auditing a
  screenshot (explicitly flag what can't be verified from a static image).
- An **Effort** tag (Quick/Involved) on every finding, alongside Severity,
  so quick wins can be derived directly from the report.
- `.claude-plugin/marketplace.json`, so the repo can be added directly as
  a plugin marketplace via `claude plugin marketplace add`.

### Changed
- Category count updated from 13 to 14 throughout `SKILL.md` and
  `README.md`.

## [0.1.0] - 2026-07-31

### Added
- Initial release: the `design-system-audit` skill, auditing a design
  system, UI, or screen against 13 categories of UI/UX best practice and
  returning a structured, severity-scored findings report.
