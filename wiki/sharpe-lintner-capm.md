# The Capital Asset Pricing Model (Sharpe 1964, Lintner 1965)

> Source: Sharpe, William F. "Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk." *Journal of Finance* 19(3), September 1964, pp. 425–442.
> Source: Lintner, John. "The Valuation of Risk Assets and the Selection of Risky Investments in Stock Portfolios and Capital Budgets." *Review of Economics and Statistics* 47(1), February 1965, pp. 13–37.
> Related: Mossin (1966); Black (1972) zero-beta extension; Treynor (unpublished, ~1962).
> Status: foundational baseline — compiled from established knowledge (no raw PDF in `raw/`).

The CAPM is the single-factor model that every other article in this wiki is defined *against*. "Alpha," "beta," the "flat security market line," "the market factor," and "risk-adjusted return" all inherit their meaning from here. Fama-French (1992) is a refutation of its empirical predictions; Betting-Against-Beta is an explanation of *why* it fails; the entire multi-factor literature exists because one factor turned out not to be enough. Reading the rest of the KB without this baseline is like reading the critiques of a theory you have never seen stated.

## Overview

Building on Markowitz's (1952) mean-variance portfolio theory, Sharpe and Lintner independently derived the first equilibrium model of asset prices. Markowitz told a single investor how to trade off risk and return; the CAPM asks what happens to prices when *every* investor optimizes that way simultaneously. The answer is startlingly clean: in equilibrium, the only risk that earns a premium is **covariance with the market portfolio**, and the expected excess return on any asset is strictly proportional to that covariance.

The model's central equation — the Security Market Line — states that for any asset $i$:

$$E[R_i] - R_f = \beta_i\left(E[R_m] - R_f\right), \qquad \beta_i = \frac{\operatorname{Cov}(R_i, R_m)}{\operatorname{Var}(R_m)}$$

Everything else an asset might do — its total volatility, its skewness, its industry, its idiosyncratic swings — is irrelevant to its expected return, because a diversified investor can hold it alongside everything else and wash the idiosyncratic part out. Only the undiversifiable part, $\beta_i$, is priced.

Two results make the model economically powerful: the **two-fund separation theorem** (everyone holds the same risky portfolio — the market — levered up or down with the riskless asset to taste) and the sharp split of risk into a **priced systematic** component and an **unpriced specific** component. That split is the conceptual seed of every factor risk model in this KB (→ [[barra-use3-handbook]]).

## The Assumptions

The CAPM's clean conclusion is bought with strong assumptions. Knowing them is knowing exactly where the later literature attacks.

| Assumption | What it says | Which later paper breaks it |
|---|---|---|
| Mean-variance preferences | Investors care only about portfolio mean and variance (one period) | — |
| Homogeneous expectations | Everyone agrees on means, variances, covariances | Behavioral factor stories |
| Frictionless, competitive markets | No taxes, no transaction costs, price-takers, all assets divisible & marketable | Cohen-Frazzini (limited attention), construction-cost papers |
| **Unrestricted riskless borrowing/lending at $R_f$** | Any investor can lever at the T-bill rate | **[[frazzini-pedersen-betting-against-beta]]** (leverage constraints) |
| Single period, no intertemporal hedging | No multi-period rebalancing motives | Merton ICAPM, factor-timing papers |

The leverage assumption is the load-bearing one for this KB: Frazzini & Pedersen show that *relaxing it alone* — letting some investors be unable to borrow — bends the clean SML into the flat line that Fama-French measured, and generates the BAB factor.

## The Geometry: CML vs. SML

Two lines come out of the model and are routinely confused.

**Capital Market Line (CML)** — applies only to *efficient* portfolios (combinations of the riskless asset and the market). It prices total risk $\sigma_p$:

$$E[R_p] = R_f + \frac{E[R_m] - R_f}{\sigma_m}\,\sigma_p$$

The slope $\tfrac{E[R_m]-R_f}{\sigma_m}$ is the market **Sharpe ratio** — the price of a unit of risk for an efficiently diversified holder.

**Security Market Line (SML)** — applies to *every* asset and portfolio, efficient or not. It prices only the systematic part, $\beta_i$. An inefficient asset sits *on* the SML (correctly priced for its beta) but *below* the CML (penalized for carrying diversifiable risk it isn't paid for). The difference between the two lines is the whole argument for diversification.

## Decomposing Risk — the Origin of "Specific Risk"

Regressing an asset's return on the market gives the CAPM's risk split:

$$\underbrace{\sigma_i^2}_{\text{total}} = \underbrace{\beta_i^2\,\sigma_m^2}_{\text{systematic}} + \underbrace{\sigma_{\varepsilon_i}^2}_{\text{specific / idiosyncratic}}$$

Systematic risk is compensated; specific risk is not, because it vanishes in a large portfolio ($\tfrac{1}{N}\!\sum$ idiosyncratic variance $\to 0$). Multi-factor risk models generalize exactly this equation — they replace the single $\beta_i\sigma_m$ term with a sum over many factor exposures, keeping the same systematic-vs-specific architecture (→ [[barra-use3-handbook]], → [[harmsworth-idiosyncratic-alpha]] for the modern "idiosyncratic alpha" reading of the specific term).

## Alpha and the Testing Regressions

The empirical CAPM is the time-series regression

$$R_i - R_f = \alpha_i + \beta_i (R_m - R_f) + \varepsilon_i.$$

The model's sharp prediction is $\alpha_i = 0$ for every asset: there should be *no* return the market factor cannot explain. A non-zero $\alpha$ is "abnormal return" — the quantity active managers claim and the quantity the rest of this KB spends its time re-measuring against better models. **This is where the word "alpha" comes from.** Jensen (1968) introduced $\alpha$ as exactly this intercept to evaluate mutual funds — the direct ancestor of [[fama-french-luck-vs-skill]] and [[harmsworth-idiosyncratic-alpha]].

Two classic test methodologies, both used throughout the KB:
- **Black-Jensen-Scholes (1972)** time-series test on beta-sorted portfolios.
- **Fama-MacBeth (1973)** cross-sectional regressions, period by period — the exact procedure FF (1992) later turns against the model, and the estimation backbone of the Barra cross-sectional approach.

## Why the CAPM Fails Empirically — the Bridge to the Rest of the KB

The data did not cooperate, and the specific pattern of failure defines the factor literature:

1. **The SML is too flat.** Realized returns rise with beta far less steeply than predicted, and the fitted line has a *positive intercept* (low-beta assets out-earn their CAPM prediction, high-beta assets under-earn). Black-Jensen-Scholes (1972) found this first; FF (1992) made it decisive (→ [[fama-french-factor-models]]); Frazzini & Pedersen (2014) explained it and monetized it as **BAB** (→ [[frazzini-pedersen-betting-against-beta]]).
2. **Characteristics beat beta.** Size, book-to-market, profitability, investment, and momentum all predict returns *after* controlling for beta — the "factor zoo" that CAPM says should not exist.
3. **Roll's critique (1977).** The true market portfolio (all wealth, including human capital and non-traded assets) is unobservable, so the CAPM is arguably untestable — any test is a joint test of the model and the market proxy. This caveat shadows every empirical "market factor" in the Barra papers.

The response was not to abandon the framework but to add factors — keeping the systematic/specific split, the regression-intercept definition of alpha, and the mean-variance machinery, while admitting that *one* source of priced risk was too few.

## Implications for Practice

1. **Beta is the null, not the answer.** Treat a one-factor CAPM alpha as a red flag, not a result: it almost always reflects uncompensated size/value/momentum tilts, not skill. FF (2010) show CAPM benchmarking spuriously manufactures manager "skill" (→ [[fama-french-luck-vs-skill]]).
2. **Diversifiable risk is free risk you shouldn't take.** The CML-vs-SML gap means an undiversified portfolio bears specific risk it is not paid for. This is the economic case for broad factor portfolios.
3. **"Alpha" and "beta" are model-relative.** Every alpha number in finance is implicitly "alpha *with respect to this factor model*." Upgrading the model (CAPM → FF3 → FF5 → Barra) reclassifies yesterday's alpha as today's beta. This is the recurring plot of the whole KB.
4. **The leverage assumption is a real-world lever.** Because few investors can borrow freely at $R_f$, demand tilts toward high-beta assets and the SML flattens — the mechanism to exploit via low-beta / BAB strategies.
5. **Market-proxy choice matters (Roll).** Any practical risk model substitutes an index for the unobservable market; conclusions are conditional on that proxy.

## Connections

- [[fama-french-factor-models]] — FF (1992) is the canonical empirical refutation: with size and B/M in the regression, the CAPM beta has a flat, insignificant slope. FF (1993) replaces the single market factor with three.
- [[frazzini-pedersen-betting-against-beta]] — Relaxes the CAPM's unrestricted-borrowing assumption; derives the flat SML as an equilibrium with leverage-constrained investors and builds the BAB factor to exploit it.
- [[barra-use3-handbook]] — Generalizes the CAPM's systematic/specific risk split from one factor to dozens; the commercial realization of the same risk-decomposition idea.
- [[fama-french-luck-vs-skill]] — Uses the CAPM-vs-multifactor contrast to show single-factor benchmarking overstates fund skill; Jensen's CAPM alpha is the starting point it improves on.
- [[harmsworth-idiosyncratic-alpha]] — Modern reframing of the CAPM's unpriced "specific" term as the *valuable* part of active return once commoditized betas are stripped out.
- [[spruyt-geometric-covariance-matrix]] — The mean-variance machinery underneath the CAPM runs on exactly the covariance geometry developed here.

#capm #sharpe #lintner #beta #market-factor #security-market-line #capital-market-line #systematic-risk #specific-risk #alpha #mean-variance #equilibrium #asset-pricing #foundational
