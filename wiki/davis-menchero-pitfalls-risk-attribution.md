# Pitfalls in Risk Attribution

> Source: Davis, Ben, and Jose Menchero. "Pitfalls in Risk Attribution." MSCI Research Insight, February 2011.
> Affiliations: MSCI Analytics Research

## Overview

This paper identifies a critical but under-appreciated problem in risk attribution for active portfolios: the mismatch between absolute and relative return sources. While most active managers make investment decisions on a benchmark-relative basis, many risk attribution models employ absolute return sources. The authors demonstrate that this inconsistency produces a series of non-intuitive and misleading results -- including universally negative correlations, cash positions that appear riskless, and aggressive bets flagged as risk-reducing.

The paper builds on the *x-sigma-rho* framework (Menchero and Davis, 2010), which decomposes risk contribution into three intuitive components: exposure size, standalone volatility, and correlation with the active portfolio. Davis and Menchero systematically compare absolute vs. relative return sources across three attribution dimensions -- sector-based, security-based, and factor-based -- using a worked example with the MSCI World Value and World Growth indices. In every case, switching from absolute to relative return sources resolves the pitfalls and produces results consistent with the manager's actual decision-making process.

The contribution is practical and methodological: for sector attribution, the fix is to use Brinson-Fachler (relative sector returns) instead of Brinson-Hood-Beebower (absolute sector returns); for security attribution, to use security relative returns rather than absolute returns; and for factor models, to augment the model with a World factor that converts industry factors from absolute to relative return sources.

## The x-sigma-rho Risk Attribution Framework

The paper's analytical backbone is the *x-sigma-rho* formula, which aligns risk and performance attribution to the same set of return sources.

**Active return decomposition:**

R^A = sum_m( x_m * g_m )

where x_m is the portfolio exposure to source m, and g_m is the return of the source.

**Risk attribution (x-sigma-rho formula):**

sigma(R^A) = sum_m( x_m * sigma(g_m) * rho(g_m, R^A) )

The three components are:
- **x** -- exposure size (more aggressive positions contribute more risk)
- **sigma** -- standalone volatility of the return source
- **rho** -- correlation of the source with the active portfolio (determines whether the source increases or decreases total risk)

**Marginal Contribution to Active Risk (MCAR):**

MCAR_m = sigma(g_m) * rho(g_m, R^A)

This gives the well-known risk decomposition: sigma(R^A) = sum_m( x_m * MCAR_m ).

**Information Ratio decomposition:**

IR = E[R^A] / sigma(R^A) = sum_m( (x_m * MCAR_m) / sigma(R^A) ) * ( E[g_m] / MCAR_m )

where the first term is the *risk weight* of source m (summing to 100%) and the second term is the *component information ratio*. The optimal portfolio equalizes component IRs across all sources, implying:

E[g_m] = IR^opt * MCAR_m^opt

This means managers should be bullish on sources with positive MCAR and bearish on those with negative MCAR. This framework is only valid when risk and return are attributed to the *same* sources -- the central requirement the paper enforces.

## Pitfall 1: Sector-Based Attribution (Absolute vs. Relative)

The paper compares two sector-based performance attribution models using a worked example:
- **Portfolio:** 95% MSCI World Growth + 5% cash (USD)
- **Benchmark:** MSCI World Value
- **Risk model:** Barra GEM2L
- **Predicted tracking error:** 6.73%; active beta: -0.18

### Brinson-Hood-Beebower (absolute sources)

R^A = sum_i( (w_i^P - w_i^B) * R_i^B ) + sum_i( w_i^P * (R_i^P - R_i^B) )

| Sector | Port Wt | Bench Wt | Active Wt | Abs Return Vol | Abs Return Corr | Alloc Risk Contrib | Selec Risk Contrib | Total Risk Contrib |
|---|---|---|---|---|---|---|---|---|
| Energy | 0.07 | 0.14 | -0.06 | 31.32% | -0.70 | 1.41% | -0.21% | 1.20% |
| Materials | 0.08 | 0.05 | 0.03 | 38.24% | -0.73 | -0.87% | 0.39% | -0.48% |
| Financials | 0.08 | 0.34 | -0.26 | 38.66% | -0.86 | 8.79% | 0.46% | 9.25% |
| IT | 0.19 | 0.03 | 0.16 | 29.32% | -0.66 | -3.00% | 0.13% | -2.86% |
| Cash | 0.05 | 0.00 | 0.05 | 0.00% | 0.00 | 0.00% | 0.00% | 0.00% |
| **Total** | 1.00 | 1.00 | 0.00 | 5.65% | 0.87 | 4.92% | 1.81% | **6.73%** |

**Pitfalls observed:**
1. **Cash appears riskless.** The 5% cash position contributes zero to tracking error because the absolute return of cash is zero with zero volatility. In reality, holding cash is a major active bet.
2. **Every sector has negative correlation with the active portfolio.** All sectors have positive beta while the active portfolio has negative beta (-0.18), forcing all absolute correlations to be negative.
3. **Assuming optimality, negative MCARs imply negative expected returns for every sector.** This is internally consistent but gives no insight into expected returns *relative to the benchmark*, which is what active managers care about.
4. **The large IT overweight appears to reduce risk by 286 bps.** This is counterintuitive for the portfolio's most aggressive sector bet.

### Brinson-Fachler (relative sources)

R^A = sum_i( (w_i^P - w_i^B) * (R_i^B - R^B) ) + sum_i( w_i^P * (R_i^P - R_i^B) )

The only difference: sector allocation uses *benchmark-relative* sector returns (R_i^B - R^B) instead of absolute sector returns.

| Sector | Port Wt | Bench Wt | Active Wt | Rel Return Vol | Rel Return Corr | Alloc Risk Contrib | Selec Risk Contrib | Total Risk Contrib |
|---|---|---|---|---|---|---|---|---|
| Energy | 0.07 | 0.14 | -0.06 | 13.19% | 0.26 | -0.22% | -0.21% | -0.43% |
| Financials | 0.08 | 0.34 | -0.26 | 10.22% | -0.77 | 2.08% | 0.46% | 2.55% |
| IT | 0.19 | 0.03 | 0.16 | 13.16% | 0.47 | 0.96% | 0.13% | 1.10% |
| Cash | 0.05 | 0.00 | 0.05 | 30.74% | 0.83 | 1.27% | 0.00% | 1.27% |
| **Total** | 1.00 | 1.00 | 0.00 | 5.65% | 0.87 | 4.92% | 1.81% | **6.73%** |

**Pitfalls resolved:**
1. **Cash now contributes 127 bps to tracking error** -- the relative return of cash is simply -R^B, which has the same volatility as the benchmark (30.74%) and is highly correlated (0.83) with the active portfolio.
2. **Most sectors now have positive correlations with the active portfolio.** Sectors with positive (negative) active weights tend to have positive (negative) correlations, matching intuition.
3. **IT overweight now adds 96 bps of risk** via allocation, not reduces it. The IT sector has correlation 0.47 with the active return -- when IT outperforms the benchmark, the portfolio tends to outperform too.
4. **Financials underweight remains the largest allocation risk** (208 bps), but is far less inflated than the 879 bps reported under absolute sources.

## Pitfall 2: Security-Based Attribution (Absolute vs. Relative)

### Absolute return sources

R^A = sum_n( w_n^A * r_n )

where r_n is the absolute security return. Applying x-sigma-rho:

MCAR_{n,abs} = sigma(r_n) * rho(r_n, R^A)

| Asset | Port Wt | Bench Wt | Active Wt | Abs Vol | Abs Corr | Abs MCAR | Active Risk Contrib |
|---|---|---|---|---|---|---|---|
| Bank of America | 0.00% | 1.38% | -1.38% | 76.10% | -0.65 | -49.64% | 0.68% |
| Exxon Mobil | 0.00% | 3.15% | -3.15% | 31.98% | -0.59 | -18.79% | 0.59% |
| Microsoft | 1.93% | 0.00% | 1.93% | 34.87% | -0.46 | -15.97% | -0.31% |
| US Dollar (Cash) | 5.00% | 0.00% | 5.00% | 0.00% | -- | -- | 0.00% |

**Pitfalls:** Every stock has negative correlation and negative MCAR. Cash contributes nothing. Microsoft (the largest overweight) appears to *reduce* risk by 31 bps. Under optimality, all stocks have negative expected returns.

### Relative return sources

R^A = sum_n( w_n^A * (r_n - R^B) )

MCAR_{n,rel} = sigma(r_n - R^B) * rho(r_n - R^B, R^A)

| Asset | Port Wt | Bench Wt | Active Wt | Rel Vol | Rel Corr | Rel MCAR | Active Risk Contrib |
|---|---|---|---|---|---|---|---|
| US Dollar (Cash) | 5.00% | 0.00% | 5.00% | 30.74% | 0.83 | 25.48% | 1.27% |
| Bank of America | 0.00% | 1.38% | -1.38% | 59.24% | -0.41 | -24.16% | 0.33% |
| Microsoft | 1.93% | 0.00% | 1.93% | 27.16% | 0.35 | 9.51% | 0.18% |
| Exxon Mobil | 0.00% | 3.15% | -3.15% | 24.34% | 0.27 | 6.69% | -0.21% |

**Key results with relative sources:**
- US Dollar becomes the riskiest position (127 bps), consistent with the sector-level cash result.
- Bank of America remains the riskiest stock (positive risk contribution from underweight times negative MCAR).
- Microsoft has positive MCAR (9.51%), confirming the manager expects it to outperform the benchmark.
- Exxon Mobil now has *positive* relative MCAR (6.69%) despite being underweighted. This reveals it serves as a **hedge** -- the manager accepts an expected loss because holding the underweight reduces tracking error by 21 bps.

### Relationship between absolute and relative MCAR

MCAR_{n,abs} = MCAR_{n,rel} - MCAR_{cash,rel}

This is exact. For example, Exxon Mobil absolute MCAR (-18.79%) = relative MCAR (6.69%) - cash relative MCAR (25.48%).

## Pitfall 3: Factor-Based Attribution (Absolute vs. Relative Industry Factors)

Factor models decompose returns as: r_n = sum_k( X_{nk} * f_k ) + u_n, and active return as:

R^A = sum_k( X_k^A * f_k ) + sum_n( w_n^A * u_n )

### Standard model (absolute industry factors)

In single-country factor models, industry factor replicating portfolios are 100% net long, making them absolute return sources. Style factors are already benchmark-relative (zero benchmark exposure by construction).

| Source | Port Exp | Bench Exp | Active Exp | Factor Vol | Factor Corr | Factor MCAR | Active Risk Contrib |
|---|---|---|---|---|---|---|---|
| Energy | 0.07 | 0.14 | -0.06 | 34.35% | -0.71 | -24.35% | 1.56% |
| Financials | 0.08 | 0.34 | -0.26 | 33.38% | -0.86 | -28.81% | 7.58% |
| IT | 0.19 | 0.03 | 0.16 | 30.14% | -0.67 | -20.12% | -3.13% |
| Utilities | 0.02 | 0.07 | -0.05 | 29.32% | -0.79 | -23.25% | 1.15% |
| Volatility | -0.34 | 0.00 | -0.34 | 10.67% | -0.72 | -7.63% | 2.59% |
| **Total** | | | | 6.73% | 1.00 | 6.73% | **6.73%** |

**Same pitfalls recur:** Every industry factor has negative correlation and negative MCAR. The IT overweight appears to *reduce* risk by 313 bps. Utilities (underweighted) contributes 115 bps -- qualitatively matching the inflated 86 bps from Brinson-Hood-Beebower in Table 1.

### Augmented model with World factor

The fix is to add a **World factor** with unit exposure for all equities and zero for cash. This introduces exact collinearity with industries, resolved by constraining cap-weighted industry factor returns to sum to zero:

sum_{k in Ind}( w_k^B * f_tilde_k ) = 0

The augmented industry factor returns become: f_tilde_k = f_k - f_World. When regression weights equal benchmark cap-weights, f_World = R^B, so the World factor captures the benchmark return and industry factors become benchmark-relative.

| Source | Port Exp | Bench Exp | Active Exp | Factor Vol | Factor Corr | Factor MCAR | Active Risk Contrib |
|---|---|---|---|---|---|---|---|
| **World** | 0.95 | 1.00 | -0.05 | 30.74% | -0.83 | -25.48% | 1.27% |
| Energy | 0.07 | 0.14 | -0.06 | 13.41% | 0.08 | 1.13% | -0.07% |
| Financials | 0.08 | 0.34 | -0.26 | 7.54% | -0.44 | -3.33% | 0.88% |
| IT | 0.19 | 0.03 | 0.16 | 12.81% | 0.42 | 5.36% | 0.83% |
| Utilities | 0.02 | 0.07 | -0.05 | 9.79% | 0.23 | 2.23% | -0.11% |
| Volatility | -0.34 | 0.00 | -0.34 | 10.67% | -0.72 | -7.63% | 2.59% |
| **Total** | | | | 6.73% | 1.00 | 6.73% | **6.73%** |

**Pitfalls resolved:**
- **World factor MCAR (-25.48%) is the exact negative of the cash relative MCAR (25.48%)** from the security-level analysis. The active risk contribution (127 bps) matches the cash allocation effect in Brinson-Fachler.
- **Industry correlations flip to intuitive signs.** IT now has positive correlation (0.42) and positive MCAR (5.36%), confirming its overweight adds risk as expected.
- **Utilities now reduces risk by 11 bps** (vs. adding 115 bps in the absolute model), consistent with the Brinson-Fachler result.
- **Style factors are unaffected** -- the World factor has zero exposure to all style factors, leaving their MCARs unchanged.

The MCAR relationship across models is:

MCAR_{k,abs} = MCAR_{k,rel} - MCAR_{World}

which is the factor-level analog of the security-level result (Eq. 17).

## Summary of Pitfalls and Solutions

| Dimension | Absolute-Source Pitfall | Relative-Source Solution |
|---|---|---|
| **Sector (BHB)** | Cash contributes zero risk; all sectors negatively correlated; allocation risk inflated | Use Brinson-Fachler with benchmark-relative sector returns |
| **Security** | All stocks have negative MCAR; cash riskless; overweighted stocks appear diversifying | Use security relative returns (r_n - R^B) |
| **Factor (industries)** | Industry factors 100% net long = absolute sources; negative MCARs; overweight IT looks risk-reducing | Add World factor; industry returns become f_tilde_k = f_k - f_World |
| **Factor (styles)** | No pitfall -- style factor exposures are benchmark cap-weighted to zero; already relative | No change needed |

## Implications for Practice

1. **Always match risk and return sources.** The x-sigma-rho framework is only valid for risk-adjusted analysis when risk and performance attribution use the same underlying return sources. Active managers should use benchmark-relative sources throughout.

2. **Replace Brinson-Hood-Beebower with Brinson-Fachler for sector risk attribution.** The BHB model uses absolute sector returns for allocation, which produces inflated and counterintuitive risk contributions. The Brinson-Fachler correction (using R_i^B - R^B) resolves all sector-level pitfalls.

3. **Use security relative returns for bottom-up risk attribution.** Attributing risk to absolute stock returns makes cash invisible and produces universally negative MCARs for portfolios with negative active beta. Relative returns (r_n - R^B) reveal the true risk profile including hedging positions.

4. **Augment factor models with a World (or market) factor to convert industry factors to relative sources.** In standard single-country models, industry factor replicating portfolios are 100% net long (absolute). Adding a World factor with the collinearity constraint causes industry returns to be expressed net of the benchmark, resolving the pitfalls while leaving style factor attribution unchanged.

5. **Watch for the beta sign.** Most of the absolute-source pitfalls stem from portfolios with negative active beta (portfolio beta < 1). When stocks have positive beta but the active portfolio has negative beta, the stock-level correlations with the active return are mechanically negative. This is the root cause of universally negative MCARs.

6. **Use relative MCARs to identify hedging positions.** A security can have positive relative MCAR (the manager expects outperformance) yet still be underweighted, because it reduces tracking error -- i.e., it functions as a hedge. This subtlety is invisible in simple performance attribution but emerges naturally in risk-adjusted relative attribution.

7. **The relationship MCAR_{abs} = MCAR_{rel} - MCAR_{cash,rel} holds exactly** at both the security and factor level. This identity provides a useful cross-check and clarifies how absolute and relative risk pictures differ by a single constant offset.

## Connections

- [[menchero-factor-alignment]] -- Factor alignment addresses which factors to include in a model; this paper addresses how those factors' return sources (absolute vs. relative) affect risk attribution. Both highlight non-obvious consequences of model specification choices.
- [[cuffe-barra-market-factor]] -- The USE4 explicit market factor is closely related to the World factor proposed here. Both serve to separate market-level risk from industry-specific risk, converting industry factors from absolute to relative return sources.
- [[menchero-characteristics-factor-portfolios]] -- The distinction between simple (100% net long) and pure (zero-net-investment) factor portfolios is directly relevant: industry simple portfolios are absolute return sources (the pitfall), while pure portfolios are benchmark-relative.
- [[barra-gem-handbook]] -- The worked example uses the Barra GEM2L model. The World factor augmentation described here is directly applicable to GEM-family models.
- [[barra-use4-methodology]] -- USE4's explicit market factor achieves the same conversion from absolute to relative industry sources described in this paper.

#risk-attribution #x-sigma-rho #mcar #tracking-error #brinson-fachler #brinson-hood-beebower #absolute-vs-relative #world-factor #barra #gem2 #active-management #information-ratio #factor-models #industry-factors
