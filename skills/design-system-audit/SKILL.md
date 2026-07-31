---
name: design-system-audit
description: Audit and revise an entire design system, UI, or app screen against a consolidated set of UI/UX best practices (iconography, color, typography, hierarchy, spacing, states, shadows, dark mode, overlays, page patterns, and landing pages). Use this whenever the user wants to review, critique, clean up, professionalize, or "make better" a design system, a component library, a set of screens, a Figma file, or AI/vibe-coded UI — even if they don't say the words "design system" or "audit." Trigger on phrases like "review my UI," "make this look professional," "what's wrong with this design," "clean up this dashboard," "redesign this," or "fix my vibe-coded app." Produces a structured findings report with severity, the specific principle violated, and a concrete fix for each issue.
---

# Design System Audit

Systematically review a design system, UI, or screen against proven UI/UX principles and return concrete, prioritized fixes. The goal is not vague praise or generic advice — it is a specific, actionable list a designer or developer can work through.

## When this applies

Use this skill whenever someone hands you a design to evaluate or improve: a full design system, a component library, a few screens, a Figma export, a screenshot, or live/AI-generated UI they want professionalized. It works equally well on a single button and a whole product.

## How to run an audit

1. **Establish scope.** Identify what you're reviewing (full system, single screen, specific component) and the surface (web app, dashboard, mobile, landing page). Dashboards and landing pages have different rules — note which apply. If the user gave you a screenshot or file, inspect it concretely; if they described it in words, work from that and ask for an image only if a visual is essential.

2. **Walk every category in order.** Read `references/checklist.md` and go through all 13 categories below. For each, check the design against the criteria, and note where it passes, where it fails, and the specific fix. Don't skip categories — a category with no issues is itself a useful finding ("Typography: no issues").

3. **Flag AI/vibe-coded tells specifically.** AI-generated UI fails in predictable ways (emojis as icons, clashing bright colors, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages). Call these out explicitly when present — they're high-value, low-effort fixes.

4. **Write the report** using the structure below. Lead with the highest-impact issues. Be specific: cite the principle, the location, and the fix — not "improve hierarchy" but "the price blends into the row; move it top-right and color it with the primary blue so it reads first."

5. **Offer to apply fixes.** After the report, offer to implement changes (e.g., rewrite tokens, produce revised component specs, or build a corrected version) if the user has the relevant files or wants code.

## The 13 categories

These consolidate the full set of principles. Detailed criteria, common failures, and fixes for each live in `references/checklist.md` — read it before auditing.

1. **Iconography** — no emojis; one consistent interface icon set; icon size matched to text line-height; icons used for meaning, not filler.
2. **Color system** — single primary/brand color with tints and shades; a full ramp for states/chips/charts; semantic colors used with intent; no clashing AI-default brights; charts over decorative buttons/icons.
3. **Typography** — one sans-serif; a constrained type scale (≤6 sizes web, ≤24px dashboards); tightened large headers.
4. **Visual hierarchy** — size, position, and color contrast rank importance; most important content is large/top; relationships shown visually.
5. **Layout, grid & spacing** — grids as guidelines; generous whitespace; consistent spacing system; grouped related elements; no duplicated modules.
6. **Affordances & signifiers** — the UI signals how it works (selected, inactive, related, hoverable) without instructions.
7. **Feedback & states** — every action has a response; buttons and inputs have full state coverage.
8. **Buttons & components** — correct button anatomy and padding; declutter with menus/icons; modals vs. sparse flyouts.
9. **Micro-interactions** — small confirmations that close the feedback loop.
10. **Depth: shadows & dark mode** — restrained shadows; depth via elevation; dark mode handled properly (no shadows, lighter cards, dimmed chips).
11. **Overlays & images** — gradients/blur to keep imagery and text readable.
12. **Page-level patterns** — sidebar hygiene, pricing-page conventions, rich analytics, removal of dead UI.
13. **Landing pages** — graphics and real product imagery over generic icons; presentation drives conversion.

## Report structure

ALWAYS use this template:

```
# Design System Audit — [scope]

## Summary
[2-4 sentences: overall state, the biggest themes, what to fix first.]

## Findings by category
For each of the 13 categories that has issues:

### [Category name]
- **[Severity: High / Medium / Low]** — [What's wrong] → [The fix]. (Principle: [which one])
[Repeat per issue. If a category is clean, state: "No issues."]

## Quick wins
[Bulleted: the highest-impact, lowest-effort changes to do first — e.g. swap emojis for icons, fix clashing colors, remove duplicated KPIs.]

## Recommended next steps
[Suggest implementation order, or offer to produce revised tokens/specs/code.]
```

## Severity guidance

- **High** — breaks usability, trust, or accessibility (clashing colors, missing input error states, illegible overlay text, no feedback on actions).
- **Medium** — clearly unprofessional but functional (emojis as icons, loose header tracking, duplicated modules, overly strong shadows).
- **Low** — polish (a missing micro-interaction, slightly off spacing, an extra pricing plan).

## Tone

Be direct and concrete, the way a senior designer reviews a junior's work — specific about what's wrong and exactly how to fix it, without hedging or filler. Explain *why* each principle matters so the user learns the reasoning, not just the rule.
