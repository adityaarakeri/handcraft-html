# Runbook: handcraft-html

The short version of everything you need when actually using this skill, written for the person mid-task, not the person reading docs for fun. The HTML field guide covers the same ground with more depth; this is the laminated card you keep next to the keyboard.

## What this skill does

Builds HTML pages that pass for human-designed. Every build ships with:

- Light and dark themes (follows system, toggle overrides, no flash on load)
- Mobile-first layout, no horizontal scroll at 360px
- Zero em-dashes, humanized copy, no zombie marketing words
- No AI visual tells (purple gradients, glass cards, icon-circle grids)
- No hotlinked images that can 404, forms that are honest about backends

Think of it as a design review that runs before you ever see the output instead of after.

## Install once, per tool

| Tool | Where the skill lives | Notes |
|---|---|---|
| Claude.ai | Save the .skill file via the file card or Settings | Applies to new chats only |
| Claude Code | `.claude/skills/` (project) or `~/.claude/skills/` (global) | Best tool for iterating, it can screenshot its own output |
| Codex CLI | `~/.codex/skills/` | Invoke with `@handcraft-html`, needs a recent CLI |
| Antigravity CLI | Migrate with `agy plugin import gemini`, or place folder and verify with `agy inspect` | Replaced consumer Gemini CLI on June 18, 2026; Agent Skills carried over. Enterprise licenses still run legacy Gemini CLI (`gemini skills install`) |
| OpenCode | Project folder + a pointer in AGENTS.md | Be explicit by name on first use to confirm wiring |
| Copilot | Flatten into `.github/copilot-instructions.md` | Trim to SKILL.md + ai-tells.md, no on-demand loading |

For every tool except Claude.ai you need the raw folder, not the .skill file. A .skill is a zip in a trenchcoat: rename to .zip, extract, done.

## Daily driving

**Lazy prompt** (skill asks what kind of site, then builds):

    build me a website for my bakery

**Loaded prompt** (skips all questions):

    Build a local business site for Marrow & Rye bakery in Oakland.
    One page. Brand colors #3B2F2A and #D9A441, font Fraunces if possible.
    Real menu: country loaf $9, seeded rye $10, morning bun $5.
    Default to light theme.

**Redesign an existing page**:

    Redesign attached landing.html with the handcraft-html skill.
    Keep all copy and the working form action. Everything visual can go.

**Force the skill when it doesn't fire**:

    Use the handcraft-html skill for this.

## Options cheat sheet

Everything is a plain sentence, and anything you state beats the skill's defaults:

- Site type: name one of the 8 (landing, portfolio, blog, local business, e-commerce, docs, event, personal) or get asked
- Brand: paste hex codes / fonts / logo, they override the anti-default rules
- Files: "split files" for css/js separated, "separate pages" for real multi-page
- Theme: "default to dark" to flip the starting state
- Copy: paste real text and it's used verbatim (minus em-dashes)

## When it goes wrong

Run these in order; each fix is a sentence you say to the tool.

1. **Doesn't trigger**: new session, check the install path, then invoke by name.
2. **Looks AI anyway**: "run the self-check in references/ai-tells.md against this output and fix every failure."
3. **Em-dashes leaked**: "search the file for the em-dash character and remove every one."
4. **White flash in dark mode**: "move the theme init script inline into the head, before styles."
5. **Sideways scroll on phone**: "find what overflows at 360px and contain it."
6. **Broken image icons**: "replace external image URLs with inline SVG or labeled placeholders."
7. **Anything else**: "read skills/handcraft-html/SKILL.md and its references, then redo this." The nuclear option, resets the whole run.

## Maintaining the skill

The skill is markdown, so editing it is editing text files:

- `SKILL.md`: the workflow. Change process here.
- `references/ai-tells.md`: the banned-patterns list and final checklist. When you spot a new AI tell in the wild, add it here and it's enforced everywhere.
- `references/site-types.md`: per-type playbooks. Add a 9th site type here.
- `references/docs-style.md`: the documentation look. Tune this if docs output drifts bland again.

After editing, repackage for Claude.ai (ask Claude to "repackage my handcraft-html skill") and re-save; for CLI tools, just overwrite the folder and start a new session.
