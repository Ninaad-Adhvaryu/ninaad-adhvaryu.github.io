---
title: When a Gas Becomes One
lede: On Bose-Einstein condensation, dipolar quantum gases, and a map of the vortex states that appear when matter is made to spin near absolute zero.
type: D (concept explored)
status: draft-v1
date: 2026-03-30
---

# When a Gas Becomes One

At around 170 nanokelvin — a temperature roughly a hundred million times colder than the cosmic microwave background — a dilute gas of atoms does something that has no classical explanation. It stops behaving like a collection of individual particles and becomes, in a precise quantum-mechanical sense, one.

This is Bose-Einstein condensation: a phase transition in which a macroscopic fraction of atoms all fall into the same quantum ground state. What makes this remarkable is not the low temperature alone but the mechanism. The atoms do not freeze. They do not crystallise. They remain a dilute gas, separated by distances far larger than their physical size. What changes is not their positions but their quantum identity — the wave functions of individual atoms begin to overlap, and when the overlap becomes total, the system suddenly behaves as if it were described by a single, coherent wave function spanning the entire cloud.

My thesis was about what happens when you add something to this picture: rotation, and long-range anisotropic interactions, in a condensate made of dysprosium — one of the most magnetic atoms on the periodic table. The result was a phase diagram: a map of the distinct vortex states that appear across the parameter space of rotation and interaction strength.

## The Statistics of Nothing

Particles in quantum mechanics come in two fundamental varieties, distinguished by a single rule about what happens when you exchange two identical ones. Fermions acquire a minus sign — the origin of the Pauli exclusion principle. Bosons acquire no sign change. Any number of bosons can occupy the same state simultaneously.

This difference has a direct consequence for the statistical distribution of particles across energy levels. In the grand canonical ensemble, the mean occupation number of a state with energy ε_i is the Bose-Einstein distribution:

    n_i = 1 / (exp(β(ε_i − μ)) − 1)

The −1 in the denominator is everything. As μ approaches ε₀ from below, the ground-state occupation diverges. At a critical temperature T_c, this happens, and the ground state occupation becomes macroscopic:

    T_c = 3.31 ℏ² n^(2/3) / (m k_B)

Below T_c, the condensate fraction grows as:

    n₀/n = 1 − (T/T_c)^(3/2)

## Two Kinds of Interaction

[Contact interaction: g_s δ(r), scattering length a_s, Feshbach resonances]

[Dipolar interaction: V_dd(r,θ) = (μ₀μ_m²/4π)(1−3cos²θ)/r³]

[ε_dd parameter: ratio of dipolar to contact strength]

## One Equation for Everything

[GPE derivation outline, mean-field approximation, Thomas-Fermi limit]

    μψ = (−ℏ²/2m ∇² + V_ext + g_s|ψ|²)ψ

## What Order Means

[One-body density matrix, ODLRO, symmetry breaking, order parameter]

    ρ^(1)(r,r') → n₀ ≠ 0 as |r−r'| → ∞

## The Physics of Not Rotating

[Irrotational flow, v = (ℏ/m)∇φ, quantised circulation, vortex cores, Abrikosov lattice]

    Γ = l h/m

## The Dipolar Difference

[Anisotropy of V_dd, combined potential, ε_dd > 1, lattice distortions, structural phase transitions]

## A Map of What's Possible

[Phase diagram across (Ω̂, ε_dd) space, numerical GPE in rotating frame, results, reflection on what the map means]

---

## EDITOR'S NOTES (not for publication)

**Claims to verify:**
- T_c formula coefficient (3.31): derived from ζ(3/2) · Γ(3/2) / (2π)^(3/2); correct.
- Condensate fraction exponent 3/2: standard ideal gas result, correct.
- Dysprosium magnetic moment ~10μ_B: standard literature value, verify with thesis.
- ε_dd formula: double-check prefactor (12π vs 3π conventions vary across references).

**Thin sections:**
- Thomas-Fermi approximation gets brief treatment; expand if needed.
- Quantum fluctuations / supersolid section in closing paragraph is brief — could expand into its own section if the page feels truncated.
- The actual numerical results of the thesis are placeholder — add specific figures and numbers when thesis figures are available.

**Questions for Ninaad:**
1. Do you want to describe the specific vortex configurations found (e.g., triangular → square transition at ε_dd ≈ X)?
2. Are there thesis figures (phase diagram plot, density profiles, vortex lattice images) you'd like to embed?
3. The callout at the end mentions imaginary-time propagation and split-step Fourier — confirm these are accurate method descriptions.
4. Should the dysprosium section mention specific experiments (e.g., Chomaz, Pfau groups) or stay general?
