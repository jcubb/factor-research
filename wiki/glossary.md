# Glossary — Factor Research Wiki

Plain-language definitions of terms used throughout the wiki. This is a dip-in
reference, not a read-through. Where a concept has a dedicated article, it's linked.
See [[start-here]] for a guided reading path.

---

## Core concepts

- **Factor** — A common source of return/risk shared across many securities (e.g. the market, value, momentum). A factor model explains a security's return as a weighted sum of factor returns plus a leftover idiosyncratic piece. See [[fama-french-factor-models]].
- **Factor return** — The return of the factor itself (often the return of a long-short portfolio built to isolate it).
- **Loading / exposure / beta** — How sensitive a security is to a factor. A stock with a value loading of 1.2 moves 1.2× the value factor. "Beta" usually means the loading; "market beta" is the loading on the market factor.
- **Alpha** — Return not explained by the factors in the model — the intercept of the return regression. Interpreted as skill or mispricing. Contrast **idiosyncratic alpha** below.
- **Active / excess return** — A fund's return minus its benchmark's return. Note this still contains factor beta; alpha is what's left after stripping factors out.
- **Idiosyncratic alpha (IA)** — Active return *net of common factor betas* — the nonreplicable part worth an active fee. More persistent than raw excess return. See [[harmsworth-idiosyncratic-alpha]].
- **Systematic vs. specific (idiosyncratic) risk** — Systematic risk comes from factor exposures (shared, undiversifiable); specific risk is security-unique (diversifiable). A risk model splits total risk into these two.
- **Cross-section** — Looking across many securities at one point in time (vs. time-series, which follows one security over time). "The cross-section of expected returns" = why different stocks earn different average returns.

## The named equity factors

- **SMB (Small Minus Big)** — The size factor: small-cap minus large-cap returns.
- **HML (High Minus Low)** — The value factor: high book-to-market (cheap) minus low (expensive).
- **RMW (Robust Minus Weak)** — The profitability factor.
- **CMA (Conservative Minus Aggressive)** — The investment factor (low vs. high asset growth).
- **UMD / MOM (Up Minus Down)** — The momentum factor: recent winners minus losers.
- **BAB (Betting Against Beta)** — Long low-beta, short high-beta, leverage-adjusted. See [[frazzini-pedersen-betting-against-beta]].
- **Low Volatility / Min Vol** — The anomaly that low-risk stocks earn high risk-adjusted returns; the practitioner cousin of BAB.
- **Quality / Yield** — Profitability-and-stability factors; dividend/earnings yield factors. Part of the MSCI six. See [[msci-foundations-of-factor-investing]].
- **Carry** — Earning the yield differential (e.g. high- vs. low-interest currencies). **Dollar factor** — a common component across all USD exchange rates. See [[verdelhan-systematic-exchange-rates]].

## Momentum vocabulary

- **Cross-sectional momentum** — Rank securities against each other; buy relative winners.
- **Time-series momentum (TSMOM)** — Judge each asset against its *own* past; go long if it's been rising. See [[moskowitz-nonlinear-momentum]].
- **Time-series factor momentum (TSFM)** — TSMOM applied to factor returns. See [[gupta-kelly-factor-momentum-everywhere]].
- **Factor momentum** — Predictability in factor returns from their own past (factor autocorrelation); argued to subsume stock momentum. See [[ehsani-linnainmaa-factor-momentum]].

## Portfolio & performance metrics

- **Sharpe ratio** — Excess return per unit of total volatility. The basic risk-adjusted-return measure.
- **Information ratio (IR)** — Active return per unit of tracking error. "Alpha IR" uses idiosyncratic alpha; "active IR" uses excess return.
- **Tracking error (TE)** — Volatility of a fund's active (vs. benchmark) return. High TE = big benchmark deviations.
- **Tangency portfolio** — The maximum-Sharpe combination of assets; the theoretical goal of mean-variance optimization.
- **Long-short / dollar-neutral** — A portfolio with offsetting long and short legs. Dollar-neutral = equal dollars each side (zero net market exposure).
- **Benchmark** — The index a fund is measured against. A core theme of the KB: cheap factor exposure should be treated as part of the benchmark, not as alpha.
- **Backtest / out-of-sample** — Testing a strategy on historical data; out-of-sample means on data not used to build it (more credible).

## Risk-model machinery

- **Covariance / correlation matrix** — Table of how assets (or factors) co-move. The correlation matrix is the covariance matrix normalized to unit variances. Geometric intuition: [[spruyt-geometric-covariance-matrix]].
- **Positive definite** — A property a valid covariance matrix must have (all variances positive, no impossible combinations). Estimation noise can break it — a problem [[mossessian-robust-covariance-estimation]] fixes.
- **Eigenvector / eigenvalue / eigendecomposition** — Decomposing a matrix into its principal directions (eigenvectors) and their magnitudes (eigenvalues). For a covariance matrix, eigenvectors are the axes of the data cloud and eigenvalues the variance along them.
- **PCA (Principal Component Analysis)** — Using the eigendecomposition to find the directions of greatest variance; the basis for statistical factor models and denoising.
- **SVD (Singular Value Decomposition)** — A generalization of eigendecomposition used to compute it (and central to [[kelly-principal-portfolios]]).
- **EWMA (Exponentially Weighted Moving Average)** — Weighting recent observations more heavily when estimating variance/covariance.
- **Half-life** — How fast EWMA weights decay; a 21-day half-life means observations 21 days old count half as much as today's.
- **GARCH** — A model where volatility clusters (calm and turbulent periods persist); used to make risk forecasts responsive.
- **GLS (Generalized Least Squares)** — A regression that accounts for unequal/​correlated errors; how Barra estimates factor returns each period. See [[barra-use3-handbook]].
- **Shrinkage** — Pulling a noisy estimate toward a stable target (e.g. shrinking sample correlations toward an average) to reduce error. Contrast the RMT approach in [[mossessian-robust-covariance-estimation]].
- **Random Matrix Theory (RMT) / Marchenko–Pastur** — Theory predicting the eigenvalue spectrum of a pure-noise correlation matrix; eigenvalues inside its "support region" are treated as noise. See [[mossessian-robust-covariance-estimation]].
- **Value at Risk (VaR)** — A loss threshold not expected to be exceeded at a given confidence (e.g. 95% 1-day VaR). See [[barbieri-var-with-factors]].

## Factor-construction terms

- **Simple vs. pure factor portfolio** — Simple = sort-based (Fama-French style), carrying incidental exposures to other factors. Pure = regression-based, controlling for everything at once. See [[menchero-characteristics-factor-portfolios]].
- **Style / industry / country / world factor** — The building blocks of a commercial risk model: style factors (value, momentum…), industry membership, country membership, and a market-wide World factor.
- **Regression weighting** — The choice of weights (cap, root-cap, equal, inverse-specific-variance) when estimating factor returns; materially changes the result. See [[msci-risk-return-factor-portfolios]].
- **Managed portfolio** — A factor portfolio whose exposure is scaled up/down over time by a timing signal. Common in factor-timing research ([[li-episodic-factor-pricing]]).
- **Orthogonalization** — Removing one factor's influence from another so exposures don't overlap.

## Theory references you'll see cited

- **Merton model** — Treats equity as a call option on firm assets; explains why high-yield bonds behave like equity (and equity factors work in them). See [[bektic-fama-french-corporate-bonds]].
- **Rayleigh quotient** — The optimization whose solution is the largest eigenvector; why the top eigenvector points along maximum variance. See [[spruyt-geometric-covariance-matrix]].
- **Treynor–Mazuy** — A regression using squared factor returns to separate market/factor *timing* skill from *selection* skill. See [[harmsworth-idiosyncratic-alpha]].
- **Bootstrap** — Resampling returns to build a distribution of outcomes under "no skill," to judge whether real funds beat luck. See [[fama-french-luck-vs-skill]].
- **White data** — Uncorrelated, unit-variance data (identity covariance matrix); the reference point a covariance matrix "transforms." See [[spruyt-geometric-covariance-matrix]].
- **Smart beta** — Low-cost index products that deliver factor exposure; their near-zero fees are why factor beta is considered "commoditized." See [[harmsworth-idiosyncratic-alpha]].
