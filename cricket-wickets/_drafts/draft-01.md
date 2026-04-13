---
SUGGESTED TITLE: Does the "corridor of uncertainty" actually take wickets?
SUGGESTED LEDE: On testing a piece of coaching folklore against 140,000 Hawkeye deliveries, and on the one result that wouldn't behave.
ESSAY TYPE: C (with A elements)
WORD COUNT: ~1400
EXTENSIONS SECTION: Yes
IMAGES USED: 5 paper figures, 1 explanatory SVG
---

There is a sentence that every cricket coach says at least once a week, usually with the same hand gesture: *pitch it up on a good length, just outside off stump, and the wickets will come*. It is the closest thing cricket has to a folk theorem. The sentence is old enough and confident enough that it mostly goes uninspected. The question I wanted to ask — with a friend who spent the summer cleaning up an IPL ball-tracking dataset — was whether the sentence actually survives contact with ball-level data. The answer turned out to be *mostly yes, with one uncomfortable exception that still bothers me*.

The dataset is a Hawkeye feed from IPL men's matches, one row per legal delivery, and the columns that mattered for this first pass were small and well-defined. Two of them carry almost all the geometric information: `pitch_x` is the lateral distance in metres from middle stump at the point where the ball bounces (negative is leg side, positive is off side), and `pitch_y` is the distance along the pitch from the stumps to where the ball lands. A third column, `dismissal_details`, is either null or carries a short text describing a wicket, and that was enough to construct a binary `is_wicket` label. After dropping rows with implausible pitch coordinates (`|pitch_x| > 2` m or `pitch_y` outside `[0, 22]` m — almost certainly sensor glitches) and filtering out sub-10 km/h ball speeds for the speed plots, the working frame held roughly 140,000 deliveries. That is a large enough sample to look at fine slices without the standard errors swallowing the result.

The first question to press on was the easy one: where, on the two-dimensional `(pitch_x, pitch_y)` plane, do wickets actually happen relative to where the ball is usually pitched? The coaching claim is specifically *relative*. Bowlers target the good-length off-stump channel heavily; the question is whether that region has an *elevated* wicket rate, or whether wickets are just mechanically dense there because the pitch count is dense there.

Before looking at the heatmap, it helps to have a shared picture of the zones coaches actually use. The ball's length — its `pitch_y` — gets carved into five discrete bands that every commentator falls back on, and they are not distributed uniformly: Yorker territory is a narrow sliver right at the stumps, Good Length is the disputed region, and "Bouncer or Very Short" is a huge tail that stretches to the far end of the pitch.

<div class="figure-wrap">
<svg viewBox="0 0 680 220" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Schematic of the five cricket length zones mapped to pitch_y in metres">
  <defs>
    <style>
      .z-label { font-family: 'JetBrains Mono', monospace; font-size: 10px; fill: #6B6460; letter-spacing: 0.04em; text-transform: uppercase; }
      .z-name { font-family: 'Source Serif 4', serif; font-size: 12px; fill: #1a1a1a; font-style: italic; }
      .z-yorker { fill: #f2d0b8; stroke: #c8c0aa; stroke-width: 1; }
      .z-full   { fill: #f6dcae; stroke: #c8c0aa; stroke-width: 1; }
      .z-good   { fill: #c8e6d0; stroke: #c8c0aa; stroke-width: 1; }
      .z-short  { fill: #b8d4e0; stroke: #c8c0aa; stroke-width: 1; }
      .z-bouncer{ fill: #9fb6cc; stroke: #c8c0aa; stroke-width: 1; }
      .stumps   { fill: #272540; }
      .tick     { stroke: #6B6460; stroke-width: 0.6; }
      .tick-lbl { font-family: 'JetBrains Mono', monospace; font-size: 9px; fill: #6B6460; }
    </style>
  </defs>
  <!-- pitch: left = stumps (0m), right = 22m -->
  <g transform="translate(40, 60)">
    <!-- stumps marker -->
    <rect class="stumps" x="-4" y="10" width="4" height="40"/>
    <!-- zones: widths proportional to metres, total 600px for 22 m -->
    <!-- Yorker 0-3m -->
    <rect class="z-yorker" x="0" y="10" width="81.8" height="40"/>
    <!-- Full 3-5.5m -->
    <rect class="z-full" x="81.8" y="10" width="68.2" height="40"/>
    <!-- Good 5.5-7.5m -->
    <rect class="z-good" x="150" y="10" width="54.5" height="40"/>
    <!-- Short 7.5-10m -->
    <rect class="z-short" x="204.5" y="10" width="68.2" height="40"/>
    <!-- Bouncer 10-22m -->
    <rect class="z-bouncer" x="272.7" y="10" width="327.3" height="40"/>
    <!-- tick marks -->
    <g>
      <line class="tick" x1="0" y1="50" x2="0" y2="58"/>
      <line class="tick" x1="81.8" y1="50" x2="81.8" y2="58"/>
      <line class="tick" x1="150" y1="50" x2="150" y2="58"/>
      <line class="tick" x1="204.5" y1="50" x2="204.5" y2="58"/>
      <line class="tick" x1="272.7" y1="50" x2="272.7" y2="58"/>
      <line class="tick" x1="600" y1="50" x2="600" y2="58"/>
      <text class="tick-lbl" x="0" y="70" text-anchor="middle">0</text>
      <text class="tick-lbl" x="81.8" y="70" text-anchor="middle">3</text>
      <text class="tick-lbl" x="150" y="70" text-anchor="middle">5.5</text>
      <text class="tick-lbl" x="204.5" y="70" text-anchor="middle">7.5</text>
      <text class="tick-lbl" x="272.7" y="70" text-anchor="middle">10</text>
      <text class="tick-lbl" x="600" y="70" text-anchor="middle">22 m</text>
    </g>
    <!-- zone labels (rotated where tight) -->
    <text class="z-name" x="40" y="35" text-anchor="middle">Yorker</text>
    <text class="z-name" x="115" y="35" text-anchor="middle">Full</text>
    <text class="z-name" x="177" y="35" text-anchor="middle">Good</text>
    <text class="z-name" x="238" y="35" text-anchor="middle">Short</text>
    <text class="z-name" x="436" y="35" text-anchor="middle">Bouncer / Very Short</text>
    <text class="z-label" x="-8" y="5" text-anchor="end">stumps</text>
    <text class="z-label" x="300" y="100" text-anchor="middle">pitch_y — distance from the stumps along the pitch</text>
  </g>
</svg>
<p class="figure-caption"><em>The five length zones as they actually map to the pitch. The "Bouncer or Very Short" band is much larger than it looks when coaches draw it — anything more than ten metres from the stumps falls into one category, which is already enough to make one suspicious of any effect measured from it.</em></p>
</div>

With that picture held in mind, the overall spatial distribution looks exactly like the coaching story would predict.

<div class="figure-wrap">
<img src="figures/kde_heatmap.png" alt="KDE heatmap of all deliveries overlaid with wicket deliveries in pitch_x and pitch_y coordinates">
<p class="figure-caption">Two-dimensional KDE overlay on the <code>(pitch_x, pitch_y)</code> plane. The bulk of all deliveries sit in a channel just outside off stump between about five and eight metres, which is the textbook "good length" region. The wicket-only density sits on the same channel but slightly fuller — closer to the batter — and a bit tighter laterally. The coaching sentence survives the first look.</p>
</div>

The one-dimensional projections make the contraction easier to see, because you can watch the wicket curve visibly crowd inward relative to the non-wicket one on both axes.

<div class="figure-wrap">
<img src="figures/length_density.png" alt="Density of pitch_y for wicket and non-wicket deliveries">
<p class="figure-caption">Marginal density of <code>pitch_y</code> (length) split by whether the ball was a wicket. Non-wicket deliveries spread broadly from roughly four to ten metres; wicket deliveries pile up in a narrower band between about 4.5 and 7 m, and the wicket mode sits slightly fuller than the non-wicket mode. The lateral axis tells the same story but more gently — wickets concentrate closer to the stump line than the average delivery does.</p>
</div>

So far the story is a tidy vindication of the folk theorem. But the moment you collapse the plane into bar chart form, something misbehaves.

<div class="figure-wrap">
<img src="figures/wicket_rate_all.png" alt="Wicket rate by length zone across all bowlers">
<p class="figure-caption">Wicket rate — fraction of deliveries in each zone that produced a dismissal — across the five length zones, pooled across all bowlers and all match phases. Full and Good Length sit where one would expect, around five to six per cent. Yorkers are a hair behind. Short is the weakest. And then Bouncer / Very Short, at roughly six per cent, is competitive with the best zone on the chart.</p>
</div>

The Bouncer bar is the result that wouldn't sit still. Taken at face value, it looks as though hurling the ball halfway down the pitch is, on average, about as effective a wicket-taking tactic as pitching it on a nagging length just outside off. That is not a conclusion anyone who has watched cricket would accept. It is worth pausing on *why* the result is almost certainly wrong before deciding what to do about it, because the answer turns out to be a useful lesson about how much damage a single pooled axis can do.

Two things are happening at once, and they both inflate that bar. The first is phase mixing. Death-overs bowling is tactically very different from powerplay bowling, and short-pitched deliveries in the final two overs are a high-wicket event — they are being used into set fields with deep fine leg and deep square leg explicitly to convert a mistimed hook or pull into a catch. Pooling those overs together with the middle-overs short balls, which are defensive, artificially shifts the rate upward. The second is the zone definition itself. The "Bouncer or Very Short" label runs from 10 m all the way to 22 m. That is more than half the pitch. Any full toss that skewed past 10 m (there are surprisingly many in the filtered data) goes into the same bucket as a genuine chest-high bouncer. The bucket is too generous, and generous buckets look more effective than they are because they absorb rare but high-wicket deliveries at both ends of the range.

The correct response to the misbehaving bar is not to throw out the finding. It is to stratify — to re-compute the wicket rate separately by bowling style, or separately by match phase, and see whether the Bouncer anomaly survives the split. And when you do that, the story becomes legible in a way that the pooled chart obscured.

<div class="figure-wrap">
<img src="figures/wicket_rate_pace.png" alt="Wicket rate by length zone for pace bowlers only">
<p class="figure-caption">The same bar chart restricted to pace bowlers. Full is still at the top. Bouncer is still elevated but no longer competitive with Good Length in the way the pooled version made it look. The pattern that survives the restriction — Full and Good Length as the reliable wicket-takers, Short as the weakest, Yorker as tactically important — is much closer to the coaching picture. The anomaly was a pooling artifact.</p>
</div>

Splitting by bowling style sharpens the picture further. Spin and pace are not merely two versions of the same process. They generate wickets through geometrically different mechanisms, and the heatmaps make that visible without any further modelling.

<div class="figure-wrap">
<img src="figures/pace_vs_spin_heatmap.png" alt="Wicket density heatmaps for pace and spin bowlers, side by side">
<p class="figure-caption">Wicket-density heatmaps for pace (left) and spin (right). Pace wickets spread out along the off-stump corridor, with the mode sitting around <code>pitch_x ≈ -0.4</code> m and <code>pitch_y</code> between six and eight metres, and the distribution tailing meaningfully into shorter lengths. Spin wickets form a much tighter, more central cluster — almost on the line of the stumps, shorter lengths between four and six metres. The two styles are producing wickets out of different regions, and the pooled story misses this entirely.</p>
</div>

There is a second, related finding that seems worth flagging. For seam bowlers specifically, ball speed carries almost no independent signal about wicket probability.

<div class="figure-wrap">
<img src="figures/ball_speed_kde.png" alt="Kernel density of ball speed for wicket vs non-wicket deliveries, seamers only">
<p class="figure-caption">KDE of ball speed for seam bowlers, split on <code>is_wicket</code>. The wicket and non-wicket curves overlap almost completely through the bulk of the professional speed range. Whatever is making a delivery a wicket ball, it is not pace by itself. (The small cluster at near-zero is sensor noise that survived the filter and should be ignored.)</p>
</div>

Here is the overall shape of the thing. The "good length just outside off" rule of thumb survives, *descriptively*: when you look at where wickets actually happen relative to where the ball gets pitched, that region really is doing disproportionate work. But any version of the analysis that reports a single pooled wicket rate per zone will also hand you the Bouncer anomaly, and that anomaly will make you believe something about bouncers that is mostly the fault of how the zones were drawn and how the phases were averaged. The finding and the artifact travel together in the same table, and the only way to separate them is to stratify until the artifact dissolves.

## An honest caveat that should go before any stronger claim

The one thing that needs restating before any of this is used in an actual coaching conversation is that it is all observational. Bowlers do not deliver uniformly across the `(pitch_x, pitch_y)` plane — they target the "good length outside off" region precisely because they already believe it is effective, which means the high wicket rate in that region is partly a selection effect and partly a real property of the region. The present analysis cannot separate the two. A rigorous causal version of the same question would need to condition on bowler identity, batter handedness, phase, and the field setting, and would probably need a matched-comparison design between balls that were *intended* for a given zone and balls that actually landed in it. None of that is in this first pass. What this pass does well is describe the joint distribution clearly enough that the next pass knows where to push.

---

## EDITOR'S NOTE (not for publication)

- Figure filename mapping (`length_density`, `kde_heatmap`, `wicket_rate_all`, `wicket_rate_pace`, `pace_vs_spin_heatmap`, `ball_speed_kde`) was inferred from page order in the extracted PDF images; spot-check against Figures 1, 3, 4, 5, 7, 8 in Yuvaan's paper before publication.
- The "Bouncer anomaly" framing is mine and is *supported by* but not explicitly written as a narrative pivot in the original paper — the paper flags phase mixing and zone width as the two candidate explanations in the Discussion. I've promoted those to the structural centre of the essay because they read as the most interesting finding.
- Ball-speed KDE caveat about the near-zero cluster is directly from the paper and retained.
- The causal-inference paragraph at the end paraphrases the Scope and Limitations section; the matched-comparison design suggestion is mine.
- Collaborator (Yuvaan Pandey) is not named per the house style rule, but is credited on the paper. Worth a check that Ninaad is OK with the "a friend who spent the summer cleaning up an IPL ball-tracking dataset" framing.
- The length-zones explanatory SVG is an original diagram; the zone cutoffs come directly from the Methods section of the paper.
