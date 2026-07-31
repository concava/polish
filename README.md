# design-audit

A Claude Code plugin that audits a design system, UI, or app screen against proven UI/UX principles — and hands back a specific, prioritized list of fixes instead of vague praise.

## Why it exists

Ask an LLM to review a UI and you usually get generic encouragement — "looks clean, maybe tighten the spacing." That's not useful feedback, and it's especially unhelpful for AI/vibe-coded apps, which tend to fail in the *same* predictable ways: emojis standing in for icons, clashing default-bright color palettes, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages. Those failures are easy to spot and cheap to fix — but only if something is actually checking for them instead of eyeballing the result.

`design-audit` exists to replace that vibe-based pass with a fixed, repeatable rubric: 13 categories of established UI/UX principle, walked in order, every time, with a severity and a concrete fix attached to each finding. The goal is a report a designer or developer can act on directly, not one more paragraph of praise.

## What it does

`design-audit` ships one skill, **design-system-audit**, which Claude runs whenever you ask it to review, critique, clean up, professionalize, or "make better" a design system, component library, set of screens, Figma file, or AI/vibe-coded UI — even if you never say the words "design system" or "audit."

It walks the design against 13 categories of UI/UX best practice:

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

It specifically flags AI/vibe-coded tells — emojis as icons, clashing default-bright palettes, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages — since these are high-value, low-effort fixes.

## Output

A structured markdown report: a summary, findings per category with severity (High/Medium/Low), the principle violated and the concrete fix for each, a "quick wins" list, and recommended next steps. Claude then offers to implement the fixes if you want revised tokens, component specs, or code.

## Install

```bash
# From this repo, as a local plugin
claude plugin add design-audit --path /path/to/design-audit

# Or once published to a marketplace
claude plugin add design-audit
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
│   └── plugin.json
├── skills/
│   └── design-system-audit/
│       ├── SKILL.md               # the audit process, report template, severity guidance
│       └── references/
│           └── checklist.md       # detailed criteria, failures, and fixes for all 13 categories
└── README.md
```

## License

MIT
