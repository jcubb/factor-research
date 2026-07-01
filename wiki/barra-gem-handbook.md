# Barra Global Equity Model (GEM) Risk Model Handbook

> Source: BARRA, Inc. "Global Equity Risk Model Handbook." BARRA, 1998.
> Affiliations: BARRA, Inc. (now MSCI Barra)

## Overview

The Barra Global Equity Model (GEM) is a multiple-factor risk model designed to analyze international portfolios of equity and currency holdings. Initially released in January 1989, GEM extends the conceptual principles of Barra's single-country equity models (such as the U.S. Equity Model) to the global equity market. The model decomposes asset returns into systematic components -- country, industry, and style (risk index) factors -- plus an asset-specific residual, enabling investors to predict risk, attribute returns, and construct optimized portfolios across dozens of markets simultaneously.

GEM comes in two versions: GEM-MSCI, which uses Morgan Stanley Capital International World Index (MSWLD) local markets and industry classifications, and GEM-FT, which uses Financial Times-Actuaries World Index (FTWLD) classifications. As of March 1998, GEM-MSCI contains 90 common factors (48 local markets, 38 industries, 4 risk indices) plus 46 currencies, while GEM-FT contains 93 common factors (51 local markets, 36 industries, 4 risk indices) plus 51 currencies. The factor covariance matrix reduces the dimensionality problem from over 1.28 million pairwise covariances (for 1,600 assets) to roughly 4,095 factor covariance terms.

The handbook serves as a technical reference covering the theoretical foundations of multiple-factor models, the structure of GEM's factor taxonomy, the estimation methodology (cross-sectional regressions, exponential weighting, GARCH scaling), and practical portfolio management applications including passive indexing, active tilts, and optimization case studies.

## Return Decomposition

GEM decomposes total return from the investor's numeraire perspective into a layered hierarchy:

```
Total Return (Numeraire) = Risk-Free Return (Numeraire) + Excess Return (Numeraire)

Excess Return = Local Excess Return + Currency Return

Local Excess Return = Country Return + Industry Return + Risk Index Return + Specific Return
```

The numeraire is the currency perspective of the investor (typically the investor's domicile currency). Currency return is separated from local excess return because it involves distinct risk sources -- exchange rate movements plus risk-free rate differentials.

### Compounding and linearization

The exact relationship between numeraire return, local return, and exchange rate return is multiplicative:

$1 + r = (1 + r_x)(1 + r_l)$ (EQ 1-4)

where $r$ = numeraire return, $r_x$ = exchange rate return, $r_l$ = local asset return. GEM linearizes by dropping the cross-product terms $(r_x \cdot r_l)$ and $(r_{fl} \cdot r_x)$, which are typically negligible at monthly frequency, yielding:

$1 + r \approx 1 + r_x + r_l$

and:

$\text{Currency Return} = r_x + r_{fl} - r_f$

where $r_{fl}$ = local risk-free rate and $r_f$ = numeraire risk-free rate.

## The GEM Factor Model Equation

### GEM-MSCI

$$R_l(n) - R_{fl}(n) = \underbrace{\sum_{k=1}^{46} b(n,k)\,h(k)}_{\text{country factors}} + \underbrace{\sum_{j=1}^{38} y(n,j)\,g(j)}_{\text{industry factors}} + \underbrace{\sum_{i=1}^{4} z(n,i)\,q(i)}_{\text{risk indices}} + e(n)$$

### GEM-FT

$$R_l(n) - R_{fl}(n) = \sum_{k=1}^{51} b(n,k)\,h(k) + \sum_{j=1}^{36} y(n,j)\,g(j) + \sum_{i=1}^{4} z(n,i)\,q(i) + e(n)$$

| Symbol | Meaning |
|--------|---------|
| $R_l(n)$ | Local return to asset n |
| $R_{fl}(n)$ | Local risk-free rate in country of asset n |
| $b(n,k)$ | Asset n's exposure to country factor k |
| $y(n,j)$ | Asset n's exposure to industry factor j |
| $z(n,i)$ | Asset n's exposure to risk index i |
| $h(k)$ | Return to country factor k |
| $g(j)$ | Return to industry factor j |
| $q(i)$ | Return to risk index i |
| $e(n)$ | Specific return to asset n |

## Risk Indices (Style Factors)

GEM uses four global risk indices (style factors) that quantify common characteristics across companies. Each is normalized within local markets: the capitalization-weighted mean is set to zero and one unit equals one cross-sectional equal-weighted standard deviation.

| Risk Index | Description | Underlying Descriptors |
|------------|-------------|----------------------|
| **Size** (SIZE) | Differentiates large vs. small companies | $\text{Size} = \ln(\text{shares outstanding} \times \text{price per share})$ |
| **Success** (SUCCESS) | Identifies recently successful stocks via relative strength / momentum | $\text{Success} = \sum_{i=1}^{12} \ln(1 + r_{l,-i}) - \sum_{i=1}^{12} \ln(1 + r_{fl,-i})$ (cumulative 12-month local excess return) |
| **Value** (VALUE) | Captures cheapness / value orientation | Four descriptors: (i) Forecast E/P = IBES FY1 EPS / price; (ii) Reported E/P = income before extraordinary items / (shares × price); (iii) Reported B/P = common equity / market cap; (iv) Yield = predicted annual dividend / price |
| **Variability in Markets** (VIM) | Predicts residual volatility net of the market | $\text{VIM} = \sigma_\epsilon$, the standard deviation of the residual from the market model regression: $r_l - r_{fl} = \alpha + \beta(r_m - r_{fl}) + \epsilon$ |

### Standardization procedure

$$\text{Normalized Risk Index} = \frac{\text{Raw Data} - \text{Capitalization-weighted Mean}}{\text{Equal-weighted Standard Deviation}}$$

- Computed within each local market separately
- Winsorization at +/-4 standard deviations (values between 4 and 10 are truncated to +/-4; values beyond 10 are eliminated)
- Missing values are set to zero

### Risk index inclusion criteria

A risk index is included in GEM if it satisfies at least one of:
1. It forecasts beta
2. It identifies historical sources of exceptional return (alpha)
3. It measures a source of residual volatility

## Factor Taxonomy: Countries, Industries, Currencies

### Local markets

Local market effects explain more portfolio risk than industry effects in GEM. Country exposures are computed by multiplying the portfolio's weight within each market by the local market factor -- a statistically-manipulated version of historical beta derived from asset-specific information. Unlike currency exposures, local market exposures are not simple percentage weights.

| Dimension | GEM-MSCI | GEM-FT |
|-----------|----------|--------|
| Local markets | 48 (as of March 1998) | 51 |
| Industries | 38 (Morgan Stanley categories) | 36 (Financial Times categories) |
| Currencies | 46 | 51 |
| Risk indices | 4 (Size, Success, Value, VIM) | 4 (same) |
| **Total common factors** | **90** (excl. currencies) | **93** (excl. currencies) |

GEM-MSCI regions: Americas, Europe, Europe/Australia/Far East, Far East, Mideast/Africa, Pacific Rim. GEM-FT regions: Asia, Europe, Latin America, North America, Pacific Basin.

### GEM-MSCI local markets (48 as of March 1998)

Argentina, Australia, Austria, Belgium, Brazil, Canada, Chile, China, Colombia, Czech Republic, Denmark, Finland, France, Germany, Greece, Hong Kong, Hungary, India, Indonesia, Ireland, Israel, Italy, Japan, Jordan, Korea, Malaysia, Mexico, Netherlands, New Zealand, Norway, Pakistan, Peru, Philippines, Poland, Portugal, Russia, Singapore, South Africa, Spain, Sri Lanka, Sweden, Switzerland, Taiwan, Thailand, Turkey, United Kingdom, United States, Venezuela.

### GEM-MSCI industries (38)

Energy Sources; Utilities--Electrical & Gas; Building Materials & Components; Chemicals; Forestry & Paper Products; Metals--Non-Ferrous; Metals--Steel; Miscellaneous Materials & Commodities; Aerospace & Military Technology; Construction & Housing; Data Processing & Reproduction; Electrical & Electronics; Electronic Components & Instruments; Energy Equipment & Services; Industrial Components; Machinery & Engineering; Appliances & Household Durables; Automobiles; Beverages & Tobacco; Food & Household Products; Health & Personal Care; Recreation; Textiles & Apparel; Broadcasting & Publishing; Business & Public Services; Leisure & Tourism; Merchandising; Telecommunications; Transportation--Airlines; Transportation--Road & Rail; Transportation--Shipping; Wholesale & International Trade; Banking; Financial Services; Insurance; Real Estate; Multi-Industry; Gold Mines.

### Economic sectors

Industries are aggregated into 7-8 economic sectors:

| MSCI Sectors | FT Sectors |
|-------------|-----------|
| Energy | Financing, Insurance, & Real Estate |
| Materials | Energy |
| Capital Equipment | Utilities |
| Consumer Goods | Transportation & Storage |
| Services | Consumer Goods/Services |
| Finance | Capital Goods |
| Multi-Industry | Basic Industry |
| Gold Mines | |

### Currencies

- GEM-MSCI: 46 currencies; GEM-FT: 51 currencies
- Argentinian and Brazilian currencies are excluded due to extreme historical volatility; assets in those countries are valued in U.S. dollars
- Currency risk exposures are percentage weights of holdings in each country

## Model Estimation Methodology

The estimation process follows nine sequential steps:

| Step | Description |
|------|-------------|
| 1. Data acquisition & cleaning | Market data (price, dividend yield, capitalization), capital restructurings, atypical events |
| 2. Risk index formulation | Compute and normalize four risk indices within each local market |
| 3. Industry definition | Map each security to one MSCI or FT industry classification |
| 4. Local market selection | Assign country membership from the estimation universe (MSWLD or FTWLD) |
| 5. Factor return estimation | Monthly cross-sectional weighted regressions |
| 6. Covariance matrix calculation | Exponential weighting + GARCH scaling |
| 7. Currency risk estimation | Independent currency volatility/correlation estimation added to covariance matrix |
| 8. Specific risk forecasting | Separate model for idiosyncratic risk |
| 9. Model testing | Ex ante and ex post evaluations of beta, specific risk, and active risk |

### Factor return estimation

Factor returns are estimated via monthly cross-sectional regression of asset excess returns on their factor exposures:

$r_t = X_t f_t + u_t$ (EQ 4-1)

where $r_t$ = vector of excess returns, $X_t$ = exposure matrix, $f_t$ = factor returns to be estimated, $u_t$ = specific returns. The regression is weighted by the square root of capitalization.

### Covariance matrix calculation

The asset covariance matrix is decomposed via the fundamental factor model equation:

$V = X F X^T + \Delta$ (EQ 2-8)

where $X$ = exposure matrix, $F$ = factor covariance matrix, $X^T$ = transpose of $X$, and $\Delta$ = diagonal matrix of specific risk variances.

#### Exponential weighting

The factor covariance matrix uses exponentially declining weights to give more importance to recent observations:

$\delta = (0.5)^{1/\text{HALF-LIFE}}$ (EQ 4-2)

$w(t) = \delta^{T-t}$ (EQ 4-3)

where $T$ is the current period and $t$ is the observation period. An observation HALF-LIFE months ago receives half the weight of the current observation.

| Component | Half-Life |
|-----------|-----------|
| Factor correlation matrix | 48 months |
| Volatility forecasts (local market, industry, risk factors) | 48 months (default) |
| Selected markets (AUS, CAN, KOR, SAF, TAI, THA, UKI) | Match single-country model half-lives |

Equal weighting of all observations corresponds to HALF-LIFE = ∞. Too short a half-life discards useful data from the beginning of the series and reduces estimation precision.

#### GARCH(1,1) volatility scaling

GEM uses GARCH models to capture time-varying market volatility:

$r_t = \mathbb{E}(r_t) + \epsilon_t$ (EQ 4-4)

$$\text{Var}(r_m)_t = \omega + \alpha \cdot \epsilon_{t-1}^{2} + \beta \cdot \text{Var}(r_m)_{t-1}$$ (EQ 4-5)

This GARCH(1,1) specification says current market volatility depends on recent realized volatility (via $\epsilon_{t-1}^2$) and recent forecast volatility (via $\text{Var}(r_m)_{t-1}$). If $\alpha$ and $\beta$ are positive, volatility increases with recent realized and forecast volatility (volatility clustering).

GARCH is applied to:
- **Equity markets**: Japanese, Swedish, and U.S. local market factors
- **Currency factors**: Some currency factors use GARCH on daily returns from the BARRA Cosmos global bond model
- GARCH parameters are incorporated only when they produce significant improvements to the model

The fitted GARCH volatility is used to scale the local market factor in the covariance matrix, producing comparable volatility forecasts to single-country models.

### Currency risk estimation

Currency return is computed as:

$\text{Currency Return} = r_x + r_{fl} - r_f$

where $r_x$ = exchange rate return, $r_{fl}$ = local risk-free rate, $r_f$ = numeraire risk-free return. Currency volatilities and correlations are calculated independently and then added to the factor covariance matrix.

### Specific risk estimation

Specific risk is independent of factor returns and is estimated using a separate model. It captures the portion of total risk related solely to a particular stock's idiosyncratic behavior. The greater an asset's specific risk, the larger the proportion of return attributable to company-specific influences rather than common factors.

## Differences Between GEM and US-Specific Models

| Feature | GEM | US Single-Country Models (e.g., USE3/USE4) |
|---------|-----|-------------------------------------------|
| Scope | Global (48-51 markets, 36-38 industries, 46-51 currencies) | Single market |
| Country factors | Explicit local market factors with beta-derived exposures | Single implicit market factor |
| Currency | Separate currency covariance model added to equity covariance | Not applicable (single currency) |
| Risk indices | 4 global indices (Size, Success, Value, VIM) | 13 descriptors (USE3) or more (USE4), including Momentum, Leverage, Earnings Variability, etc. |
| Industry classification | 38 (MSCI) or 36 (FT) global industries | ~55 industries (USE3/USE4) |
| Half-lives | 48-month default for correlations/volatilities; per-market overrides | Model-specific; USE4 uses differential half-lives per descriptor |
| GARCH | Applied to selected local market factors (JPN, SWE, USA) and some currencies | Market factor GARCH in USE4 |
| Cross-sectional regression | Monthly, sqrt(cap)-weighted, across global estimation universe | Monthly, within single market |
| Estimation universe | MSWLD (MSCI version) or FTWLD (FT version) | US-listed equities |

## Portfolio Management Applications

### Risk decomposition

GEM decomposes portfolio risk into:
- **Active residual specific risk** -- idiosyncratic stock selection risk
- **Active residual common factor risk** -- risk from factor bets (risk indices, industries, countries, currencies)
- **Active systematic risk** -- beta-related risk
- **Benchmark risk** -- risk of the benchmark itself

### Case study results (from handbook)

| Case Study | Description | Active Risk (Std. Dev.) | Key Findings |
|-----------|-------------|------------------------|--------------|
| CASE1 | Active portfolio vs. MSEAFE | 6.09% | Country bets dominate (4.88%); total risk (15.87%) lower than benchmark (17.25%) |
| CASE2 | 250-stock MSEAFE tracker | 0.64% | Very low tracking error; specific risk (0.57%) is largest component |
| CASE3 | Tilt fund (small/success/low-VIM) | 6.79% | Risk index bets (4.41%) + country risk (4.50%) dominate; specific risk controlled at 2.65% |

## Risk Index Cumulative Return Patterns (Dec 1987 -- Dec 1997)

From the appendix factor return charts:

| Risk Index | Cumulative Return Pattern |
|-----------|--------------------------|
| **Size** | Negative trend overall (-12% cumulative); small-cap underperformance globally over the decade |
| **Success** | Highly cyclical; negative through early 1990s, strong positive trend from ~1995 onward (+5% by end) |
| **Value** | Strong persistent positive trend (~+23% cumulative); value premium clearly visible globally |
| **VIM** | Persistently negative (~-5% cumulative); high-volatility stocks underperform after controlling for other factors |

## Implications for Practice

1. **Country allocation dominates global equity risk.** In GEM, local market effects explain more portfolio risk than industry classification. For active global portfolios, unintended country bets are the primary source of tracking error and must be actively monitored.

2. **Four style factors capture global equity risk premia.** Size, Success (momentum), Value, and Variability in Markets are the cross-market style factors that survive global statistical testing. The 10-year sample shows persistent value premium and negative VIM (volatility) premium globally.

3. **Exponential weighting with 48-month half-life balances responsiveness and stability.** The correlation matrix uses a 48-month half-life by default, but selected markets (AUS, CAN, KOR, SAF, TAI, THA, UKI) use half-lives matched to their single-country models, acknowledging that the optimal decay rate is market-dependent.

4. **GARCH scaling is applied selectively, not universally.** Only the Japanese, Swedish, and U.S. equity markets (and some currency factors) receive GARCH volatility adjustment. GARCH parameters are incorporated only when they produce statistically significant improvements.

5. **Currency risk is modeled separately and additively.** Currency volatilities and correlations are estimated independently from equity factors and added to the covariance matrix. This separation allows differential treatment of currency hedging decisions.

6. **The factor model dramatically reduces estimation dimensionality.** From ~1.28 million pairwise covariances (1,600 assets), the 90-factor GEM-MSCI reduces estimation to ~4,095 factor covariances, enabling more precise parameter estimates with shorter time series.

7. **Risk index standardization is performed within each local market.** Normalization subtracts the capitalization-weighted mean and divides by the equal-weighted standard deviation within each country. This ensures that style exposures capture within-market characteristics rather than cross-market level differences.

8. **Winsorization at +/-4 standard deviations limits outlier influence.** Exposures between 4 and 10 are truncated; beyond 10 are eliminated entirely. This prevents extreme observations from distorting factor return estimates.

9. **Index tracking with 250 stocks can achieve sub-1% tracking error.** The MSEAFE tracking case achieves 0.64% annual tracking error, demonstrating that the factor model efficiently captures systematic risk with far fewer securities than the benchmark (250 vs. 1,500+).

10. **The model supports active strategy design via factor alphas.** By assigning expected returns (alphas) to risk index factors and optimizing, managers can construct efficient tilt portfolios that maximize style exposure while controlling incidental country and industry bets.

## Connections

- [[barra-use3-handbook]] -- GEM is the global extension of the same Barra MFM framework; uses 4 risk indices vs. USE3's 13 descriptors; shared concepts of cross-sectional regression and exponential weighting
- [[cuffe-barra-market-factor]] -- GEM uses country-specific local market factors analogous to USE4's explicit market factor; GARCH scaling of market factors in both models
- [[menchero-characteristics-factor-portfolios]] -- GEM-MSCI's 38 industries and 4 risk indices follow the same simple/pure factor portfolio methodology; GEM2 style factors referenced in that paper build on GEM's architecture
- [[barbieri-var-with-factors]] -- GEM's factor covariance matrix is the direct input for the DFR method's VaR calculations; the same exponential weighting and GARCH approach applies
- [[menchero-factor-alignment]] -- GEM's choice of 4 risk indices reflects the factor alignment problem: including too many correlated style factors is costly; the parsimonious global set avoids the 6x asymmetric penalty of spurious factors
- [[msci-foundations-of-factor-investing]] -- GEM's Value, Size, and Success (momentum) factors are three of the six equity risk premia identified in the MSCI foundations paper; GEM provides the risk model infrastructure for harvesting these premia
- [[fama-french-factor-models]] -- GEM's Size and Value factors parallel FF HML and SMB; Success parallels the momentum factor added in Carhart (1997); GEM operationalizes these in a global, multi-country setting
- [[frazzini-pedersen-betting-against-beta]] -- GEM's VIM factor (residual volatility) is related to the BAB finding that high-beta/high-volatility stocks underperform; VIM shows persistent negative cumulative returns globally

#barra #gem #global-equity #risk-model #factor-model #covariance #garch #exponential-weighting #style-factors #size #value #momentum #volatility #country-risk #currency-risk #industry-factors #cross-sectional-regression #portfolio-construction #msci #tracking-error
