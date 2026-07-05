---
SUGGESTED TITLE: What if space flows like a river past the event horizon?
SUGGESTED LEDE: On a way of seeing gravity as flowing water rather than curvature — and on checking the picture, of all places, against the clocks aboard GPS satellites.
ESSAY TYPE: A (with B elements)
WORD COUNT: ~1350
EXTENSIONS SECTION: Yes
IMAGES USED: 1 explanatory SVG (inline light-cone diagram); 2 paper-figure suggestions flagged for Ninaad
---

The trouble with "spacetime curvature" is that nobody can picture it. It is the correct answer, and it is also a phrase that does most of its work by sounding authoritative rather than by showing you anything. So I have always been drawn to a different way of describing the same physics, one you can actually see in your head: space is not curved so much as *flowing*, pouring inward toward a massive body like water toward a drain, faster the closer you get. This is the river model of black holes, and the thing I wanted to do with a student was take it seriously enough to check it against data — not near a black hole, which is inconvenient, but twenty thousand kilometres above our heads.

The river picture is not a rival to general relativity. It is general relativity, written in a different set of coordinates. If you take the usual Schwarzschild description of the space around a non-rotating mass and change the time coordinate — from the time kept by a distant observer to the time kept by someone falling freely inward from rest — the arithmetic rearranges itself into Painlevé–Gullstrand form, and in that form space behaves like a medium with a velocity. At radius $r$ the inward flow speed is exactly the Newtonian escape velocity, $v_\text{flow}(r) = \sqrt{2GM/r}$, which is a small miracle of tidiness: the speed you would need to climb out is the speed at which space is falling in. The two are the same number because they are the same fact seen from two sides.

The metaphor pays off at the horizon. Think of light as a fish that can only ever swim at speed $c$ through the water around it. Far from the hole the water is nearly still, so an outward-swimming fish makes easy progress. As it approaches the hole the inward current quickens, and the fish's ground-speed drops. At the event horizon the current reaches $c$ exactly: now an outward-swimming photon, going flat-out, exactly treads water and never advances. Cross inside and the current runs faster than light — not because anything locally is breaking the speed limit, but because the "flow" is a property of the coordinates, not a thing you could clock as it went past. That is the whole reason the horizon is one-way, told without a single tensor.

You can watch it happen in the tilt of the local light cones.

<div class="figure-wrap">
<svg viewBox="0 0 680 300" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Five light cones drawn at increasing distance from a black hole: far from the hole the cone is symmetric and upright, closer in it tips toward the hole, at the event horizon its outgoing edge stands vertical so outward light stalls, and inside the horizon both edges point inward">
  <defs><style>
    .bhlbl { font-family: 'JetBrains Mono', monospace; font-size: 10.5px; fill: #6B6460; letter-spacing: 0.04em; }
    .bhh   { font-family: 'Source Serif 4', serif; font-size: 12px; font-style: italic; fill: #1A1714; }
  </style></defs>
  <rect x="0" y="0" width="70" height="300" fill="#1A4F4F" fill-opacity="0.20"/>
  <rect x="0" y="0" width="24" height="300" fill="#1A4F4F"/>
  <line x1="220" y1="18" x2="220" y2="250" stroke="#1A1714" stroke-width="1.4" stroke-dasharray="6 5"/>
  <text class="bhh" x="228" y="34">event horizon</text>
  <line x1="30" y1="262" x2="650" y2="262" stroke="#6B6460" stroke-width="1"/>
  <polygon points="650,262 641,258 641,266" fill="#6B6460"/>
  <text class="bhlbl" x="486" y="281">radius from the hole →</text>
  <text class="bhlbl" x="86" y="281" text-anchor="start">flow speed increases inward</text>
  <polygon points="120,215 81.4,144.9 46.2,184.2" fill="#2A6B6B" fill-opacity="0.16"/>
  <line x1="120" y1="215" x2="81.4" y2="144.9" stroke="#1A1714" stroke-width="1.6"/>
  <line x1="120" y1="215" x2="46.2" y2="184.2" stroke="#1A1714" stroke-width="1.6"/>
  <circle cx="120" cy="215" r="2.6" fill="#1A1714"/>
  <polygon points="220,215 220.0,135.0 149.2,177.7" fill="#2A6B6B" fill-opacity="0.16"/>
  <line x1="220" y1="215" x2="220.0" y2="135.0" stroke="#1A1714" stroke-width="1.6"/>
  <line x1="220" y1="215" x2="149.2" y2="177.7" stroke="#1A1714" stroke-width="1.6"/>
  <circle cx="220" cy="215" r="2.6" fill="#1A1714"/>
  <polygon points="335,215 367.8,142.0 268.5,170.5" fill="#2A6B6B" fill-opacity="0.16"/>
  <line x1="335" y1="215" x2="367.8" y2="142.0" stroke="#1A1714" stroke-width="1.6"/>
  <line x1="335" y1="215" x2="268.5" y2="170.5" stroke="#1A1714" stroke-width="1.6"/>
  <circle cx="335" cy="215" r="2.6" fill="#1A1714"/>
  <polygon points="465,215 511.7,150.1 402.5,165.1" fill="#2A6B6B" fill-opacity="0.16"/>
  <line x1="465" y1="215" x2="511.7" y2="150.1" stroke="#1A1714" stroke-width="1.6"/>
  <line x1="465" y1="215" x2="402.5" y2="165.1" stroke="#1A1714" stroke-width="1.6"/>
  <circle cx="465" cy="215" r="2.6" fill="#1A1714"/>
  <polygon points="595,215 649.8,156.7 537.0,159.9" fill="#2A6B6B" fill-opacity="0.16"/>
  <line x1="595" y1="215" x2="649.8" y2="156.7" stroke="#1A1714" stroke-width="1.6"/>
  <line x1="595" y1="215" x2="537.0" y2="159.9" stroke="#1A1714" stroke-width="1.6"/>
  <circle cx="595" cy="215" r="2.6" fill="#1A1714"/>
</svg>
<p class="figure-caption"><em>Light cones in the river picture. Far from the hole (right) a cone is symmetric: light can go either way. As the inward flow quickens the cone tips toward the hole; at the horizon the outgoing edge stands perfectly vertical — an outward photon treads water — and inside it, both edges point inward, so every future leads to the centre. The one-way horizon is just the moment the current outruns light.</em></p>
</div>

All of this is a picture, though, and a picture proves nothing. Because the river model is Schwarzschild's geometry in disguise, no observation could ever favour one over the other; they are the same theory. So the honest question is narrower and, I think, more interesting: if you actually *implement* the river bookkeeping as a computer program and run it on real data, does it reproduce the standard relativistic answer — and if it doesn't, can you predict in advance exactly how it will fail?

The place to try this is GPS. Every satellite in the constellation carries an atomic clock, and those clocks tick at a slightly different rate from clocks on the ground — faster, because they sit higher in Earth's gravity, and slower, because they are moving, with the gravitational effect winning by a wide margin. The standard accounting splits the clock-rate offset into a gravitational-redshift term, $\delta_\text{grav} = (GM/c^2)(1/R_\oplus - 1/r)$, and a kinematic time-dilation term, $\delta_\text{kin} = -v^2/2c^2$. The river accounting does something that looks completely different. It says: forget potential and velocity separately; just ask how fast the satellite is moving *relative to the inflowing river of space*. At GPS altitude that river is running inward at about 5.5 kilometres per second. Compute the satellite's speed through the current, apply one time-dilation formula to that "swim speed," and you are done.

We fed both pipelines the same thing — an ordinary precise-orbit file giving the positions of all thirty-two GPS satellites every five minutes over a two-hour window — and let them each compute the clock-rate offset epoch by epoch. Then we subtracted one series from the other.

They did not agree to zero. And that is where the essay actually starts, because for a while a non-zero residual looks exactly like a bug. The clock-rate offset itself is about $4.7 \times 10^{-10}$; the leftover between the two methods sat at around $10^{-12}$, roughly two-tenths of a percent of the signal. Small, but stubbornly present, and structured — it wobbled up and down with the orbit rather than scattering like numerical noise. The temptation is to go hunting for the mistake.

There is no mistake. If you take the river formula and expand it algebraically in the weak-field limit, it comes apart into exactly the gravitational term, exactly the kinematic term, and one extra piece: $-v_\text{flow}(r)\,(v \cdot \hat{r})/c^2$, a term proportional to the satellite's *radial* velocity — how fast it is climbing or falling through the current. That is the residual. Not approximately; the per-epoch leftover matches this closed-form expression at a correlation of 1.000, across all thirty-two satellites. It even has the right shape: because the radial velocity peaks when a satellite is nearest Earth, the residual is largest for the satellites on the most eccentric orbits, and its size — a couple of parts in $10^{12}$ — is what you get by plugging their eccentricities into the formula. The two bookkeepers were never going to give identical numbers, because they keep time in slightly different coordinates, and the gap between their clocks is a quantity you can write down on paper before running either one.

That is the payoff, and it is a conceptual one rather than a discovery. Nothing here tests general relativity — both pipelines are the same physics, so of course they mostly agree. What the exercise shows is subtler and, to me, more satisfying: a way of seeing gravity as flow, invented to make a black hole's horizon intuitive, survives all the way down to the undramatic setting of a satellite clock, and where it parts company with the textbook method it does so by precisely the term its change of coordinates predicts. The river runs from the event horizon to low Earth orbit, and the books balance to a part in a trillion.

## An honest caveat that should go before any stronger claim

The scope here is narrow and worth stating plainly. Everything quantitative lives in the weak field, with satellites treated as test particles too light to bend spacetime themselves, and with Earth approximated as a simple non-rotating Schwarzschild mass. That last approximation quietly discards the effects of Earth's oblateness and its rotation (frame-dragging); those are real, but they enter the *difference* between the two pipelines only at the level of $10^{-15}$ or below — a thousand times under the residual we care about — because both methods sit on the same Schwarzschild background and the corrections cancel. So the GPS result should not be oversold: it does not confirm the strong-field claims the light-cone picture illustrates, and because both pipelines are deterministic computations from one ephemeris file, it is not an independent measurement of relativity at all. It is a consistency check — a demonstration that two coordinate systems, one of them shaped like a flowing river, agree to the exact term the coordinate change between them requires. The strong-field version, where the river really earns its keep, is the thing a next project would have to reach.

---

## EDITOR'S NOTE (not for publication)

- **Type A framing.** The river model is the protagonist; the GPS check is the vehicle that shows it doing real, checkable work. The narrative pivot is the non-zero residual that turns out to be the predicted coordinate-time term (paper's Discussion, correlation r = 1.000). Confirm you're happy leading a "black hole" essay with GPS — I think the strong→weak-field bridge is the most memorable thing in the paper, but it is a choice.
- Numbers from the paper: v_flow(r) = √(2GM/r); ~5.5 km/s at GPS altitude; absolute offset ≈ 4.7×10⁻¹⁰; residual ≈ 10⁻¹² (~0.2%); residual = −v_flow(r)(v·r̂)/c²; correlation 1.000 across all 32 PRNs; two-hour window, 5-minute epochs. The "fish swimming upstream" image is Hamilton's own from the river-model literature, lightly reworded — flag if you'd rather attribute it explicitly.
- **Figure suggestions (paper figures not embedded — source is a Drive docx I couldn't extract images from cheaply).** If you want real plots on the page: (1) **Fig 2**, the six-PRN overlays with the residual column — the single best piece of evidence, would sit right after "They did not agree to zero"; (2) **Fig 1**, the three PG panels (flow reaching c, null-ray slopes, tipping cones) — but my inline light-cone diagram already covers that concept, so I'd only add Fig 1 if you want the paper's own rendering too. Both live in `site/figures/` if added.
- Student stays anonymous ("a student"); acknowledgments in the paper name school/family — none of that appears here.
- The inline light-cone SVG is an original schematic (tilt is illustrative, not computed from the metric). Flagging in case you'd prefer the paper's Fig 1 panel instead.
- Title alternative if you want the GPS hook up front: "Can a GPS satellite feel space flowing like a river?"
