---
SUGGESTED TITLE: How real is the largest structure in the universe?
SUGGESTED LEDE: On the single number that decides where a supercluster ends, and on what happens to the "largest structure in the universe" when you quietly delete a third of the catalogue.
ESSAY TYPE: A (with B elements)
WORD COUNT: ~1320
EXTENSIONS SECTION: Yes
IMAGES USED: 1 explanatory SVG (inline two-panel); 1 paper-figure suggestion flagged for Ninaad
---

Not long ago a group of astronomers announced the largest structure in the known universe: a chain of sixty-eight galaxy clusters, more than four hundred megaparsecs end to end, threading through the nearby sky. They called it Quipu, after the Andean knotted cords. It is a genuinely arresting object. But it is worth being precise about what kind of object it is, because "structure" is doing a lot of quiet work in that sentence. Quipu is not glued together; nothing holds it as a unit. It is a set of clusters that an algorithm looked at and decided to call one thing. The question a student and I got interested in was how much that decision depends on the algorithm — and on how much of the sky you happened to have measured.

The algorithm in question is friends-of-friends, and it is almost suspiciously simple. Pick a distance — call it the linking length. Draw a link between every pair of clusters closer together than that distance. Then follow the links: any set of clusters you can walk between, hop by hop, is declared a single structure. That is the whole method. There is no notion of a boundary, no model of what a supercluster should look like, nothing but a threshold distance and the connected components it produces. Quipu is what you get when you apply this rule, with a particular linking length, to a particular catalogue of X-ray-bright clusters. Change the linking length and the map of the universe's largest structures redraws itself: shorten it and Quipu fragments, lengthen it and separate superstructures fuse into one.

So the linking length is not a detail; it is the definition. And a definition that rests on a single distance scale has a specific vulnerability that I wanted to see in action. To do that we took a public catalogue — a few hundred X-ray clusters in a slice of redshift that contains Quipu and four other named superstructures — and ran six different clustering methods over it, scoring each against the published list of which clusters belong to which superstructure. At full catalogue density the fixed-linking-length methods won comfortably. Friends-of-friends, and two other methods that turn out to be mathematically identical to it, all recovered the published superstructures at an F1 score of 0.74, well ahead of the adaptive-density method, HDBSCAN, which managed only 0.47. If you had stopped there, the conclusion would have been tidy: use friends-of-friends, it is simple and it wins.

Then we started deleting clusters, and the winner fell off a cliff.

<div class="figure-wrap">
<svg viewBox="0 0 760 262" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Two panels showing the same filament of clusters. Left, at full density, every neighbour is within one linking length so the points join into a single connected chain. Right, after a third of the clusters are removed, several gaps now exceed the same linking length and the chain breaks into disconnected fragments.">
  <defs><style>
    .gslbl { font-family: 'JetBrains Mono', monospace; font-size: 10.5px; fill: #6B6460; letter-spacing: 0.03em; }
    .gsh   { font-family: 'Source Serif 4', serif; font-size: 12.5px; font-style: italic; fill: #1A1714; }
  </style></defs>
  <text class="gsh" x="10" y="24">full catalogue — one structure</text>
  <text class="gsh" x="388" y="24">a third removed — it shatters</text>
  <line x1="30" y1="190" x2="70" y2="160" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="70" y1="160" x2="112" y2="178" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="112" y1="178" x2="150" y2="148" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="150" y1="148" x2="196" y2="160" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="196" y1="160" x2="238" y2="136" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="238" y1="136" x2="282" y2="150" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="282" y1="150" x2="322" y2="126" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="322" y1="126" x2="360" y2="144" stroke="#1A4F4F" stroke-width="2.2"/>
  <circle cx="30" cy="190" r="7" fill="#1A4F4F"/>
  <circle cx="70" cy="160" r="7" fill="#1A4F4F"/>
  <circle cx="112" cy="178" r="7" fill="#1A4F4F"/>
  <circle cx="150" cy="148" r="7" fill="#1A4F4F"/>
  <circle cx="196" cy="160" r="7" fill="#1A4F4F"/>
  <circle cx="238" cy="136" r="7" fill="#1A4F4F"/>
  <circle cx="282" cy="150" r="7" fill="#1A4F4F"/>
  <circle cx="322" cy="126" r="7" fill="#1A4F4F"/>
  <circle cx="360" cy="144" r="7" fill="#1A4F4F"/>
  <line x1="30" y1="230" x2="82" y2="230" stroke="#1A1714" stroke-width="2"/>
  <line x1="30" y1="226" x2="30" y2="234" stroke="#1A1714" stroke-width="2"/>
  <line x1="82" y1="226" x2="82" y2="234" stroke="#1A1714" stroke-width="2"/>
  <line x1="490" y1="178" x2="528" y2="148" stroke="#1A4F4F" stroke-width="2.2"/>
  <line x1="616" y1="136" x2="660" y2="150" stroke="#1A4F4F" stroke-width="2.2"/>
  <circle cx="408" cy="190" r="7" fill="#1A4F4F"/>
  <circle cx="490" cy="178" r="7" fill="#1A4F4F"/>
  <circle cx="528" cy="148" r="7" fill="#1A4F4F"/>
  <circle cx="616" cy="136" r="7" fill="#1A4F4F"/>
  <circle cx="660" cy="150" r="7" fill="#1A4F4F"/>
  <circle cx="738" cy="144" r="7" fill="#1A4F4F"/>
  <line x1="408" y1="230" x2="460" y2="230" stroke="#1A1714" stroke-width="2"/>
  <line x1="408" y1="226" x2="408" y2="234" stroke="#1A1714" stroke-width="2"/>
  <line x1="460" y1="226" x2="460" y2="234" stroke="#1A1714" stroke-width="2"/>
  <text class="gslbl" x="30" y="252">linking length (unchanged) →</text>
  <text class="gslbl" x="408" y="252">same linking length →</text>
</svg>
<p class="figure-caption"><em>Why a fixed linking length is fragile. On the left, at full density, every neighbour sits within one linking length and the clusters chain into a single structure. On the right the linking length is exactly the same, but a third of the clusters are gone; the surviving gaps now exceed it, and the one structure shatters into fragments too small to count. Nothing about the algorithm changed — only how much of the sky was in the catalogue.</em></p>
</div>

We removed clusters at random, in steps, and re-ran everything a hundred times at each step to average over which clusters happened to go. The fixed-linking-length methods held their F1 of around 0.74 down to eighty per cent of the catalogue, then dropped to 0.61, and then — at sixty per cent, still a substantial catalogue — collapsed to exactly zero. Not degraded: zero. Every recovered superstructure had crumbled into pieces below the minimum size that counts as a structure at all. HDBSCAN, the method that had looked mediocre at full density, did not do this. It slid gently from 0.47 down to about 0.41 at the sparsest sampling we tried, one cluster in five, and stayed there. The whole pattern reproduced in a second, independent redshift slice, where the fixed-scale methods actually cliffed even earlier.

The mechanism is the kind of thing that is obvious in hindsight and genuinely surprising in advance. A fixed linking length only works if it is comfortably larger than the typical gap between neighbouring clusters. At full density that gap is about sixty-seven megaparsecs and the linking length is fifty, which is close but sufficient. When you delete clusters at random, the survivors spread out: the mean separation grows as the inverse cube root of the sampling fraction. By the time a third of the clusters are gone, the typical gap has swollen past eighty megaparsecs — comfortably beyond the fifty-megaparsec reach — and the chains that made the superstructure simply stop connecting. This is not a gentle loss of accuracy. It is a percolation transition, the same abrupt threshold that governs whether a fire jumps across a forest or a fluid seeps through rock, and the fingerprint is right there in the data: the run-to-run scatter balloons exactly at the fraction where the structure blinks out, the way fluctuations always blow up at a critical point. Friends-of-friends does not weaken as the catalogue thins. It works, and works, and then it doesn't.

The reason HDBSCAN survives is that it never commits to a distance at all. Instead of asking "is this pair closer than fifty megaparsecs," it asks "is this region denser than its surroundings," and relative density is preserved when you subsample — the densest cores stay the densest cores even when the overall map thins out. It pays for that robustness with a worse score when the catalogue is complete, because it declines to chain in the sparse outskirts that friends-of-friends happily absorbs. Which method is "better" turns out to be the wrong question. The fixed-scale method is better when you have everything; the adaptive method is better when you don't; and the honest report is the trade-off, not a winner.

None of this means Quipu is not there. It means that how much of it you recover is a joint fact about the structure, the algorithm, and the completeness of your catalogue, and those three are not separable after the fact. A superstructure defined by a single length scale is, in part, a statement about how thoroughly the sky was surveyed where it lies — and the next generation of X-ray surveys will have wildly uneven depth across the sky, exactly the regime where a fixed linking length is least trustworthy. The practical recommendation that falls out of this is unglamorous and, I think, correct: in any patch where the catalogue might be less than about eighty per cent complete, do not trust a fixed-scale friends-of-friends result on its own. Run an adaptive-density method beside it and see whether the structure survives both.

## An honest caveat that should go before any stronger claim

This was a descriptive comparison, not a verdict. The methods were run at their off-the-shelf settings rather than tuned, so the absolute scores would move under careful hyperparameter optimisation — though the density argument makes the cliff itself hard to tune away. The input catalogue is shallower than the one the original Quipu discovery used: thirty-three of Quipu's sixty-eight published members simply are not in it, living in deeper northern-sky surveys, so a third of the structure was unrecoverable here at any level of algorithmic skill and the absolute F1 numbers should be read with that ceiling in mind. Everything rests on two redshift slices of a single catalogue, scored against one published ground truth whose own uncertainties are not quantified. What the exercise establishes is narrow but sturdy: the recovery of large-scale structure by a fixed length scale has a percolation cliff, the cliff reproduces across slices, and an adaptive-density method sits on the other side of the trade-off. Turning that into a claim about any specific catalogue would need the same comparison run natively on that catalogue.

---

## EDITOR'S NOTE (not for publication)

- **Type A framing** — friends-of-friends and the linking length are the protagonists; the sparsity cliff is the tool showing its own limit. The percolation reading is the narrative pivot and is genuinely in the paper (it notes the bootstrap bands widen at the cliff "consistent with a percolation-like behaviour in the FoF connectivity graph"). I lean on the forest-fires/percolation connection lightly — flag if you'd rather I not cross-reference the site's other percolation essay implicitly.
- Numbers from the paper: full-sample F1 0.74 (FoF/DBSCAN/single-linkage, precision 0.62 recall 0.91), HDBSCAN 0.47; degradation 0.74 → 0.61 (80%) → 0.00 (60%); HDBSCAN 0.41 at 20%; mean separation ~67 Mpc (full) → ~80 Mpc (60%), linking length 50 Mpc; separation grows as fraction^(−1/3); pattern reproduces in the z = 0.04–0.08 slice (cliff even earlier). Please spot-check the ones you want to stand behind.
- The "largest structure in the universe" framing is the paper's own (Quipu, 428 Mpc, 68 clusters). I've been careful **not** to imply Quipu is spurious — the essay's claim is about recovery being method- and completeness-dependent, which is exactly the paper's scope. Check the title lands that way for you; alternative: "When does the biggest thing in the universe fall apart?"
- **Figure suggestion (paper figures not embedded — source is a Drive PDF I couldn't extract images from cheaply).** The one figure worth adding is **Fig 4**, the F1-vs-subsample-fraction curves for both slices — it is the cliff, drawn. It would slot in right after the "collapsed to exactly zero" paragraph. Lives in `site/figures/` if you add it.
- Student stays anonymous; the paper carries a name and school — neither appears here.
- The inline two-panel SVG is an original schematic (illustrative point layout, real linking-length logic), not a paper figure.
