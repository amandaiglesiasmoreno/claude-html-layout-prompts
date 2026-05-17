# AI Agent Architectures — Neobrutalist Landscape Dashboard (Single HTML)
 
Build a polished, production-ready single-page HTML app that serves as a reference guide for AI agent architectures, designed as a **neobrutalist landscape dashboard** that fills the full viewport — no scrolling, everything fits the screen.
 
The visual style should be bold, graphic, high-contrast, and intentionally rigid, using **bright colors, purple hues, hard edges, thick borders, flat fills, strong shadows, and loud visual hierarchy**. The result should feel like a contemporary neobrutalist web poster merged with a dashboard interface.
 
---
 
## Core Interaction
 
Show only one architecture at a time in the main content area.
 
Use a **vertical right-side pager** inside the content stage, vertically centered.
 
The pager contains:
 
- A **previous** arrow button at the top
- A vertical progress indicator in the middle
- A **next** arrow button at the bottom
 
The pager cycles through all six architectures in this order:
 
1. Supervisor
2. Swarm
3. Router
4. Handoffs
5. Skills
6. Human-in-the-loop
 
When the user reaches the last architecture, the next button loops back to the first. When on the first, the previous button wraps to the last.
 
The progress area should show:
- the current index such as `2 / 6`
- and/or six bold stacked markers, blocks, or bars, with the active one highlighted in a contrasting bright accent color
 
Keyboard navigation:
- `ArrowUp` / `ArrowLeft` / `PageUp` → previous
- `ArrowDown` / `ArrowRight` / `PageDown` → next
 
---
 
## Architectures
 
Include these six architectures with rich content for each:
 
- **Supervisor**
- **Swarm**
- **Router**
- **Handoffs**
- **Skills**
- **Human-in-the-loop**
 
Each architecture section includes:
 
- A custom inline SVG icon (56×56px) in a bold, graphic minimalist style
- Architecture name as `<h2>`
- A short description paragraph (2–3 sentences)
- Four subsections with uppercase tracked labels:
 
  - **How it works** — brief prose
  - **Common use cases** — bullet list (3 items)
  - **Main advantages** — bullet list (3 items)
  - **Main disadvantages** — bullet list (3 items)
 
Content should remain concise and readable, but the presentation should feel punchy, expressive, and visually assertive.
 
---
 
## Visual Direction
 
Use a **neobrutalist** aesthetic with these qualities:
 
- Thick black or near-black borders
- Flat, saturated color fills
- High contrast between surfaces and text
- Hard corners or only slightly rounded corners
- Strong offset shadows instead of soft blur
- Oversized labels, visible structural lines, and obvious hierarchy
- Slight asymmetry is allowed if it feels intentional
- The interface should feel bold, poster-like, and graphic rather than refined or delicate
 
### Color palette
 
Use a bright, energetic palette built around **purple hues**, for example:
 
- vivid violet
- electric purple
- lavender
- hot pink or magenta accents
- acid yellow or bright lime as a contrasting secondary accent
- white, off-white, or pale lavender surfaces
- black or very dark charcoal for borders and text
 
Purple should be the dominant personality color.
 
Do not use subtle beige editorial tones.  
Do not use soft Swiss neutrals.  
This version should be visually loud, playful, and unmistakably graphic.
 
### Borders and shadows
 
- Use thick borders, for example `2px` to `4px solid #111`
- Use offset shadows such as `4px 4px 0 #111` or `6px 6px 0 #111`
- Avoid subtle, soft, blurred shadows
- Visual depth should come from **hard shadow offsets**, not softness
 
### Icons
 
- Inline SVG only
- Minimal but bolder than the Swiss version
- Use thicker strokes
- Icons can sit inside a bright filled square, rectangle, or circular badge with a black border
- Make the icon area feel like a graphic sticker or stamped label
 
---
 
## Page Structure
 
**Full-viewport layout** — the page acts like a dashboard slide. `height: 100dvh; overflow: hidden;` on `<body>`.
 
**Centered page header** at the top:
- title: `AI Agent Architectures`
- compact enough to preserve space
- visually assertive through color, border treatment, or boxed styling
 
**Main stage** below the header fills the remaining height and holds:
- the active architecture section
- the vertical right-side pager
 
The stage should reserve clear space for the pager.
 
Each architecture section uses a **two-column grid**:
 
```css
grid-template-columns: 180px 1fr;
gap: 2.5rem;
```
 
### Left column (fixed 180px)
 
- An 80×80px wrapper centered in the column
- Inside it, place:
  - a bold bright shape behind the icon, such as:
    - a solid purple square
    - a magenta circle with black border
    - a yellow sticker-like rectangle behind the icon
- A custom SVG icon (56×56px), centered
- Architecture name below the wrapper, centered
- A clear dividing rule or thick border separating left and right columns
 
### Right column (fluid)
 
- Architecture `<h2>`
- Short description paragraph
- Four subsections laid out in a **2×2 grid**:
 
```css
grid-template-columns: 1fr 1fr;
gap: 1.5rem;
```
 
All four subsections must remain visible without scrolling.
 
Each subsection should look like a **neobrutalist content tile**:
- flat color or white background
- thick border
- hard shadow
- compact but clear internal spacing
- strong label treatment
- visually distinct from the stage background
 
---
 
## Right-Side Pager
 
Use a **single vertical pager on the right side of the stage**.
 
Structure:
1. top previous button
2. progress stack or numeric indicator
3. bottom next button
 
Style:
- pager should feel like a physical control strip or UI totem
- buttons can be circular or rounded-square
- thick black border
- flat bright fill
- hard shadow offset
- active marker shown in a bright purple, magenta, or acid accent
 
Hover behavior:
- slight translate effect
- color swap or inversion
- shadow offset changes subtly
 
Do not make the pager elegant or subtle — it should feel bold and tactile.
 
---
 
## Transitions & Behavior
 
- Architecture changes animate with a **fade + subtle horizontal slide**
- Motion should still feel crisp and controlled, not floaty
- Direction reverses when navigating backward
- Respect `prefers-reduced-motion` — use opacity-only fade, no slide
- JS manages active architecture state
- Update the URL hash to match the active section id (e.g. `#supervisor`)
- On page load, if a valid hash exists, show that architecture first
 
---
 
## Light/Dark Toggle
 
Fixed top-right corner:
- small but visually bold toggle button
- sun/moon icon
- `data-theme-toggle`
 
Behavior:
- default follows `prefers-color-scheme`
- sets `data-theme` on `<html>`
 
### Theme behavior
 
**Light mode**
- bright off-white or pale lavender background
- purple and pink blocks
- black borders
- strong colorful accents
 
**Dark mode**
- dark charcoal or near-black background
- bright purple, magenta, and electric accents
- preserve the neobrutalist energy instead of muting it
 
---
 
## Technical Requirements
 
- **One single `.html` file** — all CSS in `<style>`, all JS in `<script>` before `</body>`
- Semantic HTML: `<main>`, `<section id="...">`, `<header>`, `<h1>`, `<h2>`, `<ul>`, `<hr>`
- No left sidebar
- No page scrolling
- Pure viewport-filling dashboard layout
- Visible `:focus-visible` outlines on all interactive elements
- `html, body { height: 100dvh; overflow: hidden; }`
- JS manages architecture state, hash syncing, and pager updates
- Keep all six architectures readable and fully visible without scrolling
 
---
 
## Responsive Behavior
 
### Below 860px
- the two-column architecture layout collapses to a single column
- icon + architecture name become a compact inline row at the top
- the vertical right-side pager remains visible and functional
- preserve the bold neobrutalist style at smaller sizes
 
### Below 560px
- the 2×2 subsection grid collapses to a single column
- spacing and scale become slightly more compact
- borders and shadows can reduce slightly if needed, but the graphic style must remain intact
 
### General responsive goal
- avoid vertical scrolling on tablets in landscape orientation
- maintain a bold, poster-like dashboard composition
- keep the right-side pager usable at all sizes