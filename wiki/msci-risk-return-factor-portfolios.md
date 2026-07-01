# Risk and Return of Factor Portfolios: The Impact of Regression Weighting

> Source: Menchero, Jose and Zoltan Nagy. "Risk and Return of Factor Portfolios: The Impact of Regression Weighting." MSCI Research Insight, March 2013.
> MSCI Applied Research

## Overview

Factor portfolios are long-short portfolios with unit exposure to one selected style factor and zero exposure to all others. They serve two practical purposes: capturing return premia (e.g., tilting toward Earnings Yield) and hedging factor risk (e.g., reducing Beta exposure). Because factor portfolios are constructed via cross-sectional regression of stock returns on factor exposures, the regression weighting scheme directly determines the portfolio's stock-level composition, its size-cap distribution, its realized volatility, and ultimately its long-run return.

This paper examines the Barra USE4 model's style factor portfolios under four regression weighting schemes -- market capitalization, square root of market cap (root-cap), ordinary least squares (equal weight), and inverse specific variance. The key finding is that the weighting scheme matters more for some factors than others: Momentum shows return differentials exceeding 300 bps across schemes, while most other factors differ by less than 100 bps. In all cases, inverse specific variance weighting produces the lowest realized volatility, consistent with its theoretical motivation of minimizing estimation error. Market-cap weighting, by contrast, produces the highest volatility for virtually every factor due to portfolio concentration in large-cap names.

The authors also document that return correlations across weighting schemes are generally high (above 0.80), with the notable exception of market-cap weighting versus equal or inverse specific variance weighting, where average correlations drop to 0.60 and 0.70 respectively. This has practical implications: the choice of weighting scheme is not merely a statistical detail but a decision that can meaningfully alter the investability, cost structure, and risk-return profile of factor-based strategies.

## Construction of Factor Portfolios

Factor portfolios are constructed by performing a cross-sectional regression of stock returns against factor exposures. The resulting stock weights depend on the regression weighting scheme. The paper examines four schemes applied to the USE4 style factors:

| Weighting Scheme | Description | Practical Note |
|---|---|---|
| Market capitalization | Weight proportional to market cap | Large-cap stocks dominate; ~67% of absolute weight in top quintile |
| Root-cap (sqrt of market cap) | Square root of market cap | Intermediate between market-cap and equal; distribution similar to inverse specific variance |
| Equal (OLS) | All stocks weighted equally | Small-cap stocks play a larger role; slight tilt toward smallest quintile |
| Inverse specific variance | Weight inversely proportional to stock-specific variance | Minimizes sampling error in factor return estimates; minimizes predicted factor portfolio volatility |

A critical clarification: the resulting factor portfolio from, say, an equal-weighted regression is **not** an equal-weighted portfolio. Rather, the weighting scheme determines which stocks dominate the regression, and this influences the factor portfolio composition. Equal-weighted regression gives more influence to small-cap stocks, so they appear with larger absolute weights on both the long and short sides.

Root-cap weighting is commonly used in practice as a proxy for inverse specific variance weighting, since both produce similar size distributions across market-cap quintiles.

## Size Distribution of Factor Portfolios

The authors divide the estimation universe into five market-cap quintiles and compute the absolute (long + short) weight of each quintile for each regression method, using the Earnings Yield factor as a representative example. The pattern is qualitatively similar across all style factors.

| Market-Cap Quintile | Market Cap Wtd | Root-Cap Wtd | Equal Wtd | Inverse Spec Var Wtd |
|---|---|---|---|---|
| 1 (Smallest) | ~3% | ~8% | ~27% | ~27% |
| 2 | ~5% | ~14% | ~21% | ~17% |
| 3 | ~7% | ~17% | ~20% | ~17% |
| 4 | ~18% | ~24% | ~19% | ~24% |
| 5 (Largest) | ~67% | ~37% | ~13% | ~15% |

*Values are approximate, read from Figure 1 in the paper (Earnings Yield factor, September 14, 2012).*

The key implication: equal-weighted factor portfolios are dominated by small-cap stocks, which are more illiquid and costly to short. This makes equal-weighted factor portfolios harder and more expensive to implement in practice, despite their sometimes superior return performance.

## Return Performance Across Weighting Schemes

### Earnings Yield Factor (July 1995 -- September 2012)

For Earnings Yield, regression weighting had a relatively minor impact on cumulative performance. All four versions exhibited the same characteristic pattern: underperformance during the late-1990s dot-com run-up, followed by a sharp rebound after the bubble burst in 2000. Market-cap weighting slightly underperformed the other three schemes.

### Momentum Factor (July 1995 -- September 2012)

The Momentum factor showed much greater differentiation across weighting schemes. The ranking from best to worst cumulative performance:

1. **Equal weighting** -- highest cumulative return (~80%)
2. **Root-cap weighting** -- intermediate (~45%)
3. **Market-cap weighting** -- lower (~30%)
4. **Inverse specific variance** -- substantially underperformed (~10%)

The performance difference between equal and inverse specific variance weighting exceeded 300 bps annualized. All four versions exhibited the characteristic Momentum crashes of 2002 and 2009.

## Summary Statistics: Return, Volatility, and Information Ratio

**Table 1: Summary statistics for USE4 style factor portfolios, July 1995 to September 2012**

| Factor | Return (ann. %) |  |  |  | Volatility (ann. %) |  |  |  | Information Ratio |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | Mkt Cap | Root Cap | Equal | Inv Spec Var | Mkt Cap | Root Cap | Equal | Inv Spec Var | Mkt Cap | Root Cap | Equal | Inv Spec Var |
| Beta | -0.76 | -0.64 | -0.17 | -0.14 | 9.15 | 8.70 | 8.62 | 8.60 | -0.08 | -0.07 | -0.02 | -0.02 |
| Non-linear Beta | -0.14 | 0.02 | 0.46 | -0.03 | 2.73 | 2.09 | 2.04 | 1.83 | -0.05 | 0.01 | 0.23 | -0.01 |
| Book-to-price | -0.48 | 0.08 | 0.53 | -0.26 | 3.09 | 2.00 | 2.07 | 1.56 | -0.16 | 0.04 | 0.26 | -0.16 |
| Dividend Yield | 1.46 | 0.81 | 1.06 | 0.68 | 2.90 | 1.95 | 1.79 | 1.47 | 0.50 | 0.42 | 0.59 | 0.46 |
| Earnings Yield | 1.96 | 2.37 | 2.58 | 2.54 | 3.97 | 2.76 | 2.57 | 2.09 | 0.49 | 0.86 | 1.01 | 1.21 |
| Growth | 0.53 | 0.09 | -0.32 | 0.36 | 3.01 | 2.06 | 1.96 | 1.55 | 0.18 | 0.04 | -0.16 | 0.23 |
| Leverage | -0.84 | -0.50 | -0.47 | -0.89 | 2.75 | 1.93 | 1.96 | 1.54 | -0.31 | -0.26 | -0.24 | -0.58 |
| Liquidity | 2.03 | 1.57 | 1.82 | 1.55 | 3.41 | 2.62 | 3.10 | 2.25 | 0.60 | 0.60 | 0.59 | 0.69 |
| Momentum | 2.24 | 2.73 | 3.70 | 0.66 | 5.08 | 4.18 | 3.95 | 3.82 | 0.44 | 0.65 | 0.93 | 0.17 |
| Residual Volatility | -3.49 | -3.28 | -2.95 | -1.77 | 4.91 | 3.91 | 3.80 | 3.32 | -0.71 | -0.84 | -0.77 | -0.53 |
| Size | -3.74 | -3.67 | -4.36 | -3.03 | 3.49 | 3.26 | 3.58 | 3.21 | -1.07 | -1.13 | -1.22 | -0.94 |
| Non-linear Size | -1.23 | -1.62 | -2.68 | -1.57 | 4.24 | 3.14 | 3.04 | 2.78 | -0.29 | -0.52 | -0.88 | -0.57 |

### Key patterns from the table

**Volatility:** Inverse specific variance weighting produces the lowest realized volatility for every single factor. Market-cap weighting produces the highest volatility for virtually all factors, likely because cap-weighted portfolios are more concentrated.

**Returns:** For most factors, return differences across weighting schemes are below 100 bps. The notable exception is Momentum, where the spread between equal weighting (3.70%) and inverse specific variance (0.66%) exceeds 300 bps.

**Information ratios:** Earnings Yield achieves its highest IR (1.21) under inverse specific variance weighting -- the combination of competitive returns and lowest volatility. Momentum achieves its highest IR (0.93) under equal weighting, driven by its superior return despite not having the lowest volatility.

## Return Correlations Across Weighting Schemes

**Table 2: Time-series return correlations of factor portfolios across weighting schemes, USE4 Model, July 1995 to September 2012**

| Series 1 | Series 2 | Beta | Non-lin Beta | BtP | Div Yld | Earn Yld | Growth | Leverage | Liquidity | Momentum | Resid Vol | Size | Non-lin Size | Avg |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Mkt Cap | Root Cap | 0.97 | 0.87 | 0.83 | 0.86 | 0.85 | 0.84 | 0.85 | 0.79 | 0.91 | 0.89 | 0.95 | 0.88 | 0.87 |
| Mkt Cap | Equal | 0.90 | 0.56 | 0.43 | 0.52 | 0.53 | 0.48 | 0.49 | 0.46 | 0.74 | 0.67 | 0.85 | 0.55 | 0.60 |
| Mkt Cap | Spec Var | 0.93 | 0.67 | 0.62 | 0.62 | 0.68 | 0.62 | 0.65 | 0.51 | 0.81 | 0.76 | 0.85 | 0.70 | 0.70 |
| Root Cap | Equal | 0.98 | 0.85 | 0.79 | 0.82 | 0.85 | 0.81 | 0.82 | 0.87 | 0.93 | 0.90 | 0.94 | 0.85 | 0.87 |
| Root Cap | Spec Var | 0.98 | 0.89 | 0.87 | 0.86 | 0.89 | 0.85 | 0.89 | 0.86 | 0.94 | 0.92 | 0.94 | 0.90 | 0.90 |
| Equal | Spec Var | 0.98 | 0.88 | 0.78 | 0.85 | 0.83 | 0.81 | 0.83 | 0.87 | 0.92 | 0.89 | 0.94 | 0.85 | 0.87 |
| **Average** |  | 0.96 | 0.79 | 0.72 | 0.75 | 0.77 | 0.74 | 0.75 | 0.73 | 0.88 | 0.84 | 0.91 | 0.79 |  |

### Key patterns

- **Root-cap vs. inverse specific variance** has the highest average pairwise correlation (0.90), confirming that root-cap is a good practical proxy for inverse specific variance weighting.
- **Market-cap vs. equal weighting** has the lowest average correlation (0.60), indicating that these two schemes produce the most different factor portfolios.
- **Higher-volatility factors** (Beta, Momentum, Residual Volatility, Size) tend to have higher cross-scheme correlations than lower-volatility factors (Book-to-price, Growth, Liquidity).
- Market-cap weighting is the outlier: its correlations with other schemes are systematically lower, reflecting the heavy concentration in large-cap names.

## Implications for Practice

1. **Weighting scheme is a meaningful design choice, not a technicality.** For factors like Momentum, the return differential across weighting schemes can exceed 300 bps annualized -- larger than many active management fees.

2. **Inverse specific variance weighting minimizes factor portfolio volatility.** This is the theoretically motivated choice (minimizes estimation error) and empirically delivers the lowest realized risk for every USE4 style factor.

3. **Market-cap weighting produces the highest volatility** for nearly all factors, likely due to portfolio concentration, and is the most "different" scheme in terms of return correlation with the others.

4. **Equal-weighted factor portfolios tilt heavily toward small caps,** making them more expensive to implement due to higher transaction costs and shorting costs. The return advantage (when it exists, as with Momentum) must be weighed against these implementation frictions.

5. **Root-cap weighting is a practical compromise.** It correlates highly with inverse specific variance (avg 0.90) while being simpler to compute. It avoids the extreme large-cap concentration of market-cap weighting and the small-cap illiquidity problems of equal weighting.

6. **Factor portfolio properties are not unique.** Because the number of assets in the estimation universe far exceeds the number of factors, many valid factor portfolios exist. The regression weighting scheme is the key determinant of which portfolio is selected.

7. **Risk model users should understand which weighting scheme underlies their factor returns.** When comparing factor returns across different vendors or model versions, differences may stem from the regression weighting scheme rather than from genuine disagreement about factor premia.

## Connections

- [[menchero-characteristics-factor-portfolios]] -- Direct predecessor by the same lead author (Menchero 2010); this paper extends the factor portfolio construction framework to compare four regression weighting schemes and their risk-return consequences
- [[msci-foundations-of-factor-investing]] -- Provides the broader taxonomy of the six equity risk premia factors; this paper drills into how construction methodology (weighting) affects the realized properties of those factor portfolios
- [[cuffe-barra-market-factor]] -- Both papers examine Barra USE model mechanics; Cuffe focuses on the market factor and half-life design in USE3 vs USE4, while this paper examines style factor portfolio construction within USE4
- [[fama-french-factor-models]] -- Fama-French factors are implicitly equal-weighted (sorts on characteristics); this paper shows how moving to other weighting schemes materially changes factor portfolio behavior
- [[frazzini-pedersen-betting-against-beta]] -- BAB relies on a specific construction of the Beta factor; this paper shows that the Beta factor's properties (volatility ~8.6--9.2%, negative return) are relatively stable across weighting schemes but market-cap weighting is most volatile
- [[ehsani-linnainmaa-factor-momentum]] -- Factor momentum results depend on how underlying factor portfolios are constructed; the large return dispersion in Momentum across weighting schemes (0.66% to 3.70%) suggests factor momentum magnitudes are construction-dependent

#factor-portfolios #regression-weighting #barra #use4 #msci #factor-construction #momentum #earnings-yield #inverse-variance #market-cap-weighting #risk-models #style-factors
