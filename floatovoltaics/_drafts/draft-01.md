---
SUGGESTED TITLE: Can floating solar power a city and save its water?
SUGGESTED LEDE: On solar panels that make electricity and slow a drought at the same time — and on how, once a project does two things at once, which reservoir is "best" depends entirely on what you decide to count.
ESSAY TYPE: A (with B elements)
WORD COUNT: ~1320
EXTENSIONS SECTION: Yes
IMAGES USED: 1 explanatory SVG (inline); 2 paper-figure suggestions flagged for Ninaad
---

California is short of two things at once: clean electricity and water. Most fixes help with one and ignore the other, or trade one against the other — a desert solar farm makes power but eats land and does nothing for the water table. Floating photovoltaics are unusual because they help with both. Cover part of a reservoir with solar panels and you generate electricity from an otherwise idle surface, and, because the panels shade the water, you also cut how much of it evaporates away under the sun. Power and water, from the same installation. A student I was working with wanted to know what that dual benefit would actually amount to across California's reservoirs — and the more interesting thing he found was not a number but a question the number cannot answer on its own.

The setup is a deterministic model rather than a field trial: take the ten largest California reservoirs, imagine covering a tenth of each one with panels, and compute two outputs from public data. The first is electricity, estimated from each site's local solar yield and the area of panels it can hold. The second is water saved, estimated from each site's evaporation rate and how much of that a shading layer suppresses. Add it all up and the totals are substantial — on the order of twelve thousand gigawatt-hours of electricity a year and thirty-odd thousand megalitres of water kept in the reservoirs rather than lost to the air. As a demonstration that the dual benefit is real and large, the model does its job in the first paragraph of results.

Then it gets interesting, because a project that produces two different goods does not have a single "best" site. It has as many rankings as you have ways to keep score, and they do not agree.

<div class="figure-wrap">
<svg viewBox="0 0 640 330" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="A scatter plot of the ten reservoirs, annual energy on the vertical axis against water saved on the horizontal axis. Shasta sits furthest out, largest on both. A dashed line from the origin through Berryessa is the steepest, marking it as the site with the most energy generated per unit of water saved — a different winner from the biggest producer.">
  <defs><style>
    .fvlbl { font-family: 'JetBrains Mono', monospace; font-size: 10.5px; fill: #6B6460; letter-spacing: 0.03em; }
    .fvn   { font-family: 'JetBrains Mono', monospace; font-size: 10.5px; fill: #1A1714; }
    .fvh   { font-family: 'Source Serif 4', serif; font-size: 12px; font-style: italic; fill: #1A1714; }
  </style></defs>
  <line x1="70" y1="40" x2="70" y2="275" stroke="#6B6460" stroke-width="1"/>
  <line x1="70" y1="275" x2="580" y2="275" stroke="#6B6460" stroke-width="1"/>
  <text class="fvlbl" x="24" y="44">energy</text>
  <text class="fvlbl" x="430" y="298">water saved →</text>
  <line x1="70" y1="275" x2="532" y2="44" stroke="#1A4F4F" stroke-width="1.4" stroke-dasharray="6 5"/>
  <circle cx="505" cy="63" r="6" fill="#1A4F4F" fill-opacity="0.95"/>
  <circle cx="324" cy="154" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="312" cy="168" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="221" cy="204" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="383" cy="118" r="6" fill="#1A4F4F" fill-opacity="0.95"/>
  <circle cx="261" cy="180" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="281" cy="179" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="219" cy="208" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="456" cy="88" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <circle cx="150" cy="240" r="4.5" fill="#2A6B6B" fill-opacity="0.6"/>
  <text class="fvh" x="497" y="49" text-anchor="end">Shasta — biggest of both</text>
  <text class="fvh" x="395" y="122">Berryessa</text>
  <text class="fvn" x="150" y="70">steepest line = most</text>
  <text class="fvn" x="150" y="85">energy per drop saved</text>
</svg>
<p class="figure-caption"><em>Every reservoir plotted by the two things floating solar delivers: electricity up the side, water saved along the bottom. Shasta sits furthest out — it is biggest on both, because it is simply the largest lake. But "best" as a ratio is a slope, not a distance: the steepest line from the origin, through Lake Berryessa, marks the site that generates the most energy per unit of water it saves. The biggest producer and the most efficient one are not the same reservoir.</em></p>
</div>

Score the sites by raw electricity and the answer is almost boring: the biggest reservoir wins, because energy scales with how many panels you can float, which scales with surface area. Shasta, the largest, tops the list; the local sunniness of a site barely moves the ranking next to the sheer size of the lake. But raw generation is the wrong yardstick for a dual-purpose machine, because it ignores half of what the machine is for. So the study proposes a different score — energy generated per unit of water saved — and by that measure a different reservoir wins. Lake Berryessa, which is not the largest, comes first, because it sits where the baseline evaporation is relatively low. That sounds backwards until you see the arithmetic: a site with low evaporation saves less water per hectare of panel, so each megalitre it does save is "bought" with more electricity generated alongside it, and the ratio of energy to water comes out high. The biggest producer is not the most efficient dual-purpose site. Which reservoir is "best" flipped the moment the yardstick did.

A third metric reshuffles the middle of the table again, and this one is the most physical of the three. Electricity is only useful where people are, and every kilometre of transmission line bleeds a little of it away as heat. Fold that in — charge each site a small penalty per kilometre to its nearest city — and reservoirs that generate more can end up delivering less. A lake thirty-seven kilometres from Sacramento climbs past one a hundred and twenty-one kilometres away, even though the distant lake produces more power, because so much of that far-away power never arrives. The average site loses only a couple of per cent to the wire, which sounds negligible until you multiply it by a large plant: for the most remote reservoir it works out to tens of gigawatt-hours of clean electricity vanishing into the transmission lines every year. Remoteness is a quiet tax that raw generation figures never show.

None of these three rankings is wrong. They are answers to three different questions — how much power, how much power per drop of water, how much power actually delivered — and the point of the study is that you cannot avoid choosing which question you are asking. That choice is not a technicality downstream of the "real" analysis; it is the analysis. Conventional energy planning quietly picks one answer by default: it optimises energy per dollar, which is why it keeps building solar in cheap empty desert. Put water in the denominator instead and a completely different map lights up — one where a reservoir is not just a surface to rent but a dual-purpose asset, a power station that also holds back a drought. The contribution here is not the discovery that Berryessa scores well. It is the yardstick that makes Berryessa's kind of value visible at all, because a benefit you never put in the denominator is a benefit your ranking will always throw away.

I should be plain that this is a model built from annual averages, not a measurement of any real installation, and its specific numbers should be read as illustrations of the framework rather than a procurement list. But the framework is the durable part, and it generalises well past reservoirs. Whenever an intervention does two things at once — generates and conserves, treats and prevents, earns and protects — there is no single scalar that ranks the options, and the most consequential modelling decision is the humblest-looking one: what you divide by. Get the numerator and the denominator right and the arithmetic will faithfully tell you which site wins. It just cannot tell you which question you should have been asking, and that was never the model's job. It was yours.

## An honest caveat that should go before any stronger claim

The rankings here are the output of a deterministic desktop model, and every input is an approximation. Energy is estimated from annualised solar climatology, so it misses seasonal swings, heatwave temperature penalties, and — most importantly in California — the drought drawdowns that shrink a reservoir's surface and change both how many panels it can hold and how much it evaporates, the two quantities the whole analysis rests on. The water-saving figures ride on an evaporation-suppression factor that the literature places anywhere from twenty to sixty per cent, an enormous range that no single site-specific measurement here pins down. The transmission penalty is a flat loss per straight-line kilometre, which ignores real grid capacity, substation limits, and the actual routing of power lines. And coverage was fixed at a tenth of each surface by assumption, not optimised. What the study earns is not "build at Berryessa" but something more useful and more portable: a demonstration that for a dual-benefit technology the choice of efficiency metric drives the siting decision, that transmission distance can quietly overturn a generation-based ranking, and that scoring energy against water saved surfaces priorities a generation-only or dollar-only analysis would never reveal. Turning that into a real siting recommendation would need the time-varying hydrology, dynamic grid modelling, and on-site evaporation measurements the model deliberately leaves for later.

---

## EDITOR'S NOTE (not for publication)

- **Type A framing** — the tool is the dual-benefit efficiency metric (kWh per megalitre) and the ranking framework; the "story" is that the metric you choose determines which reservoir wins (gross energy → Shasta; energy-per-water → Berryessa; net-of-transmission → mid-table reshuffle). The paper reports all three rankings; I've made "the metric is the decision" the explicit thesis, which is an interpretive lift the results support. Confirm you're happy leading with that.
- Numbers from the paper: 10 reservoirs, 10% coverage; combined ~11,979.9 GWh/yr and ~34,441.0 ML/yr; Shasta highest gross 2,215.9 GWh/yr; Berryessa highest dual-benefit efficiency 365,870 kWh/ML (Millerton lowest 319,483); average transmission loss 2.11%, worst Oroville 3.63% at 121 km ≈ 45.6 GWh/yr lost; Folsom (37 km) leapfrogs Oroville (121 km) in the net ranking. Please spot-check the two efficiency figures and the Shasta/Berryessa framing. (My inline scatter's point positions are computed from the paper's per-reservoir area/PVOUT/evaporation inputs, so they should track the real Figure 5 closely, but treat them as illustrative.)
- One nuance I simplified: Shasta is the sole strictly Pareto-optimal site (biggest on both axes), while Berryessa wins the *ratio*. I've framed this as "biggest ≠ most efficient," which is faithful, but if you want I can add the word "Pareto" and the New Melones / San Luis reshuffles explicitly.
- **Figure suggestions (paper figures not embedded — source is a Drive docx I couldn't extract images from cheaply).** Two would strengthen the page: (1) **Fig 3**, the dual-benefit efficiency ranking with Berryessa on top — the cleanest statement of the pivot; (2) **Fig 5**, the energy-water trade-off scatter with the Pareto frontier, which my inline diagram schematises. Both live in `site/figures/` if added.
- Student stays anonymous; no names or institutions appear. Reservoir and city names are public geography, not identifying.
- Hero (an FPV array on a stylised reservoir) and the inline scatter are original schematics; the scatter's numbers derive from the paper's inputs but are drawn illustratively.
