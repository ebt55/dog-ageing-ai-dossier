# Verification report: 06_ai_toolkit
> Part of the dog-ageing research dossier · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> Independent fact-check by **Fable 5.1** · 2026-10-04
>
> Files audited (all three written by Opus 5.5 on 2026-10-04):
> - `06_ai_toolkit/canine_data_resources.md` (103 sources)
> - `06_ai_toolkit/ai_tools_for_dog_aging.md` (106 sources)
> - `06_ai_toolkit/research_path_candidates.md` (18 proposals, 114 sources)
>
> **Method — about 95 network calls plus two recomputations.**
> - **Recomputed from scratch:** all four human↔dog GH/IGF-axis alignments (UniProt FASTA → Biopython 1.88 `PairwiseAligner`, global, BLOSUM62, open −10 / extend −0.5, identity over non-gap columns), both in precursor and mature-chain framings; and the per-residue pLDDT means for dog and human IGF1 from the AlphaFold DB v6 confidence files.
> - **Re-downloaded and re-grepped:** the OpenGenome2 `species_metadata.csv` (15.3 MB, 76,071 rows).
> - **APIs:** Crossref (115 DOIs), Europe PMC search and `fullTextXML` (~50 records), bioRxiv details, UniProt REST (proteome, entry counts, FASTA, release headers), AlphaFold DB prediction API + `latest/` FTP listing, Hugging Face model and dataset APIs (16 models, 3 datasets), Ensembl REST and annotation pages, the **ICDC GraphQL API**, the Cellosaurus API, arXiv.
> - **Raw files, not summaries:** `LICENSE`/`LICENSE.md`/`MODEL_LICENSE.md`/`DESCRIPTION` for 28 GitHub and Hugging Face repositories, and the raw READMEs/model cards for AF3, AlphaMissense, AlphaGenome, Boltz, Chai, Evo 2, NT/NTv3, State, UCE, GPN, TranscriptFormer, RFdiffusion, Foundry, PrimateAI-3D, EnsembleAge, Geneformer, ESM3/ESMC, TxGemma and Tahoe-100M.
> - **Web pages:** AnAge (stats + dog entry), HAGR, OMIA, CRDC/ICDC, AWS Open Data registry, CELLxGENE Census docs and release-info, Zoonomia, Chai Discovery, Darwin's Ark, Dog10K, data.dogagingproject.org, and the Nature article pages for GPN-Star and Tyshkovskiy 2026.
> - **Blocked to me as well as to the author:** rvc.ac.uk (403 on both paths), aging-us.com article text (403), academic.oup.com (403), dogagingproject.org (returns no readable text), NCBI GEO (CAPTCHA).
>
> Every in-file change is marked `[verifier-corrected]`, `[verifier-added]`, `[verifier-upgraded]`, `[verifier-downgraded]`, `[verifier-confirmed]`, `[verifier-refined]`, `[verifier note]` or `Verifier comment:`. Each file ends with a "Verification notes" section.

---

## Overall reliability: **HIGH** for the two resource/tool files, **MEDIUM-HIGH** for the proposals file

**Justification.**

**What earns the rating.**
- **No fabricated citation, and no mis-attributed citation, was found anywhere in 323 source entries.** I resolved 115 DOIs through Crossref: 114 returned the stated paper with the correct journal, year and first author, and the single 404 (Kang et al. 2026 GeroScience) is a Crossref indexing gap — Europe PMC holds the DOI, PMID 42753031. This is the strongest single signal in the audit.
- **The author genuinely did the work they claimed to do.** The two "my own computation" claims both reproduce. All four alignment identities came back to the decimal (97.35 → 97.4%, 91.89 → 91.9%, 82.29 → 82.3%, 68.37 → 68.4%), the mature-IGF-1 substring test is true, and the AlphaFold DB pLDDT values (55.19, 59.06, 53.91) and the two 404s are exactly as stated. The OpenGenome2 grep reproduces row for row.
- **The flagged-as-uncertain items were, with two exceptions, correctly flagged.** Of 17 self-flagged claim groups, 7 resolved in the author's favour (and were upgraded), 4 were confirmed as stated, 4 needed correction, and 2 got worse on inspection. That is a well-calibrated confidence layer — the file's 🟡 and ❓ tags were doing real work rather than hedging.
- **Licences — the thing most likely to be wrong in a file like this — were almost all right.** Of the 15 licence claims singled out in the brief, 14 were correct as written and the 15th (Enformer) was merely under-confident. I read the actual licence text in every case.

**What holds the rating back.**
- The highest-profile *conceptual* claim in the tools file — "**Evo 2 … the only frontier DNA model that can be run on canine sequence without retraining**" — is **false**, and was stated three times. NTv3 was pretrained on the same OpenGenome2 corpus. This is the kind of claim a reader would repeat.
- Several ✅ tags were applied to figures that the author had only seen in a search summary, most visibly the DAP "PLINK1 bfiles on Terra" distribution claim and the whole VetCompass scale paragraph, where **no source either agent has ever opened** supports 7.5M dogs, 1,800 practices or 28M animals.
- One arithmetic/consistency slip in the Dog10K-adjacent material (52%/48% single-breed split, actually 54.3/45.7) and one inverted statistic (AFDB "165M proteins with 365M domain annotations" → 361M annotations covering 165M proteins).
- The proposals file is rated a notch lower only because **one of its five Tier A method sections is not executable as written** (array-based clocks applied to RRBS data, #1 step 1), and because four proposals lean on a resource that does not do what they need.

**Spot-check coverage against the brief's minimums:** every TL;DR bullet in all three files (6 + 6 + 1 multi-part); **32 cells** in the tools master table (dog-ready status, licence and link); **19 ✅ claims** sampled beyond the flagged list; **38 citations** checked for existence, metadata and whether they support the sentence; **16 URLs/endpoints** tested. All 17 flagged items and all 5 "unverified items" addressed.

---

## Counts

| Category | n |
|---|---|
| Claims checked | **147** |
| CONFIRMED | **96** |
| CORRECTED | **24** |
| DOWNGRADED | **12** |
| UPGRADED (a sub-type of corrected; counted separately for clarity) | **9** |
| REMOVED | **0** (wrong statements were corrected in place or re-scoped, never deleted) |
| UNRESOLVED | **15** |

Proposal review: 18 proposals examined, **18 `Verifier comment:` lines added**, of which **9 flag a material problem** (#1, #3, #4, #5, #6, #8, #10, #13, #14).

Each claim is counted once by its principal verdict. "Upgraded" means the author's own 🟡/❓ hedge was resolved in their favour against a primary source.

---

## Claim-by-claim table

Keys: **D** = `canine_data_resources.md`, **T** = `ai_tools_for_dog_aging.md`, **P** = `research_path_candidates.md`.

### A. The author's self-flagged claims (brief items 1–17)

| # | File | Claim | As written | Verdict | Correct value / note | Source |
|---|---|---|---|---|---|---|
| 1 | D | DAP Precision Cohort size | 976 dogs, target 1,000, as of 31 Jul 2024 | **CONFIRMED** | "One thousand dog-owner pairs were recruited… we collected and processed blood, urine, fecal, and hair samples from 976 dogs" | EPMC PMID 40038157 |
| 2 | D | DAP Pack size | 47,408 dog–owner pairs, per Prescott 2025 | **DOWNGRADED** to 🟡 | Not in the readable abstract. Adjacent confirmed figures: 47,444 enrolled through 2023 (PLoS ONE title), **52,705 as of Dec 2025** (Sohrab full text) | EPMC; Sohrab JATS |
| 3 | D | Prescott 2025 citation | GeroScience (2025), DOI 10.1007/s11357-025-01571-3 | **CONFIRMED** | *GeroScience* 47(4):5725–5748, 4 Mar 2025, PMC12397037 | Crossref; EPMC |
| 4 | D | DAP assay list | CBC, chemistry, urinalysis, flow immunophenotyping, LC-MS metabolomics, RRBS, faecal shotgun, cheek-swab low-pass WGS | **CONFIRMED** | Abstract lists every assay verbatim | EPMC PMID 40038157 |
| 5 | D | Terra release model + annual March release | annual, typically March, on Terra at the Broad | **DOWNGRADED** to 🟡/❓ | dogagingproject.org/data-access unreadable to both agents. Confirmed instead: cumulative curated releases for 2023/2024/2025 exist; Terra appears in DAP papers only as acknowledged compute | data.dogagingproject.org; Sohrab acknowledgements |
| 6 | D | 1-year DAP embargo | DAP scientists first, 1-y embargo | **UNRESOLVED** (❓) | No page either agent opened states an embargo length | — |
| 7 | D, P | Sohrab DOI format | 10.64898/2026.03.07.710297 | **CONFIRMED — the prefix is real** | bioRxiv's post-2025 prefix. Two versions: v1 10 Mar 2026, v2 25 Mar 2026; `published: NA`; EPMC PPR1217675 | api.biorxiv.org; EPMC |
| 8 | D, P | Sohrab headline numbers | 7,627 dogs; 976 profiled; 159 analytes | **CONFIRMED** | Verbatim in the abstract | bioRxiv v2 abstract |
| 9 | D | **Sohrab low-pass details (HIGHEST PRIORITY)** | 0.79× ± 0.41× (0.14–5.36×); 1,929-dog panel (12.95–31.06×); 29,089,701 biallelic SNPs; 9,871,985 MAF ≥ 0.01 — flagged 🟡, search-summary only | **UPGRADED to ✅ — all four exact** | Verbatim: "sequenced (mean depth of 0.79x ± 0.41x; range 0.14x to 5.36x), and aligned to the CanFam4.0 reference genome. Genotypes were imputed using a panel of 1,929 deeply sequenced (12.95x to 31.06x) dogs and related canids. Our final dataset includes 29,089,701 biallelic SNPs, of which 9,871,985 are common" | bioRxiv v2 JATS XML (source.xml), Methods |
| 10 | D | "distributed on Terra as PLINK1 bfiles" | 🟡 | **DOWNGRADED to ❓** | Not in the preprint. Only PLINK mention is the software citation; Terra only in acknowledgements | same |
| 11 | D | DAP single-breed/mixed split | 52% single-breed, 48% mixed | **CORRECTED** | "Overall, 45.7% of sequenced dogs are mixed-breed, and half of mixed-breed dogs (51%) are 'complex mixes'" → **54.3/45.7** | same |
| 12 | D | Sohrab scale (added) | — | **CONFIRMED (new)** | 298 genome-wide significant loci; 189 associations; 82/159 traits with ≥1 hit; 957 dogs with 3-y follow-up, 11% died | same |
| 13 | D, P | Dog10K composition | 1,987 canids; 1,611 dogs/321 breeds; 309 village; 63 wolves; 4 coyotes; >48M variants | **CONFIRMED** | Verbatim in the abstract and full text | EPMC PMC10426128 |
| 14 | D | **Dog10K 52.96M vs >48M reconciliation** | ">48M" (file D §2.1) vs "52.96M SNVs" (file D §2.1 DB bullet; sibling file) | **CORRECTED — both are right, and a third figure contradicts them** | ">48 M single-nucleotide, indel, and structural variants" (Genome Biology, all types pooled). The NAR database paper's Table 1 gives **52,963,969 SNVs**, but **its own text says "34.6 million SNVs"**, and its breed count is 324 vs 321. Filtered call set: 27,878,361 autosomal + 847,128 chrX biallelic SNVs; EVA PRJEB62420 | PMC10426128; PMC11701641 |
| 15 | D, T, P | OpenGenome2 contains dog | GCF_011100685.1 + Ensembl r112 dog mRNA/ncRNA | **CONFIRMED by independent download** | Row: `Eukaryote,NCBI_Eukaryotic_Genomes,GCF_011100685.1,…,Canis,Canis lupus,assembly_level=Chromosome`; `Ensembl_Transcripts_mRNA … Canis lupus familiaris, transcript_count=26040`; Ensembl r112 ncRNA for familiaris, basenji, boxer, greatdane, gsd **and dingo** | HF `arcinstitute/opengenome2/species_metadata.csv` |
| 16 | D, T | "five breed ncRNA sets (basenji, boxer, great dane, GSD)" | five, four listed | **CORRECTED** | Four breed sets + dingo + *C. l. familiaris* itself = six *Canis* ncRNA rows | same |
| 17 | D | AFDB has no dog bulk proteome | ~46–50 organisms, no CANLF | **CONFIRMED** | **48** `*_v6.tar` files; zero matches for CANLF or 9615 | ftp.ebi.ac.uk/pub/databases/alphafold/latest/ |
| 18 | D, T | AF-P33712-F1 (dog IGF1) | v6, created 2025-08-01, global pLDDT 55.19 | **CONFIRMED** | Exact; 153 residues; fractionPlddtVeryHigh 0.0 | alphafold.ebi.ac.uk/api/prediction/P33712 |
| 19 | D, T | AF-Q9TU69-F1 (dog GHR) | pLDDT 59.06 | **CONFIRMED** | Exact; 638 aa; fractionPlddtVeryHigh 0.27 | …/Q9TU69 |
| 20 | D | AF-A0A8I3MJV0-F1 (GHR isoform) | pLDDT 53.91 | **CONFIRMED** | Exact; created 2025-03-31 | …/A0A8I3MJV0 |
| 21 | D, T | A0A8I3RQ77 returns 404 | 404 | **CONFIRMED (+ extended)** | 404 for A0A8I3RQ77 **and** A0A8I3MER7 (1344 aa) | …/A0A8I3RQ77, …/A0A8I3MER7 |
| 22 | D | **Dog IGF-1 pLDDT: 55.19 here vs 56.3 in `../01_alphafold`** | conflict | **RECONCILED — both correct** | 55.19 = **global** pLDDT (recomputed 55.20 over 153 residues). 56.35 = mean over the **mature 70-aa domain** (residues 49–118). Same model, different window. Human P05019 for contrast: global 59.53, mature 68.69 — *higher than dog on an identical mature sequence* | v6 `plddtDocUrl` for P33712 and P05019 |
| 23 | D | UniProt UP000805418 | 43,615 proteins; 20,987 genes; 857 reviewed | **CONFIRMED** | Exact, plus 42,758 unreviewed; strain Labrador retriever; GCA_014441545.1; BUSCO 13,953/14,502 score 96; modified 2025-12-05 | rest.uniprot.org/proteomes/UP000805418 |
| 24 | D | Taxon-9615 entries | 46,473 total | **CONFIRMED** | 46,473, of which exactly 857 reviewed; release 2026_03 dated 02-September-2026 | rest.uniprot.org/uniprotkb/search |
| 25 | D | Four dog IGF1R entries | 1425/1403/1344/239 aa | **CONFIRMED** | A0A8I3RQ77 1425, A0A8I3MMA7 1403, A0A8I3MER7 1344, W5XTU7 239 — **all four unreviewed** | UniProt gene query |
| 26 | D, T, P | **IGF1R 97.4% identity** | recompute requested | **CONFIRMED by recomputation** | 1,323/1,359 = **97.35%** over aligned columns | Biopython, BLOSUM62, −10/−0.5 |
| 27 | D, T, P | IGF1 precursor 91.9% | — | **CONFIRMED** | 136/148 = **91.89%** | same |
| 28 | D, T, P | Mature 70-aa IGF-1 identical | exact substring | **CONFIRMED** | P05019[48:118] occurs verbatim in P33712 | same |
| 29 | D, T, P | GHR 82.3% | — | **CONFIRMED** | 525/638 = **82.29%** | same |
| 30 | D, T, P | GH1 68.4% | — | **CONFIRMED** | 147/215 = **68.37%** | same |
| 31 | D, T | **IGF1R: 97.4% here vs 98.1% in `../01_alphafold`** | conflict | **RECONCILED — precursor vs mature** | Human 31–1367 vs dog from residue 89 (`CGPGIDIRND`): **1,312/1,337 = 98.13%**. Of 110 differing columns in the full-length alignment, 86 are N-terminal gaps and only **24** are substitutions past human position 30. Both files now carry the explanation | same |
| 32 | T | AlphaMissense: no weights, human-only, licences | code Apache-2.0; predictions CC BY 4.0; no weights | **CONFIRMED** | Verbatim: "we are not releasing the trained model weights, the code is not meant to be used for making new predictions"; "Predictions for human major transcripts and isoforms"; CC BY 4.0 for predictions | github.com/google-deepmind/alphamissense README + LICENSE |
| 33 | T, P | Hu & Xie 2025 numbers | 284 deleterious / 90 non-deleterious; sens 0.77–0.90; spec 0.20–0.46; auROC 0.55–0.61 | **CONFIRMED (+ scope clarified)** | Every figure verbatim; *Open Vet J* 15(10):5183. Clarifications added: ranges are **across the three tools**, and the 374 variants span **8 species, 126 of them dog** | EPMC PMID 41246429 |
| 34 | D, T, P | Horvath 2022 | 742 samples, 93 breeds, R = 0.97 | **CONFIRMED** | Verbatim ×3 in the full text; PNAS 119(21):e2120887119 | PMC9173771 |
| 35 | D, T | Horvath 2022 EWAS framing | "EWAS of the inverse breed-weight↔lifespan relationship" | **CORRECTED (context added)** | Top hits are ***SF1*** (lifespan) and ***TTC8*** (weight/height); the paper found **no** significant association of epigenetic age *acceleration* with weight or lifespan. Note added so this is not cited as IGF-axis EWAS evidence | PMC9173771; consistent with `breed_wolves_verification.md` |
| 36 | D, T, P | McCoy 2024: DOI, numbers, status | 10.1101/2024.10.03.616519; 864 dogs; >3M CpGs; 0.37 y/y; 34% hazard | **CONFIRMED, status DOWNGRADED** | All figures exact. **Still a preprint** (v2 29 Oct 2024, `published: NA`, EPMC holds only PPR919998). HR 1.34 (1.06–1.69) on **49 deaths** — caveat added in all three files | api.biorxiv.org; EPMC |
| 37 | T, P | Serres Armero 2024 quote | "methylation-related markers reflecting biological age signals are rare and do not colocalize between datasets" | **CONFIRMED verbatim** | Also verbatim: "biological age methylation clocks are affected by population stratification and require heavy parameterization". *Aging* 16(13):10724–10748 | EPMC PMID 38985449 |
| 38 | T, P | TranscriptFormer species | 12 trained, 24 embedding sets, no dog | **Trained list CONFIRMED; "24" DOWNGRADED to 🟡** | TF-Metazoa: 112M cells, 12 species (6 vertebrates incl. rabbit, chicken, *Xenopus*, zebrafish; 4 invertebrates); TF-Exemplar 110M/5 species; TF-Sapiens 57M human. **No dog** in the README species table. The "24 embedding species" count is not reproducible from the current README | github.com/czi-ai/transcriptformer README |
| 39 | T | TranscriptFormer licence | MIT | **CONFIRMED** | `LICENSE.md`: MIT, © 2025 Chan Zuckerberg Initiative | same repo |
| 40 | T | CELLxGENE Census species | LTS 2025-11-08: human, mouse, macaque, marmoset, chimp | **CONFIRMED verbatim** | Census docs quote, plus per-species cell counts on the release-info page listing exactly those five | chanzuckerberg.github.io/cellxgene-census |
| 41 | T, P | AF3 licences | code Apache-2.0; weights from Google, non-commercial; server non-commercial; commercial via Google Cloud | **CONFIRMED** | "You may only use AlphaFold 3 model parameters if received directly from Google"; weights terms restrict to non-commercial organizations; commercial via **Gemini Enterprise Agent Platform on Google Cloud** | README + WEIGHTS_TERMS_OF_USE.md; LICENSE Apache-2.0 |
| 42 | T, P | Boltz-2 MIT (code + weights, incl. commercial) | MIT | **CONFIRMED** | "All the code and weights are provided under MIT license… for both academic and commercial uses"; LICENSE is MIT. Affinity output: "`log10(IC50)`, derived from an `IC50` measured in `μM`", plus `affinity_probability_binary` | github.com/jwohlwend/boltz |
| 43 | T, P | Chai-1 Apache-2.0 (code + weights) | Apache-2.0 | **CONFIRMED** | "Chai-1 is released under an Apache 2.0 License (both code and model weights)… including for drug discovery"; LICENSE Apache-2.0 | github.com/chaidiscovery/chai-lab |
| 44 | T | Arc State non-commercial | non-commercial model licence; code CC-BY-NC-SA | **CONFIRMED** | `MODEL_LICENSE.md` = "Arc Research Institute State Model Non-Commercial License" (23 Jun 2025); `LICENSE.md` = CC BY-NC-SA 4.0; plus an Acceptable Use Policy | HF `arcinstitute/SE-600M`; github ArcInstitute/state |
| 45 | T | NT v2 CC-BY-NC-SA-4.0 | non-commercial | **CONFIRMED** | HF API: `license: cc-by-nc-sa-4.0` | HF `InstaDeepAI/nucleotide-transformer-v2-500m-multi-species` |
| 46 | T | TxGemma HAI-DEF terms, gated | "other" + gated | **CONFIRMED** | `license: other`, `license_name: health-ai-developer-foundations`, link to developers.google.com/health-ai-developer-foundations/terms, `gated: auto` | HF API |
| 47 | T, P | Tyshkovskiy 2026 exists and says what is claimed | >11,000 transcriptomes, >25 tissues, 4 mammals (mouse/rat/macaque/human), CDKN1A + LGALS3, module clocks, dog absent | **CONFIRMED in full** | *Nature* 654(8117):173–188, 27 May 2026, PMC13233323. Abstract verbatim on counts, species, both genes, the UK Biobank protein validation, and "chronic disease accelerated inflammatory-module ageing, whereas caloric restriction and Klotho deficiency…" | EPMC PMID 42203874; nature.com |
| 48 | T, P | GPN-Star species | five model organisms, not dog | **CONFIRMED verbatim** | "five model organisms—*Mus musculus*, *Gallus gallus*, *Drosophila melanogaster*, *Caenorhabditis elegans* and *Arabidopsis thaliana*"; *Nature* 2026, DOI 10.1038/s41586-026-11005-5; checkpoints on HF. Added: non-human models used per-species WGAs of **18–135 species** | nature.com/articles/s41586-026-11005-5 |

### B. The author's "unverified items"

| # | File | Claim | As written | Verdict | Correct value / note | Source |
|---|---|---|---|---|---|---|
| 49 | D | VetCompass scale | >1,800 practices (>30% of UK); >28M animals; ~7.5M dogs; >200M notes 🟡 | **DOWNGRADED to ❓ — UNRESOLVED** | rvc.ac.uk returns **403 to me too** on both paths. No source either agent has opened supports any of these. Calibration from readable papers: a 2026 VetCompass brain-tumour study used a **1,537,397-dog** denominator; a 2026 review cites a 2019 VetCompass demography of "over 2 million dogs" | rvc.ac.uk (403); PMC13554163; PMC13603329 |
| 50 | D | ICDC size | 12 datasets (CRDC) vs 9 studies/598 cases (NCI 2024) | **CORRECTED — RESOLVED** | Portal GraphQL (2026-10-04): **21 studies, 1,262 cases, 1,820 samples, 4,739 files, 5 programs**. CRDC page lists **12 distinct study codes** (verified by enumeration) and states "All data in the ICDC are open-access". Both prior figures are stale snapshots | POST caninecommons.cancer.gov/v1/graphql/; datacommons.cancer.gov |
| 51 | D, P | ICDC data types (new finding) | "+ ICDC tumour transcriptomes ✅" in a single-cell inventory (P #6) | **CORRECTED** | ICDC strategies are **bulk** RNA-seq, WGS, WXS, genotyping array, DNA methylation. **No single-cell data** | datacommons.cancer.gov ICDC page |
| 52 | D | AnAge build date conflict | stats page 16 Dec 2024 vs entry page 03/07/2023 ⚠️ | **CORRECTED — no conflict exists** | **Both pages say Build 15.** Stats page: "Build 15… last updated: December 16, 2024. Entries 4,671 (4,645 species and 26 taxa)". Entry page: "Build 15 (03/07/2023): 4,671 entries". One is a page-update timestamp, the other the build date | genomics.senescence.info/species/stats.php and /entry.php |
| 53 | D | AnAge dog entry | 27 y captivity; sample size large; quality acceptable; Bluey flagged | **CONFIRMED** | "Maximum longevity 27 years (captivity)"; "Sample size Large"; "Data quality Acceptable"; residual 109%; Bluey noted | AnAge dog entry |
| 54 | D | Darwin's Ark data access | FAQ 403, accessions and licence unknown ❓ | **UNRESOLVED (URL corrected)** | `/faq` is a **404**; live paths are **`/faqs`** and **`/collaborate`** ("Data Sharing & Collaboration"). Still no accessions or licence obtainable | darwinsark.org |
| 55 | T | Chai-2 availability | "technical report only; general availability unverified ❓" | **CORRECTED — RESOLVED: no public release** | Announced **30 Jun 2025**. "We are opening up access to a number of academic and industry partners"; "sign up for early access"; granted "in accordance with our Responsible Deployment policy". No weights, no API | chaidiscovery.com/news/introducing-chai-2 |
| 56 | D, P | Cellosaurus canine lines | 990 🟡 | **UPGRADED to ✅** | 990 accessions for `ox:9615` (TSV mode, 991 lines incl. header) | api.cellosaurus.org |

### C. TL;DR bullets and master-table cells (tools file)

| # | File | Claim | As written | Verdict | Correct value / note | Source |
|---|---|---|---|---|---|---|
| 57 | T | **"Evo 2 … the only frontier DNA model that can be run on canine sequence without retraining"** | stated 3× | **CORRECTED — false** | **NTv3 was pretrained on OpenGenome2**: "Pretrained on 9 trillion base pairs from OpenGenome2 and post-trained on >16,000 functional tracks from 24 animal and plant species." Evo 2 keeps the practical advantage (Apache-2.0 vs NTv3's gated "other"), and the claim has been narrowed to "the only **openly licensed** one" | github.com/instadeepai/nucleotide-transformer README; HF `InstaDeepAI/NTv3_*` |
| 58 | T | NT v2 dog membership in the 850 | "❓ unverified" | **RESOLVED: dog absent** | InstaDeep's own URL list has *Canis lupus dingo* (GCF_012295265.1) and Arctic fox, no *C. l. familiaris* or wolf (sibling verifier downloaded the list; consistent with my reading that the NT card never names dog) | `InstaDeepAI/multi_species_genomes/original_urls.csv` via `canine_bio_ai_verification.md`; NT card |
| 59 | T | Evo 2 training scale | "9.3T bp (OpenGenome2 8.8T bp)" | **REFINED** | Nature abstract: "9 trillion DNA base pairs"; OpenGenome2 card: "8.8 trillion base pairs". The 9.3T figure is not in either | EPMC PMID 41781614; HF dataset card |
| 60 | T | Evo 2 licence and sizes | Apache-2.0; 1B/7B/20B/40B; 1M context | **CONFIRMED** | Repo LICENSE Apache-2.0; `arcinstitute/evo2_7b` card apache-2.0; README names 40B/20B/7B/1B and an NVIDIA hosted API | github.com/ArcInstitute/evo2; HF API |
| 61 | T | OpenGenome2 licence | Apache-2.0 | **CONFIRMED** | HF dataset `license: apache-2.0`; card repeats "License Apache 2" | HF API + card |
| 62 | T | AlphaGenome scope and terms | human + mouse; non-commercial API; no weights; >1M prediction cap | **CONFIRMED** | README: "human and mouse genome"; "non-commercial use only and should not be used for the training of…"; "1 million predictions"; client LICENSE Apache-2.0 | github.com/google-deepmind/alphagenome |
| 63 | T | Enformer licence | "open (Apache-2.0 upstream) 🟡" | **UPGRADED to ✅** | Upstream `google-deepmind/deepmind-research` (which hosts `enformer/`) is Apache-2.0 | raw LICENSE |
| 64 | T | Borzoi licence | Apache-2.0 | **CONFIRMED** | `calico/borzoi` LICENSE is Apache-2.0 | raw LICENSE |
| 65 | T | GPN repo licence | MIT (`songlab-cal/gpn`) | **CONFIRMED** | LICENSE MIT, © 2022 Song Lab @ Cal; README links GPN-Star models on HF | raw LICENSE + README |
| 66 | T | scGPT MIT; UCE MIT; Biomni Apache-2.0; BindCraft MIT; ProteinMPNN MIT; EVE MIT; OpenBioMed MIT | as written | **CONFIRMED (7 cells)** | Each repository's LICENSE file read directly | raw LICENSE files |
| 67 | T | popEVE GPL-3.0 | GPL-3.0 | **CONFIRMED (+ consequence flagged)** | LICENSE is GNU GPL v3. Consequence added to T §3 and P #2: a canine derivative inherits copyleft | raw LICENSE |
| 68 | T | RFdiffusion BSD, free for for-profit and non-profit | as written | **CONFIRMED** | README: "BSD License (see LICENSE file). It is free for both non-profit and for-profit use."; LICENSE is BSD, © 2023 Univ. of Washington | raw README + LICENSE |
| 69 | T | Foundry BSD-3-Clause | BSD-3-Clause (Foundry repo) | **CONFIRMED (+ note)** | `RosettaCommons/foundry` is public, BSD-3-Clause, "Central repository for biomolecular foundation models"; PyPI `rc-foundry` (IPD, BSD). **No separate `RFdiffusion3` repo exists** | github.com/RosettaCommons/foundry; pypi |
| 70 | T | ESM-2 MIT | `facebook/esm2_t33_650M_UR50D` MIT | **CONFIRMED** | HF `license: mit` | HF API |
| 71 | T | ESM-1v licence field empty; repo MIT | as written | **CONFIRMED** | HF card has no licence field; `facebookresearch/esm` LICENSE is MIT | HF API; raw LICENSE |
| 72 | T | ESM3 / ESMC licences | `esm3-sm-open-v1` MIT per card; ESMC `mit` + `other` | **CONFIRMED + CLARIFIED** | esm3 HF licence field is **empty**, but its README states MIT and links an MIT `LICENSE.md`. ESMC-6B is tagged `['mit','other']` where "other" is a **third-party dependency notice** (flash-attn/PyTorch/xformers BSD; torchmetrics Apache-2.0), not an added restriction | HF API; raw README; THIRD_PARTY_NOTICE.md |
| 73 | T | ESMC-6B specs | 6B params, 80 layers, 2.37e23 FLOPs, preprint DOI 10.64898/2026.06.03.729735 | **CONFIRMED** | All four on the card; preprint title "Language Modeling Materializes a World Model of Protein Biology" (bioRxiv, 4 Jun 2026) | HF card; api.biorxiv.org |
| 74 | T | Geneformer | V2 ~104M human transcriptomes; Apache-2.0; cancer variant | **CONFIRMED; "V2-316M" NOT FOUND** | Card: Genecorpus-30M (V1), **Genecorpus-104M** (V2), "non-cancer", separate cancer model; `license: apache-2.0`. The "V2-316M" and "~14M cancer transcriptomes" figures are not on the current card — removed from the ✅ framing | HF API + raw README |
| 75 | T | EnsembleAge | v0.99.1, MIT, "110+ individual clocks", multi-platform | **CONFIRMED** | DESCRIPTION: `Version: 0.99.1`, `License: MIT + file LICENSE`; README: "110+ individual clocks", "(Human, Mammal40k, Mammal320k)", "Free for research and commercial use" | raw README + DESCRIPTION |
| 76 | T | MammalianMethylationConsortium MIT | MIT | **CONFIRMED** | LICENSE MIT, © 2021 shorvath (both `main` and `master`) | raw LICENSE |
| 77 | T | PrimateAI-3D access terms | academic/non-profit under signed licence; commercial via Illumina | **CONFIRMED** | README: "academic, non-profit research"; signed academic licence link; "commercial use is available at AI_licensing@illumina.com" | raw README |
| 78 | T | Tahoe-100M terms and composition | "per Arc terms"; 50 lines, 379 molecules, 3 doses | **CORRECTED + DOWNGRADED** | HF dataset `tahoebio/Tahoe-100M` is **`cc0-1.0`**, from **Vevo Therapeutics**. None of "50 cell lines / 379 molecules / 3 doses" appears in the card; the figure appears to come from the secondary Shen preprint | HF API + raw README |
| 79 | T | Precious3GPT weights | "released on HF per preprint 🟡"; dog coverage ❓ | **UPGRADED (weights) / still ❓ (dog)** | `insilicomedicine/precious3-gpt` and `-multi-modal` both resolve, **`cc-by-nc-4.0`** — public but non-commercial. Card claims multi-species with 569 tissues/cell lines; every documented prompt uses `<species>human</species>`, no canine token shown | HF API + raw READMEs |
| 80 | T | MAMMAL | npj Drug Discovery; 2B samples; beat AF3 confidence on 5/7 antigens; weights Apache-2.0 | **CONFIRMED** | *npj Drug Discovery* 3(1), 4 May 2026, PMC13267068; abstract: "2 billion samples", "significantly outperform AlphaFold3 confidence scores… in five of seven"; `ibm/biomed.omics.bl.sm.ma-ted-458m` apache-2.0, ungated | EPMC PMID 42380594; HF API |
| 81 | T | Robin terms | "per repo terms ❓" | **CORRECTED** | `Future-House/robin` is public, **Apache-2.0** | github.com/Future-House/robin |
| 82 | T | Kosmos terms | "per terms ❓"; 79.4% accurate | **CORRECTED (repo) / 🟡 (figure)** | **`Future-House/kosmos` 404s** — no public repo. The 79.4% figure is an arXiv self-report (2511.02824), not independently reproduced | github (404); arXiv |
| 83 | T | GEMME licence/URL | ❓ 404 | **UNRESOLVED (independently)** | `github.com/elodielaine/gemme` 404s for me; lcqb.upmc.fr unreachable; search found no mirror. Chapter is real: *Methods Mol Biol*, "Protein Evolution", pp. 105–122, ISBN 9781071648285 | github (404); Crossref |
| 84 | T | Ahlmann-Eltze and Kedzierska benchmarks | 5 FMs + 2 deep models beaten by simple baselines; zero-shot limitations | **CONFIRMED** | *Nat Methods* 22(8):1657–1661: "None outperformed the baselines"; *Genome Biol* 26: "could be outperformed by simpler methods" | EPMC PMID 40759747, 40251685 |
| 85 | T | Virtual Cell Challenge citations | Cell 2025 and 2026 | **CONFIRMED** | *Cell* 188(13):3370–3374; *Cell* 189(19):5827–5830 | Crossref |
| 86 | T | State scale and venue | 167M cells; Cell 2026 | **CONFIRMED** | *Cell* 189(19):5914–5931.e20; "cell embeddings trained on observational data from 167 million cells" | EPMC PMID 42673963 |
| 87 | T | UCE scale and claim | embeds unseen species; 36M cells, 8 species | **CONFIRMED** | *Nature* 656(8126):183–191; "new cells can be embedded with no data labelling, model training or fine-tuning"; Integrated Mega-scale Atlas 36M cells, 8 species | EPMC PMID 42420460 |
| 88 | T | Gross 2026 pAGE | 2,358 genes; 6,442 compounds | **CONFIRMED** | *Nat Aging* 6(7):1516–1531, abstract verbatim | EPMC PMID 42362889 |
| 89 | T | TRIAD quote | "first rigorous test of a pharmacologic intervention against biological aging…" | **CONFIRMED verbatim** | *GeroScience* 47(3):2851–2877 | EPMC PMID 39951177 |
| 90 | T | Lu 2023 universal clocks | 11,754 arrays, 59 tissues, 185 species, r > 0.96; somatotropic-axis link | **CONFIRMED** | Abstract verbatim | EPMC PMID 37563227 |

### D. Resource-file claims beyond the flagged set

| # | File | Claim | As written | Verdict | Correct value / note | Source |
|---|---|---|---|---|---|---|
| 91 | D | AFDB coverage statistic | "covers >165M proteins with 365M domain annotations" | **CORRECTED (inverted)** | "over **361 million** domain annotations from the Encyclopedia of Domains (TED) covering over **165M** proteins". AFDB's own overall coverage headline is ">214 million protein sequences" (2024 paper) | PMC12807749 |
| 92 | D | AFDB legacy API retirement | retires June 2026 | **CONFIRMED verbatim** | "The legacy API will be retired in June 2026" | same |
| 93 | D | AFDB synced to UniProt 2025_03 | yes | **CONFIRMED** | "updated to UniProt release (2025_03), incorporating Swiss-Prot/UniProtKB isoforms" | same |
| 94 | D | Ensembl dog release | "release 116.1" | **CORRECTED** | Ensembl REST `info/data` → `{"releases":[116]}`; annotation page footer "Ensembl release 116 - June 2026" | rest.ensembl.org; ensembl.org |
| 95 | D | ROS_Cfam_1.0 annotation stats | 20,567 coding; 9,944 non-coding; contig N50 12.02 Mb; scaffold N50 64.04 Mb | **CONFIRMED** | "Coding genes 20,567 Non coding genes 9,944" (3,437 small + 6,485 long + 22 misc); "contigs is 12,024,593 while the scaffold N50 is 64,037,277"; GCA_014441545.1 | Ensembl annotation page; REST assembly |
| 96 | D | Dog10K variant-calling reference | UU_Cfam_GSD_1.0 | **CONFIRMED + REFINED** | UU_Cfam_GSD_1.0 "supplemented by three Y chromosome contigs from a Labrador Retriever (ROS_Cfam_1.0, GCF_014441545.1)" | PMC10426128 |
| 97 | D | Meadows detail figures | 26,960 del / 14,034 ins >50 bp; wolves 14% more; 926 parent genes; 94.9% monophyletic; >75% for 239 breeds; SnpEff + phyloP | **CONFIRMED (6 figures)** | All verbatim. ⚠️ the "14% more" is **structural** variants — noted, matching the sibling correction | same |
| 98 | D | Beagle near-T2T stats | 2.46 Gb; N50 63.17 Mb; BUSCO 98.30%; 29/39 T2T; repeats 34.90%; CC BY 4.0 🟡 | **DOWNGRADED to ❓** | Europe PMC title search returns **zero records** for this assembly; neither agent opened the figshare entry. Every number is uncorroborated | EPMC search |
| 99 | D | Jindo TTAGGA standard | "gapless + QV ≥ 60 standard" | **CORRECTED** | The TTAGGA **standard** requires QV ≥ 50; this assembly meets a stricter **QV ≥ 60**. Confirmed: QV 78.0/76.8; 2,441.6/2,340.5 Mb; BUSCO 99.3%/96.4%; chrY 21,255,890 bp = 5.4× ROS_Cfam_1.0's 3.94 Mb, +~14 Mb new Y; 813 Gb (~340×) | api.biorxiv.org 10.64898/2026.05.17.725804 |
| 100 | D | Kidd 2026 dual assemblies | 5 canines; telocentric; centromeres ~59 kb from start | **CONFIRMED** | *NAR Genom Bioinform* 8(2):lqag035; "centromeres of canine autosomes begin an average of 59 kb from the start… flanked by a 35 kb subtelomeric segment"; STRs 3× more common than VNTRs. "Authors decline the T2T label" and the JBPXEE–JBPXEL accessions remain ❓ | EPMC PMID 42038407 |
| 101 | D | mCanLor1.2 stats | 2,447 Mb; 98.91% in 40 pseudomolecules; scaffold N50 66 Mb; BUSCO 95.5% 🟡 | **UPGRADED to ✅** | All four verbatim in the data note; contig N50 34 Mb; 82 scaffolds; male *C. lupus orion*, Siorapaluk, Greenland; *Wellcome Open Res* 6:310 | PMC8649967 |
| 102 | D | PeptideAtlas | 49% of predicted proteome; 11,792 proteins (11,564 groups, 56%); 10,140 tissue / 385 plasma | **CONFIRMED** | Abstract verbatim; *Sci Data* 13(1) | EPMC PMID 41927601 |
| 103 | D | IMGT IGK | 9 assemblies, 7 breeds, 40 genes, 97 alleles; CanFam3.1 artefacts | **CONFIRMED** | Abstract verbatim; *NAR Genom Bioinform* 8(1):lqag020 | EPMC PMID 41737242 |
| 104 | D | OMIA dog statistics | 1,019 traits; 597 causal variants; 347 single-gene diseases with ≥1 variant | **CONFIRMED** | Live stats table: dog 1019 traits; 597 "all known likely causal variants"; 347 single-gene diseases with ≥1. Total phenes 6,084; 791 species; page "Last updated: 04 Oct 2026" | omia.org/home |
| 105 | D | Buckley 2025 constraint | >2,000 dogs; *PDGFRA* bifid nose (Çatalburun); two *LCORL* variants | **CONFIRMED** | Abstract verbatim; *Genome Res* 35(5):1080–1093 | EPMC PMID 40127928 |
| 106 | D | Donner 2023 | 1,054,293 of 3.5M; 811,628 mixed + 242,665 pure; >150 countries; 250 variants; EMR 43.5%; 57% carry ≥1; full penetrance for 10 | **CONFIRMED (all 7)** | Every figure verbatim, incl. "43.5%; N = 458,433" and "evidence of full penetrance for 10 variants" | PMC9997962 |
| 107 | D | Morrill 2022 | 18,385 surveyed; 2,155 genotyped; breed explains 9% | **CONFIRMED** | Abstract verbatim; *Science* 376(6592):eabk0639 | EPMC PMID 35482869 |
| 108 | D | GRLS open genotypes | 3,224 dogs (3,024 + 200 Golden Oldies); ~1.1M markers; CC-BY-SA; s3://mafgrlsgenome; no AWS account | **CONFIRMED (all)** | "~1.1 million genetic markers from 3224 unique individual dogs… 3024 were from the Golden Retriever Lifetime Study cohort and 200 from the Golden Oldies"; "License CC-BY-SA"; "Update Frequency Static"; "AWS CLI Access (No AWS account required)"; 3,044 goldens | registry.opendata.aws/maf-genome |
| 109 | D | Mammalian Methylation Consortium scale | 15,216 samples, 348 species | **CORRECTED** | Haghani et al. 2023 *Science*: "methylation profiles (n = **15,456**) from 348 mammalian species". GEO record-level count still unverifiable (CAPTCHA) | EPMC PMID 37561875 |
| 110 | D | Wang 2020 | 104 Labradors; >150×; 16·ln(dog_age)+31; GSE146920; Zenodo | **CONFIRMED** | Abstract: "104 Labrador retrievers spanning a 16-year age range, achieving >150× coverage within mammalian syntenic blocks"; *Cell Syst* 11(2):176–185 | EPMC PMID 32619550 |
| 111 | D | Thompson 2017 | 46 dogs + 62 wolves; 41/67/115 CpGs | **CONFIRMED** | Abstract verbatim; *Aging* 9(3):1055–1068 | EPMC PMID 28373601 |
| 112 | D | Jin 2024 | 71 dogs; DNAm R² 0.33, ATAC 0.26, combined 0.29 | **CONFIRMED** | Abstract: 71 dogs, ATAC 26%, DNAm 33%; *Aging Cell* 23(4) | EPMC PMID 38263575 |
| 113 | D | Jang 2026 | drift varies by body size; higher EAA in Korean vs US dogs; sex differences | **CONFIRMED** | Abstract verbatim; *PNAS* 123(29) | EPMC PMID 42441848 |
| 114 | D | Kang 2026 | paired methylome + transcriptome in beagles, 3 age groups; early/late/progressive patterns | **CONFIRMED** (Crossref 404, EPMC holds it) | Abstract verbatim; *GeroScience*, PMID 42753031 | EPMC |
| 115 | D | DoGA | biobank 5,485 samples/132 tissues/13 dogs/12 embryos/24 wolves; atlas 100 tissues from 9 dogs + 12 embryos; >100,000 promoters, >45,000 reproducible | **CONFIRMED, framing CORRECTED** | All figures verbatim. But **"includes wolves" is wrong for the atlas** — wolves are biobanked only — and the atlas dogs are not age-stratified | PMC11494170 |
| 116 | D | Abood 2026 | ~318,000 PBMC transcriptomes; largest canine scRNA dataset; 27 populations; 50/39/30 cohorts | **CONFIRMED** | Abstract verbatim, incl. 19 senior/20 young bulk and 15/15 scRNA; *Front Immunol* 17 | EPMC PMID 42774025 |
| 117 | D | Dog10K DB single-cell integration | 105,057 nuclei; 74,067 leukocytes; 8,565 DNMs from 643 dogs/43 breeds; 30 blood samples | **CONFIRMED** | All verbatim; 30 dogs aged 1–9 y vs 469 humans aged 8–73 y; free access without registration; CC BY-NC | PMC11701641 |
| 118 | D | LeishDog | "preprint 2025" | **CORRECTED** | **Published**: *iScience* (2026), DOI 10.1016/j.isci.2026.116870, per the bioRxiv record. Cell/population counts remain 🟡 (not in the abstract) | api.biorxiv.org |
| 119 | D | Canine brain bank | 55 brains; lipofuscin rises strongly with age in thalamus and hippocampus | **CONFIRMED (preprint)** | Abstract verbatim; Darcy … McKenzie, bioRxiv 14 Jul 2026. Access policy indeed not stated | api.biorxiv.org; EPMC PPR1279057 |
| 120 | D | Gustafson 2026 | 12 drugs × 13 canine + 6 human OSA lines; 4 active; indistinguishable across species | **CONFIRMED** | Abstract verbatim; *Vet Comp Oncol* 24(3):532–544 | EPMC PMID 42036120 |
| 121 | D | Bian 2026 | 6,572 DAP dogs; 100 breed classes; 91.7%; ~150 SNPs | **CONFIRMED** | Abstract verbatim (plus ADMIXTURE benchmark 87.8%) | api.biorxiv.org; EPMC PPR1245910 |
| 122 | D | Harrison 2026 mortality | 937 Precision-Cohort dogs; dog/human metabolite-mortality correlation | **CONFIRMED** | Abstract verbatim; *J Gerontol A* 81(4) | EPMC PMID 41429575 |
| 123 | D | Bamberger 2026 microbiome | >900 dogs; population-level age model | **CONFIRMED**; "compared against Lifelines-DEEP" 🟡 | Abstract confirms >900 dogs and the age-prediction model; the Lifelines-DEEP comparison is not in the abstract | EPMC PMID 42156772 |
| 124 | D | HAGR sub-database counts | DrugAge 1,097; GenAge 307; CellAge 866; LongevityMap 3,144; GenDR 214 | **DOWNGRADED to ❓** | Live HAGR home page says "over 300" genes and "**over 500** ageing-related drugs" — it does not corroborate 1,097. Only the AnAge counts were confirmed numerically | genomics.senescence.info |
| 125 | D | Teng 2022 18-breed coverage | 18 breeds = 50.6% | **CONFIRMED** | "There were 18 breeds included in the life table analyses, accounted for 50.6% of the population" | PMC9050668 |
| 126 | D | McMillan 2024 | 584,734 dogs incl. 284,734 deceased; 155 breeds | **CONFIRMED** | Abstract verbatim | EPMC PMID 38302530 |
| 127 | D | Kraus 2013 | 74 breeds; size↔ageing-rate, not onset | **CONFIRMED verbatim** | "After fitting different mortality hazard models to death data from 74 breeds of dogs… a strong positive relationship between size and aging rate" | EPMC PMID 23535614 |
| 128 | D | Low-pass methods citation [28] | cited as the source of the DAP figures | **CORRECTED** | Buckley et al. 2022 *Mamm Genome* (PMC8913487) is a **methods precedent** (97 downsampled WGS; 676-dog/91-breed panel), not the source of DAP's numbers. Full citation supplied | EPMC PMID 34498136 |
| 129 | D, P | Spatial-memory study | "strong age associations not moderated by body mass" 🟡 | **UPGRADED to ✅ (and larger than described)** | **6,753 dogs**; community scientists matched professionals; "decisive evidence for the model without the interaction"; *GeroScience* 48(1):1–16 | EPMC PMID 40993466 |
| 130 | D | Spatial transcriptomics trio | osteosarcoma Commun Biol 2026 ✅; glioma and MZL preprints 🟡 | **CONFIRMED** | All three DOIs resolve with the right types: *Commun Biol* 9(1) journal-article; the other two posted-content (Sep 2026) | Crossref |
| 131 | D | Zoonomia downloads and no dog-referenced projection | 240-species `.hal` + phyloP at cglgenomics.ucsc.edu; TOGA at senckenberg; licence unstated | **CONFIRMED** | The Data page confirms the 240-species Cactus `.hal` "made without reference to any single genome", TOGA annotation across the 240 species, and no stated licence | zoonomiaproject.org/the-data |
| 132 | D | Kowalczyk 2020, Christmas 2023, Ma 2016, Tyshkovskiy 2019/2023 citations | as written | **CONFIRMED (5)** | eLife 9:e51089; *Science* 380:eabn3943; eLife 5:e19130; *Cell Metab* 30(3):573–593; *Cell* 186(13):2929–2949 — and Tyshkovskiy 2023's abstract confirms "41 mammalian species", "downregulated Igf1", KU0063794 | Crossref; EPMC PMID 37269831 |
| 133 | D, T, P | Source-list integrity sweep | 323 entries across three files | **CONFIRMED** | 115 DOIs resolved via Crossref: 114 exact matches on journal, year and first author; 1 Crossref gap (Kang 2026) covered by EPMC. Preprints correctly typed as `posted-content`. **No fabrication, no mis-attribution** | api.crossref.org |

---

## Edits made

### `canine_data_resources.md` (20 edits)
1. Header status line → verified status.
2. TL;DR bullet 1 (DAP): Pack figure downgraded to 🟡; assay list upgraded to ✅; Terra/embargo downgraded to 🟡/❓.
3. TL;DR bullet 2 (Dog10K): confirmed, plus a **number-reconciliation note** for >48M vs 52.96M vs 34.6M.
4. TL;DR bullet 3: VetCompass downgraded to ❓ with calibration figures; GRLS figures itemised by confidence.
5. TL;DR bullet 4 (assemblies): Ensembl release corrected; chrY-contig nuance added; Beagle downgraded to ❓.
6. TL;DR bullet 6 (Evo 2): breed-set miscount corrected; **NTv3 caveat added**.
7. §1.1 Size row: Pack figure downgraded; **52,705 as of Dec 2025 added**.
8. §1.1 Genomics row: four figures upgraded to ✅ with the verbatim quote; **split corrected to 54.3/45.7**; CanFam4.0 added; PLINK/Terra downgraded to ❓.
9. §1.1 Access row: embargo and March timing downgraded; the confirmed parts separated out.
10. §1.1 clock bullet: HR and CI added; **preprint status and 49 deaths** added.
11. §1.1 GWAS bullet: scale figures added (298 loci, 957 followed, 11% died) and the "multifactorial" conclusion.
12. §1.3 Darwin's Ark: FAQ URL corrected; still ❓.
13. §1.4 VetCompass: downgraded to ❓ with two published denominators for calibration.
14. §1.4 Teng: confirmed verbatim.
15. §2.1 Meadows: structural-variant nuance; 1,929-sample panel, reference composition, EVA accession and filtered call set added.
16. §2.1 Dog10K DB: DOI added; **internal 52.96M-vs-34.6M inconsistency flagged**; 324-vs-321 breeds; age-series detail.
17. §2.2 table: four assembly rows rewritten (ROS_Cfam, Beagle, Jindo, dual assemblies) and mCanLor1.2 upgraded.
18. §2.3: UniProt confirmation; isoform-review note; **AFDB statistic un-inverted**; FTP count corrected to 48; second 404 added; **pLDDT reconciliation with `../01_alphafold`**; **alignment section rewritten with the mature-vs-precursor reconciliation**.
19. §3 table: consortium count corrected to 15,456; Horvath EWAS note; DoGA wolves/age-stratification corrected.
20. §4 table: Abood cohort detail; LeishDog publication status. §5: AnAge date conflict resolved, HAGR counts downgraded. §6: ICDC resolved via GraphQL + no-single-cell note; Cellosaurus upgraded. §7 table: ICDC and VetCompass rows. Open questions 1–8 rewritten + new item 8b. Sources 7, 28, 47, 58 corrected/completed. "Verification notes" appended.

### `ai_tools_for_dog_aging.md` (22 edits)
1. Header status line.
2. TL;DR bullet 1: mature-IGF1R figure added; recomputation confirmed.
3. TL;DR bullet 2: AlphaMissense/Hu & Xie confirmations.
4. TL;DR bullet 3: **"only frontier DNA model" corrected** with the NTv3 quote; GPN-Star's five species named.
5. TL;DR bullet 4: TranscriptFormer's 12 species listed, "24" downgraded, State's licence named precisely.
6. TL;DR bullet 5: EnsembleAge details; **DAP clock preprint/49 deaths**; **new array-vs-RRBS caveat**.
7. TL;DR bullet 6: Serres Armero quote confirmed verbatim with the second quote and pagination.
8. Master table — 14 rows edited: AF3, Boltz-2, Chai-1, **Chai-2 (no public access)**, RFdiffusion2/Foundry, ESM3/ESMC, GEMME, **Nucleotide Transformer v2 (dog absent + NTv3 note)**, Enformer (Apache-2.0), Geneformer, Arc State, TxGemma, Tahoe-100M (CC0/Vevo), Precious3GPT (CC-BY-NC-4.0), Robin (Apache-2.0), Kosmos (no repo).
9. §3: AlphaMissense and PrimateAI-3D confirmations; Hu & Xie scope clarified (per-tool values, 8 species/126 dog); **popEVE GPL-3.0 consequence added**.
10. §4 table: Evo 2 row rewritten; **new NTv3 row added**; NT v2 row corrected; GPN-Star alignment nuance. §4 closing paragraph: "only Evo 2" narrowed.
11. §5: CELLxGENE quote; TranscriptFormer MIT + "New Species" quote.
12. §6.1 table: Horvath EWAS note; DAP clock caveat.
13. §6.2: Tyshkovskiy 2026 and Gross 2026 confirmations with pagination.
14. §6.4: TRIAD quote confirmed.
15. Open questions 1–10 rewritten; **three new items added** (Tahoe composition, NTv3 track species, array-vs-RRBS).
16. "Verification notes" appended.

### `research_path_candidates.md` (23 edits)
1. Header status line.
2. TL;DR: Kraus quote confirmed; **cross-cutting array-vs-RRBS caveat added**.
3. **`Verifier comment:` added under all 18 proposals**, nine of which flag a material problem.
4. Open questions: item 2 (event counts) partly resolved; item 6 upgraded; items 8–9 refined; item 10 extended with three cross-file findings; **new item 11** (the clock-platform mismatch).
5. "Verification notes" appended.

---

## Proposal review — summary

| # | Verdict | Material problem found |
|---|---|---|
| 1 | **Material problem** | Step 1 not executable: array-based clocks (dual-species, universal) cannot be scored directly on DAP's RRBS data. Also: 864-dog clock is an unpublished preprint (49 deaths); GRLS replication is genotype-only, with no methylation in the open release. |
| 2 | Sound; licence/tooling warnings | popEVE is GPL-3.0 (copyleft inherited); GEMME has no findable repo; OMIA positives are Mendelian disease variants, not ageing variants. |
| 3 | **Material problem** | DoGA supplies no age contrast (9 dogs, not age-stratified); the real inputs are blood with n in the tens. Reframe as feasibility/placement. |
| 4 | **Material problem** | Wisdom Panel supplements cover only 250 pre-selected Mendelian variants — unusable for pathway burden. Breed n nearer 150 than 300. |
| 5 | **Material problem** | Three of six cited canid assemblies are scaffold-level (presence in OpenGenome2 ≠ alignment-grade); AnAge canid records sparse and the dog maximum is an outlier. |
| 6 | **Material problem** | **ICDC contains no single-cell data.** Also: LeishDog is now published; the fine-tuning base model sets the artefact's licence (State non-commercial vs TranscriptFormer MIT). |
| 7 | Sound; refinements | GPN-Star used bespoke 18–135-species alignments, not one 240-way; Cactus is reference-free so dog projection is real work; add NTv3 to the benchmark. |
| 8 | **Material problem** | The near-T2T Beagle assembly has no literature record, so its 34.90% repeat figure cannot anchor repeat annotation; use CanFam4 + Jindo. #8 and #1 share the same 864 samples. |
| 9 | Sound; improved | Event count partly answered: ~105 deaths among 957 followed dogs. Plan for ~100 events. |
| 10 | **Material problem** | Kosmos has no public repository (product dependency, not self-hostable); its 79.4% figure is an unreproduced self-report; VetCompass is not machine-readable. |
| 11 | Sound; refinement | Only the epigenetic layer has platform-matched human/dog data; expect wide intervals elsewhere. |
| 12 | Sound; protocol fix | Dog IGF1R's ~60-residue N-terminal extension is probably an annotation artefact — start at residue 89, verify against RefSeq; AF3 interface confidence is largely recall of 5U8Q/6PYH. |
| 13 | **Material problem** | Tahoe-100M is CC0 from Vevo (not "per Arc terms") and its stated composition is not in the dataset card; DrugAge count unverified. Put the canine-safety filter first. |
| 14 | **Material problem** | The HorvathMammalMethylChip40 is consortium-distributed, not a catalogue product — array access gates the project's main read-out and is not listed as a prerequisite. |
| 15 | Sound; better than described | DAP spatial-memory cohort is 6,753 dogs; brain-bank access is an assumption (preprint, no stated policy). |
| 16 | Sound as design-only | Added supporting evidence for the caution: Sohrab 2026 found GH-related metabolites carried *lower* mortality hazards and called canine ageing "multifactorial". |
| 17 | Sound | The one proposal using Wisdom Panel data appropriately. Flag that "lifespan load" is disease-variant load, not ageing-rate load. |
| 18 | **Clean — no change requested** | Verified as **ethics-flagged discussion only, with no technical protocol**: no target design, editing strategy, delivery route or embryo/germline methodology, and an explicit "I am not outlining how to do it". Its one citation (Zou et al. 2015, *J Mol Cell Biol* 7(6):580–583) is accurate. |

---

## Open issues

1. **VetCompass scale and licence.** rvc.ac.uk blocks both agents. The 1,800-practice / 28M-animal / 7.5M-dog / 200M-note figures have no opened source. Someone with institutional access should replace or delete them.
2. **DAP release mechanics.** The 1-year embargo, the March cadence and Terra hosting are all unconfirmed; dogagingproject.org returns no readable text to automated fetches.
3. **GEMME.** No current repository or licence could be found. The tool may have moved to GitLab or an institutional host.
4. **Beagle near-T2T assembly.** No literature record at all. Either the figshare entry must be opened or the row should be deleted.
5. **Dog coverage in Precious3GPT and in NTv3's 24 post-training track species.** Both gated or undocumented.
6. **TranscriptFormer's "24 embedding species".** Not reproducible from the current README; may have changed since the preprint.
7. **Tahoe-100M composition.** "50 lines / 379 molecules / 3 doses" needs re-derivation from the atlas paper.
8. **HAGR sub-database counts** (DrugAge 1,097, CellAge 866, LongevityMap 3,144, GenDR 214, GenAge model-organism 2,205) — none corroborated by the live pages.
9. **GEO record-level counts** for GSE223748 and GSE146920 remain CAPTCHA-blocked.
10. **Dog10K's internal SNV inconsistency** (52.96M vs 34.6M) should be raised with the authors; it affects anyone citing a Dog10K variant count.
11. **Whether the DAP DUA permits releasing model weights** trained on DAP data — gates proposals #1, #6 and #9 and is still unanswered.
12. **Zoonomia's specific statistics** (332 Mb/10.7% constrained, 4,552 UCEs, 101M constrained bases) were taken on trust from the abstract-level claim; I confirmed the paper and the download structure but not these individual figures.
13. **Harrison 2025 ptmAA details** ("~36% of metabolites show age effects", "kidney function mediates ~half") were not checked against the paper; the citation itself is confirmed.
14. **Kosmos's 79.4% accuracy** and **Kraus's "1 month per 2 kg"**-style press-derived figures remain self-reported or secondary.
15. **Jindo accessions and the Kidd "declines the T2T label" characterisation** were not verified.

---

## CROSS-FILE INCONSISTENCIES

Reported, not fixed — the sibling files belong to other verifiers. Items 1 and 2 have been **reconciled inside `06_ai_toolkit` with an explanation**, so no sibling edit is needed for them.

| # | Between | Inconsistency | Resolution |
|---|---|---|---|
| 1 | `06_ai_toolkit/canine_data_resources.md` + `ai_tools_for_dog_aging.md` vs `01_alphafold/how_to_use_alphafold.md` & `alphafold_and_dogs.md` | **IGF1R human↔dog identity: 97.4% vs 98.1%.** | **Not a conflict.** 97.4% = full-length precursor (1,323/1,359); 98.1% = mature receptor, human 31–1367 vs dog from residue 89 (1,312/1,337 = 98.13%). I recomputed both. The dog entry's ~60-residue N-terminal extension explains the gap. Both toolkit files now say so; the `01_alphafold` files already state the mature framing correctly. |
| 2 | Same pair | **Dog IGF-1 pLDDT: 55.19 vs 56.3.** | **Not a conflict.** 55.19 is the global pLDDT over 153 residues; 56.35 is the mature-domain (49–118) mean. Both recomputed from the same v6 confidence file. Explained in `canine_data_resources.md` §2.3. |
| 3 | `06_ai_toolkit` vs `03_canine_bio_ai/dog_foundation_models_landscape.md` | **Dog10K SNV count: ">48M variants" vs "52.96M SNVs".** | Both trace to real sources but the underlying **NAR paper contradicts itself** (Table 1: 52,963,969; text: "34.6 million"). ">48M" is the Genome Biology all-variant-type total. The toolkit file now carries the full reconciliation; the sibling verifier independently flagged the same inconsistency. **Neither file is wrong; both should name their source file.** |
| 4 | `06_ai_toolkit` (all three files) vs `03_canine_bio_ai` | **"Evo 2 is the only genomic LM with dog in training."** Both files made this claim; `03_canine_bio_ai` has been corrected by its verifier (NTv3). | I corrected it in all three toolkit files. **Now consistent across folders.** |
| 5 | `06_ai_toolkit/canine_data_resources.md` vs `03_canine_bio_ai` | **DoGA described as a regulatory atlas "including wolves".** The sibling verifier corrected the same error there. | Corrected here too: 24 wolves are in the **biobank**; the 2024 STRT2-seq atlas is 9 dogs + 12 embryos, no wolves. **Now consistent.** |
| 6 | `06_ai_toolkit` vs `04_dog_aging_biology/breed_size_genetics_lifespan.md` | **Horvath 2022 EWAS interpretation.** The toolkit files cite Horvath's EWAS as supporting the breed-weight↔lifespan story without naming genes; the breed file originally claimed *SMAD2*/*IGF1R* top hits and was corrected to *SF1*/*TTC8*. | Added a note in both toolkit files so the IGF-axis reading is not reintroduced. **Now consistent**, and the toolkit files never carried the wrong gene names. |
| 7 | `06_ai_toolkit` vs `04_dog_aging_biology` | **Dog10K "wolves have ~14% more variants".** The sibling files were corrected to "**structural** variants"; the toolkit file said "14% more" without the qualifier. | Qualifier added here. **Now consistent.** |
| 8 | `06_ai_toolkit` vs `04_dog_aging_biology` + `03_canine_bio_ai` | **McCoy 2024 tagged ✅/🟡 inconsistently across the dossier**, and the 49-death basis appeared only in the sibling files. | The preprint status and the 49 deaths are now stated in all three toolkit files. **Now consistent.** |
| 9 | `06_ai_toolkit/canine_data_resources.md` vs `03_canine_bio_ai` | **CanVAS is absent from the toolkit files.** The sibling documents a 2026 imputed canine variant atlas (15,451 dogs, 9.7M variants, CC-BY-4.0, Zenodo 19186944) that is arguably a better substrate for proposal #2 than Dog10K alone. | **Reported only** — a genuine gap in `06_ai_toolkit`, not an error. Worth adding when the files are next revised. |
| 10 | `06_ai_toolkit/ai_tools_for_dog_aging.md` vs `03_canine_bio_ai` | **Dog-specific imaging foundation models (VET-DINO, arXiv 2505.15248; V-REX, arXiv 2608.20069) are missing from the toolkit's tool table.** I confirmed both exist on arXiv (May 2025, Aug 2026). | **Reported only.** The toolkit file's scope is molecular/omics tools, so this is an omission rather than a contradiction, but a reader asking "what dog-ready models exist?" would want them. |
| 11 | `06_ai_toolkit` vs `03_canine_bio_ai` | **Wisdom Panel cohort size.** The toolkit file correctly says "1,054,293 dogs screened (from an existing cohort of 3.5 million)"; the sibling originally said ~1.1–1.2M and was corrected to 3.5M. | **No action** — `06_ai_toolkit` was right all along. |
| 12 | `06_ai_toolkit/canine_data_resources.md` vs `04_dog_aging_biology/wolves_vs_dogs.md` | **mCanLor1.2 confidence tags differ** (🟡 here, ✅ there). | Upgraded here to ✅ after reading the data note. **Now consistent.** |
| 13 | `06_ai_toolkit/research_path_candidates.md` (open question 10) | The file says its author had not read `04_dog_aging_biology` or `05_interventions`. Those files now exist and are verified. | Added a pointer to the three findings in them that bear on the proposal ranking. |
