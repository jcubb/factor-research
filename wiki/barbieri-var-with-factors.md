# Modeling Value at Risk with Factors

> Source: Barbieri, Angelo, Kelly Chang, Vladislav Dubikovsky, John Fox, Alexei Gladkevich, Carl Gold, and Lisa Goldberg. "Modeling Value at Risk with Factors." MSCI Barra Model Insights, October 2009.
> SSRN: 1509679 | MSCI Barra, Berkeley, CA

## Overview

Barbieri et al. demonstrate that Barra factor models — traditionally used for longer-horizon (monthly) risk forecasting and portfolio construction — can be adapted to produce accurate short-horizon (1–10 day) Value-at-Risk estimates. The key innovation is the **Daily Factor Return (DFR) method**, which retains the same factor structure as the monthly Barra Integrated Model (BIM) but estimates the factor covariance matrix using daily factor returns and an exponentially weighted moving average (EWMA) with a 21-day half-life.

The DFR method is benchmarked against two alternatives: the Scaled BIM Matrix (SBM) method, which simply divides the monthly covariance matrix by 21, and a non-factor EWMA baseline applied to realized portfolio returns. Across local equity markets (US, Europe, UK, Japan), local fixed income markets (US, Euro, Japan), and global multi-asset portfolios, the DFR method matches the accuracy of EWMA while dramatically outperforming SBM. The crucial advantage of DFR over EWMA is that it preserves the factor model's ability to decompose risk into common factor and specific components — EWMA provides only a single aggregate volatility number with no attribution.

At the global level, the optimal model depends on the forecast horizon. For one-day VaR, the DFR-1B model (one large covariance block with daily cross-market correlations) performs best, with 70% of bias tests within the confidence interval. For two-to-ten-day horizons, the DFR-MB model (multiple local blocks with monthly cross-market correlations) is superior because non-synchronous trading distorts daily cross-market correlations. For horizons beyond ten days, the rescaled monthly BIM is sufficient.

## Three VaR Methods

| Method | Construction | Factor Model? | Update Frequency | Key Property |
|---|---|---|---|---|
| DFR (Daily Factor Return) | r = Xf + ε; F_t = λF_{t-1} + (1−λ)f_t f_t^T; σ² = h^T(X^TFX + Δ)h | Yes | Daily | Full factor decomposition at daily frequency |
| SBM (Scaled BIM Matrix) | F = (1/21) F^m | Yes | Monthly | Simple rescaling — no intra-month responsiveness |
| EWMA (baseline) | σ²_t = λσ²_{t-1} + (1−λ)r²_t | No | Daily | Portfolio-level only — no factor decomposition |

All methods use VaR = α × σ, where α is the normal distribution quantile (1.645 for 95% VaR). Half-life for DFR and EWMA: 21 days (λ = (1/2)^{1/21}).

## Test Framework

| Feature | Detail |
|---|---|
| Data period | January 2003 – May 2009 |
| Testing procedure | One-year (252-day) non-overlapping observation windows; out-of-sample one-day forward forecasts |
| Testing subperiods | 6 years (ending May 2004 through May 2009) |
| VaR test | Kupiec (1995) confidence region: for 95% VaR over 252 days, violation rate should be 2.54%–7.92% |
| Bias test | Bias statistic B = SD(r_t / σ_t); acceptable range [0.91, 1.09] for T=252 at 95% confidence |
| VaR confidence level | 95% (one-sided) |

## Equity Local Market Results

Four Barra equity models tested: USE3L (US), EUE2L (Europe), UKE7L (UK), JPE3 (Japan). Test portfolios built by tilting on each factor: style (top/bottom decile), industry (cap-weighted), country (cap-weighted).

### VaR Backtesting Summary (% over- and underforecasting)

| Model Group | # Portfolios | EWMA OF / UF | DFR OF / UF | SBM OF / UF |
|---|---|---|---|---|
| USE3L | 360 | 2.5 / 17.5 | 6.9 / 13.3 | 49.2 / 32.5 |
| EUE2L | 342 | 5.3 / 9.6 | 5.3 / 12.6 | 41.2 / 29.2 |
| JPE3 | 354 | 4.0 / 3.4 | 6.8 / 4.0 | 20.3 / 31.6 |
| UKE7L | 228 | 3.9 / 7.0 | 8.3 / 6.6 | 43.4 / 28.5 |
| **Average** | | **4.2 / 8.7** | **6.7 / 9.0** | **37.8 / 30.2** |

### Bias Statistics Summary (% over- and underforecasting)

| Model Group | # Portfolios | EWMA OF / UF | DFR OF / UF | SBM OF / UF |
|---|---|---|---|---|
| USE3L | 360 | 0.3 / 21.9 | 8.3 / 17.5 | 56.4 / 33.9 |
| EUE2L | 342 | 1.2 / 19.3 | 5.3 / 33.3 | 52.3 / 38.0 |
| JPE3 | 354 | 2.0 / 14.4 | 7.1 / 28.5 | 25.1 / 45.8 |
| UKE7L | 228 | 1.8 / 27.2 | 18.4 / 17.5 | 53.9 / 32.0 |
| **Average** | | **1.6 / 20.2** | **10.3 / 25.6** | **42.7 / 38.7** |

DFR and EWMA produce comparable results. SBM violates in ~40% of cases on both sides — it is essentially unusable for short-horizon VaR.

## Fixed Income Local Market Results

Three Barra FI models: USB3 (US), EUB2 (Euro), JPB3 (Japan). Factor types: Term Structure Shift/Twist/Butterfly, Swap Spread, Sector/Rating Credit Spread, Emerging Market Spread, Implied Volatility, MBS Prepayment. Test portfolios: index (Merrill Lynch), treasury, emerging market, random (20- and 80-bond IG and HY).

### VaR Method Performance (Fixed Income)

| Portfolio Group | # Port. | EWMA OF / UF | DFR OF / UF | SBM OF / UF |
|---|---|---|---|---|
| Emerging Market Bond | 13 | 5.1 / 9.0 | 28.2 / 0.0 | 64.1 / 3.8 |
| Euro Merrill Indices | 12 | 1.4 / 13.9 | 9.7 / 18.1 | 38.9 / 22.2 |
| European Treasuries | 16 | 2.1 / 1.0 | 1.0 / 0.0 | 36.5 / 31.3 |
| Japan Merrill Indices | 12 | 1.4 / 9.7 | 19.4 / 8.3 | 18.1 / 20.8 |
| USA Merrill Indices | 20 | 0.0 / 13.3 | 0.0 / 23.3 | 50.0 / 32.5 |
| 20-Bond Euro IG | 50 | 8.3 / 3.0 | 11.3 / 6.7 | 41.3 / 30.7 |
| 80-Bond Euro IG | 50 | 2.0 / 0.0 | 7.7 / 0.3 | 39.0 / 33.0 |
| 20-Bond Euro HY | 50 | 7.7 / 24.7 | 47.0 / 9.0 | 75.0 / 16.3 |
| 80-Bond Euro HY | 50 | 1.3 / 30.0 | 28.7 / 7.0 | 77.3 / 16.3 |
| **Average** | | **3.3 / 11.6** | **17.0 / 8.1** | **48.9 / 23.0** |

DFR overforecasts VaR for small HY portfolios because specific risk dominates (20-bond HY portfolio: specific risk often exceeds common factor risk). For developed-market treasuries, DFR and EWMA are nearly identical because common factor returns explain almost all portfolio return variation (R ≈ 1.0 for UK Gilts).

## Risk Decomposition: Common vs. Specific

The factor model's core advantage over EWMA is risk decomposition:

| Portfolio Type | Common Factor Risk | Specific Risk | Total Risk Pattern |
|---|---|---|---|
| Large-cap equity (USE3L) | Dominant | Small | VaR ≈ EWMA; factor model explains most variation |
| Concentrated industry (UKE7L Leisure) | Moderate | Large (~3 effective stocks) | DFR VaR > EWMA; specific risk drives the difference |
| 20-bond HY portfolio | Variable | Often > common factor risk | DFR overforecasts; specific risk inflates VaR |
| 80-bond HY portfolio | Dominant | Significant but < common | DFR closer to EWMA |
| 20-bond IG portfolio | Dominant | Negligible | DFR ≈ EWMA; even few bonds have little specific risk in IG |

## Global Integrated Model

### Two Approaches to Cross-Market Correlations

| Model | Cross-Market Correlations | Block Structure | Best Horizon |
|---|---|---|---|
| DFR-1B (one block) | Daily-updated via EWMA | Single covariance block for all DFR markets | 1 day |
| DFR-MB (multiple blocks) | Monthly from BIM; local blocks updated daily | Separate local DFR blocks on diagonal; monthly cross-block correlations | 2–10 days |

### One-Day Horizon: Bias Test Results

| Model | % within confidence interval [0.91, 1.09] |
|---|---|
| DFR-1B | 70% (84 / 120 tests) |
| DFR-MB | 45% (54 / 120 tests) |
| SBM | ~0% (all tests fail) |

DFR-1B dominates because daily cross-market correlation updates capture same-day volatility regime shifts across markets.

### Two-Day Horizon: Bias Test Results

| Model | % within confidence interval |
|---|---|
| DFR-MB | 78% (47 / 60 tests) |
| DFR-1B | 40% (24 / 60 tests) |

DFR-1B degrades at multi-day horizons because non-synchronous trading (e.g., US/Japan) creates spurious serial autocorrelation in daily cross-market returns. Using √h scaling amplifies this error. DFR-MB avoids the problem by using monthly correlations for cross-market blocks.

### Non-Synchronous Trading

Daily correlations between US and Japan equity indices are consistently smaller (~0.1–0.3) than monthly correlations (~0.6–0.9) or lagged daily correlations (~0.4–0.5). The calendar-day convention (Japan open to US close) captures US→Japan influence but not the reverse. This does not affect one-day VaR accuracy but causes systematic underforecasting at multi-day horizons when daily correlations are scaled up.

### Horizon-Dependent Model Selection

| Forecast Horizon | Recommended Model | Rationale |
|---|---|---|
| 1 day | DFR-1B | Daily cross-market correlations are accurate at one-day frequency |
| 2–10 days | DFR-MB | Monthly cross-market correlations avoid non-synchronous trading bias |
| >10 days | Rescaled monthly BIM | Daily factor models don't outperform the scaled monthly model |

## Implications for Practice

1. **Factor models work for short-horizon VaR**: The DFR method matches EWMA accuracy while providing full factor-based risk decomposition — common vs. specific risk, factor-by-factor contributions, and risk attribution across countries, industries, and styles.
2. **Never use simple scaling for daily VaR**: The SBM method (dividing monthly covariance by 21) fails systematically across all asset classes and markets. Intra-month volatility dynamics matter.
3. **Risk decomposition enables better management**: Knowing that a portfolio's VaR is driven by specific risk (concentrated positions) vs. common factor risk (systematic exposures) leads to different hedging and diversification decisions. EWMA cannot provide this insight.
4. **The optimal global model is horizon-dependent**: Use DFR-1B for one-day VaR, DFR-MB for 2–10 day horizons, and rescaled BIM beyond 10 days. No single model is best across all horizons.
5. **Non-synchronous trading is a real problem for global models**: Daily correlations between markets in different time zones understate true co-movement. Multi-day VaR models must account for this, either by using monthly correlations or lagged-correlation adjustments.
6. **Small HY portfolios require caution**: When specific risk dominates (e.g., 20-bond HY portfolios), the factor model will overforecast VaR relative to EWMA. This is the correct behavior — specific risk is real — but may appear as conservatism in backtests.

## Connections

- [[menchero-characteristics-factor-portfolios]] — Menchero's framework for simple and pure factor portfolios provides the factor structure that the DFR model uses. The factor covariance matrix F in the DFR method is estimated over the same factors (countries, industries, styles) that define GEM2's pure factor portfolios.
- [[menchero-factor-alignment]] — The factor alignment analysis examines how the factor structure affects portfolio optimization. Barbieri et al. show a complementary concern: how the same factor structure affects risk forecasting accuracy. A misspecified factor structure would produce poor VaR forecasts for the same reasons it produces poor optimization — phantom hedging against spurious factors.
- [[bektic-fama-french-corporate-bonds]] — Bektic et al. show equity factors are strong in HY bonds and weak in IG. Barbieri et al. find a parallel result for risk forecasting: specific risk dominates in small HY portfolios (where the factor model overforecasts) but is negligible in IG portfolios (where factor models and EWMA converge). Both findings trace to the Merton model: HY bonds are equity-like with higher idiosyncratic variation.
- [[houweling-vanzundert-factor-investing-corporate-bonds]] — Houweling & van Zundert's bond-factor portfolios would be natural test cases for the DFR method: factor-tilted credit portfolios where understanding common vs. specific risk contributions is essential for VaR estimation and risk management.
- [[msci-foundations-of-factor-investing]] — The MSCI factor taxonomy (Value, Size, Momentum, Low Vol, Yield, Quality) defines the factor space over which the DFR model estimates covariances. Barbieri et al. validate that this factor space is rich enough to produce accurate short-horizon risk forecasts.

#VaR #risk-management #factor-models #barra #BIM #EWMA #daily-factor-returns #covariance-estimation #multi-asset #fixed-income #equities #non-synchronous-trading #specific-risk
