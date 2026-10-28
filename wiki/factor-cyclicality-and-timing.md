# Factor Cyclicality and Timing

> Concept synthesis (not a single paper). Ties together the KB's evidence on time-varying premia and the (contested) attempt to time them. Companion reading: [[start-here]] Stages 2 and 6.

Factor premia are not constant. They wax and wane with the business cycle, with valuation spreads, and — on a sharper reading — switch "on" and "off" in regimes. That raises the most seductive and most dangerous question in factor investing: **can you time factors?** This article assembles the KB's evidence on both halves — that premia vary (well established) and that the variation is exploitable (hotly contested) — and lands on a disciplined practical verdict.

## Part 1 — Premia vary (the easy claim)

That factor returns are *cyclical* is not seriously disputed. The evidence in the KB:

- **Business-cycle cyclicality.** [[msci-foundations-of-factor-investing]] documents that the six premia are pro- or counter-cyclical in characteristic ways (e.g. Value and Size tend to be pro-cyclical; Quality and Low Vol defensive). Factors take turns; a static multi-factor blend is partly a diversification bet across these cycles.
- **Autocorrelation.** Factor returns are serially correlated — the empirical foundation of factor momentum ([[ehsani-linnainmaa-factor-momentum]], [[gupta-kelly-factor-momentum-everywhere]]). Serial correlation *is* time-variation with structure.
- **Regime / episodic pricing.** [[li-episodic-factor-pricing]] goes furthest: premia are concentrated in identifiable **pricing-on states** and earn roughly nothing in pricing-off states. Factor returns aren't smoothly cyclical so much as *episodic* — long flat stretches punctuated by bursts.

So the premium you measure as a long-run average is a blend of distinct states. The question is whether you can tell, *in advance*, which state you're in.

## Part 2 — Can you time them? (the hard claim)

Three timing signals appear in the KB, each with a different evidentiary footing.

### Signal A — Factor momentum (time the factor by its own trend)

The best-supported timing signal is a factor's **own recent performance**. Because factor returns are autocorrelated, going long factors that have been winning works:
- [[gupta-kelly-factor-momentum-everywhere]] — TSFM across 65 factors earns SR ≈ 0.84 and dominates stock and industry momentum.
- [[ehsani-linnainmaa-factor-momentum]] — frames momentum itself as the act of timing other factors.

This is the timing signal the KB most credibly endorses — partly because it is really just "momentum applied to factors" and inherits momentum's robust evidence (see [[momentum-taxonomy]]).

### Signal B — Valuation spreads (time the factor by its cheapness)

A factor is "cheap" when the valuation gap between its long and short legs is unusually wide. The intuition: buy a factor when its spread is stretched, lighten when compressed. Intuitive and widely used in practice — but the academic verdict is mixed, and it interacts awkwardly with the value factor itself (timing value on value spreads is nearly circular). The KB holds the skeptical counterweight (Signal D) more firmly than it holds a value-spread timing paper; this is a visible ingestion gap (Asness-Moskowitz-Pedersen; value-spread timing literature).

### Signal C — Regime detection (time the factor by the state)

[[li-episodic-factor-pricing]] identifies pricing-on states in real time using a squared-error-based regime statistic plus LASSO predictors, then scales exposure up in on-states. **Managed portfolios** built this way lift a nine-factor Sharpe from 1.18 to 1.56 — a concrete, sizable timing gain. The method is the most sophisticated conditioning approach in the KB.

### Signal D — The skeptic's reply (near-arbitrage and fragility)

Against all of the above:
- **Near-arbitrage caution.** If factor timing worked as well as naive backtests suggest, it would imply implausibly high Sharpe ratios — a near-arbitrage that shouldn't survive (Haddad-Kozak-Santosh 2020 — not yet held; ingestion candidate). Much apparent timing value is an artifact of in-sample fitting.
- **Spurious-factor cost.** Timing adds parameters, and extra parameters inside a risk model are asymmetrically dangerous — a wrong conditioning factor costs far more than a missed one ([[menchero-factor-alignment]]).
- **Out-of-sample decay.** Conditioning signals that shine in-sample routinely fade live (the general replication concern from [[capm-and-the-cross-section]]).

## The tool: managed (conditional) portfolios

The common machinery across Signals A–C is the **managed portfolio** — a factor whose exposure is scaled over time by a signal $s_t$:

$$w_t = s_t \cdot w^{\text{base}}, \qquad f^{\text{managed}}_{t+1} = s_t \, f^{\text{base}}_{t+1}$$

This is how timing is *operationalized* (and tested): a timed factor is just the base factor interacted with the signal. It is also how [[moskowitz-nonlinear-momentum]]'s S-curve and [[li-episodic-factor-pricing]]'s on-state scaling are built. The elegance is that a managed factor is still a factor — so it slots into the same risk model and attribution machinery ([[risk-model-anatomy]]) as an unmanaged one.

## Practical verdict

A defensible position that the KB's evidence supports:

1. **Timing exists but is modest and fragile.** The honest effect is far smaller than naive backtests show; size it humbly (Signal D).
2. **Prefer robust, economically grounded signals.** Factor momentum (A) and regime conditioning (C) are better supported than valuation-spread timing (B) in *this* KB — though that partly reflects which papers are held.
3. **Diversify across factors first, time second.** Cyclicality means a static multi-factor blend already captures much of the "rotation" benefit by letting factors take turns ([[msci-foundations-of-factor-investing]]).
4. **Watch the parameter budget.** Every timing signal is a factor you've added; price it against the alignment cost ([[menchero-factor-alignment]]) and out-of-sample.
5. **Managed portfolios are the right unit** for both implementing and *testing* timing — if it can't be written as a conditioning weight, it can't be evaluated cleanly.

## Teaching arc (Lecture 2, timing half / bridge to Lecture 3)

1. Premia vary — cyclicality, autocorrelation, episodic pricing (the uncontroversial part).
2. The timing temptation — four signals, ranked by evidence.
3. The skeptic's reply — near-arbitrage, spurious factors, OOS decay.
4. Managed portfolios as the honest test harness.
5. Verdict — diversify first, time humbly, budget your parameters.

## Connections

- [[msci-foundations-of-factor-investing]] — the cyclicality evidence and the case for static multi-factor diversification.
- [[li-episodic-factor-pricing]] — regime/episodic pricing and real-time on-state detection; the KB's most advanced conditioning method.
- [[ehsani-linnainmaa-factor-momentum]] / [[gupta-kelly-factor-momentum-everywhere]] — factor momentum as the best-supported timing signal.
- [[moskowitz-nonlinear-momentum]] — the S-curve as a managed-portfolio weighting.
- [[menchero-factor-alignment]] — the cost of adding (wrong) conditioning factors to a model.
- [[momentum-taxonomy]] — factor timing is momentum applied to factors.
- [[capm-and-the-cross-section]] — replication/decay skepticism that timing must survive.

#concept #factor-timing #cyclicality #regime-switching #managed-portfolios #near-arbitrage #factor-momentum #teaching #lecture-2
