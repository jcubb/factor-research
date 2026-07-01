# Factor Investing in the Corporate Bond Market

> Source: Houweling, Patrick, and Jeroen van Zundert. "Factor Investing in the Corporate Bond Market." *Financial Analysts Journal* 73, no. 2 (2017): 100–115. Working paper version: November 2014.
> Robeco Quantitative Strategies, Rotterdam

## Overview

Houweling and van Zundert provide the first comprehensive, multi-factor study of corporate bond markets using **bond-only characteristics** — they deliberately avoid equity or accounting data so that all bonds in the index universe can be included, including those of private issuers. Using constituent data from the Barclays U.S. Corporate Investment Grade and High Yield indices over 1994–2013, they document that Size, Low-Risk, Value, and Momentum factors all earn economically meaningful and statistically significant risk-adjusted premiums in corporate bonds.

The multi-factor portfolio (equal allocation to all four factors) doubles the Sharpe ratio versus the market in both segments: 0.33 vs. 0.13 in IG and 0.52 vs. 0.24 in HY. The six-factor alpha (controlling for FF equity factors, TERM, and DEF) is 1.00% per annum in IG and 3.21% in HY — large relative to the Default premiums of 0.59% and 2.46% respectively. These premiums survive transaction costs: after-cost multi-factor Sharpe ratios remain 0.26 (IG) and 0.46 (HY), still well above after-cost market Sharpe ratios of 0.10 and 0.20.

A key contribution is the multi-asset analysis. Adding corporate bond factor investing on top of equity factor investing raises the combined portfolio Sharpe ratio from 0.89 to 0.97, with an incremental alpha of approximately 1% per year. Corporate bond factor alphas have low correlation with equity factor alphas (24% for IG, 46% for HY), confirming that bond factors capture distinct effects beyond their equity counterparts.

## Data and Sample

| Feature | Detail |
|---|---|
| IG universe | Barclays U.S. Corporate Investment Grade Index |
| HY universe | Barclays U.S. Corporate High Yield Index |
| Sample period | January 1994 – December 2013 (20 years) |
| Bond-month observations | ~1.1 million (800K IG + 300K HY) |
| Monthly IG constituents | 2,456 – 4,768 |
| Monthly HY constituents | 584 – 2,086 |
| Return measure | Excess return over duration-matched Treasuries |
| Portfolio weighting | Equally weighted (robustness: market-value weighted) |
| Portfolio size | Top-decile (10% of bonds); robustness: quintile (20%) |
| Holding period | 12 months (overlapping portfolios, Jegadeesh-Titman method) |
| Survivorship bias | None — defaults reflected via expected recovery rates |

## Factor Definitions (Bond-Only Characteristics)

| Factor | Definition | Measurement | Key Design Choice |
|---|---|---|---|
| Size | Company's total index weight (sum of all its bond weights) | Index weight in current month | Company-level (not bond-level), paralleling equity size effect |
| Low-Risk | High-rated, short-maturity bonds | IG: AAA to A−, shortest maturity bonds; HY: BB+ to B−, shortest maturity | Combines rating and maturity; average maturity threshold ≈ 2.8yr (IG), 3.7yr (HY) |
| Value | Spread "cheapness" vs. fundamentals | Residual from cross-sectional regression of spread on rating dummies + maturity | Bonds with the largest positive % deviation from fitted spread |
| Momentum | Past 6-month excess return (1-month lag) | Excess return vs. duration-matched Treasuries | Following Jostova et al. (2013); 1-month implementation lag |

The choice to use bond-only data (no equity or accounting information) is deliberate: it ensures universal applicability across all issuers, including private companies, and demonstrates that factor premiums exist even with the most basic inputs.

## Single-Factor Results

| Factor | Market | Excess Return vs. Market (%) | Sharpe Ratio | Market SR | Alpha vs. DEF (%) | 6-Factor Alpha (%) |
|---|---|---|---|---|---|---|
| Size | IG | 0.75 | 0.32 | 0.13 | 0.43 | 0.18–similar |
| Low-Risk | IG | 0.37 | 0.42 | 0.13 | 0.52 | 0.57–similar |
| Value | IG | 1.92 | 0.31 | 0.13 | 1.52 | 2.23 |
| Momentum | IG | 0.37 | 0.22 | 0.13 | Not sig. | Not sig. |
| Size | HY | 4.02 | 0.57 | 0.24 | 2.28 | 4.86 |
| Low-Risk | HY | 1.45 | 0.57 | 0.24 | 2.70 | 2.25 |
| Value | HY | 5.38 | 0.45 | 0.24 | 4.25 | 4.25 |
| Momentum | HY | 2.16 | 0.44 | 0.24 | 2.31 | 0.83 |

All single-factor Sharpe ratios exceed the market Sharpe ratio. All alphas are positive and statistically significant except IG Momentum. The magnitude of factor premiums relative to the Default premium (0.59% IG, 2.46% HY) is striking: investors could have quadrupled returns by allocating to factors rather than passively holding the market.

## Multi-Factor Portfolio

| Metric | Investment Grade | High Yield |
|---|---|---|
| Multi-factor return vs. market (%) | 1.44 | 5.72 |
| Multi-factor Sharpe ratio | 0.33 | 0.52 |
| Market Sharpe ratio | 0.13 | 0.24 |
| SR improvement | 2.5× | 2.2× |
| DEF alpha (%) | 1.19 | 4.52 |
| 6-factor alpha (%) | 1.00 | 3.21 |
| Multi-factor tracking error (%) | ~2.3 | ~5.8 |
| Single-factor avg tracking error (%) | ~3.5 | ~7.0 |
| CAPM beta (vs. DEF) | ~1.0 | ~1.0 |

The multi-factor portfolio halves the tracking error compared to individual factors while maintaining top-tier alpha and Sharpe ratios. Factor outperformance correlations are ≤51%, and Value is even negatively correlated with the other three, generating strong diversification benefits.

## Transaction Costs

| Factor | IG Turnover (%) | IG Net SR | HY Turnover (%) | HY Net SR |
|---|---|---|---|---|
| Size | Low | 0.28 | Low | 0.52 |
| Low-Risk | Low | 0.31 | Low | 0.49 |
| Value | Moderate | 0.27 | Moderate | 0.41 |
| Momentum | >100% | ≈ Market | >100% | 0.35 |
| Multi-factor | — | 0.26 | — | 0.46 |
| Market | 32% (IG), 56% (HY) | 0.10 | — | 0.20 |

Average transaction costs: 0.39% per bond (IG), 0.69% per bond (HY). Momentum has the highest turnover, and its after-cost IG Sharpe ratio drops to roughly market level. But the multi-factor portfolio retains substantial after-cost improvements (2.6× market SR in IG, 2.3× in HY).

## Multi-Asset Analysis

Four test portfolios with allocation: 40% equities, 20% government bonds, 20% IG, 20% HY.

| Portfolio | Equity Allocation | Bond Allocation | SR | IR vs. Traditional | Alpha vs. 4 markets (%) |
|---|---|---|---|---|---|
| Traditional | Equity market | Bond markets | 0.70 | — | — |
| Equity Factor Investing | Equity multi-factor | Bond markets | 0.89 | 0.64 | 2.49 |
| Corp Bond Factor Investing | Equity market | Bond multi-factor | 0.81 | 0.86 | 2.39–3.21 |
| Equity + Corp Bond Factor | Equity multi-factor | Bond multi-factor | 0.97 | 0.76 | 3.44 |

Adding corporate bond factors on top of equity factors increases alpha by ~1% per annum (from 2.49% to 3.44%) and IR from 0.64 to 0.76. The bond factor alphas have low correlation with equity factor alphas: 24% (IG) and 46% (HY), confirming that corporate bond factor investing captures distinct effects.

## Robustness

| Test | Result |
|---|---|
| Alternative factor definitions (bond size, spread-based Low-Risk, alternative Value, 3/9/12-month momentum) | Results robust; Low-Risk especially consistent across all definitions |
| Market-value weighting (instead of equal-weight) | Returns and alphas decrease modestly; still significant (t > 2.5) |
| Quintile portfolios (20% instead of 10%) | Weaker but still significant (SR 0.29/0.43, alpha significant) |
| Subperiods (1994–2003 vs. 2004–2013) | Significant in both halves; HY slightly stronger in 2004–2013 |
| Doubling transaction cost estimates | Results still favorable (except IG Momentum) |

## Implications for Practice

1. **Bond-specific factor definitions work**: Using only bond characteristics (rating, maturity, spread, return) — without any equity or accounting data — is sufficient to capture meaningful factor premiums. This makes implementation straightforward and universally applicable.
2. **Multi-factor portfolios are essential for credit**: Single-factor tracking errors are large (up to 9% in HY), making individual factors unattractive for benchmark-relative managers. The multi-factor combination halves tracking error while preserving alpha.
3. **Factor investing should be a strategic allocation decision**: The large tracking errors and cyclical factor returns mean that factor investing in credit is a long-term commitment, not a tactical trade. Investors should allocate to factors at the strategic asset allocation level, not delegate it implicitly to active managers.
4. **Corporate bond factors diversify equity factors**: Adding credit factor investing on top of equity factor investing adds approximately 1% alpha per annum, because the two capture partially different effects (correlation of alphas: 24–46%).
5. **HY is the natural home for factor investing in credit**: All four factors are stronger in HY than in IG, consistent with the higher credit risk (and thus higher equity sensitivity) of HY bonds. IG Momentum is the weakest link.
6. **Transaction costs are manageable**: Factor premiums survive after realistic transaction cost estimates. The overlapping 12-month holding period keeps turnover reasonable for Size, Low-Risk, and Value, though Momentum requires careful implementation.

## Connections

- [[bektic-fama-french-corporate-bonds]] — Bektic et al. (2017) study the same question but use **equity-based** factor definitions (equity market cap, book-to-market, operating profitability, asset growth) applied to corporate bond cross-sections. Houweling & van Zundert use **bond-only** definitions (index weight, rating/maturity, spread residual, past bond return). The two approaches are complementary: Bektic's relies on Merton model linkage, while Houweling & van Zundert's avoids any equity data. Both find strongest results in HY.
- [[frazzini-pedersen-betting-against-beta]] — Houweling & van Zundert's Low-Risk factor is the credit-market analog of BAB. Frazzini & Pedersen show BAB works across corporate bond indices; Houweling & van Zundert define Low-Risk using rating and maturity rather than beta, finding similar results. The Low-Risk factor has the highest Sharpe ratio among individual factors in both IG and HY.
- [[fama-french-factor-models]] — The FF three-factor model (supplemented with Carhart MOM, TERM, and DEF) serves as the benchmark for alpha estimation. The six-factor alphas of corporate bond factor portfolios are large and significant, demonstrating that bond factor premiums are not explained by equity factor exposures.
- [[msci-foundations-of-factor-investing]] — MSCI's six-factor taxonomy (Value, Size, Momentum, Low Volatility, Yield, Quality) provides the equity framework that Houweling & van Zundert extend to corporate bonds. Their four bond factors map onto MSCI's Value, Size, Momentum, and Low Volatility categories, showing that factor investing is a cross-asset phenomenon.
- [[fama-french-luck-vs-skill]] — Fama & French (2010) show that actively managed equity funds fail to cover costs. Houweling & van Zundert's results suggest a similar conclusion for credit: rather than delegating to active bond managers (who may or may not deliver factor exposure), investors should strategically and explicitly allocate to bond factors.

#corporate-bonds #factor-investing #credit-factors #size #low-risk #value #momentum #multi-factor #multi-asset #transaction-costs #strategic-allocation #bond-characteristics
