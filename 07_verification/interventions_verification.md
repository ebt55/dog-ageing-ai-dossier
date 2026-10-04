# Verification Report: 05_interventions
> Part of the dog-ageing research dossier · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> Independent fact-check by Opus 5.5 · 2026-10-04
> Files audited:
> - `05_interventions/dog_longevity_interventions.md`
> - `05_interventions/gene_editing_in_dogs.md`
>
> Both were written by Fable 5.1 on 2026-10-04.
> Method: about 90 web calls (company sites and press releases, Europe PMC REST abstracts and full text, PMC, FDA PDFs, the U.S. Code), plus local text extraction from two PDFs: the Kealy 2002 JAVMA paper and FDA GFI #187A. Every correction is marked `[verifier-corrected]` in place, and each file ends with a "Verification notes" section.

---

## Overall reliability: **MEDIUM** (medium-high for the Loyal and regulatory core; medium for literature detail)

**Why:**
- **The headline facts are sound.** All of these were confirmed against primary or company sources:
  - Nothing is approved or conditionally approved as of 4 Oct 2026.
  - Every Loyal milestone date: LOY-001 RXE 28 Nov 2023; LOY-002 RXE Feb 2025 and TAS 13 Jan 2026; LOY-003 RXE 16 Sep 2026.
  - All eligibility criteria, the STAY numbers, the TAS package contents, and the Series C details.
  - TRIAD design and dose, the Kealy median lifespans, and the Zou, Amoasii, Davidsohn, Urfer, Barnett, Bray and Simon papers.
- **The literature layer is weaker than the tags claim:**
  - One number had no support in its cited source: "13.2 vs 11.0 yr" attributed to the 2008 BJN paper. It was removed.
  - One figure was mis-attributed: TRIAD "~235" was credited to BBC Science Focus, which does not contain it.
  - ITP rapamycin values were mislabelled: late-onset (20-month) figures were presented as the headline values.
  - Three citations had the wrong author: Cideciyan should be Pierce & Bennett, Miller should be Strong, and the dvm360 byline "Mota" should be Coppock Crossley.
  - One organisation was wrong: Sooam should be Seoul National University.
  - One dose ratio was wrong: "6×" should be 2–4×.
  - Several ✅ tags rested on secondary sources (Time, Wikipedia), which breaks the files' own tag definition.
- **Spot-check of ✅-tagged claims:** about 20 were sampled across both files. About 14 were fully correct, and about 6 needed correction. Most corrections were precision issues (TRIAD weight cap, primary-endpoint wording, Zou read percentages, author count, Evans dosing), but a few changed meaning.
- **The author's ❓ flags were generally well placed.** Most of the self-flagged uncertainties turned out to be real issues.

---

## Counts

| Verdict | n |
|---|---|
| Claims checked | **88** |
| CONFIRMED | 53 |
| CORRECTED | 24 |
| DOWNGRADED (less certain than tagged) | 5 |
| REMOVED (unsupported) | 1 |
| UNRESOLVED | 5 |

Citation-integrity spot-check: **27 cited sources** were opened or resolved by DOI, PMID or PMCID. Of these, 7 had metadata or attribution errors that are now fixed: [3], [15], [18]/[7], [38], [47], [48] in the interventions file, and [19] in the gene-editing file. One source did not support the sentence citing it: [15] for the 235 figure. The other sources existed, matched their metadata, and supported the citing sentence.

---

## Claim table

**Files:** I = `dog_longevity_interventions.md`, G = `gene_editing_in_dogs.md`

| # | File | Claim | As written | Verdict | Correct value / note | Source URL |
|---|---|---|---|---|---|---|
| 1 | I | No approved or conditionally approved dog longevity drug as of 4 Oct 2026 | none | CONFIRMED | Loyal's newest blog post is 16 Sep 2026 (LOY-003 RXE); no CMC or XCA news found | https://loyal.com/blog |
| 2 | I | LOY-002 TAS accepted | 13 Jan 2026 | CONFIRMED | Business Wire 13 Jan 2026; Pet Age 14 Jan | https://www.petage.com/loyal-receives-fda-acceptance-of-safety-package-for-senior-dog-lifespan-extension-drug/ |
| 3 | I | LOY-002 RXE accepted | Feb 2025 | CONFIRMED | 26 Feb 2025 | https://www.petage.com/loyal-receives-fda-acceptance-of-rxe-for-senior-dog-lifespan-extension/ |
| 4 | I | LOY-003 RXE accepted | 16 Sep 2026 | CONFIRMED | GH/IGF-1 target, large dogs | https://www.biospace.com/press-releases/loyal-earns-third-efficacy-acceptance-rxe-from-the-fda-for-canine-lifespan-extension |
| 5 | I | LOY-001 RXE date | Nov 2023 (not Oct 2026) | CONFIRMED | 28 Nov 2023; the "Oct 2026" date is an aggregator error | https://loyal.com/posts/loyal-announces-historic-fda-milestone-for-large-dog-lifespan-extension-drug |
| 6 | I | Eligibility | LOY-002 ≥10 yr ≥14 lb; LOY-001 ≥7 yr ≥40 lb; LOY-003 ≥5 yr ≥60 lb | CONFIRMED | — | https://loyal.com/for-dog-owners |
| 7 | I | STAY | 1,300 dogs; 72 clinics; closed Jul 2025; first dog dosed Dec 2023 | CONFIRMED | The post says both "70+" and "72"; >1,500 screened; first dog Boo (whippet) | https://loyal.com/posts/stay-finishes-enrollment |
| 8 | I | LOY-002 safety package | 1×/3×/5× TAS study + >400 STAY dogs | CONFIRMED | Detail added: "for varying durations, including for up to one year" | https://loyal.com/posts/loy-002-tas |
| 9 | I | Series C | $100M, 11 Feb 2026, age1 lead, >$250M total | CONFIRMED | Baillie Gifford participated; the >$250M total is in the press releases, not the blog post | https://loyal.com/posts/100m-for-first-longevity-drug |
| 10 | I | LOY-001 RXE data | 451 (Loyal) vs 452 (dvm360); >2,300 pages | CONFIRMED | The discrepancy between the two sources is real; dvm360 adds "84 breeds, ages 2–18" | https://www.dvm360.com/view/fda-determines-drug-for-lifespan-extension-in-large-dogs-to-have-a-reasonable-expectation-of-effectiveness |
| 11 | I | XCA application timing | "next year" | DOWNGRADED | In a Jan 2026 release, "next year" literally reads as 2027; ambiguity flagged | (Pet Age, as #2) |
| 12 | I | TRIAD dose | 0.15 mg/kg weekly (via Barnett) | CONFIRMED | Now read off the protocol itself (delivered range 0.138–0.180 mg/kg) | https://pmc.ncbi.nlm.nih.gov/articles/PMC12181551/ |
| 13 | I | TRIAD eligibility | ≥7 yr, ≥44 lb | CORRECTED | Protocol: ≥7 yr and **20–55 kg inclusive** (recruitment pages say ≥44 lb) | https://pmc.ncbi.nlm.nih.gov/articles/PMC12181551/ |
| 14 | I | TRIAD primary endpoint | "lifespan" | CORRECTED | "Survival time from randomization," ITT; 290/290 arms; >80% power to detect a 6% difference | https://pmc.ncbi.nlm.nih.gov/articles/PMC12181551/ |
| 15 | I | TRIAD n and duration | 580; 1 yr treatment + 2 yr follow-up | CONFIRMED | 36 months total | same |
| 16 | I | TRIAD Dec 2024 status | 170 dogs, 20 sites, $7M NIH | CONFIRMED | Creevy quote also confirmed | https://vetmed.tamu.edu/news/press-releases/dog-aging-project-triad/ |
| 17 | I | TRIAD ~235 enrolled (BBC Science Focus) | ~235; close end-2026; conclude ~2029 | CORRECTED (source) | The figures exist, but in an Urban Dog NYC blog dated 30 Jan (year implied 2026). The Science Focus article (13 Sep 2025) has none of them | https://www.urbandognyc.com/blog/the-dog-aging-projects-triad-program-needs-you-and-your-dog |
| 18 | I | Kaeberlein quotes | ">50/50"; ">20%" | CONFIRMED | — | https://www.sciencefocus.com/nature/dogs-ageing-breakthrough-humans |
| 19 | I | Kealy 2002 median lifespan | 13.0 vs 11.2 (🟡) | CONFIRMED (upgraded) | JAVMA full text: 13.0 vs 11.2 yr, P < 0.01; max lifespan 14.0 vs 12.9 (NS) | https://pubmed.ncbi.nlm.nih.gov/11991408/ |
| 20 | I | 2008 BJN gives 13.2 vs 11.0 | 13.2 vs 11.0 | **REMOVED** | The BJN abstract says "1.8 years longer median lifespan," consistent with 13.0 vs 11.2 | https://pubmed.ncbi.nlm.nih.gov/18062831/ |
| 21 | I | Arthritis 1.5 yr later | 1.5 yr | DOWNGRADED | Not in JAVMA 2002. JAVMA reports 50% OA-treatment-free survival at 13.3 vs 10.3 yr | JAVMA (as #19); https://loyal.com/posts/the-purina-study |
| 22 | I | Cancer deaths at 11.6 vs 9.7 yr | 11.6 vs 9.7 | UNRESOLVED | Only in Loyal's blog; not in JAVMA 2002 | https://loyal.com/posts/the-purina-study |
| 23 | I | Loyal "explicitly builds LOY-002 narrative" on the Purina study | ✅ | DOWNGRADED | The post never names LOY-002 | same |
| 24 | I | LOY-002 framed as CR mimetic, citing [17] | 🟡 [17][26] | CORRECTED | [17] does not name LOY-002; framing re-attributed to commentators [26] | same |
| 25 | I | Leap Years RCT (Simon 2024) | 70 dogs; CCDR p=0.02; objective measures NS; 60% placebo improved; full-dose group older | CONFIRMED | Sci Rep 14:12399; reported group sizes sum to 67 | https://pmc.ncbi.nlm.nih.gov/articles/PMC11137034/ |
| 26 | I/G | RJB-01 ASGCT 2023 | n=17 (12 on RJB-01 + pimobendan); 600/800 days; LA −0.3 vs +0.8 | CONFIRMED | No p-values reported | https://www.dvm360.com/view/gene-therapy-demonstrates-benefit-to-dogs-with-myxomatous-mitral-valve-disease |
| 27 | I | Rejuvenate Bio $6M + Merck collaboration | 8 Jun 2026; VCapital lead | CONFIRMED (upgraded) | Company release (San Diego dateline 8 Jun 2026); it does not name RJB-01, RJB-0402 or FGF21 | https://finance.yahoo.com/sectors/healthcare/articles/rejuvenate-bio-announces-6-million-120000417.html |
| 28 | I | Phibro deal | 22 Jun 2022; "file as early as 2023" | CONFIRMED | No filing ever announced | https://www.businesswire.com/news/home/20220622005079/en/ |
| 29 | I/G | Amoasii 2018 | 3–90% skeletal; 92% cardiac; n=4 (2 IM, 2 systemic) | CONFIRMED | — | https://doi.org/10.1126/science.aau1549 (PMC6205228) |
| 30 | I/G | Davidsohn 2019 | +58% heart; −38% αSMA; −75% renal; 1 formulation treats all 4 diseases | CONFIRMED | — | https://pmc.ncbi.nlm.nih.gov/articles/PMC6876218/ |
| 31 | I/G | OSK (Macip 2024) | +109%; epigenetic reversal "in mouse and human cells" | CORRECTED | 109% confirmed (upgraded to ✅); the epigenetic markers were shown in **human keratinocytes** only | https://europepmc.org/article/PMC/PMC10909732 |
| 32 | I | Urfer 2017 | n=24, 10 wk, echo signal | CONFIRMED | Doses: 0.05 and 0.1 mg/kg, 3× weekly; only FS significant on both tests | https://pmc.ncbi.nlm.nih.gov/articles/PMC5411365/ |
| 33 | I | Barnett 2023 | n=17; 0.025 mg/kg 3×/wk; no echo difference; 26.8% vs 8.1% (p=0.04) | CONFIRMED | — | https://pmc.ncbi.nlm.nih.gov/articles/PMC10233048/ |
| 34 | I | Barnett dose "6× lower cumulative" | 6× | CORRECTED | 0.075 vs 0.15–0.3 mg/kg/week = **2–4× lower** | as #32 and #33 |
| 35 | I | Evans 2021 "supports weekly dosing" | weekly | CORRECTED | Tested 0.025 mg/kg **three times weekly** | https://doi.org/10.1101/2021.01.20.427425 |
| 36 | I | Larson 2016 AJVR | PK study | CONFIRMED | — | https://doi.org/10.2460/ajvr.77.1.65 |
| 37 | I | Bray 2022 | n=10,474 / 24,238; once-daily feeding associations | CONFIRMED | — | https://doi.org/10.1007/s11357-022-00575-7 |
| 38 | I | McKenzie 2025 Sci Rep | 451 dogs; cross-sectional; all 18 authors Cellular Longevity | CONFIRMED | Article 5380 | https://doi.org/10.1038/s41598-025-89923-z |
| 39 | I | Biological-age clock "DAP-adjacent, 2024" | DAP-adjacent | CORRECTED | Nestlé Research authors; 829 dogs; GeroScience 47(1):45–59 (2025) | https://doi.org/10.1007/s11357-024-01352-4 |
| 40 | I | Lim 2025 review details | 922 / 784 dogs; metformin in an induced-HF dog model; D+Q in MMVD VICs; MSCs | CONFIRMED | Authors Lim, Yoon, Han confirmed | https://pmc.ncbi.nlm.nih.gov/articles/PMC12520853/ |
| 41 | I | Salmon-oil immune work "in companion dogs" | dogs | CORRECTED | The review describes this work in **cats** | as #40 |
| 42 | I | Resveratrol "lacking dog evidence" | none | CORRECTED | The review cites short-term / open-label dog resveratrol studies | as #40 |
| 43 | I | GRMD nicotinamide | secondary; "improved muscle function" | CORRECTED | Cardoso 2023 Skelet Muscle 13:20; "modestly reduces aspects of striated muscle disease" | https://doi.org/10.1186/s13395-023-00328-w |
| 44 | I | NMN lowers NT-proBNP | 10–30 mg BID | CONFIRMED | Uncontrolled; J Adv Vet Anim Res 2026 | https://pubmed.ncbi.nlm.nih.gov/42180288/ |
| 45 | I | 3-month NMN series in 23 dogs | 23 dogs | UNRESOLVED | Not in the cited source [50]; could not be traced | — |
| 46 | I | D+F in rhesus macaques | fewer p16/p21 cells | CONFIRMED | n=6; conference abstract | https://pmc.ncbi.nlm.nih.gov/articles/PMC7740648/ |
| 47 | I | Pan 2010 MCT | 5.5% MCT for 8 months; better cognition | CONFIRMED (upgraded) | — | https://doi.org/10.1017/S0007114510000097 |
| 48 | I | ITP rapamycin | +13.4/+19.6 (14 ppm); +14.9/+10.6 (42 ppm) | CORRECTED | These are the **20-month late-onset** cohorts. From 9 months: 14 ppm F +17.5–22.5% / M +7.5–9.5%; 42 ppm F +28.3% / M +21.9% | https://pmc.ncbi.nlm.nih.gov/articles/PMC12301548/ |
| 49 | I | ITP acarbose / 17αE2 / canagliflozin | +4.8/+17.5; +17.2 M; +14 M / +1 F | CONFIRMED | 17αE2 is +17% at 14.4 ppm | same |
| 50 | I | Citation [48] "Miller RA et al. 2016" | Miller | CORRECTED | First author is **Strong R**; Aging Cell 15(5):872–884 | https://pmc.ncbi.nlm.nih.gov/articles/PMC5013015/ |
| 51 | I | Conditional-approval term | "1-yr + annual renewals" (❓) | CONFIRMED (upgraded) | 21 USC 360ccc(d): 1 yr + up to 4 one-year renewals | https://www.law.cornell.edu/uscode/text/21/360ccc |
| 52 | I/G | GFI #261 final July 2021; ADUFA IV 2018; §571 two criteria | — | CONFIRMED | — | https://www.fda.gov/regulatory-information/search-fda-guidance-documents/cvm-gfi-261-eligibility-criteria-expanded-conditional-approval-new-animal-drugs |
| 53 | I/G | GFI #187A final May 2024 | 🟡 | CONFIRMED (upgraded) | Read in the FDA PDF | https://www.fda.gov/media/74614/download |
| 54 | I/G | GFI #187B final Jan 2025; #251 draft Jan 2025 (comments to 10 Mar 2025) | — | CONFIRMED | 187B finalised 7 Jan 2025 (secondary source) | https://www.cov.com/en/news-and-insights/insights/2025/01/fda-finalizes-guidance-on-its-approval-process-for-intentional-genomic-alterations-in-animals-proposes-framework-for-regulating-alterations-in-food-producing-disease-models |
| 55 | I/G | 187A gives no companion-dog example | ❓ | CONFIRMED | The 187A PDF never mentions dogs; GloFish is its nearest pet precedent | https://www.fda.gov/media/74614/download |
| 56 | I/G | Slate quotes (Pierce, Korec) | — | CONFIRMED | Kait Hanson, 23 Apr 2025 | https://slate.com/technology/2025/04/dogs-pets-pill-longevity-extend-lifespan-loyal-veterinary-ethics.html |
| 57 | I/G | dvm360 2023: pricing, Rhodes "new indication", "28× IGF-1" | — | CONFIRMED | — | as #10 |
| 58 | I | dvm360 [3] author "Mota S." | Mota | CORRECTED | Byline is Kristen Coppock Crossley | https://www.dvm360.com/view/second-drug-for-canine-healthy-lifespan-extension-receives-fda-support |
| 59 | I/G | LessWrong r≈0.07 "with age at death" | age at death | CORRECTED | The post reports r=.0677 for IGF-1 vs age (88-dog 2011 dataset); not clearly age at death | https://www.lesswrong.com/posts/vHSkxmYYqW59sySqA/the-likely-first-longevity-drug-is-based-on-sketchy-science |
| 60 | I/G | CSH Perspect Med a017285 authors | Cideciyan AV et al. | CORRECTED | **Pierce EA, Bennett J** (2015) | https://europepmc.org/article/PMC/PMC4561397 |
| 61 | I/G | RPE65 durability >7 yr ("Lancelot") | >7 yr | DOWNGRADED | Primary data (Acland 2005 Mol Ther): ERG stable at 3 yr; >7 yr not confirmed | https://europepmc.org/search?query=Acland%20long-term%20restoration%20rod%20cone |
| 62 | I/G | Haemophilia B AAV (Mount 2002) | >17 mo; 3 of 4 dogs | CONFIRMED (upgraded) | Blood 99(8):2670–2676 | https://pubmed.ncbi.nlm.nih.gov/11929752/ |
| 63 | I | Okava MEOW-1 | first cat dosed ~Dec 2025; dogs to follow | CONFIRMED | INAD; Vivani NanoPortal implant | https://www.financialcontent.com/article/prlog-2025-12-3-okava-pharmaceuticals-announces-first-cat-dosed-in-meow-1-study-of-okv-119-the-worlds-first-clinical-stage-glp-1-weight-loss-therapy-for-pets |
| 64 | I | Okava FDA filing targeted 2027–2028 | 2027–28 | UNRESOLVED | okava.com did not resolve | — |
| 65 | I | Loyal blog's newest post is 16 Sep 2026 | — | CONFIRMED | — | https://loyal.com/blog |
| 66 | G | Zou 2015 pipeline | 35 → 10 → 8 → 27 → 2; 16 off-target sites clean | CONFIRMED | First attempt: 25 embryos into 6 recipients, no pregnancies | https://academic.oup.com/jmcb/article/7/6/580/2459501 |
| 67 | G | Zou #5 "~87% of reads" | ~87% edited | CORRECTED | ~100% mutated (86.8% +1 bp, 13.1% −8 bp); #11 has 99.2% 4-bp deletion | same |
| 68 | G | Dog names Tiangou / Hercules | media (🟡) | CONFIRMED (upgraded) | The names are in the paper itself | same |
| 69 | G | ApoE KO dogs (Zhao 2022): phenotype, germline transmission, affiliations | — | CONFIRMED | Also TianTan Hospital and others | https://doi.org/10.1007/s11427-021-2006-y |
| 70 | G | Zhao 2022 author count | 24 | CORRECTED | 23 | same |
| 71 | G | ApoE founder numbers (65 zygotes, 13 recipients, 7 pregnancies, 13 puppies, "Apple") | ResearchGate | UNRESOLVED | Citation corrected to Feng 2018 J Genet Genomics 45(1):47–50; numbers not re-checked | https://doi.org/10.1016/j.jgg.2017.11.003 |
| 72 | G | ApoE "13 puppies from 13 recipients" as an efficiency gain | efficiency | CORRECTED | Only 1 of 13 puppies was edited | — |
| 73 | G | Snuppy: 1,095 embryos / 123 surrogates / 3 pregnancies / 1 survivor; died May 2015 of cancer | — | CONFIRMED | Death at age 10 from cancer confirmed in Sci Rep 2017 | https://en.wikipedia.org/wiki/Snuppy |
| 74 | G | 2017 Snuppy re-clones made by Sooam | Sooam | CORRECTED | **Seoul National University** (Lee BC); 4 clones; Sci Rep 7:15235 | https://doi.org/10.1038/s41598-017-15328-2 |
| 75 | G | Colossal edits: 20 / 14 genes; 15 + 5; MC1R + MFSD12 | ✅ | DOWNGRADED (tag) | Facts agree across sources, but Time and Wikipedia are secondary, so 🟡 | https://en.wikipedia.org/wiki/Colossal_Biosciences_dire_wolf_project |
| 76 | G | Colossal: 45 embryos; surrogates; births 1 Oct 2024 / 30 Jan 2025; no miscarriage | — | CONFIRMED | Time: 45 ova → embryos; 2 surrogates + a 3rd in a later procedure | https://time.com/7274542/colossal-dire-wolf/ |
| 77 | G | Colossal peer-reviewed status | bioRxiv preprint only | CORRECTED | Published as *Cell Genomics* 6(8):101306 (Aug 2026); ancestry only, no edit data | https://doi.org/10.1016/j.xgen.2026.101306 |
| 78 | G | Critic quotes (Rawlence, Austin, IUCN, Klitzman, Van Eenennaam, Shapiro) | — | CONFIRMED | Via Wikipedia and Time | as #75, #76 |
| 79 | G | Sutter 2007 | CFA15 QTL; single IGF1 haplotype | CONFIRMED | — | https://doi.org/10.1126/science.1137045 |
| 80 | G | Plassais 2022: small allele "may predate" the large one | may predate | CORRECTED | The abstract says the small-size allele is **ancestral** | https://doi.org/10.1016/j.cub.2021.12.036 |
| 81 | G | Plassais: small allele "≥54,000 years old" | ✅ | UNRESOLVED | Not in the abstract | same |
| 82 | G | αKlotho combination detail | ❓ | CONFIRMED (resolved) | The 4-disease formulation was sTGFβR2 + FGF21, without αKlotho | https://pmc.ncbi.nlm.nih.gov/articles/PMC6876218/ |
| 83 | G | Chemical-reprogramming lipid paper | "2025 preprint" | CORRECTED | Now published: Mitchell W et al., *Aging Cell* 2026 | https://pmc.ncbi.nlm.nih.gov/articles/PMC12835892/ |
| 84 | G | Public opinion: n=338 US survey | — | CONFIRMED | Kuo et al. 2024, Public Underst Sci 33(6) | https://doi.org/10.1177/09636625241227091 |
| 85 | G | Australian germline-attitudes study | — | CONFIRMED | Critchley 2018 Front Genet; n=1,004 | https://pmc.ncbi.nlm.nih.gov/articles/PMC6334182/ |
| 86 | G | No ageing-gene edit in any dog | absence | CONFIRMED | Verifier Europe PMC search (2019–2026) found none | https://europepmc.org |
| 87 | G | Multimorbidity GeroScience 2026 | — | CONFIRMED | Foreman ER et al. (DAP) | https://doi.org/10.1007/s11357-026-02342-4 |
| 88 | G | 180-day window "for disease models" | disease models | CORRECTED | This is the general 187A Category 2 response target | https://www.fda.gov/media/74614/download |

---

## Edits made

### `dog_longevity_interventions.md` (49 `[verifier-corrected]` / added markers)

- **Header**
  - Status line updated.
- **TL;DR**
  - Flagged the ambiguity of LOY-002's "next year".
  - TRIAD: weight range, primary endpoint and dose now come from the protocol; the 235 figure is re-sourced.
  - Kealy upgraded to ✅ with P < 0.01.
  - OSK upgraded to ✅.
- **§1 (Loyal)**
  - Founding year and the >$250M total re-sourced.
  - CR-mimetic framing re-attributed to commentators.
  - Safety-data duration added.
  - Funding table total re-sourced.
  - LessWrong r≈0.07 described more precisely.
- **§2.1 TRIAD table**
  - Target n now shows the 290/290 split and the power calculation.
  - Eligibility now 20–55 kg; intervention specified as 36 months total.
  - Dose read directly off the protocol; primary endpoint corrected to survival time (ITT).
  - Enrolment source re-attributed.
- **§2.2**
  - Urfer dose groups added.
  - Evans dosing corrected to thrice weekly.
  - "6×" corrected to "2–4×", with a small-n caveat.
- **§2.3**
  - Biological-age clock re-attributed to Nestlé Research.
- **§3 Kealy**
  - Rewritten from the full text: median lifespan, maximum lifespan, OA-treatment and chronic-condition medians.
  - The "13.2 vs 11.0" claim removed.
  - Loyal's 1.5-yr arthritis figure and 11.6/9.7 cancer figure flagged as absent from JAVMA.
  - BJN 2008 citation completed.
  - Loyal/LOY-002 linkage softened.
- **§4**
  - Rejuvenate/Merck upgraded to ✅, and the press-release index noted.
  - OSK details corrected.
  - RPE65 durability claim downgraded.
  - Haemophilia upgraded.
  - GRMD citation located and effect softened.
- **§5**
  - Rapamycin ITP values corrected; acarbose, 17αE2 and canagliflozin re-sourced to the ITP review.
  - Leap Years group sizes noted.
  - NMN: 23-dog series flagged.
  - Omega-3: cats, not dogs.
  - MCT upgraded.
  - D+F n=6 added.
  - Resveratrol split out as having weak dog data.
  - §5.1 ITP table rebuilt.
- **§6**
  - Conditional-approval term confirmed in the statute.
  - #187A checked in the primary PDF (categories; no dog example; GloFish precedent).
- **Open questions**
  - Items 5, 6 and 7 updated.
- **Sources**
  - Fixed [3], [15], [16], [18], [19], [23], [28], [31], [38], [39], [47], [48], [49], [50], [52], [56].
  - Added [64]–[67].
- **End of file**
  - "Verification notes" section appended.

### `gene_editing_in_dogs.md` (28 markers)

- **Header**
  - Status line updated.
- **TL;DR**
  - Zou read percentages corrected.
  - Colossal tags lowered to 🟡, with the Cell Genomics 2026 paper noted.
  - Absence-of-evidence search noted.
  - #187A upgraded to ✅.
- **§1.1**
  - Mosaicism row corrected.
  - Dog names confirmed in the primary paper.
- **§1.2**
  - Author count corrected to 23 and affiliations expanded.
  - ApoE founder paper cited properly; its numbers marked ❓.
- **§1.3**
  - Re-cloning attributed to SNU.
  - Efficiency framing corrected.
- **§1.4 Colossal**
  - Tags changed from ✅ to 🟡.
  - Embryo and transfer rows clarified.
  - Peer-reviewed genome paper row added, plus a critiques paragraph.
- **§2**
  - RPE65 durability downgraded.
  - FIX partially upgraded.
- **§3**
  - Plassais corrected and its citation completed.
  - LessWrong r described more precisely.
  - FGF21 note added.
  - αKlotho question resolved.
  - OSK and chemical-reprogramming rows corrected.
  - Risk item 7 updated.
- **§4.2**
  - 180-day window corrected.
  - Companion-animal bullet checked against the 187A PDF.
- **Open questions**
  - Items 2, 4 and 5 updated; recent non-ageing edited-dog models added.
- **Sources**
  - Fixed [7], [8], [9], [10], [14], [15], [17], [19], [28], [29], [30].
  - Added [36] and [37].
- **End of file**
  - "Verification notes" section appended.

---

## Remaining open issues

1. **Loyal XCA timing.** It is unclear whether "next year" in the 13 Jan 2026 release means 2026 or 2027. Loyal's site gives no date, and no CMC acceptance had been announced as of 4 Oct 2026.
2. **STAY primary endpoint and statistical plan** are still not public (unchanged).
3. **TRIAD enrolment.** The 235 figure rests on a dog-owner blog whose year is implied, not stated. No DAP or academic source with a current figure was found; dogagingproject.org renders client-side and could not be read.
4. **Kealy follow-up figures.** The source of Loyal's "cancer deaths 11.6 vs 9.7 yr" and "arthritis 1.5 yr later" is unknown. A likely candidate is Lawler et al. 2005 JAVMA (causes of death), which was not checked.
5. **ApoE founder numbers** (Feng 2018 J Genet Genomics) were not re-verified, because no abstract was available.
6. **RPE65 ">7 years" durability** is not confirmed in a primary source.
7. **Plassais "≥54,000 years"** is not confirmed.
8. **Colossal embryo-transfer numbers** still conflict between Time and Wikipedia, and the edited animals have no peer-reviewed methods paper.
9. **GFI #187B** (final, Jan 2025) was not read in the primary. The companion-animal conclusion rests on #187A plus a law-firm summary.
10. **Not checked because of budget or blocked sites:**
    - Life Biosciences ARDD 2025
    - Epiterna (€10M)
    - TechCrunch $27M (2021)
    - CNN "Longlong" (HTTP 451)
    - Okava FDA timeline (domain did not resolve)
    - Doc's FIRE Substack
    - The [13] Animal Welfare attitudes paper
    - Pew document
    - AAV2/8 re-dosing paper
    - Lee et al. 2005 *Nature* (Snuppy primary)
    - RJB-0402 ACM release
11. **Coverage gap, not an error.** The gene-editing file omits recent non-ageing germline-edited dog models (RPGR beagles 2025; Kim 2022 SCNT-edited dogs; a Can f 1 knockout in CRISPR J 2026, where it is not checked whether live dogs were produced). They are now listed as leads in its Open-questions item 5.
