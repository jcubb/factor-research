# Nonlinear Time Series Momentum

> Source: Moskowitz, Tobias J., Riccardo Sabbatucci, Andrea Tamoni, and Björn Uhl. "Nonlinear Time Series Momentum." Working Paper, December 17, 2025.
> Affiliations: Yale University & AQR Capital; Stockholm School of Economics; University of Notre Dame; Universität Hamburg
> Status: Working paper (not yet published in journal)

## Overview

This paper documents a persistent **nonlinear relationship between price trends and risk-adjusted returns** across markets and asset classes. The key innovation is a theoretically motivated S-shaped weighting function for time-series momentum (TSMOM) signals that **downweights extreme signals**, producing statistically significant out-of-sample improvements over standard linear and binary TSMOM strategies. A neural network trained to maximize out-of-sample Sharpe ratios independently discovers the same S-shaped nonlinearity, providing empirical validation of the theory.

## Motivation and Theoretical Foundation

### The Problem with Linear/Binary Momentum

Standard TSMOM implementations use either:
- **Binary (sign) signals**: s = sign(past return) — go long if positive, short if negative (Moskowitz, Ooi, Pedersen 2012)
- **Linear signals**: s = past return / volatility estimate — position proportional to signal strength

Both are suboptimal. Binary signals ignore magnitude information. Linear signals increase exposure proportionally to signal strength, but extreme signals carry disproportionate risk and noise.

### Ferson and Siegel (2001) Optimal Weighting

For a mean-variance investor maximizing the unconditional Sharpe ratio, the optimal portfolio weight on a risky asset given signal s is:

**f_FS(s) = λ · μ(s) / [μ(s)² + σ²_ε]**

With the simplification μ(s) = s and σ²_ε = 1:

**f_FS(s) = s / (s² + 1)**

This is an **S-shaped function**:
- Linear in the middle range (|s| < ~1): weight increases proportionally with signal
- **Concave for large positive signals** and **convex for large negative signals**: weight rolls back toward zero
- Peak weight at approximately s = ±1

### Intuition

Even when extreme signals perfectly predict returns, the optimal weight still rolls back because:
1. Extreme signals increase expected returns but also increase concentration risk
2. At the extremes, the variance cost dominates the return benefit
3. The S-curve trades off return prediction against variance reduction
4. If signals also contain noise (likely), extreme signals are noisier, reinforcing the rollback

## Methodology

### Signal Construction

The general TSMOM signal:

**s_t = k₁ · σ̂_t⁻¹ · Σ w_τ · r_{t-τ}**

where k₁ normalizes to unit variance, σ̂_t is rolling (260-day) volatility, and w_τ are lag weights.

Three lookback periods examined: T = 1, 3, and 12 months (corresponding to 21, 62, 260 trading days).

### Empirical Nonlinear Estimation (NLTSMOM)

The nonlinear function f is estimated using **artificial neural networks (ANN)**:
- Architecture: 1–2 hidden layers, 2–16 nodes per layer, tanh activation
- Training: Adam optimizer, 50 epochs, batch size 1024
- Hyperparameter search: grid over learning rates (10⁻⁶ to 10⁻³), L₂ regularization (10⁻⁴ to 10⁻¹), dropout (25% or 50%)
- Objective: **maximize out-of-sample Sharpe ratio** (not minimize MSE)
- Training data: up to June 1994; out-of-sample: July 1994 onward
- Symmetry imposed: f(−s) = −f(s), and f(0) = 0 (market-beta-neutral)
- Markets pooled into three groups: equity indices, rates & FX, and commodities

### Data

- **55 futures markets** across four sectors: 8 equity index, 24 commodity, 21 interest rate, and currency futures
- Daily data from January 1980 through October 2024
- Front-month contracts, generically rolled with ratio adjustments
- Fully collateralized returns (notional-based)

### Portfolio Construction

Position sizing uses **volatility targeting** at σ_target = 12%:

**pos_{i,t} = (σ_target / σ̂_{i,t+1|t}) · s_{i,t}**

Strategy returns are equally weighted across markets (equivalent to volatility risk parity).

## Empirical Results

### Daily Frequency — Annualized Sharpe Ratios

| Strategy | 1-Month Lookback | 3-Month Lookback | 12-Month Lookback |
|---|---|---|---|
| Linear (TSMOM) | 0.41 | 0.33 | 0.70*** |
| Binary (sign) | 0.53 | 0.33* | 0.59*** |
| F&S Nonlinear | 0.59 | 0.47*** | 0.83*** |
| Empirical NL (ANN) | **0.83** | **0.55***  | **0.84***  |

- NL models significantly outperform linear at all lookback periods (p < 0.03 for 12M)
- The empirical NL model achieves the highest Sharpe ratio at 1M and 3M; ties F&S at 12M
- Improvement is **not driven by a specific subperiod** — holds across 2000–2007, 2007–2015, 2015–2024

### Monthly Frequency — 12-Month Lookback

- Both F&S and empirical NL models achieve Sharpe ratio of **0.65**, vs. 0.51 for linear
- Statistical tests reject equal Sharpe ratios (p = 0.09 for F&S vs. linear; p = 0.06 for empirical NL vs. linear)
- Out-of-sample R² improvement is more substantial at monthly frequency

### By Asset Class (Daily, 12M Lookback)

The nonlinear effect appears across all sectors but is particularly strong for:
- **Rates and FX**: reject null of equal Sharpe ratios at both 1M and 12M horizons
- **Equities**: empirical NL consistently delivers highest Sharpe ratio among all alternatives at monthly frequency
- **Commodities**: impact more pronounced at longer horizons

### Shape of the Estimated Nonlinear Function

The neural network independently discovers the S-curve predicted by theory:
- **Linear** in the range s ∈ [−1, 1]
- **Rollback** (concave/convex) for |s| > 1
- Shape is more sensitive to **observation frequency** than to lookback period
- At higher frequencies (weekly), the rollback is more pronounced for short lookbacks (1M)
- At lower frequencies (monthly), the rollback is more pronounced for longer lookbacks (12M)

## Tail Hedging and Convexity (Section 4.2)

A key feature of TSMOM strategies is their **convex (U-shaped) return profile** vs. the equity market — performing best in extreme up and down markets.

The NL weighting **improves this hedging property**:
- Greater outperformance in extreme down markets
- The majority of improvement in unconditional mean returns comes from improved performance in extreme down markets
- This is consistent with theory: the NL weighting mutes exposure to extreme signals, reducing risk in precisely the states where extreme signals are noisiest

## Combination with Risk Parity

Given low correlation between TSMOM and Risk Parity (RP) strategies:
- Optimal weight to nonlinear TSMOM exceeds **50% in all cases** when combined with RP
- Linear TSMOM commands a noticeably **lower optimal weight**
- The gap narrows slightly for longer lookback periods
- Nonlinear momentum is more effective at improving portfolio efficiency with faster signals

## Key Practical Implications

1. **Signal processing**: Don't treat momentum signals linearly. Apply an S-curve that downweights extreme signals — this is optimal even with perfect forecasts.
2. **Transaction costs**: The smooth NL weighting function naturally **reduces trading** compared to binary or linear models. Binary strategies flip entirely on sign changes; the NL function transitions smoothly.
3. **Multi-horizon strategies**: Combine 1M, 3M, and 12M lookbacks. The NL effect is present at all horizons but the shape varies, suggesting complementary information.
4. **CTA/managed futures relevance**: Direct application to trend-following strategies commanding hundreds of billions in AUM. The S-curve can be implemented with minimal infrastructure change.
5. **Robustness of theory-driven approach**: The Ferson-Siegel theoretical S-curve performs nearly as well as the data-mined neural network, suggesting the theoretical foundation is sound and reducing overfitting concerns.

## Connections

- Directly extends Moskowitz, Ooi, and Pedersen (2012) original TSMOM paper
- Relates to [[ehsani-linnainmaa-factor-momentum]] — NL weighting applies to factor long-short momentum strategies as well as individual assets
- Ferson and Siegel (2001) framework connects to mean-variance optimization theory
- Convexity/hedging properties relate to tail-risk and portfolio insurance literature
- Neural network estimation connects to machine learning in finance methodology
- Daniel and Moskowitz (2016) derive similar weighting for timing the cross-sectional momentum factor (XSMOM)

#momentum #time-series-momentum #nonlinear #trend-following #machine-learning #signal-processing #CTA #managed-futures #S-curve #tail-hedging
