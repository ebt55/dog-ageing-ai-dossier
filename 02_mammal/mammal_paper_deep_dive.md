# MAMMAL (IBM Research) — high-precision paper deep dive

> Part of the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 subagent · Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/mammal_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## TL;DR

- MAMMAL is a **458 M-parameter T5-style encoder–decoder** that reframes drug-discovery tasks as sequence-to-sequence problems over a *modular tokenizer* covering amino acids, SMILES, ranked gene names and cell/tissue ontology terms, with native continuous-scalar inputs/outputs [1, Methods 4.1–4.4; 5 config.json]. ✅
- The peer-reviewed version the video is about is **Shoshan et al., *npj Drug Discovery* 3, 14 (2026)**, published **4 May 2026** (received 2 Sep 2025, accepted 23 Feb 2026), CC BY 4.0 [1]. The preprint is arXiv:2410.22367 with **three versions**: v1 28 Oct 2024, v2 1 Nov 2024, v3 6 May 2025 [2]. The video was uploaded **13 May 2026**, nine days after the journal version, and its description links the *npj* article [3] — so "a new paper just dropped" refers to the journal publication of a 2024 preprint. ✅
- Headline result: **state of the art on 9 of 11 benchmarks, "competitive" on 2** (the paper's own threshold is >1 % relative improvement) [1, Abstract; Table 1]. ✅ The video's "beat the previous best on all 11" is wrong. ✅
- The **AlphaFold 3 comparison is an exploratory, asymmetric experiment**: a *fine-tuned* MAMMAL binder/non-binder classifier versus *zero-shot* AF3 confidence scores (ipTM/pTM) used as a binding proxy, on 7 antigens with 28–60 test samples each. MAMMAL wins 5, AF3 wins 1 (TBG), tie on 1 (TNFα) [1, Table 2]. ✅ Un-fine-tuned MAMMAL is at chance (AUROC 0.530 on HER2) [1, Suppl. Table S5]. ✅
- The carfilzomib result **did involve a real wet-lab assay** (CellTiter-Glo, 72 h, IC50 by Prism) — but the paper reports **no cell-line names, no n, no IC50 values, no figure and no statistics** for it, and the 90–95 % rank-preservation figure is a *computational* statement about 805 GDSC cell lines, not a wet-lab one [1, Results §2.4, Discussion]. ✅ **Verifier's addition:** the fine-tuning data already contained the same mechanism class — GDSC screens **bortezomib and MG-132**, both proteasome inhibitors — so the "generalisation to an unseen compound" framing rests on *structural* novelty (Tanimoto) while mechanistic novelty was absent. See §6. ⚠️
- Several claims amplified by the video are weaker in the paper: carfilzomib is described as having "limited efficacy in cells of solid tumors", not as believed useless (and 2014 preclinical work already showed sub-nM–36 nM potency in NSCLC lines) [1 ref. 40; 12]; the IDR explanation for AF3's failure is offered as one of three hypotheses [1, Discussion]; and **there is no ablation anywhere in the paper isolating the benefit of multimodality** (the string "ablation" does not occur in the article or supplement). ✅

---

## 1. Bibliographic details

### Journal version (the one the video is about)

| Field | Value |
|---|---|
| Title | *MAMMAL - Molecular Aligned Multi-Modal Architecture and Language for biomedical discovery* [1] |
| Venue | **npj Drug Discovery**, volume 3, article number 14 (2026) |
| DOI | 10.1038/s44386-026-00047-4 |
| Received / Accepted / Published | 2 September 2025 / 23 February 2026 / **4 May 2026** (version of record 4 May 2026) |
| Licence | Open access, **CC BY 4.0** |
| Metrics at retrieval (2026-10-04) | 30k accesses, 10 citations, 11 Altmetric [1] |
| Corresponding author | Yoel Shoshan |
| Competing interests | "The authors declare no competing interests." |
| Funding note | "Partially Supported by IBM-Technion Research Collaboration." |

**Authors (21, in order)** [1]: Yoel Shoshan¹ⁿᵃ¹, Moshiko Raboh¹ⁿᵃ¹, Michal Ozery-Flato¹ⁿᵃ¹, Vadim Ratner¹, Alex Golts¹, Jeffrey K. Weber², Ella Barkan¹, Simona Rabinovici-Cohen¹, Sagi Polaczek¹, Ido Amos¹, Ben Shapira¹, Liam Hazan¹, Matan Ninio¹, Sivan Ravid¹, Michael M. Danziger¹, Yosi Shamay³, Sharon Kurant³, Joseph A. Morrone², Parthasarathy Suryanarayanan², Michal Rosen-Zvi¹ⁿᵃ¹, Efrat Hexter¹ⁿᵃ¹.

**Affiliations** [1]: ¹ IBM Research-Israel, IBM Research, Haifa, Israel · ² IBM TJ Watson Research Center, IBM Research, New York, NY, USA · ³ Faculty of Biomedical Engineering, Technion – IIT, Haifa, Israel. Equal contributors (na1): Shoshan, Raboh, Ozery-Flato, Rosen-Zvi, Hexter.

> Note: the wet-lab work is attributable to the Technion co-authors — "Experiments: M.R., V.R., A.G., E.B., I.A., **Y. Shamay, and S.K.** conducted the experiments" [1, Contributions]. Shamay and Kurant are the only non-IBM authors. ✅

### Preprint versions

| Version | Date (UTC) | Size | Notable differences |
|---|---|---|---|
| v1 | 28 Oct 2024 20:45 | 744 KB | Abstract: 11 tasks, **9 SOTA / 2 comparable**. **The string "AlphaFold" does not occur anywhere in v1** — not just absent from the abstract [verifier-corrected; 2, v1 full text]. ✅ Also **19 authors and 2 affiliations**: Yosi Shamay and Sharon Kurant (Technion) and the Technion affiliation are **absent from v1** and appear only from v3/journal — independent corroboration that the wet-lab work post-dates the preprint [verifier-added]. ✅ |
| v2 | 1 Nov 2024 16:53 | 1,139 KB | Minor (same benchmark table as v1 on inspection). 🟡 |
| v3 | 6 May 2025 07:46 | 15,362 KB | Adds the AF3 comparison: "significantly better classification performance of MAMMAL in **3 out of 4 targets**" (HER2 + CD206, VWF, TBG; "154 sequences: 46 binders and 108 non-binders", split 50/50 for fine-tuning and evaluation) [2, v3 Abstract, §1.10]. ✅ v3 reports HER2 AUROC **0.93** in text and **0.931** in its Table S5. ✅ |
| Journal | 4 May 2026 | — | AF3 experiment expanded to **7 targets / 668 nanobody–antigen pairs**, "five of seven"; Results restructured; benchmark Table 1 numbers **unchanged** from v1 [1, Table 2; 2, v3 Table 1]. ✅ |

All three arXiv versions carry the shorter title *MAMMAL -- Molecular Aligned Multi-Modal Architecture and Language*; "for biomedical discovery" was added only for the journal version [verifier-corrected: the original draft attached this difference to v1 alone]. ✅

So the "beats AlphaFold 3" story grew between v1 (absent) → v3 (3 of 4) → journal (5 of 7). The video's "5 of 7" matches only the journal version, consistent with its publication date. ✅

**Links** [1, Code availability]:
- Paper: https://www.nature.com/articles/s44386-026-00047-4 · Preprint: https://arxiv.org/abs/2410.22367
- Code: https://github.com/BiomedSciAI/biomed-multi-alignment — **Apache-2.0**, created 2024-10-27, last push 2026-09-16, 131 stars / 35 forks at retrieval [4]
- Weights: https://huggingface.co/ibm/biomed.omics.bl.sm.ma-ted-458m — **this path resolves**: the HF API serves it as `ibm-research/biomed.omics.bl.sm.ma-ted-458m` (Apache-2.0; `model.safetensors` 1,832,066,472 B = 1.83 GB; `safetensors.total` = 458,007,202 F32 params) [5]. The model card's own example code calls `Mammal.from_pretrained("ibm/biomed.omics.bl.sm.ma-ted-458m")`, so the paper's printed path is the documented one [verifier-confirmed; resolves earlier open question 9]. ✅
- Fine-tuned checkpoints: `https://huggingface.co/models?other=base_model:finetune:ibm-research/biomed.omics.bl.sm.ma-ted-458m` (web-UI filter; the equivalent API query does not honour the filter, so treat the enumeration below as the authoritative list) 🟡
- Demo Space: https://huggingface.co/spaces/ibm/biomed-multi-alignment — exists, Gradio SDK, last modified 2024-12-09 ✅
- arXiv licence: **CC BY-SA 4.0** ✅ [verifier-confirmed against the licence href `creativecommons.org/licenses/by-sa/4.0/` on both the v1 and v3 listing pages]

---

## 2. Architecture

**Backbone.** "builds upon the transformer architecture introduced by Vaswani et al. and draws inspiration from the **T5 framework**" [1, Methods 4.1]. ✅ The published `config.json` shows it is literally initialised from the **T5 v1.1-base** configuration [5]:

| Hyper-parameter | Value [5] |
|---|---|
| `d_model` / `d_ff` / `d_kv` | 768 / 2048 / 64 |
| `num_layers` (encoder) / `num_decoder_layers` | 12 / 12 |
| `num_heads` | 12 |
| Activation | `gated-gelu` (`feed_forward_proj`), `dense_act_fn: gelu_new` |
| Position encoding | `t5_default_relative`, 32 buckets, max distance 128 |
| `vocab_size` | **100,001** (`max_possible_token_id: 100000`, `max_special_token_id: 500`) |
| `tie_word_embeddings` | false |
| Encoder classification head | MLP `[2048, 1024]`, dropout 0.2 |
| Scalar prediction head | `num_classes: 1`, no hidden layers, dropout 0.0 |
| `support_input_scalars` | true |
| Total parameters | **458,007,202** (F32) — hence "458m" in the model name [5] ✅ |

**Two modes, one shared encoder** [1, Methods 4.1]: *encoder-only* mode (token-prediction head + optional scalar head) for classification/regression; *encoder-decoder* autoregressive mode for generation, where "residual connections inject features from the encoder's final hidden layer into each decoder layer" [verifier-corrected: this sentence is from the **Fig. 1 caption, panel B**, not Methods 4.1]. Encoder weights are shared across modes and "parameter updates conducted through gradient accumulation across all tasks" [1, Methods 4.1]. ✅

**Numeric values.** Scalars are **not** tokenised. Input token IDs go through the learned token embedding; input scalars go through "a learned linear transformation that projects each single scalar element into the model dimension (e.g., 768)"; the two are **added, not concatenated** [1, Suppl. §1]. A per-element scalar prediction head produces scalar outputs. Positions with no scalar carry NaN by convention. A stated limitation: "The support of scalar outputs in the **encoder-decoder** mode is an improvement that we intend to add in future generations" [1, Suppl. §1]. ✅

**Modular tokenizer.** Four sub-tokenizers share one ID space [5, tokenizer/config.yaml] ✅:

| Sub-tokenizer | id | Backing file | Vocab size |
|---|---|---|---|
| `AA` (amino acids + all special tokens) | 0 | `t5_tokenizer_AA_special.json` | 340 tokens |
| `SMILES` | 1 | `bpe_tokenizer_trained_on_chembl_zinc_with_aug_4272372_samples_balanced_1_1.json` — a BPE tokenizer trained on 4,272,372 augmented ChEMBL+ZINC SMILES | — |
| `CELL_ATTRIBUTES` | 2 | `cell_attributes_tokenizer.json` | 1,103 tokens, incl. **580 `[CL:…]` cell-ontology and 209 `[UBERON:…]` tissue terms** |
| `GENE` | 3 (`minimal_token_id: 5000`) | `gene_tokenizer.json` | **95,218 tokens, of which 94,904 are `[GENE_SYMBOL]`-style entries** (2,049 of them contain human Ensembl `ENSG…` IDs; **zero** contain dog `ENSCAFG…` IDs) |

Precision note [verifier-added]: `tokenizer/config.yaml` lists **exactly these four** `tokenizers_info` entries and no others. Methods 4.3 additionally refers to "a designated numeric sub-tokenizer … for handling continuous values", and benchmark prompts use `@TOKENIZER-TYPE=SCALARS_LITERALS`, but scalars are handled by the learned projection layer rather than by a fifth entry in the shipped config — so "four sub-tokenizers" is correct for the released artefact, with the scalar path as a fifth, non-vocabulary modality. ✅

Meta-tokens switch sub-tokenizer mid-prompt and are themselves never tokenised: `@TOKENIZER-TYPE=AA`, `@TOKENIZER-TYPE=SMILES`, and modifiers such as `@TOKENIZER-TYPE=AA@MAX-LEN=1000` [1, Suppl. §2.1]. Implementation lives in FuseMedML: `fuse/data/tokenizers/modular_tokenizer` [1, Suppl. §2.1; 4]. ✅

**Prompt/query syntax.** Entity hierarchy: *Sequence* → *Molecule* (`<MOLECULAR_ENTITY>` + a type token) → *MolecularSystem* (`<COMPLEX_ENTITY>`) → *GlobalSystem*, plus *Attribute* tokens; `<SENTINEL_ID_n>` placeholders mark output slots (one for classification/regression, several for infilling) [1, Suppl. §2]. The real, runnable PPI example from the repo/model card [4, 5] ✅:

```
<@TOKENIZER-TYPE=AA><BINDING_AFFINITY_CLASS><SENTINEL_ID_0>
<MOLECULAR_ENTITY><MOLECULAR_ENTITY_GENERAL_PROTEIN><SEQUENCE_NATURAL_START>{protein_1}<SEQUENCE_NATURAL_END>
<MOLECULAR_ENTITY><MOLECULAR_ENTITY_GENERAL_PROTEIN><SEQUENCE_NATURAL_START>{protein_2}<SEQUENCE_NATURAL_END><EOS>
```

Benchmark prompts (abridged from [1, Suppl. Table S1]) ✅:

| Task | Encoder input (shape) | Decoder label |
|---|---|---|
| Cell type | `@TOKENIZER-TYPE=GENE <MOLECULAR_ENTITY><MOLECULAR_ENTITY_CELL_GENE_EXPRESSION_RANKED> [MALAT1][RPL10]…[ZNF136][ZNF514] <CELL_TYPE_CLASS><SENTINEL_ID_0><EOS>` | `@TOKENIZER-TYPE=CELL_ATTRIBUTES <SENTINEL_ID_0>[CL:0001062]<EOS>` |
| BBBP | `@TOKENIZER-TYPE=SMILES <MOLECULAR_ENTITY><MOLECULAR_ENTITY_SMALL_MOLECULE><BBBP><SENTINEL_ID_0> @TOKENIZER-TYPE=SMILES@MAX-LEN=2100 C(Cl)Cl <EOS>` | `<SENTINEL_ID_0>1<EOS>` |
| ClinTox (two heads) | same shape with `<TOXICITY>` or `<FDA_APPR>` | `<SENTINEL_ID_0>0/1<EOS>` |
| Cancer-drug response | `@TOKENIZER-TYPE=SCALARS_LITERALS <MASK> @TOKENIZER-TYPE=SMILES <MOLECULAR_ENTITY_SMALL_MOLECULE> CN(C)CCOc…[nH]2)cc1 @TOKENIZER-TYPE=GENE <MOLECULAR_ENTITY_CELL_GENE_EXPRESSION_RANKED> [B2M][RPL10]…[ZNF429]<EOS>` | `@TOKENIZER-TYPE=SCALARS_LITERALS 3.966226` |
| Antibody design (infilling) | antigen AA sequence + antibody FR regions with `<SENTINEL_ID_0…3>` in place of CDRs, `<ATTRIBUTE_ORGANISM><ATTRIBUTE_ORGANISM_HUMAN>` | `<SENTINEL_ID_0>ABC<SENTINEL_ID_1>DDDDD…<EOS>` |
| DTI | protein AA + drug SMILES, `<MASK>` scalar slot | `@TOKENIZER-TYPE=SCALARS_LITERALS {standardized pKd}` |

Notable special tokens present in the shipped vocabulary but *not* exercised by the 11 benchmarks [5]: `<STRUCTURE>`, `<DISTANCE>`, `<DIFFUSION>`, `<TIMESTEP>`, `<AUTOENCODER_*>`, `<SELFIES_SEQUENCE>`, `<EPITOPE_PARATOPE_PREDICTION>`, `<DISORDER>`, `<DISEASE>`, `<SOLUBILITY>`, `<FLUORESCENCE>`, `<ABSORPTION>/<DISTRIBUTION>/<METABOLISM>/<EXCRETION>`. ✅ **There is no DNA/nucleotide sub-tokenizer and no DNA-sequence entity token.** ✅ (Important for fact-checking the video.)

---

## 3. Pretraining data and tasks

Pretraining ran on **"two billion samples sourced from six datasets … covering three distinct domains across seven tasks"** [1, Methods 4.4]. Table 3 verbatim [1]:

| Task name | Domain | Entity type | Task type | Dataset | # Samples |
|---|---|---|---|---|---|
| Protein LM | Biologic | General protein | Spans masking LM | **UniRef90** | 180 M |
| Antibody LM | Biologic | Antibody | Spans masking LM | **OAS** | 650 M |
| Small Molecule LM | Small molecules | Small molecule | Spans masking LM | **ZINC + PubChem** | 200 M |
| Cell Genes LM | Single-cell transcriptomics | Cell genes | Spans masking LM | **CELLxGENE** | 30 M |
| Protein–Protein Interaction | Biologic | General protein | Classification | **STRING** | 780 M |
| Protein–Protein Interaction Gen. | Biologic | General protein | Generation | **STRING** | 390 M |
| Antibody Denoise | Biologic | Antibody | Denoise sequence | **OAS** | 650 M |

**On the "2 billion" figure.** The seven rows sum to **2,880 M**, but OAS (650 M) is listed twice and the STRING generation task (390 M positives) is a subset of the STRING classification set (390 M positives + 390 M pseudo-negatives = 780 M; the supplement calls the latter "a second dataset of 780 million samples"). Counting each *dataset* once gives 180 + 650 + 200 + 30 + 780 = **1,840 M ≈ 2 billion**. So "2 billion samples" is best read as ~1.84 B unique samples, consumed across 2.88 B task instances — not 2 B distinct biological entities. ✅ [verifier-corrected confidence: this was flagged as the author's unsupported inference, but the paper's own **Fig. 1 caption, panel A** states "a multi-align model pretrained on **six datasets**, each containing tens to hundreds of millions of data points … with a **combined sample size of 2 billion**", i.e. the paper itself counts per-dataset, not per-task. The reconciliation is therefore the paper's own arithmetic, and 2,880 M is the task-instance total.]

**Per-dataset preprocessing** [1, Suppl. §3.3] ✅:
- **UniRef90** — UniProt Reference Clusters at ≥90 % identity / 80 % overlap with the seed sequence. No species filter stated.
- **OAS** — unpaired antibody variable regions; filtered to complete variable domains with standard amino acids → **~650 M sequences**; "Each sequence is annotated with its chain type (heavy or light) **and species information**."
- **STRING** — 390 M positive pairs with confidence score **> 500**, plus 390 M pseudo-negatives "by **randomly matching proteins from the same species**" → 780 M.
- **CELLxGENE** — "After filtering for **human** samples labeled as 'cell' in the 'suspension type' field, we curated a dataset of 30 million samples." ✅ **Human-only.**
- **PubChem** — 80 M "drug-like" molecules, de-duplicated, following **Lipinski's rule of five**.
- **ZINC22** — 120 M molecules sampled, restricted to **< 30 heavy atoms**. (80 + 120 = 200 M ✅)

**Gene-expression representation (Geneformer-style, with differences)** [1, Methods 4.2 and Suppl. §3.3] ✅:
> "created as ranked lists of gene names, similar to **Geneformer** […] Instead of normalizing by median expression and ranking the now unique values of expression count, we **log-normalized and binned** the samples, followed by **alphabetic sorting** to make the task well-defined. The binning removes the ability of noisy reads to significantly affect the pretraining and alphabetic sorting ensures that for every masked token there is a unique correct answer."

Entity representations [1, Methods 4.2]: small molecules = SMILES (paracetamol → `CC(=O)NC1=CC=C(O)C=C1`); gene expression = ordered gene-name list, descending log-normalised binned value, alphabetical tie-break; proteins = concatenated amino-acid chains, **"only sequence data, without structural information"**; antibodies = same, each chain prefixed with a heavy/light type token. ✅

**Pretraining objectives** [1, Suppl. §3.5] ✅: four span-denoising LM tasks (T5-style, **mean noise span 5, noise density 0.15**); an antibody-denoising task (corruption level sampled t ∈ [1, 500], token corruption probability ∝ t); and the two STRING PPI tasks (classification on balanced positives/negatives, generation on positives only — "generate an interacting protein given an input protein"). Entity-type special tokens were added per entity (`<MOLECULAR_ENTITY_TYPE_ANTIBODY_HEAVY_CHAIN>`); **"When sequences were available from different species, an additional special token was also introduced (e.g., `ATTRIBUTE ORGANISM HUMAN`)"**. ✅ The shipped vocabulary contains exactly six such organism tokens: **HUMAN, MOUSE, RAT, RABBIT, MONKEY, CAMEL** [5] ✅ — see `mammal_for_dogs.md`.

**Compute** [1, Suppl. §3.1–3.2] ✅: OpenShift cluster, **"trained for three months over two nodes with 16 A100-80G GPUs"** (ambiguous whether 16 total or 16 per node — quoted as written); FuseMedML + PyTorch with **FSDP**; AdamW (β₁ 0.9, β₂ 0.999), weight decay 0.01, gradient-clip norm 1.0, 2 K warm-up steps, cosine decay to 10 % of peak LR; per-task max sequence length and batch size; long sequences wrapped in start/end tokens and randomly cropped rather than truncated at the end.

---

## 4. All 11 benchmarks (Table 1 verbatim)

Evaluation rules [1, Results §2.1]: benchmarks chosen for predefined splits; fine-tune → select on validation → report on test; standard errors from **3 random seeds** unless cross-validation was prescribed; DTI uses NRMSE (RMSE ÷ SD of test labels); **"We consider MAMMAL to outperform existing state of the art when the relative improvement, computed as |SOTA − MAMMAL|/SOTA, exceeds 1 %."** ✅

| # | Benchmark | Domain | Type | Metric | SOTA (ref) | MAMMAL | Imp. | Beat SOTA? |
|---|---|---|---|---|---|---|---|---|
| 1 | Cell type (Zheng68k) | GE | cls | ↑ F1 | **0.710** — CIForm, Xu et al. 2023 [ref 27] | **0.763 ± 0.012** | 7.5 % | ✅ yes |
| 2 | BBBP (MoleculeNet) | SM | cls | ↑ AUROC | **0.937** — MoLFormer, Ross et al. 2022 [ref 32] | **0.957 ± 0.006** | 2.2 % | ✅ yes |
| 3 | ClinTox (MoleculeNet) | SM | cls | ↑ AUROC | **0.948** — MoLFormer [ref 32] | **0.986 ± 0.007** | 4.0 % | ✅ yes |
| 4 | Cancer-Drug Response 1 (GDSC1/TDC) | GE+SM | reg | ↑ Pearson | **0.887** — Tx-LLM, Chaves et al. 2024 [ref 92] | **0.917 ± 0.001** | 3.4 % | ✅ yes |
| 5 | Cancer-Drug Response 2 (GDSC2/TDC) | GE+SM | reg | ↑ Pearson | **0.900** — Tx-LLM [ref 92] | **0.931 ± 0.002** | 3.4 % | ✅ yes |
| 6 | Cancer-Drug Response 3 (DeepCDR split) | GE+SM | reg | ↑ Pearson | **0.923 [0.917–0.929]** — DeepCDR, Liu et al. 2020 [ref 36] | **0.928 ± 0.000** | 0.5 % | ⚠️ **no** — below the 1 % rule ("comparable") |
| 7 | Ab Infilling (SAbDab) | Protein | gen | ↑ CDRH3-AAR | **0.375** — dyMEAN, Kong et al. 2023 [ref 47] | **0.446 ± 0.002** | 19.0 % | ✅ yes |
| 8 | AbAg Bind (HER2/trastuzumab DMS) | Protein | cls | ↑ AUROC | **0.924 [0.923–0.925]** — Jing et al. 2024 [ref 63] | **0.928 ± 0.002** | 0.4 % | ⚠️ **no** — "comparable" |
| 9 | TCR Bind (Weber/TITAN) | Protein | cls | ↑ AUROC | **0.862 [0.85–0.868]** — Weber et al. 2021 [ref 54] | **0.879 ± 0.003** | 2.0 % | ✅ yes |
| 10 | PPI ΔΔG (SKEMPI S1131) | Protein | reg | ↑ Pearson | **0.663** — AttABseq, Jin et al. 2024 [ref 104] | **0.852 ± 0.041** | 28.5 % | ✅ yes vs **sequence-only**; **structure-based best is 0.866, 1.6 % above MAMMAL** [1, §2.7] |
| 11 | DTI (PEER / BindingDB) | Prot.+SM | reg | ↓ NRMSE | **0.942 ± 0.028** — Xu et al. 2022 [ref 60] | **0.906 ± 0.011** | 3.8 % | ✅ yes |

So: **9 wins, 2 "comparable" (#6 Cancer-Drug Response 3 and #8 AbAg Bind)**, exactly matching the abstract. ✅ Table 1 is numerically **identical** in arXiv v1, v3 and the journal version [1; 2]. ✅

### Per-benchmark details worth keeping

- **Cell type** [1, §2.2]: Zheng68k (Zheng et al. 2017), human PBMCs, **68,579 cells, 11 cell types**, 32,738 genes → **20,387** after removing non-expressed genes. Normalisation → log transform → binning; input is the ranked expressed-gene-name list; label is a Cell Ontology ID (`CL:NNNNNN`). **5-fold CV**, stratified by cell type. Suppl. Table S2: scBERT acc 0.759 / F1 0.691; CIForm acc 0.820 / F1 0.710; **MAMMAL acc 0.856 ± 0.004, F1 0.763 ± 0.012, precision 0.774 ± 0.016, recall 0.761 ± 0.011**. ✅ The 7.5 % is *relative* on F1 (absolute +5.3 points).
- **BBBP / ClinTox** [1, §2.3]: MoleculeNet; splits taken from the MoLFormer repo. MoLFormer was "trained on **1.1 billion SMILES** sequences" ✅ [also 11]. ClinTox score = average of two sub-tasks (clinical-trial toxicity failure, FDA approval).
- **Ab Infilling** [1, §2.6]: SAbDab, preprocessed exactly as dyMEAN (samples with missing CDRs filtered out; splits clustered by CDRH3 similarity). Only **sequence** inputs: antigen + antibody framework regions. Suppl. Table S4 ✅:

  | Model | CDRH1 | CDRH2 | **CDRH3** | CDRL1 | CDRL2 | CDRL3 |
  |---|---|---|---|---|---|---|
  | dyMEAN [ref 47] | 0.757 | 0.685 | **0.375** | 0.755 | 0.831 | 0.521 |
  | MAMMAL | 0.832 ± 0.003 | 0.742 ± 0.012 | **0.446 ± 0.002** | 0.780 ± 0.017 | 0.844 ± 0.012 | **0.724 ± 0.010** |

  Two caveats. (a) The 0.375 dyMEAN baseline is dyMEAN's **"simultaneous design of 6 CDRs"** number (Table 5: L1 75.55 / H1 75.72 / L2 83.10 / H2 68.48 / L3 52.12 / **H3 37.51 %** — all six match MAMMAL's Table S4 dyMEAN row exactly), not its headline single-CDR-H3 RAbD result of **43.65 %** (Table 1) [13, Tables 1 and 5] — the comparison is apples-to-apples for a 6-CDR infilling setting, but a reader who looks up "dyMEAN CDR-H3 AAR" will find 43.65 %. ✅ [verifier-confirmed against the dyMEAN preprint] (b) **CDRL3 improved more in relative terms (+39.0 %) than CDRH3 (+18.9 %)**; the video's claim that CDRH3 is where MAMMAL "completely blew away the competition" is not what Table S4 shows. ✅ dyMEAN's own authors also warn that a meaningless unigram pattern (`ARDG***DY`) scores AAR = 39.61 % on their test set, i.e. AAR has a high trivial floor [13, **§7 "Limitations" → "Data Diversity and Evaluation Metrics"**; verifier-corrected from "§6"]. ✅
- **TCR Bind** [1, §2.5]: Weber et al. benchmark, **47,182 TCR β–epitope pairs, 192 epitopes, 23,139 unique TCR β sequences**, 50 % negatives by random pairing; **10-fold CV** with pre-defined folds; fine-tuned with three concurrent tasks (β-chain mask infilling + two binding classifications), only the β-chain-vs-epitope result reported. "statistically significant improvement of 2 % over the SOTA, as our result falls outside the SOTA's confidence interval."
- **PPI ΔΔG** [1, §2.7]: SKEMPI **S1131** single-point mutations, 10-fold CV, sequence-only input (wild-type + mutant complexes), regression via the scalar head.
- **DTI** [1, §2.8]: PEER benchmark over BindingDB with four protein classes held out (estrogen receptor, GPCRs, ion channels, receptor tyrosine kinases); LR 4e-4, no dropout, no weight decay; pKd standardised then inverted for reporting.
- **AbAg Bind** [1, §2.9]: Mason et al. 2021 HER2 DMS set — **8,935 binding and 25,114 non-binding trastuzumab CDR-H3 mutants** (≤10 mutations), de-duplicated, conflicting labels removed; 70/15/15 split with the train portion further split into 5 folds. Input = antigen sequence + whole heavy-chain variable region. "slightly surpassing the SOTA, which incorporated structural data, unlike our model."
- **vs. a text LLM** [1, Suppl. §6, Table S8]: BioMedLM (ref. 76 = Bolton et al., arXiv:2403.18421) fine-tuned on five benchmarks — BBBP 0.957 vs 0.957 (0.0 %), ClinTox 0.982 vs 0.986 (0.41 %), cell-type F1 0.509 vs 0.758 (**53.44 %** as printed), Ab-Ag binding AUROC 0.567 vs 0.928 (63.67 %), DTI NRMSE 1.13 vs 0.924 (18.23 %). ✅ (all five rows verified verbatim). Two caveats [verifier-added]: (i) BioMedLM's free-text inputs were **capped at 1,024 tokens** and cell-type training was **capped at two days per fold**, so the comparison is compute- and context-limited, not a clean architecture test; (ii) the cell-type "53.44 %" **does not follow from its own row** — (0.758 − 0.509)/0.509 = **+48.9 %**, whereas the other four rows reproduce exactly under (MAMMAL − baseline)/baseline. Either the printed BioMedLM F1 or the printed improvement is wrong; a new internal inconsistency in the paper. ⚠️ Note also that the MAMMAL column in Table S8 (0.758 / 0.928 / 0.924) differs slightly from Table 1 (0.763 / 0.928 / 0.906) — presumably different runs. 🟡

---

## 5. The AlphaFold 3 comparison — exactly what was done

**Task.** Binary **binder vs non-binder classification** for antibody/nanobody–antigen pairs. Not structure prediction, not docking accuracy. [1, §2.10] ✅

**How AF3 was used.** AF3 is "not explicitly designed as a binary protein–protein interaction (PPI) classifier"; binding likelihood was inferred from **structure-derived confidence scores — pTM and interface pTM (ipTM)** — computed on predicted complexes, citing Bennett et al. 2025 (RFdiffusion) and Yin & Pierce 2024 as evidence that such scores correlate with binding [1, §2.10]. The authors label it "**an exploratory comparison**" and explicitly state "the comparison is intended to assess relative discriminative power for binding prediction rather than to equate the underlying modeling approaches." ✅ In the Discussion AF3 is described as "**applied in a zero-shot setting**" [1]. ✅

**Asymmetry to keep in mind:** MAMMAL was **fine-tuned on binders and non-binders of these very targets** (a single model trained across all targets, then evaluated per target), while AF3 saw no training signal. Un-fine-tuned MAMMAL is at chance: AUROC **0.530** on HER2 [1, Suppl. Table S5] and 0.428 / 0.478 / 0.406 / 0.644 / 0.663 / 0.506 on albumin / CD206 / EGFR / TBG / TNF / VWF [1, Suppl. Table S6]. ✅ The discriminative ability therefore comes from supervised fine-tuning, not from the foundation model's pretraining.

**Datasets.**
- *HER2 ECD* (benchmark #8 above): test set **downsampled to 60 examples (30 binders / 30 non-binders)** "due to the computational demands and limited availability of AF3". ✅
- *Six nanobody targets*: binders from **SAbDab-nano, patents, and proprietary datasets**; non-binders from phage-display screens confirmed non-binding plus nanobodies against unrelated antigens. **668 pairs total (131 binders / 537 non-binders)** → **475 for fine-tuning (64 binders / 411 non-binders)** and **193 held out (67 binders / 126 non-binders)**. ✅ (Internally consistent: 475 + 193 = 668; 64 + 67 = 131; 411 + 126 = 537; per-target test n sums to 193.)
- ⚠️ "patents and proprietary datasets" conflicts with the Data-availability statement "All datasets used in this study are publicly available" — the nanobody binder/non-binder set is **not** released. ✅ This is the least reproducible experiment in the paper.

**Table 2 verbatim** [1] ✅ (AF3 column = ipTM-based):

| Target | length (AA) | n | pos | MAMMAL AUROC | AF3 AUROC | ΔAUROC | P-value |
|---|---|---|---|---|---|---|---|
| HER2 ECD | 630 | 60 | 30 | **0.93** | 0.45 | +0.42 | 1.5 × 10⁻⁶ |
| Albumin | 609 | 28 | 11 | **0.91** | 0.59 | +0.32 | 7.4 × 10⁻³ |
| CD206 | 1,456 | 37 | 14 | **1.00** | 0.59 | +0.41 | 1.1 × 10⁻⁵ |
| EGFR | 1,210 | 28 | 11 | **0.94** | 0.49 | +0.45 | 2.2 × 10⁻⁵ |
| TBG | 384 | 32 | 5 | 0.63 | **1.00** | −0.37 | 1.0 × 10⁻⁴ |
| TNFα | 233 | 34 | 13 | 0.86 | **0.87** | −0.01 | NS |
| VWF | 2,813 | 34 | 13 | **0.83** | 0.32 | +0.51 | 3.9 × 10⁻⁶ |

P-values by **DeLong test** for correlated ROC curves; NS = p > 0.1. The seven targets are therefore **HER2 (antibodies) + albumin, CD206, EGFR, TBG, TNFα, VWF (nanobodies/VHHs)** — this is the exact answer to "which 7 targets". ✅ Sequence lengths match UniProt full-length entries exactly for EGFR (P00533, 1,210), CD206/MRC1 (P22897, 1,456), VWF (P04275, 2,813), albumin (P02768, 609) and TNF (P01375, 233) ✅; HER2 full length is 1,255 and its annotated extracellular topological domain is residues **23–652 = exactly 630 aa**, so 630 is the ECD ✅ [6, verifier-confirmed]. **Correction:** TBG/SERPINA7 (P05543) is a 415-aa precursor with signal peptide 1–20 and mature chain **21–415 = 395 aa**, so the paper's **384 aa matches neither the precursor nor the mature chain**; which construct was used is unexplained ❓ [verifier-corrected — the draft asserted 384 = the mature chain].

Rounding note [verifier-added]: Table 2's CD206 MAMMAL AUROC of **1.00 is a rounding of 0.997** (Suppl. Table S6), not a perfect score. TBG's AF3 AUROC of 1.00 *is* exactly 1.0 in Suppl. Table S6. The other Table 2 MAMMAL values round from Suppl. Table S6's 0.914 / 0.941 / 0.63 / 0.857 / 0.832. ✅

**Caveats the paper states or implies**
1. Exploratory; confidence scores are "a reference proxy for binding likelihood", not a classifier output. ✅
2. Tiny test sets (n = 28–60; **TBG has only 5 positives**, so its AUROC = 1.00 rests on 5 × 27 = 135 pairwise comparisons). ✅
3. AF3 zero-shot vs MAMMAL fine-tuned on the same targets. ✅
4. Multiple AF3 configurations were tried and **all were near chance on HER2** [1, Suppl. Table S5]: heavy-chain-only ipTM 0.448, heavy-only pTM 0.496, heavy+light ipTM 0.504, heavy+light pTM 0.497. A CD206 "control" gave 0.455 (ipTM) / 0.66 (pTM). ✅
5. **The paper does not report how many AF3 seeds/diffusion samples were used.** The AF3 paper states that "for AF3, top-ranked predictions **keep improving with more model seeds, even at as many as 1,000**" and names antibody–antigen complexes as the class where the effect is strongest; in AF3's own benchmark table every other category was scored from five model seeds while **protein–antibody scores were ranked across 1,000 model seeds** [7, Fig. 5a and Fig. 1c caption; verifier-confirmed verbatim] — so a low-seed AF3 run is a known weak configuration for exactly this class of target. ❓ (unverifiable from the MAMMAL paper; a genuine methodological gap)
6. **Internal inconsistency**: the Results text says the HER2 MAMMAL model achieved "an **AUROC of 0.88**" and Suppl. Table S5 lists MAMMAL Fine Tuned = **0.881**, while **Table 2 lists 0.93** for HER2 ECD [1]. arXiv v3 had 0.93 in text and 0.931 in Table S5 [2, v3]. So the journal revision changed two of the three places. ✅ (flagged for the verifier; MAMMAL still beats AF3's 0.45 either way)

**Why AF3 did poorly — the paper's three hypotheses** [1, Discussion] ✅:
> "These limitations may reflect AF3's **bias toward true-positive PDB complexes**, its **lack of explicit negative supervision**, and its **reliance on a single static conformation**. As a result, AF3 struggles with proteins containing heterogeneous or intrinsically disordered regions (IDRs), **which comprise 30–40 % of the human proteome** and are known to challenge structure-based models [ref 72], including IDR-rich therapeutic targets such as **EGFR [ref 73] and HER2 [ref 74]**."

Checks on that chain of reasoning:
- ref 72 = Gopalan & Narayanan, arXiv:2510.15939, whose abstract states IDPs "comprise 30 to 40 percent of the human proteome" — **a non-peer-reviewed preprint** is the sole support for the 30–40 % figure as used here 🟡 [8].
- ref 74 = Pinet et al., *Biophys. J.* 2021 — characterises the **C-terminal cytoplasmic tail** of ErbB2/HER2 as disordered [9] ✅. But the AF3 experiment used the **HER2 extracellular domain**, UniProt topological domain 23–652 (= the 630 AA in Table 2), whereas the disordered tail is the cytoplasmic domain 676–1255 — i.e. the two do not overlap at all [6, verifier-confirmed residue ranges]. So the IDR explanation does **not** apply to the HER2 row of Table 2. ✅ **This is the single biggest logical gap in the AF3 narrative.**
- ref 73 = Thomas et al., *Brief. Bioinform.* 2025, on IDRs/disorder hotspots across the human kinome [10] ✅ — supports EGFR being IDR-containing (its 1,210-AA full-length input does include the disordered C-tail).
- AF3's own paper independently documents (i) hallucinated order in disordered regions, mitigated by AF2 cross-distillation, (ii) static single-conformation output, and (iii) antibody–antigen complexes as the class most needing many seeds [7] ✅ — so hypotheses (1)–(3) are consistent with Google DeepMind's own stated limitations.

---

## 6. Cancer drug-response experiment (the carfilzomib story)

**Benchmark datasets** [1, §2.4, Suppl. Table S3] ✅:

| Name in paper | Source | # cell lines | # drugs | # cell–drug pairs | Split |
|---|---|---|---|---|---|
| Cancer-Drug Response 1 | **GDSC1** via Therapeutics Data Commons | **958** | 208 | 177 K | TDC random split |
| Cancer-Drug Response 2 | **GDSC2** via TDC | **805** | 137 | 92 K | TDC random split |
| Cancer-Drug Response 3 | subset from DeepCDR [ref 36] | **561** | 223 | 107 K | DeepCDR methodology; 5 % test, stratified by TCGA pathway |

All nine cells of Suppl. Table S3 are now **verified verbatim** — 958/208/177K, 805/137/92K, 561/223/107K — so the reconstructed row mapping was correct [verifier-confirmed; the draft's 🟡 caveat is withdrawn]. ✅ Fine-tuning used **only gene-expression ranks + drug SMILES** (no mutation/CNV/methylation), regression mode on continuous IC50 [1, §2.4] ✅.

**The four held-out drugs** — the ASR names in the video decode as [1, §2.4] ✅:
**Carfilzomib, Nintedanib, Infigratinib, Vemurafenib** (so "infigretinib" = infigratinib; "vimura fenib"/"venmerafenib" = vemurafenib).

**Tanimoto analysis** [1, §2.4] ✅ verbatim:
> "Tanimoto similarity analysis confirmed that **three of these drugs (Carfilzomib, Nintedanib, and Infigratinib) have no structurally similar compounds in the training set (Tanimoto coefficient < 0.7)**, while **Vemurafenib shares moderate similarity (0.82) with PLX-4720**, a BRAF inhibitor present in GDSC."

PLX-4720 is indeed in the GDSC compound list (DRUG_IDs 1036 and 1371, target BRAF) [14] ✅. The fingerprint type and radius used for Tanimoto are **not stated** ❓ — a materially missing method detail, since 0.7 means different things for ECFP4 vs MACCS.

**Two new findings from re-parsing the GDSC release-8.5 compound catalogue** [14; verifier-added]:

1. **The proteasome-inhibitor mechanism class was already in the training distribution.** GDSC 8.5 screens **bortezomib** (DRUG_IDs 104 and 1191, target "Proteasome") and **MG-132** (9 and 1862, "Proteasome, CAPN1") — four entries in all. Bortezomib and MG-132 are among the most broadly cytotoxic agents in cell-line panels. MAMMAL's prediction that carfilzomib is the most potent of four held-out drugs across solid-tumour lines is therefore substantially explainable by **target-class transfer from compounds whose GDSC IC50 profiles it fine-tuned on**, not only by generalisation from unfamiliar structure. The Tanimoto analysis tests *structural* novelty and is silent on *mechanistic* novelty — carfilzomib (peptide epoxyketone) and bortezomib (boronic dipeptide) are structurally unrelated yet hit the same target, so a low Tanimoto is exactly what one expects for two proteasome inhibitors. **This is the strongest single caveat on the carfilzomib result and neither the paper nor the video raises it.** ⚠️
2. **Nintedanib *is* in the GDSC 8.5 catalogue — under its development code `BIBF-1120` (DRUG_ID 380; targets VEGFR, PDGFR, FGFR).** Carfilzomib, infigratinib and vemurafenib are absent under every synonym checked (incl. PR-171/Kyprolis, BGJ398/NVP-BGJ398, PLX-4032/RG7204/Zelboraf). The paper's "four drugs **not present in the GDSC training data**" must therefore be read as "not present in the TDC GDSC1/GDSC2 and DeepCDR subsets actually used" — which is plausible (TDC's subsets cover 208 and 137 drugs out of GDSC's 621 catalogued compounds) and is implied by the reported Tanimoto < 0.7, since self-similarity would be 1.0. But the paper's phrasing is looser than the fact. 🟡

Important scope limit: "no structurally similar compounds **in the training set**" most plausibly refers to the **GDSC fine-tuning set** rather than the 200 M-molecule SMILES pretraining corpus, given the preceding sentence's "not present in the GDSC training data" — but the paper does not say so explicitly 🟡 [verifier-downgraded from ✅: this is a reading, not a statement]. Whether these four drugs appeared in pretraining is unstated and unverifiable from the paper ❓. Suggestive datum: the PubChem portion was filtered by Lipinski's rule of five, and carfilzomib (MW 719.9), nintedanib (539.6) and infigratinib (560.5) all exceed the 500 Da criterion, while vemurafenib (489.9) does not [15–18; verifier-confirmed against PubChem] — which makes exclusion of the first three plausible but unproven 🟡. The ZINC22 portion was filtered to < 30 heavy atoms, and all four exceed it (carfilzomib 52, nintedanib 40, infigratinib 38, vemurafenib 33 heavy atoms) ✅ — note, however, that **PLX-4720 (413.8 Da, 27 heavy atoms) and bortezomib (384.2 Da, 28) pass both filters**, so the close structural analogue of vemurafenib and the mechanistic analogue of carfilzomib were both eligible for the pretraining corpus [verifier-added]. 🟡

**Wet-lab validation — what is and is not reported** [1, §2.4] ✅ verbatim:
> "We performed **experimental validation using the same assay protocol employed in GDSC: cell viability was measured using CellTiter-Glo following 72-hour drug incubation, and IC50 values were determined with Prism (GraphPad)**. The experimental measurements revealed a consistent potency ranking **across all tested cell lines**: Carfilzomib (most potent), followed by Nintedanib, Infigratinib, and Vemurafenib (least potent). MAMMAL predictions reproduced this exact ranking for the tested cell lines. When extended to **all 805 cell lines in GDSC**, the model preserved this relative ordering in **approximately 90–95 % of cases**, suggesting that the predicted potency differences are largely cell line–independent."

So: **yes, a new wet-lab experiment was run** (answering the orchestrator's crucial question) — but the paper gives **no cell-line identities, no number of cell lines, no IC50 values, no dose–response figure, no replicate count and no statistics** for it, and no supplementary table contains them. ✅ The Discussion repeats only: "**Wet-lab validation using the same CellTiter-Glo assay protocol as GDSC confirmed the predicted ordering.**" The **90–95 %** figure is explicitly a *model-prediction* statement over the 805 GDSC cell lines, not a wet-lab measurement. ✅ The experiment as described tests a **between-drug ranking** (4 drugs, consistent across lines), which is a much weaker claim than per-cell-line precision medicine, and the authors themselves note the ordering is "largely cell line–independent" — i.e. a single global potency ordering.

**How the paper describes carfilzomib's status** [1, §2.4] ✅ verbatim:
> "Notably, Carfilzomib is a proteasome inhibitor **approved exclusively for hematological malignancies (multiple myeloma), with limited efficacy in cells of solid tumors** [ref 40]. The model's prediction of Carfilzomib as the most potent agent across diverse solid tumor cell lines aligns with our experimental observations and **suggests potential broader applicability that warrants further investigation**."

Reference 40 is Kortuem & Stewart, "Carfilzomib", *Blood* 121:893–897 (2013) — a general drug review, **not** a study showing failure in solid tumours ✅ [verifier-confirmed]. And the prior literature does **not** say carfilzomib is inactive on solid-tumour cells *in vitro*: Baker et al. 2014 report "marked anti-proliferative activity in A549, H1993, H520, H460, and H1299 non-small cell lung cancer cell lines, with IC50 values after 96 hour exposure from **< 1.0 nM to 36 nM**", plus SCLC IC50s from "< 1 nM to 203 nM" and a survival benefit in an SHP77 xenograft [12] ✅ (verified verbatim). That paper's own background states "**Phase 1B studies indicated clinical activity signals in solid tumors, including small cell lung cancer**" ✅ [verifier-added]. The recognised obstacles to solid-tumour use are **poor aqueous solubility and in-vivo instability**, i.e. pharmacokinetics/delivery, not target-cell insensitivity [19] ✅. Carfilzomib was also taken into solid-tumour clinical study (PX-171-007 phase Ib/II) [15] 🟡 (secondary source only).

**Balanced reading** [verifier-added, replacing a one-sided closing line]: there *is* a real clinical limitation behind the paper's phrase — carfilzomib has been approved only for multiple myeloma since July 2012, and proteasome inhibitors as a class have never converted their in-vitro potency into a solid-tumour indication. So a clinician saying "carfilzomib doesn't work in solid tumours" would be making a defensible statement **about clinical outcomes**. What is not supportable is (i) the paper's narrower claim of "limited efficacy **in cells** of solid tumors", which the 2014 cell-line data contradict, and (ii) the video's upgrade of that to a categorical, decades-long expert consensus that the drug is useless — see `video_claims_factcheck.md` #43–#44, #49, where the verdicts were re-worded accordingly.

**Related collaborations** [1, Discussion] ✅: a published joint study on predicting antibody activity against influenza A hemagglutinin (Barkan et al., *Comput. Struct. Biotechnol. J.* 27:1286–1295, 2025 [ref 71]); "Additional collaborative studies involving **prospective** wet-lab validation of MAMMAL-guided predictions are currently in progress."

---

## 7. Limitations stated by the authors, and gaps I identified

**Stated by the authors**
1. "our evaluation is limited to models that **publicly report results on these tasks**, and claims of state-of-the-art performance should therefore be interpreted within this scope" [1, Discussion]. ✅
2. Combining the sequence-to-sequence abstraction "with the expressive power of specialized models, particularly **diffusion-based architectures** that excel at high-fidelity structural generation" is "a key open challenge" [1, Discussion]; arXiv v3 states "we plan to expand MAMMAL to **natively support 3D input and output**" [2, v3 Discussion]. ✅
3. Scalar **outputs** are not yet supported in encoder-decoder mode [1, Suppl. §1]. ✅
4. Free-text input is only a "natural extension", not implemented [1, Methods 4.1]. ✅
5. PPI ΔΔG remains 1.6 % below the best **structure-based** method [1, §2.7]. ✅

**Gaps / critiques I identified (not stated by the authors)**
- **No ablation study.** The word "ablation" appears **zero** times in the article and supplement [verifier-confirmed: 0 matches for `ablat` across the full article text and all 17 supplement pages]. There is no experiment holding architecture fixed while removing a pretraining modality, so the paper's (and the video's) claim that multimodality *causes* the chemistry gains is **unsupported**; the BioMedLM comparison is a different-model comparison at a 1,024-token context cap, not an ablation. ✅
- **The carfilzomib result is confounded by mechanism-class leakage**, not by structural similarity: bortezomib and MG-132 are in GDSC and were available to fine-tuning (see §6). ⚠️ [verifier-added]
- **Table S8's cell-type improvement (53.44 %) does not follow from its own row** (0.509 → 0.758 is +48.9 %). ⚠️ [verifier-added]
- **Table 2's TBG sequence length (384 aa) matches neither the SERPINA7 precursor (415) nor its mature chain (395)**; the construct is unexplained. ❓ [verifier-added]
- **No comparison against the obvious same-architecture baseline** (e.g., T5-base pretrained on SMILES only), and no comparison against ESM-2/ESM-3 or scGPT on the protein and transcriptomic tasks respectively. ✅
- The HER2 AUROC discrepancy (0.88 in text / 0.881 in Table S5 / 0.93 in Table 2) is unresolved. ✅
- The nanobody binder set includes patent and proprietary data, so the AF3 comparison is **not reproducible** despite the blanket public-data statement. ✅
- AF3 seed count / software version / whether the AlphaFold Server or open weights were used is unreported ❓.
- Tanimoto fingerprint definition unreported ❓.
- Wet-lab experiment under-reported (see §6) ✅.
- `Cancer-Drug Response` fine-tuning used gene expression only; the SOTA it beats (Tx-LLM) and DeepCDR use additional omics — favourable for MAMMAL's story but it means the comparison is across different input sets 🟡.

**Independent commentary found.** Coverage is thin. The only substantive third-party piece I could retrieve is a trade article by Ron Patel, Startup Fortune, 15 May 2026, which is directionally cautious and makes the same two corrections I do: "In antibody-antigen binding tests, fine-tuned MAMMAL prediction scores outperformed AlphaFold 3 confidence-score proxies on five of seven antigen targets. **That does not mean MAMMAL is broadly better than AlphaFold 3**, which is built around structural biology and has its own strengths"; and "**Benchmarks are useful, but they are not clinical validation.**" [20] ✅ **both quotes verified verbatim against the live page** [verifier-confirmed; upgraded from 🟡]. I found no peer-reviewed critique, no published replication, and no retraction/correction notice. The article reports 10 citations as of 2026-10-04 [1]; neither the author nor the verifier enumerated them ❓.

---

## 8. How to actually use it

**Install** [4] ✅:
```
conda create -n mammal_env python=3.10 -y && conda activate mammal_env
conda install pytorch pytorch-cuda=12.1 -c pytorch -c nvidia
pip install "biomed-multi-alignment[examples]"        # or [examples,vllm]
```
PyPI package `biomed-multi-alignment`, latest **0.2.6** (uploaded 2026-09-16), requires **Python ≥3.10, <3.13**, Apache-2.0; dependencies include `fuse-med-ml==0.4.1`, `transformers>=5.0,<6.0`, `hydra-core`, `peft>=0.19`; extras: `examples` (PyTDC, anndata, click), `vllm` (vLLM ≥0.29 embedding plugin) [21] ✅. Tested on "Python >= 3.10 and PyTorch >= 2.0" [4].

**Minimal inference** (zero-shot PPI, a pretraining task, hence works without fine-tuning) — verbatim shape from the model card [5] ✅:
```python
from fuse.data.tokenizers.modular_tokenizer.op import ModularTokenizerOp
from mammal.model import Mammal
from mammal.keys import *
model = Mammal.from_pretrained("ibm/biomed.omics.bl.sm.ma-ted-458m"); model.eval()
tokenizer_op = ModularTokenizerOp.from_pretrained("ibm/biomed.omics.bl.sm.ma-ted-458m")
sample_dict = {ENCODER_INPUTS_STR: f"<@TOKENIZER-TYPE=AA><BINDING_AFFINITY_CLASS><SENTINEL_ID_0>"
  f"<MOLECULAR_ENTITY><MOLECULAR_ENTITY_GENERAL_PROTEIN><SEQUENCE_NATURAL_START>{p1}<SEQUENCE_NATURAL_END>"
  f"<MOLECULAR_ENTITY><MOLECULAR_ENTITY_GENERAL_PROTEIN><SEQUENCE_NATURAL_START>{p2}<SEQUENCE_NATURAL_END><EOS>"}
# tokenize -> torch.tensor -> model.generate([sample_dict], max_new_tokens=5) -> decode(batch_dict[CLS_PRED][0])
```

**Fine-tuning** is a one-liner per example config [4] ✅:
```
python mammal/main_finetune.py --config-name config.yaml --config-path examples/<task>
python mammal/main_finetune.py ... evaluate=True model.pretrained_kwargs.pretrained_model_name_or_path=<dir>/best_epoch.ckpt
```
Example tasks shipped in the repo [4] ✅: `protein_solubility`, `carcinogenicity` (TDC), `dti_bindingdb_kd`, `molnet`, `scrna_cell_type`, `cell_line_drug_response`, `tcr_epitope_binding`, plus a beginner Colab notebook and an "advanced: create a new Mammal task" tutorial. There is also a **`mammal_mcp` FastMCP server** exposing MAMMAL tasks as tools to agents, and a `mammal_vllm` plugin for high-throughput embedding inference [4] ✅.

The `scrna_cell_type` README documents the gene-expression input contract precisely [22] ✅: AnnData `.h5ad`; rows = cells, columns = genes; `adata.X` must contain **only gene counts**; labels in `adata.obs['cell_type']`; preprocessing = filter cells with < 200 distinct genes, normalise total counts to 1.0, `log(value+1)`, then **uniform binning into n bins numbered 0…n−1 where a smaller bin number means a bigger count**, written back into `.X`; and crucially "**all the names of genes and cell types need to be consistent with the format/naming schema in the tokenizer**". The `cell_line_drug_response` example accepts either a GDSC cell-line name or a custom `.h5ad` plus a drug SMILES [4] ✅.

**Available fine-tuned checkpoints on Hugging Face** (7 from IBM + 2 later, retrieved 2026-10-04) [5] ✅:
`ibm-research/biomed.omics.bl.sm.ma-ted-458m.protein_solubility`, `.dti_bindingdb_pkd`, `.dti_bindingdb_pkd_peer`, `.tcr_epitope_bind`, `.moleculenet_clintox_tox`, `.moleculenet_clintox_fda`, `.moleculenet_bbbp`; plus `michalozeryflato/biomed.omics.bl.sm.ma-ted-458m.wdr91_asms` and `.pgk2_del_cdd` (both 2026-03-02, suggesting later DEL/affinity-selection work), and third-party mirrors (`introvoyz041/…`, `Aurigene-AI/…`). ⚠️ **No public checkpoint exists for the two headline results** — cancer-drug response / carfilzomib and the antibody–antigen AF3 comparison. ✅

**Compute.** Pretraining: ~3 months on 2 nodes with 16 × A100-80 GB [1, Suppl. §3.1] ✅. Inference/fine-tuning: the base model is 458 M parameters / 1.83 GB of F32 safetensors [5], so it fits comfortably on a single 16–24 GB GPU for inference; the repo's Colab notebook runs the PPI example on free-tier hardware [4] 🟡 (not tested by me).

---

## Open questions / gaps

1. How many cell lines, which ones, and with what replicates/IC50 values was the carfilzomib wet-lab experiment run? Not in the paper or supplement. ❓
2. Which AF3 implementation, how many seeds and diffusion samples? Given AF3's documented seed sensitivity on antibody–antigen interfaces [7], this could materially change Table 2. ❓
3. Which fingerprint/radius underlies the Tanimoto < 0.7 claim? ❓
4. Were the four held-out drugs present in the 200 M-molecule SMILES pretraining corpus? (Lipinski/heavy-atom filters make exclusion plausible but unproven.) ❓
5. Why does Table 2 report HER2 MAMMAL AUROC 0.93 while the text and Table S5 say 0.88/0.881? ❓
6. Is there any evidence that multimodal pretraining *causes* the small-molecule gains? No ablation exists. ❓
7. Were the STRING pretraining pairs restricted to particular species? Unstated (relevant to `mammal_for_dogs.md`). ❓
8. What are the 10 citing works, and do any replicate the benchmarks independently? Not enumerated. ❓
9. ~~Does `huggingface.co/ibm/biomed.omics.bl.sm.ma-ted-458m` resolve?~~ **Resolved** — it does; the HF API serves it as `ibm-research/…` and the model card's own code uses the `ibm/` path. ✅ [verifier-resolved]
10. **Were the TDC GDSC1/GDSC2 and DeepCDR subsets free of `BIBF-1120` (= nintedanib)?** Nintedanib is in the GDSC 8.5 catalogue under that code (§6). Verifying this needs the actual TDC drug lists (PyTDC download), which I did not run. ❓ [verifier-added]
11. **Was the carfilzomib ranking driven by proteasome-inhibitor mechanism transfer from bortezomib/MG-132?** Testable by holding out all proteasome inhibitors from fine-tuning and re-predicting; the paper does not do this. ❓ [verifier-added]
12. Which TBG construct gives 384 aa? ❓ [verifier-added]

## Sources

1. Shoshan, Y., Raboh, M., Ozery-Flato, M., Ratner, V., Golts, A., Weber, J. K., Barkan, E., Rabinovici-Cohen, S., Polaczek, S., Amos, I., Shapira, B., Hazan, L., Ninio, M., Ravid, S., Danziger, M. M., Shamay, Y., Kurant, S., Morrone, J. A., Suryanarayanan, P., Rosen-Zvi, M. & Hexter, E. (2026). *MAMMAL – Molecular Aligned Multi-Modal Architecture and Language for biomedical discovery.* npj Drug Discovery 3, 14. https://www.nature.com/articles/s44386-026-00047-4 (article + Supplementary Information PDF, 44386_2026_47_MOESM1_ESM.pdf)
2. Shoshan, Y. et al. (2024–2025). *MAMMAL – Molecular Aligned Multi-Modal Architecture and Language.* arXiv:2410.22367 v1/v2/v3. https://arxiv.org/abs/2410.22367 and https://arxiv.org/html/2410.22367v3 , https://arxiv.org/html/2410.22367v1
3. AI Search (@theAIsearch) (2026). *The biggest AI breakthrough in medicine & drug discovery.* YouTube, uploaded 2026-05-13, 1,914 s. https://www.youtube.com/watch?v=s3rNDndvav0 (title/date/description via YouTube oEmbed + page metadata)
4. IBM BiomedSciAI (2026). *biomed-multi-alignment* GitHub repository (README, examples, mammal_mcp/README). https://github.com/BiomedSciAI/biomed-multi-alignment (metadata via GitHub API, retrieved 2026-10-04)
5. Hugging Face model repository `ibm-research/biomed.omics.bl.sm.ma-ted-458m` — README, `config.json`, `tokenizer/config.yaml`, `tokenizer/gene_tokenizer.json`, `tokenizer/t5_tokenizer_AA_special.json`, `tokenizer/cell_attributes_tokenizer.json`, safetensors parameter count. https://huggingface.co/ibm-research/biomed.omics.bl.sm.ma-ted-458m
6. UniProt Consortium. UniProtKB entries P00533 (EGFR), P04626 (ERBB2/HER2), P22897 (MRC1/CD206), P04275 (VWF), P02768 (ALB), P05543 (SERPINA7/TBG), P01375 (TNF). https://rest.uniprot.org/ (release 2026_03)
7. Abramson, J. et al. (2024). *Accurate structure prediction of biomolecular interactions with AlphaFold 3.* Nature 630, 493–500. https://www.nature.com/articles/s41586-024-07487-w
8. Gopalan, S. & Narayanan, S. (2025). *Hallucinations in AlphaFold3 for Intrinsically Disordered Proteins with disorder in Biological Process Residues.* arXiv:2510.15939v2. https://arxiv.org/abs/2510.15939
9. Pinet, L. et al. (2021). *Structural and dynamic characterization of the C-terminal tail of ErbB2: Disordered but not random.* Biophysical Journal 120, 1869–1882. doi:10.1016/j.bpj.2021.03.005
10. Thomas, S. D. et al. (2025). *Impact of intrinsically disordered regions and functional disorder hotspots in the human kinome.* Briefings in Bioinformatics 26, bbaf662. doi:10.1093/bib/bbaf662
11. Ross, J., Belgodere, B., Chenthamarakshan, V., Padhi, I., Mroueh, Y. & Das, P. (2022). *Large-scale chemical language representations capture molecular structure and properties.* Nature Machine Intelligence 4, 1256–1264 (preprint doi:10.21203/rs.3.rs-1570270/v1)
12. Baker, A. F., Hanke, N. T., Sands, B. J., Carbajal, L., Anderl, J. L. & Garland, L. L. (2014). *Carfilzomib demonstrates broad anti-tumor activity in pre-clinical non-small cell and small cell lung cancer models.* Journal of Experimental & Clinical Cancer Research 33, 111. doi:10.1186/s13046-014-0111-8
13. Kong, X., Huang, W. & Liu, Y. (2023). *End-to-End Full-Atom Antibody Design.* ICML 202, 17409–17429; arXiv:2302.00203 (Tables 1, 5 and §6 "Data Diversity and Evaluation Metrics")
14. Genomics of Drug Sensitivity in Cancer. `screened_compounds_rel_8.5.csv` and `Cell_Lines_Details.xlsx`, GDSC release 8.5. https://cog.sanger.ac.uk/cancerrxgene/GDSC_release8.5/
15. Wikipedia. *Carfilzomib* (formula C40H57N5O7, molar mass 719.924 g/mol; FDA approval July 2012 for multiple myeloma; PX-171-007 phase Ib/II in solid tumours). https://en.wikipedia.org/wiki/Carfilzomib
16. Wikipedia. *Nintedanib* (C31H33N5O4, 539.636 g/mol). https://en.wikipedia.org/wiki/Nintedanib
17. Wikipedia. *Infigratinib* (C26H31Cl2N7O3, 560.48 g/mol; FGFR1-3; accelerated approval May 2021 for cholangiocarcinoma). https://en.wikipedia.org/wiki/Infigratinib
18. Wikipedia. *Vemurafenib* (C23H18ClF2N3O3S, 489.92 g/mol; BRAF V600E, melanoma). https://en.wikipedia.org/wiki/Vemurafenib
19. Park, J. E. et al. (2019). *Expanding therapeutic utility of carfilzomib for breast cancer therapy by novel albumin-coated nanocrystal formulation.* Journal of Controlled Release 302, 148–159. doi:10.1016/j.jconrel.2019.04.006
20. Patel, R. (2026). *IBM's MAMMAL model puts open AI drug discovery in sharper focus.* Startup Fortune. https://startupfortune.com/ibms-mammal-model-puts-open-ai-drug-discovery-in-sharper-focus/
21. Python Package Index. *biomed-multi-alignment* 0.2.6 metadata. https://pypi.org/pypi/biomed-multi-alignment/json
22. IBM BiomedSciAI. `mammal/examples/scrna_cell_type/README.md`. https://raw.githubusercontent.com/BiomedSciAI/biomed-multi-alignment/main/mammal/examples/scrna_cell_type/README.md

---

## Verification notes

*Independent audit by Fable 5.1, 2026-10-04. ~75 primary-source retrievals. Full record: `../07_verification/mammal_verification.md`.*

**Reliability: high.** Every table reproduced in this file (journal Tables 1–3, Suppl. Tables S1–S8) was re-fetched and matched **cell for cell**, as did the architecture table against the live `config.json`, the parameter count (458,007,202 F32), the tokenizer counts (AA 340 / CELL_ATTRIBUTES 1,103 incl. 580 `CL:` + 209 `UBERON:` / GENE 95,218 incl. 94,904 bracketed, 2,049 `ENSG`, **0** `ENSCAFG`), all seven UniProt lengths, the PyPI 0.2.6 metadata, the GitHub stats (Apache-2.0, 131 stars, 35 forks) and the Hugging Face checkpoint list. Fifteen citation spot-checks (refs 22, 24, 27, 32, 36, 40, 47, 54, 60, 62, 63, 71, 72, 73, 74, 92, 104) were all correctly attributed. Every verbatim quotation checked was verbatim — including the carfilzomib passage, the Tanimoto sentence, the CELLxGENE human-only filter, the STRING "same species" negatives, the three-month/16×A100 sentence, the AF3 three-hypotheses sentence, the Table 1 footnote, the Contributions line, the AF3 and dyMEAN quotes, and both Startup Fortune quotes.

**Corrected:** the TBG mature-chain claim (395 aa, not 384 — the paper's 384 matches no annotated form); the attribution of the "residual connections" quote (Fig. 1 caption, not Methods 4.1); the dyMEAN unigram citation (§7, not §6); the title-difference note (all three arXiv versions use the short title).

**Upgraded from flagged-uncertain:** the Suppl. Table S3 row mapping (now verified exactly); the "2 billion ≈ 1,840 M" reconciliation (the paper's own Fig. 1A caption counts per dataset); the arXiv CC BY-SA 4.0 licence; the `ibm/…` Hugging Face path (it resolves); the Startup Fortune quotes.

**Downgraded:** the Tanimoto "training set = GDSC fine-tuning set" reading (an inference, not a statement).

**Added by the verifier** — three findings the original draft did not have: (1) GDSC contains **bortezomib and MG-132**, so the carfilzomib result is confounded by proteasome-inhibitor **mechanism-class** transfer, not only by structural novelty; (2) **nintedanib is in the GDSC 8.5 catalogue as `BIBF-1120`**, so "not present in the GDSC training data" must be scoped to the TDC/DeepCDR subsets; (3) Suppl. Table S8's cell-type improvement (53.44 %) **contradicts its own row** (+48.9 %). Also: arXiv v1 has 19 authors and no Technion affiliation, independently corroborating that the wet-lab work post-dates the preprint; Table 2's CD206 "1.00" is 0.997 rounded.

**Unresolved:** open questions 1–8 and 10–12 above stand as written.
