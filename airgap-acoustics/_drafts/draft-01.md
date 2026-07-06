---
SUGGESTED TITLE: Can a computer leak secrets through its fan?
SUGGESTED LEDE: On stealing data from a machine connected to nothing by listening to its cooling fan — and on a covert channel that fades with distance instead of failing outright.
ESSAY TYPE: C (with A elements)
WORD COUNT: ~1320
EXTENSIONS SECTION: Yes
IMAGES USED: 1 explanatory SVG (inline); 2 paper-figure suggestions flagged for Ninaad
---

The most secure computer is one that is not connected to anything. Unplug it from every network, wired and wireless, and you have an air-gapped machine: whatever secrets it holds cannot be siphoned out over the internet, because there is no internet to siphon them over. This is how genuinely sensitive systems are protected — in defence, in finance, in critical infrastructure. The catch, and it is the whole subject of a small project I worked on with a student, is that an air gap is a wall built against one kind of threat. It stops data from leaving over the network. It does nothing about data leaving through the air.

The trick that makes this concrete is almost comic in its simplicity. Suppose malware has already made it onto the isolated machine — carried in on a USB stick, say. It can read the secrets, but it has no network to send them over and, on many secure builds, no speaker to play them out loud. What it does have is a cooling fan, and it can change the fan's speed. A fan spinning faster makes a higher-pitched sound than a fan spinning slowly. So run the fan at one speed to mean zero and a faster speed to mean one, and you have turned a cooling component into a transmitter, spelling out a message in pitches. A microphone nearby — a phone left casually on the desk — records the hum, and software on the far end reads the pitches back into bits. This is the Fansmitter technique, and the point of the replication was to build it from ordinary parts and see how well it actually works.

The build was as everyday as possible. A consumer fan-control app drove a single GPU fan between two duty settings, twenty-five and a hundred per cent, which produced two distinguishable low tones — around forty-seven hertz for a zero and seventy for a one. A phone running a physics-teaching app recorded the audio and exported its running spectrum. Because fans are heavy and slow to change speed, each bit had to be held for a full five seconds, which fixes the transmission rate at a glacial tenth of a bit per second or so — enough for a password over a couple of minutes, and not much more. Six-bit messages were sent at distances from twenty to fifty centimetres, in a normal, noisy shared room, and a decoding script tried to recover them from the recorded pitches, searching over the timing because a hand-triggered fan never switches exactly on the beat.

Up close, it works. At twenty centimetres the two tones sit in clearly separated bands and the six-bit patterns come back correctly. But move the microphone away and let the ordinary noise of a room compete, and the channel starts to come apart: the pitch tracker wanders off onto harmonics and stray peaks, the two bands blur into each other, and beyond short range the message can no longer be recovered with any consistency.

<div class="figure-wrap">
<svg viewBox="0 0 640 330" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Error rate against distance for the fan covert channel. Both the binary and the softer confidence-weighted error rise as the microphone moves from 20 to 50 centimetres, but the soft error sits consistently below the binary error, showing the channel degrades gradually rather than failing all at once. A dashed line marks the fifty-per-cent, coin-flip level.">
  <defs><style>
    .aglbl { font-family: 'JetBrains Mono', monospace; font-size: 10.5px; fill: #6B6460; letter-spacing: 0.03em; }
    .agn   { font-family: 'JetBrains Mono', monospace; font-size: 10px; fill: #1A1714; }
    .agh   { font-family: 'Source Serif 4', serif; font-size: 12.5px; font-style: italic; fill: #1A1714; }
  </style></defs>
  <line x1="60" y1="40" x2="60" y2="280" stroke="#6B6460" stroke-width="1"/>
  <line x1="60" y1="280" x2="600" y2="280" stroke="#6B6460" stroke-width="1"/>
  <text class="aglbl" x="24" y="44">error</text>
  <text class="aglbl" x="470" y="303">distance →</text>
  <line x1="60" y1="60" x2="600" y2="60" stroke="#2A6B6B" stroke-width="1" stroke-dasharray="5 5"/>
  <text class="agn" x="596" y="55" text-anchor="end">50% — a coin flip</text>
  <polyline points="90,227 243,170 396,113 549,82" fill="none" stroke="#1A4F4F" stroke-width="2.6"/>
  <circle cx="90" cy="227" r="4" fill="#1A4F4F"/>
  <circle cx="243" cy="170" r="4" fill="#1A4F4F"/>
  <circle cx="396" cy="113" r="4" fill="#1A4F4F"/>
  <circle cx="549" cy="82" r="4" fill="#1A4F4F"/>
  <polyline points="90,245 243,196 396,148 549,113" fill="none" stroke="#2A6B6B" stroke-width="2.6" stroke-dasharray="7 4"/>
  <circle cx="90" cy="245" r="4" fill="#2A6B6B"/>
  <circle cx="243" cy="196" r="4" fill="#2A6B6B"/>
  <circle cx="396" cy="148" r="4" fill="#2A6B6B"/>
  <circle cx="549" cy="113" r="4" fill="#2A6B6B"/>
  <text class="agh" x="415" y="98">binary error</text>
  <text class="agh" x="415" y="150">soft error</text>
  <text class="agn" x="90" y="298" text-anchor="middle">20cm</text>
  <text class="agn" x="243" y="298" text-anchor="middle">30cm</text>
  <text class="agn" x="396" y="298" text-anchor="middle">40cm</text>
  <text class="agn" x="549" y="298" text-anchor="middle">50cm</text>
</svg>
<p class="figure-caption"><em>How the channel fails matters as much as that it fails. Two error measures rise as the microphone retreats: the hard binary error — was the bit right or wrong — and a softer score that asks how close the evidence came to the correct answer. The soft error runs consistently below the binary error, which means the channel does not snap off. It fades. Even where full bit recovery breaks down, the signal still leans the right way.</em></p>
</div>

The most interesting result is hiding in the gap between those two curves, and it is worth being careful about. Every recovered bit was scored two ways. The blunt way is binary: for each of the six windows the decoder takes a vote — what fraction of the pitch samples in that window sit in the high band rather than the low — and calls the bit a one if the vote crosses a half, a zero otherwise. Get it wrong and that is a whole bit of error. The gentler way keeps the vote itself: a window where seventy per cent of the samples pointed the right way is scored as nearly correct even if some noise nudged the final tally; a window that was confidently, badly wrong is penalised hard. Across the distances, this soft error came out consistently below the binary error. The reading is that when a bit flipped, it usually flipped narrowly — the evidence was sitting near the boundary, not pointing firmly the wrong way. The channel does not have a clean cliff past which nothing gets through. It degrades gradually, and structure lingers in the signal even after the last cleanly decoded bit.

That distinction is exactly what makes this kind of channel awkward to defend against, and the study's own countermeasure follows from it. If the channel died abruptly at some range, you could relax anywhere past it. Because it fades instead, a defence that only pushes the decoder's success rate down still leaves recoverable structure behind for a more patient attacker. The clarity of the signal itself has to be attacked. The fix the paper proposes is neat precisely because it is so cheap: have the operating system inject small, random jitter into the fan's speed and timing — a bit of wobble on the duty cycle, a little irregularity in when it changes. To a person the fan just sounds like a fan. To the covert channel it is poison, because the two carefully separated tones smear together and the transmitter can no longer keep time with the receiver. No new hardware, no locked room; you simply make the fan a worse liar.

I want to be careful not to oversell what was built. In this form the channel is slow to the point of absurdity, works only across a desk, is thrown by the ordinary noise of a room, and can be given away by the very fan-revving it depends on — a lab demonstration far more than a practical weapon. But the principle underneath it is not fragile at all, and that is the part worth keeping. An air gap is a wall raised against the network, and the fan is a reminder that a wall only stops what it was built to stop. Any component that can be driven at two distinguishable rates — a fan, a disk, a power supply, a screen's brightness — is a component that can be made to talk, in a medium nobody thought to guard. The secret does not have to escape the way you were watching for.

## An honest caveat that should go before any stronger claim

This was a feasibility replication on a single ordinary desktop, not a demonstration of a deployable attack. One controllable fan, one machine, one session, sixteen short runs in a single straight line at four distances, in an uncontrolled and genuinely noisy room, with the fan triggered by hand — which is why the decoder had to search over the timing at all. The error-versus-distance behaviour should be read as the shape of a trend rather than a benchmark: the numbers would move with a different fan, a different room, or a better receiver, and the study makes no claim otherwise. The proposed jitter countermeasure is argued for but not itself tested here. What the work honestly establishes is narrow and, I think, sufficient: an everyday machine with no speaker and no network can be made to emit a decodable acoustic signal from its cooling fan at close range, that signal degrades gracefully rather than cliffing as conditions worsen, and the cheapest place to break it is the clarity of the sound, not the cleverness of the decoder.

---

## EDITOR'S NOTE (not for publication)

- **Type C framing** — a replication that partly confirms the effect and is honest about its fragility. I've made the pivot the soft-vs-binary gap (graceful degradation) rather than the bare "it works up close," because that nuance is the paper's most interesting and least obvious result and it drives the countermeasure logic. Confirm you're happy with that emphasis.
- Numbers/details from the paper: two duty states 25% / 100%; observed tones ≈ 47 Hz (0) and 70 Hz (1) (nominal ≈ 67 / 107 Hz); 5 s per bit → ≈ 0.1–0.15 bits/s; 6-bit messages; distances 20–50 cm; 16 trials; phyphox on an iPhone; FanControl app. The error-vs-distance figures in my inline diagram are **illustrative of the reported trend, not exact values** — the paper gives Figure 4 (binary vs soft vs distance) but not a clean per-distance table, so please treat the curve as schematic and confirm you're OK with that.
- **Anonymity / institutions:** the source lists suggested reviewers including you and "Pangea Society" — none of that appears here, and the student is unnamed ("a student I worked with"). Please double-check I haven't leaked any identifying detail.
- **Figure suggestions (paper figures not embedded — source is a Drive docx I couldn't extract images from cheaply).** Two would strengthen the page if added to `site/figures/`: (1) **Fig 3**, expected vs decoded bit patterns near and far — the clearest picture of the degradation, and a good companion to the hero; (2) **Fig 4**, error vs distance for binary and soft scoring, which my inline diagram schematises (so add it only if you want the paper's own numbers shown).
- The hero is an original schematic (a fan-tone spectrogram dissolving into noise); the inline curve is original and illustrative. Neither is paper data.
- Framed the threat model straight from the paper (air gap defends the network, not the physics; four covert-channel families). The "make the fan a worse liar" line is my gloss on the jitter countermeasure — flag if too cute.
