Create a **single-page, self-contained HTML app** that serves as a navigation hub for AI agent architectures. All navigation must use **hash-based routing** (`#supervisor`, `#swarm`, etc.) so the entire experience lives in one `.html` file with no external page dependencies.
 
---
 
## Architectures
 
Each architecture has a dashboard tile and an embedded detail view:
 
1. Supervisor
2. Swarm
3. Router
4. Handoffs
5. Skills
6. Human-in-the-loop
 
---
 
## Dashboard view (`#home` or default)
 
- A **3-column × 2-row grid** of equally-sized rectangular cards.
- Each card contains  a minimalist line icon with the name of the architecture.
- Each card is **fully clickable** and navigates to its detail view via hash (e.g. `href="#supervisor"`).
- CSS Grid layout:
  - `grid-template-columns: repeat(3, 1fr)`
  - `gap: 0.75rem`
- Card style:
  - Thin light-grey border (`#d0d0d0`), slightly rounded corners.
  - No background fill, no shadows, no gradients — wireframe look.
  - Icon centered horizontally and vertically.
 
---
 
## Detail views (one per architecture)
 
Each detail view replaces the dashboard when its hash is active. It must include:
 
- A **back link** (e.g. `← Back`) that navigates to `#home`.
- The same **line icon** used on the dashboard tile, shown at a larger size.
- The architecture **name** as a heading (Poppins, `font-weight: 500`).
- A **short description** of how the architecture works.
- Four clearly labelled sections with uppercase tracked labels:
  - **How it works** — a brief prose explanation.
  - **Common use cases** — bullet list (3 items).
  - **Main advantages** — bullet list (3 items).
  - **Main disadvantages** — bullet list (3 items).
 
---
 
## Routing behavior
 
- On page load, read `window.location.hash`.
- If it matches a known architecture key, show that detail view and hide the dashboard.
- If it is empty or `#home`, show the dashboard.
- Listen to `hashchange` to switch views without reloading.
- On view change, scroll to the top of the page.
 
---
 
## Layout and visual style
 
- Dashboard-style layout, centered on the page with plenty of white space.
- No background fills, shadows, gradients, or bright colors anywhere — strictly wireframe / monochrome.
- Overall max-width: around `960px`, centered with `margin-inline: auto`.
 
---
 
## Typography and icons
 
- Load **Poppins** from Google Fonts (`weights: 300, 400, 500, 600`).
- Use Poppins for all headings, labels, and body text.
- Centered page title above the grid: `"AI Agent Architectures"` in Poppins `font-weight: 500`.
- All six icons: simple, minimalist **monochrome SVG line icons** drawn inline, consistent
  stroke width and size across the dashboard and detail views.
 
---
 
## Technical requirements
 
- **One single `.html` file** — no external CSS files, no JavaScript modules, no build tools.
- All CSS in a single `<style>` block in `<head>`.
- All JavaScript in a single `<script>` block before `</body>`.
- Semantic HTML: use `<nav>`, `<main>`, `<section>`, `<header>`, `<h1>`, `<h2>`, `<ul>`, etc.
- Responsive: grid collapses to **2 columns** below `540px` and **1 column** below `340px`.
- Include a **light/dark theme toggle** button (sun/moon icon) that switches a `data-theme`
  attribute on `<html>` and defaults to the system preference via `prefers-color-scheme`.
- Respect `prefers-reduced-motion` — disable transitions and animations for users who have
  it enabled.
- All interactive elements must have visible `:focus-visible` outlines.
