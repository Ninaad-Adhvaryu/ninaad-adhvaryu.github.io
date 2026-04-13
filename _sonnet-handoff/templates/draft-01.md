---
SUGGESTED TITLE: {{A question-form title, like the other four essays}}
SUGGESTED LEDE: On {{the specific move the essay makes}}, and on {{the one thing that misbehaved in the data}}.
ESSAY TYPE: {{A | B | C | D}}
WORD COUNT: ~{{n}}
EXTENSIONS SECTION: {{Yes | No}}
IMAGES USED: {{n}} paper figures, {{n}} explanatory SVGs
---

<!--
  VOICE CHECKLIST (delete before review):
  [ ] First person, lightly used — Ninaad present but not the subject
  [ ] No bullet points anywhere in prose
  [ ] One narrative pivot — something in the data misbehaved OR a non-obvious method choice
  [ ] Honest caveat at the end (causal vs observational, selection effects, scope)
  [ ] 3–6 figures wrapped in <div class="figure-wrap"><img><p class="figure-caption"><em>…</em></p></div>
  [ ] Editor's note at the bottom flagging: figure mapping, promoted framing, collaborator credit
-->

{{OPENING PARAGRAPH — the hook. A sentence that sounds like something someone would actually say, followed by the question the essay is going to ask. If Type A/C, personal register. If Type B, a tight framing of the problem domain.}}

{{BACKGROUND — one paragraph of what the dataset/system is and what the units of analysis are. Mention the columns or the variables that matter. This is where you earn the reader's trust that you actually know the data.}}

{{THE FIRST LOOK — what the naive reading of the data shows. This is usually the result the coaches/theorists would predict. Include one figure here, referenced as follows:}}

<div class="figure-wrap">
  <img src="figures/fig1.png" alt="{{descriptive alt}}">
  <p class="figure-caption"><em>{{Caption that does narrative work — what the figure shows AND why it matters AND what to notice. Not just "Figure 1: Distribution of X."}}</em></p>
</div>

{{THE PIVOT — the moment something misbehaves. "But the moment you collapse the plane into bar chart form, something misbehaves." "What I didn't expect was…" "The dataset disagreed with itself." This is the essay's structural spine.}}

<div class="figure-wrap">
  <img src="figures/fig2.png" alt="{{alt}}">
  <p class="figure-caption"><em>{{Caption that introduces the anomaly.}}</em></p>
</div>

{{DIAGNOSIS — two or three paragraphs unpacking why the anomaly happens. Usually: pooling artifact, selection effect, instrument limit, definition slippage. Name the mechanism explicitly.}}

{{THE STRATIFIED VIEW — how the picture changes once the confounding is removed. The pivot dissolves and the real pattern becomes legible.}}

<div class="figure-wrap">
  <img src="figures/fig3.png" alt="{{alt}}">
  <p class="figure-caption"><em>{{Caption showing the resolved picture.}}</em></p>
</div>

{{OPTIONAL: A second finding the paper flags that deserves a short paragraph. For example, "There is a second, related finding that seems worth flagging."}}

{{CLOSING — the overall shape of what was learned. What survived, what didn't, and what is now structural vs. what is now an artifact. This paragraph should make the reader feel like they've been through something.}}

## An honest caveat that should go before any stronger claim

{{Observational vs causal framing. Selection effects. Scope limits. What the next version of the analysis would need to do to turn this into a rigorous claim. Paraphrased directly from the paper's Scope and Limitations section.}}

---

## EDITOR'S NOTE (not for publication)

- Figure filename mapping (`fig1`, `fig2`, `fig3`) was inferred from {{source}}; spot-check against {{Figures 1, 3, 5 in the paper}} before publication
- The "{{pivot framing}}" framing is mine and is *supported by* but not explicitly written as a narrative pivot in the original paper — the paper flags {{mechanism}} as the candidate explanation in the Discussion
- Collaborator ({{Name}}) is credited per the house style rule; check that Ninaad is OK with the framing of their role in the opening paragraph
- Any inline explanatory SVG is an original diagram; cutoffs/values come directly from {{paper section}}
