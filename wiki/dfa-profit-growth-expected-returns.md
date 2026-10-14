# Profit Growth and Expected Stock Returns

> Source: Ahn, Byung Hyun, Stanley Black, Mia Huang, Tom Lord, Savina Rizova, and Namiko Saito. "Profit Growth and Expected Stock Returns." Dimensional Fund Advisors, Research white paper, October 2026.
> Affiliations: Dimensional Fund Advisors (Strategy Research / Investment)
> Status: Practitioner research white paper (not peer-reviewed)

## Overview

This paper argues that **current profit growth** — the year-on-year change in quarterly operating profits, scaled by book equity — is a systematic proxy for *expected future profit growth*, and therefore for expected future profitability and returns, even after controlling for the current *level* of profitability. The logic sits inside the standard valuation framework: future profits equal current profits plus future growth in profits, so any signal about future profit growth improves the forecast of future profitability and, through valuation theory, of expected returns.

The second contribution is a **unifying link between profit growth and price momentum**. Both predict profit growth over the next three or so quarters; profit growth is the stronger and "cleaner" predictor but is updated at most once a quarter (at earnings), while price momentum is noisier but continuously updated between announcements. The two overlap only moderately (~40%) and neither subsumes the other in return tests. This leads to a **cash-flow-based (valuation) explanation of momentum**: momentum predicts returns because it proxies for expected short-term profit growth, and it is fast-decaying because that profit-growth information only pertains to the next few quarters.

The results are documented in the US (CRSP/Compustat, Jul 1974–Dec 2024) and replicated in developed ex-US and emerging markets (Bloomberg, Jan 2005–Dec 2024), including countries like Japan where price momentum has historically looked weak.

## Variable Definitions

| Variable | Definition |
|---|---|
| **Profitability** | Latest four-quarter profits / book equity at the latest quarter-end. Profits = operating profits before depreciation & amortization, less interest expense. Book equity includes minority interest. |
| **Profit growth (PG)** | $(\pi_{q} - \pi_{q-4})\,/\,BE_q$ — the difference between profits in the most recent quarter and four quarters ago, scaled by book equity. The year-on-year (same-quarter) differencing removes seasonality; scaling by BE keeps it inside the valuation framework (profitability = profits/BE, relative price = mktcap/BE). |
| **Price momentum (MOM)** | Cumulative return over the trailing 12 months, skipping the most recent month (skip-month avoids short-term reversal contamination). |
| **SUE** | Standardized unexpected earnings: YoY change in quarterly EPS (before extraordinary items) / std. dev. of those changes over the latest 8 quarters (min 6). |
| **CAR3** | Compounded stock return over the 3-day window around an earnings announcement, in excess of the country market return over the same window. |

**Timing / data start:** New quarterly data are used from the end of the announcement month (or three months after report date if the announcement date is missing). Lagging all quarterly data by three extra months yields qualitatively similar results. Why quarterly (not annual as in FF 2015)? Quarterly reports move prices well before the annual report, so changes in quarterly profits capture the most recent trend.

## 1. Profit Growth Predicts Future Profit Growth (Exhibit 1)

Fama-MacBeth (1973) monthly cross-sectional regressions of *N-quarter-ahead* profit growth on current characteristics. All variables decile-transformed (size in 5 groups), Newey-West 11 lags. Coefficients read as "effect of moving up one decile."

**Univariate — coefficient (and avg. adj. R²) by horizon N quarters ahead:**

| Predictor | N=1 | N=2 | N=3 | N=4 |
|---|---|---|---|---|
| **Profit Growth** | **0.50*** (25.6%) | **0.30*** (9.5%) | **0.14*** (2.5%) | −0.06*** (0.9%) |
| Momentum | 0.22*** (5.2%) | 0.15*** (2.5%) | 0.08*** (0.9%) | 0.03*** (0.3%) |
| SUE | 0.34*** (9.0%) | 0.20*** (3.3%) | 0.09*** (0.7%) | −0.07*** (0.6%) |
| CAR3 | 0.12*** (1.6%) | 0.10*** (1.1%) | 0.08*** (0.7%) | 0.00* (0.0%) |

Profit growth has the largest effect and the highest R² at every near-term horizon. Moving from the bottom to the top PG decile is associated with a 4–5 decile jump in next-quarter profit growth, ~3 deciles two quarters out, ~1 decile three quarters out. The other proxies are about half as strong. In the **multivariate** regression (all proxies plus size, B/M, profitability, investment), profit growth still dominates, with momentum second. All four proxies predict profit growth positively only for the next ~3–4 quarters, then the coefficients turn negative — **strong near-term persistence followed by weak reversion**, consistent with Fama-French (2000) and Lim et al. (2024).

## 2. Profit Growth Predicts Future Profitability (Exhibit 2)

Regressing 1-year-ahead profitability on current characteristics: both **profit growth (0.06***→0.04***)** and **momentum (0.06***→0.04***)** retain reliable predictive power *after controlling for current profitability* (whose coefficient is ~0.70) and beat SUE (0.01) and CAR3 (0.02). Robust to annual (non-overlapping) regressions and to using ROE as the dependent variable.

## 3. Profit Growth Predicts Returns; the Fresh/Stale Split (Exhibit 3)

Monthly cross-sectional regressions of 1-month-ahead returns. Profit growth has information about returns beyond size, relative price, profitability, and investment, and is robust to controlling for momentum and one-month reversal. **A one-decile increase in profit growth predicts +0.16% next-month return.**

**The key interaction — fresh vs. stale data (Panel B):** "Fresh" = profit-growth data newly released this month (not yet used); "Stale" = released ≥1 month ago.

| | All Firms | Fresh PG | Stale PG |
|---|---|---|---|
| Profit Growth | 0.16*** | 0.17*** | 0.14*** |
| **Momentum** | **0.04** (t 1.98) | **0.00** (t 0.07) | **0.06*** (t 3.35) |

Profit growth's attenuation of momentum comes **entirely from fresh-data firms**: right after an earnings announcement, profit growth reflects the latest trend while momentum (by skip-month construction) does not yet reflect the latest price move, so profit growth overshadows it. Among stale-data firms, momentum keeps its full predictive power — it is the channel through which new, between-announcement information keeps updating the cash-flow forecast. Same pattern holds internationally.

## 4. Portfolio Sorts and the Volatility Contrast (Exhibits 4–5)

Univariate top/bottom-30% sorts (monthly rebalanced). Return spreads for profit growth and momentum are similar in **magnitude**, but momentum's are roughly **twice as volatile**:

| | PG premium σ | MOM premium σ |
|---|---|---|
| Large cap | 9.3% | 15.4% |
| Small cap | 7.6% | 15.8% |

The extra momentum volatility is largely **momentum crashes** — e.g. in 2009 the small-cap momentum premium was ≈ −99% versus ≈ −17% for profit growth. Profit-growth spreads are not sector-driven (sector-neutral sorts give similar spreads). This mirrors Novy-Marx (2015): fundamental momentum has fewer drawdowns than price momentum.

**Pre/post-formation dynamics (Exhibits 6–7):** spreads in profit growth widen in the year *before* formation (so does the cumulative return spread); after formation the profit-growth spread reverts to zero over ~a year and the return spread plateaus, with the monthly return spread decaying to zero over ~6–9 months. Momentum-sorted portfolios show the same trajectory — evidence the two carry **similar fast-dissipating information** about future profits and returns.

## 5. The Two Signals Are Complementary, Not Redundant

- **Overlap (Exhibit 8):** the average month-end overlap between equivalent PG and MOM groupings is ~40% — related but only partially; "40 cents of each \$1 is invested identically."
- **Double sorts (Exhibit 9):** within each momentum group there is a positive PG spread, and within each PG group a positive momentum spread; the **diagonal** spread (high-PG/high-MOM minus low-PG/low-MOM) exceeds either single-sort spread. Neither subsumes the other.
- **Matched sorts (Exhibits 10–11):** sorting on PG within momentum deciles (then aggregating) preserves a large PG return spread with momentum held fixed, and vice versa — following Novy-Marx's (2015) matched-group approach.

## 6. Spanning Regressions and the Variance Artifact (Exhibit 13)

A profit-growth factor is built FF-style (NYSE 30/70 breakpoints, long high-PG / short low-PG, large+small averaged). RMW is reconstructed with the *same* up-to-date four-quarter-profit lagging as PG, to remove PG's data-freshness advantage.

- Regressing the **PG factor** on FF5 + momentum + short-term reversal leaves a **positive, reliable intercept** (0.37, t=5.27) — not spanned.
- Regressing the **momentum factor** on FF5 + reversal + PG produces a **near-zero, insignificant intercept** (−0.04, t=−0.22) — *appears* subsumed.

But this asymmetry is largely a **variance artifact**: a univariate slope is cov/var of the RHS variable, so when two variables have very different variances (momentum vol ≈ 2× PG vol) the regression is sensitive to which side is the dependent variable. **Volatility-matching the momentum factor** to the PG factor restores reliably positive intercepts for *both* (≈0.24 each, column 9 of each panel). Conclusion: the two factors are genuinely **complementary**, not one inside the other. Excluding 2009 does not overturn this.

## 7. International Evidence (Exhibits 14–20)

- Future-profit-growth and future-profitability regressions replicate in developed ex-US and emerging markets: PG predicts profit growth positively for ~3 quarters then negatively; PG and momentum both predict future profitability after controlling for current profitability.
- Return regressions replicate the **fresh/stale** result: profit growth attenuates momentum only when PG data are fresh.
- The fresh/stale and complementary spanning results hold; after vol-matching, momentum is again not subsumed by PG (though the PG-factor intercept becomes indistinguishable from zero in developed ex-US, driven by weak large-cap PG spreads there).
- **Reporting-frequency robustness (Exhibit 20):** the profit-growth premium appears across countries regardless of whether quarterly reporting is mandatory, voluntary, or semiannual — **including Japan**, long cited as lacking a momentum premium.

## 8. A Valuation-Theory Framework for Momentum (Section 7)

Valuation theory: expected return is driven by today's price and expected future cash flows; cash flows are driven by expected future profits = current profits + expected profit growth. Since both current profit growth and price momentum carry reliable information about near-term future profit growth and profitability (net of current price and profitability), both should forecast returns — and the information's short horizon explains momentum's **fast decay / high turnover**.

For a *rational* (risk-based) reading, the paper leans on **Vassalou & Apedjinou (2004)**: "corporate innovation" (the part of a firm's gross-margin change not explained by capital/labor) resembles profit growth, is priced in the cross-section, and absorbs the priced information in the momentum factor. Corporate innovation is akin to total factor productivity (TFP) — an ICAPM (Merton 1973) state variable. The transitory nature is explained by **competition / mean reversion in profitability** (Fama-French 2000): rivals imitate innovators, losers must innovate or exit. Empirically this matches the ~1-year reversion of profit-growth spreads and 6–9-month return convergence. The paper acknowledges the standing challenge for any rational momentum story: its high turnover and large (~5–10%/yr) premium.

## Implications for Practice

1. **Use both signals, for different jobs.** Price momentum, continuously updated, suits daily portfolio management; profit growth, tied more directly to future profitability, suits capturing the profitability premium. They complement rather than replace each other.
2. **Profit growth sharpens the profitability premium.** Because future profits = current profits + growth, adding a profit-growth signal improves the forecast of future profitability beyond the current level alone.
3. **Profit growth is the lower-risk sibling of momentum.** Similar average spreads at roughly half the volatility and without the 2009-style crashes — attractive on a risk-adjusted basis and as a crash-tempering complement to a momentum sleeve.
4. **Freshness matters.** Profit growth dominates momentum only right after earnings (fresh data); between announcements, momentum carries the incremental information. A combined signal should weight by data recency.
5. **Beware variance artifacts in spanning tests.** A "subsumed" verdict can flip once factors are volatility-matched; compare like-for-like volatility before concluding one factor is redundant.
6. **A cash-flow lens on momentum.** Treating momentum as a noisy proxy for expected short-term profit growth gives a valuation-based rationale for why it works and why it is short-lived — useful for horizon and turnover expectations.

## Connections

- [[novy-marx-gross-profitability]] — the direct ancestor: profitability as a priced "good growth" characteristic and the empirical origin of RMW. This paper extends the logic from the *level* of profitability to its *change*, and borrows Novy-Marx's (2015) fundamental-momentum findings (fewer drawdowns than price momentum) and matched-group sort methodology.
- [[fama-french-factor-models]] — built on the FF valuation framework (FF 2000/2006/2015), uses FF5 + momentum + reversal as the spanning benchmark, and reconstructs RMW with matched lagging. Profit growth is proposed as an additional, non-spanned factor.
- [[ehsani-linnainmaa-factor-momentum]] — a complementary explanation of momentum. Ehsani-Linnainmaa attribute momentum to *factor autocorrelation*; this paper attributes it to *fundamental* (profit-growth) persistence. Both imply momentum is not a standalone primitive and both emphasize its fast decay.
- [[gupta-kelly-factor-momentum-everywhere]] — shares the theme that momentum's crash risk (esp. 2009) is a key weakness; profit growth is offered here as a lower-volatility, crash-resistant alternative source of the same short-horizon information.
- [[moskowitz-nonlinear-momentum]] — another angle on improving momentum; this paper's fresh/stale result is effectively a *conditioning* improvement (weight momentum less when fresh fundamentals are available).
- [[cohen-frazzini-economic-links]] — both connect returns to the arrival and diffusion of fundamental/earnings information; here the information is own-firm profit growth rather than supply-chain spillovers.

#profit-growth #momentum #profitability #earnings-momentum #valuation-theory #cross-section #fama-macbeth #factor-construction #spanning-regressions #international #dimensional #post-earnings-drift
