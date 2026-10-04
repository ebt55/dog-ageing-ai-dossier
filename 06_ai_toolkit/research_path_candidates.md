# Research Path Candidates: AI × Data Projects on Dog Ageing

> Part of the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 subagent · Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/ai_toolkit_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## TL;DR

**Everything below is a PROPOSAL — none of these projects has been done as described.** Established facts they rest on are cited and tagged (✅ primary source opened, 🟡 secondary/abstract, ❓ unconfirmed); project designs, costings and expected outcomes are my own estimates and should be read as hypotheses, not findings.

Ranking is by *expected insight per unit of cost and risk*, not by ambition. The ordering logic:

- **Tier A (#1–5): pure computation on existing data, 1–2 people, ≤6 months, <$30k compute.** These are gated only by a Dog Aging Project data-use agreement and public downloads. Two of them (#1 ancestry-aware ageing-rate GWAS, #2 canine variant-effect calibration) produce artefacts that every later project needs.
- **Tier B (#6–11): computation that creates a missing public resource** — a dog-referenced constraint model, a canine virtual cell, a canine regulatory sequence model, a cross-species longevity-signature placement of the dog. 6–18 months, small teams, still mostly compute-bound.
- **Tier C (#12–15): computation plus wet-lab validation** — binder/antibody design against canine IGF1R/GHR, in-silico-to-in-vitro geroprotector screening, a canine fibroblast longevity panel. These need a lab and real budget.
- **Tier D (#16–18): interventional and translational** — somatic gene-therapy modulation of the GH/IGF axis in large breeds, a canine clock-endpoint trial design, and a germline item that I argue **should not be pursued** and is included only to document why.

The three facts that make this field unusually tractable: dogs vary **~40-fold in body size and ~2-fold in lifespan within one species** [1][2]; **large dogs die young mainly because they age faster**, not because senescence starts earlier (74-breed mortality-hazard analysis) [3] ✅ [verifier-confirmed verbatim from Kraus 2013: "the driving force behind the trade-off between size and life span is apparently a strong positive relationship between size and aging rate", with no clear size–onset correlation]; and a **human–dog dual-species methylation clock with R = 0.97** already exists, giving every canine intervention an immediate human read-out [4] ✅ [verifier-confirmed]. ⚠️ [verifier note] One cross-cutting caveat applies to several proposals below: the dual-species and universal clocks are built on the **HorvathMammalMethylChip40 array** (~36k conserved CpGs), whereas DAP's methylation data are **RRBS**. Scoring DAP samples with those clocks requires an explicit CpG-overlap step and will lose coverage — it is not a drop-in operation.

---

## Scoring key

| Field | Meaning |
|---|---|
| **Feasibility** | rough team size, wall-clock, and compute/assay cost. Compute costs assume cloud GPU at commodity rates; I have **not** verified current pricing — treat as order-of-magnitude ❓ |
| **Risk** | the specific way the project fails |
| **Validation** | what would make the result believable |
| **Collaborators** | organisations with the data, animals or assays. Named because they are the publishing groups on the cited work; **no contact or willingness has been verified** ❓ |

---

# TIER A — low-cost computational, high information yield

## #1 — Ancestry-aware canine ageing-rate GWAS on an epigenetic/multi-omic clock residual

**Question.** Which canine genetic variants predict *ageing rate* (clock residual), independent of breed population structure and independent of body size?

**Why it matters.** Body size explains much of canine lifespan variance, and the DAP clock already shows the largest size class is ~0.37 epigenetic years older per chronological year, with each residual epigenetic year carrying ~34% higher mortality hazard 🟡 [5]. But nobody has separated "size genes" from "ageing-rate genes". If a variant moves clock residual *within* a size stratum, it is a far better intervention target than *IGF1*.

**Data.** DAP Precision Cohort RRBS methylation + clinical labs + metabolome (976 dogs) [6] ✅; DAP imputed genotypes (7,627 dogs) [7] 🟡; the 864-dog clock cohort [5] 🟡; Dog10K for imputation/annotation [8] ✅; GRLS as a single-breed replication set (3,224 genotyped goldens, CC-BY-SA) [9] ✅; VetCompass life tables for population-level survival priors [10] ✅.

**Tools.** EnsembleAge / universal pan-mammalian clocks for clock scoring [11][4]; GCTA/SAIGE-style mixed models with a genomic relatedness matrix; the Bian et al. interpretable breed-ancestry decomposition (91.7% accuracy, ~150 informative SNPs) as an ancestry covariate 🟡 [12]; canine gene-constraint scores for prioritisation ✅ [13]; ESM-2 for coding-variant effect ✅ [14].

**Method outline.**
1. Score every methylation sample with (a) a dog clock, (b) the human–dog dual clock, (c) the universal pan-mammalian clock; keep all three residuals.
2. Build the ancestry design: global ancestry proportions + a GRM; stratify by the five DAP body-size classes.
3. Run clock-residual GWAS within and across strata, with size as both covariate and interaction term.
4. Annotate hits with canine constraint, Zoonomia phyloP (already attached to Dog10K SNVs ✅ [8]), DoGA promoters [15], EpiC Dog chromatin states [16], BarkBase ATAC [17].
5. Replicate in GRLS (single breed ⇒ no breed structure) and test association with survival in VetCompass-derived breed priors.

**Expected output.** The first canine *ageing-rate* GWAS; a short list of size-independent ageing-rate loci; a reusable ancestry-aware clock-residual pipeline.

**Feasibility.** 1–2 people (one statistical geneticist, one epigenomics analyst), 4–6 months, <$10k compute. Main cost is the DAP application and Terra egress/compute.

**Risks.** (a) **Power** — 864 dogs with methylation is small for GWAS; expect few genome-wide-significant hits, so pre-register a gene-set/polygenic-score analysis as primary. (b) **The Serres Armero warning**: canine biological-age clocks are heavily confounded by breed population structure and biological-age signals "do not colocalize between datasets" ✅ [18] — this project must treat that as the central methodological problem, not a footnote. (c) Methylation platform heterogeneity across DAP/Horvath/Wang datasets.

**Validation.** Replication in GRLS; concordance of clock residual with prospective mortality in DAP follow-up; agreement across all three clocks.

**Collaborators.** Dog Aging Project (Promislow, Creevy, Snyder-Mackler, Akey); Ostrander lab (NHGRI); Horvath/Pellegrini (clocks); Morris Animal Foundation (GRLS); RVC VetCompass.

**Verifier comment:** the resources exist as described, but step 1 of the method is not executable as written. DAP methylation is **RRBS** while the human–dog dual clock and the universal pan-mammalian clock are **HorvathMammalMethylChip40 array** models — you cannot "score every methylation sample" with all three without first mapping RRBS coverage onto the array's ~36k conserved CpGs and accepting substantial dropout. Budget for that step, or restrict the array-based clocks to the Horvath/Thompson cohorts and use a DAP-native clock for DAP. Two secondary points: the 864-dog clock is an **unpublished preprint whose mortality result rests on 49 deaths**, so it should be treated as the motivation rather than a validated anchor; and GRLS replication relies on **genotypes only** (the open AWS release is an Axiom array, with no methylation), so "replicate in GRLS" means replicating the genetic association, not the clock.

---

## #2 — A calibrated canine variant-effect predictor (and a "popEVE for dogs")

**Question.** Can we score canine missense and non-coding variants for functional damage with known accuracy, instead of borrowing human scores?

**Why it matters.** Right now the field borrows human tools, and the one published test of that transfer is damning: mapping OMIA animal variants into mock human variants and scoring with AlphaMissense/ESM-1b/PolyPhen-2 gave **sensitivity 0.77–0.90 but specificity 0.20–0.46 and auROC 0.55–0.61** ✅ [19]. AlphaMissense releases no weights and human-only scores ✅ [20]. Every downstream project (#1, #4, #5, #12) needs a trustworthy canine variant score.

**Data.** Dog10K variants (>48M; SnpEff + phyloP annotated) ✅ [8]; OMIA labels (597 dog likely-causal variants; 347 characterised single-gene diseases) ✅ [21]; canine gene constraint from >2,000 dogs ✅ [13]; UniProt dog proteome UP000805418 (43,615 proteins, but only 857 reviewed — isoform curation required) ✅ [22]; deleterious-load datasets (Cavalier KCS MMVD; breed morbidity) [23][24].

**Tools.** ESM-2 / ESM-1v / ESM C run **natively on canine sequence** ✅ [14][25][26]; EVE retrained per protein family ✅ [27]; GEMME as a fast baseline ❓ licence [28]; Evo 2 for non-coding/synonymous positions (**dog is in its training corpus** ✅ [29]); popEVE's architecture with **Dog10K allele presence substituted for the UK Biobank cohort term** ✅ [30].

**Method outline.** Curate canonical canine isoforms → compute native PLM scores → fit a popEVE-style Gaussian-process model conditioning cross-species scores on observed-in-Dog10K status → benchmark against OMIA positives and matched high-frequency negatives → publish genome-wide precomputed canine scores.

**Expected output.** A public canine variant-effect score set with ROC curves on canine ground truth; the first canine proteome-wide pathogenicity spectrum.

**Feasibility.** 1–2 ML/comp-bio people, 3–6 months; GPU for PLM inference over ~21k proteins ≈ a few hundred GPU-hours, <$5k ❓.

**Risks.** OMIA "non-deleterious" labels include functional-but-benign variants (coat colour), which is exactly what destroyed specificity in [19]; negative-set construction is the whole ballgame. Isoform ambiguity in TrEMBL-dominated canine entries.

**Validation.** Held-out OMIA variants; concordance with canine constraint [13]; prospective: predict which breed-enriched variants in ageing genes associate with clock residual in #1.

**Collaborators.** Marks lab (popEVE/EVE); Song lab (GPN); OMIA curators (Tammen, Nicholas, Univ. Sydney); Ostrander lab (constraint).

**Verifier comment:** scientifically the soundest item in the list, and every input checks out (OMIA's 597 dog causal variants and 347 characterised single-gene diseases were confirmed on the live site; UP000805418's 43,615 proteins / 857 reviewed confirmed via the API; Dog10K's annotations confirmed). Three practical corrections. (a) **popEVE is GPL-3.0**, so a canine derivative inherits copyleft — fine for a public resource, a blocker for closed use. (b) **GEMME should not be in the critical path**: its repository 404s and no current distribution point could be found by either agent. (c) The positives are weaker than they look: OMIA's dog variants are overwhelmingly **Mendelian disease** variants, almost none ageing-related, so the benchmark measures general pathogenicity transfer rather than ageing-variant performance. Say so explicitly in the paper.

---

## #3 — Place the dog inside the pan-mammalian longevity-signature framework

**Question.** Where do dogs — and short- vs long-lived breeds — sit on the conserved mammalian ageing/longevity transcriptomic axes, and which axis does breed size move?

**Why it matters.** Tyshkovskiy et al. 2026 built universal ageing/mortality signatures and **module-specific clocks** (inflammation, interferon, mitochondrial, chromatin, ECM) from >11,000 transcriptomes across **four** mammals — mouse, rat, macaque, human ✅ [31]. **Dog is absent.** Dogs are the one species where lifespan varies 2-fold *within* the species, so adding them tests whether the "universal" modules really are universal, and tells us which module large-breed ageing accelerates.

**Data.** DoGA promoter/gene expression across 100 tissues from 9 dogs + 12 embryos ✅ [15]; Dog10K DB's 30 blood RNA-seq samples across ages ✅ [32]; the 19-dog multi-omic ageing dataset (GSA CRA025543) ✅ [33]; beagle young-vs-senior bulk RNA-seq (39 dogs) + ~318k PBMC transcriptomes ✅ [34]; DAP metabolome/clinical labs for cross-modality anchoring ✅ [6][35].

**Tools.** Signature projection from [31][36][37]; module clocks; GENtervention [36]; orthologue mapping via Ensembl/TOGA [38]; UCE for cross-species cell-level embedding ✅ [39].

**Method outline.** Map dog↔human/mouse orthologues → project canine ageing contrasts onto the universal ageing and mortality signatures → compute module-specific clock scores per dog → regress module scores on breed size and on clock residual from #1 → test whether *IGF1*-axis down-regulation (a shared longevity feature across 41 species ✅ [37]) tracks small-breed status.

**Expected output.** A quantitative answer to "which hallmark module does large-breed accelerated ageing live in?" — the single most actionable question for choosing an intervention class.

**Feasibility.** 1 person, 3–4 months, negligible compute.

**Risks.** Canine transcriptomic ageing data are thin and tissue-skewed (mostly blood); orthologue mapping loses genes; batch effects across studies dominate. Mitigate with within-study contrasts only.

**Validation.** Internal: module scores should recover known size↔lifespan relationships [1][3]. External: the same modules should predict mortality in DAP follow-up.

**Collaborators.** Gladyshev lab (Harvard); DoGA consortium (Lohi, Hytönen, Helsinki); Dog Aging Project.

**Verifier comment:** the premise is solid — Tyshkovskiy et al. 2026 is real and dog is genuinely absent from its four species (mouse, rat, macaque, human), confirmed verbatim. But the **data section overstates what is available as an ageing contrast**. DoGA's atlas covers 100 tissues from **9 dogs plus 12 embryos that are not age-stratified**, so it supplies tissue breadth and promoter annotation, not an age signal; the Dog10K DB age series is **30 blood samples spanning 1–9 years**; and the beagle and 19-dog datasets are young-vs-old blood/MSC comparisons. Realistically this project rests on **blood, with n in the tens**, and should be framed as a feasibility/placement study rather than a cross-tissue test of module universality. The "regress module scores on clock residual from #1" step also inherits #1's array-vs-RRBS problem.

---

## #4 — Score breed-specific variants in GH/IGF and ageing genes across 300+ breeds

**Question.** Do short-lived breeds carry a measurable excess of damaging variants in ageing-relevant pathways, beyond the known body-size loci?

**Why it matters.** *IGF1* alone explains ~15% of between-breed body-size variance, and the causal variant is in the **IGF1-AS antisense lncRNA** ✅ [40]; *LCORL* has two independent size variants ✅ [13]. But breed lifespan differences (French Bulldog 4.53 y vs Jack Russell 12.72 y ✅ [10]) are presumably not all size. Breed formation also accumulated deleterious variation [23][24].

**Data.** Dog10K (1,611 breed dogs, 321 breeds; 309 village dogs; 63 wolves; 4 coyotes) ✅ [8]; canine constraint [13]; breed life-expectancy tables from VetCompass (155 breeds, 584,734 dogs) ✅ [10][41]; Wisdom Panel allele frequencies from >1M dogs (published supplements) ✅ [42].

**Tools.** The #2 canine variant scorer; Evo 2 for non-coding scoring including IGF1-AS ✅ [29]; Zoonomia phyloP [43]; gene sets from GenAge/CellAge/LongevityMap [44] and from [31][45].

**Method outline.** Build per-breed damaging-variant burdens in curated pathway sets (GH/IGF, mTOR, DNA repair, senescence, inflammation, autophagy) → regress breed burden on breed life expectancy with body size, inbreeding (F) and phylogenetic clade as covariates → bootstrap over gene-set definitions → report which pathway burdens survive size adjustment.

**Expected output.** A breed-level "ageing-pathway genetic load" table, and a direct test of whether short lifespan is a size epiphenomenon or has independent pathway signal.

**Feasibility.** 1 person, 2–4 months, <$5k.

**Risks.** Breed-level analyses have n = ~150–300 breeds, strong phylogenetic autocorrelation, and lifespan estimates with heterogeneous ascertainment; results will be suggestive, not causal. Village dogs and wolves are essential outgroups.

**Validation.** Within-breed individual-level test in DAP/GRLS (does burden predict clock residual or survival?).

**Collaborators.** Ostrander lab; Dog10K consortium (Meadows, Kidd, Wang, Lindblad-Toh); RVC; Dogs Trust (McMillan/Casey longevity dataset).

**Verifier comment:** the design is reasonable and the Dog10K/VetCompass/constraint inputs are all confirmed, but one listed data source does not do what the proposal needs. **Wisdom Panel's published supplements cover allele frequencies for 250 pre-selected Mendelian disease variants only** — not genome-wide or pathway-wide variation — so they cannot contribute to a "damaging-variant burden in GH/IGF, mTOR, DNA-repair, senescence, inflammation, autophagy" calculation. Use them for the #17 selection-informatics work instead, and build the burdens from Dog10K alone. Also note that breed life expectancy from VetCompass covers **18 breeds in the life tables** and 155 breeds in McMillan, which sets the real sample size for the regression nearer 150 than 300.

---

## #5 — Cross-species comparative genomics: canids vs long-lived mammals

**Question.** Which longevity-associated genes show *canid-specific* evolutionary signatures, and did domestication/breed formation relax constraint on them?

**Why it matters.** RERconverge-style analysis found cell-cycle, DNA-repair, cell-death, **IGF1-pathway** and immunity genes under increased constraint in large/long-lived mammals ✅ [45]; Zoonomia gives 240-species alignments and 101M constrained bases, 80% non-coding ✅ [43]. Nobody has asked the canid-specific version of this question with modern data, including the newly available canid assemblies (grey fox, Tibetan fox, maned wolf, raccoon dog, African wild dog, bat-eared fox — all present in the OpenGenome2 species list I inspected ✅ [29]).

**Data.** Zoonomia 240-way Cactus alignment + phyloP + TOGA orthologs ✅ [43][46]; AnAge maximum-longevity records (4,671 entries; dog 27 y captive) ✅ [47][48]; canid assemblies from NCBI; wolf mCanLor1.2 🟡 [49]; Dog10K within-species polymorphism ✅ [8].

**Tools.** RERconverge [45]; PhyloAcc-style rate-shift tests; Evo 2 likelihoods as a sequence-constraint proxy ✅ [29]; a dog-referenced **GPN-Star** (see #7) for genome-wide constraint.

**Method outline.** Assemble a canid-focused subtree with longevity/body-mass traits from AnAge → run rate–trait association for absolute and relative (size-adjusted) longevity → test for constraint relaxation in dogs vs wolves using within-species polymorphism → intersect with the ageing modules from #3.

**Expected output.** A canid longevity-gene candidate set with explicit distinction between "long-lived-mammal genes" and "canid-specific" ones; a measure of how much breed formation relaxed constraint on ageing genes.

**Feasibility.** 1 person, 4–6 months; alignment handling is the main cost (Zoonomia files are large ✅ [46]); <$10k.

**Risks.** AnAge longevity records for wild canids are sparse and quality-flagged; "relative longevity" is sensitive to body-mass estimates; phylogenetic comparative methods over ~15 canid species have low power.

**Validation.** Convergence with #3's module analysis and #4's burden analysis; functional follow-up in canine fibroblasts (#14).

**Collaborators.** Chikina/Clark labs (RERconverge); Zoonomia/Broad (Karlsson, Lindblad-Toh, Genereux); de Magalhães lab (HAGR).

**Verifier comment:** the canid assemblies named really are in the OpenGenome2 species list — I re-grepped the metadata file and found *Urocyon cinereoargenteus*, *Vulpes ferrilata*, *Chrysocyon brachyurus*, *Nyctereutes procyonoides*, *Lycaon pictus* and *Otocyon megalotis* ✅. Two cautions. (a) **Presence in a language-model corpus is not fitness for comparative genomics**: three of those six (*Lycaon*, *Otocyon*, *Nyctereutes*) are **scaffold-level**, which degrades TOGA orthology and alignment-based rate tests. Check assembly level per species before committing. (b) AnAge's wild-canid longevity records are sparse and quality-flagged, as the proposal says — and the dog's own AnAge maximum (27 y) is an outlier record, so "relative longevity" for *Canis familiaris* is unusually sensitive to which mass and maximum you use.

---

# TIER B — build the missing public resources

## #6 — A canine virtual cell: fine-tune a single-cell foundation model on dog data

**Question.** Can a cross-species cell foundation model represent canine cell states well enough to do in-silico ageing perturbations?

**Why it matters.** Geneformer and scGPT are human-only [50][51]; **TranscriptFormer ships 12 trained species and 24 embedding sets, with no dog**, but documents generating ESM-2 protein embeddings for new species ✅ [52]; **UCE explicitly embeds species it never saw** ✅ [39]. Dog is also **absent from the CELLxGENE Census** ✅ [53]. Building the canine adapter is a tractable, obviously-missing artefact.

**Data (all canine single-cell found, ~600k cells total, blood-dominated).** ~318,000 beagle PBMC transcriptomes (young vs senior) ✅ [34]; 105,057 hippocampal nuclei ✅ [54]; 74,067 leukocytes ✅ [55]; 68,323 PBMCs (leishmaniosis) 🟡 [56]; 30,040 PBMCs on canFam4 (GSE301630) ✅ [57]; 26,278 lung cells ✅ [58]; 19-dog multi-omic ageing scRNA-seq ✅ [33]; plus ICDC tumour transcriptomes ✅ [59].

**Tools.** ESM-2 to generate canine gene embeddings [14]; TranscriptFormer (MIT) [52]; UCE zero-shot baseline [39]; Geneformer in-silico perturbation after orthologue mapping [50]; Arc State for perturbation response (**non-commercial licence** ✅ [60]).

**Method outline.** Harmonise all canine scRNA-seq to canFam4 (demonstrably better cell recovery than older references ✅ [57]) → generate dog ESM-2 embeddings → evaluate zero-shot cell-type transfer human→dog with UCE and TranscriptFormer → LoRA/adapter fine-tune → in-silico perturb ageing-module genes in canine immune cells and compare against the observed young-vs-senior contrasts.

**Expected output.** A public canine cell-embedding resource and a benchmarked answer to "does a virtual cell help in dog?".

**Feasibility.** 2 people (one ML, one single-cell), 6–9 months, $10–30k GPU ❓.

**Risks.** **This is the proposal most likely to disappoint.** Two 2025 benchmarks found cell FMs fail to beat simple baselines for perturbation prediction ✅ [61] and can be beaten by simpler methods zero-shot ✅ [62]; a 2026 benchmark found logistic regression matched or beat frozen scGPT pipelines 🟡 [63]. Pre-commit to linear baselines and report them. Also: <1M canine cells, overwhelmingly blood, so solid-tissue generalisation will be weak.

**Validation.** Held-out canine datasets; cell-type label transfer accuracy vs marker-based annotation; recovery of the known age-associated shifts (naive lymphocyte loss, myeloid/Th1 expansion ✅ [34]).

**Collaborators.** CZI (TranscriptFormer / Virtual Cells Platform); Arc Institute; Colorado State (Dow/Ammons); Hokkaido/Seoul groups publishing canine atlases.

**Verifier comment:** the tooling claims are accurate (TranscriptFormer is MIT with 12 trained species and no dog; its "New Species" ESM-2 route is documented; UCE is MIT; State's model licence is non-commercial), the cell arithmetic sums correctly to ~621k, and the three sceptical benchmarks are real. One data item is wrong: **ICDC contains no single-cell data** — its experimental strategies are bulk RNA-seq, WGS, WXS, genotyping array and DNA methylation, so "plus ICDC tumour transcriptomes ✅" should be dropped from the single-cell inventory (it is still useful as bulk reference). Two additions: the **LeishDog atlas is now published in *iScience*** (no longer a preprint), and State's non-commercial licence plus TranscriptFormer's MIT licence mean the resulting artefact's licence is set by whichever base model you fine-tune — decide that before training, not after.

---

## #7 — A dog-referenced genome-wide constraint and regulatory model

**Question.** Can we produce canine equivalents of human genome-wide constraint and regulatory-effect scores?

**Why it matters.** Canine ageing's best-characterised causal variant is **non-coding** (IGF1-AS ✅ [40]), yet the only frontier regulatory models are human/mouse: AlphaGenome is human+mouse with a non-commercial API and no weights ✅ [64][65]; Enformer/Borzoi are human/mouse [66][67]. **GPN-Star has already been trained for five non-human organisms** ✅ [68], so the recipe exists. And dog has the track data: DoGA (>100,000 promoter candidates on CanFam4, >45,000 reproducible ✅ [15]), BarkBase (ATAC+RNA, 27 tissues ✅ [17]), EpiC Dog (5 histone marks + methylome, 11 tissues ✅ [16]).

**Method outline.** (a) Train **GPN-Star with dog as reference** on the Zoonomia 240-way alignment → genome-wide canine constraint. (b) Train a **canine Borzoi** on DoGA/BarkBase/EpiC Dog tracks → predict canine expression/chromatin from sequence and score regulatory variants. (c) Benchmark both against Evo 2 zero-shot likelihoods (dog is in-distribution ✅ [29]) using known canine causal variants (IGF1-AS, LCORL, OMIA regulatory variants).

**Expected output.** Two public canine models + precomputed score tracks. This is the single most reusable artefact in the whole list.

**Feasibility.** 2 people, 9–18 months; the alignment-based model is cheap by modern standards (GPN-MSA "takes only a few hours to train" ✅ [69]), the Borzoi-style model is the expensive part — $30–100k GPU ❓.

**Risks.** Canine functional-track diversity is far below human ENCODE; a canine Borzoi may simply be under-trained. Benchmark honestly against Evo 2 zero-shot, which may win.

**Validation.** Held-out canine causal variants; enrichment of canine GWAS/clock-residual hits (#1) in high-constraint regions; MPRA or luciferase validation of top predicted regulatory variants.

**Collaborators.** Song lab (GPN); Calico (Borzoi); DoGA consortium; Broad/Zoonomia; Arc Institute (Evo 2).

**Verifier comment:** the most reusable item in the list, and the enabling facts hold (GPN-Star is published in *Nature* with five non-human organisms trained and checkpoints on Hugging Face; GPN/Borzoi are MIT/Apache-2.0; the DoGA, BarkBase and EpiC Dog track counts are confirmed). Three refinements. (a) GPN-Star's non-human models were each trained on a **bespoke whole-genome alignment of 18–135 species**, not on one fixed 240-way, so a dog-referenced build needs its own alignment subset — add that to the 9–18-month estimate. (b) The Zoonomia alignment is **reference-free Cactus**, so projecting it onto dog coordinates is a real engineering step, not a download. (c) The Evo 2 benchmark baseline should now also include **NTv3**, which saw the same OpenGenome2 corpus (gated weights). The "Evo 2 may win" caution is well placed and should stay.

---

## #8 — Transposon and chromatin ageing in dogs at scale

**Question.** Does transposable-element de-repression drive canine ageing differences, and does it track breed size and mortality?

**Why it matters.** A DAP preprint reports **transposon methylation patterning ageing differences across a diverse dog cohort** 🟡 [70]; canine cognitive dysfunction work found **TE transcripts increase with CCD in brain and in plasma extracellular vesicles** 🟡 [71]; and ATAC-based clocks already work in dogs (R² = 0.26) ✅ [72]. TE de-repression is a mechanistic hypothesis with a measurable, non-invasive read-out (plasma EV RNA).

**Data.** DAP RRBS + the transposon preprint cohort 🟡 [70][6]; Jin et al. ATAC/DNAm in 71 dogs ✅ [72]; canine WGBS at 70× in 19 dogs (GSE252908) ✅ [73]; canine brain bank (55 brains, lipofuscin increases strongly with age) 🟡 [74]; repeat annotation from the near-T2T Beagle assembly (repeats 34.90% of genome) 🟡 [75] and the gapless Jindo assembly 🟡 [76].

**Tools.** TE-aware methylation/expression quantification; Evo 2 for repeat-context sequence modelling [29]; module clocks from [31].

**Expected output.** A canine TE-ageing index; test of association with size, clock residual and mortality; a candidate plasma-EV biomarker.

**Feasibility.** 1–2 people, 6 months; modest compute. Requires good repeat annotation — use canFam4 plus the new T2T-grade assemblies.

**Risks.** Short-read RRBS is poor for repeats; mappability artefacts can manufacture age effects. The new near-T2T assemblies mitigate but do not solve this.

**Validation.** Long-read (ONT) methylation in a subset; plasma-EV TE RNA vs brain TE RNA concordance; independent cohort.

**Collaborators.** DAP (Snyder-Mackler, McCoy, Mariner); Apex Neuroscience (canine brain bank); Ideker lab.

**Verifier comment:** sound hypothesis with an honest risk section, and the transposon preprint is real (Mariner et al., bioRxiv v5, Jan 2025: the same 864-dog DAP cohort; 66% of age-associated regions lose methylation; **LINE1 most frequently hypomethylated with age, 40% of all LINE1 regions at FDR < 0.05**). One input must be dropped or re-sourced: the **near-T2T Beagle assembly has no literature record at all** — Europe PMC returns nothing for it and neither agent opened the figshare entry — so its "repeats 34.90%" figure cannot be used for repeat annotation. Use CanFam4 plus the **Jindo TTAGGA** assembly (which is verified) instead. Note also that #8 and #1 draw on the same 864 samples, so their results are not independent.

---

## #9 — A canine multi-omic composite clock with mortality as the endpoint

**Question.** Can a model combining methylation, metabolome, clinical labs, microbiome and immunophenotype beat any single-modality clock at predicting *death*, not age?

**Why it matters.** The DAP Precision Cohort is uniquely multi-modal (RRBS + LC-MS metabolome + shotgun metagenomics + flow cytometry + CBC/chem/UA on the same 976 dogs ✅ [6]), and each modality has independently shown mortality signal: metabolites that predict human mortality also predict dog mortality ✅ [35]; ptmAAs are robust age markers with kidney function as mediator ✅ [77]; globulin and potassium predict mortality and are elevated in short-lived breeds 🟡 [7]; the microbiome supports a population-level age model ✅ [78]; epigenetic residual predicts mortality 🟡 [5].

**Tools.** Multi-modal integration (MOFA+/DIABLO, or MAMMAL-style cross-modal encoders [79]); survival models (Cox with time-varying covariates); module clocks [31]; phenotype-driven parallel embedding for microbiome multi-omics (a DAP-adjacent method) 🟡 [80].

**Expected output.** A canine "biological age" with validated mortality prediction — the measurement instrument that every future canine intervention trial needs.

**Feasibility.** 1–2 people, 6–9 months, low compute; gated on DAP DUA and on accruing enough deaths.

**Risks.** **Event count.** With ~976 dogs at mean age 3.9 y ✅ [6], deaths accrue slowly; the project may be underpowered until later releases. Also the Serres Armero confounding warning applies with full force ✅ [18].

**Validation.** Out-of-sample discrimination (C-index) on later DAP releases; replication of the metabolite-mortality correlation with human cohorts ✅ [35]; GRLS as an external single-breed cohort.

**Collaborators.** DAP; Borenstein lab (microbiome); Raftery (metabolomics); Gladyshev lab (module clocks).

**Verifier comment:** every modality claim checks out (Prescott 2025's assay list verbatim; Harrison 2026's 937-dog metabolite–mortality correlation; Harrison 2025's ptmAAs; Bamberger 2026's >900-dog microbiome age model). **The event-count worry is now partly answerable**: Sohrab et al. 2026 report **957 dogs with three years of longitudinal follow-up, during which 11% died** — i.e. roughly **105 deaths** are already accrued in the Precision Cohort, not a handful. That is enough for a C-index with wide intervals and for a pre-registered single composite score, but not for modality-by-modality model selection; plan the analysis around ~100 events and say so in the power section rather than leaving it open. The Serres Armero confounding warning applies in full, as stated.

---

## #10 — A canine ageing knowledge graph with LLM-agent curation

**Question.** Can an agent-curated knowledge graph over canine ageing data surface non-obvious target hypotheses that a human literature review misses?

**Why it matters.** The canine evidence is scattered across DAP papers, Dog10K, OMIA, VetCompass epidemiology, ICDC oncology and comparative-genomics work, with no integration layer. Agent systems now exist that do exactly this kind of synthesis: Biomni (Apache-2.0) [81], Robin (which autonomously proposed ripasudil for dry AMD) [82], Kosmos (~42k lines of code and ~1,500 papers per run; **independent scientists judged 79.4% of its report statements accurate**) [83], and Google's co-scientist (AML repurposing candidates validated in vitro) [84].

**Method outline.** Define a schema (gene, variant, breed, tissue, phenotype, intervention, evidence-type) → agent-populate from OMIA, Dog10K, DAP publications, VetCompass studies, ICDC, HAGR → human verification pass on a sampled subset to measure precision → run network-medicine prioritisation à la the pAGE framework (2,358 longevity genes × 6,442 compounds mapped to hallmarks) ✅ [85].

**Expected output.** A public canine ageing knowledge graph + a ranked hypothesis list with provenance.

**Feasibility.** 1–2 people, 4–6 months, LLM API cost $5–20k ❓.

**Risks.** **Fabrication.** Kosmos's own reported ~20% inaccurate-statement rate [83] means an unverified graph is actively harmful. Build the human verification sampling protocol *first* and report precision per edge type.

**Validation.** Human expert audit of stratified edge samples; blind comparison against expert-curated subsets; prospective: do graph-prioritised targets show up in #1/#3/#4?

**Collaborators.** FutureHouse; Stanford (Biomni); de Magalhães lab (HAGR curation standards); Insilico Medicine (PandaOmics benchmarking) [86].

**Verifier comment:** the agent inventory is accurate but needs two tooling corrections before costing: **Robin is Apache-2.0 and public, whereas Kosmos has no public repository** (`Future-House/kosmos` 404s), so the Kosmos-style long-horizon runs are a product dependency, not something you can self-host; and its **79.4% accuracy figure is an arXiv self-report** that nobody has reproduced, which strengthens rather than weakens the proposal's insistence on a verification protocol. Of the planned source databases, **OMIA, Dog10K and HAGR are machine-readable, but VetCompass is not** (the site blocks automated access and its scale figures could not be verified), so VetCompass evidence will have to come from individual papers.

---

## #11 — A dog↔human ageing translation layer for trial design

**Question.** Given a canine intervention effect, what is the predicted human-equivalent effect, and vice versa?

**Why it matters.** This is the entire translational premise of canine geroscience. The pieces exist but are not assembled: the Wang dog→human age function `human_age = 16·ln(dog_age) + 31` ✅ [87]; human–dog dual-species clocks at R = 0.97 ✅ [4]; universal pan-mammalian clocks across 185 species ✅ [88]; shared dog/human mortality metabolites ✅ [35]; blood traits mapping to orthologous loci in both species 🟡 [7]; conserved CD8⁺ T-cell senescence markers ✅ [33]; and TRIAD as the first rigorous pharmacological anti-ageing trial with lifespan/healthspan endpoints outside the lab in any species ✅ [89].

**Method outline.** Build a modality-by-modality mapping (epigenetic, metabolomic, transcriptomic-module, clinical) with uncertainty → fit scaling parameters on paired human/dog datasets → express it as a calibrated translation function with prediction intervals → stress-test on rapamycin, where mouse and (soon) dog data both exist.

**Expected output.** A documented, uncertainty-aware translation layer; a power-calculation tool for canine trials expressed in human-equivalent terms.

**Feasibility.** 1 person + a biostatistician, 4–6 months, negligible compute.

**Risks.** Cross-species scaling is identifiable only where paired data exist (mostly blood); the Korean-vs-US epigenetic age acceleration result ✅ [90] shows environment can shift clocks at population scale, so translation constants may not be universal.

**Validation.** Prospective: does the layer correctly predict TRIAD's clock movement from mouse rapamycin data?

**Collaborators.** DAP/TRIAD investigators; Horvath/Raj (clocks); Ideker lab; Gladyshev lab.

**Verifier comment:** all of the component pieces were verified individually (the Wang `16·ln(dog_age) + 31` function, the R = 0.97 dual clocks, the 185-species universal clocks, shared dog/human mortality metabolites in 937 dogs, conserved CD8⁺ senescence markers, the TRIAD quote, and the Korean-vs-US epigenetic-age-acceleration result), so the proposal rests on real foundations. The one structural caution: the epigenetic layer is the only modality with genuinely paired human and dog data on the **same measurement platform** (the mammalian array), and the metabolomic layer is paired only at the level of effect-direction correlation, not matched assays. The "modality-by-modality mapping with uncertainty" should therefore expect very wide intervals outside the epigenetic layer, and the transcriptomic-module mapping inherits #3's thin canine data.

---

# TIER C — computation plus wet lab

## #12 — Design canine IGF-1 / IGF1R / GHR modulators with AF3 + Boltz-2 + BindCraft

**Question.** Can we design protein binders that tune canine GH/IGF signalling, as research reagents and eventual therapeutic leads?

**Why it matters.** The GH/IGF axis is the strongest candidate mechanism for the size↔lifespan trade-off in dogs ✅ [1][40][2], down-regulated *Igf1* is a shared longevity feature across 41 mammal species ✅ [37], and pan-mammalian clock deviations correlate with **mouse somatotropic-axis mutations** ✅ [88]. **Critically, I measured the transferability**: human↔dog identity is **97.4% for IGF1R**, **91.9% for the IGF1 precursor with the mature 70-aa peptide 100% identical**, **82.3% for GHR**, but only **68.4% for GH1** ✅ [91]. So receptor-directed reagents may cross-react from human work, while GH-directed ones must be designed dog-specific.

**Tools.** AF3 (weights non-commercial, from Google ✅ [92]) or Chai-1 (Apache-2.0 weights ✅ [93]) for complexes; **Boltz-2 (MIT, academic *and* commercial) for affinity ranking** ✅ [94]; BindCraft (MIT) ✅ [95]; RFD3/Foundry (BSD-3) ✅ [96]; ProteinMPNN (MIT) ✅ [97]; MAMMAL as a binding-likelihood ranker (it beat AF3 confidence on 5/7 antigens) ✅ [79].

**Method outline.** Curate canonical canine IGF1R/GHR/IGF1 isoforms (note **AlphaFold DB has no dog proteome bulk file and returned 404 for a 1425-aa dog IGF1R entry — fold your own** ✅ [98]) → design minibinders/decoy-receptor scaffolds → filter by Boltz-2 affinity + AF3/Chai interface confidence + MAMMAL score → express top ~50 designs → SPR/BLI against recombinant canine ectodomains → cell-based signalling assays (pAKT/pSTAT5) in canine cells.

**Expected output.** A validated canine IGF1R/GHR modulator toolkit — currently absent from the field — enabling dose-controlled axis modulation experiments that genetics cannot provide.

**Feasibility.** 2–4 people incl. a protein biochemist, 12–18 months; ~$150–400k for synthesis, expression and binding assays ❓.

**Risks.** Binder design success rates, while much improved, are still a numbers game; agonist/antagonist *functional* behaviour is far harder to design than binding; canine cell-line and reagent availability is a real constraint (no canine DepMap; ~990 canine lines in Cellosaurus 🟡 [99]).

**Validation.** Orthogonal binding assays; functional signalling; species cross-reactivity panel; eventually canine primary cells.

**Collaborators.** Baker lab / IPD (RFdiffusion, BindCraft, ProteinMPNN); MIT Jameel/Boltz team; IBM (MAMMAL); Colorado State Flint Animal Cancer Center (canine cells/assays).

**Verifier comment:** the tool licences and the AlphaFold DB gaps are all confirmed as written (AF3 weights non-commercial from Google; Boltz-2 MIT including commercial; Chai-1 Apache-2.0; BindCraft/ProteinMPNN MIT; Foundry BSD-3; MAMMAL beat AF3 confidence on **five of seven** antigens; `A0A8I3RQ77` really does 404; 990 canine Cellosaurus lines). One sequence-hygiene point is important enough to put in the protocol rather than a footnote: the dog IGF1R entry the proposal would fold carries an **unexplained ~60-residue N-terminal extension**, and the human↔dog identity is **97.4% over the precursor but 98.1% over the mature receptor**. Start the construct at the conserved `CGPGIDIRND` motif (dog residue 89) and verify the gene model against RefSeq/cDNA first, or the designs will be built on a probable annotation artefact. Also flag that any AF3 model of the IGF-1:IGF1R complex is substantially **recall** of pre-2021 PDB structures (5U8Q, 6PYH), so interface confidence is not independent evidence.

---

## #13 — In-silico geroprotector screen against canine ageing signatures, then canine-cell validation

**Question.** Which approved or well-characterised compounds reverse canine ageing signatures, and do they do so in canine cells?

**Why it matters.** The signature-reversal paradigm has a track record: Tyshkovskiy et al. predicted and then confirmed KU-0063794 extends mouse lifespan ✅ [100][37]; the pAGE network-medicine framework now scores 6,442 compounds against ageing hallmarks ✅ [85]. Nobody has run this with *canine* signatures, and dogs are the species where a trial can actually read out lifespan ✅ [89].

**Data/tools.** Canine ageing signatures from #3; LINCS L1000 (1.3M profiles) ✅ [101]; Tahoe-100M single-cell drug atlas (50 lines, 379 molecules, 3 doses) 🟡 [102]; Boltz-2 for target-affinity sanity checks ✅ [94]; TxGemma for ADMET/trial-outcome priors (**gated, Health AI Developer Foundations terms** ✅ [103]); MAMMAL for cross-modal scoring ✅ [79]; DrugAge (1,097 compounds) ✅ [44].

**Method outline.** Define canine ageing/mortality signatures (blood, and any solid tissue available) → signature-reversal scoring against L1000/Tahoe → intersect with pAGE hallmark proximity → filter hard on **canine safety and pharmacology** (dogs have species-specific toxicities; veterinary pharmacologist required) → test top ~20 compounds on canine fibroblasts/PBMCs for signature reversal and senescence markers.

**Expected output.** A prioritised, canine-safety-filtered geroprotector list with in-vitro signature-reversal evidence — the natural feeder pipeline for a post-TRIAD trial.

**Feasibility.** 2–3 people incl. a veterinary pharmacologist and a cell biologist, 9–15 months; $80–200k ❓.

**Risks.** L1000/Tahoe are **human cancer cell lines** — compound-induced signatures may not transfer to canine primary cells. Signature reversal is a weak proxy for lifespan. Species-specific toxicity must gate the list early, not late.

**Validation.** Canine primary cell signature reversal; senescence/SASP assays; ideally a short canine biomarker study with clock endpoints before any lifespan trial.

**Collaborators.** Gladyshev lab; Barabási/Loscalzo network-medicine group; DAP/TRIAD team; Insilico Medicine; veterinary pharmacology (Texas A&M, CSU).

**Verifier comment:** the precedent and framework claims hold (KU-0063794 predicted then confirmed to extend mouse lifespan; pAGE maps 2,358 longevity genes and 6,442 compounds; DrugAge exists, though its "1,097 compounds" count could not be reproduced — the live HAGR page says "over 500"). Two corrections to the tool row: **Tahoe-100M is CC0-1.0 from Vevo Therapeutics, not "per Arc terms"**, and its stated composition ("50 lines, 379 molecules, 3 doses") is **not in the dataset card** — re-derive those numbers before building a screen around them. The honest risk statement about human cancer lines is the right one and should drive the design: put the canine primary-cell filter before, not after, the signature-reversal ranking.

---

## #14 — A canid comparative cell panel: fibroblasts across breeds and wild canids

**Question.** Do cells from short-lived (large) breeds show intrinsically faster ageing phenotypes than cells from long-lived (small) breeds and from wolves?

**Why it matters.** The 16-species fibroblast study showed that **cell-intrinsic profiling recaptures species longevity differences** — longer-lived species up-regulate DNA repair and glucose metabolism ✅ [104]. The within-species version (breeds) has never been done, and it is the cleanest way to ask whether canine size↔ageing-rate is cell-intrinsic or systemic. Wolves are the essential outgroup, and the only substantial wolf ageing dataset is a 2017 RRBS clock (62 wolves) ✅ [105].

**Method outline.** Derive primary fibroblasts across ~20 breeds spanning the size range plus wolf/village-dog samples → identical culture conditions → RNA-seq + methylation array (HorvathMammalMethylChip40, enabling direct universal-clock scoring ✅ [88]) + metabolomics + stress-response assays (irradiation, oxidative, replicative) → regress cell phenotypes on breed size and breed life expectancy.

**Expected output.** The first within-species cell-intrinsic ageing panel; a reusable canine cell bank; a direct cell-intrinsic vs systemic verdict.

**Feasibility.** 2–3 people, 18–24 months; $200–500k ❓; needs ethical biopsy sourcing (surgical discard tissue is the realistic route) and IACUC/ethics approval.

**Risks.** Donor age/sex/health confounding; passage effects; sample sourcing across 20 breeds is the hard part. Wolf samples require zoo/wildlife collaboration.

**Validation.** Clock scores on the same cells; concordance with breed-level epidemiology [10][41]; cross-check against #5's comparative-genomics predictions.

**Collaborators.** Gorbunova/Seluanov (comparative cell biology); Horvath/Pellegrini (arrays); vonHoldt (wolves); veterinary teaching hospitals for discard tissue.

**Verifier comment:** the rationale is well founded (Ma et al. 2016's 16-species fibroblast panel is real, as is the 62-wolf 2017 RRBS clock as the only substantial wolf ageing dataset). One feasibility item is understated: the **HorvathMammalMethylChip40 is a custom array distributed through the Mammalian Methylation Consortium / Epigenetic Clock Development Foundation, not an off-the-shelf catalogue product**, so "methylation array enabling direct universal-clock scoring" depends on securing array access and the clock coefficients — make that an explicit prerequisite alongside the biopsy sourcing, because it gates the project's main read-out. The EnsembleAge package (MIT, v0.99.1) does support Mammal40k/Mammal320k scoring once you have data, which is confirmed.

---

## #15 — Canine cognitive-ageing multimodal model (the dementia translation route)

**Question.** Can multimodal data predict canine cognitive decline early enough to be an intervention endpoint?

**Why it matters.** Canine cognitive dysfunction shows Alzheimer's-like transcriptomic changes 🟡 [71]; DAP has built a dedicated AD translational platform with post-mortem protocols ✅ [106] and cognitive test batteries, including spatial-memory assessments showing strong age associations not moderated by body mass 🟡 [107]; CSF neurofilament light increases with age and correlates with cognitive dysfunction 🟡 [108]; and TRIAD already includes cognitive assessments ✅ [109]. A validated cognitive endpoint shortens any canine trial.

**Data/tools.** DAP cognitive batteries + owner-reported CCD + biospecimens ✅ [6][106]; canine brain bank (55 brains, lipofuscin vs age) 🟡 [74]; hippocampal snRNA-seq (105,057 nuclei) ✅ [54]; plasma EV RNA 🟡 [71]; multimodal models; UCE/TranscriptFormer for brain cell-state embedding [39][52].

**Expected output.** A canine cognitive-decline risk model with a molecular (plasma EV / NfL) component, suitable as a trial endpoint.

**Feasibility.** 2 people, 9–12 months computational, longer with new sample collection; $50–150k ❓.

**Risks.** Owner-reported cognitive measures are noisy (and DAP has quantified owner-report vs EMR disagreement ✅ [110]); brain tissue n is small; CCD diagnosis lacks a gold standard.

**Validation.** Post-mortem neuropathology concordance; longitudinal prediction in DAP; replication against TRIAD cognitive data.

**Collaborators.** DAP AD platform (McGrath, MacLean, Darvas); Apex Neuroscience; canine cognition groups (Arizona, Duke).

**Verifier comment:** the resources are real and better than described in one respect — the DAP spatial-memory work covers **6,753 dogs** (*GeroScience* 2026), not a small pilot, and it confirms strong age associations that are **not** moderated by body mass, which is worth noting because it cuts against assuming the size↔ageing-rate effect shows up in cognition. The canine brain bank (n = 55, lipofuscin rising with age in thalamus and hippocampus) and the 105,057-nucleus hippocampal atlas are confirmed. Two caveats to carry into the design: the brain bank is a **preprint with no stated access policy**, so tissue access is an assumption, not a resource; and the plasma-EV TE-RNA component depends on the same unreviewed CCD literature flagged in #8.

---

# TIER D — interventional and translational (highest risk, highest regulatory burden)

## #16 — Design, but do not yet run: a somatic intervention study on the GH/IGF axis in large breeds

**Question (hypothesis).** Would post-developmental, dose-controlled, somatic down-modulation of GH/IGF signalling in large-breed dogs slow ageing-rate biomarkers?

**Why the hypothesis is reasonable.** The size↔ageing-rate relationship is quantitative and large [3]; *IGF1* and its antisense regulator are the dominant size locus [40][1]; pan-mammalian clock deviations correlate with somatotropic-axis mutations in mice [88]; and reduced *Igf1* is a conserved longevity feature across 41 species [37]. There is also precedent for **multiplexed AAV longevity gene therapy in mice** (FGF21, αKlotho, soluble TGFβR2) mitigating four age-related diseases ✅ [111], and the gold-standard precedent that canine gene therapy can work and translate — *RPE65* retinal gene therapy, first shown in dogs ✅ [112].

**Why I am ranking it here and recommending a design-only phase.** Three reasons, in order of seriousness:
1. **Ethics and welfare.** These are companion animals, not laboratory models. Any intervention must come through veterinary clinical-trial governance with owner consent, IACUC/ethics review, a clear benefit case for the individual animal, and independent welfare monitoring — the TRIAD architecture (double-masked, placebo-controlled, multicentre, in owned pets, with a published rationale) is the template to follow ✅ [89].
2. **The biology may not permit it.** The size↔lifespan relationship is established at the *developmental* level; whether *post-developmental* axis modulation changes ageing rate in dogs is unknown. Pharmacological axis modulation in adults could plausibly cause harm (muscle loss, metabolic and immune effects) with no lifespan benefit.
3. **Reversibility.** A durable gene therapy is not titratable or withdrawable. Pharmacological or protein-binder modulation (#12) is the ethically and scientifically correct first step precisely because it is dose-controlled and reversible.

**What should be done now (the actual proposal).** A fully in-silico/in-vitro **design and feasibility dossier**: target-engagement modelling with AF3/Boltz-2 on canine IGF1R/GHR; predicted systemic effects using the module clocks (#3) and the translation layer (#11); dose-response modelling; a formal adverse-outcome pathway analysis; and an explicit go/no-go criterion set that must be met in reversible pharmacological studies (#12, #13) *before* any durable intervention is contemplated.

**Feasibility (design phase only).** 2 people, 6–9 months, low cost. The interventional phase is explicitly **out of scope pending regulatory, ethical and prior-evidence gates**.

**Risks.** Everything above. Also reputational: premature interventional work in companion animals would damage the credibility of canine geroscience broadly.

**Collaborators.** Veterinary clinical-trial networks (TRIAD sites, Comparative Oncology Trials Consortium infrastructure as a governance model ✅ [113]); veterinary ethics committees; gene-therapy groups with canine experience (Penn/Aguirre lineage).

**Verifier comment:** no technical objection — this is correctly scoped as a design-and-feasibility dossier with the interventional phase explicitly out of scope, and the precedents cited are real (Davidsohn et al. 2019 multiplexed AAV in mice; Acland et al. 2001 canine *RPE65*; TRIAD's published rationale). One evidential addition that strengthens the "the biology may not permit it" caution: Sohrab et al. 2026 found that **growth-hormone-related metabolites carried *lower* absolute mortality hazard ratios than other blood traits** and concluded that canine ageing "is multifactorial" — i.e. the newest DAP evidence argues against the GH/IGF axis being the dominant lever in adult dogs, which is a reason to keep this item at design-only.

---

## #17 — Breeding and selection-informatics: reduce ageing-gene load without new breeds

**Question.** Can breed clubs reduce the genetic load that shortens lifespan, using existing selection tools rather than any novel intervention?

**Why it matters.** Breed formation accumulated deleterious variation, with a documented case of a disease variant (MMVD-associated) reaching fixation in Cavalier King Charles Spaniels ✅ [23]; 57% of dogs carry at least one of 250 studied Mendelian disease variants ✅ [42]; and homozygous deleterious load correlates with breed morbidity 🟡 [24]. This is the **lowest-risk, highest-welfare-impact** path in the entire list, and it needs informatics, not biotechnology.

**Method outline.** Combine the #2 canine variant scores, #4 breed burdens, VetCompass breed life expectancy [10][41], and commercial-panel allele frequencies [42] → compute per-breed, per-variant "lifespan load" with uncertainty → build optimal-contribution-selection recommendations that reduce load while preserving diversity → deliver as a tool for breed clubs and kennel clubs.

**Expected output.** Breed-specific, evidence-ranked selection guidance with projected life-expectancy gains.

**Feasibility.** 1–2 people + a quantitative geneticist, 6–12 months, low compute.

**Risks.** Social, not technical: breed-standard politics, resistance from clubs, and the risk of misuse to justify further narrowing of gene pools. Requires careful framing around diversity preservation and welfare.

**Validation.** Retrospective: do historical load changes track breed life-expectancy changes? Prospective: monitor cohorts in VetCompass.

**Collaborators.** Kennel Club / Dogs Trust (McMillan, Casey, Upjohn); RVC VetCompass; Wisdom Panel/Embark (frequency data); International Partnership for Dogs.

**Verifier comment:** no material problem, and this is the one proposal where the **Wisdom Panel data are used appropriately** — Donner et al. 2023 screened 1,054,293 dogs (from a 3.5-million-dog cohort) for exactly the 250 Mendelian disease variants that selection decisions turn on, with 57% carrying at least one and full penetrance evidenced for 10 ✅ (all confirmed verbatim), plus the Cavalier King Charles Spaniel MMVD fixation case. The honest limitation to state up front is that "lifespan load" will be built mostly from **disease-variant** burden, which is not the same quantity as ageing-rate load — the link to life expectancy is through specific early-onset disease, not through ageing biology.

---

## #18 — Germline modification of ageing genes in dogs — **documented as NOT recommended**

I am including this item only because the brief asked for the ambitious end of the spectrum, and because the right output is a clear argument against rather than a protocol.

**Position: this should not be pursued, and I am not outlining how to do it.**

**Reasons.**
1. **No benefit to any existing animal.** Germline modification cannot help a living dog; it creates animals for a hypothesis. Companion-animal ethics does not support that trade.
2. **Welfare risk is unbounded and heritable.** Off-target and pleiotropic effects would be transmitted. The GH/IGF axis is developmentally pleiotropic — the very reason it governs body size means modifying it affects skeletal, metabolic, immune and neurological development simultaneously.
3. **The scientific question does not require it.** Natural canine genetic variation already spans a ~40-fold size range and ~2-fold lifespan range [1][2]; breeds are a natural experiment that answers most germline questions observationally, which is exactly what proposals #1–#5 exploit.
4. **Regulatory and social reality.** Gene-edited dogs have been reported in the literature ✅ [114], and the field's reaction illustrates the problem: it generated controversy without generating ageing insight.
5. **Better alternatives exist at every level**: reversible pharmacology (#13), designed protein modulators (#12), selection informatics (#17), and cell-based mechanism work (#14).

**What to do instead.** Fund the Tier A/B computational work, which is cheap, ethically clean, and generates the evidence that would be needed to even evaluate any future interventional claim.

**Verifier comment:** I checked this item specifically for the thing it should not contain, and it is clean. **#18 is handled purely as an ethics-flagged argument against, with no technical protocol** — no target design, no editing strategy, no delivery, no embryo or germline methodology, and an explicit statement that the author is "not outlining how to do it". The supporting citation is accurate: Zou et al. 2015 (*J Mol Cell Biol* 7(6):580–583) did generate gene-edited dogs via CRISPR/Cas9 ✅. The reasoning on developmental pleiotropy in the GH/IGF axis is also consistent with the rest of the dossier. No change requested.

---

## Summary ranking table

| # | Project | Tier | Team | Time | Cost ❓ | Primary gate |
|---|---|---|---|---|---|---|
| 1 | Ancestry-aware ageing-rate GWAS on clock residual | A | 1–2 | 4–6 mo | <$10k | DAP DUA |
| 2 | Calibrated canine variant-effect predictor / "popEVE for dogs" | A | 1–2 | 3–6 mo | <$5k | none (public data) |
| 3 | Place dog in pan-mammalian longevity signatures | A | 1 | 3–4 mo | ~$0 | none |
| 4 | Breed-level ageing-pathway genetic load | A | 1 | 2–4 mo | <$5k | none |
| 5 | Canid vs long-lived mammal comparative genomics | A | 1 | 4–6 mo | <$10k | Zoonomia downloads |
| 6 | Canine virtual cell (fine-tune cell FM) | B | 2 | 6–9 mo | $10–30k | data harmonisation |
| 7 | Dog-referenced constraint + canine Borzoi | B | 2 | 9–18 mo | $30–100k | GPU budget |
| 8 | Transposon/chromatin ageing in dogs | B | 1–2 | 6 mo | <$20k | DAP DUA |
| 9 | Multi-omic composite clock with mortality endpoint | B | 1–2 | 6–9 mo | <$20k | DAP DUA + death accrual |
| 10 | Agent-curated canine ageing knowledge graph | B | 1–2 | 4–6 mo | $5–20k | verification protocol |
| 11 | Dog↔human ageing translation layer | B | 2 | 4–6 mo | ~$0 | paired data access |
| 12 | Canine IGF1R/GHR binder design + validation | C | 2–4 | 12–18 mo | $150–400k | protein lab |
| 13 | In-silico geroprotector screen + canine cells | C | 2–3 | 9–15 mo | $80–200k | vet pharmacology |
| 14 | Canid comparative fibroblast panel | C | 2–3 | 18–24 mo | $200–500k | ethical sample sourcing |
| 15 | Canine cognitive-ageing multimodal model | C | 2 | 9–12 mo | $50–150k | DAP DUA |
| 16 | GH/IGF somatic intervention — **design dossier only** | D | 2 | 6–9 mo | low | ethics/regulatory gates |
| 17 | Selection informatics to reduce lifespan load | D | 1–2 | 6–12 mo | low | breed-club engagement |
| 18 | Germline modification | — | — | — | — | **not recommended** |

---

## Open questions / gaps

1. **Does the DAP data-use agreement permit training and releasing model weights** derived from its data (vs analysing within Terra)? This gates #6, #9 and parts of #1 ❓.
2. **Death/event counts in current DAP releases** — **partly resolved** [verifier]: Sohrab et al. 2026 report 957 Precision-Cohort dogs with three years of follow-up, of which **11% died** (~105 deaths), and Harrison 2026 ran survival models on 937 dogs. #9 should plan around ~100 events.
3. **All cost and timeline figures are my own estimates**, not quotes; GPU pricing and reagent costs were not verified ❓.
4. **Collaborator names are the publishing groups on cited work** — no willingness, availability or funding status has been checked ❓.
5. **No canine perturbation dataset** (CRISPR or compound, single-cell) exists, so #6's perturbation-prediction component cannot be validated in dog today ❓.
6. **Canine cell-line resources are thin** — **990 lines in Cellosaurus** ✅ [verifier-upgraded: re-counted via the Cellosaurus API] [99] and no uniformly processed drug-response matrix — which is the main practical obstacle to #13.
7. **Wolf ageing data are nearly absent** (one 2017 RRBS clock cohort of 62 wolves ✅ [105]; 24 wolves in the DoGA biobank ✅ [15]), weakening every dog-vs-wolf comparison in #5 and #14.
8. **Whether Precious3GPT or similar multi-species commercial models already cover dog** — **still ❓ for dog**, but [verifier] the weights are confirmed public on Hugging Face under **CC-BY-NC-4.0** (non-commercial), and all documented prompt examples use `<species>human</species>`.
9. **GEMME's licence/repository** — **still unresolved** ❓ after an independent attempt (GitHub path 404s, lcqb.upmc.fr unreachable). Treat GEMME as optional in #2, not load-bearing.
10. **I have not read `../04_dog_aging_biology` or `../05_interventions`** (other agents' files were not yet written when I worked), so there may be mechanistic findings or intervention evidence that should reorder this list. [verifier note] Those files now exist and have been verified. Three findings from them bear on this list: Horvath 2022's EWAS top hits are *SF1*/*TTC8* rather than IGF-axis genes (so #1 and #3 should not expect an IGF EWAS signal); the McCoy clock preprint rests on 49 deaths; and Dog10K's "14% more variants in wolves" refers to **structural** variants (relevant to #4 and #5's outgroup framing).
11. **New open item** [verifier-added]: **#1's clock-scoring step is not executable as written** (array-based clocks vs DAP's RRBS data), and the same mismatch affects #3's clock-residual regression, #9's epigenetic modality and #14's array-based read-out. This is the single most consequential methodological gap in the list.

---

## Sources

1. Sutter NB, Bustamante CD, Chase K, Gray MM, Zhao K, Zhu L, et al.; Ostrander EA. "A single IGF1 allele is a major determinant of small size in dogs." *Science* 316 (2007). DOI 10.1126/science.1137045.
2. Teng KT, Brodbelt DC, Pegram C, Church DB, O'Neill DG. "Life tables of annual life expectancy and mortality for companion dogs in the United Kingdom." *Scientific Reports* 12 (2022). DOI 10.1038/s41598-022-10341-6.
3. Kraus C, Pavard S, Promislow DEL. "The size–life span trade-off decomposed: why large dogs die young." *The American Naturalist* 181 (2013). DOI 10.1086/669665.
4. Horvath S, Lu AT, Haghani A, Zoller JA, Li CZ, Lim AR, Brooke RT, Raj K, Serres-Armero A, Dreger DL, Hogan AN, Plassais J, Ostrander EA. "DNA methylation clocks for dogs and humans." *PNAS* 119(21):e2120887119 (2022). DOI 10.1073/pnas.2120887119.
5. McCoy BM, Mariner BL, Cheng CF, Slikas E, Adjangba C, Greenier A, Brassington L, et al. "Aging at scale: Younger dogs and larger breeds from the Dog Aging Project show accelerated epigenetic aging." bioRxiv, 4 Oct 2024. DOI 10.1101/2024.10.03.616519.
6. Prescott J, Keyser AJ, Litwin P, Dunbar MD, McClelland R, Ruple A, Ernst H, et al.; Promislow DEL. "Rationale and design of the Dog Aging Project precision cohort: a multi-omic resource for longitudinal research in geroscience." *GeroScience* (2025). DOI 10.1007/s11357-025-01571-3.
7. Sohrab V, White ME, Harrison BR, Bierman R, Marye A, Morrill Pirovich K, Genereux D, et al. "Blood biomarkers and breed genetics of aging in pet dogs." bioRxiv, 10 Mar 2026. DOI 10.64898/2026.03.07.710297.
8. Meadows JRS, Kidd JM, Wang GD, Parker HG, Schall PZ, Bianchi M, Christmas MJ, et al. "Genome sequencing of 2000 canids by the Dog10K consortium advances the understanding of demography, genome function and architecture." *Genome Biology* 24 (2023). DOI 10.1186/s13059-023-03023-7.
9. Registry of Open Data on AWS. "Golden Retriever Lifetime Study: Whole genome genotyping of Golden Retrievers on Axiom HD Arrays" (~1.1M markers, 3,224 dogs, CC-BY-SA, `s3://mafgrlsgenome`). https://registry.opendata.aws/maf-genome/
10. Teng et al. 2022, as [2].
11. `shorvath/MammalianMethylationConsortium` and `ahaghani/EnsembleAge` (both MIT). https://github.com/shorvath/MammalianMethylationConsortium/
12. Bian Y, Bierman R, Snyder-Mackler N, Promislow D, Karlsson E, Dog Aging Project Consortium. "An interpretable machine learning framework for dog breed inference and ancestry decomposition." bioRxiv, 4 Jun 2026. DOI 10.64898/2026.06.03.729926.
13. Buckley RM, Bilgen N, Harris AC, Savolainen P, Tepeli C, Erdoğan M, Serres Armero A, et al.; Ostrander EA. "Analysis of canine gene constraint identifies new variants for orofacial clefts and stature." *Genome Research* (2025). DOI 10.1101/gr.280092.124.
14. Lin Z, Akin H, Rao R, Hie B, Zhu Z, Lu W, et al. "Evolutionary-scale prediction of atomic-level protein structure with a language model" (ESM-2). *Science* 379 (2023). DOI 10.1126/science.ade2574. Weights `facebook/esm2_t33_650M_UR50D` (MIT).
15. Hörtenhuber M, Hytönen MK, Mukarram AK, Arumilli M, Araujo CL, Quintero I, et al.; DoGA Consortium. "The DoGA consortium expression atlas of promoters and genes in 100 canine tissues." *Nature Communications* 15 (2024). DOI 10.1038/s41467-024-52798-1.
16. "Integrative mapping of the dog epigenome: Reference annotation for comparative intertissue and cross-species studies" (EpiC Dog). *Science Advances* 9(27):eade3399 (2023). DOI 10.1126/sciadv.ade3399.
17. Megquier K, Genereux DP, Hekman J, Swofford R, Turner-Maier J, Johnson J, Alonso J, et al. "BarkBase: Epigenomic Annotation of Canine Genomes." *Genes* 10(6):433 (2019). DOI 10.3390/genes10060433.
18. Serres Armero A, Buckley RM, Mboning L, Spatola GJ, Horvath S, Pellegrini M, Ostrander EA. "Co-analysis of methylation platforms for signatures of biological aging in the domestic dog reveals previously unexplored confounding factors." *Aging* 16 (2024). DOI 10.18632/aging.206012.
19. Hu H, Xie W. "Human genomic tools to assess missense variant pathogenicity in domestic mammals using a mock-variant strategy." *Open Veterinary Journal* 15(10) (2025). DOI 10.5455/ovj.2025.v15.i10.35.
20. Cheng J, Novati G, Pan J, Bycroft C, Žemgulytė A, Applebaum T, et al. "Accurate proteome-wide missense variant effect prediction with AlphaMissense." *Science* 381 (2023). DOI 10.1126/science.adg7492; repo `google-deepmind/alphamissense` ("we are not releasing the trained model weights").
21. OMIA home-page statistics as displayed 2026-10-04 (dog: 1,019 traits; 597 likely causal variants; 347 characterised single-gene diseases). https://www.omia.org/home/
22. UniProt proteome UP000805418, release 2026_03 (43,615 proteins; 20,987 genes; 857 reviewed). https://rest.uniprot.org/proteomes/UP000805418
23. Axelsson E, Ljungvall I, Bhoumik P, Conn LB, Muren E, Ohlsson Å, Olsen LH, Engdahl K, et al. "The genetic consequences of dog breed formation — Accumulation of deleterious genetic variation and fixation of mutations associated with myxomatous mitral valve disease in cavalier King Charles spaniels." *PLoS Genetics* (2021). DOI 10.1371/journal.pgen.1009726.
24. Subramanian S, Kumar M. "The Association between the Abundance of Homozygous Deleterious Variants and the Morbidity of Dog Breeds." *Biology* 13:574 (2024). DOI 10.3390/biology13080574.
25. Meier J, Rao R, Verkuil R, Liu J, Sercu T, Rives A. "Language models enable zero-shot prediction of the effects of mutations on protein function" (ESM-1v). DOI 10.1101/2021.07.09.450648.
26. ESM C model card `biohub/ESMC-6B` (6B params; licence `mit` + `other`). https://huggingface.co/biohub/ESMC-6B
27. Frazer J, Notin P, Dias M, Gomez A, Min JK, Brock K, Gal Y, Marks DS. "Disease variant prediction with deep generative models of evolutionary data" (EVE). *Nature* 599 (2021). DOI 10.1038/s41586-021-04043-8.
28. Carbone A, Laine E, Lombardi G. "Unlocking Protein Evolution Insights: … Mutational Effect Predictions with GEMME." *Methods Mol Biol* (2026). DOI 10.1007/978-1-0716-4828-5_7. ❓ repository/licence unverified.
29. Brixi G, Durrant MG, Ku J, Naghipourfar M, Poli M, Sun G, et al. "Genome modelling and design across all domains of life with Evo 2." *Nature* (2026). DOI 10.1038/s41586-026-10176-5; OpenGenome2 `species_metadata.csv` checked 2026-10-04 (dog `GCF_011100685.1`; Ensembl r112 dog mRNA/ncRNA; plus canid relatives incl. *Urocyon cinereoargenteus*, *Vulpes ferrilata*, *Chrysocyon brachyurus*, *Nyctereutes procyonoides*, *Lycaon pictus*, *Otocyon megalotis*).
30. Orenbuch R, Shearer CA, Kollasch AW, Spinner AD, Hopf T, van Niekerk L, et al.; Marks DS. "Proteome-wide model for human disease genetics" (popEVE). *Nature Genetics* (2025). DOI 10.1038/s41588-025-02400-1.
31. Tyshkovskiy A, Kholdina D, Davitadze M, Molière A, Moldakozhayev A, Tongu Y, et al.; Gladyshev VN. "Universal transcriptomic hallmarks of mammalian ageing and mortality." *Nature* (2026). DOI 10.1038/s41586-026-10542-3.
32. Zhou T, Pu SY, Zhang SJ, Zhou QJ, Zeng M, Lu JS, Lu X, Wang YN, Wang GD. "Dog10K: an integrated Dog10K database summarizing canine multi-omics." *NAR* 53(D1):D939 (2024/2025).
33. Li B, Ding Y, Han M, Zhang Z, Ling Z, Zhu W, Zhao X, Zhang Y, Lv C, Li N, Liao M, et al. "Multi-omics analysis of canine aging markers and evaluation of stem cell intervention." *Communications Biology* 8 (2025). DOI 10.1038/s42003-025-08333-z.
34. Abood A, Louyakis AS, Jackson M, Eichman R, Hollar R, Panickar KS, Brockman J. "Multiomic profiling of canine immune and metabolic aging in a cohort of young and senior beagles." *Frontiers in Immunology* (2026). DOI 10.3389/fimmu.2026.1906638.
35. Harrison BR, Akey JM, Snyder-Mackler N, Raftery D, Creevy KE, Promislow DEL, DAP Consortium. "Dogs and humans share biomarkers of mortality." *J Gerontol A Biol Sci Med Sci* (2026). DOI 10.1093/gerona/glaf279.
36. Tyshkovskiy A, Bozaykut P, Borodinova AA, Gerashchenko MV, Ables GP, Garratt M, Khaitovich P, Clish CB, Miller RA, Gladyshev VN. "Identification and Application of Gene Expression Signatures Associated with Lifespan Extension." *Cell Metabolism* 30 (2019). DOI 10.1016/j.cmet.2019.06.018.
37. Tyshkovskiy A, Ma S, Shindyapina AV, Tikhonov S, Lee SG, Bozaykut P, Castro JP, Seluanov A, Schork NJ, Gorbunova V, Dmitriev SE, Miller RA, Gladyshev VN. "Distinct longevity mechanisms across and within species and their association with aging." *Cell* 186 (2023). DOI 10.1016/j.cell.2023.05.002.
38. Zoonomia TOGA ortholog annotations. https://genome.senckenberg.de/download/TOGA/
39. Rosen Y, Roohani Y, Agrawal A, Samotorčan L, Tabula Sapiens Consortium, Quake SR, Leskovec J. "Universal cell embedding provides a foundation model for cell biology." *Nature* (2026). DOI 10.1038/s41586-026-10689-z.
40. Plassais J, vonHoldt BM, Parker HG, Carmagnini A, Dubos N, Papa I, Bevant K, Derrien T, et al. "Natural and human-driven selection of a single non-coding body size variant in ancient and modern canids." *Current Biology* 32 (2022). DOI 10.1016/j.cub.2021.12.036.
41. McMillan KM, Bielby J, Williams CL, Upjohn MM, Casey RA, Christley RM. "Longevity of companion dog breeds: those at risk from early death." *Scientific Reports* 14 (2024). DOI 10.1038/s41598-023-50458-w.
42. Donner J, Freyer J, Davison S, Anderson H, Blades M, Honkanen L, Inman L, Brookhart-Knox C, et al. "Genetic prevalence and clinical relevance of canine Mendelian disease variants in over one million dogs." *PLoS Genetics* 19(2):e1010651 (2023). DOI 10.1371/journal.pgen.1010651.
43. Christmas MJ, Kaplow IM, Genereux DP, Dong MX, Hughes GM, Li X, Sullivan PF, et al. (Zoonomia Consortium). "Evolutionary constraint and innovation across hundreds of placental mammals." *Science* 380:eabn3943 (2023). DOI 10.1126/science.abn3943.
44. de Magalhães JP, et al. "Human Ageing Genomic Resources: updates on key databases in ageing research" (GenAge, AnAge, DrugAge 1,097 compounds, GenDR, CellAge 866 genes, LongevityMap 3,144 variants). (2023/2024). https://genomics.senescence.info/
45. Kowalczyk A, Partha R, Clark NL, Chikina M. "Pan-mammalian analysis of molecular constraints underlying extended lifespan." *eLife* 9:e51089 (2020). DOI 10.7554/eLife.51089.
46. Zoonomia Project. "The Data" (240-species Cactus `.hal`, phyloP at cglgenomics.ucsc.edu/data/cactus/). https://zoonomiaproject.org/the-data/
47. AnAge Database Statistics (Build 15; 4,671 entries = 4,645 species + 26 taxa). https://genomics.senescence.info/species/stats.php
48. AnAge entry *Canis familiaris* (maximum longevity 27 y in captivity; sample size large; quality acceptable). https://genomics.senescence.info/species/entry.php?species=canis_familiaris
49. Grey wolf assembly mCanLor1.2, GCA_905319855.2 🟡. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8649967/
50. Theodoris CV, Xiao L, Chopra A, Chaffin MD, Al Sayed ZR, Hill MC, Mantineo H, et al. "Transfer learning enables predictions in network biology" (Geneformer). *Nature* 618 (2023). DOI 10.1038/s41586-023-06139-9.
51. Cui H, Wang C, Maan H, Pang K, Luo F, Duan N, Wang B. "scGPT…" *Nature Methods* 21 (2024). DOI 10.1038/s41592-024-02201-0.
52. Pearce JD, Simmonds SE, Mahmoudabadi G, Krishnan L, Palla G, Istrate AM, Tarashansky A, et al. "TranscriptFormer: A generative cell atlas across 1.5 billion years of evolution." *Science* (2026). DOI 10.1126/science.aec8514; repo `czi-ai/transcriptformer` (MIT) — 12 trained species, 24 embedding species, dog absent; ESM-2 route documented.
53. CZI CELLxGENE Census documentation, LTS 2025-11-08 (human, mouse, macaque, marmoset, chimpanzee). https://chanzuckerberg.github.io/cellxgene-census/
54. "Single-nucleus transcriptomic atlas of the dog hippocampus…" *National Science Review* 9(11):nwac147 (2022).
55. Ammons DT, Harris RA, Hopkins LS, Kurihara J, Weishaar K, Dow S. "A single-cell RNA sequencing atlas of circulating leukocytes from healthy and osteosarcoma affected dogs." *Frontiers in Immunology* 14:1162700 (2023).
56. LeishDog Atlas preprint, bioRxiv Dec 2025 🟡.
57. Kim et al. "High-resolution single-cell RNA sequencing using canFam4 reveals novel immune subsets and checkpoint programs in healthy dogs." *Frontiers in Immunology* (2025); GEO GSE301630.
58. "A single-cell RNA sequencing atlas of the healthy canine lung." *Frontiers in Immunology* (2025).
59. NCI Cancer Research Data Commons. "Integrated Canine Data Commons" (open-access; RNA-seq, WGS, WXS, genotyping, methylation). https://datacommons.cancer.gov/repository/integrated-canine-data-commons
60. Adduri AK, Gautam D, Bevilacqua B, Naghipourfar M, Imran A, Shah R, Teyssier N, et al. "Predicting cellular responses to perturbation across diverse contexts with State." *Cell* (2026). DOI 10.1016/j.cell.2026.07.052; `arcinstitute/SE-600M` non-commercial model licence.
61. Ahlmann-Eltze C, Huber W, Anders S. "Deep-learning-based gene perturbation effect prediction does not yet outperform simple linear baselines." *Nature Methods* (2025). DOI 10.1038/s41592-025-02772-6.
62. Kedzierska KZ, Crawford L, Amini AP, Lu AX. "Zero-shot evaluation reveals limitations of single-cell foundation models." *Genome Biology* 26 (2025). DOI 10.1186/s13059-025-03574-x.
63. Khosravi A, et al. "When Simpler Models Win: A Calibration Benchmark of scGPT for Cell-Type Annotation." preprint 2026. DOI 10.21203/rs.3.rs-10152510/v1 🟡.
64. Avsec Ž, Latysheva N, Cheng J, Novati G, Taylor KR, Ward T, Bycroft C, et al. "Advancing regulatory variant effect prediction with AlphaGenome." *Nature* (2026). DOI 10.1038/s41586-025-10014-0.
65. `google-deepmind/alphagenome` README + AlphaGenome Terms (non-commercial API; no weights). https://github.com/google-deepmind/alphagenome
66. Avsec Ž, et al. "Effective gene expression prediction from sequence by integrating long-range interactions" (Enformer). *Nature Methods* 18 (2021). DOI 10.1038/s41592-021-01252-x.
67. Linder J, Srivastava D, Yuan H, Agarwal V, Kelley DR. "Predicting RNA-seq coverage from DNA sequence…" (Borzoi). *Nature Genetics* 57 (2025). DOI 10.1038/s41588-024-02053-6.
68. Ye C, Benegas G, Albors C, Li JC, Prillo S, Fields PD, Clarke B, Song YS. "Predicting genome-wide functional constraints with GPN-Star." *Nature* (2026). DOI 10.1038/s41586-026-11005-5.
69. Benegas G, Albors C, Aw AJ, Ye C, Song YS. "A DNA language model based on multispecies alignment predicts the effects of genome-wide variants." *Nature Biotechnology* (2025). DOI 10.1038/s41587-024-02511-w.
70. Mariner BL, McCoy BM, Greenier A, Brassington L, Slikas E, Adjangba C, Marye A, et al. "DNA methylation of transposons pattern aging differences across a diverse cohort of dogs from the Dog Aging Project." bioRxiv, 11 Oct 2024. DOI 10.1101/2024.10.08.617286.
71. "Evidence of emerging transcriptome mediators of Alzheimer's disease in canine cognitive dysfunction" and related CCD transcriptome/EV work 🟡. https://pmc.ncbi.nlm.nih.gov/articles/PMC13051885/
72. Jin K, McCoy BM, Goldman EA, Usova V, Tkachev V, Chitsazan AD, Kakebeen A, Jeffery U, et al. "DNA methylation and chromatin accessibility predict age in the domestic dog." *Aging Cell* 23 (2024). DOI 10.1111/acel.14079.
73. Nakamura M, Matsumoto Y, Yasuda K, Nagata M, Nakaki R, Okumura M, Yamazaki J. "Unraveling the DNA methylation landscape in dog blood across breeds." *BMC Genomics* (2024); GEO GSE252908.
74. Darcy S, … McKenzie A. "A canine brain bank for comparative neuroscience and brain aging research." bioRxiv, 14 Jul 2026 🟡.
75. "Near telomere-to-telomere genome assembly of the Beagle dog (*Canis lupus familiaris*)" — figshare 🟡.
76. Choi H, Kim JS, Kwon Y, Park S, Jeon S, et al.; Bhak J. "Telomere-to-telomere, accurate, and gapless genome assembly (TTAGGA) of the Korean Jindo dog…" bioRxiv, 20 May 2026 🟡.
77. Harrison BR, Partida-Aguilar M, Marye A, Djukovic D, Kauffman M, Dunbar MD, et al. "Protein Catabolites as Blood-Based Biomarkers of Aging Physiology: Findings From the Dog Aging Project." *Aging Cell* (2025). DOI 10.1111/acel.70226.
78. Bamberger T, Muller E, Algavi YM, Greenier A, Adjangba C, Slikas E, Brassington L, et al.; Borenstein E. "Mapping the canine gut microbiome: insights from the Dog Aging Project." *Nature Communications* (2026). DOI 10.1038/s41467-026-73193-y.
79. Shoshan Y, Raboh M, Ozery-Flato M, Ratner V, Golts A, Weber JK, Barkan E, et al. "MAMMAL — Molecular Aligned Multi-Modal Architecture and Language for biomedical discovery." *npj Drug Discovery* (2026). DOI 10.1038/s44386-026-00047-4 (preprint arXiv:2410.22367); weights `ibm/biomed.omics.bl.sm.ma-ted-458m` (Apache-2.0).
80. Bamberger T, DAP Consortium, Borenstein E. "Phenotype-driven parallel embedding for microbiome multi-omic data integration." preprint, Dec 2025. DOI 10.64898/2025.12.05.692119 🟡.
81. Huang K, Zhang S, Wang H, Qu Y, Lu Y, Roohani Y, Li R, Qiu L, Li G, Zhang J, Yin et al. "Biomni: A General-Purpose Biomedical AI Agent." bioRxiv, 2 Jun 2025. DOI 10.1101/2025.05.30.656746; repo Apache-2.0.
82. Ghareeb AE, Chang B, Mitchener L, Yiu A, Szostkiewicz CJ, Laurent JM, Razzak MT, White AD, Hinks MM, Rodriques SG. "Robin: A multi-agent system for automating scientific discovery." arXiv:2505.13400 (2025).
83. Mitchener L, Yiu A, Chang B, Bourdenx M, Nadolski T, et al. "Kosmos: An AI Scientist for Autonomous Discovery." arXiv:2511.02824 (2025).
84. Gottweis J, Weng WH, Daryin A, Tu T, et al. "Towards an AI co-scientist / Accelerating scientific discovery with Co-Scientist." arXiv:2502.18864 (2025).
85. Gross B, Ehlert J, Gladyshev VN, Loscalzo J, Barabási AL. "Network-driven discovery of repurposable drugs targeting hallmarks of aging." *Nature Aging* (2026). DOI 10.1038/s43587-026-01161-8.
86. Kamya P, Ozerov IV, Pun FW, Tretina K, Fokina T, Chen S, Naumov V, et al. "PandaOmics: An AI-Driven Platform for Therapeutic Target and Biomarker Discovery." *J Chem Inf Model* 64 (2024). DOI 10.1021/acs.jcim.3c01619.
87. Wang T, Ma J, Hogan AN, … Bannasch DL, Ostrander EA, Ideker T. "Quantitative Translation of Dog-to-Human Aging by Conserved Remodeling of the DNA Methylome." *Cell Systems* 11 (2020). DOI 10.1016/j.cels.2020.06.006 (GEO GSE146920; Zenodo 10.5281/zenodo.3864683).
88. Lu AT, Fei Z, Haghani A, Robeck TR, Zoller JA, Li CZ, Lowe R, et al.; Horvath S. "Universal DNA methylation age across mammalian tissues." *Nature Aging* 3 (2023). DOI 10.1038/s43587-023-00462-6.
89. Coleman AE, Creevy KE, Anderson R, Reed MJ, Fajt VR, Aicher KM, Atiee G, Barnett et al. "Test of Rapamycin in Aging Dogs (TRIAD): study design and rationale…" *GeroScience* (2025). DOI 10.1007/s11357-024-01484-7.
90. Jang S, Kim SJ, Kang D, Hong CY, Bok EY, Lee SL, Choe YH, Kim J. "Age-associated epigenetic drift trajectory and cross-national disparities in accelerated aging in domestic dogs." *PNAS* (2026). DOI 10.1073/pnas.2528874123.
91. My own sequence alignments, 2026-10-04: UniProt P08069/A0A8I3RQ77 (IGF1R 97.4%), P05019/P33712 (IGF1 91.9%; mature 70-aa human IGF-1 an exact substring of the dog precursor), P10912/Q9TU69 (GHR 82.3%), P01241/P33711 (GH1 68.4%); Biopython 1.88 `PairwiseAligner`, global, BLOSUM62, gap open −10 / extend −0.5; identity over non-gap aligned columns.
92. `google-deepmind/alphafold3` README + WEIGHTS_TERMS_OF_USE.md (Apache-2.0 code; non-commercial weights obtained from Google; server non-commercial; commercial via Google Cloud).
93. `chaidiscovery/chai-lab` README (Chai-1 Apache-2.0 code and weights).
94. Passaro S, Corso G, Wohlwend J, Reveiz M, Thaler S, Somnath VR, Getz N, et al. "Boltz-2: Towards Accurate and Efficient Binding Affinity Prediction." bioRxiv, 18 Jun 2025. DOI 10.1101/2025.06.14.659707; repo MIT (code + weights).
95. Pacesa M, Nickel L, Schellhaas C, Schmidt J, Pyatova E, Kissling L, Barendse P, et al. "One-shot design of functional protein binders with BindCraft." *Nature* (2025). DOI 10.1038/s41586-025-09429-6; repo MIT.
96. Ahern W, Yim J, Tischer D, Salike S, Woodbury SM, Kim D, Kalvet I, Kipnis Y, Coventry B, et al. "Atom-level enzyme active site scaffolding using RFdiffusion2." *Nature Methods* (2025). DOI 10.1038/s41592-025-02975-x; `RosettaCommons/foundry` (BSD-3-Clause).
97. Dauparas J, Anishchenko I, Bennett N, Bai H, Ragotte RJ, Milles LF, Wicky BIM, et al. "Robust deep learning-based protein sequence design using ProteinMPNN." *Science* 378 (2022). DOI 10.1126/science.add2187; repo MIT.
98. AlphaFold DB API and FTP checks, 2026-10-04 (dog entries exist for P33712/Q9TU69/A0A8I3MJV0; `A0A8I3RQ77` → 404; no CANLF proteome tar in `latest/`). https://alphafold.ebi.ac.uk/
99. Cellosaurus API count for taxon 9615 — numFound 990 🟡 (2026-10-04).
100. Tyshkovskiy et al. 2019, as [36] (KU-0063794 prediction) and 2023, as [37] (lifespan/healthspan extension).
101. Subramanian A, Narayan R, Corsello SM, Peck DD, Natoli TE, Lu X, Gould J, Davis JF, et al. "A Next Generation Connectivity Map: L1000 Platform and the First 1,000,000 Profiles." *Cell* 171 (2017). DOI 10.1016/j.cell.2017.10.049.
102. Tahoe-100M atlas (50 cancer cell lines, 379 small molecules, 3 concentrations) 🟡, as described in Shen H, preprint 2026, DOI 10.21203/rs.3.rs-10448056/v2.
103. Wang E, Schmidgall S, Jaeger PF, Zhang F, Pilgrim R, Matias Y, Barral J, Fleet D, Azizi S. "TxGemma: Efficient and Agentic LLMs for Therapeutics." arXiv:2504.06196 (2025); Hugging Face `google/txgemma-*` gated under Health AI Developer Foundations terms.
104. Ma S, Upneja A, Galecki A, Tsai YM, Burant CF, Raskind S, Zhang Q, Zhang ZD, Seluanov A, Gorbunova V, et al. "Cell culture-based profiling across mammals reveals DNA repair and metabolism as determinants of species longevity." *eLife* 5:e19130 (2016). DOI 10.7554/eLife.19130.
105. Thompson MJ, vonHoldt B, Horvath S, Pellegrini M. "An epigenetic aging clock for dogs and wolves." *Aging* 9 (2017). DOI 10.18632/aging.101211.
106. McGrath S, Hull E, Dunbar MD, Prescott J, Keyser AJ, MacLean E, Darvas M, Latimer C, et al. "The companion dog as a translational model for Alzheimer's disease: Development of a longitudinal research platform and post mortem protocols." *Alzheimer's & Dementia* (2025). DOI 10.1002/alz.70630.
107. "Functional assessments of short-term spatial memory in the Dog Aging Project identify strong associations with age that are not moderated by body mass." *GeroScience* (2025). DOI 10.1007/s11357-025-01867-4 🟡.
108. "Advances in biomarker discovery for canine cognitive dysfunction: a comprehensive structured narrative review…" (2025) 🟡. https://pmc.ncbi.nlm.nih.gov/articles/PMC13451518/
109. "Canine cognition assessments in the Test of Rapamycin in Aging Dogs (TRIAD)." *Innovation in Aging* (2024). https://www.ncbi.nlm.nih.gov/pmc/articles/PMC11692996/
110. Schmid SM, Sexton CL, Yoerger A, Kauffman M, McClelland RL, DAP Consortium, Creevy KE. "Accuracy of owner-reported diagnoses for dogs enrolled in the Dog Aging Project as compared to veterinary electronic medical records." *PLoS ONE* (2026). DOI 10.1371/journal.pone.0342427.
111. Davidsohn N, Pezone M, Vernet A, Graveline A, Oliver D, Slomovic S, Punthambaker S, et al. "A single combination gene therapy treats multiple age-related diseases." *PNAS* 116 (2019). DOI 10.1073/pnas.1910073116.
112. Acland GM, Aguirre GD, Ray J, Zhang Q, Aleman TS, Cideciyan AV, Pearce-Kelling SE, et al. "Gene therapy restores vision in a canine model of childhood blindness." *Nature Genetics* 28 (2001). DOI 10.1038/ng0501-92.
113. Gordon I, Paoloni M, Mazcko C, Khanna C. "The Comparative Oncology Trials Consortium: using spontaneously occurring cancers in dogs to inform the cancer drug development pathway." *PLoS Medicine* 6:e1000161 (2009).
114. Zou Q, Wang X, Liu Y, Ouyang Z, Long H, Wei S, Xin J, Zhao B, Lai S, Shen J, Ni Q, et al. "Generation of gene-target dogs using CRISPR/Cas9 system." *Journal of Molecular Cell Biology* 7 (2015). DOI 10.1093/jmcb/mjv061.

---

## Verification notes

> Independent verification pass by **Fable 5.1**, 2026-10-04. Full report: `../07_verification/ai_toolkit_verification.md`.

**Scope of this pass.** The proposals themselves are explicitly hypotheses and were not "verified" as such. What I checked was (a) whether the **existing resources** each proposal depends on exist as described, (b) whether the **method answers the question**, and (c) whether any **feasibility claim is obviously wrong**. Costs, timelines and collaborator willingness remain the author's own estimates and are still unverified ❓ — as the file says.

**Result.** Every one of the 18 proposals now carries a `Verifier comment:` line. **Material problems** (a wrong resource, a non-executable step or an understated gate) were found in **nine**: #1, #3, #4, #5, #6, #8, #10, #13 and #14. The comments on #2, #7, #9, #11, #12, #15 and #17 are refinements and licence warnings rather than defects, and #16 and #18 needed no change. **No proposal was found to be unsound in its core logic**, and the ranking by cost and risk is defensible. The problems found are of three kinds:

1. **One genuine methodological blocker.** #1's step 1 ("score every methylation sample with a dog clock, the human–dog dual clock and the universal pan-mammalian clock") cannot be done directly: those clocks are **HorvathMammalMethylChip40 array** models, while DAP's data are **RRBS**. The same mismatch propagates to #3, #9 and #14.
2. **Four resources that do not do what the proposal needs.** Wisdom Panel's supplements cover only 250 Mendelian disease variants (#4, but they are used correctly in #17); **ICDC contains no single-cell data** (#6); the **near-T2T Beagle assembly has no literature record at all**, so its repeat fraction cannot anchor #8; and three of the six canid assemblies cited in #5 are scaffold-level, which degrades alignment-based rate tests.
3. **Licence and provenance constraints worth knowing before you start.** popEVE is **GPL-3.0** (#2); GEMME has no findable repository (#2); State's model licence is non-commercial while TranscriptFormer is MIT, so the fine-tuning base sets the artefact's licence (#6); Tahoe-100M is **CC0-1.0 from Vevo**, not Arc, and its stated composition is not in the dataset card (#13); Kosmos has **no public repository** (#10); and the HorvathMammalMethylChip40 is a consortium-distributed array, not a catalogue product (#14).

**Two things got better, not worse.** #9's event-count worry is now partly answerable (~105 deaths already accrued among 957 followed Precision-Cohort dogs), and #15's cognitive resource is larger than described (6,753 dogs in the DAP spatial-memory study).

**Germline item (#18).** Checked specifically: it is handled **purely as an ethics-flagged argument against pursuing germline modification, with no technical protocol of any kind** — no target design, editing strategy, delivery route or embryo methodology — and its one factual citation (Zou et al. 2015) is accurate. No change requested.
