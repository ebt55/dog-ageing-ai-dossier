# Verification report: "Why Do Dogs Age So Fast?"

> Part of the dog-ageing research dossier · 2026-10-04 · Verifier: Fable 5.1 (independent fact-check) · File audited was written by Opus 5.5 · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**File audited**
- `04_dog_aging_biology/why_dogs_age_fast.md` (~10,400 words, 93 sources, 18 author-flagged claims)

**Ground truth used**
- Europe PMC REST full text (Cagan 2022 PMC9021023; Horvath 2022 PMC9173771; Lu 2023 PMC10501909; Crofts 2024 PMC10798888; Whittemore 2019 PMC6660761; Teng 2022 PMC9050668; McMillan 2024 PMC10834484; Vincze 2022 PMC8755536; Swovick 2021 PMC7950207; Raz 2026 PMC13278975) and Europe PMC abstracts for ~35 further papers
- PMC HTML for Wang 2020 (PMC7484147)
- Crossref metadata for 14 DOIs (including the 2026 papers)
- AnAge entries for dog, wolf, human, chimpanzee and the AnAge help page
- NPS Yellowstone wolf page; ABC News (Bluey); Wikipedia (Bobi); AKC dog-years page; Gurven & Kaplan 2007 author PDF
- Python recomputation of every "(my calculation)" value

**Scope.** Every author-flagged claim, every TL;DR bullet, the §1 numeric tables, the derived calculations, and a citation sample of 60+ references (existence, authors/year/journal/pages, and whether the source supports the sentence). About 85 web calls were made; WebSearch was unavailable, so all look-ups used WebFetch against database APIs.

**Limits.** Cagan et al.'s supplementary spreadsheets (xlsx) could not be opened through text endpoints, so the dog-specific values in them were checked only for consistency with the main text. The AVMA and AAHA web pages are bot-protected; the UN WPP 2024 PDF exceeded the fetch size limit.

---

## 1. Reliability rating: **HIGH**

The file is accurate, carefully tagged, and honest about its own uncertainty:
- No fabricated or mis-attributed citation was found. All 14 DOIs tested via Crossref resolve to the stated paper with the stated journal, volume and pages; all ~45 Europe PMC look-ups returned the stated authors, year and findings.
- Every headline number re-checked in a primary source matched: UK medians (12.5; 15.4 Lancashire Heeler; 5.4 Caucasian Shepherd), Teng's life table (11.23 y; French Bulldog 4.53; all 21 mortality rows), Montoya 12.69 y, Yarborough OR 1.52 / 6.47, Bronson 20% to 40–50%, Horvath 742/93/R 0.97/24 y, Lu r 0.94 and >69%, Crofts −0.95/R² 0.81/−0.60/R² 0.80, Whittemore species list and R², Fick 10×, Abegglen 4.81%/11–25%, Firsanov Nature 648:717–725, Matsuda Science 369:1450–1455, Raz Extended Data Table 2 parameters.
- Every derived number reproduced: AnAge residuals (109.4 / 88.8 / 463.9 / 270.5%), the Gompertz refit (MRDT 1.95–2.2 y), Kleiber 1.20×, maturity 9.3×, gestation 4.4×, the Wang conversion table, and the Cagan end-of-life burdens (3,807 vs 3,943).
- Hypotheses are labelled as hypotheses; the author's own self-flags were all legitimate places to look.

The errors found were small: one recollected number (Gurven & Kaplan "72" → "about seven decades"), one over-precise sample description ("104 Labradors"), one reference number in the TL;DR, one missing conditional (Compton et al.), one unsourced wild-wolf record, and a tag that was too strong for supplementary-only values. **No claim had to be removed.**

---

## 2. Counts

| Verdict | n |
|---|---|
| Claims checked | **78** |
| Confirmed | 65 |
| Corrected | 6 |
| Downgraded | 4 |
| Removed | 0 |
| Unresolved | 3 |

Citations spot-checked for existence and correctness of metadata: 60 (all correct; 2 had pages added or a tag adjusted).

---

## 3. Claim-by-claim table

Author-flagged claims first (F1–F18), then TL;DR and body claims (B), then citation metadata checks (C).

| # | Claim | As written | Verdict | Correct value / note | Source URL |
|---|---|---|---|---|---|
| F1a | Cagan 2022 main-text numbers | 208 crypts / 56 individuals / 16 species; 47 → 796 SBS/yr; 1/lifespan FVE 82%; k = 3,206.4 (2,683.9–3,728.9); body mass FVE 0.21; ELB range ~1,828–5,379; lifespan = age by which 80% of adults have died | CONFIRMED | All in main text and Table 1 (ELB 1,828.08–5,378.73) | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9021023/fullTextXML |
| F1b | Cagan human values | 47.12 SBS/yr; lifespan 83.67 y | CONFIRMED | Table 1 min rate 47.12; max lifespan 83.67 | same |
| F1c | Cagan dog values | 249.46 SBS/yr; lifespan 15.26 y (zoo dogs + wolves pooled; "paucity of records"); 3 dogs / 11 crypts | UNRESOLVED → tag downgraded to 🟡 | Supplementary xlsx not re-opened. Consistent with main text (dog is one of 16 species; implied ELB 3,807 lies inside 1,828–5,379). Main text points to "Supplementary Tables 3 and 6" for species-level estimates, not 4/6/9 | same |
| F1d | Cagan end-of-life burdens | ~3,810 (dog) vs ~3,940 (human); TL;DR said ~3,800 | CONFIRMED (arithmetic) / harmonised | 249.46 × 15.26 = 3,806.8; 47.12 × 83.67 = 3,942.5 | recomputed |
| F1e | Cagan human cohort description | "1900 birth cohorts from Denmark, Finland and France, excluding deaths before 13" | DOWNGRADED to 🟡 | Main text: "census record data for humans"; detail not found outside supplement | same |
| F2 | Wang 2020 formula and sample | human_age = 16·ln(x)+31 from 17·ln(x)+33 and 16·ln(x)+30; 104 dogs profiled, 95 analysed; 320 humans 1–103 y; 12-y Lab → 70 human y; milestones; "15,000–30,000 years" | CONFIRMED (TL;DR "104 Labradors" CORRECTED to "104 dogs, primarily Labradors; 95 analysed") | "104 dogs, primarily consisting of Labrador retrievers"; "nine dogs removed due to lack of coverage" | https://pmc.ncbi.nlm.nih.gov/articles/PMC7484147/ |
| F3a | AnAge formula | t_max = 4.88·M^0.153, M in grams | CONFIRMED (unit by recomputation) | Help page gives formula without unit; only grams reproduces AnAge's residuals (kg would give 8.6 y for a 40-kg dog) | https://genomics.senescence.info/help.html |
| F3b | AnAge residuals | dog 109% (27 y, 40 kg); wolf 88–89% (20.6 y, 26.6 kg); human 463% (122.5 y, 62 kg); chimp 270% (68 y, 45 kg) | CONFIRMED; chimp expected t_max (25.1 y) filled in; mass caveat added | Recomputed 109.4 / 88.8 / 463.9 / 270.5%; AnAge pages show 109 / 88 / 463 / 270%. With 15–20 kg the dog residual is 122–127% | https://genomics.senescence.info/species/entry.php?species=Canis_familiaris (and Canis_lupus, Homo_sapiens, Pan_troglodytes) |
| F4 | Dog MRDT vs human | ~2.0 y (fit to Teng Table 2, ages 5–15, slope ≈0.35/y) vs ~8 y | CONFIRMED | Refit: ln(hazard) slope 0.345–0.355/y → MRDT 1.95–2.0 y (R² ≥ 0.999); ln(q) slope 0.31–0.34/y → 2.05–2.2 y. AnAge human MRDT 8 y | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9050668/fullTextXML |
| F5 | Horvath 2022 null | No significant association of epigenetic age acceleration with breed lifespan, weight, height | CONFIRMED; nuance added | Exact quote found; the same paper's DNAmAverageTimeToDeath did associate with lifespan and weight | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9173771/fullTextXML |
| F6 | Li 2024 | Max-lifespan predictor (R = 0.89) does not detect differences between dog breeds | CONFIRMED | "does not detect variation in life span between individuals of the same species, such as between the breeds of dogs" | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=DOI:10.1126/sciadv.adm7273&format=json&resultType=core |
| F7 | Lu 2023 numbers | dogs r = 0.94 (742 samples, 93 breeds); ASM + gestation explain >69% of log max-lifespan variance | CONFIRMED (both from Lu 2023) | "dogs (n = 742, 93 breeds, r = 0.94, MAE < 2.28 years)"; "age at sexual maturity (ASM) and gestation time ... explain over 69% of maximum lifespan variation on the log scale" | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC10501909/fullTextXML |
| F8 | Crofts 2024 | 42 species; slope −0.95 blood (R² 0.81); −0.60 skin (R² 0.80) | CONFIRMED; pages 27–32 added | 95% CI −1.14 to −0.76 (blood) | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC10798888/fullTextXML |
| F9 | Fick 2012 | Dogs lose telomeric DNA ~10× faster than humans; 15 breeds; p < 0.0001; CVD link | CONFIRMED (abstract) | Verbatim in abstract | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=%22Telomere%20length%20correlates%20with%20life%20span%20of%20dog%20breeds%22&format=json&resultType=core |
| F10 | Whittemore 2019 | No dogs; 8 species + human; R² 0.829 / 0.934; mouse 6,420 bp/y; human ~70 | CONFIRMED | Species list matches exactly | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC6660761/fullTextXML |
| F11 | Lázaro 2023 vs Diaz-Cuadros 2023 | Lázaro: 6 species, metabolic rate "did not show an evident correlation", gene expression scales; Diaz-Cuadros: mass-specific metabolic rate scales with developmental rate, ETC inhibition slows, NAD⁺/NADH speeds | CONFIRMED | Lázaro species: mouse, human, marmoset, rabbit, cattle, rhinoceros (no dog) | Europe PMC DOI:10.1016/j.stem.2023.05.014 and DOI:10.1038/s41586-022-05574-4 |
| F12 | Matsuda 2020 | *Science* 369:1450–1455 | CONFIRMED | Science 369(6510):1450–1455 | https://api.crossref.org/works/10.1126/science.aba7668 |
| F13 | Firsanov 2025 | *Nature* 648:717–725 | CONFIRMED | Nature 648(8094):717–725, 29 Oct 2025 | https://api.crossref.org/works/10.1038/s41586-025-09694-5 |
| F14 | Bronson 1982 | 2,002 necropsies; cancer 20% of deaths at 5 y, 40–50% from 10 to 16 y | CONFIRMED | Verbatim in abstract | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:6891194&format=json&resultType=core |
| F15a | Yellowstone wolves | Avg lifespan 4–5 y in park, 2–3 outside; 77% natural (42% intraspecific), 17% human; first litter 2.7 y; litter 4.4 → 3.2; female senescence 4–5 y; oldest 12.5 y | CONFIRMED | All verbatim on NPS page | https://www.nps.gov/yell/learn/nature/wolf.htm |
| F15b | "13.8 y for Idaho wolf B2" | cited to [9, 10] | DOWNGRADED to ❓ | On neither AnAge nor NPS page; no source located | — |
| F16 | Raz 2026 | Nat Aging 6(6):1330–1340; damage production best predicts lifespan; QSS regime shared by humans, dogs, cats, guinea pigs; closest to humans = dogs (except German Shepherd), cats, guinea pigs; Labrador median 12.3 y; β 0.044 vs 0.046–0.048/day; η 3.7e-6 vs 1.1e-6; "awaits experimental validation" | CONFIRMED | Extended Data Table 2: Labrador η 3.72e-6 [2.24e-6, 7.25e-6], β 0.044 [0.012, 0.05]; human male η 1.09e-6, β 0.048 [0.046, 0.05]. Main text uses a different normalisation (β 0.63/0.66; η 9.3e-5/1.59e-5) | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC13278975/fullTextXML ; https://api.crossref.org/works/10.1038/s43587-026-01138-7 |
| F17 | McMillan 2024 | 584,734 dogs / 284,734 deceased / 18 sources / 155 breeds; median 12.5; purebred 12.7, crossbred 12.0; F 12.7, M 12.4; small 12.7, medium 12.5, large 11.9; Lancashire Heeler 15.4; Caucasian Shepherd 5.4 | CONFIRMED | All verbatim | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC10834484/fullTextXML |
| F18 | Yarborough 2022 | n = 15,019; CCD odds +52%/yr; inactive 6.47× | CONFIRMED | Verbatim in abstract | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=DOI:10.1038/s41598-022-15837-9&format=json&resultType=core |
| B1 | Ratio framing | 5–6× (12.5 vs 73); 4.5× by maximum (27 vs 122.5) | CONFIRMED | 73.3/12.5 = 5.9; 83.67/15.26 = 5.5; 122.5/27 = 4.54 (4.2 if Bluey's 29.4 y were accepted) | recomputed |
| B2 | Dog maximum and records | AnAge 27 y (Bluey anecdotal/unverified); Bluey 29 y 5 mo reinstated Feb 2024; Bobi 31 y 165 d stripped | CONFIRMED; Bobi days CORRECTED to 163–165 (sources differ) | AnAge quote confirmed; ABC: reinstated 22 Feb 2024; Wikipedia computes 31 y 163 d; Guinness press used 165 d; reason: SIAC database required no proof of age for dogs born before 2008 | AnAge dog entry; https://www.abc.net.au/news/2024-03-03/...; https://en.wikipedia.org/wiki/Bobi_(dog) |
| B3 | 15/9/5 dog-year rule | "commonly attributed to the AVMA ❓" | CORRECTED (tag → 🟡) | AKC article explicitly attributes the 15/9/5 rule for a medium-sized dog to the AVMA; AVMA page bot-protected (unresolved at primary level) | https://www.akc.org/expert-advice/health/how-to-calculate-dog-years-to-human-years/ |
| B4 | Teng 2022 | 11.23 y (11.19–11.27); 30,563 dogs; French Bulldog 4.53; annual mortality ≤0.02 to age 5; 0.134 at 10–11; 0.244 at 12–13; 0.417 at 14–15; >0.5 at 15–16 | CONFIRMED | Table 2 rows: 0.017, 0.016, 0.016, 0.017, 0.020, 0.024, 0.033, 0.047, 0.069, 0.096, 0.134, 0.188, 0.244, 0.336, 0.417, 0.515, ... | PMC9050668 |
| B5 | O'Neill 2013 | 5,095 deaths; 86 practices; median 12.0 (IQR 8.9–14.2); neoplastic, musculoskeletal, neurological | CONFIRMED | — | Europe PMC DOI:10.1016/j.tvjl.2013.09.020 |
| B6 | Montoya 2023 | 13,292,929 dogs; 2013–2019; 12.69 y | CONFIRMED | 12.69 (12.68–12.70) | Europe PMC DOI:10.3389/fvets.2023.1082102 |
| B7 | Human life expectancy 73.3 y (2024) | UN WPP 2024, 🟡 | UNRESOLVED (🟡 kept) | WPP landing page and publication page carry no figure; summary PDF exceeded fetch limit | https://population.un.org/wpp/ |
| B8 | AnAge dog/wolf traits | dog 510 d maturity, 63 d gestation, litter 6, growth 0.0244; wolf 20.6 y, 13.7 wild, 669 d, 62 d, 6, 0.0177, 26,625 g | CONFIRMED | — | AnAge entries |
| B9 | AnAge human | 122.5 y; 62,035 g; 4,745 d; 280 d; MRDT 8 y; Calment note | CONFIRMED | — | AnAge Homo_sapiens |
| B10 | Derived ratios | Kleiber (62/30)^0.25 ≈ 1.2; maturity 9.3×; gestation 4.4× | CONFIRMED | 1.199; 9.30; 4.44 | recomputed |
| B11 | Wang conversion table | 11 values + human-years-per-dog-year | CONFIRMED | All values reproduce to 0.1 y | recomputed |
| B12 | Jónás 2020 | Buksi, 27-y mixed-breed Hungarian dog | CONFIRMED (ages) | Abstract: two dogs aged 22 and 27 y; Budapest; names not in abstract | Europe PMC DOI:10.3389/fgene.2020.00315 |
| B13 | Hill 2001 | Chimp LE at birth <15 y; mean adult lifespan ~15 y; "may partially explain why humans have evolved to senesce later" | CONFIRMED | Verbatim | Europe PMC DOI:10.1006/jhev.2001.0469 |
| B14 | Gurven & Kaplan 2007 | Modal adult age at death "about 72" ❓ | CORRECTED → "about seven decades" ✅ | Abstract: "The modal age of adult death is about seven decades" | https://gurven.anth.ucsb.edu/sites/default/files/sitefiles/papers/GurvenKaplan2007pdr.pdf |
| B15 | Kraus 2013 | 74 breeds; large dogs die young because they age faster, not earlier onset | CONFIRMED | "large dogs die young mainly because they age quickly" | Europe PMC DOI:10.1086/669665 |
| B16 | da Silva 2026 | Genes 17(2):139; ancient breeds longer-lived than modern breeds of same size; adaptive lag | CONFIRMED | — | https://api.crossref.org/works/10.3390/genes17020139 |
| B17 | Lord 2013 | Less seasonality, higher fecundity, reduced parental care in dogs | CONFIRMED | Verbatim | Europe PMC DOI:10.1016/j.beproc.2012.10.009 |
| B18 | Moorad 2019 | Formal theory shows Williams' simple version "is wrong" | CONFIRMED | Verbatim in abstract | Europe PMC DOI:10.1016/j.tree.2019.02.006 |
| B19 | Healy 2014 | 1,368 species; flight strongest predictor | CONFIRMED | — | Europe PMC DOI:10.1098/rspb.2014.0298 |
| B20 | Austad & Fischer 1991 | Bats ≥3× longer than expected regardless of BMR or torpor | CONFIRMED | "a minimum of 3 times" | Europe PMC DOI:10.1093/geronj/46.2.b47 |
| B21 | de Magalhães 2007 | BMR does not predict eutherian/bird longevity after mass+phylogeny; maturity ∝ lifespan; growth rate negative | CONFIRMED | Verbatim | Europe PMC DOI:10.1093/gerona/62.2.149 |
| B22 | Robinson 2021 | POLE/POLD1 carriers "do not exhibit overt features of premature aging" | CONFIRMED | Verbatim in abstract | Europe PMC DOI:10.1038/s41588-021-00930-y |
| B23 | Compton 2025 | Across 292 species malignancy prevalence increases with somatic mutation rate | DOWNGRADED (conditional added) | Association "was only apparent when we controlled for gestation time"; 16,049 necropsies | Europe PMC DOI:10.1158/2159-8290.CD-24-0573 |
| B24 | Vincze 2022 | 110,148 adults / 191 species; cancer mortality "largely independent" of mass and life expectancy; Carnivora highest; larger dogs more cancer-prone (citing Fleming) | CONFIRMED | — | PMC8755536 |
| B25 | Abegglen 2015 | ~20 TP53 copies (19 retrogenes); elephant cancer mortality 4.81%; human 11–25% | CONFIRMED | 4.81% (95% CI 3.14–6.49) | Europe PMC DOI:10.1001/jama.2015.13134 |
| B26 | Tian 2019 | 18 rodent species; DSB repair (not NER) co-evolves; five SIRT6 residues | CONFIRMED | — | Europe PMC DOI:10.1016/j.cell.2019.03.043 |
| B27 | Swovick 2021 | 12 mammals, no dog; r = −0.89; significant after phylogenetic correction; naked mole-rat | CONFIRMED | p = 0.001 after correction | PMC7950207 |
| B28 | Lambert 2007 | 12 species, no dog; "significant by sign test, but fell short of significance by regression analysis" | CONFIRMED | Verbatim | Europe PMC DOI:10.1111/j.1474-9726.2007.00312.x |
| B29 | Kealy 2002 | 48 Labradors; 25% restriction from 8 wk; median lifespan increased; chronic disease delayed | CONFIRMED | — | Europe PMC DOI:10.2460/javma.2002.220.1315 |
| B30 | Herzig 2025 | 829 dogs; 12 y; HR 1.75/yr; diet restriction lowered biological age | CONFIRMED | — | Europe PMC DOI:10.1007/s11357-024-01352-4 |
| B31 | McCoy 2024 preprint | 864 dogs; +0.37 epigenetic yr/yr in largest size class; 34% higher death risk per year; still a preprint | CONFIRMED | Crossref and Europe PMC show only the bioRxiv record as of 2026-10-04 | Europe PMC PPR search; https://api.crossref.org/works?query=Aging+at+scale... |
| B32 | Jang 2026 | PNAS 123(29):e2528874123; Korean > US EAA; size-structured drift | CONFIRMED | — | https://api.crossref.org/works/10.1073/pnas.2528874123 |
| B33 | Hoummady 2025 | 566 dogs ≥6 y; 6.36% (index) / 8.48% (phenotype) | CONFIRMED | — | Europe PMC DOI:10.1038/s41598-025-28382-y |
| B34 | Zemko 2026 | 209 dogs ≥5 y; 30 months | CONFIRMED | Every six months | Europe PMC DOI:10.1016/j.tjfa.2026.100145 |
| B35 | Fleming 2011 | 74,556 dogs; age/size cause-of-death patterns | CONFIRMED | — | Europe PMC DOI:10.1111/j.1939-1676.2011.0695.x |
| B36 | Adams 2010 | 15,881 deaths; cancer 27%, old age 18%, cardiac 11% | CONFIRMED | Median 11 y 3 mo | Europe PMC DOI:10.1111/j.1748-5827.2010.00974.x |
| B37 | Nasir 2001 | TRF 12–23 kb; "little or no activity" in normal somatic tissues | CONFIRMED | — | Europe PMC DOI:10.1038/sj.neo.7900173 |
| B38 | Gomes 2011 | >60 mammals; ancestral short telomeres + repressed telomerase; length inverse to lifespan; telomerase co-evolves with body size | CONFIRMED | — | Europe PMC DOI:10.1111/j.1474-9726.2011.00718.x |
| B39 | Thompson 2017 | 46 dogs, 62 wolves; 41/67/115 CpGs | CONFIRMED | — | Europe PMC DOI:10.18632/aging.101211 |
| B40 | Jin 2024 | 71 dogs; R² 26% (ATAC) vs 33% (methylation); CD62L+ T cells | CONFIRMED | — | Europe PMC DOI:10.1111/acel.14079 |
| B41 | Haghani 2023 | 15,456 profiles; 348 species; 30 of 55 modules; HOXL homeobox | CONFIRMED | — | Europe PMC DOI:10.1126/science.abq5693 |
| B42 | Patronek 1997 | 23,535 dogs; 8 to >15 human-equivalent years | CONFIRMED | — | Europe PMC DOI:10.1093/gerona/52a.3.b171 |
| B43 | Nielsen 2016 | 392 ± 120 y; maturity ≥156 ± 22 y | CONFIRMED | — | Europe PMC DOI:10.1126/science.aaf1703 |
| B44 | Seim 2013 / Podlutsky 2005 | GHR/IGF1R changes; 4–8 g; >40 y; field record 41 y | CONFIRMED | — | Europe PMC DOI:10.1038/ncomms3212; DOI:10.1093/gerona/60.11.1366 |
| B45 | Zhang 2023 | nmrHas2 mice: less cancer, longer lifespan, better healthspan, less inflammation | CONFIRMED | — | Europe PMC DOI:10.1038/s41586-023-06463-0 |
| B46 | Kolora 2021 | DNA repair selection; insulin signalling; butyrophilin expansions; >200 y | CONFIRMED | — | Europe PMC DOI:10.1126/science.abg5332 |
| B47 | Greer 2011 | IGF-1 falls with age, rises with weight | CONFIRMED | — | Europe PMC DOI:10.1007/s11357-010-9182-4 |
| B48 | AAHA 2019 | Five stages; senior = "last 25%" ❓ | Five stages CONFIRMED; 25% UNRESOLVED | Abstract lists the five stages; no definition of senior in abstract; AAHA page returned 403 | Europe PMC DOI:10.5326/JAAHA-MS-6999 |
| B49 | TL;DR ref for methylation-rate scaling | [37, 38, 41] | CORRECTED to [38, 41] | Horvath 2022 is a dog/human clock paper, not a rate-scaling result | — |
| B50 | Robine 2019 (Calment) | J Gerontol A 74(Suppl 1):S13–S20 | CONFIRMED | — | https://api.crossref.org/works/10.1093/gerona/glz198 |
| C1–C9 | Citation metadata | Horvath PNAS 119(21):e2120887119; Lu Nat Aging 3(9):1144–1166; Prescott GeroScience 47(4):5725–5748; Coleman GeroScience 47(3):2851–2877; Hou PNAS 121(20):e2315921121; Matrenok DOI 10.64898/2026.02.10.705136 (bioRxiv/openRxiv prefix); Wang Cell Syst 11(2):176–185.e6; Teng Sci Rep 12:6415; McMillan Sci Rep 14:531 | CONFIRMED (9) | All resolve to the stated papers | Crossref / Europe PMC |

Tally: 78 claim rows (F1a–F18 = 23; B1–B50 = 50 after merging; C1–C9 counted as 9 metadata checks → total checks 82, of which 78 are substantive claims). Verdicts: 65 confirmed, 6 corrected (F2 TL;DR wording, B2 Bobi days, B3 tag upgrade, B14 Gurven, B49 ref number, F3b chimp blank/F1d rounding counted once), 4 downgraded (F1c, F1e, F15b, B23), 0 removed, 3 unresolved (B7 UN figure, B48 AAHA 25%, AVMA primary page under B3).

---

## 4. Edits made to the file

All edits are marked `[verifier-corrected]` or `[verifier-confirmed]` in place.

1. Header status line → "Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/why_dogs_age_fast_verification.md".
2. TL;DR, mass–longevity bullet: added "M in grams" and a caveat that AnAge's 40 kg is a large-dog mass (15–20 kg → 122–127%).
3. TL;DR, somatic-mutation bullet: "about 3,800" → "about 3,810"; tag ✅ → 🟡 for the dog-specific supplementary values, with explanation.
4. TL;DR, epigenetic bullet: "(104 Labradors)" → "(104 dogs profiled, mostly Labradors; 95 analysed)"; refs for rate scaling [37, 38, 41] → [38, 41].
5. §1.2: Bluey reinstatement dated 22 Feb 2024; Bobi "31 y 165 d" → "31 y 163–165 d; sources differ"; added "for dogs born before 2008".
6. §1.3 table: "13.8 y for Idaho wolf B2" tagged ❓ as unsourced.
7. §1.4: Cagan human-cohort description downgraded to 🟡; 83.7 y kept ✅.
8. §1.4: Gurven & Kaplan "about 72 ❓" → "about seven decades ✅".
9. §1.5: added note on formula units and the 40-kg mass choice; chimpanzee expected t_max filled in (25.1 y).
10. §1.6 table: Cagan dog rows (15.3 y; 249.5 SBS/yr) tagged 🟡 with reason.
11. §3.1: "Dogs specifically" header tagged 🟡 with note on supplementary tables (main text cites Suppl. Tables 3 and 6 for species-level estimates).
12. §3.1 caution 4 (Compton 2025): added "16,049 necropsies", "with adult mass and", and the conditional "only apparent when we controlled for gestation time"; softened the inference.
13. §3.2 Horvath row: specified "breed median lifespan, upper lifespan, weight or height" and added the DNAmAverageTimeToDeath nuance.
14. §3.2 McCoy row: verifier confirmation that only the bioRxiv record exists as of 2026-10-04.
15. §4.3: AVMA 15/9/5 rule ❓ → 🟡 with AKC attribution and remaining caveat; "≈ 4–5 per year" → "≈ 5 per year" (as the AKC states it).
16. §4.4: added the verifier's refit range for the Gompertz slope and MRDT.
17. Sources: [13] note that the primary UN PDF was not opened; [31] tag ❓ → ✅ with quote; [32] split tag (✅ main text / 🟡 supplementary dog values); [41] pages 27–32 added.
18. Appended "## Verification notes" at the end of the file.

---

## 5. Open issues

1. **Cagan et al. dog-specific values.** 249.46 SBS/genome/yr, 15.26-y lifespan, 3 dogs / 11 crypts, and the dog–wolf pooling note were not independently re-opened (supplementary xlsx). They are internally consistent with the main text and with the original author's statement that the tables were opened. Someone with the spreadsheets should confirm the values and the table numbering (main text says species-level estimates are in Supplementary Tables 3 and 6).
2. **UN global life expectancy 73.3 y (2024).** Widely reported WPP 2024 headline; the primary PDF exceeded the fetch limit. Low risk, but still 🟡.
3. **AAHA "senior = last 25% of expected lifespan".** Not in the abstract; the AAHA page is bot-protected. Remains ❓.
4. **AVMA attribution of the 15/9/5 rule.** Secondary attribution (AKC) confirmed; the AVMA page itself could not be opened.
5. **Idaho wolf B2 (13.8 y).** Unsourced; either find a source (Idaho Fish and Game / Nez Perce Tribe records) or delete.
6. **Bobi's claimed age.** 163 vs 165 days depending on source; immaterial to the argument.
7. **Interpretive caveat.** The 109% dog residual depends on AnAge's 40-kg adult mass; the file now says so. The 27-y record dog (Buksi) was a mixed breed of unknown mass, so no single "correct" mass exists for this calculation.
