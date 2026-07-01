# Characteristics of Factor Portfolios

> Source: Menchero, Jose. "Characteristics of Factor Portfolios." MSCI Barra Research Insights, March 2010.
> SSRN: 1601414 | MSCI Barra, Berkeley, CA

## Overview

Menchero develops a framework for interpreting factor models by examining the portfolios that replicate each factor's return. The central insight is that every factor in a cross-sectional regression model corresponds to a portfolio whose return equals the estimated factor return. There are two types: **simple factor portfolios** (from univariate regressions treating each factor in isolation) and **pure factor portfolios** (from multivariate regressions considering all factors simultaneously). Comparing the two reveals the effects of collinearity in the factor structure.

Using the Barra Global Equity Model (GEM2) — which includes a World factor, 55 country factors, 34 industry factors, and 8 style factors — the paper shows that for most country and industry factors, simple and pure portfolios are nearly identical (weight correlations > 0.95). For style factors, however, the portfolios diverge substantially (weight correlations 0.70–0.90) because styles are correlated with both industry composition and other styles. The pure Value portfolio, for instance, must short Financials stocks with low Value exposure and go long Information Technology stocks with high Value exposure — the opposite of what the simple Value portfolio does — to neutralize its industry bets.

The paper also introduces three intuitive measures of collinearity — Factor Weight Correlation, Factor Return Correlation, and Factor Leverage Ratio — and demonstrates how orthogonal rotation of collinear factors (e.g., replacing Size-cubed with a Non-linear Size factor) can reduce collinearity, lower leverage, and improve interpretability simultaneously.

## Factor Model Framework

The GEM2 model decomposes stock returns as:

r_n = f_w^P + Σ_c X_nc f_c^P + Σ_i X_ni f_i^P + Σ_s X_ns f_s^P + u_n^P

| Component | Description | Exposure Type |
|---|---|---|
| f_w^P | World (intercept) factor return | All stocks have exposure = 1 |
| f_c^P | Country factor returns (55) | Indicator (0/1) — each stock belongs to one country |
| f_i^P | Industry factor returns (34) | Indicator (0/1) — each stock belongs to one GICS industry |
| f_s^P | Style factor returns (8) | Continuous — standardized mean 0, SD 1 |
| u_n^P | Specific (idiosyncratic) return | — |

Regression weights v_n are proportional to √(market cap), down-weighting noisy small-cap stocks. Two constraints ensure a unique solution: cap-weighted country returns sum to zero, and cap-weighted industry returns sum to zero.

## Simple vs. Pure Factor Portfolios

| Property | Simple Factor Portfolio | Pure Factor Portfolio |
|---|---|---|
| Construction | Univariate regression (one factor + intercept) | Multivariate regression (all factors simultaneously) |
| Exposure to own factor | Unit exposure (= 1) | Unit exposure (= 1) |
| Exposure to other factors | Generally nonzero (incidental bets) | Zero to all other factors |
| Dollar neutrality | Yes (weights sum to zero, net of World) | Yes |
| Interpretation | Factor in isolation; includes correlated effects | Pure bet on one factor, hedging out everything else |
| Use case | Intuitive, easy to understand | Risk model factor return estimation; clean attribution |

### Simple Factor Portfolios

For **style factors**: portfolio weights are v_n × X_ns — long stocks with positive exposure, short those with negative, sized by regression weight and exposure magnitude. Dollar neutral, unit factor exposure.

For **group factors** (countries/industries): the simple portfolio goes 100% long the regression-weighted group portfolio and 100% short the simple World factor portfolio. Simple country factors have incidental industry and style exposures.

### Pure Factor Portfolios

Pure country factor portfolios are 100% long the country and 100% short the World factor, with zero net exposure to every industry and every style. This requires hedging trades — e.g., the pure Spain factor must short UK banks to hedge out the large banking exposure in the Spanish market.

Pure style factor portfolios have unit exposure to the target style and zero exposure to all other styles, all countries, and all industries. This requires substantial position adjustments relative to the simple portfolio.

## Example: Pure Factor Portfolio Weights (July 2009)

| Segment | ESTU World Portfolio | Pure World | Pure Spain | Pure UK | Pure Banks | Pure Value |
|---|---|---|---|---|---|---|
| World (Net) | 100.00 | 100.00 | 0.00 | 0.00 | 0.00 | 0.00 |
| Long | 100.00 | 107.02 | 121.89 | 95.85 | 97.88 | 47.20 |
| Short | 0.00 | −7.02 | −121.89 | −95.85 | −97.88 | −47.20 |
| Spain (Net) | 2.00 | 2.00 | 98.00 | −2.00 | 0.00 | 0.65 |
| UK (Net) | 7.22 | 7.22 | −7.22 | 92.78 | 0.00 | 0.00 |
| Banks (Net) | 10.12 | 10.12 | 0.00 | 0.00 | 89.88 | 0.00 |
| Spain Banks (Net) | 0.65 | 0.43 | 14.92 | −0.23 | 2.24 | 0.08 |

The pure Spain factor has 98% net weight in Spain (vs. 2% market weight), zero net weight in Banks overall, and zero net style exposure. The pure Value factor has zero net weight in every country and industry individually — its positions are spread across segments that don't correspond to any single factor.

## Measuring Collinearity

Three metrics quantify how much pure factor portfolios deviate from their simple counterparts:

| Metric | Definition | Interpretation | GEM2 Empirical Range |
|---|---|---|---|
| Factor Weight Correlation (ρ^CS) | Cross-sectional correlation of simple and pure portfolio weights | Higher = less collinearity; simple ≈ pure | Most factors > 0.95; style factors 0.70–0.90 |
| Factor Return Correlation (ρ^TS) | Time-series correlation of simple and pure factor returns (Jan 1997 – Jan 2010) | Higher = factor returns similar regardless of construction | Wide spread: 0.60–1.00; Volatility 0.97, Momentum 0.94 |
| Factor Leverage Ratio (L_k) | Ratio of sum of absolute weights: Σ\|Ω^P\| / Σ\|Ω^S\| | Higher = more hedging trades in pure portfolio; always ≥ 1 | Most < 1.3; Jordan > 2.0 (80% banks) |

Style factors consistently show the most divergence between simple and pure versions, because styles are correlated with both industry composition and other styles. The simple Value portfolio overweights Financials and underweights Information Technology — the pure Value portfolio must reverse these industry tilts, reducing weight correlation.

## Reducing Collinearity: Non-Linear Size

The Size-cubed (Size³) factor is a canonical example of collinearity: large-cap stocks have positive exposure to both Size and Size³, while small-cap stocks have negative exposure to both. The simple factor portfolios are nearly identical.

**Solution**: Define Non-linear Size (NLS) as the orthogonal residual:

X_n(NLS) = X_n(Size³) − b × X_n(Size), where b is chosen so Σ v_n X_n(NLS) X_n(Size) = 0

| Metric | Before (Size + Size³) | After (Size + NLS) |
|---|---|---|
| Size Factor Leverage Ratio | 1.86 | 1.12 |
| Size Factor Weight Correlation | 0.83 | 0.89 |
| NLS interpretation | Size³ — large vs. small (same as Size) | Mid-cap vs. large + small |

The orthogonalized NLS factor captures the performance differential of mid-cap stocks versus the extremes — a genuinely different economic effect from Size. Orthogonalization simultaneously improves the interpretability of both factors.

## Sector Decomposition of Style Returns (August 2009)

Pure style factor returns can be decomposed by GICS sector:

| Sector | Volatility | Momentum | Size | Value | Growth | NL Size | Liquidity | Leverage |
|---|---|---|---|---|---|---|---|---|
| Energy | −0.07 | −0.14 | −0.10 | −0.04 | −0.02 | 0.00 | 0.07 | 0.03 |
| Consumer Disc. | 0.50 | −0.51 | −0.11 | 0.12 | 0.07 | 0.06 | 0.02 | 0.20 |
| Financials | 1.12 | −0.95 | 0.13 | 0.47 | −0.13 | 0.17 | 0.07 | 0.33 |
| Info Technology | 0.09 | −0.06 | 0.03 | −0.01 | −0.06 | −0.03 | −0.07 | 0.04 |
| **Total** | **2.02** | **−2.43** | **−0.30** | **1.20** | **−0.34** | **0.16** | **−0.15** | **0.77** |

Financials dominated both Volatility (+1.12%) and Momentum (−0.95%): beaten-down high-beta financial stocks recovered strongly. Size was −0.30% overall (large-cap underperformed), but within Financials the sign reversed — large-cap financials outperformed small-cap. This illustrates that style factors do not move in lockstep across sectors.

## Implications for Practice

1. **Factor portfolios make factor models interpretable**: Every factor return is the return of a specific portfolio. Examining these portfolios — their country, industry, and style exposures — demystifies the "black box" of factor models.
2. **Pure factors are the correct lens for risk models**: Pure factor portfolios have zero exposure to all other factors, making them the appropriate building blocks for covariance estimation and performance attribution. Simple factor portfolios include incidental bets that contaminate interpretation.
3. **Style factors are most affected by collinearity**: Country and industry factor portfolios are largely unchanged between simple and pure constructions (weight correlation > 0.95). Style factors diverge substantially (weight correlation 0.70–0.90) because styles are correlated with industry composition.
4. **Orthogonalization can improve interpretability**: When two factors are collinear (e.g., Size and Size³), rotating the offending factor to be perpendicular can produce a more interpretable factor (Non-linear Size = mid-cap effect) while reducing leverage and improving weight correlations.
5. **Sector decomposition reveals within-factor dynamics**: The same style factor can behave differently across sectors in the same month. Portfolio managers should analyze factor returns at the sector level, not just in aggregate, to understand the sources of factor performance.
6. **Factor Leverage Ratio flags problematic factors**: A high leverage ratio (e.g., Jordan > 2.0) signals that the pure portfolio requires large offsetting positions to hedge out collinear exposures — increasing transaction costs and estimation error.

## Connections

- [[menchero-factor-alignment]] — This paper provides the portfolio construction foundations (simple, pure, minimum-volatility factor portfolios) that underpin the factor alignment analysis. The alignment paper extends the framework by asking: what happens when the factor structure used for optimization is misspecified?
- [[fama-french-factor-models]] — FF's SMB, HML, RMW, CMA are simple factor portfolios in Menchero's taxonomy: they sort on one characteristic at a time with no explicit control for other factors. Barra-style pure factor portfolios control for all other factors simultaneously, which is why Barra factor returns can differ from FF factor returns even when the underlying characteristics are similar.
- [[kelly-principal-portfolios]] — Kelly et al.'s principal portfolios are formed via SVD of the prediction matrix, producing portfolios that are orthogonal by construction. This achieves the same zero-cross-exposure property as pure factor portfolios, but without specifying the factor structure ex ante — the SVD discovers the factors endogenously.
- [[msci-foundations-of-factor-investing]] — MSCI's six-factor taxonomy uses characteristics (Value, Size, Momentum, etc.) that correspond to Menchero's style factors. This paper explains why the MSCI factor indexes — which sort on one characteristic at a time — may have incidental exposures to other factors, and how pure factor construction addresses this.
- [[frazzini-pedersen-betting-against-beta]] — BAB sorts stocks on beta (a style-like characteristic) without controlling for other factors, making it a simple factor portfolio. Menchero's framework predicts that the pure BAB portfolio — controlling for country, industry, and other styles — would behave differently, particularly in markets where beta is correlated with industry composition.

#factor-portfolios #simple-factors #pure-factors #collinearity #barra #GEM2 #risk-models #factor-construction #style-factors #orthogonalization #sector-decomposition
