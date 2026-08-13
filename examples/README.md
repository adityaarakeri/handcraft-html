# Examples

Pages built by the skill, kept here as reference output.

## handcraft-html-field-guide.html

A documentation page covering how to run this skill across six tools. Built with the Anthropic theme, product documentation page type. It doubles as a working sample of the layout and components the skill produces: sidebar nav, scroll-tracking table of contents, callouts, code blocks with copy buttons, card grids, and a symptom-cause-fix table.

Open it directly:

```bash
open handcraft-html-field-guide.html        # macOS
xdg-open handcraft-html-field-guide.html    # Linux
```

Or serve it, which you want if you plan to extend it:

```bash
python3 -m http.server 8000
# http://localhost:8000/handcraft-html-field-guide.html
```

No build step and no dependencies. CSS and JS are inline, fonts are system stacks, icons are inline SVG, so the page makes no external requests and works offline.
