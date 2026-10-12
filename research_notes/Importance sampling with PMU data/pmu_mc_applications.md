# Monte Carlo and Importance Sampling in PMU / Synchrophasor Applications (focus: IEEE Trans. 2020–2026)

> Method note: these notes come from about 15 web-search calls. Direct page fetches (arXiv, OSTI) failed with DNS errors, so most details come from search-result snippets and abstracts, not full texts. Sample sizes and estimated probabilities could rarely be confirmed and are marked as such. In the searches run, IEEE Transactions papers from 2020–2026 that combine PMU data with Monte Carlo were hard to surface. Several of the papers found are older (2014–2018) or appear in other venues; each one's venue and year is labelled.

## Q1. Which IEEE Trans. (and adjacent) papers use MC with PMU data, and with what sample sizes / probabilities?

### Takeaway
Crude Monte Carlo (simple random sampling, often 10^2–10^4 runs) is the standard way to validate PMU-based state estimation (SE), dynamic SE, and detector false-alarm and detection rates. None of the papers found used variance reduction. MC estimates moderate quantities (RMSE, empirical P_FA ≈ 10^-2–10^-1, detection rates), not rare-event probabilities.

### Cited Findings
**State estimation (linear/hybrid) uncertainty**
- Chakhchoukh, Vittal & Heydt, "PMU based state estimation by integrating correlation," *IEEE Trans. Power Systems*, vol. 29, no. 2, pp. 617–626 (2014). It models the time correlation of PMU measurements and validates with simulated MC runs on the IEEE 14- and 118-bus systems. The number of runs was not confirmed. This paper predates 2020. — [search summary / aggregator](https://search.isc.ac/inventory/49/55100.htm)
- Zhou, Meng, Huang & Welch, "Dynamic State Estimation of a Synchronous Machine Using PMU Data: A Comparative Study," *IEEE Trans. Smart Grid* (2015). It compares EKF, UKF, EnKF, and particle filter "using Monte Carlo methods" on a two-area four-machine system. The particle filter is itself sequential importance sampling, the only routine use of IS found in the PMU literature, but it serves state tracking, not rare-event estimation. — [UCF STARS](https://stars.library.ucf.edu/scopus2015/880)
- An *IEEE Trans. Instrumentation & Measurement* paper (2009, details from an aggregator only) estimates state-variable uncertainty from PMU data in three ways: GUM-style uncertainty propagation, Monte Carlo, and random-fuzzy variables. Authors and title should be checked in IEEE Xplore. — [aggregator](https://search.isc.ac/inventory/49/55100.htm)
- Linear probabilistic SE with "Simple Random Sampling Monte Carlo simulation" on top of a linear SE models PMU and RTU parameter uncertainty and is said to scale to very large systems. A related preprint reports 10^4 MC samples drawn from measurement-uncertainty distributions on a synthetic US system. — [arXiv 1812.05052](https://arxiv.org/pdf/1812.05052); [arXiv 1905.00329](https://arxiv.org/pdf/1905.00329)
- *IEEE Access* (2025) uses interval/bounded uncertainty in SE, the "MoK-FoBS" method, and checks with MC that the computed hard bounds contain the true states. — [DOAJ](https://doaj.org/article/b0d3aa2406714834be744298c884da16). Similarly, the 2025 preprint "Linear State Estimation in Presence of Bounded Uncertainties" uses interval arithmetic and linear-fractional programming instead of MC. — [arXiv 2510.16693](https://arxiv.org/html/2510.16693)
- Multi-snapshot PMU-based SE that accounts for systematic instrument-transformer errors and line-parameter uncertainty comes from the University of Cagliari measurement group (Muscas, Pegoraro et al.; repository record, 2025). Those authors typically validate with MC trials, but this was not confirmed for the paper. — [IRIS UniCa](https://iris.unica.it/handle/11584/475847)

**Optimal PMU placement (OPP) under PMU or communication failure**
- Jimada-Ojuolape (2021, IEEE IFEEC *conference*, not Transactions) uses MC simulation on the IEEE RTS to study PMU failures plus line outages for cyber-physical reliability. With 7 vs. 13 PMUs, the 13-PMU case keeps observability under single-line outages. — [KWASU repository](https://kwasuspace.kwasu.edu.ng/handle/123456789/2597) (DOI 10.1109/IFEEC53238.2021.9662031)
- Frontiers in Energy Research (2022) uses MC simulation of random component failures in a synchrophasor communication network, followed by a multi-objective GA for PMU and PDC placement, on the West Bengal grid. — [DOAJ](https://doaj.org/article/2db5745afdfe412ca779d645f9a958ba)
- Dehghani & Vafamand, *IET Smart Grid* 6(3):284–296 (2023), DOI 10.1049/stg2.12098, place PDCs using fuzzy MC with communication-failure probabilities. — [DOAJ](https://doaj.org/article/258fe6432ff7410285df71ed453bea8a)
- Almeida et al. (RNDM 2019) jointly optimize PMU locations and communication paths using shared-risk link groups. This approach is deterministic and uses no MC. — [UC repository](https://estudogeral.uc.pt/bitstream/10316/90454/1/Almeida-et-al_RNDM2019.pdf)
- The Aalto paper "Optimal allocation of PMUs in active distribution network considering reliability of state estimation results" was found, but no MC details were extracted. — [Aalto](https://research.aalto.fi/en/publications/optimal-allocation-of-pmus-in-active-distribution-network-conside/)

**Event and oscillation detection thresholds**
- Follum & Pierre, "Detection of Periodic Forced Oscillations in Power Systems," *IEEE Trans. Power Systems* 31(3):2423–2433 (2016), DOI 10.1109/TPWRS.2015.2456919. The periodogram threshold is set analytically from the periodogram's distribution to meet a target false-alarm probability, and it varies with frequency because ambient PMU noise is coloured. This is the main analytic alternative to MC calibration. — [PNNL](https://www.pnnl.gov/publications/detection-periodic-forced-oscillations-power-systems)
- Follum & Tuffner (PESGM 2016) extend this to a multi-channel detector whose threshold targets P_FA while accounting for inter-channel correlation. — [PNNL](https://www.pnnl.gov/publications/multi-channel-method-detecting-periodic-forced-oscillations-power-systems)
- Xu, Follum & Pierre (2023/2024) use a modified energy detector with whitening of ambient PMU data, so that thresholds can be set without extensive baselining. — [PNNL](https://www.pnnl.gov/publications/practical-line-framework-modified-energy-detector-whitening-ambient-pmu-data)
- In PMU-based three-phase imbalance detection, simulated false-alarm rates track the asymptotic theoretical curve even for K = 12 samples (arXiv, not Transactions). — [arXiv 1409.5530](https://arxiv.org/pdf/1409.5530)

**Missing data / data quality**
- Pourramezan, Karimi, Mahseredjian & Paolone, *IEEE Trans. Smart Grid* (2020), DOI 10.1109/TSG.2020.2968814, perform real-time recovery of missing synchrophasor data by nonconvex matrix completion with a Schatten-q penalty. No MC uncertainty quantification appeared in the abstract. — [EPFL Infoscience](https://infoscience.epfl.ch/handle/20.500.14299/165179)
- Konstantinopoulos et al., *IEEE Trans. Smart Grid* (2020), recover PMU data over prolonged outages with an adaptive-filtering method (temporal OLAP variant). — [NSF PAR](https://par.nsf.gov/servlets/purl/10253149)
- A Hankel/lifted low-rank recovery method claims to return an "uncertainty index" for recovered values. — [NSF PAR](https://par.nsf.gov/servlets/purl/10477241)
- Optimal singular-value-thresholding imputation on Page matrices (Biswas & Centeno, arXiv 2021). — [arXiv 2108.03220](https://www.arxiv.org/pdf/2108.03220)

**FDI / cyber-attack detection**
- FDI detectors, whether machine-learning, graph-signal-processing, or GLRT, report P_D at fixed P_FA, usually from simulation. A secured-sensor GSP detector reports up to 30% higher P_D at the same P_FA. — [ACM/Springer LNCS](https://dl.acm.org/doi/10.1007/978-3-031-44274-2_18)
- Structural-constrained GLRT for unobservable FDI provides closed-form P_FA and P_D expressions (Appendix B). These are natural targets for IS validation at small P_FA. — [arXiv 2003.08715](https://arxiv.org/pdf/2003.08715)
- An ML survey notes that FDI attacks can bypass residual-based BDD. — [arXiv 2008.06926](https://arxiv.org/pdf/2008.06926)

### Inferences
- In every PMU application area searched, MC is crude (simple random sampling). The quantities estimated (RMSE, coverage, P_D, empirical P_FA around 1–10%, observability probability with fairly unreliable components) are not rare enough to force variance reduction. That is why IS has not been needed so far, and also why reported P_FA values rarely go below about 10^-3.
- OPP reliability work mostly uses MC over component up/down states. When PMU and link unavailabilities are about 10^-3 to 10^-4, loss of observability becomes a rare event that crude MC cannot resolve, which is a clear opening for IS or cross-entropy methods.

### Gaps
- Exact MC sample sizes (e.g., 1000 vs 10^4 runs) could not be confirmed for most papers because full texts could not be fetched.
- No IEEE Trans. (2020–2026) OPP paper using MC for PMU or communication failures was confirmed in these searches. Searches only found conference, IET, and Frontiers papers. Older and other well-known OPP-reliability works (e.g., Aminifar et al., TPWRS ~2010–2011, probabilistic PMU placement) were not re-verified here.
- No IEEE Trans. I&M paper from 2020–2026 on GUM / MC propagation of PMU uncertainty into SE was confirmed by search, although the Cagliari, Politecnico di Milano, and EPFL groups are likely sources. These should be checked directly in IEEE Xplore.

## Q2. Any papers using IS (or cross-entropy / other variance reduction) for PMU-related rare events?

### Takeaway
I found no paper that applies IS or cross-entropy (CE) to a PMU-specific rare event, such as detector false-alarm probability, observability loss, extreme SE error, or missed FDI detection. IS and CE do exist in adjacent power-system reliability work and could be transferred.

### Cited Findings
- Owen, Maximov & Chertkov, "Importance sampling the union of rare events with an application to power systems analysis," *Electronic Journal of Statistics* 13:231–254 (2019). The sampler's coefficient of variation is at most √((J+J⁻¹−2)/(4n)) for J events. In a grid case with 5,772 constraints in 326 dimensions and P < 10^-22, it reaches a coefficient of variation of about 0.0024 with n = 10,000. Phase-angle differences are modelled as jointly Gaussian, and the method is related to instanton methods. — [Project Euclid](https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-13/issue-1/Importance-sampling-the-union-of-rare-events-with-an-application/10.1214/18-EJS1527.full); [arXiv 1710.06965](https://arxiv.org/abs/1710.06965)
- "Power Grid Reliability Estimation via Adaptive Importance Sampling" (arXiv 2105.08753, 2021) notes that Pmvnorm is efficient in general but limited for rare events, and it proposes adaptive IS that respects the geometry of the reliability constraints. — [arXiv 2105.08753](https://arxiv.org/pdf/2105.08753)
- Cross-entropy rare-event simulation has been used to find dangerous events in power systems, with a static voltage security example. The publication details on ResearchGate should be verified. — [ResearchGate](https://www.researchgate.net/publication/224441117_Cross-Entropy_Based_Rare-Event_Simulation_for_the_Identification_of_Dangerous_Events_in_Power_Systems)
- "Importance Sampling of Injected Powers for Electric Power System Security Analysis" treats optimal cost exceeding a large threshold as a rare event and builds IS and conditional-MC estimators with asymptotic efficiency. — [ResearchGate](https://www.researchgate.net/publication/239766423_Importance_Sampling_of_Injected_Powers_for_Electric_Power_System_Security_Analysis)
- General CE-IS methods include failure-informed dimension reduction (arXiv 2006.05496), improved CE with flexible mixtures (*RESS*), and a Bayesian improved CE with categorical mixtures for discrete component states (arXiv 2309.12490). Categorical mixtures are relevant to PMU and communication up/down states. — [arXiv 2006.05496](https://arxiv.org/abs/2006.05496); [ScienceDirect](https://www.sciencedirect.com/science/article/abs/pii/S0951832019301528); [arXiv 2309.12490](https://arxiv.org/pdf/2309.12490)
- Particle filters for PMU-based dynamic SE use sequential importance sampling or resampling, but for filtering, not rare-event probability estimation. — [UCF STARS (Zhou et al., TSG 2015)](https://stars.library.ucf.edu/scopus2015/880)

### Inferences
- Candidate rare events where IS would directly help:
  - **P_FA of chi-square or largest-normalized-residual (LNR) bad-data detection at low targets** (≤10^-4–10^-6). This matters most under non-Gaussian errors, where the chi-square threshold is miscalibrated.
  - **P(estimation error > ε)** for linear SE with PMUs, such as an angle error that breaks a protection or control margin.
  - **Loss of observability (or of N-1 observability)** given small PMU, PDC, and link failure probabilities. This needs a discrete-state IS or CE method with categorical or Bernoulli-tilted proposals.
  - **Missed detection of stealthy FDI** near the detectability boundary.
  - **False alarms of oscillation or event detectors** under coloured ambient noise, at operationally acceptable rates of about one false alarm per day or week. At 30–60 frames/s, that rate implies per-window P_FA of roughly 10^-5–10^-7.
- For linear-Gaussian PMU SE, the residual is a linear map of Gaussian noise. Mean-shift (exponential-tilting) IS toward the dominating point is near-optimal, which is the instanton analogy to Owen et al. With non-Gaussian or heavy-tailed noise, the dominating-point structure breaks and mixture or adaptive (CE) proposals are needed.

### Gaps
- Searches for "importance sampling" combined with PMU, synchrophasor, false data injection, or bad data detection returned no direct hits. That absence is itself a finding, but it should be double-checked in IEEE Xplore full-text search, since the web-search snippets are limited.
- Subset simulation, splitting, and multilevel MC were not found in PMU contexts either. They were not searched separately.

## Q3. Generative models of PMU data (GAN, normalizing flow, diffusion) that could serve as IS proposals

### Takeaway
Generative models for PMU data are almost all GANs, many from Texas A&M (Zheng, Xie et al., 2018–2023). No diffusion model or normalizing flow for synthetic PMU data generation was found. GANs lack tractable densities, so they cannot directly provide IS likelihood ratios. Flows or diffusion models with likelihoods would be needed.

### Cited Findings
- Zheng et al., "Synthetic Dynamic PMU Data Generation: A GAN Approach" (arXiv 1812.03203, 2018) trains a model-free GAN on real PMU data and calls it the first generative model for PMU data. — [ar5iv](https://ar5iv.arxiv.org/html/1812.03203)
- Zheng et al., "Creation of Synthetic Networked PMU Data: A GAN Approach" (arXiv 1908.08180, 2019) generates multi-stream PMU data on the IEEE 39-bus system and checks fidelity with statistical and modal analysis. The synthetic data improves event classification. — [arXiv 1908.08180](https://arxiv.org/pdf/1908.08180)
- "Generative Adversarial Networks-Based Synthetic PMU Data Creation for Improved Event Classification," *IEEE Open Access Journal of Power and Energy* (2021), uses a two-stage GAN plus neural ODE. Adding synthetic data to a small real set improves event classification accuracy by 2–5%. — [UTSA repository](https://rrpress.utsa.edu/handle/20.500.12588/1822)
- "Synthetic PMU Data Creation Based on GAN Under Time-varying Load Conditions," *Journal of Modern Power Systems and Clean Energy* (2023), uses a GAN for quasi-steady states and neural ODEs for transient oscillations. — [DOAJ](https://doaj.org/article/ff2f2acb688b4b6fb5fc6dafa027fa3b); [ASU](https://asu.elsevierpure.com/en/publications/synthetic-pmu-data-creation-based-on-generative-adversarial-netwo)
- pmuBAGE / pmuGE (arXiv 2204.01095, 2022) is a benchmark of almost 1,000 generated labelled PMU event instances. Its generative mechanism was not confirmed from the snippet. — [arXiv 2204.01095](https://arxiv.org/pdf/2204.01095)
- The stated motivation is that real PMU data is confidential under critical energy infrastructure rules. — [ar5iv 1908.08180](https://ar5iv.arxiv.org/html/1908.08180)
- Diffusion and flow work near PMU data (none of it PMU generation):
  - A physics-informed diffusion model for net-load (smart-meter) data is reported to beat GANs, VAEs, normalizing flows, and a baseline diffusion model by at least 20%. — [arXiv 2406.01913](https://arxiv.org/pdf/2406.01913)
  - Diffusion with AC-power-flow-constrained gradient guidance. — [arXiv 2506.11281](https://arxiv.org/abs/2506.11281v2)
  - Physics-informed DDPMs for power-flow datasets. — [arXiv 2504.17210](https://arxiv.org/abs/2504.17210v1)
  - A diffusion-based adversarial purification of PMU data appears in Nanpeng Yu's publication list. It is a defence, not data generation, and its venue was not verified. — [CatalyzeX listing](https://catalyzex.com/author/Nanpeng%20Yu)

### Inferences
- For IS you need q(x) to evaluate weights p(x)/q(x). GANs give no density, so the GAN PMU generators found here cannot be used directly as IS proposals. Possible routes:
  - Normalizing flows with exact likelihood.
  - Diffusion models with probability-flow ODE likelihoods, which are costly.
  - Using a generative model only to find failure regions (e.g., a conditional generator steered toward detector alarms), then fitting a tractable parametric or mixture proposal, as in CE.
- Weight degeneracy is a concern when the nominal p is itself a learned model of PMU data. IS estimates are then relative to the learned distribution, and model misspecification in the tails, which is exactly where heavy-tailed PMU errors matter, biases the rare-event estimate.

### Gaps
- No diffusion-model or normalizing-flow generator for PMU/synchrophasor time series was verified in IEEE Trans. 2020–2026. One may exist (e.g., 2024–2026 arXiv or TSG papers), but it did not surface in these searches.
- The Texas A&M GAN work was not confirmed as published in IEEE Trans. (e.g., TPWRS or TSG). Only the arXiv, OAJPE, and JMPSCE versions were confirmed.

## Q4. Statistical issues: non-Gaussian, heavy-tailed, time-correlated PMU errors, and their effect on MC/IS

### Takeaway
Field and laboratory evidence since 2018 shows that PMU random errors are often non-Gaussian, with possibly thick tails, and are time-correlated. Results differ between studies and depend on the test conditions. This undermines Gaussian-based analytic thresholds (chi-square BDD, periodogram thresholds) and makes the choice of error model in MC/IS a first-order issue.

### Cited Findings
- Wang, Zhao, Huang & Diao, "Assessing Gaussian Assumption of PMU Measurement Error Using Field Data," *IEEE Trans. Power Delivery* 33(6):3233–3236 (2018), letter, DOI 10.1109/TPWRD.2017.2762927. Using redundant WECC PMUs, the stability property of distributions, and the Shapiro-Wilk test, they find the Gaussian assumption "questionable" and the errors "potentially" thick-tailed. — [PNNL](https://www.pnnl.gov/publications/assessing-gaussian-assumption-pmu-measurement-error-using-field-data); [OSTI](https://www.osti.gov/biblio/1438236)
- Ahmad, Pal et al., "Statistical Characterization of Random Errors Present in Synchrophasor Measurements" (arXiv 2103.09285, 2021). A high-precision calibrator isolates device-only errors, and an adaptive moving-window MAD method is applied to synthetic and field data. Random errors in P-class and M-class PMUs are distinctly non-Gaussian even under ambient conditions. The publication venue (likely IEEE PES GM 2021) was not verified. — [arXiv 2103.09285](https://arxiv.org/pdf/2103.09285); [ASU](https://asu.elsevierpure.com/en/publications/statistical-characterization-of-random-errors-present-in-synchrop)
- Earlier, Brown et al. concluded from filtered field data that the errors are zero-mean Gaussian. This conflicts with the two studies above. — [ar5iv 2103.09285 (lit. review)](https://ar5iv.labs.arxiv.org/html/2103.09285)
- A μPMU distribution-system study finds that Shapiro-Wilk rejects Gaussianity for voltage angle in 44% of 1-s windows and 100% of 10-s and 60-s windows. The authors caution that test power depends on sample size. — [arXiv 1803.06230](https://arxiv.org/pdf/1803.06230)
- Castello, Muscas, Pegoraro et al., *IEEE Open Journal of Instrumentation and Measurement* (2022), characterize PMU errors in the laboratory and find non-Gaussian random errors. A review in the same line notes long-tail distributions in field data, but also warns that field and dynamic data may not reflect intrinsic device behaviour. Gaussian is often adequate for current-magnitude errors, while phase-angle errors may be non-Gaussian. — [DOAJ](https://doaj.org/article/342aee82febf4d1bbf34df7a6cb17ac5); [IRIS UniCa](https://iris.unica.it/retrieve/58c13406-014a-4949-bbb2-8925a77605f0/1571101936%20coverpage-iris-unica-cover.pdf)
- Pal et al. model PMU noise as a Gaussian mixture fitted by EM for robust estimation. The method beats LS, TLS, and minimum total error entropy on the IEEE 118-bus system and on proprietary US utility PMU data. — [NSF PAR](https://par.nsf.gov/servlets/purl/10096215)
- Time correlation: Chakhchoukh et al. (TPWRS 2014) integrate the temporal correlation of PMU measurements into SE. Follum & Pierre (TPWRS 2016) note that ambient PMU data is coloured, so detection thresholds must vary with frequency. — [aggregator](https://search.isc.ac/inventory/49/55100.htm); [PNNL](https://www.pnnl.gov/publications/detection-periodic-forced-oscillations-power-systems)

### Inferences
- **For crude MC:** studies that draw i.i.d. Gaussian noise at the 1% TVE level underestimate tail probabilities if real errors are thick-tailed or mixture-distributed. Reported P_FA and P_D values may not transfer to field conditions.
- **For IS:**
  - With light-tailed errors (Gaussian, GMM), exponential tilting or mean shifting is asymptotically efficient.
  - With heavy (subexponential) tails, exponential tilting does not exist or fails. Rare events are then driven by one large error, not many moderate errors, so proposals should inflate the scale or tail of individual channels: scale-mixture, conditional MC, or Asmussen–Kroese-type estimators.
  - A GMM error model suggests mixture IS proposals that put more weight on the wide component.
- **Time correlation:** P_FA over a detection window, or the probability of k consecutive alarms, becomes a path-space rare event. Tilting i.i.d. frames is wrong, so IS must tilt an AR/ARMA innovation process or use sequential IS. Coloured noise also lowers the effective sample size per window.
- **TVE limits:** C37.118.1 compliance (1% TVE) bounds errors under test conditions only. Field errors, including instrument-transformer errors, which the Cagliari group models as systematic, can add bias that MC and IS models must include separately from the random part.

### Gaps
- No study was found that fits a specific heavy-tailed family (Student-t, α-stable, Laplace) to PMU field errors with tail-index estimates. Tail-index evidence would be needed to choose IS proposals.
- No source quantified how time-correlated PMU noise changes the BDD chi-square P_FA in practice.

## Q5. Clear research gaps

### Takeaway
The gaps cluster around one idea: rare-event quantities matter for PMU applications, but they are estimated with crude MC or Gaussian analytic formulas, and IS or cross-entropy has not been applied to them.

### Cited Findings
- Existing grid IS work (Owen et al. 2019; adaptive IS 2021) targets line-flow or phase-angle limit violations from stochastic injections, not measurement, estimation, or detection rare events. — [Project Euclid](https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-13/issue-1/Importance-sampling-the-union-of-rare-events-with-an-application/10.1214/18-EJS1527.full); [arXiv 2105.08753](https://arxiv.org/pdf/2105.08753)
- OPP reliability and PDC studies use crude or fuzzy MC over failure states. — [Frontiers 2022](https://doaj.org/article/2db5745afdfe412ca779d645f9a958ba); [IET STG 2023](https://doaj.org/article/258fe6432ff7410285df71ed453bea8a); [IFEEC 2021](https://kwasuspace.kwasu.edu.ng/handle/123456789/2597)
- Forced-oscillation thresholds rely on analytic periodogram distributions. — [PNNL](https://www.pnnl.gov/publications/detection-periodic-forced-oscillations-power-systems)
- Generative PMU models are GANs without densities. — [arXiv 1908.08180](https://arxiv.org/pdf/1908.08180)

### Inferences (candidate contributions)
1. **IS for BDD / FDI detector calibration under realistic PMU noise.** Estimate P_FA ≤ 10^-6 for chi-square and LNR tests on linear PMU SE using GMM or heavy-tailed error models. Compare mean-shift IS, mixture IS, and CE against crude MC (relative error, work-normalised variance).
2. **Rare missed-detection probability of FDI.** Bias sampling toward attack vectors near the detection boundary, analogous to instanton or dominating-point methods.
3. **Observability-loss probability for PMU, PDC, and communication networks.** Discrete-state CE-IS (Bernoulli-tilted or categorical-mixture proposals, cf. arXiv 2309.12490) can compute P(unobservable) or P(N-1 observability lost) at 10^-6–10^-9 levels that crude MC cannot reach. This could then be embedded in reliability-constrained OPP.
4. **Extreme SE error probabilities** (P(|θ̂−θ| > ε)) under time-correlated, non-Gaussian errors plus instrument-transformer bias, as a complement to GUM and interval methods.
5. **Event and oscillation detector false-alarm rates on long horizons** (one per day or week) under coloured noise, using path-space or sequential IS or splitting.
6. **Likelihood-based generative PMU models (flows or diffusion) as proposal families.** Learn the nominal p from field data, then fit q to the failure region, with explicit treatment of tail misspecification.
7. **Benchmarking.** No public benchmark of rare-event PMU tasks with ground-truth small probabilities was found. pmuBAGE covers events but not rare-event probabilities.

### Gaps
- These conclusions depend partly on absence of evidence from web search. A systematic IEEE Xplore full-text search (keywords: "importance sampling" AND ("PMU" OR "synchrophasor")) is recommended to confirm that nothing exists in 2020–2026 TPWRS, TSG, TIM, TPWRD, or TII.
