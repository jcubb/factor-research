# Episodic Factor Pricing

> Source: Li, Sophia Zhengzi, Peixuan Yuan, and Guofu Zhou. "Episodic Factor Pricing." Working Paper, January 2026.
> Washington University in St. Louis / Rutgers University

## Overview

Li, Yuan, and Zhou document that factor pricing power is inherently state dependent rather than constant over time. Factor premia and cross-sectional predictability switch between "pricing-on" and "pricing-off" regimes. During pricing-on periods, factors earn large, statistically significant premia and the risk-return trade-off is strong. During pricing-off periods, factor returns are near zero and statistically insignificant. The authors develop a real-time, out-of-sample method to identify these states using the squared forecast error difference (SED) between a factor model and the CAPM, predicted via LASSO-penalized logistic regression on 28 macroeconomic, sentiment, and lagged SED variables.

The framework has three major applications. First, pricing-state-managed multifactor portfolios (PMPs) that scale down exposure during pricing-off periods deliver significantly higher Sharpe ratios than unmanaged counterparts — the nine-factor PMP achieves SR 1.56 versus 1.18 unmanaged, and the improvement survives transaction costs. Second, extending the analysis to 211 factors from Chen and Zimmermann (2022), the authors show that pricing-on breadth (the number of factors in their pricing-on state at any given time) averages 125 of 211, is procyclical, and contracts sharply during recessions. Third, at the stock level, selectively combining only pricing-on signals into a composite forecast (Comb_on) dramatically outperforms naive equal-weighted signal combination, with a high-minus-low spread of 1.98% per month (t = 9.00) versus 1.36% (t = 6.29) for the naive approach.

## Pricing-State Identification

The identification procedure works in three steps:

| Step | Method | Detail |
|---|---|---|
| 1. Forecast stock returns | Cross-sectional regression | For each factor k, regress r_{n,t+1} = α_t + β_t X_{n,t} + ε_{n,t+1} at each month t using firm characteristic X |
| 2. Compute SED | Squared error difference | SED_{k,t+1} = (1/N) Σ (ê²_{CAPM} − ê²_{factor k}); positive SED means factor k improves over CAPM |
| 3. Predict SED sign | LASSO logistic regression | I_{t+1} = 1{SED_{t+1} > 0}; predict using 28 variables Z_t with expanding window (min 120 months) |

The 28 predictor variables fall into three groups:

| Group | Variables | Examples |
|---|---|---|
| Market-wide macro (14) | Valuation ratios, rates, spreads | Dividend-price, earnings-price, book-to-market, T-bill rate, default spread, inflation, stock variance |
| Investor sentiment (8) | Baker-Wurgler type | Closed-end fund discount, number of IPOs, IPO first-day returns, share turnover, dividend premium, equity share |
| Lagged SED (6) | Own-factor persistence | Past 1-, 3-, 6-, 12-, 18-, 24-month SED |

LASSO selects exactly 5 of 28 coefficients per factor (tuned for sparsity and comparability). Pseudo R² ranges from ~29% (SMB) to ~38% (ROE).

## Representative Factor Results (8 Factors)

| Factor | Pricing-On Mean (% mo) | Pricing-Off Mean (% mo) | On SR | Off SR | Appraisal Ratio |
|---|---|---|---|---|---|
| SMB | 0.73 | −0.21 | 0.95 | −0.28 | 1.04 (high-vol) |
| HML | 0.60 | −0.20 | 0.78 | −0.34 | 0.42 |
| RMW | 0.51 | 0.04 | 1.09 | 0.04 | 0.55–0.60 |
| CMA | 0.38 | −0.29 | 0.95 | −0.56 | 0.55–0.60 |
| UMD | 0.97 | −0.12 | 0.60 | −0.04 | 0.70 |
| ROE | 0.67 | −0.06 | 1.12 | −0.03 | 0.70 |
| IA | 0.52 | −0.23 | 1.39 | −0.48 | 0.70 |
| BAB | 0.76 | −0.07 | 0.74 | −0.03 | 1.08 |

All eight factors earn significant premia during pricing-on months and insignificant returns during pricing-off months. The pattern holds in both low- and high-volatility subsamples, confirming that pricing-state identification is not a proxy for volatility timing.

## Determinants of Pricing States (Table III)

Each factor's pricing state is driven by a distinct but overlapping set of predictors:

| Factor | Key Positive Predictors | Key Negative Predictors | Pseudo R² |
|---|---|---|---|
| SMB | Stock returns (+395%), stock variance (+120%) | Number of IPOs (−58%), inflation, past 3-mo SED | 29.11 |
| HML | Long-term yield (+72%), net equity expansion (+67%), past SED | — | 28.68 |
| RMW | Past 1-mo SED (+213%), term spread (+72%), long-term yield (+48%) | Closed-end fund discount (−38%) | 29.50 |
| CMA & IA | Stock returns (+186%), past SED | Treasury bills (−38%), inflation (−32%) | 36.12 |
| UMD | Number of IPOs (+144%) | Book-to-market (−45%), default yield spread (−50%), stock returns (−62%), past 3-mo SED (−71%) | 30.01 |
| ROE | Past 1-mo SED (+225%), number of IPOs (+58%), long-term yield (+63%) | Stock variance (−70%), stock returns (−56%) | 37.90 |
| BAB | Stock returns (+314%) | Treasury bills (−42%), inflation (−27%), net equity expansion (−41%) | 31.58 |

Lagged SEDs are the dominant predictor class across all categories, reflecting strong state persistence. Sentiment variables (IPOs, closed-end fund discount) are important for Momentum, Value, and Trading Frictions factors.

## Managed Multifactor Portfolios

The pricing-state-managed portfolio (PMP) scales down exposure to factors predicted to be in their pricing-off state, retaining only a fraction η of the off-state allocation:

r_{PMP,t} = ω'_{t|t-1} diag(e − (1−η) I_{t|t-1}) R_t

| Factor Set | UMP SR | PMP SR | p-value | Appraisal Ratio |
|---|---|---|---|---|
| FF3 | 0.50 | 0.88 | 0.00 | 0.72 |
| FF3 + UMD | 0.74 | 1.09 | 0.00 | 0.80 |
| FF5 | 0.96 | 1.22 | 0.00 | 0.75 |
| FF5 + UMD | 1.06 | 1.31 | 0.01 | 0.78 |
| Nine factors | 1.18 | 1.56 | 0.00 | 1.01 |

All SR differences are statistically significant. The nine-factor specification achieves the highest appraisal ratio (1.01), indicating that pricing-state management adds nearly as much information as the factors themselves.

### Post-2000 Subsample

Unconditional factor performance weakens after 2000 (nine-factor UMP SR drops from 1.18 to 0.80), but PMP still delivers SR 1.10 with appraisal ratio 0.75 — the relative improvement from timing is comparable or larger.

## Net-of-Costs Performance (Table V)

| Portfolio | SR (gross) | SR (net, η=0) | SR (net, η=0.1) | SR (net, η=0.5) | TC (% of gross) |
|---|---|---|---|---|---|
| UMP (9 factors) | 1.18 | 0.94 | — | — | 24% |
| PMP (managed only) | 1.56 | 1.02 | 1.05 | 1.06 | 40%→30% |
| PMP⁺ (UMP + PMP sleeves) | — | 1.09 | 1.10 | 1.06 | 33%→29% |

PMP⁺ combines UMP and PMP as two independently managed sleeves, then optimizes weights across both — effectively trading 17 factor portfolios. At η = 0.1, PMP⁺ achieves the highest net SR of 1.10 (vs. UMP 0.94), with the improvement statistically significant at 1%.

## 211-Factor Breadth Analysis

Extending to 211 factors from Chen and Zimmermann (2022):

| Statistic | Value |
|---|---|
| Average pricing-on factors | 125 of 211 |
| Minimum (2008 crisis) | 84 |
| Maximum | 162 |
| Cyclicality | Procyclical — contracts in NBER recessions |
| Mean on-state t-statistic | 3.62 |
| Mean off-state t-statistic | 0.88 |

### By Factor Category (Table VII)

| Category | On Mean (%) | Off Mean (%) | On SR | Off SR | p-value (SR diff) |
|---|---|---|---|---|---|
| Momentum | 0.85 | 0.54 | 1.46 | 0.84 | 0.00 |
| Value vs. Growth | 0.75 | 0.09 | 1.83 | 0.20 | 0.00 |
| Investment | 0.74 | 0.37 | 1.68 | 0.78 | 0.00 |
| Profitability | 0.50 | 0.31 | 0.95 | 0.57 | 0.01 |
| Intangibles | 0.52 | 0.22 | 2.08 | 0.96 | 0.00 |
| Trading Frictions | 0.56 | 0.22 | 1.72 | 0.70 | 0.00 |

Value, Trading Frictions, and Intangibles show the largest on-minus-off improvement. Momentum's off state is relatively resilient (SR 0.84). All category-level SR differences are statistically significant.

## State-Dependent Risk Prices (Table VI)

The conditional price of risk for factor k is modeled as: RP_{k,t+1} = r_{k,t+1}/σ²_{k,t} = α_k + β_k Ĩ_{k,t+1|t} + ε

| Factor | Unconditional α_k | State Spread β_k | β_k t-stat |
|---|---|---|---|
| SMB | 6.79 | 22.05 | 3.09 |
| HML | 10.61 | 25.80 | 2.08 |
| RMW | 30.02 | 48.41 | 4.22 |
| CMA | 15.77 | 26.89 | 2.12 |
| UMD | 31.92 | 14.79 | 1.39 |
| ROE | 22.54 | 21.70 | 1.83 |
| IA | 43.43 | 47.48 | 3.91 |
| BAB | 42.44 | 33.42 | 3.66 |

The price of risk is higher in pricing-on months for every factor. Most β_k estimates are statistically significant (except UMD). Controlling for inverse market volatility (Panel B), the on/off coefficient remains positive for all factors — the pricing-state effect is distinct from the volatility effect.

## Ensembling Weak Signals (Table VIII)

At the stock level, 211 cross-sectional predictors produce "weak" individual return forecasts. Three combination approaches:

| Combination | Method | H-L Spread (% mo) | t-stat | Ann. Return (%) | SR | MDD (%) | FF5 α (t) |
|---|---|---|---|---|---|---|---|
| Comb_naive | Equal-weight all 211 signals | 1.36 | 6.29 | 16.33 | 0.98 | 53.46 | 0.72 (4.37) |
| Comb_on | Average only pricing-on signals | 1.98 | 9.00 | 23.76 | 1.22 | 40.76 | 1.45 (5.53) |
| Comb_off | Average only pricing-off signals | −0.12 | −0.49 | −1.49 | −0.08 | 93.69 | −0.54 (−1.78) |

Comb_on dominates in both subperiods: pre-2000 (SR 1.68 vs. 1.63) and post-2000 (SR 0.84 vs. 0.56). Comb_off carries no predictive content, confirming that pricing-off signals are noise. Comb_on also produces lower maximum drawdown and higher Calmar ratio than the naive combination.

## Implications for Practice

1. **Factor premia are episodic, not constant**: The unconditional average return of a factor is a blend of strong on-state premia and near-zero off-state returns. Evaluating factors solely by their unconditional performance masks the true opportunity set.
2. **Pricing-state timing works out of sample**: The LASSO-based state identification is fully out of sample (expanding window, 120-month minimum), uses only publicly available data, and produces economically large and statistically significant improvements in Sharpe ratios.
3. **The improvement is not volatility timing**: Pricing-state identification adds information beyond what inverse-volatility scaling (Moreira and Muir, 2017) captures. The on/off signal is distinct from and complementary to market volatility.
4. **Weak post-2000 anomaly performance reflects timing, not decay**: The conventional view that anomalies have decayed due to arbitrage or publication is incomplete. Much of the decline reflects factors spending more time in pricing-off states. Conditioning on pricing states recovers strong performance.
5. **Transaction costs are manageable**: The PMP⁺ approach (combining managed and unmanaged sleeves) achieves the best net-of-costs performance by exploiting trade netting across 17 factor portfolios, with net SR of 1.10 versus UMP's 0.94.
6. **Signal combination should be state-aware**: Averaging all available signals equally (Comb_naive) dilutes the forecast with non-informative pricing-off signals. Filtering to pricing-on signals only (Comb_on) nearly doubles the high-minus-low spread and halves the maximum drawdown.
7. **Pricing-on breadth is a macro indicator**: The number of pricing-on factors is procyclical, contracting during recessions and expanding during expansions. This connects factor timing to the business cycle and challenges models predicting stronger risk-return trade-offs in recessions.

## Connections

- [[ehsani-linnainmaa-factor-momentum]] — Ehsani & Linnainmaa show factors are autocorrelated and that stock momentum is a byproduct of factor momentum. Li et al. show that factor pricing power itself is state-dependent, with strong persistence in pricing states (lagged SEDs are the dominant predictors). Factor momentum strategies would benefit from conditioning on pricing states — momentum in a pricing-off factor carries no premium.
- [[gupta-kelly-factor-momentum-everywhere]] — Gupta & Kelly's TSFM strategy conditions on past factor returns to time factor exposures. Li et al.'s pricing-state identification uses a richer set of predictors (macro, sentiment, lagged SED) and shows that factor premia exist only during pricing-on periods. TSFM's crash avoidance in 2009 may partly reflect factors switching to pricing-off states during the crisis.
- [[fama-french-factor-models]] — Li et al. test their framework on FF3 and FF5 factors. All five FF factors exhibit strong on/off dichotomies. HML's pricing-off returns are near zero, which connects to FF (2015)'s finding that HML becomes redundant in the five-factor model — HML may be redundant unconditionally because it spends significant time pricing-off.
- [[frazzini-pedersen-betting-against-beta]] — BAB has the highest appraisal ratio (1.08) among the eight representative factors, meaning pricing-state timing adds the most value for BAB. BAB's pricing-on SR is 0.74 and pricing-off SR is −0.03, consistent with leverage constraints binding episodically rather than continuously.
- [[msci-foundations-of-factor-investing]] — MSCI documents factor cyclicality (different factors outperform at different points in the business cycle). Li et al. formalize this as episodic pricing states with a real-time identification framework, showing that the cyclicality is captured by lagged SEDs and sentiment/macro variables rather than simple business cycle indicators.
- [[kelly-principal-portfolios]] — Kelly et al.'s principal portfolios maximize the risk-return trade-off unconditionally. Li et al.'s finding that risk prices are state-dependent suggests that conditional principal portfolios — where the prediction matrix varies with pricing states — could further improve performance.
- [[moskowitz-nonlinear-momentum]] — Moskowitz et al. show the optimal TSMOM signal is nonlinear (S-shaped). Li et al.'s pricing-state identification is a different form of nonlinearity: a binary on/off regime switch rather than a continuous signal transformation. The two approaches could be complementary — apply S-curve weighting within pricing-on states.

#factor-timing #episodic-pricing #regime-switching #factor-premia #LASSO #SED #managed-portfolios #signal-combination #risk-prices #business-cycle #factor-zoo
