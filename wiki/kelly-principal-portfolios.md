# Principal Portfolios

> Source: Kelly, Bryan, Semyon Malamud, and Lasse Heje Pedersen. "Principal Portfolios." *The Journal of Finance* 78, no. 1 (February 2023): 347–387.
> DOI: 10.1111/jofi.13199 | AQR Capital Management, Yale, EPFL, Copenhagen Business School, NBER, CEPR

## Overview

Kelly, Malamud, and Pedersen introduce "principal portfolio analysis" (PPA), a new framework for optimal investing when assets exhibit cross-predictability — that is, when one asset's signal predicts another asset's return. The standard approach in empirical finance constructs a "simple factor" by weighting each asset by its own signal (e.g., its own momentum), ignoring the fact that asset j's signal may predict asset i's return. PPA exploits the full prediction matrix to construct optimal strategies.

The core object is the **prediction matrix** Π = E(R_{t+1} S_t'), an N×N matrix whose (i,j) entry captures how asset j's signal predicts asset i's return. The diagonal captures own-signal predictability (the standard focus); off-diagonal elements capture cross-predictability. The authors show that the singular-value decomposition of Π yields "principal portfolios" (PPs) — orthonormal building blocks that are ordered from most to least predictable and whose expected returns equal their corresponding singular values.

A key insight is the **symmetry decomposition**: splitting Π into symmetric (Π^s) and antisymmetric (Π^a) parts separates factor exposure (beta) from factor-neutral alpha. Eigenvectors of Π^s yield **Principal Exposure Portfolios (PEPs)** that capture beta, while eigenvectors of Π^a yield **Principal Alpha Portfolios (PAPs)** that are always factor-neutral. This decomposition also provides a new asset pricing test: if the pricing kernel is correctly specified, Π must be symmetric and positive semidefinite (all PEPs have nonnegative returns and all PAPs have zero returns).

## The Prediction Matrix Framework

| Concept | Definition | Interpretation |
|---|---|---|
| Signal S_{i,t} | Predictive characteristic for security i at time t | Momentum, B/M, beta, valuation ratio, etc. |
| Prediction matrix Π | E(R_{t+1} S_t') | Full map of how all signals predict all returns |
| Diagonal Π_{i,i} | E(R_{i,t+1} S_{i,t}) | Own-signal predictability (standard focus) |
| Off-diagonal Π_{i,j} | E(R_{i,t+1} S_{j,t}) | Cross-predictability (ignored by standard methods) |
| Simple factor F̃ | Σ_j S_{j,t} R_{j,t+1} = S_t' R_{t+1} | Standard own-signal strategy (L = Identity) |
| Linear strategy | w_t = S_t' L for position matrix L | General strategy exploiting cross-predictability |

## Principal Portfolio Construction

The optimal linear strategy maximizes expected return subject to a leverage constraint (||L|| ≤ 1). The solution is given by the SVD of Π:

**Π = U Λ̃ V'**

where Λ̃ = diag(λ̃_1, ..., λ̃_N) contains singular values and U, V are orthogonal matrices. The k-th principal portfolio has position matrix L_k = v_k u_k' and return:

**PP^k_{t+1} = S_t' v_k · u_k' R_{t+1}**

with expected return E(PP^k) = λ̃_k (the k-th singular value). The optimal strategy is the sum of all PPs.

## Alpha-Beta Symmetry Decomposition

| Component | Matrix | Portfolios | Properties |
|---|---|---|---|
| Symmetric Π^s = ½(Π + Π') | Eigendecomposition → PEPs | Factor exposure (beta) | Returns = eigenvalues; positive eigenvalues = positive beta |
| Antisymmetric Π^a = ½(Π - Π') | Eigendecomposition → PAPs | Pure alpha (zero factor exposure) | Returns = 2× eigenvalues; always factor-neutral |

**PEPs** trade portfolios based on their own signal — they are long or short a size-value bet based on its own momentum. They always have factor exposure.

**PAPs** trade two portfolios based on each other's signals — they buy portfolio y based on x's signal and sell portfolio x based on y's signal. They always have zero factor exposure (pure alpha).

## Analogy: PCA vs. PPA

| Property | PCA | PPA (Symmetric Part) |
|---|---|---|
| Decomposition target | Variance-covariance matrix Σ_R | Prediction matrix Π (or Π^s) |
| Component quantity | Variance of each PC = eigenvalue | Expected return of each PEP = eigenvalue |
| Orthogonality | Components are uncorrelated | PEP returns are uncorrelated |
| Trace identity | Σ variances = tr(Σ_R) | Σ expected returns = tr(Π^s) |
| Optimality | Top K PCs maximize variance | Top K PEPs maximize expected return |

## Asset Pricing Test (Positivity Bounds)

If signals are proportional to pricing kernel exposure (S ∝ beta), then:

1. **Π must be symmetric** — no antisymmetric component, so no PAPs exist
2. **Π must be positive semidefinite** — all PEP eigenvalues are nonnegative

Testing these restrictions requires only observing signals and returns (no need to know the risk premium θ_t). The test is unconditional even when the underlying model is conditional. Empirically, the authors reject the FF five-factor model using this test.

## Robust Strategies: Shrinkage via PPs

In practice, Π must be estimated, requiring N² parameters. PPA naturally regularizes by:

- **Rank truncation**: Retaining only the top K PPs (zeroing out noisy lower components)
- **Norm choice**: Different Schatten p-norms on L correspond to different PP weighting schemes
- K and p are tuning parameters chosen via cross-validation

The estimated prediction matrix uses a rolling 120-period window: Π̂_t = (1/120) Σ R_{τ+1} S_τ'.

## Empirical Results

### Application 1: Fama-French 25 Portfolios with Momentum Signal

- Base assets: 25 size × B/M sorted portfolios (daily data, 1963–2019)
- Signal: 20-day cumulative return (momentum), cross-sectionally ranked to [−0.5, 0.5]
- Forecast horizon: 20 trading days (≈ 1 month)

| Strategy | Sharpe Ratio | Information Ratio (vs. FF5) | Key Finding |
|---|---|---|---|
| Simple factor (own-signal) | ~0.5 | ~0.1 (insignificant) | Baseline — no cross-predictability |
| PP 1-3 | ~0.8 | ~0.5 (significant, t = 4.69) | Beats simple factor via cross-prediction |
| PEP 1-3 | ~0.5 | insignificant | Factor exposure only, no alpha |
| PAP 1-3 | ~0.5 | ~0.15 (significant, t = 4.42) | Pure alpha, zero factor exposure |
| PEP + PAP 1-3 | ~0.65 | ~0.4 (significant, t = 4.62) | Best combined performance |

PEP1 tends to go long value and short growth when value has recent momentum (a conditional size-value bet). PAP1 exploits cross-prediction between size and value portfolios.

### Application 2: Factor-Timing with 138 Anomaly Factors

- 138 long-short anomaly factors from Jensen, Kelly, and Pedersen (2022)
- 138 time-series predictors for each factor (factor-level momentum, accruals, B/M, etc.)
- PPA conducted one signal at a time, then combined across signals

| Strategy | Annualized SR | Annualized IR (vs. FF5 + hist. mean wts.) |
|---|---|---|
| Simple factor (own-predictor) | 0.2 | — |
| Historical mean weights | 0.5 | — |
| Leading PP (combined across 138 signals) | 0.6 | 1.1 (significant) |
| Leading PEP (PEP 1) | — | 0.6 (significant) |
| Short PEP N | — | 1.0 (significant) |
| Leading PAP (combined) | 0.7 | 1.3 (significant) |
| HKS (Haddad-Kozak-Santosh) | 0.7 | 0.4 |
| HKS (no covariance) | 0.0 | negative |

The PAP combination achieves the highest IR (1.3), suggesting that cross-factor predictability is a major source of alpha beyond what standard factor timing captures. HKS's outperformance comes from covariance timing, not expected return timing — PPs outperform because they capture antisymmetric (alpha) components that symmetric strategies like HKS cannot.

### Tangency Portfolio Analysis

Adding PPs to the FF five-factor model nearly doubles the ex post tangency SR from 1.1 to 2.2. PAP receives the largest tangency weight (2.1). With a nonnegativity constraint, tangency SR is still 1.5 (40% improvement over FF5 alone).

## Implications for Practice

1. **Cross-predictability matters**: The standard "simple factor" approach leaves substantial alpha on the table by ignoring how one asset's signal predicts another's return.
2. **Symmetry decomposition separates beta from alpha**: PEPs harvest factor exposure efficiently; PAPs deliver factor-neutral alpha. Investors can choose their mix based on mandates.
3. **PPA provides a new model test**: If Π is not symmetric and positive semidefinite, the pricing model is misspecified. This test rejected the FF five-factor model.
4. **Low-rank PPs regularize naturally**: Truncating to the top K PPs is an effective shrinkage method, analogous to PCA but for expected returns rather than variances.
5. **Factor-timing alpha is primarily antisymmetric**: The PAP component drives most of the out-of-sample performance in factor-timing applications, suggesting that cross-factor prediction (not own-factor momentum) is the larger opportunity.
6. **PPs expand the mean-variance frontier**: Adding PP-based strategies to standard factor models roughly doubles the tangency portfolio Sharpe ratio.
7. **Implementation is straightforward**: Compute the SVD of the estimated prediction matrix — a standard routine in any numerical computing environment.

## Connections

- [[ehsani-linnainmaa-factor-momentum]] — Ehsani & Linnainmaa show factor momentum drives stock momentum via autocorrelation of high-eigenvalue PCs. Kelly et al. use PCA's return-analog (PPA) for portfolio construction rather than factor timing. Both papers emphasize the PC structure of factor space but for different purposes: factor timing vs. optimal portfolio formation.
- [[fama-french-factor-models]] — The FF 25 size/value portfolios are Kelly et al.'s primary test bed. The FF five-factor model is used as a benchmark and is rejected by the PPA positivity test (Π is not symmetric and positive semidefinite relative to FF5 factors).
- [[frazzini-pedersen-betting-against-beta]] — Kelly et al. show that the PAP is a generalized form of BAB: when signals = betas and true expected returns are compressed relative to CAPM predictions, the antisymmetric component of Π generates a strategy that goes long the equal-weighted portfolio and shorts the beta-weighted portfolio — exactly the BAB intuition.
- [[moskowitz-nonlinear-momentum]] — Moskowitz et al. optimize the signal-weighting function (linear vs. S-curve) for TSMOM. Kelly et al. optimize the portfolio construction given a linear signal, exploiting cross-asset prediction. The two approaches are complementary.
- [[msci-foundations-of-factor-investing]] — MSCI's six-factor taxonomy provides the practitioner context for Kelly et al.'s factor-timing application. The cyclicality of factor premia that MSCI documents is precisely the predictability that PPs exploit.

#principal-portfolios #PCA #factor-timing #cross-predictability #alpha-beta-decomposition #prediction-matrix #asset-pricing-tests #SVD #dimension-reduction
