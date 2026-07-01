# Factor Research Wiki — Index

> Compiled: 2026-05-13 | Updated: 2026-07-01 | Sources: 31 raw files | Wiki articles: 25 compiled, 3 educational (no article), 3 duplicates/other

## Getting Started

New here? Two on-ramp files:
- **[[start-here]]** — a staged reading path from foundational intuition to advanced methods, with what each article teaches and why.
- **[[glossary]]** — plain-language definitions of the recurring terms (factor, loading, eigenvalue, tracking error, VaR, EWMA, etc.).

## Source Documents

| File | Authors / Year | Status | Key Content |
|---|---|---|---|
| VERDELHAN-2018-SystematicExchangeRates.pdf | Verdelhan (2018) | ✅ | Carry and dollar factors explain 18–80% of bilateral FX variation; two global shocks in SDFs |
| Ehsani22 - Factor Momentum and the Momentum Factor.pdf | Ehsani & Linnainmaa (2022) | ✅ | Momentum is not a distinct factor — it times other factors; factor autocorrelation drives stock momentum |
| NonLinear_Momentum_Moskowitz25.pdf | Moskowitz, Sabbatucci, Tamoni & Uhl (2025) | ✅ | S-shaped nonlinear weighting for TSMOM signals; outperforms linear/binary across asset classes |
| FamaFrench92_Cross-Section_of_Expected_Stock_Returns.pdf | Fama & French (1992) | ✅ | Size and B/M explain cross section; beta is flat — covered in combined article |
| FamaFrench93_CommonFactors.pdf | Fama & French (1993) | ✅ | Three-factor model (Mkt, SMB, HML) for stocks and bonds — covered in combined article |
| famafrench5factor_Sep14.pdf | Fama & French (2015) | ✅ | Five-factor model adds RMW (profitability) and CMA (investment) — covered in combined article |
| FamaFrench-LuckvSkill-JF10.pdf | Fama & French (2010) | ✅ | Bootstrap simulations: few funds have skill to cover costs; true alpha σ ≈ 1.25% p.a. |
| Betting Against Beta - Frazzini and Pedersen.pdf | Frazzini & Pedersen (2014) | ✅ | BAB factor — leveraging low-beta assets produces alpha; funding liquidity risk; five model propositions |
| Factor Momentum Everywhere JPM Quant 19.pdf | Gupta & Kelly (2019) | ✅ | TSFM (SR 0.84) dominates UMD and INDMOM; 65 factors; avoids 2009 crash; works internationally |
| KELLY22 - Principal Portfolios.pdf | Kelly et al. (2022) | ✅ | Principal portfolios via SVD of prediction matrix; PEPs (beta) and PAPs (alpha); doubles tangency SR |
| KELLY22_PrincPort_internetappendix.pdf | Kelly et al. (2022) | ✅ | Internet appendix for Principal Portfolios (covered in main article) |
| Bektic17_FamaFrenchCorpBonds.pdf | Bektic et al. (2017) | ✅ | FF factors in corporate bonds: strong in HY, weak in IG; Merton model linkage |
| houweling14_FactorsCorpBonds.pdf | Houweling & van Zundert (2014) | ✅ | Bond-only factor definitions (Size, Low-Risk, Value, Momentum); multi-factor doubles SR; adds ~1% alpha beyond equity factors |
| FactorB.pdf | Jun Yu (2015) | ❌ Duplicate | Duplicate of Factors_KalmanFilter_2015.pdf |
| factormodels_lecture7.pdf | Papanikolaou (Kellogg FIN460) | ❌ Educational | Lecture slides: three approaches to factor selection (macro, fundamental, statistical/PCA), factor timing; 52 slides |
| Factors_KalmanFilter_2015.pdf | Jun Yu (2015) | ❌ Educational | ECON671 lecture slides: Kalman filter for dynamic factor models, state-space estimation, MLE, applications to interest rates and stochastic volatility; 68 slides |
| JMenchero-Alpha-Risk-Factor-Misalignment-LQG.pdf | Lee & Menchero (MSCI Barra) | ✅ | Factor alignment effects: TC asymmetry — including spurious factor (−19 pp TC) far worse than omitting valid one (−3 pp TC) |
| menchero10_CharFactorPorts.pdf | Menchero (2010) | ✅ | Simple vs. pure factor portfolios; collinearity measures; orthogonalization; GEM2 style factor sector decomposition |
| barbieri09_ModelVaRwithFactors.pdf | Barbieri et al. (2009) | ✅ | DFR method for short-horizon VaR; matches EWMA accuracy; factor decomposition; horizon-dependent global model |
| Cuffe11_BarraMarketFactor.pdf | Cuffe (2011) | ✅ | USE3→USE4: market factor improves correlation responsiveness; differential half-lives; 2008 crisis evidence |
| cohen08_EconomicLinks.pdf | Cohen & Frazzini (2008) | ✅ | Customer momentum: 150 bps/month alpha from supply-chain links; limited attention mechanism |
| Li26_FactorTiming.pdf | Li, Yuan & Zhou (2026) | ✅ | Episodic factor pricing: on/off regimes detected via SED + LASSO; premia concentrated in pricing-on states; managed portfolios boost SR 1.18→1.56; 211-factor breadth is procyclical |
| barra_handbook_USE3.pdf | BARRA Inc. (1998) | ✅ | US-E3 handbook: 65-factor structure (52 industries + 13 risk indices), GLS estimation, EWMA covariance with GARCH, three-component specific risk |
| USE4_Methodology_Notes_August_2011.pdf | Menchero, Orr & Wang (MSCI, 2011) | ✅ | USE4 methodology: eigenfactor risk adjustment, volatility regime adjustment, Country factor, Bayesian shrinkage, EM for missing returns |
| barra_handbook_gem.pdf | BARRA Inc. (1989/1998) | ✅ | GEM handbook: global multi-factor model with 48–51 countries, 36–38 industries, 4 styles, currency covariance, GARCH scaling |
| DavisMenchero11_PitfallsRiskAttrib.pdf | Davis & Menchero (MSCI, 2011) | ✅ | Pitfalls in risk attribution: absolute vs. relative return sources; World factor converts industry factors from net-long to dollar-neutral |
| Research_Insight_Risk_and_Return_of_Factor_Portfolios_March_2013.pdf | Menchero & Ji (MSCI, 2013) | ✅ | Regression weighting impact on USE4 factor portfolios: inverse specific variance minimizes volatility; return differences exceed 300 bps for Momentum |
| Foundations_of_Factor_Investing.pdf | Bender, Briand, Melas & Subramanian (MSCI, 2013) | ✅ | Six equity risk premia factors; why premia persist; factor cyclicality; factor indexes vs. market cap |
| A geometric interpretation of the covariance matrix.pdf | Spruyt (visiondummy, 2014) | ✅ | Covariance matrix as rotation+scaling of white data; Σ = TTᵀ, T = RS; eigenvectors = orientation, eigenvalues = spread |
| Robust Estimation of Risk Factor Model Covariance Matrix.pdf | Mossessian & Vieli (FactSet, 2017) | ✅ | RMT eigenvalue regularization; Marchenko–Pastur support region denoising; guarantees positive-definite matrix; regularization raises VaR |
| a-cut-above-why-idiosyncratic-alpha-is-better-than-beating-the-benchmark.pdf | Harmsworth & Mand (AllianceBernstein, 2022) | ✅ | Idiosyncratic alpha (alpha net of factor betas) is more persistent and predictive than excess return; manager selection + fund-portfolio construction; 30,000-manager database |

## Wiki Articles

### Momentum & Factor Dynamics
- [[ehsani-linnainmaa-factor-momentum]] — Factor momentum subsumes stock momentum; factors are autocorrelated; momentum = timing other factors
- [[moskowitz-nonlinear-momentum]] — Nonlinear S-curve weighting for TSMOM signals; Ferson-Siegel theory; neural nets confirm S-shape
- [[gupta-kelly-factor-momentum-everywhere]] — TSFM (SR 0.84) across 65 factors; dominates UMD and INDMOM; avoids 2009 crash; works internationally

### Currency & International
- [[verdelhan-systematic-exchange-rates]] — Carry and dollar factors in bilateral exchange rates; two global shocks required in SDFs

### Foundational Factor Models
- [[msci-foundations-of-factor-investing]] — MSCI practitioner overview: six risk premia factors (Value, Size, Momentum, Low Vol, Yield, Quality); cyclicality; factor indexation; systematic risk vs. behavioral explanations
- [[fama-french-factor-models]] — FF (1992): flat SML, size and B/M dominate beta; FF (1993): three-factor model (Mkt, SMB, HML) for stocks and bonds; FF (2015): five-factor model adds RMW and CMA; HML becomes redundant in five-factor world
- [[frazzini-pedersen-betting-against-beta]] — BAB factor: leverage-constrained investors bid up high-beta assets → flat SML; BAB Sharpe 0.78 across US equities 1926–2012; works in 20 equity markets, Treasuries, credit, and futures

### Corporate Bond Factors
- [[bektic-fama-french-corporate-bonds]] — FF factors extend to HY bonds (all four significant, multi-factor SR +30%); weak in IG; profitability reverses sign in IG; Merton model linkage
- [[houweling-vanzundert-factor-investing-corporate-bonds]] — Bond-only factor definitions (Size, Low-Risk, Value, Momentum); multi-factor doubles SR in IG and HY; adds ~1% alpha beyond equity factors in multi-asset context

### Barra Risk Model Methodology
- [[barra-use3-handbook]] — US-E3 (1998): 65-factor model (52 industries + 13 risk indices), GLS factor return estimation, EWMA covariance with 90-month half-life, asymmetric GARCH for market volatility, three-component specific risk (time-series, structural, cap-decile scaling)
- [[barra-use4-methodology]] — USE4 (2011): eigenfactor risk adjustment (Monte Carlo eigenvalue correction), volatility regime adjustment (cross-sectional bias scaling), explicit Country factor with differential half-lives, Bayesian shrinkage for specific risk, EM for missing returns, USE4S/USE4L variants
- [[barra-gem-handbook]] — GEM (1989/1998): global multi-factor model with 48–51 countries, 36–38 industries, 4 style risk indices (Size, Success, Value, VIM), exponential weighting with 48-month half-life, selective GARCH, separate currency covariance
- [[davis-menchero-pitfalls-risk-attribution]] — Absolute return sources in risk attribution produce misleading results (zero cash risk, universally negative MCARs); switching to benchmark-relative sources at sector/security/factor level resolves all pitfalls; World factor converts industry factors from net-long to dollar-neutral
- [[msci-risk-return-factor-portfolios]] — Regression weighting impact on USE4 style factor portfolios: four schemes (market-cap, root-cap, equal, inverse specific variance); inverse specific variance minimizes volatility for all factors; return differences exceed 300 bps for Momentum

### Covariance Estimation & Linear Algebra
- [[spruyt-geometric-covariance-matrix]] — Geometric intuition: any covariance matrix is a rotation+scaling of white data (Σ = TTᵀ, T = RS); eigenvectors give orientation, eigenvalues give spread; foundation for PCA, eigenfactor adjustment, RMT denoising
- [[mossessian-robust-covariance-estimation]] — RMT regularization of factor covariance matrices: Marchenko–Pastur support region separates signal from noise eigenvalues; keep eigenvectors, discard noise eigenvalues, reset diagonal to ones; guarantees positive definiteness; regularization raises VaR by removing spurious diversification

### Factor Construction & Risk
- [[menchero-factor-alignment]] — Factor alignment effects in portfolio construction: TC asymmetry (spurious factor inclusion costs −19 pp vs. valid factor omission costs −3 pp); simple/pure/min-vol factor portfolios; alpha decomposition into spanned and residual components
- [[menchero-characteristics-factor-portfolios]] — Simple vs. pure factor portfolios; collinearity metrics (weight correlation, return correlation, leverage ratio); orthogonalization (NLS); sector decomposition of style returns
- [[barbieri-var-with-factors]] — DFR method adapts Barra factor models to daily VaR; matches EWMA accuracy with full risk decomposition; DFR-1B for 1-day, DFR-MB for 2–10 day, scaled BIM for >10 day; non-synchronous trading effects
- [[cuffe-barra-market-factor]] — USE3→USE4: explicit market factor enables differential half-lives for market volatility vs. industry correlations; dramatically improves crisis responsiveness

### Advanced Methods
- [[kelly-principal-portfolios]] — SVD of prediction matrix yields PPs; PEPs (beta) and PAPs (factor-neutral alpha); doubles tangency SR; rejects FF5 via positivity test
- *(educational — no article)* Jun Yu, Kalman filter factor estimation lecture slides
- *(educational — no article)* Papanikolaou, Multifactor models in practice lecture slides
- [[li-episodic-factor-pricing]] — Episodic factor pricing: factors switch between pricing-on/off states; LASSO-predicted SED identifies regimes in real time; managed portfolios boost nine-factor SR from 1.18 to 1.56; 211-factor breadth is procyclical; Comb_on signal combination doubles H-L spread vs. naive

### Cross-Asset & Links
- [[cohen-frazzini-economic-links]] — Customer momentum: 150 bps/month alpha from supply-chain links (SFAS 131); limited attention mechanism; COMOWN proxy for inattention

### Fund Performance
- [[fama-french-luck-vs-skill]] — Bootstrap simulations show few funds cover costs net of fees; true alpha σ ≈ 1.25% p.a.; skill concentrated in small funds; CAPM benchmark is misleading
- [[harmsworth-idiosyncratic-alpha]] — Idiosyncratic alpha (active return net of commoditized factor betas) is more persistent (IA coeff 0.15 vs 0.04 for excess return) and more predictive of future active return than trailing performance; top-IA managers beat benchmarks 75% of the time; combining funds on aggregate + diversified + factor-neutral IA yields best portfolios (+1.64% 5yr fwd)

## Key Themes & Cross-Links

- **Factor momentum ↔ Stock momentum**: Ehsani & Linnainmaa show stock momentum is a byproduct of factor autocorrelation. The FF factor zoo (SMB, HML, RMW, CMA) is the universe over which this momentum is documented. [[ehsani-linnainmaa-factor-momentum]] → [[fama-french-factor-models]]
- **Linear vs. nonlinear signals**: Moskowitz et al. show the optimal TSMOM signal is an S-curve, not a line or sign function. The NL effect applies to factor momentum strategies too. [[moskowitz-nonlinear-momentum]] → [[ehsani-linnainmaa-factor-momentum]]
- **Carry factor across markets**: Verdelhan's carry factor in FX parallels the value/carry concept in equities and bonds. [[verdelhan-systematic-exchange-rates]]
- **MSCI foundations → everything**: The six-factor taxonomy in [[msci-foundations-of-factor-investing]] provides the practitioner map for the academic factors studied in all other papers. Its cyclicality analysis motivates the timing strategies in Ehsani & Linnainmaa and the signal-weighting improvements in Moskowitz et al. The MSCI Low Volatility factor is the practitioner analog of the BAB factor in [[frazzini-pedersen-betting-against-beta]].
- **Flat SML**: FF (1992) establishes the flat security market line empirically for US stocks. BAB provides the theoretical mechanism (leverage constraints) and extends the flat SML to 20 equity markets, Treasuries, corporate bonds, and futures. [[fama-french-factor-models]] → [[frazzini-pedersen-betting-against-beta]]
- **Two global shocks**: Verdelhan's finding that SDFs need two global shocks connects to the multi-factor structure documented by Fama-French and extended to bonds by Bektic/Houweling.
- **HML redundancy**: FF (2015) shows HML's average return is explained by its RMW and CMA loadings in the five-factor model. This connects to Ehsani & Linnainmaa: if HML is redundant when profitability and investment are included, then "value momentum" strategies may be proxying for momentum in profitability/investment signals. [[fama-french-factor-models]] → [[ehsani-linnainmaa-factor-momentum]]
- **Principal components**: Both Ehsani & Linnainmaa (high-eigenvalue PCs drive momentum) and Kelly (principal portfolios) use PCA as a core tool, but for different purposes — factor timing vs. portfolio construction. [[ehsani-linnainmaa-factor-momentum]] → [[kelly-principal-portfolios]]
- **Sentiment and autocorrelation**: Ehsani & Linnainmaa's use of the KNS (2018) model ties factor momentum to investor sentiment persistence — connecting behavioral and rational frameworks.
- **Factor momentum hierarchy**: Gupta & Kelly show TSFM subsumes both stock momentum (UMD) and industry momentum, confirming Ehsani & Linnainmaa's theoretical result with a practitioner implementation across 65 named factors. TSFM's crash avoidance (+18% in 2009 vs. UMD −31%) makes it a superior momentum implementation. [[gupta-kelly-factor-momentum-everywhere]] → [[ehsani-linnainmaa-factor-momentum]]
- **Cross-predictability from signals to returns**: Kelly et al.'s prediction matrix Π captures exactly the cross-predictability that Cohen & Frazzini document for supply-chain links. The off-diagonal elements of Π encode how customer j's signal predicts supplier i's return. [[kelly-principal-portfolios]] → [[cohen-frazzini-economic-links]]
- **Equity factors across asset classes**: Bektic et al. show equity FF factors work in HY bonds (equity-like via Merton model) but not IG bonds (rate-like). This parallels Frazzini & Pedersen's finding that BAB magnitude varies across asset classes based on the equity-like behavior of the instrument. [[bektic-fama-french-corporate-bonds]] → [[frazzini-pedersen-betting-against-beta]]
- **Active management vs. factor investing**: Fama & French (2010) show that few funds cover costs net of fees, while MSCI's factor indexes offer systematic access to the same premia at low cost. The factors producing spurious CAPM alpha in fund evaluation are exactly what factor indexes capture. [[fama-french-luck-vs-skill]] → [[msci-foundations-of-factor-investing]]
- **Limited attention and information diffusion**: Cohen & Frazzini document that investors fail to incorporate publicly available supply-chain information, creating predictable supplier return drift. This behavioral mechanism is distinct from the factor autocorrelation that drives factor momentum. [[cohen-frazzini-economic-links]] → [[ehsani-linnainmaa-factor-momentum]]
- **Two approaches to credit factors**: Bektic et al. use equity-based factor definitions (Merton model linkage), while Houweling & van Zundert use bond-only definitions (rating, spread, maturity). Both find strongest results in HY, weakest in IG. The approaches are complementary — equity-based captures issuer fundamentals, bond-based captures credit-specific pricing. [[bektic-fama-french-corporate-bonds]] → [[houweling-vanzundert-factor-investing-corporate-bonds]]
- **Factor alignment and risk model design**: Lee & Menchero show that adding factors to a risk model is asymmetrically risky — including a spurious factor costs ~6× more TC than omitting a valid one. This has implications for every factor in the KB: FF's five-factor model risks HML redundancy as a spurious factor, and Kelly's principal portfolios sidestep the alignment problem entirely by unifying alpha and risk in one decomposition. [[menchero-factor-alignment]] → [[fama-french-factor-models]], [[kelly-principal-portfolios]]
- **Simple vs. pure factor portfolios**: Menchero (2010) shows that FF-style sort-based factors are "simple" portfolios with incidental exposures to other factors, while Barra-style pure factors control for everything simultaneously. Style factors diverge most between simple and pure (weight correlation 0.70–0.90), explaining why FF factor returns differ from Barra factor returns even for the same named characteristic. [[menchero-characteristics-factor-portfolios]] → [[fama-french-factor-models]], [[menchero-factor-alignment]]

- **Episodic factor pricing and factor timing**: Li et al. show that factor premia are concentrated in pricing-on states identified by SED + LASSO. This reframes factor cyclicality from [[msci-foundations-of-factor-investing]] as a binary regime-switching problem. Factor momentum strategies ([[ehsani-linnainmaa-factor-momentum]], [[gupta-kelly-factor-momentum-everywhere]]) implicitly benefit from pricing-state persistence — momentum in a pricing-off factor earns nothing. BAB ([[frazzini-pedersen-betting-against-beta]]) has the highest appraisal ratio from state timing (1.08), suggesting leverage constraints bind episodically. [[li-episodic-factor-pricing]]

- **Barra model evolution (USE3 → USE4 → GEM)**: USE3 introduced GARCH-adjusted EWMA covariance and the 13 risk indices. USE4 added three major innovations: eigenfactor risk adjustment (Monte Carlo eigenvalue correction for optimized portfolio bias), volatility regime adjustment (cross-sectional scaling for crisis responsiveness), and the explicit Country factor (differential half-lives for volatility vs. correlation). GEM extends the framework globally with 48–51 countries and separate currency covariance. [[barra-use3-handbook]] → [[barra-use4-methodology]] → [[barra-gem-handbook]]; [[cuffe-barra-market-factor]] provides the intuition for the Country factor change.
- **Risk attribution pitfalls**: Davis & Menchero show that absolute return sources produce misleading risk attribution (zero cash risk, universally negative MCARs). The World/Country factor that Cuffe motivates for correlation responsiveness also resolves the attribution pitfall by converting industry factors from net-long to dollar-neutral. [[davis-menchero-pitfalls-risk-attribution]] → [[cuffe-barra-market-factor]] → [[menchero-characteristics-factor-portfolios]]
- **Factor portfolio construction choices matter**: Menchero & Ji show that regression weighting (market-cap vs. root-cap vs. equal vs. inverse specific variance) can change factor portfolio returns by >300 bps for Momentum. This complements the simple vs. pure factor distinction from Menchero (2010) and explains why FF factor returns differ from Barra factor returns even for the same characteristic. [[msci-risk-return-factor-portfolios]] → [[menchero-characteristics-factor-portfolios]] → [[fama-french-factor-models]]

- **Two answers to "can you identify skill ex ante?"**: Fama & French (2010) evaluate raw fund alpha via bootstrap and conclude few managers beat costs — skill is scarce and hard to distinguish from luck. Harmsworth & Mand (2022) change the *measure*: stripping cheap factor betas out of active return leaves idiosyncratic alpha, which they show is persistent and predictive ex ante. The disagreement is really about whether factor exposure was contaminating the skill signal. This connects to the factor-timing literature — AB isolates timing alpha via Treynor-Mazuy squared factors, exactly the timing skill Ehsani & Linnainmaa argue drives momentum. [[fama-french-luck-vs-skill]] → [[harmsworth-idiosyncratic-alpha]] → [[ehsani-linnainmaa-factor-momentum]]
- **The eigendecomposition thread (geometry → estimation → application)**: Spruyt provides the geometric foundation — a covariance matrix is a rotation (eigenvectors) plus scaling (eigenvalues) applied to white data. Mossessian & Vieli operationalize this for noisy finite samples: keep the eigenvectors, denoise the eigenvalues using the RMT/Marchenko–Pastur support region. USE4's eigenfactor risk adjustment is the same move via Monte Carlo debiasing, and Kelly's principal portfolios apply the identical "keep informative singular directions" logic to prediction rather than risk. [[spruyt-geometric-covariance-matrix]] → [[mossessian-robust-covariance-estimation]] → [[barra-use4-methodology]] → [[kelly-principal-portfolios]]

## Gaps & Future Ingestion Candidates

- Moskowitz, Ooi, and Pedersen (2012) — original TSMOM paper (foundational reference for nonlinear paper)
- Lustig, Roussanov, and Verdelhan (2011) — carry trade risk factors (foundational for Verdelhan 2018)
- Kozak, Nagel, and Santosh (2018, 2020) — factor structure, sentiment model (key for Ehsani & Linnainmaa)
- Haddad, Kozak, and Santosh (2020) — factor timing and near-arbitrage
- Asness, Moskowitz, and Pedersen (2013) — value and momentum everywhere
- Daniel and Moskowitz (2016) — momentum crashes
- Ferson and Siegel (2001) — conditional portfolio optimization (theoretical foundation for NL momentum)
- Ang et al. (2006) — cross section of volatility and expected returns
