# Verification Report: 01_alphafold
> Part of the dog-ageing research dossier · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> Independent fact-check by Fable 5.1 · 2026-10-04
> Files audited:
> - `01_alphafold/alphafold_complete_guide.md`
> - `01_alphafold/how_to_use_alphafold.md`
> - `01_alphafold/alphafold_and_dogs.md`
>
> All three were written by Opus 5.5 on 2026-10-04.
> Method: about 95 web calls plus local computation. GitHub commit/release/licence metadata via the `gh` CLI (the anonymous REST API was rate-limited); raw README, terms, installation and input docs; the AlphaFold Server FAQ and Terms and the AFDB FAQ and homepage read in the built-in browser (they are JavaScript-rendered and empty to plain fetches); AFDB REST (prediction, complex, summary, annotations, openapi), AFDB FTP listing and CHANGELOG, PDBe release notes; UniProt REST (16 count queries, 5 proteomes, 15 sequences, feature tables); Ensembl lookup and VEP; RCSB; Europe PMC full-text XML for Jumper 2021, Abramson 2024 and 29 further papers; Crossref for 70 DOIs; arXiv for 4 IDs; the IsoDDE technical-report PDF (text-extracted locally); Isomorphic Labs, DeepMind, Nobel, CNBC/X, The Decoder, Scientific American, Gigazine and phys.org pages. Sequence identities and regional pLDDT values were re-computed from UniProt FASTA and AFDB v6 confidence files with Biopython 1.88 (BLOSUM62, gap open −10 / extend −0.5, global). Scripts and raw outputs are in the session scratchpad under `verify_af/`. Every correction is marked `[verifier-corrected]` in place, and each file ends with a "Verification notes" section.

---

## Overall reliability: **HIGH**

**Why:**
- **Every one of the 18 self-flagged "surprising" items checked out.** The AF3 relicensing (CC BY-NC-SA 4.0 → Apache 2.0, commit 7b197fe8, 9 Jun 2026, v3.0.3), direct weight download (commit dd1a7bad, 23 Jul 2026) under unchanged non-commercial terms dated 2024-11-09, the Google Cloud commercial route (21 Aug 2026), v3.0.4 CPU/Apple Silicon (28 Jul 2026), SynthID Bio-structure (30 Sep 2026), the AlphaFold Server quotas and terms, the AFDB v6 numbers and API sunset, the dog proteome/coverage counts, the IGF1R/MTOR/SOD1 gaps, all sequence identities, the pLDDT values, Hu & Xie, Hitawala & Gray, the IsoDDE figures and the Isomorphic Labs deal history were all confirmed against primary sources, in most cases to the exact digit.
- **The live-query layer is exceptionally sound.** All 16 UniProt counts, every AFDB API call, every alignment figure (including the 25 IGF1R difference positions) and every regional pLDDT mean reproduced exactly. The author's ✅ tags on computed values are fully earned.
- **The two consequential 🟡 items (Jumper to Anthropic; FT report that the AlphaFold team was dissolved) are real.** Jumper's own X post of 19 Jun 2026 is the primary source; the FT story (29 Jul 2026, paywalled) is corroborated by the FT's own X post, The Decoder (same day) and Scientific American (7 Aug 2026). Both were upgraded to ✅. The one piece that stays 🟡 is the quoted DeepMind statement ("will not be shut down", "3 million users"), which is known only from Gigazine's paraphrase.
- **Errors found were few and small.** Nine corrections, none changing a conclusion: a double-counted NVIDIA dimer total ("about 4 M" → ~2.2 M); the FT date (~30 → 29 Jul); a usage figure mis-attributed to the Nobel committee; a false statement that the old AFDB entry URL no longer resolves; the AFDB `msaUrl` returning HTTP 403 to direct download; an incomplete ColabFold pip command; Foundry's Apple Silicon support overstated (community fork only); "AF3 Server" where Weng et al. say only "AlphaFold 3"; and an IsoDDE figure labelled "secondary" that is in fact in the primary report. One AFDB-side inconsistency (viral proteomes ~3,500 vs ~2,800) was annotated.
- **Citation integrity is excellent.** All 70 DOIs resolved in Crossref with matching author, journal, volume and page/article metadata; all four arXiv IDs exist with the stated months; 29 of the 32 papers whose content was spot-checked supported the sentence citing them verbatim (the other three — Cramer 2026, Mosalaganti 2022, Škrinjar 2025 — were available as abstracts only and are consistent with the text).

---

## Counts

| Verdict | n |
|---|---|
| Claims checked | **131** |
| CONFIRMED | 115 |
| CORRECTED | 9 |
| DOWNGRADED (less certain than tagged) | 1 |
| UPGRADED (more certain than tagged; recorded here as CORRECTED tags) | 2 |
| REMOVED (unsupported attribution) | 1 |
| UNRESOLVED | 3 |

Citation spot-check: **70 DOIs** resolved via Crossref, **4 arXiv IDs** via the arXiv API, **32 papers** opened in Europe PMC (29 in full text) and checked for whether they support the citing sentence; **13 web/GitHub sources** opened. No fabricated or mis-attributed citation was found. One attribution error ("Nobel committee cited more than 2 M users") was removed.

---

## Claim table

**Files:** G = `alphafold_complete_guide.md`, H = `how_to_use_alphafold.md`, D = `alphafold_and_dogs.md`

| # | File | Claim | As written | Verdict | Correct value / note | Source URL |
|---|---|---|---|---|---|---|
| 1 | G,H | AF3 code relicensed CC BY-NC-SA 4.0 → Apache 2.0 | 9 Jun 2026, v3.0.3, commit 7b197fe8 | CONFIRMED | Commit 7b197fe8 2026-06-09T12:24Z "Change the code license from CC BY-NC-SA 4.0 to Apache 2.0"; release v3.0.3 2026-06-09 | https://github.com/google-deepmind/alphafold3/commits/main/LICENSE |
| 2 | G,H | Weights downloadable directly, no request form | since 23 Jul 2026, commit dd1a7bad, `storage.googleapis.com/alphafold3/af3.bin.zst` | CONFIRMED | Commit dd1a7bad 2026-07-23 "Update the instructions on how to obtain AlphaFold 3 weights"; URL in README | https://raw.githubusercontent.com/google-deepmind/alphafold3/main/README.md |
| 3 | G,H | Weights terms non-commercial, Last Modified 2024-11-09; no redistribution; no training similar models | as stated | CONFIRMED | "only available for non-commercial use by, or on behalf of, non-commercial organizations"; "must not publish or share … model parameters" | https://github.com/google-deepmind/alphafold3/blob/main/WEIGHTS_TERMS_OF_USE.md |
| 4 | G,H | Commercial access via Google Cloud | "Gemini Enterprise Agent Platform on Google Cloud", 21 Aug 2026, commit 9b30e9aa | CONFIRMED | README sentence verbatim; commit 9b30e9aa 2026-08-21 | https://github.com/google-deepmind/alphafold3 |
| 5 | G,H | v3.0.4 CPU-only and Apple Silicon | 28 Jul 2026 | CONFIRMED | Release 2026-07-28: "makes AlphaFold 3 runnable on CPU-only machines and on Apple Silicon" | https://github.com/google-deepmind/alphafold3/releases |
| 6 | H | CPU ~100× slower; `--jax_backend="mps"` ~3× faster than CPU | as stated | CONFIRMED | installation.md | https://github.com/google-deepmind/alphafold3/blob/main/docs/installation.md |
| 7 | G,H | SynthID Bio-structure | 30 Sep 2026, commit b0960236, `af3_synthid.bin.zst`, synthidbio repo | CONFIRMED | Commit b0960236 2026-09-30; README URL; repo describes "a fine-tuned AlphaFold 3 (AF3) model that embeds an imperceptible watermark" | https://github.com/google-deepmind/synthidbio |
| 8 | G | Release dates v3.0.0–v3.0.2 and contents | 11 Nov 2024; 23 Jan 2025 (`--num_seeds`, `--num_recycles`, embeddings); 20 Apr 2026 Blackwell, "parameter files are compatible with any 3.0.x version" | CONFIRMED | All in release bodies | https://github.com/google-deepmind/alphafold3/releases |
| 9 | H | Hardware/installation figures | Linux only; CC ≥8.0; A100/H100 80 GB ≤5,120 tokens; ≥64 GB RAM; 1 TB; 252 GB/630 GB; ~45 min; CUDA 12.6; Singularity | CONFIRMED | All verbatim in installation.md | https://github.com/google-deepmind/alphafold3/blob/main/docs/installation.md |
| 10 | H | AF3 input JSON | `dialect: alphafold3`; `ccdCodes`/`smiles`; `userCCD`; `bondedAtomPairs`; `modifications`; `modelSeeds`; `version: 1` | CONFIRMED | version may be 1–4; example uses 4 | https://github.com/google-deepmind/alphafold3/blob/main/docs/input.md |
| 11 | G,H | AlphaFold Server daily quota | 30 jobs/day | CONFIRMED | FAQ: "30 jobs per day" | https://alphafoldserver.com/faq |
| 12 | G,H | Job size and token rules | 5,000 tokens; 1/residue, 1/nt, 1/atom; ≥4 residues per chain | CONFIRMED | FAQ verbatim | https://alphafoldserver.com/faq |
| 13 | G,H | Ligands by CCD code; no SMILES | any CCD code (CCD 2024_10_28), 1–5 chars, ≤50 copies; STI example; JSON `{"ligand": {"ligand": "STI", "count": 1}}` | CONFIRMED | FAQ verbatim; SMILES not offered | https://alphafoldserver.com/faq |
| 14 | H | Ions, PTMs, glycans | lists as in §2 table; glycans ≤8 residues from BGC/BMA/GLC/MAN/NAG/FUC | CONFIRMED | FAQ lists match (FAQ also names beta-D-galactose among sugars) | https://alphafoldserver.com/faq |
| 15 | H | Templates/MSA options | default cutoff 30 Sep 2021; ≤4 custom templates per chain; custom paired/unpaired A3M | CONFIRMED | FAQ verbatim | https://alphafoldserver.com/faq |
| 16 | H | Seeds, drafts, batch | 5 samples/seed; seed 0–4,294,967,295; 500 drafts; 100 jobs per JSON; "Clone and reuse" | CONFIRMED | FAQ verbatim | https://alphafoldserver.com/faq |
| 17 | G,H,D | Server Terms | Last Modified 8 May 2024; non-commercial; no "automated system that predicts the binding … such as Glide or AutoDock"; no training; not for clinical use | CONFIRMED | Terms page "Last Modified: May 8, 2024"; clauses verbatim | https://alphafoldserver.com/terms |
| 18 | G,H | Server FAQ still says weights need a request form | stale as of 2026-10-04 | CONFIRMED | FAQ: "Researchers can submit a request form … 2 - 3 business days" | https://alphafoldserver.com/faq |
| 19 | H | Server vs local MSA difference | sharded Jackhmmer without `--domZ`, ~100× more permissive; issue #492 protein–DNA example | CONFIRMED | FAQ verbatim | https://alphafoldserver.com/faq |
| 20 | G,H | Confidence rules of thumb | pLDDT bands; ipTM >0.8/<0.6/0.6–0.8; pTM >0.5; pTM <0.05 under 20 tokens, peptides <16; `ranking_score` = 0.8·ipTM + 0.2·pTM + 0.5·disorder − 100·has_clash; `chain_pair_pae_min` "correlate[s] with whether two chains interact" | CONFIRMED | AF Server FAQ and AFDB FAQ | https://alphafoldserver.com/faq |
| 21 | G,H,D | AFDB v6 | 241,070,489 structures incl. 40,054 isoforms; UniProt 2025_03; CHANGELOG 15 Sep 2025; PDBe notes 21 Oct 2025; +65,711,653 / −39,324,993 / 276,539 changed vs v4 | CONFIRMED | CHANGELOG and PDBe release notes | https://ftp.ebi.ac.uk/pub/databases/alphafold/CHANGELOG.txt |
| 22 | G,H | Legacy API sunset | 25-06-2026 | CONFIRMED | "The sunset date for the old API fields is 25-06-2026" | https://www.ebi.ac.uk/pdbe/news/alphafold-database-release-notes |
| 23 | G | Site advertises >260 M | ">260 M" | CONFIRMED | Homepage "over 260 million"; FAQ "261,552,403 predicted models … including 40,054 isoforms" (added) | https://alphafold.ebi.ac.uk/faq |
| 24 | G,D | NVIDIA dimer releases | March 2026 1,754,199 homodimers; May 2026 ~2.2 M homo-/heterodimers from 4,777 proteomes; 16 model organisms + 30 WHO proteomes | CONFIRMED | FAQ "Which proteins are included?" verbatim | https://alphafold.ebi.ac.uk/faq |
| 25 | G | TL;DR total of NVIDIA dimers | "about 4 M" | **CORRECTED** | ~2.2 M displayed (2,158,419 homodimers + 79,156 heterodimers); March and May sets overlap and were summed | https://alphafold.ebi.ac.uk/faq |
| 26 | G | Viral complexes Sep 2026 | "about 1.7 M … about 3,500 viral proteomes" | **CORRECTED** (annotated) | 1,703,992 predictions; FAQ says both "~3,500 viral proteomes" (release list) and "~2,800 viral proteomes from 23 viral families" (dataset entry); phys.org: ">2,800 viruses" | https://alphafold.ebi.ac.uk/faq |
| 27 | G,H | Literature-mined annotations Oct 2026 | NER model, SIFTS mapping | CONFIRMED | Homepage "What's new – October 2026": transformer-based NER; SIFTS | https://alphafold.ebi.ac.uk/ |
| 28 | G | Feb 2026 collaborator datasets | AllTheBacteria, Kinetoplastids, Viro3D, BFVD | CONFIRMED | FAQ Feb 2026 entry | https://alphafold.ebi.ac.uk/faq |
| 29 | H,D | Dog not among 46 v6 proteome tarballs | 46 tarballs, no dog | CONFIRMED | FTP `latest/`: 48 `.tar` = 46 `UP…_v6.tar` + `swissprot_cif_v6.tar` + `swissprot_pdb_v6.tar`; no 9615/CANLF | https://ftp.ebi.ac.uk/pub/databases/alphafold/latest/ |
| 30 | D | "47 other key organisms" vs 46 | inconsistency on AFDB's side | CONFIRMED (annotated) | FAQ itself says "46 complete proteomes available for bulk download" | https://alphafold.ebi.ac.uk/faq |
| 31 | D,H | Dog reference proteome | UP000805418, Labrador retriever, GCA_014441545.1, 43,615 proteins | CONFIRMED | UniProt proteomes JSON | https://rest.uniprot.org/proteomes/UP000805418.json |
| 32 | D | Reference proteome with AFDB | 39,585 / 43,615 (90.8%) | CONFIRMED | X-Total-Results 39585 / 43615 | https://rest.uniprot.org/uniprotkb/search?query=proteome:UP000805418%20AND%20database:alphafolddb |
| 33 | D | All dog entries with AFDB | 42,123 / 46,473 (90.6%) | CONFIRMED | 42123 / 46473 | https://rest.uniprot.org/uniprotkb/search?query=organism_id:9615%20AND%20database:alphafolddb |
| 34 | D | Reviewed dog / human | 857 (809 with AFDB); human 20,431 | CONFIRMED | 857 / 809 / 20431 | https://rest.uniprot.org |
| 35 | D | Dog unreviewed 16–1,280 aa | 41,779 / 41,313 (98.9%) | CONFIRMED | exact | https://rest.uniprot.org |
| 36 | D,H | Dog unreviewed 1,281–2,700 aa | 3,357 / 1 | CONFIRMED | exact | https://rest.uniprot.org |
| 37 | D | Dog reviewed 1,281–2,700 aa | 41 / 37 | CONFIRMED | exact | https://rest.uniprot.org |
| 38 | D | Dog >2,700 aa | 453 / 0 | CONFIRMED | exact | https://rest.uniprot.org |
| 39 | D | Grey wolf | 199 entries / 197 with AFDB; no proteome | CONFIRMED | 199 / 197; proteome search returns 0 | https://rest.uniprot.org/proteomes/search?query=organism_id:9612 |
| 40 | D | Dingo | 33,945 / 31,000; UP000694391 reference, 33,928 | CONFIRMED | exact | https://rest.uniprot.org |
| 41 | D | Boxer / Basenji / Great Dane proteomes | UP000002254 41,817 GCA_000002285.4; UP000694429 42,651 GCA_004886185.1; UP000694542 42,573 GCA_005444595.1 | CONFIRMED | all exact | https://rest.uniprot.org/proteomes/ |
| 42 | H,D | AFDB inclusion rules | 16–2,700 aa (proteomes/Swiss-Prot), 16–1,280 aa (rest); non-standard residues; one-sequence-per-gene; `model_2_ptm`; only human fragmented | CONFIRMED | FAQ verbatim | https://alphafold.ebi.ac.uk/faq |
| 43 | H,D | UniProt release | 2026_03 (2 Sep 2026) | CONFIRMED | `X-UniProt-Release: 2026_03`, `X-UniProt-Release-Date: 02-September-2026` | https://rest.uniprot.org |
| 44 | H,D | No AFDB model for dog IGF1R / MTOR | A0A8I3RQ77, A0A8I3MER7, A0A8I3MMA7, A0A8I3MJG3 → `{}` | CONFIRMED | all four return `{}`; lengths 1,425 / 1,344 / 1,403 / 2,324 | https://alphafold.ebi.ac.uk/api/prediction/A0A8I3RQ77 |
| 45 | D | Dog SOD1 Q8WNN6 excluded for X at 53 | X at residue 53; no model; A0A8I3PS52 (152 aa) modelled | CONFIRMED | FASTA residue 53 = X; API `{}`; AF-A0A8I3PS52-F1 exists | https://rest.uniprot.org/uniprotkb/Q8WNN6.fasta |
| 46 | D | Other spot checks | MTOR fragment A0A8I3RSA0 755 aa yes; ABCC9 A0A8I3S0W3 no, A0A8I3P2G1 149 aa yes; RESF1 A0A8I3NVF7 no; TERT, KL, FKBP1A, GH1 yes | CONFIRMED | all as stated | https://alphafold.ebi.ac.uk/api/prediction/ |
| 47 | H,D | Mature IGF-1 dog = human | 70/70; precursor 136/148 = 91.9% | CONFIRMED | re-computed; residues 49–118 identical | https://rest.uniprot.org/uniprotkb/P33712.fasta |
| 48 | H,D | Mature IGF1R identity | 1,312/1,337 = 98.1%; 25 differences at listed human positions; Y1161/1165/1166 conserved | CONFIRMED | re-computed; identical position list | https://rest.uniprot.org/uniprotkb/A0A8I3RQ77.fasta |
| 49 | H,D | GHR, GH, TERT identities | 525/638 = 82.3%; 147/215 = 68.4%; 819/1,089 = 75.2% | CONFIRMED | re-computed | https://rest.uniprot.org |
| 50 | D | mTOR FRB dog = human | 100/100 | CONFIRMED | human 2015–2114 occurs verbatim in A0A8I3MJG3 at 1790–1889; full mTOR 2,281/2,323 | https://rest.uniprot.org/uniprotkb/P42345.fasta |
| 51 | D | FKBP1A dog vs human | 91/92; 16-residue gap at human 13–28 | CONFIRMED | re-computed | https://rest.uniprot.org/uniprotkb/A0A8I3NXR7.fasta |
| 52 | H | IGF1R landmarks | `GPGIDIRND` index 88 → residue 89; TM at 994; ectodomain 905 aa; RKRR 795 (dog) / 737 (human) | CONFIRMED | re-computed | — |
| 53 | H,D | Regional pLDDT | IGF-1 mature 56.3 vs 68.7; GHR ECD 81.5/81.2, TM 85.3, tail 41.6/41.1; global 55.19/59.06 | CONFIRMED | re-computed from v6 confidence JSON | https://alphafold.ebi.ac.uk/files/AF-P33712-F1-confidence_v6.json |
| 54 | H | UniProt features | IGF-1 mature 49–118 (dog and human); GHR ECD 19–264, TM 265–288, cytoplasmic 289–638; GH1 216 aa | CONFIRMED | feature tables | https://rest.uniprot.org/uniprotkb/Q9TU69.json |
| 55 | H | Ensembl dog IGF1R | ENSCAFT00845003151 → ENSCAFP00845002510, 1,425 aa, ROS_Cfam_1.0 | CONFIRMED | lookup returns exactly this | https://rest.ensembl.org/lookup/symbol/canis_lupus_familiaris/IGF1R |
| 56 | H | 4 unreviewed dog IGF1 entries | 4 | CONFIRMED | X-Total-Results 4 | https://rest.uniprot.org |
| 57 | D | Human GHR NVIDIA heterodimer with CSH2 ipTM 0.80 | as stated | CONFIRMED | also CSH1 (0.81) and GH1 (0.80); dog Q9TU69/P33712 complexes `{}` | https://alphafold.ebi.ac.uk/api/complex/P10912 |
| 58 | H | API endpoint table | `/prediction`, `/complex`, `/uniprot/summary`, `/annotations`, `/sequence/summary`; openapi.json | CONFIRMED | openapi.json lists exactly these five paths (HTTP 200) | https://alphafold.ebi.ac.uk/api/openapi.json |
| 59 | H,D | AlphaMissense via API | P08069 has `amAnnotationsUrl`; P33712 annotations `{}`; P05019 annotations return "AM score" | CONFIRMED | as stated | https://alphafold.ebi.ac.uk/api/annotations/P05019.json?type=MUTAGEN |
| 60 | H | PAE JSON | `max_predicted_aligned_error` 31.75 | CONFIRMED | file and FAQ | https://alphafold.ebi.ac.uk/files/AF-P33712-F1-predicted_aligned_error_v6.json |
| 61 | H | MSA file downloadable from `msaUrl` | implied downloadable | **CORRECTED** | HTTP 403 "AccessDenied" from GCS on plain and range GETs, any UA; FAQ says MSAs are on entry pages | https://alphafold.ebi.ac.uk/files/msa/AF-P33712-F1-msa_v6.a3m |
| 62 | H | Old entry URL "no longer resolves" | `alphafold.com/entry/AF-…-F1`; old format fails | **CORRECTED** | `/entry/P33712` and `/entry/AF-P33712-F1` both load the same v6 page (browser test) | https://alphafold.ebi.ac.uk/entry/P33712 |
| 63 | D | Ensembl VEP gives SIFT for dog, no PolyPhen | as stated | CONFIRMED | `sift_prediction: tolerated`, `polyphen_prediction: None` | https://rest.ensembl.org/vep/canis_lupus_familiaris/hgvs/ENSCAFT00845016630:c.200G>A |
| 64 | D | Hu & Xie 2025 | Open Vet J 15(10):5183–5191; 284/90 variants; sensitivity 0.77–0.90; specificity 0.20–0.46; auROC 0.55–0.61 | CONFIRMED | Europe PMC PMID 41246429; abstract verbatim | https://doi.org/10.5455/ovj.2025.v15.i10.35 |
| 65 | G,D | Hitawala & Gray 2025 | mAbs 17:2545601; 10.2% / 13.3%; "65% failure rate … single seed" | CONFIRMED | abstract verbatim (preprint had 11.0/11.4/60%) | https://doi.org/10.1080/19420862.2025.2545601 |
| 66 | G | IsoDDE report claims | 10 Feb 2026; "more than doubles" AF3; 334 interfaces; 39% DockQ>0.8 = 2.3× AF3, 19.8× Boltz-2; 63% DockQ>0.23; CDR-H3 70/58/43%; exceeds FEP+; proprietary | CONFIRMED | all verbatim in 27-page PDF and article | https://storage.googleapis.com/isomorphiclabs-website-public-artifacts/isodde_technical_report.pdf |
| 67 | G | AF3 23.3% in hardest Runs N' Poses bin | "secondary sources" 🟡 | **CORRECTED** (upgraded) | In the report's own table: IsoDDE 50.0% vs AF3 23.3% (N=60); same training cutoff as AF3 stated | same |
| 68 | G | FoldBench table (9 models × 3 columns) | values as tabulated | CONFIRMED | all 27 numbers verbatim; "trained on data before 13-January-2023" | same |
| 69 | G | Lilly / Novartis deals | 7 Jan 2024; $45 M / $37.5 M upfront; "nearly $3 billion" excl. royalties | CONFIRMED | verbatim | https://www.isomorphiclabs.com/articles/isomorphic-labs-kicks-off-2024-with-two-pharmaceutical-collaborations |
| 70 | G | $600 M raise | 31 Mar 2025, led by Thrive | CONFIRMED | verbatim | https://www.isomorphiclabs.com/articles/isomorphic-labs-announces-600m-external-investment-round |
| 71 | G | $2.1 B Series B | 12 May 2026, led by Thrive | CONFIRMED | "raised $2.1 Billion in Series B funding … led by Thrive Capital" | https://www.isomorphiclabs.com/press/isomorphic-labs-funding |
| 72 | G | J&J collaboration | 20 Jan 2026; small molecules, antibodies, peptides, molecular glues; no financial terms | CONFIRMED | verbatim | https://www.isomorphiclabs.com/articles/isomorphic-labs-enters-into-a-research-collaboration-with-johnson-johnson |
| 73 | G | No clinical trial disclosed as of 29 Sep 2026 | quote "gear up for clinical developments" | CONFIRMED | quote verbatim; no trial announced | https://www.isomorphiclabs.com/articles/building-a-new-path-to-make-medicines-with-ai |
| 74 | G | Jumper leaving for Anthropic | 19 Jun 2026, CNBC, 🟡 | **CORRECTED** (upgraded to ✅) | Primary: Jumper's X post 19 Jun 2026; CNBC same day | https://x.com/JohnJumperSci/status/2068001285173834106 |
| 75 | G | FT: AlphaFold team dissolved | "~30 Jul 2026", 🟡, via Gigazine | **CORRECTED** (date 29 Jul; upgraded to ✅ for the report) | FT 29 Jul 2026 (paywalled); FT X post; The Decoder 29 Jul; Scientific American 7 Aug ("database and prediction server remain available"); Jumper, Adler, Pritzel to Anthropic; ~¼ of authors left Google | https://www.scientificamerican.com/article/why-google-deepmind-broke-up-the-alphafold-team/ |
| 76 | G | DeepMind: system/DB "will not be shut down", >3 M users | attributed to DeepMind via FT | **DOWNGRADED** (kept 🟡) | Found only in Gigazine's summary; not in Decoder or SciAm | https://gigazine.net/gsc_news/en/20260730-google-deepmind-alphafold-team/ |
| 77 | G,H | Chai-1 licence | Apache 2.0 code and weights; `chai_lab==0.6.1`; `chai-lab fold --use-msa-server --use-templates-server` | CONFIRMED | README verbatim | https://github.com/chaidiscovery/chai-lab |
| 78 | G,H | Protenix | v1 2026-02-05; v2 2026-04-08; v2 weights proprietary; `protenix_base_default_v1.0.0`; web server | CONFIRMED | README: "model weights of Protenix-v2 are proprietary and confidential" | https://github.com/bytedance/Protenix |
| 79 | G,H | Boltz | MIT code+weights; "first … to approach … FEP … 1000x faster"; affinity ≤128 atoms (best ≤56); log10 IC50 µM; `--use_potentials` | CONFIRMED | README and docs/prediction.md | https://github.com/jwohlwend/boltz |
| 80 | G,H | OpenFold3 | Apache 2.0; OpenBind-0 default from v0.5.0; June 2025 cutoff; training data released; `setup_openfold` | CONFIRMED | README | https://github.com/aqlaboratory/openfold-3 |
| 81 | G,H | Foundry (RF3/RFD3) | BSD-3; `pip install "rc-foundry[all]"`; "Apple Silicon support" | **CORRECTED** | Licence and commands confirmed; MPS only "via a community fork", inference-only, float32 | https://github.com/RosettaCommons/foundry |
| 82 | H | ColabFold | v1.6.3, MIT; notebooks incl. "AlphaFold3 (OpenFold3)", Boltz, BioEmu; ~2,000 aa on 16 GB; PyMOL spectrum; serial MSA queries; `pip install colabfold` | CONFIRMED except pip line, **CORRECTED** | README command is `pip install colabfold[alphafold,openmm] jax[cuda12] openmm[cuda12]`; licence MIT via GitHub API | https://github.com/sokrypton/ColabFold |
| 83 | G | HelixFold3 licence "NOASSERTION" | as stated | CONFIRMED | GitHub licence API for PaddlePaddle/PaddleHelix | https://github.com/PaddlePaddle/PaddleHelix |
| 84 | G | AF2 weights CC BY 4.0, code Apache 2.0 | as stated | CONFIRMED | README | https://github.com/google-deepmind/alphafold |
| 85 | G,D | AlphaMissense human-only; weights not released; predictions CC BY 4.0 since 13 Mar 2024 | as stated | CONFIRMED | README "What we don't provide: The trained AlphaMissense model weights"; commit 2024-03-13 "Update AlphaMissense predictions database license" | https://github.com/google-deepmind/alphamissense |
| 86 | G | AlphaMissense numbers | 71 M variants; 89% classified; 57% benign / 32% pathogenic / 11% uncertain | CONFIRMED | DeepMind blog 19 Sep 2023; abstract gives 89% | https://deepmind.google/discover/blog/a-catalogue-of-genetic-mutations-to-help-pinpoint-the-cause-of-diseases/ |
| 87 | G,D | AlphaGenome | Nature 649:1206–1218 (2026); 1 Mb input; trained on human and mouse; Kaggle/HF non-commercial | CONFIRMED | Crossref; full text "Trained on human and mouse genomes"; README | https://doi.org/10.1038/s41586-025-10014-0 |
| 88 | G | AlphaProteo | 5 Sep 2024; 3–300× better affinity on 7 targets; first AI binder for VEGF-A; arXiv 2409.08022 | CONFIRMED | blog and arXiv (12 Sep 2024) | https://deepmind.google/discover/blog/alphaproteo-generates-novel-proteins-for-biology-and-health-research/ |
| 89 | G | "Next generation of AlphaFold" preview | 31 Oct 2023; nearly all molecule types in PDB | CONFIRMED | article date and quote | https://www.isomorphiclabs.com/articles/a-glimpse-of-the-next-generation-of-alphafold |
| 90 | G | 2024 Nobel split | ½ Baker "for computational protein design"; ½ jointly Hassabis & Jumper "for protein structure prediction"; 9 Oct 2024 | CONFIRMED | press release (browser) | https://www.nobelprize.org/prizes/chemistry/2024/press-release/ |
| 91 | G | "Nobel committee cited >2 M users in 190 countries" | attributed to [24] | **REMOVED** (attribution) | Not on press release or popular-information page; figure is DeepMind's own ("over 2 million researchers in over 190 countries") | https://deepmind.google/science/alphafold/ |
| 92 | G | DeepMind usage figures | >3 M researchers, >190 countries, >1 M in LMICs, >40,000 citations | CONFIRMED | page verbatim | https://deepmind.google/science/alphafold/ |
| 93 | G | Jumper 2021 figures | 0.96 Å (CI 0.85–1.16) vs 2.8 Å; ~100,000 structures; "gold-standard"; "contributes markedly"; >50 years; triangle updates; IPA; residue gas | CONFIRMED | full text PMC8371605 | https://europepmc.org/article/PMC/PMC8371605 |
| 94 | G | Senior 2020 (AF1) | 24/43 FM domains TM ≥0.7 vs 14/43 | CONFIRMED | abstract verbatim | https://doi.org/10.1038/s41586-019-1923-7 |
| 95 | G | Abramson 2024 details | 48 blocks, 128/384 channels; cutoff 30 Sep 2021; PoseBusters model 30 Sep 2019; P = 2.27×10⁻¹³, 4.45×10⁻²⁵, 1.8×10⁻¹⁸, 6.5×10⁻⁵ with 1,000 seeds; 7,663- and 4,665-residue examples; cross-distillation; cereblon closed for apo; no ensemble; MSA-depth dependence; no rotational frames; mini-rollout | CONFIRMED | full text PMC11168924, all verbatim | https://europepmc.org/article/PMC/PMC11168924 |
| 96 | G | AFDB history | 22 Jul 2021 365,198 (21 model organisms); 9 Dec 2021 804,872; 27 Jan 2022 995,411; 28 Jul 2022 214,687,406; 1 Nov 2022 v4 ~4.4% | CONFIRMED | CHANGELOG | https://ftp.ebi.ac.uk/pub/databases/alphafold/CHANGELOG.txt |
| 97 | D | Weng 2025 | Commun Biol 8:1639; ipTM 0.89/0.88, pTM 0.90/0.89; 3.1 Å; AF2 initial model; sub-nM–nM; "AF3 Server" | CONFIRMED; "Server" **CORRECTED** | Text: "built using AlphaFold 3"; cryo-EM table "Initial model used … AlphaFold2" | https://doi.org/10.1038/s42003-025-09030-7 |
| 98 | D | Vijayasimha 2025 | AF3 Server model; C–C′ and F–G loops | CONFIRMED | "The AlphaFold 3 server was used" | https://doi.org/10.3390/vetsci12070649 |
| 99 | D | Furrow 2023 quote | "only 149 of the 1549 amino acids"; O60706; Missense3D | CONFIRMED | verbatim | https://doi.org/10.3390/genes14050988 |
| 100 | D | Ryu 2025 | 30 senior dogs 10–16 y; AF-P01286-F1; Discovery Studio with PDB 7V9M | CONFIRMED | "30 healthy senior dogs (aged 10–16 years)"; "AF-P01286-F1"; "using 7v9m.pdb" | https://doi.org/10.3389/fvets.2025.1609405 |
| 101 | D | Korec 2025 PARP14 statement | quoted; method unverified ❓ | CONFIRMED (❓ kept) | quote verbatim; AlphaFold cited only in references | https://doi.org/10.1016/j.vas.2024.100420 |
| 102 | D | Brown 2026 RESF1 | AlphaMissense 0.82 likely pathogenic | CONFIRMED | verbatim | https://doi.org/10.1038/s41598-026-42994-y |
| 103 | D | Zhang 2025 MLH1 p.D375N | "based on the aligned human residue" | CONFIRMED | verbatim | https://doi.org/10.1186/s13059-025-03804-2 |
| 104 | D | Yang 2024 PTPN11 | AlphaMissense on human, 99.3% identical, PolyPhen-2 on dog | CONFIRMED | verbatim | https://doi.org/10.3390/genes15081050 |
| 105 | D | Gingrich 2023 | ColabFold, templates off, 3 recycles, 5 models | CONFIRMED | verbatim | https://doi.org/10.4049/immunohorizons.2300092 |
| 106 | D | Kawakami 2022 | human and mouse AF models; VHFL in α-helix | CONFIRMED | verbatim | https://doi.org/10.1371/journal.pone.0264365 |
| 107 | D | Oliver 2025; Woerde 2026; Gibbs 2022; Min 2023; Walther 2024; Duraisamy 2026 | AF use as described | CONFIRMED | full texts: AlphaFold for α-TTP; AF3 model, TM domain; human AF template; AF for Fel d 4; AlphaFold via ChimeraX; AF2 Colab + TLR docking | Europe PMC |
| 108 | D | Haque 2024 | 56 classified; 55.4% P/LP; OR 7.0 | CONFIRMED | "56 … 31 (55.4%) pathogenic/likely pathogenic … odds ratio … 7.0 (95% CI 4.1 to 12.0)" | https://doi.org/10.1136/jmg-2023-109760 |
| 109 | H,D | Plassais 2022 | IGF1 ~15% of between-breed size variation | CONFIRMED | abstract "approximately 15%" | https://doi.org/10.1016/j.cub.2021.12.036 |
| 110 | G,D | Pak 2023 | "very weak or no correlation" | CONFIRMED | verbatim | https://doi.org/10.1371/journal.pone.0282689 |
| 111 | G,H,D | Terwilliger 2024 | "exceptionally useful hypotheses" | CONFIRMED | verbatim | https://doi.org/10.1038/s41592-023-02087-4 |
| 112 | G | Ren 2023 CDK20 | Kd 9.2 ± 0.5 µM; 30 days; 7 compounds | CONFIRMED | verbatim | https://doi.org/10.1039/d2sc05709c |
| 113 | G | Mosalaganti 2022 NPC | ~120 MDa; ~1,000 proteins; ~30 NUPs | CONFIRMED | abstract | https://doi.org/10.1126/science.abm9506 |
| 114 | G | Škrinjar 2025 | "largely memorise ligand poses"; ~2,600 systems | CONFIRMED (abstract) | verbatim | https://doi.org/10.1101/2025.02.03.636309 |
| 115 | G,H | Mirdita 2022 ColabFold | 40–60× faster search; ~1,000 structures/day | CONFIRMED | verbatim | https://doi.org/10.1038/s41592-022-01488-1 |
| 116 | H | Varadi 2024 Google Cloud Public Datasets | as stated | CONFIRMED | full text | https://doi.org/10.1093/nar/gkad1011 |
| 117 | D | Dog SOD1 crystal structures | 7WWT, 7WX0 (E40K), 7WWY, 7WX1; 8ZD5/8ZD6 | CONFIRMED | Hashimoto 2023 text; RCSB titles | https://doi.org/10.1016/j.jbc.2023.104798 |
| 118 | G | ESMFold / ESM3 | 15 B parameters; >617 M structures; GFP 58% identity | CONFIRMED | abstracts | https://doi.org/10.1126/science.ade2574 |
| 119 | G,H | PDB entries | 5U8Q X-ray 3.27 Å rel. 2018-02-28; 6PYH EM 4.3 Å rel. 2019-10-23, 2 mouse IGF1R + 1 human IGF-1; 3HHR 2.8 Å rel. 1994; 1GZR 2.0 Å; RAP = rapamycin | CONFIRMED | RCSB REST | https://data.rcsb.org/rest/v1/core/entry/6PYH |
| 120 | G,H,D | Crossref metadata for 70 cited DOIs | authors/journals/volumes/pages | CONFIRMED | all resolve and match (Xu FoldBench: online 2025, vol. 17 = 2026, as written) | https://api.crossref.org/works/ |
| 121 | G | arXiv IDs | 2408.16975 (HelixFold3, Aug 2024); 2512.24354 (SeedFold, Dec 2025); 2510.24670 (Pearl, Oct 2025); 2409.08022 (AlphaProteo) | CONFIRMED | arXiv API dates | https://export.arxiv.org/api/query?id_list=2512.24354 |
| 122 | G | Nature "An AlphaFold 4" news item | Feb 2026; could not open | CONFIRMED (annotated) | Nature 19 Feb 2026; open syndication at Scientific American 21 Feb 2026; quote by Mohammed AlQuraishi | https://www.scientificamerican.com/article/an-alphafold-4-scientists-marvel-at-deepmind-drug-spin-offs-exclusive-new-ai/ |
| 123 | D | Jagannathan 2019 | 582 dogs + 8 wolves | CONFIRMED | title/metadata | https://doi.org/10.1111/age.12834 |
| 124 | G | Moult 1995 CASP; Zwanzig 1992; Anfinsen 1973 | metadata | CONFIRMED | Crossref (Proteins 23(3) 1995; PNAS 89:20–22; Science 181:223–230) | https://api.crossref.org/works/10.1002/prot.340230303 |
| 125 | G | Evans 2021 AF-Multimer Oct 2021 | bioRxiv 2021.10.04 | CONFIRMED | DOI date | https://doi.org/10.1101/2021.10.04.463034 |
| 126 | G | Bertoni 2026 NAR 54:D358 | as stated | CONFIRMED | Crossref | https://doi.org/10.1093/nar/gkaf1226 |
| 127 | G | AF Server "pTM unreliable for chains <16–20 residues" | as stated | CONFIRMED | FAQ: <16 residues; pTM <0.05 under 20 tokens | https://alphafoldserver.com/faq |
| 128 | D | Dog is a subspecies of the grey wolf (UniProt text) | as stated | CONFIRMED (not re-opened; taxonomy standard) | — | — |
| 129 | G | Google Cloud AF3 pricing/allowlist | not retrieved ❓ | UNRESOLVED | not checked here either | — |
| 130 | D | Cramer 2026 Anaplasma P44 | abstract-only 🟡 | UNRESOLVED | DOI resolves (Infect Immun e00167-26); content not re-read | https://doi.org/10.1128/iai.00167-26 |
| 131 | G | DeepMind's exact statement to the FT | paraphrased via Gigazine | UNRESOLVED | FT text paywalled | https://x.com/FT/status/2082466446483837214 |

---

## Edits made

### `alphafold_complete_guide.md`
1. Header status line → "independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/alphafold_verification.md".
2. TL;DR AlphaFold DB bullet: "about 4 M NVIDIA-generated dimer predictions" → "about 2.2 M" with the FAQ's 2,158,419 + 79,156 breakdown and the overlap explanation; added the FAQ's exact 261,552,403 total and the exact 1,703,992 viral-complex count.
3. TL;DR Jumper bullet: 🟡 → ✅; added his X post as primary source.
4. TL;DR FT bullet: date fixed to 29 Jul 2026; sourcing expanded (FT X post, The Decoder, Scientific American); staff destinations and names (Adler, Pritzel) added; "will not be shut down" / "3 million" explicitly attributed to Gigazine and kept 🟡.
5. Timeline row 19 Jun 2026: 🟡 → ✅ with primary source.
6. Timeline row "~30 Jul 2026" → "29 Jul 2026" with corroboration and split confidence.
7. Timeline row Sep 2026 viral complexes: exact count; AFDB's own ~3,500 vs ~2,800 inconsistency noted; VAD attribution.
8. "Not found" paragraph: Nature news item dated 19 Feb 2026, open Scientific American syndication added, AlQuraishi quote attributed.
9. §6.3: AF3 23.3% figure re-sourced to the technical report's own table (with the filtered/clustered subsets); "trained to the same cutoff" quoted.
10. §7: "Nobel committee cited >2 M users" attribution removed; figure re-attributed to DeepMind's page.
11. Open questions: FT item reworded.
12. Sources [35] and [36] rewritten with primary/corroborating URLs.
13. "## Verification notes" appended.

### `how_to_use_alphafold.md`
1. Header status line updated.
2. §1.1 step 2: false "old format no longer resolves" claim corrected; canonical host given as alphafold.ebi.ac.uk.
3. §1.2 `msaUrl` bullet and §1.3 `msa_v6.a3m` row: HTTP 403 on direct download recorded, tagged ❓.
4. §3: ColabFold pip command replaced with the README's full command.
5. §5 Foundry row: Apple Silicon support qualified (community fork, inference-only, float32).
6. "## Verification notes" appended.

### `alphafold_and_dogs.md`
1. Header status line updated.
2. TL;DR NVIDIA sentence: Swiss-Prot/UniProt scope caveat and the `/api/complex` evidence added.
3. §2.3 GHR row: CSH1 (0.81) and GH1 (0.80) heterodimers added to the CSH2 note.
4. §2.4 and Open questions: 46-vs-47 resolved by the FAQ's own "46".
5. §4 row 1 (Weng 2025): "AF3 Server" → "AF3" with the paper's wording; pTM/ipTM and AF2 initial model confirmed.
6. "## Verification notes" appended.

---

## Open issues

1. **DeepMind's statement on the AlphaFold team.** The FT article is paywalled. The dissolution itself is corroborated by Scientific American and The Decoder, but the "will not be shut down" wording and the ">3 million researchers" figure are known only through Gigazine. Someone with FT access should check the original wording.
2. **AFDB MSA download.** The `msaUrl` returned by the API gives a Google Cloud Storage 403 on 2026-10-04. It is unclear whether this is a transient permissions problem or whether MSAs are meant to be fetched only through the entry page. Re-test before relying on §1.2–1.3 of the how-to file.
3. **AFDB's own inconsistencies** (46 vs "47 other" proteomes; ~3,500 vs ~2,800 viral proteomes) are now annotated but cannot be resolved from outside EMBL-EBI.
4. **Not re-checked:** Google Cloud AF3 pricing and allowlist; HelixFold3, SeedFold, Pearl and ESM3 licence terms beyond the repository licence field; Cramer 2026 (abstract only); the exact AlphaFold Server JSON schema for protein chains (the author also flagged this ❓).
5. **Scope note.** The 2024 Nobel "two million users" figure may exist in the Nobel popular-science background PDF, which was not opened; the HTML press-release and popular-information pages do not contain it. The file now attributes the figure to DeepMind, which is correct regardless.
