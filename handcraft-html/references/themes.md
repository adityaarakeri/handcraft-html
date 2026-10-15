# Named color themes

Six color presets. Every value below is contrast-tested: body text and link text clear 4.5:1 against their background in both light and dark. Use them verbatim. Do not "improve" a preset mid-build, and do not blend two of them. The Minimal, Notebook, and Glass docs style themes in `docs-style.md` reuse these palettes and add layout guidance.

**Always offer the choice.** Present the six color themes by name and one-line character; for documentation pages also offer Minimal, Notebook, and Glass as named choices. Skip this when the user already named a theme or supplied their own brand colors. Brand colors override the preset palette while a named docs style still controls layout.

**Never invent a palette when a preset fits.** Freehand palettes are how pages drift into the accidental green or navy cast. Only go custom when the user asks for something none of these cover, and when you do, say the palette out loud in one line first (see SKILL.md Step 3).

Every preset defines the same variable set, so swapping themes is a swap of two CSS blocks and nothing else:

    --bg  --surface  --surface-2  --border  --text  --muted  --accent  --accent-soft
    --code-bg  --code-text  --code-border  --tk-cmd  --tk-str  --tk-com  --tk-flag
    --note  --note-bg  --tip  --tip-bg  --warn  --warn-bg

---

## 1. Anthropic (warm paper, terracotta)

Warm, calm, editorial. The default choice for polished product documentation. Serif display over clean sans.

**Light**: bg `#FAF9F5`, surface `#F0EEE6`, surface-2 `#E9E6DB`, border `#DFD9CA`, text `#1F1E1D`, muted `#71695C`, accent `#B04A2C`, accent-soft `#F4E3D9`
**Dark**: bg `#1F1E1B`, surface `#262521`, surface-2 `#2D2C27`, border `#3A382F`, text `#EDEAE2`, muted `#A29C8E`, accent `#E08D6D`, accent-soft `#3B2A22`

Note: the brand's bright coral `#D97757` fails contrast as link text on cream. Use it only for large display elements or filled buttons with white text; `#B04A2C` carries links and small text.

## 2. Slate (cool grey, ink blue)

Neutral and corporate-safe. Good for API references and internal engineering docs where the content should feel institutional rather than branded.

**Light**: bg `#FBFBFC`, surface `#F2F3F5`, surface-2 `#E8EAED`, border `#DCDFE4`, text `#1C1E21`, muted `#666B73`, accent `#2C5A9E`, accent-soft `#E3EAF5`
**Dark**: bg `#16181C`, surface `#1D2026`, surface-2 `#24272E`, border `#31353D`, text `#E4E6EA`, muted `#969CA6`, accent `#7FA9E8`, accent-soft `#1E2634`

## 3. Terminal (near-black, phosphor amber)

For CLI documentation and runbooks. Monospace-forward, high contrast, minimal chrome. The light mode is a paper-terminal look rather than a washed-out dark mode.

**Light**: bg `#FCFBF7`, surface `#F3F1E9`, surface-2 `#EAE7DC`, border `#DAD6C7`, text `#1A1917`, muted `#6B6659`, accent `#8A5B00`, accent-soft `#F5E9CE`
**Dark**: bg `#121210`, surface `#191917`, surface-2 `#20201D`, border `#2C2C27`, text `#E6E4DC`, muted `#96938A`, accent `#E0A93B`, accent-soft `#2E2616`

## 4. Forest (warm off-white, deep green)

Calm and slightly organic. Suits internal wikis, handbooks, and knowledge bases that want to feel less like a product and more like a library.

**Light**: bg `#FAFAF7`, surface `#EFF1EC`, surface-2 `#E5E8E0`, border `#D6DBD0`, text `#1B1F1A`, muted `#636B5E`, accent `#2F6844`, accent-soft `#E0EDE4`
**Dark**: bg `#151815`, surface `#1C201B`, surface-2 `#232823`, border `#2F352E`, text `#E5E8E1`, muted `#949B90`, accent `#7FBF95`, accent-soft `#1E2C22`

## 5. Plum (soft grey, deep aubergine)

Distinct without being loud. Use when the subject already owns green or blue and you want separation, or for design-adjacent documentation.

**Light**: bg `#FCFBFC`, surface `#F3F0F3`, surface-2 `#EAE5EA`, border `#DDD5DD`, text `#1E1B1E`, muted `#6A626A`, accent `#6D3A76`, accent-soft `#EFE2F1`
**Dark**: bg `#18151A`, surface `#1F1B21`, surface-2 `#262129`, border `#332C36`, text `#E9E4EA`, muted `#9C939F`, accent `#C297CC`, accent-soft `#2A2130`

## 6. Mono (paper white, black, one red)

Nearly colorless. Swiss, print-like, all hierarchy carried by type and space. The strongest choice for a portfolio, since it puts zero color competition against the work.

**Light**: bg `#FFFFFF`, surface `#F4F4F4`, surface-2 `#EAEAEA`, border `#DBDBDB`, text `#111111`, muted `#5E5E5E`, accent `#C0271B`, accent-soft `#F8E4E2`
**Dark**: bg `#0E0E0E`, surface `#161616`, surface-2 `#1E1E1E`, border `#2A2A2A`, text `#EDEDED`, muted `#9A9A9A`, accent `#FF7A6B`, accent-soft `#2A1815`

---

## Shared values (all themes)

Code panels stay dark in both light and dark mode, which is standard for technical docs and keeps code visually distinct from prose.

**Light mode code**: code-bg `#21201C`, code-text `#EDEAE2`, code-border `#38362E`
**Dark mode code**: code-bg `#131311`, code-text `#E4E0D6`, code-border `#26251F`
**Tokens (both)**: tk-cmd `#8FB8F0`, tk-str `#A8C39A`, tk-com `#8A857A`, tk-flag `#D9B25F`

Exception: the Terminal theme uses warmer tokens: tk-cmd `#E0A93B`, tk-str `#B8C98A`, tk-com `#7C776B`, tk-flag `#D98E3B`.

Callouts are semantic, not decorative, so they keep their meanings across every theme. Blue reads as informational, green as positive, amber as cautionary. These stay constant even when the accent is green or blue; a Forest-theme Tip callout still reads as a Tip because of its icon and label, and the slight hue overlap with the accent is acceptable.

**Light**: note `#4A6B8A` on `#E9EEF2`, tip `#57794C` on `#EBF0E2`, warn `#9A6620` on `#F6EDDB`
**Dark**: note `#8FAEC9` on `#232A31`, tip `#98BA8A` on `#242B1F`, warn `#D9A85C` on `#322A1C`

## Type pairings per theme

- **Anthropic**: serif display (Iowan Old Style, Palatino, Georgia fallbacks), grotesque sans body
- **Slate**: sans display and sans body, differentiated by weight and size only
- **Terminal**: monospace display, sans body, monospace UI labels
- **Forest**: serif display, humanist sans body
- **Plum**: serif or high-contrast display, neutral sans body
- **Mono**: one grotesque at several weights, tight tracking on headings

All pairings use system font stacks by default so pages carry no external requests. Only load a webfont if the user asks, and always keep a system fallback.
