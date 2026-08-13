---
name: handcraft-html
description: >
  Build HTML pages that look and read like a real person made them, not an AI. Tuned for technical
  documentation, API references, runbooks, code docs, internal wikis, and simple portfolios, with
  six named light/dark themes the user picks from. Use whenever the user asks for docs, a reference
  site, a runbook, a README as a page, a portfolio, a landing page, or any HTML/CSS front-end work,
  even if they don't say "make it not look AI generated". Also trigger on "build me a site",
  "document this API", "turn this into a docs page", or "this site looks too AI". Every page ships
  with light and dark mode and is mobile optimized by default.
---

# Handcraft HTML

Build pages that a stranger would assume came from a small studio or a careful engineer, not a prompt. Three things every time: a design that dodges the current AI visual cliches, copy that sounds like one person wrote it, and a technical floor of light/dark theming plus mobile-first responsiveness.

The skill is tuned for documentation work (product docs, API references, runbooks, code docs, wikis) and also handles portfolios, landing pages, and personal sites.

Work through the steps in order. Never skip Step 1 or the self-check in Step 6.

---

## Step 1: Get the two choices

Two things must be settled before any design work: **page type** and **theme**. Both are the user's call.

If the user already stated one or both ("an API reference, Anthropic style"), take it and don't re-ask. If they supplied their own brand colors, that replaces the theme choice entirely.

Otherwise, ask for both in one turn. If an interactive option-picker tool is available, use it: one question for page type, one for theme, presented together so the user answers once. Otherwise ask in plain text with both lists.

**Page type** (from `references/page-types.md`):

1. Product documentation
2. API reference
3. Runbook / operations guide
4. Code documentation (library or repo)
5. Internal wiki / handbook
6. Portfolio
7. Landing page
8. Personal / resume site
9. Something else

**Theme** (from `references/themes.md`):

1. Anthropic, warm paper and terracotta, editorial and calm
2. Slate, cool grey and ink blue, neutral and institutional
3. Terminal, near-black and phosphor amber, monospace-forward
4. Forest, warm off-white and deep green, quiet and library-like
5. Plum, soft grey and deep aubergine, distinct without being loud
6. Mono, paper white and black with one red, Swiss and colorless

Suggest a default alongside the list based on the page type (Terminal for runbooks, Mono for portfolios, Anthropic or Slate for product docs and API references), so the user can accept in one word.

Then read the relevant section of `references/page-types.md`, plus `references/docs-style.md` if it's a documentation-family type, plus the chosen preset in `references/themes.md`.

Also pin down the subject: what it actually is, who reads it, and the one job the page has. If the user left that vague, make a concrete choice and say what you chose. Generic subject in, generic page out.

## Step 2: Never invent a palette when a preset fits

The six presets exist because freehand palettes drift. Left to improvise while avoiding the banned stock looks, models reliably land on the same two substitutes: a green cast or a navy cast. Avoiding one default that way just manufactures another.

So:

- **User's brand beats everything.** Provided colors, fonts, or a logo override every rule here, even if they match a stock AI look.
- **A named theme beats improvisation.** If a preset was chosen, use its values verbatim. Don't adjust them mid-build, don't blend two, don't "warm it up a little".
- **Custom palettes only on request.** When the user genuinely wants something outside the six, build it from the subject's real world (a foundry has rust, slag, firebrick), then state it in one line before writing code: "Palette: warm slate and rust, from the foundry setting." If your custom palette is green or navy, justify it from the subject in that same line or pick differently.

## Step 3: Design the rest

Read `references/ai-tells.md` before designing. It lists the visual patterns that read as machine-made. With the palette settled by Step 2, plan the remaining axes:

- **Type**: a characterful display face with restraint, a readable body face, optionally a utility face for labels or code. Never one font doing all three jobs. The chosen theme suggests a pairing; follow it.
- **Layout**: one sentence describing the concept. Documentation types have a prescribed skeleton in `docs-style.md`; follow it rather than inventing.
- **Signature**: one memorable element. One. Spend boldness there, keep everything else quiet.

Then critique the plan once: anything that's what you'd produce for any similar prompt is a default, not a decision.

## Step 4: Write copy like a person

Placeholder copy sinks the whole effort. A perfect layout full of "Unlock seamless solutions" still reads as AI.

- Real, specific words. Name the actual command, endpoint, price, place, or version.
- Vary sentence length. Short ones land. Longer ones can wander before making their point.
- Kill zombie words: seamless, elevate, unlock, empower, cutting-edge, robust, leverage, streamline, holistic, game-changer, "in today's world".
- No emoji in headings. Sentence case beats Title Case Everywhere.
- Buttons and links say what they do.
- **No em-dashes, ever.** Not in headings, body, captions, code comments, or alt text. The em-dash is a top AI writing tell. Use a comma, period, colon, or parentheses instead. En-dashes in ranges ("9 to 5", "2019–2024") are fine.
- **Always run a humanization pass** over every word before delivering. If a humanize-content skill exists in the environment, read and apply it. Otherwise apply this section plus the copy tells in `ai-tells.md` as a dedicated final pass.
- If the user gave you real content, use it verbatim (minus em-dashes) and shape the design around it.

## Step 5: Build with the required technical floor

Default to a single self-contained `.html` file (inline CSS and JS) unless asked otherwise. For multiple "pages", default to sections with anchor navigation in one file; use separate linked files when the user asks for real pages or the content outgrows one file.

### Light and dark mode, always

- Every color as a CSS custom property on `:root`, with a `[data-theme="dark"]` override block. No hardcoded colors in component rules, which is what makes theme swaps a two-block edit.
- Respect `prefers-color-scheme`, and include a visible toggle that overrides it.
- Persist with `localStorage` wrapped in try/catch. In Claude artifacts, browser storage is unavailable, so hold the choice in memory and skip persistence.
- The init script goes **inline in the head, before styles and content**, or dark-mode readers get a white flash on every load.

```js
(function () {
  var stored = null;
  try { stored = localStorage.getItem('theme'); } catch (e) {}
  var prefersDark = matchMedia('(prefers-color-scheme: dark)').matches;
  document.documentElement.dataset.theme = stored || (prefersDark ? 'dark' : 'light');
})();
```

### Mobile optimized, always

- `<meta name="viewport" content="width=device-width, initial-scale=1">`.
- Mobile-first CSS: base styles for small screens, widen with `min-width` queries.
- Fluid type via `clamp()`.
- Touch targets at least 44x44px with space between them.
- No horizontal scroll at 360px. Watch fixed widths, long unbroken strings, wide tables (wrap them in a scroll container), and images without `max-width: 100%`.
- Sidebars collapse to a slide-over; multi-column grids collapse to one column.
- Line length 45 to 75 characters at every width.

### Images that can't break

- Never hotlink external image URLs. They 404 and instantly sink the handmade impression.
- Prefer inline SVG and CSS compositions, which also theme correctly via the CSS variables.
- When a real photo is required, build a labeled placeholder sized correctly, give it real alt text, and tell the user what to drop in.
- Every `<img>`: `max-width: 100%`, explicit dimensions or aspect-ratio, meaningful alt.

### Forms that do something

- Prefer `mailto:` or `tel:` links, which need no backend.
- If a real form is wanted, build proper labels and validation, point at a placeholder action, and say plainly where a backend must be connected.
- Never fake a success message for a form that sent nothing.

### Quality floor

- Visible keyboard focus styles that suit the design.
- `prefers-reduced-motion` respected.
- Semantic HTML: real `<nav>`, `<main>`, `<footer>`, one `<h1>`, meaningful alt text.
- System font fallbacks after any webfont; prefer system stacks so pages make no external requests.

## Step 6: Self-check before delivering

Run the checklist at the end of `references/ai-tells.md` against your own output. If you can render or screenshot the page, view it in both themes and at 360px. Fix what you find, then deliver with a sentence or two on the direction taken, not an essay.

---

## Reference files

- `references/page-types.md`: structure, components, and traps per page type. Read the relevant section in Step 1.
- `references/themes.md`: the six presets with tested hex values for both modes. Read the chosen preset in Step 1.
- `references/docs-style.md`: layout and component playbook for all documentation-family types. Mandatory for types 1 through 5.
- `references/ai-tells.md`: patterns that read as machine-made, plus the final checklist. Read in Step 3 and again in Step 6.
