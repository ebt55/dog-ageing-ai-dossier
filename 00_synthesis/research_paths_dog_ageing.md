# Research paths: understanding and changing dog ageing

> Synthesis for the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 (orchestrator) from the independently verified files in this dossier · Every factual claim points to the dossier file that holds its primary-source citation · Everything labelled **PROPOSAL** is a research design, not a finding · Cost and time figures are rough estimates (❓), not quotes. · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

This document answers the user's end goal: *find compelling research paths to better understand, and possibly edit, dog ageing.* It merges and re-ranks:
- the 18 proposals in [`../06_ai_toolkit/research_path_candidates.md`](../06_ai_toolkit/research_path_candidates.md);
- the six mechanistic proposals in [`../04_dog_aging_biology/why_dogs_age_fast.md`](../04_dog_aging_biology/why_dogs_age_fast.md) §6.4;
- the canine fine-tuning plans in [`../02_mammal/mammal_for_dogs.md`](../02_mammal/mammal_for_dogs.md);
- the dog use-cases in [`../01_alphafold/alphafold_and_dogs.md`](../01_alphafold/alphafold_and_dogs.md);
- the gaps the verifiers exposed.

---

## 1. What the evidence says we are actually trying to change

The verified files establish five facts. Each one constrains which research path makes sense.

| # | Fact | Strength | Where |
|---|---|---|---|
| F1 | **The dog–human gap is about 5–6×, not 10×.** Median dog lifespan is about 12.5 y against human life expectancy of about 73 y. On the mammalian body-mass–lifespan line, **dogs are roughly where a mammal of their size should be (about 109% of expected maximum); humans are about 4.6× above it.** The question "why do dogs die so young?" is really "why do humans live so long?" plus a smaller dog-specific question. | Established (comparative data) | [why_dogs_age_fast §1, §6](../04_dog_aging_biology/why_dogs_age_fast.md) |
| F2 | **Within dogs the size rule reverses.** Large and giant breeds die years earlier: about 4.0 y separates small (13.5 y) from giant (9.5 y) purebreds in US Banfield data. The best mortality decomposition (Kraus 2013, 74 breeds) says big dogs die young mainly because they **age faster**, not because ageing starts earlier. The effect is **breed-level and genetic**: within a breed, bigger individuals are not shorter-lived. | Well supported (large cohorts) | [breed_size_genetics_lifespan](../04_dog_aging_biology/breed_size_genetics_lifespan.md) |
| F3 | **Breed size runs through a few genes on the GH/IGF-1 axis.** About seven markers explain about half of breed-weight variance (IGF1, IGF1R, GHR, HMGA2, SMAD2, STC2…), and about 14–20 loci explain 90–95% at breed level. The key small-size variant is a **non-coding SNP in an IGF1 antisense lncRNA (IGF1-AS)**. Its "small" allele is *ancestral*, present in a 53,000-year-old wolf, and resurrected by human selection. Standard poodles have about 6× the serum IGF-1 of toy poodles. | Established genetics; the link to *ageing rate* is correlational | [breed_size_genetics_lifespan](../04_dog_aging_biology/breed_size_genetics_lifespan.md) |
| F4 | **Large canid size does not by itself force a short life.** Grey wolves (often 36–59 kg) average only 4–5 y in the wild, almost all from extrinsic deaths, but reach a recorded maximum of 20.6 y in captivity. That is longer than large and giant dog breeds (US life expectancy 11.5 and 9.5 y). **No size-matched dog-vs-wolf comparison of ageing rate has ever been done.** | Data solid; the inference "large-breed brevity is a selection artefact" is ❓ | [wolves_vs_dogs](../04_dog_aging_biology/wolves_vs_dogs.md) |
| F5 | **Dog ageing is malleable, but only one intervention has proven it.** 25% lifelong caloric restriction gave **+1.8 y median lifespan (13.0 vs 11.2 y)** in 48 paired Labradors (Kealy 2002). **Nothing is approved for dog lifespan as of 4 Oct 2026.** Loyal's LOY-002 has two of three FDA technical sections accepted (efficacy expectation Feb 2025, safety Jan 2026; manufacturing pending). LOY-001 and LOY-003 have efficacy-expectation acceptances. The **TRIAD rapamycin RCT** (target n=580, lifespan endpoint) and Loyal's **STAY** study (1,300 dogs) have not reported. The dog rapamycin *cardiac* signal (Urfer 2017) **did not replicate** (Barnett 2023). | Verified | [dog_longevity_interventions](../05_interventions/dog_longevity_interventions.md) |

And one mechanistic picture, a well-supported correlation with causation unproven ([why_dogs_age_fast §3, §6](../04_dog_aging_biology/why_dogs_age_fast.md)):
- Almost every biological "clock" runs 4–10× faster in dogs than in humans:
  - somatic mutations 5.3× faster (about 249 vs 47 per genome per year), reaching a similar end-of-life burden;
  - telomere loss about 10× faster;
  - maturity about 9× sooner;
  - adult mortality doubling about every 2 y versus about 8 y in humans.
- These look like **readouts of one coordinated life-history tempo**, probably set by species-specific cellular kinetics, rather than independent causes.

### So there are four different "things" one could edit

| Target | What it means | Tractability | Paths below |
|---|---|---|---|
| **A. Species tempo** | Why canid cells and bodies run a ~5× faster programme than human ones | Hardest; fundamental science; years | 7 |
| **B. Adult rate of ageing** | Slowing ageing in adults through nutrient sensing (CR, mTOR, insulin/IGF) | Realistic; trials under way (TRIAD, STAY) | 5, 6 |
| **C. Breed-specific acceleration** | The extra ageing in large breeds (GH/IGF-1, growth, cancer) | **The most tractable dog-specific lever**: recent, oligogenic, mapped | 1, 2, 3, 4, 9, 10, 11 |
| **D. Specific killers** | Cancer, cognitive dysfunction, heart disease | Most certain near-term gains in median lifespan | 6, 8 (and veterinary medicine generally) |

---

## 2. Where AI genuinely helps, and where it doesn't

The core finding from folders [`01_alphafold`](../01_alphafold/), [`02_mammal`](../02_mammal/), [`03_canine_bio_ai`](../03_canine_bio_ai/) and [`06_ai_toolkit`](../06_ai_toolkit/): **the bottleneck for dog ageing is canine data and causal experiments, not model architecture.**

| AI capability | Status for dogs (Oct 2026) | Implication |
|---|---|---|
| **Protein structure** (AlphaFold 3, Boltz-2, Chai-1…) | Species-agnostic and ready. About 90.6% of dog UniProt entries have an AlphaFold DB model. Mature dog IGF-1 is 100% identical to human, and the mTOR rapamycin-binding (FRB) domain is 100% identical. **Full-length dog IGF1R and MTOR have no AFDB model** (unreviewed entries over 1,280 aa are excluded), so model them yourself. | Structure is **not** the bottleneck for geroprotector targets. AF3 models of IGF-1/IGF1R mostly recall known PDB structures. |
| **Variant-effect prediction** | **The weakest link.** AlphaMissense is human-only with no released weights. Mapping dog variants onto human proteins gives sensitivity 0.77–0.90 but specificity only 0.20–0.46 (auROC 0.55–0.61). | A native canine variant-effect model is a prerequisite for most genetics paths (Path 4). |
| **DNA / regulatory models** | **Evo 2** (and InstaDeep's **NTv3**, pre-trained on the same OpenGenome2 corpus) saw a dog genome during training. AlphaGenome, Enformer and Borzoi are human/mouse only. No canine regulatory model exists. | Path 3: the key ageing variant (IGF1-AS) is non-coding, so a dog regulatory model is the gap. |
| **Single-cell foundation models** | Dog is absent from training (scGPT, Geneformer, UCE, TranscriptFormer). UCE and TranscriptFormer can embed unseen species zero-shot. China's scCompass database includes dog cells. | Path 8. Also no pan-tissue canine cell atlas exists. |
| **Multimodal biomedical models (IBM MAMMAL)** | Human-centric. Single-cell data were filtered to human; there are no dog antibodies; organism tokens are human/mouse/rat/rabbit/monkey/camel; **78% of canine gene symbols** have a token. Small-molecule tasks transfer; protein tasks transfer weakly; canine antibody design is effectively blocked. | Usable after fine-tuning for canine drug-response and geroprotector screens (Path 6). |
| **Ageing clocks** | **The most dog-ready AI artefact.** The pan-mammalian methylation clock gives r = 0.94 in 742 dogs, and a human–dog dual clock reaches R = 0.97. Caveat: canine clocks are confounded by breed population structure (Serres Armero 2024). | Path 5: clocks as trial endpoints. |
| **Dog-specific foundation models** | **None exist** for protein, DNA or single-cell data (independently re-searched by the verifier). Dog *imaging* foundation models do exist (VET-DINO, 5 M canine radiographs; V-REX). | Building canine data resources is where a newcomer can matter most. |

**What MAMMAL and AlphaFold will and won't do for dog ageing.** They are **enablers for specific sub-steps**:
- designing a binder to canine IGF1R;
- ranking compounds against canine cell lines;
- scoring protein–protein interactions.

They do not, on their own, explain why a dog ages fast. The YouTube video's framing ("one model that understands everything") overstates even the human case: MAMMAL has no DNA modality, and its AlphaFold 3 "win" came from supervised fine-tuning on those exact targets ([video_claims_factcheck](../02_mammal/video_claims_factcheck.md), [mammal_paper_deep_dive §5](../02_mammal/mammal_paper_deep_dive.md)).

---

## 3. The research paths, ranked

Ranked by **expected insight per unit of cost and risk**, weighted toward paths that (a) target the tractable dog-specific lever C, (b) create resources other paths need, or (c) answer a question no one has asked.

### Tier 1: do first (computational, existing data, months not years)

#### Path 1 — Separate "size genes" from "ageing-rate genes" · PROPOSAL
- **Question.** Which variants change the *rate* of ageing independently of body size and breed ancestry? And do large breeds age faster at the molecular level, or only die earlier?
- **Why compelling.** Every current dog-ageing hypothesis is tangled with size, and nobody has untangled it. The two best epigenetic studies **disagree**:
  - Dog Aging Project clock, n=864: the largest breeds age about 0.37 extra epigenetic years per year. This is an unreviewed preprint, and its mortality link rests on 49 deaths.
  - Horvath 2022, 742 samples: no association between age acceleration and breed weight.
  - Resolving this is itself a headline result.
- **How.**
  1. Score Dog Aging Project methylation with clocks that can actually read it.
     - DAP methylation is **RRBS**, so use a DAP-native RRBS clock on DAP data.
     - The human–dog dual and pan-mammalian clocks are built for the **mammalian methylation array**. Apply them to RRBS only after mapping RRBS coverage onto the array's ~36k conserved CpGs, and budget for substantial CpG dropout. Otherwise, restrict them to the array cohorts (Horvath 2022, Thompson 2017). *[Point raised by the toolkit verifier.]*
  2. Run an ancestry-aware GWAS on the clock residual within and across the five DAP size classes.
  3. Separately fit Gompertz mortality models (initial mortality vs rate of increase) per breed in DAP and VetCompass data.
  4. Replicate in the Golden Retriever Lifetime Study, a single breed and so free of breed structure.
- **Data and tools.**
  - DAP (Terra, data-use agreement; one-year embargo)
  - Dog10K (imputation/annotation)
  - GRLS (CC-BY-SA genotypes)
  - VetCompass life tables
  - GCTA/SAIGE mixed models
- **First step.** Apply for DAP data access.
- **Cost.** 1–2 people, 4–6 months, under $10k compute ❓.
- **Main risk.** Power (only 864–976 dogs with methylation), plus breed-structure confounding (Serres Armero 2024). Pre-register a gene-set analysis as the primary test.
- **Sources.** Toolkit #1 and #9; why_dogs §6.4 #5–6.

#### Path 2 — The wolf as the control group · PROPOSAL (new synthesis)
- **Question.** Do large dogs age faster than size-matched wolves, i.e. is large-breed brevity a domestication or selection artefact?
- **Why compelling.** This is the cleanest natural experiment available and it has **never been done**:
  - Wolves of 36–59 kg reach 15–20 y in captivity, while Great Danes, Irish Wolfhounds and Mastiffs rarely pass 10.
  - Wolves carry the derived "large" IGF1-AS allele, so size genetics alone don't explain the gap.
  - The only dog–wolf molecular study (Thompson 2017: 46 dogs, 62 wild wolves) built a joint clock but **did not compare ageing rates**.
- **How.**
  1. Collect blood from captive wolves of known age (zoos and sanctuaries; non-invasive, during routine veterinary care).
  2. Profile the wolf samples on a platform that matches the dog comparison data.
     - **Option A:** the mammalian methylation array (HorvathMammalMethylChip40), to compare against Horvath's 742 dogs. This is a custom array distributed through the Mammalian Methylation Consortium / Epigenetic Clock Development Foundation, so securing array access and clock coefficients is a prerequisite.
     - **Option B:** RRBS, to compare against the Dog Aging Project's clock.
  3. Compare clock slopes and residuals with size-matched giant and large breeds, and with small breeds.
  4. Add IGF-1, metabolomic and immune-ageing markers.
  5. Mine zoo records (e.g. ZIMS) for captive-wolf life tables.
- **Expected output.** A direct test of whether large-breed acceleration is specific to domestic dogs. If it is, the levers are recent, selected alleles, which are much more tractable than a species programme.
- **Cost.** 1–2 people plus array costs for about 100–200 animals; roughly $50–150k ❓; 12–18 months, dominated by sample access.
- **Main risks.** Sample access, permits, and small n for old wolves. Captive wolves differ from wild ones in diet and activity.
- **Collaborators to approach.** vonHoldt (Princeton), the Horvath/Mammalian Methylation Consortium groups, zoo veterinary networks.
- **Sources.** [wolves_vs_dogs](../04_dog_aging_biology/wolves_vs_dogs.md); [canine_bio_ai/companies](../03_canine_bio_ai/companies_and_research_groups.md).

#### Path 3 — Decode the IGF1-AS / GH–IGF-1 regulatory mechanism with sequence models · PROPOSAL
- **Question.** *How* does the non-coding IGF1-AS variant change IGF-1 output, in which tissues, and at what developmental time? Which other breed-size regulatory variants act the same way?
- **Why compelling.** IGF1-AS is the best-validated size-and-lifespan locus in dogs, yet it is non-coding, and no model scores canine regulatory variants properly. Understanding its mechanism is the precondition for *reversible* modulation instead of a genetic edit.
- **How.**
  1. Score IGF1-AS and the other size loci zero-shot with **Evo 2**, whose training includes the dog genome.
  2. Build a dog-referenced constraint map and a canine Borzoi-style sequence-to-function model, trained on DoGA promoter atlases, BarkBase and EpiC Dog chromatin tracks.
  3. Prioritise variants and test them in canine cell reporter assays (MPRA).
- **Cost.** 2 people, 9–18 months, $30–100k GPU ❓.
- **Main risk.** Canine functional-genomics tracks are thin (DoGA's published atlas covers 9 dogs plus 12 embryos).
- **Sources.** Toolkit #7; [dog_foundation_models_landscape](../03_canine_bio_ai/dog_foundation_models_landscape.md).

#### Path 4 — A native canine variant-effect predictor and a breed "ageing-gene load" map · PROPOSAL
- **Question.** Which breeds carry damaging variants in ageing-pathway genes (GH/IGF, mTOR, DNA repair, proteostasis), and does that load predict breed lifespan beyond size?
- **Why compelling.** Every genetics project depends on variant scoring, and the borrowed human tools perform near chance in animals (auROC 0.55–0.61).
- **How.**
  1. Train or calibrate a canine predictor (popEVE/ESM-style, conditioned on Dog10K and CanVAS population frequencies).
  2. Benchmark it against OMIA known causal variants.
  3. Score more than 300 breeds.
  4. Regress breed lifespan on load, controlling for size and inbreeding.
- **Data.** Dog10K (1,987 canids), CanVAS (15,451 dogs, CC-BY), OMIA, UniProt UP000805418.
- **Cost.** 1–2 people, 3–6 months, under $5k ❓.
- **Main risks.**
  - Few validated canine pathogenic variants to benchmark against. OMIA's 597 dog causal variants are mostly Mendelian.
  - popEVE is GPL-3.0, so a canine derivative inherits copyleft.
  - Wisdom Panel's public data cover only 250 pre-selected disease variants, so build pathway burdens from Dog10K and CanVAS instead.
- **Sources.** Toolkit #2 and #4; [alphafold_and_dogs](../01_alphafold/alphafold_and_dogs.md).

#### Path 5 — Clocks as trial endpoints: a canine multi-omic composite clock validated against mortality and interventions · PROPOSAL
- **Question.** Can a clock built from methylation, metabolome and clinical labs predict death well enough to act as a surrogate endpoint, so that dog longevity trials take 1–2 years instead of 4–5?
- **Why compelling.** Every interventional path is gated by trial length. TRIAD needs a year of treatment plus two years of observation; STAY runs about 4 years. Diet restriction already shifts biological-age markers in dogs, and the dual human–dog clock gives a direct human read-out.
- **How.**
  1. Fit the clock in the DAP Precision Cohort (976 dogs) against accruing deaths.
  2. Test for pre-registered responsiveness in TRIAD and STAY samples, if access is possible.
  3. Note that a 2026 DAP preprint found GH/IGF-1 metabolites are weaker mortality predictors than several others; keep IGF-1 as one feature, not the model.
- **Cost.** 1–2 people, 6–9 months, under $20k ❓.
- **Power.** About **105 deaths** have already accrued: Sohrab et al. 2026 report 957 Precision-Cohort dogs followed for 3 years, with 11% dying. That is enough to validate one pre-registered composite score, but not to select models modality by modality.
- **Sources.** Toolkit #9 and #11; [why_dogs_age_fast §6.4 #6](../04_dog_aging_biology/why_dogs_age_fast.md); [breed_size_genetics_lifespan](../04_dog_aging_biology/breed_size_genetics_lifespan.md).

### Tier 2: build the missing canine resources, then use them

#### Path 6 — Put the dog on the pan-mammalian longevity map, then screen for geroprotectors in silico · PROPOSAL
- **Question.** Which conserved ageing module (inflammation, interferon, mitochondrial, chromatin, ECM) does large-breed ageing accelerate? Which approved drugs reverse that module in canine cells?
- **Why compelling.** Tyshkovskiy et al. 2026 (*Nature*) built universal ageing and mortality signatures from 4 mammals; **the dog is absent**. The dog is the only species with about 2-fold lifespan variation *within* the species, so it is the perfect test of whether the modules are causal.
- **How.**
  1. Project canine transcriptomes (DoGA, Dog10K blood RNA-seq, beagle ageing PBMC data) onto the signatures.
  2. Regress module scores on breed size and on Path 1's clock residual.
  3. Score compounds against the large-breed signature, using signature reversal (CMap-style) plus **MAMMAL fine-tuned on canine drug-response data**. Use ortholog-mapped gene tokens; 78% of dog gene symbols already have a token.
  4. Validate the top hits in canine cell lines. Cellosaurus lists about 990 dog lines, including the FACC panel; GDSC already screens rapamycin, temsirolimus, AZD8055, navitoclax and dasatinib for human cells.
- **Cost.** About $0 for the projection step (1 person, 3–4 months). The screen plus validation costs $80–200k and takes 9–15 months ❓.
- **Main risk.** The data supply tissue breadth but little age contrast.
  - DoGA's atlas is not age-stratified, so it provides tissue breadth, not an age signal.
  - The real ageing contrasts are blood datasets with n in the tens: Dog10K's 30 blood samples aged 1–9 y, a beagle young-vs-senior set, and a 19-dog multi-omic set.
  - Treat the first phase as a feasibility and placement study.
  - There is also no canine equivalent of DepMap.
- **Sources.** Toolkit #3 and #13; [mammal_for_dogs](../02_mammal/mammal_for_dogs.md).

#### Path 7 — The tempo question: a canid "stem-cell zoo", a somatic-mutation atlas, and DNA-repair assays · PROPOSAL
- **Question.** What sets the species ageing tempo (lever A)? Do giant-breed cells run faster than toy-breed cells? Do wolf cells differ from dog cells?
- **Why compelling.** Developmental tempo (protein turnover, biochemical reaction speeds, segmentation-clock period) has been measured across species in "stem-cell zoo" assays, and it correlates with lifespan. **No dog or wolf cells have been put in these assays.** Cagan 2022's dog somatic-mutation estimate rests on only 3 dogs. No one has measured canine double-strand-break repair against human repair (SIRT6) or checked CIRBP levels.
- **How.**
  1. Derive iPSCs and fibroblasts from toy and giant dogs, wolves and humans.
  2. Measure segmentation-clock period, protein half-lives, metabolic rate and DSB-repair efficiency.
  3. Sequence somatic mutations in colon crypts or blood clones from hundreds of DAP dogs across breeds and ages.
- **Expected output.** The first test of whether breed size changes intracellular tempo, and whether large breeds accumulate mutations faster per year. That would link to the "adaptive lag in cancer suppression" hypothesis.
- **Cost.** 2–3 people, 18–24 months, $200–500k ❓. This is the most fundamental and most expensive path.
- **Main risk.** Ethical sample sourcing for wolves, and iPSC derivation for canids is less mature.
- **Sources.** [why_dogs_age_fast §3.9, §6.4 #1–3](../04_dog_aging_biology/why_dogs_age_fast.md); Toolkit #14.

#### Path 8 — A canine virtual cell · PROPOSAL
- **Question.** Can a single-cell foundation model adapted to dog predict how canine cells respond to ageing-relevant perturbations?
- **How.**
  1. Embed existing canine single-cell data (PBMC atlases, Dog10K hippocampus with 105k nuclei, scCompass dog subsets) with UCE or TranscriptFormer zero-shot.
  2. Fine-tune on harmonised dog data.
  3. Generate a canine perturbation dataset (CRISPRi or compounds on canine cells), because none exists.
- **Cost.** 2 people, 6–9 months, $10–30k for compute only. The perturbation data cost more.
- **Main risk.** Without perturbation data the model cannot be validated. Also unresolved: whether the DAP data-use agreement allows releasing trained weights.
- **Sources.** Toolkit #6; [dog_foundation_models_landscape](../03_canine_bio_ai/dog_foundation_models_landscape.md).

### Tier 3: from understanding to intervention

#### Path 9 — Reversible GH/IGF-axis modulators designed with AI, validated in canine cells · PROPOSAL
- **Question.** Can we make a **reversible, dose-controllable** way to turn down GH/IGF-1 signalling in adult large-breed dogs? Candidates include binders or caninised antibodies against canine IGF1R or GHR, or IGF-1 sequestering proteins.
- **Why compelling.** It tests lever C directly without touching the genome. It is also the ethically correct precursor to any durable genetic intervention. Loyal is in this space commercially (LOY-001 and LOY-003 lower IGF-1, but their molecules are undisclosed), so an open academic reagent would also let the field test the mechanism independently.
- **How.**
  1. Design binders with AlphaFold 3, Boltz-2 and BindCraft/RFdiffusion against canine IGF1R or GHR ectodomains.
     - Dog GHR is only about 82% identical to human, so canine-specific epitopes matter.
     - The dog IGF1R UniProt entry carries an unexplained ~60-residue N-terminal extension, and it has no AlphaFold DB model. Start constructs at the conserved mature sequence (98.1% identical to human), not the predicted precursor.
  2. Express and test the binders in canine cells (IGF-1-stimulated AKT phosphorylation, proliferation).
  3. Caninise the best candidates on the model of approved canine mAbs (lokivetmab, bedinvetmab).
  4. Run safety and pharmacology work before any animal study.
- **Cost.** 2–4 people with a protein lab, 12–18 months, $150–400k ❓.
- **Main risks.** Over-suppression (metabolic effects, growth in young dogs), and immunogenicity.
- **Sources.** Toolkit #12; [how_to_use_alphafold §7](../01_alphafold/how_to_use_alphafold.md); [dog_longevity_interventions](../05_interventions/dog_longevity_interventions.md).

#### Path 10 — Selection informatics: edit lifespan through breeding, not editing · PROPOSAL
- **Question.** Can breed clubs reduce ageing-gene load and inbreeding without creating new breeds?
- **Why compelling.** This is the "edit" with no new technology and the cleanest ethics. Supporting evidence:
  - The small-size IGF1-AS allele is the *ancestral* canid allele.
  - Morbidity rises with inbreeding (mean breed F about 0.25).
  - Breed size and purebred status explain about 95% of breed life-expectancy variance.
- **How.** Combine Path 4's load scores with inbreeding coefficients and outcross options into breeding-advice tools, piloted with one or two giant breeds.
- **Cost.** 1–2 people, 6–12 months, low cost ❓.
- **Main risk.** Adoption by breed clubs, and generational timescales.
- **Sources.** Toolkit #17; [breed_size_genetics_lifespan](../04_dog_aging_biology/breed_size_genetics_lifespan.md).

#### Path 11 — Somatic GH/IGF-axis gene therapy for large breeds: design dossier only, for now · PROPOSAL
- **Feasibility.** Dogs are an established gene-therapy species:
  - AAV-CRISPR restored dystrophin to 3–90% in skeletal muscle and 92% in heart (Amoasii 2018, n=2 systemic).
  - Dogs were the pivotal model for RPE65 (→ Luxturna) and haemophilia B therapies.
  - Rejuvenate Bio's RJB-01 has pilot data in Cavaliers with mitral-valve disease (conference abstract only; n=17).
- **Gap.** **No one has edited an ageing gene in a dog.**
- **Recommendation.** Write the design, ethics and regulatory dossier only after Paths 3 and 9 have validated the target and the dose–response. Regulatory guidance for intentional genomic alterations (GFI #187A/B) offers no companion-dog precedent.
- **Sources.** Toolkit #16; [gene_editing_in_dogs](../05_interventions/gene_editing_in_dogs.md).

#### Not recommended: germline editing of ageing genes
- **Technically feasible.** Examples:
  - MSTN-knockout beagles (2015): 27 puppies, only 2 edited.
  - ApoE-knockout dogs.
  - Colossal's grey wolves (2024–25): 20 edits in 14 genes, cloned via dog surrogates. There is still no peer-reviewed methods paper on the edited animals.
- **Why not.**
  - Mosaicism and off-target risk.
  - Large welfare costs from cloning.
  - A regulatory vacuum.
  - The obvious target (IGF1/IGF1-AS) is the locus that *makes dogs small*, so a naive edit trades lifespan for dwarfism and metabolic effects.
- **Sources.** Toolkit #18; [gene_editing_in_dogs](../05_interventions/gene_editing_in_dogs.md); [wolves_vs_dogs](../04_dog_aging_biology/wolves_vs_dogs.md).

---

## 4. Suggested sequencing (one possible portfolio)

```
Months 0–6    Path 1 (size vs rate GWAS + Gompertz)   Path 4 (canine VEP)   Path 6a (dog on pan-mammal map)
              Path 2 starts: secure wolf samples       Path 5 starts: composite clock
Months 6–18   Path 3 (IGF1-AS regulatory model + MPRA)  Path 6b (in-silico screen → canine cells)
              Path 2 readout (wolf vs large-dog ageing)  Path 8 (canine virtual cell)
Months 12–30  Path 9 (GH/IGF binder design + validation)  Path 7 (stem-cell zoo / mutation atlas)
              Path 10 pilot with a giant breed
Year 3+       Path 11 dossier — only if Paths 3 + 9 + 5 justify it; read TRIAD/STAY results first
```

**Decision points that should re-order everything:**
1. **TRIAD and STAY results** (TRIAD is expected to conclude around 2029 per a secondary source; STAY runs about 4 years from 2023–25 enrolment).
   - If rapamycin or LOY-002 extends lifespan, lever B is proven, and Paths 5 and 6 become the priority (better endpoints, better compounds).
   - If they fail, lever C (Paths 1–4 and 9) becomes the main bet.
2. **Path 1 / Path 2 outcome.**
   - If large breeds do *not* age faster molecularly, the large-breed effect is about specific killers (cancer, especially osteosarcoma at about 45× the odds in dogs over 40 kg). Re-weight toward lever D.
   - One early hint: the Dog Aging Project's spatial-memory study of 6,753 dogs found strong age effects that were **not** moderated by body mass.
3. **The IGF-1 question.**
   - The 2026 DAP preprint found GH/IGF-1 metabolites to be *weaker* mortality predictors than several others. If Paths 1 and 3 confirm that IGF-1 is a size marker more than an ageing driver, deprioritise Paths 9 and 11.

---

## 5. What would change these conclusions

- A peer-reviewed version of the DAP epigenetic-clock preprint, or its refutation, decides whether large breeds age faster molecularly.
- Any dog lifespan RCT readout (TRIAD, STAY).
- Evidence that developmental tempo can be shifted after development without harm, which would unlock lever A.
- A canine single-cell or perturbation atlas, which would unlock Paths 6 and 8.
- Clarification of the DAP data-use agreement on releasing model weights, which gates Paths 1, 5, 6 and 8 as open resources.

---

## 6. A practical starter kit (first 30 days)

1. **Data access.**
   - Apply to the Dog Aging Project (Terra data-use agreement).
   - Download Dog10K (free, no login) and CanVAS (CC-BY).
   - Pull the dog reference proteome UP000805418 from UniProt.
   - See [canine_data_resources](../06_ai_toolkit/canine_data_resources.md).
2. **Tools.**
   - Boltz-2 (MIT) and Chai-1 (Apache-2.0) for commercially unrestricted structure work.
   - AlphaFold Server for quick complexes (non-commercial, 30 jobs/day).
   - ESM-2 for protein embeddings and variant scoring.
   - Evo 2 for dog DNA.
   - MAMMAL from `BiomedSciAI/biomed-multi-alignment`.
   - See [how_to_use_alphafold](../01_alphafold/how_to_use_alphafold.md), [ai_tools_for_dog_aging](../06_ai_toolkit/ai_tools_for_dog_aging.md) and [mammal_paper_deep_dive §8](../02_mammal/mammal_paper_deep_dive.md).
3. **Core papers to read first**, all cited with DOIs in the linked files:
   - Kraus, Pavard & Promislow 2013 (why large dogs die young)
   - Plassais 2022 (IGF1-AS)
   - Cagan 2022 (somatic mutation rates)
   - Wang 2020 (dog–human epigenetic conversion)
   - Kealy 2002 (caloric restriction)
   - Coleman 2025 (TRIAD protocol)
   - Tyshkovskiy 2026 (universal ageing signatures)
   - Shoshan 2026 (MAMMAL)
4. **People and organisations to know.** See [companies_and_research_groups](../03_canine_bio_ai/companies_and_research_groups.md):
   - the Dog Aging Project / Dog Aging Institute
   - Loyal
   - the Ostrander (NHGRI) and Karlsson (Darwin's Ark) labs
   - the DoGA consortium (Helsinki)
   - vonHoldt (wolves)
   - the Mammalian Methylation Consortium
