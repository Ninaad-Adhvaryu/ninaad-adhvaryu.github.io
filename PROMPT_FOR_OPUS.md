# Add five new essays to Project Essays — execution prompt

You are working in `~/Documents/Project Essays` (mount it if it isn't). It is Ninaad Adhvaryu's personal site (ninaad-adhvaryu.github.io), a git repo served by GitHub Pages. Your job: produce five new explainer essays from five completed research papers, each with a hero SVG and an essay page, then wire them into the homepage's secondary list. Work end to end, but stop for review where this prompt says to.

## Read these first, in order — do not draft anything before finishing all four
1. `COWORK_INSTRUCTIONS.md` — folder conventions and hard boundaries.
2. `EXPLAINER_ESSAY_PROMPT.md` — the essay-writing system prompt. This governs voice, structure, essay types A–D, figure discipline, and the banned-move list. It is read-only; never edit it.
3. `_sonnet-handoff/SKILL.md` + the files in `_sonnet-handoff/templates/` — the build pipeline (draft → hero → page → wiring) and hero-SVG house rules. Note: its `/sessions/focused-bold-cray/...` paths are stale; use the real folder. Two of its instructions are overridden below (§Overrides).
4. Two calibration reads: `markov-raga/site/index.html` (canonical current page structure, including the modern `<head>`, skip link, `<main>`, and 480px nav block) and `forest-fires/_drafts/draft-01.md` or `cricket-wickets/_drafts/draft-01.md` (voice).

## The slate (approved by Ninaad)
Folder scaffolding (`_source/`, `_drafts/`, `site/`) already exists for all five slugs.

| Slug | Working title (question form; final title from your read of the paper) | Primary source (Google Drive) | Drive fileId |
|---|---|---|---|
| `sudoku-entropy` | What does Shannon entropy see in a Sudoku grid that a solver doesn't? | "Shannon Entropy as a Lens for Human-Computer Sudoku Analysis.pdf" | `1rSsfNvOpyLi6fldGiES_HB6weXDWBj7k` |
| `black-hole-rivers` | What if space flows like a river past the event horizon? | "The river model of black holes - Revised - Online.docx" | `1m3ovA1QwuRF-mxXSUzJHPh4p8qkknpbN` |
| `galaxy-superstructures` | How do you decide whether galaxies cluster into something larger? | "MANUSCRIPT_IJAP.pdf" | `17EYLq-W3lY__H3k7vE_DD871kD5YfHOf` |
| `fractals` | (from the paper — fractal geometry study, IJSR revised) | "Dubey_Neer_IJSR_revised" (Google Doc — export as docx) | `1HXcq27Tgw8I6d-T9T9VvQbnnNxh6ACMdpOIw_B2k2bw` |
| `geoid-harmonics` | Why isn't the Earth's gravity field a sphere? (geoid / spherical harmonics) | "Geoid.pdf" | `1pbAVRvtu2y3FcuJF2ww_nav2Pra3eFqt` |

## Step 0 — Source staging (before anything else)
Check each `<slug>/_source/` for the paper file. If missing, ask Ninaad to drag the five files above from Drive into the matching `_source/` folders (give him the list with Drive links), OR — if a Google Drive connector is available — pull the *text* with `read_file_content(fileId)` and save it as `<slug>/_source/<slug>-extracted.txt`. Binary figures: prefer extracting from the local PDF/docx per SKILL.md §3 (`pdfimages` / unzip `word/media/*`); only ask Ninaad for figure files if extraction fails. Do not proceed on a paper you haven't read in full.

Optional texture: if `mcp__session_info__read_transcript` is available, the local sessions "Jai Goel project review" (sudoku-entropy) and "Aaryan K - NHSJS Review Apr 27" (black-hole-rivers) contain project history worth mining per EXPLAINER_ESSAY_PROMPT Part 4.2. Skip silently if unavailable.

## Per-essay workflow (repeat ×5, in the table's order)
1. Read the paper end-to-end. Identify the narrative pivot (SKILL.md §4 rule 3) and pick essay Type A–D.
2. Write `<slug>/_drafts/draft-01.md` — frontmatter per SKILL.md §4, 800–1500 words, Editor's Note at the bottom (draft only, never published).
3. Extract needed paper figures to `<slug>/site/figures/` (only ones the essay actually references; 3–6).
4. Build `<slug>/site/hero.svg` — SKILL.md §5 hard rules: zero `<text>` elements, no dark panels, teal-dominant, fills the 1200×675 canvas, legible at 520px.
5. Build `<slug>/site/index.html` from `_sonnet-handoff/templates/essay-page.html`, then bring it up to current site standards (§Page standards below). Body prose = the draft, converted to HTML.
6. Present to Ninaad: draft path, hero path, one-line thesis. **Collect all five reviews before any wiring.** Revise what he flags.

## Review stop (hard)
After all five drafts + heroes + pages exist: show a compact summary (per essay: title, type, word count, pivot, figure count) and ask which to wire. **Do not touch the root `index.html` until he answers.**

## Wiring (approved essays only)
Homepage placement is **secondary list only** — do not add featured cards, do not re-curate the featured grid, do not renumber anything. In root `index.html`, append one `<li class="secondary-item">` per essay inside `<ul class="secondary-list">`, exactly matching the existing entries' structure: `secondary-domain` (e.g. "Mathematics · Information Theory"), `secondary-title` (the question-form title), `href="<slug>/site/index.html"`, `secondary-status` = "Complete". Keep the `.athena-framing` line untouched.

## Page standards (new pages must match the post-July-2026 polish; markov-raga is the reference)
- `<head>`: title "«Essay Title» — Ninaad Adhvaryu"; meta description; canonical `https://ninaad-adhvaryu.github.io/<slug>/site/`; og:type article, og:title/og:description/og:url; twitter:card summary; theme-color `#1C1A2E`; `<link rel="icon" href="../../favicon.svg" type="image/svg+xml">`; preconnect + Google Fonts link (copy from markov-raga) **before** `../../style.css`. Escape any `"` inside meta content attributes as `&quot;`.
- Body: `<a class="skip-link" href="#main">Skip to content</a>`, `<nav aria-label="Main">`, content in `<main id="main">` (closed before any footer).
- Every figure `<img>`: real `width`/`height` attributes, `loading="lazy" decoding="async"` (hero image: no lazy, just `decoding="async"`), alt text that describes what the figure shows.
- Include the ≤480px media block from markov-raga (gutter 1rem; `.nav-links` overflow-x auto etc.).
- Compress extracted figure PNGs: resize to ≤1600px wide, `optimize=True`; if a re-save comes out larger than the original, keep the original. Target <200KB per figure where quality allows.

## Overrides & boundaries (these win over anything else you read)
- **Students stay anonymous.** No student names anywhere in essays, pages, or homepage. "A student I was working with" is the pattern (EXPLAINER prompt Part 2.3). Ignore SKILL.md's `{{COLLABORATOR}}` slot — set it to "—" / omit the row. No "Athena", "Pangea", or institutional mentions inside essay bodies.
- **Do not modify** `EXPLAINER_ESSAY_PROMPT.md`, `style.css`, other essays' folders, anything in other projects' `_source`/`_drafts`, or `IMPROVEMENTS.md`'s existing entries.
- **No git operations.** Ninaad commits himself.
- SKILL.md's "Inquiry NN" span in the card template is stale — current featured cards don't use it, and you're not adding cards anyway.
- Log every change you make as one-line entries appended to `IMPROVEMENTS.md` under a new "## New essays — <date>" heading.

## Final verification (after wiring)
Run per page and on root `index.html`: HTML parses (SKILL.md §8 snippet); exactly one `<main>`, `<nav>`, `<h1>`; all local hrefs/srcs resolve; every og:/twitter: meta line is a well-formed single-quoted-free attribute; figure width/height match actual file dimensions (PIL); hero.svg has zero `<text>` elements; draft word count in range (`wc -w`); homepage secondary list count went from 7 to 7+N with no other homepage diffs (`git diff index.html` should show only the list insertions). Report anything that fails plainly, with evidence — do not report unverified work as done.
