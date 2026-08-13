# handcraft-html

An [Agent Skill](https://github.com/anthropics/skills) that builds HTML pages which look and read like a person made them, not a model. Tuned for technical documentation: product docs, API references, runbooks, code docs, internal wikis, plus portfolios and landing pages.

Every page it produces ships with light and dark mode, is mobile optimized, contains no em-dashes, and passes a self-audit against a list of known AI design tells before you ever see it.

Works in Claude.ai, Claude Code, Codex CLI, Antigravity CLI, OpenCode, and GitHub Copilot.

## Why this exists

Ask any model for a web page and you tend to get the same page back: purple gradient hero, three feature cards with icons in tinted circles, copy about unlocking seamless solutions, and a fistful of em-dashes. It is competent and completely anonymous.

This skill is the opposite approach. Instead of correcting those patterns after the fact, it bakes the review into the build. The model reads a list of banned patterns before designing, picks from contrast-tested palettes instead of improvising, and runs a checklist against its own output before delivering. Think of it as a design review that happens before the work reaches you rather than after.

## What you get

- **Nine page types**, each with its own structure, components, and traps. A runbook and an API reference do not share a skeleton.
- **Six named themes**, each with hand-tuned light and dark values. All 36 text and background pairings clear WCAG AA at 4.5:1.
- **A technical floor on every build**: theme toggle with no flash on load, mobile-first CSS with no horizontal scroll at 360px, 44px touch targets, semantic landmarks, visible focus styles, reduced-motion support.
- **Copy rules**: no em-dashes anywhere, no zombie marketing words, mandatory humanization pass before delivery.
- **No broken output**: no hotlinked images that 404, no forms that silently swallow submissions.

## Install

### Claude.ai

Zip the `handcraft-html/` folder, rename the archive to `handcraft-html.skill`, then upload it under Settings and Capabilities. Applies to new conversations.

### Claude Code

```bash
# project-scoped, travels with the repo
mkdir -p .claude/skills && cp -r handcraft-html .claude/skills/

# or personal, available everywhere
cp -r handcraft-html ~/.claude/skills/
```

### Codex CLI

```bash
mkdir -p ~/.codex/skills
cp -r handcraft-html ~/.codex/skills/
```

Invoke with `@handcraft-html` or let it trigger on a matching task.

### Antigravity CLI

Antigravity CLI (`agy`) replaced the consumer Gemini CLI on June 18, 2026 and kept Agent Skills intact.

```bash
# migrating an existing Gemini CLI setup
agy plugin import gemini
agy inspect                  # confirm handcraft-html registered

# fresh install: place the folder, then verify
agy inspect
```

Enterprise Gemini Code Assist licenses still run the legacy CLI, where `gemini skills install ./handcraft-html` applies.

### OpenCode

Place the folder in your project, then point `AGENTS.md` at it:

```markdown
## Skills
When the task involves building or redesigning HTML pages,
load and follow skills/handcraft-html/SKILL.md before writing code.
```

### GitHub Copilot

Copilot has no skill loader, so the content gets flattened into instructions:

```bash
cat handcraft-html/SKILL.md handcraft-html/references/*.md >> .github/copilot-instructions.md
```

This loses on-demand loading, so consider trimming to `SKILL.md` plus `ai-tells.md` to keep context lean.

## Usage

Ask for a page. The skill asks two questions (page type and theme), then builds.

```
Build a docs site for our CLI.
```

Answer anything upfront and it skips the questions:

```
Build an API reference for our payments endpoints, Slate theme.
Endpoints: POST /charges, GET /charges/:id, POST /refunds.
```

Redesign an existing page:

```
Redesign docs/index.html with the handcraft-html skill.
Keep all copy and working links. Terminal theme.
```

### Page types

| Type | Best for | Suggested theme |
|---|---|---|
| Product documentation | Guides and tutorials for a product | Anthropic or Slate |
| API reference | Endpoint and method documentation | Slate |
| Runbook | Operational procedures, incident response | Terminal |
| Code documentation | Library or repo docs | Slate or Terminal |
| Internal wiki | Handbooks, policies, team knowledge | Forest |
| Portfolio | Showing work | Mono |
| Landing page | One conversion action | Any |
| Personal site | Resume, links, bio | Mono or Plum |
| Something else | Anything not listed | Ask |

### Themes

| Theme | Character |
|---|---|
| Anthropic | Warm paper and terracotta. Editorial, calm. |
| Slate | Cool grey and ink blue. Neutral, institutional. |
| Terminal | Near-black and phosphor amber. Monospace-forward. |
| Forest | Warm off-white and deep green. Quiet, library-like. |
| Plum | Soft grey and deep aubergine. Distinct without being loud. |
| Mono | Paper white, black, one red. Swiss and colorless. |

Supplying your own brand colors overrides theme selection entirely.

### Other options

All of these are plain sentences in your prompt, not flags:

| Option | Say this | Default if silent |
|---|---|---|
| File layout | "split files" | One self-contained `.html` |
| Multi-page | "separate pages" | Anchor-linked sections in one file |
| Starting theme | "default to dark" | Follows the visitor's system setting |
| Content | Paste real text, endpoints, prices | Skill writes specific, humanized copy |

## Repository layout

```
handcraft-html/
  SKILL.md              the workflow, six steps
  references/
    page-types.md       structure and traps per page type
    themes.md           six presets, tested hex values, both modes
    docs-style.md       layout and components for documentation types
    ai-tells.md         banned patterns and the final checklist
examples/
  handcraft-html-field-guide.html   a page built by the skill
RUNBOOK.md              quick reference for daily use
```

## Customizing

Everything is markdown, so editing the skill is editing text.

- **Add a theme**: copy a block in `themes.md`, keep the same variable names, and verify contrast at 4.5:1 minimum for text, muted text, and accent against both backgrounds.
- **Add a page type**: add a section to `page-types.md` and list it in Step 1 of `SKILL.md`.
- **Ban a new pattern**: add it to `ai-tells.md` and add a matching line to the checklist at the bottom. Anything in that checklist gets enforced on every build.
- **Change the docs look**: `docs-style.md` governs layout and components for the documentation types.

After editing, restart your session so the tool re-reads the skill.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Skill never triggers | Start a fresh session, verify the install path, then invoke by name |
| Output still looks AI generated | "Run the self-check in references/ai-tells.md against this output and fix every failure" |
| Em-dashes appear | "Search the file for the em-dash character and remove every one" |
| White flash on load in dark mode | "Move the theme init script inline into the head, before styles" |
| Horizontal scroll on mobile | "Find what overflows at 360px and contain it" |
| Broken image icons | "Replace external image URLs with inline SVG or labeled placeholders" |
| Unexpected green or navy cast | Name a theme explicitly; improvised palettes drift toward those two |
| Rules ignored in Copilot | Trim the flattened instructions and move the rules you care about to the top |

The universal reset, in any tool: "Read handcraft-html/SKILL.md and its references, then redo this."

## Requirements

None. The skill is plain markdown and produces plain HTML with no build step, no dependencies, and no external requests. Pages use system font stacks and inline SVG so they work offline.

## License

MIT. See [LICENSE](LICENSE).
