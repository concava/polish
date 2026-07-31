# Polish

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.3.1-blue.svg)](CHANGELOG.md)
[![Contributor Covenant](https://img.shields.io/badge/Contributor%20Covenant-2.1-4baaaa.svg)](CODE_OF_CONDUCT.md)

A coding-agent plugin (Claude Code, Codex, Cursor, Gemini CLI, Kimi Code) that audits a design system, UI, or app screen against proven UI/UX principles — and hands back a specific, prioritized list of fixes instead of vague praise.

## Why it exists

Ask an LLM to review a UI and you usually get generic encouragement — "looks clean, maybe tighten the spacing." That's not useful feedback, and it's especially unhelpful for AI/vibe-coded apps, which tend to fail in the *same* predictable ways: emojis standing in for icons, clashing default-bright color palettes, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages. Those failures are easy to spot and cheap to fix — but only if something is actually checking for them instead of eyeballing the result.

`Polish` exists to replace that vibe-based pass with a fixed, repeatable rubric: 14 categories of established UI/UX principle, walked in order, every time, with a severity, an effort estimate, and a concrete fix attached to each finding. The goal is a report a designer or developer can act on directly, not one more paragraph of praise.

## What it does

`Polish` ships one skill, **design-system-audit**, which your agent runs whenever you ask it to review, critique, clean up, professionalize, or "make better" a design system, component library, set of screens, Figma file, or AI/vibe-coded UI — even if you never say the words "design system" or "audit."

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

A structured markdown report: a summary, findings per category with severity (High/Medium/Low) and effort (Quick/Involved), the principle violated and the concrete fix for each, a "quick wins" list, and recommended next steps. Your agent then offers to implement the fixes if you want revised tokens, component specs, or code.

## Install

Installation differs by harness. If you use more than one, install `Polish` separately for each.

### Claude Code

```bash
# From this GitHub repo, as a marketplace
claude plugin marketplace add concava/polish
claude plugin install polish@polish

# Or from a local clone, as a marketplace
claude plugin marketplace add /path/to/polish
claude plugin install polish@polish
```

### Codex

```text
/plugin marketplace add concava/polish
/plugin install polish@polish
```

This registers the repo-scoped marketplace at `.agents/plugins/marketplace.json` and installs the plugin manifest at `.codex-plugin/plugin.json`.

### Cursor

```bash
cursor-agent plugin marketplace add https://github.com/concava/polish
```

Then in a `cursor-agent` session, run `/plugin`, open the Marketplace tab, select `Polish`, and press Enter to install (Cursor doesn't yet have a non-interactive install command for a specific plugin).

### Gemini CLI

```bash
gemini extensions install https://github.com/concava/polish
```

### Kimi Code

```text
/plugins install https://github.com/concava/polish
```

## Use

Ask your agent:

> Review my UI
> What's wrong with this design?
> Clean up this dashboard
> Audit our design system
> Fix my vibe-coded app

Any of these trigger the `design-system-audit` skill.

## Structure

```
Polish/
├── .claude-plugin/
│   ├── plugin.json
│   └── marketplace.json       # lets this repo be added directly via `claude plugin marketplace add`
├── .codex-plugin/
│   └── plugin.json            # Codex plugin manifest
├── .agents/plugins/
│   └── marketplace.json       # repo-scoped Codex marketplace, lets this repo be added via `/plugin marketplace add`
├── .cursor-plugin/
│   └── plugin.json            # Cursor plugin manifest
├── .kimi-plugin/
│   └── plugin.json            # Kimi Code plugin manifest
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── skills/
│   └── design-system-audit/
│       ├── SKILL.md               # the audit process, report template, severity/effort guidance
│       └── references/
│           └── checklist.md       # detailed criteria, failures, and fixes for all 14 categories
├── CLAUDE.md               # repo conventions for anyone (human or agent) editing this repo
├── GEMINI.md               # imports SKILL.md into Gemini CLI's context (see gemini-extension.json)
├── gemini-extension.json   # Gemini CLI extension manifest
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
└── README.md
```

Every harness manifest (`plugin.json` under `.claude-plugin/`, `.codex-plugin/`, `.cursor-plugin/`, `.kimi-plugin/`, plus `gemini-extension.json` and the marketplace manifests) points at the same `skills/` directory — there's one skill, described once, wired into five harnesses.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for project structure and how to propose a new criterion or category. This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

MIT
