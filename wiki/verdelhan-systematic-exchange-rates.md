# The Share of Systematic Variation in Bilateral Exchange Rates

> Source: Verdelhan, Adrien. "The Share of Systematic Variation in Bilateral Exchange Rates." *The Journal of Finance* 73, no. 1 (February 2018): 375–418.
> DOI: 10.1111/jofi.12587
> Affiliation: MIT Sloan and NBER

## Overview

This paper identifies two currency risk factors — **carry** and **dollar** — that together account for 18% to 80% of the monthly variation in bilateral exchange rates. Unlike principal components, which offer a purely statistical description, these two factors are *priced* in currency markets and have natural interpretations within no-arbitrage models. The paper's key insight is that stochastic discount factors (SDFs) must exhibit at least **two kinds of global shocks** to generate the two independent cross sections of currency risk premia observed in the data.

## The Two Factors

| Factor | Construction | Interpretation |
|---|---|---|
| **Carry** | Average exchange rate change between baskets of high and low interest rate currencies | Captures global shocks priced globally; related to volatility and uncertainty |
| **Dollar** | Average change in all exchange rates vs. the U.S. dollar | Captures U.S.-specific shocks + a second global shock; related to the global component of dollar risk |

The factors are constructed from **portfolios** of currencies, not individual bilateral rates. Crucially, the carry and dollar factors are **orthogonal** to each other — their volatilities depend on different state variables (global volatility shocks vs. U.S.-specific volatility shocks).

## Theoretical Framework

The model starts from the law of motion of log SDFs in each country, following Cox, Ingersoll, and Ross (1985):

- Each log nominal SDF is driven by **country-specific shocks** (uncorrelated across countries) and **global shocks** (common to all).
- Volatilities follow autoregressive Gamma processes (ensuring positivity).
- Under parameter restrictions that make the carry and dollar factors orthogonal, the model delivers closed-form expressions for interest rates, exchange rates, and factor betas.

**Key model result**: Without two kinds of global shocks, even if all parameters are country-specific, the model cannot produce two independent cross sections of currency risk premia. The dollar factor needs a second global shock beyond the one that drives carry.

### Currency Betas

- **Dollar betas** vary across countries because of different country-specific volatilities (κᵢσᵢ,ₜ). High dollar beta countries are those where U.S.-specific volatility is high relative to local volatility.
- **Carry betas** differ across countries because of different loadings (δᵢ) on global shocks. High interest rate countries load more heavily on the carry factor.

## Empirical Results

### Developed Countries (Table I)

- Regressions of bilateral exchange rate changes on carry and dollar factors for 13 developed countries, monthly, 11/1983 to 12/2010.
- **Dollar factor loadings** are positive and significant in all 13 countries, ranging from 0.3 to 1.6.
- Average adjusted R² = **61%** with both factors; 57% without carry factors.
- Carry factors are jointly significant in 11 of 13 countries at 1% level.
- The dollar factor alone explains 19%–91% of variation; the carry factor adds meaningful explanatory power for countries like Australia and Japan (carry traders' favorites).

### Emerging Markets (Table II)

- 18 developing countries tested with the same factors.
- For **floating currencies**, results are similar to developed countries: R²s range from 10% to 75%.
- **Pegged currencies** (Hong Kong, Saudi Arabia, UAE) do not exhibit significant dollar factor loadings.
- Loadings are positive and significant for 15 of 18 countries on the dollar factor.

### Frequency Robustness

- Results hold at **daily, monthly, quarterly, and annual** frequencies.
- At the daily frequency, the dollar factor accounts for 2%–17% and carry for an additional share.
- The distribution of R²s is remarkably stable across frequencies.

## Two Cross Sections of Currency Risk Premia

The paper uncovers a **novel cross section** of currency excess returns based on **dollar betas** (not interest rates):

- Portfolios sorted by time-varying dollar betas reveal a monotonic spread in average excess returns.
- The high dollar beta portfolio earns 5.8% average log excess return (Sharpe ratio ~0.6); the low dollar beta portfolio earns just 0.6%.
- This cross section is distinct from the well-known carry trade cross section.
- Covariances of the dollar factor with portfolio returns account for this new cross section, while carry factor covariances do not.

### Dollar Beta Portfolios — Key Innovation

The **global component of the dollar factor** is extracted by going long high dollar beta currencies and short low dollar beta currencies. This long-short portfolio is:
- Highly correlated (0.85) with the dollar factor itself
- Uncorrelated with the carry factor
- Captures only global shocks (U.S.-specific shocks cancel out)

## Link to Capital Flows

The paper explores the connection between systematic currency risk and macroeconomic variables:

- Cross-country differences in systematic currency risk are **strongly related to international capital flow comovements**, much more than to trade flows.
- Differences in total capital flow characteristics account for up to **53%** of cross-country differences in systematic risk.
- Trade flow differences (exports/imports) account for only **17%**.
- Among capital flows, **portfolio and other investments** are much more informative than FDI.

## Implications for Practice

1. **Factor model design**: Any currency factor model needs at least two global shocks — a single-factor model (carry alone) is insufficient.
2. **Portfolio construction**: Dollar beta sorting reveals a distinct risk premium separate from carry, creating a second dimension for currency allocation.
3. **Risk measurement**: The dollar factor is the dominant driver of bilateral exchange rate variation (more than carry), which has implications for hedging and risk management.
4. **No-arbitrage models**: The results constrain the structure of SDFs in international finance — they must have heterogeneous loadings on at least two global shocks.

## Connections

- Builds on Lustig, Roussanov & Verdelhan (2011) carry trade research
- Dollar factor relates to the [[frazzini-pedersen-betting-against-beta]] concept of funding currency risk
- Factor structure parallels equity market findings in [[fama-french-factor-models]]
- Capital flow linkage connects to macro-finance literature on international capital movements

#currency #exchange-rates #factor-model #carry-trade #dollar-risk #systematic-risk #SDF #cross-section
