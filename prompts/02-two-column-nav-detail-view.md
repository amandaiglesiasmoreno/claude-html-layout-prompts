Create a single-page, self-contained HTML app that serves as a reference guide for AI agent architectures. All content lives on one scrollable page.
 
## Architectures
 
Six architectures are displayed on the page, stacked vertically one after another:
- Supervisor
- Swarm
- Router
- Handoffs
- Skills
- Human-in-the-loop
 
## Page Structure
 
A centered page header at the top: title "AI Agent Architectures" in Poppins font-weight: 500.
Below the header, each architecture is rendered as a full-width section, stacked vertically with consistent spacing between them.
A thin horizontal divider (`<hr>`) separates each section from the next.
A sticky left sidebar navigation lists all six architecture names and highlights the one currently in view.
 
## Left Sidebar Navigation
 
- A `<nav>` element, `168px` wide, full viewport height, `position: sticky; top: 0`, with a `1px solid --color-divider` right border.
- A small uppercase label at the top: "Architectures" (`font-size: 0.65rem`, `letter-spacing: 0.1em`, muted color).
- One `<a>` link per architecture, each with a `6px` hollow circle dot on its left.
- **Active state** (section currently in the viewport): link text becomes full-weight (`font-weight: 500`), dot fills solid and scales up (`transform: scale(1.35)`), a `2px` vertical accent bar appears flush with the nav's left border.
- Active section detected via `IntersectionObserver` with `rootMargin: "-15% 0px -70% 0px"`. A `scroll` event fallback (80ms debounce) sets active to whichever section's top is geometrically closest to the viewport top.
- Clicking a link smooth-scrolls to its section.
 
## Architecture Section Layout — Two Columns
 
Each architecture section uses a two-column layout:
 
### Left column
- A wrapper div (80×80px) that positions the icon and its decorative blob.
- A decorative circle (50px diameter), soft semi-transparent light-blue fill (`rgba(173, 210, 255, 0.55)`), no stroke, positioned absolutely at `bottom: -3px; right: -3px` — it does **not** surround the icon but sits behind it, offset to the bottom-right.
- The minimalist SVG line icon (56×56px) is centered in the wrapper and shifted `transform: translate(6px, 6px)` so it overlaps the blob toward the bottom-right, while the icon's visual weight sits top-left.
- The architecture name sits below the wrapper, in Poppins font-weight: 500, font-size: 0.95rem, centered.
- This column is fixed-width (~160px), not fluid.
 
### Right column
- The architecture name as a section heading (`<h2>`, Poppins font-weight: 500).
- A short description paragraph.
- Four subsections with uppercase tracked labels (letter-spacing: 0.08em, font-size: 0.7rem, font-weight: 600):
  - **How it works** — brief prose.
  - **Common use cases** — bullet list (3 items).
  - **Main advantages** — bullet list (3 items).
  - **Main disadvantages** — bullet list (3 items).
 
### Column rules
- Column gap: 2rem.
- Left column is top-aligned with the right column content.
- CSS layout: `display: grid; grid-template-columns: 160px 1fr;`
 
## Layout and Visual Style
 
- The page uses a two-column outer grid: `grid-template-columns: 168px 1fr`, `max-width: 1060px`, `margin-inline: auto`. The left column is the sidebar nav; the right column is the scrollable content area (`padding-inline: 2rem 2.5rem`).
- No backgrounds, shadows, gradients, or bright colors — strictly monochrome except the blob.
- Color palette: `--color-bg: #edeae4`, `--color-text: #2c2a26`, `--color-text-muted` for nav inactive links.
- `padding-block: 2.5rem` per section.
- Dividers: `border: none; border-top: 1px solid #d0d0d0;`
- `html { scroll-behavior: smooth; scroll-padding-top: 2rem; }`
 
## Technical Requirements
 
- One single `.html` file. All CSS in `<style>`. All JS in `<script>` before `</body>`.
- Semantic HTML: `<main>`, `<section id="...">` (each section has an `id` matching its nav anchor), `<nav>`, `<header>`, `<h1>`, `<h2>`, `<ul>`, `<hr>`.
- Responsive:
  - Below `860px`: sidebar collapses into a sticky horizontal top bar (`flex-direction: row`, `border-bottom` replaces `border-right`, active indicator becomes a bottom underline bar).
  - Below `560px`: arch sections collapse to single column, icon + label inline on top.
- Light/dark toggle button fixed top-right (sun/moon icon), `data-theme` on `<html>`, defaults to `prefers-color-scheme`. Dark mode: text `#e0e0e0`, dividers `#333`.
- `prefers-reduced-motion` respected — disable all transitions.
- Visible `:focus-visible` outlines on all interactive elements.