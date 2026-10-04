# Why Do Dogs Age So Fast? The Comparative Biology of a ~12-Year Lifespan

> Part of the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 subagent · Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/why_dogs_age_fast_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**Evidence tags.** ✅ = confirmed in a primary source I opened (full text, PDF or supplementary tables); 🟡 = abstract, database entry or reputable secondary source only; ❓ = unconfirmed, contested, or from recollection.
**Explanation labels.** Each causal claim is marked as **established**, **well-supported correlation**, **hypothesis** or **speculation**, and the study type and species are named (cross-species comparative, dog cohort, mouse model, cell culture, modelling).
**Derived numbers.** Values marked *(my calculation)* are arithmetic I did on published numbers. The inputs are cited, and an auditor should re-check them.

---

## TL;DR

- **The gap is about 5–6×, not 10×.** Median dog lifespan is about 11–13 years (UK median 12.5 y from 584,734 dogs [4] ✅; US life expectancy at birth 12.69 y from about 13 million dogs [3] 🟡). Human life expectancy is 73.3 y worldwide [13] 🟡. The best-verified maximums are 27 y for dogs [5] 🟡 and 122.5 y for humans [11, 12] 🟡. The ratios are about 5–6× for typical lifespans and about 4.5× for maximums.
- **Humans are the anomaly, not dogs.** On the mammalian body-mass–longevity line used by AnAge (t_max = 4.88·M^0.153, M in grams), a 40-kg dog is expected to live about 25 y at most. The observed 27 y is 109% of that. Gray wolves reach 88–89% of their expected value and humans 463% [5, 9, 11, 14] ✅ *(my calculation reproduces the AnAge residuals; independently recomputed by the verifier)*. Dogs have roughly the lifespan a mammal of their size "should" have. Humans live about 4.6× longer than expected, and chimpanzees about 2.7× [15]. [verifier-corrected: AnAge's 40 kg is a large-dog mass; a 15–20-kg "typical" dog would give 122–127%, so the conclusion is robust to the mass chosen but the exact residual is not.]
- **Ultimate cause (hypothesis, strongly supported by theory and comparative data).** Canids have a fast life history: maturity at about 1.4–1.8 y, gestation of about 62–63 days, litters of 4–6, and high adult mortality in the wild. Yellowstone wolves average 4–5 years [9, 10] ✅. Under such conditions, selection to maintain the body beyond about 10–15 y is weak (Medawar/Williams/Kirkwood logic [19–22]). Humans evolved the opposite: low adult mortality, late maturity, and probably grandmothering [29, 30].
- **Domestication did not reset the wolf's ageing programme.** Dogs inherited it and, if anything, sped up development: earlier maturity, faster growth and higher fecundity [5, 9, 26]. Artificial selection for large size added faster ageing in big breeds [27] 🟡. The argument that domestication sped up development is a hypothesis.
- **Somatic mutation clock (cross-species comparative, colon crypts).** Dogs gain about 249 single-base substitutions per genome per year versus 47 in humans, a 5.3× difference. They reach about the same burden by the end of life: about 3,810 for dogs versus 3,940 for humans [32] 🟡 *(my calculation from the supplementary tables)*. [verifier-corrected: the human values (47.12 SBS/yr; lifespan 83.67 y) and the end-of-life-burden range are confirmed in the main text and Table 1; the dog-specific values live only in the supplementary spreadsheets, which the verifier could not re-open, so the dog figures are downgraded to 🟡.] This is a strong correlation. It is not proven to be a cause: humans with hereditary hypermutation are not obviously prematurely aged [33] 🟡.
- **Epigenetic clocks.** The dog methylome remodels very fast in puppyhood, then slows. Wang et al. 2020 give the conversion **human_age = 16·ln(dog_age) + 31** (104 dogs profiled, mostly Labradors; 95 analysed) [36] ✅ [verifier-corrected: not all 104 were Labradors]. Pan-mammal clocks show that methylation rates scale with maximum lifespan [38, 41] ✅ [verifier-corrected: ref 37 is a dog/human clock paper, not a rate-scaling result], and that ageing-related methylation is "intertwined with developmental processes" [38] ✅.
- **Telomeres.** Dogs have human-like telomere biology: short telomeres and little or no somatic telomerase [47] 🟡. Dogs lose telomeric DNA about 10× faster than humans, and breed telomere length predicts breed lifespan [48] 🟡. The cross-species "telomere shortening rate predicts lifespan" paper did **not** include dogs [49] ✅.
- **Rate-of-living is discredited as the explanation.** A 30-kg dog and a 62-kg human differ by only about 1.2× in expected mass-specific metabolic rate (Kleiber scaling, *my calculation*), but by about 5–6× in lifespan. After correcting for body mass and phylogeny, basal metabolic rate does not predict eutherian longevity [17] 🟡.
- **Developmental tempo is a promising unifying lead (hypothesis).** Species-specific speeds of protein turnover and other biochemical reactions set developmental pace [62–65], and the same pace correlates with lifespan [17, 38, 66]. Dogs reach maturity about 9× sooner than humans (510 vs 4,745 days) [5, 11] ✅. No dog cells have been put into these "stem-cell zoo" tempo assays yet. That is an open research path.
- **Dog ageing is front-loaded and then steep.** Epigenetically, puppyhood counts for a lot. Demographically, adult dogs' annual mortality doubles about every 2 years (UK life table [2] ✅, *my calculation*), versus about 8 years in humans [11] ✅. That is about 4× faster actuarial ageing.
- **What kills old dogs.** Cancer, neurological disease (including canine cognitive dysfunction, CCD) and cardiac disease are the main causes [1, 58–60] 🟡. The popular claim that "half of dogs over 10 develop cancer" is ❓ as an incidence figure. It appears to stem from cause-of-death data: 40–50% of necropsied dogs aged 10–16 died of cancer [58] 🟡.
- **Implication for intervention (speculation, based on the above).** The species "clock" is polygenic and developmental, and probably cannot be reset near-term. Realistic levers act on the *rate* of adult ageing through nutrient sensing (caloric restriction in dogs [73]; mTOR) and on specific killers (cancer, CCD, cardiac). See `../05_interventions/`.

---

## 1. The numbers

### 1.1 Dogs: typical lifespan

| Estimate | Population | Value | Source | Tag |
|---|---|---|---|---|
| Median longevity | 5,095 deaths, 86 first-opinion practices, England | 12.0 y (IQR 8.9–14.2) | O'Neill et al. 2013 [1] | 🟡 |
| Life expectancy at birth | 30,563 deceased dogs, VetCompass UK, 2016–2020 | 11.23 y (95% CI 11.19–11.27) | Teng et al. 2022 [2] | ✅ |
| Life expectancy at birth | 13,292,929 dogs, Banfield (US), 2013–2019 | 12.69 y | Montoya et al. 2023 [3] | 🟡 |
| Median survival | 584,734 dogs (284,734 deceased), 18 UK sources, 155 breeds | 12.5 y (purebred 12.7; crossbred 12.0; F 12.7; M 12.4) | McMillan et al. 2024 [4] | ✅ |
| Labrador median (UK) | Life-table fit | 12.3 y | Raz et al. 2026 (from Teng data) [75] | ✅ |

Breed ranges are wide. McMillan et al. report breed medians from 15.4 y (Lancashire Heeler) down to 5.4 y (Caucasian Shepherd Dog) [4] ✅. In Teng et al., French Bulldogs had a life expectancy at birth of only 4.53 y [2] ✅.

### 1.2 Dogs: maximum lifespan (records need scepticism)

- **AnAge** (Human Ageing Genomic Resources) lists a verified maximum of **27 y** ("acceptable" data quality). The record is "Buksi", a mixed-breed male from Hungary whose genome was sequenced by Jónás et al. 2020 [5, 6] 🟡. AnAge explicitly treats anecdotal ~30-year reports as unverified [5] ✅.
- **Guinness World Records** reinstated **Bluey** (Australian cattle dog, 1910–1939) at **29 y 5 mo** on 22 February 2024 [7] 🟡. This followed the posthumous removal of the title from **Bobi** (claimed 31 y 163–165 d; sources differ by two days) [verifier-corrected], because his age evidence (a Portuguese pet-registry entry that did not require proof of age for dogs born before 2008) was judged inconclusive [7, 8] 🟡. Bluey's age rests on early-20th-century documentation that is far weaker than the standard used for human supercentenarians. Treat it as ❓.
- **Takeaway.** The plausible dog maximum is about 22–27 y, about 2× the median. The ratio of maximum to median lifespan is similar in humans (122.5 ÷ ~73).

### 1.3 Gray wolves (Canis lupus)

| Metric | Value | Source | Tag |
|---|---|---|---|
| Maximum longevity (captivity) | 20.6 y | AnAge [9] | ✅ |
| Wild record | 13.7 y (AnAge) ✅; oldest known Yellowstone wolf 12.5 y ✅; "13.8 y for Idaho wolf B2" ❓ [verifier-corrected: not on either cited page; unsourced] | [9, 10] | ✅/❓ |
| Average lifespan, Yellowstone National Park | 4–5 y inside the park; 2–3 y outside | NPS [10] | ✅ |
| Adult mortality causes, Yellowstone | 77% natural (42% killed by other wolves); 17% human-caused | NPS [10] | ✅ |
| Female sexual maturity | 669 days (~1.8 y); Yellowstone average age at first litter 2.7 y | [9, 10] | ✅ |
| Litter size | 6 (AnAge); 4.4 at den emergence, 3.2 surviving to late December (Yellowstone) | [9, 10] | ✅ |
| Gestation | 62 days | [9] | ✅ |
| Onset of female reproductive senescence (Yellowstone) | 4–5 y | NPS [10] | ✅ |

**Interpretation (hypothesis).** In the wild, few wolves live long enough to show senescence. When wolves are protected (captivity), their maximum (about 21 y) is close to that of protected dogs (27 y). Wolf–dog comparisons are covered in `./wolves_vs_dogs.md`.

### 1.4 Humans

- Maximum: **Jeanne Calment, 122 y 164 d**, "the most thoroughly validated age claim" [12] 🟡. AnAge uses 122.5 y [11] ✅.
- Global life expectancy at birth was **73.3 y in 2024** [13] 🟡.
- The age by which 80% of adults had died averaged **83.7 y** [32] ✅ (used by Cagan et al. as the human "lifespan"; the value 83.67 y is in their Table 1). The cohort detail ("1900 birth cohorts from Denmark, Finland and France, excluding deaths before 13") is 🟡 [verifier-corrected: the main text says only "census record data for humans"; the cohort description was not found outside the supplement].
- Long human lives are not purely modern. Wild chimpanzees have life expectancy at birth below 15 y, and their mean adult lifespan after maturity is only about 15 y [29] 🟡. Hunter-gatherers who reach adulthood commonly live into their 60s–70s. Gurven & Kaplan put the modal adult age at death at "about seven decades" [31] ✅ [verifier-corrected: the original draft said "about 72" from recollection; the abstract of the PDF says "about seven decades", with mortality roughly flat to about age 40 and Gompertz-like thereafter].
- Human annual mortality doubles about every **8 y** after about age 30 [11] ✅.

### 1.5 Where dogs, wolves and humans sit on the body-mass–lifespan line

Across mammals, maximum lifespan rises with body mass [16, 17]. AnAge expresses each species' residual as a percentage of the maximum lifespan expected from its adult mass, using **t_max = 4.88·M^0.153** (M in grams) [14] ✅. The calculations below reproduce AnAge's published residuals. [verifier-corrected: the AnAge help page gives the formula but does not state the mass unit; grams is confirmed because only grams reproduces AnAge's own residuals (with M in kg a 40-kg dog would be "expected" to live 8.6 y). AnAge's 40,000 g "adult weight" for the dog is a large-breed mass; using 15–20 kg gives expected t_max 21.3–22.2 y and a residual of 122–127%, so the qualitative conclusion (dogs near the line) holds, but the 109% figure depends on that mass choice.]

| Species | Adult mass (AnAge) | Expected t_max | Observed t_max | Residual | Tag |
|---|---|---|---|---|---|
| Domestic dog | 40 kg | 24.7 y | 27 y | **109%** | ✅ [5] |
| Gray wolf | 26.6 kg | 23.2 y | 20.6 y | **88–89%** | ✅ [9] |
| Chimpanzee | 45 kg | 25.1 y [verifier-corrected: was blank] | 68 y | **270%** | ✅ [15] |
| Human | 62 kg | 26.4 y | 122.5 y | **463–464%** | ✅ [11] |

- **The longevity quotient (LQ)** of Austad & Fischer is the same idea: observed lifespan ÷ lifespan expected for a non-flying eutherian of that mass [16] 🟡. Bats live at least 3× longer than expected [16] 🟡. Flight is the strongest ecological predictor of longer-than-expected lifespan in 1,368 endotherm species [18] 🟡.
- **Reframing (well-supported correlation, cross-species comparative).** Dogs and wolves are ordinary mammals for their size. Humans, and primates generally, are the outliers. A better version of the question is: *"why did humans evolve a lifespan about 4.6× longer than the mammalian norm for our size, while canids kept the norm?"*

### 1.6 How many "times faster" is a dog? It depends on which clock you read

| Clock | Dog | Human | Ratio (human ÷ dog) | Source |
|---|---|---|---|---|
| Maximum recorded lifespan | 27 y | 122.5 y | 4.5× | [5, 11] ✅ |
| Age by which 80% of adults have died (Cagan) | 15.3 y (zoo dogs and wolves) | 83.7 y | 5.5× | [32] 🟡 (dog value from supplement, not re-opened by verifier; human value ✅) [verifier-corrected] |
| Median / life expectancy at birth | ~12.5 y | ~73 y (global) | ~5.8× | [4, 13] |
| Female sexual maturity (AnAge) | 510 d | 4,745 d | 9.3× | [5, 11] ✅ |
| Gestation | 63 d | 280 d | 4.4× | [5, 11] ✅ |
| Colon-crypt somatic substitutions per year | 249.5 | 47.1 | 5.3× (faster in dogs) | [32] 🟡 (dog rate from supplement; human rate ✅ in Table 1) [verifier-corrected] |
| Telomere loss per year (blood cells) | — | — | ~10× (faster in dogs) | [48] 🟡 |
| Mortality-rate doubling time (adults) | ~2.0 y | ~8 y | ~4× | [2, 11] *(my calculation)* |
| Methylome age equivalence | not constant: 16 human-years per dog-year at age 1, 2 at age 8 | — | — | [36] ✅ |

**Takeaway.** Almost every biological clock runs about 4–10× faster in dogs. This suggests one coordinated life-history "tempo" rather than a single broken component. That is a hypothesis, discussed in §3.9 and §6.

---

## 2. Ultimate (evolutionary) explanations

### 2.1 Theory primer

| Theory | Core idea | Key reference | Status |
|---|---|---|---|
| Mutation accumulation | Selection weakens with age because few individuals survive to old age. Mutations that act late in life therefore accumulate (the "selection shadow"). | Medawar 1952 [19] 🟡 | Established theory |
| Antagonistic pleiotropy | Genes that help early reproduction are favoured even if they cause late-life damage. | Williams 1957 [20] 🟡 | Established theory; specific genes rarely identified |
| Disposable soma | Energy is split between reproduction and body maintenance. When extrinsic mortality is high, investing in long-term repair does not pay. | Kirkwood 1977; Kirkwood & Austad 2000 [21, 22] 🟡 | Established theory; mechanistic predictions mixed |
| Extrinsic mortality / pace of life | Species with high unavoidable adult mortality evolve faster senescence and shorter lives. | Williams 1957 [20]; Austad's island opossums [25] 🟡; flight and fossoriality data [18] 🟡 | Contested in its simple form (see §2.5) |

### 2.2 The canid "lifespan setting"

The wolf, the dog's ancestor, has a classic fast-to-moderate carnivore life history:

- Maturity at about 1.8 y. Yellowstone females average 2.7 y at first litter [9, 10] ✅.
- Large litters (4–6) on a short gestation (62 d) [9, 10] ✅.
- High adult mortality, mostly violent or human-caused. Average age at death is 4–5 y even in a protected park, and 2–3 y outside it [10] ✅.

- In Yellowstone, female reproductive senescence begins at 4–5 y [10] ✅.

**Hypothesis (cross-species theory applied to canids).** Under this regime, a wolf's expected reproductive output is concentrated in years 2–7. The force of selection against late-acting deleterious alleles, and for costly maintenance such as DNA repair, cancer suppression and proteostasis, falls steeply after that window. A maximum potential lifespan of about 20 y, seen only in protected wolves, is what such a regime predicts. It matches the mammalian average for a 25–40-kg animal (§1.5). No canid-specific test of this has been done: it is inferred from general theory and comparative patterns.

### 2.3 What domestication did and didn't change

- Dogs carry the wolf's programme. The roughly 15,000–30,000 years of domestication cited by Wang et al. [36] ✅ is short relative to the evolution of species lifespans. Pan-mammal methylation data suggest that maximum lifespan has an intrinsic, species-level epigenetic signature. The DNAm maximum-lifespan predictor "does not detect variation in life span between… the breeds of dogs" [40] 🟡. In other words, dogs are still canids at the species level.
- Dogs mature earlier and grow faster than wolves:

  | Trait (AnAge) | Dog | Wolf |
  |---|---|---|
  | Female sexual maturity | 510 d | 669 d |
  | Gompertz postnatal growth constant | 0.0244 d⁻¹ | 0.0177 d⁻¹ |

  Source: [5, 9] ✅ (AnAge growth constants rest on limited data). Free-living dogs show less seasonal breeding, higher fecundity and reduced parental care than other Canis [26] 🟡.
- **Hypothesis.** Human-controlled breeding mostly selects on appearance, behaviour and early reproduction. It does not select for late-life health, because sires and dams are typically bred young. Mutation-accumulation and antagonistic-pleiotropy logic therefore still applies under domestication, and the low extrinsic mortality dogs now enjoy has had no time, and no selective route, to lengthen intrinsic lifespan. This is plausible, but I found no direct test.
- **Size.** Artificial selection produced roughly 50-fold differences in body mass. Within dogs, large size shortens life mainly because large dogs **age faster** (a steeper hazard slope across 74 breeds), not because ageing starts earlier [27] 🟡. A 2026 comparative test supports an "adaptive lag" hypothesis: large modern breeds have not had time to evolve the cancer suppression that large-bodied species normally possess. Ancient breeds live longer than modern breeds of the same size [28] 🟡 (single-author study; correlational). Details are in `./breed_size_genetics_lifespan.md`.

### 2.4 What happened to humans

- Wild chimpanzees have life expectancy at birth below 15 y. Human foragers have much lower early-adult mortality, which "may partially explain why humans have evolved to senesce later than chimpanzees" [29] 🟡.
- **Grandmother hypothesis.** Food sharing by post-reproductive women raised their daughters' fertility, increasing selection against senescence. Combined with Charnov's life-history rules, this also accounts for late human maturity [30] 🟡. Status: influential hypothesis, still debated.
- Humans have a very slow life history: female maturity about 13 y, single births, 280-d gestation [11] ✅. Primates as a group live long for their size (chimpanzees 270%) [15] ✅, and humans extend this further (463%) [11] ✅.

### 2.5 Caveats and criticisms

- **Williams' extrinsic-mortality prediction is formally contested.** Moorad, Promislow & Silvertown (2019) argue that formal theory shows "it is wrong" in its simple form. The direction of the effect depends on *how* mortality sources act across ages and on density dependence [23] 🟡. See also Day & Abrams 2020 [24] 🟡. The comparative pattern (flight, arboreality, fossoriality and island life correlate with long life [18, 25]) is real. Its explanation should be framed as "age-specific vulnerability and density regulation", not simply "high extrinsic mortality → fast ageing".
- **None of these theories has been tested in canids.** Applying them to wolves and dogs is inference.
- **Body-size confounding.** Within dogs, larger means shorter-lived; across species, larger means longer-lived [27]. Any explanation must handle both.

---

## 3. Proximate (mechanistic) correlates of species lifespan, with dog data where it exists

**Read this first.** The mechanisms below roughly follow the "hallmarks of ageing" framework [93]. Most cross-species ageing studies did **not** include dogs. The table flags where dog data exist. A correlate of species lifespan is not necessarily a cause.

| Mechanism | Dog-specific data? | Dog vs human | Status for "why dogs are short-lived" |
|---|---|---|---|
| Somatic mutation rate | Yes (3 dogs) [32] | 5.3× faster | Well-supported correlation; causality doubtful [33] |
| Epigenetic (methylation) ageing rate | Yes (many studies) [35–37, 43] | Nonlinear; fast early | Well-supported correlation; causality unknown |
| Telomere attrition | Yes [47, 48] | ~10× faster | Correlation (within dogs and across species) |
| DNA double-strand-break repair / SIRT6 | **No** comparable dog data | Unknown | Hypothesis for dogs |
| Cancer suppression (Peto) | Dog cause-of-death data [1, 58–60] | Dogs: cancer is the leading cause of death; humans: 11–25% cancer mortality [55] | Plausible contributor |
| Metabolic rate (rate-of-living) | Indirect | ~1.2× (Kleiber) | Largely refuted as an explanation |
| Mitochondrial ROS | **No** dog data in key studies [67] | Unknown | Weak evidence overall |
| GH/IGF-1, mTOR | Yes, within dogs [69, 70, 73] | — | Strong lever in models; plausible lever in dogs |
| Proteome turnover | **No** dog data [66] | Unknown | Correlation (r ≈ −0.89 across 12 species) |
| Developmental tempo | **No** dog cells in tempo assays [62–65] | Maturity ~9× faster | Hypothesis; candidate unifying cause |
| Senescence, immunity, stem cells | Sparse [42, 74] | Unknown | Gap |

### 3.1 Somatic mutation rates (Cagan et al. 2022, Nature)

**Study.** Cross-species comparative; whole-genome sequencing of 208 colorectal crypts from 56 individuals of 16 mammal species [32] ✅. I opened the full text and supplementary tables.

**Core findings** [32] ✅:
- Substitution rates ranged from **47 SBS/genome/year in humans to 796 in mice**.
- The inverse of lifespan explained **82%** of inter-species variance (zero-intercept model; slope k = 3,206.4 SBS; 95% CI 2,683.9–3,728.9).
- Body mass explained much less (FVE = 0.21).
- The expected end-of-lifespan burden varied only about 3-fold across species (range about 1,828–5,379).

**Dogs specifically** [32] 🟡 (Suppl. Tables 4, 6, 9 as cited by the original author; the main text points to "Supplementary Tables 3 and 6" for species-level estimates) [verifier-corrected: the verifier could not re-open the supplementary spreadsheets; the dog-specific numbers below are consistent with the main text (which gives the 16-species ranges and the human values) but are not independently confirmed]:

| | Dog | Human |
|---|---|---|
| Sample | 3 dogs, 11 crypts, aged 4.99–11.99 y | 8 people, 28 crypts |
| Mean substitution rate | **249.5 SBS/genome/year** | **47.1** |
| Rate ratio | 5.3× | — |
| "Lifespan" used (age by which 80% of adults had died) | **15.26 y**, from zoo records pooling domestic dogs and wolves "because of the paucity of records for domestic dogs" | 83.7 y |
| Implied end-of-life burden *(my calculation)* | 249.5 × 15.26 ≈ **3,810** | 47.1 × 83.7 ≈ **3,940** |

- **Interpretation (well-supported correlation).** Dogs pile up mutations about 5× faster and die about 5.5× sooner. They end with roughly the same mutational load as a human at the end of life.
- **Cautions:**
  1. The dog sample is tiny and covers one tissue.
  2. The dog "lifespan" figure is partly wolf data.
  3. Humans with germline POLE/POLD1 proofreading defects carry markedly higher somatic burdens. Apart from higher cancer risk they "do not exhibit overt features of premature aging" [33] 🟡. This argues that somatic mutations are not *the* cause of ageing.
  4. Across 292 tetrapod species (16,049 necropsies), malignancy prevalence increases with adult mass and with somatic mutation rate, but the mutation-rate association "was only apparent when we controlled for gestation time" [34] 🟡 [verifier-corrected: added the conditional]. Faster mutation in dogs may therefore matter for **cancer**, the leading cause of death in old dogs (§5), though this cross-species link is weaker than the sentence originally implied.
- **Research lever? Probably not directly.** Mutation rate is set by many repair and replication pathways. It is more useful as a readout.

### 3.2 Epigenetic clocks and rates

| Study | Design | Key result | Tag |
|---|---|---|---|
| Thompson et al. 2017, *Aging* | Reduced-representation bisulfite sequencing of blood; 46 dogs, 62 wild gray wolves | Accurate clocks for dogs (41 CpGs), wolves (67) and combined (115). Age-related methylation hits gene categories similar to humans. | 🟡 [35] |
| **Wang et al. 2020, *Cell Systems*** | Oligo-capture methylomes; 104 dogs (mostly Labradors) aged 0.1–16 y, compared with 320 humans aged 1–103 | Two reciprocal fits (17·ln(x)+33 and 16·ln(x)+30) combined into **human_age = 16·ln(dog_age) + 31**. Remodelling is "very rapid… in early life" in dogs, then slows. A 12-y Labrador maps to about 70 human years. Conserved changes centre on developmental gene networks. | ✅ [36] |
| Horvath et al. 2022, *PNAS* | Mammalian methylation array; 742 blood samples from 93 breeds | Dog clocks; human–dog dual-species clocks (R = 0.97); relative-age clock (dog max 24 y vs human 122.5 y). **No significant association** between epigenetic age acceleration and breed median lifespan, upper lifespan, weight or height. [verifier-corrected: the same paper then built a different biomarker, DNAmAverageTimeToDeath, which *did* associate with breed lifespan and weight, so the null is specific to age-acceleration residuals.] | ✅ [37] |
| **Lu et al. 2023, *Nature Aging*** | 11,754 arrays; 185 species; 59 tissues | Universal clocks (r ≥ 0.95); dogs r = 0.94. Clocks "tick faster during development". Age at sexual maturity and gestation time explain over 69% of log maximum-lifespan variation. Ageing is "evolutionarily conserved and intertwined with developmental processes". | ✅ [38] |
| Haghani et al. 2023, *Science* | 15,456 profiles; 348 species | 30 of 55 co-methylation modules relate to traits. Maximum lifespan is associated with methylation of HOXL-subclass homeobox and developmental genes. | 🟡 [39] |
| Li et al. 2024, *Science Advances* | Same consortium | DNA-methylation predictor of maximum lifespan (R = 0.89). It does **not** detect differences between dog breeds. Species lifespan appears to be an intrinsic epigenetic signature, distinct from individual mortality risk. | 🟡 [40] |
| Crofts et al. 2024, *Nature Aging* | 42 species, conserved age-related CpGs | Methylation rates scale as a power law with maximum lifespan: slope −0.95 in blood (R² = 0.81), −0.60 in skin (R² = 0.80). | ✅ [41] |
| Jin et al. 2024, *Aging Cell* | 71 dogs; methylation and ATAC-seq of peripheral blood mononuclear cells | Chromatin accessibility also predicts age (R² 26% vs 33% for methylation). CD62L+ T-cell subsets correlate with age. | 🟡 [42] |
| McCoy et al. 2024 (bioRxiv preprint; not peer-reviewed as of this writing — [verifier-confirmed: Crossref and Europe PMC list only the bioRxiv record as of 2026-10-04]) | 864 Dog Aging Project dogs | Largest size class about 0.37 epigenetic years older per chronological year than the smallest. 34% higher death risk per year of residual epigenetic age. | 🟡 [43] |
| Jang et al. 2026, *PNAS* | Korean and US dog cohorts | Epigenetic drift is structured and varies with body size. Korean dogs show consistently higher epigenetic age acceleration than US dogs. | 🟡 [44] |
| Herzig et al. 2025, *GeroScience* | 829 dogs, 12 y of clinical blood tests | Biological-age deviation predicts death (HR 1.75 per year). Lifelong diet restriction lowered biological age. | 🟡 [45] |

**Interpretation:**
- **Well-supported correlation.** Methylation rates track species lifespan, and dog methylomes change fastest in puppyhood.
- **Hypothesis.** The lifespan signature sits in developmental (HOX/Polycomb) networks [38–40], which suggests that the developmental programme and the ageing rate are linked (§3.9).
- **Unresolved.** Is epigenetic drift a cause of ageing or a clock face? Partial reprogramming can restore some youthful epigenetic information and function in mice [46] 🟡. Whether slowing or reversing methylation drift extends dog lifespan is untested.
- **Unexplained discrepancy (❓).** Large breeds age faster *demographically* [27], and a large preprint finds faster *epigenetic* ageing in big dogs [43]. Yet Horvath 2022 [37] found no breed-level epigenetic acceleration. Possible reasons are different platforms, cohorts and models. A secondary web summary claimed that giant breeds accumulate drift "40% faster". I could not find that figure in the primary paper; treat it as unverified.

### 3.3 Telomeres and telomerase

- **Dog telomere biology is human-like.** Telomere restriction fragments are 12–23 kb, with "little or no activity" of telomerase in normal somatic tissues [47] 🟡. Across more than 60 mammals, short telomeres plus repressed telomerase appear to be the ancestral state. Telomere length correlates inversely with lifespan, while telomerase expression co-evolves with **body size** [50, 51] 🟡.
- **Fick et al. 2012** (dog cohort; 15 breeds) [48] 🟡:
  - Blood-cell telomere length strongly predicts breed average lifespan (p < 0.0001).
  - "Dogs lose telomeric DNA ~10-fold faster than humans", similar to the ratio of their lifespans.
  - Breeds with shorter telomeres die more often of cardiovascular disease.
- **Whittemore et al. 2019, PNAS** [49] ✅:
  - Telomere *shortening rate*, not initial length, predicts species lifespan (power law: R² = 0.829 for maximum and 0.934 for average lifespan).
  - Rates: mouse 6,420 bp/y; human about 70 bp/y (from the literature).
  - **Dogs were not included.** The species were mouse, goat, gull, reindeer, vulture, dolphin, flamingo, elephant, plus humans from the literature.
- **Status: well-supported correlation.** Telomere attrition probably reflects cell turnover and damage rates rather than acting as a master timer. No study shows that lengthening telomeres in dogs extends lifespan.

### 3.4 DNA repair, cancer suppression and Peto's paradox

- **Repair co-evolves with longevity in rodents** (cross-species comparative, cell culture) [52] 🟡:
  - Across 18 rodent species, double-strand-break (DSB) repair, but not nucleotide-excision repair, co-evolves with longevity.
  - SIRT6 activity accounts for much of the difference.
  - Five amino-acid residues explain the gap between a weak SIRT6 (mouse) and a strong one (beaver).
- **Bowhead whale (over 200 y)** (cell culture, plus a Drosophila model) [53] 🟡:
  - Bowhead cells need *fewer* oncogenic hits to transform than human cells.
  - However, they show enhanced DSB repair capacity and fidelity, and lower mutation rates.
  - The protein CIRBP is highly expressed. Bowhead CIRBP boosts repair in human cells and extends fruit-fly lifespan.
- **Dog gap.** I found no head-to-head DSB-repair or SIRT6 comparison of dog vs human or wolf cells. This is an obvious experiment (see §6).
- **Peto's paradox** (cross-species comparative) [54] ✅:
  - Across 110,148 adult zoo mammals of 191 species, cancer mortality is "largely independent" of body mass and life expectancy.
  - **Carnivora have the highest cancer mortality**, especially mammal-eaters.
  - Vincze et al. also cite evidence that larger *individuals within* dogs are more cancer-prone.
  - Elephants have about 20 TP53 copies (19 retrogenes), stronger p53-mediated apoptosis and an estimated 4.81% cancer mortality, versus 11–25% in humans [55] 🟡 (see also [56, 57]).
- **Dogs (dog cohort / necropsy).** Cancer is the most common cause of death in several datasets:
  - 27% of 15,881 UK pedigree deaths [59] 🟡.
  - Neoplasia is the most frequent cause in English first-opinion data [1] 🟡.
  - Older dogs die more of neoplastic and neurological causes [60] 🟡.
  - In 2,002 necropsies, cancer caused 20% of deaths at age 5, rising to 40–50% from age 10 to 16 [58] 🟡.
  - The widely repeated "half of dogs over 10 develop cancer" is probably a garbled version of such cause-of-death data, which also comes from referral or necropsy samples. As an incidence statistic it is ❓.
- **Hypothesis.** Dogs combine a carnivoran tendency to cancer, a fast somatic mutation rate, and (in large breeds) an "adaptive lag" in cancer suppression [28]. This makes cancer the proximate killer that most often sets realised dog lifespan.

### 3.5 Metabolic rate and the "rate of living"

- **Kleiber argument (my calculation).** Mass-specific metabolic rate scales roughly as M^−0.25. A 30-kg dog and a 62-kg human are therefore expected to differ by only (62/30)^0.25 ≈ **1.2×** per gram. That cannot explain a 5–6× lifespan gap.
- After correcting for body mass and phylogeny, basal metabolic rate does not correlate with longevity in eutherian mammals or birds [17] 🟡. Bats outlive similar-sized eutherians at least 3-fold regardless of metabolic rate or torpor [16] 🟡. See the review by Speakman [61] 🟡.
- **Status.** The rate-of-living theory as a general law is **largely refuted**.
- **A subtle revival at the cellular level (contested).**
  - Diaz-Cuadros et al. 2023 showed that mass-specific metabolic rates scale with the twofold mouse-vs-human difference in developmental rate. Inhibiting the electron transport chain slowed the segmentation clock, and raising NAD⁺/NADH sped it up [62] 🟡 (cell culture).
  - Lázaro et al. 2023, comparing six species, found that cellular metabolic rates "did not show an evident correlation" with segmentation-clock period. Instead, the expression of genes for biochemical reactions scaled with it [63] 🟡.
  - The task brief described Lázaro et al. as showing that metabolic rate sets tempo. That is **not** what the abstract says.

### 3.6 Mitochondria and reactive oxygen species (ROS)

- Heart mitochondria from longer-lived homeotherms produce less H₂O₂ at complex I during reverse electron transport (12 species; no dogs). After phylogenetic correction the association was significant by sign test but "fell short of significance by regression analysis" [67] 🟡.
- Antioxidant manipulations in mice mostly fail to extend lifespan; see the review asking whether oxidative-stress theory is dead [68] 🟡.
- **Status.** A weak correlate; no dog data.

### 3.7 Nutrient sensing: GH/IGF-1 and mTOR

- **Across species.** The Brandt's bat (4–8 g; lives over 40 y) carries unique changes in the growth-hormone receptor and IGF-1 receptor [71] 🟡. In mice, growth-hormone receptor knockout and caloric restriction (CR) shift lifespan-associated methylation modules [39] 🟡. Rapamycin (an mTOR inhibitor) extends mouse lifespan even when started late in life [72] 🟡 (mouse model).
- **Within dogs:**
  - A single IGF1 allele is a major determinant of small size [69] 🟡.
  - Serum IGF-1 falls with age and rises with body weight [70] 🟡.
  - 25% diet restriction from 8 weeks of age significantly increased median lifespan and delayed chronic disease in 48 paired Labradors [73] 🟡.
- **Status.** Within species, this pathway is the best-supported *lever* in animal models, and it is plausibly relevant to the dog size–lifespan trade-off. Across species, it is a contributor, not the whole story. Dog interventions (e.g., the TRIAD rapamycin trial [91]) are covered in `../05_interventions/`.

### 3.8 Proteostasis and protein turnover

- Across fibroblasts from 12 mammals (no dogs), protein turnover rates correlate negatively with maximum lifespan (r = −0.89). The correlation stays significant after phylogenetic correction. Long-lived naked mole-rat cells turn proteins over more slowly yet handle misfolding stress better [66] ✅.
- Mouse cells run the motor-neuron differentiation programme more than 2× faster than human cells. This is due to about 2× lower protein stability and shorter cell cycles, not to differences in gene sequence or signalling [64] 🟡.
- Segmentation-clock periods are 2–3 h in mouse cells and 5–6 h in human cells, because of slower HES7 biochemical reactions (degradation and expression delays) in human cells [65] 🟡.
- **Hypothesis.** Faster turnover and biochemical kinetics in short-lived species are part of a coordinated cellular "tempo" that sets both development and ageing.

### 3.9 Developmental timing: is ageing rate coupled to developmental rate?

- **Established comparative pattern.** "Age at maturity is typically proportional to adult life span." Mammals that live long for their size (bats, primates) also develop slowly for their size, and postnatal growth rate correlates negatively with adult lifespan [17] 🟡. Hou 2024 argues that the energetic cost of biosynthesis links growth rate and longevity [77] 🟡.
- **Epigenetic evidence.** Lu et al. found that age at maturity plus gestation explains over 69% of maximum-lifespan variance, and clocks tick faster during development [38] ✅. Wang et al. found that the dog-to-human methylome mapping lines up developmental milestones [36] ✅:
  - Infant stage: about 8 weeks in dogs ≈ 9 months in humans, when deciduous teeth appear in both.
  - Adolescence: 6 months–2 y in dogs vs about 12–25 y in humans.
- **Dog numbers.** Female maturity: dog 510 d, wolf 669 d, human 4,745 d [5, 9, 11] ✅. Dogs are therefore about 9× faster to maturity, a somewhat larger factor than the about 5–6× lifespan ratio.
- **Hypothesis (well-supported correlation).** Developmental tempo and ageing rate are coupled outputs of shared species-specific cellular kinetics (protein turnover, biochemical reaction speeds) and of developmental gene-regulatory networks [38–40, 62–66].
- **Speculation.** Lifespan could be slowed by "slowing the developmental clock". There is no direct evidence for this in mammals beyond correlational and pharmacological hints.
- **Gap.** None of the stem-cell-zoo tempo studies has included dog or wolf cells [63].

### 3.10 Long-lived species: lessons and how they apply to dogs

| Species | Longevity | Proposed mechanism | Applicability to dogs | Tag |
|---|---|---|---|---|
| Naked mole-rat | Over 30 y (a mouse of similar size: ~4 y) | Very high-molecular-mass hyaluronan (more than 5× larger than human or mouse); cells resist transformation [84]. Mice given the naked mole-rat Has2 gene had less cancer, longer lifespan, better healthspan and less inflammation [85]. | Transferable mechanism *in principle*; untested in dogs | 🟡 |
| Bowhead whale | Over 200 y | Enhanced DSB repair and fidelity; high CIRBP and RPA2 [53] | CIRBP levels and repair fidelity in dog cells are unknown; testable | 🟡 |
| Elephants | ~65–70 y ❓ | About 20 TP53 copies; LIF6 "zombie gene" pro-apoptotic response [55–57] | Shows that cancer suppression can be amplified; dogs are TP53-standard ❓ | 🟡 |
| Brandt's bat | 41 y (wild record) at 4–8 g | GHR/IGF1R changes, hibernation, low reproductive rate [71, 86] | Supports the GH/IGF-1 lever | 🟡 |
| Pacific rockfishes | Some among the longest-lived vertebrates (≈200 y ❓) | Positive selection in DNA repair; insulin signalling; immune-modulating butyrophilin gene expansions [88] | Comparative-genomics template for a dog-breed scan | 🟡 |
| Greenland shark | Largest animal 392 ± 120 y; maturity at least 156 ± 22 y | Cold, slow life history [87] | Mainly illustrates the extreme slow-tempo end; little direct transfer | 🟡 |

### 3.11 Senescence, immune ageing, stem cells, and systems models

- **Cellular senescence and stem cells in dogs.** I found little dog-specific comparative data. **Gap.** Reviews summarise canine hallmarks [92] 🟡.
- **Immune ageing.** Dogs show inflammageing and immunosenescence [74] 🟡. Labrador T- and B-cell counts decline with age (Greeley et al. 2001, cited in [36]) ✅. CD62L+ T-cell subsets correlate with age [42] 🟡.
- **Damage-accumulation model (modelling; Raz et al. 2026)** [75] ✅:
  - Survival curves from yeast to humans were fitted with a stochastic "saturating-removal" model.
  - The damage *production* rate is the parameter that best predicts lifespan.
  - Dogs (UK breeds), cats, guinea pigs and humans share a "quasi-steady-state" ageing regime with Gompertz-like hazard curves.
  - In dimensionless parameter space, the species closest to humans were dogs (except the German Shepherd), cats and guinea pigs.
  - For Labradors the fitted removal parameter (β ≈ 0.044/day) is similar to humans' (≈ 0.046–0.048/day). The production parameter is higher (η ≈ 3.7 × 10⁻⁶ vs ≈ 1.1 × 10⁻⁶, in model units) with wide credible intervals.
  - **Status: model-based hypothesis** ("awaits experimental validation").
- **Matrenok et al. 2026 (preprint; 99 retired sled dogs)** [76] 🟡. This lamivudine trial proposes a "phenotypic temperature" that governs the Gompertz parameters but not the slope of damage accumulation. It is a preprint, and lamivudine's effects were reversible.

---

## 4. "Dog years": conversions and what they mean

### 4.1 The 7× rule is a myth

No single multiplier works:
- Dogs mature about 9× faster than humans but die only about 5–6× sooner (§1.6).
- The epigenetic mapping is strongly nonlinear [36] ✅.

The origin of the 7× rule is folklore; I found no primary source.

### 4.2 Wang et al. 2020 log formula (exact)

**human_age = 16 · ln(dog_age) + 31** (ages in years) [36] ✅

- It was derived by combining two reciprocal nearest-neighbour fits, human_age = 17·ln(x)+33 and 16·ln(x)+30, from blood methylomes of 95 analysable dogs (mostly Labradors) and 320 humans [36] ✅.

| Dog age | 0.25 | 0.5 | 1 | 2 | 4 | 6 | 8 | 10 | 12 | 14 | 16 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Human-equivalent (y) | 8.8 | 19.9 | 31.0 | 42.1 | 53.2 | 59.7 | 64.3 | 67.8 | 70.8 | 73.2 | 75.4 |
| Human-years per dog-year at that age (16/dog_age) | 64 | 32 | 16 | 8 | 4 | 2.7 | 2.0 | 1.6 | 1.3 | 1.1 | 1.0 |

*(Table: my calculation from the formula.)*

**Limitations:**
- The formula was built on one breed and on blood only. The authors note that other breeds "could yield different age-translation functions" [36] ✅.
- It compresses old age. A 16-y dog maps to only about 75 human years, although such dogs are physiologically very old.
- For adolescent and mature stages, "the correspondence was more approximate" [36] ✅.
- It measures methylome similarity, not frailty or mortality risk.

### 4.3 Other conversions

- **Patronek, Waters & Glickman 1997** standardised dog age to human-year equivalents from 23,535 dog deaths. Physiological age differed by 8 to more than 15 human-equivalent years between the smallest and largest weight classes at the same chronological age [78] 🟡. This makes the case for **size-specific** conversion.
- **AAHA 2019 Canine Life Stage Guidelines** use five stages: puppy, young adult, mature adult, senior and end of life [79] 🟡. The senior stage is defined relative to each dog's expected lifespan (I recall "last 25%") ❓; I could not open the full text.
- The widely circulated "first year ≈ 15 human years, second ≈ 9, then ≈ 5 per year" rule is attributed to the AVMA by the American Kennel Club's dog-years article 🟡 [verifier-corrected: upgraded from ❓; the AKC page explicitly attributes the 15/9/5 rule for a medium-sized dog to the AVMA, but the AVMA page itself could not be opened because of bot protection, so the primary attribution remains unconfirmed].
- **Relative-age conversions** (age ÷ species maximum lifespan; e.g., dog 24 y vs human 122.5 y) underpin the dual-species epigenetic clocks [37, 38] ✅.

### 4.4 What the conversions mean biologically

- **Front-loaded epigenetic ageing.** The canine methylome races through developmental remodelling in the first 1–2 years, which corresponds to the human years from birth to the early 40s on the Wang scale [36] ✅. Clocks tick fastest during development in all mammals [38] ✅.
- **Steep adult demographic ageing (my calculation).** I fitted log hazard against age (ages 5–15) on the UK cohort life table in Teng et al. [2] ✅:
  - Gompertz slope ≈ 0.35/y, so **mortality doubles about every 1.95–2.0 y** in adult dogs. [verifier-confirmed: refitting Teng's Table 2 gives a slope of 0.345–0.355/y on ln(hazard) (MRDT 1.95–2.0 y, R² ≥ 0.999) or 0.31–0.34/y on ln(q) (MRDT 2.05–2.2 y), depending on the age window; "about 2 y" is robust.]
  - Humans double about every 8 y [11] ✅, i.e. about 0.087/y.
  - So adult dogs age actuarially about **4× faster**.
  - Caveat: Teng's table is built only from dogs that died in 2016–2020.
- **Reconciling the two.** Epigenetic remodelling slows in adult dogs, but actuarial risk keeps rising steeply. The Wang curve therefore is not a guide to "how much ageing per year" in senior dogs. Annual mortality is ≤ 0.02 before age 5, becomes prominent after about 6–7, and is 0.134 at 10–11, 0.244 at 12–13 and 0.417 at 14–15 [2] ✅.

---

## 5. The ageing trajectory in dogs

- **Life-table shape (dog cohort, UK)** [2] ✅. Annual death probability stays at or below 0.02 until age 5, rises noticeably after 6–7, and passes 0.5 at 15–16. Dogs, like humans, show a Gompertz-like hazard [75] ✅.
- **Causes of death by age** (dog cohorts; North American teaching hospitals, 74,556 dogs) [60] 🟡:
  - Young dogs die more often of gastrointestinal and infectious causes.
  - Older dogs die more often of **neurological and neoplastic** causes.
  - Cardiovascular, endocrine and urogenital deaths rise with age.
  - Larger breeds die more of musculoskeletal and gastrointestinal causes; smaller breeds more of endocrine causes.
  - UK data: neoplastic, musculoskeletal and neurological causes predominate [1]. In pedigree dogs: cancer 27%, "old age" 18%, cardiac 11% [59] 🟡.
- **Canine cognitive dysfunction** (Dog Aging Project, 15,019 dogs) [80] 🟡. Odds of CCD rose **52% per additional year of age**. Inactive dogs had 6.47× higher odds than very active dogs (association; direction of causality unclear).
- **Frailty** (CaniAge cohort, 566 dogs aged 6 y and over) [81] 🟡. Frailty prevalence was 6.36% by a frailty index and 8.48% by a frailty phenotype, with limited overlap between the two. The OLD-DOG project (209 dogs aged 5 and over, followed for 30 months) is validating biomarkers [82] 🟡.
- **Healthspan vs lifespan.** Dogs share the human environment and healthcare. They develop the same multimorbidities: cancer, cardiac disease, CCD with amyloid deposits, and hearing loss [5, 83]. Diet restriction in Labradors delayed the onset of chronic disease [73] 🟡, showing that dog healthspan is modifiable.
- **Size within dogs (summary only; see `./breed_size_genetics_lifespan.md`).**
  - Bigger dogs die younger, mainly because they age faster (a steeper hazard slope) [27] 🟡.
  - UK medians: small 12.7 y, medium 12.5 y, large 11.9 y [4] ✅.
  - Telomere length tracks breed lifespan [48] 🟡.
  - IGF-1 is higher in larger dogs [70] 🟡.
  - Ancient breeds outlive modern breeds of the same size [28] 🟡.

---

## 6. Synthesis: why do dogs live about 5–6× shorter than humans?

### 6.1 A layered answer

| Layer | Answer | Evidence level |
|---|---|---|
| 0. Reframe | Dogs are roughly *on* the mammalian body-mass–lifespan line. Humans are about 4.6× *above* it. | Established (comparative data) [5, 11, 14] |
| 1. Ultimate: wolf ancestry | Canid ecology (high adult mortality, early large litters) gave weak selection for maintenance after about 10 y, so the canid lifespan setting is about 15–20 y. | Hypothesis consistent with established theory; contested details [19–23] |
| 2. Ultimate: humans | Low early-adult mortality, slow maturation, and possibly grandmothering selected for slow senescence. | Hypothesis, well supported comparatively [29, 30] |
| 3. Domestication | Recent; did not select for late-life health; sped up development; created large breeds with faster ageing and lagging cancer suppression. | Hypothesis [26–28] |
| 4. Life-history tempo | Development and ageing run on coupled, species-specific cellular kinetics: maturity about 9× faster, mortality-rate doubling about 4× faster. | Well-supported correlation [17, 38, 62–66]; causation unproven |
| 5. Cellular "clocks" | Somatic mutation (5.3×), telomere loss (~10×) and methylation drift all scale with lifespan. Dogs reach human-like end-of-life burdens in about 12–15 y. | Well-supported correlations [32, 41, 48]; mostly *readouts*, not proven causes [33] |
| 6. Proximate killers | Cancer (carnivore predisposition plus fast mutation), neurodegeneration, cardiac disease. | Well-supported, dog cohorts [1, 54, 58–60] |

### 6.2 Levers vs correlates

| Candidate | Likely a lever? | Why |
|---|---|---|
| Nutrient sensing (IGF-1, mTOR, caloric restriction) | **Yes (most promising)** | Causal in mouse models [72]; diet restriction extends dog median lifespan [73]; IGF-1 is linked to dog size [69, 70] |
| Cancer-suppression pathways (p53, DNA repair, high-molecular-mass hyaluronan, CIRBP) | **Plausible** | Cancer is the top dog killer. Transfer of naked mole-rat HAS2 extended mouse lifespan [85]. CIRBP extended fly lifespan [53]. |
| Epigenetic state | **Unclear** | Good biomarker; reprogramming hints in mice [46]; no dog lifespan data |
| Somatic mutation rate | **Probably correlate** | Humans with high somatic burdens are not prematurely aged [33] |
| Telomeres | **Probably correlate / partial contributor** | No dog intervention data |
| Metabolic rate | **Not the explanation** | Refuted as a general law [16, 17] |
| Developmental tempo | **Unknown; potentially fundamental** | Unclear whether tempo can be changed after development without harm |

### 6.3 What this implies for intervention (speculation)

- **Changing the species clock is unrealistic in the near term.** The dog–human difference spans development, cell kinetics and many pathways at once. Species lifespan is an intrinsic, polygenic and largely developmental property [40].
- **Slowing adult ageing (the rate) is realistic in principle.** Dogs share humans' Gompertz-type ageing regime [75], and diet restriction moves both lifespan and biological-age markers [45, 73]. Rapamycin and related drugs are being tested (TRIAD [91]). Cross-reference: `../05_interventions/`.
- **Disease-specific gains are the most certain.** Cancer screening and prevention, cardiac care, and preventing or managing CCD (activity) can raise *median* lifespan and healthspan without touching the species clock.
- **Large breeds may offer a special opportunity** because their extra ageing rate is recent and partly IGF-1- and cancer-linked [27, 28, 70].

### 6.4 Research paths (PROPOSAL — speculative by design)

1. **Canine "stem-cell zoo" tempo study.** Derive induced pluripotent stem cells from toy and giant dogs, wolves and humans. Measure segmentation-clock period, protein half-lives and metabolic rate [62–65]. Test whether breed size or species changes intracellular tempo, and whether tempo predicts lifespan.
2. **Dog somatic-mutation atlas.** Extend Cagan's 3 dogs to hundreds across breeds, ages and tissues, for example from the Dog Aging Project biobank [90]. Test whether large breeds have higher per-year substitution rates, linking to the adaptive-lag cancer hypothesis [28].
3. **Head-to-head DNA-repair assays.** Compare DSB repair efficiency and fidelity and SIRT6 activity in dog, wolf and human fibroblasts, and in short- vs long-lived breeds [52]. Measure CIRBP and RPA2 levels [53].
4. **Comparative genomics across dog breeds and wild canids.** Use the rockfish design [88] to look for selection signatures in DNA repair and insulin signalling in long-lived breeds and canids.
5. **Decompose the Gompertz parameters per breed.** Separate initial mortality from the rate of increase [27, 75] in Dog Aging Project and VetCompass data. Classify interventions as rate-slowing or onset-delaying.
6. **Validate epigenetic and clinical biological-age clocks as trial endpoints.** Use the clocks in [43–45] and resolve the size-acceleration discrepancy (Horvath 2022 vs McCoy 2024).

---

## 7. Cross-references

- Within-dog size, breed genetics (IGF1, GHR, etc.) and wolf vs dog comparisons: `./breed_size_genetics_lifespan.md`, `./wolves_vs_dogs.md`.
- Interventions (rapamycin/TRIAD, caloric restriction, LOY-series drugs, senolytics, gene therapy): `../05_interventions/`.
- AI and structural tools (AlphaFold, IBM MAMMAL) for exploring candidate proteins such as SIRT6, CIRBP, TP53 or HAS2: `../01_alphafold/`, `../02_mammal/`.

---

## Open questions / gaps

1. **No dog cells in key comparative mechanism studies:**
   - SIRT6 and DSB repair [52].
   - Protein turnover [66].
   - Mitochondrial H₂O₂ [67].
   - Fibroblast profiling across 16 mammals [89].
   - Stem-cell-zoo tempo [63].
   - Telomere-shortening-rate scaling [49].
2. **Cagan's dog data are thin.** Three dogs, colon only, and a "lifespan" pooled with wolves.
3. **Contradictory evidence on whether large breeds age faster epigenetically** [37] vs [43]. The faster-ageing result is still a preprint as far as Europe PMC shows.
4. **Causality.** For mutation, methylation and telomeres, it is unknown whether the faster rates *cause* the short lifespan or are coordinated readouts of a faster life history.
5. **The extrinsic-mortality explanation is theoretically contested** [23, 24] and untested in canids.
6. **Dog cancer incidence.** There is no robust population incidence figure for "cancer in dogs over 10"; the commonly quoted 50% is unverified.
7. **Record ages.** Pre-1940 Guinness dog records (Bluey) cannot be independently validated.
8. **Developmental tempo vs ageing.** It is unknown whether tempo can be changed post-development, and whether doing so would extend lifespan.
9. **Health of very old dogs.** Data on frailty, senescent-cell burden and stem-cell exhaustion in old dogs are sparse.

---

## Sources

1. O'Neill DG, Church DB, McGreevy PD, Thomson PC, Brodbelt DC (2013). Longevity and mortality of owned dogs in England. *Vet J* 198(3):638–643. doi:10.1016/j.tvjl.2013.09.020 🟡
2. Teng KT, Brodbelt DC, Pegram C, Church DB, O'Neill DG (2022). Life tables of annual life expectancy and mortality for companion dogs in the United Kingdom. *Sci Rep* 12:6415. doi:10.1038/s41598-022-10341-6 ✅ (full text and Table 2 via Europe PMC)
3. Montoya M, Morrison JA, Arrignon F, et al. (2023). Life expectancy tables for dogs and cats derived from clinical data. *Front Vet Sci* 10:1082102. doi:10.3389/fvets.2023.1082102 🟡
4. McMillan KM, Bielby J, Williams CL, Upjohn MM, Casey RA, Christley RM (2024). Longevity of companion dog breeds: those at risk from early death. *Sci Rep* 14:531. doi:10.1038/s41598-023-50458-w (Author Correction doi:10.1038/s41598-024-59331-w, a figure-legend fix only) ✅
5. AnAge: Domestic dog (*Canis familiaris*) entry. Human Ageing Genomic Resources. https://genomics.senescence.info/species/entry.php?species=Canis_familiaris ✅ (accessed 2026-10-04)
6. Jónás D, Sándor S, Tátrai K, Egyed B, Kubinyi E (2020). A preliminary study to investigate the genetic background of longevity based on whole-genome sequence data of two Methuselah dogs. *Front Genet* 11:315. doi:10.3389/fgene.2020.00315 🟡
7. ABC News (Australia) (3 Mar 2024). Rochester's Bluey reclaims title of world's oldest dog after Guinness World Records reviews Bobi's credentials. https://www.abc.net.au/news/2024-03-03/bluey-rochester-dog-reclaims-guinness-world-record-as-oldest-dog/103513372 🟡 (secondary)
8. NPR (22 Feb 2024). Guinness World Records posthumously strips Bobi of his title of 'oldest dog ever'. https://www.npr.org/2024/02/22/1233186931/bobi-guinness-world-records-oldest-dog-ever-title 🟡 (secondary)
9. AnAge: Gray wolf (*Canis lupus*) entry. https://genomics.senescence.info/species/entry.php?species=Canis_lupus ✅
10. U.S. National Park Service. Wolf Ecology – Yellowstone National Park. https://www.nps.gov/yell/learn/nature/wolf.htm ✅ (accessed 2026-10-04)
11. AnAge: Human (*Homo sapiens*) entry. https://genomics.senescence.info/species/entry.php?species=Homo_sapiens ✅
12. Robine JM, Allard M, Herrmann FR, Jeune B (2019). The real facts supporting Jeanne Calment as the oldest ever human. *J Gerontol A* 74(Suppl 1):S13–S20. doi:10.1093/gerona/glz198 🟡
13. United Nations DESA Population Division (2024). World Population Prospects 2024: Summary of Results. https://population.un.org/wpp/ 🟡 (global life expectancy 73.3 y in 2024, via secondary summaries of the report; the verifier also could not open the primary PDF, so this remains 🟡)
14. AnAge help / documentation (longevity residual formula t_max = 4.88·M^0.153). https://genomics.senescence.info/help.html ✅
15. AnAge: Chimpanzee (*Pan troglodytes*) entry. https://genomics.senescence.info/species/entry.php?species=Pan_troglodytes ✅
16. Austad SN, Fischer KE (1991). Mammalian aging, metabolism, and ecology: evidence from the bats and marsupials. *J Gerontol* 46(2):B47–B53. doi:10.1093/geronj/46.2.b47 🟡
17. de Magalhães JP, Costa J, Church GM (2007). An analysis of the relationship between metabolism, developmental schedules, and longevity using phylogenetic independent contrasts. *J Gerontol A* 62(2):149–160. doi:10.1093/gerona/62.2.149 🟡
18. Healy K, Guillerme T, Finlay S, et al. (2014). Ecology and mode-of-life explain lifespan variation in birds and mammals. *Proc R Soc B* 281:20140298. doi:10.1098/rspb.2014.0298 🟡
19. Medawar PB (1952). *An Unsolved Problem of Biology*. H.K. Lewis, London (reprinted in *The Uniqueness of the Individual*). 🟡 (classic; not opened)
20. Williams GC (1957). Pleiotropy, natural selection, and the evolution of senescence. *Evolution* 11(4):398–411. doi:10.1111/j.1558-5646.1957.tb02911.x 🟡
21. Kirkwood TBL (1977). Evolution of ageing. *Nature* 270:301–304. doi:10.1038/270301a0 🟡
22. Kirkwood TBL, Austad SN (2000). Why do we age? *Nature* 408:233–238. doi:10.1038/35041682 🟡
23. Moorad J, Promislow D, Silvertown J (2019). Evolutionary ecology of senescence and a reassessment of Williams' 'extrinsic mortality' hypothesis. *Trends Ecol Evol* 34(6):519–530. doi:10.1016/j.tree.2019.02.006 🟡
24. Day T, Abrams PA (2020). Density dependence, senescence, and Williams' hypothesis. *Trends Ecol Evol* 35(4):300–302. doi:10.1016/j.tree.2019.11.005 🟡 (title/metadata only)
25. Austad SN (1993). Retarded senescence in an insular population of Virginia opossums (*Didelphis virginiana*). *J Zool* 229:695–708. doi:10.1111/j.1469-7998.1993.tb02665.x 🟡 (metadata only; findings from recollection ❓)
26. Lord K, Feinstein M, Smith B, Coppinger R (2013). Variation in reproductive traits of members of the genus *Canis* with special attention to the domestic dog. *Behav Processes* 92:131–142. doi:10.1016/j.beproc.2012.10.009 🟡
27. Kraus C, Pavard S, Promislow DEL (2013). The size–life span trade-off decomposed: why large dogs die young. *Am Nat* 181(4):492–505. doi:10.1086/669665 🟡
28. da Silva J (2026). A test of the adaptive lag hypothesis of the evolution of cancer suppression and lifespan in dog breeds. *Genes* 17(2):139. doi:10.3390/genes17020139 🟡
29. Hill K, Boesch C, Goodall J, Pusey A, Williams J, Wrangham R (2001). Mortality rates among wild chimpanzees. *J Hum Evol* 40(5):437–450. doi:10.1006/jhev.2001.0469 🟡
30. Hawkes K, O'Connell JF, Jones NG, Alvarez H, Charnov EL (1998). Grandmothering, menopause, and the evolution of human life histories. *PNAS* 95(3):1336–1339. doi:10.1073/pnas.95.3.1336 🟡
31. Gurven M, Kaplan H (2007). Longevity among hunter-gatherers: a cross-cultural examination. *Popul Dev Rev* 33(2):321–365. doi:10.1111/j.1728-4457.2007.00171.x ✅ [verifier-corrected: author's PDF opened by the verifier; abstract states "The modal age of adult death is about seven decades"]
32. Cagan A, Baez-Ortega A, Brzozowska N, et al. (2022). Somatic mutation rates scale with lifespan across mammals. *Nature* 604:517–524. doi:10.1038/s41586-022-04618-z ✅ for main-text claims / 🟡 for dog-specific supplementary values (PDF text plus Supplementary Tables 4, 6, 9 opened by the original author via Europe PMC; PMC9021023. [verifier-corrected: main text and Table 1 re-checked and confirmed; the supplementary spreadsheets were not re-opened by the verifier])
33. Robinson PS, Coorens THH, Palles C, et al. (2021). Increased somatic mutation burdens in normal human cells due to defective DNA polymerases. *Nat Genet* 53:1434–1442. doi:10.1038/s41588-021-00930-y 🟡
34. Compton ZT, Mellon W, Harris VK, et al. (2025). Cancer prevalence across vertebrates. *Cancer Discov* 15(1):227–244. doi:10.1158/2159-8290.CD-24-0573 🟡
35. Thompson MJ, vonHoldt B, Horvath S, Pellegrini M (2017). An epigenetic aging clock for dogs and wolves. *Aging (Albany NY)* 9(3):1055–1068. doi:10.18632/aging.101211 🟡
36. Wang T, Ma J, Hogan AN, et al. (2020). Quantitative translation of dog-to-human aging by conserved remodeling of the DNA methylome. *Cell Syst* 11(2):176–185.e6. doi:10.1016/j.cels.2020.06.006 ✅ (full-text PDF)
37. Horvath S, Lu AT, Haghani A, et al. (2022). DNA methylation clocks for dogs and humans. *PNAS* 119(21):e2120887119. doi:10.1073/pnas.2120887119 ✅ (PMC9173771 via WebFetch)
38. Lu AT, Fei Z, Haghani A, et al. (2023). Universal DNA methylation age across mammalian tissues. *Nat Aging* 3:1144–1166. doi:10.1038/s43587-023-00462-6 ✅ (PMC10501909 full text)
39. Haghani A, Li CZ, Robeck TR, et al. (2023). DNA methylation networks underlying mammalian traits. *Science* 381:eabq5693. doi:10.1126/science.abq5693 🟡
40. Li CZ, Haghani A, Yan Q, et al. (2024). Epigenetic predictors of species maximum life span and other life-history traits in mammals. *Sci Adv* 10(23):eadm7273. doi:10.1126/sciadv.adm7273 🟡
41. Crofts SJC, Latorre-Crespo E, Chandra T (2024). DNA methylation rates scale with maximum lifespan across mammals. *Nat Aging* 4(1):27–32 [verifier-corrected: pages added]. doi:10.1038/s43587-023-00535-6 ✅ (PMC10798888 full text)
42. Jin K, McCoy BM, Goldman EA, et al. (2024). DNA methylation and chromatin accessibility predict age in the domestic dog. *Aging Cell* 23(4):e14079. doi:10.1111/acel.14079 🟡
43. McCoy BM, Mariner BL, Cheng CF, et al., Dog Aging Project Consortium (2024). Aging at scale: younger dogs and larger breeds from the Dog Aging Project show accelerated epigenetic aging. *bioRxiv* (preprint). doi:10.1101/2024.10.03.616519 🟡
44. Jang S, Kim SJ, Kang D, et al. (2026). Age-associated epigenetic drift trajectory and cross-national disparities in accelerated aging in domestic dogs. *PNAS* 123(29):e2528874123. doi:10.1073/pnas.2528874123 🟡
45. Herzig S, Zollinger A, Texari L, et al. (2025). A biological age based on common clinical markers predicts health trajectory and mortality risk in dogs. *GeroScience* 47(1):45–59. doi:10.1007/s11357-024-01352-4 🟡
46. Lu Y, Brommer B, Tian X, et al. (2020). Reprogramming to recover youthful epigenetic information and restore vision. *Nature* 588:124–129. doi:10.1038/s41586-020-2975-4 🟡 (title/metadata)
47. Nasir L, Devlin P, McKevitt T, Rutteman G, Argyle DJ (2001). Telomere lengths and telomerase activity in dog tissues: a potential model system to study human telomere and telomerase biology. *Neoplasia* 3(4):351–359. doi:10.1038/sj.neo.7900173 🟡
48. Fick LJ, Fick GH, Li Z, et al. (2012). Telomere length correlates with life span of dog breeds. *Cell Rep* 2(6):1530–1536. doi:10.1016/j.celrep.2012.11.021 🟡
49. Whittemore K, Vera E, Martínez-Nevado E, Sanpera C, Blasco MA (2019). Telomere shortening rate predicts species life span. *PNAS* 116(30):15122–15127. doi:10.1073/pnas.1902452116 ✅ (PMC6660761)
50. Gomes NMV, Ryder OA, Houck ML, et al. (2011). Comparative biology of mammalian telomeres: hypotheses on ancestral states and the roles of telomeres in longevity determination. *Aging Cell* 10(5):761–768. doi:10.1111/j.1474-9726.2011.00718.x 🟡
51. Seluanov A, Chen Z, Hine C, et al. (2007). Telomerase activity coevolves with body mass not lifespan. *Aging Cell* 6(1):45–52. doi:10.1111/j.1474-9726.2006.00262.x 🟡
52. Tian X, Firsanov D, Zhang Z, et al. (2019). SIRT6 is responsible for more efficient DNA double-strand break repair in long-lived species. *Cell* 177(3):622–638.e22. doi:10.1016/j.cell.2019.03.043 🟡
53. Firsanov D, Zacher M, Tian X, et al. (2025). Evidence for improved DNA repair in the long-lived bowhead whale. *Nature* 648:717–725. doi:10.1038/s41586-025-09694-5 🟡 (preprint version: bioRxiv doi:10.1101/2023.05.07.539748)
54. Vincze O, Colchero F, Lemaître JF, et al. (2022). Cancer risk across mammals. *Nature* 601:263–267. doi:10.1038/s41586-021-04224-5 ✅ (PMC8755536 full text)
55. Abegglen LM, Caulin AF, Chan A, et al. (2015). Potential mechanisms for cancer resistance in elephants and comparative cellular response to DNA damage in humans. *JAMA* 314(17):1850–1860. doi:10.1001/jama.2015.13134 🟡
56. Sulak M, Fong L, Mika K, et al. (2016). TP53 copy number expansion is associated with the evolution of increased body size and an enhanced DNA damage response in elephants. *eLife* 5:e11994. doi:10.7554/eLife.11994 🟡 (metadata)
57. Vazquez JM, Sulak M, Chigurupati S, Lynch VJ (2018). A zombie LIF gene in elephants is upregulated by TP53 to induce apoptosis in response to DNA damage. *Cell Rep* 24(7):1765–1776. doi:10.1016/j.celrep.2018.07.042 🟡 (title/metadata)
58. Bronson RT (1982). Variation in age at death of dogs of different sexes and breeds. *Am J Vet Res* 43(11):2057–2059. PMID 6891194 🟡
59. Adams VJ, Evans KM, Sampson J, Wood JLN (2010). Methods and mortality results of a health survey of purebred dogs in the UK. *J Small Anim Pract* 51(10):512–524. doi:10.1111/j.1748-5827.2010.00974.x 🟡
60. Fleming JM, Creevy KE, Promislow DEL (2011). Mortality in North American dogs from 1984 to 2004: an investigation into age-, size-, and breed-related causes of death. *J Vet Intern Med* 25(2):187–198. doi:10.1111/j.1939-1676.2011.0695.x 🟡
61. Speakman JR (2005). Body size, energy metabolism and lifespan. *J Exp Biol* 208:1717–1730. doi:10.1242/jeb.01556 🟡 (title/metadata)
62. Diaz-Cuadros M, Miettinen TP, Skinner OS, et al. (2023). Metabolic regulation of species-specific developmental rates. *Nature* 613:550–557. doi:10.1038/s41586-022-05574-4 🟡
63. Lázaro J, Costanzo M, Sanaki-Matsumiya M, et al. (2023). A stem cell zoo uncovers intracellular scaling of developmental tempo across mammals. *Cell Stem Cell* 30(7):938–949.e7. doi:10.1016/j.stem.2023.05.014 🟡
64. Rayon T, Stamataki D, Perez-Carrasco R, et al. (2020). Species-specific pace of development is associated with differences in protein stability. *Science* 369:eaba7667. doi:10.1126/science.aba7667 🟡
65. Matsuda M, Hayashi H, Garcia-Ojalvo J, et al. (2020). Species-specific segmentation clock periods are due to differential biochemical reaction speeds. *Science* 369:1450–1455. doi:10.1126/science.aba7668 🟡 (note: published in *Science*, not *Nature*)
66. Swovick K, Firsanov D, Welle KA, et al. (2021). Interspecies differences in proteome turnover kinetics are correlated with life spans and energetic demands. *Mol Cell Proteomics* 20:100041. doi:10.1074/mcp.RA120.002301 ✅ (PMC7950207)
67. Lambert AJ, Boysen HM, Buckingham JA, et al. (2007). Low rates of hydrogen peroxide production by isolated heart mitochondria associate with long maximum lifespan in vertebrate homeotherms. *Aging Cell* 6(5):607–618. doi:10.1111/j.1474-9726.2007.00312.x 🟡
68. Pérez VI, Bokov A, Van Remmen H, et al. (2009). Is the oxidative stress theory of aging dead? *Biochim Biophys Acta* 1790(10):1005–1014. doi:10.1016/j.bbagen.2009.06.003 🟡 (title/metadata)
69. Sutter NB, Bustamante CD, Chase K, et al. (2007). A single IGF1 allele is a major determinant of small size in dogs. *Science* 316:112–115. doi:10.1126/science.1137045 🟡 (title/metadata)
70. Greer KA, Hughes LM, Masternak MM (2011). Connecting serum IGF-1, body size, and age in the domestic dog. *Age (Dordr)* 33(3):475–483. doi:10.1007/s11357-010-9182-4 🟡
71. Seim I, Fang X, Xiong Z, et al. (2013). Genome analysis reveals insights into physiology and longevity of the Brandt's bat *Myotis brandtii*. *Nat Commun* 4:2212. doi:10.1038/ncomms3212 🟡
72. Harrison DE, Strong R, Sharp ZD, et al. (2009). Rapamycin fed late in life extends lifespan in genetically heterogeneous mice. *Nature* 460:392–395. doi:10.1038/nature08221 🟡 (title/metadata)
73. Kealy RD, Lawler DF, Ballam JM, et al. (2002). Effects of diet restriction on life span and age-related changes in dogs. *J Am Vet Med Assoc* 220(9):1315–1320. doi:10.2460/javma.2002.220.1315 🟡
74. Day MJ (2010). Ageing, immunosenescence and inflammageing in the dog and cat. *J Comp Pathol* 142(Suppl 1):S60–S69. doi:10.1016/j.jcpa.2009.10.011 🟡 (title/metadata)
75. Raz N, Yang Y, Pridham G, et al. (2026). A damage accumulation model identifies distinct aging regimes across species. *Nat Aging* 6(6):1330–1340. doi:10.1038/s43587-026-01138-7 ✅ (PMC13278975 full text, incl. Extended Data Table 2)
76. Matrenok S, Andrianova EL, Avchaciov K, et al. (2026). Thermodynamic scaling of canine aging and reversible clock deceleration by a reverse transcriptase inhibitor. Preprint. doi:10.64898/2026.02.10.705136 🟡 (preprint abstract)
77. Hou C (2024). Energetic cost of biosynthesis is a missing link between growth and longevity in mammals. *PNAS* 121(20):e2315921121. doi:10.1073/pnas.2315921121 🟡
78. Patronek GJ, Waters DJ, Glickman LT (1997). Comparative longevity of pet dogs and humans: implications for gerontology research. *J Gerontol A* 52(3):B171–B178. doi:10.1093/gerona/52a.3.b171 🟡
79. Creevy KE, Grady J, Little SE, et al. (2019). 2019 AAHA Canine Life Stage Guidelines. *J Am Anim Hosp Assoc* 55(6):267–290. doi:10.5326/JAAHA-MS-6999 🟡
80. Yarborough S, Fitzpatrick A, Schwartz SM, Dog Aging Project Consortium (2022). Evaluation of cognitive function in the Dog Aging Project: associations with baseline canine characteristics. *Sci Rep* 12:13316. doi:10.1038/s41598-022-15837-9 🟡
81. Hoummady S, Besegher A, Jeannin S, et al. (2025). Comparison of the frailty phenotype and frailty index for identifying vulnerable companion dogs. *Sci Rep* 15:44608. doi:10.1038/s41598-025-28382-y 🟡
82. Zemko P, Bonsembiante F, Canevelli M, et al. (2026). OLD DOG – Validating the dog as an animal model for human aging studies. *J Frailty Aging* 15(3):100145. doi:10.1016/j.tjfa.2026.100145 🟡
83. Creevy KE, Akey JM, Kaeberlein M, Promislow DEL, Dog Aging Project Consortium (2022). An open science study of ageing in companion dogs. *Nature* 602:51–57. doi:10.1038/s41586-021-04282-9 🟡
84. Tian X, Azpurua J, Hine C, et al. (2013). High-molecular-mass hyaluronan mediates the cancer resistance of the naked mole rat. *Nature* 499:346–349. doi:10.1038/nature12234 🟡
85. Zhang Z, Tian X, Lu JY, et al. (2023). Increased hyaluronan by naked mole-rat Has2 improves healthspan in mice. *Nature* 621:196–205. doi:10.1038/s41586-023-06463-0 🟡
86. Podlutsky AJ, Khritankov AM, Ovodov ND, Austad SN (2005). A new field record for bat longevity. *J Gerontol A* 60(11):1366–1368. doi:10.1093/gerona/60.11.1366 🟡
87. Nielsen J, Hedeholm RB, Heinemeier J, et al. (2016). Eye lens radiocarbon reveals centuries of longevity in the Greenland shark (*Somniosus microcephalus*). *Science* 353:702–704. doi:10.1126/science.aaf1703 🟡
88. Kolora SRR, Owens GL, Vazquez JM, et al. (2021). Origins and evolution of extreme life span in Pacific Ocean rockfishes. *Science* 374:842–847. doi:10.1126/science.abg5332 🟡
89. Ma S, Upneja A, Galecki A, et al. (2016). Cell culture-based profiling across mammals reveals DNA repair and metabolism as determinants of species longevity. *eLife* 5:e19130. doi:10.7554/eLife.19130 🟡 (full text searched: no dog samples)
90. Prescott J, Keyser AJ, Litwin P, et al. (2025). Rationale and design of the Dog Aging Project precision cohort: a multi-omic resource for longitudinal research in geroscience. *GeroScience* 47(4):5725–5748. doi:10.1007/s11357-025-01571-3 🟡
91. Coleman AE, Creevy KE, Anderson R, et al. (2025). Test of Rapamycin in Aging Dogs (TRIAD): study design and rationale. *GeroScience* 47(3):2851–2877. doi:10.1007/s11357-024-01484-7 🟡
92. Guelfi G, Capaccia C, Tedeschi M, et al. (2024). Dog aging: a comprehensive review of molecular, cellular, and physiological processes. *Cells* 13(24):2101. doi:10.3390/cells13242101 🟡 (title/metadata)
93. López-Otín C, Blasco MA, Partridge L, Serrano M, Kroemer G (2023). Hallmarks of aging: an expanding universe. *Cell* 186(2):243–278. doi:10.1016/j.cell.2022.11.001 🟡 (background framework; title/metadata)

---

## Verification notes

*Independent fact-check by Fable 5.1, 2026-10-04. Full table in `../07_verification/why_dogs_age_fast_verification.md`.*

- **Scope.** All 18 author-flagged claims, every TL;DR bullet, the §1 numbers, the derived calculations, and 60+ citations were re-checked against primary sources (Europe PMC full text or abstracts, Crossref, AnAge, NPS) using ~85 web calls. Derived numbers (AnAge residuals, Gompertz refit of Teng's life table, Kleiber ratio, Wang conversion table, Cagan end-of-life burdens) were recomputed in Python.
- **Result.** 78 claims checked: 65 confirmed, 6 corrected, 4 downgraded, 0 removed, 3 unresolved. No fabricated or mis-attributed citation was found; every DOI tested resolved to the stated paper, and every journal/volume/page checked was correct (including the two 2026 papers, Raz et al. and Jang et al., and the openRxiv-prefixed Matrenok preprint).
- **Corrections made (each marked "[verifier-corrected]" in the text).** (1) Gurven & Kaplan's modal adult age at death is "about seven decades", not the recollected "about 72"; tag raised from ❓ to ✅. (2) TL;DR: Wang et al. profiled 104 dogs "primarily Labrador retrievers" (95 analysed), not "104 Labradors". (3) TL;DR: methylation-rate scaling is from refs 38 and 41, not 37. (4) Chimpanzee expected t_max filled in (25.1 y). (5) Bobi's claimed age is 31 y 163–165 d depending on source. (6) The 15/9/5 dog-year rule's AVMA attribution is upgraded from ❓ to 🟡 (the AKC explicitly attributes it to the AVMA; the AVMA page itself could not be opened).
- **Downgrades.** (a) Cagan et al.'s dog-specific values (249.46 SBS/yr, 15.26-y lifespan, 3 dogs/11 crypts, dog–wolf pooling) are in supplementary spreadsheets the verifier could not re-open; they are consistent with the main text (human 47.12 SBS/yr and 83.67-y lifespan confirmed in Table 1; dog is one of the 16 species; the implied burdens fall inside the published 1,828–5,379 range) but are now tagged 🟡. (b) The human-cohort description for Cagan's 83.7 y is 🟡 (main text says only "census record data"). (c) "Idaho wolf B2, 13.8 y" is on neither cited page → ❓. (d) Compton et al.'s mutation-rate–malignancy association holds only after controlling for gestation time; the conditional was added.
- **Nuances added.** Horvath et al. 2022 found no breed-level association for epigenetic *age acceleration*, but their DNAmAverageTimeToDeath biomarker did associate with breed lifespan and weight. AnAge's 40-kg dog mass is a large-breed value; with 15–20 kg the dog residual would be 122–127%, so "dogs sit near the mammalian line" is robust but the 109% figure is mass-dependent. The AnAge formula's mass unit is not stated on the help page; grams is confirmed only because it reproduces AnAge's residuals.
- **Confirmed derived numbers.** MRDT refit on Teng Table 2: 1.95–2.0 y (ln hazard, R² ≥ 0.999) or 2.05–2.2 y (ln q); human 8 y per AnAge. Raz et al. 2026 Extended Data Table 2 gives exactly the β and η values quoted (β 0.044 vs 0.048 X_c/day; η 3.72e-6 vs 1.09e-6 X_c/day²); note the main text uses a differently normalised parameter set (β 0.63 vs 0.66; η 9.3e-5 vs 1.59e-5), so cite the table when quoting.
- **Still open.** UN global life expectancy 73.3 y (2024) — primary PDF not opened; AAHA "senior = last 25% of expected lifespan" — not in the abstract; AVMA primary page for the 15/9/5 rule.
