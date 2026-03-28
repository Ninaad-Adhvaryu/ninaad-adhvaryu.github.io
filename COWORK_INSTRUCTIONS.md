# COWORK INSTRUCTIONS
# Project Essays — Ninaad Adhvaryu
# Last updated: 2026-03-28

This document is the authoritative reference for how Claude should work
within this project. Read it at the start of any Cowork session.

---

## What this project is

A personal science website published via GitHub Pages. The root folder
(`~/Documents/Project Essays/`) IS the repository — everything here is
live at ninaad.github.io (or equivalent).

Essays document research projects — computational, experimental, and
mathematical — that Ninaad has developed, often in conversation with
students, colleagues, and peers. The audience is scientifically literate
but not specialist.

---

## Folder structure

```
Project Essays/           ← repo root, published to GitHub Pages
│
├── index.html            ← homepage listing all essays
├── style.css             ← shared stylesheet (design tokens, components)
├── COWORK_INSTRUCTIONS.md ← this file
├── EXPLAINER_ESSAY_PROMPT.md  ← system prompt for writing essays (read-only)
│
└── double-pendulum/
    ├── _source/          ← raw materials: paper, figures, chat exports, prompt
    ├── _drafts/          ← essay iterations — NEVER published, never modify unless asked
    └── site/             ← PUBLISHED FILES ONLY (index.html, figures/, scripts/)
```

Each essay project follows this exact three-folder pattern.

---

## The essay prompt

`EXPLAINER_ESSAY_PROMPT.md` lives at the repo root and is used for every
essay on this site. It defines:

- Ninaad's voice and the alternating personal/technical register
- Narrative structure and essay types (A / B / C / D)
- Visual strategy: paper figures, explanatory diagrams, interactives
- What not to do (no bullet points in prose, no "novel", no named collaborators)

**Never modify this file.** If Ninaad wants to revise the prompt, he will
do so directly.

---

## The _source / _drafts / site convention

### `_source/`
Raw project materials. Read-only unless Ninaad explicitly says otherwise.
Contents typically include:
- The research paper (PDF or DOCX)
- Figure PNGs with captions
- AI chat export (markdown)
- A brief or notes from Ninaad

### `_drafts/`
Essay iterations produced by Claude or Ninaad during the writing process.
Name files chronologically: `draft-01.md`, `draft-02.md`, etc.
Never publish anything from `_drafts/`. Never delete drafts without asking.

### `site/`
**Published files only.** This folder is what GitHub Pages serves.
Typical contents:
- `index.html` — the essay HTML
- `figures/` — figure images referenced in the essay
- Any embedded JS/CSS specific to this essay

Only copy files to `site/` when Ninaad says the essay is ready to publish.

---

## How to add a new essay

1. Create the three folders:
   ```
   new-essay-name/_source/
   new-essay-name/_drafts/
   new-essay-name/site/
   ```
2. Add a `.gitkeep` file to each folder so git tracks them when empty.
3. Add a new `<li>` entry to the `<ul class="essay-list">` in `index.html`.
   Match the existing entry's HTML structure exactly:
   ```html
   <li class="essay-list__item">
     <a href="new-essay-name/site/">
       <p class="essay-meta">Category &middot; Subcategory</p>
       <h2 class="essay-title">The essay title as a question or surprising claim</h2>
       <p class="essay-lede">One-sentence description in italic. What is the essay about?</p>
     </a>
   </li>
   ```
4. Do not create `EXPLAINER_ESSAY_PROMPT.md` again — it lives at the root
   and is reused for every essay.

---

## Publishing an essay

When Ninaad says "publish" or "the essay is ready":
1. Copy the final HTML file from `_drafts/` to `site/index.html`.
2. Copy any figures to `site/figures/`.
3. Verify all asset paths in the HTML are relative to `site/`.
4. Check that `index.html` at the root links correctly to `essay-name/site/`.
5. Do NOT commit or push — Ninaad handles git.

---

## Style conventions

All HTML files use `style.css` from the repo root via a relative path.
The design tokens defined there are:

| Token              | Value      | Use                          |
|--------------------|------------|------------------------------|
| `--color-obsidian` | `#0f0f0f`  | Page background              |
| `--color-ink`      | `#1a1a1a`  | Card / panel backgrounds     |
| `--color-cream`    | `#f0ead8`  | Primary text                 |
| `--color-cream-dim`| `#c8c0aa`  | Secondary text, captions     |
| `--color-teal`     | `#4db8a0`  | Accent, links, labels        |
| `--font-mono`      | JetBrains Mono | Nav, labels, captions    |
| `--font-serif`     | Source Serif 4 | All body text, headings  |

Essay HTML files should reference the stylesheet as:
```html
<link rel="stylesheet" href="../../style.css" />
```
(two levels up from `essay-name/site/index.html`)

---

## What Claude should never do

- Modify anything in `_source/` or `_drafts/` unless explicitly asked.
- Write to `site/` before Ninaad says the essay is ready to publish.
- Modify `EXPLAINER_ESSAY_PROMPT.md`.
- Commit or push to git (Ninaad handles all git operations).
- Create a README.md or any documentation file that wasn't asked for.
- Add an essay to `index.html` without being asked to.
