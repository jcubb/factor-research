# Returns to Buying Winners and Selling Losers (Jegadeesh & Titman 1993)

> Source: Jegadeesh, Narasimhan and Sheridan Titman. "Returns to Buying Winners and Selling Losers: Implications for Stock Market Efficiency." *Journal of Finance* 48(1), March 1993, pp. 65–91.
> Status: foundational — the empirical origin of the momentum factor (UMD / MOM / PR1YR). Compiled from established knowledge (no raw PDF in `raw/`).

This is the paper that discovered **cross-sectional momentum** and, with it, one of the most durable and troublesome anomalies in finance. Every momentum article in this KB descends from it: the Carhart momentum factor (→ [[carhart-four-factor-persistence]]) is built on this strategy, Ehsani & Linnainmaa argue stock momentum is really *factor* momentum (→ [[ehsani-linnainmaa-factor-momentum]]), Gupta & Kelly scale it across 65 factors (→ [[gupta-kelly-factor-momentum-everywhere]]), Moskowitz et al. refine its signal shape (→ [[moskowitz-nonlinear-momentum]]), and the DFA profit-growth paper offers a fundamental explanation for it (→ [[dfa-profit-growth-expected-returns]]). The anomaly it documents — that past winners keep winning over 3–12 months — directly contradicts both the weak-form efficient market hypothesis and the CAPM.

## Overview

Jegadeesh & Titman show that a **zero-cost "relative strength" strategy** — buy the stocks that performed best over the past 3–12 months, short the stocks that performed worst, hold for 3–12 months — earns large, statistically significant, risk-adjusted profits. The headline 6-month/6-month strategy returned about **0.95% per month** (≈12% annualized) over 1965–1989 for US stocks.

Crucially, these profits are **not explained by systematic risk** (the winner portfolio's CAPM beta is, if anything, *higher* only modestly and cannot account for the spread) nor by the **lead-lag / delayed-reaction cross-serial effects** that Lo & MacKinlay proposed for contrarian profits. Momentum is a genuinely new phenomenon: short-horizon *continuation*, sitting between De Bondt & Thaler's short-term (weekly/monthly) and long-term (3–5 year) *reversals*.

The second decisive finding: momentum profits **partially reverse** in the second and third years after formation. Returns accumulate for about 12 months, then bleed back. This hump-then-reversal pattern is the empirical fingerprint that points toward **under-reaction followed by over-reaction** (delayed incorporation of information, then overshooting) rather than compensation for risk.

## The Strategy Construction

The design is a grid of **J-month formation × K-month holding** periods, the template copied by essentially all later momentum research.

| Step | Rule |
|---|---|
| Rank | Sort all NYSE/AMEX stocks by cumulative return over the past **J** months (J = 3, 6, 9, 12) |
| Form | Winner decile (top 10%) long, loser decile (bottom 10%) short — equal-weighted, zero net cost |
| Hold | Hold **K** months (K = 3, 6, 9, 12), then rebalance |
| Overlap | Use **overlapping portfolios**: in any month, hold K cohorts formed in the last K months; average their returns (raises power, reduces noise) |

A **one-week (and in robustness tests, one-month) skip** between formation and holding is used to sidestep bid-ask bounce and short-term reversal contamination — the reason the practitioner momentum factor is conventionally "12-minus-2 month" (skip the most recent month).

### Representative Results (16 J×K strategies, 1965–1989)

| | Hold K=3 | K=6 | K=9 | K=12 |
|---|---|---|---|---|
| Form J=3 | small + | + | + | + |
| J=6 | + | **~0.95%/mo** | + | + |
| J=9 | + | + | + | + |
| J=12 | + | + | + | smaller + |

All 16 combinations are positive; the diagonal around **6×6 to 12×3** is strongest. Profits weaken as holding extends past ~12 months because the reversal sets in.

## Why It Isn't Risk

Jegadeesh & Titman rule out the obvious benign explanations:

1. **Not CAPM beta.** Adjusting for market risk does not shrink the spread; the alpha survives. The winner leg does not carry enough extra systematic risk to justify its extra return.
2. **Not the size effect.** Momentum holds within size groups and after size adjustment.
3. **Not lead-lag (Lo-MacKinlay).** Decomposing the profit into own-autocovariance, cross-serial covariance, and cross-sectional dispersion in means, they show momentum comes overwhelmingly from **positive own-serial correlation** in returns — stocks continuing their own trend — not from one group leading another.
4. **Reversal in years 2–3.** About half the year-1 profit reverses over the following 24 months. A risk premium should not systematically reverse; this is the signature of mispricing that corrects.
5. **January effect.** Momentum profits are strongly *negative* in January (losers bounce) and positive in the other 11 months — hard to reconcile with a stable risk story.

## The Interpretation Debate

The paper frames momentum as a challenge to market efficiency and leans toward a **behavioral under-reaction** reading: investors are slow to fully impound information (earnings news, analyst revisions), so prices drift in the direction of the news for several months, then over-shoot and reverse. This under-reaction framing seeded a large theory literature (Barberis-Shleifer-Vishny, Daniel-Hirshleifer-Subrahmanyam, Hong-Stein). The KB carries two modern descendants of the explanation question:
- **Statistical:** momentum is autocorrelation *in factor returns*, not a stock-level effect (→ [[ehsani-linnainmaa-factor-momentum]]).
- **Fundamental:** momentum proxies for expected near-term profit growth, hence expected cash flows — which also explains why it decays fast (→ [[dfa-profit-growth-expected-returns]]).

## From Anomaly to Factor

The practitioner object that came out of this paper is the momentum factor — variously **UMD** (Up Minus Down), **MOM**, **WML** (Winners Minus Losers), or **PR1YR** (Carhart's prior-one-year return factor):

- Rank on past ~12 months of return, skipping the most recent month.
- Long high-momentum, short low-momentum, typically value-weighted within legs.
- Carhart (1997) added exactly this factor to the Fama-French three-factor model to form the **four-factor benchmark** that the rest of the KB uses to judge alpha (→ [[carhart-four-factor-persistence]]).

Momentum is the factor Fama-French never included in their own models (they treat it as an unexplained embarrassment the three- and five-factor models fail to price), which is precisely why Carhart's add-on became the standard.

## Implications for Practice

1. **Momentum is the benchmark's fourth leg.** Any strategy with a trend-following or winner-chasing tilt must be evaluated against a model that *includes* momentum, or its "alpha" is just UMD exposure (→ [[carhart-four-factor-persistence]]).
2. **Skip the most recent month.** The one-month gap between formation and holding is not cosmetic — it removes short-term reversal and microstructure noise that otherwise corrupts the signal.
3. **Momentum has a shelf life.** The 12-month-then-reverse pattern means momentum is a medium-horizon signal; holding winners indefinitely gives the profit back. This is the empirical basis for momentum's known crash risk and for signal-timing refinements.
4. **The formation window is a design choice, not a constant.** Results are robust across J = 3–12, but the optimal window interacts with the holding period and the universe; the 6×6 and 12×1 variants anchor most implementations.
5. **Beware January and crowding.** The strong January reversal and the subsequent-year unwind mean naive momentum carries predictable drawdowns — motivating the nonlinear and managed variants elsewhere in the KB (→ [[moskowitz-nonlinear-momentum]], → [[li-episodic-factor-pricing]]).

## Connections

- [[carhart-four-factor-persistence]] — Carhart (1997) turns this strategy into the PR1YR/UMD factor and adds it to Fama-French, creating the standard four-factor benchmark used throughout the KB.
- [[fama-french-factor-models]] — Fama-French pointedly exclude momentum; the FF3/FF5 models fail to price it, which is exactly why the Carhart add-on exists.
- [[ehsani-linnainmaa-factor-momentum]] — Reinterprets this stock-level anomaly as a byproduct of autocorrelation in *factor* returns; argues factor momentum subsumes Jegadeesh-Titman momentum.
- [[gupta-kelly-factor-momentum-everywhere]] — Scales time-series momentum across 65 factors; shows TSFM dominates the original UMD and avoids the 2009 momentum crash.
- [[moskowitz-nonlinear-momentum]] — Refines the signal: the optimal momentum weighting is an S-curve, not the linear/decile sort used here.
- [[dfa-profit-growth-expected-returns]] — Offers a fundamental (cash-flow) explanation for why momentum works and decays quickly, complementing the behavioral under-reaction story.

#momentum #jegadeesh-titman #umd #mom #wml #relative-strength #cross-sectional-momentum #anomaly #market-efficiency #under-reaction #reversal #foundational
