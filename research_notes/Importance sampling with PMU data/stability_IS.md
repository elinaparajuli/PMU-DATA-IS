# Importance Sampling and Rare-Event Monte Carlo for Probabilistic Stability / Dynamic Security Assessment (focus: IEEE Trans., 2020–2026)

> Method note for the report writer: these notes rest on web-search results (titles, abstracts, snippets and repository listings). Direct page fetches failed during this session: arxiv.org, ieeexplore.ieee.org, osti.gov and sites.google.com did not resolve through the sandbox proxy. So I could not read full texts, DOIs or IEEE Xplore records directly. Where a venue, year, author list or DOI was not visible in the search output, it is flagged **[unverified]**. Overall finding: **in 2020–2026 IEEE Transactions papers, explicit IS / rare-event estimators for *dynamic* stability are scarce.** Most rare-event power-system work targets static reliability, line overloads or DC-OPF chance constraints. Stability-specific rare-event work from 2025–2026 appears mainly as conference papers, arXiv preprints or non-IEEE journals.

## Q1. Which IEEE Trans. (and closely related) papers 2020–2026 apply IS / rare-event methods to stability problems?

### Takeaway
I found no IEEE Transactions paper from 2020–2026 that clearly applies IS, CE-IS or subset simulation to transient, small-signal, frequency or voltage stability. The closest verified items fall into three groups. (a) Stability-focused rare-event work from 2025–2026 in IEEE PES GM, arXiv and IJEPES (Liu/Wang/Wang at McGill: subset simulation and Kriging active learning for rare transient instability). (b) IEEE TPWRS 2025 probabilistic transient stability work that uses surrogates (a GP emulator) and crude MC, but not IS (Tan, Deka, Zhao). (c) IS / adaptive IS for static grid reliability (Lukashevich/Maximov; Owen/Maximov/Chertkov). Pre-2020 IEEE TPWRS works (Perninge et al. 2012; Hua et al. 2014) form the methodological base.

### Cited Findings
**Stability-specific rare-event estimation (2025–2026)**
- *Efficient Sampling and Sensitivity Analysis of Rare Transient Instability Events via Subset Simulation*, by Jingyu Liu, Xiaoting Wang and Xiaozhe Wang (McGill / Alberta). The authors' group page lists it as an **IEEE PES General Meeting 2025** paper (a conference paper, not a Transactions paper). It uses subset simulation (SubSim) to estimate small probabilities of transient instability (TI), and adds sensitivity analysis of the input uncertainties. Test system: modified WSCC 9-bus. It reports efficiency gains over direct MC; the exact speed-up factor was not visible in the snippet **[unverified number]**. DOI not found. — [arXiv 2503.02858](https://arxiv.org/pdf/2503.02858); [X. Wang publications page](https://sites.google.com/view/xiaozhewang/publications)
- The SubSim paper's literature review says earlier power-system rare-event risk studies used "surrogate model-based methods [5], cross entropy-based importance sampling [6] or subset simulation (SubSim) [7]", but "lack comprehensive sensitivity analysis of input parameter uncertainties". I could not resolve the identities of refs [5]–[7] because the full text could not be fetched. — [arXiv 2503.02858](https://arxiv.org/pdf/2503.02858)
- *Probabilistic Assessment of Rare Transient Instability Events via Kriging-based Active Learning Framework* (arXiv 2605.06442, 2026). A Kriging surrogate, trained on transient stability margins obtained from time-domain simulation (TDS), is retrained iteratively. New samples are drawn from an enrichment pool to locate the boundary of the rare instability region under a limited TDS budget. This is AK-MCS-style active learning plus MC, not IS. The Wang group lists it as "to appear in **International Journal of Electrical Power & Energy Systems**, 2026" (Elsevier, not IEEE). — [arXiv 2605.06442](https://arxiv.org/pdf/2605.06442); [X. Wang publications](https://sites.google.com/view/xiaozhewang/publications)
- The same group lists a further paper as "Submitted": *A Hierarchical Density-based Sensitivity Analysis Framework for Rare Transient Instability Events*. — [X. Wang publications](https://sites.google.com/view/xiaozhewang/publications)
- *Subset Simulation as an Advanced Monte Carlo Method for Analyzing the Small Signal Stability of Electric Power Systems Under Consideration of Uncertainties* (IEEE Xplore document 11202156, so likely published 2025). It applies SubSim with intermediate failure events and MCMC conditional samples to probabilistic small-signal stability. Authors, venue (conference or journal) and test system **[unverified]**. The document number suggests a conference proceeding rather than Transactions. — [IEEE Xplore 11202156](https://ieeexplore.ieee.org/document/11202156/)

**IEEE TPWRS probabilistic transient stability with surrogates (no IS)**
- Bendong Tan, Deepjyoti Deka and Junbo Zhao, *Spatial-Temporal Global Sensitivity Analysis for Probabilistic Transient Stability Assessment*, **IEEE Trans. Power Systems (2025)**, per the NSF PAR record (ISSN 0885-8950; NSF award 2550498). It builds a multi-output Gaussian process emulator (MOGPE) to replace TDS in probabilistic transient stability assessment (PTSA), and uses it for hierarchical spatio-temporal global sensitivity analysis with correlated IBR/load uncertainties. Test systems: modified IEEE 9-bus and NPCC 140-bus. DOI **[unverified]**. — [NSF PAR 10658132](https://par.nsf.gov/biblio/10658132); [ResearchGate](https://www.researchgate.net/publication/398728325_Spatial-Temporal_Global_Sensitivity_Analysis_for_Probabilistic_Transient_Stability_Assessment)
- A sparse polynomial chaos expansion (PCE) method for probabilistic transient stability assessment and enhancement (arXiv 2206.04244) is a surrogate-based PTSA alternative to MC. Venue **[unverified]**. — [arXiv 2206.04244](https://arxiv.org/pdf/2206.04244)
- *Fast Monte Carlo Simulation of Dynamic Power Systems Under Continuous Random Disturbances* (arXiv 2007.03847) accelerates MC for stochastic dynamics but is not a rare-event estimator. Venue **[unverified]**. — [arXiv 2007.03847](https://arxiv.org/pdf/2007.03847)
- Ju et al. (IEEE TPWRS, OSTI-hosted, 2017 era) present an analytical alternative to MC for transient stability under stochastic continuous disturbances. Their review notes that the probability of system failure had been "estimated … by utilizing importance sampling based Monte Carlo simulation" in their ref. [20], whose identity is not resolved. — [OSTI 1415905](https://www.osti.gov/servlets/purl/1415905)

**Probabilistic DSA with biased sampling (non-IEEE / preprint)**
- Frédéric Sabot, Pierre-Etienne Labeau and Pierre Henneaux (ULB), *Towards Probabilistic Dynamic Security Assessment and Enhancement of Large Power Systems*, arXiv 2505.01147 (May 2025, eess.SY). Operating states are sampled from a database built from weather data, a market model and operator preventive actions, and contingencies (including N-2 and uncertain protection-driven cascades) are applied. The paper gives statistical indicators for choosing how many **biased and unbiased samples** to simulate for a target error on per-contingency risk. Test system: 73-bus RTS (per SOTAVerified). No journal version found. — [arXiv 2505.01147](https://arxiv.org/pdf/2505.01147); [SOTAVerified](https://sotaverified.org/papers/towards-probabilistic-dynamic-security)

**IS / adaptive IS in grid reliability (static; the methodological neighbours)**
- *Power Grid Reliability Estimation via Adaptive Importance Sampling* (arXiv 2105.08753, from Lukashevich/Maximov's group). It builds a **physics-informed mixture proposal** (one component per linear constraint), with weights tuned by convex optimization. It estimates failure probability "based only on a few dozens of random samples, compared to thousands required by the plain Monte-Carlo." The setting is DC/linear reliability constraints (line overloads), not dynamics. One search snippet cited it as IEEE TPWRS, but the venue was not confirmed; it may be IEEE Control Systems Letters **[unverified venue/year]**. — [arXiv 2105.08753](https://arxiv.org/pdf/2105.08753); [OSTI 1972176](https://www.osti.gov/pages/biblio/1972176-power-grid-reliability-estimation-via-adaptive-importance-sampling); [PapersWithCode](https://math.paperswithcode.com/paper/power-grid-reliability-estimation-via)
- Owen, Maximov and Chertkov, *Importance sampling the union of rare events with an application to power systems analysis*, Electronic Journal of Statistics 13(1), 2019 (ALOE mixture IS). It estimated probabilities below 1e-22, defined by 5772 constraints in 326 dimensions, with a coefficient of variation of about 0.0024 from 10,000 samples. — [Project Euclid](https://projecteuclid.org/journals/electronic-journal-of-statistics/volume-13/issue-1/Importance-sampling-the-union-of-rare-events-with-an-application/10.1214/18-EJS1527.pdf); [arXiv 1710.06965](https://arxiv.org/pdf/1710.06965)
- *Importance sampling approach to chance-constrained DC optimal power flow* (Lukashevich, Maximov et al., arXiv 2111.11729). — [arXiv 2111.11729](https://arxiv.org/pdf/2111.11729)
- INFORMS WSC 2024 paper on distribution-network failure probabilities: a change of measure from Large Deviations with linear power flow, or from CE, with a duality-based feasibility check, tested on an IEEE 15-bus network. — [WSC 2024](https://informs-sim.org/wsc24papers/inv132.pdf)

**Pre-2020 IEEE TPWRS foundations (outside the date window but heavily cited)**
- Perninge, Lindskog and Söder, *Importance Sampling of Injected Powers for Electric Power System Security Analysis*, IEEE TPWRS (2012). It reports a 2–3 orders-of-magnitude reduction in computation on the IEEE 39- and 118-bus systems. — [ResearchGate](https://www.researchgate.net/publication/239766423_Importance_Sampling_of_Injected_Powers_for_Electric_Power_System_Security_Analysis)
- *Efficient Estimation of the Probability of Small-Disturbance Instability of Large Uncertain Power Systems* uses IS focused on operating conditions "with high information content" for low-probability small-signal instability. Authors, venue and year **[unverified]**; possibly Perninge et al. — [ResearchGate](https://www.researchgate.net/publication/276113319_Efficient_Estimation_of_the_Probability_of_Small-Disturbance_Instability_of_Large_Uncertain_Power_Systems)
- Hua et al., *Extracting Rare Failure Events in Composite System Reliability Evaluation via Subset Simulation*, IEEE TPWRS (2014): SubSim with MCMC conditional sampling. — [ResearchGate](https://www.researchgate.net/publication/273395126_Extracting_Rare_Failure_Events_in_Composite_System_Reliability_Evaluation_Via_Subset_Simulation)
- *Cross-Entropy Based Rare-Event Simulation for the Identification of Dangerous Events in Power Systems*: CE-IS applied to static voltage security on the IEEE 30-bus system. Venue and year **[unverified]**. — [ResearchGate](https://www.researchgate.net/publication/224441117_Cross-Entropy_Based_Rare-Event_Simulation_for_the_Identification_of_Dangerous_Events_in_Power_Systems)
- *An importance sampling technique for probabilistic security assessment in power systems with large amounts of wind power*: IS for N-1 **small-signal stability** margin on a North Sea Wind Power Hub model. It runs in under 10% of the time of existing approaches on IEEE 14-bus and NESTA 162-bus systems. Authors, venue and year **[unverified]**; probably the DTU group (Thams / Chatzivasileiadis), EPSR/PSCC ca. 2016. — [ResearchGate](https://www.researchgate.net/publication/283782417_An_importance_sampling_technique_for_probabilistic_security_assessment_in_power_systems_with_large_amounts_of_wind_power)
- *Efficient Database Generation for Data-driven Security Assessment of Power Systems* (arXiv 1806.01074; DTU group). It argues that IS needs an initial sample already covering the region of interest, which becomes infeasible as that region shrinks. It proposes boundary-focused sampling instead. Venue **[unverified; likely IEEE TPWRS 2020]**. — [arXiv 1806.01074](https://arxiv.org/pdf/1806.01074)
- A 2025 DSA dataset-generation toolbox (arXiv 2501.09513) benchmarks boundary-focused sampling against generic and importance sampling for training decision trees on two test systems. — [arXiv 2501.09513](https://arxiv.org/pdf/2501.09513)

**Voltage stability / loadability**
- *Identification of Efficient Sampling Techniques for Probabilistic Voltage Stability Analysis of Renewable-Rich Power Systems*, Energies 14(8):2328 (2021, MDPI). It compares six samplers (MC, IS, QMC variants, MCMC) using loadability margin as the index. — [doi:10.3390/en14082328](https://doi.org/10.3390/en14082328)
- Slice-sampling MCMC for the probability distribution of the voltage stability margin (Zhang, Int. Trans. Electr. Energy Syst., 2017). — [Wiley](https://onlinelibrary.wiley.com/doi/10.1002/etep.2366)

**Small-signal (crude MC / QMC / LHS baseline)**
- Probabilistic small-signal studies still mostly use crude MC, QMC or LHS: QMC with PEV and wind ([ResearchGate](https://www.researchgate.net/publication/260509337_Quasi-Monte_Carlo_Based_Probabilistic_Small_Signal_Stability_Analysis_for_Power_Systems_With_Plug-In_Electric_Vehicle_and_Wind_Power_Integration)), LHS-MC for PSS/STATCOM-POD coordination ([Springer, Electr. Eng. 2024](https://link.springer.com/article/10.1007/s00202-024-02763-4)), and MC probabilistic eigenanalysis by Rueda and Erlich, J. Risk & Reliability 2012 ([IDEAS](https://ideas.repec.org/a/sae/risrel/v226y2012i1p118-133.html)).
- A security index has been defined as the probability that all critical electromechanical modes keep their damping ratio above a threshold. — [ResearchGate](https://www.researchgate.net/publication/261423358_A_small-signal_stability_related_probabilistic_security_assessment_of_wind_power_integration_into_power_systems)

### Inferences
- For a "2020–2026 IEEE Transactions + IS + stability" table, the honest count from this search is about zero confirmed entries. The best 2025–2026 stability rare-event items are an IEEE PES GM 2025 paper (SubSim, transient), an IEEE Xplore 2025 paper of unconfirmed venue (SubSim, small-signal), an IJEPES 2026 paper (Kriging active learning, transient), and an arXiv preprint (probabilistic DSA with biased sampling).
- Reported efficiency figures come almost entirely from static problems: 2–3 orders of magnitude (Perninge 2012); tens of samples versus thousands (adaptive IS mixture); CoV 0.0024 at 1e-22 with 1e4 samples (ALOE). No verified efficiency numbers for transient stability IS were found.

### Gaps
- The full texts of arXiv 2503.02858 and 2605.06442 (speed-ups, sample counts, failure-probability magnitudes), and the identities of refs [5]–[7] in 2503.02858, could not be retrieved.
- I could not confirm DOIs or IEEE Xplore records for any of the 2025–2026 items. Direct IEEE Xplore searches, filtered to TPWRS / TSG / TSTE / TPWRD for 2020–2026, are still needed. Example queries: "importance sampling" AND "stability"; "subset simulation"; "cross-entropy" AND "transient".
- I found no frequency-stability IS paper (e.g., rare nadir/RoCoF violations).

## Q2. How are proposal distributions designed?

### Takeaway
In power-system rare-event work, proposals are built in five ways:
- physics-informed Gaussian mixtures centred on linearized constraint boundaries (ALOE, adaptive IS);
- CE-tuned parametric families;
- large-deviations / design-point shifts;
- subset-simulation MCMC levels, which avoid an explicit proposal;
- surrogate-guided (Kriging/GP/RBF) boundary sampling.

Normalizing-flow proposals exist in structural reliability, but I found none applied to power-system stability.

### Cited Findings
- Adaptive IS mixture: a "physics-informed mixture distribution" with convex optimization of the mixture weights. — [arXiv 2105.08753](https://arxiv.org/pdf/2105.08753)
- ALOE: a mixture of conditional Gaussians, one per violated linear constraint (phase-difference half-spaces), giving an unbiased estimator of the probability of a union of rare events. — [arXiv 1710.06965](https://arxiv.org/pdf/1710.06965)
- LDP-based change of measure, or CE, for distribution-network failure. — [WSC 2024](https://informs-sim.org/wsc24papers/inv132.pdf)
- SubSim expresses a small probability as a product of larger conditional probabilities, sampled via MCMC. — [Hua et al. TPWRS 2014](https://www.researchgate.net/publication/273395126_Extracting_Rare_Failure_Events_in_Composite_System_Reliability_Evaluation_Via_Subset_Simulation); [IEEE 11202156](https://ieeexplore.ieee.org/document/11202156/)
- Kriging surrogate with active-learning enrichment near the stability boundary, trained on TDS margins. — [arXiv 2605.06442](https://arxiv.org/pdf/2605.06442)
- An RBF surrogate of power flow embedded inside conventional IS for rare probabilities in probabilistic power flow (summarized by search; not opened). — [search summary; no direct link retrieved]
- Known CE weaknesses: stalling when initial samples contain no failures ("cold start"), difficulty with multimodal failure regions, and a limit of roughly 100 dimensions for parametric CE families. Remedies include Safe-ICE (heavy-to-light-tailed mixture), constrained Gaussian mixtures and failure-informed dimension reduction. — [Safe-ICE arXiv 2509.07160](https://arxiv.org/pdf/2509.07160); [constrained GM arXiv](https://arxiv.org/html/2610.07485); [Uribe et al. arXiv 2006.05496](https://arxiv.org/pdf/2006.05496); [ETH ICE report](https://ethz.ch/content/dam/ethz/special-interest/baug/ibk/risk-safety-and-uncertainty-dam/publications/reports/RSUQ-2024-004.pdf)
- Normalizing-flow IS (structural reliability; Dasgupta and Johnson, NZSEE 2023) was benchmarked against SubSim and CE at failure probabilities around 1e-7 with multiple failure modes. — [NZSEE repo](https://repo.nzsee.org.nz/handle/nzsee/2629)
- Neural-network surrogates lose accuracy in the probability tails. One mitigation retrains them on IS samples drawn near the limit state. — [arXiv 2605.16078](https://arxiv.org/html/2605.16078); [arXiv 2605.15356](https://arxiv.org/html/2605.15356)
- The DTU critique: IS needs prior knowledge of the region of interest (from expert knowledge, regression or linear sensitivities), which risks missing critical regions. — [arXiv 1806.01074](https://arxiv.org/pdf/1806.01074)

### Inferences
- Transient stability has no closed-form limit state. A FORM/design-point proposal would need a differentiable margin, such as CCT, TSI from TDS, an energy-function margin or a surrogate. This is a likely reason why SubSim (gradient-free) and Kriging active learning dominate recent transient-stability work rather than design-point IS.
- Small-signal limit states (min damping ratio ≥ ζ_th) are smooth almost everywhere, with eigenvalue sensitivities available. They are therefore the most natural target for FORM/design-point or CE-IS, and this appears under-exploited after 2020.

### Gaps
- No verified FORM/design-point IS for damping ratio from 2020–2026 was found.
- No normalizing-flow or other deep-generative IS was found for any power-system stability problem.

## Q3. State of measurement-based (PMU) probabilistic oscillation/stability assessment; where crude MC is still used

### Takeaway
PMU-based mode estimation and ambient-data estimation of the state matrix or Jacobian are mature. Uncertainty in them is quantified either analytically or Bayesian (posterior of modal parameters), or by crude MC trials to characterize estimator variance. I found no PMU-driven work that uses IS or rare-event estimation to obtain probabilities of low damping or instability.

### Cited Findings
- ModeMeter-type estimation of modes and damping from real-time phasor data, with low damping treated as an early warning (PNNL report). — [PNNL-18945](https://www.pnnl.gov/main/publications/external/technical_reports/pnnl-18945.pdf)
- A Bayesian frequency-domain approach identifies frequency, damping and modal excitation, together with their uncertainty, from ambient PMU data. It was tested on the IEEE New England system, a Nordic model and real Nordic PMU data. — [Univ. Liverpool repository](https://livrepository.liverpool.ac.uk/3003224/1/Bayesian%20Approach%20in%20the%20Modal%20Analysis%20of%20Electromechanical%20Oscillations_Final.pdf)
- **Crude MC to characterize estimators:** a cascade damped-SOGI multi-mode estimator (IEEE Access 2023) was evaluated with 1200 MC trials, and its estimation variance grows with noise variance. — [ResearchGate](https://www.researchgate.net/publication/381695479_The_On-line_Estimation_of_Multi-mode_Electromechanical_Oscillations_Using_the_Cascade_Structure_of_Damped-SOGI)
- In PMU-based modal analysis of two RTE oscillation events, Matrix Pencil, HTLS and ERA gave negative damping early in one event while Prony gave near-zero damping. Method choice therefore materially changes damping estimates. — [ResearchGate](https://www.researchgate.net/publication/388639962_PMU-based_Modal_Analysis_of_Two_RTE_Oscillation_Events)
- An MC model of PMU measurement-chain uncertainty (transducer, digitizer and synchrophasor algorithm) exists. — [IEEE Xplore 7540660](https://ieeexplore.ieee.org/document/7540660)
- Xiaozhe Wang's group has several ambient-PMU papers: estimating the dynamic state Jacobian / system state matrix from PMU statistics (Wang, Bialek, Turitsyn), dynamic load parameters from ambient data via Ornstein-Uhlenbeck regression, and state-matrix estimation with integrated VSCs (IEEE 68-bus). The same group (Liu, Wang, Wang) produced the SubSim and Kriging rare-transient-instability papers. This is the clearest bridge between PMU-based stochastic estimation and rare-event estimation, although no paper of theirs that I found combines the two. — [arXiv 1706.01114](https://arxiv.org/pdf/1706.01114.pdf); [arXiv 2002.08310](https://ar5iv.arxiv.org/html/2002.08310); [arXiv 2006.15244](https://arxiv.org/pdf/2006.15244); [arXiv 1510.07603](https://ar5iv.arxiv.org/html/1510.07603)
- WAMS/synchrophasor data combined with MC for probabilistic PSS placement and tuning on the New England 39-bus system (2019, non-IEEE journal). — [IIETA](https://www.iieta.org/download/file/fid/26665)
- Model-free trajectory stability margins from PMU disturbance trajectories (Xu et al., 2009, Chinese journal). — [CityU scholars](https://scholars.cityu.edu.hk/en/publications/pmu-%E6%89%80%E8%8E%B7%E8%BD%A8%E8%BF%B9%E7%9A%84%E7%A8%B3%E5%AE%9A%E8%A3%95%E5%BA%A6/)
- **Crude MC remains standard in DSA dataset generation and probabilistic DSA.** A 2026 tabular-foundation-model DSA preprint notes that insecure operating conditions are rare under naive MC, so many simulations are needed. — [arXiv 2607.16031](https://arxiv.org/html/2607.16031v1); [arXiv 2505.01147](https://arxiv.org/pdf/2505.01147)
- A PMU-based voltage stability patent notes that the computational burden of MC is a "major concern for online applications". — [USPTO 11271398](https://image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11271398)

### Inferences
- PMU-derived quantities could naturally feed a rare-event estimator, either as the nominal distribution or by conditioning the proposal on the current operating point. Examples are a posterior over modal parameters, an estimated state matrix with its covariance, and estimated load-dynamics parameters. The literature retrieved here does not do this.
- Crude MC is still used in: (i) estimator performance evaluation (noise trials); (ii) DSA training-database generation; (iii) probabilistic small-signal eigenanalysis; (iv) probabilistic voltage-margin distributions (CPF per sample).

### Gaps
- I found no IEEE Transactions paper from 2020–2026 on "PMU-driven probabilistic DSA with IS". The search was limited by the lack of IEEE Xplore access.

## Q4. Neural / physics-informed surrogates + IS for rare transient instability?

### Takeaway
I found no verified paper that combines a neural-network or physics-informed (PINN) surrogate with importance sampling for transient-instability probability. The nearest work uses Kriging/GP surrogates with active learning or MC (arXiv 2605.06442; Tan-Deka-Zhao TPWRS 2025 MOGPE), or SubSim without a surrogate. Surrogate + adaptive IS methods are maturing outside power systems.

### Cited Findings
- Kriging active-learning framework for rare TI (IJEPES 2026, per the group page). — [arXiv 2605.06442](https://arxiv.org/pdf/2605.06442)
- MOGPE surrogate replacing TDS for PTSA (IEEE TPWRS 2025), used for sensitivity analysis rather than rare-event estimation. — [NSF PAR](https://par.nsf.gov/biblio/10658132)
- Sparse PCE surrogate for PTSA. — [arXiv 2206.04244](https://arxiv.org/pdf/2206.04244)
- Generic surrogate-guided adaptive IS for failure probability (2026) and proposal-guided greedy surrogate refinement. The latter reports accuracy comparable to true-model adaptive IS with substantially fewer high-fidelity evaluations, and notes that standard NNs lack reliable posterior uncertainty for active learning. — [arXiv 2603.20959](https://arxiv.org/pdf/2603.20959); [arXiv 2605.15356](https://arxiv.org/html/2605.15356)
- AK-MCS with conformal certification (2026) is a candidate certification tool for surrogate-based rare-event estimates. — [arXiv 2606.20191](https://arxiv.org/pdf/2606.20191)
- The SubSim TI paper cites "surrogate model-based methods [5]" for power-system rare-event risk, but the reference is unresolved. — [arXiv 2503.02858](https://arxiv.org/pdf/2503.02858)

### Inferences
- An NN/PINN surrogate of the transient stability margin (for example TSI or CCT) used as a proposal or control-variate generator inside IS, with TDS correction to keep the estimator unbiased, appears to be an open niche. The GP/Kriging route is already being explored by the Liu/Wang group and Tan/Deka/Zhao.

### Gaps
- I could not verify any PINN-based transient-stability rare-event paper. Targeted IEEE Xplore and Scholar queries are needed to confirm absence; my searches found none.

## Q5. Gaps where PMU data + IS has not been combined

### Takeaway
Across all four stability classes, I found no work in which PMU / synchrophasor measurements define, condition or update the IS proposal or nominal distribution for rare stability-violation probabilities. This appears to be a clear gap, with the caveat that IEEE Xplore could not be queried directly.

### Cited Findings
- PMU modal estimation quantifies parameter uncertainty (Bayesian) but does not estimate rare-event probability. — [Liverpool](https://livrepository.liverpool.ac.uk/3003224/1/Bayesian%20Approach%20in%20the%20Modal%20Analysis%20of%20Electromechanical%20Oscillations_Final.pdf)
- Rare-event stability work (SubSim, Kriging) is model-based, driven by input distributions of renewables and loads, with no measurement conditioning found. — [arXiv 2503.02858](https://arxiv.org/pdf/2503.02858); [arXiv 2605.06442](https://arxiv.org/pdf/2605.06442)
- Adaptive/mixture IS has been shown only on linear (DC) reliability constraints. — [arXiv 2105.08753](https://arxiv.org/pdf/2105.08753); [arXiv 1710.06965](https://arxiv.org/pdf/1710.06965)
- Damping-ratio security indices (probability that all critical modes exceed ζ_th) are computed with MC, QMC or LHS, not IS. — [ResearchGate](https://www.researchgate.net/publication/261423358_A_small-signal_stability_related_probabilistic_security_assessment_of_wind_power_integration_into_power_systems); [Springer 2024](https://link.springer.com/article/10.1007/s00202-024-02763-4)

### Inferences (candidate research gaps)
1. **PMU-conditioned IS for damping-ratio violation.** Use the ambient-PMU estimate of the state matrix or modes, plus its covariance, as a nominal model. Build a design-point or CE proposal toward ζ < ζ_th, using eigenvalue sensitivities for the gradient.
2. **PMU-driven DSA with CE/adaptive IS for online risk.** Condition the operating-point distribution on the current PMU snapshot, then use IS over contingencies and short-term renewable/load deviations. Today online DSA uses crude MC or ML classifiers trained on MC databases.
3. **Rare-event estimation for frequency stability** (nadir/RoCoF limits) using PMU-estimated inertia: no IS work found.
4. **Voltage stability margin IS conditioned on PMU-based Thevenin/margin estimates:** only crude MC, slice sampling or generic sampler comparisons were found.
5. **Surrogate (NN/PINN) + IS with TDS correction for transient instability, using PMU-calibrated dynamic models:** no work found.
6. **Using IS to evaluate PMU modal-estimator failure probability** (e.g., the probability of a sign error in damping), rather than crude MC trials.

### Gaps
- Verification of these "absences" is limited by the failed IEEE Xplore and arXiv fetches. A systematic Xplore query is needed before any absence is stated as definitive in a final report.
