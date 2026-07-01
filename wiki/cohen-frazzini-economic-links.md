# Economic Links and Predictable Returns

> Source: Cohen, Lauren, and Andrea Frazzini. "Economic Links and Predictable Returns." *The Journal of Finance* 63, no. 4 (August 2008): 1977–2011.
> DOI: 10.1111/j.1540-6261.2008.01379.x | Harvard Business School, University of Chicago, NBER

## Overview

Cohen and Frazzini document that stock prices of supplier firms react with a predictable lag to news about their principal customers, generating a tradable "customer momentum" anomaly. Using SFAS No. 131 disclosures (which require firms to report customers accounting for >10% of sales), they construct a data set of 11,484 unique customer-supplier pairs from 1980 to 2004 and show that lagged customer returns strongly predict supplier returns.

The core finding is that a long-short strategy buying suppliers whose customers had the best recent returns and shorting those whose customers had the worst returns earns abnormal returns of approximately 150 basis points per month (18.6% annualized), with a five-factor alpha t-statistic of 2.99. This "customer momentum" effect is robust to controls for the firm's own momentum, industry momentum, cross-industry momentum, size, book-to-market, liquidity, and lead-lag effects. The result is driven by investor limited attention: stock prices underreact to publicly available information about economically related firms.

The paper provides three layers of evidence for the limited attention mechanism: (1) the underreaction coefficient shows suppliers absorb only ~60% of customer news in the initial month, closing the remaining ~40% over the next 6 months; (2) the effect is significantly stronger when fewer mutual fund managers jointly hold both the customer and the supplier (high inattention); and (3) common fund managers trade promptly on customer news while noncommon managers trade with a one-quarter lag.

## Data and Sample Construction

| Feature | Detail |
|---|---|
| Source | Compustat segment files (SFAS 131 disclosures) |
| Reporting threshold | Customers representing >10% of total reported sales |
| Sample period | 1980–2004 (24 years) |
| Firm-year observations | 30,622 distinct firm-year relationships |
| Unique customer-supplier pairs | 11,484 |
| Average customer sales share | 20.25% of supplier's total sales |
| Cross-industry links | 78% of pairs are in different industries |
| Average link duration | 2.0 years (median) |
| Customer size | Average at 90th percentile of CRSP universe |
| Coverage: equal-weighted | ~20% of CRSP stocks |
| Coverage: value-weighted | ~51% of CRSP market cap |

## Customer Momentum Strategy

**Construction**: Each month, sort supplier stocks into quintiles based on the previous month's return of their customer portfolio (equally weighted across principal customers). Go long Q5 (highest customer returns), short Q1 (lowest customer returns). Rebalance monthly, value- or equal-weighted within quintiles. Exclude stocks below $5.

| Model | Monthly Alpha (%) | t-statistic | Annualized (%) |
|---|---|---|---|
| Excess returns (Q5 − Q1, VW) | 1.58 | 3.79 | ~18.6 |
| Three-factor alpha (FF93) | 1.55 | 3.61 | ~18.4 |
| Four-factor alpha (+ Carhart MOM) | 1.37 | 3.12 | ~16.3 |
| Five-factor alpha (+ Liquidity) | 1.24 | 2.99 | ~14.7 |
| Equal-weighted (Q5 − Q1) | 1.31 | 4.93 | ~15.5 |
| EW, five-factor alpha | 1.36 | 4.79 | ~16.1 |

The alphas are monotonically increasing across quintiles from Q1 to Q5. The short side (Q1) is larger and more significant than the long side — consistent with slow diffusion of negative news and short-sale constraints.

## Underreaction Coefficients

The paper quantifies the speed of information incorporation:

| Measure | Value |
|---|---|
| Supplier initial price response (month 0) | ~60% of total |
| Supplier remaining drift (months 1–6) | ~40% of total |
| URC for suppliers | 0.60 (t = 5.71) |
| URC for customers | 0.94 (not significantly different from 1.0) |
| Supplier CAR over 12 months post-formation | 4.73% |

Customers themselves show no underreaction (URC ≈ 1.0) — information about customers is rapidly impounded into customer stock prices. But the same information takes 6+ months to fully reach supplier prices, generating the predictable drift.

## Robustness Tests

| Test | Result |
|---|---|
| Controlling for own-firm momentum (1-month, 12-month) | Alpha unchanged |
| Controlling for industry momentum | Alpha unchanged |
| Controlling for cross-industry momentum | Alpha unchanged |
| Hedging size, B/M, and momentum (DGTW) | Alpha survives |
| Restricting to supplier ME > customer ME | Still significant |
| Restricting to liquid stocks only | Still significant |
| Skipping a week between formation and holding | Alpha unchanged |
| Excluding low-priced stocks (<$5) | Baseline specification |
| Splitting by subperiod (1981–1992, 1993–2004) | Significant in both halves |
| Industry-adjusted returns | Alpha survives |
| Same-industry vs. different-industry links | Significant in both; stronger for different-industry links |
| Fama-MacBeth regressions with full controls | ~88 bps/month (VW), significant |

## Variation in Inattention: The COMOWN Test

The paper uses **common mutual fund ownership** (COMOWN = #funds holding both customer and supplier / #funds holding supplier) as a proxy for investor attention to the customer-supplier link.

| COMOWN Group | Monthly Customer Momentum Return (EW) | t-stat |
|---|---|---|
| Low COMOWN (high inattention) | 1.65% | 5.46 |
| High COMOWN (low inattention) | 0.75 | 1.97 |
| Spread (High − Low inattention) | −0.90 | −2.08 |

The customer momentum effect is **2.2× larger** for suppliers with low common ownership (where attention to the customer link is weakest). This is consistent with limited attention driving the predictability.

## Mutual Fund Trading Behavior

| Fund Type | Response to Customer Shock | Timing |
|---|---|---|
| Common managers (hold both customer and supplier) | Strong, contemporaneous | Quarter 0 |
| Noncommon managers (hold supplier only) | Weak initially, then delayed | Quarter 1 lag |

Common managers react immediately to customer news and trade the supplier in the same quarter. Noncommon managers show no contemporaneous response but spike in net purchases one quarter later — exactly consistent with delayed information processing.

## Real Effects of Customer-Supplier Links

When firms are linked via a customer-supplier relationship:
- Correlation of operating income increases by 38.7% (t = 3.88)
- Correlation of sales increases by 51.4% (t = 8.55)
- Customer shocks today predict supplier's future real shocks (sales, operating income) — but only when firms are linked, not when they are unlinked

This confirms that the customer-supplier relationship is economically meaningful and that the predictability reflects real cash flow linkages, not just statistical noise.

## Implications for Practice

1. **Cross-asset predictability from economic links**: Customer returns predict supplier returns with a lag, generating ~150 bps/month of alpha. This is a form of cross-predictability that standard factor models miss entirely.
2. **Limited attention is the mechanism**: The predictability is driven by investors failing to promptly incorporate publicly available information about economically linked firms. It is not explained by risk factors, momentum, or industry effects.
3. **Attention proxies modulate the effect**: Where institutional overlap is low (few common fund managers), the effect is strongest. This confirms the behavioral mechanism and suggests the anomaly is harder to arbitrage for inattentive investors.
4. **Short side is dominant**: The long-short return is driven primarily by the short leg (suppliers with bad customer news that has not yet been priced in). Short-sale constraints likely contribute to the persistence of the anomaly.
5. **Practical implementation requires supply-chain data**: The strategy depends on identifying customer-supplier relationships from SFAS 131 disclosures (now ASC 280). This data has become more accessible through commercial providers since 2008.

## Connections

- [[kelly-principal-portfolios]] — Kelly et al.'s prediction matrix Π directly captures the cross-predictability that Cohen & Frazzini document. The off-diagonal elements Π_{i,j} = E(R_{i,t+1} S_{j,t}) encode exactly the phenomenon where customer j's signal predicts supplier i's return. Cohen & Frazzini provide a concrete economic mechanism (supply-chain links) for the cross-predictability that PPA exploits abstractly.
- [[ehsani-linnainmaa-factor-momentum]] — Ehsani & Linnainmaa show that factor autocorrelation drives momentum. Cohen & Frazzini's customer momentum is a distinct source of cross-sectional predictability that operates through economic links rather than factor structure — it survives controls for own and industry momentum.
- [[fama-french-factor-models]] — The FF three- and five-factor models are used as benchmarks. Customer momentum earns large alpha relative to all factor models tested, including the four-factor model with Carhart momentum.
- [[msci-foundations-of-factor-investing]] — MSCI's factor taxonomy does not include a "supply-chain" or "economic links" factor. Cohen & Frazzini's result suggests that supply-chain-based signals are a distinct source of alpha beyond the standard six risk premia.

#customer-momentum #economic-links #limited-attention #supply-chain #cross-predictability #underreaction #mutual-fund-trading #SFAS-131 #behavioral-finance
