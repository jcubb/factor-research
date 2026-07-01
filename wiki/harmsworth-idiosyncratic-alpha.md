# A Cut Above: Why Idiosyncratic Alpha Is Better than Beating the Benchmark

> Source: Harmsworth, Alla, and Harjaspreet Mand. "A Cut Above: Why Idiosyncratic Alpha Is Better than Beating the Benchmark." AllianceBernstein (Alphalytics / AB Institutional Solutions), November 10, 2022.
> Status: Practitioner research note — For Investment Professional use only

## Overview

AllianceBernstein argues that **idiosyncratic alpha (IA)** — a manager's active return *net of common, commoditized factor exposures* — is a far better tool for selecting active managers and building portfolios of funds than traditional benchmark-relative excess return. The core claim is empirical: across a database of 30,000+ equity and fixed-income strategies, managers with high trailing IA go on to beat their benchmarks (and their lower-IA peers) with high hit rates over the following three to five years, even net of fees. IA is both **more persistent** and **more predictive of future active return** than past excess return, which is famously mean-reverting.

The motivation is the commoditization of factor beta: with smart-beta/factor ETFs now available at near-zero (occasionally negative) fees, common factor exposures embedded in a manager's active return can be replicated cheaply and should not command an active fee. What genuinely warrants an active fee is the return that "survives" after stripping out those factor betas — the idiosyncratic component, reflecting security selection and factor/market timing skill. The paper positions IA as "the new alpha" as the definition of what counts as skill shrinks.

Beyond individual-manager selection, AB shows the results carry over to **portfolios of funds**: combining managers on aggregate IA — and further ensuring IA *diversification* (low correlation between funds' idiosyncratic streams) and *factor neutrality* — produces materially higher and more stable forward active returns than combining on trailing excess return. The note closes with manager-attribute findings (smaller funds, longer tenure, higher concentration, lower turnover, higher tracking error, ESG, and small-cap/credit/muni sleeves tend to generate more IA) and a stylized real-life example using 80 AB equity strategies.

## What Is Idiosyncratic Alpha?

IA is the intercept (plus, optionally, timing terms) of a regression of a fund's active return on the active returns of cheap, investable factor benchmarks. The key principle is **investability**: the goal is not a full theoretical attribution but a measure of how much of a manager's return can be replicated by static exposures to available products — i.e., whether the manager is worth paying for.

| Concept | Definition |
|---|---|
| Excess (active) return | Fund return − benchmark return |
| Common factor beta | Portion of active return replicable via cheap factor ETFs (value, quality, momentum, min-vol, etc.) |
| Idiosyncratic alpha (IA) | Active return that survives after stripping out common factor betas — the nonreplicable, fee-worthy component |
| Sources of IA | Security selection; factor/market/country/sector timing; portfolio construction; implementation |

IA can be decomposed into **stock-picking alpha** and **factor-timing alpha** (see Methodology). A complementary measure is 1 − R² from the factor regression: how much of a manager's return is *not* explained by factors.

## Key Empirical Findings

### IA is more persistent than excess return

Panel regressions of forward IA on trailing IA vs. forward excess return on trailing excess return. The IA persistence coefficient is much larger and more statistically significant:

| Sample | Measure | Coefficient | t-stat |
|---|---|---|---|
| US equity (~500 S&P 500 funds, 1998–2019) | Excess return persistence | 0.04 | 2.20 |
| US equity | **IA persistence** | **0.15** | **7.10** |
| Global equity (~2,000 funds), 3yr | Excess return persistence | 0.02 | 0.55 |
| Global equity, 3yr | **IA persistence** | **0.07** | **4.59** |
| Global equity, 5yr | Excess return persistence | −0.04 | −0.79 |
| Global equity, 5yr | **IA persistence** | **0.04** | **1.47** |
| US fixed income, 3yr | Excess return persistence | 0.17 | 7.41 |
| US fixed income, 3yr | **IA persistence** | **0.21** | **9.69** |

Excess-return persistence for equities is near zero or negative (mean-reverting); IA persistence is reliably positive. For fixed income, both persist but IA persists more.

### IA is more predictive of future active return

For top-quartile equity managers, forward 3-year outperformance (gross):

| Ranking metric | % that beat benchmark (next 3yr) | Avg forward outperformance |
|---|---|---|
| Random / average manager | — | +0.2% |
| Top quartile by trailing **excess return** | 65% | +0.5% |
| Top quartile by trailing **IA** | 75% | +1.1% |

Top-quartile IA managers average **4.86% gross annualized IA** over a trailing 3-year window. Adding an **IA-persistency** filter improves results further (see below).

### Layering filters (equity, forward excess return, gross)

| Selection criteria | 3yr forward | 5yr forward |
|---|---|---|
| Random manager | +0.2% | +0.0% |
| Trailing excess return (top quartile) | +0.5% | −0.3% |
| IA level | +1.1% | +0.1% |
| IA level + IA persistence | +1.5% | +1.0% |
| IA level + IA persistence + excess return | +2.5% | +1.3% |

Note the top-quartile *excess-return* managers go on to a **negative** −0.3% five-year forward — performance-chasing actively destroys value at the five-year horizon.

## IA in Portfolio Construction

Combining funds on IA beats combining on excess return, and the effect compounds when IA is diversified and factor exposures are neutralized.

### Probability a 5-fund portfolio beats its benchmark (5yr forward)

| Portfolio construction basis | P(beat benchmark) |
|---|---|
| Positive aggregate excess return | 56.2% |
| Positive aggregate IA | 73.1% |
| Top-quartile aggregate excess return | 52.4% |
| **Top-quartile aggregate IA** | **85.6%** |

### Forward 5yr annualized excess return by method (individual funds vs. portfolios)

| Approach | 5yr fwd excess return |
|---|---|
| Random manager | −0.07% |
| Top excess-return fund (individual) | −1.27% |
| Top IA fund (individual) | +0.68% |
| Top excess-return 5-fund portfolio | −1.25% |
| Top IA 5-fund portfolio | +1.30% |
| **Top IA + factor-neutral + low IA-correlation portfolio** | **+1.64%** |

The combination is "better than the sum of the parts": high-IA fund portfolios beat even the best individual funds, and adding **IA diversification** (low cross-fund idiosyncratic correlation) plus **factor neutrality** delivers the best outcome. In the stylized 80-strategy AB example, a max-IA/max-Sharpe optimization (factor betas constrained to [−0.5, 0.5], 40% single-fund cap) beat a max-excess-return optimization by **7.7% p.a.** and produced a far less concentrated, more regionally diverse allocation.

## How Much IA Is Out There, and Who Generates It?

| Cohort | Positive-IA rate (gross) | Notes |
|---|---|---|
| Equity managers (avg) | 59% | Avg IA 0.55%; higher dispersion, higher gross IA |
| US equity only | 50.4% | — |
| Fixed income (avg) | 64% | Lower but more consistent IA; higher IR (IA per unit risk) |
| US fixed income | 74.1% | Credit, aggregate, munis are richest FI areas |

**Manager attributes associated with higher IA:** small-cap (equities); credit/aggregate/munis (FI); ESG; longer manager tenure (10–20 yrs highest, ~1% IA); higher concentration; **lower turnover** (churn is costly); higher tracking error (more risk-adjusted IA per unit TE). **Smaller funds generate more IA** — strategy-level AUM is robustly negatively related to future returns (a $5M AUM increase ≈ −19 bp; $50M ≈ −70 bp annualized), surviving controls for style, tenure, turnover, and past returns. Likely drivers: index-hugging as AUM grows, decision-making frictions in large teams, and trading/liquidity constraints — an argument for a multi-boutique structure.

**ESG:** self-identified ESG strategies beat non-ESG peers by ~4.9% over 10 years; the "ESG alpha" survives adjustment for value/quality/momentum/min-vol factors, sector exposures, and even a passive ESG-Leaders proxy.

## Methodology (Appendix)

**Equity IA** — regress fund active return on active (vs. market) factor returns:

r_{i,t} = α_i + β₁V_t + β₂Q_t + β₃M_t + β₄R_t + ε_{i,t}

where V, Q, M, R are Value, Quality, Momentum, and Minimum-Volatility returns in excess of the broad market. The intercept α_i is IA.

**Separating stock-picking from timing** — add squared factors (extending Treynor & Mazuy 1966 market-timing):

r_{i,t} = α_i + Σβ_k F_{k,t} + Σγ_k F_{k,t}² + ε_{i,t}

Now α_i measures **security-selection alpha**; the return contribution of the squared terms measures **factor-timing alpha**. Their sum ≈ total IA (≈ the intercept of the simple regression).

**Fixed income** — same structure with duration, credit, securitized, and volatility premia (from Bloomberg/J.P. Morgan indices; AQR style indices for value/momentum/carry/defensive), returns in excess of cash or Treasuries, USD-hedged. Investable factor products are scarcer in FI, so commonly used indices proxy the premia.

## Implications for Practice

1. **Rank managers by IA, not trailing excess return.** Past excess return is mean-reverting (top-quartile equity managers went on to *lag* over five years); IA is persistent and predictive. Using IA raises the 3-year hit rate from 65% to 75% and average outperformance from 0.5% to 1.1%.
2. **Add an IA-persistency filter.** Managers with high *and* persistent IA outperform those with high but unstable IA; layering the filter lifts forward outperformance to 1.5% (3yr).
3. **Build fund portfolios on aggregate IA, and diversify it.** Top-quartile-IA 5-fund portfolios beat their benchmark 86% of the time vs. 52% for top excess-return portfolios; neutralizing factor betas and minimizing cross-fund IA correlation adds the most value (+1.64% 5yr fwd).
4. **Don't pay active fees for replicable factor beta.** With factor ETFs near zero fees, only nonreplicable IA justifies an active fee — treat cheap factor exposures as part of the benchmark.
5. **Favor smaller, lower-turnover, longer-tenured, higher-conviction managers.** These attributes are empirically associated with higher IA; strategy-level scale erodes alpha.
6. **Match the alpha source to the mandate.** Equities offer higher IA at higher risk; fixed income offers more modest but more efficient (higher-IR) IA — blend by risk budget and return target.

## Connections

- [[fama-french-luck-vs-skill]] — Fama & French (2010) use bootstrap simulations to separate fund skill from luck and conclude few managers cover their fees; Harmsworth & Mand reach a more optimistic practitioner conclusion by changing the *measure* — stripping factor betas to isolate a persistent skill signal (IA) rather than evaluating raw CAPM/FF alpha. Both agree that factor exposure masquerading as skill is the central problem; they differ on whether persistent skill can be identified ex ante.
- [[msci-foundations-of-factor-investing]] — The six commoditized MSCI factors (Value, Size, Momentum, Low Vol, Yield, Quality) are exactly the "cheap beta" that IA strips out. AB's argument depends on these premia being cheaply replicable via factor ETFs, which the MSCI foundations paper documents.
- [[frazzini-pedersen-betting-against-beta]] — Minimum Volatility is one of the four equity factors AB regresses out; BAB is the academic mechanism behind the low-vol premium. A manager whose "alpha" is really a low-beta tilt would show low IA under AB's method.
- [[ehsani-linnainmaa-factor-momentum]] — Ehsani & Linnainmaa show factor *timing* is the source of momentum profits; AB explicitly isolates factor-timing alpha (via Treynor-Mazuy squared factors) as a distinct, fee-worthy skill within IA — a practitioner operationalization of the same timing-vs-selection distinction.
- [[menchero-characteristics-factor-portfolios]] — Menchero's simple-vs-pure factor portfolios formalize how sort-based factor definitions carry incidental exposures; AB's investable-factor regression is the practitioner analog, deliberately using "simple," replicable factor products rather than pure factors because investability (not theoretical purity) is the goal.
- [[li-episodic-factor-pricing]] — AB repeatedly notes IA (and factor premia) are cyclical; Li et al.'s episodic on/off pricing regimes provide a formal model for why factor betas are "highly cyclical" and why stripping them out yields a more persistent skill signal.
- [[kelly-principal-portfolios]] — Kelly et al. decompose returns into factor-spanned (PEPs) and factor-neutral alpha (PAPs); IA is conceptually the fund-level analog of the PAP — the return orthogonal to priced factors.

#idiosyncratic-alpha #manager-selection #active-management #alpha #factor-betas #persistence #portfolio-construction #fund-of-funds #smart-beta #ESG #treynor-mazuy #stock-picking #factor-timing #tracking-error #fund-size #AllianceBernstein #practitioner #fixed-income #equities
