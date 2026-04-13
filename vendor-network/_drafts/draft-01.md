---
SUGGESTED TITLE: When does a market tip from many small sellers to one platform?
SUGGESTED LEDE: On the phase boundary between local and digital vendors, and on how two perfectly reasonable simulation engines can disagree about which knob is doing the work.
ESSAY TYPE: B (with D elements)
WORD COUNT: ~1500
EXTENSIONS SECTION: Yes
IMAGES USED: 4 paper figures, 1 explanatory SVG
---

Statistical physics learned something useful about markets long before it was allowed to say so out loud. The useful thing is this: once you have a lot of almost-identical things that interact with each other and with a few global parameters, you can often describe their collective behaviour without knowing much about any individual. Water boils at 100°C whether the specific molecules are bored or excited about it. Markets, by the same logic, might concentrate or diversify according to a handful of global knobs whose effect has nothing to do with what any particular buyer is thinking. This essay is about trying to take that idea seriously for a specific question — the competition between digital platforms and local vendors — and about what happened when I did.

The question I wanted to press on was a tipping question. Digital platforms didn't arrive and immediately dominate every market. They grew, and in some sectors they captured nearly everything, and in others they didn't. The standard explanations for this — network effects, lock-in, switching costs — are all real, but they are structural descriptions of *why* concentration is possible. They don't tell you when a market actually flips, or what a small change in conditions would do. A colleague I was working with on this kept returning to the same framing: "What does the market look like just before it tips?" That is a question about phase boundaries, and it is exactly the sort of thing a physicist has tools for.

The model, in its simplest form, is almost embarrassingly stripped down. A square unit of geography contains customers and local vendors as points, and digital vendors as delocalised entries with a delivery delay. At every round, each customer picks one vendor. The choice is not deterministic; it follows a Boltzmann rule,

\[P_{ij} = \frac{\exp(U_{ij}/T)}{\sum_{k} \exp(U_{ik}/T)},\]

where the utility \(U_{ij}\) combines price, rating, delay (distance for local vendors, a latency parameter for digital ones), a reinforcement term for past purchases, and a social-influence term. The denominator is taken over the vendors currently *visible* to the customer, which matters more than it looks like it should.

Three global parameters do almost all the work in this model. The first is the temperature \(T\), which controls how deterministic choices are. At \(T \to 0\), each customer picks the vendor with the highest utility and nothing else. At large \(T\) they might as well be rolling dice. The second is an information-access rate \(\gamma \in [0, 1]\), which governs how quickly customers discover local vendors. Digital vendors are visible by construction; local vendors are not. At \(\gamma = 0\), a nearby local baker could be next door and the customer will never order from them because they don't know the baker exists. The third is a social coupling strength \(J\) that amplifies the utility of vendors already popular in the previous round — popularity begets popularity, in an Ising-type feedback. These three parameters are the axes of the phase diagram.

The phases themselves are easy to describe once you have the order parameter. We tracked the steady-state local market share \(L^*\) — the fraction of all purchases going to local vendors after the dynamics have equilibrated — and from it a magnetisation-like quantity \(m\) that is positive when the market favours digital vendors and negative when it favours locals. The three phases are:

<div class="phase-cartoon-wrap">
<svg viewBox="0 0 680 280" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Schematic of the three market phases: Digital Dominance, Local Dominance, and Mixed Equilibrium">
  <defs>
    <style>
      .phase-label { font-family: 'JetBrains Mono', monospace; font-size: 11px; fill: #6B6460; letter-spacing: 0.05em; text-transform: uppercase; }
      .phase-title { font-family: 'Source Serif 4', serif; font-size: 14px; fill: #1a1a1a; font-style: italic; }
      .phase-box { fill: #FDFBF8; stroke: #c8c0aa; stroke-width: 1.2; }
      .dot-dig { fill: #272540; }
      .dot-loc { fill: #4db8a0; }
      .axis { stroke: #6B6460; stroke-width: 0.8; }
    </style>
  </defs>
  <!-- Three panels -->
  <rect class="phase-box" x="20" y="40" width="200" height="200" rx="3"/>
  <rect class="phase-box" x="240" y="40" width="200" height="200" rx="3"/>
  <rect class="phase-box" x="460" y="40" width="200" height="200" rx="3"/>

  <!-- Digital Dominance: mostly dark dots -->
  <g>
    <circle class="dot-dig" cx="60" cy="80" r="5"/><circle class="dot-dig" cx="90" cy="110" r="5"/><circle class="dot-dig" cx="130" cy="90" r="5"/><circle class="dot-dig" cx="170" cy="120" r="5"/>
    <circle class="dot-dig" cx="55" cy="150" r="5"/><circle class="dot-dig" cx="105" cy="170" r="5"/><circle class="dot-dig" cx="155" cy="185" r="5"/><circle class="dot-dig" cx="190" cy="155" r="5"/>
    <circle class="dot-dig" cx="75" cy="210" r="5"/><circle class="dot-dig" cx="135" cy="220" r="5"/><circle class="dot-dig" cx="180" cy="215" r="5"/>
    <circle class="dot-loc" cx="115" cy="140" r="5"/>
  </g>
  <text class="phase-label" x="120" y="60" text-anchor="middle">Digital Dominance</text>
  <text class="phase-title" x="120" y="258" text-anchor="middle">low T, low γ</text>

  <!-- Mixed Equilibrium: scattered dark and teal -->
  <g>
    <circle class="dot-dig" cx="270" cy="80" r="5"/><circle class="dot-loc" cx="310" cy="100" r="5"/><circle class="dot-dig" cx="350" cy="90" r="5"/><circle class="dot-loc" cx="395" cy="115" r="5"/>
    <circle class="dot-loc" cx="275" cy="140" r="5"/><circle class="dot-dig" cx="325" cy="150" r="5"/><circle class="dot-loc" cx="370" cy="140" r="5"/><circle class="dot-dig" cx="420" cy="165" r="5"/>
    <circle class="dot-loc" cx="295" cy="190" r="5"/><circle class="dot-dig" cx="345" cy="200" r="5"/><circle class="dot-loc" cx="390" cy="195" r="5"/><circle class="dot-dig" cx="410" cy="215" r="5"/>
  </g>
  <text class="phase-label" x="340" y="60" text-anchor="middle">Mixed Equilibrium</text>
  <text class="phase-title" x="340" y="258" text-anchor="middle">high T, any γ</text>

  <!-- Local Dominance: mostly teal -->
  <g>
    <circle class="dot-loc" cx="490" cy="80" r="5"/><circle class="dot-loc" cx="525" cy="105" r="5"/><circle class="dot-loc" cx="570" cy="90" r="5"/><circle class="dot-loc" cx="610" cy="115" r="5"/>
    <circle class="dot-loc" cx="495" cy="140" r="5"/><circle class="dot-loc" cx="540" cy="155" r="5"/><circle class="dot-loc" cx="590" cy="140" r="5"/><circle class="dot-loc" cx="625" cy="170" r="5"/>
    <circle class="dot-loc" cx="510" cy="195" r="5"/><circle class="dot-loc" cx="560" cy="210" r="5"/><circle class="dot-loc" cx="605" cy="200" r="5"/>
    <circle class="dot-dig" cx="580" cy="180" r="5"/>
  </g>
  <text class="phase-label" x="560" y="60" text-anchor="middle">Local Dominance</text>
  <text class="phase-title" x="560" y="258" text-anchor="middle">low T, high γ</text>
</svg>
<p class="figure-caption"><em>The three market phases, schematically. Dark dots are purchases going to digital vendors; teal dots are purchases going to locals. The phases are not about individual preferences — they are about which basin the aggregate settles into.</em></p>
</div>

Digital Dominance (\(m > 0\), \(L^* < 0.5\)) sits in the low-information, low-noise corner: customers can't see local vendors, and the choices they make with the vendors they *can* see are deterministic enough to concentrate their purchases on a small set of them. Local Dominance (\(m < 0\), \(L^* > 0.5\)) is the opposite corner: enough information access to build up knowledge of nearby local vendors, and enough decisiveness to prefer them once the short Euclidean distance gives them a utility premium. Mixed Equilibrium (\(m \approx 0\)) is what happens at high temperature, regardless of \(\gamma\) — the softmax flattens, and market share ends up distributed roughly in proportion to how many vendors of each type are visible.

The central quantitative output is the phase diagram across the \((T, \gamma)\) plane. What it actually looks like is the less pretty but more informative part.

<div class="figure-wrap">
  <img src="figures/phase_diagram_abm.png" alt="Steady-state local market share across the temperature-gamma plane in the agent-based model">
  <p class="figure-caption">Steady-state local market share \(L^*\) across the \((T, \gamma)\) plane from the agent-based simulation. The low-γ band is almost entirely digital; the high-γ, low-T corner is almost entirely local. The dashed contour marks \(L^* = 0.5\). What matters in this image is the width of the crossover — and whether that width is a physical fact or an artefact of the engine generating it.</p>
</div>

That last sentence is where the project stopped being a mapping exercise and became interesting. Because I ran the same sweep with two different simulation engines. The first is the agent-based model above — individual customers with individual histories, choosing stochastically each round. The second is a self-consistent mean-field fixed-point solver that treats the population as a single aggregate magnetisation \(m\) that updates against its own average field. The two are formally equivalent in the \(N \to \infty\) limit; the law-of-large-numbers argument is textbook. They should agree, and in the bulk of both ordered phases they do. Where they disagree is at the boundary.

<div class="figure-wrap">
  <img src="figures/phase_diagram_mf.png" alt="Mean-field version of the phase diagram, with the gamma axis visibly compressed">
  <p class="figure-caption">The mean-field version of the same sweep. The overall topology is preserved, but the crossover is sharper, more vertical, and organised almost entirely along the \(T\) axis. The \(\gamma\) axis is visibly compressed. The same parameters produce qualitatively different-looking phase boundaries depending on which engine you ask.</p>
</div>

The interesting diagnostic turned out to be susceptibility — the partial derivative of \(L^*\) with respect to each control parameter, computed numerically from the grid. In a physical phase transition, the susceptibility peaks along the critical line; the ridge of \(\chi = \partial L^* / \partial \gamma\) is where the system is most responsive to information access, and the ridge of \(\chi_T = \partial L^* / \partial T\) is where it is most responsive to noise. When you plot both for both engines, something concrete happens.

<div class="figure-wrap">
  <img src="figures/susceptibility.png" alt="Finite-difference susceptibility maps in the T-gamma plane for both ABM and mean-field">
  <p class="figure-caption">Susceptibility maps. In the ABM, \(\chi_\gamma\) shows localised hotspots — specific cells where a small increase in information access produces a disproportionate gain in local share. In the mean-field engine, \(\chi_\gamma\) is near-zero almost everywhere. Both engines agree that \(T\) is an active control; they disagree about whether \(\gamma\) is.</p>
</div>

Read that image the way you'd read a diagnostic. The ABM says: information access is a genuine dynamical control. In the places where the susceptibility is concentrated, a nudge in \(\gamma\) moves the market meaningfully. The mean-field solver says: \(\gamma\) barely matters. The difference is not noise. It is structural, and it has a mechanism. In the ABM, every customer is building up a visibility mask through repeated discovery events; the masks evolve round by round, and \(\gamma\) sets the rate at which that evolution happens. In the mean-field treatment, the consideration sets are frozen at their expected value. That approximation is fine when \(\gamma\) is either very low or very high — in both regimes the typical mask looks close to its average — but near the boundary, where the distribution of masks is wide and the dynamics depend on accumulating over time, the static-mask approximation loses the mechanism that makes \(\gamma\) matter.

I find this unexpectedly satisfying as a result, because it is the kind of thing that would be easy to miss. The two engines agree on their major claims: three phases, the same general geometry of the boundary, the same behaviour at large \(J\) where social coupling drives the transition first-order and recovers a bistable region with hysteresis. A paper summarising only those things would be internally consistent and quite misleading. The places where the engines *disagree* are the places where the simplification being made by the mean-field engine — freezing the consideration sets — stops being benign. Any model of this kind that takes \(\gamma\) seriously as a policy lever should probably be checked against an engine where \(\gamma\) is dynamically active.

## An extension, less stylised

There is a follow-up study that takes the same framework and asks a sharper policy question. If a recommendation system deliberately weights vendors by proximity — for instance, through an Open Network for Digital Commerce-style protocol with a distance weight \(w\) — how much does the market shift? The experiment is a two-parameter sweep over \(\gamma\) and \(w\) at fixed \(T\). The result is that \(\gamma\) acts as a *gate*: at \(\gamma = 0\) no amount of distance weighting produces any local share at all, because local vendors are never discovered. Once \(\gamma > 0\), \(w\) becomes the active knob. Moving \(w\) from \(0\) to \(1\) at a fixed \(\gamma = 0.3\) more than triples late-time local share, from about \(0.17\) to about \(0.55\), and roughly halves the HHI concentration index.

<div class="figure-wrap">
  <img src="figures/ondc_gamma_w_slice.png" alt="Interaction slice between information access gamma and protocol distance weight w">
  <p class="figure-caption">The \(\gamma \times w\) interaction slice at fixed \(T = 0.5\). Each curve is a different distance weight. \(\gamma = 0\) collapses them all to zero local share by construction; above that, the curves fan out, and the gap between low-\(w\) and high-\(w\) persists all the way to full discovery. Visibility is a necessary precondition, but distance weighting is a separate channel once that precondition is met.</p>
</div>

The gated shape of that slice is the part I'd keep, even if the specific numbers are soft. It says something about how policy interventions of this kind work: no amount of protocol design helps sellers who never enter the consideration set, but once they do, even modest changes in how proximity is weighted can produce substantial shifts in aggregate structure. Two parameters, two jobs, and the order in which they matter is fixed.

What this whole exercise really reinforced for me is how fragile the intuition gets when you combine two reasonable-looking assumptions. Agent-based and mean-field models are both defensible framings of the same system. They disagree near the boundary not because one is wrong but because one of them is averaging over something that matters. The honest move, when you find a disagreement like that, is not to pick a winner. It is to ask what the averaging threw away, and whether the thing it threw away is the mechanism you were trying to study in the first place.

---

## EDITOR'S NOTE (not for publication)

- The figure filename mapping from `pdfimages` to the paper's Figure numbers was inferred by page order; `phase_diagram_abm.png`, `phase_diagram_mf.png`, and `susceptibility.png` should be spot-checked against Fig 7 and Fig 10/12 in the JCS paper before publication.
- The claim that the two engines "agree on their major claims" at \(J \to J_c\) is lightly paraphrased from Section 3.9 of the JCS paper. The specific statement about bistability and hysteresis is in the paper; the framing as a reason to be cautious about mean-field is mine.
- The ONDC numbers (0.17 → 0.55 and HHI 0.64 → 0.30) are pulled directly from the NHSJS Table 2, but the claim that "visibility is a necessary precondition" is paraphrased from the Discussion section.
- Collaborator not named, per the style prompt. Amaira Goyal is credited on the paper itself, but not mentioned by name in the essay — worth a check that Ninaad is OK with this.
- The explanatory SVG shows three panels with dots coloured by the vendor type the customer bought from. It's schematic, not data — consider whether to keep or replace with a Category 2 diagram built from an actual simulation snapshot.
