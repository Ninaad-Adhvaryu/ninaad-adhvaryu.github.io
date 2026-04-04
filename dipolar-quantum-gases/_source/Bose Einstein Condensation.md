---
type: concept
tags: []
aliases: [BECs, BEC, Bose Einstein Condensates, Bose-Einstein Condensation, Bose-Einstein Condensates]
status: growing
---
Sources: 
- [Pitaevskii 2003 - Bose-Einstein Condensation](zotero://select/items/1_XT6439XH) 
- [Huber 2013 - Experimental and Theoretical Aspects of Quantum Gases.pdf](zotero://select/items/[Adhvaryu undefined - Dipolar Quantum Gases under Rotation](zotero://select/items/1_MRA5Q9K6)1_72VMSXQR) 
- [Adhvaryu 2023 - Dipolar Quantum Gases under Rotation](zotero://select/items/1_MRA5Q9K6)
## Long Range Order, Symmetry Breaking and Order Parameter

### One-body density matrix and long-range order




## Ideal Bose Gas

Developing a description of the non-interacting (ideal) Bose gas helps predict many of the phenomena seen in actual BECs. 

### Ideal Bose Gas in Grand Canonical Ensemble

Probability of a system with N' particles, in state k and with energy $E_k$ , 

$$ P_{N'} (E_k) = \frac{e^{\beta (\mu N' - E_k)}}{Z (\beta, \mu)} $$
where $\beta = \frac{1}{k_B T}$ and $\mu$ is the chemical potential of the reservoir with which the system is in thermal equilibrium. 

Remember this is the *probability* of finding a configuration with N' particles.

$Z (\beta, \mu)$ is the [[grand canonical ensemble]], 

$$
Z (\beta, \mu) = \sum_{N' = 0} e^{\beta \mu N'} Q_{N'} (\beta)
$$
where $Q_{N'} (\beta)$ is the [[canonical partition function]] which has to be summed over the complete set of eigenstates of the Hamiltonian with energy $E_k$.

After this point we find the thermodynamic behavior of the system, the entropy and total number of particles.

Eventually, the [[grand potential function]], $\Omega$, reduces to, for uniform systems,
$$ \Omega = - P V $$where P is the pressure an V is the volume. 

Now, we can consider a system described by the independent particle Hamiltonian, 
$$\hat{H}=\sum_i \hat{H}_i^{(1)}$$
here the eigenstates $k$ are defined by specifying the set of ${\{n_i\}}$ of microscopic occupation numbers $n_i$ of the single-particle states, obtained by solving the [[Schrodinger equation]].
$$ \hat{H}^{(1)} \varphi_i(r) = \epsilon_i \varphi_i (r)$$
For the independent particle Hamiltonian, we are able to find the grand canonical partition function (above) exactly and rewritten,

$$
Z = \sum_{n_{0}} \left( e^{\beta (\mu - \epsilon_0)} \right)^{n_0}  

\sum_{n_{1}} \left( e^{\beta (\mu - \epsilon_1)} \right)^{n_1} 

...
$$
the sum here will extend over all integer values for the case of Bose statistics and for 1,2 for Fermi statistics.

This sum form of grand canonical partition function can be inserted into the equation for grand canonical potential, 

$$
\Omega = k_B T \sum_{i} ln \left( 1 - e^{\beta ( \mu - \epsilon_i)} \right).
$$
The total number of particles, $N=-\frac{\partial \Omega}{\partial \mu}$, gives the total number of particles for a Bose gas as
$$
N = \sum_i \frac{1}{e^{\beta(\epsilon_i - \mu)} - 1}.
$$

Which is written as the sum of the average occupation numbers for each single-particle state,
$$
\begin{align}
	n_i &= - \frac{\partial}{\partial \beta \epsilon_i} 
	ln Z \\
	&= \frac{1}{e^{\beta(\epsilon_i - \mu)} - 1}
\end{align}
$$
This hints at an important physical constraint: $\mu < \epsilon_0$, the chemical potential of the ideal Bose gas must be lower than the lowest eigenvalue of the single-particle Hamiltonian $H^{(1)}$.

The violation of this condition results in a negative value for the occupation number of the states with energy smaller than $\mu$. 

As $\mu \rightarrow \epsilon_0$, the occupation number of the lowest energy state becomes larger. This is the phenomena of Bose-Einstein condensation. 

(a discussion of how the temperature relations of ideal gas model give rise to a critical temperature below which BECs occur)

**Switching to Thesis Notes**

A Bose gas is composed of Bosons, which are identical particles with a wave-function that is symmetric under particle exchange. 

The distribution function of a system of bosons
$$ %distribution function
n_i = \frac{g_i}{e^{\beta(\epsilon_i - \mu)} - 1}
$$

^36f6bf

is characterised by energy levels, $\epsilon_i$, degeneracy, $g_i$. 

Now, we transition from the discussion of discrete energy levels to continuous energy levels, switching [[#^36f6bf|the distribution function]] from a sum over states to an integral,
$$\begin{align} %\tag{1} \label{eq: bose-continuous}
	N \approx \int d\epsilon \frac{1}{e^{\frac{\epsilon - \mu}{k_B T}} - 1} g(\epsilon)
\end{align}
$$
where $\epsilon$ is the density of states, we have also set the degeneracy to 1.  

- [ ] Add Equation reference beyond this point!

The density of states for a three-dimensional homogeneous system is

$$\begin{align}
	g(\epsilon) = V \frac{\sqrt{2}}{3 \pi^2 \hbar^3} (m)^\frac{3}{2} \sqrt{\epsilon}
\end{align}$$

where $V$ is the volume and $m$ is the mass.

We will now explore how Equation \ref{eq: bose-continuous} behaves when additional particles are introduced into the system, while keeping the temperature fixed.

By combining Equations \ref{eq: bose-continuous} and \ref{eq: 3d-density-states}, we can express the density

$$\begin{align}
	n = \frac{N}{V} = \frac{m^\frac{3}{2}}{\sqrt{2} \pi^2 \hbar^3} \int d\epsilon \frac{\epsilon^\frac{1}{2}}{e^\frac{\epsilon - \mu}{k_B T}}
\end{align}$$

As the density increases, $\mu$ must also increase, while remaining negative.

Leading to 

$$\begin{align} %\label{eq: bose-density-mu0}
	n (\mu = 0) &\ = \frac{m^\frac{3}{2}}{\sqrt{2} \pi^2 \hbar^3} \int d\epsilon \frac{\epsilon^\frac{1}{2}}{e^\frac{\epsilon - \mu}{k_B T}} \\ \nonumber
	&\ = \frac{m^\frac{3}{2}}{\sqrt{2} \pi^2 \hbar^3} (k_B T)^\frac{3}{2} \int dx \frac{\sqrt{x}}{e^x -1}
\end{align}$$

^58cb34

where $x = \frac{\epsilon}{k_B T}$.

The evaluation of Equation $\eqref{eq: bose-density-mu0}$ 

$$\begin{align}
	n_c = \Gamma (3/2) \zeta (3/2) \frac{m^\frac{3}{2}}{\sqrt{2} \pi^2 \hbar^3}
\end{align}$$

is in term of Gamma function $\Gamma$ and the Riemann zeta function $\zeta$.

However, this expression shows the density of states is bounded and independent of the particle number.

The underlying issue arises from Equation \ref{eq: bose-continuous} when transitioning from discrete to continuous states. The transition, as currently formulated, does not hold when the density of states approaches zero. This can be rectified by considering the lowest energy state in addition to other excited states, yielding \$n = n_0 + n_{\text{ex}}$\

$$\begin{align}
	n_0 = \frac{1}{V} \frac{1}{e^\frac{-\mu}{k_B T} - 1} ; \
	n_{ex} = \frac{m^\frac{3}{2}}{\sqrt{2} \pi^2 \hbar^3}  \int d\epsilon \frac{\epsilon^\frac{1}{2}}{e^\frac{\epsilon - \mu}{k_B T}}
\end{align}$$

As new particles are added $\mu$ must approach zero and $\(n_{ex}\)$ is bound as seen in Equation \ref{eq: bose-density-mu0-fixed} and $\(n_0\)$ grows without an upper-bound. Physically, any new particles added to the system, over the critical density, must then go to ground-state. *This is Bose-Einstein condensation.*

The critical density, $\(n_c\)$ can be expressed as the thermal de-Broglie wavelength, $\lambda_{T}^3$

$$\begin{align}
	n_c = 2.3 \frac{2}{\sqrt{\pi}} \frac{1}{\lambda_{T}^3}
\end{align}$$

Physically, this can be understood to be how far the wave-function of particles extends in real space.

We can understand that the phenomenon of BEC will occur as the inter particle distance approaches the de Broglie wavelength, with critical temperature

$$\begin{align}
	T_c = 3.31 \frac{\hbar^2 n^{\frac{2}{3}}}{m k_B}
\end{align}$$

and condensate fraction

$$\begin{align}
	n_0 = 1 - \left( \frac{T}{T_c} \right )  ^\frac{3}{2}
\end{align}$$
### Ideal Bose Gas in a Box

(add from class notes)

- [ ] Add content from the [ETH Notes](https://ethz.ch/content/dam/ethz/special-interest/phys/theoretical-physics/cmtm-dam/documents/qg/Chapter_01.pdf)

## Interacting Bose Gas

At low temperatures, an interacting atomic system exhibits behaviours that significantly impact its phase and properties. One of the key phenomena that occur in such conditions is three-body recombination, wherein three atoms come together and form molecules. This process has a significant influence on the system, often shifting it towards a solid state of matter due to the formation of molecular structures. A BEC phase is only meta-stable for interacting atoms if the density remains sufficiently low to prevent three-body interactions.

When the atoms are more dilute, with a typical inter-atomic spacing of the order of $10^2$ nm, two-body interactions tend to dominate the behaviour of the system.

The prevalent two-body interactions in such dilute atomic gases can be effectively modelled using s-wave scattering theory.

This theory allows for a mathematical understanding of the collisions between two atoms and offers valuable insights into the interactions that occur at the atomic level.

### Contact Interaction

The behaviour of neutral atoms in a Bose-Einstein Condensate (BEC) is influenced by the Van der Waals force between atoms, typically described by the Lennard-Jones potential

$$\begin{equation} %\label{eq:LJ-Pot}
	V(\textbf{r}) = \frac{A}{r^{12}} - \frac{B}{r^6}
\end{equation}
$$
where r is the inter-particle distance and A and B are species-specific constants. First term is an overlap of electron orbitals leading to an electrostatic repulsion, the second term describes the long-range interaction.

![[Bose Einstein Condensation-img-2405130812.png]]

In the absence of relativistic spin-spin and [[spin-orbital interactions]], the [[Schrodinger equation]] for two colliding atoms can be written as

$$ 
\begin{equation} %\label{eq:sq-two-particles}
	\left( \frac{-\hbar^2}{2m_{r}} \nabla + V(\textbf{r}) - E \right)  \psi(\textbf{r}) = 0
\end{equation}
$$
where $\textbf{r}$ is the relative distance between particles, and $m_r$ is the reduced mass.

We use an Ansatz, a sum of the incoming wave and the scattered wave,

$$\begin{equation} %\label{eq:two-particle-ansatz}
	\psi(\textbf{r}) = e^{i\textbf{k}\cdot\textbf{r}} + \psi_{scat. wave}
\end{equation}
$$

(see notes from thesis for detail)

From here, as we are ignoring the [[bound state solutions]] and focusing on the [[scattering states]], their energy is $E>0$. 

- [ ] Better understand the line: a metastable Bose Einstein condensate the full V (r) would necessarily lead to wrong thermodynamic results, i.e., a crystal.
- [ ] Add discussions about [[Feshbach resonances]]

This can be inserted into the pseudo-potential, 

$$\begin{equation}
	V_s (r) = g_s \cdot \delta (r)
\end{equation}$$

why this form of pseudo-potential can be applied to this situation can be found in [Pethick 2008-09-11 - Bose–Einstein Condensation in Dilute Gases](zotero://select/items/1_39QCWYZ3)

where $\delta$ is the Dirac delta, and $g_s$ is defined

$$\begin{equation} %\label{eq:contact-strength}
	g_s = \frac{4 \pi \hbar^2}{m} a_s
\end{equation}$$

The entire contact interaction can is described by varying the scattering length $a_s$, which can be positive or negative- depending on [[Feshbach resonances]].

### Dipolar Interaction

Dysprosium atoms in the ground state possess a large magnetic moment (μm ≈ 10μB) and experience the magnetic dipole-dipole interaction, also known as dipolar interaction. In contrast to the short-range contact interaction this is anisotropic and long-range.

To achieve alignment of dipoles, an external magnetic field is applied, resulting in polarization of the atom cloud.

Dipole-dipole interaction potential, $V_{dd}(r, \theta)$, 

$$\begin{equation} %\label{eq:dipole-dipole}
	V_{dd}(r, \theta) = \frac{\mu_0 \mu_{m}^2}{4 \pi} \frac{1 - 3 \cos^2 \theta}{r^3}
\end{equation}$$

where r is the relative distance between dipoles, $\theta$ is the angle between the external magnetic field and the dipole, $\mu_0$ is the [[magnetic permeability]] of vacuum.

In the weak dipolar interaction limit (first order Born approximation), the effective potential is the sum of contact and dipolar potentials

$$\begin{equation} %\label{eq:combine-vint}
	V_{\text{int}}(r) = \frac{g_s}{2} \left(1 + \epsilon_{dd} \left(3\cos^2 \theta - 1\right)\right)
\end{equation}$$
The dipolar interaction, due to its long-range nature and anisotropy, significantly impacts the scattering problem. It involves all partial waves $(l > 0)$ and cannot be reduced to a simple pseudo-potential. However, at low collision energies, dipolar scattering becomes universal and mainly involves s-wave channels. The Born approximation remains valid in this regime, allowing the total elastic scattering cross-sections to be conveniently added for identical bosons and fermions.
## Gross-Pitaevskii Equation

Let's begin with the most general case. In a condensed system, all particles occupy the same single-particle state $\phi(r)$, satisfying normalization condition ${\int d^3 r |\psi(\textbf{r})|^2 = 1}$. The total wave function in a mean-field approximation is a symmetric product of the single-particle wave functions.

As this is a simple case, we define the mean-field energy as only contact interaction, leading to the total Hamiltonian

$$\begin{equation} %\label{eq:simple-hamil}
	H = \sum_{i=1}^{N} \left(\frac{\textbf{p}_i^2}{2m} + V_{ext}(\textbf{r}_i)\right) + g_s \sum_{i < j} \delta (\textbf{r}_i - \textbf{r}_j)
\end{equation}$$
To solve this Hamiltonian, we employ the variation method with an appropriate Ansatz. By minimizing the energy functional under variations of the wave function while keeping the total atom number constant, we obtain the time-independent Gross-Pitaevskii Equation

$$\begin{equation} %\label{eq:simple-gpe}
	\mu \psi(\textbf{r}) = \left(-\frac{\hbar^2}{2m} \nabla^2 + V_{ext}(\textbf{r}) + g_s |\psi(\textbf{r})|^2\right)
\end{equation}$$

Our focus will extend beyond this fundamental form, incorporating *beyond mean-field* additions and dipolar terms, leading to an extended Gross-Pitaevskii Equation. 

With inclusion of the interaction potential, 

### The Thomas-Fermi approximation





## Rotation and Vortices

BECs and superfluids are both irrational fluids that form vortices upon the additional angular momentum. The vortex in this case can be thought of as can excitation that carries angular momentum, or a density hole with particles rotating around the core.

The [[continuity equation]], for BECs, showing that the velocity field of the condensate is connected to the wave function

$$\begin{equation}
	\frac{\partial}{\partial t} |\psi|^2 = \frac{-i\hbar}{2m} \nabla \left ( \psi* \nabla \psi + \psi \nabla \psi*  \right) = 0
\end{equation}$$which can be compared to the continuity question derived from the linear [[Schrödinger Equation]]

$$\begin{equation}
	\frac{\partial}{\partial t} n + \nabla (n\textbf{v}) = 0
\end{equation}$$
From this comparison we get the velocity field for the condensate as

$$\begin{equation}
	\textbf{v} = \frac{-i\hbar}{2m} \frac{ (\psi* \nabla \psi + \psi \nabla \psi* )}{|\psi|^2}
\end{equation}$$
where $m$ is the mass.

Using the Ansatz, $\psi = f e^{i\phi}$, with $f$ as the modulus and $\phi$ as the phase, we write the velocity field

$$\begin{equation}
	\textbf{v} = \frac{\hbar}{m} \nabla \phi
\end{equation}$$

Importantly, the gradient of the phase of the wave function describes the velocity field of the condensate.

From classical physics, we define the measure [[circulation]].

$$\begin{equation}
	\Gamma = \frac{h}{m} \int_A \nabla \times \nabla\phi = 0
\end{equation}$$

C is a contour that encloses the area A. 

This equation implies that a superfluid cannot rotate. 

The expression circulation of a superfluid is still valid in cases where the phase, $\phi$, has a singularity. The change in the phase going around the contour must then be a multiple of $2\pi$. The circulation becomes *quantised*.

$$\begin{equation}
	\Gamma = 2\pi l \frac{\hbar}{m}
\end{equation}$$

where integer $l$ is the [[winding number]].

### Rotating Frame
(best seen in thesis)




