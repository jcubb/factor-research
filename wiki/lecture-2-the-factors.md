# Lecture 2 — The Factors and Their Dynamics

> Course material (not a paper). A ~50-minute lecture beat sheet: the surviving factors and their economic stories, a taxonomy of momentum, the subsumption debate, factor cyclicality and the case for/against timing, and momentum crashes. Instructor's main texts: [[momentum-taxonomy]] and [[factor-cyclicality-and-timing]]. Middle of a three-lecture course ([[lecture-1-cross-section]] → this → [[lecture-3-building-models]]).

## At a glance

| | |
|---|---|
| **Duration** | 50 min (≈18 slides) + 10 min Q&A |
| **Level** | Upper-undergrad / intro-MBA; assumes Lecture 1 |
| **Instructor texts** | [[momentum-taxonomy]], [[factor-cyclicality-and-timing]] |
| **Pre-reading for students** | both instructor texts; skim [[frazzini-pedersen-betting-against-beta]] and [[jegadeesh-titman-momentum]] §Overview |
| **Recap needed** | the surviving-factors table and "alpha is model-relative" from [[lecture-1-cross-section]] |

## Learning objectives

By the end, students can:
1. Give the **economic story** for value, profitability, and low-beta, and say whether each reads as risk or friction/mispricing.
2. **Taxonomize momentum** on three axes (cross-sectional vs. time-series; unit; signal shape).
3. State the **subsumption** claim — stock momentum as factor momentum — and the evidence.
4. Distinguish factor **cyclicality** (settled) from factor **timing** (contested), and rank the timing signals by evidence.
5. Explain the **momentum crash** and how managed portfolios address it.

---

## Section A — The surviving factors, with stories (10 min, slides 1–4)

**Slide 1 · Recap & roadmap.** From Lecture 1 we have a table of survivors; today we give them *stories* and *dynamics*. The risk-vs-mispricing lens stays on the board.

**Slide 2 · Value & profitability — two sides of one coin.** Profitability (RMW) is "good growth"; it *hedges* value (corr ≈ −0.57) and roughly doubles the market Sharpe when combined. Why HML goes redundant. Source: [[novy-marx-gross-profitability]].

**Slide 3 · Low beta / BAB — a friction, not a risk.** Leverage-constrained investors bid up high-beta assets → flat SML (the one from Lecture 1). BAB = lever the low-beta leg, short the high. Works across 20 markets, Treasuries, credit. Source: [[frazzini-pedersen-betting-against-beta]]. *Talking point: this is a clean non-risk, non-behavioral story — a constraint.*

**Slide 4 · Beyond equities.** Carry & dollar factors in FX ([[verdelhan-systematic-exchange-rates]]); FF factors in HY bonds via the Merton link ([[bektic-fama-french-corporate-bonds]]). The factor idea generalizes — but the *definitions* must be adapted.

## Section B — A taxonomy of momentum (12 min, slides 5–9)

**Slide 5 · Why momentum needs a map.** The most fragmented factor; "momentum" means a dozen things. Introduce three axes. Source: [[momentum-taxonomy]].

**Slide 6 · Axis 1 — cross-sectional vs. time-series.** Rank-against-peers (dollar-neutral) vs. judge-against-own-past (can be net long). Origin: [[jegadeesh-titman-momentum]].

**Slide 7 · Axis 2 — the unit.** Stocks → factors → industries → asset classes. Flag that this hosts today's big twist.

**Slide 8 · Axis 3 — signal shape.** Formation/holding/**skip-a-month**; linear vs. sign vs. **S-curve** (ramp in the middle, saturate at extremes — the optimal shape). *(Show the S-curve figure.)* Source: [[moskowitz-nonlinear-momentum]].

**Slide 9 · Place every variant.** One-glance table: relative strength, UMD, factor momentum, TSFM, nonlinear TSMOM, customer momentum — each in its cell. Source: [[momentum-taxonomy]] §"One-glance map".

## Section C — Explanations & the subsumption twist (10 min, slides 10–12)

**Slide 10 · The twist — stock momentum *is* factor momentum.** When factors trend, stocks loading on them inherit the trend. Momentum = timing other factors. Source: [[ehsani-linnainmaa-factor-momentum]]; scaled in [[gupta-kelly-factor-momentum-everywhere]].

**Slide 11 · Three explanations, not mutually exclusive.** Behavioral under-reaction (explains the reversal) / statistical autocorrelation (explains breadth across the zoo) / fundamental cash-flow (explains fast decay). Table. Sources: [[jegadeesh-titman-momentum]], [[ehsani-linnainmaa-factor-momentum]], [[dfa-profit-growth-expected-returns]].

**Slide 12 · Discussion beat (2 min).** *Ask:* if momentum reverses in years 2–3, can it be a risk premium? Steer toward "risk premia shouldn't systematically reverse."

## Section D — Cyclicality & timing (12 min, slides 13–16)

**Slide 13 · Premia vary (the easy claim).** Business-cycle cyclicality (factors take turns), autocorrelation, and *episodic* on/off pricing. Sources: [[msci-foundations-of-factor-investing]], [[li-episodic-factor-pricing]].

**Slide 14 · Can you time them? Four signals ranked.** Factor momentum (best supported) > regime detection > valuation spreads > (the skeptic's reply). Source: [[factor-cyclicality-and-timing]].

**Slide 15 · The skeptic's reply.** Near-arbitrage (timing that good shouldn't survive), spurious-factor cost, out-of-sample decay. *Teach the humility here — this is where naive backtests lie.*

**Slide 16 · Managed portfolios — the honest test harness.** $f^{\text{managed}}_{t+1}=s_t\,f^{\text{base}}_{t+1}$: a timed factor is the base factor times a signal. Li's managed portfolios lift SR 1.18 → 1.56. Sources: [[factor-cyclicality-and-timing]], [[li-episodic-factor-pricing]].

## Section E — The dark side & synthesis (6 min, slides 17–18)

**Slide 17 · Momentum crashes.** Rare, violent losses in panic rebounds (2009 junk rally): momentum is short the names that rally hardest. Why factor momentum and the S-curve help. Sources: [[momentum-taxonomy]] §"dark side", [[gupta-kelly-factor-momentum-everywhere]].

**Slide 18 · Tie-off.** Highest Sharpe *and* worst tail; diversify across factors first, time humbly second. Preview Lecture 3: how these factors are actually *built* and *used*.

---

## In-class discussion questions
1. BAB is a "constraint" story, not risk or behavior. What would break it?
2. If stock momentum is just factor momentum, should you ever trade stock-level UMD directly?
3. A manager claims a factor-timing overlay with Sharpe 2.0 in backtest. What's your first question?

## Suggested exercise / problem set
- Build a simple 6×6 momentum portfolio from French data; then add a one-month skip and compare — students *feel* the microstructure effect.
- Compute a value-spread signal and test timing the value factor on it; compare in-sample vs. a held-out window → students *see* out-of-sample decay firsthand.

## Known coverage caveat (tell students / note for yourself)
The timing material leans on the KB's *skeptic* side; the value-spread-timing and near-arbitrage **origin papers are not yet in the KB** (Asness-Moskowitz-Pedersen; Haddad-Kozak-Santosh). Present Signal B (valuation spreads) as practitioner-standard-but-contested rather than settled. See [[factor-cyclicality-and-timing]] §"Signal B".

## Connections
- [[momentum-taxonomy]], [[factor-cyclicality-and-timing]] — the two instructor texts this lecture follows.
- [[jegadeesh-titman-momentum]], [[carhart-four-factor-persistence]], [[ehsani-linnainmaa-factor-momentum]], [[gupta-kelly-factor-momentum-everywhere]], [[moskowitz-nonlinear-momentum]], [[dfa-profit-growth-expected-returns]] — the momentum evidence.
- [[novy-marx-gross-profitability]], [[frazzini-pedersen-betting-against-beta]], [[verdelhan-systematic-exchange-rates]], [[bektic-fama-french-corporate-bonds]], [[msci-foundations-of-factor-investing]], [[li-episodic-factor-pricing]] — the other factors and the dynamics.
- [[lecture-1-cross-section]] / [[lecture-3-building-models]] — the course bookends.

#course #lecture #lecture-2 #momentum #factor-timing #cyclicality #teaching
