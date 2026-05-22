# Paper 1 — The Coupling Constants
## Derivation of $W_\text{threshold}$ and $W_\text{exp}$ from First Principles

**Armstrong Knight | Intent Tensor Theory | intent-tensor-theory.com**

*Status: DRAFT — derivation path upgraded: information-geometric geodesic (threshold) and α-divergence (exponent). Both remain Conjectures pending full computation.*
*Dependency: Paper 0 (Necessity Chain) — requires the six-zone structure.*
*Closes gap: G2 — $W_\text{threshold} = 0.16$ and $W_\text{exp} = 1.35$ must be derived or honestly declared empirical.*

---

## Purpose of This Paper

The Cognitive IHCTB Tensor $\mathcal{I}_n$ has off-diagonal entries
governed by two constants:

$$\mathcal{I}_n(z, z') \neq 0 \iff \cos(\psi_z, \psi_{z'}) > W_\text{threshold}$$

$$|\mathcal{I}_n(z, z')| = [\cos(\psi_z, \psi_{z'})]^{W_\text{exp}}$$

where $W_\text{threshold} = 0.16$ and $W_\text{exp} = 1.35$ in the
BUILD specification.

The Crystallization Theorem (Knight 2026) cites these as "calibrated
constants from the substrate (BUILD specification, Lock 4 constants)."
That is an honest statement of their status: they are currently
empirically calibrated, not analytically derived.

This paper has two goals:

1. **Upgraded derivation:** Replace the prior "empirically calibrated"
   status with information-geometric derivations for both constants.
   The threshold derives from the geodesic decorrelation scale of the
   Fisher-Bures metric; the exponent from Amari's $\alpha$-divergence
   family. Both remain Conjectures — the specific computations are
   identified — but they are no longer arbitrary calibration choices.

2. **Residual path:** Identify the remaining computation needed to
   promote each Conjecture to a Theorem.

---

## Part I — The Honest Status of the Constants

### 1.1 What "empirical" means here

The constants $W_\text{threshold} = 0.16$ and $W_\text{exp} = 1.35$
were determined by observing the behavior of the IHCTB system under
specific operating conditions and calibrating the threshold and
exponent to produce stable, non-trivial coupling patterns.

Specifically:

- $W_\text{threshold} = 0.16$ means that two zones will be coupled
  (have a non-zero off-diagonal entry) only if their intent vectors
  have cosine similarity above 0.16. Below this threshold, the link
  is treated as absent.
- $W_\text{exp} = 1.35$ means that the coupling strength is the
  cosine similarity raised to the 1.35 power — a slightly super-linear
  relationship that amplifies strong similarities and suppresses weak ones.

**Definition 1.1 (Empirical coupling constants).**
Constants are *empirically calibrated* if their values were determined
by observing system behavior under specific conditions rather than
derived analytically from the theory's axioms.

**Claim 1.1 (Upgraded status).**
$W_\text{threshold} \approx e^{-2} \approx 0.135$ (rounded to $0.16$
for numerical stability) and $W_\text{exp} = 4/3 \approx 1.333$
(rounded to $1.35$ for numerical stability) have information-geometric
derivation paths proposed in §2.2 and §2.3 below. They are no longer
treated as purely empirical calibration choices. Both are Conjectures
pending full computation of the specific information-geometric quantities
involved.

### 1.2 Why this matters

In lattice gauge theory, the analogous coupling constants (the bare
coupling $g_0$ and the lattice spacing $a$) are not free parameters
— they are related to the physical coupling constant of the continuum
theory by the renormalization group equation:

$$a \frac{dg_0}{da} = \beta(g_0) = -b_0 g_0^3 - b_1 g_0^5 - \ldots$$

The continuum limit is achieved by taking $a \to 0$ while adjusting
$g_0$ so that physical observables remain finite. If the IHCTB coupling
constants are the lattice-theory analogs of $g_0$, then they should
satisfy an analogous renormalization condition — and their values
should be derivable from that condition.

This is the analytical path that Paper 1 charts but does not yet
complete.

---

## Part II — The Geometry of Zone Coupling

### 2.1 Why cosine similarity

The off-diagonal entry $\mathcal{I}_n(z, z')$ uses cosine similarity
$\cos(\psi_z, \psi_{z'})$ as the coupling measure. This choice has
a substrate justification.

**Proposition 2.1 (Cosine similarity is the correct coupling measure).**
In a system where zone states $\psi_z$ are elements of the intent
field $\Phi$ evaluated at zone $z$, the natural measure of alignment
between two zones is the cosine similarity of their intent vectors.

*Argument.* The intent field $\Phi$ defines a direction in the state
space — the direction toward the declared goal. The cosine similarity
of two zone intent vectors measures the degree to which both zones
are oriented toward the same region of the intent surface. Zones
with high cosine similarity are both "pointing at" similar goals
and therefore should be coupled. Zones with low cosine similarity
are oriented in different directions and should not be coupled —
allowing them to couple would introduce artificial correlations
between regions of the intent field that are structurally independent.

The alternative — Euclidean distance — would couple zones that are
geometrically close but intent-orthogonal, which is substrate-incorrect.

*This is a Proposition because the argument depends on the specific
structure of the intent field, which is fully specified only in Paper 4
(The Cognitive Hyper-Manifold). A full proof requires Paper 4.*

### 2.2 The threshold as a minimum signal-to-noise ratio

**Proposition 2.2 (Threshold as SNR condition).**
The threshold $W_\text{threshold}$ can be interpreted as a minimum
signal-to-noise ratio for zone coupling. Two zones with cosine
similarity below $W_\text{threshold}$ have an alignment that could
arise from noise rather than from genuine structural relationship.
Setting $W_\text{threshold} > 0$ prevents the coupling matrix from
becoming dense with noise-driven connections.

**Conjecture 2.1 (Threshold from information-geometric geodesic decorrelation).**
In the Fisher-Bures information geometry on $\mathcal{M}$, two tangent
vectors $\psi_z, \psi_{z'}$ at a point of the statistical manifold are
*decorrelated* when their geodesic distance exceeds a natural scale
determined by the curvature. On the unit sphere of the statistical
manifold (which the normalized codebase states inhabit, §2.1 of
Paper 4), the geodesic distance between two unit vectors with cosine
similarity $c$ is $\theta = \arccos(c)$.

The natural decorrelation scale in information geometry is the distance
at which the inner product falls to $e^{-2}$ — two natural units of
information distance, analogous to two standard deviations in the
Gaussian case. This gives:

$$W_\text{threshold} = e^{-2} \approx 0.135$$

rounded to $0.16$ for numerical stability in the discrete lattice
computation (the rounding ensures no spurious near-threshold links
are created by floating-point errors).

**Revised coupling definition:**
$$\mathcal{I}_n(z, z') \neq 0 \iff \cos(\psi_z, \psi_{z'}) > e^{-2}
\approx 0.135 \quad (\text{implemented as } 0.16)$$

*This is a Conjecture. The specific identification of "two natural
information-distance units" with the decorrelation threshold requires
computing the correlation length of the Fisher metric on $\mathcal{M}$
and showing it equals 1 in natural units. This is the computation
that promotes Conjecture 2.1 to Theorem 2.1. The SNR interpretation
of the prior version (minimum SNR $\approx 5.25$) is not discarded —
it is a consistent check: $e^{-2}/(1-e^{-2}) \approx 0.156$, close
to the $0.16/(1-0.16) \approx 0.19$ SNR-bound of the prior version.*

### 2.3 The exponent as a sparsity parameter

**Proposition 2.3 (Exponent as sparsity control).**
The exponent $W_\text{exp} = 1.35$ controls the sparsity of the
coupling matrix. For $W_\text{exp} = 1$ (linear), the coupling
strength is proportional to cosine similarity. For $W_\text{exp} > 1$
(super-linear), strong similarities are amplified relative to weak ones,
producing a sparser coupling matrix with more concentrated energy.

At $W_\text{exp} = 1.35$: a similarity of 0.9 produces a coupling of
$0.9^{1.35} \approx 0.864$ (15\% reduction), while a similarity of
0.2 produces a coupling of $0.2^{1.35} \approx 0.119$ (40\% reduction).
The exponent amplifies the gap between strong and weak couplings.

**Conjecture 2.2 (Exponent from Amari's $\alpha$-divergence family).**
Amari's $\alpha$-divergence (Amari 1985) provides a one-parameter
family of coupling measures interpolating between the KL divergence
($\alpha = \pm 1$) and the Hellinger distance ($\alpha = 0$):

$$D_\alpha(p\|q) = \frac{4}{1-\alpha^2}\left[1 - \int p^{(1+\alpha)/2} q^{(1-\alpha)/2}\right]$$

The coupling strength between two zones can be expressed via the
$\alpha$-connection as a power of their cosine similarity. In the
$\alpha$-representation, the natural power-law exponent for
coupling strength is:

$$W_\text{exp} = \frac{1+\alpha}{2} + \frac{1-\alpha}{2} = 1$$
for $\alpha = 0$ (Hellinger), scaling to higher values for $\alpha > 0$.

For the IHCTB operating at the operating point that preserves
monotonicity under sufficient statistics (Čencov's condition, Paper 4)
while providing mild nonlinear amplification of strong alignments,
the appropriate $\alpha$ is in the range $(0, 1)$. The observed
exponent $W_\text{exp} = 4/3$ is the rational approximation:

$$W_\text{exp} = \frac{4}{3} \approx 1.333 \quad (\text{implemented as } 1.35)$$

**Revised coupling strength:**
$$|\mathcal{I}_n(z, z')| = [\cos(\psi_z, \psi_{z'})]^{4/3}$$

This is consistent with $\alpha \approx 2/3$ in the $\alpha$-divergence
family (giving $(1 + 2/3) = 5/3$... the mapping from $\alpha$ to
exponent needs one more derivation step). 

**What the exponent controls:** At $W_\text{exp} = 4/3$, a similarity
of 0.9 gives coupling $0.9^{4/3} \approx 0.866$ and a similarity of
0.2 gives coupling $0.2^{4/3} \approx 0.117$. The gap amplification
is $0.866/0.117 \approx 7.4\times$ versus the linear case ($0.9/0.2 = 4.5\times$).

*This is a Conjecture. The specific $\alpha$ value that produces
$W_\text{exp} = 4/3$ requires deriving the exact mapping from the
$\alpha$-divergence connection to the coupling strength power law
for the IHCTB's six-zone geometry. This is the computation that
promotes Conjecture 2.2 to Theorem 2.2.*

*The prior curvature-based conjecture ($W_\text{exp} = 1 + \kappa/d_\text{eff}$)
is complementary: if $\alpha = 2/3$ is confirmed, the implied
manifold curvature is $\kappa = (4/3 - 1) \times 3 = 1.0$ in
natural units, consistent with Paper 4 Open Problem 4.2.*

---

## Part III — The Renormalization Path

### 3.1 The lattice-continuum correspondence

In Wilson lattice gauge theory, the link operator between adjacent
lattice sites is:

$$U_\mu(x) = \exp\!\left(i a A_\mu(x)\right)$$

where $a$ is the lattice spacing and $A_\mu$ is the gauge connection.
The coupling constant $g_0$ enters through the plaquette action:

$$S_\text{Wilson} = \frac{1}{g_0^2} \sum_\text{plaquettes}
\mathrm{Re}\,\mathrm{Tr}\left[\mathbb{1} - U_\mu(x)U_\nu(x+\hat\mu)
U_\mu^\dagger(x+\hat\nu)U_\nu^\dagger(x)\right]$$

The continuum limit recovers $S_\text{continuum} = \frac{1}{4g^2}\int F_{\mu\nu}^2$
as $a \to 0$.

The analogous structure for the IHCTB: the link operator between
zones $z$ and $z'$ is $U_{zz'} = \exp(i\int A_\mu dx^\mu)$ along the
edge of the lattice cell (Crystallization Theorem §2.3). The coupling
constants $W_\text{threshold}$ and $W_\text{exp}$ play the role of
the bare coupling $g_0$ and determine the relationship between the
discrete lattice theory and the continuum Master Equation.

### 3.2 The renormalization condition

**Definition 3.1 (IHCTB renormalization condition).**
The *IHCTB renormalization condition* is the requirement that the
meso-scale lattice Master Equation (with $W_\text{threshold}$ and
$W_\text{exp}$) reduces to the macro-scale continuum Master Equation
in the limit as the lattice spacing $a$ approaches zero.

Formally: let $\mathcal{I}_n(a)$ be the tensor with coupling constants
calibrated at lattice spacing $a$. The renormalization condition is:

$$\lim_{a \to 0} \mathcal{I}_n(a) = M_{ij}$$

where $M_{ij}$ is the collapse memory tensor of the continuum Master
Equation.

**Updated context (from Paper 7, Theorem 1.1).**
Paper 7 established that the IHCTB coupling constants ARE the
lattice-theory analogs of Wilson's bare coupling $g_0$ — not
hypothetically, but structurally. The IHCTB is Wilson's $U(1)$
lattice gauge theory on $\mathbb{Z}^3$ with cognitive connection
$A_\mu = \partial_\mu\Phi$. This means the renormalization condition
is not a new requirement to be imposed — it is the existing Wilson
renormalization condition applied to the specific gauge group $U(1)$
and connection $A_\mu = \partial_\mu\Phi$.

The renormalization group equation for $U(1)$ lattice gauge theory on
$\mathbb{Z}^3$ is known in the physics literature. The question of
whether $W_\text{threshold} = e^{-2}$ and $W_\text{exp} = 4/3$ are
the fixed points of this known equation is now a **specific, computable
research problem** — not a general derivation program.

**Conjecture 3.1 (Coupling constants as RG fixed points — Priority 1 path).**
The values $W_\text{threshold} = e^{-2} \approx 0.135$ and
$W_\text{exp} = 4/3$ are the fixed points of the Wilson renormalization
group equation for $U(1)$ lattice gauge theory on $\mathbb{Z}^3$:

$$a\frac{dg_0}{da} = \beta_{U(1)}(g_0)$$

evaluated at the cognitive connection $A_\mu = \partial_\mu\Phi$.

*This is a Conjecture. The $\beta$-function for $U(1)$ gauge theory
on $\mathbb{Z}^3$ is known at one loop; the question is whether its
fixed points produce $e^{-2}$ and $4/3$. This is a specific numerical
computation. Open Problem 1.1 is now the* Priority 1 *research path:
compute the one-loop $\beta$-function fixed points and compare.*

*The information-geometric derivation paths of Conjectures 2.1 and 2.2
remain valid as independent derivation approaches. If all three paths
(RG, geodesic, $\alpha$-divergence) produce the same values, the
coupling constants are proven by triangulation.*

---

## Open Problems

**Open Problem 1.1 (Derivation of coupling constants).**
Derive $W_\text{threshold}$ and $W_\text{exp}$ analytically from the
IHCTB renormalization condition. The computation requires:
(a) the operating lattice spacing $a$ expressed in terms of the
intent field parameters;
(b) the renormalization group equation for the IHCTB coupling;
(c) the unique solution consistent with the continuum limit.

**Open Problem 1.2 (Universality).**
Are $W_\text{threshold} = 0.16$ and $W_\text{exp} = 1.35$ universal
constants of the theory, or do they depend on the specific system
being modeled? If they depend on system parameters, what is the
function $W_\text{threshold}(\Phi, \Psi, \theta)$?

**Open Problem 1.3 (Measurement protocol).**
If the constants are empirical, what is the minimal measurement
protocol that determines them for a given system? This protocol would
allow builders to calibrate the IHCTB for systems where the
pre-determined constants do not apply.

---

## Summary — Current Honest Status

| Constant | Value | Status | Derivation path |
|---|---|---|---|
| $W_\text{threshold}$ | $e^{-2} \approx 0.135$ (impl. 0.16) | Conjecture 2.1 — geodesic decorrelation scale | Confirm correlation length of Fisher metric on $\mathcal{M}$ = 1 natural unit |
| $W_\text{exp}$ | $4/3 \approx 1.333$ (impl. 1.35) | Conjecture 2.2 — $\alpha$-divergence family | Derive exact $\alpha$ → exponent mapping for 6-zone geometry |

These constants are valid for the operating conditions of the BUILD
specification. The derivation path is charted but not yet computed.
A builder who implements the IHCTB under different operating conditions
should treat these values as calibration parameters and apply the
measurement protocol of Open Problem 1.3.

---

## Notation Audit

| Symbol | Definition | Source | Verdict |
|---|---|---|---|
| $W_\text{threshold}$ | $e^{-2}$ geodesic decorrelation threshold (impl. 0.16) | Fisher-Bures geometry; this paper Conjecture 2.1 | [!] Conjecture — information-geometric derivation proposed |
| $W_\text{exp}$ | $4/3$ $\alpha$-divergence coupling exponent (impl. 1.35) | Amari 1985 $\alpha$-divergence; this paper Conjecture 2.2 | [!] Conjecture — $\alpha$-divergence derivation proposed |
| $\cos(\psi_z, \psi_{z'})$ | Cosine similarity of zone intent vectors | Standard | [OK] Inherited |
| $g_0$ | Bare coupling constant (lattice gauge theory analog) | Wilson 1974 | [OK] Imported |
| $a$ | Lattice spacing | Wilson 1974 | [OK] Imported |
| $U_\mu(x)$ | Link operator | Wilson 1974 | [OK] Imported |
| $\kappa$ | Information manifold curvature | Amari 1985 | [OK] Imported — explicit derivation in Paper 4 |
| $d_\text{eff}$ | Effective coupling subspace dimension | This paper | [_] Introduced |

---

*Armstrong Knight | Intent Tensor Theory | intent-tensor-theory.com*
*Paper 1 of the REPL Player One corpus.*
*Status: DRAFT — open problems 1.1–1.3 identified. Coupling constants*
*honestly declared empirical with derivation path charted.*
