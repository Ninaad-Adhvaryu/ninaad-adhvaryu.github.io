# IMPROVEMENTS.md
Change log for the site polish pass — 2026-07-03. One entry per change with rationale. Nothing in `_source/` or `_drafts/` was touched; no git operations were performed.

## SEO & metadata
- **All 17 pages: added canonical URL, Open Graph tags (type/title/description/url), Twitter card, theme-color, and favicon link.** Links shared with recruiters/collaborators now unfurl with a real title and description instead of a bare URL. Canonical URLs use `https://ninaad-adhvaryu.github.io/…` (from the git remote).
- **Root `index.html`: title changed from "Ninaad Adhvaryu" to "Ninaad Adhvaryu — Computational Physicist & Data Scientist".** The title is the single strongest SEO/first-impression signal; name alone wastes it. `og:image` set to `photo.jpg`.
- **Created `favicon.svg`** (teal "N" monogram on obsidian, matching the palette). Every browser tab previously showed a blank default icon.

## Performance
- **`style.css`: removed the render-blocking `@import` of three Google Font families; each page now loads fonts via `<link rel="preconnect">` + stylesheet links in `<head>`.** `@import` inside CSS serializes font discovery behind the stylesheet download; `<link>` lets the browser fetch in parallel.
- **All figure images: added `width`/`height` attributes (real intrinsic dimensions) and `loading="lazy" decoding="async"` on below-the-fold images.** Eliminates layout shift and defers ~1.5 MB of images until scrolled to. Hero images are not lazy-loaded (above the fold).
- **Compressed `mapping-mangroves` figures 984 KB → 376 KB** (resized 2048px → 1400px, palette-quantized — safe for discrete-class maps) and **`photo.jpg` 88 KB → 62 KB** (resized to 600px, 2.7× its 220px display size). Page `width`/`height` attributes updated to match.

## Accessibility
- **`style.css`: added skip-to-content link styles, `:focus-visible` outlines, and a `prefers-reduced-motion` block** that disables the entrance animations and smooth scrolling. Keyboard users previously had no visible focus indicator and no way past the 6-link nav.
- **All pages: added `<a class="skip-link" href="#main">`, `<nav aria-label="Main">`, and a `<main id="main">` landmark** around page content (footers kept outside `<main>`).
- **Homepage: section markers (`inquiries`, `building`, `teaching`, `writing`, `contact`) changed `<p>` → `<h2>`, and featured-card titles `<h2>` → `<h3>`.** Screen-reader users can now navigate by heading; hierarchy is h1 (name) → h2 (sections) → h3 (items). Visual styling unchanged (`.section-marker` got an explicit `font-weight: 400` so the h2 default bold doesn't apply).
- **`--obsidian-muted` bumped `#7C789A` → `#918DAE` everywhere** (nav monogram, footer text on the dark obsidian background). The old value was ~4.0:1 contrast, below WCAG AA for small text; the new one passes while staying in the same lavender family.
- **Homepage nav at ≤480px: reduced link font-size/letter-spacing/gap** so all six links fit without horizontal overflow.

## Content accuracy
- **Thesis intro: "seven vortices in a Abrikosov-like lattice" → "three vortex cores in a triangular arrangement — the seed of an Abrikosov-like lattice…".** The hero SVG shows three cores, not seven, and there is no phase colour-coding in it; the text now describes the image that's actually there (and fixes "a Abrikosov").
- **Homepage: "other inquiries · in progress" → "more inquiries".** Every item in that list is marked "Complete"; the header contradicted its own content.
- **Homepage photo alt: "Ninaad Adhvaryu" → "Portrait of Ninaad Adhvaryu".**

## Code quality
- **Homepage: removed ~250 lines of dead CSS** (`.filter-bar`, `.filter-btn`, `.index-list`, `.index-entry`, all `.entry-*` / `.note-*` rules, staggered `.index-entry` animations, and their responsive rules) — these referred to an accordion index that no longer exists in the HTML.
- **Homepage: removed the entire `<script>` block.** Both functions (`toggleEntry`, filter-bar handler) targeted the removed accordion; the page now ships zero JS.
- **`style.css`: added shared secondary tokens** (`--cream-dark`, `--cream-card`, `--ink-muted`, `--teal-pale`, `--teal-rule`, `--obsidian-*`). Essay pages were using `var(--teal-rule)` without any definition in scope (silently falling back); now there's a guaranteed fallback, and future pages can stop redeclaring these.

## Verification round (fixes found by fresh-context audits + automated checks)
- **`double-pendulum`: fixed dead back-link `../../inquiries.html` → `../../index.html#inquiries`.** The target file never existed.
- **`cricket-wickets` & `teaching-emergence`: escaped straight double quotes inside `og:title`/`og:description` content attributes (`&quot;`).** Unescaped quotes terminated the attribute early — social scrapers would have read a truncated title.
- **`dipolar-quantum-gases` & `double-pendulum`: removed `outline: none` from range sliders.** It suppressed keyboard focus indicators on the interactive controls; the global `:focus-visible` style now applies.
- **All 17 pages: added a ≤480px rule** — gutter 1.5rem → 1rem, nav links become horizontally scrollable (hidden scrollbar) with `white-space: nowrap`. The six-link nav previously overflowed the viewport on phones ≤480px wide.
- **Reverted my re-encode of three `vendor-network` figures** (j_sweep, scatter_validation, spatial_population): re-compression made them *larger* (e.g. 157 KB → 218 KB), so the originals were restored byte-for-byte and their `width`/`height` attributes corrected to the true dimensions.
- **Accepted as-is, with reasons:** homepage featured-card heroes keep `loading="lazy"` (they are below the fold — the opening section fills the first viewport); p5.js loads synchronously in `<head>` on the two interactive essays (the inline sketches reference p5 globals at parse time, so `defer` would break them); MathJax was already `async` everywhere.

## Not done (deliberately) / recommended next
- **CSS consolidation:** each essay page still carries ~100 lines of duplicated inline nav/body/template CSS. It works and is self-contained; merging into `style.css` across 16 pages is the highest-risk refactor on the list, so it's left as a follow-up.
- **COWORK_INSTRUCTIONS.md token table is stale** (documents a dark theme — obsidian background, cream text — that doesn't match `style.css`). Worth updating so future Cowork sessions don't design to the wrong palette. Left alone since it's your process doc.
- **`og:image` for essay pages:** hero images are SVG, which most social scrapers won't render. If unfurl images matter, export a PNG social card per essay (or one generic card) and reference it.
- **Possible new essays** (from recent work visible in your chat history): the Schelling model project ("F5 - Schelling Prompt"), the daily physics puzzle site / Connections-style puzzle game, and the workflow/agent-infrastructure work from "F5 - Workflow" (Brain_OS, boot-file protocol) — the last would sit well in *Building* alongside Athena Intelligence.

## How to revert
Every change above is in your working tree and uncommitted (I made no git operations). `git diff` shows exactly what changed; `git checkout -- <file>` reverts any file you don't like. The three mangrove PNGs and `photo.jpg` are binary — revert those the same way if you prefer the originals.

## New essays — 2026-07-05
Five new explainer essays built from five completed student-project papers (anonymised — no student names, no institution mentions in essay bodies) and wired into the homepage. Papers pulled from Google Drive via the connector; `EXPLAINER_ESSAY_PROMPT.md` (voice) and `_sonnet-handoff/SKILL.md` (hero house-style) governed the work. Nothing else on the homepage or in other essays was touched.

- **`sudoku-entropy/` — "Can a single number tell you how hard a Sudoku is?"** Type C, ~1479 words. `_drafts/draft-01.md`, `site/hero.svg` (two Sudoku grids draining of entropy) + `site/index.html`, `_source/` extract. Pivot: the human-vs-machine entropy gap is mostly a measurement artifact; only the difficulty-grading survives.
- **`black-hole-rivers/` — "What if space flows like a river past the event horizon?"** Type A, ~1314 words. Hero = inflow streamlines into a horizon; inline light-cone-tilt diagram. Pivot: the GPS residual between the two pipelines is exactly the predictable coordinate-time term (r = 1.000), not an error.
- **`galaxy-superstructures/` — "How real is the largest structure in the universe?"** Type A/B, ~1289 words. Hero = a friends-of-friends filament; inline sparsity two-panel. Pivot: the top method collapses to F1 = 0 under mild subsampling (a percolation cliff); adaptive HDBSCAN survives.
- **`fractals/` — "How many fractal dimensions does a coastline have?"** Type C, ~1218 words. Hero = a box-counted fractal coastline; inline divider two-panel. Pivot: the two estimators disagree and box-counting drifts with resolution — the "scale-free" dimension isn't.
- **`geoid-harmonics/` — "How many numbers does it take to store the shape of gravity?"** Type A/B, ~1298 words. Hero = a geoid undulation contour map; inline error-decay schematic. Pivot: gravity needs ~37,249 coefficients where the core field needs 49, yet a shallow crustal field compresses worse than gravity — compressibility tracks source depth.
- **Homepage `index.html`: appended 5 `<li class="secondary-item">` to `<ul class="secondary-list">` (7 → 12).** Secondary list only — no featured cards added, no featured-grid re-curation, no renumbering; both `.athena-framing` lines untouched. `git diff index.html` shows only the 5 insertions.
- **Figures: built original house-style SVGs (1 hero + 1 inline explanatory diagram per essay) instead of embedding paper figures.** The Drive source binaries were too large to extract through the connector economically; each draft's Editor's Note flags the specific real paper figures worth dropping into `site/figures/` (e.g. Fig 4 / Fig 13 / Fig 2). No fabricated data plots — inline diagrams are schematic concept-builders only.
- **Pages built to the post-2026-07-03 polish standard** (`markov-raga` as reference): full OG/canonical/favicon meta with `&quot;`-escaped quotes, skip link, `<nav aria-label="Main">`, `<main id="main">`, ≤480px nav rule, `decoding="async"` hero. Verified: each page parses; exactly one `<main>`/`<nav>`/`<h1>`; every hero SVG has zero `<text>` elements; drafts 800–1500 words; all local hrefs/srcs resolve.

## New essays — Wave 2 — 2026-07-07
Five more explainer essays from the ESSAY_ROADMAP Tier-A queue (anonymised; no student names or institution mentions in essay bodies), same pipeline and standards as the 2026-07-05 wave. Method-diverse by design (no repeated core method within the wave). Homepage kept as a single flat secondary list per Ninaad's call; domain-header grouping deferred.

- **`prime-gaps/` — "Do prime gaps have favorite sizes?"** Type C, ~1290 words. Hero = a prime-gap frequency "comb" with jumping-champion spikes at 6 and 30; inline two-panel (flat r = 0.05 scatter vs the aligned peaks). Pivot: a near-zero correlation is blind to the real local structure — the statistic averages the pattern away.
- **`chaos-encryption/` — "Does more chaos make a better cipher?"** Type B, ~1288 words. Hero = a uniform byte-cloud vs a banded one; inline = the real Hénon attractor collapsing to a finite-precision loop. Pivot: the 2D Hénon map was predicted best and came last; the plain Tent map won — Hénon undone by finite-precision short cycles.
- **`airgap-acoustics/` — "Can a computer leak secrets through its fan?"** Type C, ~1290 words. Hero = a fan-tone spectrogram dissolving into noise; inline = error-vs-distance (binary vs soft). Pivot: the covert channel decodes up close but fades with distance/noise, and the soft-vs-binary gap shows it degrades gracefully, not cliffing.
- **`chaine-turns/` — "Does a faster spin make a better turn?"** Type C, ~1317 words. Hero = the periodic angular-velocity waveform of turning; inline = the mean-vs-variance dot plot. Pivot: rosin wins the mean but is the least repeatable; Marley (the pro standard) wins on consistency — the variance is the honest signal. (Single-subject study; heavy caveats surfaced in-essay.)
- **`floatovoltaics/` — "Can floating solar power a city and save its water?"** Type A, ~1259 words. Hero = an FPV array on a stylised reservoir; inline = the energy–water scatter with the efficiency ray. Pivot: once a project does two things, the chosen metric picks the winner — gross energy → Shasta, energy-per-water → Berryessa, delivered energy → reshuffle.
- **Homepage `index.html`: appended 5 more `<li class="secondary-item">` to `<ul class="secondary-list">` (12 → 17).** Secondary list only — no featured cards, no featured-grid change, no renumbering; both `.athena-framing` lines untouched. The only new homepage diff is the 5 insertions.
- **Figures:** same approach as Wave 1 — 1 original house-style hero SVG + 1 inline explanatory diagram per essay; real paper figures flagged in each Editor's Note for `site/figures/` (no fabricated data plots). Verified across all five: parse OK, one `<main>`/`<nav>`/`<h1>`, heroes text-free and valid XML, drafts 1259–1317 words, all local refs resolve.
