# Site Redesign — Task List

> This file is the handoff document. Each task has a designated model.
> Run a new chat with the right model, point it at this file, and tell it to do its section.

---

## Sonnet Tasks

### ~~S1. Merge Opening + Background into a single section~~ ✓ Done

**Goal:** Eliminate the separate `#background` section. Combine its content into `#opening` so the visitor gets the full picture in one screen, then hits Inquiries immediately.

**Current state (index.html):**
- `#opening` (line ~1007): Name, two-paragraph bio, location, photo placeholder.
- `#background` (line ~1550): Prose paragraph (training, Stuttgart, Ahmedabad, Athena), "at a glance" facts card (education, current role, prior roles, CV download link).

**What to do:**
1. Move the "at a glance" facts card into `#opening`, placing it below the photo frame (or beside the bio on wide screens — use the existing `.opening-grid` and add a third row or a second column group).
2. The background *prose* is largely redundant with the opening statement. Do NOT keep it as a separate paragraph. Instead, lightly revise the opening statement to incorporate any missing details (specifically: "Ahmedabad University teaching 2024–25" and "Athena Education, internal tooling" are not in the current opening). Keep the tone and length roughly the same — two paragraphs, not three.
3. Delete the entire `#background` section from the HTML.
4. Remove `background` from the nav links.
5. Update any CSS that targets `#background` — either remove it or keep it if the classes are reused.
6. The CV download link (`<a href="#" class="cv-link">`) currently has a placeholder `href="#"`. Leave it as-is for now.

**Visual check:** After the edit, the page should go: Opening (name + bio + facts card + photo) → Inquiries → Thesis → Teaching → Writing → Contact. Six nav links become five.

**Files to edit:** `index.html` only.

---

### ~~S2. Redesign the thesis hero image (SVG)~~ ✓ Done

**Goal:** Replace the current abstract SVG hero in `#thesis` with something that looks like an actual BEC density plot, inspired by Figure 4.7 from Ninaad's thesis.

**Reference (Figure 4.7, bottom-right panel):** Three vortex cores in a triangular arrangement, surrounded by a smooth condensate density envelope. Dark purple background, viridis-like colourmap (purple → blue → green → yellow for increasing density), vortex cores appear as dark circular dips.

**What to build:**
1. An SVG (same viewport: `viewBox="0 0 700 240"`) with a dark background (`#0D0B1A`).
2. Centre of the image: a condensate density blob rendered as concentric ellipses or radial gradient, using a viridis-inspired palette:
   - Core density (highest): `#FDE725` (yellow)
   - Mid density: `#21918C` (teal-green)
   - Low density: `#440154` (deep purple)
   - Background: `#0D0B1A`
3. Inside the density blob: three vortex cores arranged in a tight equilateral triangle (roughly matching the bottom-right panel of Fig 4.7). Each core is a small dark circle (`#0D0B1A` or very dark purple) ~8–10px radius, with a subtle ring of lower density around it (a thin annulus in the blue-purple range).
4. **CMM grid overlay:** Behind or semi-transparently over the density plot, draw a grid that transitions from coarse cells (~20px spacing) at the edges to fine cells (~5px spacing) near the vortex cores. Use very faint lines (`rgba(255,255,255,0.06)` for coarse, `rgba(255,255,255,0.10)` for fine). This communicates the Cascadic Multigrid Method visually.
5. Keep the existing left-side annotations (ROTATING DIPOLAR BEC, ¹⁶⁴Dy · N = 75,000, Ω̂/ω⊥ = 0.90, ε_dd = 1.36, 128³ spatial grid) and right-side annotations (UNIV. STUTTGART, PI5 · 2023, methods, CGM · ITE · CMM). Adjust positions if needed but keep the same font families and colours.
6. Replace the current phase-legend strip (bottom-right) with a small viridis colourbar labelled "density (10²¹ m⁻³)" with values 0 → 14 (matching Fig 4.7 scale).

**Files to edit:** `index.html` — replace the entire `<svg>` block inside `.thesis-hero-wrap` (lines ~1369–1500 in the current file, but line numbers may shift after S1).

---

## Haiku Tasks

*(None yet — will be added as mechanical edits arise.)*
