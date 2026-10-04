# Dog & Wolf Biological Foundation Models: Landscape (as of 2026-10-04)
> Part of the dog-ageing research dossier · Written 2026-10-04 by Fable 5.1 subagent · Status: independently verified by Opus 5.5 on 2026-10-04 — see ../07_verification/canine_bio_ai_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

Confidence tags: ✅ = confirmed in a primary source I opened (paper, dataset file, official page, API); 🟡 = reputable secondary source or abstract/search-summary only; ❓ = unconfirmed / inferred / contested.

## TL;DR

- **There is no dog- or wolf-specific *molecular* foundation model** (protein, DNA, single-cell) as of October 2026. Searches of bioRxiv/arXiv/PubMed and the Hugging Face Hub API for "canine", "canfam", "dog genome" and "veterinary" returned no canine genomic/protein/cell model; "canine" on Hugging Face returns 176 models, overwhelmingly Google's CANINE character-level NLP model and its fine-tunes, plus a handful of small dog-related *task* models (e.g. a canine dermatology classifier, a body-condition-score model, ResNet cytology classifiers, a "canine-health" Mistral-7B LoRA) — none a biological foundation model [verifier-corrected: author reported "57 variants, all CANINE"; limit=1000 query returns 176 and they are not all CANINE]; "veterinary" returns 13 small fine-tunes (chat LLMs, Whisper adapters, one cardiomegaly segmentation model) [1][2][3]. ✅ **Caveat [verifier-added]:** dog-specific *imaging* foundation models do exist — VET-DINO, a self-supervised model trained on 5 million radiographs from 668,000 canine studies (arXiv 2505.15248, May 2025), and V-REX, a veterinary-radiograph vision-language model (arXiv 2608.20069, Aug 2026) [71][72] ✅ (abstracts). They are not molecular/biological-sequence models, so the molecular headline stands.
- **Dogs are nevertheless covered by several species-agnostic models — but unevenly, and you have to check the training file, not the paper abstract.** I downloaded the actual species lists: Evo 2's OpenGenome2 *does* contain a domestic-dog nuclear genome (GCF_011100685.1 = UU_Cfam_GSD_1.0, a German Shepherd assembly) plus six other canid genomes and ~15 canid mitogenomes [4][5][6] ✅, and also Ensembl ncRNA sets for dog (reference + Basenji, Boxer, Great Dane and GSD assemblies) and dingo, and Ensembl mRNA transcripts for dog (26,040) and dingo (7,145) [4] ✅ [verifier-added]; InstaDeep's **Nucleotide Transformer v3** (bioRxiv Dec 2025) was pre-trained on OpenGenome2 and therefore also saw the dog genome [73] ✅ [verifier-added]; the Nucleotide Transformer's 850-genome set has **no** *Canis lupus familiaris* — only the dingo (*Canis lupus dingo*) and Arctic fox [7][8] ✅; DNABERT-2's 135 species include only 7 mammals, none canid [9] ✅.
- **Protein side is fully covered**: dog proteins are in UniProt (reference proteome UP000805418, Labrador, 43,615 proteins; three more breed proteomes) and therefore in UniRef-trained protein LMs (ESM family) and in AlphaFold DB (e.g., dog albumin P49822, model v6, 2025-08-01) [10][11][12]. ✅ (Dog is *not* among AFDB's per-organism bulk-download archives — the v6 FTP listing has no 9615/CANLF file; dog structures come per-entry or via the full UniProt dump [verifier-added].)
- **Regulatory-genomics models (AlphaGenome, Enformer, Borzoi) are human+mouse only**; AlphaGenome's FAQ says performance on other species "has not been determined" and outputs are non-commercial [13]. ✅ A canine AlphaGenome-type model does not exist — but the raw material now does (DoGA: a tissue biobank of 5,485 samples, 132 tissues, 13 dogs, 12 embryos and 24 wolves, from which a STRT2-seq promoter/expression atlas of 100 tissues from 9 dogs + 12 embryos was published in 2024; plus a 2026 CAGE enhancer/promoter atlas from 9 dogs) [14][15]. ✅ [verifier-corrected: the author called the 2024 resource a "CAGE atlas" of 5,485 samples including wolves; 5,485/24 wolves describes the biobank, the 2024 atlas used STRT2-seq and profiled no wolves, and CAGE appears only in the 2026 preprint]
- **Single-cell foundation models exclude dog from training** (UCE: 8 species; TranscriptFormer: 12 species; GeneCompass/scGPT/Geneformer: human ± mouse) but UCE and TranscriptFormer are explicitly designed for zero-shot embedding of unseen species via protein-language-model gene embeddings [16][17][18][19]. ✅ The Chinese scCompass database (104.6M cells, 13 species) *does* include dog (aligned to UU_Cfam_GSD_1.0) and is built to feed foundation-model training [20]. ✅ It also distributes GeneCompass/scGPT/Geneformer checkpoints pre-trained on scCompass subsets; whether any of those checkpoints contain dog cells is not stated ❓ [verifier-added].
- **The only "foundation-model-like" artefact already validated in dogs is the pan-mammalian methylation clock**: the Mammalian Methylation Consortium's universal clocks (11,754 arrays, 185 species) give r = 0.94 and MAE < 2.28 yr in dogs (n = 742, 93 breeds) [21][22]. ✅ Whether gray wolves are in the 185-species panel is not stated in the main text (verifier grep of the Europe PMC full text: zero hits for "wolf", "wolves", "Canis") ❓; a separate 2017 dog+wolf clock exists (46 dogs, 62 wolves) [23]. ✅
- **Canine-specific AI exists at the task level, not the foundation level**: epigenetic clocks (several groups, 2022–2026), veterinary clinical-text LMs (PetBERT, VetLLM), radiology AI (SignalPET, Zoetis Vetscan Imagyst "AI Masses" 2025), precision-oncology survival analysis (Cox regression) on 2,119 dogs (FidoCure/Stanford) [verifier-corrected: statistical, not ML], and statistical/network modelling on Dog Aging Project data (26,614 dogs) [24]–[33]. ✅/🟡
- **Variant-effect prediction for dogs currently piggybacks on human tools** (AlphaMissense/ESM-1b/PolyPhen-2 via a "mock-variant" mapping; sensitivity 0.77–0.90 but specificity only 0.20–0.46 — ranges are across the three tools on 374 variants pooled from 8 species, 126 of them dog) [34]. ✅ [verifier-corrected wording: the ranges vary by tool, not by species] A dog-trained VEP does not exist; the 2026 CanVAS imputed atlas (15,451 dogs, 9.7M variants, CC-BY) is the obvious substrate [35]. ✅
- **Practical conclusion**: a dog-ageing AI project should (a) reuse Evo 2 / ESM / AFDB / UCE-TranscriptFormer zero-shot for dog sequences and cells, (b) treat Horvath-array clocks as the mature cross-species biomarker, and (c) target the real gap — a canine regulatory-sequence model and a canine VEP trained on Dog10K + DoGA + DAP data.

---

## 1. Direct answer: is there a dog/wolf-specific foundation model?

**No (for molecular modalities).** As of 2026-10-04 I found no pre-trained, self-supervised, large-scale model whose training corpus is dog- or wolf-specific in any of the four modalities. Evidence of absence (necessarily weaker than evidence of presence). [verifier-added: an independent re-search on 2026-10-04 (Hugging Face models + datasets for canine/canis/canfam/dog genome/dog DNA/dog single cell/CanineGPT/DogGPT/PetGPT/pet genome/vet foundation/wolf genome; Europe PMC incl. bioRxiv preprints; arXiv API) also found no dog-specific protein, DNA or single-cell FM. It did find dog-specific *radiograph* FMs (VET-DINO 2025; V-REX 2026) [71][72], several new cross-species single-cell FMs that do not list dog (LucaCell, Sep 2026 — trained on 85 M human + mouse cells; EpiZoo, Sep 2026 — scATAC, species list not given in abstract ❓), and NTv3 (pre-trained on OpenGenome2, which includes the dog genome) [73].]

| Search | Result | Confidence |
|---|---|---|
| Hugging Face Hub API `search=canine` (50 results) | ~~57 hits, all Google **CANINE**~~ 176 hits at limit=1000 (limit=50 caps at 50): mostly Google **CANINE** character-level NLP fine-tunes, plus a few small dog-related task models (dermatology/cytology image classifiers, body-condition score, a "canine-health" Mistral LoRA); zero biological foundation models [1] [verifier-corrected] | ✅ |
| Hugging Face API `search=canfam`, `search=dog genome` | empty result sets [2] | ✅ |
| Hugging Face API `search=veterinary` | 13 models: Flan-T5 vet-QA, Whisper-medium veterinary adapters, GPT-2/Qwen/Llama-3.1 veterinary chat LoRAs, one cardiomegaly segmentation model — none genomic [3] | ✅ |
| Web/bioRxiv/arXiv queries ("canine foundation model", "dog genome language model", "Canis lupus familiaris transformer", "veterinary foundation model") | returned only general human/multi-species scFMs and genomic LMs; the dog hits were data resources (DoGA, CanVAS, Dog10K), not models [14][15][35][36] | 🟡 (search coverage limited) |

What exists instead is (i) multi-species models that happen to include dog sequence (Section 2), (ii) large canine data resources now big enough to fine-tune on (Section 3.6), and (iii) narrow canine task models (Section 3). The nearest things to a "canine foundation model" are **PetBERT** (a veterinary-EHR language model — text, not biology) [29], **VET-DINO** (self-supervised vision model on 5 M canine radiographs — imaging, not molecular) [71] [verifier-added], and the **Horvath mammalian-array clocks** (a cross-species predictor validated in 742 dogs) [21][22].

---

## 2. Species-agnostic / multi-species models — training-data audit

I prioritised opening the actual species files over trusting abstracts. Where I could not open the file, the row is marked 🟡/❓.

### 2.1 Protein models

| Model | Dog data? | Evidence | Notes |
|---|---|---|---|
| UniProt / UniRef (substrate for ESM-2, ESM3, ESM C) | **Yes** | UniProt lists four *C. l. familiaris* proteomes: UP000805418 (reference; Labrador retriever GCA_014441545.1; 43,615 proteins), UP000002254 (Boxer; 41,817), UP000694429 (Basenji; 42,651), UP000694542 (Great Dane; 42,573) [10] ✅ | ESM-2 was trained on UniRef50/UniRef90 clusters [37] 🟡; because UniRef is derived from all of UniProtKB, dog proteins are in the corpus (inference, not a per-sequence check) 🟡. ESM-2 is MIT-licensed; ESM3/ESM C have mixed open/non-commercial licences 🟡 |
| AlphaFold DB | **Yes** | API entry for P49822 returns "Albumin", *Canis lupus familiaris*, taxId 9615, modelCreatedDate 2025-08-01, latestVersion 6 [11] ✅ | AFDB covers >214 M UniProt sequences [12] ✅; bulk-download page lists 48 organisms — **dog is not among them** (v6 FTP listing has no 9615/CANLF archive) ✅ [verifier-corrected from ❓] |

### 2.2 DNA / genome language models

| Model (size) | Training genomes | Dog / wolf in training? (with evidence) | Licence |
|---|---|---|---|
| **Evo 2** (7B, 40B; Arc Institute; Nature 652:1349–1361, 4 Mar 2026) | OpenGenome2: >8.8 T nt across bacteria, archaea, eukarya, phage [38]; eukaryotes = 16,704 NCBI reference genomes (downloaded May 2024) → 15,032 representatives, 6.98 T nt [39] 🟡 | **Yes (domestic dog).** `species_metadata.csv` lists `Eukaryote, NCBI_Eukaryotic_Genomes, GCF_011100685.1 … Canidae, Canis, Canis lupus, assembly_level=Chromosome` [4] ✅; NCBI identifies GCF_011100685.1 as **UU_Cfam_GSD_1.0, *Canis lupus familiaris*** (German Shepherd Dog assembly) [5] ✅. Other canid nuclear genomes in the file: *Urocyon cinereoargenteus*, *Vulpes ferrilata*, *Chrysocyon brachyurus*, *Nyctereutes procyonoides*, *Lycaon pictus*, *Otocyon megalotis*; mitogenomes for *C. lupus*, *C. latrans*, *C. rufus*, *C. simensis*, *C. aureus*, *C. lupaster*, *Cuon alpinus* and others [4] ✅. The file has 15,653 eukaryote rows (15,044 NCBI nuclear genomes + 338 Ensembl ncRNA + 271 Ensembl mRNA sets; organelles are a separate 32,240-row domain) and 2,037 rows tagged Mammalia (this count does include organelle records; 524 mammalian nuclear genomes) [4] ✅ [verifier-corrected breakdown]. **Also in the file [verifier-added]:** Ensembl ncRNA for *C. l. familiaris* and its Basenji, Boxer, Great Dane and GSD assemblies plus dingo, and Ensembl mRNA transcripts for dog (26,040) and dingo (7,145) [4] ✅ | Dataset Apache-2.0 [6] ✅; Evo 2 weights Apache-2.0 on HF ✅ |
| **Nucleotide Transformer v1/v2 multi-species** (InstaDeep; 500M–2.5B) | 850 genomes, 174 B nt: 667 bacteria, 46 fungi, 39 invertebrates, 10 protozoa, **31 mammals**, 57 other vertebrates; "one species per genus" per the card, though the URL list has both *Mus musculus* and *Mus caroli* [verifier-corrected]; no plants/viruses [7] ✅ | **No *C. l. familiaris*.** `original_urls.csv` (850 lines) contains `vertebrate_mammalian/Canis_lupus_dingo/…GCF_012295265.1_UNSW_AlpineDingo_1.0` and `Vulpes_lagopus` (Arctic fox); no *familiaris*, no gray wolf [8] ✅. Mammals present include *Homo sapiens*, *Mus musculus*, *Rattus*, *Gorilla*, *Nomascus*, *Saimiri*, *Tupaia*, *Ornithorhynchus*, *Phascolarctos*, *Panthera*, *Lynx*, *Puma*, *Zalophus*, *Myotis*, *Erinaceus*, *Choloepus*, *Neophocaena* [8] ✅ | CC-BY-NC-SA 4.0 [40] ✅ |
| **Nucleotide Transformer v3 (NTv3)** (InstaDeep; bioRxiv 2025.12.22.695963, posted 25 Dec 2025) [verifier-added] | Pre-trained on ~9 T bp from **OpenGenome2**; post-trained on ~16,000 functional tracks/annotations from 24 animal and plant species [73] ✅ (abstract) | **Yes, at pre-training** (OpenGenome2 contains GCF_011100685.1, see Evo 2 row) ✅ by inference from the dataset file + abstract; dog is **not** named among the post-training species 🟡 (full text read via summariser) | 8M–650M checkpoints on HF (`InstaDeepAI/NTv3_*`), gated, licence tag "other" ✅ |
| **DNABERT-2** (ICLR 2024) | 135 species, 32.49 B nt, 6–7 categories [9] ✅ | **No.** Appendix Table 11 "Mammalian" = *Bubalus bubalis*, *Camelus dromedarius*, Human, *Macaca assamensis*, *Macaca nigra*, *Mus musculus*, *Peromyscus californicus* (7 species); zero hits for "Canis"/"dog" in the PDF text [9] ✅ | Open (GitHub/HF) 🟡 |
| **GPN-MSA** (Song lab; Benegas et al., *Nat Biotechnol* 43(12):1960–1965, online 2 Jan 2025, doi:10.1038/s41587-024-02511-w [41] ✅) | Human genome conditioned on the UCSC hg38 100-way vertebrate MSA [41] 🟡 | **Dog is an aligned species**: UCSC multiz100way README lists "Dog — *Canis lupus familiaris* — Sep 2011 — Broad CanFam3.1/canFam3 — Syntenic net"; no wolf/fox [42] ✅ | The model scores *human* variants; dog is context, not target. Reusing it for dog variants would need a dog-centred MSA and retraining 🟡 |
| **Caduceus** (Cornell, 2024) | hg38 human reference only [43] ✅ | No | Open weights (HF) ✅ |
| **HyenaDNA** | Human reference only 🟡 | No | — |
| **AlphaGenome** (Google DeepMind, 2025/2026) | Human + mouse; predicts 5,930 human / 1,128 mouse tracks [13][44] | **No.** FAQ: "trained and evaluated on human and mouse DNA. Its performance on DNA from other species has not been determined" and "prediction quality is likely to degrade as evolutionary distance … increases … not formally benchmarked" [13] ✅ | Outputs non-commercial research use only; commercial via Google Cloud [13] ✅ |
| **Enformer / Borzoi** (DeepMind / Calico) | Human + mouse 🟡 | No | Open 🟡 |

### 2.3 Single-cell foundation models

| Model | Training species | Dog? | Zero-shot to new species? | Evidence |
|---|---|---|---|---|
| **UCE** (Stanford/Leskovec; *Nature* 656:183–191, online 8 Jul 2026 [verifier-corrected citation]) | "eight species: human, mouse, mouse lemur, zebrafish, pig, rhesus macaque, crab eating macaque and western clawed frog"; 36 M cells, >300 datasets [16] ✅ | No (not mentioned) ✅ | Yes — "able to align datasets from novel species without additional model training"; tested on green monkey, naked mole-rat, chicken [16] ✅ | genes represented via protein-LM embeddings, so dog proteome can be fed in |
| **TranscriptFormer** (CZI, 2025 preprint) | TF-Sapiens: human only; TF-Exemplar: human, mouse, zebrafish, fruit fly, *C. elegans*; TF-Metazoa (112 M cells): human, mouse, rabbit, chicken, African clawed frog, zebrafish, sea urchin, *C. elegans*, fruit fly, freshwater sponge, yeast, malaria parasite [17] ✅ | No ✅ | Yes — out-of-distribution species supported via ESM-2 protein embeddings [17] ✅ | weights on CZI S3; repository is **MIT-licensed** (LICENSE.md, © 2025 CZI); no separate weights licence stated [17] ✅ [verifier-corrected: author wrote "README states no licence"] |
| **SATURN** (Rosen … Leskovec, *Nat Methods* 21:1492–1500, 2024; PMID 38366243) | Not a pretrained FM: a cross-species integration method applied to "three species whole-organism atlases and frog and zebrafish embryogenesis datasets" [45] ✅ | No ✅ (abstract) | By design (protein-embedding gene space) ✅ [45] | |
| **GeneCompass** (CAS; Cell Research 34:830–845, 2024) | >120 M human + mouse cells (101,768,420 after QC) [18] ✅ (abstract) [verifier-upgraded] | No | — | sister resource **scCompass** (Advanced Science 2025): 104,637,783 cells, 15,270 samples after QC (15,337 before), **13 species incl. dog** (dog reads aligned to UU_Cfam_GSD_1.0), explicitly built as AI-ready input for GeneCompass/scGPT/Geneformer training [20] ✅; ships pre-trained checkpoints whose species mix is not stated ❓ [verifier-added] |
| **scGPT, Geneformer** | Human only [19] 🟡 (Mouse-Geneformer, 21 M mouse cells, PLoS Genet 2025 🟡) | No | — | |

### 2.4 Epigenetic (pan-mammalian) clocks

| Resource | Species coverage | Dog / wolf | Evidence |
|---|---|---|---|
| **Mammalian Methylation Consortium** universal clocks (Lu et al., Nat Aging 2023) | 11,754 arrays, 59 tissues, 185 species, 19 orders, HorvathMammalMethylChip40 (~36 k conserved CpGs) [21] ✅ | Dogs: "including dogs (n = 742, 93 breeds, r = 0.94, MAE < 2.28 years)" (leave-one-species-out, Clocks 2 and 3) [21] ✅ (verifier re-grepped full text). Wolves: no mention in main text (0 hits for wolf/Canis); species list is in Supplementary Data 1 — **unverified** ❓ | Raw data in GEO (GSE147002–4, GSE162662, GSE164127, GSE173330, GSE174544, GSE174758/67/77/78, GSE184211–23 and more) [21] ✅; code/manifests at github.com/shorvath/MammalianMethylationConsortium [46] ✅ |
| Haghani et al., Science 2023 (methylation networks) | 15,456 profiles, 348 species [47] ✅ | not checked for canids ❓ | |
| Horvath et al., PNAS 2022 "DNA methylation clocks for dogs and humans" | 742 blood samples, 93 breeds; dual-species human–dog clocks R = 0.97; EWAS of breed-weight/lifespan CpGs [22] ✅ | Dog ✅ (coauthors include Ostrander/NHGRI; affiliations UCLA, Altos Labs, NHGRI — **no Embark coauthor found in the full text**, contrary to one search summary) ✅ | |
| Thompson, vonHoldt, Horvath, Pellegrini, *Aging* 9(3):1055–1068, 2017 | 46 dogs + 62 wild gray wolves; 41-CpG (dog), 67-CpG (wolf) and 115-CpG (combined) estimators [23] ✅ | Dog + wolf ✅ | RRBS-based, not array |

---

## 3. Canine-specific ML/AI in research — concrete examples

### 3.1 Dog epigenetic / biological-age clocks (the most mature "AI-for-dog-ageing" area)

| Study | Data | Method & result | Status |
|---|---|---|---|
| Horvath et al. 2022 PNAS [22] | 742 blood, 93 breeds, mammalian array | penalised regression clocks; dog–human dual clocks R = 0.97 | published ✅ |
| Jin, McCoy, … Snyder-Mackler, Promislow 2024 Aging Cell [24] | 71 healthy dogs, 1–16 y; RRBS (13,336 CpGs) + ATAC-seq (15,417 peaks) | elastic net, LOO-CV; DNAm clock R² = 0.33, RMSE 3.08 y; ATAC clock R² ≈ 0.26; data SRA PRJNA1049514 / PRJNA1048909; code GitHub kleejin/canine_epigenetic_clock | published ✅ |
| McCoy, Mariner, … Snyder-Mackler 2024 bioRxiv (Dog Aging Project) [25] | 864 DAP dogs, >3 M CpGs, some sampled 2–3 years | largest breeds' epigenomes ~0.37 y older per chronological year vs smallest; 34 % higher death risk per year of residual epigenetic age | preprint, no journal version found as of Oct 2026 ✅ |
| Armero, Buckley, … Ostrander 2024 Aging [26] | co-analysis of methylation platforms | biological-age clocks "affected by population stratification and require heavy parameterization" | published ✅ (abstract) |
| Jang, Kim, Kang, … Kim 2026 PNAS 123(29):e2528874123 (Gyeongsang Natl Univ / NIAS, Korea — affiliations not re-checked) [27] | Korean vs US dogs | entropy/variance "epigenetic drift" analysis; consistently higher epigenetic age acceleration in Korean dogs; drift varies by body size | published 13 Jul 2026 ✅ (abstract, Europe PMC) [verifier-upgraded] |
| Kang, Bok, … Kim 2026 GeroScience [28] | healthy beagles, 3 age groups; methylome + transcriptome | rising variability with age; loss of CpG–gene coupling; early-/late-/progressive-shift CpG classes | published online 17 Sep 2026 ✅ (abstract, Europe PMC) [verifier-upgraded] |
| **Embark Age Test** (commercial) [48] | methylation-based; launched 4 Oct 2022, US$159 | company claims 70 % of dogs within ±5 months, 92 % within ±10 months | marketing claim, no peer-reviewed validation found 🟡 |

### 3.2 Variant-effect prediction
- Hu & Xie 2025, *Open Vet J* 15(10):5183–5191: mapped 374 animal missense variants (126 dog, 93 cattle, 60 cat, 43 horse, …) onto human orthologues ("mock-variant" strategy) and scored with AlphaMissense, ESM-1b, PolyPhen-2; on the pooled set, sensitivity 0.77 (AlphaMissense) / 0.86 (ESM-1b) / 0.90 (PolyPhen-2) and specificity 0.46 / 0.32 / 0.20 respectively, auROC 0.55–0.61 (dog-specific values not separately reported; dogs were the reference group in species-adjusted regressions) [34]. ✅ [verifier-corrected: ranges are across tools, not "across species"] This is the state of the art — i.e., *no dog-trained VEP exists*.
- Substrates now available: Dog10K harmonised variant set (52.96 M SNVs per the NAR database Table 1 — note the same paper's text says 34.6 M SNVs, and the Genome Biology paper reports ">48 M" SNVs + indels + SVs [verifier-added]; 1,987 canids) [36][49] ✅; **CanVAS** (Brundage, UW–Madison, bioRxiv 15 Apr 2026): 15,451 dogs from 15 public datasets harmonised to CanFam4 and imputed against the Dog10K panel (1,929 dogs, Beagle 5.4) → 9.7 M variants incl. ~3 M rare; Zenodo (record 19186944, published 23 Mar 2026, licence cc-by-4.0 confirmed via Zenodo API) + GitHub [35] ✅.

### 3.3 Canine cancer genomics ML
- **FidoCure / One Health Company + Stanford (Zou lab)** — Wu et al. 2023 *npj Precision Oncology* 7:8: real-world clinico-genomic data on 2,119 tumour-bearing dogs (1,108 with genomics), 48 targeted genes sequenced (mean 2.4 mutated genes/dog), 10 targeted therapies; Cox proportional-hazards survival analysis of prognosis and treatment response (statistical modelling, not ML) [30]. ✅ [verifier-corrected wording] Company markets "proprietary AI/ML" therapy matching 🟡 [50].
- **NCI Integrated Canine Data Commons (ICDC)** — part of NCI's Cancer Research Data Commons; built by Frederick National Laboratory for NCI/DCTD from a Nov 2018 kickoff; hosts canine clinical-trial, imaging and sequencing data from the Comparative Oncology Program for human–dog comparative analysis [31] ✅/🟡.

### 3.4 Veterinary imaging / diagnostics AI (industry)
- **SignalPET** (SignalRAY): Ndiaye et al. 2025 *Front Vet Sci* compared the AI with 11 board-certified radiologists on 50 cases — strong at confirming normals, less sensitive to subtle abnormalities [32] 🟡; company claims >2,300 clinics and 50,000 films/week 🟡.
- **Zoetis Vetscan Imagyst**: FY2025 10-K states AI dermatology & AI fecal *for equine* (2023), AI urine sediment (2024) — plus the separately launched Vetscan OptiCell AI haematology analyser (2024) — and "AI Masses, which detects potentially neoplastic cells" (2025) [33] ✅ [verifier-refined].
- **Antech (Mars) RenalTech**: ML on ~150,000 Banfield cats, 6 analytes + age, predicts feline CKD up to 2 years early; a *dog* version was not found [51] 🟡. Antech RapidRead Dental (AI dental radiograph reads, May 2025) 🟡.
- **AI FOR PET (TTCare)**: multimodal image/video + clinical-data software; AJVR paper Jan 2026 per Purina blog 🟡 [52].
- **VET-DINO / V-REX** [verifier-added]: VET-DINO (Dourson, Taylor, Qiao, Fitzke; arXiv 2505.15248, May 2025) is a self-supervised multi-view model trained on 5 million radiographs from 668,000 canine studies — effectively a canine radiograph foundation model; V-REX (Elsner, McNally, Dourson, Fitzke; arXiv 2608.20069, Aug 2026) is a veterinary-radiograph vision-language model for report generation [71][72] ✅ (abstracts). Author affiliations and weight availability not checked ❓.

### 3.5 Veterinary language models / NLP
- **PetBERT** (SAVSNET, Univ. Liverpool): BERT-base further pre-trained on 5.1 M UK veterinary EHRs (>500 M words); PetBERT-ICD codes ICD-11 with F1 > 83 % across 20 codes; Open RAIL licence; Farrell et al., *Sci Rep* 2023 [29] ✅.
- **VetLLM** (Jiang, Irvin, Ng, Zou; Stanford; PSB 2024, 29:120–133): Alpaca-7B fine-tuned on 5,000 veterinary notes for diagnosis prediction (F1 0.747 on CSU test / 0.637 on PP test data) [53] ✅ (numbers confirmed in abstract) [verifier-upgraded].
- Fine-tuning foundation models to code diagnoses from veterinary records (PLoS Digital Health, 2025/26) 🟡 [54].

### 3.6 Statistical/ML modelling on Dog Aging Project (DAP) data
- Fang, Kumar, Creevy, Promislow, Ma & DAP Consortium 2025 *PLoS Comput Biol* 21(8): comorbidity networks from 26,614 dogs with ≥1 of 160 conditions (Poisson-binomial comorbidity, logistic regression, age-stratified, directed progression networks) [55] ✅.
- Harrison, Akey, Snyder-Mackler, … Promislow 2026 *J Gerontol A*: longitudinal survival models on 937 Precision-Cohort dogs show dogs and humans share biomarkers of mortality [56] ✅ (abstract).
- Prescott, Keyser, Litwin, … Promislow 2025 *GeroScience* 47:5725–5748: Precision Cohort design — 1,000 dog–owner pairs, 976 dogs sampled (blood, urine, faeces, hair) for CBC/chemistry, flow immunophenotyping, metabolomics, faecal microbiome, epigenome [57] ✅.
- DAP curated data are released annually (2023, 2024, 2025 releases) on the Broad Institute's Terra platform after application [58] ✅/🟡 — an unusually AI-ready longitudinal pet dataset.

### 3.7 Canine single-cell and functional-genomics resources (training substrates, not models)
- No whole-organism dog cell atlas found ✅. Tissue atlases: healthy canine lung (26,278 cells, 4 dogs, 46 subpopulations; Liège, *Front Immunol* 2025) [59] ✅; Dog10K database bundles snRNA-seq hippocampus (105,057 nuclei) and scRNA leukocytes (74,067 cells) [49] ✅; PBMC/NK/leishmaniasis atlases 2025 🟡 [60].
- **DoGA consortium** (Helsinki/Lohi + Karolinska/Daub): expression atlas of promoters and genes in 100 canine tissues (*Nat Commun* 15:9082, 2024). The consortium's **biobank** holds 5,485 samples from 132 tissues of 13 dogs, 12 dog embryos and **24 wolves**; the published **STRT2-seq** (5′-end RNA-seq, not CAGE) promoter/expression atlas covers 100 tissues from **9 dogs and 12 embryos — no wolves** (>100,000 candidate promoter regions on CanFam4, >45,000 highly reproducible) [14] ✅ [verifier-corrected: author described "5,485 CAGE samples … 24 wolves" as the atlas]; the 2026 preprint adds 114 **CAGE** libraries / 56 tissues & stages / 9 dogs → 68,446 promoters, 46,661 enhancers, 69 dog–human orthologous enhancer structures [15] ✅. Wolf tissue therefore exists in the biobank but not yet in a published DoGA regulatory atlas. This is exactly the kind of data an AlphaGenome/Borzoi-style canine model would need.

---

## 4. Summary table

| Model / resource | Modality | Dog/wolf data included? | Evidence | Usable for dog research how | Licence / availability |
|---|---|---|---|---|---|
| ESM-2 / ESM3 / ESM C | protein LM | **Y** (dog in UniProt/UniRef; inferred) | UniProt proteomes [10]; ESM-2 paper [37] 🟡 | embed/score dog proteins & variants directly | ESM-2 MIT; ESM3 mixed 🟡 |
| AlphaFold DB | structures | **Y** (per-entry; no dog bulk-proteome archive) | P49822 dog albumin entry [11] ✅ | retrieve dog structures | CC-BY 4.0 🟡 |
| Evo 2 (OpenGenome2) | DNA LM | **Y** — 1 domestic-dog genome (UU_Cfam_GSD_1.0) + 6 canid genomes + canid mitogenomes + Ensembl dog/dingo ncRNA & mRNA sets [verifier-added]; **gray wolf nuclear genome: not listed** | species_metadata.csv [4]; NCBI/ENA [5] ✅ | zero-shot variant scoring / embeddings on CanFam sequences; fine-tune | Apache-2.0 data; Apache-2.0 weights ✅ |
| NTv3 (InstaDeep) [verifier-added] | DNA LM (long-context, seq→function) | **Y** at pre-training (OpenGenome2); dog not among post-training species 🟡 | bioRxiv 2025.12.22.695963 [73] ✅ | embeddings / fine-tuning on dog sequence | HF, gated, licence "other" ✅ |
| Nucleotide Transformer v1/v2 multi-species | DNA LM | **N** for *C. l. familiaris*; dingo + Arctic fox only | original_urls.csv [8] ✅ | transfer from near relatives; fine-tune | CC-BY-NC-SA 4.0 ✅ |
| DNABERT-2 | DNA LM | **N** (7 mammals, no canid) | PDF Table 11 [9] ✅ | fine-tune only | open 🟡 |
| GPN-MSA | DNA LM (MSA) | dog is an aligned species, not a target | UCSC README [42] ✅ | not directly; would need dog-centred MSA | open 🟡 |
| Caduceus / HyenaDNA | DNA LM | **N** (human) | [43] ✅/🟡 | fine-tune | open |
| AlphaGenome | regulatory seq→function | **N** (human, mouse) | FAQ [13] ✅ | untested on dog; non-commercial | API, non-commercial ✅ |
| Enformer / Borzoi | regulatory | **N** (human, mouse) | 🟡 | retrain on DoGA/ATAC | open 🟡 |
| UCE | single-cell | **N** (8 species) | [16] ✅ | **zero-shot** embedding of dog scRNA-seq via protein embeddings | open (HF/CZI) 🟡 |
| TranscriptFormer | single-cell | **N** (12 species) | README [17] ✅ | zero-shot via ESM-2 embeddings | weights on S3; code MIT (LICENSE.md), weights licence not separately stated ✅ [verifier-corrected] |
| GeneCompass / scGPT / Geneformer | single-cell | **N** (human ± mouse) | [18][19] 🟡 | retrain; scCompass has dog data [20] ✅ | open 🟡 |
| scCompass | single-cell DB | **Y** (13 species incl. dog; 104.6 M cells) | [20] ✅ | AI-ready dog scRNA-seq | public DB ✅ |
| Mammalian Methylation Consortium clocks | DNA methylation | **Y** dogs (742 samples, 93 breeds); wolves ❓ | [21][22] ✅ | ready-made cross-species biological-age readout; array must be purchased/run | data GEO; code GitHub ✅ |
| Dog10K | WGS variants + omics | **Y** (1,611 dogs, 309 village dogs, 63 wolves, 4 coyotes) | [36][49] ✅ | training/eval data for canine VEP, selection scans | free, no login ✅ |
| DoGA | STRT2-seq promoter atlas (2024) + CAGE promoters/enhancers (2026 preprint) | **Y** dogs (atlas: 9 dogs + 12 embryos; CAGE: 9 dogs); wolves only in the biobank (24), not in a published atlas [verifier-corrected] | [14][15] ✅ | training data for a canine regulatory model | free DCC; prepublication on request ✅ |
| CanVAS | imputed genotypes | **Y** (15,451 dogs + village dogs, dingoes, wolves, coyotes) | [35] ✅ | GWAS/ML on ageing traits | CC-BY 4.0 (Zenodo) ✅ |
| DAP curated data | phenotypes + multi-omics | **Y** (tens of thousands of dogs; 976-dog Precision Cohort) | [57][58] ✅ | longitudinal ageing ML | application via Terra ✅/🟡 |
| PetBERT / VetLLM | clinical text | **Y** (vet EHRs) | [29][53] ✅ | phenotype extraction from vet records | Open RAIL / academic |
| VET-DINO / V-REX [verifier-added] | radiograph imaging (SSL / VLM) | **Y** (5 M canine radiographs, 668 k studies for VET-DINO) | arXiv [71][72] ✅ (abstracts) | imaging phenotypes (e.g. musculoskeletal/cardiac ageing) | not checked ❓ |

---

## 5. What this means for a dog-ageing AI project

1. **Protein layer: solved.** Dog proteomes are in UniProt/AFDB and ESM-class models; dog missense variants can be scored today (with the specificity caveat from [34]).
2. **Genome layer: partially solved.** Evo 2 has a domestic-dog genome in training [4][5], and so does any model pre-trained on OpenGenome2 — notably InstaDeep's NTv3 (gated weights) [73] [verifier-corrected: author wrote "Evo 2 is the only large open genomic LM with a domestic-dog genome in training"; other RefSeq-eukaryote-trained LMs such as GENERator may also include dog but were not checked ❓]; NT v1/v2 and DNABERT-2 do not. A wolf nuclear genome is **not** in OpenGenome2's list (only *Canis lupus* via the dog assembly, plus canid mitogenomes) ✅ — relevant if the project wants wolf–dog comparative embeddings.
3. **Regulatory layer: unsolved and tractable.** No canine AlphaGenome/Borzoi exists; DoGA's STRT2-seq and CAGE atlases (dogs and embryos; wolf tissue is biobanked but not yet profiled in a published atlas [verifier-corrected]) [14][15] plus Dog10K/CanVAS variants [36][35] are a credible training set for a first canine regulatory model or for fine-tuning Borzoi-style architectures.
4. **Cell layer: zero-shot is the pragmatic path.** UCE/TranscriptFormer were built to embed unseen species [16][17]; dog atlases are small and tissue-specific [59][49], so a dog-specific scFM is premature, but scCompass [20] signals that Chinese groups may add dog to GeneCompass-type training.
5. **Ageing biomarker layer: mature.** Pan-mammalian clocks already give r = 0.94 in dogs [21]; DAP epigenetic data on 864 dogs ties breed size to epigenetic acceleration and mortality [25]. This is the natural "label" for any canine foundation-model fine-tuning aimed at ageing (see ../04_dog_aging_biology/ and ../05_interventions/).

---

## Open questions / gaps

- **Wolves in the Mammalian Methylation Consortium panel**: not stated in the main text; needs Supplementary Data 1 check [21] ❓.
- ~~**AlphaFold DB bulk proteomes**: whether dog is among the 48 bulk-download organisms~~ — resolved by verifier: dog is not among them (per-protein entries exist regardless) ✅.
- **Evo 2 dog coverage is one assembly**; OpenGenome2 taxonomy collapses *C. l. familiaris* to "Canis lupus", so no separate gray-wolf reference is listed — confirm with Arc whether wolf assemblies (e.g., GCF_905319855 mCanLor1.2) were filtered as redundant ❓.
- **ESM3 / ESM C exact training corpora** (UniRef + MGnify + JGI) — dog inclusion is inferred, not enumerated 🟡.
- **GPN-MSA training-alignment details** taken from the preprint/GitHub rather than the journal text (journal citation itself confirmed via Crossref) 🟡; SATURN's exact atlas species (beyond "three species whole-organism atlases" + frog/zebrafish) not enumerated 🟡.
- No canine-specific VEP, regulatory model, or cell atlas model was found; absence claims rest on Hugging Face API searches and literature searches up to 2026-10-04 and could miss unindexed preprints or in-house industry models (Embark, Wisdom Panel, Loyal) ❓.
- Search budget was exhausted during this task (200 web searches); some blocked pages (Nature news, STAT, Science news, GRLS site) were replaced by secondary summaries — flagged 🟡 where used.
- [verifier-added] Whether EpiZoo (cross-species scATAC FM, bioRxiv Sep 2026) includes dog in its ~20.9 M-cell pre-training corpus was not determined ❓; the NTv3 post-training species list was read through a summariser, not directly ❓.

---

## Sources

1. Hugging Face Hub API, `GET /api/models?search=canine&limit=50`, accessed 2026-10-04 — https://huggingface.co/api/models?search=canine&limit=50
2. Hugging Face Hub API, `search=canfam` and `search=dog%20genome` (empty results), accessed 2026-10-04 — https://huggingface.co/api/models?search=canfam&limit=50
3. Hugging Face Hub API, `search=veterinary&limit=50`, accessed 2026-10-04 — https://huggingface.co/api/models?search=veterinary&limit=50
4. Arc Institute, OpenGenome2 dataset, `species_metadata.csv` (downloaded and grepped 2026-10-04) — https://huggingface.co/datasets/arcinstitute/opengenome2/resolve/main/species_metadata.csv
5. NCBI Assembly, GCF_011100685.1 "UU_Cfam_GSD_1.0", *Canis lupus familiaris* — https://www.ncbi.nlm.nih.gov/assembly/GCF_011100685.1
6. Arc Institute, OpenGenome2 dataset card (licence Apache-2.0) — https://huggingface.co/datasets/arcinstitute/opengenome2
7. InstaDeepAI, `multi_species_genomes` dataset card (850 species; class counts) — https://huggingface.co/datasets/InstaDeepAI/multi_species_genomes
8. InstaDeepAI, `multi_species_genomes/original_urls.csv` (850 NCBI URLs; downloaded and grepped 2026-10-04) — https://huggingface.co/datasets/InstaDeepAI/multi_species_genomes/resolve/main/original_urls.csv
9. Zhou Z. et al. (2024). DNABERT-2: Efficient Foundation Model and Benchmark for Multi-Species Genomes. ICLR 2024; Appendix Table 11 — https://arxiv.org/pdf/2306.15006
10. UniProt REST, proteomes for taxon 9615 (*Canis lupus familiaris*) — https://rest.uniprot.org/proteomes/search?query=organism_id:9615&format=json
11. AlphaFold DB API, prediction for UniProt P49822 (dog albumin) — https://alphafold.ebi.ac.uk/api/prediction/P49822
12. Varadi M. et al. (2024). AlphaFold Protein Structure Database in 2024: providing structure coverage for over 214 million protein sequences. *Nucleic Acids Res* 52:D368 — https://academic.oup.com/nar/article/52/D1/D368/7337620
13. Google DeepMind, AlphaGenome documentation FAQ (species; terms of use) — https://www.alphagenomedocs.com/faqs.html
14. Hörtenhuber M., Hytönen M.K., Mukarram A.K., … Lohi H. (2024). The DoGA consortium expression atlas of promoters and genes in 100 canine tissues. *Nat Commun* 15:9082; PMID 39433728; PMC11494170; doi:10.1038/s41467-024-52798-1 (metadata and abstract via Europe PMC) [verifier-corrected: volume/article number added]
15. Takan I., Daub C.O. et al. (2026). The DoGA Consortium Atlas of Canine Enhancers and Promoters Across Tissues and Development. bioRxiv, posted 2026-03-25 — https://www.biorxiv.org/content/10.64898/2026.03.24.713649v1
16. Rosen Y., Roohani Y., Agrawal A., … Leskovec J. Universal Cell Embeddings: A Foundation Model for Cell Biology. bioRxiv 2023.11.28.568918 (full text) — https://www.biorxiv.org/content/10.1101/2023.11.28.568918v1.full ; published as Rosen Y., Roohani Y., Agrawal A., Samotorčan L., Tabula Sapiens Consortium, Quake S.R., Leskovec J. (2026). Universal cell embedding provides a foundation model for cell biology. *Nature* 656:183–191 (online 8 Jul 2026), doi:10.1038/s41586-026-10689-z (PMID 42420460) [verifier-corrected: published title and pages]
17. CZI, TranscriptFormer README and LICENSE.md (MIT) — https://github.com/czi-ai/transcriptformer/blob/main/README.md ; preprint Pearce J.D. et al. (2025). A Cross-Species Generative Cell Atlas Across 1.5 Billion Years of Evolution: The TranscriptFormer Single-cell Model. bioRxiv 2025.04.25.650731
18. Yang X. et al. (2024). GeneCompass: deciphering universal gene regulatory mechanisms with a knowledge-informed cross-species foundation model. *Cell Research* 34:830–845 — https://www.nature.com/articles/s41422-024-01034-y
19. Mouse-Geneformer (PLoS Genet 2025; notes human-only training of Geneformer/scGPT) — https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1011420
20. scCompass: An Integrated Multi-Species scRNA-seq Database for AI-Ready. *Advanced Science* 2025;12(25):2500870; PMC12224968 — https://pmc.ncbi.nlm.nih.gov/articles/PMC12224968/
21. Lu A.T., Fei Z., Haghani A., … Horvath S. (2023). Universal DNA methylation age across mammalian tissues. *Nat Aging* 3:1144–1166; PMID 37563227; PMC10501909 (full text grepped via Europe PMC) — https://www.nature.com/articles/s43587-023-00462-6
22. Horvath S., Lu A.T., Haghani A., … Ostrander E.A. (2022). DNA methylation clocks for dogs and humans. *PNAS* 119(21):e2120887119; PMC9173771 — https://www.pnas.org/doi/10.1073/pnas.2120887119
23. Thompson M.J., vonHoldt B., Horvath S., Pellegrini M. (2017). An epigenetic aging clock for dogs and wolves. *Aging (Albany NY)* 9(3):1055–1068; PMID 28373601 — doi:10.18632/aging.101211
24. Jin K., McCoy B.M., … Snyder-Mackler N., Promislow D.E.L. (2024). DNA methylation and chromatin accessibility predict age in the domestic dog. *Aging Cell* 23(4):e14079; PMC11019125 — https://pmc.ncbi.nlm.nih.gov/articles/PMC11019125
25. McCoy B.M., Mariner B.L., Cheng C.F., … Snyder-Mackler N. (2024). Aging at scale: Younger dogs and larger breeds from the Dog Aging Project show accelerated epigenetic aging. bioRxiv 2024.10.03.616519 — https://www.biorxiv.org/content/10.1101/2024.10.03.616519v1
26. Armero A.S., Buckley R.M., Mboning L., … Ostrander E.A. (2024). Co-analysis of methylation platforms for signatures of biological aging in the domestic dog… *Aging (Albany NY)* 16(13):10724–10748; PMID 38985449 — https://www.aging-us.com/article/206012/text
27. Jang S., Kim S.J., Kang D., … Kim J. (2026). Age-associated epigenetic drift trajectory and cross-national disparities in accelerated aging in domestic dogs. *PNAS* 123(29):e2528874123; PMID 42441848 — https://www.pnas.org/doi/10.1073/pnas.2528874123
28. Kang D., Bok E.Y., Hong C.Y., … Kim J. (2026). Integration of methylome and transcriptome reveals age-associated signatures… in dogs. *GeroScience*; PMID 42753031 — https://link.springer.com/article/10.1007/s11357-026-02533-z
29. SAVSNET/PetBERT model card; Farrell S. et al. (2023). PetBERT: automated ICD-11 syndromic disease coding… *Sci Rep* 13:18015 (authors Farrell S., Appleton C., Noble P.-J.M., Al Moubayed N.); doi:10.1038/s41598-023-45155-7 — https://huggingface.co/SAVSNET/PetBERT
30. Wu K., Rodrigues L., Post G., … Zou J. (2023). Analyses of canine cancer mutations and treatment outcomes using real-world clinico-genomics data of 2119 dogs. *npj Precision Oncology* 7:8; PMID 36658200 — https://www.nature.com/articles/s41698-023-00346-3
31. NCI Wiki, Integrated Canine Data Commons Home — https://wiki.nci.nih.gov/display/ICDC/Integrated+Canine+Data+Commons+Home ; portal https://caninecommons.cancer.gov/
32. SignalPET, "Breakthrough Study Validates AI…" citing Ndiaye Y.S. et al. (2025) *Front Vet Sci* 12 — https://www.signalpet.com/articles/breakthrough-study-validates-ai/
33. Zoetis Inc., Form 10-K FY2025 (Vetscan Imagyst AI features; Basepaws) — https://www.sec.gov/Archives/edgar/data/1555280/000155528026000011/zts-20251231.htm
34. Hu H., Xie W. (2025). Human genomic tools to assess missense variant pathogenicity in domestic mammals using a mock-variant strategy. *Open Vet J* 15(10):5183–5191; PMC12613190 — https://pmc.ncbi.nlm.nih.gov/articles/PMC12613190/
35. Brundage D.M. (2026). CanVAS: A Harmonized and Imputed Canine Variant Atlas. bioRxiv, posted 2026-04-15 — https://www.biorxiv.org/content/10.64898/2026.04.13.718238v1
36. Meadows J.R.S., Kidd J.M., Wang G.-D., … Ostrander E.A. (2023). Genome sequencing of 2000 canids by the Dog10K consortium… *Genome Biology*; PMID 37582787 — https://link.springer.com/article/10.1186/s13059-023-03023-7
37. Lin Z. et al. (2023). Evolutionary-scale prediction of atomic-level protein structure with a language model (ESM-2). *Science* 379:1123 — doi:10.1126/science.ade2574 🟡 (cited from memory for the UniRef training statement)
38. Brixi G. et al. (2025/2026). Genome modelling and design across all domains of life with Evo 2. bioRxiv 2025.02.18.638918; *Nature* 652(8112):1349–1361 (online 4 Mar 2026; issue 30 Apr 2026; confirmed via Crossref), doi:10.1038/s41586-026-10176-5; PMC13128491 — https://www.biorxiv.org/content/10.1101/2025.02.18.638918v1.full
39. NVIDIA BioNeMo Framework docs, Evo2 model page (OpenGenome2 composition: 16,704 → 15,032 eukaryotic genomes, 6.98 T nt) — https://docs.nvidia.com/bionemo-framework/2.5/models/evo2/
40. InstaDeepAI, nucleotide-transformer-2.5b-multi-species model card (licence CC-BY-NC-SA 4.0) — https://huggingface.co/InstaDeepAI/nucleotide-transformer-2.5b-multi-species
41. Benegas G., Albors C., Aw A.J., Ye C., Song Y.S. (2025). A DNA language model based on multispecies alignment predicts the effects of genome-wide variants. *Nat Biotechnol*, published 2025-01-02, doi:10.1038/s41587-024-02511-w (confirmed via Crossref); preprint "GPN-MSA…" bioRxiv 2023.10.10.561776 — https://github.com/songlab-cal/gpn
42. UCSC Genome Browser, hg38 multiz100way README (species list) — https://hgdownload.soe.ucsc.edu/goldenPath/hg38/multiz100way/README.txt
43. Schiff Y. et al. (2024). Caduceus: Bi-Directional Equivariant Long-Range DNA Sequence Modeling (hg38 pretraining) — https://arxiv.org/pdf/2403.03234 ; HF card https://huggingface.co/kuleshov-group/caduceus-ps_seqlen-131k_d_model-256_n_layer-16
44. Avsec Ž. et al. AlphaGenome: advancing regulatory variant effect prediction… (DeepMind paper PDF) — https://storage.googleapis.com/deepmind-media/papers/alphagenome.pdf ; PMC12851941
45. Rosen Y., … Leskovec J. (2024). Toward universal cell embeddings: integrating single-cell RNA-seq datasets across species with SATURN. *Nat Methods*; PMID 38366243; doi:10.1038/s41592-024-02191-z; PMC11310084 (metadata/abstract via Europe PMC)
46. Horvath lab, MammalianMethylationConsortium GitHub (array manifests, clocks, code) — https://github.com/shorvath/MammalianMethylationConsortium
47. Haghani A., Li C.Z., Robeck T.R., … Horvath S. (2023). DNA methylation networks underlying mammalian traits. *Science* 381; PMID 37561875 — doi:10.1126/science.abq5693
48. Embark Veterinary press release (2022-10-04). Embark Launches First-Of-Its-Kind Age Test… — https://www.prnewswire.com/news-releases/embark-launches-first-of-its-kind-age-test-to-accurately-determine-dogs-calendar-age-301640141.html
49. Zhou T., Wang G.-D. et al. (2025). Dog10K: an integrated Dog10K database summarizing canine multi-omics. *Nucleic Acids Res* 53:D939–D947 — https://academic.oup.com/nar/article/53/D1/D939/7831084 ; http://dog10k.kiz.ac.cn/
50. FidoCure blog, "FidoCure Leads Canine Cancer Research with the World's Largest Canine Cancer Database" (company marketing) — https://blog.fidocure.com/fidocure-blog/fidocure-leads-canine-cancer-research-with-the-worlds-largest-canine-cancer-database
51. Antech Diagnostics, RenalTech (AI prediction of feline CKD) — https://www.antechdiagnostics.com/reference-lab/renaltech/ ; dvm360 coverage https://www.dvm360.com/view/predictive-diagnostic-renaltech-now-available
52. Purina "Unleashed" blog, AI FOR PET / TTCare — https://www.unleashedbypurina.com/blog/ai-for-pet
53. Jiang Y., Irvin J.A., Ng A.Y., Zou J. (2024). VetLLM: Large Language Model for Predicting Diagnosis from Veterinary Notes. *Pac Symp Biocomput* 29:120–133; PMID 38160274; doi:10.1142/9789811286421_0010 — http://psb.stanford.edu/psb-online/proceedings/psb24/jiang.pdf
54. Fine-tuning foundational models to code diagnoses from veterinary health records. *PLoS Digital Health*; PMC12923131 — https://pmc.ncbi.nlm.nih.gov/articles/PMC12923131/
55. Fang A., Kumar L., Creevy K.E., Promislow D.E.L., Ma J., DAP Consortium (2025). Constructing the first comorbidity networks in companion dogs in the Dog Aging Project. *PLoS Comput Biol* 21(8):e1012728 — https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1012728
56. Harrison B.R., Akey J.M., Snyder-Mackler N., … Promislow D.E.L. (2026). Dogs and humans share biomarkers of mortality. *J Gerontol A Biol Sci Med Sci*; PMID 41429575; doi:10.1093/gerona/glaf279
57. Prescott J., Keyser A.J., Litwin P., … Promislow D.E.L. (2025). Rationale and design of the Dog Aging Project precision cohort… *GeroScience* 47:5725–5748; PMC12397037 — https://link.springer.com/article/10.1007/s11357-025-01571-3
58. Dog Aging Project, Curated Data Summary Tables (2023/2024/2025 releases; Terra) — https://data.dogagingproject.org/ ; access via https://dogagingproject.org/data-access
59. Rizzoli E., Fievez L., Fastrès A., … Clercx C. (2025). A single-cell RNA sequencing atlas of the healthy canine lung. *Front Immunol*; PMID 40114924; PMC11922831
60. LeishDog Atlas / canine PBMC single-cell atlases (2025) — https://pmc.ncbi.nlm.nih.gov/articles/PMC13444607/ 🟡
71. [verifier-added] Dourson A., Taylor K., Qiao X., Fitzke M. (2025). VET-DINO: Learning Anatomical Understanding Through Multi-View Distillation in Veterinary Imaging. arXiv:2505.15248 (submitted 21 May 2025) — https://arxiv.org/abs/2505.15248
72. [verifier-added] Elsner T., McNally N., Dourson A., Fitzke M. (2026). V-REX: Efficient Specialist VLM Training for Veterinary X-Rays. arXiv:2608.20069 (submitted 20 Aug 2026) — https://arxiv.org/abs/2608.20069
73. [verifier-added] Boshar S., Evans B., Tang Z., … de Almeida B.P., Pierrot T. (2025). A foundational model for joint sequence-function multi-species modeling at scale for long-range genomic prediction (Nucleotide Transformer v3). bioRxiv 2025.12.22.695963 (posted 25 Dec 2025) — https://www.biorxiv.org/content/10.64898/2025.12.22.695963v1 ; weights https://huggingface.co/InstaDeepAI/NTv3_650M_post (gated, licence "other")

---

## Verification notes

Independently checked by Opus 5.5 on 2026-10-04 (full log: ../07_verification/canine_bio_ai_verification.md). Methods: re-downloaded and grepped OpenGenome2 `species_metadata.csv`, InstaDeep `original_urls.csv`, the DNABERT-2 PDF, the UniProt proteome API, the AlphaFold API and FTP listing, ENA assembly records, Crossref metadata, Europe PMC abstracts/full texts (Lu 2023, Jin 2024, Hu & Xie 2025, scCompass, Dog10K NAR, FidoCure), the Zoetis 10-K, Zenodo, and fresh Hugging Face / Europe PMC / arXiv searches for any dog-specific foundation model.

- **Headline survives for molecular modalities**: no dog- or wolf-specific protein, DNA or single-cell foundation model was found. It was narrowed: dog-specific *radiograph* foundation models exist (VET-DINO 2025, V-REX 2026).
- **Main corrections**: (1) DoGA's "5,485 CAGE samples incl. 24 wolves" is the tissue biobank; the 2024 atlas is STRT2-seq on 9 dogs + 12 embryos, with no wolves. (2) Evo 2 is not the only genomic LM with dog in its training data: NTv3 was pre-trained on OpenGenome2. (3) The Hugging Face "canine" search returns 176 models, not 57, and not all are CANINE NLP. (4) The TranscriptFormer repository is MIT-licensed. (5) Dog is not in AlphaFold DB's bulk proteome downloads. (6) The UCE Nature citation now has the published title and pages. (7) The Hu & Xie ranges are across tools, not species. (8) The FidoCure analysis is Cox regression, not ML.
- **Additions**: OpenGenome2 also contains Ensembl dog/dingo ncRNA and mRNA transcript sets, and scCompass ships pre-trained checkpoints of unknown species mix.
- **Still open**: whether wolves are in the 185-species Mammalian Methylation Consortium clock panel ❓; whether EpiZoo includes dog ❓; the NTv3 post-training species list ❓.
