# From the CAPM to the Factor Zoo — The Cross-Section of Expected Returns

> Concept synthesis (not a single paper). Stitches the foundational asset-pricing articles into one narrative. Companion reading: [[start-here]] Stages 1–2.

Every empirical factor paper in this KB is an answer to one question: **why do different stocks earn different average returns?** This article tells that story as a single arc — from the one clean theoretical answer (the CAPM), through its empirical collapse, to the sprawling "factor zoo" and the skepticism it provoked. It is the connective tissue for the individual paper articles, and the spine of a first lecture on factors.

## The question, stated precisely

Fix a moment in time and look *across* stocks (the **cross-section**). Their expected returns differ. What characteristic of a stock — measurable today — predicts how much it will earn? Two families of answer recur throughout the KB and are worth separating from the start:

- **Risk-based:** high-return stocks are riskier in some way investors care about; the extra return is *compensation* and should persist.
- **Mispricing-based:** high-return stocks are *cheap* for behavioral or frictional reasons; the extra return is a correction and may erode as it becomes known.

The whole literature oscillates between these two readings, and most papers decline to settle it. Holding the distinction in mind is the single most useful habit for reading the KB.

## The one clean answer: the CAPM

The [[sharpe-lintner-capm]] gives the most elegant possible answer: the *only* thing that should predict a stock's expected return is its **beta** — its covariance with the market portfolio.

$$E[R_i] - R_f = \beta_i\,(E[R_m] - R_f)$$

Everything else — size, industry, volatility, "cheapness" — is irrelevant, because a diversified investor washes it out. This is a beautiful theory: one factor, one line (the SML), and a sharp null hypothesis ($\alpha_i = 0$ for every asset). It also hands the field its permanent vocabulary: **beta, alpha, the market factor, systematic vs. specific risk.**

## The empirical collapse

The data refused to cooperate, and *how* it failed defines everything after:

1. **The SML is too flat.** Beta earns far less than the CAPM predicts; low-beta stocks out-earn their prediction and high-beta stocks under-earn. Documented decisively in [[fama-french-factor-models]] (1992), explained and monetized as a factor in [[frazzini-pedersen-betting-against-beta]].
2. **Characteristics beat beta.** Variables the CAPM says should not matter — predict returns *after* controlling for beta.

The survivors of decades of cross-sectional testing:

| Characteristic | Factor | Direction | KB article |
|---|---|---|---|
| Market covariance | Market (RMRF) | + (but flat) | [[sharpe-lintner-capm]] |
| Small size | SMB | small > big | [[fama-french-factor-models]] |
| Cheapness (book/market) | HML (value) | cheap > expensive | [[fama-french-factor-models]] |
| Past 3–12m return | UMD (momentum) | winners > losers | [[jegadeesh-titman-momentum]] |
| Profitability | RMW | profitable > weak | [[novy-marx-gross-profitability]] |
| Investment / asset growth | CMA | conservative > aggressive | [[fama-french-factor-models]] |
| Low beta / low vol | BAB / Low-Vol | low-risk > high-risk | [[frazzini-pedersen-betting-against-beta]] |

## The models nest

The empirical models are a sequence of *additions*, each keeping the previous architecture (a return regression with a zero-alpha null) and adding priced dimensions:

$$\text{CAPM} \subset \text{FF3} \subset \text{Carhart 4} \subset \text{FF5} \;(\subset \text{Barra, q-factor, \dots})$$

| Model | Factors | Adds | Article |
|---|---|---|---|
| CAPM | Mkt | — | [[sharpe-lintner-capm]] |
| FF three-factor | + SMB, HML | size, value | [[fama-french-factor-models]] |
| Carhart four-factor | + UMD | momentum | [[carhart-four-factor-persistence]] |
| FF five-factor | + RMW, CMA | profitability, investment | [[fama-french-factor-models]] |

Two structural lessons fall out of this ladder:

- **"Alpha" is model-relative.** Each rung reclassifies the previous rung's alpha as beta. A CAPM alpha is often just size/value/momentum exposure; a Carhart alpha can still be profitability exposure. This is the recurring plot of the entire KB — see especially [[fama-french-luck-vs-skill]] and [[harmsworth-idiosyncratic-alpha]].
- **Factors can make each other redundant.** Once RMW and CMA enter, HML's premium is explained by its loadings on them — value is "profitability and investment in disguise" ([[novy-marx-gross-profitability]] is the mechanism). Adding a factor is not free; it can reveal an old one was never independent.

## The factor zoo and the skeptic's reply

By the 2010s, hundreds of published "factors" existed — the **factor zoo**. This provoked a methodological backlash that every serious factor user must internalize:

- **Multiple testing.** Test enough characteristics and some clear any fixed significance bar by chance. The honest hurdle for a "new" factor is far higher than the textbook *t* > 2 (Harvey-Liu-Zhu, 2016 — referenced across the KB but not yet held; a prime ingestion candidate).
- **Replication and decay.** Many anomalies weaken out-of-sample or after publication (McLean & Pontiff). The KB's own [[li-episodic-factor-pricing]] reframes this as premia switching *off* in certain regimes rather than vanishing.
- **Spurious factors are costly.** Adding a bogus factor to a *risk model* is asymmetrically damaging — far worse than omitting a real one ([[menchero-factor-alignment]]).

The disciplined response is not nihilism but parsimony: a handful of factors with (a) a plausible economic story, (b) out-of-sample and international evidence, and (c) robustness to construction choices. The [[msci-foundations-of-factor-investing]] six — Value, Size, Momentum, Low Vol, Yield, Quality — are the practitioner's shortlist of survivors.

## Risk vs. mispricing, revisited

With the survivors in hand, the risk/mispricing question sharpens into concrete, testable sub-claims rather than philosophy:

- **Value** — distress risk (risk) vs. extrapolation/overreaction (mispricing). Both have evidence.
- **Momentum** — hard to cast as risk (it *reverses*); mostly read as under-reaction ([[jegadeesh-titman-momentum]]) or as factor autocorrelation ([[ehsani-linnainmaa-factor-momentum]]) or expected cash-flow growth ([[dfa-profit-growth-expected-returns]]).
- **Low beta** — a *friction* story: leverage constraints, not classic risk ([[frazzini-pedersen-betting-against-beta]]).

The practical upshot: a premium you believe is *risk* you hold through drawdowns; a premium you believe is *mispricing* you harvest while watching for decay and crowding.

## Teaching arc (Lecture 1 skeleton)

1. The question: the cross-section of expected returns; risk vs. mispricing as the two lenses.
2. The CAPM as the clean null — derive the SML, define alpha/beta/specific risk.
3. The collapse — flat SML, the size/value/momentum anomalies; the model ladder.
4. The factor zoo — why more is not better; multiple testing and replication.
5. Closing synthesis — the surviving factors and how to judge a new one.

## Connections

- [[sharpe-lintner-capm]] — the clean null this whole arc departs from.
- [[fama-french-factor-models]] — the empirical refutation and the model ladder's main rungs.
- [[jegadeesh-titman-momentum]] / [[carhart-four-factor-persistence]] — the momentum rung and the benchmark model.
- [[novy-marx-gross-profitability]] — profitability as the origin of RMW and the mechanism behind HML redundancy.
- [[frazzini-pedersen-betting-against-beta]] — the flat-SML explanation and the low-risk factor.
- [[msci-foundations-of-factor-investing]] — the practitioner shortlist of surviving premia.
- [[menchero-factor-alignment]] — why a bloated zoo is dangerous inside a risk model.
- [[momentum-taxonomy]] / [[factor-cyclicality-and-timing]] — the next two concept layers, zooming into momentum and into time-variation of premia.

#concept #cross-section #capm #factor-zoo #risk-vs-mispricing #model-ladder #multiple-testing #teaching #lecture-1
