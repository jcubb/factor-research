# Betting Against Beta

> Source: Frazzini, Andrea and Lasse Heje Pedersen. "Betting Against Beta." *Journal of Financial Economics* 111(1), 2014, pp. 1–25.
> DOI: 10.1016/j.jfineco.2013.10.005
> Affiliations: AQR Capital Management; NYU Stern; Copenhagen Business School; CEPR; NBER

## Overview

A basic tenet of the CAPM is that all investors should hold the tangency portfolio and lever or de-lever it to meet their risk preferences. But many real investors — mutual funds, pension funds, insurance companies, and retail investors — face binding leverage and margin constraints. Unable to lever, they tilt toward high-beta assets to achieve higher expected returns. This collective demand bids up high-beta assets and depresses their risk-adjusted returns.

Frazzini and Pedersen formalize this intuition in an overlapping-generations model where agents face heterogeneous margin constraints. The model generates a flat (or inverted) security market line: high-beta assets earn low alphas and low-beta assets earn high alphas. The signature strategy is the **BAB factor** — long leveraged low-beta assets, short de-leveraged high-beta assets — which earns a positive expected return in equilibrium.

The empirical evidence is striking in its breadth. BAB factors work in US equities (1926–2012), 19 international equity markets, US Treasury bonds, corporate bonds, and futures markets. A single economic mechanism — the tightness of funding constraints — provides a unified explanation across all asset classes and markets.

## The Model

### Setup

An overlapping-generations economy where agents i = 1, …, I are born each period with wealth W and live two periods. Agents trade S securities, maximizing mean-variance utility subject to a portfolio constraint:

$$\max \; x'(\mathbb{E}[P_{t+1} + \delta_{t+1}] - (1+r_f)P_t) - \frac{\gamma_i}{2} x'\Omega x$$

$$\text{subject to:} \quad m_i \sum_s (x_s \cdot P_s) \leq W_i$$

The constraint parameter m_i captures the investor's leverage limit:
- m_i = 1: cannot use leverage (no borrowing)
- m_i > 1: must hold cash fraction, e.g., m_i = 1.25 → 20% cash requirement
- m_i = 0.5: 50% margin requirement, can invest up to 2× wealth

### Equilibrium Pricing (Proposition 1)

The equilibrium required return for any security s is:

$$\mathbb{E}[r_s] = r_f + \psi_t + \beta_s \cdot \lambda_t$$

where:
- ψ_t = weighted average Lagrange multiplier across agents (measures funding constraint tightness)
- λ_t = E[r_M] − r_f − ψ_t (effective risk premium, flattened by constraints)

**Alpha relative to the market**:

$$\alpha_s = \psi_t \cdot (1 - \beta_s)$$

This is the key result: alpha *decreases* in beta. High-beta stocks have negative alpha; low-beta stocks have positive alpha. The alpha is proportional to ψ_t — when constraints are loose (ψ_t ≈ 0), the standard CAPM holds; when constraints bind tightly, the SML flattens dramatically.

### The BAB Factor Construction (Proposition 2)

The BAB factor is constructed to be market-neutral (beta = 0):

$$r_{\text{BAB}} = \frac{1}{\beta_L}(r_L - r_f) - \frac{1}{\beta_H}(r_H - r_f)$$

where:
- r_L = return on a portfolio of low-beta assets
- r_H = return on a portfolio of high-beta assets
- β_L, β_H = portfolio betas (both rescaled to one before differencing, making the portfolio market-neutral)

**Expected return** (Proposition 2):

$$\mathbb{E}[r_{\text{BAB}}] = \frac{\beta_H - \beta_L}{\beta_L \cdot \beta_H} \cdot \psi_t \geq 0$$

The BAB premium is increasing in: (1) the spread between high and low betas, and (2) the tightness of funding constraints ψ_t.

### Dynamic Predictions

**Proposition 3 (Funding shocks and BAB returns)**: When margin constraints tighten (higher m_k), BAB realizes a contemporaneous *loss* (forced de-leveraging of the long low-beta side) but its expected future return *rises*. This creates a time-series signature: BAB returns are negatively related to the TED spread contemporaneously.

**Proposition 4 (Beta compression)**: When funding liquidity risk rises, the dispersion of betas across securities is compressed toward one. A variance in the discount factor compresses betas, making the BAB portfolio's conditional beta drift positive (from zero).

**Proposition 5 (Constrained investors hold high betas)**: More constrained investors (higher ψ) tilt portfolios toward higher-beta assets. Less constrained investors tilt toward lower-beta assets, potentially applying leverage.

## Empirical Evidence

### Data

- **US equities**: all common stocks on CRSP, January 1926 – March 2012 (55,600+ stocks across 20 countries)
- **International equities**: 19 MSCI developed markets, January 1989 – March 2012
- **US Treasuries**: CRSP Treasury database, monthly returns
- **Corporate bonds**: portfolio-level data by rating and maturity
- **Futures**: equity indices, government bonds, commodities, and currencies

### Cross-Section of Betas (Proposition 1 Evidence)

For each asset class, portfolios are sorted by beta. In every asset class, the relationship between beta and alpha is flat or negative:

| Asset class | Observation |
|---|---|
| US equities | Alphas nearly monotonically decline with beta decile |
| 19 international equity markets | Same pattern in each country |
| US Treasuries | Short-duration (low-beta) bonds earn higher Sharpe ratios than long-duration |
| Corporate bonds | Higher-rated (lower-beta) corporate bonds earn more per unit of risk |
| Futures | BAB patterns hold across equity futures, bond futures, commodity futures, and FX |

### BAB Factor Performance (US Equities)

Beta estimation: rolling 1-year daily return regressions, then shrunk toward one using:

$$\beta_{\text{shrunk}} = 0.6 \cdot \beta_{\text{raw}} + 0.4 \cdot 1.0$$

**US BAB factor** (1926–March 2012):

| Metric | Value |
|---|---|
| Sharpe ratio | **0.78** |
| vs. value (HML) Sharpe | ~0.38 (BAB is ~2× HML) |
| vs. momentum (UMD) Sharpe | ~0.56 (BAB is ~40% higher) |
| Significant positive returns | All four 20-year subperiods |
| Alpha vs. 1-factor (CAPM) | Significant |
| Alpha vs. 3-factor (FF) | Significant |
| Alpha vs. 4-factor (Carhart) | Significant |
| Alpha vs. 5-factor | Significant |

The BAB Sharpe ratio of 0.78 is robust across subperiods and is not explained by exposure to size, value, momentum, or liquidity.

### International Equity BAB

| Market | Result |
|---|---|
| Combined non-US developed | Similar Sharpe to US BAB |
| Individual countries | Generally positive returns; statistically significant in most |

Results are consistent across countries, time, size deciles, and idiosyncratic risk deciles, making coincidence or data mining unlikely explanations.

### Bond Markets

**US Treasuries**: The BAB factor holds leveraged short-duration bonds and shorts de-leveraged long-duration bonds. Sharpe ratio ≈ **0.81** — slightly higher than the equity BAB. This is not a contradiction of the term premium: the BAB factor earns more *per unit of risk* from short-duration bonds than long-duration bonds, consistent with the model's prediction that leverage-constrained investors bid up high-beta (long-duration) bonds.

**Corporate bonds**: Leveraged investment-grade (high-rated, lower-beta) corporate bond portfolios outperform de-leveraged high-yield (lower-rated, higher-beta) portfolios on a risk-adjusted basis, consistent with the model.

### Time-Series Evidence (Proposition 3)

The TED spread (3-month LIBOR minus 3-month T-bill) proxies for funding conditions:

| Test | Finding |
|---|---|
| Contemporaneous TED spread ↑ | BAB returns negative (as constraints tighten, BAB loses) |
| Lagged TED spread | Predicts BAB negatively (possibly consistent with extended deleveraging) |
| TED spread volatility ↑ | Beta dispersion in cross-section narrows (compression toward 1, as in Proposition 4) |

### Investor Composition Evidence (Proposition 5)

| Investor type | Beta of holdings | Consistent with model? |
|---|---|---|
| Mutual funds (constrained) | Average beta > 1 | ✅ |
| Individual investors (constrained) | Average beta > 1 | ✅ |
| LBO funds (levered, unconstrained) | Average beta < 1 (applied leverage) | ✅ |
| Warren Buffett (Berkshire Hathaway) | Long low-beta stocks with leverage | ✅ |

Buffett's strategy — buying low-beta, high-quality stocks with corporate leverage — is a real-world implementation of the BAB idea.

## BAB vs. Low-Volatility Strategies

BAB is related to but distinct from simple low-volatility strategies:

| Feature | BAB factor | Low-volatility (simple) |
|---|---|---|
| Construction | Long low-beta, short high-beta; beta-neutral | Long low-vol stocks; long only |
| Market exposure | Zero (beta-neutral by design) | Positive (net long) |
| Beta rescaling | Yes (both sides rescaled to beta = 1) | No |
| Theoretical grounding | Leverage constraints model | Often atheoretical |
| Breadth | All asset classes | Typically equities |

## Connections to CAPM Theory

The paper's theoretical framework unifies several prior results:

| Prior work | BAB paper's contribution |
|---|---|
| Black (1972): restricted borrowing CAPM | Special case (m_i = 1 for all agents); BAB generalizes to heterogeneous, time-varying constraints |
| Black, Jensen, Scholes (1972): flat SML empirically | Confirmed and extended globally and across asset classes |
| Sharpe (1964)/Lintner (1965): standard CAPM | Special case of BAB model when ψ_t = 0 |
| Garleanu & Pedersen (2011): Margin CAPM | Complementary; BAB focuses on same margins across securities, Margin CAPM on cross-security margin differences |

## Implications for Practice

1. **Beta is not the right measure of risk for constrained investors**: If investors cannot lever, beta underestimates the true risk-adjusted cost of high-beta assets and overestimates it for low-beta assets. A flat or inverse SML is the equilibrium outcome.
2. **Low-beta / low-volatility strategies have a durable economic rationale**: The BAB premium is not a data-mining artifact — it exists in 20 equity markets, Treasury bonds, corporate bonds, and futures, all with the same sign. Its durability is linked to the persistently constrained investor base.
3. **BAB provides diversification to factor portfolios**: BAB alpha survives controlling for size, value, and momentum, so it adds genuine factor diversification to multi-factor strategies.
4. **Beware funding liquidity crises**: BAB strategies have a known failure mode. When funding liquidity tightens sharply (TED spread spikes — e.g., 2007–2008), BAB suffers contemporaneous losses as constrained investors are forced to de-leverage and sell low-beta positions. BAB is a funding liquidity risk factor itself.
5. **Beta compression near crises**: As BAB loses, betas compress toward one, reducing the effectiveness of beta-sorted portfolios. Strategies should account for this cyclicality (→ [[msci-foundations-of-factor-investing]]).
6. **Warren Buffett's alpha explained**: Buffett's strategy is essentially BAB — buying safe, high-quality low-beta stocks with corporate leverage. This explains much of Berkshire's apparent "alpha" as compensation for carrying a low-beta / safe-asset tilt with leverage.

## Connections

- [[fama-french-factor-models]] — FF (1992) documents the flat SML that motivates BAB. The 1993 three-factor model is the benchmark against which BAB alpha is measured; BAB alpha survives full four- and five-factor controls.
- [[msci-foundations-of-factor-investing]] — The MSCI Low Volatility factor overlaps with BAB conceptually. MSCI notes that low-vol strategies are cyclical and underperform in strong bull markets — this maps to BAB's time-varying premium (driven by ψ_t) and drawdowns in risk-on environments.
- [[ehsani-linnainmaa-factor-momentum]] — BAB is one of the factors in Ehsani & Linnainmaa's universe; factor momentum strategies can time the BAB factor when it exhibits autocorrelation.
- [[verdelhan-systematic-exchange-rates]] — Verdelhan's dollar factor can be viewed as related to BAB across currencies: high-interest-rate (higher-beta) currency portfolios earn lower risk-adjusted returns, consistent with a leverage-constrained demand for "carry" assets.

#betting-against-beta #bab #low-beta #leverage-constraints #funding-liquidity #frazzini-pedersen #security-market-line #capm #factor-models #low-volatility #international
