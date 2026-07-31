# Design System Audit — Detailed Checklist

The criteria, common failures, and fixes for all 13 categories. Audit the design against every item. Each category lists what good looks like, the failures to watch for (AI-generated UI failures flagged with ⚠️ AI tell), and the fix.

## 1. Iconography

**Good:** A single consistent interface icon set. Icons sized to match the text they sit beside. Icons that carry meaning or add a deliberate splash of color.

- ⚠️ AI tell: **Emojis used as icons.** Replace with a proper interface icon set (Phosphor, Lucide, or similar). Emojis can work in rare cases (e.g. Notion), but as a default they read as amateur.
- **Icons too large.** Most icons are oversized. Set icon size to the font's line-height (commonly ~24px), then tighten the adjacent text so the pair feels intentional.
- **Mixed icon sets / inconsistent weights.** Pick one library and one stroke weight; don't mix outline and filled arbitrarily.
- **Decorative icon spam.** Don't add icons that carry no meaning. Where an icon-and-button row exists purely for decoration, consider replacing it with information (e.g. a micro chart) that adds real value and color.

## 2. Color system

**Good:** Start from one primary (usually the brand) color. Lighten it for backgrounds, darken it for text — subtle ways to make a drab design interesting. Build out a full color ramp, which is what mature companies use for chips, states, charts, and everything else. Use semantic colors deliberately.

- ⚠️ AI tell: **AI-chosen clashing brights.** AI defaults to saturated colors that don't work together. Never let the model pick the palette. Often a single swap (e.g. dark blue → dark green backgrounds) transforms the feel.
- **No semantic system.** Colors should have meaning: **blue = trust, red = danger/urgency, yellow = warning, green = success.** Use color for purpose, not decoration. Apply it where it earns attention — an announcement bar, an input focus state, a "new" chip.
- **Missing ramp.** Without a ramp you can't build consistent chips/states/charts. Generate tints and shades from the primary so every component pulls from the same scale.
- **Buttons/icons where charts belong.** Conveying data through charts (and their color) communicates more than rows of buttons and icons.

## 3. Typography

**Good:** One typeface, well-tuned. Design is mostly text, so typography does most of the work.

- **More than one font family.** You almost never need more than one. Pick a clean sans-serif and commit. This is not where to spend time.
- **Loose large headers.** Big text often feels too airy. Tighten letter-spacing to about **-2% to -3%** and drop line-height to about **110–120%** — this instantly makes large text look professional.
- **Too many sizes.** Landing pages/websites: no more than ~6 font sizes (a wide range is fine). **Dashboards: a much tighter range — rarely larger than 24px**, because information density is higher.
- **No type hierarchy.** Sizes should vary deliberately to support visual hierarchy, not randomly.

## 4. Visual hierarchy

**Good:** Use size, position, and color to rank importance. The most important thing is large, bold, and near the top; secondary info is smaller and below. Hierarchy is created by *contrast* — big vs. small, colorful vs. muted.

- **Spreadsheet look.** If a card lists everything in one flat, uniform format, it reads like data, not design. Introduce contrast.
- **Lead element buried.** The primary item (e.g. a title) must be large/bold/top so it doesn't blend with metadata like time and date.
- **Key value not emphasized.** A value like price should be set apart — e.g. top, right-aligned, and in the primary color — because being *different* draws the eye.
- **Telling instead of showing relationships.** Use an image for scannability and color; use icons and a connecting line to show movement/relationship (A → B) instead of spelling it out.
- Note: hierarchy isn't an exact science — multiple valid layouts exist. The rule is consistent: important things near the top, bigger/colorful = more important, images wherever possible.

## 5. Layout, grid & spacing

**Good:** Grids and the "8px apart / 12-column" conventions are *guidelines*, not laws. Whitespace matters more than rigid grids — let things breathe. Use a consistent spacing system and group elements that belong together.

- **Grid dogma.** Custom landing pages often don't align to columns, and that's fine. Grids earn their keep on structured, repeating content (galleries, blogs) and for responsive behavior (e.g. 12 / 8 columns tablet / 4 columns mobile).
- **Cramped layout.** Add breathing room — e.g. ~32px between items in a simple section. Whitespace is the cheapest professionalism upgrade.
- **No grouping.** Group related elements (announcement + heading, heading + subtext) so proximity reinforces hierarchy.
- **Off-system spacing.** Use a 4-point system: every value a multiple, so things can always be split in half, creating consistency throughout.
- ⚠️ AI tell: **Duplicated modules.** AI repeats the same block (e.g. the same four KPIs appearing two or three times across a small app). Remove duplicates; each piece of information should have one home.

## 6. Affordances & signifiers

**Good:** The UI signals how it works without written instructions. A container around items shows they're related; a container around one shows it's selected and toggleable; graying out shows inactive. Users *just know*.

- **Missing signifiers.** Add button press states, highlights on active nav items, hover states, and tooltips — these tell the user what an element affords.
- **Ambiguous state.** If something is selectable, inactive, or grouped, the visual treatment must say so. If you had to write instructions, the UI is under-signifying.

## 7. Feedback & states

**Good:** Every user action gets a response. This is non-negotiable.

- **Incomplete button states.** Every button needs at least four: **default, hover, active/pressed, disabled** — plus a **loading** state (with spinner) where relevant.
- **Incomplete input states.** Inputs are even more critical: **focus** state on click-in, **error** state (red border + message), and sometimes a **warning** state for optional issues.
- **Silent operations.** Loading spinners while data fetches, success messages when an action completes, animations on scroll/swipe. No action should happen silently.

## 8. Buttons & components

**Good:** Components follow predictable anatomy and proportions.

- **Sidebar links done wrong.** Sidebar links are just **ghost buttons** — no background until hover. Isolate and center one and you have a standalone button.
- **Bad button padding.** A good rule for standalone buttons: **width padding ≈ double the height padding.** Works with or without icons.
- **Primary/secondary pairing.** Primary + secondary CTAs commonly sit side by side; treat them as a pair with clear emphasis difference.
- **Busy cards.** Declutter: collapse action buttons into a **triple-dot menu**, center the date, collapse chips to **icons only**, move the key value (e.g. clicks) to the right.
- ⚠️ AI tell: **Sparse flyout with lots of empty space.** If a create/edit flyout has few fields but plenty of room, a **modal** fits better. Collapse advanced options by default, modernize the styling, and add the obvious missing options. AI is poor at complex layouts and cards — this is where the least effort yields the largest visual change.

## 9. Micro-interactions

**Good:** A heightened form of feedback that *confirms* an action and adds polish. They range from highly practical to playful.

- **Action not confirmed.** Example: a copy button with hover/click states still doesn't tell you anything was copied. A small chip that slides up ("Copied") closes the loop.
- **No delight anywhere.** Some playful motion (within reason) signals craft. Don't overdo it — micro-interactions confirm, they don't distract.

## 10. Depth: shadows & dark mode

**Shadows (light mode):**
- **Too strong.** Most shadows are too heavy. **Lower the opacity and increase the blur.** Strength depends on context: cards need very little; content floating above other content (popovers, dropdowns) needs more.
- **Misused depth.** Use inner + outer shadows for tactile effects (e.g. a raised button). Rule of thumb: **if the shadow is the first thing you notice, it's wrong.**

**Dark mode:**
- **Light borders too harsh.** High-contrast light borders create too much contrast; reduce them.
- **No depth.** Dark mode has no real shadows, so create depth by making cards **lighter than the background**, not by adding shadows.
- **Chips too bright.** Dim saturation and brightness on bright chips; flip values for the text to keep hierarchy.
- **Navy/gray monotony.** Dark mode allows deep purples, reds, and greens — not just navy blue or gray.

## 11. Overlays & images

**Good:** Overlays must not ruin the underlying image or its text.

- **Flat full-screen overlay.** A solid overlay often doesn't do the image justice. Use a **linear gradient** that reveals the image at top and fades into a text-readable background.
- **Want extra polish?** Add a **progressive blur** on top of the gradient for a more modern look.

## 12. Page-level patterns

**Sidebar:**
- Don't surface metrics that don't matter in context (e.g. click/link counts on a settings page) — that belongs on the dashboard/analytics tab. Align left, tighten spacing.
- ⚠️ AI tell: **gradient profile circle with initials.** Replace with a proper **account card**. Tuck secondary links into a **popover** on click; collapse settings/billing/usage together.

**Pricing pages:**
- **Too many plans.** Five plans is too many; consolidate (drop the weakest tier). Aim for a clean set.
- **Wrong emphasis.** Shrink the plan **name** (nobody cares) and enlarge the **cost per month** (people do). Rename a top tier to **Enterprise** when its limits imply bigger needs.
- **Hidden value.** Show the **actual discount** the user is getting, and show **what the next tier adds** over the current one. This pattern is standard (e.g. Resend, Supabase).
- Add a billing email and payment method. A tabbed layout scales — add Documents / Integrations / AI as new tabs later.

**Analytics:**
- Don't repeat KPI blocks already shown elsewhere. Capture **low-hanging fruit**: a toggle to split into individual links so users can **compare** items; info-rich rows with helpful icons (which also add color).
- Replace a plain bar chart with a **map of shaded regions** plus the data alongside it for a richer experience.

**Dead UI:**
- ⚠️ AI tell: **cards/components that do nothing.** Remove no-op elements — a very common AI pattern.

## 13. Landing pages

**Good:** This is where most customers are lost if it's vibe-coded. SaaS landing pages have a quality bar that builds trust, even subconsciously. Presentation drives conversion.

- **Generic icons as hero graphics.** ⚠️ AI tell. Replace with real **graphics** and lightly edited **screenshots of your actual product** (e.g. the analytics view, a password-protection screen).
- **Flat presentation.** Even simple touches — product/link cards with a slight **skew** — elevate the page.
- **Over-engineering.** Landing pages aren't about complexity; they're about presentation. Better presentation → better conversion.

## 14. Accessibility

**Good:** The design works for people who aren't using a mouse, aren't seeing full color, or aren't seeing the screen at all. This isn't a separate audience — it's the baseline. Accessibility failures are also usability failures for everyone else (low contrast is hard to read in sunlight; missing focus states break keyboard *and* power-user workflows).

- **Insufficient color contrast.** Body text needs at least **4.5:1** contrast against its background (**3:1** for large/bold text ≥18px); interactive elements and icons that carry meaning need **3:1**. Check this wherever a light-tinted brand color sits on white, or light text sits on a mid-tone image/overlay.
- ⚠️ AI tell: **Missing or invisible focus indicators.** AI-generated CSS frequently strips `outline` for aesthetics without adding a replacement. Every focusable element (link, button, input, custom control) needs a visible focus state distinct from hover — a ring or offset outline, not `outline: none` alone.
- **Color as the only signal.** If red/green (or any single hue) is the only way to distinguish states — error vs. success, selected vs. not — add a second cue: an icon, a label, a pattern. Roughly 1 in 12 men have some form of color vision deficiency.
- **Touch targets too small.** Tappable elements should be **at least 44×44px** (iOS) / **48×48px** (Android/Material), including padding — not just the visible icon or glyph. Icon-only buttons in dense toolbars are the most common offender.
- **Missing semantics.** Buttons built from `<div>`/`<span>` with a click handler, images without `alt` text, form inputs without associated `<label>` elements, icon-only buttons without an accessible name. If reviewing code, grep for these directly rather than inferring from a screenshot.
- **No keyboard path.** Anything reachable by mouse (dropdown menus, modals, custom selects, drag-to-reorder) needs an equivalent keyboard interaction and a visible, logical tab order. Modals need focus trapped inside them and returned to the trigger on close.
- **Motion with no escape hatch.** Autoplaying carousels, parallax, or elaborate micro-interactions should respect `prefers-reduced-motion` — reduce or disable non-essential motion for users who request it.
- **Note on verifiability:** several of these (focus order, keyboard traps, `prefers-reduced-motion`) can't be confirmed from a static screenshot. When auditing an image rather than code, say so explicitly ("could not verify keyboard behavior from a screenshot") rather than silently passing the category.
