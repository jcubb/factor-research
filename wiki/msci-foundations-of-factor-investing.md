# Foundations of Factor Investing

> Source: Bender, Jennifer, Remy Briand, Dimitris Melas, and Raman Aylur Subramanian. "Foundations of Factor Investing." MSCI Research Insight, December 2013.
> Type: Practitioner white paper (MSCI)
> Part 1 of a three-paper MSCI series on factor investing

## Overview

This paper provides an institutional investor's roadmap to factor investing. It defines what factors are, catalogs the six equity risk premia factors MSCI considers well-grounded (Value, Low Size, Momentum, Low Volatility, Dividend Yield, Quality), examines why factor premia may persist, and introduces factor indexes as a cost-effective, transparent implementation vehicle. The key distinction it draws is between **generic factors** (any characteristic explaining returns/risk) and **risk premia factors** (those earning a persistent premium over long periods reflecting systematic risk exposure).

## The Six Systematic Factors

| Factor | What It Captures | Common Measures | Risk-Based Theory | Behavioral/Constraint Theory |
|---|---|---|---|---|
| **Value** | Excess returns to low-price-to-fundamental stocks | B/P, E/P, sales/price, cash flow/price, dividends | Higher business cycle risk; less flexible firms | Loss aversion; errors-in-expectations; investment flows |
| **Low Size** | Excess returns of smaller firms | Market capitalization | Proxy for other systematic risks; higher tail risk | Errors-in-expectations |
| **Momentum** | Excess returns to stocks with strong recent performance | 3-month, 6-month, 12-month relative returns (skip last month) | Higher systematic tail risk | Underreaction and overreaction; herding |
| **Low Volatility** | Excess returns to lower-risk stocks | Std. dev. (1–3 yr), downside std. dev., idiosyncratic vol, beta | N/A (anomaly) | Lottery effect; overconfidence; leverage aversion |
| **Dividend Yield** | Excess returns to high-dividend stocks | Dividend yield | Higher business cycle risk | Errors-in-expectations |
| **Quality** | Excess returns to financially healthy firms | ROE, earnings stability, dividend growth, leverage, accruals | N/A (anomaly) | Errors-in-expectations |

### Key Distinction: Risk Premia vs. Generic Factors

Not all factors that explain risk earn a premium. The paper distinguishes:
- **Risk premia factors**: Earn a persistent, long-term premium reflecting systematic risk exposure (all six above)
- **Generic factors**: Important for explaining risk or returns in the short term but do not earn a persistent premium (e.g., Growth, Liquidity — see Exhibit 3)
- **Alpha signals**: Stock characteristics used by active managers (e.g., earnings revisions, earnings momentum) — generate excess returns but don't explain risk well; could become risk premia factors if they have strong theoretical foundations

## Why Factor Premia May Persist

Two main schools of thought:

### 1. Systematic Risk (Efficient Markets View)
- Factors reflect compensation for bearing undiversifiable risk (Ross, 1976 APT)
- Small cap premium: compensation for illiquidity (Liu 2006), opacity (Zhang 2006), distress risk (Chan & Chen 1991, Dichev 1998)
- Value & size linked to macroeconomic shocks — more sensitive to real GDP (Winkelmann et al. 2013)
- Value stocks are riskier: higher leverage, more uncertain earnings (Chen & Zhang 1998)
- **Implication**: If risk is the driver, factor premia should persist as long as the underlying risk exists

### 2. Systematic Errors (Behavioral/Constraints View)
- **Behavioral biases**: Overreaction, loss aversion, home bias, chasing winners, overconfidence
- **Investor constraints**: Different time horizons, leverage restrictions, benchmark-relative mandates
- Low volatility anomaly: institutional benchmarking creates preference for relative returns → demand for high-beta stocks → low-vol stocks underpriced (Baker et al. 2011)
- Momentum from herding: reputation concerns cause managers to herd (Dasgupta, Prat, Verardo 2011)
- **Vayanos and Woolley (2011)**: Investment flows create both value and momentum effects simultaneously — negative shocks trigger outflows → fire sales → value effect; gradual outflows → momentum
- **Implication**: Factor premia persist as long as biases exist and are too costly to arbitrage

### Persistence Risk: Crowding

As factor strategies become popular, increased capital flows may compress future returns. However:
- Factor portfolios are **not macro-consistent** (unlike market cap weighting) — not all investors can hold the same factor portfolio
- Increased flows initially produce a **tailwind** before any potential reversal
- Cyclicality itself may protect premia: investors with shorter horizons can't hold through multi-year drawdowns

## Factors vs. Market Cap Investing

The paper takes a clear position: **factor indexes are not replacements for market cap benchmarks**.

| Feature | Market Cap Index | Factor Index |
|---|---|---|
| Investment view | Truly passive — no active view required | Active view — tilts away from market weights |
| Macro consistency | Yes — can be held by all investors simultaneously | No — zero-sum deviations from market |
| Turnover | Structurally very low | Higher (esp. Momentum: 127.5% annual) |
| Capacity | Extremely large | More limited |
| Purpose | Capture long-term equity risk premium | Capture specific factor risk premia |

Factor investing sits **between passive and active management**: rule-based and transparent like passive, but pursuing active returns like traditional active (Exhibit 8 Venn diagram).

## Factor Cyclicality — No Free Lunch

All factors experience extended periods of underperformance (Exhibit 7):
- Each factor has had at minimum a **2-to-3-year consecutive underperformance** period
- Small Cap/Size: six-year drawdown in the 1990s
- Factor underperformance periods have historically **not coincided** — diversification across factors shortens drawdown length

### Institutional Responses to Cyclicality
1. **Set a long time horizon** (15+ years) — impractical for most institutions
2. **Time factor entry** — extremely difficult; timing factors is as hard as timing markets
3. **Multi-factor diversification** — the most practical approach; combining Quality with Momentum and Value yields a "smoother ride"

## MSCI Factor Index Family (Exhibit 10–11)

Performance characteristics, June 1988 to June 2013:

| Index | Factor | Total Return | Total Risk | Active Return | Active Risk | Turnover | Correlation to World |
|---|---|---|---|---|---|---|---|
| MSCI World | — | 7.1% | 15.4% | 0.0 | 0.0 | 3.9% | — |
| Equal Weighted | Size | 8.3% | 16.3% | 1.2 | 5.2 | 31.8% | 0.22 |
| Min Volatility | Volatility | 8.5% | 11.6% | 1.4 | 6.7 | 20.0% | 0.30 |
| Value Weighted | Value | 8.6% | 15.6% | 1.5 | 3.6 | 20.3% | 0.30 |
| Risk Weighted | Size, Vol | 9.5% | 13.7% | 2.4 | 5.3 | 27.2% | 0.46 |
| Quality | Growth, Leverage | 10.9% | 14.0% | 3.8 | 5.9 | 27.6% | 0.13 |
| Momentum | Momentum | 10.4% | 15.9% | 3.3 | 8.5 | 127.5% | 0.03 |
| High Div Yield | Yield | 10.3% | 14.6% | 3.2 | 6.5 | 22.0% | 0.41 |

Key observations:
- All factor indexes outperformed MSCI World over this period
- **Quality and Momentum** showed the strongest historical returns
- **Min Volatility** achieved significant risk reduction (11.6% vs. 15.4%)
- **Momentum has by far the highest turnover** (127.5%) — implementation cost matters
- **Pairwise correlations are low** (0.03 to 0.46), confirming diversification benefits

### Investability Tradeoff

There is a fundamental tradeoff between **factor exposure purity** and **investability**:
- Broad indexes (e.g., Value Weighted — holds all names, reweights) → lower tracking error, higher capacity, lower factor exposure
- Concentrated indexes (e.g., Momentum — holds subset) → higher tracking error, lower capacity, higher factor exposure
- Estimated trading costs (at 50 bps one-way) range from 20.3 bps (Value Weighted) to 127.5 bps (Momentum) annually — both more than offset by historical return premiums (150–330 bps)

## Institutional Framework Shift (Exhibit 9)

The paper envisions factor investing transforming how institutions allocate:

| Dimension | Current Framework | Factor-Based Framework |
|---|---|---|
| Strategy | Diversify across alpha managers | Diversify across factor index mandates |
| Alpha definition | Broad: skill, timing, top-down | Narrow: returns excluding factors |
| Risk control | Asset allocation + manager selection | Managing factor exposures directly |
| Economics | Active mandates dominate costs | Factor mandates at lower cost; active narrowly defined |

## Connections

- The six factors here are the building blocks studied in depth by [[fama-french-factor-models]] (FF 1992, 1993, 2015 combined article)
- Momentum cyclicality and crashes connect to [[ehsani-linnainmaa-factor-momentum]] — factor timing via autocorrelation is one response to cyclicality
- The investability/turnover tradeoff for Momentum indexes is directly relevant to [[moskowitz-nonlinear-momentum]] — the smooth NL weighting function reduces turnover
- Low Volatility factor connects to [[frazzini-pedersen-betting-against-beta]] — BAB provides the theoretical foundation (leverage constraints) for why low-vol strategies earn positive risk-adjusted returns
- Barra factor model references connect to Menchero and Cuffe papers (pending)
- Multi-factor diversification strategy relates to factor timing literature (Li 2026, pending)

#factor-investing #practitioner #MSCI #value #size #momentum #low-volatility #quality #yield #indexation #cyclicality #risk-premia
