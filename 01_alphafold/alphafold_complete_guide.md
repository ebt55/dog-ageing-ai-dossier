# AlphaFold: The Complete Guide (2018 to October 2026)
> Part of the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 subagent · Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/alphafold_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**Confidence tags:** ✅ = confirmed in a primary source I opened (paper, official page, GitHub, database API) · 🟡 = reputable secondary source, abstract only, or a figure I read but could not fully check · ❓ = unconfirmed, recalled from memory, or contested.

---

## TL;DR

- **What AlphaFold is.** It is a family of deep-learning systems from Google DeepMind that predict 3D molecular structure from sequence. AlphaFold 2 (AF2) was effectively the first method to reach near-experimental accuracy on single protein chains: at CASP14 its median backbone error was 0.96 Å, against 2.8 Å for the next-best method [5] ✅. AlphaFold 3 (AF3, May 2024) goes further and models joint complexes of proteins, DNA, RNA, small-molecule ligands, ions and modified residues [18] ✅.
- **Nobel Prize.** The 2024 Nobel Prize in Chemistry was split in two. One half went to David Baker "for computational protein design". The other half went jointly to Demis Hassabis and John Jumper "for protein structure prediction" [24] ✅.
- **AlphaFold DB.** It went from 365,198 structures in July 2021 to about 214.7 M in July 2022, then to 241,070,489 in v6. v6 was synced to UniProt 2025_03 and released in September/October 2025 [10][11] ✅. The site now advertises more than 260 M predictions (the FAQ gives 261,552,403 models, including 40,054 isoforms) [12] ✅. Since then it has added isoforms, MSAs, about 2.2 M NVIDIA-generated dimer predictions (2026) [12] ✅ ([verifier-corrected] was "about 4 M": the FAQ lists 2,158,419 homodimers and 79,156 heterodimers displayed; the March 2026 1.75 M homodimer set and the May 2026 ~2.2 M set overlap and must not be summed), 1,703,992 viral protein-complex predictions (September 2026) and literature-mined residue annotations (October 2026) [12] ✅.
- **AF3 licensing in 2026 (big changes).**
  - The AF3 code was relicensed from CC BY-NC-SA 4.0 to Apache 2.0 on 9 June 2026 (v3.0.3) [19] ✅.
  - Since 23 July 2026 the weights can be downloaded directly, with no request form. They are still under the **non-commercial** AF3 Model Parameters Terms [19][20] ✅.
  - Commercial use is routed through Google Cloud [19] ✅.
  - AF3 runs on CPU and Apple Silicon since v3.0.4 (28 July 2026) [19] ✅.
  - A watermarking variant, "SynthID Bio-structure", has been offered since 30 September 2026 [19] ✅.
- **AlphaFold Server** (free, non-commercial) currently allows 30 jobs/day and 5,000 tokens per job. You can add any ligand by its PDB Chemical Component Dictionary (CCD) code, but not by SMILES (a text notation for small molecules). Its terms (last modified 8 May 2024) prohibit commercial use, using outputs in docking/screening tools, and using outputs to train structure-prediction models [22][23] ✅.
- **Main limitations.**
  - It predicts single static structures, not ensembles or dynamics [18] ✅.
  - It hallucinates order in disordered regions (worse in AF3, which is a diffusion model) [18] ✅.
  - It is poor at predicting how point mutations change stability [42] ✅.
  - Antibody–antigen docking is still weak. One independent study found a 65% single-seed failure rate [39] ✅.
  - Protein–ligand "cofolding" models largely memorise binding poses seen in training [40] 🟡.
- **Open alternatives that you can use commercially.**
  - Boltz-1/Boltz-2 (MIT; Boltz-2 also predicts binding affinity) [58][59][60] ✅
  - Chai-1 (Apache 2.0, code and weights) [62] ✅
  - Protenix v0.x–v1 (Apache 2.0) [64] ✅
  - OpenFold3 / OpenBind-0 (Apache 2.0) [57] ✅
  - RF3 / RFdiffusion3 (BSD) [52][53] ✅
- **Organisational turbulence in 2026.**
  - John Jumper announced on 19 June 2026 that he was leaving DeepMind for Anthropic [35] ✅ ([verifier-corrected] upgraded from 🟡: confirmed in Jumper's own post on X of 19 June 2026 — "After nearly 9 years, I have decided to leave Google DeepMind and join Anthropic (after taking some time to recharge)" — and in CNBC the same day).
  - On 29 July 2026 the Financial Times reported that the dedicated AlphaFold team had been dissolved: most original AlphaFold authors were reassigned over the preceding year (Gemini-based projects, enzyme design, genomics, fusion), some moved to Isomorphic Labs, and nearly a quarter left Google (Jumper, Jonas Adler and Alexander Pritzel to Anthropic) [36] ✅ ([verifier-corrected] the FT article itself is paywalled, but the report is independently corroborated by the FT's own post on X, The Decoder (29 Jul 2026) and Scientific American (7 Aug 2026), which also notes that the public database and prediction server remain available). The wording that the AlphaFold system and database "will not be shut down" and the "more than 3 million researchers" figure come from Gigazine's summary of the FT piece and were not found in the other reports 🟡.
  - Isomorphic Labs' proprietary IsoDDE (February 2026) reports more than 2× AF3 accuracy on the hardest protein–ligand generalisation bin [32] ✅. No clinical trial had been publicly disclosed as of 29 September 2026 [34] ✅.
- **For dogs.** AlphaFold is species-agnostic. Dog-specific coverage, gaps and use cases are in `alphafold_and_dogs.md`; practical recipes are in `how_to_use_alphafold.md`.

---

## 1. The problem AlphaFold solves

### 1.1 Why structure matters
A protein is a chain of amino acids that folds into a specific 3D shape, and that shape largely determines what the protein does. Anfinsen's experiments, summarised in his 1973 Nobel lecture paper, established that the information needed to fold a protein is encoded in its sequence [1] ✅ (citation verified; the principle is textbook). "Predict the shape from the sequence" is the structure-prediction part of the protein folding problem. The AF2 paper describes it as an important open problem for more than 50 years [5] ✅.

### 1.2 Levinthal's paradox
Cyrus Levinthal pointed out that a protein cannot find its folded state by randomly searching all conformations: there are astronomically many. Yet real proteins fold in milliseconds to seconds. Zwanzig, Szabo & Bagchi (1992) give a quantitative treatment of the paradox [2] ✅ (citation verified; Levinthal's original 1968–69 remarks were not opened, ❓ for exact wording). Note that AlphaFold does not *simulate* folding. It learns a mapping from sequence (plus evolutionary information) to the final structure.

### 1.3 The data gap
The AF2 paper says experiments had determined structures for about 100,000 unique proteins. That is a small fraction of the billions of known protein sequences, and a single structure can take months to years [5] ✅.

### 1.4 CASP
CASP (Critical Assessment of protein Structure Prediction) is a biennial blind competition. Organisers release sequences of structures that have been solved but not yet published, and predictors submit models that are scored after the experimental structures come out [3] 🟡. The AF2 paper calls CASP "the gold-standard assessment for the accuracy of structure prediction" [5] ✅.

---

## 2. Full timeline

| Date | Event | Key facts | Src | Conf. |
|---|---|---|---|---|
| 2018 (CASP13; month 🟡) | **AlphaFold 1** at CASP13 | Predicted inter-residue *distance distributions* with a neural net, built a potential, and optimised it by gradient descent. Produced high-accuracy models (TM-score ≥ 0.7) for 24 of 43 free-modelling domains, against 14/43 for the next-best method. Published in *Nature* 577:706 (2020). | [4] | ✅ results; 🟡 date |
| 2020 (CASP14; month 🟡) | **AlphaFold 2** at CASP14 | Median backbone accuracy 0.96 Å r.m.s.d.95 (95% CI 0.85–1.16 Å), against 2.8 Å for the next-best method. | [5] | ✅ results; 🟡 date |
| Jul–Aug 2021 | AF2 paper and open-source code; human proteome paper | Jumper et al., *Nature* 596:583. Tunyasuvunakool et al., *Nature* 596:590 (human proteome). AF2 weights are now CC BY 4.0. The exact code-release day was not checked 🟡. | [5][6][75] | ✅ |
| 22 Jul 2021 | **AlphaFold DB** launched (EMBL-EBI + DeepMind) | "Initial release of 21 model organisms": 365,198 structures. | [10] | ✅ |
| Oct 2021 | **AlphaFold-Multimer** preprint | Extends AF2 to protein–protein complexes. | [13] | ✅ |
| Dec 2021 / Jan 2022 | AFDB adds Swiss-Prot, then WHO global-health proteomes | 804,872 structures, then 995,411. | [10] | ✅ |
| 28 Jul 2022 | AFDB expands to almost all of UniProt (2021_04) | 214,687,406 structures. | [10] | ✅ |
| Nov 2022 | AFDB v4 | Fixed a numerical bug affecting about 4.4% of predictions. | [10][12] | ✅ |
| 19 Sep 2023 | **AlphaMissense** (*Science* 381:eadg7492) | Fine-tuned from AlphaFold on human and primate population frequencies. Covers 71 M possible human missense variants: 57% likely benign, 32% likely pathogenic, 11% uncertain. **Human only.** Predictions have been CC BY 4.0 since 13 March 2024. **Weights not released.** | [14][15][16] | ✅ |
| 31 Oct 2023 | "Next generation of AlphaFold" preview | Covered nearly all molecule types in the PDB. | [17] | ✅ |
| 7 Jan 2024 | Isomorphic Labs deals with Eli Lilly and Novartis | Upfront payments of $45 M (Lilly) and $37.5 M (Novartis). Combined potential value "nearly $3 billion" excluding royalties. | [29] | ✅ |
| 8 May 2024 | **AlphaFold 3** (*Nature* 630:493) and **AlphaFold Server** | Models joint complexes of proteins, nucleic acids, ligands, ions and modified residues. At launch it was available only via the Server. | [18][37] | ✅ |
| 5 Sep 2024 | **AlphaProteo** (binder design) | 3- to 300-fold better binding affinities than the best existing methods on 7 targets. First successful AI-designed binder for VEGF-A. Not open-sourced. | [25][26] | ✅ |
| 9 Oct 2024 | **Nobel Prize in Chemistry** | ½ to Baker; ½ jointly to Hassabis and Jumper. | [24] | ✅ |
| 11 Nov 2024 | **AF3 code release** (v3.0.0) | Code under CC BY-NC-SA 4.0. Weights available on request (Google form, "2–3 business days"), under the AF3 Model Parameters Terms (dated 2024-11-09), non-commercial only. | [19][20] | ✅ |
| 23 Jan 2025 | AF3 v3.0.1 | Added flags such as `--num_seeds` and `--num_recycles`, and the option to output embeddings. | [19] | ✅ |
| 31 Mar 2025 | Isomorphic raises $600 M | Led by Thrive Capital. | [30] | ✅ |
| 2025 | **AlphaGenome** | DNA-sequence model taking 1 Mb of input. Predicts thousands of functional-genomics tracks. **Trained on human and mouse.** Published in *Nature* 649:1206 (2026). Weights on Kaggle/Hugging Face under non-commercial terms. | [27][28] | ✅ (June 2025 announcement date 🟡) |
| 15 Sep / 21 Oct 2025 | **AFDB v6** | Synced to UniProt 2025_03. 241,070,489 structures, including 40,054 isoforms. Per-entry MSAs added. Added 65.7 M / removed 39.3 M / changed 276,539 sequences relative to v4. | [10][11] | ✅ |
| 20 Jan 2026 | Isomorphic–Johnson & Johnson collaboration | Multi-modality: small molecules, antibodies, peptides, molecular glues. No financial terms disclosed. | [31] | ✅ |
| Feb 2026 | AFDB adds isoforms and collaborator sets | AllTheBacteria, Kinetoplastids, Viro3D, BFVD. | [12] | ✅ |
| 10 Feb 2026 | **Isomorphic IsoDDE** technical report | Proprietary. See §6.3. | [32] | ✅ |
| Mar & May 2026 | AFDB adds **NVIDIA dimer dataset** | 1,754,199 homodimers (March), then about 2.2 M homo- and heterodimers from 4,777 proteomes (May). Generated with ColabFold and AF2/AF-Multimer weights. Only the **16 model organisms + 30 WHO proteomes**. | [12] | ✅ |
| 20 Apr 2026 | AF3 v3.0.2 | Supports NVIDIA Blackwell GPUs. "Parameter files are compatible with any 3.0.x version." | [19] | ✅ |
| 12 May 2026 | Isomorphic Series B | $2.1 B, led by Thrive Capital. | [33] | ✅ |
| 9 Jun 2026 | **AF3 code relicensed to Apache 2.0** (v3.0.3) | Weights terms unchanged (non-commercial). | [19] | ✅ |
| 19 Jun 2026 | John Jumper announces move to Anthropic | Announced by Jumper himself on X; reported by CNBC and others. [verifier-corrected: primary source located; upgraded from 🟡.] | [35] | ✅ |
| 25 Jun 2026 | AFDB legacy API fields sunset | | [11] | ✅ |
| 23 Jul 2026 | **AF3 weights: direct download**, no request form | URL `storage.googleapis.com/alphafold3/af3.bin.zst`. Use remains subject to the non-commercial Terms. | [19] | ✅ |
| 28 Jul 2026 | AF3 v3.0.4 | Runs CPU-only (slow) and on Apple Silicon. | [19] | ✅ |
| 29 Jul 2026 | FT report: dedicated AlphaFold team dissolved | [verifier-corrected: date was "~30 Jul"; the FT published on 29 Jul 2026.] Most original authors reassigned (Gemini, enzyme design, genomics, fusion) or moved to Isomorphic; nearly a quarter left Google (Jumper, Adler, Pritzel to Anthropic). Corroborated by Scientific American (7 Aug 2026): the public database and server remain available. The "will not be shut down" and ">3 M users" lines are Gigazine's paraphrase. | [36] | ✅ report · 🟡 quoted statement |
| 21 Aug 2026 | AF3 README links commercial access | Via "Gemini Enterprise Agent Platform on Google Cloud". | [19] | ✅ |
| Sep 2026 | AFDB viral complexes and Portal View | 1,703,992 viral protein–protein complex predictions, plus the Viral AlphaFold Database (VAD, Atkinson lab). [verifier-corrected] The AFDB FAQ is internally inconsistent on scope: its release list says "~3,500 viral proteomes" while its dataset description says "~2,800 viral proteomes from 23 viral families"; press coverage (24 Sep 2026) says "more than 2,800 viruses". | [12][38] | ✅ |
| 29 Sep 2026 | Isomorphic update | "Our preclinical data is helping us to gear up for clinical developments." **No trial disclosed.** | [34] | ✅ |
| 30 Sep 2026 | **SynthID Bio-structure** | A fine-tuned AF3 that embeds an imperceptible watermark in predicted structures. Weights posted alongside AF3. | [19][78] | ✅ |
| Oct 2026 | AFDB adds AI-derived residue and mutation annotations | Text-mined by a PubMedBERT-based named-entity-recognition model and mapped via SIFTS. | [12] | ✅ |

**Not found.** I found no evidence of an "AlphaFold 4" release from Google DeepMind up to 4 October 2026. A *Nature* news item (19 February 2026) was headlined "'An AlphaFold 4' — scientists marvel at DeepMind drug spin-off's exclusive new AI", referring to IsoDDE. [verifier-corrected] The piece is openly syndicated at Scientific American (21 Feb 2026, https://www.scientificamerican.com/article/an-alphafold-4-scientists-marvel-at-deepmind-drug-spin-offs-exclusive-new-ai/); the "AlphaFold4" phrase is a quote from Mohammed AlQuraishi (Columbia University), and the article stresses that IsoDDE is proprietary and that its technical report "offers scant insight" into the method ✅.

---

## 3. How it works

### 3.1 Plain-English version
1. **Evolution as a clue (MSA, multiple sequence alignment).** AlphaFold first collects hundreds to thousands of related sequences of the same protein from other species and lines them up. If two positions always mutate together (co-evolve), they are probably touching in 3D. A mutation at one is compensated by a mutation at the other.
2. **Templates.** If a related protein's structure is already in the PDB, AlphaFold can use it as a rough guide.
3. **Reasoning about pairs.** The network keeps a big table recording, for every pair of residues, how they relate to each other. It repeatedly refines that table using geometric consistency. If A is near B and B is near C, that constrains A–C (the "triangle" idea).
4. **Building 3D coordinates.** A final module turns the pair table into atom positions.
5. **Recycling.** The output is fed back in a few times to polish it.
6. **Self-assessment.** The network also predicts how confident it is in each residue (pLDDT) and in each pair's relative position (PAE).

AF3 keeps steps 1–3 but slims down the MSA processing. It replaces step 4 with a **diffusion model**: the same family of generative model used in image generators. It starts from noisy atom clouds and denoises them into a structure. Because it works directly on atoms, AF3 can handle any molecule type, including drugs, DNA, RNA, metal ions and sugars [18] ✅.

### 3.2 Technical version: AlphaFold 2
- **Inputs.** The query sequence, an MSA (from genetic database searches) and structural templates [5] ✅.
- **Evoformer trunk.** Repeated blocks update an **MSA representation** (N_seq × N_res) and a **pair representation** (N_res × N_res). Information flows both ways between them. The pair track uses **triangle multiplicative updates** and **triangle self-attention**, which treat the pair representation as a graph of directed edges [5] ✅.
- **Structure module.** Each residue is a rigid body (a "residue gas"): a backbone frame plus side-chain χ angles. Frames start at the identity/origin and are refined with **Invariant Point Attention (IPA)** [5] ✅.
- **Recycling.** The whole network is applied iteratively to its own outputs. The authors say this "contributes markedly to accuracy with minor extra training time" [5] ✅.
- **Confidence.** pLDDT predicts per-residue lDDT-Cα, and the predicted TM-score is accurately estimated [5] ✅.
- **AlphaFold-Multimer** retrains the system on complexes and adds cross-chain MSA pairing [13] ✅.

### 3.3 Technical version: AlphaFold 3
- **Tokens.** One token per standard residue or nucleotide, and one token per atom for ligands and modified residues [22] ✅.
- **Pairformer** replaces the Evoformer and reduces MSA processing. It has **48 blocks**, each with its own parameters; channels are 128 (pair) and 384 (single) [18] ✅.
- **Diffusion module.** It "operates directly on raw atom coordinates … without rotational frames or any equivariant processing". This removes the need for torsion parametrisation and stereochemical violation losses [18] ✅. The network is trained to denoise noised coordinates.
- **Hallucination control.** Generative models can invent plausible-looking structure in unstructured regions. AF3 counters this with **cross-distillation**: AF-Multimer v2.3 predictions, in which disorder appears as extended loops, are added to the training data [18] ✅.
- **Confidence head.** It is trained on a fast diffusion "mini-rollout" and uses the pair representation to predict a modified pLDDT and a PAE matrix "as in AF2", plus further error terms from which pTM/ipTM are derived [18] ✅ (the exact list of heads is in the Supplement, which I did not read 🟡).
- **Training cutoff.** No structural data released after **30 September 2021**. The PoseBusters evaluation used a separate model with a 30 September 2019 cutoff [18] ✅.
- **Molecule types.** Proteins, DNA, RNA, ligands (CCD codes; SMILES locally), ions, covalent modifications/PTMs, glycans (including branched) and modified nucleotides [18][22] ✅. AF3 does **not** predict waters or hydrogens and is unaware of membranes [22] ✅.

---

## 4. Confidence metrics and how to read them

| Metric | Scope | What it means | Rules of thumb (official) | Src |
|---|---|---|---|---|
| **pLDDT** (0–100) | Per residue (AF2) or per atom (AF3) | Predicted local accuracy, i.e. how well local geometry matches | >90 very high · 70–90 confident · 50–70 low · <50 very low (often disordered) | [12][18][22] ✅ |
| **PAE** (Å) | Pairs of residues or tokens | Expected position error of token *j* when the prediction is aligned on token *i*. Low PAE between two domains means their **relative placement** is reliable. | Look at the off-diagonal blocks between domains or chains | [12][22] ✅ |
| **pTM** (0–1) | Whole structure | Predicted TM-score of the overall fold | >0.5 means the overall fold *might* be similar to the true one | [22] ✅ |
| **ipTM** (0–1) | Interfaces | Confidence in relative positions of subunits | >0.8 confident · <0.6 likely failed · 0.6–0.8 grey zone | [22] ✅ |
| `chain_pair_iptm`, `chain_pair_pae_min` | Specific chain pairs | Interface confidence for a chosen pair. Minimum PAE across a pair "correlates with whether two chains interact" and can sometimes distinguish binders from non-binders. | Use when you care about one interface, e.g. antibody–antigen | [22] ✅ |
| `ranking_score` | Per sample | 0.8·ipTM + 0.2·pTM + 0.5·disorder − 100·has_clash | **Only for ranking samples**, not as an accuracy estimate | [22] ✅ |

**Caveats from the AlphaFold Server FAQ** [22] ✅:
- pTM is unreliable for chains shorter than about 16–20 residues. Use pLDDT or PAE for peptides.
- Disordered tails depress nearby pLDDT. Trimming them gives a clearer picture.
- For antibody–antigen complexes, run multiple seeds and take the top-ranked sample.

Confidence is *correlated* with accuracy, but the strength of that correlation differs by molecule type [22] ✅. Terwilliger et al. compared AF predictions with experimental crystallographic maps and conclude that predictions are "exceptionally useful hypotheses". Even very high-confidence predictions can be distorted globally (domain orientation) or locally (side chains) [45] ✅.

---

## 5. What AlphaFold does well, and what it cannot do

### 5.1 Strengths
- **Single-domain folds with deep MSAs.** These reach near-experimental accuracy [5] ✅.
- **Complexes (AF3).** AF3 was far more accurate than classical docking (Vina) on PoseBusters V1 (428 protein–ligand complexes), with Fisher's exact P = 2.27 × 10⁻¹³. It was also far better than blind cofolding with RoseTTAFold All-Atom (P = 4.45 × 10⁻²⁵) [18] ✅. Protein–nucleic-acid accuracy was higher than RoseTTAFold2NA's, and protein–protein accuracy rose over AF-Multimer v2.3 (P = 1.8 × 10⁻¹⁸) [18] ✅.
- **Very large assemblies.** Examples include a 7,663-residue 40S ribosomal subunit complex and a 4,665-residue glycosylated coronavirus spike bound by antibodies [18] ✅.

### 5.2 Limitations (with evidence)

| Limitation | Evidence | Conf. |
|---|---|---|
| **Intrinsically disordered regions (IDRs).** Low pLDDT often flags disorder, but an AF model of an IDR is not a "structure". AF3 can output spurious helices in disordered regions that lack AF2's tell-tale ribbon look. | [18][22]; discussion in Ruff & Pappu [44] | ✅ ([44] 🟡) |
| **Dynamics and ensembles.** Models are static, PDB-like snapshots. Multiple AF3 seeds "do not produce an approximation of the solution ensemble". | [18] | ✅ |
| **Apo vs holo states.** In the AF3 paper, cereblon was predicted in the *closed* (ligand-bound) conformation even without a ligand. | [18] | ✅ |
| **Workarounds for alternative states.** MSA subsampling/clustering (AF-Cluster) and generative ensemble emulators (BioEmu) can partly recover alternative states. | [46][47] | ✅ (titles/abstracts) |
| **Effects of point mutations on stability (ΔΔG).** Changes in AF pLDDT showed "very weak or no correlation" with experimental ΔΔG or GFP fluorescence. AF usually returns essentially the same fold for a destabilising missense variant. | [42]; [43] | ✅ ([43] 🟡) |
| **Antibody–antigen docking.** AF3 improved markedly over AF-Multimer (Wilcoxon P = 6.5 × 10⁻⁵) only when ranking over **1,000 seeds**. An independent test found single-seed high-accuracy docking success of 10.2% (antibodies) and 13.3% (nanobodies), and "AF3's 65% failure rate for antibody and nanobody docking (with single seed sampling)". | [18]; [39] | ✅ |
| **Benchmark numbers for antibody–antigen.** On FoldBench (post-January 2023 structures, DockQ ≥ 0.23), AF3 scored 47.9% antibody–antigen success, against 75.6% for IsoDDE. On Isomorphic's 334-structure novel-interface set, IsoDDE reached 39% at DockQ > 0.8, described as 2.3× AF3 and 19.8× Boltz-2. | [32] (FoldBench values as reported in [32], citing [41]) | ✅ for the report; 🟡 for FoldBench itself |
| **Ligand memorisation / generalisation.** Runs N' Poses (about 2,600 post-cutoff systems) found that current cofolding methods "largely memorise ligand poses from their training data". | [40] | 🟡 (abstract) |
| **Stereochemistry.** Chirality is sometimes wrong. There are occasional clashes, and whole overlapping chains in some homomers, mostly in large protein–nucleic-acid complexes. | [18][22] | ✅ |
| **Shallow MSAs.** AF3 has "a very similar dependence on MSA depth" to AF-Multimer v2.3: shallow MSAs mean lower accuracy. This matters for orphan or lineage-specific proteins. | [18] | ✅ |
| **Data leakage.** Training includes PDB structures up to 30 September 2021 [18] ✅. Any complex solved before then (e.g. IGF-1/IGF1R 5U8Q (2018) and 6PYH (2019); GH/GHR 3HHR (1992)) was likely seen in training, so reproducing it is **recall, not discovery** [79] ✅. Fair evaluation needs time-split, low-homology sets (PoseBusters, Runs N' Poses, FoldBench). | [18][40][41][79] | ✅/🟡 |
| **Licensing restrictions.** Server and weights are non-commercial. Outputs cannot be used to train competing structure models, and Server outputs cannot be fed to docking/screening tools. | [20][23] | ✅ |
| **Not validated for clinical use.** Explicit disclaimer in the Server terms and the AF3 README. | [19][23] | ✅ |

---

## 6. Competitors and open alternatives

### 6.1 Overview table

| Model (org) | Year | What it does | Licence / availability (as checked 2026-10-04) | Src | Conf. |
|---|---|---|---|---|---|
| **AlphaFold 2 / Multimer** (DeepMind) | 2021 | Proteins and protein complexes | Weights CC BY 4.0; code open | [5][13][75] | ✅ |
| **AlphaFold 3** (DeepMind / Isomorphic) | 2024 | All-atom complexes | Code Apache 2.0 (since June 2026); weights non-commercial; Server non-commercial; commercial via Google Cloud | [19][20] | ✅ |
| **RoseTTAFold** (Baker lab) | 2021 | Three-track network for structures and interactions | Open | [48] | ✅ |
| **RoseTTAFold All-Atom / RFdiffusionAA** | 2024 | Proteins, nucleic acids, small molecules, metals, covalent modifications; ligand-binder design | Open | [49] | ✅ |
| **RFdiffusion** | 2023 | Diffusion-based de novo protein design | Open | [50] | ✅ |
| **RF3 (RoseTTAFold-3) + RFdiffusion3** (Foundry/AtomWorks) | 2025 | AF3-class prediction with improved chirality; all-atom design | BSD | [51][52][53] | ✅ |
| **ESMFold** (Meta) | 2023 | Single-sequence (no MSA) prediction from a 15 B-parameter language model. Produced the ESM Metagenomic Atlas (>617 M structures). | Open | [54] | ✅ |
| **ESM3** (EvolutionaryScale) | 2025 | Generative multimodal model of sequence, structure and function. Designed a GFP 58% identical to known proteins. | Varies by model size (not rechecked) | [55] | ✅ (licence ❓) |
| **OpenFold** | 2024 | Trainable AF2 reproduction | Open | [56] | ✅ |
| **OpenFold3-preview / OpenBind-0** | 2025–26 | Open AF3 reproduction. Default weights since v0.5.0 are "OpenBind-0", with a June 2025 training cutoff. | Apache 2.0 | [57] | ✅ |
| **Boltz-1** (MIT/Recursion) | Nov 2024 | Open AF3-level complexes; "Boltz-steering" | MIT (code, weights, data) | [58] | ✅ |
| **Boltz-2** | Jun 2025 | Structure **plus binding affinity**. "First AI model to approach the performance of FEP" (free-energy perturbation physics simulations), and ≥1000× faster. Outputs `affinity_probability_binary` and `affinity_pred_value` (log10 IC50, µM). | MIT (academic and commercial) | [59][60] | ✅ |
| **Chai-1** (Chai Discovery) | Sep 2024 | AF3-class; restraint prompting; single-sequence mode | **Apache 2.0, code and weights** (originally non-commercial weights) | [61][62] | ✅ |
| **Chai-2** | 2025 | Zero-shot antibody design ("in a 24-well plate") | Not open (technical report only) | [62] | ✅ title; performance ❓ |
| **Protenix** (ByteDance) | 2025 → v1 (Feb 2026) → v2 (Apr 2026) | AF3 reproduction. v1 claims to beat AF3 at the same data cutoff, model scale and inference budget. v2 improves antibody–antigen. | v0.x–v1 Apache 2.0; **v2 weights proprietary** | [63][64] | ✅ |
| **HelixFold3** (Baidu PaddleHelix) | Aug 2024 | AF3 replication | Repository licence "NOASSERTION"; terms not checked | [65] | ✅ / licence ❓ |
| **SeedFold** (ByteDance Seed) | Dec 2025 | Scales Pairformer width; linear triangular attention; large distillation set | Not checked | [66] | ✅ abstract |
| **Pearl** (Genesis Molecular AI) | Oct 2025 | Protein–ligand cofolding foundation model | Not checked | [67] | ✅ abstract |
| **IsoDDE** (Isomorphic Labs) | Feb 2026 | Structure, pocket finding and affinity | **Proprietary**, internal use | [32] | ✅ |
| **AlphaProteo** (DeepMind) | Sep 2024 | De novo binder design | Not released | [25][26] | ✅ |

### 6.2 Head-to-head numbers (FoldBench, as tabulated in the IsoDDE report)
Success rate of the top-confidence prediction on post-January 2023 structures. Antibody–antigen and protein–protein columns use DockQ ≥ 0.23. The protein–ligand column uses pocket-aligned RMSD < 2 Å and LDDT-PLI > 0.8 [32] ✅ (as reported; values for most models were taken by Isomorphic from the FoldBench website [41]).

| Model | Antibody–antigen | Protein–ligand | Protein–protein |
|---|---|---|---|
| IsoDDE | 75.58 | 75.99 | 74.19 |
| AlphaFold 3 | 47.90 | 64.90 | 72.93 |
| Protenix-v1 | 50.12 | 62.79 | 74.00 |
| SeedFold | 53.21 | 63.12 | 74.03 |
| SeedFold-Linear | 46.91 | 66.48 | 74.14 |
| Chai-1 | 23.64 | 51.23 | 68.53 |
| HelixFold 3 | 28.40 | 51.82 | 66.27 |
| Protenix (v0.x) | 34.13 | 50.70 | 68.18 |
| OpenFold 3 (preview) | 28.83 | 44.49 | 69.96 |

Boltz-1/2 do not appear in that table. Caution: this table comes from a company promoting its own model 🟡.

### 6.3 IsoDDE details (Isomorphic Labs, 10 February 2026) [32] ✅
- **Runs N' Poses, hardest bin (0–20% similarity to training).** IsoDDE had a 50% success rate (30/60), "more than doubles" AF3. [verifier-corrected] The 23.3% figure for AF3 is not merely from secondary sources: the technical report's own table gives AF3 23.3% vs IsoDDE 50.0% on the same 60 systems (filtered set 18.0% vs 44.0%, n = 50; filtered + clustered 16.7% vs 37.2%, n = 39) ✅. The report states that IsoDDE "has the same training cutoff date as AF3" ✅.
- **Antibody–antigen (334 novel interfaces).**
  - 39% at DockQ > 0.8, i.e. 2.3× AF3 and 19.8× Boltz-2.
  - 63% at DockQ > 0.23 with one seed.
  - CDR-H3 loop (the most variable antibody loop) within ≤2 Å backbone RMSD for 70% of antibodies (AF3 58%, Boltz-2 43%).
- **Affinity.** IsoDDE claims to exceed FEP+ physics methods.

---

## 7. Real-world applications (selected, with sources)

- **Usage scale.** DeepMind reports more than 3 M users in more than 190 countries, more than 1 M of them in low- and middle-income countries, and more than 40,000 citations [37] ✅ (company figures). The older "over 2 million researchers in over 190 countries" figure for the AFDB also appears on DeepMind's AlphaFold page [37] ✅. [verifier-corrected] That figure could not be found in the Nobel press release or the Nobel "popular information" page, so the earlier attribution of it to the Nobel committee has been dropped 🟡.
- **Integrative structural biology.** The structure of the human nuclear pore complex (about 120 MDa; about 1,000 proteins from about 30 distinct nucleoporins) was assembled using AI-based models [69] ✅.
- **Vaccines.** The structure of the malaria transmission-blocking vaccine candidate Pfs48/45 and its recognition by antibodies [70] ✅ (title/metadata; AF's specific role not re-read 🟡).
- **Drug discovery on a target with no experimental structure.** Insilico Medicine used an AF-predicted CDK20 structure with generative chemistry. It found a hit with K_d = 9.2 ± 0.5 µM within 30 days of target selection, after synthesising only 7 compounds [71] ✅.
- **Proteome-scale complexes.** Core eukaryotic protein complexes (yeast) [72] and a structurally resolved human protein-interaction network [73] ✅ (titles/metadata).
- **Clustering the protein universe.** AFDB-scale structure clustering revealed new folds and families [74] ✅ (title/metadata).
- **Veterinary and dog examples:** see `alphafold_and_dogs.md` §4.

---

## 8. Cross-reference: IBM MAMMAL vs AF3
The YouTube video in this dossier claims that IBM's MAMMAL beat AlphaFold 3 on five of seven antibody–antigen targets ([video at 23:03](https://www.youtube.com/watch?v=s3rNDndvav0&t=1383s); transcript not redistributed).

Per the sister file `02_mammal/mammal_paper_deep_dive.md` [77]:
- The comparison is between MAMMAL *fine-tuned* on labelled binders/non-binders and AF3 used *zero-shot*, with ipTM/pTM as a binding score.
- The test sets are tiny (n = 28–60 per target).
- Without fine-tuning, MAMMAL was near chance.

This is a binder-*classification* comparison, not a structure-accuracy comparison. It should not be read as "MAMMAL predicts structures better than AF3". See the MAMMAL files for details (not re-verified here).

---

## Open questions / gaps

- **Antibody–antigen headline figures in the AF3 paper.** The exact percentages for AF3 vs AF-M are shown only in Fig. 1c/5a bars. I did not extract them from the text and so have not quoted them.
- **Future of the AlphaFold programme after the July 2026 team dissolution.** The FT report (29 Jul 2026) is corroborated by Scientific American and The Decoder, but the FT text itself is paywalled, and DeepMind's exact statement is known only through paraphrase. Long-term maintenance commitments for AlphaFold Server and AFDB beyond "remain available" / "will not be shut down" are not documented.
- **Is a successor model (an "AlphaFold 4") coming from DeepMind?** None found. IsoDDE is proprietary and unpublished in peer-reviewed form.
- **AlphaFold Server FAQ is stale.** As of 2026-10-04 it still says AF3 weights require a request form, while GitHub shows direct download since 23 July 2026 [19][22]. Treat GitHub as authoritative.
- **Commercial Google Cloud AF3.** Pricing and allowlist terms were not retrievable.
- **Licences not checked:** HelixFold3, SeedFold, Pearl and ESM3.
- **FoldBench and Runs N' Poses.** Read via abstracts and a third-party report, not the full papers.

---

## Sources

1. Anfinsen CB (1973). Principles that govern the folding of protein chains. *Science* 181:223–230. doi:10.1126/science.181.4096.223
2. Zwanzig R, Szabo A, Bagchi B (1992). Levinthal's paradox. *PNAS* 89:20–22. doi:10.1073/pnas.89.1.20
3. Moult J, Pedersen JT, Judson R, Fidelis K (1995). A large-scale experiment to assess protein structure prediction methods. *Proteins* 23:ii–v. doi:10.1002/prot.340230303
4. Senior AW et al. (2020). Improved protein structure prediction using potentials from deep learning. *Nature* 577:706–710. doi:10.1038/s41586-019-1923-7
5. Jumper J et al. (2021). Highly accurate protein structure prediction with AlphaFold. *Nature* 596:583–589. doi:10.1038/s41586-021-03819-2 (full text read via Europe PMC PMC8371605)
6. Tunyasuvunakool K et al. (2021). Highly accurate protein structure prediction for the human proteome. *Nature* 596:590–596. doi:10.1038/s41586-021-03828-1
7. Varadi M et al. (2022). AlphaFold Protein Structure Database: massively expanding the structural coverage of protein-sequence space with high-accuracy models. *Nucleic Acids Res* 50:D439–D444. doi:10.1093/nar/gkab1061
8. Varadi M et al. (2024). AlphaFold Protein Structure Database in 2024: providing structure coverage for over 214 million protein sequences. *Nucleic Acids Res* 52:D368–D375. doi:10.1093/nar/gkad1011
9. Bertoni D et al. (2026). AlphaFold Protein Structure Database 2025: a redesigned interface and updated structural coverage. *Nucleic Acids Res* 54:D358–D362. doi:10.1093/nar/gkaf1226
10. AlphaFold DB CHANGELOG.txt. https://ftp.ebi.ac.uk/pub/databases/alphafold/CHANGELOG.txt (accessed 2026-10-04)
11. PDBe/EMBL-EBI. AlphaFold Database release notes (v6), 21 Oct 2025. https://www.ebi.ac.uk/pdbe/news/alphafold-database-release-notes (accessed 2026-10-04)
12. AlphaFold DB homepage, "What's new" and FAQ. https://alphafold.ebi.ac.uk/ and https://alphafold.ebi.ac.uk/faq (accessed 2026-10-04)
13. Evans R et al. (2021). Protein complex prediction with AlphaFold-Multimer. bioRxiv. doi:10.1101/2021.10.04.463034
14. Cheng J et al. (2023). Accurate proteome-wide missense variant effect prediction with AlphaMissense. *Science* 381:eadg7492. doi:10.1126/science.adg7492
15. Google DeepMind blog (19 Sep 2023). A catalogue of genetic mutations to help pinpoint the cause of diseases. https://deepmind.google/discover/blog/a-catalogue-of-genetic-mutations-to-help-pinpoint-the-cause-of-diseases/
16. google-deepmind/alphamissense GitHub README. https://github.com/google-deepmind/alphamissense (accessed 2026-10-04)
17. Isomorphic Labs (31 Oct 2023). A glimpse of the next generation of AlphaFold. https://www.isomorphiclabs.com/articles/a-glimpse-of-the-next-generation-of-alphafold
18. Abramson J et al. (2024). Accurate structure prediction of biomolecular interactions with AlphaFold 3. *Nature* 630:493–500. doi:10.1038/s41586-024-07487-w (full text read via Europe PMC PMC11168924)
19. google-deepmind/alphafold3 GitHub: README, release notes v3.0.0–v3.0.4, commit history (commits 7b197fe8 relicensing 2026-06-09; dd1a7bad weights instructions 2026-07-23; 9b30e9aa Cloud API 2026-08-21; b0960236 SynthID 2026-09-30). https://github.com/google-deepmind/alphafold3 (accessed 2026-10-04)
20. AlphaFold 3 Model Parameters Terms of Use (Last Modified 2024-11-09). https://github.com/google-deepmind/alphafold3/blob/main/WEIGHTS_TERMS_OF_USE.md
21. AlphaFold 3 installation documentation. https://github.com/google-deepmind/alphafold3/blob/main/docs/installation.md
22. AlphaFold Server FAQ. https://alphafoldserver.com/faq (accessed 2026-10-04)
23. AlphaFold Server Additional Terms of Service (Last Modified 8 May 2024). https://alphafoldserver.com/terms (accessed 2026-10-04)
24. Royal Swedish Academy of Sciences (9 Oct 2024). Press release: The Nobel Prize in Chemistry 2024. https://www.nobelprize.org/prizes/chemistry/2024/press-release/
25. Zambaldi V et al. (2024). De novo design of high-affinity protein binders with AlphaProteo. arXiv:2409.08022
26. Google DeepMind blog (5 Sep 2024). AlphaProteo generates novel proteins for biology and health research. https://deepmind.google/discover/blog/alphaproteo-generates-novel-proteins-for-biology-and-health-research/
27. Avsec Ž et al. (2026). Advancing regulatory variant effect prediction with AlphaGenome. *Nature* 649:1206–1218. doi:10.1038/s41586-025-10014-0
28. google-deepmind/alphagenome_research GitHub README. https://github.com/google-deepmind/alphagenome_research (accessed 2026-10-04)
29. Isomorphic Labs (7 Jan 2024). Isomorphic Labs kicks off 2024 with two pharmaceutical collaborations. https://www.isomorphiclabs.com/articles/isomorphic-labs-kicks-off-2024-with-two-pharmaceutical-collaborations
30. Isomorphic Labs (31 Mar 2025). Isomorphic Labs announces $600m external investment round. https://www.isomorphiclabs.com/articles/isomorphic-labs-announces-600m-external-investment-round
31. Isomorphic Labs (20 Jan 2026). Isomorphic Labs enters into a research collaboration with Johnson & Johnson. https://www.isomorphiclabs.com/articles/isomorphic-labs-enters-into-a-research-collaboration-with-johnson-johnson
32. Isomorphic Labs Team (10 Feb 2026). Accurate Predictions of Novel Biomolecular Interactions with IsoDDE (technical report, 27 pp.) and article "The Isomorphic Labs Drug Design Engine unlocks a new frontier beyond AlphaFold". https://storage.googleapis.com/isomorphiclabs-website-public-artifacts/isodde_technical_report.pdf ; https://www.isomorphiclabs.com/articles/the-isomorphic-labs-drug-design-engine-unlocks-a-new-frontier
33. Isomorphic Labs (12 May 2026). Isomorphic Labs secures $2.1 billion funding. https://www.isomorphiclabs.com/press/isomorphic-labs-funding
34. Isomorphic Labs (29 Sep 2026). Building a new path to make medicines with AI. https://www.isomorphiclabs.com/articles/building-a-new-path-to-make-medicines-with-ai
35. John Jumper on X (19 Jun 2026), https://x.com/JohnJumperSci/status/2068001285173834106 (primary announcement); CNBC (19 Jun 2026). "John Jumper to leave Google DeepMind for Anthropic." https://www.cnbc.com/2026/06/19/john-jumper-to-leave-google-deepmind-for-anthropic.html [verifier-corrected: primary source added] ✅
36. Financial Times (29 Jul 2026), paywalled; FT's announcement on X: https://x.com/FT/status/2082466446483837214. Corroboration: The Decoder (29 Jul 2026), "Deepmind dismantles its AlphaFold team as key authors leave for Anthropic", https://the-decoder.com/deepmind-dismantles-its-alphafold-team-as-key-authors-leave-for-anthropic/ ; Scientific American (7 Aug 2026), "Why Google DeepMind broke up the AlphaFold team", https://www.scientificamerican.com/article/why-google-deepmind-broke-up-the-alphafold-team/ ; GIGAZINE (30 Jul 2026), https://gigazine.net/gsc_news/en/20260730-google-deepmind-alphafold-team/ (source of the "will not be shut down" and "3 million" wording) [verifier-corrected] ✅ report / 🟡 quoted statement
37. Google DeepMind. AlphaFold science page. https://deepmind.google/science/alphafold/ (accessed 2026-10-04)
38. Phys.org / EMBL (24 Sep 2026). New AlphaFold Database release adds viral protein complexes to support pandemic preparedness. https://phys.org/news/2026-09-alphafold-database-viral-protein-complexes.html 🟡
39. Hitawala FN, Gray JJ (2025). What does AlphaFold3 learn about antibody and nanobody docking, and what remains unsolved? *mAbs* 17:2545601. doi:10.1080/19420862.2025.2545601
40. Škrinjar P, Eberhardt J, Tauriello G, Schwede T, Durairaj J (2025). Have protein-ligand cofolding methods moved beyond memorisation? bioRxiv. doi:10.1101/2025.02.03.636309
41. Xu S et al. (2026). Benchmarking all-atom biomolecular structure prediction with FoldBench. *Nat Commun* 17:442. doi:10.1038/s41467-025-67127-3 (cited via [32]; not opened 🟡)
42. Pak MA et al. (2023). Using AlphaFold to predict the impact of single mutations on protein stability and function. *PLoS One* 18:e0282689. doi:10.1371/journal.pone.0282689
43. Buel GR, Walters KJ (2022). Can AlphaFold2 predict the impact of missense mutations on structure? *Nat Struct Mol Biol* 29:1–2. doi:10.1038/s41594-021-00714-2
44. Ruff KM, Pappu RV (2021). AlphaFold and implications for intrinsically disordered proteins. *J Mol Biol* 433:167208. doi:10.1016/j.jmb.2021.167208
45. Terwilliger TC et al. (2024). AlphaFold predictions are valuable hypotheses and accelerate but do not replace experimental structure determination. *Nat Methods* 21:110–116. doi:10.1038/s41592-023-02087-4
46. Wayment-Steele HK et al. (2024). Predicting multiple conformations via sequence clustering and AlphaFold2. *Nature* 625:832–839. doi:10.1038/s41586-023-06832-9
47. Lewis S et al. (2025). Scalable emulation of protein equilibrium ensembles with generative deep learning. *Science* 389:eadv9817. doi:10.1126/science.adv9817
48. Baek M et al. (2021). Accurate prediction of protein structures and interactions using a three-track neural network. *Science* 373:871–876. doi:10.1126/science.abj8754
49. Krishna R et al. (2024). Generalized biomolecular modeling and design with RoseTTAFold All-Atom. *Science* 384:eadl2528. doi:10.1126/science.adl2528
50. Watson JL et al. (2023). De novo design of protein structure and function with RFdiffusion. *Nature* 620:1089–1100. doi:10.1038/s41586-023-06415-8
51. Butcher J et al. (2025). De novo design of all-atom biomolecular interactions with RFdiffusion3. bioRxiv. doi:10.1101/2025.09.18.676967
52. Corley N et al. (2025). Accelerating biomolecular modeling with AtomWorks and RF3. bioRxiv. doi:10.1101/2025.08.14.670328
53. RosettaCommons/foundry GitHub README (BSD-3-Clause). https://github.com/RosettaCommons/foundry (accessed 2026-10-04)
54. Lin Z et al. (2023). Evolutionary-scale prediction of atomic-level protein structure with a language model. *Science* 379:1123–1130. doi:10.1126/science.ade2574
55. Hayes T et al. (2025). Simulating 500 million years of evolution with a language model. *Science* 387:850–858. doi:10.1126/science.ads0018
56. Ahdritz G et al. (2024). OpenFold: retraining AlphaFold2 yields new insights into its learning mechanisms and capacity for generalization. *Nat Methods* 21:1514–1524. doi:10.1038/s41592-024-02272-z
57. aqlaboratory/openfold-3 GitHub README (Apache 2.0). https://github.com/aqlaboratory/openfold-3 (accessed 2026-10-04)
58. Wohlwend J et al. (2024). Boltz-1: Democratizing biomolecular interaction modeling. bioRxiv. doi:10.1101/2024.11.19.624167
59. Passaro S et al. (2025). Boltz-2: Towards accurate and efficient binding affinity prediction. bioRxiv. doi:10.1101/2025.06.14.659707
60. jwohlwend/boltz GitHub README (MIT). https://github.com/jwohlwend/boltz (accessed 2026-10-04)
61. Chai Discovery et al. (2024). Chai-1: Decoding the molecular interactions of life. bioRxiv. doi:10.1101/2024.10.10.615955
62. chaidiscovery/chai-lab GitHub README (Apache 2.0, code and weights; cites the Chai-2 technical report "Zero-shot antibody design in a 24-well plate", 2025). https://github.com/chaidiscovery/chai-lab (accessed 2026-10-04)
63. ByteDance AML AI4Science Team et al. (2025). Protenix: Advancing structure prediction through a comprehensive AlphaFold3 reproduction. bioRxiv. doi:10.1101/2025.01.08.631967
64. bytedance/Protenix GitHub README (Protenix-v1 2026-02-05, Protenix-v2 2026-04-08). https://github.com/bytedance/Protenix (accessed 2026-10-04)
65. Liu L et al. (2024). Technical report of HelixFold3 for biomolecular structure prediction. arXiv:2408.16975
66. Zhou Y et al. (2025). SeedFold: Scaling biomolecular structure prediction. arXiv:2512.24354
67. Genesis Research Team et al. (2025). Pearl: A foundation model for placing every atom in the right location. arXiv:2510.24670
68. Mirdita M et al. (2022). ColabFold: making protein folding accessible to all. *Nat Methods* 19:679–682. doi:10.1038/s41592-022-01488-1
69. Mosalaganti S et al. (2022). AI-based structure prediction empowers integrative structural analysis of human nuclear pores. *Science* 376:eabm9506. doi:10.1126/science.abm9506
70. Ko KT et al. (2022). Structure of the malaria vaccine candidate Pfs48/45 and its recognition by transmission blocking antibodies. *Nat Commun* 13:5603. doi:10.1038/s41467-022-33379-6
71. Ren F et al. (2023). AlphaFold accelerates artificial intelligence powered drug discovery: efficient discovery of a novel CDK20 small molecule inhibitor. *Chem Sci* 14:1443–1452. doi:10.1039/d2sc05709c
72. Humphreys IR et al. (2021). Computed structures of core eukaryotic protein complexes. *Science* 374:eabm4805. doi:10.1126/science.abm4805
73. Burke DF et al. (2023). Towards a structurally resolved human protein interaction network. *Nat Struct Mol Biol* 30:216–225. doi:10.1038/s41594-022-00910-8
74. Barrio-Hernandez I et al. (2023). Clustering predicted structures at the scale of the known protein universe. *Nature* 622:637–645. doi:10.1038/s41586-023-06510-w
75. google-deepmind/alphafold (AF2) GitHub README: model parameters CC BY 4.0. https://github.com/google-deepmind/alphafold (accessed 2026-10-04)
76. Zhang J et al. (2025). Assessment of protein complex predictions in CASP16: Are we making progress? bioRxiv. doi:10.1101/2025.05.29.656875 (title only; listed for further reading)
77. This dossier: `02_mammal/mammal_paper_deep_dive.md` (sister agent; not re-verified here)
78. google-deepmind/synthidbio GitHub. https://github.com/google-deepmind/synthidbio (accessed 2026-10-04)
79. RCSB PDB entries 5U8Q (human IGF1R ectodomain + IGF-I, X-ray 3.27 Å, released 2018-02-28), 6PYH (IGF1R–IGF1 cryo-EM 4.3 Å, released 2019-10-23; mouse IGF1R ×2 + human IGF-1 ×1), 3HHR (hGH–GHR extracellular domain, 2.8 Å, released 1994). https://data.rcsb.org (accessed 2026-10-04)

---

## Verification notes

*Independent check by Fable 5.1, 2026-10-04. Full report: `../07_verification/alphafold_verification.md`.*

- **Method.** About 95 web calls: GitHub via the `gh` CLI (commit and release metadata for google-deepmind/alphafold3, alphamissense, ColabFold, openfold-3, PaddleHelix), raw README/terms/installation/input docs, the AlphaFold Server FAQ and Terms and the AFDB FAQ/homepage read in a browser (they are JavaScript-rendered), AFDB and UniProt REST, the AFDB FTP listing and CHANGELOG, PDBe release notes, RCSB, Europe PMC full texts (Jumper 2021, Abramson 2024 and 29 other papers), Crossref for 70 DOIs, arXiv, Isomorphic Labs, DeepMind, Nobel, CNBC/X, The Decoder, Scientific American, Gigazine, phys.org, and the IsoDDE technical report PDF (text-extracted).
- **Headline items all held up:** AF3 relicensing to Apache 2.0 on 9 Jun 2026 (commit 7b197fe8, v3.0.3); direct weight download since 23 Jul 2026 (commit dd1a7bad) under the unchanged non-commercial 2024-11-09 terms; Google Cloud commercial route (21 Aug 2026); v3.0.4 CPU/Apple Silicon (28 Jul 2026); SynthID Bio-structure (30 Sep 2026); AlphaFold Server 30 jobs/day, 5,000 tokens, CCD-only ligands, terms dated 8 May 2024; AFDB v6 figures and the 25-06-2026 API sunset; all 2024–2026 Isomorphic Labs figures; the 2024 Nobel split; the Hitawala & Gray and Hu & Xie numbers; the IsoDDE and FoldBench numbers (checked against the 27-page report).
- **Corrected in place** (each marked `[verifier-corrected]`): the TL;DR NVIDIA dimer total ("about 4 M" → ~2.2 M; the two releases overlap); the FT report date (29 Jul, not ~30 Jul 2026) and its sourcing; the "2 M users in 190 countries" figure (DeepMind's, not the Nobel committee's); the IsoDDE 23.3% AF3 figure (primary, not secondary); the viral-complex proteome count (AFDB's own FAQ gives both ~3,500 and ~2,800).
- **Upgraded:** Jumper's move to Anthropic (🟡 → ✅; his own X post of 19 Jun 2026) and the FT team-dissolution report (🟡 → ✅ for the report itself, corroborated by Scientific American and The Decoder). **Downgraded:** the "will not be shut down" / "3 million users" DeepMind statement stays 🟡 because it is known only from Gigazine's paraphrase.
- **Still open:** DeepMind's exact statement to the FT; Google Cloud AF3 pricing/allowlist; HelixFold3/SeedFold/Pearl/ESM3 licence terms (not re-checked beyond the PaddleHelix "NOASSERTION" licence field); Cramer 2026 read from abstract only.
