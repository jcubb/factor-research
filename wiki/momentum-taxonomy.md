# A Taxonomy of Momentum

> Concept synthesis (not a single paper). Organizes the KB's momentum cluster into one framework. Companion reading: [[start-here]] Stage 2.

Momentum is the most fragmented factor in the KB — the one place where "the same idea" splinters into a dozen variants that are easy to confuse. This article is the map: three axes that locate any momentum strategy, the subsumption debate over which variant is primary, the three competing explanations, and momentum's defining danger (crashes). It turns six paper articles into one teachable structure.

## Why momentum needs a taxonomy

Unlike value (one idea, a few ratios), momentum comes in kinds that behave differently and are priced differently: you can rank stocks against *each other* or against *their own past*; you can apply it to stocks, to factors, or to whole asset classes; and the signal can be a straight line, a sign, or an S-curve. Calling all of these "momentum" hides exactly the distinctions that matter for risk and implementation.

## Axis 1 — Cross-sectional vs. time-series

| | **Cross-sectional (relative)** | **Time-series (absolute)** |
|---|---|---|
| Rule | Rank securities against each other; long winners, short losers | Judge each asset against its own past; long if it rose, short if it fell |
| Net exposure | Dollar-neutral by construction | Can be net long or net short the whole market |
| Origin | [[jegadeesh-titman-momentum]] | TSMOM (Moskowitz-Ooi-Pedersen 2012 — not yet held; ingestion candidate) |
| KB refinement | [[carhart-four-factor-persistence]] (UMD factor) | [[moskowitz-nonlinear-momentum]] (S-curve signal) |

The distinction is not cosmetic: time-series momentum carries a directional market bet that cross-sectional momentum nets out, so the two diverge sharply in trending-vs-choppy markets.

## Axis 2 — What is the unit?

| Unit | What has momentum | KB article |
|---|---|---|
| **Stocks** | Individual equities (the original) | [[jegadeesh-titman-momentum]] |
| **Factors** | Factor returns are autocorrelated | [[ehsani-linnainmaa-factor-momentum]], [[gupta-kelly-factor-momentum-everywhere]] |
| **Industries** | Sector returns persist | subsumed by TSFM in [[gupta-kelly-factor-momentum-everywhere]] |
| **Asset classes** | Equities, bonds, FX, commodities each trend | [[moskowitz-nonlinear-momentum]], [[verdelhan-systematic-exchange-rates]] (carry's cousin) |

This axis hosts the KB's central momentum argument (below): the claim that **factor** momentum is the primary object and stock momentum merely its shadow.

## Axis 3 — Signal construction

Three sub-choices define any implementation, and each is a lever with real P&L consequences:

- **Formation / holding / skip windows.** The canonical grid is formation *J* = 3–12 months, holding *K* = 3–12 months, with a **one-month skip** to dodge short-term reversal and microstructure noise ([[jegadeesh-titman-momentum]]). The practitioner "12-minus-2" convention is this skip made standard.
- **Signal shape.** How a past return maps to a position weight:
  - *Linear* — weight ∝ past return (classic).
  - *Sign / binary* — long or short at full size (naive TSMOM).
  - *S-curve* — the optimal shape: ramp up in the middle, **saturate at the extremes** (don't chase blow-off moves). [[moskowitz-nonlinear-momentum]] shows this beats both linear and sign, with neural nets independently recovering the S-shape.
- **Weighting within legs** — equal vs. value-weighted; interacts with the simple-vs-pure construction choice in [[factor-construction-methods]].

## The subsumption debate — which momentum is primary?

The KB's sharpest momentum result: **stock momentum may not be a distinct factor at all.**

- [[ehsani-linnainmaa-factor-momentum]] argue stock-level momentum is a *byproduct of autocorrelation in factor returns* — when factors trend, the stocks loading on them inherit the trend. Momentum is really the *timing* of other factors.
- [[gupta-kelly-factor-momentum-everywhere]] confirm this at scale: time-series factor momentum (TSFM) across 65 factors subsumes both UMD and industry momentum, and crucially **avoids the 2009 momentum crash** (+18% vs. UMD's −31%).

If this is right, momentum sits *on top of* the rest of the factor zoo rather than beside it — a meta-factor. That reframing is why the momentum cluster connects to [[factor-cyclicality-and-timing]]: factor momentum is one concrete way to time factors.

## Three explanations (and why they coexist)

| Lens | Claim | KB source |
|---|---|---|
| **Behavioral** | Investors under-react to news; prices drift, then overshoot and reverse | [[jegadeesh-titman-momentum]] (reversal in yrs 2–3); [[cohen-frazzini-economic-links]] (attention) |
| **Statistical** | Factor returns are autocorrelated; stock momentum inherits it | [[ehsani-linnainmaa-factor-momentum]] |
| **Fundamental** | Momentum proxies expected near-term profit growth → expected cash flows | [[dfa-profit-growth-expected-returns]] |

These are not mutually exclusive. The fundamental story explains *why momentum decays fast* (cash-flow news is short-lived); the behavioral story explains *the reversal*; the statistical story explains *why it shows up across the whole factor zoo at once*. A good lecture presents all three and resists picking a winner.

## Momentum's dark side: crashes

Momentum's distinguishing risk is the **crash** — rare, violent losses that occur in panic *rebounds*, when beaten-down losers (which momentum is short) rally hardest (the "junk rally" of 2009; Daniel & Moskowitz 2016 — ingestion candidate). This is why:

- the S-curve's extreme-saturation matters (don't be maximally short the most beaten names) — [[moskowitz-nonlinear-momentum]];
- factor momentum's crash-avoidance is a selling point — [[gupta-kelly-factor-momentum-everywhere]];
- regime/volatility scaling and managed portfolios are common overlays — [[li-episodic-factor-pricing]], [[factor-cyclicality-and-timing]].

Momentum has the highest Sharpe *and* the worst tail of the major factors; any honest treatment pairs the premium with the crash.

## One-glance map

| Strategy | X-sec / T-series | Unit | KB article |
|---|---|---|---|
| Relative strength (winners−losers) | X-sec | stocks | [[jegadeesh-titman-momentum]] |
| UMD / PR1YR factor | X-sec | stocks | [[carhart-four-factor-persistence]] |
| Factor momentum | both | factors | [[ehsani-linnainmaa-factor-momentum]] |
| TSFM across 65 factors | T-series | factors | [[gupta-kelly-factor-momentum-everywhere]] |
| Nonlinear TSMOM | T-series | assets | [[moskowitz-nonlinear-momentum]] |
| Customer/supply-chain momentum | X-sec | linked stocks | [[cohen-frazzini-economic-links]] |

## Teaching arc (Lecture 2, momentum half)

1. The anomaly and why it embarrasses efficient markets ([[jegadeesh-titman-momentum]]).
2. The three axes — put each KB variant in its cell.
3. The subsumption twist — stock momentum as factor timing.
4. The three explanations — behavioral / statistical / fundamental.
5. The crash — the price of the premium; how the modern variants manage it.

## Connections

- [[jegadeesh-titman-momentum]] — the origin; defines the formation/holding/skip grid and the reversal evidence.
- [[carhart-four-factor-persistence]] — turns momentum into the UMD factor and the standard benchmark.
- [[ehsani-linnainmaa-factor-momentum]] / [[gupta-kelly-factor-momentum-everywhere]] — the factor-momentum reframing and its scaled, crash-avoiding implementation.
- [[moskowitz-nonlinear-momentum]] — the signal-shape refinement (S-curve).
- [[dfa-profit-growth-expected-returns]] — the fundamental explanation and momentum's fast decay.
- [[cohen-frazzini-economic-links]] — a targeted momentum source (limited attention along supply chains).
- [[factor-cyclicality-and-timing]] — factor momentum as a special case of factor timing.
- [[capm-and-the-cross-section]] — where momentum sits in the broader model ladder.

#concept #momentum #taxonomy #time-series-momentum #cross-sectional-momentum #factor-momentum #momentum-crash #teaching #lecture-2
