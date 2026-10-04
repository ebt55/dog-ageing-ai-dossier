# Executive summary: AlphaFold, MAMMAL, AI for dogs, and why dogs age fast

> Synthesis for the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 (orchestrator) · Built only from files that passed independent cross-model verification (see §7) · Links point to the detailed files, which hold the primary-source citations. · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

This page answers each of the questions asked, in order. For the research plan, see [research_paths_dog_ageing.md](research_paths_dog_ageing.md).

---

## 1. AlphaFold: what it is and how to use it

- **What it is.** AlphaFold is a family of Google DeepMind models that predict 3D molecular structure from sequence.
  - **AlphaFold 2** (CASP14, 2020; *Nature* 2021) reached near-experimental accuracy on single protein chains, with a median backbone error of 0.96 Å against 2.8 Å for the next-best method.
  - **AlphaFold 3** (*Nature*, May 2024) models complexes of proteins, DNA, RNA, ligands, ions and modified residues.
  - The 2024 Nobel Prize in Chemistry went half to David Baker and half jointly to Demis Hassabis and John Jumper.
  - → [alphafold_complete_guide.md](../01_alphafold/alphafold_complete_guide.md)
- **How to use it** (step-by-step in [how_to_use_alphafold.md](../01_alphafold/how_to_use_alphafold.md)):
  1. **Look up** an existing prediction in AlphaFold DB (v6, more than 240 M structures, CC BY 4.0) via `https://alphafold.ebi.ac.uk/api/prediction/<UniProt accession>`.
  2. **Model a complex** in AlphaFold Server (free, non-commercial, about 30 jobs/day; ligands by CCD code, not SMILES).
  3. **Run AF3 locally.** Since mid-2026 the code is Apache-2.0 and the weights download directly, but the weights remain **non-commercial**.
  4. **Use open alternatives** for commercial work: Boltz-2 (MIT; also predicts binding affinity), Chai-1 (Apache-2.0), OpenFold3, Protenix.
- **Limits that matter.**
  - One static structure, no dynamics or ensembles.
  - Hallucinated order in disordered regions.
  - Poor at predicting point-mutation effects on stability.
  - Antibody–antigen docking is still weak (one independent study found about 65% single-seed failure).
  - Ligand co-folding partly memorises poses seen in training.
- **2026 news worth knowing** (each item verified to a commit or primary post):
  - AF3's code was relicensed to Apache-2.0 on 9 June 2026.
  - The weights became a direct download on 23 July 2026 and remain non-commercial.
  - CPU and Apple Silicon support arrived in v3.0.4.
  - A SynthID watermark option was added on 30 September 2026.
  - Isomorphic Labs announced a proprietary successor engine, IsoDDE, in February 2026; no Isomorphic clinical trial had been disclosed by late September 2026.
  - John Jumper announced on 19 June 2026 that he was leaving DeepMind for Anthropic (his own post).
  - The FT reported on 29 July 2026 that the dedicated AlphaFold team had been dissolved; Scientific American corroborated this.
  - DeepMind is reported to have said the AlphaFold system and database will not be shut down. That quote is secondary-sourced only.

## 2. Is there an AlphaFold-like model for dogs or wolves? Who is working on this?

- **No dog- or wolf-specific *molecular* foundation model exists** (protein, DNA or single-cell) as of October 2026. The verifier re-searched Hugging Face, Europe PMC/bioRxiv and arXiv independently and confirmed this. → [dog_foundation_models_landscape.md](../03_canine_bio_ai/dog_foundation_models_landscape.md)
- **None is needed for structure.** AlphaFold is species-agnostic.
  - About **90.6% of dog UniProt entries** have an AlphaFold DB model.
  - Gaps: dog is not a downloadable proteome bundle, and **long unreviewed dog proteins (>1,280 aa), including full-length IGF1R and MTOR, have no model**.
  - Wolves have only about 199 UniProt entries; use dog sequences plus wolf variants.
  - → [alphafold_and_dogs.md](../01_alphafold/alphafold_and_dogs.md)
- **Where dogs *are* covered.**
  - **Evo 2** and InstaDeep's **NTv3** were trained on a corpus that includes a dog genome (verified by downloading the training metadata).
  - Dog proteins are in all UniProt-trained protein language models (ESM).
  - The **pan-mammalian methylation clock** works in dogs (r = 0.94, 742 dogs).
- **Where dogs are missing.**
  - AlphaGenome, Enformer and Borzoi cover human and mouse only.
  - Every single-cell foundation model excludes dogs from training.
  - AlphaMissense is human-only. Mapping dog variants onto human proteins has poor specificity (0.20–0.46).
- **Canine AI that does exist** is task-level:
  - imaging foundation models (VET-DINO, trained on 5 M canine radiographs; V-REX);
  - clinical-text models (PetBERT, VetLLM);
  - epigenetic clocks;
  - diagnostic AI (SignalPET, Zoetis).
- **Who to know** (→ [companies_and_research_groups.md](../03_canine_bio_ai/companies_and_research_groups.md)):
  - **Public data:** the **Dog Aging Project** (>50,000 dogs; 976-dog multi-omic Precision Cohort; data on Terra), **Dog10K** (1,987 canid genomes incl. 63 wolves), **DoGA** (Helsinki tissue atlas), **CanVAS** (15,451 dogs, CC-BY).
  - **Private genomic databases:** Wisdom Panel/Mars (about 3.5 M dogs) and Embark (about 2.5 M).
  - **Longevity drugs:** **Loyal**.
  - **Gene therapy:** **Rejuvenate Bio**.
  - **Canid genome editing and cloning:** **Colossal Biosciences** (edited grey wolves; bought ViaGen).
  - **No company is building a dog-ageing foundation model.** That is an open niche.

## 3. The MAMMAL video: what is true

The video is *The biggest AI breakthrough in medicine & drug discovery* by AI Search (13 May 2026, 31:54). It covers IBM Research's **MAMMAL**: Shoshan et al., *npj Drug Discovery* 3, 14 (2026), published 4 May 2026, from arXiv preprint 2410.22367 (Oct 2024). → [video_transcript_documented.md](../02_mammal/video_transcript_documented.md), [the video itself](https://www.youtube.com/watch?v=s3rNDndvav0) (transcript not redistributed), [mammal_paper_deep_dive.md](../02_mammal/mammal_paper_deep_dive.md), [video_claims_factcheck.md](../02_mammal/video_claims_factcheck.md)

- **What MAMMAL is.** A **458 M-parameter T5-style encoder–decoder**. A modular tokenizer turns four kinds of input into one token sequence: amino-acid sequences, SMILES (molecules as text), gene symbols ranked by expression, and cell-type/tissue ontology terms. It was pre-trained on about 2 billion samples (OAS antibodies, UniRef90, ZINC/PubChem, human CELLxGENE, STRING).
- **77 claims fact-checked:**

  | Verdict | Claims |
  |---|---|
  | Accurate | 33 |
  | Mostly accurate | 19 |
  | Exaggerated | 10 |
  | Misleading | 8 |
  | Inaccurate | 4 |
  | Unverifiable | 2 |
  | Transcripts disagree | 1 |

  **No benchmark number is fabricated; the hype is in the framing (7/10).**
- **Key corrections.**
  - "State-of-the-art on all 11 benchmarks" → **9 of 11** (2 "comparable").
  - "Understands DNA / feed it a DNA sample" → **false**: MAMMAL has no nucleotide input at all.
  - "Beat AlphaFold 3 on 5 of 7 targets" → **true, but asymmetric**:
    - MAMMAL was **fine-tuned on binders of those exact targets**.
    - AF3 was zero-shot, scored by its own confidence, on 28–60 samples per target.
    - Un-fine-tuned MAMMAL is at chance (AUROC 0.53).
    - The paper calls the comparison "exploratory".
    - Its disordered-region explanation does not apply to the HER2 extracellular domain that was tested.
  - Carfilzomib "against expert belief" → **exaggerated**:
    - The paper says "limited efficacy in cells of solid tumors… warrants further investigation".
    - A 2014 study had already shown nanomolar potency in lung-cancer cell lines.
    - A wet-lab test was run, but the paper gives no cell lines, IC50s or statistics.
    - "95% of 805 cell lines" is a *model prediction*, and the paper says 90–95%.
    - The training data already contained the same drug class (bortezomib, MG-132).
  - "19% better on CDR-H3" → relative; CDR-L3 improved more (+39%).
  - The 12:29 transcript conflict ("huge" vs "few" percentage points) is settled as **"a few"**: BBBP +2.0 points, ClinTox +3.8 points.

## 4. Can MAMMAL do dogs?

Not out of the box. → [mammal_for_dogs.md](../02_mammal/mammal_for_dogs.md)

- **Nothing in MAMMAL is canine:**
  - its single-cell data were filtered to human;
  - its antibody data contain no dog;
  - its organism tokens are human, mouse, rat, rabbit, monkey and camel.
- **What does transfer:**
  - **Small-molecule tasks:** the inputs transfer freely, because chemistry is species-agnostic. The training labels (BBBP, toxicity, IC50) come from human data, though, and canine pharmacology differs. For example, the MDR1/ABCB1 deletion in collies and herding breeds changes how drugs cross the blood–brain barrier.
  - **Protein tasks** transfer weakly; STRING includes dog proteins, so some canine interaction pairs may have been seen.
  - **Gene-expression tasks** need ortholog mapping: **78% of canine gene symbols** have an exact token, versus 98% for human.
  - **Canine antibody design** is effectively blocked.
- **Fine-tuning data exist:**
  - canine cancer cell-line panels (about 990 dog lines in Cellosaurus);
  - canine blood single-cell atlases;
  - Dog Aging Project data;
  - approved caninised antibodies such as lokivetmab and bedinvetmab as anchors.
- **Best use for dog ageing:** a fine-tuned canine drug-response and geroprotector screen (Path 6 in the research plan).

## 5. Why do dogs age so fast?

→ [why_dogs_age_fast.md](../04_dog_aging_biology/why_dogs_age_fast.md), [breed_size_genetics_lifespan.md](../04_dog_aging_biology/breed_size_genetics_lifespan.md), [wolves_vs_dogs.md](../04_dog_aging_biology/wolves_vs_dogs.md)

1. **The premise needs a correction.** The gap is about **5–6×** (median dog about 12.5 y vs human about 73 y), not 10×. For their body size, **dogs live about as long as a typical mammal should; humans live about 4.6× longer than expected.** Humans are the outlier.
2. **Ultimate (evolutionary) cause.** This is a well-supported hypothesis.
   - Dogs inherited the grey wolf's fast life history: maturity at about 1.5–2 y, litters of 4–6, and violent adult death (wild wolves average 4–5 y).
   - Under that regime, natural selection barely maintains the body past about 10–15 y (Medawar, Williams and Kirkwood theory).
   - Humans evolved the opposite: low adult mortality, slow maturation, and possibly grandmothering.
   - Domestication was too recent, and selected for early reproduction, so it did not lengthen life.
3. **Proximate (mechanistic) picture.** Nearly every biological clock runs 4–10× faster in dogs:
   - somatic mutations about 249 vs 47 per genome per year, reaching a similar burden by death;
   - telomere loss about 10× faster;
   - maturity about 9× sooner;
   - mortality doubling every ~2 y vs ~8 y in humans;
   - DNA methylation that remodels fast in puppyhood. Human-equivalent age ≈ **16·ln(dog age) + 31** (Wang 2020), so the "×7 rule" is a myth.
   - These look like **one coordinated life-history tempo**, probably set by species-specific cellular kinetics, rather than separate causes.
   - **Metabolic rate ("rate of living") does not explain it.**
4. **Within dogs, size reverses the rule.**
   - Large and giant breeds die years earlier (about 9.5 y for giant vs 13.5 y for small purebreds, US data), mainly because they **age faster** (Kraus 2013).
   - The genetics are few and mapped, on the **GH/IGF-1 axis** (IGF1-AS, IGF1R, GHR, HMGA2…).
   - Large breeds die more of cancer: osteosarcoma odds are about 45× higher in dogs over 40 kg.
   - Captive wolves of similar size reach 15–20 y, so large-breed brevity looks like a product of selection, not a law of canid biology (inference).
5. **What kills old dogs:** cancer, neurological disease (including canine cognitive dysfunction) and heart disease.
6. **What has been shown to change it.**
   - Only lifelong 25% caloric restriction: **+1.8 y median** in Labradors (Kealy 2002).
   - **Nothing is approved** (status as of 4 Oct 2026):
     - **Loyal's LOY-002:** 2 of 3 FDA sections accepted; manufacturing pending.
     - **LOY-001 and LOY-003** (IGF-1-lowering, for large dogs): efficacy-expectation sections accepted.
     - **TRIAD** (rapamycin RCT, target n=580) and **STAY** (1,300 dogs): pending.
   - Gene therapy works in dogs (AAV, CRISPR) but **has never targeted an ageing gene**. Germline editing of canids is feasible (MSTN beagles; Colossal's edited wolves) but not recommended for ageing.
   - → [dog_longevity_interventions.md](../05_interventions/dog_longevity_interventions.md), [gene_editing_in_dogs.md](../05_interventions/gene_editing_in_dogs.md)

## 6. Research paths: the short list

Full ranked plan, with methods, data, costs and risks: [research_paths_dog_ageing.md](research_paths_dog_ageing.md).

1. **Separate "size genes" from "ageing-rate genes."** Run an ancestry-aware GWAS on epigenetic-clock residuals, plus per-breed Gompertz decomposition, on Dog Aging Project data. This also resolves the conflicting evidence on whether big dogs age faster molecularly.
2. **Use the wolf as the control group.** Compare ageing rate in size-matched captive wolves and large dogs. This has never been done, and it directly tests whether large-breed fast ageing is a domestication artefact.
3. **Decode the IGF1-AS regulatory mechanism** with Evo 2 (trained on the dog genome) and a new canine regulatory model, followed by reporter assays. This is the route to reversible GH/IGF-1 modulation.
4. **Build a native canine variant-effect predictor** and a breed "ageing-gene load" map, because borrowed human tools perform near chance in animals.
5. **Make clocks into trial endpoints.** A composite canine clock validated against mortality and interventions could shorten 4–5-year dog trials.

Then:
- put the dog on the pan-mammalian ageing-signature map and screen geroprotectors, including with fine-tuned MAMMAL;
- a canid "stem-cell zoo" to study species tempo;
- AI-designed reversible GH/IGF-axis binders;
- breeding informatics;
- and only later, a somatic gene-therapy design dossier.

**Germline editing is documented as not recommended.**

## 7. How reliable is this dossier?

Eight subagents researched (Opus 5.5 and Fable 5.1). Each topic was then audited by the **other** model family against primary sources, with in-place corrections marked `[verifier-corrected]` and full reports in [`07_verification/`](../07_verification/).

| Topic | Verifier | Reliability rating | Claims checked | Corrected / downgraded / removed |
|---|---|---|---|---|
| Video transcript documentation | Opus 5.5 | High (fidelity) | 126 claim rows + 177 quotes + 58 paragraphs | 5 timestamps, 6 wordings, 18 claims added |
| Why dogs age fast | Fable 5.1 | High | 78 | 6 / 4 / 0 |
| Breed size, genetics, wolves | Opus 5.5 | Medium-high | 109 | 18 / 4 / 0 |
| Canine bio-AI landscape and organisations | Opus 5.5 | Medium-high | 93 | 21 / 3 / 0 |
| Interventions and gene editing | Opus 5.5 | Medium | 88 | 24 / 5 / 1 |
| AlphaFold | Fable 5.1 | High | 131 | 9 / 1 / 1 (plus 70 DOIs resolved; all sequence alignments and live AlphaFold DB counts reproduced) |
| MAMMAL paper, fact-check, dogs | Fable 5.1 | High | ~200 | 9 / 2 / 0 (6 over-hedged claims upgraded; canine gene-coverage figure re-computed and reproduced exactly; "fabricated" carfilzomib verdict softened to "overstated") |
| AI toolkit, data, proposals | Fable 5.1 | High for the tools and data files; medium-high for the proposals | 147 | 24 / 12 / 0 (9 upgraded; 115 DOIs resolved; all 18 proposals reviewed, 9 with material problems, which are now flagged in the file and fixed in the synthesis) |

**No verifier found a fabricated citation.** Most corrections were wrong numbers, wrong attributions, outdated statuses, or confidence tags set too high. Claims still marked 🟡 or ❓ after verification are leads to follow up, not settled facts.
