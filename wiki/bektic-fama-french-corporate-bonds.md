# Extending Fama-French Factors to Corporate Bond Markets

> Source: Bektic, Demir, Josef-Stefan Wenzler, Michael Wegner, Dirk Schiereck, and Timo Flags. "Extending Fama-French Factors to Corporate Bond Markets." *The Journal of Fixed Income* 27, no. 2 (Fall 2017): 5–30.
> DOI: 10.3905/jfi.2017.27.2.005 | Deka Investment, TU Darmstadt

## Overview

Bektic et al. test whether the four equity-based Fama-French factors — size, value, profitability, and investment — extend to corporate bond markets. Using BAML bond index data for U.S. high-yield (HY), U.S. investment-grade (IG), and European IG markets from December 1996 to December 2016, they construct corporate bond factor portfolios based on the equity characteristics of the bond issuers. The theoretical justification comes from the Merton (1974) structural model: a corporate bond is equivalent to a risk-free bond plus a short put on the issuer's equity, so any factor that predicts equity returns should also predict bond returns through the default probability channel.

The results are strongest for U.S. HY bonds, where all four single factors are statistically significant and the equal-weighted multi-factor portfolio delivers an annualized excess return of 2.33% (t = 3.12) with Sharpe ratios up to 30% higher than the market. For U.S. IG and European IG markets, results are weaker and mixed — consistent with the Merton model prediction that IG bonds (with low probability of default) behave more like risk-free bonds and are less sensitive to equity-linked factors.

A notable finding is that profitability is **negatively priced** in both IG segments: bonds of less profitable firms outperform, the opposite of the equity result. The authors attribute this to default risk compensation — low-profitability firms have higher default risk, and IG bondholders are compensated for bearing it. In contrast, profitability is positively priced in U.S. HY, where the equity-like behavior of high-yield debt aligns with the equity profitability premium.

## Data and Sample

| Feature | Detail |
|---|---|
| Data source | Bank of America Merrill Lynch (BAML) bond indices |
| U.S. HY universe | BAML US High Yield Master II Index |
| U.S. IG universe | BAML US Corporate Master Index |
| European IG universe | BAML Euro Corporate Index |
| Sample period | December 1996 – December 2016 (20 years) |
| Bond pricing | Month-end bid prices from BAML |
| Equity data | Bloomberg (market cap, book equity, earnings, total assets) |
| Portfolio construction | Top-decile (long-only) and long-short decile portfolios |
| Rebalancing | Monthly |
| Benchmark | Equal-weighted average of all decile excess returns per market |

## Factor Definitions

All factors use equity characteristics of the bond issuer, applied to the corporate bond cross-section:

| Factor | Definition | Equation | Portfolio |
|---|---|---|---|
| Size | Equity market capitalization | Size = SO × PPS | Smallest 10% of issuers |
| Value | Book-to-market equity | Value = BE_{t-6} / ME_t | Highest 10% B/M issuers |
| Profitability (OP) | Operating profitability | OP = EBT_{t-6} / BE_{t-6} | Most profitable 10% of issuers |
| Investment (Inv) | Asset growth | Inv = (TA_{t-6} − TA_{t-18}) / TA_{t-18} | Lowest 10% asset growth |

The use of equity-based rather than bond-specific factor definitions is deliberate: it tests whether the Merton structural model linkage between equity and credit is strong enough to transmit equity factor premia to bond markets.

## Single-Factor Results (Long-Only, Top Decile)

| Factor | Market | Annual Return (%) | Sharpe Ratio | Alpha vs. DEF (%) | t-stat (DEF) | Alpha vs. 7-Factor (%) | t-stat (7F) |
|---|---|---|---|---|---|---|---|
| Size | US HY | 6.94 | 0.46 | Significant | >2.0 | Significant | >2.0 |
| Value | US HY | 5.99 | 0.46 | Significant | >2.0 | — | — |
| Profitability | US HY | 5.86 | 0.62 | Significant | >2.0 | Significant | >2.0 |
| Investment | US HY | 7.21 | 0.52 | Significant | >2.0 | Significant | >2.0 |
| Size | US IG | 1.41 | 0.33 | Sig. at 10% | ~1.7 | Not significant | <1.6 |
| Value | US IG | 1.37 | 0.27 | Significant | >2.0 | Not significant | <1.6 |
| Profitability | US IG | 0.78 | 0.24 | Not significant | <1.6 | Not significant | <1.6 |
| Investment | US IG | 1.19 | 0.29 | Significant | >2.0 | Not significant | <1.6 |
| Size | EUR IG | 1.27 | 0.39 | Not significant | <1.6 | Not significant | <1.6 |
| Value | EUR IG | 1.01 | 0.27 | Not significant | <1.6 | Not significant | <1.6 |
| Profitability | EUR IG | 0.77 | 0.43 | Not significant | <1.6 | Not significant | <1.6 |
| Investment | EUR IG | 1.68 | 0.68 | Significant | >2.0 | Significant | >2.0 |

Market comparisons: US HY market SR = 0.45, US IG market SR = 0.23, EUR IG market SR = 0.42.

## Multi-Factor Portfolio Results

Equal-weighted combination: r^MultiFactor = 0.25 × r^Size + 0.25 × r^Value + 0.25 × r^OP + 0.25 × r^Inv

| Market | Long-Only Annual Excess Return (%) | t-stat | Long-Only SR | Market SR | L/S SR |
|---|---|---|---|---|---|
| US HY | 2.33 | 3.12 | 0.59 | 0.45 | 0.51 |
| US IG | 0.23 | 1.63 | 0.31 | 0.23 | 0.34 |
| EUR IG | 0.21 | 1.39 | 0.45 | 0.42 | 0.56 |

Multi-factor portfolios consistently achieve higher Sharpe ratios than the market across all segments. The improvement is largest in US HY (+31%) and meaningful in EUR IG (+7% long-only, +33% long-short). Maximum drawdowns are comparable to the market, and results survive controls for the seven-factor model (FF5 equity + TERM + DEF) in U.S. HY.

## Cross-Asset Correlations

Correlations between corporate bond factor portfolios and equity FF factors are low, suggesting that bond factors capture different aspects than their equity counterparts:

| Market | Correlation Range (Bond factors vs. Equity FF + TERM + DEF) |
|---|---|
| US HY | −0.15 (OP and DEF) to 0.56 (Size and Inv) |
| US IG | −0.44 (OP and DEF) to 0.58 (Size and DEF) |
| EUR IG | −0.67 (OP and DEF) to 0.51 (Value and DEF) |

Low and negative correlations between equity and bond factors imply significant diversification benefits from combining factor portfolios across asset classes.

## The HY vs. IG Divide

The Merton (1974) model explains the asymmetric results:

| Feature | High Yield | Investment Grade |
|---|---|---|
| Default probability | High | Low |
| Equity put component | Large (at-the-money) | Small (deep out-of-the-money) |
| Bond behavior | Equity-like | Risk-free-like |
| Sensitivity to equity factors | Strong | Weak |
| Profitability premium sign | Positive (as in equities) | Negative (compensating default risk) |
| All four factors significant | Yes | No |

HY bonds behave like equities because their value is dominated by the equity put component (higher probability of default makes the put more valuable). IG bonds behave more like government bonds because the default probability is low and the put is far out-of-the-money.

## Robustness

| Test | Result |
|---|---|
| Transaction costs (estimated by rating, maturity, turnover) | Results unchanged |
| Long-short portfolio construction | Multi-factor SR still higher than market |
| Duration controls | Results unchanged |
| Market-cap weighting (instead of equal-weight) | Results unchanged |
| Subperiod analysis | Results unchanged |
| Excluding financials | Results unchanged |
| Controlling for FF5 equity factors + TERM + DEF | US HY alphas survive; IG alphas do not |

## Implications for Practice

1. **Equity factors extend to HY bonds**: All four FF factors — size, value, profitability, and investment — are statistically and economically significant in U.S. HY corporate bonds. This is consistent with the Merton structural model: HY bonds are equity-like, so equity factors predict their returns.
2. **IG markets are a different regime**: Factor effects are weak and mostly insignificant in IG bonds. Practitioners should not assume equity factor strategies translate directly to IG credit.
3. **Profitability reverses sign in IG**: Bonds of less profitable IG firms outperform because investors are compensated for bearing default risk. This is the opposite of the equity profitability premium and requires careful factor design for credit markets.
4. **Multi-factor diversification works**: Combining all four factors in equal weights produces Sharpe ratios 30% higher than the market benchmark across segments, even though individual factors are noisy.
5. **Bond-specific factor definitions may improve results**: The authors use equity-based definitions throughout. Bond-specific definitions (e.g., spread-based value, issue-size-based size) could potentially capture credit-specific premia that equity characteristics miss.
6. **Low equity-bond factor correlations enable cross-asset factor portfolios**: The weak correlation between bond factor returns and equity FF factor returns suggests that combining equity and bond factor strategies within a single portfolio offers meaningful diversification.

## Connections

- [[fama-french-factor-models]] — Bektic et al. directly extend the FF five-factor model to corporate bonds. The four equity factors (SMB, HML, RMW, CMA) serve as both the theoretical motivation and the empirical benchmark. The seven-factor regression model (FF5 + TERM + DEF) is used to test whether bond factor returns are independent of equity factor returns.
- [[frazzini-pedersen-betting-against-beta]] — Frazzini & Pedersen show BAB works across US equities, Treasuries, credit indices, and futures. Bektic et al.'s finding that equity factors work best in HY (where bonds are equity-like) and weakest in IG (where bonds are rate-like) parallels BAB's variation in magnitude across asset classes based on leverage constraints.
- [[msci-foundations-of-factor-investing]] — MSCI's six-factor taxonomy covers equity markets only. Bektic et al. demonstrate that factor investing can extend to credit, but the transmission is asymmetric: strong in HY, weak in IG. This has implications for multi-asset factor allocation strategies that MSCI-style factor indexes might eventually address.
- [[cohen-frazzini-economic-links]] — Cohen & Frazzini document cross-predictability between economically linked equities. Bektic et al. document a related phenomenon: cross-asset predictability from equities to bonds of the same issuer, mediated by the Merton structural model rather than supply-chain links.

#corporate-bonds #fama-french #credit-factors #high-yield #investment-grade #merton-model #size #value #profitability #investment #multi-factor #cross-asset
