# On Persistence in Mutual Fund Performance (Carhart 1997)

> Source: Carhart, Mark M. "On Persistence in Mutual Fund Performance." *Journal of Finance* 52(1), March 1997, pp. 57–82.
> Status: foundational benchmark — the origin of the "four-factor (Carhart) model." Compiled from established knowledge (no raw PDF in `raw/`).

Carhart (1997) is cited more often in this KB for its *model* than for its *result*. The paper adds a momentum factor (PR1YR, built from Jegadeesh-Titman → [[jegadeesh-titman-momentum]]) to the Fama-French three-factor model (→ [[fama-french-factor-models]]), creating the **four-factor model** that became the default benchmark for evaluating active performance. When the other articles here write "four-factor alpha" or "Carhart MOM" — [[frazzini-pedersen-betting-against-beta]], [[cohen-frazzini-economic-links]], [[fama-french-luck-vs-skill]], [[houweling-vanzundert-factor-investing-corporate-bonds]], [[barra-gem-handbook]] — this is the paper they mean.

## Overview

Carhart asks whether mutual fund outperformance *persists* — whether last year's winning funds keep winning. Earlier work (Hendricks, Patel & Zeckhauser's "hot hands") had found short-run persistence and read it as evidence of manager skill. Carhart's contribution is to show that **almost all of this persistence is mechanical, not skill**: it disappears once you control for the momentum factor and fund costs.

The logic: funds that happened to hold last year's winning *stocks* post good returns this year simply because those stocks have momentum — the fund didn't skillfully pick them, it passively rode the momentum factor. Control for momentum and the persistence of the *winners* evaporates. What remains is persistence at the **bottom**: the worst funds reliably stay worst, driven by high expense ratios and transaction costs. Skill, in the sense of repeatable positive alpha, is essentially absent — a conclusion later sharpened by Fama & French (2010) with bootstrap methods (→ [[fama-french-luck-vs-skill]]).

Using a **survivorship-bias-free** sample of diversified US equity funds, 1962–1993, the paper's enduring legacy is methodological: the four-factor model it introduced to *do* this test is now the field's standard performance yardstick.

## The Four-Factor Model

$$R_{it} - R_{ft} = \alpha_i + b_i\,\text{RMRF}_t + s_i\,\text{SMB}_t + h_i\,\text{HML}_t + p_i\,\text{PR1YR}_t + \varepsilon_{it}$$

| Factor | Source | What it captures |
|---|---|---|
| RMRF | Market excess return | CAPM market factor (→ [[sharpe-lintner-capm]]) |
| SMB | Fama-French | Size |
| HML | Fama-French | Value (book-to-market) |
| **PR1YR** | **Carhart (new)** | **Momentum** |

**PR1YR construction**: equal-weighted average return of the top 30% of stocks on prior 11-month return (lagged one month) minus the bottom 30%, rebalanced monthly. It is a direct operationalization of Jegadeesh-Titman relative strength as a tradable factor. Carhart is careful to present the four factors as a *performance-attribution* model — a parsimonious set of passive benchmark strategies — rather than a claim about equilibrium risk pricing.

## Key Empirical Results

### The 1%-per-year sort

Ranking funds into deciles on prior-year return and holding one year, the spread between the top and bottom decile is about **8% per year**. Carhart decomposes where it comes from:

| Source of the top-minus-bottom-decile spread | Approx. contribution |
|---|---|
| **One-year momentum (PR1YR exposure)** | ~4.6% |
| Expense ratio differences | ~0.7% |
| Size/value (SMB, HML) exposure | ~0.7% |
| **Unexplained (true persistent alpha)** | ~small / mostly in worst decile |

The great majority of "hot-hands" persistence is momentum exposure that funds acquire passively, not stock-picking skill.

### Costs destroy returns, one-for-one

Carhart's cross-sectional cost findings are as influential as the factor model:

- **Expense ratio**: roughly −1 for −1. Each 1% of expense ratio reduces net return by about 1%.
- **Turnover**: about −0.95% of return for each 1% of turnover (trading costs are real and roughly linear).
- **Load fees**: load funds underperform no-load funds.

The only robust persistence is the **worst funds staying worst** — a cost phenomenon, not negative skill.

### After four-factor adjustment

Fund four-factor alphas are, on average, **negative** and close to minus the expense ratio. The representative actively managed equity fund roughly earns back its gross costs before fees and then loses the fee — it does not add value net of the four passive factors. This is the quantitative setup for the manager-skill debate that [[fama-french-luck-vs-skill]] and [[harmsworth-idiosyncratic-alpha]] continue.

## Why This Model Became the Standard

- **It plugs the biggest hole in FF3.** Fama-French deliberately omit momentum, yet momentum is large, pervasive, and strongly loaded by many real portfolios. Judging a momentum-tilted strategy on FF3 mislabels its momentum exposure as alpha. The Carhart model closes that gap with one factor.
- **It is the minimal "honest" benchmark.** Four factors span market, size, value, and momentum — the exposures a low-cost passive investor can replicate — so any surviving alpha is a cleaner claim to skill.
- **It is parsimonious and tradable.** Each factor is a transparent long-short portfolio, keeping attribution interpretable.

Its limits matter too: it predates profitability and investment (RMW, CMA → [[fama-french-factor-models]]), so a "Carhart alpha" can still be quality/investment exposure in disguise. Lee & Menchero's alignment work (→ [[menchero-factor-alignment]]) is the caution that bolting factors onto a model is asymmetrically risky — a reason the four-factor model is a *benchmark convention*, not a claimed true risk model.

## Implications for Practice

1. **Use four factors as the floor for performance attribution.** Reporting a CAPM or even FF3 alpha for a strategy that could be tilted toward winners overstates skill; include momentum or expect to be fooled (→ [[sharpe-lintner-capm]], → [[fama-french-luck-vs-skill]]).
2. **"Hot hands" is mostly momentum.** Chasing last year's top funds buys momentum exposure you can get far more cheaply as a factor — and you inherit momentum's crash risk without the diversification.
3. **Costs are the most reliable predictor of net performance.** Expense ratio and turnover subtract from return roughly one-for-one; the single most robust persistence in the data is poor funds staying poor because of fees.
4. **Beware factor-model vintage.** A positive Carhart alpha may be RMW/CMA exposure the model cannot see; re-test against the five-factor model before calling it skill.
5. **Separate the model from the finding.** Cite Carhart for the four-factor benchmark; cite it also as the first clean evidence that active equity funds, in aggregate, do not beat passive factor exposure net of costs.

## Connections

- [[jegadeesh-titman-momentum]] — Supplies the momentum phenomenon that Carhart packages into the PR1YR factor.
- [[fama-french-factor-models]] — The three-factor model Carhart extends; FF deliberately exclude momentum, which is the gap Carhart fills. Later superseded in coverage by FF's own five-factor model (RMW, CMA).
- [[sharpe-lintner-capm]] — The one-factor baseline; Carhart's RMRF is the CAPM market factor, and the paper's message is that CAPM/FF3 alphas overstate skill.
- [[fama-french-luck-vs-skill]] — Extends Carhart's negative-net-alpha finding with bootstrap simulations distinguishing luck from skill; uses the four-factor model as a primary benchmark.
- [[cohen-frazzini-economic-links]] and [[houweling-vanzundert-factor-investing-corporate-bonds]] — Both evaluate their alphas against the four-factor (plus extensions) benchmark introduced here.
- [[frazzini-pedersen-betting-against-beta]] — BAB alpha is reported relative to the four-factor Carhart model.
- [[harmsworth-idiosyncratic-alpha]] — The modern practitioner answer to Carhart's pessimism: strip the four (and more) betas and the residual *idiosyncratic* alpha is persistent after all.

#carhart #four-factor-model #momentum #pr1yr #umd #mutual-funds #performance-persistence #fund-costs #expense-ratio #benchmark #alpha #attribution #foundational
