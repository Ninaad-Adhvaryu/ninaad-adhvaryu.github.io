---
name: featured-essay-builder
description: Turn a source paper (PDF, docx, or conversation) into a new featured essay on Ninaad's personal site. Produces a draft-01.md in the essay's voice, a stylised hero.svg matching house style, and a wiring patch for the Mockup C grid on index.html. STOPS for user review before wiring. Trigger when the user says "add a new essay", "turn this paper into an essay", "draft an essay from this", or uploads a PDF/docx of a paper to the Project Essays folder.
---

# Featured Essay Builder — Sonnet handoff skill

This skill encodes everything a Sonnet session needs to take a new paper from raw source to a finished card on Ninaad Adhvaryu's personal site at `/sessions/focused-bold-cray/mnt/Project Essays/`. It replaces the ad-hoc reasoning Opus used in the initial build and gives Sonnet a repeatable, semi-automated workflow.

The guiding rule of this skill is: **Sonnet produces the essay and the hero image; the user reviews; only then does Sonnet wire the card into the site.** Do not skip the review stop.

---

## 1. What you are producing

For every new featured essay, three things get made, in order:

1. **`<slug>/_drafts/draft-01.md`** — a written draft of the essay in the house voice (Type A–D, 800–1500 words, image discipline). This is the artifact the user reviews and edits.
2. **`<slug>/site/hero.svg`** — a stylised 16:9 re-render of the paper's key figure in the site palette. Cream background, teal-dominant fills, no title text, no Inquiry label, no dark meta panel. This image is used in two places: as the card image on the Mockup C grid and as the splash image at the top of the essay page.
3. **`<slug>/site/index.html`** — the full essay page, styled to match the other essay sites (forest-fires, vendor-network, cricket-wickets, double-pendulum). Built from `templates/essay-page.html` with slug-specific content slotted in.

And one patch:

4. **A new `<a class="featured-card">` inserted into the `.featured-grid` block in the root `/Project Essays/index.html`**, plus a corresponding entry removed from the secondary list (or the grid re-curated if the featured set changes). This is the last thing you do, and only after user review.

---

## 2. The review stop

**After step 1 and step 2, stop and show the user:**
- The draft markdown
- The hero SVG rendered (inline if possible, or a path)
- A one-line summary of what the essay argues

Ask explicitly: *"Shall I wire this into the site, or should I revise first?"*

Do not proceed to step 3 or 4 without an affirmative response. This is the semi-automated handoff point the user asked for.

---

## 3. Input types & extraction pipeline

The user will hand you the paper in one of three forms. Extraction is the first thing to do, always.

### 3a. PDF
```bash
# Extract text
pdftotext -layout <input>.pdf <slug>.txt

# Extract embedded figures (for reference — NOT used directly as hero)
mkdir -p <slug>/site/figures
pdfimages -png <input>.pdf <slug>/site/figures/fig
```

Read `<slug>.txt` end-to-end. Identify: the research question, methods, key result, the "one thing that surprised them" (this is almost always where the essay's narrative pivot lives), and any caveat the paper itself flags.

### 3b. docx
```bash
# docx is a zip; text lives in word/document.xml
unzip -p <input>.docx word/document.xml | python3 -c "
import sys, re
txt = sys.stdin.read()
txt = re.sub(r'<[^>]+>', ' ', txt)
txt = re.sub(r'\s+', ' ', txt)
print(txt)
" > <slug>.txt
```

Images in docx live under `word/media/`. Extract with `unzip -j <input>.docx 'word/media/*' -d <slug>/site/figures/` if you want to reference them in the draft.

### 3c. Conversation only
If the user is describing the work verbally and you have no source file, ask them to paste the abstract + methods + results sections. Treat that pasted text as if it were `<slug>.txt` and proceed.

---

## 4. Voice and structure (the draft)

The essay voice across all four existing essays follows a consistent pattern. Read at least **one** of these before drafting, to calibrate register:
- `/sessions/focused-bold-cray/mnt/Project Essays/forest-fires/_drafts/draft-01.md`
- `/sessions/focused-bold-cray/mnt/Project Essays/cricket-wickets/_drafts/draft-01.md`
- `/sessions/focused-bold-cray/mnt/Project Essays/vendor-network/_drafts/draft-01.md`

### Voice rules — non-negotiable

1. **First person, lightly used.** Ninaad is present but not the subject. "I wanted to ask whether the sentence actually survives contact with ball-level data" — yes. "In this essay I will discuss..." — never.
2. **No bullet points in prose.** Lists go into natural language. The only bullets allowed are in the *Editor's Note* at the bottom.
3. **One narrative pivot per essay.** Every good essay has a moment where something *misbehaves* — a result that doesn't fit, an assumption that breaks, a dataset that disagrees with itself. Find that pivot in the source paper and build the essay around it. If the paper has no such moment, the essay should instead surface a non-obvious methodological choice and make *that* the pivot.
4. **Honest caveat at the end.** A short section (often labelled "An honest caveat that should go before any stronger claim") acknowledging observational vs. causal limits, selection effects, or what the next version of the work would need to do. Taken directly from the paper's Scope/Limitations section, lightly rewritten.
5. **Word count: 800–1500.** Cricket-wickets (~1400) and vendor-network (~1500) are on the longer end; forest-fires is ~1100.
6. **Image discipline.** Reference 3–6 figures from the paper, plus optionally one inline explanatory SVG the essay builds from scratch. Figures are wrapped in `<div class="figure-wrap">…<p class="figure-caption">…</p></div>`. Captions are italicised and do narrative work — they don't just name the figure.
7. **Editor's Note at bottom** (not for publication) flagging: figure filename mapping to verify, any promoted framing that is the writer's not the paper's, collaborator credit check, anything copied vs. paraphrased.

### Essay types (pick one in frontmatter)
- **Type A** — personal register, reflective. Opens with a story or a question, ends with a recognition.
- **Type B** — technical register, narrative. Explains a model or finding, with prose doing the structural work.
- **Type C** — hybrid (most common). Technical body with personal openings/closings. Cricket-wickets is C.
- **Type D** — short, opinionated. 600–800 words. Reserved for essays where the source paper is short.

### Draft frontmatter format
```yaml
---
SUGGESTED TITLE: <question form, like the other four>
SUGGESTED LEDE: On <the specific move the essay makes>, and on <the one thing that misbehaved>.
ESSAY TYPE: <A | B | C | D>
WORD COUNT: ~<n>
EXTENSIONS SECTION: <Yes | No>
IMAGES USED: <n paper figures, n explanatory SVGs>
---
```

The frontmatter is NOT rendered on the site. It's metadata for the user's review.

---

## 5. Hero image (SVG) — house style

A hero is a **pure visual**. It is not a figure from the paper, not a diagram, not a chart. It is one clear shape or arrangement that reads at a glance on the landing-page card (~520px wide) and still holds up as a full-width splash at the top of the essay page.

The same `hero.svg` is used in **two** places: (a) the image on the Mockup C landing-page card, and (b) the splash image at the top of the essay page, with the essay title rendered as HTML `<h1>` below it. The hero must work in both contexts without any accompanying text inside it.

### Hard rules — do not break these

1. **NO text inside the SVG.** Not a title, not an Inquiry label, not axis labels, not legend labels, not italic annotations, not footer captions. Zero `<text>` elements. If you want to label something, make the visual clearer instead.
2. **NO dark panels.** No obsidian rectangles. No meta boxes. No filled ink backgrounds.
3. **NO empty space.** The visual fills the canvas (aim for ≤80px margins on all sides). If it leaves half the canvas blank, enlarge it until it doesn't.
4. **Teal dominates.** `#2A6B6B` is the primary fill. Ink `#1A1714` is reserved for thin outlines and the occasional frame. Darker accents use teal-deep `#1A4F4F`, never obsidian.
5. **Legible at 520px without text.** If you can't tell what the shape is without a caption, the shape is wrong.

### Layout template (`templates/hero-template.svg`)

- **viewBox:** `0 0 1200 675` (16:9)
- **Background:** cream `#F7F3EE`
- **Main visual:** fills the canvas edge-to-edge with generous teal fills

### Palette (lock these tokens exactly)
```
--cream:        #F7F3EE
--ink:          #1A1714   (thin outlines only)
--ink-muted:    #6B6460   (rare — only for a subtle tick mark)
--teal:         #2A6B6B   (primary fill — dominant)
--teal-light:   #3D9090
--teal-deep:    #1A4F4F   (darker accents, "burned", dominant phase)
```
Obsidian `#1C1A2E` is reserved for the site nav and footer — **never use it in a hero SVG**.

### What the "key figure" means, by figure type

The goal is always: take the paper's central idea and convert it into one bold shape that fills the canvas.

| Paper's key figure type | Hero strategy |
|---|---|
| Phase diagram (regions on a 2D plane) | Full-canvas rectangle filled with the three phases as big teal layers of varying opacity, separated by a hard ink curve and a dashed teal soft curve. No labels. |
| KDE / heatmap on a physical plane | The physical plane (pitch, grid, map) drawn big in ink outline, filling most of the canvas; density shown as 6–8 nested teal ellipses with increasing opacity, clustered where the paper says the density peaks. |
| Percolation / network grid | Big dense grid of teal circles (12+ cols, 10+ rows) filling most of the canvas; a contiguous blob of teal-deep circles showing the cluster; optionally a sparse region on one side separated by a dashed threshold line. |
| Trajectory / chaos plot | A single large trail or two side-by-side trails filling the canvas, with the object (pendulum, orbit, particle) rendered big in ink outlines and teal bobs. Field lines in dashed ink-muted if they add texture. |
| Bar chart | Never use as-is. Recast as a shape — the largest bar becomes a block, the rest become a rhythm. |
| Time series | Never use as-is. Recast as two frames (before / after) or a single trace that fills the canvas. |

### Reference heroes (read these before drafting a new one)
- `forest-fires/site/hero.svg` — dense percolation grid with a burned cluster, sparse field on the left
- `vendor-network/site/hero.svg` — full-canvas 3-phase diagram with a dashed soft boundary
- `cricket-wickets/site/hero.svg` — vertical cricket pitch filling the canvas, KDE contours clustered in the good-length corridor
- `double-pendulum/site/hero.svg` — two side-by-side trails filling the canvas, one smooth and one chaotic

All four are text-free, meta-panel-free, and use teal-only fills. Match that bar or raise it. If the key figure in the new paper doesn't fit any of these categories cleanly, default to a "concept shape" — the essay's central object rendered large and iconic, not as a re-drawn figure.

---

## 6. Essay page (`<slug>/site/index.html`)

Copy `templates/essay-page.html` to `<slug>/site/index.html` and do a slug-wide find/replace on:

```
{{SLUG}}               → kebab-case directory name (e.g. "cricket-wickets")
{{TITLE}}              → full title
{{LEDE}}               → the subtitle line
{{DOMAIN}}             → "Sports Analytics · Spatial Statistics"
{{METHODS}}            → "Hawkeye ball-tracking · KDE · Zone-based stratification"
{{COLLABORATOR}}       → collaborator full name + school, or "—" if solo
{{YEAR}}               → "2026" (or paper year)
{{DRAFT_BODY_HTML}}    → the essay prose as HTML (paragraphs + figure-wraps)
```

The template pulls in the shared `../../style.css` (site root) and declares page-specific tokens only for hero-width overrides. Do not inline-copy style.css; link to it.

### Figure references inside the essay body
```html
<div class="figure-wrap">
  <img src="figures/<filename>.png" alt="<alt text>">
  <p class="figure-caption"><em>Caption doing narrative work, not just labelling.</em></p>
</div>
```

Paper figures go in `<slug>/site/figures/` — extract them at the same time as text (see §3). DO NOT confuse these with the hero SVG, which lives at `<slug>/site/hero.svg` and is referenced both from the root index grid card **and** from the essay page as a splash image at the top of `<slug>/site/index.html` (inside a `<figure class="essay-hero"><img src="hero.svg" alt="..."></figure>` block placed above the `<h1 class="essay-title">`).

---

## 7. Wiring into the root `index.html` grid

**Only after the user approves the draft and hero.** Open `/sessions/focused-bold-cray/mnt/Project Essays/index.html`, find the `<div class="featured-grid">` block, and:

### If replacing an existing card
Find the `<a class="featured-card">` for the essay being replaced and swap its contents.

### If adding a new card (grid still has room; ask user if >4)
Insert a new `<a class="featured-card">` block using this shape:

```html
<a class="featured-card" href="<SLUG>/site/index.html">
  <div class="featured-hero-wrap">
    <img src="<SLUG>/site/hero.svg" alt="<hero alt text>">
    <span class="featured-num">Inquiry NN</span>
  </div>
  <div class="featured-body">
    <p class="featured-domain"><DOMAIN></p>
    <h2 class="featured-title"><TITLE></h2>
    <p class="featured-lede"><LEDE></p>
    <span class="featured-read">Read full essay →</span>
  </div>
</a>
```

### Secondary list
If the new essay was previously in the `secondary-list` as "In progress", remove its `<li class="secondary-item">` block and bump any neighbours that share a row.

### Inquiry numbering
Inquiry numbers are **persistent**. They are the original order from before any essay was written. Do not renumber when promoting from secondary to featured. Look up the number by grepping the current `index.html` for the essay's title or slug.

---

## 8. Verification checklist (before stopping for review, and again after wiring)

Run through these every time:

1. `python3 -c "from html.parser import HTMLParser; ..."` on the root `index.html` to confirm it still parses (use the snippet at the end of this skill)
2. The hero SVG is valid — open it in a browser tab or view as base64. No missing closing tags, no broken `<text>` elements
3. The draft markdown is 800–1500 words (count: `wc -w <slug>/_drafts/draft-01.md`)
4. The essay references at least 3 figures and has at least one narrative pivot
5. The editor's note is present at the bottom and flags: figure filename mapping, promoted framing, collaborator credit
6. The collaborator (if any) is credited exactly as on the paper — check both the essay body and the root index card's tag metadata (if `.note-tag` or meta-row is used)
7. `.athena-framing` line in the root index is still present (Athena Education attribution)
8. No dark backgrounds leaked back into content sections — the only obsidian elements on the site should be `nav`, `footer`, and (in future) an About/Contact panel. Content cards must remain cream.

### HTML parse snippet
```python
from html.parser import HTMLParser
class P(HTMLParser):
    def __init__(self): super().__init__(); self.stack=[]; self.ok=True
    def handle_starttag(self,t,a):
        if t not in ('br','img','input','link','meta','hr','source'):
            self.stack.append(t)
    def handle_endtag(self,t):
        if self.stack and self.stack[-1]==t: self.stack.pop()
        else: self.ok=False
p = P()
p.feed(open('index.html').read())
print('OK' if p.ok and not p.stack else f'FAIL: stack={p.stack}')
```

---

## 9. What NOT to do

- Do not modify `style.css` at the site root. All page-specific styles go in the essay's own `<style>` block.
- Do not use Playfair Display. The site moved to Fraunces (with Playfair as fallback).
- Do not add new dark-background content cards. Cream-card with a teal left border is the pattern.
- Do not create bullet-point lists in prose. Natural language only.
- Do not reproduce large blocks of the source paper verbatim. Paraphrase aggressively; only quote in rare cases, always with attribution.
- Do not skip the review stop between hero/draft and wiring.
- Do not renumber existing inquiries.
- Do not write the essay in the third person. Ninaad is the narrator.

---

## 10. Files in this skill

- `SKILL.md` — this document
- `templates/draft-01.md` — frontmatter + scaffold for a new essay draft
- `templates/hero-template.svg` — the house-style hero skeleton; fill in title, key-figure paths, and meta panel values
- `templates/essay-page.html` — the full HTML shape of a single-essay page with `{{TOKENS}}` for substitution
- `templates/wiring-patch.html` — the exact `<a class="featured-card">` block to paste into the root index grid
