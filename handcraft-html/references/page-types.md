# Page types

Read the section for the chosen type before designing. The technical floor from SKILL.md (theming, mobile, accessibility) applies to all of them and isn't repeated here. Types 1 through 5 are documentation-family pages and all additionally require `references/docs-style.md`, which holds the layout and component playbook they share.

## Contents

1. Product documentation
2. API reference
3. Runbook / operations guide
4. Code documentation (library or repo)
5. Internal wiki / handbook
6. Portfolio
7. Landing page
8. Personal / resume site
9. Something else

---

## 1. Product documentation

**Job**: get a reader from "I want to do X" to a working X.

**Also read**: `docs-style.md`. This is the canonical type it was written for.

**Structure**: sidebar grouped by user journey (Getting started, Guides, Reference, Troubleshooting), not by internal team structure. Every page opens with a one-sentence statement of what the reader will have when they finish. Task pages are numbered steps; concept pages are prose with a diagram.

**Components that earn their place**: callouts for prerequisites and gotchas, code blocks with copy buttons, card grids on index pages, prev/next pagination at the bottom.

**Traps**: writing what the feature is instead of what the reader does with it. Burying the prerequisite in paragraph three instead of a callout at the top.

## 2. API reference

**Job**: let someone find an endpoint or parameter and use it correctly without reading anything else.

**Also read**: `docs-style.md`, especially the field-list component.

**Structure**: one section per endpoint or method. Each opens with the signature in a code block, then a field list of parameters (monospace name chip, type, required flag, description), then a response example, then errors. Ruthlessly consistent order across every endpoint, because readers scan by position.

**Recommended layout**: two-column on wide screens, prose on the left and the request/response example sticky on the right. Collapse to stacked on tablet and below, examples following their prose.

**Components**: field lists, method badges (GET, POST, DELETE) as small colored chips, status code tables, tabbed language examples if multiple SDKs are documented.

**Traps**: undocumented error cases, examples with placeholder values that don't parse, inconsistent field ordering between endpoints. Every example should be copy-pasteable and actually valid.

## 3. Runbook / operations guide

**Job**: get someone through a procedure correctly at 3am while stressed.

**Also read**: `docs-style.md`.

**Structure**: this type inverts normal doc priorities. Lead with the fastest path. Put a "when to use this" line at the very top, then the procedure as numbered steps, then verification, then rollback, then background context last. Context is for the reader who has time; the top of the page is for the reader who doesn't.

**Components**: numbered steps with the command in a copy-button code block, warning callouts before any destructive action, a verification checkbox list, a symptom-cause-fix table for troubleshooting.

**Design notes**: Terminal theme is the natural fit. Wider steps, larger code type than usual, generous spacing between steps so nobody loses their place mid-procedure.

**Traps**: prose paragraphs where a command should be. Mixing "explain the system" with "fix the system"; if both are needed, the explanation goes below the procedure or on a separate page. Never bury a destructive command without a warning callout directly above it.

## 4. Code documentation (library or repo)

**Job**: get a developer from install to first working call, then serve as a reference afterward.

**Also read**: `docs-style.md`.

**Structure**: install snippet within the first screen, minimal working example immediately after (the shortest code that does something real), then usage guides, then a per-function or per-module reference, then contributing and license.

**Components**: language-tabbed install blocks (npm, pip, cargo), function signature blocks, field lists for options objects, badge row for version and license if the user wants it.

**Traps**: an example that needs three unmentioned setup steps to run. Documenting every function equally when four of them cover 90% of usage; the common ones go first and get real examples. Skipping the "what is this even for" line at the top, which readers arriving from search need most.

## 5. Internal wiki / handbook

**Job**: be findable and current for people inside one organization.

**Also read**: `docs-style.md`.

**Structure**: sidebar grouped by department or topic, a prominent search affordance, and per-page metadata that matters internally: owner, last reviewed date, related pages. Cross-links between pages carry more weight here than in any other type.

**Components**: card grids for section landing pages, tables for policies and matrices, note callouts for exceptions, an owner and last-updated line under each h1.

**Design notes**: Forest or Slate suit this best. Lower visual intensity than product docs, since people read this daily and internally.

**Traps**: no owner and no review date, which is how wikis rot. Marketing tone in an internal handbook. Deep nesting; keep the tree at two levels wherever possible.

## 6. Portfolio

**Job**: make the work look good and the person easy to contact.

**Structure**: work first, often before any intro. Each project gets an image or result plus one or two sentences (what it was, your role, one outcome). Short bio, clear contact.

**Design notes**: Mono is the strongest default here, because a colorless page puts nothing in competition with the work. Vary project sizes by importance rather than using a uniform grid; identical cards make varied work look templated.

**Traps**: "passionate creative professional" copy. Skill bars with percentages. A uniform three-column grid that flattens the good work down to the level of the filler.

## 7. Landing page

**Job**: get one specific action taken.

**Structure**: hero stating plainly what the thing is, proof or demonstration, how it works if non-obvious, one honest CTA section. Cut any section that exists only because landing pages usually have it.

**Traps**: the type where AI tells concentrate hardest. No invented testimonials, no fake logo walls, no "trusted by 10,000+ teams". If there's no social proof, show the product instead.

## 8. Personal / resume site

**Job**: represent one person credibly.

**Structure**: name and what they do, selected work or experience with concrete outcomes, contact and links. One page.

**Traps**: skill bars, decorative dot-and-line timelines, and five distinctive design choices where one would read as taste.

## 9. Something else

The user wants a page type not listed. Ask what the page's single job is and who reads it, then borrow the closest structure above. If it's technical and reference-shaped, `docs-style.md` still applies. Don't force an ill-fitting template; the floor rules (theming, mobile, no AI tells, humanized copy) carry regardless of type.
