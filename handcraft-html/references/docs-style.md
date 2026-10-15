# Polished technical docs

Read this whole file whenever the site type is documentation / knowledge site. Docs pages go bland when they're built as "an article with a sidebar". Modern reference-quality docs (the Anthropic / Stripe school) feel expensive because of crafted components and layout structure, not decoration. Restraint applies to ornament; it does not mean plain.

## Docs style themes

The six color themes in `themes.md` use **Classic** by default. Three additional named choices combine a docs layout with an existing contrast-tested palette. If the user asks for "Minimal theme", "Notebook theme", or "Glass theme", apply the corresponding layout and palette below without another choice. If the user supplies brand colors, use those colors with the selected layout. These patterns are adapted from the [Fumadocs layout family](https://www.fumadocs.dev/docs/ui/layouts); they are style options, not a claim about popularity.

| Theme | Palette | Best fit | Layout |
|---|---|---|---|
| Classic | User's chosen color theme | Broad product docs | Three-zone layout below |
| Minimal | Mono | Short guides and narrative docs | Sparse header, narrow reading column, compact navigation |
| Notebook | Slate | Dense API references, code docs, wikis | Compact sidebar and header, dense reference components |
| Glass | Slate | Product docs with a distinct visual identity | Floating translucent header and sidebar, quiet content surface |

### Minimal

Give the article most of the width and visual weight. Keep a small product mark, visible search trigger, theme toggle, and navigation access in a narrow header. A short desktop sidebar or collapsible section index is enough when the content tree is small. Use an inline "On this page" block for longer articles; a right rail is optional. Set generous line spacing, clear heading intervals, and hairline separators. Keep callouts and code panels where content needs them. Search matters more when navigation is sparse: make the trigger real if the site has multiple pages, or label it plainly as a placeholder until connected.

### Notebook

Use a compact top bar and a tight, independently scrollable sidebar. Group navigation under clear labels and support nested items; tabs can separate major product areas if the content tree warrants them. Keep the article readable while reducing excess space around field lists, tables, code examples, and metadata. A right-rail TOC remains useful on long pages, but can collapse into an inline block on narrower screens. Compact means efficient scanning, not small body text or sub-44px touch targets.

### Glass

Float the header and sidebar above a quiet page background with a modest translucent fill, a thin border, and limited backdrop blur. Keep the article itself opaque so prose and code contrast remain stable. Use the selected palette for text, links, callouts, and code; translucency affects navigation surfaces only. Provide an opaque fallback when `backdrop-filter` is unavailable, and check contrast over every background the panels can cross. On mobile, the sidebar becomes an opaque slide-over. Avoid colorful blobs, frosted card grids, and layered shadows.

## Classic layout anatomy

Classic desktop is a three-zone layout:

- **Left sidebar** (~250 to 280px, sticky, independently scrollable): the full nav tree.
- **Main content column**: measure capped around 65 to 72 characters, generous vertical rhythm.
- **Right rail** (~200px, sticky): an "On this page" mini table of contents built from the page's h2/h3s.

A slim top bar runs above all three: product name or logo on the left, a search input (decorative is fine, style it with a keyboard hint chip like "Ctrl K"), and the theme toggle.

For Classic, responsive collapse goes in order: tablet drops the right rail (fold the TOC into a collapsible "On this page" block above the content). Mobile collapses the sidebar behind a menu button into a slide-over panel. All four layouts keep the content column readable, provide navigation access on mobile, and avoid horizontal scroll.

## Navigation details

- Links grouped under small, muted labels ("Getting started", "API reference"). Classic and Notebook may use all caps; Minimal keeps labels quieter.
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
- Use the selected palette's background, text, and accent values. One confident accent carries links, active nav, and focus states. Accent discipline is what makes docs feel calm.
- Muted color does a lot of work: ledes, group labels, metadata, TOC links all step back so content steps forward.

**Color comes from the chosen theme, not from improvisation.** All palette values live in `themes.md`; use the selected preset verbatim. What matters at the docs level is how color is *deployed*: one confident accent carrying links, active nav, and focus states, with muted tones stepping back for ledes, group labels, metadata, and TOC links so the content steps forward. Accent discipline is what makes docs feel calm.

A note on the Anthropic preset specifically: its warm cream and terracotta combination is the same one `ai-tells.md` flags as a stock AI look, flagged precisely because everyone copies it. When the user picks it by name, that is a deliberate choice and it wins. The flag only governs improvised palettes.

## Dark mode for docs

Docs readers disproportionately use dark mode, so it gets equal design effort:

- Use the selected dark palette's background. Surfaces (sidebar, cards, code panels) step up from it in small value increments.
- Code blocks go slightly lighter than the page background in dark mode so they still read as panels.
- Syntax token colors re-picked for dark, not reused.
- Accent nudged brighter to hold contrast; callout tints darkened so they whisper instead of glow.

## Micro-details that make it feel expensive

- Heading anchor links: a "#" appears on hover next to h2/h3s.
- When a right-rail TOC is present, highlight the section currently in view (a small IntersectionObserver).
- 1px low-contrast borders instead of drop shadows almost everywhere.
- Smooth scroll for in-page anchors, gated behind `prefers-reduced-motion`.
- `scroll-margin-top` on headings so anchors don't hide under the top bar.

## The bland test

Before delivering a docs page, check for useful structure beyond plain prose: a callout, styled code block with a copy button, card grid, field list, table, inline or right-rail TOC, or prev/next links. Use at least three where the content genuinely calls for them. Minimal can omit cards and the right rail; its hierarchy, navigation, and article details must still feel deliberate. Short pages need fewer components than a full reference page.
