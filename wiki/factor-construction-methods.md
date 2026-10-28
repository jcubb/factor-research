# Factor Construction — From Characteristic to Factor Return

> Concept synthesis (not a single paper). Explains how a raw stock characteristic becomes a tradable factor return, and why the "same" factor has different returns in different hands. Companion reading: [[start-here]] Stage 4.

A factor is not a number you look up — it is a *portfolio* you build, and the build choices change the answer. This article walks the pipeline from a raw characteristic (say, book-to-market) to a factor return, flags the decision at each step, and explains the KB's central construction result: **Fama-French factor returns and Barra factor returns for the "same" characteristic are genuinely different objects.** It is the most directly transferable concept article for anyone building a cross-sectional model.

## The pipeline

$$\text{raw characteristic} \;\to\; \text{standardized exposure} \;\to\; \text{factor-forming rule} \;\to\; \text{factor return } f_t$$

Every arrow hides a choice. The two families of factor-forming rule — **sorts** and **cross-sectional regression** — are the fork that produces "simple" vs. "pure" factors.

## Step 1 — Define and standardize the exposure

Before any portfolio, the characteristic must be made comparable across stocks and over time:

- **Winsorize / clip** extreme values (a few microcaps can dominate an unstandardized signal).
- **Standardize** — z-score or rank-standardize cross-sectionally so the factor is unit-scaled.
- **Center** — subtract a cross-sectional mean so zero exposure = "average stock." *Which* mean matters: an **equal-weighted** mean vs. a **cap-weighted** mean put "zero" in different places. Cap-weighted demeaning makes the market portfolio have zero style tilt — the right convention when the downstream model uses a cap-weighted market/sum-to-zero constraint. Mixing equal-weighted centering with cap-weighted constraints is a silent inconsistency.
- **Handle the denominator.** Ratios with small/near-zero denominators (ROE on tiny book equity) explode; prefer robust definitions (e.g. gross-profits-to-assets, [[novy-marx-gross-profitability]]).

This step is where "weighting coherence end to end" is won or lost: centering, regression weights, and aggregation must all use the same weighting scheme or the pieces won't reconcile.

## Step 2 — The factor-forming rule

### Route A — Sorts (the Fama-French way)

Rank stocks on the characteristic, form bucket portfolios, and take a long-short spread. The canonical recipe ([[fama-french-factor-models]]): a 2×3 sort on size × characteristic, then **high-minus-low**:

$$\text{HML} = \tfrac{1}{2}(\text{Small-High} + \text{Big-High}) - \tfrac{1}{2}(\text{Small-Low} + \text{Big-Low})$$

- **Pros:** transparent, non-parametric, robust, reproducible.
- **Cons:** the resulting portfolio carries *incidental* exposures to everything correlated with the sort (a value sort is also short profitability, long small-cap, etc.). These are **"simple" factor portfolios** ([[menchero-characteristics-factor-portfolios]]).

### Route B — Cross-sectional regression (the Barra way)

Regress the period's stock returns on *all* exposures at once:

$$r_t = X_t f_t + u_t$$

where $X_t = [\,\text{market} \mid \text{industries} \mid \text{countries} \mid \text{styles}\,]$. Each estimated $f_t$ is a **"pure" factor return** — the return to the characteristic *holding every other factor fixed* (Frisch-Waugh-Lovell). A pure value factor is net of its industry, country, and other-style loadings.

- **Pros:** clean, mutually orthogonal factors; exactly what a risk model needs ([[risk-model-anatomy]]).
- **Cons:** requires the full exposure matrix and care with collinearity (next section).

## Step 3 — Weighting the regression

In Route B, *how* you weight the cross-sectional regression changes the factor return materially — not a rounding effect:

| Weighting | Rationale | KB note |
|---|---|---|
| Equal | simple | noisy; microcap-driven |
| Cap | matches market portfolio | — |
| **Root-cap** ($\sqrt{\text{cap}}$) | GLS compromise; specific variance ∝ 1/size | Barra default |
| **Inverse specific variance** | GLS-optimal; minimizes factor-portfolio volatility | [[msci-risk-return-factor-portfolios]] |

[[msci-risk-return-factor-portfolios]] shows these choices move factor returns by **>300 bps for Momentum**. Weighting is a first-order modeling decision, not plumbing.

## Step 4 — Identification: the collinearity trap

Route B has a structural pitfall when the design includes exhaustive categorical blocks (industries, countries). Each exhaustive partition sums to the vector of ones, so it is **collinear with the intercept** — the design is rank-deficient (deficiency equal to the number of such partitions). Dropping the constant does *not* fix it. The standard, closed-form resolutions:

- **Sum-to-zero (effects) constraints** — the finance standard; the market/world return is the grand mean and each industry/country factor is a pure deviation summing to zero against the (cap-weighted) market. This is the Heston-Rouwenhorst world-plus-pure-effects split.
- **Reference-cell coding** — drop one category; coefficients become gaps vs. the baseline (less interpretable for decompositions).
- **Bordered KKT / restricted least squares** — keep all columns, add the constraint rows; one linear solve, every category survives as a named factor.

All linear equality constraints are **closed form** — no numerical optimization (that's only needed for *inequality* constraints). Styles need no constraint once centered. The identification weakens (but doesn't break) when a category lives in one place only — e.g. an industry present in a single country.

## Simple vs. pure — the central result

The two routes produce different objects for the *same* named characteristic:

| | Simple (sort) | Pure (regression) |
|---|---|---|
| Controls for other factors? | No — incidental exposures | Yes — all simultaneously |
| Interpretation | raw characteristic spread | effect *holding others fixed* |
| Used by | Fama-French, academic | Barra, risk models |
| Agreement | diverges most for **styles** (weight corr 0.70–0.90) | — |

[[menchero-characteristics-factor-portfolios]] quantifies the gap (weight correlation, return correlation, leverage ratio) and shows styles diverge most. This is **why FF factor returns ≠ Barra factor returns** even for "the same" value factor — and why cross-model alpha comparisons require care. [[novy-marx-gross-profitability]] is a worked example of the payoff of control: *industry-adjusted* value/momentum/profitability prices far more of the anomaly zoo than raw sorts.

## Orthogonalization (a related but distinct tool)

Even within a factor set you can **orthogonalize** — strip one factor's influence from another so exposures don't overlap (e.g. make a "pure" momentum net of value). [[menchero-characteristics-factor-portfolios]] uses constrained/NLS orthogonalization. Note the asymmetry: orthogonalizing *A on B* is not the same as *B on A*; the order encodes an economic choice about which factor is primary.

## Teaching arc (Lecture 3, construction half)

1. A factor is a portfolio — the pipeline and its decision points.
2. Standardization and the weighting-coherence trap.
3. Sorts vs. regression — simple vs. pure factors (the central distinction).
4. Weighting and identification — why >300 bps rides on choices, and the collinearity/constraint machinery.
5. Payoff — why FF ≠ Barra, and why control (industry-adjustment, orthogonalization) matters.

## Connections

- [[menchero-characteristics-factor-portfolios]] — the definitive simple-vs-pure treatment; collinearity metrics and orthogonalization.
- [[msci-risk-return-factor-portfolios]] — how regression weighting moves factor returns (>300 bps for momentum).
- [[fama-french-factor-models]] — the canonical sort-based (simple) construction.
- [[novy-marx-gross-profitability]] — industry-adjusted construction as a worked payoff of control; robust-denominator profitability.
- [[menchero-factor-alignment]] — the risk of putting badly-constructed/spurious factors into a model.
- [[risk-model-anatomy]] — where the pure factor returns from Route B feed in.
- [[capm-and-the-cross-section]] — the factors being constructed and the model ladder they populate.

#concept #factor-construction #simple-vs-pure #cross-sectional-regression #sorts #regression-weighting #standardization #orthogonalization #collinearity #constraints #teaching #lecture-3
