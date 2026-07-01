# Luck versus Skill in Mutual Fund Returns

> Source: Fama, Eugene F., and Kenneth R. French. "Luck versus Skill in Mutual Fund Returns." *The Journal of Finance* 65, no. 5 (October 2010): 1915–1947.
> DOI: 10.1111/j.1540-6261.2010.01598.x | University of Chicago, Dartmouth College, NBER

## Overview

Fama and French use bootstrap simulations to distinguish luck from skill in the cross-section of US equity mutual fund returns. Their approach compares the actual distribution of fund-level t-statistics of alpha (t(alpha)) against a simulated distribution in which all funds have zero true alpha. If the actual distribution shows fatter tails than the simulated one, some funds must have nonzero true alpha — either positive (skill) or negative (lack of skill).

The headline result is stark: on net returns (after expenses), the distribution of t(alpha) estimates for actual funds is almost always to the left of the simulated zero-alpha distribution. This means that few if any funds have enough skill to cover their costs. The extreme right tail (97th–99th percentile) of net fund returns roughly matches the simulated distribution, suggesting that even the "best" net performers are consistent with luck. In contrast, tests on gross returns (before expense ratios) reveal statistically significant evidence of both positive and negative managerial skill — the tails of the actual distribution are fatter than the simulated distribution on both sides. However, the skill is small in magnitude and concentrated among small funds.

The paper also estimates the likely distribution of true alpha across funds. For the full sample (AUM > $5 million), true gross alpha appears normally distributed with mean zero and standard deviation sigma around 1.25% per year. For larger funds ($250 million and $1 billion groups), the right-tail sigma drops to about 0.75%, indicating that whatever skill exists is more prevalent among small funds. The central message is that the costs of active management — primarily expense ratios — consume whatever value skilled managers create.

## Data and Sample

| Feature | Detail |
|---|---|
| Source | CRSP Survivor-Bias-Free Mutual Fund Database |
| Sample period | January 1984 – September 2006 |
| Inclusion rule | Fund enters sample after reaching $5 million AUM; included thereafter with ≥8 months of returns |
| Fund count (AUM > $5M) | 3,156 funds |
| Fund count (AUM > $250M) | 1,269 funds |
| Fund count (AUM > $1B) | 660 funds |
| Average months per fund | 138 (range: 8 to 273) |
| Benchmark models | CAPM, three-factor (Mkt, SMB, HML), four-factor (+ MOM) |
| Simulation runs | 10,000 bootstrap iterations |

## Equilibrium Accounting Framework

The paper begins from Sharpe's (1991) equilibrium accounting identity: the value-weighted aggregate of all active funds must hold the market portfolio before costs. Therefore:

- VW aggregate alpha of active funds ≈ 0 before costs
- VW aggregate alpha ≈ −expense ratios after costs
- Any fund with positive true alpha must be offset by others with negative true alpha

Empirically, the VW average four-factor alpha for all funds is −0.07% per month net (t = −2.29), closely matching the average expense ratio of 0.08% per month.

## Bootstrap Simulation Methodology

1. Estimate alpha and factor loadings for each fund using the full time series
2. Subtract estimated alpha from each fund's returns to create zero-alpha adjusted returns
3. Draw a random sample of 273 months (with replacement) from the time series
4. Re-estimate alpha for every fund using the resampled months
5. Record the cross-sectional distribution of t(alpha) estimates
6. Repeat 10,000 times to build the null distribution

The joint sampling of fund returns preserves cross-fund correlations, correlations between fund and explanatory returns, and heteroskedasticity — advantages over the independent simulation approach of Kosowski et al. (2006).

## Key Results: Net Returns

| Percentile | Sim t(alpha) | Actual t(alpha) | % Sims < Actual |
|---|---|---|---|
| 1st | −2.30 | −3.44 | 0.22 |
| 2nd | −2.00 | −3.10 | 0.28 |
| 5th | −1.61 | −2.66 | 0.47 |
| 10th | −1.28 | −2.07 | 1.11 |
| 50th (median) | 0.00 | −0.43 | 1.21 |
| 90th | 1.25 | 1.24 | 54.62 |
| 95th | 1.58 | 1.58 | 48.87 |
| 97th | 1.79 | 1.79 | 51.51 |
| 99th | 2.12 | 2.20 | 41.62 |

*Three-factor model, AUM > $5 million group. Four-factor results are similar.*

The actual net return distribution is shifted left at virtually every percentile. Even at the 99th percentile, about 42% of simulations produce t(alpha) values as high as the actual — consistent with luck, not skill.

## Key Results: Gross Returns

| Percentile | Sim t(alpha) | Actual t(alpha) | % Sims < Actual |
|---|---|---|---|
| 1st | −2.30 | −3.14 | 1.42 |
| 2nd | −2.00 | −2.78 | 1.70 |
| 3rd | −1.85 | −2.63 | 1.35 |
| 5th | −1.61 | −2.32 | 2.02 |
| 10th | −1.28 | −1.75 | 4.17 |
| 90th | 1.25 | 1.46 | 28.74 |
| 95th | 1.58 | 2.00 | 14.17 |
| 97th | 1.79 | 2.35 | 8.04 |
| 98th | 1.95 | 2.55 | 7.67 |
| 99th | 2.12 | 2.98 | 3.42 |

*Three-factor model, AUM > $5 million group.*

Both tails of the actual gross return distribution extend beyond the simulated distribution. In the left tail, actual funds are worse than simulated in ~98% of runs (evidence of truly unskilled managers). In the right tail, actual funds beat simulated in ~92-97% of runs at the 97th–99th percentiles (evidence of truly skilled managers before costs).

## Estimating the Distribution of True Alpha

The paper injects normally distributed true alpha (mean zero, standard deviation sigma) into simulated fund returns and varies sigma to find values consistent with the actual distribution.

| AUM Group | Left-tail sigma estimate | Right-tail sigma estimate |
|---|---|---|
| > $5 million | 1.25% p.a. | 1.25% p.a. |
| > $250 million | 1.25% p.a. | 0.75% p.a. |
| > $1 billion | 1.25% p.a. | 0.25–1.25% p.a. |

With sigma = 1.25% per year:
- About 1 in 6 funds has true gross alpha > 1.25% p.a. (~10 bps/month)
- Only ~2.4% have true alpha > 2.50% p.a. (~21 bps/month)
- The average imprecision of individual fund alpha estimates is 3.4% p.a. (0.28%/month), dwarfing the true skill signal

The right-tail sigma is markedly lower for large funds, indicating that skill is concentrated among smaller, less scalable operations.

## Comparison with Kosowski et al. (2006)

| Feature | Fama & French (2010) | Kosowski et al. (2006) |
|---|---|---|
| Simulation approach | Joint sampling of fund returns | Independent sampling per fund |
| Survival rule | 8 months after $5M AUM | 60 months (more survival bias) |
| Period focus | 1984–2006 | 1975–2002 |
| Conclusion on net returns | Almost no skill to cover costs | Strong evidence of skill at 95th+ percentile |
| Key methodological difference | Preserves cross-fund correlations and joint distribution of fund/factor returns | Does not capture cross-fund correlation or joint factor dynamics |

When Fama & French replicate Kosowski et al.'s approach using the earlier (1975–2002) period and their inclusion rules, the 95th percentile of net four-factor t(alpha) beats 82% of simulations (vs. Kosowski's 99%). The remaining gap is explained by Kosowski's 60-month survival rule (which introduces survival bias) and independent sampling.

## CAPM as a Misleading Benchmark

The CAPM bootstrap produces strikingly different results from the three- and four-factor tests: CAPM t(alpha) values for actual funds typically beat 80%+ of simulations at high percentiles, seemingly implying widespread skill. This is an artifact:

- Funds with size, value, or momentum tilts earn positive CAPM alpha mechanically
- The three- and four-factor models control for these common return patterns
- The CAPM simulations correctly wash out the common patterns by subtracting estimated alpha, so the gap between actual and simulated CAPM t(alpha) reflects the factors' average returns, not skill

## Implications for Practice

1. **Active management destroys value in aggregate**: The VW average net alpha is approximately equal to the negative of the average expense ratio. Whatever skill exists is consumed by fees.
2. **Skill exists but is small and hard to identify**: Gross return tests show statistically significant positive and negative skill, but the dispersion of true alpha (~1.25% p.a.) is smaller than the measurement noise (~3.4% p.a.). Identifying skilled managers ex ante is nearly impossible from return data alone.
3. **Skill does not scale**: The right-tail sigma drops from 1.25% to 0.75% (or lower) as the AUM filter increases from $5 million to $1 billion. This is consistent with Berk and Green's (2004) model of decreasing returns to scale in active management.
4. **Benchmark model matters enormously**: CAPM-based performance evaluation produces misleading conclusions about skill because it does not control for common factor tilts. Multi-factor benchmarks are essential.
5. **Bootstrap methodology matters**: Joint sampling of fund returns (preserving cross-fund correlations) produces more conservative estimates of skill than independent sampling approaches.
6. **The 1975–2002 period overstates skill**: Evidence of skill is stronger in the earlier period, possibly due to fewer funds, data biases, or a genuinely more favorable environment for active management. The 1984–2006 period is more relevant for current investors.

## Connections

- [[fama-french-factor-models]] — The FF three-factor and four-factor (with Carhart momentum) models are the primary benchmarks for the bootstrap simulations. The paper demonstrates that using these multi-factor models rather than the CAPM is critical for correctly evaluating fund performance — CAPM tests spuriously indicate skill because they miss size, value, and momentum tilts that passive funds can replicate.
- [[msci-foundations-of-factor-investing]] — MSCI's factor indexation approach provides the practical counterpoint: if size, value, momentum, and quality premia can be harvested through low-cost factor indexes, the case for active management is even weaker than Fama & French's results suggest. The factors that generate spurious CAPM alpha are exactly what factor indexes capture systematically.
- [[ehsani-linnainmaa-factor-momentum]] — Ehsani & Linnainmaa show that momentum is a byproduct of factor autocorrelation rather than a distinct source of return. This has implications for fund evaluation: a manager who appears to time momentum may simply be loading on persistent factor returns, which would show up as positive gross alpha in Fama & French's tests without representing true stock-picking skill.
- [[frazzini-pedersen-betting-against-beta]] — BAB documents that leverage-constrained investors overpay for high-beta assets. Mutual funds, as leverage-constrained vehicles, are precisely the investors whose behavior creates the BAB anomaly. Fama & French's finding that fund skill does not scale is consistent with the leverage constraints that Frazzini & Pedersen model.

#mutual-fund-performance #bootstrap #luck-vs-skill #alpha #active-management #expense-ratios #benchmark-models #simulation #manager-selection #CAPM-bias
