# Breed size, genetics and lifespan: why large dogs die young (the within-species story)
> Part of the dog-ageing research dossier · Written 2026-10-04 by Fable 5.1 subagent · Status: independently verified by Opus 5.5 on 2026-10-04 — see ../07_verification/breed_wolves_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Tags used below: ✅ = confirmed in a primary source I opened (full text or the paper's own abstract); 🟡 = abstract/secondary source only, or a number taken from press coverage of a paper; ❓ = unconfirmed, contested, or my own inference.

## TL;DR

- Across mammals, bigger species live longer; **within dogs the pattern reverses**: every large population study (UK VetCompass, UK Dogs Trust/registry compilation, US Banfield, US VMDB) finds that heavier breeds die younger [3][5][6]. ✅ The size of the gap depends on how size classes are cut: ~4.0 y between small (13.53 y) and giant (9.51 y) purebreds in Banfield life tables [6], but only 0.8 y between small (12.7 y) and large (11.9 y) breeds in McMillan's three-class UK analysis, which has no giant class [5]; Teng et al. [4] report breeds, not size classes. [verifier-corrected: original "2–4 years between small and giant classes [4][5][6]" over-generalised]
- Kraus, Pavard & Promislow (2013; 74 breeds, VMDB) decomposed mortality curves and concluded large dogs die young **mainly because they age faster** (steeper rise in mortality hazard), not because they start ageing earlier or have much higher baseline mortality [1]. ✅ Press coverage of the paper quotes ~1 month of life expectancy lost per 2 kg of breed mass [48]. 🟡 The same figure appears in an academic commentary (Selman, Nussey & Monaghan 2013, *Curr Biol* dispatch [49]); the verifier could not access the Kraus full text to confirm it there. [verifier-corrected]
- The effect is a **breed-level** phenomenon: within a breed, bigger individuals are not shorter-lived (Galis et al. 2007 found a slightly positive within-breed relationship) [11]. ✅ This points to the genetic architecture of breed size (and selection for fast growth), not body mass per se.
- Breed body size is unusually oligogenic: a handful of loci in the **GH/IGF-1 axis and growth regulators** (IGF1, IGF1R, GHR, HMGA2, SMAD2, STC2, LCORL, IGSF1 ...) explain roughly half of breed-weight variance with 7 markers [15] and ~90–95% with ~14–20 markers at the breed level [16]. ✅
- The single most important small-size variant is a non-coding SNP in an **IGF1 antisense lncRNA (IGF1-AS)**; the "small" allele is ancestral, was present (heterozygous) in a ~53,000-year-old Pleistocene Siberian wolf [verifier-corrected: the paper says 53,000, not 54,000], is rare in modern wolves and large breeds, and resurged under human selection for small dogs [17]. ✅ Serum IGF-1 scales with body size: standard poodles have ~6× the IGF-1 of toy poodles with equivalent GH secretory capacity (r = 0.88) [18]. ✅
- Mechanistic evidence for *how* large breeds age faster is suggestive but incomplete: fibroblasts from large breeds are more glycolytic [23][24], blood telomere length predicts breed lifespan [31], cancer mortality rises with breed size as predicted by a multistage carcinogenesis model with no compensatory tumour suppression [28], and osteosarcoma odds are ~45× higher in dogs >40 kg than <10 kg [29]. ✅ Cellular stress-resistance does **not** differ by breed size [25]. ✅
- Epigenetic evidence is mixed: a 2024 Dog Aging Project RRBS clock (n = 864) finds the largest size class accrues ~0.37 extra epigenetic years per chronological year and that residual epigenetic age predicts mortality (HR 1.34/yr, 95% CI 1.06–1.69, based on only 49 deaths) [34] 🟡 (bioRxiv preprint, still not peer-reviewed as of 2026-10-04) [verifier-corrected]; but Horvath et al. 2022 (742 samples, 93 breeds, array-based) found **no significant** association between epigenetic age acceleration and breed weight or lifespan [33]. ✅ A widely repeated "giant breeds drift 40% faster" claim is misattributed (see §5.5). ❓
- Other modifiers with good evidence: brachycephaly (−1.6 y median vs mesocephalic) [5]; neutering/sterilisation (+13.8% male, +26.3% female lifespan in VMDB; +0.9 y (male) to +1.5 y (female) in UK life tables [verifier-corrected from "+1–1.5 y"], with confounding) [38][4]; obesity (−1.5 y life expectancy at BCS 5 vs 3) [6]; lifelong 25% caloric restriction (+1.8 y median in Labradors, RCT) [39]; inbreeding (morbidity rises with F; lifespan effect present but smaller than size) [37][9][10]. ✅
- GWAS of canine lifespan itself remain weak and underpowered: breed-level GWAS (n = 149 breeds) nominate IGSF1/ARHGAP36 [42]; a 41-dog Cavalier study nominates 9 genes [43]; the Dog Aging Project's 2026 preprint (7,627 genotyped dogs) is a GWAS of blood traits, not of lifespan, and finds GH/IGF-1 metabolites have *lower* mortality hazards than several other markers [44]. ✅
- Translational lever: the within-dog size–lifespan trade-off is the rationale for Loyal's LOY-001, an injectable that lowers IGF-1 in large dogs; FDA CVM accepted its "reasonable expectation of effectiveness" package in Nov 2023 [45] (details in ../05_interventions/). ✅

---

## 1. The phenomenon: lifespan by size and breed

### 1.1 Population studies (observational, retrospective; all correlational)

| Study | Design / n | Key size-related finding |
|---|---|---|
| Greer, Canterberry & Murphy 2007 [2] | 77 AKC breeds, >700 dogs, owner/breeder data | Weight vs longevity r = −0.679; height r = −0.603; weight the significant predictor (p<0.001). ✅ (abstract) |
| Fleming, Creevy & Promislow 2011 [27] | 74,556 deaths, VMDB (27 N. American teaching hospitals), 1984–2004 | Causes of death segregate by breed-standard mass: larger breeds more musculoskeletal and GI deaths; smaller breeds more endocrine; older dogs more neurologic and neoplastic deaths. ✅ (abstract) The claims that larger breeds had more *neoplastic* deaths and that neoplasia peaked at ~10 y are not in the abstract, and the verifier could not confirm them in the full text. 🟡 [verifier-corrected] |
| Kraus, Pavard & Promislow 2013 [1] | 74 breeds, VMDB (>50,000 dogs) | Parametric hazard models: strong positive association of body size with **ageing rate**; no strong link to onset of senescence; only marginally elevated baseline mortality in large breeds. "Large dogs die young mainly because they age quickly." ✅ (abstract) |
| O'Neill et al. 2013 [3] | VetCompass UK, 102,609 dogs, 86 practices, 5,095 deaths | Median longevity 12.0 y (IQR 8.9–14.2); crossbreds outlive purebreds by 1.2 y (95% CI 0.9–1.4); bodyweight negatively correlated with longevity. Longest: Miniature Poodle, Bearded Collie, Border Collie, Miniature Dachshund; shortest: Dogue de Bordeaux, Great Dane. ✅ (abstract) |
| Urfer et al. 2020 [7] | 20,970 dogs, 3 US primary-care clinics | Larger size → shorter survival; neutering → longer survival (stronger in females); "Mountain" ancestral clade breeds 3.5–4.6 y shorter median survival. ✅ (abstract) |
| Teng et al. 2022 [4] | VetCompass UK life tables, 30,563 deaths 2016–2020 | Life expectancy at age 0: 11.23 y (95% CI 11.19–11.27). Breed range: Jack Russell Terrier 12.72 y to French Bulldog 4.53 y. ✅ |
| Montoya et al. 2023 [6] | Banfield (USA), 1,152 hospitals, 13.3 M dogs; records Jan 2013–Jul 2022, with life tables built for survey years 2013–2019 [verifier-corrected] | Life expectancy at birth 12.69 y overall; purebred size groups: toy 13.36, small 13.53, medium 12.70, large 11.51, **giant 9.51** y. ✅ |
| McMillan et al. 2024 [5] | UK, 18 data sources, 584,734 dogs (284,734 deceased), 155 breeds | Median 12.5 y overall; small 12.7 / medium 12.5 / large 11.9 y; brachycephalic 11.2 vs mesocephalic 12.8 vs dolichocephalic 12.1 y; female 12.7 vs male 12.4 y; purebred 12.7 vs crossbred 12.0 y (note: opposite direction to [3] and [9] — see §6.3). ✅ |
| Nam et al. 2024 (Dog Aging Project) [8] | 27,541 owner-reported dogs, cross-sectional | Larger size → higher lifetime prevalence of skin, orthopaedic, GI, ENT, cancer, neurologic, endocrine and infectious disease; smaller size → more ocular, cardiac, hepatic, respiratory disease; age × size interactions for several categories. ✅ |

Caveats: veterinary-hospital databases (VMDB) over-represent referral cases and sick dogs; primary-care and insurance data have their own selection biases; registry/owner-reported data may be imprecise on cause of death. Breed-level medians can rest on small n for rare breeds (e.g., Caucasian Shepherd Dog in [5]).

### 1.2 Example breeds (median lifespan or life expectancy at birth)

| Breed (approx. adult mass) | Estimate | Source |
|---|---|---|
| Lancashire Heeler (~6 kg) | 15.4 y median | McMillan 2024 [5] ✅ |
| Tibetan Spaniel (~5 kg) | 15.2 y median | [5] ✅ |
| Shiba Inu (~9 kg) | 14.6 y median | [5] ✅ |
| Toy Poodle (2.3 kg, per [33]) | 14.6 y median (breed table) | Horvath 2022 [33] ✅ |
| Jack Russell Terrier (~7 kg) | 12.72 y LE at birth | Teng 2022 [4] ✅ |
| Yorkshire Terrier (~3 kg) | 12.54 y | [4] ✅ |
| Border Collie (~18 kg) | 12.10 y | [4] ✅ |
| Labrador Retriever (~30 kg) | 11.77 y | [4] ✅ |
| Staffordshire Bull Terrier (~15 kg) | 11.33 y | [4] ✅ |
| French Bulldog (~11 kg, brachycephalic) | 4.53 y (Teng, LE at birth; young, rapidly growing population); 9.8 y (McMillan, median) | [4][5] ✅ |
| English Bulldog | 7.39 y LE at birth | [4] ✅ |
| Mastiff (~70 kg) | 9.0 y median | [5] ✅ |
| Cane Corso (~45 kg) | 8.1 y median | [5] ✅ |
| Presa Canario (~50 kg) | 7.7 y median | [5] ✅ |
| Great Dane (64 kg, per [33]) | 6.3 y median (breed table) | [33] ✅ |
| Caucasian Shepherd Dog (~50–90 kg) | 5.4 y median (small n likely) | [5] ✅ |

Note the French Bulldog discrepancy (4.53 vs 9.8 y) illustrates how metric (life expectancy from a life table vs median age at death among the deceased), population age structure and data source change breed estimates; Teng et al. explicitly caution that rapidly growing young breed populations depress life-table estimates [4].

### 1.3 "Age faster" vs "start ageing earlier": the debate

- **Mortality demography**: Kraus et al. 2013 found the dominant driver is ageing *rate* (slope of the Gompertz hazard), with little effect on onset of senescence and only marginal baseline mortality effects [1]. ✅
- **Behaviour/cognition**: Turcsán & Kubinyi (GeroScience 2024; >15,000 owner surveys) report the *opposite* pattern for behavioural ageing: dogs >30 kg show onset of behavioural decline 2–3 years earlier but *slower* rates of decline than small dogs; small, dolichocephalic and purebred dogs had higher canine cognitive dysfunction risk [46]. ✅ (abstract)
- **Epigenetics**: the Dog Aging Project RRBS clock finds a larger per-year accrual of epigenetic age in the largest size class [34] ✅, supporting "faster", but Horvath et al. 2022 found no association of age acceleration with breed weight [33] ✅ (see §5.5).
- **Development/growth**: Galis et al. 2007 argue artificial selection for extremely high growth rates in large breeds produced developmental diseases that curtail lifespan [11] ✅; Jimenez's review notes small dogs have "faster and shorter developmental trajectories" and higher mass-specific metabolic rates yet live longer [22]. ✅
- Synthesis (my inference ❓): "faster ageing" is well supported for all-cause mortality and plausibly for epigenetic drift; disease-specific trajectories differ (cancer and orthopaedic disease load early in large breeds; cognitive decline later), so the demographic and functional answers need not coincide.

---

## 2. Genetics of body size and its links to longevity

### 2.1 The IGF1 locus
- **Sutter et al. 2007 (Science)**: genome-wide scan in Portuguese Water Dogs identified a major size QTL on CFA15; a 15-Mb interval showed a selective sweep spanning *IGF1*; a single IGF1 SNP haplotype "is common to all small breeds and nearly absent from giant breeds" [12]. ✅ (abstract) Press/secondary summaries give ~15% of skeletal size variance explained in PWDs. 🟡
- **Gray et al. 2010 (BMC Biol)**: the small-dog IGF1 SNP allele and an associated SINE insertion are absent from grey wolves; Middle Eastern wolf haplotypes are most closely related, suggesting the small-size mutation post-dates domestication and arose in the Middle East [13]. ✅ (abstract)
- **Plassais et al. 2022 (Current Biology)**: analysed 1,431 genomes from 13 canid species, ancient and modern, and identified a single variant in the antisense lncRNA *IGF1-AS* (which forms a duplex with IGF1 mRNA). The derived allele predominates in modern grey wolves and large breeds; the **ancestral allele predisposes to small size** and is common in small breeds and smaller wild canids. The variant "nearly vanished in Pleistocene wolves" before resurging under human selection for small dogs [17]. ✅ (abstract) The paper's full text (PMC8891063) confirms that the ancestral small allele is C and the derived large allele is T at rs22397284; that it was present (heterozygous) in a 53,000-year-old Pleistocene Siberian wolf; and that 75% (third quartile) of dogs homozygous for C have breed mean body mass <15 kg [17]. ✅ [verifier-corrected: previously 🟡 from press; the age is 53,000 years, not 53,000–54,000] This supersedes Gray et al.'s inference that the small allele post-dates domestication (the causal SNP is old; the dog-specific SINE haplotype may be younger). ❓

### 2.2 Other GH/IGF-axis and growth loci
- **Hoopes et al. 2012 (Mamm Genome)**: fine-mapping identified a nonsynonymous *IGF1R* SNP (chr3:44,706,389; **R204H**) contributing to reduced size [14]. ✅ (abstract/secondary)
- **Rimbault et al. 2013 (Genome Res)**: fine-mapped *GHR, HMGA2, SMAD2, STC2*; genotyped 500 dogs/93 breeds + 30 wild canids; derived alleles at all markers reduce size; **7 markers explain 46–52.5% of breed body-size variance, 64.3% among breeds <41 kg** [15]. ✅ (abstract)
- **Plassais et al. 2019 (Nat Commun)**: 722 canid WGS (144 breeds, 54 wild canids, ~100 village dogs; >91 M variants). Body-weight genes/loci: *IGF1R, LCORL, STC2, GHR (two variants), SMAD2, HMGA2, ZNF608, IGF1, R3HDM1, ADAMTS9-AS, HNF4G, ACSL4, IGSF1*; new loci *ADAMTSL3, ZNF608, HNF4G*; combined with earlier data these "account for as much as 95% of SBW [standard breed weight] variation in purebred dogs" [16]. ✅ (full text via PMC) Note this is **breed-level** variance explained, not individual-level heritability.
- **Horvath et al. 2022 EWAS**: the top genome-wide CpGs were in *SF1* (breed lifespan; 16 significant CpGs) and *TTC8* (breed weight, 67 CpGs; breed height, 10 CpGs). In a separate look-up of 47 array probes near size-GWAS genes, only four CpGs downstream of **SMAD2** and one in exon 2 of **IGF1R** correlated positively with breed weight and negatively with breed lifespan; the authors call this "modest" epigenetic regulation. The breed-weight EWAS overlapped human GWAS loci for leukocyte telomere length (P = 1.2 × 10⁻⁶) [33]. ✅ [verifier-corrected: SMAD2/IGF1R CpGs came from a candidate-gene look-up, not from the top EWAS hits]
- Several of these loci (*IGF1, IGF1R, GHR, SMAD2*) sit directly on the GH/IGF-1/TGF-β growth axis, which is the best-replicated lifespan-modulating pathway in laboratory animals (see §2.4).

### 2.3 Circulating IGF-1 and breed size
- **Eigenmann, Patterson & Froesch 1984**: in poodles of three size varieties, standard poodles had ~6× the plasma IGF-I of toy poodles; IGF-I correlated with body weight (r = 0.88, P<0.001) while GH response to clonidine was similar across sizes — i.e., size tracks IGF-I rather than GH secretory capacity [18]. ✅ (abstract)
- **Greer, Hughes & Masternak 2011**: serum IGF-1 in purebred and mixed dogs (age months to 204 months; 5–160 lb): IGF-1 rises with body weight, declines with age in all groups (sex differences), and the weight relationship depends on neuter status [19]. ✅ (abstract)
- **Dog Aging Project 2026 preprint** (976 dogs, 159 blood analytes/metabolites; 957 with 3-y mortality follow-up): markers in the GH/IGF-1 pathway "had lower absolute mortality hazard ratios" than other metabolites; the strongest risk markers were globulin, potassium, suberic acid, dimethylglycine, ethylmalonic acid, succinate; protective: ethanolamine, deoxycarnitine, guanidinoacetate, hydroxyproline. The authors conclude ageing is "multifactorial" rather than dominated by size-related pathways alone [44]. ✅ (preprint full text) Important nuance against an IGF-1-only model. ❓ (preprint; not peer-reviewed)

### 2.4 Cross-species parallels (causal evidence from other species)
- **Laron syndrome (human GHR deficiency)**: Guevara-Aguirre et al. 2011 followed Ecuadorian GHR-deficient individuals for 22 years: one non-lethal malignancy and no diabetes vs 17% cancer and 5% diabetes in relatives; serum reduced DNA breaks and lowered RAS/PKA/mTOR expression in cultured cells [20]. ✅ (abstract) Protection from cancer/diabetes is clear; lifespan extension in Laron patients is not established. ❓
- **GH-deficient dwarf mice**: Ames (Prop1 df/df) and Snell dwarfs and GHR-knockout mice are the canonical long-lived mammals; secondary sources summarise roughly 50–65% lifespan extension for Ames dwarfs in Brown-Borg et al. 1996, with sex-specific figures of ~49% and ~64–68% that differ between secondary sources [21]. 🟡 [verifier-corrected from "~40–50%", which understates the commonly cited values] (The primary 1996 Nature letter is not open access and was not read.)
- Logic: dogs are the only species in which humans have *already* run a GH/IGF-1 titration experiment at population scale, with ~40-fold mass range [17] and ~2-fold lifespan range [33]. The small-breed/low-IGF-1/long-life correlation is consistent with the mouse and human genetics, but in dogs it is still correlational and confounded by everything else that differs between breeds.

### 2.5 GWAS of canine lifespan itself (all preliminary)
- **Ko et al. 2025 (Mol Cells)** [42]: breed-level phenotype matrix (20 traits, 149 breeds, AKC-derived), GWAS with adjusted phenotypes; lifespan hits *IGSF1* and *ARHGAP36* (X chromosome); size/BMI hits *MSRB3, HMGA2, IGF1, IGSF1*; also an unexpected "drooling–lifespan" association. ✅ (abstract) Breed-level n = 149 with heavy size confounding; treat as hypothesis-generating. ❓
- **Korec et al. 2024 (Vet Anim Sci)** [43]: 24 long-lived (>13 y) vs 17 reference Cavalier King Charles Spaniels; 15 SNPs in 9 genes (*B3GALNT1, NLRP1-like, PARP14, IQCJ-SCHIP1, COL9A1, COL19A1, SDHAF4, B3GAT2, DIRC2*). ✅ (PMC) Tiny n; unreplicated. ❓
- **Sohrab et al. 2026 bioRxiv (Dog Aging Project)** [44]: 7,627 genotyped dogs; 298 genome-wide significant loci for **blood traits** (median SNP heritability 0.39 vs 0.15 for survey traits). Of 181 distinct dog loci, 27% overlap a human association for the same or a directly related trait; this rises to 79% for the 14 strongest signals [verifier-corrected: denominator clarified]. Not a lifespan GWAS; lifespan links are via breed-lifespan correlations and 3-year mortality. ✅
- Horvath et al. 2022's EWAS of breed lifespan [33] is the closest thing to a molecular "lifespan scan" with decent power (742 samples, 93 breeds). Its top hits were *SF1* (lifespan) and *TTC8* (weight); only a handful of candidate-gene CpGs near *SMAD2/IGF1R* tracked weight and lifespan, which the authors call "modest" [33]. ✅ [verifier-corrected: original said the EWAS "points back to IGF1R/SMAD2"]
- Plassais et al. 2017 (PLoS Genet) reported X-chromosome loci (incl. *IGSF1*) for weight/muscling in large vs small dogs (cited in [36]). 🟡 The title was verified ("Analysis of large versus small dogs reveals three genes on the canine X chromosome associated with body weight, muscling and back fat thickness", PMC5357063), but the content was not read. [verifier note]

---

## 3. Proposed mechanisms for why large breeds age faster

| Mechanism | Evidence | Status |
|---|---|---|
| **Growth rate / developmental disease** | Galis et al. 2007: within-breed size–lifespan relation not negative; across breeds negative → "artificial selection for extremely high growth rates in large breeds appears to have led to developmental diseases" [11]. Large breeds dominate orthopaedic disease prevalence [8]. | ✅ correlational |
| **GH/IGF-1 signalling** | IGF-1 scales with size [18][19]; small-size alleles at *IGF1/IGF1R/GHR/SMAD2* [12][14][15][16][17]; a few candidate-gene CpGs at *IGF1R/SMAD2* (5 of 47 probes) track weight and lifespan, which the authors describe as "modest" [33] [verifier-corrected]; Laron/dwarf-mouse causal parallels [20][21]; but DAP biomarker study finds IGF-axis metabolites weaker mortality predictors than others [44]. | ✅ correlational in dogs; causal in mice/humans for some outcomes |
| **Cellular metabolism / oxidative stress (Jimenez lab)** | Primary dermal fibroblasts from small (≤15 kg) and large (≥20 kg) breeds, puppies and old dogs. The breakdown "32 breeds; 11 small / 21 large puppies; 15 small / 22 large seniors" could not be confirmed; sample sizes vary by assay (e.g., 8-OHdG: 27 small puppy / 16 small old / 52 large puppy / 25 large old) [verifier-corrected]. All aspects of glycolysis higher in large breeds; proton leak higher in older dogs regardless of size; no size difference in reactive-species production; authors propose higher glycolysis and DNA damage in large breeds [23]. Metabolomics: old dogs of both sizes have lower glutathione and ATP; large old dogs show an apparent pyruvate-kinase-level glycolytic defect, increased glutamine anaplerosis, possible CoA-biosynthesis defect [24]. Stress resistance (heat, paraquat, cadmium, H₂O₂; n = 18/32/11/23) did **not** differ by size or age [25]. In blood, small breeds have *higher* circulating lipid damage than large breeds, opposite to their lifespan advantage [26]. | ✅ in vitro/ex vivo; mixed |
| **Telomeres** | Fick et al. 2012: PBMC telomere length strongly predicts breed average lifespan across 15 breeds (p<0.0001); dogs lose telomeric DNA ~10× faster than humans; shorter-telomere breeds have more cardiovascular deaths [31]. | ✅ (abstract) correlational, 15 breeds |
| **Cancer / multistage carcinogenesis** | Nunney 2024 (85 breeds, 3 datasets): breed weight and lifespan fit a multistage model with ~4 driver mutations; larger breeds' lower mass-specific metabolic rate does not reduce cancer; no evidence of compensatory tumour suppression (i.e., no within-species Peto's paradox; this is an interpretation of the model fit — the abstract says increased risk follows "unless selection promotes increased cancer suppression"). Of 85 breeds, only the flat-coated retriever had *significantly* elevated cancer mortality; Scottish terrier, Bernese mountain dog and bullmastiff showed "notable" risk (>50% over expected) [28] [verifier-corrected: significance nuance added]. Osteosarcoma: dogs >40 kg have OR 45.44 vs <10 kg [29]; Scottish Deerhound OR 118.4, Leonberger 55.8, Great Dane 34.2, Rottweiler 26.7 in 905,552 VetCompass dogs; chondrodystrophic breeds protected (OR 0.10) [30]. Large breeds have higher lifetime cancer prevalence [8]; neoplasia is the leading adult cause of death in VMDB [27]. Large dogs show higher proportional cancer mortality after bias correction [10]. | ✅ correlational |
| **Epigenetic ageing** | Thompson 2017: age-acceleration vs breed weight r = 0.25, n.s., n = 46 [32]. Horvath 2022: no significant EAA association with breed weight/lifespan [33]. McCoy 2024 (DAP, n = 864, RRBS): largest size class +0.37 epigenetic years per chronological year vs smallest; residual epigenetic age HR 1.34 per year (95% CI 1.06–1.69) for death, based on 49 deaths; preprint, not peer-reviewed [34] [verifier-corrected]. Jang 2026 (PNAS 123(29)): extent of age-associated methylation drift varies by body size; Korean dogs show higher EAA than US dogs [35]. | ✅ mixed; see §5.5 |
| **Inbreeding / deleterious alleles** | See §6.1. Contributes to morbidity, but size dominates lifespan variance [9][37]. | ✅ |

---

## 4. Other genetic and demographic modifiers

### 4.1 Inbreeding and genetic diversity
- **Bannasch et al. 2021** (227 breeds; F estimated from median heterozygosity from commercial DNA testing of 49,378 dogs, adjusted against a smaller dataset genotyped on the Illumina canine HD 173K array [verifier-corrected: original implied the 227-breed estimates were themselves from the 173K array]): mean genotype-based F = 0.249 (95% CI 0.235–0.263) — i.e., the average purebred is as inbred as a full-sib mating; relative risk of insured veterinary-care events vs mixed breeds: 1.01 (F<0.125), 1.22 (F 0.126–0.25), 1.29 (F>0.25); body weight and F together explain morbidity with r² = 0.77; lowest-F breeds are landraces or recently outcrossed [37]. ✅
- **Yordy et al. 2019/2020** (4,586 dogs, 117 breeds; VMDB e(2) life expectancy): body size and purebred status explain 95% of breed-mean life-expectancy variance (purebred status alone 46%); once size is in the model, breed F adds nothing; mixed breeds live ~1.2 y longer than size-matched purebreds; "recent inbreeding ... is more likely to affect fitness than historic inbreeding" [9]. ✅
- **Kraus, Snyder-Mackler & Promislow 2023** (>40,000 dogs, 118 breeds): after correcting bias in breed lifespan estimates, old-age lifespan increases with genetic diversity and decreases with size; large breeds have higher proportional cancer mortality; authors recommend outcross programmes [10]. ✅ (abstract)
- **Nunney 2024**: elevated inbreeding shortens lifespan but has no overall effect on cancer mortality [28]. ✅ (abstract)
- Dog10K: wolves carry on average ~14% more *structural variants* (insertions/deletions >50 bp, relative to the GSD reference) per genome than breed dogs [verifier-corrected: the 14% refers to structural variants, not all variants]. This is one indicator of the diversity lost in breed formation [see ../04_dog_aging_biology/wolves_vs_dogs.md].

### 4.2 Head shape / brachycephaly
- McMillan 2024: brachycephalic median 11.2 y vs mesocephalic 12.8 y vs dolichocephalic 12.1 y [5]. ✅ Teng 2022: French Bulldog 4.53 y and English Bulldog 7.39 y life expectancy at birth [4]. ✅ Cause pathways (BOAS, heat intolerance, spinal, ocular) are reviewed in [36]. 🟡

### 4.3 Purebred vs crossbred
- Crossbreds +1.2 y (VetCompass 2013) [3] and mixed breeds +1.2 y vs size-matched purebreds (VMDB) [9] ✅, but McMillan 2024 found purebred median (12.7 y) *above* crossbred (12.0 y) [5] ✅, and Urfer et al. 2020 (US primary care, n = 20,970) found no significant purebred vs mixed-breed difference [7] ✅ [verifier-added] — a discrepancy likely reflecting the changing composition of UK "crossbreds" (designer crosses, brachycephalic crosses) and data-source mix; unresolved. ❓

### 4.4 Sex and sterilisation
- Hoffman, Creevy & Promislow 2013 (VMDB; 70,574 dogs, 40,139 in cause-of-death analysis): sterilisation associated with +13.8% lifespan in males and +26.3% in females; sterilised dogs less likely to die of infectious disease, trauma, vascular and degenerative disease, more likely to die of neoplasia and immune-mediated disease [38]. ✅
- Teng 2022 life expectancy at birth: neutered female 11.98 y vs entire female 10.50; neutered male 11.49 vs entire male 10.58; female 11.41 vs male 11.07 [4]. ✅ Montoya 2023: female 12.76 vs male 12.63 [6]; McMillan: 12.7 vs 12.4 [5]. ✅
- Caveat: neuter status is confounded (dogs must survive long enough to be neutered; owner-care correlates), so the "neutering adds years" effect is likely overstated; the cause-of-death shift (more cancer in neutered dogs) is the more robust signal [38]. ❓

### 4.5 Body condition and caloric restriction
- **Kealy et al. 2002 (JAVMA)** — the one lifespan RCT in dogs: 48 Labrador Retrievers pair-fed from 8 weeks, one of each pair fed 25% less for life; restricted dogs weighed less, had lower body fat, triglycerides, T3, insulin and glucose; median lifespan significantly increased and onset of chronic disease delayed [39]. ✅ (abstract) Primary text: median lifespan was 11.2 y in control-fed vs 13.0 y in restricted dogs (P < 0.01; +1.8 y). "Maximum" lifespan (age at which 90% had died) was 12.9 vs 14.0 y, not significantly different. ✅ [verifier-corrected: upgraded from 🟡 after reading the primary results section] The study was run by Nestlé Purina. Interventions are covered in ../05_interventions/.
- Montoya 2023: obese dogs (BCS 5) life expectancy 11.71 y vs ideal (BCS 3) 13.18 y [6]. ✅ correlational.

### 4.6 Breed-specific inherited diseases that truncate lifespan (examples)
- **Dilated cardiomyopathy, Dobermann**: Wess et al. 2010 (412 European Dobermanns, echo + Holter): prevalence 3.3% at 1–2 y rising to 43.6% at 6–8 y and 44.1% >8 y; cumulative prevalence 58.2%; autosomal dominant inheritance [40]. ✅ (abstract)
- **Myxomatous mitral valve disease, Cavalier King Charles Spaniel**: secondary sources state ~50% affected by 5 y and ~90–100% by 10 y [47]. 🟡 (not verified in a primary paper this pass)
- **Degenerative myelopathy (SOD1 E40K)**: Awano et al. 2009 GWAS in 38 Pembroke Welsh Corgis → *SOD1* E40K; homozygosity associated with DM in 5 breeds; onset ≥8 y; first spontaneous animal model of ALS [41]. ✅ (abstract)
- **Osteosarcoma** in giant/large breeds [29][30]; **cancer-prone breeds** (flat-coated retriever, Bernese, Scottish terrier, bullmastiff) [28]. ✅
- These Mendelian/oligogenic diseases show that a large part of "breed lifespan" is breed-specific disease burden layered on top of the size effect; they are also the most tractable targets for genetic testing, selection or editing.

---

## 5. Points of tension and verification notes

### 5.1 Breed-level vs individual-level
Almost all size–lifespan effects are estimated across breeds. Within a breed, heavier dogs are not shorter-lived (Galis 2007 [11]) — though within-breed weight is confounded by obesity and sex. The relevant variable is therefore likely *breed-standard* size (and the alleles that produce it), not an individual's mass.

### 5.2 Metric confusion
Median age at death among the deceased (McMillan, O'Neill) ≠ life expectancy at birth from a life table (Teng, Montoya) ≠ e(2) adult life expectancy from Gompertz fits (Yordy, Kraus). Numbers are not interchangeable across tables above.

### 5.3 Variance-explained figures
"95% of body-size variance explained by ~15–20 genes" [16] refers to among-breed variance in standard breed weight, a trait with extreme between-breed differentiation; individual-level heritability estimates would be much lower. ❓ (interpretive)

### 5.4 Serum IGF-1 as *the* mediator
The Dog Aging Project biomarker preprint [44] weakens the case that IGF-1 is the single dominant mediator of mortality in pet dogs. Loyal's framing of large-breed short lifespan as an "accelerated aging disorder" driven by IGF-1 [45] is a hypothesis under test, not an established mechanism. ❓

### 5.5 The "giant breeds drift 40% faster than toy breeds" claim
The 2025 review by Ko & Shin states "Giant breeds such as Great Danes accumulate epigenetic drift up to 40% faster than toy breeds like Toy Poodles" and cites Horvath et al. 2022 for it [36]. In the Horvath paper itself, the test of epigenetic age acceleration against breed median lifespan, maximum lifespan, weight and height returned "no significant results" [33]. ✅ I could not locate a "40%" figure in the Horvath text I accessed. The closest supported statistic is McCoy et al.'s 0.37 extra epigenetic years per chronological year for the largest vs smallest size class [34], from a different cohort and platform. Treat the 40% figure as **unverified** ❓ and do not propagate it. **Verifier confirmation:** Ko & Shin (PMC12520860) do make this statement and cite Horvath et al. 2022 (their ref. 60). The Horvath full text (PMC9173771) contains no "40%" figure and reports that epigenetic age acceleration showed "no significant results" against breed lifespan, maximum lifespan, weight or height. The misattribution is CONFIRMED. ✅ [verifier-corrected]

---

## 6. What the within-species size effect teaches about the levers of ageing

1. **A few growth loci move lifespan by years.** Breed size is controlled by ~15–20 loci, mostly in the GH/IGF-1/TGF-β growth axis [15][16], and breed size is the strongest single predictor of breed lifespan [1][2][9]. This is the most compelling naturally occurring, polygenic-but-tractable "ageing-rate" perturbation in any mammal. The IGF1-AS variant is a *non-coding regulatory* allele that is ancestral, viable in the wild, and already segregating in wolves [17] — a plausible first target for allele-replacement experiments in large-breed cells or embryos (feasibility of canid germline editing: see wolves_vs_dogs.md §7).
2. **Growth trajectory, not adult mass, may be the real variable.** The within-breed null [11] and the "developmental disease" burden of giant breeds [8][11] suggest the lever is how fast and how far a puppy grows. Experiments that decouple adult size from growth rate (e.g., slowed growth via diet or IGF-1 modulation only during development) would test this. ❓
3. **Cancer scales with size without compensation.** Nunney's result that dog breeds show no Peto-type tumour-suppression scaling [28] implies large breeds are "under-protected" relative to their cell number — an argument for interventions that add tumour-suppressive capacity (or reduce IGF-1-driven proliferation) specifically in large breeds. ❓ (inference)
4. **Epigenetic clocks are a usable readout.** The DAP clock predicts mortality (HR 1.34/yr; 49 deaths; unreviewed preprint) [34] [verifier-corrected]; dual-species dog–human clocks (R = 0.97) exist [33]. These make 1–2-year intervention trials feasible without waiting for death outcomes.
5. **Pharmacological proof-of-concept is already in regulatory review.** LOY-001 (IGF-1-lowering, 3–6-monthly injectable for large/giant dogs) obtained FDA CVM agreement on "reasonable expectation of effectiveness" on 28 Nov 2023 [45]; if conditional approval and the pivotal trial succeed, it would be the first causal test in dogs of the size/IGF-1 hypothesis. See ../05_interventions/.
6. **Natural controls exist.** Wolves mostly carry the "large" IGF1-AS allele [17] and can live to ~20 years in captivity (one AnAge record of a wild-born male, ~20.6 y; see wolves_vs_dogs.md) [verifier-corrected: original "reach ≥20 years" generalised from a single record], suggesting large size per se is compatible with long canid life, and that breed-specific growth selection, inbreeding and disease alleles do the damage. ❓ (inference; needs a size-matched wolf–dog comparison)

---

## Open questions / gaps

- Is the size effect mediated by *adult* IGF-1, by *developmental* IGF-1 exposure, or by pleiotropic effects of growth alleles (e.g., SMAD2/TGF-β, HMGA2 on cell proliferation)? No study has dissociated these in dogs.
- Why do two well-powered epigenetic studies disagree on size-dependent age acceleration ([33] vs [34])? Platform (array vs RRBS), tissue, cohort and clock-training differences are candidates; a head-to-head analysis is needed. The direction of the size effect in Jang et al. 2026 [35] was not captured here. The published PNAS abstract says only that drift "varied by body size"; the full text was not accessible to the verifier (UNRESOLVED).
- No individual-level GWAS of lifespan in dogs with adequate power exists yet; the Dog Aging Project's longitudinal cohort (52,705 enrolled by Dec 2025 per press) is the obvious vehicle.
- The purebred-vs-crossbred direction reversed between 2013 [3] and 2024 [5] UK data — composition change or artefact?
- Within-breed size–lifespan relationships should be re-examined in large modern datasets with obesity controlled.
- Kealy 2002 remains the only lifespan RCT in dogs; its 25% restriction effect (+1.8 y) has not been replicated in other breeds.
- Confirm the Ames-dwarf lifespan numbers and the Cavalier MVD prevalence figures against primary papers (not opened here).

## Sources

1. Kraus C, Pavard S, Promislow DEL (2013). The size–life span trade-off decomposed: why large dogs die young. *Am Nat* 181(4):492–505. doi:10.1086/669665. PMID 23535614. (A correction notice exists, doi:10.1086/670646; its content was not accessible and it was not checked whether it affects the numbers. [verifier note])
2. Greer KA, Canterberry SC, Murphy KE (2007). Statistical analysis regarding the effects of height and weight on life span of the domestic dog. *Res Vet Sci* 82(2):208–214. doi:10.1016/j.rvsc.2006.06.005. PMID 16919689.
3. O'Neill DG, Church DB, McGreevy PD, Thomson PC, Brodbelt DC (2013). Longevity and mortality of owned dogs in England. *Vet J* 198(3):638–643. doi:10.1016/j.tvjl.2013.09.020. PMID 24206631.
4. Teng KT, Brodbelt DC, Pegram C, Church DB, O'Neill DG (2022). Life tables of annual life expectancy and mortality for companion dogs in the United Kingdom. *Sci Rep* 12:6415. doi:10.1038/s41598-022-10341-6. PMC9050668.
5. McMillan KM, Bielby J, Williams CL, Upjohn MM, Casey RA, Christley RM (2024). Longevity of companion dog breeds: those at risk from early death. *Sci Rep* 14:531. doi:10.1038/s41598-023-50458-w. PMC10834484.
6. Montoya M, Morrison JA, Arrignon F, Spofford N, Charles H, Hours M-A, Biourge V (2023). Life expectancy tables for dogs and cats derived from clinical data. *Front Vet Sci* 10:1082102. doi:10.3389/fvets.2023.1082102. PMC9989186.
7. Urfer SR, Kaeberlein M, Promislow DEL, Creevy KE (2020). Lifespan of companion dogs seen in three independent primary care veterinary clinics in the United States. *Canine Med Genet* 7:7. doi:10.1186/s40575-020-00086-8. PMID 32835231.
8. Nam Y, White M, Karlsson EK, Creevy KE, Promislow DEL, McClelland RL; Dog Aging Project Consortium (2024). Dog size and patterns of disease history across the canine age spectrum: Results from the Dog Aging Project. *PLoS ONE* 19(1):e0295840. doi:10.1371/journal.pone.0295840.
9. Yordy J, Kraus C, Hayward JJ, White ME, Shannon LM, Creevy KE, Promislow DEL, Boyko AR (2019/2020). Body size, inbreeding, and lifespan in domestic dogs. *Conserv Genet* 21(1):137–148. doi:10.1007/s10592-019-01240-x. PMID 32607099; PMC7326369.
10. Kraus C, Snyder-Mackler N, Promislow DEL (2023). How size and genetic diversity shape lifespan across breeds of purebred dogs. *GeroScience* 45:627–643. doi:10.1007/s11357-022-00653-w. PMID 36066765; PMC9886701. (Data: owner-reported lifespans from a public database, not VMDB. [verifier note])
11. Galis F, Van der Sluijs I, Van Dooren TJM, Metz JAJ, Nussbaumer M (2007). Do large dogs die young? *J Exp Zool B* 308B(2):119–126. doi:10.1002/jez.b.21116. PMID 16788896.
12. Sutter NB, Bustamante CD, Chase K, et al., Ostrander EA (2007). A single IGF1 allele is a major determinant of small size in dogs. *Science* 316(5821):112–115. doi:10.1126/science.1137045. PMID 17412960.
13. Gray MM, Sutter NB, Ostrander EA, Wayne RK (2010). The IGF1 small dog haplotype is derived from Middle Eastern grey wolves. *BMC Biol* 8:16. doi:10.1186/1741-7007-8-16. PMID 20181231.
14. Hoopes BC, Rimbault M, Liebers D, Ostrander EA, Sutter NB (2012). The insulin-like growth factor 1 receptor (IGF1R) contributes to reduced size in dogs. *Mamm Genome* 23:780–790. doi:10.1007/s00335-012-9417-z.
15. Rimbault M, Beale HC, Schoenebeck JJ, Hoopes BC, Allen JJ, Kilroy-Glynn P, Wayne RK, Sutter NB, Ostrander EA (2013). Derived variants at six genes explain nearly half of size reduction in dog breeds. *Genome Res* 23:1985–1995. doi:10.1101/gr.157339.113. PMID 24026177.
16. Plassais J, Kim J, Davis BW, et al., Ostrander EA (2019). Whole genome sequencing of canids reveals genomic regions under selection and variants influencing morphology. *Nat Commun* 10:1489. doi:10.1038/s41467-019-09373-w. PMC6445083.
17. Plassais J, vonHoldt BM, Parker HG, et al., Larson G, Frantz L, Ostrander EA (2022). Natural and human-driven selection of a single non-coding body size variant in ancient and modern canids. *Curr Biol* 32(4):889–897.e9. doi:10.1016/j.cub.2021.12.036. PMID 35090588; PMC8891063. (Press coverage used for allele letters and the 54-kyr wolf: Science news 2022 "Gene for 'toy' dog breeds found in ancient wolves"; sci.news 2022.)
18. Eigenmann JE, Patterson DF, Froesch ER (1984). Body size parallels insulin-like growth factor I levels but not growth hormone secretory capacity. *Acta Endocrinol (Copenh)* 106(4):448–453. doi:10.1530/acta.0.1060448. PMID 6382895.
19. Greer KA, Hughes LM, Masternak MM (2011). Connecting serum IGF-1, body size, and age in the domestic dog. *Age (Dordr)* 33(3):475–483. doi:10.1007/s11357-010-9182-4. PMID 20865338.
20. Guevara-Aguirre J, Balasubramanian P, Guevara-Aguirre M, et al., Longo VD (2011). Growth hormone receptor deficiency is associated with a major reduction in pro-aging signaling, cancer, and diabetes in humans. *Sci Transl Med* 3(70):70ra13. doi:10.1126/scitranslmed.3001845. PMID 21325617.
21. Brown-Borg HM, Borg KE, Meliska CJ, Bartke A (1996). Dwarf mice and the ageing process. *Nature* 384(6604):33. doi:10.1038/384033a0. PMID 8900272. 🟡 Not opened in this pass; lifespan-extension percentages taken from secondary summaries. [verifier: metadata confirmed]
22. Jimenez AG (2016). Physiological underpinnings in life-history trade-offs in man's most popular selection experiment: the dog. *J Comp Physiol B* 186:813–827. doi:10.1007/s00360-016-1002-4. PMID 27222254.
23. Jimenez AG, Winward J, Beattie U, Cipolli W (2018). Cellular metabolism and oxidative stress as a possible determinant for longevity in small breed and large breed dogs. *PLoS ONE* 13(4):e0195832. doi:10.1371/journal.pone.0195832.
24. Brookes PS, Jimenez AG (2021). Metabolomics of aging in primary fibroblasts from small and large breed dogs. *GeroScience* 43:1683–1698. doi:10.1007/s11357-021-00388-0. PMID 34132979.
25. Harper JM, Hicks M, Jimenez AG (2025). The resistance of domestic canine skin-derived fibroblasts to oxidative and non-oxidative chemical injury: implications of breed and body size. *GeroScience* 47(3):3665–3675. doi:10.1007/s11357-024-01358-y. PMID 39316259. [verifier-corrected: pages added]
26. Jimenez AG, Downs CJ (2020). Untangling life span and body mass discrepancies in canids: phylogenetic comparison of oxidative stress in blood from domestic dogs and wild canids. *Am J Physiol Regul Integr Comp Physiol* 319(2):R203–R210. doi:10.1152/ajpregu.00067.2020. PMID 32609535.
27. Fleming JM, Creevy KE, Promislow DEL (2011). Mortality in North American dogs from 1984 to 2004: an investigation into age-, size-, and breed-related causes of death. *J Vet Intern Med* 25(2):187–198. doi:10.1111/j.1939-1676.2011.0695.x. PMID 21352376.
28. Nunney L (2024). The effect of body size and inbreeding on cancer mortality in breeds of the domestic dog: a test of the multi-stage model of carcinogenesis. *R Soc Open Sci* 11(1):231356. doi:10.1098/rsos.231356. PMID 38298404.
29. Edmunds GL, Smalley MJ, Beck S, Errington RJ, Gould S, Winter H, Brodbelt DC, O'Neill DG (2021). Dog breeds and body conformations with predisposition to osteosarcoma in the UK: a case-control study. *Canine Med Genet* 8:2. doi:10.1186/s40575-021-00100-7. PMID 33750475.
30. O'Neill DG, Edmunds GL, Urquhart-Gilmore J, Church DB, Rutherford L, Smalley MJ, Brodbelt DC (2023). Dog breeds and conformations predisposed to osteosarcoma in the UK: a VetCompass study. *Canine Med Genet* 10:8. doi:10.1186/s40575-023-00131-2. PMID 37365662; PMC10294386. [verifier-corrected: title and article number confirmed. Scottish Deerhound OR 118.40 (95% CI 41.12–340.95), Leonberger 55.79, Great Dane 34.24, Rottweiler 26.67, chondrodystrophic OR 0.10]
31. Fick LJ, Fick GH, Li Z, Cao E, Bao B, Heffelfinger D, Parker HG, Ostrander EA, Riabowol K (2012). Telomere length correlates with life span of dog breeds. *Cell Rep* 2(6):1530–1536. doi:10.1016/j.celrep.2012.11.021. PMID 23260664.
32. Thompson MJ, vonHoldt B, Horvath S, Pellegrini M (2017). An epigenetic aging clock for dogs and wolves. *Aging (Albany NY)* 9(3):1055–1068. doi:10.18632/aging.101211. PMID 28373601; PMC5391218. [verifier-corrected: DOI confirmed]
33. Horvath S, Lu AT, Haghani A, Zoller JA, Li CZ, Lim AR, Brooke RT, Raj K, Serres-Armero A, Dreger DL, Hogan AN, Plassais J, Ostrander EA (2022). DNA methylation clocks for dogs and humans. *Proc Natl Acad Sci USA* 119(21):e2120887119. doi:10.1073/pnas.2120887119. PMID 35580182; PMC9173771.
34. McCoy BM, et al., Snyder-Mackler N; Dog Aging Project Consortium (2024). Aging at scale: Younger dogs and larger breeds from the Dog Aging Project show accelerated epigenetic aging. *bioRxiv* 2024.10.03.616519 (v2, 29 Oct 2024). doi:10.1101/2024.10.03.616519. PMID 39553930 (preprint). [verifier: no peer-reviewed version found in bioRxiv or Europe PMC as of 2026-10-04; the HR is based on 49 deaths]
35. Jang S, Kim SJ, Kang D, Hong CY, Bok EY, Lee SL, Choe YH, Kim J (2026). Age-associated epigenetic drift trajectory and cross-national disparities in accelerated aging in domestic dogs. *Proc Natl Acad Sci USA* 123(29):e2528874123 (July 2026). doi:10.1073/pnas.2528874123. PMID 42441848. [verifier-corrected: volume/issue added]
36. Ko WH, Shin S (2025). Diverse breeds, diverse lifespans: understanding longevity in domestic dogs. *J Vet Sci* 26(Suppl 1):S22–S33. doi:10.4142/jvs.25175. PMC12520860.
37. Bannasch D, Famula T, Donner J, Anderson H, Honkanen L, Batcher K, Safra N, Thomasy S, Rebhun R (2021). The effect of inbreeding, body size and morphology on health in dog breeds. *Canine Med Genet* 8:12. doi:10.1186/s40575-021-00111-4. PMID 34852838; PMC8638537.
38. Hoffman JM, Creevy KE, Promislow DEL (2013). Reproductive capability is associated with lifespan and cause of death in companion dogs. *PLoS ONE* 8(4):e61082. doi:10.1371/journal.pone.0061082. PMC3629191.
39. Kealy RD, Lawler DF, Ballam JM, Mantz SL, Biery DN, Greeley EH, Lust G, Segre M, Smith GK, Stowe HD (2002). Effects of diet restriction on life span and age-related changes in dogs. *J Am Vet Med Assoc* 220(9):1315–1320. doi:10.2460/javma.2002.220.1315. PMID 11991408.
40. Wess G, Schulze A, Butz V, Simak J, Killich M, Keller LJ, Maeurer J, Hartmann K (2010). Prevalence of dilated cardiomyopathy in Doberman Pinschers in various age groups. *J Vet Intern Med* 24(3):533–538. doi:10.1111/j.1939-1676.2010.0479.x. PMID 20202106.
41. Awano T, Johnson GS, Wade CM, et al., Coates JR (2009). Genome-wide association analysis reveals a SOD1 mutation in canine degenerative myelopathy that resembles amyotrophic lateral sclerosis. *Proc Natl Acad Sci USA* 106(8):2794–2799. doi:10.1073/pnas.0812297106. PMID 19188595.
42. Ko WH, Kim S, Catry A, Cho JY, Shin S (2025). Genome-wide statistical evidence elucidates candidate factors of life expectancy in dogs. *Mol Cells* 48(1):100162. doi:10.1016/j.mocell.2024.100162. PMID 39580055; PMC11721540.
43. Korec E, Ungrová L, Kalvas J, Hejnar J (2025; online Dec 2024). Identification of genes associated with longevity in dogs: 9 candidate genes described in Cavalier King Charles Spaniel. *Vet Anim Sci* 27:100420. doi:10.1016/j.vas.2024.100420. PMID 39823074; PMC11737349. [verifier-corrected: volume/year/DOI]
44. Sohrab V, White ME, Harrison BR, Bierman R, Marye A, Morrill Pirovich K, Genereux DP, Megquier K, Li X, Kenney B, Reichel C, Snyder-Mackler N, Akey JM, Promislow DEL, Chen FL, Karlsson EK (2026). Blood biomarkers and breed genetics of aging in pet dogs. *bioRxiv* 2026.03.07.710297 (posted 10 Mar 2026). doi:10.64898/2026.03.07.710297. Preprint, not peer-reviewed.
45. Loyal (28 Nov 2023). "FDA Center for Veterinary Medicine agrees Loyal's data supports reasonable expectation of effectiveness for large dog lifespan extension." https://loyal.com/posts/loyal-announces-historic-fda-milestone-for-large-dog-lifespan-extension-drug (company communication).
46. Turcsán B, Kubinyi E (2024). Differential behavioral aging trajectories according to body size, expected lifespan, and head shape in dogs. *GeroScience* 46:1731–1754. doi:10.1007/s11357-023-00945-9. PMID 37740140.
47. cavalierhealth.org, "Mitral Valve Disease and the Cavalier King Charles Spaniel" (breed-club compilation; secondary). 🟡
48. Choi C (2013). "Why little dogs outlive big dogs." NBC News / LiveScience coverage of [1]. https://www.nbcnews.com/news/all/why-little-dogs-outlive-big-dogs-flna1C8737416 (secondary; source of the "~1 month per 2 kg" figure; dated 6 Mar 2013, verified).
49. Selman C, Nussey DH, Monaghan P (2013). Ageing: it's a dog's life. *Curr Biol* 23(10):R451–R453. doi:10.1016/j.cub.2013.04.005. PMID 23701689. (Dispatch on [1]; per search-engine excerpt it says body mass explained 44% of breed variance in mortality at onset of senescence, "equating to a reduction in lifespan of one month for every 2 kg increase in mass"; full text not accessed.) [verifier-added]

## Verification notes

*Independent verification by Opus 5.5 on 2026-10-04. Full audit table: ../07_verification/breed_wolves_verification.md.*

- **Confirmed against primary full text or abstract.**
  - Kraus 2013: abstract on ageing rate vs onset.
  - McMillan 2024: all figures — n, deceased count, 155 breeds, size, cephalic, sex and purebred/crossbred medians, and all breed medians in §1.2.
  - Teng 2022: all life-expectancy values, plus the French Bulldog popularity caveat.
  - Montoya 2023: size-class, BCS and sex values.
  - Genetics: Rimbault 2013 (46–52.5% / 64.3%); Plassais 2019 (14 genes, "as much as 95%"; 722 genomes); Plassais 2022 (1,431 genomes / 13 species; C ancestral-small / T derived-large; 53,000-y wolf; 75% of CC dogs <15 kg); Eigenmann 1984 (6×, r = 0.88).
  - Horvath 2022: no age-acceleration association with breed traits; Great Dane 6.3 y / Toy Poodle 14.6 y.
  - Ko & Shin 2025: the "40%" misattribution.
  - Preprints: McCoy 2024 (n = 864, 0.37 y/y, HR 1.34 [1.06–1.69]); Sohrab 2026 (7,627 dogs, 298 loci, 159 traits, 957 with follow-up).
  - Cancer: Nunney 2024; Edmunds 2021 (OR 45.44); O'Neill 2023 (OR 118.40; 905,552 dogs).
  - Inbreeding: Bannasch 2021 (F = 0.249, RR 1.22/1.29, r² = 0.77); Yordy 2020 (4,586 dogs / 117 breeds; 95% / 46%).
  - Hoffman 2013 (+13.8% / +26.3%; 70,574 and 40,139 dogs) and Kealy 2002 (13.0 vs 11.2 y, P < 0.01).
  - Also confirmed: Greer 2007, O'Neill 2013, Urfer 2020, Kraus 2023, Nam 2024 (27,541 dogs), Fick 2012, Gray 2010, Sutter 2007, Hoopes 2012, Greer 2011, Guevara-Aguirre 2011, Brookes 2021, Harper 2025, Turcsán 2024, Ko 2025 (*IGSF1/ARHGAP36*), Korec, Wess 2010, Awano 2009, Galis 2007 and the Loyal 28 Nov 2023 announcement.
- **Corrected.**
  - TL;DR size-gap wording.
  - Siberian wolf age (53,000, not 54,000).
  - Horvath EWAS: *SMAD2/IGF1R* came from a candidate-gene look-up, not the top hits. The top hits were *SF1* and *TTC8*.
  - Bannasch methods description.
  - Dog10K "14%" refers to structural variants.
  - UK neutering gain is +0.9–1.5 y.
  - Ames dwarf percentage.
  - Fleming neoplasia details downgraded.
  - Nunney significance nuance.
  - Jimenez 2018 sample-size breakdown flagged.
  - Missing bibliographic details added: O'Neill 2023 title and 10:8, Thompson DOI, Korec, Jang, Harper, Brown-Borg.
- **Downgraded.** The McCoy 2024 mortality result is now 🟡, because it is an unreviewed preprint based on 49 deaths.
- **Still open.**
  - The "1 month per 2 kg" figure is supported by press and the Selman 2013 dispatch excerpt, not by the Kraus text.
  - Direction of the body-size effect in Jang 2026.
  - Jimenez 2018 breed/sample counts.
  - Content of the Kraus 2013 correction notice.
  - DAP enrolment figure (52,705) not checked.
