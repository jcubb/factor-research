# Lecture 1 — From the CAPM to the Factor Zoo

> Course material (not a paper). A ~50-minute lecture beat sheet: the cross-section of expected returns, the CAPM and its collapse, the model ladder, and the factor-zoo skepticism. Instructor's main text: [[capm-and-the-cross-section]]. Part of a three-lecture course with [[lecture-2-the-factors]] and [[lecture-3-building-models]].

## At a glance

| | |
|---|---|
| **Duration** | 50 min (≈18 slides) + 10 min Q&A |
| **Level** | Upper-undergrad / intro-MBA finance; assumes basic statistics and the idea of a portfolio |
| **Instructor text** | [[capm-and-the-cross-section]] |
| **Pre-reading for students** | [[capm-and-the-cross-section]] (whole); skim [[sharpe-lintner-capm]] and [[fama-french-factor-models]] §Overview |
| **Prerequisite math** | mean, variance, covariance, a univariate regression |

## Learning objectives

By the end, students can:
1. State the cross-sectional question and distinguish the **risk** vs. **mispricing** lenses.
2. Write and interpret the **CAPM/SML**, and define alpha, beta, and the systematic/specific split.
3. Explain *how* the CAPM fails empirically — the **flat SML** and characteristic anomalies.
4. Describe the **model ladder** (CAPM ⊂ FF3 ⊂ Carhart4 ⊂ FF5) and why "alpha is model-relative."
5. Critically assess the **factor zoo** — multiple testing and replication.

---

## Section A — The question (5 min, slides 1–2)

**Slide 1 · Hook.** Two stocks, same market, wildly different average returns over 20 years. Why? Pose it as *the* question of the course. *(Show two real cumulative-return lines.)*

**Slide 2 · Two lenses.** Every answer is either **risk** (compensation, persists) or **mispricing** (correction, may erode). Put the dichotomy on the board; promise to return to it every lecture.
- Talking point: this is the habit, not a fact to memorize.
- Source: [[capm-and-the-cross-section]] §"The question".

## Section B — The CAPM answer (12 min, slides 3–7)

**Slide 3 · From Markowitz to equilibrium.** One investor optimizing (mean-variance) → everyone optimizing → prices must clear. The leap from portfolio choice to asset *pricing*.

**Slide 4 · The one equation.** $E[R_i]-R_f=\beta_i(E[R_m]-R_f)$, with $\beta_i=\operatorname{Cov}(R_i,R_m)/\operatorname{Var}(R_m)$. Only covariance-with-the-market is priced. Source: [[sharpe-lintner-capm]].

**Slide 5 · Two-fund separation & the SML.** Everyone holds market + riskless asset; draw the SML. Every asset should lie *on* it.

**Slide 6 · The risk split (the idea that outlives the model).** $\sigma_i^2=\beta_i^2\sigma_m^2+\sigma_{\varepsilon_i}^2$ — systematic (priced) vs. specific (diversified away, unpriced). Flag: *this reappears as the backbone of every risk model* ([[lecture-3-building-models]]).

**Slide 7 · Where "alpha" comes from.** The testing regression $R_i-R_f=\alpha_i+\beta_i(R_m-R_f)+\varepsilon_i$; CAPM predicts $\alpha_i=0$. Jensen's alpha = this intercept. *Board definition students will use all course.*

## Section C — The empirical collapse (12 min, slides 8–11)

**Slide 8 · The flat SML.** Realized return rises with beta far less than predicted; positive intercept. *(Show the classic beta-decile scatter with the too-flat fitted line vs. the steeper CAPM line.)* Source: [[fama-french-factor-models]] (1992); mechanism in [[frazzini-pedersen-betting-against-beta]] (preview Lecture 2).

**Slide 9 · Characteristics beat beta.** FF (1992): with size and B/M in the regression, beta's slope is ~flat. Characteristics the CAPM says can't matter, do.

**Slide 10 · The survivors.** Table: Market, Size, Value, Momentum, Profitability, Investment, Low-beta — each with direction and the KB article. Source: [[capm-and-the-cross-section]] §"The empirical collapse".

**Slide 11 · Discussion beat (2 min).** *Ask the room:* is the value premium risk or mispricing? Harvest both sides; show neither is settled.

## Section D — The model ladder (8 min, slides 12–14)

**Slide 12 · Models nest.** CAPM ⊂ FF3 ⊂ Carhart4 ⊂ FF5. Each keeps the zero-alpha regression and adds dimensions. Table of what each adds. Sources: [[fama-french-factor-models]], [[carhart-four-factor-persistence]].

**Slide 13 · Alpha is model-relative.** The punchline: climbing the ladder reclassifies alpha as beta. A CAPM "star" fund may just be a momentum tilt. Forward-link to [[fama-french-luck-vs-skill]] (Lecture 2/assessment).

**Slide 14 · Factors can kill factors.** HML becomes redundant once RMW and CMA enter — value was "profitability + investment in disguise." Adding a factor isn't free. Source: [[fama-french-factor-models]], mechanism [[novy-marx-gross-profitability]].

## Section E — The factor zoo & skepticism (8 min, slides 15–17)

**Slide 15 · The zoo.** Hundreds of published factors. Picture the explosion; name the problem.

**Slide 16 · Multiple testing & replication.** Test enough signals and some clear t>2 by luck; many anomalies decay out-of-sample / post-publication. The honest hurdle is much higher than textbook significance. (Harvey-Liu-Zhu — flag as not-yet-in-KB.)

**Slide 17 · How to judge a new factor.** Checklist: economic story + out-of-sample + international + robust to construction. The MSCI six as the survivor shortlist. Source: [[msci-foundations-of-factor-investing]].

## Section F — Synthesis (5 min, slide 18)

**Slide 18 · Tie-off.** Return to the two lenses: a *risk* premium you hold through drawdowns; a *mispricing* you harvest while watching for decay. Preview Lecture 2 (the individual factors and their dynamics).

---

## In-class discussion questions
1. If the CAPM is "wrong," why is beta still everywhere in practice?
2. A fund shows positive CAPM alpha but zero four-factor alpha. What has it actually done?
3. You find a new signal with t = 2.5 in one backtest. What would convince you it's real?

## Suggested exercise / problem set
- Pull Ken French's data library; regress 10 beta-sorted portfolios on the market; plot realized vs. CAPM-predicted returns → students *reproduce the flat SML*.
- Re-run with FF3 and Carhart4; watch a portfolio's alpha shrink as factors are added (makes "alpha is model-relative" tangible).

## Board-ready equations
- SML: $E[R_i]-R_f=\beta_i(E[R_m]-R_f)$
- Risk split: $\sigma_i^2=\beta_i^2\sigma_m^2+\sigma_{\varepsilon_i}^2$
- Alpha regression: $R_i-R_f=\alpha_i+\beta_i(R_m-R_f)+\varepsilon_i$

## Connections
- [[capm-and-the-cross-section]] — the instructor text this lecture follows section-for-section.
- [[sharpe-lintner-capm]], [[fama-french-factor-models]], [[carhart-four-factor-persistence]], [[novy-marx-gross-profitability]], [[frazzini-pedersen-betting-against-beta]], [[msci-foundations-of-factor-investing]] — the backing evidence per slide.
- [[lecture-2-the-factors]] — the sequel: the factors themselves and their dynamics.
- [[lecture-3-building-models]] — where the risk split and construction choices are developed.

#course #lecture #lecture-1 #cross-section #capm #factor-zoo #teaching
