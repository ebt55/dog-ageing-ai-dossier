# AlphaFold and Dogs (and Wolves)
> Part of the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 subagent · Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/alphafold_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**Confidence tags:** ✅ = confirmed in a primary source I opened, or by a live database query I ran on 2026-10-04 · 🟡 = secondary source or abstract only · ❓ = unconfirmed or my inference. **Numbers from live queries will drift** as UniProt and AFDB update.

---

## TL;DR

- **There is no "dog AlphaFold", and none is needed for structure prediction.** AlphaFold is trained on PDB structures from all species and reads evolutionary signal from MSAs spanning the tree of life, so the same model predicts dog, wolf or human proteins [1][2] ✅. What *is* species-specific lies mostly outside structure prediction: variants, gene models and isoforms, expression, non-coding regulation, PTMs, immune repertoires and host–pathogen pairs.
- **Dog coverage in AlphaFold DB is good but has holes** (UniProt 2026_03 vs AFDB v6, queried 2026-10-04) [3][4] ✅.
  - 42,123 of 46,473 dog UniProt entries (90.6%) have an AFDB model.
  - 39,585 of 43,615 entries (90.8%) in the dog **reference proteome UP000805418** (Labrador retriever assembly) have one.
  - Only **857** dog entries are Swiss-Prot-reviewed, against 20,431 for human.
- **Dog is *not* one of AFDB's 46 downloadable proteome bundles** (v6 FTP) [5] ✅. It is also not in the 2026 NVIDIA dimer dataset, which covers 16 model organisms plus 30 WHO proteomes (the FAQ also mentions Swiss-Prot and UniProt proteins, but the dog Swiss-Prot entries GHR and IGF1 have no complex entries) [6] ✅ ([verifier-confirmed] `/api/complex/Q9TU69` and `/api/complex/P33712` return `{}`; human GHR P10912 returns three NVIDIA dimers).
- **Systematic gap: long dog proteins.** Unreviewed entries outside the model proteomes are only modelled up to **1,280 aa** [6] ✅. Result: 1 of 3,357 unreviewed dog entries of 1,281–2,700 aa has a model, and none of the 453 dog entries longer than 2,700 aa do [3] ✅. Examples include the **full-length dog IGF1R and MTOR** (ageing-relevant), ABCC9 and RESF1 [4] ✅. Dog SOD1 (Swiss-Prot Q8WNN6) is missing because its sequence contains an "X" [3][4] ✅.
- **Wolves.** *Canis lupus* (taxid 9612) has only 199 UniProt entries (197 with AFDB models) and **no proteome**. The dingo has a reference proteome (UP000694391, 33,928 proteins) [3] ✅. In practice, use dog sequences for wolf work and add wolf variants (the dog is a subspecies of the grey wolf [3] ✅).
- **AlphaMissense is human-only.** It provides human-only precomputed scores and no released weights [7][8] ✅. The AFDB API returns AlphaMissense annotations for human IGF1 but nothing for dog IGF1 [4] ✅.
- **Mapping dog variants onto human proteins is only partly reliable.** Veterinary geneticists map dog variants onto the human ortholog ("mock-human" variants). A systematic test across domestic mammals found **high sensitivity (0.77–0.90) but poor specificity (0.20–0.46), auROC 0.55–0.61** [9] ✅. Ensembl VEP *does* provide SIFT predictions for dog [10] ✅.
- **Published veterinary uses of AF are real but modest.** They include an AF3-guided design of universal dog/human TNFα minibinders [11] ✅ and an AF3 model of an anti-canine PD-1 nanobody [12] ✅. Many studies of disease variants simply use the **human** AFDB model as a proxy for the dog protein [13][14][15][16] ✅. I found **no published study applying AF to dog ageing biology per se**. The closest is a canine GHRH gene-therapy trial in senior dogs that used a human AFDB model for illustration [17] ✅.

---

## 1. Is there a "dog AlphaFold"?

**No.** Here is why structure prediction is largely species-agnostic:
1. **Same physics, same folds.** Orthologous proteins in mammals usually share the same fold, and AlphaFold is trained on PDB structures from every kingdom [1][2] ✅.
2. **The MSA is cross-species by construction.** For a dog query, the MSA already contains human, mouse, wolf and other mammalian homologs plus distant relatives. The dog sequence just sets which residues are queried [1] ✅.
3. **Dog and human orthologs are highly similar.** For example, mature IGF-1 is 100% identical, mature IGF1R 98.1%, GHR 82.3% and GH 68.4% (my alignments; see `how_to_use_alphafold.md` §7) ✅. Predictions for such pairs are near-identical in fold.

**What is species-specific (and where AF helps or does not help):**

| Layer | Dog-specific? | Can AF-family tools address it? |
|---|---|---|
| Coding variants (breed alleles, disease mutations) | Yes | Partly. AF can *place* a variant in 3D. It cannot reliably predict the stability or ΔΔG change [18] ✅. AlphaMissense is human-only [7] ✅. |
| Gene models / isoforms | Yes; dog annotations come from Ensembl gene builds (ROS_Cfam_1.0) [3] ✅ | Bad gene models produce bad inputs. Example: the dog IGF1R and FKBP1A entries have odd N-termini or missing segments (my alignments) ✅. |
| Non-coding regulation (e.g. the IGF1-AS size variant) | Yes [19] ✅ | **No** for protein-structure tools. AlphaGenome is trained on human and mouse only [20] ✅; its transfer to dog is untested ❓. |
| Expression levels / tissue specificity | Yes | No |
| PTMs and glycosylation | Can differ | AF3 can model specified PTMs and glycans, but you must supply them [21] ✅ |
| Immune repertoire (DLA/MHC, antibodies, NK receptors) | Yes | Partly: modelling of dog MHC, Ly49 and nanobody–target complexes [12][22] ✅. Antibody docking accuracy is limited (see the complete guide §5). |
| Host–pathogen (canine viruses, ticks) | Yes | Yes; e.g. parvovirus vaccine design and Anaplasma antigens [23][24] ✅ |

**Dog-trained foundation models.** For dog- or veterinary-trained models of other kinds (genomic, clinical), see `03_canine_bio_ai/` (sister agent).

---

## 2. Dog and wolf coverage in AlphaFold DB (verified 2026-10-04)

### 2.1 Proteomes in UniProt (release 2026_03) [3] ✅

| Proteome | Organism / breed | Type | Assembly | Proteins |
|---|---|---|---|---|
| **UP000805418** | *Canis lupus familiaris*, Labrador retriever | **Reference proteome** | GCA_014441545.1 (Ensembl) | 43,615 |
| UP000002254 | Dog, Boxer | Non-reference | GCA_000002285.4 | 41,817 |
| UP000694429 | Dog, Basenji | Non-reference | GCA_004886185.1 | 42,651 |
| UP000694542 | Dog, Great Dane | Non-reference | GCA_005444595.1 | 42,573 |
| UP000694391 | *Canis lupus dingo* | Reference proteome | GCA_003254725.1 | 33,928 |
| none | *Canis lupus* (grey wolf, taxid 9612) | **No proteome** | – | – |

### 2.2 AlphaFold DB cross-references (UniProt query counts) [3] ✅

| Query | Entries | With AFDB model | % |
|---|---|---|---|
| Dog, all (organism 9615) | 46,473 | 42,123 | 90.6% |
| Dog, reviewed (Swiss-Prot) | 857 | 809 | 94.4% |
| Dog reference proteome UP000805418 | 43,615 | 39,585 | 90.8% |
| Dog unreviewed, 16–1,280 aa | 41,779 | 41,313 | 98.9% |
| Dog unreviewed, **1,281–2,700 aa** | **3,357** | **1** | ≈0% |
| Dog reviewed, 1,281–2,700 aa | 41 | 37 | 90% |
| Dog, any status, **>2,700 aa** | 453 | 0 | 0% |
| Grey wolf, organism 9612 | 199 | 197 | 99% |
| Dingo, organism 286419 | 33,945 | 31,000 | 91.3% |
| (Reference) Human, reviewed | 20,431 | – | – |

**Interpretation** ✅ (rule from the AFDB FAQ [6]; counts from [3]):
- AFDB models proteomes and Swiss-Prot up to 2,700 aa, but the rest of UniProt only up to 1,280 aa. It also skips sequences containing non-standard residues and anything outside the "one sequence per gene" set.
- Dog is not an AFDB model organism, and few dog proteins are Swiss-Prot. So **almost every dog protein longer than 1,280 aa lacks a model.**
- Human and mouse long proteins are probably mostly covered through their Swiss-Prot entries and proteome bundles. This is my inference; I did not count it ❓.

### 2.3 Spot checks of ageing- and disease-relevant dog proteins [4] ✅

| Dog protein (accession) | Length | AFDB v6 model? | Note |
|---|---|---|---|
| IGF1 (P33712, Swiss-Prot) | 153 | Yes; global pLDDT 55.19; mature-domain mean 56.3 | Human P05019 mature domain: 68.7 (identical sequence) |
| GHR (Q9TU69, Swiss-Prot) | 638 | Yes; ECD 81.5, cytoplasmic 41.6 | No dimer model. Human GHR has NVIDIA heterodimers with CSH2 (ipTM 0.80), CSH1 (0.81) and GH1 (0.80) [verifier-confirmed via `/api/complex/P10912`]. |
| GH1 (P33711) | 216 | Yes | |
| **IGF1R** (A0A8I3RQ77 / A0A8I3MER7 / A0A8I3MMA7) | 1,425 / 1,344 / 1,403 | **No** | Model it yourself (`how_to_use_alphafold.md` §7) |
| **MTOR** (A0A8I3MJG3) | 2,324 | **No** | A 755-aa fragment entry (A0A8I3RSA0) has a model |
| FKBP1A (A0A8I3NXR7) | 92 | Yes | Human FKBP12 is 108 aa; the dog entry lacks 16 residues (13–28 in human numbering), a likely gene-model gap. Otherwise 91/92 identical (my alignment). |
| TERT (Q6A548, Swiss-Prot) | 1,123 | Yes | |
| KL (klotho, A0A8I3NKX5) | 1,024 | Yes | |
| **SOD1** (Q8WNN6, Swiss-Prot) | 153 | **No** | The sequence contains "X" at position 53. Unreviewed A0A8I3PS52 (152 aa) has a model. Experimental dog SOD1 crystal structures exist (PDB 7WWT, 7WX0 E40K, etc.) [25][26] ✅ |
| ABCC9 (A0A8I3S0W3 etc.) | 1,549 | **No** (only a 149-aa fragment entry, A0A8I3P2G1) | Same gap reported by Furrow et al. in 2023 [13] ✅ |
| RESF1 (A0A8I3NVF7) | 1,705 | **No** | Addison's-disease gene in NSDTRs [27] ✅ |

### 2.4 Bulk downloads and complexes
- The v6 FTP `latest/` folder has **46 proteome tarballs**: human, mouse, rat, zebrafish, fly, worm, yeast, *Arabidopsis*, maize, rice, soybean, plus WHO pathogens. It has **no dog, cat, horse, cow or pig** [5] ✅.
- The AFDB homepage text says "47 other key organisms". That figure does not match the 46 tarballs I counted, which already include human [5][6] ✅. [verifier-corrected] The AFDB FAQ itself says "46 complete proteomes available for bulk download", so the homepage's "47 other" is the stale figure.
- **NVIDIA dimer dataset** (March and May 2026): about 2.2 M homo- and heterodimers for **16 model organisms + 30 WHO proteomes** (+ Swiss-Prot per one FAQ sentence). Generated with ColabFold/AF-Multimer [6] ✅. API checks: `/api/complex/Q9TU69` (dog GHR) and `/api/complex/P33712` (dog IGF1) return nothing [4] ✅.
- **No dog complexes are precomputed.** Model them yourself.

---

## 3. Variant-effect prediction for dogs

### 3.1 AlphaMissense: human only
- AlphaMissense scored "all possible human single amino acid substitutions" [7] ✅.
- The repository releases predictions for human transcripts only, and **"What we don't provide: The trained AlphaMissense model weights"** [8] ✅. So you **cannot run AlphaMissense on dog proteins**.
- The AFDB API serves AlphaMissense annotations for human P05019 but returns `{}` for dog P33712 [4] ✅.
- I found **no AlphaMissense successor covering non-human species** as of 2026-10-04 (searched Europe PMC, AlphaMissense GitHub, AFDB) ❓ (absence of evidence).

### 3.2 What veterinary geneticists actually do
1. **Mock-human mapping.** Map the dog residue to the aligned human residue and read the human AlphaMissense score. Examples:
   - MLH1 p.D375N in a hypermutated Border Collie dam: classified "pathogenic … based on the aligned human residue" [28] ✅.
   - RESF1 variant in Nova Scotia Duck Tolling Retrievers: AlphaMissense 0.82, likely pathogenic [27] ✅.
   - PTPN11/SHP2 in canine histiocytic sarcoma: AlphaMissense on the human protein, 99.3% identical, combined with PolyPhen-2 on the dog protein [29] ✅.
2. **How well does it work?** Hu & Xie (2025) converted 374 domestic-mammal OMIA variants (284 deleterious, 90 non-deleterious) into mock human variants. AlphaMissense, ESM-1b and PolyPhen-2 reached sensitivity 0.77–0.90 but specificity only **0.20–0.46**, with auROC **0.55–0.61** [9] ✅.

   Haque et al. (2024) mapped OMIA missense variants from 9 domestic species to human. Of 56 that ClinVar had already classified, 55.4% were pathogenic/likely pathogenic (OR 7.0 vs other missense variants in the same genes). REVEL and AlphaMissense scores of the rest resembled pathogenic variants [30] ✅.

   **Bottom line:** human tools flag real dog disease variants well but over-call benign ones.
3. **Species-native options.**
   - Ensembl VEP returns **SIFT** predictions for dog transcripts. My test on dog IGF1 returned SIFT but no PolyPhen [10] ✅.
   - Protein language models such as ESM-1b score any sequence without species-specific training [31] ✅. Note that Brandes et al. validated it on human data only.
4. **Variant catalogues.** The Dog Biomedical Variant Database (582 dogs + 8 wolves) [32] ✅ provides population context. Larger cohorts (Dog10K, Dog Aging Project) are covered by sister agents.

---

## 4. Published research using AlphaFold on dog (or dog-pathogen) proteins

All entries below were checked in full text via Europe PMC unless marked otherwise. "How AF was used" is quoted or paraphrased from the paper.

| # | Study | Target | How AF was used | Conf. |
|---|---|---|---|---|
| 1 | **Weng et al. 2025**, *Commun Biol* 8:1639 [11] | Canine TNFα | Cryo-EM of dog TNFα + nanobody at 3.1 Å, refined from an AF2 initial model. **AF3** models of dog TNFα–TNFR1 (pTM 0.90 / ipTM 0.89) and –TNFR2 (0.89 / 0.88) were used to pick hotspots ([verifier-corrected] the paper says "built using AlphaFold 3" and does not specify the Server; the pTM/ipTM values and the AlphaFold2 initial model for cryo-EM refinement are confirmed in the full text). De novo minibinders bound both dog and human TNFα with sub-nM to nM affinity. | ✅ |
| 2 | **Vijayasimha et al. 2025**, *Vet Sci* 12:649 [12] | Anti-canine PD-1 nanobody (STX-1b5) | AF3 Server model of the nanobody–cPD-1 complex. The interface at the C–C′ and F–G loops overlaps the PD-L1/PD-L2 sites, consistent with ELISA blocking. | ✅ |
| 3 | **Gingrich et al. 2023**, *ImmunoHorizons* 7:760 [22] | Canine NK receptor Ly49 | AF2 via ColabFold, templates off, 3 recycles, 5 models; docked to MHC-I | ✅ |
| 4 | **Furrow et al. 2023**, *Genes* 14:988 [13] | ABCC9 p.R1186Q (sudden cardiac death / DCM in Manchester Terriers) | Used the **human** AFDB model O60706 "because the only canine UniProt entry with a prediction … was incomplete with only 149 of the 1549 amino acids"; then Missense3D | ✅ |
| 5 | **Woerde et al. 2026**, *J Vet Intern Med* 40:aalaf046 [14] | CASR p.Glu649Lys (familial hypocalciuric hypercalcaemia-like) | AF3 model showing the variant in the transmembrane domain | ✅ |
| 6 | **Oliver et al. 2025**, *G3* 15:jkaf016 [15] | TTPA deletion (retinopathy, English Cocker Spaniel) | **Human** AF model of α-TTP to assess the deletion | ✅ |
| 7 | **Kawakami et al. 2022**, *PLoS One* 17:e0264365 [16] | EPS8L2 in-frame deletion (deafness, Rhodesian Ridgeback) | **Human and mouse** AF models showed the deleted VHFL residues lie in an α-helix | ✅ |
| 8 | **Gibbs et al. 2022**, *PLoS One* 17:e0277607 [33] | Dog bitter-taste receptor Tas2r10 | **Human** AF model used as the template for a dog homology model | ✅ |
| 9 | **Ryu et al. 2025**, *Front Vet Sci* 12:1609405 [17] | Canine GHRH gene therapy in **30 senior dogs (10–16 y)** | Human GHRH model from AFDB (AF-P01286-F1) for illustration. The canine GHRHR–GHRH complex was template-modelled (Discovery Studio, PDB 7V9M), **not** with AF. (Ageing-relevant; clinical outcomes are not assessed here.) | ✅ |
| 10 | **Cramer et al. 2026**, *Infect Immun* e00167-26 [24] | *Anaplasma* P44 (canine anaplasmosis diagnostics) | 1.65 Å crystal structure "consistent with AlphaFold v2 predictions". A DALI search against AFDB showed a new fold. Chimeric antigen ADC1: 100% sensitivity, 98.04% specificity. | 🟡 (abstract) |
| 11 | **Duraisamy et al. 2026**, *Microorganisms* 14:1721 [23] | Multi-epitope canine/feline parvovirus vaccine (in silico) | AF2 Colab for MHC alleles and the vaccine construct; docking to TLRs | ✅ (in silico only) |
| 12 | **Walther & Waring 2024**, *Biomedicines* 12:163 [34] | Canine surfactant protein C mimics | AlphaFold (via ChimeraX) models refined by MD | ✅ |
| 13 | **Min et al. 2023**, *Front Allergy* 4:1133412 [35] | Dog allergen **Can f 1** (lipocalin) | Can f 1 structures are *experimental* (crystal, NMR). AF was used only to model the comparison cat lipocalin Fel d 4. | ✅ |
| 14 | **Korec et al. 2025**, *Vet Anim Sci* 27:100420 [36] | **Longevity** GWAS in Cavalier King Charles Spaniels (9 candidate genes) | Cites AF2 and states that a longevity-linked PARP14 missense SNP "does not have any significant effect on the protein structure". The method behind that statement was not verified. **Caution: AF cannot assess point-mutation effects** [18]. | ❓ |

**Related experimental benchmark (not AF).** Crystal structures of dog SOD1 (wild type, E40K, M117L, E40K/M117L) show that the degenerative-myelopathy E40K variant causes **species-specific** aggregation through a vulnerable hydrophobic core [25][26] ✅. The SOD1 E40K association with canine DM was established by Awano et al. 2009 [37] ✅.

This is the kind of dog-specific, single-residue effect that AF is *not* designed to predict [18]. It makes a good **negative-control test case** for any AF/variant pipeline.

**Wolves.** My Europe PMC searches found **no** published study applying AlphaFold specifically to grey-wolf proteins ❓ (absence of evidence; searches were limited to titles/abstracts containing wolf/wolves plus AlphaFold).

**Pattern.** Most veterinary papers use AF (a) to visualise where a variant sits, often on the *human* model, or (b) to make a complex model for a biologic (nanobody, minibinder) aimed at a dog target. Few test predictions experimentally. Weng 2025, Vijayasimha 2025 and Cramer 2026 are the exceptions, with binding or diagnostic assays.

---

## 5. How AlphaFold-family tools could be used in dog-ageing research (PROPOSALS)

> These are **proposals**, not established results. Each is tied to a verified gap or capability above. "Ageing relevance" refers to biology covered by sister files (`04_dog_aging_biology/`, `05_interventions/`) that I did not verify here.

| # | Proposal | Why it is grounded | Tools | Key caveat |
|---|---|---|---|---|
| P1 | **Fill the dog structural gap for long ageing-pathway proteins.** Intersect a curated ageing/longevity gene list (e.g. human GenAge orthologs ❓) with the ~3,800 dog UniProt entries that lack AFDB models (>1,280 aa unreviewed or >2,700 aa). Model the hits with ColabFold, AF3 or Boltz-2, first checking and correcting the gene models. | Gap quantified in §2.2 ✅. IGF1R and MTOR are missing ✅. | ColabFold, AF3 (non-commercial), Boltz-2/Chai-1 | Garbage-in: dog gene models have N-terminal and exon errors (IGF1R, FKBP1A) ✅. Validate sequences against cDNA or RefSeq. |
| P2 | **Structural triage of coding variants from large dog cohorts** in growth and longevity genes (IGF1R, GHR, IGFBPs, PAPPA ❓, FOXO3, MTOR pathway) and in the CKCS longevity candidates [36]. Map variants onto models; flag interface or buried-core hits; prioritise for wet-lab assays. | Variant catalogues exist [32] ✅. Mock-human AlphaMissense is sensitive but non-specific [9] ✅. | AFDB / AF3 models + SIFT (Ensembl) + ESM-1b-style scores + mock-human AlphaMissense | **Do not** treat AF pLDDT changes as stability predictions [18] ✅. Most size and longevity signal may be **non-coding** (e.g. IGF1-AS [19]), which is outside AF's scope. |
| P3 | **Model the dog GH/IGF axis complexes** (GH:GHR 1:2, IGF-1:IGF1R, IGF-1:IGFBP3) with dog sequences, then map breed-associated coding variants onto the interfaces. | Worked example in `how_to_use_alphafold.md` §7. Dog GH is only 68% identical to human, so the dog complex is less trivially "memorised". | AF Server / AF3; Boltz-2 for comparison | Pre-2021 human complexes are in AF3's training data, so high ipTM partly reflects recall ✅. No affinity output from AF3. |
| P4 | **Design dog-specific biologics against ageing-relevant targets**, e.g. inflammaging cytokines. Precedents: dog/human TNFα minibinders [11] and an anti-canine PD-1 nanobody [12]. | Demonstrated workflow in dogs ✅ | RFdiffusion3 / RF3 (BSD), Boltz-2 (MIT), AF3 for triage (non-commercial), Protenix v1 | Antibody–antigen prediction is weak (65% single-seed failure for AF3 [38]) ✅. Wet-lab affinity tests and caninisation/immunogenicity checks are needed. Commercial programmes must avoid AF Server/AF3 outputs [21][39]. |
| P5 | **Check whether drug-target structure even differs between dog and human before modelling geroprotectors.** Example: for rapamycin, the dog mTOR FRB domain (human 2015–2114) is **100/100 identical** to human, and FKBP12 is near-identical (my alignments ✅). Structure is therefore *not* the bottleneck. Species differences lie in pharmacokinetics and metabolism (e.g. dog CYP2B11/2C21/2D15). | Alignments ✅; dog CYP modelling papers exist (homology models) [40] ✅ | AF3/Boltz-2 for dog CYPs + ligands (Boltz-2 for affinity) | AF Server terms forbid feeding outputs to docking/screening tools [39] ✅. Use open models for any screening. |
| P6 | **Benchmark AF-family tools on known dog-specific variants** (SOD1 E40K, ABCC9 R1186Q, CASR E649K) before using them predictively | Experimental dog SOD1 structures exist [25][26] ✅ | AF3/Boltz/ESM + stability predictors | Expected result: structure predictors will **not** capture destabilisation. A useful negative control. |
| P7 | **Dog vs wolf comparisons of ageing genes.** Use dog structural models plus wolf variant calls (8 wolves in [32]; larger sets elsewhere) to check whether coding differences fall in functional sites. | No wolf proteome exists; dog models suffice for the ~identical sequences ✅ | AFDB dog models + variant mapping | Domestication and lifespan differences are likely largely regulatory, which AF cannot address ❓ |
| P8 | **Regulatory variants**: try AlphaGenome-style sequence-to-function models on dog loci (e.g. IGF1-AS) | AlphaGenome weights are available for non-commercial use [20] ✅ | AlphaGenome (human/mouse-trained) | Cross-species transfer to dog is **untested** ❓. This would be a research project in itself. |

**What AlphaFold cannot do for dog ageing** (so as not to over-promise):
- It cannot predict lifespan, healthspan, or the effect of a gene edit on ageing.
- It cannot predict binding affinity or signalling strength (AF3).
- It cannot predict expression or regulatory effects.

At best it supplies **structural hypotheses** (where a variant sits, how two proteins likely dock, what a designed binder might look like). These must be tested experimentally [41] ✅.

---

## Open questions / gaps

- **No AF study of dog ageing proteins was found.** The literature search was via Europe PMC (titles, abstracts, open-access full text), because web search quota ran out. Non-open-access papers may be missed ❓.
- **Wolf-specific AF studies:** none found ❓.
- **Cross-species variant-effect predictors.** Beyond SIFT (Ensembl), mock-human mapping and protein language models, I did not find a validated dog-specific missense predictor. Sister agent `03_canine_bio_ai/` may cover this.
- **AFDB "47 other key organisms" vs 46 tarballs**: the FAQ says 46; the homepage figure appears stale [verifier-corrected].
- **Whether dog Swiss-Prot proteins are in the NVIDIA dimer set.** One FAQ sentence mentions Swiss-Prot, but the spot checks for dog GHR and IGF1 returned no complexes. I scanned only 2 entries.
- **Dog gene-model quality for IGF1R/FKBP1A.** I flagged anomalies but did not check against RefSeq or cDNA.

---

## Sources

1. Jumper J et al. (2021). Highly accurate protein structure prediction with AlphaFold. *Nature* 596:583–589. doi:10.1038/s41586-021-03819-2
2. Abramson J et al. (2024). Accurate structure prediction of biomolecular interactions with AlphaFold 3. *Nature* 630:493–500. doi:10.1038/s41586-024-07487-w
3. UniProt REST API, release 2026_03 (2 Sep 2026), queried 2026-10-04: `proteomes/search?query=organism_id:9615|9612|taxonomy_id:9612`; `proteomes/{UP000805418, UP000002254, UP000694429, UP000694542, UP000694391}.json` (proteome type, breed, assembly; description text stating the dog is a subspecies of the grey wolf); `uniprotkb/search` counts (X-Total-Results) for organism_id 9615/9612/286419/9606 with `reviewed`, `length`, `database:alphafolddb` and `proteome:` filters; entries Q8WNN6, A0A8I3RQ77, A0A8I3MER7, A0A8I3MJG3 (audit and sequence). https://rest.uniprot.org
4. AlphaFold DB API, queried 2026-10-04: `/api/prediction/{P33712, Q9TU69, P08069, P05019, P10912, A0A8I3RQ77, A0A8I3MER7, A0A5F4DDH2, Q8WNN6}`; `/api/complex/{Q9TU69, P33712, P10912}`; `/api/annotations/{P05019, P33712}.json`; `confidence_v6.json` files. https://alphafold.ebi.ac.uk/api
5. AlphaFold DB FTP, `latest/` directory listing (46 `*_v6.tar` proteome files; `swissprot_cif_v6.tar` 37 GB). https://ftp.ebi.ac.uk/pub/databases/alphafold/latest/ (accessed 2026-10-04)
6. AlphaFold DB FAQ and homepage ("Which proteins are included?", length limits 16–2,700 / 1,280 aa, non-standard residues, NVIDIA dataset description, "47 other key organisms"). https://alphafold.ebi.ac.uk/faq ; https://alphafold.ebi.ac.uk/ (accessed 2026-10-04)
7. Cheng J et al. (2023). Accurate proteome-wide missense variant effect prediction with AlphaMissense. *Science* 381:eadg7492. doi:10.1126/science.adg7492
8. google-deepmind/alphamissense README ("What we don't provide: The trained AlphaMissense model weights"; predictions for human transcripts). https://github.com/google-deepmind/alphamissense (accessed 2026-10-04)
9. Hu H, Xie W (2025). Human genomic tools to assess missense variant pathogenicity in domestic mammals using a mock-variant strategy. *Open Vet J* 15(10):5183–5191. doi:10.5455/ovj.2025.v15.i10.35
10. Ensembl REST API, `vep/canis_lupus_familiaris/hgvs/ENSCAFT00845016630:c.200G>A` (returned `sift_prediction`, no PolyPhen), queried 2026-10-04. https://rest.ensembl.org
11. Weng J et al. (2025). Design of minibinder proteins as universal antagonists against canine and human TNFα. *Commun Biol* 8:1639. doi:10.1038/s42003-025-09030-7
12. Vijayasimha K et al. (2025). Characterization of a potential therapeutic anti-canine PD-1 single domain antibody produced in yeast. *Vet Sci* 12:649. doi:10.3390/vetsci12070649
13. Furrow E et al. (2023). An ABCC9 missense variant is associated with sudden cardiac death and dilated cardiomyopathy in juvenile dogs. *Genes* 14:988. doi:10.3390/genes14050988
14. Woerde DJ et al. (2026). A novel missense variant in the calcium-sensing receptor gene in a dog with hypercalcemia. *J Vet Intern Med* 40:aalaf046. doi:10.1093/jvimsj/aalaf046
15. Oliver JAC et al. (2025). A TTPA deletion is associated with retinopathy with vitamin E deficiency in the English Cocker Spaniel dog. *G3* 15:jkaf016. doi:10.1093/g3journal/jkaf016
16. Kawakami T et al. (2022). Early onset adult deafness in the Rhodesian Ridgeback dog is associated with an in-frame deletion in the EPS8L2 gene. *PLoS One* 17:e0264365. doi:10.1371/journal.pone.0264365
17. Ryu MO et al. (2025). Wellness-enhancing effects of the canine growth hormone releasing hormone therapy mediated by plasmid and electroporation in healthy old dogs. *Front Vet Sci* 12:1609405. doi:10.3389/fvets.2025.1609405
18. Pak MA et al. (2023). Using AlphaFold to predict the impact of single mutations on protein stability and function. *PLoS One* 18:e0282689. doi:10.1371/journal.pone.0282689
19. Plassais J et al. (2022). Natural and human-driven selection of a single non-coding body size variant in ancient and modern canids. *Curr Biol* 32(4):889–897.e9. doi:10.1016/j.cub.2021.12.036
20. Avsec Ž et al. (2026). Advancing regulatory variant effect prediction with AlphaGenome. *Nature* 649:1206–1218. doi:10.1038/s41586-025-10014-0 ; google-deepmind/alphagenome_research README (weights via Kaggle/Hugging Face, non-commercial terms)
21. AlphaFold Server FAQ. https://alphafoldserver.com/faq (accessed 2026-10-04)
22. Gingrich AA et al. (2023). Missing a "missing self" mechanism: modeling and detection of Ly49 expression in canine NK cells. *ImmunoHorizons* 7:760–770. doi:10.4049/immunohorizons.2300092
23. Duraisamy N et al. (2026). Immunoinformatics-guided computational design and in silico validation of multi-epitope vaccine candidates targeting canine and feline parvoviruses. *Microorganisms* 14:1721. doi:10.3390/microorganisms14081721
24. Cramer NA et al. (2026). Structure-guided design of Anaplasma P44 protein-based chimeric antigens for serodiagnosis of anaplasmosis in dogs. *Infect Immun* e00167-26. doi:10.1128/iai.00167-26
25. Hashimoto K et al. (2023). Intrinsic structural vulnerability in the hydrophobic core induces species-specific aggregation of canine SOD1 with degenerative myelopathy-linked E40K mutation. *J Biol Chem* 299:104798. doi:10.1016/j.jbc.2023.104798 ; PDB 7WWT, 7WWY, 7WX0, 7WX1 (RCSB metadata checked 2026-10-04)
26. Shino Y et al. (2024). Disulfide-mediated oligomerization of mutant Cu/Zn-superoxide dismutase associated with canine degenerative myelopathy. *Protein Sci* 33:e5210. doi:10.1002/pro.5210 ; PDB 8ZD5, 8ZD6
27. Brown E et al. (2026). A variant in RESF1 is associated with Addison's disease and multiple autoimmune syndrome in young Nova Scotia Duck Tolling Retrievers. *Sci Rep* 16:13194. doi:10.1038/s41598-026-42994-y
28. Zhang SJ et al. (2025). Determinants of de novo mutations in extended pedigrees of 43 dog breeds. *Genome Biol* 26:305. doi:10.1186/s13059-025-03804-2
29. Yang YT et al. (2024). Canine histiocytic and hemophagocytic histiocytic sarcomas display KRAS and extensive PTPN11/SHP2 mutations… *Genes* 15:1050. doi:10.3390/genes15081050
30. Haque B et al. (2024). A comparative medical genomics approach may facilitate the interpretation of rare missense variation. *J Med Genet* 61:817–821. doi:10.1136/jmg-2023-109760
31. Brandes N et al. (2023). Genome-wide prediction of disease variant effects with a deep protein language model. *Nat Genet* 55:1512–1522. doi:10.1038/s41588-023-01465-0
32. Jagannathan V, Drögemüller C, Leeb T, Dog Biomedical Variant Database Consortium (2019). A comprehensive biomedical variant catalogue based on whole genome sequences of 582 dogs and eight wolves. *Anim Genet* 50:695–704. doi:10.1111/age.12834
33. Gibbs M et al. (2022). Bitter taste sensitivity in domestic dogs (Canis familiaris) and its relevance to bitter deterrents of ingestion. *PLoS One* 17:e0277607. doi:10.1371/journal.pone.0277607
34. Walther FJ, Waring AJ (2024). Structure and function of canine SP-C mimic proteins in synthetic surfactant lipid dispersions. *Biomedicines* 12:163. doi:10.3390/biomedicines12010163
35. Min J et al. (2023). Structural and ligand binding analysis of the pet allergens Can f 1 and Fel d 7. *Front Allergy* 4:1133412. doi:10.3389/falgy.2023.1133412
36. Korec E et al. (2025). Identification of genes associated with longevity in dogs: 9 candidate genes described in Cavalier King Charles Spaniel. *Vet Anim Sci* 27:100420. doi:10.1016/j.vas.2024.100420
37. Awano T et al. (2009). Genome-wide association analysis reveals a SOD1 mutation in canine degenerative myelopathy that resembles amyotrophic lateral sclerosis. *PNAS* 106:2794–2799. doi:10.1073/pnas.0812297106
38. Hitawala FN, Gray JJ (2025). What does AlphaFold3 learn about antibody and nanobody docking, and what remains unsolved? *mAbs* 17:2545601. doi:10.1080/19420862.2025.2545601
39. AlphaFold Server Additional Terms of Service (Last Modified 8 May 2024). https://alphafoldserver.com/terms ; AlphaFold 3 Model Parameters Terms of Use (2024-11-09). https://github.com/google-deepmind/alphafold3/blob/main/WEIGHTS_TERMS_OF_USE.md
40. Soares-Santos RR et al. (2025). Interactions of linalool and linalyl acetate with selected dog cytochrome P450 (CYP) proteins… *Pharmaceuticals* 18:1499. doi:10.3390/ph18101499 (used SWISS-MODEL homology models, not AF; cited only as precedent for dog CYP modelling)
41. Terwilliger TC et al. (2024). AlphaFold predictions are valuable hypotheses and accelerate but do not replace experimental structure determination. *Nat Methods* 21:110–116. doi:10.1038/s41592-023-02087-4

---

## Verification notes

*Independent check by Fable 5.1, 2026-10-04. Full report: `../07_verification/alphafold_verification.md`.*

- **Every live-query number was reproduced** against UniProt REST (release 2026_03) and the AFDB API on 2026-10-04: 46,473 / 42,123 dog entries with AFDB models; 857 / 809 reviewed; 43,615 / 39,585 in UP000805418; 41,779 / 41,313 unreviewed 16–1,280 aa; 3,357 / 1 unreviewed 1,281–2,700 aa; 41 / 37 reviewed 1,281–2,700 aa; 453 / 0 above 2,700 aa; wolf 199 / 197 with no proteome; dingo 33,945 / 31,000 and reference proteome UP000694391 (33,928); human reviewed 20,431. All five proteome rows (breed, type, assembly, protein count) match UniProt. The dog SOD1 sequence (Q8WNN6) does carry X at residue 53, and `/api/prediction/Q8WNN6` returns `{}`; the IGF1R, MTOR, ABCC9 and RESF1 entries return `{}`; the fragment and small entries listed as modelled are modelled.
- **AFDB rules and datasets** (FAQ read in a browser): the 16–2,700 / 16–1,280 aa limits, non-standard-residue and one-sequence-per-gene exclusions, 46 downloadable proteomes, the NVIDIA (March 1,754,199 homodimers; May ~2.2 M from 4,777 proteomes, 16 model organisms + 30 WHO) and viral-complex (1,703,992) datasets all match.
- **Literature**: Hu & Xie 2025 (284 deleterious / 90 non-deleterious; sensitivity 0.77–0.90, specificity 0.20–0.46, auROC 0.55–0.61), Haque 2024 (56 classified, 55.4%, OR 7.0), Weng 2025 (ipTM 0.89/0.88, 3.1 Å, AF2 initial model), Vijayasimha 2025 (AF3 server, C–C′/F–G loops), Furrow 2023 ("149 of the 1549"), Ryu 2025 (30 senior dogs 10–16 y; AF-P01286-F1; Discovery Studio with 7v9m), Brown 2026 (AlphaMissense 0.82), Zhang 2025 (MLH1 p.D375N), Yang 2024 (99.3%), Gingrich 2023, Kawakami 2022, Oliver 2025, Woerde 2026, Gibbs 2022, Min 2023, Walther 2024, Duraisamy 2026, Korec 2025, Hashimoto 2023 (PDB 7WWT/7WX0/7WWY/7WX1), Shino 2024 (8ZD5), Plassais 2022 (~15%), Pak 2023, Terwilliger 2024, Hitawala & Gray 2025 were all checked in Europe PMC full text or abstracts; metadata for all 41 sources resolved via Crossref. Cramer 2026 remains abstract-only.
- **Alignments** quoted from `how_to_use_alphafold.md` §7 (mature IGF-1 100%, IGF1R 98.1%, GHR 82.3%, GH 68.4%, mTOR FRB 100/100, FKBP1A 91/92 with the 16-residue gap) were re-computed and reproduce exactly.
- **Corrected in place** (`[verifier-corrected]`): Weng 2025 used "AlphaFold 3", not explicitly the Server; the 46-vs-47 proteome count is resolved by the FAQ's own "46"; the NVIDIA-dataset scope sentence in the TL;DR now carries the Swiss-Prot caveat. No numbers needed changing.
- **Still open:** a dog-specific missense predictor; wolf-specific AF studies; whether any dog Swiss-Prot proteins are in the NVIDIA dimer set (only 2 spot checks); IGF1R/FKBP1A gene-model quality vs RefSeq.
