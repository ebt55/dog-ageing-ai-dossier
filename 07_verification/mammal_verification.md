# Verification: the MAMMAL files (`02_mammal/`)
> Part of the dog-ageing research dossier · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> Independent audit by **Fable 5.1**, 2026-10-04. Subject: three files written by Opus 5.5 — `mammal_paper_deep_dive.md`, `video_claims_factcheck.md` (77 claims), `mammal_for_dogs.md`. Method: ~75 primary-source retrievals (journal HTML + all three tables, the 17-page supplementary PDF, arXiv v1/v2/v3, Hugging Face config + all four tokenizer files + safetensors metadata, GitHub, PyPI, STRING bulk files, UniProt, Ensembl, Cellosaurus, GDSC release 8.5, PubChem, Europe PMC, the dyMEAN and AlphaFold 3 papers, YouTube metadata, and the raw video transcripts). Scratch work: `scratchpad/verify_mammal/`.

## Reliability rating

**High (4.5/5).** This is unusually careful work. Of roughly 200 checkable assertions across the three files I found **two substantive factual errors, one arithmetic-bookkeeping failure, three citation mis-locations and one overstated characterisation** — and no fabricated figure anywhere.

Justification:

- **Every table reproduced in the deep dive matched the source cell for cell.** Journal Tables 1, 2 and 3 and Supplementary Tables S1–S8 were re-fetched and compared value by value. Table 1's 11 benchmark rows are numerically identical across arXiv v1, arXiv v3 and the journal version, exactly as claimed — I compared all 33 SOTA/MAMMAL/improvement cells across the three.
- **Every verbatim quotation I checked was genuinely verbatim** — roughly 30 of them, including all the load-bearing ones: the carfilzomib passage, the Tanimoto sentence, the CELLxGENE human-only filter, the STRING "same species" negatives, "trained for three months over two nodes with 16 A100-80G GPUs", the AF3 three-hypotheses sentence, the 1 % rule, the Table 1 footnote, the Contributions line, the AF3 and dyMEAN quotes, the Baker et al. carfilzomib IC50s, the Mealey 4-bp-deletion sentence, and both Startup Fortune quotes. Not one was a paraphrase dressed as a quote.
- **The hardest claim to check was reproduced to the digit.** The canine gene-coverage figure (15,784 / 20,199 = 78.1 %; human 19,352 / 19,699 = 98.2 %) came back exactly on an independent re-run from the STRING bulk files and the shipped tokenizer.
- **All 15 citation spot-checks resolved to the right paper**, including the fiddly ones (ref 40 = Kortuem & Stewart *Blood* 2013; ref 63 = Jing et al. 2024; ref 92 = Chaves *Tx-LLM*; ref 104 = Jin *AttABseq*; refs 72/73/74 = Gopalan preprint / Thomas kinome / Pinet ErbB2).
- **Calibration was good in both directions.** Where the files hedge (🟡/❓) the hedges were warranted; where they assert (✅) the assertions held, with the exceptions listed below. The author also self-flagged the two places that most needed checking (the Table S3 reconstruction and the "2 billion" inference) — and both turned out to be *right*, which is the better kind of error to make.

Half a point off for: the claim-count arithmetic in the fact-check file being wrong three ways at once; the TBG mature-chain error; and the canine miss-bucket overstatement. None of these changes a conclusion, but the claim counts were visible in the TL;DR and would have been quoted downstream.

## Counts

| | Count |
|---|---|
| Assertions checked against a primary source | **~200** (incl. all 18 author-flagged items, every TL;DR bullet in all three files, 31 of the 77 fact-check rows, and ~40 deep-dive ✅ claims) |
| Confirmed unchanged | **178** |
| Corrected | **9** |
| Downgraded in confidence | **2** |
| Upgraded in confidence (over-hedged) | **6** |
| Verdict-severity adjustments (all softenings) | **2** |
| Removed | **0** |
| Unresolved / left open | **13** (11 pre-existing ❓ plus 2 new) |
| New findings added by the verifier | **7** |

Of the 18 author-flagged items, **16 were confirmed exactly as written**, one was corrected (item 10's TBG length gloss) and one was upgraded from "my inference" to "the paper's own arithmetic" (item 6).

## Claim-by-claim table

### Author-flagged items (checked first)

| # | Claim as written | Verdict | Correct value / note | Source |
|---|---|---|---|---|
| 1 | npj Drug Discov. 3, 14 (2026); rec. 2 Sep 2025, acc. 23 Feb 2026, pub. 4 May 2026; CC BY 4.0; 21 authors; 3 affiliations; corresp. Yoel Shoshan | **CONFIRMED** | All exact, including DOI 10.1038/s44386-026-00047-4 and metrics 30k/10/11. Corresponding e-mail yoels@il.ibm.com | journal HTML; suppl. p1 |
| 2 | arXiv v1 28 Oct 2024, v2 1 Nov 2024, v3 6 May 2025; v3 says "3 out of 4", journal "five of seven" | **CONFIRMED** | Timestamps exact to the minute (20:45:52 / 16:53:58 / 07:46:11 UTC) and sizes exact. Both abstract phrasings verbatim | arXiv abs pages |
| 3 | Table 1 identical across v1, v3, journal (≥6 rows) | **CONFIRMED** | All **11** rows identical, all three versions. (It is "Table 2" in v1) | v1 PDF, v3 HTML, journal |
| 4 | "nine tasks and competitive results on two"; >1 % rule; non-wins are CDR-3 (+0.5 %) and AbAg (+0.4 %) | **CONFIRMED** | Abstract and rule verbatim; both improvements recomputed (0.54 %, 0.43 %) | journal Abstract, §2.1, Table 1 |
| 5 | 458,007,202 params; T5 v1.1-base (768 / 2048 / 12+12 / 12 heads / vocab 100,001) | **CONFIRMED** | Every value exact; `_name_or_path` literally `t5/t5-v1_1-base`; safetensors total 458,007,202 F32 | HF `config.json`, model API |
| 6 | Table 3 sums to 2,880 M vs 1,840 M ≈ "2 billion"; labelled author's inference | **CONFIRMED + UPGRADED** | Arithmetic right and the label was *too modest*: Fig. 1A says "**six datasets** … combined sample size of 2 billion", so per-dataset counting is the paper's own | journal Table 3, Fig. 1 caption |
| 7 | CELLxGENE filtered to human samples | **CONFIRMED** | Verbatim: "After filtering for human samples labeled as 'cell' in the 'suspension type' field, we curated a dataset of 30 million samples" | suppl. §3.3 |
| 8 | STRING negatives "randomly matching proteins from the same species" | **CONFIRMED** | Verbatim; 390 M positives at score > 500 + 390 M pseudo-negatives = "a second dataset of 780 million samples" | suppl. §3.3 |
| 9 | "trained for three months over two nodes with 16 A100-80G GPUs" | **CONFIRMED** | Verbatim; ambiguity correctly preserved | suppl. §3.1 |
| 10 | Table 2 per-target AUROCs and n/positives | **CONFIRMED** (one gloss **CORRECTED**) | All 7 rows × 8 columns exact. UniProt lengths exact for EGFR/CD206/VWF/ALB/TNF; HER2 ECD = topological domain 23–652 = **exactly 630**. **But TBG (P05543) has signal peptide 1–20 and mature chain 21–415 = 395 aa, so 384 is neither the precursor nor the mature chain** | journal Table 2; UniProt |
| 11 | HER2 inconsistency: text 0.88 / Table S5 0.881 / Table 2 0.93 | **CONFIRMED** | All three verbatim. v3 had 0.93 in text and 0.931 in its Table S5, as claimed | journal §2.10, Table 2; suppl. S5; v3 |
| 12 | Pre-trained MAMMAL 0.530 on HER2; nanobody values | **CONFIRMED** | S5: 0.530 / AUPRC 0.509. S6 pre-trained: 0.428 / 0.478 / 0.406 / 0.644 / 0.663 / 0.506 — all six exact | suppl. Tables S5, S6 |
| 13 | Nanobody counts 668 (131/537), 475 (64/411), 193 (67/126); "patents, and proprietary datasets" | **CONFIRMED** | All counts and the wording verbatim | journal §2.10 |
| 14 | Carfilzomib passage, "approximately 90–95 %", "limited efficacy in cells of solid tumors", ref 40 = Kortuem & Stewart; Baker et al. 2014 | **CONFIRMED** (+ fairness adjustment, below) | Whole passage verbatim; ref 40 correct; Baker quote verbatim, and that paper also states "Phase 1B studies indicated clinical activity signals in solid tumors" | journal §2.4, refs; Europe PMC |
| 15 | Tanimoto: three drugs < 0.7; vemurafenib 0.82 vs PLX-4720; fingerprint unreported | **CONFIRMED** | Sentence verbatim; PLX-4720 confirmed in GDSC as DRUG_IDs 1036/1371, target BRAF; no fingerprint stated anywhere | journal §2.4; GDSC 8.5 |
| 16 | Suppl. Table S4 AARs; CDR-H3 +19 %, CDR-L3 +39 %; dyMEAN baseline explanation | **CONFIRMED** | S4 exact; +18.9 % / +39.0 % recomputed; dyMEAN Table 5 six-CDR row matches MAMMAL's baseline exactly (H3 37.51 %), headline RAbD is 43.65 % (Table 1) | suppl. S4; dyMEAN |
| 17 | No "ablation" in article or supplement | **CONFIRMED** | 0 matches for `ablat` in the full article text and all 17 supplement pages | journal, suppl. |
| 18 | 15,784 / 20,199 canine (78.1 %) vs 98.2 % human; 0 ENSCAFG; six organism tokens | **CONFIRMED** (re-run) | Reproduced exactly; 0 ENSCAFG and 2,049 ENSG; six species tokens — **plus a bare `<ORGANISM>` the draft omitted**, in all four sub-tokenizer files | STRING v12.0; HF tokenizer |

### Video-related verdicts

| Claim | Verdict | Note | Source |
|---|---|---|---|
| "MAMMAL does not understand DNA" — no nucleotide modality | **CONFIRMED** | `tokenizer/config.yaml` lists exactly four sub-tokenizers (AA, SMILES, CELL_ATTRIBUTES, GENE); a regex sweep for DNA/RNA/nucleotide/genome tokens across all four vocabularies returned only false positives (`<ALTERNATIVE>`, `<INTERNAL_n>`). Claim #73's "Inaccurate" is fair | HF tokenizer files |
| "beat SOTA on all 11" is false | **CONFIRMED** | 9 wins, 2 below the paper's own 1 % threshold. #23's "Inaccurate" is fair | journal Abstract, Table 1 |
| BBBP 0.937→0.957, ClinTox 0.948→0.986, baseline MoLFormer | **CONFIRMED** | Exact; MoLFormer confirmed as the baseline and as "trained on 1.1 billion SMILES sequences" (its own paper: "1.1 billion unlabeled molecules from the PubChem and ZINC datasets"). **But #28's "third-smallest of the nine wins" is wrong — 4.0 % is sixth-smallest** | journal §2.3, Table 1; MoLFormer |
| Zheng68k 7.5 % | **CONFIRMED** | 0.710 → 0.763 = +7.46 % relative on macro-F1; 68,579 cells / 11 types / 32,738→20,387 genes all exact; the paper itself says "a 7.5 % improvement in F1" | journal §2.2; suppl. S2 |
| A wet-lab assay was actually run (CellTiter-Glo, Technion co-authors) | **CONFIRMED + strengthened** | Protocol sentence verbatim; Contributions credit Y. Shamay and S. Kurant. **New corroboration: both, and the Technion affiliation, are absent from arXiv v1 (19 authors, 2 affiliations)** | journal §2.4, Contributions; arXiv v1 |

### Other items checked

| Claim | Verdict | Note |
|---|---|---|
| Suppl. Table S3 statistics (958/208/177K; 805/137/92K; 561/223/107K) | **CONFIRMED → UPGRADED** | The draft flagged this as a PDF-layout reconstruction needing re-check; all nine cells are correct |
| Suppl. Table S8 BioMedLM comparison | **CONFIRMED + new error found** | All five rows verbatim, **but the printed cell-type improvement 53.44 % does not follow from 0.509 → 0.758 (= +48.9 %)** while the other four rows reproduce exactly — a fresh internal inconsistency in the paper |
| Table 2 CD206 MAMMAL = 1.00 | **CONFIRMED + precision added** | Table 2 does say 1.00, but Suppl. Table S6 gives **0.997** — a rounding, not a perfect score |
| "residual connections inject features from the encoder's final hidden layer…" cited to Methods 4.1 | **CORRECTED** | It is the **Fig. 1 caption, panel B** |
| dyMEAN unigram warning cited to "§6" | **CORRECTED** | §7 "Limitations" → "Data Diversity and Evaluation Metrics". The 39.61 % figure and "trick the evaluation metrics" are verbatim |
| arXiv licence CC BY-SA 4.0 (flagged 🟡) | **UPGRADED** | Confirmed from the licence href on both v1 and v3 pages |
| Does `hf.co/ibm/biomed.omics…` resolve? (open question) | **RESOLVED** | Yes — API serves it as `ibm-research/…`, and the model card's own example uses the `ibm/` path |
| Startup Fortune quotes (flagged 🟡) | **UPGRADED** | Both verbatim; author Ron Patel, 15 May 2026 |
| Evo 2 attribution (flagged 🟡) | **UPGRADED** | *Nature* 652, 1349–1361 (2026), Arc Institute |
| Tanimoto "training set" = GDSC fine-tuning set (marked ✅) | **DOWNGRADED to 🟡** | A reasonable reading, but the paper does not say it |
| Canine misses "overwhelmingly un-named genes" / four buckets | **CORRECTED** | The four buckets cover ~52 %; truly un-named ~44 %; ~45 % are properly named canine symbols |
| Organism tokens in "all three sub-tokenizer files" | **CORRECTED** | All **four**, including the SMILES BPE file; and eight organism-related tokens, not seven |
| Fact-check claim counts ("61 substantive claims", 31/13/8/6/2/1; tally summing to 62) | **CORRECTED** | The table has **77** rows: 33 / 19 / 10 / 8 / 4 / 2 / 1 |
| GDSC cell-line tissue parse (1,002 lines; NSCLC 111, urogenital 105, …) | **CONFIRMED** | Re-parsed `Cell_Lines_Details.xlsx`; all twelve counts exact |
| Wouters 2020 ($985.3 M median, 95 % CI 683.6–1228.9; mean $1,335.9 M); Wong 2019 (406,038 entries, 3.4 % oncology); Mullard 2016 as the paper's 90 % source | **CONFIRMED** | All verbatim |
| 2024 Chemistry Nobel split | **CONFIRMED** | Baker 1/2 "for computational protein design"; Hassabis and Jumper 1/4 each "for protein structure prediction" |
| AF3 limitation quotes + 1,000-seed sensitivity | **CONFIRMED + strengthened** | Both quotes verbatim; exact wording is "keep improving" (file had "keeps"). AF3's own benchmark used five seeds everywhere **except protein–antibody, ranked across 1,000** |
| Video metadata (2026-05-13, 1,914 s, 122,790 views, npj link) | **CONFIRMED** | Exact; the description's chapter list also corroborates the timestamp column and the 13:48 sponsor boundary |
| Six load-bearing video quotations | **CONFIRMED** | All verbatim in the raw transcripts, including the #28 arbitration ("a **few** percentage points" in the auto-captions) |
| PyPI 0.2.6 / GitHub (Apache-2.0, 131★, 35 forks) / HF checkpoint list / HF Space | **CONFIRMED** | Every item exact, including `fuse-med-ml==0.4.1`, `transformers>=5.0,<6.0`, `peft>=0.19`, upload 2026-09-16, and "no public checkpoint for the two headline results" |
| Dog-file external sources (Mealey, FACC, Ammons, DAP, Cellosaurus 990, UniProt 46,473/857/199, UniRef90 19,003, Ensembl ROS_Cfam_1.0 + IGF1/CDKN2A orthology, CELLxGENE Census species, OAS species menu, three vet mAbs, scrna README contract) | **CONFIRMED** | All exact; quotations verbatim |

## Edits made

**`mammal_paper_deep_dive.md`** (33 `[verifier-…]` markers)
1. Status line updated.
2. §5: TBG "384 = mature chain" corrected to 395 aa, construct unexplained, confidence → ❓.
3. §2: "residual connections" quote re-attributed to the Fig. 1 caption.
4. §1: v1 row rewritten — "AlphaFold" absent from v1 *entirely*; 19 authors / 2 affiliations; Technion authors added later; short title applies to all three arXiv versions, not v1 alone.
5. §3: the "2 billion" reconciliation upgraded from the author's inference to the paper's own arithmetic (Fig. 1A).
6. §6: Suppl. Table S3 caveat withdrawn (verified exactly).
7. §6: Tanimoto scope-limit reading downgraded ✅ → 🟡.
8. §6: **new** — bortezomib/MG-132 mechanism-class confound; nintedanib as `BIBF-1120`; PLX-4720 and bortezomib pass both pretraining filters.
9. §6: carfilzomib closing line replaced with a two-sided "balanced reading".
10. §4: Table S8's 53.44 % vs +48.9 % inconsistency, plus BioMedLM's 1,024-token and two-day caps.
11. §5: CD206 1.00 = 0.997 rounded; HER2 ECD/C-tail residue ranges; AF3 1,000-seed detail.
12. §2.6: dyMEAN §6 → §7, with the six-CDR row match spelled out.
13. §1/§8: arXiv licence, `ibm/` path and HF Space confirmed; fine-tune filter URL caveated.
14. §7: three new critique bullets; open questions 9 resolved, 10–12 added.
15. TL;DR: mechanism-class caveat added to the carfilzomib bullet.
16. `## Verification notes` appended.

**`video_claims_factcheck.md`** (13 `[verifier-…]` markers)
1. Status line updated.
2. TL;DR claim counts replaced with a correct 77-row recount; tally block replaced with a per-verdict table listing the row numbers so it is checkable.
3. #28: "third-smallest" → sixth-smallest, with the full ranking shown.
4. #12 and #47 downgraded in severity (see below).
5. #43, #44, #49 evidence cells re-balanced; "fabricated" softened in the TL;DR and the Overall assessment.
6. #2: "byte-identical" → "numerically identical", with the reason.
7. #8 Evo 2 verified; source 12 given a real citation.
8. #35: nintedanib/`BIBF-1120` and bortezomib/MG-132 findings; PubChem weights and heavy-atom counts.
9. #45: arXiv v1 author-list corroboration.
10. #55: CD206 rounding; the Discussion's "six of seven" framing.
11. #60: exact AF3 wording + the 1,000-seed benchmark detail.
12. #67/#69: dyMEAN table and section references fixed.
13. Open questions: #6 timestamp fixed, #7 resolved, two added.
14. `## Verification notes` appended.

**`mammal_for_dogs.md`** (12 `[verifier-…]` markers)
1. Status line updated.
2. TL;DR: miss-set characterisation corrected with measured percentages; human denominator added.
3. §2: organism-token list corrected (bare `<ORGANISM>`; all four files; eight tokens, six species).
4. §2: miss buckets replaced with a measured breakdown table, and the "other" 45 % characterised — DLA/MHC, CYP2D15/CYP3A12, β-defensins — with the practical consequence stated.
5. §4.1: GDSC drug IDs re-confirmed; 621-compound catalogue size and the code-name warning added.
6. §4.3 and source 11: TCRαβ atlas expanded with authors, full title and the 22-cluster result; upgraded from 🟡.
7. Open question 6 partly resolved and re-scoped to expression-weighted loss.
8. `## Verification notes` appended.

## Verdict-severity adjustments

Two softenings, no hardenings.

| Row | Was | Now | Why |
|---|---|---|---|
| #12 "billions of antibody sequences" | Exaggerated | **Mostly accurate** | OAS states "over one billion". "Billions" overstates it, but mildly, and the database is genuinely of that order; the 650 M figure cited against the claim describes MAMMAL's filtered subset, not OAS's size, so it was doing unfair work in the evidence cell. |
| #47 "approximately 95 % of all 805" | Exaggerated | **Mostly accurate** | The video keeps the hedge "approximately", and 95 % is the top of the paper's *own* stated 90–95 % range. Quoting an upper bound inside a stated interval is imprecision, not inflation. The substantive criticism — that this is a model-prediction figure presented where a wet-lab figure is implied — is retained and is the real problem with the claim. |

**The carfilzomib "fabricated" wording — the fairness question I was asked to settle.** I softened the *characterisation* and kept the *verdicts*.

Kept: #43 **Misleading**, #44 and #49 **Inaccurate**. These are fair. The video asserts a categorical, currently-held expert consensus that carfilzomib "was useless against solid tumors" and that "we don't have this knowledge before" — and 2014 work reports IC50s from "< 1.0 nM to 36 nM" in five NSCLC lines plus a xenograft survival benefit, with the recognised barrier being solubility and in-vivo instability rather than target-cell insensitivity. "For decades" is additionally wrong on the timeline: carfilzomib was approved in July 2012, about 14 years before the video.

Softened: the word **"fabricated"** (TL;DR) and **"invents"** (Overall assessment), now "overstated" and "inflates a genuine clinical limitation". Reasoning: there is a real clinical fact underneath. Carfilzomib holds no solid-tumour indication, and proteasome inhibitors as a class have never converted preclinical potency into one — so a clinician saying "it doesn't work in solid tumours", meaning *clinically*, is making a defensible statement. The video's error is a category slide from "limited clinical success" to "inert in solid-tumour cells, and everyone believed it", not an invention from nothing. Notably the 2014 paper's own background says "Phase 1B studies indicated clinical activity signals in solid tumors", which cuts against a consensus of futility but also shows the question was live rather than settled either way. Calling the narrative fabricated implies the video made up the premise; it did not — it exaggerated a real one, which is the pattern the rest of the file correctly identifies. The paper is not blameless either: its own "limited efficacy **in cells** of solid tumors" is the phrase the 2014 cell-line data actually contradict, and it rests on a general drug review.

## New findings the original files did not have

1. **The carfilzomib result is confounded by mechanism-class leakage.** GDSC release 8.5 screens **bortezomib** (DRUG_IDs 104, 1191) and **MG-132** (9, 1862), both proteasome inhibitors and both among the most broadly cytotoxic agents in cell-line panels. MAMMAL fine-tuned on their IC50 profiles. Predicting carfilzomib as most potent across solid-tumour lines is therefore substantially explainable as target-class transfer. The Tanimoto analysis tests *structural* novelty and is blind to this — indeed a low Tanimoto between carfilzomib (peptide epoxyketone) and bortezomib (boronic dipeptide) is exactly what two same-target drugs of different chemotypes would give. **This is the strongest available caveat on the paper's headline generalisation claim, and neither the paper, the video, nor the original files raise it.**
2. **Nintedanib is in the GDSC 8.5 catalogue** as `BIBF-1120` (DRUG_ID 380; VEGFR/PDGFR/FGFR). Carfilzomib, infigratinib and vemurafenib are absent under every synonym checked. So "four drugs not present in the GDSC training data" must mean "not in the TDC/DeepCDR subsets used" — plausible (208 and 137 drugs out of 621 catalogued) and implied by the reported Tanimoto < 0.7, but looser than the paper's phrasing.
3. **Supplementary Table S8's cell-type improvement is internally inconsistent**: 53.44 % printed, +48.9 % implied by its own 0.509 → 0.758, while the other four rows reproduce exactly.
4. **arXiv v1 has 19 authors and no Technion affiliation.** Yosi Shamay and Sharon Kurant — the two co-authors credited with the experiments — appear only from v3. Independent corroboration that the wet-lab assay post-dates the October 2024 preprint, which is the best available evidence that it is a genuinely new experiment.
5. **"AlphaFold" does not appear anywhere in arXiv v1**, not merely in its abstract.
6. **Table 2's CD206 "1.00" is 0.997 rounded**; TBG's AF3 1.00 is exactly 1.0.
7. **The canine coverage gap removes two specific load-bearing biologies** — the canine MHC (`DLA-DRA`, `DLA-DQA1`, `DLA-DMA`, `DLA-DOA`, `DLA88`) and the canine drug-metabolising cytochromes (`CYP2D15`, `CYP3A12`) — not just poorly annotated filler. These are precisely the gene sets behind the immunogenicity risk in `mammal_for_dogs.md` §4.2 and the canine-ADME caveat in §3.

## Open issues

1. **Did the TDC GDSC1/GDSC2 or DeepCDR splits contain `BIBF-1120`?** Decides whether the paper's "not present in the GDSC training data" is strictly true. Needs the PyTDC drug lists; not downloaded.
2. **How much of the carfilzomib ranking is proteasome-class transfer?** Only a held-out-mechanism re-run answers it, and no public checkpoint exists for the cancer-drug-response model.
3. **Which TBG construct gives 384 aa?** Matches neither the SERPINA7 precursor (415) nor its mature chain (395).
4. **Which is right in Suppl. Table S8 — the 0.509 baseline or the 53.44 % improvement?**
5. **The carfilzomib wet-lab experiment's scale remains unknown** (no cell lines, n, IC50s, replicates or statistics anywhere). Claim #46's "perfectly matched" stays unfalsifiable.
6. **AF3 version, seed count and diffusion samples unreported** — material, given AF3's own paper used 1,000 seeds for protein–antibody targets and five elsewhere.
7. **Tanimoto fingerprint type/radius unreported.**
8. **The nanobody binder set is not public** ("patents, and proprietary datasets"), despite the blanket "All datasets used in this study are publicly available". The AF3 comparison is irreproducible.
9. **The paper's 10 citing works were not enumerated** by either the author or me, so independent replication remains unassessed.
10. **Was the STRING pretraining pull restricted by species?** Unstated; the single biggest unknown for canine protein tasks.
11. **No OAS-scale canine antibody repertoire resource was found**; if one exists, `mammal_for_dogs.md` §4.2 changes materially.
12. **Expression-weighted canine tokenization loss unquantified** — the 78.1 % is a symbol-count figure; the fraction of a real dog transcriptome's *reads* falling on untokenizable genes needs an actual canine `.h5ad`.
13. **Nothing was tested empirically.** No model was downloaded or run, by the author or by me. Every readiness verdict in `mammal_for_dogs.md` §3 remains an inference from documented data composition and vocabulary contents — which that file states plainly, and which is the correct framing.
