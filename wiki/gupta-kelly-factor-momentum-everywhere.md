# Factor Momentum Everywhere

> Source: Gupta, Tarun, and Bryan Kelly. "Factor Momentum Everywhere." *The Journal of Portfolio Management* 45, no. 3 (Quantitative Special Issue, 2019): 13–36.
> AQR Capital Management, Yale School of Management

## Overview

Gupta and Kelly document that momentum is a pervasive phenomenon among common equity factors, not just individual stocks. Using a collection of 65 characteristic-based long-short factor portfolios, they show that factor returns exhibit strong serial correlation and that a portfolio strategy exploiting this persistence — buying recently winning factors and selling recently losing factors — outperforms traditional stock-level momentum (UMD), industry momentum (INDMOM), and short-term reversal (STR) on a standalone basis.

The paper distinguishes between two implementations: **time-series factor momentum (TSFM)**, which scales exposure to each factor by its own recent return, and **cross-section factor momentum (CSFM)**, which ranks factors by recent performance and goes long winners / short losers. Though TSFM and CSFM are highly correlated (>0.90), TSFM is the more efficient implementation — it earns significant alpha relative to CSFM, while CSFM earns negative alpha relative to TSFM. The combined TSFM strategy achieves an annualized Sharpe ratio of 0.84 with a one-month formation window, outperforming UMD (SR = 0.56) and surviving controls for the FF five-factor model.

A striking finding is that factor momentum **avoided the 2009 momentum crash** entirely. While UMD lost 31% from March to May 2009 and INDMOM lost 24%, one-month TSFM and CSFM both earned 18% over the same period. Factor momentum also works internationally across European, Pacific, and global equity markets with comparable magnitudes.

## Factor Sample and Construction

- **65 factors** covering the main anomaly categories: valuation ratios, factor exposures (BAB), size, investment, profitability, risk measures, and liquidity measures
- Constructed from US equities using 6 size × characteristic bins (2×3), value-weighted within bins
- Long-short portfolio = 0.5 × (Large High + Small High) − 0.5 × (Large Low + Small Low)
- Sample: 1963–2017 (US), with international variants for Europe, Pacific, and Global ex-US
- Factors oriented so predicted sign of expected return is positive

## Factor Persistence: AR(1) Evidence

| Statistic | Value |
|---|---|
| Average monthly AR(1) across 65 factors | 0.11 |
| Factors with positive AR(1) | 59 of 65 |
| Factors with statistically significant AR(1) | 49 of 65 |
| Market excess return AR(1) (comparison) | 0.07 |
| PCs needed to explain 90% of factor variance | 19 of 65 |

The AR(1) structure is ubiquitous — factor returns are serially correlated at the monthly frequency, providing the statistical foundation for factor timing.

## TSFM Construction

For factor i with formation window j months:

**f^TSFM_{i,j,t+1} = s_{i,j,t} × f_{i,t+1}**

where the scaling term is: s_{i,j,t} = min{ max( (1/σ_{i,j}) × Σ f_{i,t-τ+1} , −2 ), 2 }

- Converts past returns to z-scores using trailing volatility (3-year for j < 12, 10-year for j ≥ 12)
- Caps z-scores at ±2
- Combined TSFM aggregates long and short legs across all 65 factors, scaled to $1 long / $1 short

## Performance Comparison: US Equities

| Strategy | Formation Window | Annualized Return (%) | Annualized SR | Alpha vs. EW Factor (%) | Alpha vs. FF5 (%) |
|---|---|---|---|---|---|
| TSFM | 1-1 (one month) | 12.0 | 0.84 | 10.3 (t = 4.6) | ~10 |
| TSFM | 1-12 | 9.5 | 0.70 | ~6 | ~8 |
| TSFM | 1-60 (five year) | 7.1 | 0.72 | ~5 | ~5 |
| TSFM | 2-12 | — | 0.54 | — | — |
| TSFM | 13-60 | — | 0.53 | — | — |
| CSFM | 1-1 | — | 0.77 | — | — |
| CSFM | 1-12 | — | 0.70 | — | — |
| UMD | 2-12 | 6.1 | 0.56 | — | — |
| INDMOM | 1-12 | — | 0.61 | — | — |
| STR | 1-1 | 3.4 | 0.34 | — | — |
| EW (equal-weighted raw factors) | — | — | 1.07 | — | — |

Key findings:
- One-month formation is strongest, but all windows (1-month through 5-year) produce positive and significant performance
- TSFM alpha vs. EW factor portfolio is 10.3% p.a. (t = 4.6) — not simply harvesting static factor premia
- TSFM dominates CSFM: positive alpha of TSFM vs. CSFM, but negative alpha of CSFM vs. TSFM

## TSFM vs. CSFM: Why TSFM Wins

| Feature | TSFM | CSFM |
|---|---|---|
| Signal source | Own past return (absolute) | Relative ranking among factors |
| When all factors rise together | Goes long all of them | Mixed (relative ranking unchanged) |
| Alpha vs. the other | Positive, significant | Negative, significant |
| Correlation between the two | >0.90 for all formation windows | >0.90 |
| Interpretation | Purer measure of factor momentum | Contaminates momentum with relative performance |

## Factor Momentum vs. Stock Momentum

| Feature | Factor Momentum (TSFM 1-1) | Stock Momentum (UMD) |
|---|---|---|
| Sharpe ratio | 0.84 | 0.56 |
| 2009 crash behavior | +18% (Mar–May 2009) | −31% |
| Correlation with STR | −0.80 (1-month window) | — |
| Formation window stability | Positive for all windows (1m–5yr) | Reversal at short and long horizons |
| Alpha after controlling for the other | TSFM has sig. alpha vs. UMD | UMD has ~zero alpha vs. TSFM |

Factor momentum captures persistence in the common factors that drive stock returns. Unlike stock momentum (concentrated at 6–12 month horizons with reversal at short and long horizons), factor momentum is positive at all horizons from one month through five years.

## Spanning Results

- **TSFM subsumes UMD**: After controlling for 1-12 TSFM, UMD's alpha drops below 1% and is insignificant
- **TSFM subsumes INDMOM**: INDMOM alpha is insignificant after controlling for TSFM
- **TSFM does not subsume STR**: Short-term reversal retains large, significant alphas (5–10% p.a.) even after controlling for factor momentum — they capture distinct patterns
- **CSFM does not subsume TSFM**: TSFM earns significant alpha relative to CSFM for all look-back windows

## Portfolio Combinations (Ex Post Tangency)

| Portfolio Combination | Tangency SR |
|---|---|
| TSFM variants only (1-1, 2-12, 13-60) | 1.07 |
| CSFM variants only | 0.83 |
| TSFM + CSFM (levered TSFM, short CSFM) | 0.98 |
| TSFM + UMD + FF5 | 1.65 |
| TSFM + UMD + STR + FF5 | 1.32 |
| All momentum + FF5 + HML-Devil | 1.70 |

TSFM 1-1 consistently receives the largest tangency weight. MKT, CMA, and RMW are significant contributors alongside factor momentum.

## Implementability

- Factor momentum turnover (~30× annual for TSFM 1-1) is comparable to stock momentum (~30× for UMD)
- Net Sharpe ratios (assuming 10 bps per unit of turnover): TSFM 1-12 net SR = 0.63, vs. UMD net SR = 0.51
- STR's performance is **entirely wiped out** by transaction costs
- Factor momentum trades Fama-French-style factors (large, liquid portfolios), so implementation is more practical than stock-level strategies

## International Evidence

- International AR(1) coefficients: average 0.10 (vs. 0.11 US), positive for 51/62 factors, significant for 30
- International TSFM SR = 0.73 (vs. 0.84 US)
- International alpha vs. raw factors: 6.6% p.a.
- US and international TSFM 1-1 correlation: 0.62
- Combined US + international tangency SR: 0.83
- UMD and INDMOM alphas are zero after controlling for international TSFM/CSFM

## Implications for Practice

1. **Factor momentum is the more general phenomenon**: Stock momentum (UMD) and industry momentum are special cases — they arise because factors are persistent, and stocks inherit factor persistence through their loadings.
2. **Time-series implementation dominates cross-section**: TSFM is the more efficient approach because it captures absolute factor persistence rather than relative rankings.
3. **Factor momentum complements value**: Combining TSFM with value strategies (especially HML-Devil) produces especially strong tangency portfolios, echoing the momentum-value diversification benefit at the stock level.
4. **Crash resilience**: Factor momentum did not crash in 2009 when stock momentum lost 31% — making it a more robust momentum implementation.
5. **Practical implementation advantage**: Factor portfolios are large and liquid; timing them involves less turnover and lower costs than stock-level momentum.
6. **Multi-horizon signal**: Unlike stock momentum (6–12 month sweet spot), factor momentum works from one month through five years, simplifying signal construction.

## Connections

- [[ehsani-linnainmaa-factor-momentum]] — Ehsani & Linnainmaa (2022, JF) provide the theoretical framework: factor autocorrelation drives stock momentum, and high-eigenvalue PCs of factor returns capture the bulk of momentum profits. Gupta & Kelly's empirical TSFM strategy is the practitioner implementation of this insight, using 65 named factors rather than PCs. Both papers converge on the conclusion that momentum is fundamentally a factor-level phenomenon.
- [[kelly-principal-portfolios]] — Kelly et al.'s principal portfolios framework provides the optimal way to exploit the factor return predictability that Gupta & Kelly document. The prediction matrix Π captures exactly the AR(1) persistence structure across factors that TSFM times.
- [[moskowitz-nonlinear-momentum]] — Moskowitz et al. show that the optimal TSFM signal weighting is an S-curve, not linear. Gupta & Kelly use a linear (z-score, capped) implementation. Applying Moskowitz et al.'s nonlinear weighting to Gupta & Kelly's 65-factor universe is a natural extension.
- [[fama-french-factor-models]] — The FF five-factor model is used as a benchmark throughout. TSFM earns large alpha relative to FF5, and FF5 factors (especially MKT, RMW, CMA) are significant tangency portfolio components alongside TSFM.
- [[frazzini-pedersen-betting-against-beta]] — BAB is one of the 65 factors in the sample and has the highest individual Sharpe ratio (0.90). Factor momentum's ability to time BAB alongside other factors further amplifies its performance.
- [[msci-foundations-of-factor-investing]] — MSCI documents factor cyclicality as a key challenge for practitioners. Gupta & Kelly's TSFM strategy is a systematic answer to factor cyclicality: dynamically adjust factor exposure based on recent performance.

#factor-momentum #TSFM #CSFM #momentum #factor-timing #stock-momentum #international #serial-correlation #AR1 #momentum-crash
