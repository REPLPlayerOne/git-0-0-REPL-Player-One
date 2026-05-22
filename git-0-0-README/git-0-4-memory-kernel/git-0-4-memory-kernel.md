# Paper 3 — The Memory Kernel and the Overdamped Limit
## When the Mori-Zwanzig Memory Kernel Is Negligible

**Armstrong Knight | Intent Tensor Theory | intent-tensor-theory.com**

*Status: DRAFT — conditions for neglecting memory kernel stated explicitly.*
*Dependency: Paper 0 (Necessity Chain), Paper 4 (Cognitive Manifold — for metric).*
*Closes gap: G4 — the Mori-Zwanzig memory kernel is dropped without justification.*

---

## Purpose of This Paper

The meso-scale Master Equation contains the term:

$$-\lambda_b(\mathbb{1} - P_D[\Phi])\Psi$$

This is identified in the Crystallization Theorem as the Mori-Zwanzig
projector onto the admissible declaration subspace. However, the full
Mori-Zwanzig identity includes a *memory kernel* — a non-Markovian
contribution that is dropped in the Master Equation without explicit
justification.

This paper states the conditions under which dropping the memory
kernel is valid, what it means physically when it is not valid, and
what the system looks like in the non-Markovian regime.

---

## Part I — The Full Mori-Zwanzig Identity

### 1.1 Statement of the identity

The Mori-Zwanzig identity (Mori 1965; Zwanzig 1960) provides an exact
decomposition of the dynamics of a "relevant" observable $A$ in a
system with many degrees of freedom. Let $P$ be the projection onto
the relevant subspace (here: the admissible declaration subspace
spanned by $\Phi$) and $Q = \mathbb{1} - P$ the orthogonal projection
onto the irrelevant complement (here: the basis-leak subspace).

The exact equation of motion for $P\Psi$ (the relevant part of
$\Psi$) is:

$$
\frac{d}{dt}P\Psi(t) = P\mathcal{L}P\Psi(t)
+ \underbrace{\int_0^t K(t-s)\,P\Psi(s)\,ds}_{\text{memory kernel}}
+ \underbrace{e^{Qt\mathcal{L}}Q\Psi(0)}_{\text{fluctuation term}}
$$

where $\mathcal{L}$ is the Liouvillian (the generator of the full
dynamics) and the memory kernel is:

$$K(t-s) = PQ\mathcal{L}e^{Q(t-s)\mathcal{L}}Q\mathcal{L}P$$

**The three terms:**
1. **Markovian term** $P\mathcal{L}P\Psi(t)$: the dynamics of the
   relevant subspace driven by itself. This is what the Master Equation
   keeps.
2. **Memory kernel** $\int_0^t K(t-s)\,P\Psi(s)\,ds$: the effect of
   the irrelevant degrees of freedom on the relevant subspace,
   integrated over history. This is what the Master Equation drops.
3. **Fluctuation term** $e^{Qt\mathcal{L}}Q\Psi(0)$: the contribution
   from initial conditions in the irrelevant subspace. Typically treated
   as noise or set to zero.

### 1.2 What "dropping the memory kernel" means physically

When the memory kernel $K(t-s)$ is set to zero, the dynamics of
$P\Psi$ depends only on its current value — not on its history.
This is the **Markov approximation**: the system has no memory of
its past trajectory in the irrelevant subspace.

Physically: the irrelevant degrees of freedom (the components of
$\Psi$ outside the admissible declaration subspace) relax to zero
*faster* than the relevant dynamics evolve. If the irrelevant modes
relax on a timescale $\tau_\text{irr}$ and the relevant dynamics
evolve on a timescale $\tau_\text{rel}$, the Markov approximation
is valid when:

$$\tau_\text{irr} \ll \tau_\text{rel}$$

In this limit, the memory kernel $K(t-s)$ is sharply peaked at $s = t$
and its integral reduces to a local (instantaneous) term — which is
then absorbed into $\lambda_b$.

---

## Part II — The Conditions for the Overdamped Limit

### 2.1 The two-timescale condition

**Definition 2.1 (Relevant relaxation time $\tau_\text{rel}$).**
The *relevant relaxation time* is the characteristic time over which
$P\Psi$ changes appreciably under the Markovian dynamics
$P\mathcal{L}P\Psi$. In the IHCTB context, this is the time for
one full agent loop iteration — the time between consecutive
selection events.

**Definition 2.2 (Irrelevant relaxation time $\tau_\text{irr}$).**
The *irrelevant relaxation time* is the characteristic time over
which $Q\Psi = (\mathbb{1} - P_D[\Phi])\Psi$ decays to zero
under the $-\lambda_b Q$ term. This is:

$$\tau_\text{irr} = \frac{1}{\lambda_b}$$

**Theorem 2.1 (Validity of the Markov approximation).**
The memory kernel is negligible, and the Master Equation is a valid
approximation to the full Mori-Zwanzig dynamics, whenever:

$$\frac{1}{\lambda_b} \ll \tau_\text{rel}$$

i.e., when the inadmissible components of $\Psi$ decay much faster
than the relevant dynamics evolve.

*Proof.* In the limit $\tau_\text{irr} \ll \tau_\text{rel}$, the
propagator $e^{Qt\mathcal{L}}$ in the memory kernel decays to zero
on the timescale $\tau_\text{irr}$. The memory kernel integral
$\int_0^t K(t-s)P\Psi(s)ds$ is dominated by $s \approx t$ (since
$K(t-s) \approx 0$ for $t-s \gg \tau_\text{irr}$). In this regime,
$P\Psi(s) \approx P\Psi(t)$ (since $P\Psi$ changes slowly), and the
integral reduces to $P\Psi(t)\int_0^\infty K(\tau)d\tau$, which is
a local multiplicative correction to $\lambda_b$. This correction is
absorbed into the definition of $\lambda_b$, giving the Markovian
Master Equation. $\square$

### 2.2 What this means in practice

**Proposition 2.1 (IHCTB operating condition).**
The Master Equation is valid for the IHCTB when $\lambda_b$ is
large compared to the inverse loop iteration time. Concretely:
if an agent loop iteration takes $\sim 1$ second and $\lambda_b$
is calibrated in units of $\text{seconds}^{-1}$, the Markov
approximation holds when $\lambda_b \gg 1$ s$^{-1}$.

**Open Problem 3.1 (Calibration of $\lambda_b$).**
What is the correct value of $\lambda_b$ for the IHCTB under the
operating conditions of the BUILD specification? This requires:
(a) identifying the relevant relaxation time $\tau_\text{rel}$
in terms of the system's operating frequency;
(b) choosing $\lambda_b \gg 1/\tau_\text{rel}$;
(c) verifying that the chosen $\lambda_b$ does not create numerical
instability in the discrete approximation to the continuous dynamics.

---

## Part III — The Non-Markovian Regime

### 3.1 When the memory kernel matters

The memory kernel becomes non-negligible when:

$$\frac{1}{\lambda_b} \gtrsim \tau_\text{rel}$$

This can happen when:
- $\lambda_b$ is small (inadmissible components relax slowly)
- $\tau_\text{rel}$ is small (the relevant dynamics evolve quickly —
  many rapid loop iterations)
- The irrelevant subspace has slow internal dynamics
  (the basis-leak is "sticky")

### 3.2 What non-Markovian behavior looks like

When the memory kernel is active, the IHCTB has *memory* of its
past trajectory in the inadmissible subspace. This manifests as:

**Hysteresis:** The current state $\Psi$ depends not just on $\Phi$
and the current selection event, but on the history of how $\Psi$
arrived at its current position. Two paths to the same $\Psi$ can
produce different future dynamics.

**Oscillation:** The memory kernel can introduce oscillatory behavior
in the relaxation of $Q\Psi$. Instead of exponentially decaying to
zero, inadmissible components may oscillate before decaying — or may
not decay at all if the memory kernel has resonances.

**Drift from intent:** In the non-Markovian regime, the $-\lambda_b Q\Psi$
term alone is insufficient to drive $\Psi$ toward $P_D[\Phi]\Psi$.
The memory of past excursions into the inadmissible subspace actively
pulls $\Psi$ away from the admissible subspace, potentially causing
the system to fail Triple Closure.

### 3.3 Detection and repair

**Proposition 3.1 (Memory kernel signature).**
Non-Markovian behavior is detectable from the trajectory of
$\mathfrak{i}(W)$: if $\mathfrak{i}(W)$ oscillates rather than
monotonically decreasing toward zero, the memory kernel is active
and the Markov approximation is invalid.

**Proposition 3.2 (Repair strategy).**
If non-Markovian behavior is detected, the repair is to increase
$\lambda_b$ (faster decay of inadmissible components), reduce the
loop iteration frequency (slower relevant dynamics), or modify $\Phi$
to enlarge the admissible subspace (reducing the projection residual).

---

## Open Problems

**Open Problem 3.1 (Calibration of $\lambda_b$):** Determine the
correct value of $\lambda_b$ from the operating parameters of the
BUILD specification.

**Open Problem 3.2 (Non-Markovian extension of the Master Equation):**
Write the explicit form of the Master Equation with the memory kernel
included. This is the "exact" equation whose Markov approximation
is the current Master Equation. When the exact equation is needed
(non-Markovian regime), what is the computational cost of evaluating
the memory kernel integral?

**Open Problem 3.3 (Relationship between $\lambda_b$ and the coupling
constants):** Is there a consistency condition between $\lambda_b$,
$W_\text{threshold}$, and $W_\text{exp}$ (Paper 1)? The threshold
determines which zone couplings exist; $\lambda_b$ determines how fast
non-admissible states decay. If these are independently calibrated,
there may be parameter combinations that produce inconsistent dynamics.

---

## Notation Audit

| Symbol | Definition | Source | Verdict |
|---|---|---|---|
| $P$ | Projection onto admissible subspace $= P_D[\Phi]$ | Mori 1965; Pre-Veil Vol I §3.X.5 | [OK] Identified |
| $Q$ | Orthogonal complement $= \mathbb{1} - P$ | Zwanzig 1960 | [OK] Imported |
| $\mathcal{L}$ | Liouvillian (generator of full dynamics) | Mori 1965 | [OK] Imported |
| $K(t-s)$ | Memory kernel | Mori 1965 | [OK] Imported |
| $\tau_\text{rel}$ | Relevant relaxation time | This paper §2.1 | [_] Introduced |
| $\tau_\text{irr}$ | Irrelevant relaxation time | This paper §2.2 | [_] Introduced |
| $\lambda_b$ | Admissibility decay rate | Pre-Veil Vol I §3.X.5 | [OK] Inherited — calibration Open Problem 3.1 |

---

*Armstrong Knight | Intent Tensor Theory | intent-tensor-theory.com*
*Paper 3 of the REPL Player One corpus.*
*Status: DRAFT — Markov approximation conditions stated; three open problems labeled.*
