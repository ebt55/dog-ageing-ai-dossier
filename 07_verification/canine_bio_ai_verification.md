# Verification Report: 03_canine_bio_ai
> Part of the dog-ageing research dossier · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> Independent fact-check by Opus 5.5 · 2026-10-04
> Files audited (both written by Fable 5.1 on 2026-10-04):
> - `03_canine_bio_ai/dog_foundation_models_landscape.md`
> - `03_canine_bio_ai/companies_and_research_groups.md`
>
> Method: about 85 web calls.
> - **Primary-data checks:** downloaded and grepped the OpenGenome2 `species_metadata.csv` (15.3 MB), InstaDeep `original_urls.csv` (850 lines), the DNABERT-2 PDF (local text extraction) and the Zoetis FY2025 10-K (3.3 MB).
> - **APIs:** UniProt proteomes, AlphaFold DB API and FTP listing, ENA assembly XML, Crossref, Europe PMC (abstracts and full texts), bioRxiv details, Zenodo, and Hugging Face models and datasets.
> - **Web:** company and official pages (Loyal, TAMU, Dog Aging Institute, Mars, Cornell, PR Newswire, DOI/FWS, CZI GitHub, AlphaGenome docs, UCSC), plus about 8 web searches for 2025–2026 company news.
>
> Every in-file change is marked `[verifier-corrected]`, `[verifier-added]`, `[verifier-upgraded]` or `[verifier-downgraded]`, and each file ends with a "Verification notes" section.

---

## Overall reliability: **MEDIUM-HIGH**

**Why:**
- **No fabricated citations were found.** Every DOI, PMID and URL I tested resolved to the stated paper or page, with correct first authors and journals. That covers about 40 Crossref and Europe PMC lookups plus about 20 page fetches.
- **Most numbers are right.** 64 of 93 checked claims were confirmed exactly, and most corrections are scope or framing rather than wrong digits. The author did genuinely open the species files: the OpenGenome2, NT and DNABERT-2 findings reproduce.
  - Every detailed number reproduced: Lu 2023 (dogs n = 742, r = 0.94), Jin 2024 (R² = 0.33, RMSE 3.08), McCoy (864 dogs, 0.37, 34 %), CanVAS, Dog10K, scCompass, and the Loyal milestones.
- **The headline survives my independent search, with its scope narrowed.** There is still no dog- or wolf-specific *molecular* foundation model (protein, DNA or single-cell). Dog-specific *imaging* foundation models do exist, though: VET-DINO (May 2025) and V-REX (Aug 2026).
- **There are several material errors:**
  1. **DoGA was mis-described.** The "5,485 CAGE samples … 24 wolves" figure describes the tissue *biobank*. The 2024 atlas used STRT2-seq (not CAGE) on 9 dogs and 12 embryos, with **no wolves**. This undercuts the files' repeated claim that DoGA is a ready "regulatory atlas with wolves".
  2. **The dire-wolf status was out of date.** The preprint is described as unpublished, but it appeared in *Cell Genomics* in Aug 2026.
  3. **"Evo 2 is the only genomic LM with dog in training" is false.** NTv3 was pre-trained on OpenGenome2.
  4. **Wisdom Panel's size was misframed.** It was given as ~1.1–1.2 M dogs, but the cohort was 3.5 M in 2023, larger than Embark's 2.5 M.
  5. **The Hugging Face "canine" result was wrong.** It returns 176 models, not 57, and not all are CANINE NLP.
  6. **TranscriptFormer's licence was misstated.** "Licence unstated" is wrong; the repository is MIT.
- **Overstatement:** FidoCure/Stanford is repeatedly called "ML" or an "AI-native" clinico-genomic model. The paper actually uses Cox proportional-hazards regression.
- **The self-flagged uncertainties were well placed.** Of 23 flagged items:
  - 14 were confirmed outright.
  - 7 needed correction or refinement: TranscriptFormer licence, Hu & Xie wording, DoGA, Colossal/dire-wolf status, FidoCure "ML", Wisdom Panel size, and the Rejuvenate date.
  - 2 remain partly open: wolves in the Lu 2023 panel, and Loyal's total funding.

---

## Counts

| Category | n |
|---|---|
| Claims checked (both files; rows 1–93 below) | **93** |
| CONFIRMED | **64** |
| CORRECTED | **21** |
| DOWNGRADED | **3** |
| REMOVED | **0** (wrong statements were struck through or replaced, not deleted) |
| UNRESOLVED | **5** |

Each row is counted once, by its main verdict. Rows with mixed sub-verdicts (#11, #21, #22, #25) are counted as CORRECTED, CONFIRMED, CORRECTED and DOWNGRADED respectively; their unresolved parts appear as separate rows (#68, #75).
| Verifier additions (new facts, not counted above) | 3 (VET-DINO/V-REX imaging FMs; OpenGenome2 Ensembl dog transcripts; Loyal LOY-003 RXE Sep 2026) |

Coverage of the requested minimums:
- Flagged items: all 23 checked.
- TL;DR bullets: all 8 (landscape) + 7 (companies) checked.
- Table cells: more than 30 spot-checked across the §2 audit tables, the §4 summary table and the quick-directory table.
- ✅-tagged claims: about 45 sampled; 38 were fully correct, 7 needed correction or downgrade.
- Citations: about 40 checked for existence, authors, year, journal and support.

---

## Claim-by-claim table

Abbreviations: **L** = landscape file, **C** = companies file. EPMC = Europe PMC REST.

### A. Author's self-flagged claims

| # | Claim | As written | Verdict | Correct value | Source |
|---|---|---|---|---|---|
| 1 | L: no dog/wolf biological FM exists | "no dog- or wolf-specific biological FM (protein, DNA, single-cell or multimodal)" | **CONFIRMED** for molecular FMs; scope narrowed | No molecular FM found in HF models/datasets, EPMC (incl. bioRxiv) or arXiv. Dog-specific *imaging* FMs exist: VET-DINO (5 M radiographs, 668 k canine studies; arXiv 2505.15248) and V-REX (arXiv 2608.20069) | https://huggingface.co/api/models?search=canine&limit=1000 ; https://export.arxiv.org/api/query?search_query=ti:VET-DINO |
| 2 | L: HF "canine" search | "57 hits, all Google CANINE" | **CORRECTED** | 176 hits at limit=1000 (limit=50 returns 50). Mostly CANINE NLP, but they include small dog task models (vet-dermatology-canine, canineBCS, Canine-LSA ResNet, canine-health Mistral LoRA) | https://huggingface.co/api/models?search=canine&limit=1000 |
| 3 | L: Evo 2 OpenGenome2 includes GCF_011100685.1 | yes, plus 6 canid genomes and mitogenomes | **CONFIRMED** (+ addition) | Line 28642 of `species_metadata.csv`. The file also contains Ensembl ncRNA (dog + Basenji/Boxer/Great Dane/GSD + dingo) and Ensembl mRNA (dog 26,040; dingo 7,145). No grey-wolf nuclear genome | https://huggingface.co/datasets/arcinstitute/opengenome2/resolve/main/species_metadata.csv |
| 4 | L: GCF_011100685.1 identity | UU_Cfam_GSD_1.0, *C. l. familiaris* | **CONFIRMED** | ENA: "UU_Cfam_GSD_1.0 assembly for Canis lupus familiaris" | https://www.ebi.ac.uk/ena/browser/api/xml/GCA_011100685.1 |
| 5 | L: Evo 2 publication | Nature 652:1349–1361, 4 Mar 2026 | **CONFIRMED** | 652(8112):1349–1361; online 4 Mar 2026, issue 30 Apr 2026; 62 authors, Brixi … Hie | https://api.crossref.org/works/10.1038/s41586-026-10176-5 |
| 6 | L: NT 850 genomes: no *familiaris*; dingo GCF_012295265.1 + Arctic fox | as stated | **CONFIRMED** | 850 URLs, 31 mammals; `Canis_lupus_dingo` GCF_012295265.1 and `Vulpes_lagopus` GCF_018345385.1; no *familiaris* or wolf | https://huggingface.co/datasets/InstaDeepAI/multi_species_genomes/resolve/main/original_urls.csv |
| 7 | L: DNABERT-2 mammals | 7 mammals, no canid | **CONFIRMED** | Table 11: Bubalus, Camelus, Human, Macaca assamensis, Macaca nigra, Mus musculus, Peromyscus; 135 species; 32.49 B nt | https://arxiv.org/pdf/2306.15006 |
| 8 | L: Lu 2023 dogs | n = 742, 93 breeds, r = 0.94, MAE < 2.28 y | **CONFIRMED** | Exact quote in the full text (LOSO, Clocks 2 and 3) | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC10501909/fullTextXML |
| 9 | L: wolves among Lu 2023's 185 species | unstated ❓ | **UNRESOLVED** | Zero hits for wolf/wolves/Canis/Canidae in the main text; Supplementary Data 1 not accessed | same |
| 10 | L/C: Horvath 2022 venue and title | PNAS 119(21):e2120887119, "DNA methylation clocks for dogs and humans" | **CONFIRMED** | 13 authors, Horvath … Ostrander (incl. Brooke, Raj, Serres-Armero, Dreger, Hogan, Plassais). All sibling files also say PNAS; I found no conflicting venue | https://api.crossref.org/works/10.1073/pnas.2120887119 |
| 11 | L: UCE | 8 species, 36 M cells | **CONFIRMED**; citation **CORRECTED** | Nature version: "Universal cell embedding provides a foundation model for cell biology", *Nature* 656:183–191 (8 Jul 2026); IMA of 36 M cells across 8 species | EPMC PMID 42420460; Crossref 10.1038/s41586-026-10689-z |
| 12 | L: TranscriptFormer species | 12 species, no dog | **CONFIRMED** | TF-Metazoa: 112 M cells, 12 species | https://github.com/czi-ai/transcriptformer |
| 13 | L: TranscriptFormer licence | "README states no licence" | **CORRECTED** | Repository is MIT (LICENSE.md, © 2025 CZI); no separate weights licence stated | https://github.com/czi-ai/transcriptformer/blob/main/LICENSE.md |
| 14 | L: AlphaGenome scope and terms | human + mouse; outputs non-commercial | **CONFIRMED** | FAQ: "trained and evaluated on human and mouse DNA"; outputs "for non-commercial use only"; commercial access via Google Cloud | https://www.alphagenomedocs.com/faqs.html |
| 15 | L: McCoy DAP preprint | 864 dogs, >3 M CpGs, 0.37 y/yr, 34 % mortality; no journal version | **CONFIRMED** | bioRxiv v1 4 Oct 2024, v2 29 Oct 2024; "published: NA"; no McCoy journal paper in EPMC | https://api.biorxiv.org/details/biorxiv/10.1101/2024.10.03.616519 |
| 16 | L: Jin 2024 | 71 dogs, R² = 0.33, RMSE 3.08 y | **CONFIRMED** | DNAm R²adj 0.33, RMSE 3.08; ATAC 0.26/3.22; combined 0.29/3.15; 13,336 CpGs; 15,417 peaks; PRJNA1049514/PRJNA1048909 | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC11019125/fullTextXML |
| 17 | L: Hu & Xie 2025 | sens 0.77–0.90, spec 0.20–0.46 "across 8 species", 126 dog variants | **CORRECTED** (wording) | Ranges are across the three tools on 374 pooled variants (AM 0.77/0.46; ESM-1b 0.86/0.32; PolyPhen-2 0.90/0.20); 126 dog of 374 across 8 species; OVJ 15(10):5183–5191 | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC12613190/fullTextXML |
| 18 | L/C: Dog10K | 1,987 canids; 63 wolves; 52.96 M SNVs; 105,057 nuclei | **CONFIRMED** (source inconsistency flagged) | NAR Table 1: 52,963,969 SNVs, but the same paper's text says "34.6 million SNVs"; Genome Biol 24:187 abstract gives ">48 M" variants of all types. 8,565 DNMs, 643 dogs, 74,067 cells, 30 dogs vs 469 humans, no registration | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC11701641/fullTextXML ; EPMC 37582787 |
| 19 | L/C: DoGA Nat Commun 2024 | "5,485 CAGE samples, 132 tissues, 13 dogs, 12 embryos, 24 wolves" | **CORRECTED** | Biobank = 5,485 samples / 132 tissues / 13 dogs / 12 embryos / 24 wolves. Atlas = STRT2-seq on 100 tissues from 9 dogs + 12 embryos (no wolves); *Nat Commun* 15:9082 | EPMC PMID 39433728 |
| 20 | L/C: CanVAS | 15,451 dogs, CC-BY, Apr 2026 | **CONFIRMED** | bioRxiv 15 Apr 2026; 375+ breeds; Dog10K panel 1,929; Beagle 5.4; 9.7 M variants; Zenodo 19186944, cc-by-4.0, 23 Mar 2026 | https://zenodo.org/api/records/19186944 ; EPMC PPR1214852 |
| 21 | C: Loyal milestones | RXE Feb 2025; TAS 13 Jan 2026; $100 M Series C 11 Feb 2026 led by age1; >$250 M total | **CONFIRMED** except total (**UNRESOLVED**) | Posts confirm all dates; Series C: age1 lead + Longevity Fund + Baillie Gifford; STAY 1,300+ dogs at 70+ clinics; total raised not stated. No CMC acceptance or approval found by Oct 2026 | https://loyal.com/posts/loy-002-tas ; https://loyal.com/posts/100m-for-first-longevity-drug |
| 22 | C: Colossal | 20 edits/14 genes; preprint only; $10.2 B; ViaGen Nov 2025 | Mixed: ViaGen and $10.2 B **CONFIRMED**; preprint status **CORRECTED**; edits **UNRESOLVED**; valuation **UPDATED** | Dire-wolf paper published in *Cell Genomics* 6(8):101306, Aug 2026. ViaGen acquired 4 Nov 2025. 2026 talks at $20–30 B (TechCrunch 20 Jul; Axios 30 Sep), not closed | https://api.biorxiv.org/details/biorxiv/10.1101/2025.04.09.647074 ; Crossref 10.1016/j.xgen.2026.101306 ; https://techcrunch.com/2026/07/20/colossal-biosciences-reportedly-in-talks-to-raise-new-capital-at-20b-30b-valuation/ |
| 23 | C: DAP | $7 M NIH grant Jan 2025; 2024 lapse; founders' roles; Dog Aging Institute | **CONFIRMED** (minor refinements) | TAMU 6 Jan 2025: $7 M, 170 → 580 dogs, Creevy/Reed/Anderson. Lapse: NIA U19 not renewed, ran out mid-2024 (STAT/WGBH/AVMA). Dog Aging Institute: Kaeberlein President (Optispan CEO), Creevy Secretary (TAMU), Promislow Treasurer & Chair (Tufts); incorporated 6 Dec 2023, 501(c)(3) | https://stories.tamu.edu/news/2025/01/06/dog-aging-project-nih-grant-to-expand-trial-of-anti-aging-drug/ ; https://dogaginginstitute.org/team/ ; https://dogaginginstitute.org/faqs/ |
| 24 | C: Mars–Broad | 10 k dog + 10 k cat genomes, Jan 2023 | **CONFIRMED** | 9 Jan 2023; 10 years; NCBI SRA; Broad/Karlsson | https://www.mars.com/news-and-stories/press-releases-statements/mars-petcare-broad-institute-open-access-database-dog-cat-genomes |
| 25 | L/C: FidoCure/Stanford | 2,119 dogs; ML | Numbers **CONFIRMED**; "ML" **DOWNGRADED** | 2,119 dogs, 1,108 sequenced, 48 genes, 2.4 genes/dog, 10 therapies; method is Cox PH (Lifelines) | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9852553/fullTextXML |
| 26 | C: Embark / Wisdom Panel sizes | Embark 2.5 M; Wisdom ~1.1–1.2 M | Embark **CONFIRMED**; Wisdom **CORRECTED** | Embark 2.5 M dogs (Apr 2025). Donner 2023 analysed 1,054,293 dogs "from our existing cohort of 3.5 million" | https://news.cornell.edu/stories/2025/04/dog-owners-help-advance-research-one-dna-test-time ; EPMC PMID 36848397 |
| 27 | C: first CRISPR dogs from GIBH/CAS, not Sinogene | as stated | **CONFIRMED** | Zou et al. *JMCB* 7(6):580–583; affiliations GIBH-CAS, Nanjing U, Guangzhou General Pharmaceutical Research Institute Co., Jilin U; Sinogene not mentioned; 35 zygotes → 10 recipients → 27 pups; Tiangou biallelic, Hercules chimeric | https://academic.oup.com/jmcb/article/7/6/580/2459501 |
| 28 | C: Rejuvenate Bio $6 M / Merck | 8 Jun 2026, single source | **CORRECTED** (date) + **UPGRADED** | BusinessWire 2 Jun 2026; PR Newswire (Lifespan Vision Ventures) 11 Jun 2026; led by VCapital; Merck Animal Health participated; San Diego HQ | https://www.prnewswire.com/news-releases/lifespan-portfolio-company-rejuvenate-bio-closes-6-million-financing-and-rd-collaboration-with-merck-animal-health-302798157.html |
| 29 | L/C: scCompass | 104.6 M cells, 13 species incl. dog | **CONFIRMED** | 104,637,783 cells; 15,270 samples after QC; dog aligned to UU_Cfam_GSD_1.0. Ships pre-trained checkpoints, species mix not stated | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC12224968/fullTextXML |

### B. Other landscape-file claims (TL;DR, tables, ✅ sample)

| # | Claim | As written | Verdict | Correct value | Source |
|---|---|---|---|---|---|
| 30 | HF `canfam`, `dog genome` | empty | **CONFIRMED** | 0 models and 0 datasets | HF API |
| 31 | HF `veterinary` | 13 small fine-tunes | **CONFIRMED** | 13 | HF API |
| 32 | Other canid nuclear genomes in OG2 | Urocyon, V. ferrilata, Chrysocyon, Nyctereutes, Lycaon, Otocyon | **CONFIRMED** | as stated | OG2 csv |
| 33 | OG2 row counts | "15,653 eukaryote rows, 2,037 Mammalia (counts include organelle records)" | **CORRECTED** | 15,653 eukaryote rows exclude organelles (15,044 NCBI genomes + 338 ncRNA + 271 mRNA; organelles = separate 32,240 rows). 2,037 Mammalia includes organelles; 524 mammalian nuclear genomes | OG2 csv |
| 34 | OG2 / Evo 2 licences | Apache-2.0 data; open weights | **CONFIRMED** | Both dataset and `arcinstitute/evo2_40b` are apache-2.0 | HF API |
| 35 | NT "one species per genus" | as stated | **CORRECTED** (minor) | The URL list has *Mus musculus* and *Mus caroli* | NT csv |
| 36 | NT licence | CC-BY-NC-SA 4.0 | **CONFIRMED** | cc-by-nc-sa-4.0 | HF API |
| 37 | "Evo 2 is the only large open genomic LM with a domestic-dog genome in training" | as stated (§5) | **CORRECTED** | NTv3 (InstaDeep, bioRxiv 25 Dec 2025) was pre-trained on ~9 T bp of OpenGenome2; checkpoints on HF (gated, licence "other"). GENERator (RefSeq eukaryotes) may also include dog; not checked | EPMC PPR1230501 ; https://huggingface.co/InstaDeepAI/NTv3_650M_post |
| 38 | GPN-MSA citation | Nat Biotechnol, 2 Jan 2025 | **CONFIRMED** | 43(12):1960–1965 | Crossref 10.1038/s41587-024-02511-w |
| 39 | UCSC 100-way includes dog | canFam3, syntenic net; no wolf/fox | **CONFIRMED** | exact line | https://hgdownload.soe.ucsc.edu/goldenPath/hg38/multiz100way/README.txt |
| 40 | Caduceus | hg38, open weights | **CONFIRMED** | apache-2.0 on HF | HF API |
| 41 | UniProt dog proteomes | UP000805418 (43,615), UP000002254 (41,817), UP000694429 (42,651), UP000694542 (42,573) | **CONFIRMED** | exact match; reference proteome assembly GCA_014441545.1 | https://rest.uniprot.org/proteomes/search?query=organism_id:9615&format=json |
| 42 | AFDB P49822 | Albumin, dog, 2025-08-01, v6 | **CONFIRMED** | exact | https://alphafold.ebi.ac.uk/api/prediction/P49822 |
| 43 | AFDB bulk downloads include dog? | ❓ | **CORRECTED** (resolved) | No: the v6 FTP has no 9615/CANLF archive | https://ftp.ebi.ac.uk/pub/databases/alphafold/latest/ |
| 44 | ESM-2 licence | MIT | **CONFIRMED** | mit | HF API (facebook/esm2_t33_650M_UR50D) |
| 45 | SATURN | Nat Methods 2024 | **CONFIRMED** | 21(8):1492–1500 | EPMC 38366243 |
| 46 | GeneCompass | >120 M cells; 101.8 M after QC 🟡 | **CONFIRMED** (upgraded) | 101,768,420; *Cell Res* 34:830–845 | EPMC 39375485 |
| 47 | Mouse-Geneformer | 21 M mouse cells | **CONFIRMED** | 21 million | EPMC 40106407 |
| 48 | Lu 2023 scale | 11,754 arrays, 59 tissues, 185 species | **CONFIRMED** | exact; *Nat Aging* 3(9):1144–1166 | EPMC full text |
| 49 | Haghani 2023 | 15,456 profiles, 348 species | **CONFIRMED** | exact; *Science* 381:eabq5693 | EPMC 37561875 |
| 50 | Thompson 2017 | 46 dogs, 62 wolves, 41/67 CpGs | **CONFIRMED** | + 115-CpG combined; *Aging* 9(3):1055–1068 | EPMC 28373601 |
| 51 | Armero 2024 | *Aging*, co-analysis of platforms | **CONFIRMED** | 16(13):10724–10748 | EPMC 38985449 |
| 52 | Jang 2026 PNAS | published 2026 🟡 | **CONFIRMED** (upgraded) | 123(29):e2528874123; 13 Jul 2026 | EPMC 42441848 |
| 53 | Kang 2026 GeroScience | Sep 2026 🟡 | **CONFIRMED** (upgraded) | online 17 Sep 2026 | EPMC 42753031 |
| 54 | Embark Age Test | 4 Oct 2022, $159, 70 % ± 5 mo, 92 % ± 10 mo | **CONFIRMED** | exact; validation described only as "hundreds of dogs" | https://www.prnewswire.com/news-releases/embark-launches-first-of-its-kind-age-test-to-accurately-determine-dogs-calendar-age-301640141.html |
| 55 | DoGA 2026 preprint | 114 CAGE libraries, 56 tissues/stages, 9 dogs, 68,446 promoters, 46,661 enhancers, 69 orthologous enhancers | **CONFIRMED** | exact | EPMC PPR1218313 |
| 56 | PetBERT | 5.1 M EHRs, >500 M words, F1 > 83 %, Sci Rep 2023 | **CONFIRMED** | *Sci Rep* 13:18015 | EPMC 37865683 |
| 57 | VetLLM | F1 0.747 / 0.637 (🟡) | **CONFIRMED** (upgraded) | 0.747 CSU, 0.637 PP; PSB 29:120–133 | EPMC 38160274 |
| 58 | Zoetis 10-K AI features | AI derm & fecal 2023; urine + OptiCell 2024; AI Masses 2025 | **CONFIRMED** (refined) | AI fecal is "for equine"; OptiCell is a separate analyser; AI Masses quote exact | https://www.sec.gov/Archives/edgar/data/1555280/000155528026000011/zts-20251231.htm |
| 59 | Fang 2025 | 26,614 dogs, 160 conditions | **CONFIRMED** | *PLoS Comput Biol* 21(8):e1012728 | EPMC 40811246 |
| 60 | Harrison 2026 | 937 Precision-Cohort dogs | **CONFIRMED** | *J Gerontol A* 81(4):glaf279 | EPMC 41429575 |
| 61 | Prescott 2025 | 1,000 pairs; 976 dogs | **CONFIRMED** | *GeroScience* 47(4):5725–5748 | EPMC 40038157 |
| 62 | Rizzoli 2025 lung atlas | 26,278 cells, 4 dogs, 46 subpopulations | **CONFIRMED** | *Front Immunol* 16:1501603 | EPMC 40114924 |

### C. Other companies-file claims

| # | Claim | As written | Verdict | Correct value | Source |
|---|---|---|---|---|---|
| 63 | DAP founding | "founded 2014 by Promislow, Kaeberlein and Creevy at UW" | **CORRECTED** (minor) | Founded 2014 at UW; Creevy was a Texas A&M internist, not UW | The Scientist via search; Wikipedia DAP |
| 64 | DAP enrolment | >50,000 dogs 🟡 | **CONFIRMED** (secondary) | ~50–54 k in press coverage | WGBH; search summaries |
| 65 | TRIAD sites | "17+ sites" | **CORRECTED** (minor) | 20 current locations; 17 listed by name | TAMU release |
| 66 | Mars SRA deposits | ❓ | **UNRESOLVED** | ENA search found no Mars/Biobank-titled dog study | ENA portal API |
| 67 | Embark details | founded 2015 by Boykos; 230 k markers; 270/350/55 | **CONFIRMED** | exact | Cornell Chronicle |
| 68 | Loyal ">$250 M total" | 🟡 | **UNRESOLVED** (downgraded to ❓) | not in the Series C post | Loyal post |
| 69 | Loyal STAY / TAS | 1,300+ dogs, 70+ clinics, >400 treated dogs | **CONFIRMED** | exact | Loyal posts |
| 70 | Rejuvenate RJB-0402 | from PackGene 🟡 | **UNRESOLVED** | not in the PR Newswire release | PR Newswire |
| 71 | Colossal Series C | $200 M, Jan 2025, $10.2 B, $435 M total | **CONFIRMED** | as stated | Wikipedia; TechCrunch 2025-01-15 |
| 72 | Colossal current valuation | "$10.2 B valuation" (status 2026) | **CORRECTED** (updated) | Talks at $20–30 B reported Jul–Sep 2026; not closed | TechCrunch 2026-07-20; Axios 2026-09-30 |
| 73 | ViaGen acquisition | 4 Nov 2025, 25 staff | **CONFIRMED** | as stated; terms undisclosed | Fast Company / D CEO / Dallas Innovates via search |
| 74 | Dire-wolf preprint | "no journal version as of Oct 2026" | **CORRECTED** | *Cell Genomics* 6(8):101306 (Aug 2026) | bioRxiv API; Crossref |
| 75 | "20 edits in 14 genes" | 🟡 (company/Wikipedia) | **UNRESOLVED** | not checked against the journal paper | — |
| 76 | Anat Rec rebuttal | 309(7):1788–1796 | **CONFIRMED** | online 10 Sep 2025 | EPMC 40927892 |
| 77 | Colossal–DOI/FWS | "June 2026 biobanking partnership" 🟡 | **CONFIRMED** (upgraded) | MOU announced 25 Jun 2026; ~2,300 ESA species; no federal funds obligated | https://www.doi.gov/pressreleases/interior-announces-new-partnership-advance-conservation-imperiled-species-through |
| 78 | FidoCure "clinico-genomic ML" (TL;DR, directory, §2.6) | as stated | **DOWNGRADED** | Cox regression survival analysis | PMC9852553 |
| 79 | Charruau 2016 | 25 wolves, 625 genes ✅ | **DOWNGRADED** to 🟡 | Abstract confirms the study design and conclusions; counts not checkable (no OA full text) | EPMC 27189566 |
| 80 | Bergström 2022 | 72 ancient wolf genomes 🟡 | **CONFIRMED** (upgraded) | *Nature* 607:313–320 | EPMC 35768506 |
| 81 | Morrill 2022 | 18,385 surveyed, 2,155 genotyped, breed explains 9 % | **CONFIRMED** | *Science* 376:eabk0639 | EPMC 35482869 |
| 82 | GRLS | 3,044 goldens enrolled Jun 2012–Apr 2015 | **CONFIRMED** | exact | EPMC 35679242 |
| 83 | OLD DOG | 209 dogs, 30-month study, *J Frailty Aging* 2026 | **CONFIRMED** | 15(3):100145; preliminary cross-sectional results | EPMC 41860870 |
| 84 | Mars Biobank cohort | *BMC Vet Res* 2026, first 2,000 dogs | **CONFIRMED** | 22:252 | EPMC 41857781 |
| 85 | McMillan 2024 | 584,734 dogs | **CONFIRMED** | *Sci Rep* 14:531 | EPMC 38302530 |
| 86 | Jiménez review | "GeroScience 2024" | **CORRECTED** (minor) | 46(1):241–255, online Aug 2023 | EPMC 37594598 |
| 87 | Zoetis–Basepaws | acquired 2022 | **CONFIRMED** | 10-K text | SEC 10-K |
| 88 | DoGA "only canine regulatory atlas with wolves" | as stated | **CORRECTED** | Wolves are biobanked but not profiled in a published atlas | EPMC 39433728 |
| 89 | DoGA directory row: "CAGE functional annotation of dog & wolf genome" | as stated | **CORRECTED** | STRT2-seq 2024 + CAGE 2026 preprint, both dogs only | EPMC 39433728; PPR1218313 |
| 90 | Wisdom Panel in directory and §3 tables | 1.1–1.2 M | **CORRECTED** | 3.5 M-dog cohort (2023) | EPMC 36848397 |
| 91 | DoGA in wolf-data sources (TL;DR, §2.2 iv) | DoGA wolf samples as a usable source | **CORRECTED** | biobanked only | as above |
| 92 | Mammalian Methylation Consortium dog arrays | 742 dogs, 93 breeds; GEO | **CONFIRMED** | as in #8 | Lu 2023 |
| 93 | Dog Aging Institute "founded 2023" | as stated | **CONFIRMED** | incorporated 6 Dec 2023 | FAQ |

**Verifier additions (not counted above):**
- (a) VET-DINO / V-REX canine radiograph FMs (arXiv 2505.15248; 2608.20069).
- (b) OpenGenome2 contains Ensembl dog/dingo ncRNA and mRNA sets.
- (c) Loyal LOY-003 RXE acceptance announced 16 Sep 2026 (BusinessWire via search summary; 🟡). The sibling `interventions_verification.md` independently lists the same date.

---

## Edits made

**`dog_foundation_models_landscape.md`**
1. Header status line replaced with the verified-status line.
2. TL;DR bullet 1:
   - narrowed the headline to *molecular* FMs;
   - corrected the HF "canine" count (176, not "57, all CANINE");
   - added the VET-DINO/V-REX imaging caveat.
3. TL;DR bullet 2: added the OpenGenome2 Ensembl dog transcripts and NTv3.
4. TL;DR bullet 3: added that dog is not among AFDB's bulk proteome archives.
5. TL;DR bullet 4: rewrote the DoGA description (biobank vs STRT2-seq atlas vs 2026 CAGE; no wolves profiled).
6. TL;DR bullet 5: added the scCompass checkpoint caveat.
7. TL;DR bullet 6: added the wolf full-text grep result.
8. TL;DR bullet 7: FidoCure described as Cox regression, not ML.
9. TL;DR bullet 8: Hu & Xie wording corrected.
10. §1: added the independent re-search note (incl. LucaCell, EpiZoo, NTv3); corrected the HF table row; added VET-DINO to the "nearest things" list.
11. §2.1: AFDB bulk-download ❓ resolved to "No".
12. §2.2:
    - Evo 2 row: corrected the count breakdown and added the Ensembl dog/dingo sets;
    - NT row: refined "one species per genus";
    - **new NTv3 row**;
    - GPN-MSA citation completed;
    - fixed a pre-existing table defect: the header had 5 columns while every row had 4.
13. §2.3:
    - UCE published citation corrected;
    - TranscriptFormer licence corrected to MIT;
    - GeneCompass upgraded to ✅;
    - SATURN pages added;
    - scCompass sample and cell counts plus checkpoint caveat.
14. §2.4: Lu 2023 note; Thompson pages and 115-CpG clock.
15. §3.1: Jang and Kang upgraded to ✅ with volume/date.
16. §3.2: Hu & Xie per-tool values; Dog10K SNV-count inconsistency flagged; CanVAS Zenodo metadata.
17. §3.3: FidoCure method corrected.
18. §3.4: Zoetis refined; **new VET-DINO/V-REX bullet**.
19. §3.5: VetLLM upgraded.
20. §3.7: DoGA rewritten.
21. §4 summary table: AFDB, Evo 2, **new NTv3 row**, TranscriptFormer licence, DoGA row, **new VET-DINO/V-REX row**.
22. §5 points 2–3: corrected "Evo 2 only" and "DoGA incl. wolves".
23. Open questions: AFDB item resolved; EpiZoo/NTv3 items added.
24. Sources: citation details completed for [14], [16], [17], [18], [23], [26], [27], [29], [38] and [53]; **new sources [71]–[73]**.
25. Appended "## Verification notes".

**`companies_and_research_groups.md`**
1. Header status line replaced.
2. TL;DR:
   - DoGA wording;
   - Wisdom Panel 3.5 M vs Embark 2.5 M;
   - DAP lapse/grant detail (upgraded);
   - Rejuvenate date and investors;
   - Colossal 2026 valuation talks;
   - **dire-wolf paper published in *Cell Genomics***;
   - FidoCure "Cox regression, not ML";
   - DoGA wolves biobanked only.
3. Quick directory rows: DoGA, Mars, Embark, Rejuvenate (upgraded), Colossal (publication + valuation), FidoCure.
4. Profiles:
   - DAP founding (Creevy at TAMU), TRIAD sites, lapse upgraded, Dog Aging Institute incorporation date;
   - Mars–Broad detail and ENA check;
   - Dog10K detail and SNV-count inconsistency;
   - DoGA rewritten;
   - CanVAS Zenodo date;
   - Bergström upgraded; **Charruau downgraded to 🟡**; wolves-in-open-datasets corrected;
   - Embark and Wisdom Panel cohort sizes;
   - Zoetis refined;
   - Loyal: investors, ">$250 M" downgraded, no-approval-yet note, LOY-003 RXE added;
   - Rejuvenate corrected and upgraded;
   - Colossal: valuation talks, **journal publication**, ViaGen upgraded, DOI/FWS MOU upgraded;
   - GIBH affiliations completed.
5. §2.6 FidoCure wording; §2.7 Jiménez citation; §3 table: DoGA, Mars/Wisdom, Embark.
6. Open questions: Colossal and Rejuvenate items updated.
7. Sources: [6], [22], [25], [27] and [70] completed; **new sources [71], [72]**.
8. Appended "## Verification notes".

---

## Open issues

1. **Wolves in the Mammalian Methylation Consortium's 185-species clock panel.** This needs Supplementary Data 1 of Lu et al. 2023 or the consortium sample sheet. The full text has no wolf mention.
2. **EpiZoo** (bioRxiv 2026.09.24.754017, a cross-species scATAC FM with a ~20.9 M-cell corpus): the species list was not checked. It could include dog.
3. **NTv3 post-training species.** My reading came through a summariser of the bioRxiv full text. Dog was not named, but the full 24-species list was not enumerated. The HF model card is gated.
4. **Other RefSeq-eukaryote genomic LMs** (e.g. GENERator, AIDO.DNA 796 species) may include dog sequence; not checked.
5. **Colossal "20 edits / 14 genes"** should be checked against the *Cell Genomics* paper, as should the preprint numbers (3.4×/12.8× coverage, 80 genes).
6. **Loyal total funding (>$250 M)** and **Mars SRA deposits** remain unverified.
7. **Charruau 2016** wolf count (25) and gene count (625) need the full text.
8. **Affiliation and weight availability for VET-DINO and V-REX** were not checked. Both papers share authors (Dourson, Fitzke); the industry affiliation is unconfirmed.
9. **Dog10K SNV-count discrepancy.** The NAR database paper gives 52.96 M (Table 1) but 34.6 M in its text. Users should cite the number matching the VCF they download.
10. **Small nuance, not edited:** the AlphaGenome FAQ wording "has not been determined" was not seen verbatim in my fetch, which paraphrased it as "not formally benchmarked". The substance (human + mouse only) is confirmed.
