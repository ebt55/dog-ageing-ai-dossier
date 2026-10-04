# Verification report: breed size and lifespan; wolves vs dogs
> Part of the dog-ageing research dossier · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> Independent fact-check by Opus 5.5 · 2026-10-04
>
> Files audited (both written by Fable 5.1 on 2026-10-04):
> - `04_dog_aging_biology/breed_size_genetics_lifespan.md`
> - `04_dog_aging_biology/wolves_vs_dogs.md`
>
> Method:
> - About 85 web and API calls: Europe PMC REST abstracts and full-text XML, PMC pages, bioRxiv, Crossref, AnAge, NPS, TIME/CNN, WebSearch.
> - Local text extraction from four PDFs: Kealy 2002 (JAVMA), the Tidière 2016 supplement, Holyan et al. 2005, and the Ko & Shin 2025 full text via XML.
>
> Every in-place change is marked `[verifier-corrected]` (or `[verifier-added]` / `[verifier note]`). Each file ends with a "Verification notes" section.

---

## Overall reliability: **MEDIUM-HIGH**

**Why:**
- **No fabricated citations were found.** Every DOI, PMID and PMCID tested resolved to the stated paper with the stated authors, year and journal. Bibliographic gaps (missing titles, volumes or DOIs) were filled.
- **The headline numbers hold up.** The following were confirmed against primary full text or abstracts:
  - Every lifespan figure from McMillan 2024, Teng 2022 and Montoya 2023, including all breed medians.
  - The genetics variance-explained figures: Rimbault 46–52.5% / 64.3%; Plassais 2019 "as much as 95%" with 14 genes.
  - Eigenmann 6× / r = 0.88.
  - Cancer odds ratios: Edmunds 45.44; O'Neill 118.40.
  - Inbreeding figures: Bannasch F = 0.249 / RR 1.22 / 1.29; Yordy 95% / 46%.
  - Hoffman +13.8% / +26.3%.
  - Kealy 13.0 vs 11.2 y (from the primary results section).
  - Wolf life-history numbers: AnAge and NPS.
  - Thompson 2017 statistics and DOI.
  - Zou 2015 details.
- **The author's self-flagged uncertainties were mostly well placed.** The suspected Ko & Shin "40% faster" misattribution is real.
- **Errors are mostly about precision and overstated certainty, not invented facts.** The most substantive problems:
  1. **Horvath 2022 EWAS misread.** The file said the top EWAS CpGs were in *SMAD2* and *IGF1R*. In fact the top hits were *SF1* (lifespan) and *TTC8* (weight/height). The *SMAD2/IGF1R* CpGs (4 + 1 of 47 probes) came from a candidate-gene look-up that the authors themselves call "modest". This had propagated into §2.5 and the mechanism table.
  2. **Preprints tagged ✅ as if established.** McCoy 2024 is still unreviewed, and its mortality HR rests on 49 deaths.
  3. **A doubtful captive-wolf lifespan figure.** The "9–16 y typical captive lifespan" comes from a review that cites a *wild*-wolf paper (Mech 1988) for it.
  4. **Overstated generalisations:**
     - "2–4 y small-vs-giant gap" across studies: only Banfield has a giant class.
     - "~14% more variants" in wolves: it is *structural* variants.
     - "Wolves reach ≥20 years": this is one record.
     - "Conflicts with Perri 2021": the dire-wolf paper is now peer-reviewed with Perri as co-author, and it partly revises rather than contradicts her result.
- **Several open questions were resolved:**
  - Tidière 2016 does **not** include *Canis lupus*.
  - The Thompson DOI is confirmed.
  - The dire-wolf ancestry paper is published (*Cell Genomics* 2026).
  - McCoy 2024 is still not peer-reviewed.

**Spot-check of ✅-tagged claims:** about 70 were sampled across both files.
- About 58 were fully correct.
- About 12 needed correction or downgrade. Most were precision fixes. One changed meaning: the Horvath *SMAD2/IGF1R* claim.

---

## Counts

| | Breed file | Wolves file | Total |
|---|---|---|---|
| Claims checked | 64 | 45 | **109** |
| Confirmed | 47 | 33 | **80** |
| Corrected | 11 | 7 | **18** |
| Downgraded | 2 | 2 | **4** |
| Removed | 0 | 0 | **0** |
| Unresolved | 4 | 3 | **7** |

(Over 30 citations were spot-checked for existence, metadata and support of the sentence.)

---

## Claim table

### A. `breed_size_genetics_lifespan.md`

| # | Claim | As written | Verdict | Correct value / note | Source |
|---|---|---|---|---|---|
| B1 | Kraus 2013: ageing *rate*, not onset, drives size effect | rate ↑ with size; no clear onset link; baseline slightly higher | CONFIRMED | Abstract verbatim agrees | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:23535614&format=json&resultType=core |
| B2 | "~1 month lost per 2 kg" | press only 🟡 | UNRESOLVED | In NBC/LiveScience (6 Mar 2013) and, per search excerpt, Selman et al. 2013 *Curr Biol* dispatch; Kraus full text not accessible | https://www.nbcnews.com/news/all/why-little-dogs-outlive-big-dogs-flna1C8737416 ; https://doi.org/10.1016/j.cub.2013.04.005 |
| B3 | Kraus 2013 correction notice | not mentioned | UNRESOLVED | A "Correction" (doi:10.1086/670646) exists; content not accessible | https://api.crossref.org/works/10.1086/670646 |
| B4 | McMillan cohort | 584,734 dogs, 284,734 deceased, 18 sources, 155 breeds | CONFIRMED | Exact | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC10834484/fullTextXML |
| B5 | McMillan size medians | 12.7 / 12.5 / 11.9 y | CONFIRMED | Exact (no giant class) | same |
| B6 | McMillan cephalic | brachy 11.2 / meso 12.8 / dolicho 12.1 | CONFIRMED | Exact | same |
| B7 | McMillan purebred vs crossbred; sex | 12.7 vs 12.0; F 12.7 vs M 12.4 | CONFIRMED | Exact | same |
| B8 | McMillan breed medians | Lancashire Heeler 15.4, Tibetan Spaniel 15.2, Shiba 14.6, French Bulldog 9.8, Mastiff 9.0, Cane Corso 8.1, Presa 7.7, Caucasian Shepherd 5.4 | CONFIRMED | Exact | same |
| B9 | Teng 2022 life expectancy | 11.23 y; 30,563 deaths; JRT 12.72 … French Bulldog 4.53; Yorkie 12.54; Border Collie 12.10; Lab 11.77; SBT 11.33; English Bulldog 7.39 | CONFIRMED | Exact | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9050668/fullTextXML |
| B10 | Teng caveat on growing breeds | popularity depresses French Bulldog life expectancy | CONFIRMED | KC registrations rose 2,771 → 39,266 (2011–2020); explicit caveat | same |
| B11 | Teng neuter/sex values | NF 11.98, EF 10.50, NM 11.49, EM 10.58; F 11.41 vs M 11.07 | CONFIRMED | Exact | same |
| B12 | TL;DR neutering gain in UK tables | "+1–1.5 y" | CORRECTED | +0.9 y (males) to +1.5 y (females) | same |
| B13 | Montoya size classes | toy 13.36, small 13.53, medium 12.70, large 11.51, giant 9.51 | CONFIRMED | Exact (purebreds); Banfield rounded values match | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9989186/fullTextXML |
| B14 | Montoya BCS and sex | BCS5 11.71 vs BCS3 13.18; F 12.76 vs M 12.63; overall 12.69 | CONFIRMED | Exact (BCS4 13.14) | same |
| B15 | Montoya period | "2013–2022" | CORRECTED (minor) | Records Jan 2013–Jul 2022; life tables for survey years 2013–2019 | same |
| B16 | TL;DR size-lifespan gap | "2–4 y between small and giant classes [4][5][6]" | CORRECTED | ~4.0 y only in Banfield (giant class); 0.8 y small vs large in McMillan; Teng has no size classes | sources above |
| B17 | Rimbault 2013 | 7 markers 46–52.5%; 64.3% in breeds <41 kg | CONFIRMED | Exact (title says "six genes") | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:24026177&format=json&resultType=core |
| B18 | Plassais 2019 | 14 genes "as much as 95%" of SBW; 722 WGS; 144 breeds; 54 wild canids; >91 M variants | CONFIRMED | Exact; abstract says ">90%" | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC6445083/fullTextXML |
| B19 | Plassais 2022 scope | 1,431 genomes / 13 species; IGF1-AS ancestral small allele | CONFIRMED | Exact | https://pmc.ncbi.nlm.nih.gov/articles/PMC8891063/ |
| B20 | Plassais 2022 ancient wolf age | "~54,000-year-old" (TL;DR); "53–54 kyr" (§2.1) | CORRECTED | 53,000-year-old Pleistocene Siberian wolf, heterozygous (PP(CT) > 0.9) | same |
| B21 | Plassais 2022 allele letters; 75% statistic | C small (press 🟡); 75% of homozygotes <15 kg | CONFIRMED (upgraded to ✅) | C = ancestral small, T = derived large (rs22397284); 75% (Q3) of CC dogs have BMA <15 kg | same |
| B22 | Eigenmann 1984 | standard ~6× toy IGF-I; r = 0.88; similar GH response | CONFIRMED | Exact | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:6382895&format=json&resultType=core |
| B23 | Horvath 2022: no age-acceleration association | no significant association with breed weight/lifespan | CONFIRMED | "we found no significant results" (lifespan, max lifespan, weight, height) | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC9173771/fullTextXML |
| B24 | Horvath EWAS top CpGs | "top CpGs … lie in SMAD2 and IGF1R"; EWAS "points back to IGF1R/SMAD2" | CORRECTED | Top EWAS hits: *SF1* exon (lifespan, z = −6.3), *TTC8* intron (weight z = 7.2; height z = 6.2). Only 4 CpGs near *SMAD2* + 1 in *IGF1R* (of 47 candidate-gene probes) track weight and lifespan: "modest" | same |
| B25 | Horvath stats | 742 samples / 93 breeds; Great Dane 6.3 (64 kg), Toy Poodle 14.6 (2.3 kg); R = 0.97; MAE <0.58 y; telomere overlap P = 1.2e-6 | CONFIRMED | Exact | same |
| B26 | Ko & Shin 2025 "40% faster" misattribution | misattributed to Horvath | CONFIRMED | Ko & Shin ref. 60 = Horvath 2022; Horvath has no 40% and found no significant age-acceleration association | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC12520860/fullTextXML |
| B27 | McCoy 2024 numbers | n = 864; +0.37 y/y largest vs smallest; HR 1.34 (1.06–1.69) | CONFIRMED | Exact; 49 deaths in survival analysis | https://www.biorxiv.org/content/10.1101/2024.10.03.616519v2 |
| B28 | McCoy 2024 evidence status | ✅ | DOWNGRADED → 🟡 | Still a bioRxiv preprint (v2, 29 Oct 2024); no journal version in bioRxiv or Europe PMC as of 2026-10-04 | same; Europe PMC author search |
| B29 | Sohrab 2026 counts | 7,627 dogs; 298 loci; 159 traits; 976 profiled; 957 with 3-y follow-up | CONFIRMED | Exact; 11% died | https://www.biorxiv.org/content/10.64898/2026.03.07.710297v1.full |
| B30 | Sohrab human overlap | "27% overlap human loci" | CORRECTED (clarified) | 27% of 181 distinct dog loci; 79% of the 14 strongest | same |
| B31 | Sohrab GH metabolites | lower mortality hazards | CONFIRMED | "GH-related metabolites had lower absolute mortality hazard ratios (mean \|z\| 0.96 vs 1.35; p = 0.0092)" | same |
| B32 | Nunney 2024 core | multistage fit, ~4 drivers, 85 breeds, inbreeding shortens lifespan but no cancer effect | CONFIRMED | Abstract | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:38298404&format=json&resultType=core |
| B33 | Nunney breed list | four breeds "have elevated cancer mortality" | CORRECTED | Only flat-coated retriever significant; other three "notable" (>50% over expected) | same |
| B34 | Edmunds 2021 | OR 45.44 (>40 kg vs <10 kg) | CONFIRMED | Exact (1,756 cases) | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:33750475&format=json&resultType=core |
| B35 | O'Neill 2023 osteosarcoma | OR 118.4; 905,552 dogs; title unknown | CONFIRMED (+ title supplied) | "Dog breeds and conformations predisposed to osteosarcoma in the UK: a VetCompass study", *Canine Med Genet* 10:8; 331 cases; Leonberger 55.79, Great Dane 34.24, Rottweiler 26.67, chondrodystrophic 0.10 | https://doi.org/10.1186/s40575-023-00131-2 |
| B36 | Bannasch 2021 numbers | F = 0.249 (0.235–0.263); RR 1.01 / 1.22 / 1.29; r² = 0.77 | CONFIRMED | Exact | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC8638537/fullTextXML |
| B37 | Bannasch method | "227 breeds, Illumina HD 173K SNPs" | CORRECTED | 227-breed F from commercial-panel heterozygosity (49,378 dogs), adjusted with an Illumina HD 173K dataset | same |
| B38 | Yordy 2020 | 4,586 dogs / 117 breeds; size + purebred = 95% (purebred 46%); +1.2 y mixed | CONFIRMED | Exact; e(2) from VMDB | https://pmc.ncbi.nlm.nih.gov/articles/PMC7326369/ |
| B39 | Hoffman 2013 | +13.8% M / +26.3% F; 70,574 / 40,139 | CONFIRMED | Exact | https://www.ebi.ac.uk/europepmc/webservices/rest/PMC3629191/fullTextXML |
| B40 | Kealy 2002 medians | 13.0 vs 11.2 y (🟡 secondary) | CONFIRMED (upgraded to ✅) | Primary text: control 11.2 vs restricted 13.0 y, P < 0.01; 90%-mortality age 12.9 vs 14.0 (n.s.) | Kealy 2002 PDF (JAVMA 220:1315) |
| B41 | Greer 2007 | r = −0.679 (weight), −0.603 (height) | CONFIRMED | Exact | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:16919689&format=json&resultType=core |
| B42 | Fleming 2011 neoplasia details | larger breeds more neoplastic deaths; neoplasia peaks ~10 y (✅ abstract) | DOWNGRADED → 🟡 | Abstract says larger breeds: musculoskeletal and GI; older dogs: neurologic and neoplastic. Size-neoplasia and ~10-y peak not in abstract | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=EXT_ID:21352376&format=json&resultType=core |
| B43 | O'Neill 2013 | 102,609 dogs; median 12.0; crossbred +1.2 y | CONFIRMED | Exact | EXT_ID:24206631 (Europe PMC) |
| B44 | Urfer 2020 | 20,970 dogs; size ↓; neuter ↑; Mountain clade 3.5–4.6 y shorter | CONFIRMED | Exact; also found no purebred/mixed difference (added to §4.3) | EXT_ID:32835231 |
| B45 | Kraus 2023 | >40,000 dogs, 118 breeds; diversity ↑ lifespan; size ↑ proportional cancer | CONFIRMED | Exact (owner-reported public database, not VMDB) | EXT_ID:36066765 |
| B46 | Nam 2024 | 27,541 dogs; disease-category directions | CONFIRMED | Exact | PMC10793924 |
| B47 | Galis 2007 | within-breed relationship slightly positive | CONFIRMED | Exact | EXT_ID:16788896 |
| B48 | Fick 2012 | 15 breeds; p < 0.0001; ~10× faster loss | CONFIRMED | Exact | EXT_ID:23260664 |
| B49 | Sutter 2007 / Gray 2010 / Hoopes 2012 | IGF1 haplotype; Middle Eastern wolves; IGF1R R204H | CONFIRMED | Exact (Hoopes: *Mamm Genome* 23(11–12):780–790) | EXT_ID:17412960; 20181231; DOI 10.1007/s00335-012-9417-z |
| B50 | Greer 2011 | IGF-1 rises with weight, falls with age | CONFIRMED | Exact | EXT_ID:20865338 |
| B51 | Guevara-Aguirre 2011 | 22 y; 1 non-lethal malignancy; 17% / 5% in controls | CONFIRMED | Exact | EXT_ID:21325617 |
| B52 | Ames dwarf lifespan | "~40–50%" | CORRECTED (stays 🟡) | Commonly cited ~49% and ~64–68% (sex-specific; secondary sources differ) | Brown-Borg 1996, doi:10.1038/384033a0 (secondary summaries) |
| B53 | Jimenez 2018 sample breakdown | "32 breeds; 11/21 puppies; 15/22 seniors" | UNRESOLVED | Not found in the text; assay-specific N differ (e.g., 27/16/52/25) | PMC5918822 |
| B54 | Brookes 2021; Harper 2025 | metabolomics; no stress-resistance difference (n 18/32/11/23) | CONFIRMED | Exact (Harper: *GeroScience* 47(3):3665–3675) | EXT_ID:34132979; 39316259 |
| B55 | Turcsán & Kubinyi 2024 | >30 kg: onset 2–3 y earlier, slower decline; >15,000 dogs | CONFIRMED | Exact | EXT_ID:37740140 |
| B56 | Ko et al. 2025 *Mol Cells* | lifespan hits *IGSF1, ARHGAP36*; BMI hits *MSRB3, HMGA2, IGF1, IGSF1* | CONFIRMED | Full text agrees | PMC11721540 |
| B57 | Korec 2024 | 24 vs 17 CKCS; 15 SNPs / 9 genes | CONFIRMED (citation corrected) | *Vet Anim Sci* 27:100420 (2025), doi:10.1016/j.vas.2024.100420 | PMC11737349 |
| B58 | Wess 2010; Awano 2009 | DCM prevalence 3.3%→44.1%, cumulative 58.2%; SOD1 E40K | CONFIRMED | Exact | EXT_ID:20202106; 19188595 |
| B59 | Dog10K diversity | "wolves carry ~14% more variants per genome" | CORRECTED | ~14% more *structural variants* (>50 bp indels) per genome | PMC10426128 |
| B60 | Loyal LOY-001 | FDA CVM RXE 28 Nov 2023; IGF-1 lowering; 3–6-monthly injection | CONFIRMED | Exact | https://loyal.com/posts/loyal-announces-historic-fda-milestone-for-large-dog-lifespan-extension-drug |
| B61 | Jang 2026 body-size direction | not captured | UNRESOLVED | Published PNAS 123(29) e2528874123; abstract gives no direction; full text 403 | https://www.ebi.ac.uk/europepmc/webservices/rest/search?query=DOI:10.1073/pnas.2528874123&format=json&resultType=core |
| B62 | §6.6 wolves in captivity | "reach ≥20 years" | CORRECTED | Single AnAge record (~20.6 y, one wild-born male) | https://genomics.senescence.info/species/entry.php?species=Canis_lupus |
| B63 | Thompson 2017 age acceleration vs weight | r = 0.25, n.s., n = 46 | CONFIRMED | Exact | PMC5391218 |
| B64 | Plassais 2017 PLoS Genet | X-chromosome loci (🟡 not opened) | CONFIRMED (title only) | Title verified, PMC5357063 | https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5357063/ |

### B. `wolves_vs_dogs.md`

| # | Claim | As written | Verdict | Correct value / note | Source |
|---|---|---|---|---|---|
| W1 | AnAge max longevity | 20.6 y (captivity) | CONFIRMED | "One wild born male was around 20.6 years old when he died in captivity"; sample size large, quality high | https://genomics.senescence.info/species/entry.php?species=Canis_lupus |
| W2 | Wild record | 13.7 y | CORRECTED (nuance) | AnAge note says 13.7 y; wolf B-2 (Idaho) estimated at 13.8 y at death (cementum suggested 11 y); 9013 at 13.2 y | AnAge; https://www.nps.gov/yell/learn/nature/wolf.htm ; Holyan et al. 2005 *Can Field-Nat* 119:447 |
| W3 | AnAge life history | 669 d maturity; 62 d gestation; litter 6; 365 d interval; 26,625 g; 10-y-old females breed | CONFIRMED | Exact (litters/yr 0.8) | AnAge |
| W4 | NPS Yellowstone life history | M 100–130 lb, F 80–110 lb; 4–5 y in park, 2–3 y outside; oldest 12.5 y; first litter 2.7 y; 4.4 → 3.2 pups | CONFIRMED | Exact (page updated 9 Sep 2026) | https://www.nps.gov/yell/learn/nature/wolf.htm |
| W5 | NPS mortality | 42% intraspecific, 17% human, 8% interspecific, 5% malnutrition, 3% disease | CONFIRMED | Exact (+15% natural-unknown, 4% other, 6% unknown) | same |
| W6 | Wolf 1090F | ~12 y in Jan 2026 (press) | CONFIRMED | 11 y 9 mo ("nearly 12"), Cowboy State Daily 10 Jan 2026 | https://cowboystatedaily.com/2026/01/10/yellowstone-wolf-1090f-hits-longevity-milestone/ |
| W7 | Cubaynes 2014 | 280 wolves, 13 y; >6 y lower survival; density-dependent aggression | CONFIRMED | Exact | EXT_ID:24749694 |
| W8 | Borg 2015 | 26 y; 387 wolves; 77% of 53 dissolutions | CONFIRMED | Exact | EXT_ID:25041127 |
| W9 | Robinson 2019 | Isle Royale inbreeding depression from strongly deleterious recessives | CONFIRMED | Exact | EXT_ID:31149628 |
| W10 | Oliynyk 2023 | human mortality 10.0% → 35.8%; survival 0.783 → 0.566 | CONFIRMED | Mortality 21.7% → 43.4% (= survival 0.783 → 0.566); *Sci Rep* 13:11084 | PMC10329645 |
| W11 | Typical captive lifespan | "~9–16 y" 🟡 | DOWNGRADED → 🟡❓ | Review attributes it to Mech 1988, a *wild*-wolf longevity note; same review cites sanctuary deaths at 5–19 y (Lawler 2016) | PMC13314318 |
| W12 | Tidière 2016 includes wolves? | unknown ❓ | CORRECTED (resolved: No) | 61 species in supplementary table; canids are *Lycaon*, *Nyctereutes*, *Urocyon*, *Vulpes*; no *Canis lupus* | srep36361 supplementary PDF; PMC5098244 |
| W13 | Thompson 2017 statistics | 46 dogs / 62 Yellowstone wolves; 41/67/115 CpGs; LOO r ≈ 0.8, MAE 0.8; r = 0.65/0.54; r = 0.07; r = 0.20 | CONFIRMED | Exact; wolves young (median 2 y, range 0.5–8) | PMC5391218 |
| W14 | Thompson DOI | "believed 10.18632/aging.101211" | CONFIRMED | DOI confirmed; PMID 28373601 | same |
| W15 | Horvath 2022 has no wolves | no wolves | CONFIRMED | Dog samples only | PMC9173771 |
| W16 | Lu 2023 includes wolves? | unknown ❓ | UNRESOLVED | Main text never mentions wolves; species list only in supplements (not checked) | PMC10501909 |
| W17 | Jimenez & Downs 2020 | dog lipid damage ↑ with age; wild-canid TAC/GPx ↑; small breeds higher lipid damage | CONFIRMED | Exact | EXT_ID:32609535 |
| W18 | Review quote | "unusual for wild gray wolves to reach or surpass 10 years" | CONFIRMED | Present (cites Lawler 2016; Barber-Meyer 2021) | PMC13314318 |
| W19 | Axelsson 2013 | 3.8 M variants; 36 regions; 19 brain; 10 starch/fat | CONFIRMED | Exact | EXT_ID:23354050 |
| W20 | Arendt 2014; Ollivier 2016 | 🟡 not opened | CONFIRMED (upgraded to ✅) | Abstracts support claims | DOI 10.1111/age.12179; 10.1098/rsos.160449 |
| W21 | vonHoldt 2017 | *GTF2I/GTF2IRD1*; 5-Mb CFA6 | CONFIRMED | Exact | EXT_ID:28776031 |
| W22 | Garamszegi 2023 wolf n | 55 wolves | CORRECTED (→ 🟡) | Press release: 48 wolf specimens; 865 dogs / 159 breeds confirmed | https://phys.org/news/2023-05-brains-modern-dog-larger-ancient.html |
| W23 | Garamszegi 2023 statistics | 24.32%; β = 0.745; pMCMC = 0.652 | UNRESOLVED | Paper not open access; press gives ~131 vs ~100 cm³ (~24%) | same |
| W24 | Garamszegi & Kolm 2024 | 25 canids; residual −0.101; 7 with larger residuals | CONFIRMED | Exact | PMC11299805 |
| W25 | TL;DR "not unusual among canids" | not unusual | CORRECTED | "not an unambiguous singularity"; sensitive to ancestral-value assumptions; raccoon dog is the outlier | same |
| W26 | Drake 2011 | 677 dogs / 106 breeds vs 401 wolves; "not paedomorphic wolves" | CONFIRMED | Exact | EXT_ID:21410876 |
| W27 | Lord 2013 | decreased seasonality, increased fecundity, reduced parental care | CONFIRMED | Exact | EXT_ID:23124015 |
| W28 | Dog10K counts | 1,987 canids; 1,611 dogs (321 breeds); 309 village; 63 wolves; 4 coyotes; >48 M variants; 14.7% wolf-only | CONFIRMED | Exact (an author correction exists, doi:10.1186/s13059-023-03101-w) | PMC10426128 |
| W29 | Dog10K "14% more variants" | variants | CORRECTED | 14% more *structural* variants | same |
| W30 | mCanLor1.2 | 98.91% in 40 pseudomolecules incl. X, Y | CONFIRMED | Exact; authors Sinding … Gilbert, *Wellcome Open Res* 6:310 | EXT_ID:34926833 |
| W31 | Greenland-wolf variant map (2024) | authors unknown, 🟡 | CONFIRMED | Nguyen A, Schall PZ, Kidd JM; 1,929 samples remapped | DOI 10.1101/2024.06.03.597150 |
| W32 | Colossal edits | 20 edits / 14 genes; 15 dire-wolf + 5 coat (MC1R, MFSD12) | CONFIRMED (stays 🟡, press/company) | TIME: "20 edits in 14 genes"; Wikipedia: 15 + 5 | https://time.com/7274542/colossal-dire-wolf/ |
| W33 | Colossal method | EPCs + CRISPR + SCNT into dog oocytes; dog surrogates | CONFIRMED (🟡) | TIME (EPCs, denucleated ova); CNN (donor eggs from domestic dogs) | TIME; https://www.cnn.com/2025/04/07/science/dire-wolf-de-extinction-cloning-colossal |
| W34 | Colossal efficiency | 45 ova → 4 viable embryos | UNRESOLVED (partly confirmed) | 45 engineered ova confirmed (TIME); "4 viable embryos" only in Wikipedia/derivatives; TIME: 2 surrogates, then 1 more, no miscarriages | TIME; Wikipedia |
| W35 | Birth dates | 1 Oct 2024; 30 Jan 2025 | CONFIRMED | TIME | TIME |
| W36 | IUCN SSC CSG statement | "neither dire wolves nor proxies" | CONFIRMED (🟡) | Wikipedia quote of statement | https://en.wikipedia.org/wiki/Colossal_Biosciences_dire_wolf_project |
| W37 | "optimistically 1/100,000th dire wolf" | press | CONFIRMED (🟡) | Francis Crick Institute geneticist, Dallas News / Snopes | https://www.dallasnews.com/news/2025/04/09/colossal-biosciences-says-it-brought-back-the-dire-wolf-some-scientists-arent-convinced/ |
| W38 | Cloned red wolves | four, incl. "Neka Kayda" | CONFIRMED (🟡) | Hope (= Neka Kayda) + Blaze, Cinder, Ash | press (chron.com; galvnews) |
| W39 | Dire-wolf ancestry numbers | ~4.5 Mya (2.89–5.84); 39% / 61%; 99.94% | CONFIRMED | Same in peer-reviewed version | PMC13477035 |
| W40 | Dire-wolf paper status | preprint; *Cell Genomics* page inaccessible | CORRECTED | *Cell Genomics* 6(8):101306, 27 Jul 2026, doi:10.1016/j.xgen.2026.101306, PMID 42508403 | same |
| W41 | Relation to Perri 2021 | "conflicts with Perri" | CORRECTED | Partly revises (4.5 vs 5.7 Mya); dual ancestry explains Perri's gene-tree discordance; Perri is co-author | same |
| W42 | *NCAPG* top selected gene | ✅ (preprint) | DOWNGRADED → 🟡 | Not in the published brief report; preprint-only | same |
| W43 | Perri 2021 | 5 genomes; ~5.7 Mya; no gene flow with N. American grey wolves/coyotes | CONFIRMED | Exact | EXT_ID:33442059 |
| W44 | Jensen-Seaman 2026 | "three pups possessing a small amount of dire wolf-like DNA" | CONFIRMED | Exact; *Anat Rec* 309(7):1788–1796 | EXT_ID:40927892 |
| W45 | Zou 2015 | 35 zygotes → 10 recipients → 27 pups → 2 edited; #5 biallelic, phenotype at 4 mo; #11 chimera ~0.5% WT; −4 bp in sperm | CONFIRMED | Exact (#5 "Tiangou", #11 "Hercules") | https://academic.oup.com/jmcb/article/7/6/580/2459584 |

---

## Edits made

### `breed_size_genetics_lifespan.md`

1. Changed the header status line to the verified status.
2. TL;DR, size gap: corrected the cross-study "2–4 y" wording. Now reads Banfield ~4.0 y (small vs giant) and McMillan 0.8 y (small vs large).
3. TL;DR, "1 month per 2 kg": added the Selman 2013 dispatch as corroboration; still 🟡.
4. TL;DR, Siberian wolf: 54,000 → 53,000 years (heterozygous).
5. TL;DR, McCoy: added CI and 49 deaths; ✅ → 🟡 (preprint).
6. TL;DR, UK neutering gain: "+1–1.5 y" → "+0.9–1.5 y".
7. §1.1 Fleming row: neoplasia-by-size and the ~10-y peak downgraded to 🟡.
8. §1.1 Montoya row: period clarified (records 2013–Jul 2022; tables for 2013–2019).
9. §2.1 Plassais 2022: allele letters, the 53,000-y wolf and the 75% statistic upgraded to ✅ from the full text.
10. §2.2 Horvath EWAS: rewritten. Top hits are *SF1/TTC8*; *SMAD2/IGF1R* were candidate-gene CpGs described as "modest".
11. §2.4 Ames dwarf: "~40–50%" → "~50–65% (sex-specific ~49% and ~64–68%)".
12. §2.5 Sohrab: overlap denominator clarified (27% of 181 loci; 79% of the top 14).
13. §2.5 Horvath: "points back to IGF1R/SMAD2" corrected.
14. §2.5 Plassais 2017: title verified.
15. §3 table, GH/IGF row: Horvath candidate-gene wording.
16. §3 table, Jimenez row: unverifiable sample breakdown flagged.
17. §3 table, Nunney row: significance nuance.
18. §3 table, epigenetic row: McCoy preprint and 49 deaths; Jang volume.
19. §4.1 Bannasch: method corrected.
20. §4.1 Dog10K: "variants" → "structural variants".
21. §4.3: added the Urfer 2020 null purebred/mixed result.
22. §4.5 Kealy: primary-text medians, P value and max-lifespan n.s.; 🟡 → ✅; Purina sponsorship noted.
23. §5.5: verifier confirmation of the Ko & Shin misattribution.
24. §6.4: McCoy caveat.
25. §6.6: "reach ≥20 years" corrected.
26. Open questions: Jang status noted.
27. Sources:
    - [1] Kraus correction notice noted.
    - [9] Yordy PMID added.
    - [10] Kraus 2023 PMCID and data source added.
    - [21] Brown-Borg DOI and PMID added.
    - [25] Harper pages added.
    - [30] O'Neill 2023 full title and 10:8 added.
    - [32] Thompson DOI confirmed.
    - [34] McCoy status noted.
    - [35] Jang volume and issue added.
    - [43] Korec citation corrected.
    - [48] NBC date confirmed.
    - New [49] added: Selman 2013.
28. Appended "Verification notes".

### `wolves_vs_dogs.md`

1. Changed the header status line to the verified status.
2. TL;DR, wild record: added the B-2 ~13.8 y nuance and new source [35] (Holyan et al. 2005).
3. TL;DR, captive 9–16 y: provenance flagged (🟡❓); Lawler 2016 5–19 y added.
4. TL;DR, Tidière: resolved. Wolves not included; canids listed.
5. TL;DR, brain size: "not unusual" softened.
6. TL;DR, Dog10K: "structural variants".
7. TL;DR, Colossal: TIME/CNN confirmation added; dire-wolf paper now peer-reviewed; "versus Perri" reframed.
8. §1 table: wild-record row (B-2, 1090F detail); captive-lifespan row provenance.
9. §3.1: Tidière resolved; captive range caveat.
10. §3.2: Thompson wolf age-range caveat; Lu 2023 main-text check noted (unresolved).
11. §4 table:
    - AMY2B row upgraded to ✅.
    - Garamszegi 2023: 55 → 48 wolves (press), statistics flagged 🟡.
    - Garamszegi & Kolm nuance added.
    - Dog10K wording corrected.
12. §5: Gedman publication status.
13. §6.1:
    - TIME confirmation of the animals.
    - Method: dog eggs confirmed; "4 viable embryos" marked Wikipedia-only; surrogate/pregnancy detail added.
    - Genomic basis: published version noted; *NCAPG* preprint-only (🟡); Perri relation softened.
    - Red-wolf clone names.
14. Open questions: Tidière, Thompson DOI and dire-wolf peer review marked resolved; captive-lifespan provenance added.
15. Sources:
    - [6] Oliynyk article number, DOI and PMID added.
    - [8] Thompson DOI confirmed.
    - [12] Castro-Fuentes full citation and Mech/Lawler provenance.
    - [14][15] Arendt and Ollivier verified.
    - [17][18] Garamszegi DOIs and PMIDs added.
    - [23] mCanLor1.2 authors and DOI added.
    - [24] Nguyen/Schall/Kidd authors added.
    - [26] *Cell Genomics* citation added.
    - [28] Anat Rec volume and pages added.
    - [34] TIME and CNN URLs and the 1/100,000 quote attribution added.
    - New [35] Holyan 2005.
16. Appended "Verification notes".

---

## Open issues

1. **Kraus 2013 "1 month per 2 kg".** Supported only by press and a search-engine excerpt of Selman et al. 2013. Not confirmed in the Kraus primary text, which was not accessible. A correction notice to Kraus 2013 (doi:10.1086/670646) exists, and its content is unknown.
2. **Jang et al. 2026 (PNAS).** The direction of the body-size effect on epigenetic drift was not determined; the full text was blocked.
3. **Lu et al. 2023.** Whether the universal clocks include grey wolf samples needs a check of Supplementary Data 1.1–1.4 or the Mammalian Methylation Consortium sample sheet.
4. **Captive wolf lifespan.** No primary life table was found. The "9–16 y" figure has doubtful provenance. A Species360/ZIMS-based analysis is the obvious source.
5. **Garamszegi 2023 exact statistics.** "24.32%", β = 0.745 and pMCMC = 0.652 were not checked, and the wolf sample size conflicts (55 in the file vs 48 per the press release). The paper is not open access.
6. **Jimenez 2018.** The breed and sample-size breakdown is unconfirmed.
7. **Colossal.** The "4 viable embryos" figure is Wikipedia-only. No peer-reviewed paper describing the edited animals (edit list, off-target data) was found as of 2026-10-04.
8. **McCoy 2024.** Still not peer-reviewed. Its mortality result (49 deaths) should not be cited as established.
9. **Fleming 2011.** Neoplasia-by-size and the age-peak details were not confirmed in the full text (the publisher blocked access).
10. **Not checked.** The DAP enrolment figure (52,705 by Dec 2025, "per press") and textbook dog reproductive parameters were not verified.
