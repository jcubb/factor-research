# Start Here — A Reading Path Through the Factor Research Wiki

New to factor investing and risk models? This is the on-ramp. It orders the wiki's
articles from foundational intuition to advanced methods, so you build concepts in
the right sequence instead of diving into a random paper. Each step says **what you'll
learn** and **why it's here**. Unfamiliar terms are defined in [[glossary]].

> Tip: read this alongside an LLM assistant. Ask it to unpack any term or equation as
> you go — the articles are written densely and assume some background.

---

## Stage 0 — Mathematical intuition (start if you're new to the machinery)

1. **[[spruyt-geometric-covariance-matrix]]** — What a covariance matrix *is*, geometrically: a rotation-plus-scaling of "white" data, with eigenvectors giving orientation and eigenvalues giving spread. Nearly every later article uses eigenvectors, PCA, or covariance matrices; this is the picture underneath all of them.

## Stage 1 — The core idea of a factor model

2. **[[fama-french-factor-models]]** — The canonical starting point. How the cross-section of stock returns is explained by a handful of factors (market, size, value, later profitability and investment). Establishes the vocabulary: factors, loadings, long-short portfolios, the "factor zoo."
3. **[[msci-foundations-of-factor-investing]]** — A practitioner's plain-language map of the six main equity risk premia (Value, Size, Momentum, Low Vol, Yield, Quality), why the premia persist, and how factor indexes work. The gentlest conceptual overview in the KB.

## Stage 2 — The individual factors

4. **[[frazzini-pedersen-betting-against-beta]]** — The low-risk anomaly: why low-beta assets outperform risk-adjusted, and the leverage-constraint mechanism (BAB). A clean example of a factor with both evidence and theory.
5. **[[ehsani-linnainmaa-factor-momentum]]** — Momentum, and the surprising claim that stock momentum is really momentum *in factors*. Introduces factor autocorrelation and timing.
6. **[[gupta-kelly-factor-momentum-everywhere]]** — The practitioner implementation of factor momentum across 65 factors; pairs with #5.
7. **[[moskowitz-nonlinear-momentum]]** — Refinement: the best momentum signal is an S-curve, not a straight line. Read once #5–6 make sense.
8. **[[verdelhan-systematic-exchange-rates]]** — Factors beyond equities: carry and dollar factors in currencies. Shows the factor idea generalizes across asset classes.
9. **[[bektic-fama-french-corporate-bonds]]** and **[[houweling-vanzundert-factor-investing-corporate-bonds]]** — Factors in corporate bonds, via two routes (equity-style definitions vs. bond-specific ones). Introduces the Merton link between equity and credit.

## Stage 3 — How risk models are actually built (the Barra family)

10. **[[barra-use3-handbook]]** — The foundational commercial risk model: how factor returns are estimated (GLS), how the covariance matrix is built (EWMA + GARCH), and the three-part specific-risk model. Denser — take your time.
11. **[[barra-use4-methodology]]** — The next generation: eigenfactor risk adjustment, volatility regime adjustment, the explicit Country factor. Read after #10.
12. **[[barra-gem-handbook]]** — Extending the model globally (countries, industries, currency covariance).
13. **[[cuffe-barra-market-factor]]** — A focused look at why an explicit market/country factor improves crisis responsiveness. Good companion to #11.

## Stage 4 — Factor portfolio construction & risk attribution

14. **[[menchero-characteristics-factor-portfolios]]** — "Simple" (sort-based) vs. "pure" (regression) factor portfolios, and why they differ. Explains why Fama-French factor returns ≠ Barra factor returns.
15. **[[msci-risk-return-factor-portfolios]]** — How regression weighting choices change factor returns (by >300 bps for momentum).
16. **[[menchero-factor-alignment]]** — Why adding a wrong factor to a model is far more costly than omitting a right one.
17. **[[davis-menchero-pitfalls-risk-attribution]]** — Common mistakes when decomposing portfolio risk, and how a World factor fixes them.

## Stage 5 — Covariance estimation & risk forecasting

18. **[[mossessian-robust-covariance-estimation]]** — Cleaning noise out of a covariance matrix using random matrix theory. Builds directly on the eigen-picture from Stage 0.
19. **[[barbieri-var-with-factors]]** — Using factor models to forecast Value at Risk at short horizons.

## Stage 6 — Advanced & applied

20. **[[kelly-principal-portfolios]]** — A modern unifying method (SVD of a prediction matrix) that produces portfolios capturing both risk and alpha.
21. **[[li-episodic-factor-pricing]]** — Factor premia switch "on" and "off" in regimes; how to detect the on-states in real time.
22. **[[cohen-frazzini-economic-links]]** — A specific alpha source: supply-chain links and limited investor attention.

## Stage 7 — Evaluating managers (does any of this beat the market?)

23. **[[fama-french-luck-vs-skill]]** — The sobering academic view: bootstrap tests showing few funds cover their fees. How to separate skill from luck.
24. **[[harmsworth-idiosyncratic-alpha]]** — The practitioner counterpoint: strip out factor betas and the remaining "idiosyncratic alpha" *is* persistent and predictive. A fitting capstone — it ties factors, skill, and portfolio construction together.

---

## Alternative entry points by interest

- **"I just want the equity factors"** → 2, 3, 4, 5
- **"I build/use risk models"** → 10, 11, 12, 18, 19
- **"I select managers / allocate to funds"** → 23, 24, then 14
- **"I'm here for the math"** → 1, 18, 20
- **"Momentum specifically"** → 5, 6, 7

See the [[index]] for the full topic map and cross-cutting themes.
