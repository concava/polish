---
name: design-system-audit
description: Audit and revise an entire design system, UI, or app screen against a consolidated set of UI/UX best practices (iconography, color, typography, hierarchy, spacing, states, shadows, dark mode, overlays, page patterns, landing pages, and accessibility). Use this whenever the user wants to review, critique, clean up, professionalize, or "make better" a design system, a component library, a set of screens, a Figma file, or AI/vibe-coded UI — even if they don't say the words "design system" or "audit." Also trigger for accessibility/a11y-focused reviews. Trigger on phrases like "review my UI," "make this look professional," "what's wrong with this design," "clean up this dashboard," "redesign this," "is this accessible," or "fix my vibe-coded app." Produces a structured findings report with severity, effort, the specific principle violated, and a concrete fix for each issue.
---

# Design System Audit

Systematically review a design system, UI, or screen against proven UI/UX principles and return concrete, prioritized fixes. The goal is not vague praise or generic advice — it is a specific, actionable list a designer or developer can work through.

## When this applies

Use this skill whenever someone hands you a design to evaluate or improve: a full design system, a component library, a few screens, a Figma export, a screenshot, or live/AI-generated UI they want professionalized. It works equally well on a single button and a whole product.

## How to run an audit

1. **Establish scope.** Identify what you're reviewing (full system, single screen, specific component) and the surface (web app, dashboard, mobile, landing page). Dashboards and landing pages have different rules — note which apply.

2. **Gather evidence appropriately for the source.** How you inspect depends on what you were handed:
   - **A codebase.** Don't just eyeball rendered output — read the actual source. Grep for hardcoded hex/rgb values outside a token file (color-system violations), count distinct `font-family` declarations (typography violations), scan for `<div onClick>` patterns, missing `alt`/`aria-label`, inputs without associated `<label>` elements, and `outline: none` without a replacement focus style (accessibility violations). Check the Tailwind/CSS-variable config for the actual spacing and color scale in use versus what components actually reference.
   - **A screenshot, Figma export, or live URL.** Inspect it concretely for everything visible. But some criteria genuinely can't be verified from a static image — hover/focus/loading states, keyboard tab order, `prefers-reduced-motion` handling. Say so explicitly in the finding ("not verifiable from a static screenshot") instead of silently passing the category or guessing.
   - If the user described the design in words with no file or image, work from that, and ask for a screenshot or the relevant files only if a visual or code-level check is essential to a claim you'd otherwise be guessing at.

3. **Walk every category in order.** Read `references/checklist.md` and go through all 14 categories below. For each, check the design against the criteria, and note where it passes, where it fails, and the specific fix. Don't skip categories — a category with no issues is itself a useful finding ("Typography: no issues").

4. **Flag AI/vibe-coded tells specifically.** AI-generated UI fails in predictable ways (emojis as icons, clashing bright colors, duplicated modules, dead no-op cards, sparse flyouts, generic icon-only landing pages, missing focus indicators). Call these out explicitly when present — they're high-value, low-effort fixes.

5. **Write the report** using the structure below. Lead with the highest-impact issues. Be specific: cite the principle, the location, and the fix — not "improve hierarchy" but "the price blends into the row; move it top-right and color it with the primary blue so it reads first."

6. **Offer to apply fixes.** After the report, offer to implement changes (e.g., rewrite tokens, produce revised component specs, or build a corrected version) if the user has the relevant files or wants code.

## The 14 categories

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
14. **Accessibility** — color contrast ratios, visible focus indicators, color-independent state signaling, touch target size, semantic markup/ARIA, keyboard reachability, `prefers-reduced-motion`.

## Report structure

ALWAYS use this template:

```
# Design System Audit — [scope]

## Summary
[2-4 sentences: overall state, the biggest themes, what to fix first.]

## Findings by category
For each of the 14 categories that has issues:

### [Category name]
- **[Severity: High / Medium / Low]** **[Effort: Quick / Involved]** — [What's wrong] → [The fix]. (Principle: [which one])
[Repeat per issue. If a category is clean, state: "No issues." If a criterion couldn't be checked from the given material, state that explicitly rather than skipping it.]

## Quick wins
[Every finding tagged Effort: Quick, regardless of severity — e.g. swap emojis for icons, fix clashing colors, remove duplicated KPIs, add a focus ring.]

## Recommended next steps
[Suggest implementation order — typically High severity first, then remaining Quick-effort items, then the rest — or offer to produce revised tokens/specs/code.]
```

## Severity guidance

- **High** — breaks usability, trust, or accessibility (clashing colors, missing input error states, illegible overlay text, no feedback on actions, insufficient contrast, no visible focus state, no keyboard path to a control).
- **Medium** — clearly unprofessional but functional (emojis as icons, loose header tracking, duplicated modules, overly strong shadows).
- **Low** — polish (a missing micro-interaction, slightly off spacing, an extra pricing plan).

## Effort guidance

Tag each finding's effort independently of its severity — a High-severity issue can still be a five-minute fix (e.g. add a focus ring), and a Low-severity one can require real rework (e.g. consolidating five pricing tiers into three).

- **Quick** — a token change, a single CSS property, a copy/paste fix, removing an element. No new component or layout decision needed.
- **Involved** — requires a new component, a layout restructure, new content (real screenshots, copy), or a decision the user needs to weigh in on.

## Tone

Be direct and concrete, the way a senior designer reviews a junior's work — specific about what's wrong and exactly how to fix it, without hedging or filler. Explain *why* each principle matters so the user learns the reasoning, not just the rule.
