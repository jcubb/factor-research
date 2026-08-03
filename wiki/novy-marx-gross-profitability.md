# The Other Side of Value: The Gross Profitability Premium

> Source: Novy-Marx, Robert. "The Other Side of Value: The Gross Profitability Premium." *Journal of Financial Economics* 108, no. 1 (2013): 1–28. (WP: June 2012.)
> JEL: G12. Simon Graduate School of Business, University of Rochester.

## Overview

Novy-Marx documents that **gross profitability** — gross profits (revenue minus cost of goods sold) scaled by total assets, $\text{GP/A} = (\text{REVT} - \text{COGS})/\text{AT}$ — has "roughly the same power as book-to-market" predicting the cross-section of average returns. More profitable firms earn significantly higher returns than unprofitable firms *despite* trading at higher valuations (lower book-to-market) and larger market caps. This is the "other side of value": a profitability strategy is a **growth** strategy, yet it earns value-like excess returns.

The paper's central methodological claim is that **gross profits is the cleanest accounting measure of true economic profitability**. The farther down the income statement one goes, the more "polluted" the measure becomes — a firm that spends aggressively on R&D, advertising, or SG&A to build future competitive advantage looks *less* profitable on bottom-line earnings even though it is unambiguously more productive. This resolves the earlier mixed findings (e.g., Fama & French 2006, 2008) that used current earnings as the profitability proxy: earnings has weak predictive power, but gross profits has "far more power than earnings."

Because profitability and value are **negatively correlated** (Spearman rank correlation ≈ −18%; profitable firms tend to be growth firms), each strategy is an excellent hedge for the other, and controlling for one dramatically improves the other. The paper builds this into a four-factor model — market, industry-adjusted value, momentum, and a gross-profitability factor — that prices a wide range of seemingly unrelated anomalies (earnings surprises, default risk, net stock issuance, organizational capital) as different expressions of the same few underlying signals. The paper is the empirical origin of the profitability factor later formalized as RMW in the Fama-French (2015) five-factor model.

## Why Gross Profits, Not Earnings

A dividend-discount / clean-surplus argument (following Fama & French 2006) motivates the prediction. With price equal to the present value of expected dividends and book equity evolving by retained earnings, the market value of equity is

$$M_t = \sum_{\tau=0}^{\infty} \frac{\mathbb{E}_t[Y_{t+\tau} - dB_{t+\tau}]}{(1+r)^{\tau}},$$

where $Y_t$ is earnings, $dB_t \equiv B_t - B_{t-1}$ the change in book equity, and $r$ the required return. Holding all else equal, higher expected earnings imply higher expected returns — so profitable firms should outperform unprofitable ones, just as value firms should outperform growth firms. As with value, the argument is **consistent with, but not predicated on, rational pricing** — it works equally well if the variation is behavioral.

Key construction choices:

| Choice | Rationale |
|---|---|
| **Gross profits** (REVT − COGS), not earnings | Expensed investments (R&D, advertising, SG&A) reduce earnings without reducing book equity; they signal *higher* future profits. Gross profits sits highest on the income statement, least polluted. |
| **Scale by book assets** (AT), not market equity | A book-based denominator avoids "hopelessly conflating" the productivity proxy with book-to-market. |
| **Scale by assets, not equity** | Gross profits is an asset-level measure — not reduced by interest payments, so it is independent of leverage. |

## Key Empirical Results (US, July 1963 – December 2010, ex-financials)

### Fama-MacBeth regressions (Table 1)
Gross profits-to-assets has roughly the same predictive power as book-to-market, and **subsumes** earnings-to-book and free-cash-flow-to-book. Industry-adjusting (demeaning by Fama-French 49 industries) makes it *stronger*: the t-statistic on industry-adjusted GP/A is more than 1.5× that on log(B/M) and almost 2.5× that on momentum ($r_{12,2}$). EBITDA/A and SG&A/A (a decomposition of gross profits) each predict individually but are subsumed by GP/A. The power survives controls for accruals (Sloan 1996) and R&D (Chan et al. 2001).

### Value-weighted sorts (Table 2)
| Strategy (profitable − unprofitable) | Value (spread) |
|---|---|
| Excess return **0.31%/mo** (t = 2.49) | Value strategy **0.41%/mo** |
| FF3 alpha **0.52%/mo** (t = 4.49) — large *negative* HML loading | — |

The profitability strategy is a growth strategy (significant negative HML loading, ~half the B/M variation of a direct value sort) yet earns a significant premium — "good growth" firms.

### Profitability as insurance for value
Profitability and value returns are correlated **−0.57** over the sample. A 50/50 mix captures both strategies' returns (0.71%/mo) at *lower* volatility than either leg alone (joint σ 2.89% vs. 2.94% and 3.27%), despite doubling gross exposure. The mixed strategy has a realized annual **Sharpe ratio of 0.85** — 2.5× the market's 0.34 — and never had a losing five-year period over 1963–2010. The strategy is orthogonal to momentum.

### It works among the largest stocks (Tables 3–4)
Among the largest-cap quintile, the profitability spread is **26 bps/mo** (t = 1.88), larger than the value spread of 14 bps (t = 0.95). Large-cap profitability and value correlate −0.58; a 50/50 mix has a Sharpe of 0.44 — *trading only in the Fortune 500 universe*. Profitability's incremental power above book-to-market is "largely undiminished with size."

### International & double-sort evidence (Tables 5–6)
The profitability spread in developed markets ex-US (July 1990 – October 2009) is significant and even larger than the international value spread. In double sorts on GP/A and B/M, controlling for profitability lifts the average value spread to 0.68%/mo (vs. 0.41% unconditional) and controlling for value lifts the average profitability spread to 0.54%/mo (vs. 0.31%). Trading the "corners" (profitable value firms long, unprofitable growth firms short) produces the largest spreads. A simple Fortune-500 joint strategy earns 0.62%/mo, Sharpe 0.74, turning over only ⅓ per side per year.

## Conditional Factors: HML|GP and PMU|BM (Table 8)

Constructing HML-like factors that control for the other dimension confirms the double-sort intuition explicitly:

| Factor | Excess return | t-stat |
|---|---|---|
| Standard HML | 0.40%/mo | 3.25 |
| **HML\|GP** (value controlling for profitability) | **0.54%/mo** | 5.01 |
| **PMU\|BM** (profitability controlling for value) | **0.48%/mo** | 5.35 |

Standard HML lies **inside the span** of these two factors: it loads 1.04 on HML|GP and −0.18 on PMU|BM, and these loadings explain *all* of HML's average return (insignificant alpha). PMU|BM has a larger information ratio relative to the three Fama-French factors than UMD does, and is essentially orthogonal to momentum.

## The Alternative Four-Factor Model (Section 4)

Novy-Marx builds a four-factor model from the market plus three **industry-adjusted** factors — value (HML\*), momentum (UMD\*), and profitability (PMU\*) — each constructed with the HML methodology on industry-demeaned sorts and hedged for industry exposure. Applied to **fifteen anomaly strategies** (size, B/M, momentum, profitability; ROA, E/P, asset turnover, gross margins, PEAD; and the Chen-Novy-Marx-Zhang set: failure probability, O-score, net stock issuance, asset growth, total accruals, organizational capital):

- The alternative model prices **all fifteen except total accruals** (and only half of PEAD), largely via loadings on the profitability factor PMU\*.
- **Root-mean-squared pricing error is 0.22%/mo**, versus 0.54%/mo for the standard Fama-French four-factor (FF3 + UMD) model — less than half.
- Roughly two-thirds of the improvement comes from adding the industry-adjusted profitability factor; one-third from industry-adjusting value and momentum.

The economic reading: many "seemingly unrelated" anomalies are different expressions of a few underlying signals. Distressed / high-default-risk firms (Campbell-Hilscher-Szilagyi failure probability, Ohlson O-score) are simply firms with low industry-adjusted gross profitability; net issuers are low-profitability growth firms; high-organizational-capital firms are more profitable. Pricing the monthly-rebalanced ROA strategy with an annually-rebalanced, "stale" profitability factor is especially striking.

## Implications for Practice

1. **Use gross profits-to-assets as the profitability signal**, not earnings or ROE. It sits highest on the income statement and is least contaminated by discretionary investment; earnings-based measures are weak and subsumed by GP/A.
2. **Pair profitability with value.** Their −0.57 correlation makes profitability a natural hedge for value: the 50/50 mix roughly doubles the market Sharpe and had no losing five-year window over 1963–2010. Value investors can add the profitability premium with *no* added volatility.
3. **The premium is tradable at scale.** Profitability's edge survives — indeed its incremental power over B/M is undiminished — among the largest, most liquid stocks, and turns over slowly (~⅓/year), so it is implementable in a Fortune-500 universe at low transaction cost.
4. **Improve value sorts by screening out unprofitable "cheap" firms** (and profitability sorts by screening out expensive "fully priced" profitable firms). Conditional value/profitability factors dominate their unconditional counterparts.
5. **Treat distress, issuance, and earnings-quality anomalies as profitability in disguise.** A market + industry-adjusted value/momentum/profitability model prices most of them; adding a profitability factor to a risk model captures commonality that FF3 + UMD misses.

## Connections

- [[fama-french-factor-models]] — This paper is the direct empirical antecedent of the profitability factor **RMW** in Fama & French's (2015) five-factor model, and shows *why* HML becomes partially redundant once profitability is controlled (standard HML lies inside the span of HML|GP and PMU|BM). Novy-Marx uses gross profits where FF (2015) use operating profitability.
- [[msci-foundations-of-factor-investing]] — Gross profitability is the academic origin of the practitioner **Quality** factor (of which profitability is the core component) in MSCI's six-factor taxonomy; the "good growth" characterization maps onto quality-growth indexation.
- [[ehsani-linnainmaa-factor-momentum]] — Novy-Marx's four-factor model treats momentum as one of a few base signals; Ehsani & Linnainmaa argue momentum is timing of these underlying factors — profitability among them. The negative HML loading of profitability is exactly the factor cross-exposure that momentum can time.
- [[frazzini-pedersen-betting-against-beta]] — Both papers argue that a characteristic long associated with "growth"/"low-risk" firms nonetheless carries a premium; profitable firms (like low-beta firms) are the "boring" stocks that outperform on a risk-adjusted basis.
- [[harmsworth-idiosyncratic-alpha]] — Gross profitability / PMU is one of the "commoditized" factor betas AB strips out to isolate idiosyncratic alpha; a manager whose returns are really a profitability tilt would show low IA. The profitability factor is now a cheap ETF beta, exactly the kind of exposure that should not command an active fee.
- [[menchero-characteristics-factor-portfolios]] — Novy-Marx's industry-adjusted, industry-hedged factor construction (HML\*, UMD\*, PMU\*) is a "simple" sort-based factor built to reduce incidental industry exposure — a practitioner-flavored midpoint between raw FF simple factors and Barra pure factors.
- [[fama-french-luck-vs-skill]] — The anomaly-pricing result implies much apparent manager "skill" is loading on a profitability factor; a fund long profitable firms would generate spurious CAPM/FF3 alpha that PMU\* explains.

#gross-profitability #profitability-factor #value #RMW #quality #Novy-Marx #cross-section #anomalies #four-factor-model #HML #book-to-market #industry-adjusted #factor-construction #good-growth #distress-risk #Fama-French
