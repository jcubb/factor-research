# BARRA US Equity Model Version 3 (US-E3) Handbook

**Source:** BARRA, Inc. *United States Equity Model Version 3 (US-E3) Handbook.* Berkeley, CA: BARRA, 1998.

---

## Overview

The US-E3 handbook is BARRA's definitive reference for their third-generation US equity risk model, published in 1998 as the successor to US-E1 (1975) and US-E2 (early 1980s). The model decomposes equity returns into 65 common factors (52 industries + 13 risk indices) plus an asset-specific return, enabling portfolio risk forecasting, performance attribution, and optimization. This document covers the full estimation pipeline: universe construction, factor exposure definition, cross-sectional factor return estimation via GLS regression, factor covariance matrix estimation with exponential weighting and GARCH volatility adjustment, and specific risk modeling via a three-component structural decomposition. US-E3 introduced several methodological advances over US-E2, including momentum as a risk index, multiple industry allocation, option-implied volatility descriptors, and an extended asymmetric GARCH model for market volatility forecasting.

---

## The Multiple-Factor Model

The core of US-E3 is the **Multiple-Factor Model (MFM)**, which decomposes the excess return of asset $j$ as:

$$r_j = \sum_{k=1}^{K} X_{jk} \cdot f_k + u_j$$

where $X_{jk}$ is asset $j$'s exposure to factor $k$, $f_k$ is the return to factor $k$, and $u_j$ is the asset-specific return. For a portfolio with weights $h_p$, the predicted risk decomposes into factor and specific components:

$$V_p = h_p^T (X F X^T + \Delta) h_p$$

where $F$ is the $K \times K$ factor covariance matrix and $\Delta$ is the diagonal matrix of specific variances. This structure reduces the dimensionality problem from estimating an $N \times N$ covariance matrix (millions of parameters) to a $K \times K$ factor covariance matrix plus $N$ specific variances.

### Risk Decomposition

The model enables several decompositions useful in practice:

| Decomposition | Formula | Use Case |
|---|---|---|
| **Total active risk** | $\psi_p^2 = h_{pA}^T V h_{pA}$ | Tracking error vs. benchmark |
| **Factor contribution** | $\psi_{factor}^2 = h_{pA}^T X F X^T h_{pA}$ | Systematic risk budget |
| **Specific contribution** | $\psi_{specific}^2 = h_{pA}^T \Delta h_{pA}$ | Idiosyncratic diversification |
| **Marginal contribution** | $MCA_k = \partial \psi_p / \partial X_{pk}$ | Risk attribution by factor |

where $h_{pA} = h_p - h_b$ is the vector of active weights.

---

## US-E3 Factor Structure

US-E3 uses 65 common factors: 52 industry factors and 13 risk indices.

### Risk Indices

| # | Risk Index | Key Descriptors | Interpretation |
|---|---|---|---|
| 1 | **Volatility** | BTSG, DASTD, HILO, LPRI, CMRA, VOLBT, SERDP, OPSTD | Market-based risk; beta-times-sigma, daily std dev, high-low range, cumulative range, option-implied vol |
| 2 | **Momentum** | RSTR, HALPHA | Relative strength (12-month cumulative excess return), historical alpha from 60-month regression |
| 3 | **Size** | LNCAP | Log of market capitalization |
| 4 | **Size Nonlinearity** | LCAPCB | Cube of normalized log market cap; captures non-linear size effect |
| 5 | **Trading Activity** | STOA, STOQ, STOM, STO5, FSPLIT, VLVR | Share turnover at multiple horizons, forward split indicator, volume-to-variance ratio |
| 6 | **Growth** | PAYO, VCAP, AGRO, EGRO, EGIBS, DELE | Payout ratio, capital structure variability, asset/earnings growth rates, analyst-predicted growth |
| 7 | **Earnings Yield** | EPIBS, ETOP, ETP5 | Analyst-predicted E/P, trailing E/P, historical 5-year E/P |
| 8 | **Value** | BTOP | Book-to-price ratio |
| 9 | **Earnings Variability** | VERN, VFLO, EXTE, SPIBS | CV of earnings, CV of cash flows, extraordinary items ratio, analyst forecast dispersion |
| 10 | **Leverage** | MLEV, BLEV, DTOA, SNRRT | Market leverage, book leverage, debt-to-assets, senior debt rating |
| 11 | **Currency Sensitivity** | CURSENS | Regression of market-model residuals on contemporaneous + 2 lagged FX index returns |
| 12 | **Dividend Yield** | P_DYLD | BARRA-predicted dividend yield from trailing dividends, stock returns, and dividend announcements |
| 13 | **Non-Estimation Universe** | NONESTU | Binary indicator: 1 if outside estimation universe, 0 if inside |

Descriptors are standardized to zero mean and unit standard deviation (cap-weighted) within the estimation universe before being combined into risk indices. The method of combining descriptors into risk indices is proprietary to BARRA.

### Improvements Over US-E2

| Feature | US-E2 | US-E3 |
|---|---|---|
| Risk indices | 12 (no Momentum) | 13 (adds Momentum) |
| Industries | 55 | 52 (+ 82 mini-industries) |
| Industry assignment | Single industry per stock | Multiple industry allocation via Compustat segments |
| Volatility descriptors | No option-implied | Adds option-implied standard deviation (OPSTD) |
| Market variance | Simple exponential weighting | Extended asymmetric GARCH(1,1) |
| Specific risk | Two-component | Three-component structural model with cap-decile scaling |
| Estimation universe | ~1,500 stocks | ~1,900 stocks (industry fill-in rule) |
| History | Back to Dec 1984 | Back to Dec 1972 |

---

## Estimation Universe

The estimation universe is the set of assets used to estimate factor returns and covariances. US-E3 constructs it as follows:

1. **Start with the top ~1,500 stocks by market capitalization** (covering roughly 93% of total US equity market cap)
2. **Fill each industry to a minimum of 20 members** by adding the largest stocks from under-represented industries
3. **Result: approximately 1,941 stocks** (as of December 1997)

The fill-in rule ensures that every industry factor return is estimated with sufficient cross-sectional observations, preventing noisy or degenerate industry factor returns for small industries.

Stocks outside the estimation universe are still covered by the model. The NONESTU factor captures any systematic return differential between estimation-universe and non-estimation-universe stocks.

---

## Industry Classification

US-E3 uses a proprietary three-tier classification: 13 **sectors** (display only), 52 **industries** (model factors), and 82 **mini-industries** (monitoring and future promotion).

### Multiple Industry Allocation

A key US-E3 innovation is allowing stocks to belong to multiple industries simultaneously, with fractional weights summing to 1. This is achieved using Compustat segment data:

- For each company, business segments are mapped to US-E3 industries
- Weights are derived from a blend of segment sales, assets, and operating income
- A conglomerate like GE can thus have exposures of, say, 0.30 to Heavy Electrical Equipment, 0.25 to Financial Services, 0.20 to Media, etc.

This substantially improves the risk model's treatment of diversified companies, which were previously forced into a single best-fit industry.

### Sector and Industry Mapping (Selected Examples)

| Sector | Industries (Code) | Count |
|---|---|---|
| Basic Materials | Mining & Metals (MINING), Gold (GOLD), Forest Products (FOREST), Chemicals (CHEM) | 6 |
| Energy | Energy Reserves (RESERVES), Oil Refining (OILREF), Gas Pipelines (GASPIPE), Oil Services (OILSERV) | 4 |
| Technology | Electronic Equipment (MANHT), Communications Equipment (COMMEQP), Semiconductors (SEMICOND), Computer Hardware (COMPUTER), Computer Software (SOFTWARE), Defense & Aerospace (DEFAERO) | 6 |
| Financial | Life Insurance (LIFEINS), P&C Insurance (OTHERINS), Banks (BANK), Money Center Banks (MONCENTR), Thrifts (THRIFT), Securities & Asset Management (SECASSET), Financial Services (FINSERV) | 8 |
| Health Care | Medical Providers (MEDPROV), Medical Products (MEDPROD), Drugs (DRUGS) | 5 |
| Utilities | Electric Utilities (ELECUTIL), Gas Utilities (GASWATER) | 3 |

---

## Factor Return Estimation

Factor returns are estimated each month via a **cross-sectional GLS regression**:

$$r_t = X_t f_t + u_t$$

where $r_t$ is the $N \times 1$ vector of excess returns, $X_t$ is the $N \times K$ exposure matrix, and $f_t$ is the $K \times 1$ vector of factor returns to be estimated. The GLS estimator is:

$$\hat{f}_t = (X_t^T W_t X_t)^{-1} X_t^T W_t r_t$$

where $W_t$ is a diagonal weight matrix with entries $w_i = h\sigma_i^{-2}$, i.e., inverse specific variance weights, **truncated** such that no weight exceeds the 99th percentile. This truncation prevents any single stock (typically a very low specific-risk mega-cap) from dominating the regression.

### Regression Constraints

Industry factor exposures sum to 1 for each asset (they represent fractional industry membership). The regression includes a market-cap constraint ensuring the cap-weighted market portfolio has zero exposure to all risk index factors. This means risk index factor returns represent the return to a zero-investment, market-neutral strategy.

### The NONESTU Factor

The Non-Estimation Universe Indicator (NONESTU) is a binary factor included in the regression. Its factor return captures the systematic performance differential between estimation-universe stocks and the broader coverage universe. This prevents any systematic return difference from contaminating the other factor return estimates.

---

## Factor Covariance Matrix Estimation

The factor covariance matrix $F$ is estimated from the time series of estimated factor returns $\{\hat{f}_t\}$. US-E3 uses three key techniques.

### Exponential Weighting

Rather than equal-weighting all historical observations, US-E3 applies exponential decay weights:

$$w(t) = \delta^{T-t}$$

where $\delta = 0.5^{1/\text{HALF-LIFE}}$ is the decay parameter and the **half-life is 90 months** for factor covariance estimation. This means an observation from 90 months ago receives half the weight of the most recent observation. The exponentially-weighted covariance estimator is:

$$\hat{F}_{kl} = \frac{\sum_{t=1}^{T} w(t)(f_{kt} - \bar{f}_k)(f_{lt} - \bar{f}_l)}{\sum_{t=1}^{T} w(t)}$$

| Parameter | Value | Purpose |
|---|---|---|
| Half-life (factor covariance) | 90 months | Balances stability vs. responsiveness |
| Half-life (specific risk) | Shorter (not disclosed) | Specific risk is noisier, needs faster adaptation |
| Decay parameter $\delta$ at 90-month HL | $0.5^{1/90} \approx 0.9923$ | Weight per month |
| Effective window | ~20 years | History back to Dec 1972 |

### GARCH Volatility Adjustment

The exponentially-weighted covariance matrix captures long-run factor correlations but may understate risk during volatile periods. US-E3 applies an **extended asymmetric GARCH(1,1)** model to the market portfolio variance to dynamically adjust the overall level of the covariance matrix:

$$\text{Var}(r_m)_t = \alpha + \gamma \cdot \epsilon_{t-1}^2 + \beta \cdot \text{Var}(r_m)_{t-1} + \theta \cdot \epsilon_{t-1}$$

The **asymmetric term** $\theta \cdot \epsilon_{t-1}$ (where $\epsilon_{t-1}$ is the signed market shock) captures the empirical finding that **negative market returns increase future volatility more than positive returns of the same magnitude**. The ratio of the GARCH-predicted variance to the exponentially-weighted variance provides a scaling factor applied to the entire factor covariance matrix:

$$F^{adj}_t = \frac{\text{Var}^{GARCH}(r_m)_t}{\text{Var}^{EWMA}(r_m)_t} \cdot \hat{F}_t$$

This allows the model to react rapidly to volatility regime changes (e.g., the 1987 crash or the 1998 LTCM crisis) without waiting for the slow exponential weighting to catch up.

### Relationship to BARRA Country Models

US-E3 shares its estimation methodology with other BARRA single-country models, though parameter choices vary:

| Parameter | US-E3 | Japan (JPE2) | UK (UKE2) | Germany (GRE1) |
|---|---|---|---|---|
| Industries | 52 | 36 | 38 | 25 |
| Risk indices | 13 | 8 | 10 | 9 |
| Estimation universe | ~1,900 | ~1,400 | ~800 | ~300 |
| Factor cov half-life | 90 months | 90 months | 90 months | 90 months |

---

## Specific Risk Estimation

Specific risk for stock $i$ at time $t$ is estimated via a **three-component structural model**:

$$\sigma(u_{it}) = \text{scale}_{it} \cdot \hat{S}_t \cdot (1 + \hat{V}_{it})$$

where:

| Component | Symbol | Description | Estimation Method |
|---|---|---|---|
| **Average specific risk** | $\hat{S}_t$ | Time-series level of average specific risk across all stocks | AR(1) model with lagged market returns as exogenous variable |
| **Relative specific risk** | $\hat{V}_{it}$ | Cross-sectional variation: how stock $i$ deviates from the average | Pooled cross-sectional regression on factor exposures |
| **Capitalization scaling** | $\text{scale}_{it}$ | Adjustment for systematic over/under-prediction by cap decile | 10 cap-decile scaling coefficients, updated monthly |

### Average Specific Risk ($\hat{S}_t$)

The time-series component captures the common movement in the overall level of specific risk. It is modeled as an autoregressive process with lagged market returns:

$$\hat{S}_t = a_0 + a_1 \hat{S}_{t-1} + a_2 |r_{m,t-1}|$$

The inclusion of lagged absolute market returns reflects the empirical pattern that specific risk rises after large market moves (both up and down), consistent with the GARCH-type behavior observed in market volatility.

### Relative Specific Risk ($\hat{V}_{it}$)

This cross-sectional component captures persistent differences in specific risk levels across stocks based on their observable characteristics. It is estimated by regressing realized specific risk deviations on factor exposures in a pooled cross-sectional regression. Stocks with high volatility, high leverage, or small size tend to have above-average specific risk.

### Cap-Decile Scaling

Even after the $S_t$ and $V_{it}$ adjustments, the model may systematically over- or under-predict specific risk for certain capitalization ranges. The scaling coefficients correct for this, estimated as the ratio of realized to predicted specific risk within each capitalization decile. This is particularly important because the largest stocks tend to have lower specific risk than predicted by the cross-sectional model alone.

---

## Descriptor Definitions (Selected Key Formulas)

### Volatility Descriptors

| Descriptor | Code | Formula / Definition |
|---|---|---|
| Beta times sigma | BTSG | $\sqrt{\beta^2 \cdot \sigma_e^2}$ where $\beta$ = historical beta, $\sigma_e$ = residual std dev; set to 0 if negative |
| Daily std deviation | DASTD | $\sqrt{N_{days} \cdot \sum_{t=1}^{T} w_t r_t^2}$ using 65 trading days, $N_{days}=23$ |
| High-low range | HILO | $\log(P_H / P_L)$ over last month |
| Cumulative range | CMRA | $\log\frac{1+Z_{max}}{1+Z_{min}}$ where $Z_t$ = cumulative excess return over risk-free, max/min over 12 months |
| Serial dependence | SERDP | Ratio of variance of 3-month overlapping residuals to sum of individual monthly residual variances |
| Option-implied vol | OPSTD | Black-Scholes implied vol from nearest ATM call option |

### Momentum Descriptors

| Descriptor | Code | Formula |
|---|---|---|
| Relative strength | RSTR | $\sum_{t=1}^{12} \log(1+r_{i,t}) - \sum_{t=1}^{12} \log(1+r_{f,t})$ (12-month cumulative excess return, continuously compounded) |
| Historical alpha | HALPHA | Intercept from 60-month regression of stock excess returns on S&P 500 excess returns |

### Growth Descriptors

| Descriptor | Code | Formula |
|---|---|---|
| Payout ratio (5yr) | PAYO | $\frac{\frac{1}{T}\sum D_t}{\frac{1}{T}\sum E_t}$ (average dividends / average earnings) |
| Asset growth | AGRO | Slope $b$ from regression $TA_t = a + bt + \epsilon_t$ ($t=1,...,5$), divided by mean total assets |
| Earnings growth | EGRO | Slope $b$ from regression $EPS_t = a + bt + \epsilon_t$ ($t=1,...,5$), divided by mean EPS |
| Analyst-predicted growth | EGIBS | $\frac{EARN - EPS}{(EARN + EPS)/2}$ where $EARN$ = weighted I/B/E/S consensus |
| Recent earnings change | DELE | $\frac{EPS_t - EPS_{t-1}}{(EPS_t + EPS_{t-1})/2}$ |

### Leverage Descriptors

| Descriptor | Code | Formula |
|---|---|---|
| Market leverage | MLEV | $(ME + PE + LD) / ME$ |
| Book leverage | BLEV | $(CEQ + PE + LD) / CEQ$ |
| Debt-to-assets | DTOA | $(LD + DCL) / TA$ |

where $ME$ = market equity, $PE$ = book preferred equity, $LD$ = book long-term debt, $CEQ$ = book common equity, $DCL$ = debt in current liabilities, $TA$ = total assets.

### Currency Sensitivity

The CURSENS descriptor is constructed via a two-step regression:

1. Regress stock excess returns on S&P 500 excess returns to get residuals $\epsilon_{it}$
2. Regress residuals on contemporaneous and two lags of an FX index: $\epsilon_{it} = c_i + \gamma_{i1}(FX)_t + \gamma_{i2}(FX)_{t-1} + \gamma_{i3}(FX)_{t-2} + u_{it}$
3. $CURSENS = \gamma_{i1} + \gamma_{i2} + \gamma_{i3}$ (sum of slope coefficients)

---

## Portfolio Risk Decomposition in Practice

The MFM enables rich portfolio analytics. For any portfolio $p$ with active weights $h_{pA}$:

### Systematic Risk Budget

$$\psi_p^2 = \underbrace{h_{pA}^T X F X^T h_{pA}}_{\text{factor risk}} + \underbrace{h_{pA}^T \Delta h_{pA}}_{\text{specific risk}}$$

The factor risk can be further decomposed into contributions from each factor or group of factors (e.g., "how much tracking error comes from industry bets vs. style bets?").

### Risk-Adjusted Performance Attribution

Monthly portfolio return can be decomposed as:

$$r_p = \sum_{k=1}^{K} \left(\sum_{i} h_{pi} X_{ik}\right) f_k + \sum_{i} h_{pi} u_i$$

This separates return into factor timing (active factor exposures times factor returns) and stock selection (weighted specific returns). Over multiple periods, this decomposes into contributions from each of the 65 factors.

### Mean-Variance Optimization

Given expected excess returns $\alpha$, the optimizer maximizes:

$$U = h^T \alpha - \lambda \cdot h^T V h$$

subject to constraints. The risk model $V = XFX^T + \Delta$ is an essential input; its accuracy directly determines the quality of the optimized portfolio. Poor covariance estimates lead to portfolios that take unintended bets.

---

## Historical Context and Model Evolution

| Model | Year | Factors | Coverage | Key Innovation |
|---|---|---|---|---|
| US-E1 | 1975 | ~40 | ~1,000 | First commercial multi-factor model |
| US-E2 | Early 1980s | ~67 (55 ind + 12 risk) | ~1,500 | Added exponential weighting, more risk indices |
| **US-E3** | **1998** | **65 (52 ind + 13 risk)** | **~1,900** | **Momentum, multiple industry allocation, GARCH, three-component specific risk** |
| US-E4 (USE4) | 2011 | ~78 | ~5,000+ | Bayesian shrinkage, factor volatility regime switching |

BARRA (later acquired by MSCI) maintained backward compatibility: US-E3 factor returns are available from December 1972, enabling 25+ years of backtesting at the time of publication.

---

## Implications for Practice

1. **Covariance matrix quality matters more than alpha estimation.** The handbook emphasizes that poor risk models lead optimizers to load on unintended, noisy bets. The elaborate estimation pipeline (exponential weighting, GARCH overlay, specific risk decomposition) exists to produce a covariance matrix that is both responsive to regime changes and stable enough to avoid spurious turnover.

2. **Exponential weighting with a 90-month half-life is a deliberate compromise.** Shorter half-lives would make the model more responsive but introduce sampling noise (the 65x65 factor covariance matrix requires many observations for stable estimation). The GARCH overlay provides short-term responsiveness without destabilizing the correlation structure.

3. **Multiple industry allocation substantially improves conglomerate risk forecasts.** Forcing GE or Berkshire Hathaway into a single industry creates large specific risk residuals. Fractional industry memberships from Compustat segment data reduce these residuals and improve portfolio risk attribution accuracy.

4. **The NONESTU factor prevents contamination of factor return estimates** by non-estimation-universe stocks, which may have different return dynamics (illiquidity, information asymmetry). This is a practical solution to the tension between wanting a clean estimation sample and wanting broad model coverage.

5. **Specific risk is not purely idiosyncratic.** The three-component model ($S_t$, $V_{it}$, $\text{scale}_{it}$) reveals that specific risk has both a market-wide time-series component (rising after large market moves) and predictable cross-sectional variation based on observable characteristics. This has implications for how portfolio managers think about diversification.

6. **The asymmetric GARCH captures the leverage effect.** Negative market returns increase predicted volatility more than positive returns of the same magnitude, producing asymmetric risk forecasts. This means the model predicts higher risk after market declines, which aligns with empirical observations and is important for risk budgeting during drawdowns.

---

## Connections to Other Articles

- **[Cuffe -- Barra Market Factor](cuffe-barra-market-factor.md):** Analyzes how Barra models handle the market factor, which is implicit in US-E3's factor structure (the market portfolio's return is decomposed across industry and risk index factors rather than having a dedicated market factor).
- **[Menchero -- Factor Alignment Problems](menchero-factor-alignment.md):** Discusses factor alignment issues that can arise in models like US-E3 when factor exposures are correlated, leading to unstable factor return estimates; US-E3's GLS weighting and constraints are partial mitigants.
- **[Menchero -- Characteristics of Factor Portfolios](menchero-characteristics-factor-portfolios.md):** Extends the analysis of how factor portfolios (the minimum-risk unit-exposure portfolios whose returns are US-E3's factor returns) behave in practice.
- **[MSCI -- Foundations of Factor Investing](msci-foundations-of-factor-investing.md):** Provides the broader context for why the six style factors (value, momentum, size, quality, volatility, yield) identified in US-E3's risk indices also serve as investable return premia.
- **[Fama-French -- Factor Models](fama-french-factor-models.md):** The academic factor model tradition that parallels and informs Barra's commercial models; US-E3's risk indices overlap substantially with Fama-French factors (size, value, momentum).
- **[Frazzini-Pedersen -- Betting Against Beta](frazzini-pedersen-betting-against-beta.md):** The Volatility risk index in US-E3 captures beta and residual volatility characteristics that relate to the BAB phenomenon.
- **[Barbieri -- VaR with Factors](barbieri-var-with-factors.md):** Demonstrates how the factor covariance matrix from models like US-E3 can be used to construct VaR estimates, leveraging the same $V = XFX^T + \Delta$ decomposition.
- **[MSCI -- Risk and Return of Factor Portfolios](msci-risk-return-factor-portfolios.md):** Empirically evaluates the long-run risk-return characteristics of factor portfolios constructed from Barra-style models, providing evidence on the economic significance of the factors US-E3 identifies.
- **[Ehsani-Linnainmaa -- Factor Momentum](ehsani-linnainmaa-factor-momentum.md):** Factor momentum findings suggest US-E3's Momentum risk index captures a phenomenon that extends across all factors, not just stock-level momentum.

---

`tags: barra, risk-model, factor-model, covariance-estimation, GARCH, specific-risk, exponential-weighting, GLS-regression, industry-classification, US-equity, portfolio-optimization, estimation-universe, momentum, volatility, size, value, earnings-yield, leverage, USE3`
