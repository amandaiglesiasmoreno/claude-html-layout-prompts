# AI Agent Architectures — Landscape Dashboard (Single HTML)
Build a polished, production-ready single-page HTML app that serves as a reference guide for AI agent architectures, designed as a **landscape dashboard** that fills the full viewport — no scrolling, everything fits the screen.
---
## Core Interaction
Show only one architecture at a time in the main content area.
 
Two circular navigation arrows — one on the left edge, one on the right edge of the content stage — move to the **previous** and **next** architecture respectively.
 
The arrows cycle through all six architectures in this order:
1. Supervisor
 
2. Swarm
 
3. Router
 
4. Handoffs
 
5. Skills
 
6. Human-in-the-loop
When the user reaches the last architecture, the right arrow loops back to the first. When on the first, the left arrow wraps to the last.
---
## Architectures
Include these six architectures with rich content for each:
 
- **Supervisor**, **Swarm**, **Router**, **Handoffs**, **Skills**, **Human-in-the-loop**
Each architecture section includes:
 
- A minimalist custom inline SVG icon (56×56px)
 
- Architecture name as `<h2>` in Poppins, font-weight 500
 
- A short description paragraph (2–3 sentences)
 
- Four subsections with uppercase tracked labels:
 
  - **How it works** — brief prose
 
  - **Common use cases** — bullet list (3 items)
 
  - **Main advantages** — bullet list (3 items)
 
  - **Main disadvantages** — bullet list (3 items)
---
## Page Structure
**Full-viewport layout** — the page acts like a dashboard slide. `height: 100dvh; overflow: hidden;` on `<body>`.
**Centered page header** at the top: title "AI Agent Architectures" in Poppins, font-weight 500. Keep it compact — single line, small size.
**Main stage** below the header fills the remaining height and holds the active architecture section.
Each architecture section uses a **two-column grid** (`grid-template-columns: 180px 1fr`, gap `2.5rem`):
**Left column (fixed 180px):**
 
- A wrapper div (80×80px) centered in the column, containing:
 
  - A decorative circle (50px diameter), soft semi-transparent light-pink fill (`rgba(255, 182, 193, 0.5)`), positioned absolutely at `bottom: -3px; right: -3px`
 
  - A minimalist SVG line icon (56×56px), centered, shifted `transform: translate(6px, 6px)` to overlap the blob
 
- Architecture name below the wrapper: Poppins, font-weight 500, `font-size: 0.9rem`, centered
 
- A thin vertical right border (`1px solid --color-divider`) dividing left from right column
**Right column (fluid):**
 
- Architecture `<h2>` — Poppins, font-weight 500
 
- Short description paragraph
 
- Four subsections laid out in a **2×2 grid** (`grid-template-columns: 1fr 1fr`, gap `1.5rem`) so all four subsections are visible without scrolling
---
## Bottom Navigation
Two circular arrow buttons:
 
- **Left arrow** (`←`): centered vertically on the left edge of the stage
 
- **Right arrow** (`→`): centered vertically on the right edge of the stage
Each button:
 
- 44×44px circular, border `1.5px solid --color-border`, background `--color-surface`
 
- A small progress label such as `2 / 6` centered below the stage
 
- On hover: background becomes `--color-surface-2`, border darkens slightly
 
- `aria-label="Previous architecture"` / `aria-label="Next architecture"`
Keyboard navigation:
 
- `ArrowLeft` / `ArrowUp` / `PageUp` → previous
 
- `ArrowRight` / `ArrowDown` / `PageDown` → next
---
## Transitions & Behavior
- Architecture changes animate with a **fade + subtle horizontal slide** (content slides out left, new slides in from right; reversed for back)
 
- Respect `prefers-reduced-motion` — use opacity-only fade, no slide
 
- JS manages active architecture state
 
- Update the URL hash to match the active section id (e.g., `#supervisor`)
 
- On page load, if a valid hash exists, show that architecture first
---
## Light/Dark Toggle
Fixed top-right corner: small circular button (sun/moon icon) with `data-theme-toggle`.
 
Default follows `prefers-color-scheme`. Sets `data-theme` on `<html>`.
---
## Technical Requirements
- **One single `.html` file** — all CSS in `<style>`, all JS in `<script>` before `</body>`
 
- Semantic HTML: `<main>`, `<section id="...">`, `<header>`, `<h1>`, `<h2>`, `<ul>`, `<hr>`
 
- No left sidebar, no page scrolling — pure viewport-filling dashboard layout
 
- Visible `:focus-visible` outlines on all interactive elements
 
- `html, body { height: 100dvh; overflow: hidden; }` — must fit entirely in the viewport
---
## Responsive Behavior
- **Below 860px**: two-column architecture layout collapses to single column; icon + name become a compact inline row at the top
 
- **Below 560px**: the 2×2 subsection grid collapses to single column; use compact font sizes
 
- Navigation arrows remain visible and functional at all sizes
 
- Design avoids vertical scroll on tablets in landscape orientation