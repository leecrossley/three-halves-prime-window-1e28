# The three-halves prime window stays below its main term through $10^{28}$

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24410819.svg)](https://doi.org/10.5281/zenodo.24410819)

This result is now maintained in [prime-window-all-widths](https://github.com/leecrossley/prime-window-all-widths/tree/main/results/three-halves-prime-window-1e28). This repository is archived and keeps its releases and DOI.

At dilation $b=3/2$, the weighted sum of primes between $y$ and $2.25y$ is strictly below its predicted size $\tfrac34y\log(3/2)$ at every real scale up to $10^{28}$. The proof is unconditional: it uses no unproven hypothesis such as the Riemann hypothesis, and relies instead on published proven results, among them Platt and Trudgian's verified height, the zero-density estimates of Kadiri, Lumley and Ng, and Büthe's bound for $\vartheta$.

This extends the earlier direct check, which stopped at $10^5$, by 23 orders of magnitude. Under RH and rational linear independence of the distinct positive ordinates of the nontrivial zeta zeros the sign is known to change arbitrarily far out, so under those hypotheses the sum exceeds its main term for some $y$. This result shows that every such $y$ is larger than $10^{28}$. [Earlier direct certificate](https://github.com/leecrossley/prime-band-three-halves-finite/tree/v1.0.0)

## Statement

For every real $0<y\le10^{28}$,

$$
\sum_{p\ {\rm prime}}(\log p)\thinspace W(p/y)<\tfrac34 y\log(3/2).
$$

This finite-range theorem is unconditional.

Put $b=3/2$. The weight $W(t)$ equals $b(1-1/t)$ for $1<t\le b$, $b^2/t-1$ for $b<t<b^2$, and zero elsewhere. Write $D(y)$ for the main term minus this ordinary-prime sum, and $Q(y)=\sum_p(\log p)W(p^2/y)$ for the square contribution. All logarithms are natural.

## How the proof goes

1. For $y>1$, the explicit formula writes the deficit $D(y)$ as a sum over the zeta zeros plus terms that only help: positive trivial-zero terms and non-negative prime powers.
2. Every zero up to height $H=3\cdot10^{12}$ is on the critical line (Platt and Trudgian). Their total weight is at most $M<0.13121$.
3. Zeros above $H$ might lie off the line. Explicit zero-density estimates of Kadiri, Lumley and Ng at 16 cuts bound their contribution by $E(y)$, with $E(10^{28})<0.0505$.
4. A direct check covers $y\le10^5$. Above that, the prime squares $Q(y)$ and the first 128 known zeros make up the difference:

| Range of $y$ | Why the inequality holds |
|---|---|
| $0<y\le10^5$ | Direct check at the 13,848 prime centres and the final endpoint. The deficit is concave in between. |
| $10^5\le y\le10^{10}$ | A tangent certificate on 34,728 intervals gives $Q(y)>0.11\sqrt y$. |
| $10^{10}\le y\le10^{28}$ | Büthe's explicit bound for $\vartheta$ gives $Q(y)/\sqrt y>0.10$. |

Above $10^5$ the 128 zero terms are enclosed on 138,000 closed logarithmic cells. On each one they, together with the square bound, exceed $M+E$.

The full argument is in [PROOF.md](PROOF.md).

## Verification

The main program encloses the first 128 phase terms on 138,000 closed logarithmic intervals. On each interval their sum, with the square lower bound, exceeds $M+E$. The second program isolates 4,520 distinct zeros from sign changes of the completed zeta function. It bounds the remaining mass from the published sum of inverse squared ordinates, bounds the density integrals with a fourth-degree polynomial, and uses 160 phase terms with derivative bounds on 132,399 cells. Both programs also verify the prime-side breakpoints. Only the published analytic estimates, the published finite height and FLINT's certified zero isolation and counting enter from outside. The two programs implement the same written argument separately, so they share its analytic inputs.

```sh
python -m pip install -r requirements.txt
python verify.py
python independent.py
```

[Recorded verification](evidence/check.txt), [SHA-256 manifest](SHA256SUMS)

## Prior work

At width $b=2$, bramble_trace's earlier certificate reached $10^{35}$ in its centre variable $x=2y$, using a finite verified zero height, density estimates and phases of low zeros. Here the width is $3/2$ and the certified endpoint in $y$ is $10^{28}$. [Dyadic certificate, revision 26](https://rstation.ai/api/v1/posts/uw5cfb_J_Cj7XJO6/attachment?revision=26)

Caceres previously used zero-density strips to certify a different, cumulative logarithmic Riesz weight for the von Mangoldt function. This is a precedent for the finite-height method. [Caceres, Theorem 6](https://hexagonmath.org/pdf/2610.00661v2)

The literature checked included Suzuki's cumulative criterion, the Caceres verification, Zhao's integrated Mertens errors and prior calculations for this exact window. I found no prior bound of this size for this $3/2$ ordinary-prime sum. [Suzuki](https://arxiv.org/abs/2411.07436), [Zhao](https://arxiv.org/html/2411.18903v2), [Previously established conditional sign changes](https://github.com/leecrossley/prime-band-three-halves-oscillation/tree/v1.0.1)
