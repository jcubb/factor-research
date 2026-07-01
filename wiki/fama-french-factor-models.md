# Fama-French Factor Models: The Trilogy (1992, 1993, 2015)

> Source: Fama, Eugene F. and Kenneth R. French. "The Cross-Section of Expected Stock Returns." *Journal of Finance* 47(2), June 1992, pp. 427–465.
> Source: Fama, Eugene F. and Kenneth R. French. "Common Risk Factors in the Returns on Stocks and Bonds." *Journal of Financial Economics* 33(1), 1993, pp. 3–56.
> Source: Fama, Eugene F. and Kenneth R. French. "A Five-Factor Asset Pricing Model." *Journal of Financial Economics* 116(1), 2015, pp. 1–22. DOI: 10.1016/j.jfineco.2014.10.010

Three papers; one unified research program. The 1992 paper identifies *which* characteristics explain the cross-section of returns. The 1993 paper builds risk-factor portfolios to mimic those characteristics and tests whether they explain common variation. The 2015 paper extends the model by adding profitability and investment, motivated by the dividend discount model. Together they define the dominant empirical factor model used in academic finance.

## Overview

**FF (1992)** delivers a decisive blow to the single-factor CAPM: beta has essentially no power to explain average returns when size and book-to-market equity (B/M) are included. Using NYSE, Amex, and NASDAQ data from 1963–1990, Fama and French run Fama-MacBeth cross-sectional regressions and show that size (ME, market equity) and B/M absorb the apparent explanatory roles of leverage and earnings/price. The security market line is flat — more beta does not mean more return.

**FF (1993)** shifts from cross-sectional to time-series methodology. The paper constructs zero-investment mimicking portfolios — SMB (Small Minus Big) and HML (High Minus Low B/M) — and shows that a three-factor model of Mkt, SMB, and HML produces near-zero intercepts in time-series regressions for 25 size × B/M sorted portfolios. The three-factor model is extended to bonds by adding TERM and DEF factors, establishing a unified framework for stocks and bonds. The 1993 paper is the operational specification that practitioners and academics have used for 30+ years.

**FF (2015)** adds two factors motivated directly by the dividend discount model: RMW (Robust Minus Weak profitability) and CMA (Conservative Minus Aggressive investment). The five-factor model explains more of the cross-section of average returns than the three-factor model. The striking finding: once profitability and investment factors are included, HML becomes statistically redundant — its average return is fully explained by its loadings on RMW and CMA.

## The CAPM Failure (1992)

The Sharpe-Lintner CAPM predicts that expected excess return on any asset equals its beta times the expected market excess return. FF (1992) tests this directly.

### Key Findings of the 1992 Paper

| Variable | Used alone | Used with size | Used with size + B/M |
|---|---|---|---|
| Beta (β) | Weak positive slope | Negligible | Negligible |
| Size (ln ME) | Strong negative: ~−0.15%/mo per unit ln ME | — | Significant |
| B/M (ln BE/ME) | Strong positive: ~+0.50%/mo per unit ln B/M | — | Significant |
| Leverage | Significant alone | Absorbed by B/M | Redundant |
| E/P | Significant alone | Absorbed by B/M | Redundant |

**The central result**: In the presence of size and B/M, beta has near-zero slope in cross-sectional regressions of average returns. The SML is too flat relative to the CAPM's prediction. This flat SML becomes a cornerstone of the BAB literature (→ [[frazzini-pedersen-betting-against-beta]]).

The average monthly return difference between the smallest and largest size quintile is roughly **0.74%** (about 9% annualized). The average monthly return difference between the highest and lowest B/M quintile is roughly **1.53%** (about 18% annualized). Both are economically large and statistically robust across subperiods.

## The Three-Factor Model (1993)

### Factor Construction

FF (1993) constructs factor-mimicking portfolios using 6 size × B/M portfolios formed annually:

| Sort | Groups | Description |
|---|---|---|
| Size (ME) | 2 groups | NYSE median cutpoint; Small (S) and Big (B) |
| B/M | 3 groups | Bottom 30% Low, middle 40% Medium, top 30% High |
| Intersection | 6 portfolios | S/L, S/M, S/H, B/L, B/M, B/H |

**SMB** (Small Minus Big): monthly return on equally-weighted average of three small-stock portfolios (S/L, S/M, S/H) minus average of three big-stock portfolios (B/L, B/M, B/H). Captures size risk while being roughly orthogonal to B/M.

**HML** (High Minus Low): monthly return on equally-weighted average of two high-B/M portfolios (S/H, B/H) minus average of two low-B/M portfolios (S/L, B/L). Captures value risk while being roughly orthogonal to size. Correlation between SMB and HML in 1963–1991 data: −0.08.

**Mkt** (Market factor): excess return on a value-weighted portfolio of all sample stocks over the one-month Treasury bill rate.

### The Time-Series Regression

The three-factor model is:

```
R_i - RF = a_i + b_i(RM - RF) + s_i·SMB + h_i·HML + e_i
```

**Asset pricing test**: if the model is well-specified, intercepts a_i should be statistically indistinguishable from zero.

### Results for Stock Portfolios

For 25 size × B/M sorted stock portfolios (1963–1991):

- Three-factor regressions produce intercepts that are close to 0 for virtually all 25 portfolios, despite the wide dispersion in average returns (ranging from ~0.3% to ~1.6% per month)
- R² values for the 25 portfolios range from **0.83 to 0.97** — the three factors explain nearly all time-series variation
- The CAPM alone (one-factor) leaves large, systematic intercepts for extreme size and B/M portfolios

### Bond Extensions

FF (1993) also constructs two bond-market factors:

| Factor | Construction | Interpretation |
|---|---|---|
| TERM | Long-term government bond return − one-month T-bill | Unexpected interest rate changes; term premium |
| DEF | Long-term corporate bond return − long-term government bond return | Default risk premium |

For bonds: TERM and DEF explain most of the common variation in returns on 7 government and corporate bond portfolios. Stock-market factors (Mkt, SMB, HML) add little explanatory power for bonds once TERM and DEF are included, except for low-grade corporates. Markets are integrated but primarily through term-structure risk, not size/value.

### Average Factor Returns (1963–1991)

| Factor | Mean monthly return | Interpretation |
|---|---|---|
| Mkt − RF | ~0.43% | Equity premium |
| SMB | ~0.27% | Size premium |
| HML | ~0.40% | Value premium |
| TERM | ~0.06% | Term premium (statistically small) |
| DEF | ~0.02% | Default premium (very small) |

## The Five-Factor Model (2015)

### Motivation from the Dividend Discount Model

FF (2015) starts from the Miller-Modigliani valuation identity. If total equity value equals the present value of future earnings net of investment:

```
M_t/B_t = [Σ E(Y_t+τ - dB_t+τ) / (1+r)^τ] / B_t
```

This identity implies three cross-sectional predictions, holding everything else fixed:
1. **Lower market price (higher B/M)** → higher expected return (value effect)
2. **Higher expected earnings (profitability)** → higher expected return
3. **Higher expected investment (growth in book equity)** → lower expected return

These three valuation-implied relations motivate adding profitability and investment factors to the three-factor model.

### The Five-Factor Model

```
R_i - RF = a_i + b_i(RM-RF) + s_i·SMB + h_i·HML + r_i·RMW + c_i·CMA + e_i
```

**New factors**:

| Factor | Full Name | Construction | Interpretation |
|---|---|---|---|
| RMW | Robust Minus Weak | Return on diversified portfolio of high-OP stocks minus low-OP stocks | Profitability premium |
| CMA | Conservative Minus Aggressive | Return on low-investment stocks minus high-investment stocks | Investment premium |

OP (operating profitability) = (revenues − COGS − interest expense − SG&A) / book equity.

Investment = annual change in total assets divided by lagged total assets.

### Key Results of the 2015 Paper

- The five-factor model produces lower GRS test statistics (fewer rejected intercepts) than the three-factor model for portfolios sorted on size, B/M, profitability, and investment
- **HML becomes redundant**: after adding RMW and CMA, the average return on HML is fully captured by its loadings on other factors — its alpha in the five-factor model is statistically zero. This happens because value-tilted (high B/M) firms also tend to be more profitable and more conservative in investment
- **Main failure**: small-cap stocks with high investment but low profitability — "small junk" — remain problematic; the model systematically under-explains their negative average excess returns
- Results are robust across multiple factor construction choices (different sort cutpoints, value-weighted vs. equal-weighted components)

### Comparison of Models

| Model | Factors | GRS F-stat (lower = better) | Key failure |
|---|---|---|---|
| CAPM | Mkt | Very high | Size, value, profitability, investment effects |
| FF (1993) 3-factor | Mkt, SMB, HML | Moderate | Profitability, investment, momentum |
| FF (2015) 5-factor | Mkt, SMB, HML, RMW, CMA | Lower | Small-low profitability-high investment stocks |

## Factor Construction Details

### Annual Rebalancing Calendar

Both the 1993 and 2015 papers form portfolios annually in **June of year t** using:
- Size: market equity at end of June (current)
- B/M: book equity for fiscal year ending in calendar year t−1 divided by market equity at end of December t−1
- OP: operating profitability for fiscal year t−1 / book equity for year t−1
- Investment: annual asset growth for fiscal year t−1

Portfolio returns run from **July of year t through June of year t+1**, then reformed.

### Universe

NYSE, Amex, and NASDAQ stocks with CRSP/Compustat data. NYSE breakpoints only for size, B/M, OP, and investment sorts (to prevent microcap-dominated breakpoints). Negative B/M firms excluded. Firms need 2 years on Compustat to avoid backfill bias.

## Risk vs. Mispricing Interpretations

Fama and French present both interpretations without taking a strong stand:

**Risk-based**: Size and B/M proxy for sensitivity to undiversifiable macroeconomic risks. Small firms and high-B/M firms are distressed; they perform poorly precisely when the marginal utility of wealth is high. Factor loadings are legitimate risk measures.

**Behavioral**: High-B/M stocks are underpriced by overreacting investors who extrapolate recent poor performance. Size effects partly reflect neglected-firm phenomena. The mispricing corrects slowly.

**Empirical evidence is ambiguous**: The three-factor model passes the time-series test (near-zero intercepts) but this is compatible with both risk and mispricing stories. The MSCI foundations paper (→ [[msci-foundations-of-factor-investing]]) notes that both explanations co-exist — the premium persists because neither fully eliminates it.

## Implications for Practice

1. **Beta alone is insufficient**: A portfolio's CAPM beta explains almost nothing about its expected return. Practitioners must account for size and value tilts at minimum.
2. **The three-factor model is the baseline**: Any claimed alpha should be evaluated against a three-factor (and ideally five-factor) benchmark. Single-factor alphas massively overstate active manager skill for strategies with size/value tilts.
3. **Factor construction matters less than you think**: The 2015 paper shows that different reasonable construction choices produce similar inferences — the economic signals are robust.
4. **HML is theoretically redundant but practically useful**: Although the 2015 paper shows HML is redundant in-sample, standalone value exposure remains a useful portfolio construction tool — especially because HML's correlation with CMA and RMW is not perfect out-of-sample.
5. **Small-cap quality interaction**: The FF models have a known failure mode — small stocks that combine high investment with low profitability ("junk"). Practitioners building small-cap strategies should overlay quality screens.
6. **Bond integration**: The 1993 framework integrates stocks and bonds — the same TERM and DEF factors that explain bond returns also show up in stock returns. A true multi-asset risk model requires at least five factors (3 stock + 2 bond).

## Connections

- [[msci-foundations-of-factor-investing]] — The MSCI practitioner overview takes FF as the foundation; the Value and Size factors in the MSCI taxonomy map directly to HML and SMB. FF's risk-vs-mispricing ambiguity is discussed in the MSCI cyclicality analysis.
- [[ehsani-linnainmaa-factor-momentum]] — Factor momentum exploits autocorrelation in factor returns including SMB, HML, RMW, and CMA. The FF factor zoo is the universe over which Ehsani & Linnainmaa demonstrate momentum timing.
- [[frazzini-pedersen-betting-against-beta]] — The BAB paper takes the FF (1992) flat SML as its empirical motivation; BAB alpha is evaluated in a world where size, value, and momentum are already accounted for (four-factor Carhart model).
- [[moskowitz-nonlinear-momentum]] — The nonlinear momentum paper also evaluates TSMOM strategies in FF factor environments; factor momentum signals studied include HML and SMB.

#fama-french #factor-models #size #value #profitability #investment #smb #hml #rmw #cma #capm #three-factor #five-factor #asset-pricing #cross-section
