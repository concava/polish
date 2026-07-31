# design-audit

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.2.0-blue.svg)](CHANGELOG.md)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT.md)

A Claude Code plugin that audits a design system, UI, or app screen against proven UI/UX principles — and hands back a specific, prioritized list of fixes instead of vague praise.

## Why it exists

Ask an LLM to review a UI and you usually get generic encouragement — "looks clean, maybe tighten the spacing." That's not useful feedback, and it's especially unhelpful for AI/vibe-coded apps, which tend to fail in the *same* predictable ways: emojis standing in for icons, clashing default-bright color palettes, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages. Those failures are easy to spot and cheap to fix — but only if something is actually checking for them instead of eyeballing the result.

`design-audit` exists to replace that vibe-based pass with a fixed, repeatable rubric: 14 categories of established UI/UX principle, walked in order, every time, with a severity, an effort estimate, and a concrete fix attached to each finding. The goal is a report a designer or developer can act on directly, not one more paragraph of praise.

## What it does

`design-audit` ships one skill, **design-system-audit**, which Claude runs whenever you ask it to review, critique, clean up, professionalize, or "make better" a design system, component library, set of screens, Figma file, or AI/vibe-coded UI — even if you never say the words "design system" or "audit."

It walks the design against 14 categories of UI/UX best practice:

1. Iconography
2. Color system
3. Typography
4. Visual hierarchy
5. Layout, grid & spacing
6. Affordances & signifiers
7. Feedback & states
8. Buttons & components
9. Micro-interactions
10. Depth: shadows & dark mode
11. Overlays & images
12. Page-level patterns
13. Landing pages
14. Accessibility

It specifically flags AI/vibe-coded tells — emojis as icons, clashing default-bright palettes, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages, missing focus indicators — since these are high-value, low-effort fixes. When run against a codebase rather than a screenshot, it reads the actual source (tokens, CSS, markup) instead of only judging rendered output.

## Output

A structured markdown report: a summary, findings per category with severity (High/Medium/Low) and effort (Quick/Involved), the principle violated and the concrete fix for each, a "quick wins" list, and recommended next steps. Claude then offers to implement the fixes if you want revised tokens, component specs, or code.

## Install

```bash
# From this GitHub repo, as a marketplace
claude plugin marketplace add concava/design-audit
claude plugin install design-audit@design-audit

# Or from a local clone, as a marketplace
claude plugin marketplace add /path/to/design-audit
claude plugin install design-audit@design-audit
```

## Use

Ask Claude Code (or Claude with this plugin loaded):

> Review my UI
> What's wrong with this design?
> Clean up this dashboard
> Audit our design system
> Fix my vibe-coded app

Any of these trigger the `design-system-audit` skill.

## Structure

```
design-audit/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json       # lets this repo be added directly via `claude plugin marketplace add`
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── skills/
│   └── design-system-audit/
│       ├── SKILL.md               # the audit process, report template, severity/effort guidance
│       └── references/
│           └── checklist.md       # detailed criteria, failures, and fixes for all 14 categories
├── CLAUDE.md               # repo conventions for anyone (human or agent) editing this repo
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
└── README.md
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for project structure and how to propose a new criterion or category. This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

MIT
