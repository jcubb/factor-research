# Lecture 3 — Building and Using Factor Models

> Course material (not a paper). A ~50-minute lecture beat sheet: how a characteristic becomes a factor return (simple vs. pure), the identification/constraint machinery, the four components of a commercial risk model, covariance estimation, and using the model for attribution/VaR/optimization. Instructor's main texts: [[factor-construction-methods]] and [[risk-model-anatomy]]. Finale of a three-lecture course ([[lecture-1-cross-section]] → [[lecture-2-the-factors]] → this).

## At a glance

| | |
|---|---|
| **Duration** | 50 min (≈18 slides) + 10 min Q&A |
| **Level** | Upper-undergrad / intro-MBA; the most technical of the three — assumes comfort with regression and matrices |
| **Instructor texts** | [[factor-construction-methods]], [[risk-model-anatomy]] |
| **Pre-reading for students** | both instructor texts; skim [[menchero-characteristics-factor-portfolios]] and [[barra-use3-handbook]] §Overview |
| **Recap needed** | the systematic/specific split from [[lecture-1-cross-section]] |

## Learning objectives

By the end, students can:
1. Walk the **construction pipeline** and distinguish **simple** (sort) from **pure** (regression) factors.
2. Explain why **regression weighting** and **identification constraints** change the factor return.
3. Name the **four components** of a risk model and the one equation linking them.
4. Describe how a **factor covariance matrix** is cleaned (the eigen-thread).
5. Use the model: **risk attribution, VaR, and the optimization/alignment pitfall.**

---

## Section A — A factor is a portfolio you build (10 min, slides 1–4)

**Slide 1 · Reframe.** Lectures 1–2 treated factors as given. Today: a factor is a *portfolio*, and the build choices change the number. Source: [[factor-construction-methods]].

**Slide 2 · The pipeline.** raw characteristic → standardized exposure → factor-forming rule → factor return. Every arrow is a decision.

**Slide 3 · Standardize first.** Winsorize, z-score/rank, and **center** — and *which* mean matters (equal- vs. cap-weighted). "Weighting coherence end to end": centering, regression weights, and aggregation must agree. Robust denominators (gross-profits-to-assets, not ROE on tiny book equity).

**Slide 4 · Two routes to a factor.** Route A sorts (Fama-French 2×3 HML); Route B cross-sectional regression $r_t=X_tf_t+u_t$. *Set up the simple-vs-pure contrast.*

## Section B — Simple vs. pure, weighting, identification (12 min, slides 5–9)

**Slide 5 · Simple vs. pure.** Sort portfolios carry *incidental* exposures; regression factors are *pure* (net of everything else, via Frisch-Waugh-Lovell). Table of differences. Source: [[menchero-characteristics-factor-portfolios]].

**Slide 6 · Why FF ≠ Barra.** The same "value factor" differs across methods (weight corr 0.70–0.90 for styles). This is why cross-model alpha comparisons need care. Source: [[menchero-characteristics-factor-portfolios]].

**Slide 7 · Weighting is first-order.** Equal / cap / root-cap / inverse-specific-variance — moves factor returns by **>300 bps for momentum**. Not plumbing. Source: [[msci-risk-return-factor-portfolios]].

**Slide 8 · The identification trap.** Exhaustive industry/country dummies each sum to the ones vector → collinear with the intercept → rank-deficient. Dropping the constant does *not* fix it. *(Board: show two dummy blocks both summing to 1.)*

**Slide 9 · The fix is closed-form.** Sum-to-zero (effects) constraints = the finance standard (world mean + pure deviations); or bordered KKT keeping every category as a named factor. Linear equality constraints never need optimization. Source: [[factor-construction-methods]] §"Identification".

## Section C — Anatomy of a risk model (10 min, slides 10–13)

**Slide 10 · The job.** Millions of pairwise covariances → collapse through a few factors. Source: [[risk-model-anatomy]].

**Slide 11 · The one equation.** $\Sigma_{\text{assets}} = X\,\Sigma_F\,X' + \Delta$. Four objects: exposures $X$, factor covariance $\Sigma_F$, specific risk $\Delta$ (diagonal). Connect $\Delta$ back to Lecture 1's "specific risk."

**Slide 12 · Components 1–2.** Exposures $X$ (styles + industry/country dummies, from Section B) and factor returns $f$ (the cross-sectional GLS regression, with constraints).

**Slide 13 · Component 4 — specific risk.** Modeled, not just sampled: time-series + structural + shrinkage. *The twist:* this "noise" is where a skilled manager's real edge lives → forward-link to manager evaluation ([[harmsworth-idiosyncratic-alpha]]).

## Section D — Cleaning the covariance matrix (10 min, slides 14–16)

**Slide 14 · The eigen-picture.** A covariance matrix = rotation (eigenvectors) + scaling (eigenvalues) of white data. *(Show the ellipse figure.)* Source: [[spruyt-geometric-covariance-matrix]].

**Slide 15 · Cleaning $\Sigma_F$.** EWMA (recency) → GARCH / vol-regime adjustment (crises) → differential half-lives (vol moves faster than correlation) → **eigenfactor adjustment** / **RMT denoising** (keep eigenvectors, fix eigenvalues). Table. Sources: [[barra-use4-methodology]], [[mossessian-robust-covariance-estimation]], [[cuffe-barra-market-factor]].

**Slide 16 · One thread.** geometry → RMT → USE4 eigenfactor adjustment → Kelly's SVD are the *same move*. The KB's deepest technical through-line. Source: [[risk-model-anatomy]] §Component 3.

## Section E — Using the model (8 min, slides 17–18)

**Slide 17 · Attribution, VaR, optimization.** $\sigma_p^2=w'\Sigma w$ decomposed; attribution pitfalls (use benchmark-relative sources + a World factor — [[davis-menchero-pitfalls-risk-attribution]]); short-horizon VaR ([[barbieri-var-with-factors]]). **The optimization danger:** optimizers exploit exactly the directions the model gets wrong; a *spurious* factor costs far more than a missing one ([[menchero-factor-alignment]]) — which is *why* eigenfactor adjustment exists.

**Slide 18 · Course tie-off.** Barra USE3 → USE4 → GEM *are* Components 1–4 refined over three generations. Loop back to Lecture 1: it all generalizes one CAPM idea — systematic vs. specific. Sources: [[barra-use3-handbook]], [[barra-use4-methodology]], [[barra-gem-handbook]].

---

## In-class discussion questions
1. Your "pure" momentum factor and French's UMD disagree in a given month. Who's right?
2. Why can't you just use the sample covariance matrix of 50 factor returns?
3. An optimizer hands you a portfolio with suspiciously low forecast risk. What do you suspect?

## Suggested exercise / problem set
- Given a tiny cross-section (say 6 stocks, 2 industries, 1 style), have students **build $X$**, hit the rank-deficiency, and resolve it with effects coding *by hand* — then confirm the bordered-KKT solve matches. (Directly exercises [[factor-construction-methods]] §Identification.)
- Take 10 factor return series; compare sample $\Sigma_F$ vs. an EWMA/shrunk version in a mean-variance optimization; show how the naive one produces extreme, fragile weights.

## Board-ready equations
- Cross-sectional model: $r_t = X_t f_t + u_t$
- Risk decomposition: $\Sigma_{\text{assets}} = X\,\Sigma_F\,X' + \Delta$
- Portfolio risk: $\sigma_p^2 = w'\Sigma_{\text{assets}}\,w$

## Connections
- [[factor-construction-methods]], [[risk-model-anatomy]] — the two instructor texts this lecture follows.
- [[menchero-characteristics-factor-portfolios]], [[msci-risk-return-factor-portfolios]] — construction and weighting evidence.
- [[barra-use3-handbook]], [[barra-use4-methodology]], [[barra-gem-handbook]], [[cuffe-barra-market-factor]] — the risk model worked example.
- [[spruyt-geometric-covariance-matrix]], [[mossessian-robust-covariance-estimation]] — the covariance/eigen material.
- [[davis-menchero-pitfalls-risk-attribution]], [[barbieri-var-with-factors]], [[menchero-factor-alignment]], [[harmsworth-idiosyncratic-alpha]] — using the model.
- [[lecture-1-cross-section]] / [[lecture-2-the-factors]] — the earlier lectures this builds on.

#course #lecture #lecture-3 #factor-construction #risk-model #covariance #teaching
