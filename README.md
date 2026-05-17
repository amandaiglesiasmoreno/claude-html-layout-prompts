# Amazing HTML Layouts with Claude — In Minutes

> A collection of 4 battle-tested prompts to generate stunning, production-quality HTML layout designs using Claude. 
---

## Prompts

| # | Prompt | Style | What it builds |
|---|--------|-------|----------------|
| 01 | [Minimal Icon Card Grid](prompts/01-minimal-icon-card-grid.md) | Minimalist | 3×2 grid of rectangular cards with icon + label — clean, no-noise layout |
| 02 | [Two-Column Nav Detail View](prompts/02-two-column-nav-detail-view.md) | Structured | Two-column layout with active sidebar nav + rich detail panel |
| 03 | [Fullscreen Slide Navigator](prompts/03-fullscreen-slide-navigator.md) | Presentational | PowerPoint-style landscape viewer with edge arrows + progress indicator |
| 04 | [Neo-Brutalist Vertical Pager](prompts/04-neo-brutalist-vertical-pager.md) | Expressive | Thick borders, bright colors, right-side vertical pager with stacked progress bar |

---

## How to Use

1. Open any prompt file from the `prompts/` folder
2. Copy the prompt text
3. Paste it into [Claude](https://claude.ai) (works best with Claude Sonnet or Opus)
4. Customize the `{{variables}}` with your own content
5. Copy Claude's HTML output → save as `.html` → open in your browser

All prompts are tested and produce **complete, single-file HTML** — no dependencies, no build tools.

---

## Repository Structure

```
claude-html-layout-prompts/
├── README.md
├── prompts/
│   ├── 01-minimal-icon-card-grid.md
│   ├── 02-two-column-nav-detail-view.md
│   ├── 03-fullscreen-slide-navigator.md
│   └── 04-neo-brutalist-vertical-pager.md

```

---

## Style Spectrum

The 4 prompts cover a full range of design styles — from ultra-clean to bold and expressive:

```
Minimalist ──────────────────────────────────── Expressive
    01            02            03            04
  Icon Grid   Master-Detail  Slide Viewer  Neo-Brutalist
```

---

## Tips for Best Results

- **Be specific in your content brief** — mention your topic, audience, and tone
- **Use the prompts in sequence** — start with 01 to explore the minimalist style, then experiment with 04 for a bold contrast
- **Claude Sonnet 4** is recommended for the best balance of speed and quality
- **Iterate freely** — ask Claude to tweak colors, swap icons, or adjust layout after the first output

---

## Requirements

- A Claude account at [claude.ai](https://claude.ai) (free tier works)
- A text editor or browser to preview the HTML output
- No coding knowledge required

---

## License

MIT — free to use, modify, and share.

---
