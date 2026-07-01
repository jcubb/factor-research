# Factor Momentum and the Momentum Factor

> Source: Ehsani, Sina, and Juhani T. Linnainmaa. "Factor Momentum and the Momentum Factor." *The Journal of Finance* 77, no. 3 (June 2022): 1877–1919.
> DOI: 10.1111/jofi.13131
> Affiliations: Northern Illinois University / Research Affiliates; Dartmouth College / NBER / Kepos Capital

## Overview

This paper makes a striking claim: **momentum is not a distinct risk factor — it is a portfolio that times other factors.** Most equity factors are positively autocorrelated, and this autocorrelation generates momentum in individual stock returns through stocks' factor loadings. Factor momentum in the high-eigenvalue principal components of factor returns subsumes most forms of individual stock momentum. The paper resolves the long-standing puzzle of why momentum stocks comove: they are exposed to the same autocorrelated systematic risks.

## Core Thesis

The argument proceeds in three steps:

1. **Factors are autocorrelated**: The average factor earns 51 bps/month following a year of gains but only 6 bps following a year of losses (t-value on the difference: 4.22).
2. **Factor momentum transmits into the cross section**: Because stocks have different factor loadings, autocorrelation in factor returns creates cross-sectional momentum in individual stocks.
3. **Factor momentum subsumes stock momentum**: A strategy trading momentum in high-eigenvalue PC factors renders individual stock momentum strategies statistically insignificant.

## Data and Factor Universe

### Off-the-Shelf Factors (22 factors)

Data from three sources: Kenneth French, AQR, and Robert Stambaugh.

| Category | U.S. Factors (15) | Global Factors (7) |
|---|---|---|
| Start dates | Jul 1963 (most) | Jul 1990 (most) |
| End date | Dec 2019 | Dec 2019 |
| Notable returns | BAB: 9.8% ann. (t=6.55) | BAB: 9.6% ann. (t=5.70) |
| Lowest returns | Size: 2.7% ann. (t=1.97) | Size: 1.1% ann. (t=0.83) |

### Extended Factor Set (47 factors)

From Kozak, Nagel, and Santosh (2020) — characteristics expressed as weights on zero-investment long-short factors. Seven momentum-related characteristics excluded.

## Factor Autocorrelation Results (Table II)

Regressions of factor monthly returns on an indicator for whether the factor's prior-year return was positive:

- **Pooled result**: Intercept = 6 bps (t=0.72), slope = 45 bps (t=4.22)
- After a losing year, the average anomaly earns just 6 bps/month
- After a winning year, it earns 51 bps/month
- Six anomalies earn **negative** average returns following a year of losses
- All slope coefficients are positive except U.S. momentum itself (−0.09)

**Key takeaway**: Factor premiums are highly state-dependent. An investor who knows a factor's recent performance can substantially improve the timing of exposure.

## Why Factors Are Autocorrelated — The KNS Model

The paper uses the Kozak, Nagel, and Santosh (2018) [KNS] model of sentiment investors:

- Two investor types: rational arbitrageurs and sentiment investors with distorted beliefs
- Sentiment demand follows an AR(1) process: ξₜ₊₁ = μ + φξₜ + νₜ₊₁
- Arbitrageurs nearly fully subsume sentiment demand **not aligned** with factor covariances
- Sentiment demand **aligned** with factor covariances persists → generates factor momentum

**When do factors exhibit momentum?** Factors positively autocorrelate when sentiment is sufficiently persistent: φ ∈ (1/Rf, 1]. With an average monthly risk-free rate of 0.39%, the threshold is φ > 0.996 — extremely persistent, but plausible given that the Baker-Wurgler sentiment index has first-order autocorrelation of 0.986.

**Which factors have more momentum?** High-eigenvalue factors (those explaining more cross-sectional variation) display more momentum. This follows directly from the KNS model: the sentiment-driven demand component δ has large impact on SDF variance only when aligned with high-eigenvalue (volatile) PCs.

## Factor Momentum in PC Factors (Table III)

Momentum strategies trading subsets of PC factors ordered by eigenvalues:

| PCs | Full Sample Return | t-value | First Half | Second Half |
|---|---|---|---|---|
| 1–10 | 19 bps/mo | 7.07 | 27 bps (t=8.49) | 11 bps (t=2.60) |
| 11–20 | 13 bps/mo | 5.23 | 20 bps (t=6.13) | 5 bps (t=1.50) |
| 21–30 | 10 bps/mo | 5.02 | 18 bps (t=7.93) | 2 bps (t=0.63) |
| 31–40 | 10 bps/mo | 4.05 | 16 bps (t=5.07) | 4 bps (t=1.08) |
| 41–47 | 7 bps/mo | 2.51 | 9 bps (t=2.71) | 6 bps (t=1.17) |

- Momentum concentrates in high-eigenvalue PCs as predicted by theory
- First 10 PCs: momentum is significant in both halves of the sample
- Lower PCs: momentum decays, especially in the second half
- All PC subsets correlate with each other positively — momentum is synchronized across factors

### Subsumption Tests (Table III, Panels B & C)

- Momentum in PCs 1–10 **subsumes** momentum found in all other PC subsets in the second half
- The reverse does not hold: lower-eigenvalue PC momentum cannot explain high-eigenvalue PC momentum
- Adj. R² of ~20–40% when regressing lower-PC momentum on higher-PC momentum + FF5

## Factor Momentum vs. Individual Stock Momentum (Figure 1 & Table IV)

### The Horse Race

Six individual stock momentum strategies tested: standard, industry-adjusted, industry, intermediate, Sharpe ratio, and FF5 residual momentum.

**Result**: When the five-factor model is augmented with factor momentum (from first 10 high-eigenvalue PCs):
- All six individual stock momentum strategies become **statistically insignificant** (absolute alphas negligible, GRS test does not reject)
- The reverse does not hold: adding all five individual stock momentum strategies to FF5 leaves factor momentum with a significant alpha (t=5.32)

### Transmission Mechanism (Equation 13)

Cross-sectional stock momentum profits decompose into four sources:

1. **Factor autocovariances × beta dispersion** — the dominant channel
2. **Factor cross-serial covariances × beta covariances** — lead-lag effects between factors
3. **Autocovariances in firm-specific returns** — firm-level momentum
4. **Variation in mean returns** — Conrad and Kaul (1998) mechanism

The key insight: even weak autocorrelation in individual factors generates large cross-sectional momentum if the number of autocorrelated factors is large.

### Momentum-Neutral Factors

The paper constructs factors whose weights are orthogonal to past stock returns. These **momentum-neutral factors exhibit more momentum** than standard factors, and factor momentum in momentum-neutral factors subsumes standard factor momentum. This demonstrates factor momentum is not merely an artifact of individual stock momentum — it is a distinct phenomenon.

## Pricing Momentum-Sorted Portfolios (Table IV)

| Model | Avg. |α̂| | GRS F-value | GRS p-value |
|---|---|---|---|
| FF5 | 0.26 | 4.24 | 0.00% |
| FF5 + UMD | 0.12 | 3.10 | 0.04% |
| FF5 + FMOM (individual factors) | 0.11 | 2.33 | 1.06% |
| FF5 + FMOM (PC 1–10) | 0.10 | 1.30 | 20.29% |

FF5 + FMOM from the first 10 PCs is the **only model** that cannot reject the null that all alphas are jointly zero (p=20.3%).

## Implications for Practice

1. **Factor timing**: Since factors are autocorrelated, a simple timing strategy (increase exposure after a winning year, decrease after a losing year) captures a large premium — 51 bps vs. 6 bps per month.
2. **Momentum is not independent**: There is no need for a separate momentum factor. Momentum profits come from timing other factors. Investors can either (a) time existing factors, (b) redefine factors to incorporate momentum, or (c) trade UMD — all are equivalent.
3. **Residual momentum is an artifact**: Residual momentum strategies (sorting on CAPM or multi-factor residuals) appear to show firm-specific momentum, but this is actually "omitted-factor momentum" — the factors omitted from the model are more autocorrelated than those included.
4. **Alpha decay**: Factor momentum profits are lower in the second half of the sample, consistent with arbitrageurs learning about and harvesting momentum over time.

## Key Distinction: Factor Momentum vs. Factor Timing

Factor momentum is a **time-series** strategy (go long factors with positive recent returns, short those with negative recent returns). It does not require an estimate of factors' unconditional means — only knowledge of recent performance. This is practically valuable because determining which leg of a new factor outperforms requires historical analysis or economic modeling, while momentum requires only observing recent returns.

## Connections

- Directly relates to [[moskowitz-nonlinear-momentum]] on optimal signal weighting for time-series momentum
- Builds on Kozak, Nagel, and Santosh (2018) framework for factor structure and sentiment
- Connects to [[fama-french-factor-models]] — the FF factor zoo (SMB, HML, RMW, CMA) is the universe over which factor momentum is documented; HML's redundancy in the five-factor model raises the question of whether value momentum is really profitability/investment momentum
- Relates to [[frazzini-pedersen-betting-against-beta]] through shared autocorrelation: if BAB also exhibits momentum, timing leverage-constrained factor bets may be a driver
- Extends cross-asset momentum literature of Moskowitz, Ooi, and Pedersen (2012)

#momentum #factor-momentum #autocorrelation #principal-components #sentiment #cross-section #asset-pricing #timing
