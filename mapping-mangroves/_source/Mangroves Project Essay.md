SUGGESTED TITLE: What Happens When a Forest Dataset Meets a Mangrove?
SUGGESTED LEDE: A comparison of two widely used global datasets in Mumbai turned into a more interesting question: not where mangroves are, but what a satellite product means when it says a forest is "there."
ESSAY TYPE: C
WORD COUNT: ~1320
EXTENSIONS SECTION: Yes
IMAGES USED: 3 paper figures, 1 image suggestion, 1 optional new figure from data

A mangrove is obviously a forest until you ask a global dataset to prove it every year. Then the answer becomes strangely unstable.

What drew me to this project was not just the ecology of Mumbai's coastline, though that is interesting enough on its own. It was the fact that two open-access datasets, both widely used and both superficially plausible, could look at the same urban mangrove system and tell slightly different stories. That is usually where the science gets interesting: not when the map looks clean, but when the disagreement forces you to ask what exactly is being measured.

[IMAGE SUGGESTION: A simple locator map of Mumbai's coastal mangrove belt, with Thane Creek, Mahim, Versova, and Gorai labeled. Recommended source: generate from OpenStreetMap coastline and AOI boundary data rather than using a stock image. Placement: immediately after the opening paragraph.]

## Two datasets, two ideas of a mangrove

At first glance, the comparison seems straightforward. Hansen Global Forest Change is a general forest-monitoring product built largely from Landsat optical imagery at 30 m resolution. It is very good at answering a broad question: where is tree cover, and where has it changed? Global Mangrove Watch is a more specific product. It is built for mangroves, uses radar as well as optical data, and bakes coastal and intertidal context into the classification.

Those are not minor technical differences. They amount to two different ideas of what counts as evidence. Hansen is asking whether a pixel looks enough like forest to cross a canopy threshold. GMW is asking whether a coastal wetland pixel belongs to a mangrove system.

Mumbai is a good place to make that distinction matter. Its mangroves are ecologically important and geographically awkward: muddy, intertidal, fragmented, and pressed against one of the densest urban regions in the world. They sit in exactly the sort of landscape where mixed pixels, tidal inundation, cloud-contaminated optical scenes, and threshold effects are likely to show up. If a generic forest product is going to wobble anywhere, it will wobble here.

So the first job was not analysis in the glamorous sense. It was making the datasets comparable at all. Both rasters had to be projected into a common CRS, EPSG:32643, and aligned on a common grid. I used the GMW mangrove mask as the baseline spatial extent and then asked a narrower question inside that mask: when, and how consistently, does Hansen classify those same pixels as forest?

That narrowing matters. It turns a vague comparison of two maps into a concrete test. Instead of asking whether the datasets look similar in the abstract, the project asks whether a pixel that a mangrove-specific dataset considers mangrove is treated as stable forest by a generic forest product.

[FIGURE: overlap_disagreement_map.png]
[CAPTION: This is the cleanest single picture of the project. The point is not merely that the datasets disagree, but where they disagree: the mismatches cluster around the messy intertidal edges, where a generic forest classifier should be expected to struggle. This is the strongest candidate for the website hero figure.]

Once the grids were aligned, the basic overlap looked encouraging. Within the study region, the GMW mask covered 1508.85 hectares of mangroves. Roughly 92% of those mangrove pixels were detected as forest at least once by Hansen. If the analysis had stopped there, the conclusion would have been mild and fairly comforting: the generic forest product is imperfect, but it broadly sees the mangroves.

The trouble started the moment I asked the temporal question more carefully.

## The suspicious result

Hansen provides more than a yes-or-no forest signal. It also records the first year and last year a pixel is detected as forest. That makes it possible to do something more interesting than a static overlap map. Inside the GMW mangrove mask, each pixel can be sorted into three classes: never forest, temporary forest, and persistent forest.

This is where the project stopped being a routine comparison and became a lesson in what datasets do under stress.

About 92.34% of the mangrove area fell into the "temporary forest" category. About 7.66% was "never forest." Persistent forest, on the other hand, came out to exactly 0%.

That result is not merely surprising. It is scientifically suspicious.

If one took it literally, the implication would be absurd: Mumbai's mangroves are somehow being detected as forest briefly, intermittently, and then not persisting through the end of the record at all. Mangroves do not behave like a crop that appears and disappears on yearly timescales. The more plausible interpretation is that the classification itself is flickering.

[FIGURE: mangrove_presence_classes.png]
[CAPTION: This is the figure that makes the problem impossible to ignore. The absence of any persistent-forest class is too extreme to read as ecology; it has to be read as a property of the classifier interacting with a difficult landscape.]

The duration analysis says the same thing in a slightly different language. Detection durations were dominated by short intervals, with a median near zero years and very few pixels showing long-lived forest persistence. Spatially, the duration map does not reveal a system that is steadily degrading. It reveals a system that drops in and out of recognition.

[FIGURE: detection_duration_histogram_and_map.png]
[CAPTION: The histogram gives the summary, but the map makes the pattern legible. The short durations are not isolated outliers; they are spread across the mangrove system, which is exactly what one would expect from unstable classification rather than synchronized ecological collapse.]

That distinction is the entire essay. A bad interpretation here would be to turn a classification artifact into a dramatic environmental claim. A better interpretation is more modest and more useful: Hansen does detect mangrove vegetation in Mumbai, but it does not do so in a temporally stable way.

## What the mismatch is really about

Once the result is framed that way, the physics and remote sensing become easier to think about. Mangroves live in an intertidal environment. The same pixel can contain different mixtures of canopy, water, exposed mudflat, and shadow depending on tide stage, season, and image conditions. At 30 m resolution, those mixtures matter. A pixel near a canopy threshold can cross it, then fall back below it, without the ecosystem having meaningfully changed.

This is one of the quiet ways classification systems mislead people. The output looks categorical, but the underlying reality is continuous and messy. A pixel is not deciding whether it is forest. A model is deciding whether the evidence is strong enough, under a particular sensing modality and a particular set of assumptions, to call it forest.

That is also why the comparison with GMW is so useful rather than merely adversarial. GMW is not "better" in some universal sense. It is better for this ecosystem because it was built with this ecosystem in mind. Radar is less vulnerable to the cloud and haze problems that affect optical products, and the mangrove-specific ecological constraints matter precisely in wetlands where inland forest logic begins to fray.

This changed the way I think about dataset choice. The question is not which product is globally correct. The question is what question the product is actually equipped to answer. If I want baseline extent mapping for Mumbai mangroves, GMW is the safer foundation. If I want a tentative annual signal for where a generic forest product thinks tree cover has fluctuated inside mangroves, Hansen can still be useful, but only with caution and only after the mangrove extent has been defined externally.

There is a broader planning point hiding in that conclusion. Open-access geospatial products often enter environmental workflows with an aura of objectivity. But a map is not a neutral mirror. It is a compressed bundle of sensor choices, classification rules, thresholds, and ecological assumptions. In a coastal city such as Mumbai, where mangroves matter for flood buffering, shoreline stability, and environmental regulation, that bundle matters.

What I like about this project is that it resisted the easy ending. It did not produce a neat one-line answer about how much mangrove loss occurred. Instead it exposed a more basic issue: a generic forest product can look persuasive while being unstable in exactly the landscape where many people would be tempted to trust it. That is not a failure of the project. It is the project.

If I were extending it, I would do two things next. The first would be to add a third comparator such as ESA WorldCover or a regionally validated mangrove layer, just to see whether the GMW-versus-Hansen mismatch sits inside a broader consensus or a broader disagreement. The second would be to cleanly audit the first/last-year encoding one more time, because when a result is this stark, it deserves to be challenged before it is interpreted. But even without that extension, the main lesson is already clear. When a forest dataset meets a mangrove, the interesting question is not only what it sees. It is what kind of seeing it was built to do.

## Suggested visual package

**Hero figure recommendation:** use the overlap/disagreement map as the main image. It is the most legible visual summary of the whole project because it shows the geography, the core comparison, and the direction of disagreement in a single glance. For the website version, it should be exported again as a standalone figure with larger labels, a cleaner legend, lighter axes, and a small locator inset for Mumbai.

**Best secondary figures for the essay body:** the mangrove presence classes map, and the detection-duration histogram paired with the duration map. Those two figures carry the interpretive burden of the essay: first that the temporal classification is suspicious, and second that the instability is widespread rather than local.

**Optional figure to generate from the data:** a very simple web-native summary panel showing the three class shares inside the GMW mask — 92.34% temporary forest, 7.66% never forest, 0% persistent forest. This would not replace the map, but it would give the reader the key result immediately before they scroll into the longer explanation.

**Optional figure pair if you want a longer version of the essay:** the first-year and last-year detection maps together. They are useful if the essay leans more heavily into temporal behavior and sensor instability, but they are less effective than the three figures above if the goal is a tight narrative.

## EDITOR'S NOTE

The central numerical claim that needs one more verification pass is the 0% persistent-forest result. It is clearly the most interesting result in the paper, but it is also the most vulnerable to any decoding mistake in Hansen's first/last-year layers.

I chose a Type C framing because the scientifically interesting part of the project is the classifier instability, not a clean area-change result. A Type A version is also possible if you want the essay to emphasize remote-sensing methodology and dataset design more explicitly.

The essay assumes the website version should be about the project as an intellectual investigation, not about the submitted paper as such. That is consistent with the explainer prompt, but it does mean I intentionally stripped away most of the paper's formal literature-review posture.

Editorial question 1: do you want the website essay to lean harder into Mumbai as an urban-climate and planning case study, or keep the emphasis on dataset epistemology?

Editorial question 2: do you want one short paragraph on why this matters for civil/environmental engineering workflows, since that theme appears in the mentor dashboard context but not strongly in the submitted manuscript?

Figure choice note: I picked the overlap/disagreement map as the hero because it answers the reader's first question immediately. The alternative would be the presence-classes map, which is more dramatic scientifically, but less intuitive as an entry image because it requires more explanation before it becomes legible.
