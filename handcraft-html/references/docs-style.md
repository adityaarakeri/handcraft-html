# Polished technical docs

Read this whole file whenever the site type is documentation / knowledge site. Docs pages go bland when they're built as "an article with a sidebar". Modern reference-quality docs (the Anthropic / Stripe school) feel expensive because of crafted components and layout structure, not decoration. Restraint applies to ornament; it does not mean plain.

## Layout anatomy

Desktop is a three-zone layout:

- **Left sidebar** (~250 to 280px, sticky, independently scrollable): the full nav tree.
- **Main content column**: measure capped around 65 to 72 characters, generous vertical rhythm.
- **Right rail** (~200px, sticky): an "On this page" mini table of contents built from the page's h2/h3s.

A slim top bar runs above all three: product name or logo on the left, a search input (decorative is fine, style it with a keyboard hint chip like "Ctrl K"), and the theme toggle.

Responsive collapse, in order: tablet drops the right rail (fold the TOC into a collapsible "On this page" block above the content). Mobile collapses the sidebar behind a menu button into a slide-over panel. The content column always survives untouched.

## Sidebar details

- Links grouped under small, muted, all-caps group labels ("Getting started", "API reference").
- The active page gets an accent-tinted background and accent-colored text, not just bold.
- Hover states on everything. Collapsible groups get a rotating chevron.
- Breadcrumb or section label above the h1 in the content area so the reader always knows where they are.

## Components: this is where blandness dies

Build these as real, styled components with their own CSS. A docs page with zero of them will look like a default markdown render no matter how nice the fonts are.

**Callouts.** Note, Tip, and Warning boxes: tinted background or a 3px left accent border, a small inline SVG icon, a bold label. Each type gets its own hue (informational blue-ish, positive green-ish, cautionary amber-ish), tuned separately for both themes.

**Code blocks.** The centerpiece of any docs page, so overinvest here:
- A distinct panel surface. A dark code panel inside the light theme is a legitimate, professional look.
- A header strip on the block: language label on the left, a copy button on the right that gives "Copied" feedback on click.
- Real syntax highlighting: hand a small token palette (keyword, string, comment, function, number) to `<span>`s in the sample code. Comments muted, strings and keywords distinct. Both themes get their own token colors.
- Inline code as tinted monospace chips with a little horizontal padding and a subtle border.

**Card grids.** Overview and landing pages get link cards: title, one-line description, subtle 1px border, slight hover lift or border-color shift. Two columns desktop, one on mobile.

**Parameter and field lists.** For API-ish content: field name as a monospace chip, type in small muted text next to it, required/optional flag, then the description. This one component makes reference pages look serious.

**Tables.** Header row with a background tint, hairline row borders, comfortable cell padding, horizontal scroll wrapper on mobile.

**Prev / next pagination.** Two cards at the bottom of the content: muted "Previous"/"Next" label over the page title, arrows, hover state.

## Typography and color

- A characterful display face for the h1 and h2s (a good serif works well against technical content), a clean sans for body, and a genuinely good monospace for code, since code is half the page.
- Warm near-white background rather than pure white, near-black warm ink, one confident accent carrying links, active nav, and focus states. Accent discipline is what makes docs feel calm.
- Muted color does a lot of work: ledes, group labels, metadata, TOC links all step back so content steps forward.

**Color comes from the chosen theme, not from improvisation.** All palette values live in `themes.md`; use the selected preset verbatim. What matters at the docs level is how color is *deployed*: one confident accent carrying links, active nav, and focus states, with muted tones stepping back for ledes, group labels, metadata, and TOC links so the content steps forward. Accent discipline is what makes docs feel calm.

A note on the Anthropic preset specifically: its warm cream and terracotta combination is the same one `ai-tells.md` flags as a stock AI look, flagged precisely because everyone copies it. When the user picks it by name, that is a deliberate choice and it wins. The flag only governs improvised palettes.

## Dark mode for docs

Docs readers disproportionately use dark mode, so it gets equal design effort:

- Warm dark background, not pure black. Surfaces (sidebar, cards, code panels) step up from it in small value increments.
- Code blocks go slightly lighter than the page background in dark mode so they still read as panels.
- Syntax token colors re-picked for dark, not reused.
- Accent nudged brighter to hold contrast; callout tints darkened so they whisper instead of glow.

## Micro-details that make it feel expensive

- Heading anchor links: a "#" appears on hover next to h2/h3s.
- The right-rail TOC highlights the section currently in view (a small IntersectionObserver).
- 1px low-contrast borders instead of drop shadows almost everywhere.
- Smooth scroll for in-page anchors, gated behind `prefers-reduced-motion`.
- `scroll-margin-top` on headings so anchors don't hide under the top bar.

## The bland test

Before delivering a docs page, count: if it has no callout, no styled code block with a copy button, no card grid or field list, and no right-rail TOC, it will read as a markdown dump with a sidebar. At least three of these components should exist on any real docs page, used where the content genuinely calls for them.
