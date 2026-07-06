---
SUGGESTED TITLE: Do prime gaps have favorite sizes?
SUGGESTED LEDE: On the gaps between consecutive primes preferring 6 and 30 — and on how the statistic you'd reach for to prove it flatly reports there is nothing there.
ESSAY TYPE: C (with A elements)
WORD COUNT: ~1330
EXTENSIONS SECTION: Yes
IMAGES USED: 1 explanatory SVG (inline two-panel); 2 paper-figure suggestions flagged for Ninaad
---

Primes are supposed to be the unpredictable ones. There is no formula that spits out the next one, and the sequence 2, 3, 5, 7, 11, 13 looks, at a glance, like it wanders without a plan. But the differences between consecutive primes — the gaps — turn out to have distinct preferences. Some gap sizes show up far more often than their neighbours, and the favouritism is not subtle. In the first twenty-five million primes, a gap of 6 is enormously more common than a gap of 8, and a gap of 30 stands well above the gaps of 28 or 32 on either side. The primes, so irregular one at a time, keep a remarkably orderly set of habits in the aggregate. The question a student and I chased was whether those habits are real arithmetic or a trick of the eye — and the answer turned out to hinge on which number you compute to check.

The habits are easiest to see if you plot how often each even gap occurs. (Every gap above 2 is even, since one of any two consecutive odd numbers is divisible by nothing helpful.) The frequencies fall off roughly exponentially as gaps get larger, but not smoothly: laid over the decline is a strong rhythm, with every third even gap — 6, 12, 18, 24 — standing taller than the gaps flanking it, and outright spikes at 6 and at 30. These are sometimes called jumping champions: the gap sizes that, over a given range, win the popularity contest. And there is a clean reason for them. A gap is easy to realise if it dodges the constraints imposed by small primes. Six is divisible by both 2 and 3, so a pair of primes six apart sidesteps obstructions from the two smallest primes at once; thirty throws in 5 as well. The First Hardy–Littlewood conjecture turns this intuition into a number: a weight for each gap, built as a product over the odd prime divisors of half the gap, that says how favoured that gap should be. Gaps rich in small prime factors get boosted; gaps that fight the small primes get suppressed.

So there is a theory that predicts which gaps are popular, and there is data on which gaps are actually popular. The obvious thing to do is check whether they agree — correlate the predicted weights against the observed frequencies and read off how tight the relationship is. We did, and the correlation came back at 0.05.

<div class="figure-wrap">
<svg viewBox="0 0 720 300" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Two panels. Left: a scatter of prime-gap frequency against Hardy-Littlewood weight forms vertical bands with no upward trend, and the fitted line is nearly flat — correlation about 0.05. Right: the same data drawn as a frequency comb, where the gaps at six and thirty spike exactly where the theory predicts a peak.">
  <defs><style>
    .pglbl { font-family: 'JetBrains Mono', monospace; font-size: 10.5px; fill: #6B6460; letter-spacing: 0.03em; }
    .pgn   { font-family: 'JetBrains Mono', monospace; font-size: 11px; fill: #1A1714; }
    .pgh   { font-family: 'Source Serif 4', serif; font-size: 12.5px; font-style: italic; fill: #1A1714; }
  </style></defs>
  <text class="pgh" x="12" y="24">the statistic you'd reach for</text>
  <text class="pgh" x="392" y="24">the structure that's actually there</text>
  <line x1="55" y1="40" x2="55" y2="235" stroke="#6B6460" stroke-width="1"/>
  <line x1="55" y1="235" x2="320" y2="235" stroke="#6B6460" stroke-width="1"/>
  <text class="pglbl" x="24" y="40">freq</text>
  <text class="pglbl" x="205" y="255">HL weight →</text>
  <circle cx="78" cy="137" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="84" cy="90" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="80" cy="71" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="75" cy="200" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="131" cy="150" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="129" cy="76" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="129" cy="172" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="126" cy="175" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="175" cy="105" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="185" cy="143" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="183" cy="156" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="183" cy="126" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="227" cy="85" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="233" cy="168" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="225" cy="131" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="227" cy="109" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="284" cy="111" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="285" cy="99" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="275" cy="198" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <circle cx="280" cy="125" r="3.2" fill="#2A6B6B" fill-opacity="0.8"/>
  <line x1="70" y1="150" x2="305" y2="140" stroke="#1A1714" stroke-width="1.6" stroke-dasharray="6 5"/>
  <text class="pglbl" x="150" y="128">r = 0.05  (p = 0.62)</text>
  <rect x="430" y="120" width="20" height="105" fill="#3D9090"/>
  <rect x="457" y="132" width="20" height="93" fill="#3D9090"/>
  <rect x="484" y="24" width="20" height="201" fill="#1A4F4F"/>
  <rect x="511" y="152" width="20" height="73" fill="#3D9090"/>
  <rect x="538" y="160" width="20" height="65" fill="#3D9090"/>
  <rect x="565" y="167" width="20" height="58" fill="#3D9090"/>
  <rect x="592" y="101" width="20" height="124" fill="#1A4F4F"/>
  <rect x="619" y="180" width="20" height="45" fill="#3D9090"/>
  <rect x="646" y="185" width="20" height="40" fill="#3D9090"/>
  <rect x="673" y="189" width="20" height="36" fill="#3D9090"/>
  <line x1="420" y1="225" x2="700" y2="225" stroke="#6B6460" stroke-width="1"/>
  <path d="M488.0,10 L494.0,18 L500.0,10" fill="none" stroke="#1A1714" stroke-width="1.6"/>
  <text x="494.0" y="241" text-anchor="middle" class="pgn">6</text>
  <path d="M596.0,87 L602.0,95 L608.0,87" fill="none" stroke="#1A1714" stroke-width="1.6"/>
  <text x="602.0" y="241" text-anchor="middle" class="pgn">30</text>
  <text class="pglbl" x="392" y="255">even gap size →</text>
</svg>
<p class="figure-caption"><em>The same data, two ways. Plot frequency against the theory's weight and the points scatter into vertical bands with no upward drift — the correlation is 0.05, statistically indistinguishable from nothing. Plot frequency against gap size and the theory's peaks land exactly where the spikes are. The relationship is real; the correlation just cannot see it.</em></p>
</div>

A Pearson correlation of 0.05, with a p-value of 0.62, is the statistical equivalent of a shrug. Taken at face value it says the Hardy–Littlewood weights carry no information about how often gaps occur. And yet the peaks in the frequency plot sit precisely on the peaks the theory predicts. Both statements are true at once, and the reason they are is the whole point. A correlation asks a specific question: as the weight goes up, does the frequency go up too, proportionally, across all the gaps? The answer is no, because the weights and the frequencies live on different scales and slide past each other — small gaps are common for reasons of raw density that have nothing to do with the arithmetic weight, so the cloud of points spreads into vertical stripes with no global tilt. But that was never what the conjecture claimed. Hardy and Littlewood do not predict that a gap with twice the weight is twice as frequent. They predict an *ordering*: among gaps of similar size, the ones divisible by more small primes win. The structure is entirely local — is this gap favoured over its immediate neighbours? — and a global correlation is designed to average exactly that local structure away. The number that was supposed to confirm the pattern is blind to it by construction.

You can watch the same blindness in the leftover errors. If you take the theory's weights and rescale them by a single best-fit factor to line them up with the data, the residuals are not random noise: they run positive for small gaps — the gap of 6 alone is off by a clear margin — cross through zero around a gap of fifty, and turn gently negative after. One scaling factor cannot simultaneously match the steep drop at small gaps and the flatter arithmetic curve, so it splits the difference and leaves a signature behind. The misfit is systematic, which is another way of saying the structure is real and a single summary number is the wrong tool for it.

The primes' other famous habit concerns not which gaps are common but how large the rare ones get, and here a different number behaves better. Cramér's conjecture says the biggest gaps near a prime *p* grow no faster than the square of its logarithm, which means the normalised ratio of a gap to that square should stay bounded no matter how far out you go. Across all twenty-five million primes, up to just under half a billion, the running maximum of that ratio climbs briefly among the small primes and then flattens into a nearly horizontal line, sitting comfortably below the refined theoretical ceiling of about 1.123. Large normalised gaps do not become more common as the primes grow; if anything they thin out. It looks like clean support for Cramér — until you remember what finite evidence can and cannot do. The data at this scale genuinely cannot tell Cramér's original guess apart from a well-known correction to it, and Cramér's underlying model is itself known to be subtly wrong, because it pretends the integers are statistically independent when divisibility quietly correlates them. The flat line is consistent with the conjecture. It is not, and can never be, a confirmation.

That is the honest shape of computational number theory, and I find it more interesting than a clean win would have been. Twice over, the same lesson: the primes carry real structure, and the first number you reach for to measure it can miss it completely — a correlation that averages away a local pattern, a bounded ratio that cannot separate two models it appears to endorse. The gap between "consistent with" and "true" is where all the mathematics still lives. The computation does not close it. It just shows you, very precisely, how far there is still to go.

## An honest caveat that should go before any stronger claim

Everything here is finite and therefore provisional. Twenty-five million primes sounds like a lot and is a rounding error against infinity, and both conjectures are statements about the limit as the primes grow without bound — so no dataset, however large, can do more than fail to contradict them. The specific numbers also depend on choices: how the gaps are binned, how the weights are normalised to sit on the same axis as the frequencies, and the floating-point precision underneath it all. Rare large gaps are exactly the events most sensitive to dataset size, so any claim resting on the extreme values should be read with caution. What the study earns is modest and real: over this range, the jumping champions are where the arithmetic says they should be, the large gaps stay bounded on the logarithmic scale, and — the part worth carrying away — a near-zero correlation is not the same as a near-zero pattern.

---

## EDITOR'S NOTE (not for publication)

- **Type C framing** — the pivot is the r = 0.05 correlation that coexists with perfect peak alignment; I've made "the summary statistic is blind to local structure" the spine, with the Cramér thread as a second, rhyming instance ("consistent with" ≠ "confirms"). The paper states both plainly (Fig 3 discussion; the finite-evidence caveat); I've promoted them to the thesis. Confirm you're happy leading with the statistical-humility angle rather than the number-theory results.
- Numbers from the paper: 25M primes up to 472,882,027; jumping champions g = 6 and g = 30; Pearson r = 0.0507 (p = 0.616), Spearman ρ = 0.0364 (p = 0.719); residual +0.107 at g = 6, sign change near g ≈ 50, residual SD 0.022; Cramér running max flat below the Granville threshold 2e^(−γ) ≈ 1.1229; best unconditional bound Baker–Harman–Pintz O(p^0.525). Please spot-check the correlation figures and the Granville constant.
- The "sidesteps obstructions from small primes" intuition for why 6/30 are favoured is my plain-language gloss on the Hardy–Littlewood weight (product over odd prime divisors of g/2 of (p−1)/(p−2)); the paper gives the formula, not the metaphor — flag if you'd rather state the product explicitly.
- **Figure suggestions (paper figures not embedded — source is a Drive PDF I couldn't extract images from cheaply).** Two are worth adding to `site/figures/`: (1) **Fig 2**, empirical frequencies vs Hardy–Littlewood weights with the 6/30 peaks — the evidence my inline right-panel schematises; (2) **Fig 4**, the running maximum of the Cramér ratio flattening below the Granville line. Fig 3 (the r ≈ 0 scatter) is the pivot but my left panel stands in for it.
- Student stays anonymous; the paper carries a name and school — neither appears here.
- The inline SVG is an original schematic (illustrative scatter + comb, real values r = 0.05 and the 6/30 peaks), not paper data.
