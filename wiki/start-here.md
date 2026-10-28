# Start Here — A Reading Path Through the Factor Research Wiki

New to factor investing and risk models? This is the on-ramp. It orders the wiki's
articles from foundational intuition to advanced methods, so you build concepts in
the right sequence instead of diving into a random paper. Each step says **what you'll
learn** and **why it's here**. Unfamiliar terms are defined in [[glossary]].

> Tip: read this alongside an LLM assistant. Ask it to unpack any term or equation as
> you go — the articles are written densely and assume some background.

> **Two ways through the wiki.** The numbered path below moves paper-by-paper. If you'd
> rather read the *argument* first and dip into papers for evidence, start with the five
> **concept syntheses**, which braid the papers into teachable narratives:
> [[capm-and-the-cross-section]] (the big picture) → [[momentum-taxonomy]] and
> [[factor-cyclicality-and-timing]] (the factors and their dynamics) →
> [[factor-construction-methods]] and [[risk-model-anatomy]] (how models are built and used).
> They also map directly onto a three-lecture course ([[lecture-1-cross-section]],
> [[lecture-2-the-factors]], [[lecture-3-building-models]]).

---

## The big picture — five throughlines

Before any paper, hold these five recurring ideas in mind. Almost every article is a variation on one of them; together they are the field's spine. (This section plus the five concept syntheses *are* the primer — read them and you understand the shape of factor research before touching a single paper.)

1. **One question: the cross-section of expected returns.** Why do different securities earn different average returns? Every factor is a proposed answer. → [[capm-and-the-cross-section]]
2. **Two lenses on every premium: risk vs. mispricing.** Is the extra return *compensation for risk* (should persist) or a *mispricing* (may erode as it's arbitraged)? The literature rarely settles it; keeping the distinction live is the most useful reading habit you can have.
3. **"Alpha" is model-relative.** Every alpha is "alpha *with respect to this model*." Upgrade the model (CAPM → FF3 → Carhart → FF5 → Barra) and yesterday's alpha becomes today's beta. This is the recurring plot — from factor discovery ([[fama-french-factor-models]]) to manager evaluation ([[fama-french-luck-vs-skill]], [[harmsworth-idiosyncratic-alpha]]).
4. **A factor is a portfolio you *build*, not a number you look up.** Construction choices — sorts vs. regression, weighting, standardization, constraints — change the answer materially (>300 bps for momentum). "Simple" (sort) and "pure" (regression) factors are different objects. → [[factor-construction-methods]]
5. **Systematic vs. specific risk — the split that organizes risk models.** Pricing asks *why* returns differ; risk modeling asks how they *co-move*, splitting risk into priced factor exposure and diversifiable specific risk. Every risk model generalizes this one CAPM idea. → [[risk-model-anatomy]]

Two structural motifs recur beneath these: the **eigendecomposition thread** (covariance = rotation + scaling; the engine of PCA, RMT denoising, and eigenfactor adjustment — [[spruyt-geometric-covariance-matrix]]) and **the factor zoo problem** (hundreds of published factors; most fail multiple-testing and replication — judge new factors harshly).

---

## Stage 0 — Mathematical intuition (start if you're new to the machinery)

1. **[[spruyt-geometric-covariance-matrix]]** — What a covariance matrix *is*, geometrically: a rotation-plus-scaling of "white" data, with eigenvectors giving orientation and eigenvalues giving spread. Nearly every later article uses eigenvectors, PCA, or covariance matrices; this is the picture underneath all of them.

## Stage 1 — The core idea of a factor model

2. **[[sharpe-lintner-capm]]** — The single-factor baseline everything else is defined against. Where "beta," "alpha," "the market factor," and the systematic-vs-specific risk split come from — and the specific ways it fails empirically (flat SML, characteristic anomalies) that motivate adding more factors. Read this before Fama-French so the refutation lands.
3. **[[fama-french-factor-models]]** — The canonical starting point. How the cross-section of stock returns is explained by a handful of factors (market, size, value, later profitability and investment). Establishes the vocabulary: factors, loadings, long-short portfolios, the "factor zoo."
4. **[[msci-foundations-of-factor-investing]]** — A practitioner's plain-language map of the six main equity risk premia (Value, Size, Momentum, Low Vol, Yield, Quality), why the premia persist, and how factor indexes work. The gentlest conceptual overview in the KB.

## Stage 2 — The individual factors

5. **[[frazzini-pedersen-betting-against-beta]]** — The low-risk anomaly: why low-beta assets outperform risk-adjusted, and the leverage-constraint mechanism (BAB). A clean example of a factor with both evidence and theory — and the explanation for the flat SML you met in #2.
6. **[[jegadeesh-titman-momentum]]** — The origin of momentum: winners keep winning over 3–12 months, unexplained by risk. Read before the momentum-dynamics papers — it's the anomaly they all build on.
7. **[[carhart-four-factor-persistence]]** — Packages momentum into the PR1YR factor and defines the four-factor model — the alpha benchmark cited across the rest of the KB. Also the first clean evidence that fund "hot hands" is mostly momentum plus costs, not skill (sets up Stage 7).
8. **[[ehsani-linnainmaa-factor-momentum]]** — Momentum, and the surprising claim that stock momentum is really momentum *in factors*. Introduces factor autocorrelation and timing.
9. **[[gupta-kelly-factor-momentum-everywhere]]** — The practitioner implementation of factor momentum across 65 factors; pairs with #8.
10. **[[moskowitz-nonlinear-momentum]]** — Refinement: the best momentum signal is an S-curve, not a straight line. Read once #8–9 make sense.
11. **[[verdelhan-systematic-exchange-rates]]** — Factors beyond equities: carry and dollar factors in currencies. Shows the factor idea generalizes across asset classes.
12. **[[bektic-fama-french-corporate-bonds]]** and **[[houweling-vanzundert-factor-investing-corporate-bonds]]** — Factors in corporate bonds, via two routes (equity-style definitions vs. bond-specific ones). Introduces the Merton link between equity and credit.

## Stage 3 — How risk models are actually built (the Barra family)

13. **[[barra-use3-handbook]]** — The foundational commercial risk model: how factor returns are estimated (GLS), how the covariance matrix is built (EWMA + GARCH), and the three-part specific-risk model. Denser — take your time.
14. **[[barra-use4-methodology]]** — The next generation: eigenfactor risk adjustment, volatility regime adjustment, the explicit Country factor. Read after #13.
15. **[[barra-gem-handbook]]** — Extending the model globally (countries, industries, currency covariance).
16. **[[cuffe-barra-market-factor]]** — A focused look at why an explicit market/country factor improves crisis responsiveness. Good companion to #14.

## Stage 4 — Factor portfolio construction & risk attribution

17. **[[menchero-characteristics-factor-portfolios]]** — "Simple" (sort-based) vs. "pure" (regression) factor portfolios, and why they differ. Explains why Fama-French factor returns ≠ Barra factor returns.
18. **[[msci-risk-return-factor-portfolios]]** — How regression weighting choices change factor returns (by >300 bps for momentum).
19. **[[menchero-factor-alignment]]** — Why adding a wrong factor to a model is far more costly than omitting a right one.
20. **[[davis-menchero-pitfalls-risk-attribution]]** — Common mistakes when decomposing portfolio risk, and how a World factor fixes them.

## Stage 5 — Covariance estimation & risk forecasting

21. **[[mossessian-robust-covariance-estimation]]** — Cleaning noise out of a covariance matrix using random matrix theory. Builds directly on the eigen-picture from Stage 0.
22. **[[barbieri-var-with-factors]]** — Using factor models to forecast Value at Risk at short horizons.

## Stage 6 — Advanced & applied

23. **[[kelly-principal-portfolios]]** — A modern unifying method (SVD of a prediction matrix) that produces portfolios capturing both risk and alpha.
24. **[[li-episodic-factor-pricing]]** — Factor premia switch "on" and "off" in regimes; how to detect the on-states in real time.
25. **[[cohen-frazzini-economic-links]]** — A specific alpha source: supply-chain links and limited investor attention.

## Stage 7 — Evaluating managers (does any of this beat the market?)

26. **[[fama-french-luck-vs-skill]]** — The sobering academic view: bootstrap tests showing few funds cover their fees. How to separate skill from luck.
27. **[[harmsworth-idiosyncratic-alpha]]** — The practitioner counterpoint: strip out factor betas and the remaining "idiosyncratic alpha" *is* persistent and predictive. A fitting capstone — it ties factors, skill, and portfolio construction together.

---

## Alternative entry points by interest

- **"I just want the equity factors"** → 2, 3, 4, 5, 6
- **"I build/use risk models"** → 13, 14, 15, 21, 22
- **"I select managers / allocate to funds"** → 7, 26, 27, then 17
- **"I'm here for the math"** → 1, 21, 23
- **"Momentum specifically"** → 6, 7, 8, 9, 10

See the [[index]] for the full topic map and cross-cutting themes.
