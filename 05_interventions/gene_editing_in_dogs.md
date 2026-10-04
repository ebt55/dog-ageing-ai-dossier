# Gene Editing in Dogs: Feasibility, Targets, Ethics (October 2026)

> Part of the dog-ageing research dossier · Written 2026-10-04 by Fable 5.1 subagent · Status: independently verified by Opus 5.5 on 2026-10-04 — see ../07_verification/interventions_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**Evidence tags:** ✅ = confirmed in a primary source I opened · 🟡 = secondary / news / press-release only · ❓ = unconfirmed · **[SPECULATIVE]** = my own reasoning, not a claim from any source.

---

## TL;DR

- **Germline gene editing in dogs has been done, repeatedly, since 2015.** Zou et al. produced **myostatin-knockout beagles** by Cas9 mRNA + sgRNA injection into zygotes: 35 injected zygotes, 10 recipient females, 8 pregnancies, **27 puppies, 2 edited**, only one of which (biallelic: essentially all reads mutated, 86.8% +1 bp / 13.1% −8 bp) showed the expected muscle-hypertrophy phenotype ✅ [1] [verifier-corrected].
- **CRISPR + cloning (SCNT) is the workhorse.** ApoE-knockout dogs were made by combining zygote CRISPR with somatic cell nuclear transfer; they develop hypercholesterolaemia, severe atherosclerosis with arterial stenosis and occlusion, and **clinical stroke and gangrene**, and transmit the phenotype to offspring ✅ [2]. Beijing Sinogene Biotechnology is a co-author institution ✅ [2].
- **Dog cloning is commercial but brutally inefficient at the frontier.** Snuppy (2005) required **1,095 embryos transferred into 123 surrogate females** to yield 3 pregnancies, 2 live births, and 1 surviving dog — a <0.2% success rate 🟡 [3].
- **Colossal's 2025 "dire wolves" are the current state of the art for edited-canid creation — and they used domestic dogs as surrogates.** Gray-wolf endothelial progenitor cells from blood, **20 edits across 14 genes**, nuclei transferred by SCNT into denucleated ova, **45 engineered embryos**, implantation into **hound-mix surrogate dogs**, planned C-sections. Romulus and Remus born **1 Oct 2024**, Khaleesi **30 Jan 2025** 🟡 [4][5]. Only 15 of the 20 edits derive from dire-wolf genomes; 5 were for pale coat colour, using loss-of-function edits in **MC1R and MFSD12** chosen to avoid a variant carrying blindness/deafness risk 🟡 [5]. [verifier-corrected: tags lowered to 🟡 because Time and Wikipedia are secondary sources; the editing/embryo details have still not appeared in a peer-reviewed paper — Colossal's dire-wolf **genome** paper was published in *Cell Genomics* in Aug 2026 [36], but its abstract does not cover the edited animals.]
- **Somatic (non-heritable) in vivo editing works in dogs.** Amoasii et al. delivered AAV-CRISPR systemically to ΔE50-MD dogs and restored dystrophin to **3–90% of normal in skeletal muscle and 92% in cardiac muscle** (highest dose) at 8 weeks ✅ [6]. Dogs were also the pivotal species for **RPE65** retinal gene therapy (→ Luxturna) 🟡 [7] and **haemophilia B** AAV-FIX 🟡 [8].
- **No one has edited an ageing-relevant gene in a dog.** Not germline, not somatic, not announced. ✅ (absence of evidence after targeted search; a verifier Europe PMC search of 2019–2026 dog-editing papers also found none)
- **Ageing targets are identifiable but all speculative.** The **IGF1 / IGF1-AS small-dog haplotype** is the single best-validated size-and-lifespan locus in dogs ✅ [9][10] — and also the most dangerous to edit, because it is the locus that *makes dogs small*, with dwarfism and metabolic consequences as the expected cost of a naive intervention **[SPECULATIVE]**.
- **The regulatory picture for companion-animal editing is close to empty.** Heritable IGAs are regulated as new animal drugs under GFI #187A (risk-based, final May 2024 ✅ [11], read in the FDA PDF) and #187B (approval process, final Jan 2025 🟡 [12]) [verifier-corrected], but I could find **no category determination, approval, or worked example for a companion dog** ❓.
- **Public-opinion data are indirect but consistent:** support for gene editing in animals is lower than for plants, is higher when the purpose is **animal health** rather than enhancement, and the public's dominant question is **animal welfare** 🟡 [13][14][15].

---

## 1. Germline editing and cloning in dogs

### 1.1 MSTN-knockout beagles (Zou et al. 2015) — the first gene-edited dogs

**Zou Q, et al. "Generation of gene-target dogs using CRISPR/Cas9 system." *Journal of Molecular Cell Biology* 7(6):580–583 (2015). DOI 10.1093/jmcb/mjv061** ✅ [1]

| Parameter | Value |
|---|---|
| Method | **Cas9 mRNA + sgRNA microinjected into dog zygotes**, targeting **Myostatin (MSTN)** |
| First attempt | Allo-transplantation **failed** due to reproductive asynchrony between donor and recipient |
| Working method | **Auto-transplantation** — zygotes from one oviduct returned to the contralateral oviduct of the **same** donor-recipient female |
| Embryos | **35** injected (25 in the failed first attempt) |
| Recipients | **10** females |
| Pregnancies to term | **8 of 10 (80%)** |
| Puppies born | **27** |
| Edited puppies | **2** (#5 and #11) |
| Mosaicism | #5 **biallelic**: almost all reads mutated (86.8% +1 bp, 13.1% −8 bp) [verifier-corrected: "~87%" was one allele's share, not the edited fraction]; #11 **chimeric**: 99.2% of reads carried a 4-bp deletion, ~0.5% wild-type |
| Phenotype | **Only the biallelic dog (#5) showed muscle hypertrophy**; the chimeric dog had muscle mass similar to a wild-type littermate |
| Off-target | **16** potential sites screened by T7E1 + sequencing; **no confirmed off-target mutations** |
| Stated purpose | Establish a protocol for generating knockout dogs as **biomedical disease models** |

The two edited dogs were named **Hercules** (male, #11, incompletely edited) and **Tiangou** (female, #5, the successful knockout) — names also given in the paper itself ✅ [1][16] [verifier-corrected]. The team stated intent to produce dogs modelling Parkinson's disease and muscular dystrophy 🟡 [16].

**Key efficiency numbers to carry forward: ~2/27 puppies edited (7%), 1/27 (~4%) with the intended phenotype, from 35 injected embryos.** Direct zygote editing in dogs is therefore feasible but **mosaicism-limited**, which is exactly why the field moved to CRISPR-then-clone.

### 1.2 ApoE-knockout dogs (CRISPR + SCNT)

**Zhao H, et al. (23 authors incl. Lai L, Zhang YQ) [verifier-corrected: was "24"]. "Dogs lacking Apolipoprotein E show advanced atherosclerosis leading to apparent clinical complications." *Science China Life Sciences* 65(7):1342–1356 (2022). DOI 10.1007/s11427-021-2006-y** ✅ [2]

- Generated by **CRISPR/Cas9 plus somatic cell nuclear transfer**
- Phenotype: **hypercholesterolaemia and severe atherosclerosis** with **stenosis and occlusion of arteries**, plus **clinical stroke and gangrene**
- **Germline transmission confirmed:** phenotypes in F0 mutants are recapitulated in their offspring
- Authors argue the disease pattern is closer to human patients than other animal models
- Affiliations include the **Institute of Genetics and Developmental Biology (CAS)**, **Guangzhou Institutes of Biomedicine and Health (CAS)**, **Beijing Sinogene Biotechnology Co. Ltd**, **Xuanwu Hospital** and **TianTan Hospital (Capital Medical University)**, among others ✅ [2]

The founder paper is **Feng C, Wang X, Shi H, … Mi J, Lai L, "Generation of ApoE deficient dogs via combination of embryo injection of CRISPR/Cas9 with somatic cell nuclear transfer," *J Genet Genomics* 45(1):47–50 (2018)** [17] [verifier-corrected: previously cited only as a ResearchGate record]. Its reported generation numbers — **65 zygotes microinjected, 13 recipient females, 7 pregnancies to term, 13 puppies**, one of which (a male named **"Apple"**) carried a 34-bp deletion plus 17-bp insertion — could not be re-checked (no abstract on Europe PMC) ❓. Sinogene then **cloned** Apple to produce "Longlong," announced December 2017, explicitly to propagate the disease model 🟡 [18].

**This is the clearest template for how an ageing-edited dog would actually be made: edit cells → verify the edit → SCNT → surrogate.** It removes mosaicism and lets you check the genotype before committing a pregnancy. It also means the animal is a clone, with all of cloning's welfare costs.

### 1.3 Dog cloning

| Programme | Facts | Tag |
|---|---|---|
| **Snuppy (2005)** — world's first cloned dog | Afghan hound; SCNT using an adult ear fibroblast; **1,095 embryos transferred into 123 surrogate females → 3 pregnancies → 2 live births → 1 survivor** (the other died of pneumonia within weeks); born **24 Apr 2005** at Seoul National University (Hwang Woo-Suk group); published in *Nature*, online 3 Aug 2005; **success rate <0.2%**. Snuppy died in **May 2015** at ~10 years, of cancer. Independently verified as a true clone despite the Hwang fabrication scandal in the group's stem-cell work | 🟡 [3] |
| **Re-cloning Snuppy (2017)** | **Seoul National University** (Lee BC group) produced **4 clones of Snuppy himself** from his adipose-derived MSCs — the first clones of a cloned dog — reported in *Scientific Reports* 7:15235 (2017); the paper also confirms Snuppy and his donor Tai both died of cancer, at 10 and 12 yr | ✅ [19] [verifier-corrected: Wikipedia credits Sooam Biotech, but the primary paper's authors are all SNU / MSU / UIUC] |
| **Sooam Biotech (Korea)** | Commercial pet cloning, founded by Hwang | ❓ (not verified in this pass) |
| **Sinogene (Beijing)** | Commercial cloning + the gene-edited-then-cloned beagle work above | ✅ [2]; 🟡 [18] |
| **ViaGen Pets (US)** | Commercial dog cloning service | ❓ (not verified in this pass) |

**Welfare arithmetic matters here.** Snuppy's 123 surrogate females for one surviving dog is the single most important number in any ethical analysis of germline dog engineering. Efficiency may have improved — Colossal *claims* high cloning efficiency from EPCs 🟡 [4]; the ApoE zygote-injection round reportedly produced 13 puppies from 13 recipients, but **only 1 of the 13 was edited** ❓ [17] [verifier-corrected: previously presented as an efficiency gain] — and the procedure still requires oocyte donors, hormonal synchronisation, surgical embryo transfer, surrogate pregnancy and C-sections.

### 1.4 Colossal's 2025 gene-edited wolves — method, in detail

This is the most ambitious multiplex canid edit performed to date, and it ran **through domestic dogs**.

| Step | Detail | Tag |
|---|---|---|
| Starting cells | **Endothelial progenitor cells (EPCs) isolated from gray wolf blood** — deliberately less invasive than tissue biopsy; George Church calls the EPC route "a game changer" (Time quotes him on the less invasive sampling) | 🟡 [4] |
| Edits | **20 edits across 14 genes**; **only 15 of the 20 derive from dire wolf genomes**; the other 5 produce light coat colour via **loss-of-function edits in MC1R and MFSD12**, chosen in place of the naturally occurring variant that "carried a risk of blindness and deafness" | 🟡 [5] |
| No ancient DNA inserted | No dire-wolf DNA was spliced in; the gray wolf genome was rewritten to match | 🟡 [4] |
| Reconstruction | Edited nuclei transferred into **denucleated ova**; embryos developed in vitro | 🟡 [4][5] |
| Embryos | **45 engineered ova that developed into embryos** (Time); Wikipedia says 45 engineered ova, of which **4 viable embryos** were implanted | 🟡 [4][5] |
| Transfer | Implanted into **surrogate hound-mix domestic dogs**, chosen for health and **size** (large pups expected). Time: embryos went into **two** surrogates with "one embryo taking hold" in each, and a **third** surrogate received embryos in a later procedure; "no dogs experienced a miscarriage or stillbirth." Wikipedia: **4 embryos implanted, 3 pups survived** — the two accounts are in tension on transfer/attrition numbers ❓ | 🟡 [4][5]; discrepancy ❓ [verifier-corrected] |
| Births | **Romulus and Remus: 1 Oct 2024. Khaleesi: 30 Jan 2025.** All three by **planned caesarean section** | 🟡 [4][5] |
| Company's own retraction of framing | Chief scientist **Beth Shapiro, May 2025**: the animals are "grey wolves with 20 edits," and "it is impossible to bring back an extinct organism" | 🟡 [5] |
| Peer-reviewed publication | The dire-wolf **paleogenome** paper (Gedman GL … Shapiro B, "On the ancestry and evolution of the extinct dire wolf," *Cell Genomics* 6(8):101306, Aug 2026) is now published; its abstract covers ancestry only (~2/3 from a lineage sister to gray wolf + coyote + dhole) and **does not report the edits, embryos or surrogates** | ✅ [36] [added by verifier] |

[verifier-corrected: all rows above were tagged ✅, but Time and Wikipedia are secondary sources under this file's own definition, so they are now 🟡.]

**Peer-reviewed critiques (2025–2026)** located by the verifier (titles and venues confirmed via Europe PMC; arguments not reviewed): Jensen-Seaman, "The dire wolf (*Aenocyon dirus*) resurrection that wasn't," *Anat Rec* (2026); Ilic, "Engineered proxies and the illusion of de-extinction," *Stem Cell Reports* (2025); Höglund, "How to clone a Dire Wolf?", *EMBO Rep* (2025); Azevedo, "Reviving the Dire Wolf? A Case Study in Welfare Ethics, Legal Gaps, and Ontological Ambiguity," *Animals* 15:1839 (2025) [37].

**Scientific criticism** 🟡 [5] [verifier-corrected: was ✅]:
- Nic Rawlence: dire wolves diverged from gray wolves **~2.5–6 million years ago**, making reconstruction from fragmentary ancient DNA untenable
- Jeremy Austin: the result is "not a dire wolf under any definition of a species ever"
- **IUCN Species Survival Commission Canid Specialist Group**: the animals are neither dire wolves nor valid conservation proxies, and the project "does not contribute to conservation"

**Welfare and biology criticism** 🟡 [4] (quotes confirmed in Time) [verifier-corrected: was ✅]:
- Bioethicist Robert Klitzman (Columbia): "There's a risk of death. There's a risk of side effects that are severe… There are going to be miscarriages."
- Alison Van Eenennaam (UC Davis) on **pleiotropy**: genes targeted for one trait "could have effects that are not compatible with survival"

**Regulatory oversight: not described.** Neither the Time feature nor the Wikipedia account identifies USDA, FDA or any agency as having reviewed the work ✅ [4] — a notable gap given that heritable IGAs in animals are nominally new animal drugs 🟡 [11].

**Why this matters for dog ageing.** Colossal demonstrated that **~20 simultaneous edits in a canid genome, followed by SCNT into dog surrogates, produces live, apparently healthy animals.** Whatever one thinks of the dire-wolf framing, the engineering capability is the relevant fact: multiplex canid germline engineering is no longer the bottleneck. Phenotype prediction and welfare are.

---

## 2. Somatic (non-heritable) in vivo editing and gene therapy in dogs

This is the route that could actually reach pet dogs, because it doesn't create a new animal.

| System | Delivery | Result | Tag |
|---|---|---|---|
| **AAV-CRISPR exon skipping, DMD** | AAV, **intramuscular (n=2)** and **systemic (n=2)** in **ΔE50-MD dogs** | Dystrophin restored to **3–90% of normal across skeletal muscles** at 8 weeks post-systemic delivery; **92% of normal in cardiac muscle** in the highest-dose dog; improved muscle histology. Authors: "with further development, gene editing approaches may prove clinically useful" | ✅ [6] |
| **AAV-RPE65, retina** | Subretinal AAV | Vision restored in Briard dogs with a naturally occurring RPE65 null mutation (Acland 2001, *Nat Genet* 28:92–95); primary follow-up shows ERG responses stable at **3 years** (Acland 2005, *Mol Ther*); the ">7 years" figure is unconfirmed ❓ [verifier-corrected]; directly enabled **voretigene neparvovec (Luxturna)** | 🟡 [7] |
| **AAV-FIX, liver** | Liver-directed AAV2 and AAV2/8 | Sustained therapeutic factor IX **>17 months** (5–12% of normal); near-complete phenotypic correction in 3 of 4 dogs including 2 FIX-null animals ✅ [8] (Mount 2002 abstract); AAV2-pretreated dogs re-treated with AAV2/8 🟡 (not re-checked) | ✅/🟡 [8] [verifier-corrected] |
| **RJB-01 (Rejuvenate Bio)** | AAV; **FGF21 up, TGFβ1 down via sTGFβR2** | Cavalier King Charles Spaniels with mitral valve disease; **n=17 dogs (12 on RJB-01 + pimobendan)**; durable expression up to 3 years; progression delayed >1.5 yr; **no p-values published**; conference abstract only | 🟡 [20] |
| **Base editing / prime editing in dogs** | — | **I found no in vivo base- or prime-editing study in dogs.** The 2024–2025 literature advances LNP-RNP delivery (>300-fold editing enhancement with SM102 ionizable lipid), dual-AAV split prime editors (40–50% editing in mouse brain/liver/heart), and eVLP delivery — **all rodent** | ❓ / 🟡 [21] |
| **LNP delivery in dogs** | — | No canine LNP gene-editing study located ❓ |

**The honest summary.** Dogs are an *excellent, well-characterised* large-animal gene-therapy species: systemic AAV reaches muscle and heart, liver-directed AAV gives multi-year expression, and in vivo Cas9 editing achieves clinically meaningful protein restoration. What has **never** been shown in a dog: base editing, prime editing, LNP-delivered editing, re-dosing across a 12-year lifespan, or any edit aimed at an ageing phenotype.

---

## 3. Ageing-relevant targets that could in principle be edited

> **Everything in this section is speculative.** No dog has been edited at any of these loci for an ageing purpose. The genetics columns are sourced; the "what editing would do" column is my inference and is labelled **[SPECULATIVE]** throughout.

### 3.1 The GH/IGF-1 axis — best-validated, highest-risk

**What is actually established:**
- **Sutter et al. 2007, Science**: a genome-wide scan found a major body-size QTL on **CFA15**; a selective sweep spans **IGF1**; a single IGF1 SNP haplotype is **common to all small breeds and nearly absent from giant breeds**, implying one causal variant is a major contributor to small size across all small dogs ✅ [9]
- **Plassais et al. 2022, Current Biology 32(4):889–897**: the functional variant lies not in IGF1 itself but in **IGF1-AS**, a non-coding antisense lncRNA that forms a duplex with IGF1; the **small-size allele is the ancestral allele** (so it predates the derived large allele), was common in smaller wild canids, "nearly vanished in Pleistocene wolves", then resurged under human selection for small breeds ✅ [10]. The "≥54,000 years old" figure is not in the abstract and was not re-checked ❓ [verifier-corrected]
- Serum IGF-1 in dogs is negatively correlated with lifespan and positively with body weight; reviews describe IGF1 as the one dog-size/longevity gene validated by multiple independent lines of evidence 🟡 [22]
- Large dogs have been reported to carry **up to 28× the IGF-1 levels** of small dogs 🟡 [23]
- **Counter-evidence:** within a weight class, IGF-1 varies enormously (e.g. ~20–300 ng/mL among 20–30 lb dogs), and a blog re-analysis of an 88-dog 2011 dataset reports only a weak correlation (**r≈0.07**) between IGF-1 and age (not clearly age at death) 🟡 [24] [verifier-corrected]

| Candidate target | Rationale | Expected risk if edited | Tag |
|---|---|---|---|
| **IGF1 / IGF1-AS** (introduce small-dog allele) | The single best-validated size-and-lifespan locus in dogs ✅ [9][10] | **This is the dwarfing allele.** Editing it in an adult does nothing to body size already attained; editing it in the germline produces a *smaller dog*, not a longer-lived large dog. Developmental growth-plate, organ-scaling and metabolic effects are the point, not a side effect | ✅ for genetics; **[SPECULATIVE]** for consequences |
| **GHR** (growth hormone receptor) | GHR-null mice (Laron model) are the longest-lived single-gene mice; GHR variants contribute to dog size | Laron-type dwarfism, hypoglycaemia, impaired growth, possible immune and skeletal effects | **[SPECULATIVE]** |
| **IGF1R** | Heterozygous IGF1R-mutant mice live longer | Severe growth restriction if biallelic; insulin-signalling crosstalk | **[SPECULATIVE]** |
| **GH1 / somatotroph axis** | Reducing GH output mimics the small-dog phenotype; Loyal's LOY-003 is a *pharmacological* GH/IGF-1 intervention ✅ [25] | Pituitary dysfunction, muscle loss, poor wound healing | **[SPECULATIVE]** |

**My read:** the IGF-1 axis is simultaneously the **most evidentially supported** and the **least editable** ageing target in dogs, because the dog-specific evidence is a *developmental body-size* allele, and large-breed owners want big dogs that live long, not small dogs. A somatic, adult-onset, dose-controlled, **reversible** intervention (which is what Loyal is attempting pharmacologically) is a far better fit to this biology than a germline edit **[SPECULATIVE]**.

### 3.2 Secreted longevity factors — better fit for somatic delivery

| Target | Evidence | Note | Tag |
|---|---|---|---|
| **FGF21** | AAV-FGF21 alone completely reversed obesity and type II diabetes in mice (the reversal was seen in all FGF21 recipients "regardless of any other treatment") ✅ [26]; FGF21 is the shared payload in **RJB-01** (dog MMVD pilot) 🟡 [20] and **RJB-0402** (liver-directed) 🟡 [27] | The only ageing-pathway gene with **any** in-dog delivery experience. Over-expression risks: bone loss, growth suppression, appetite/body-weight effects reported in rodents ❓ | ✅ mouse; 🟡 dog |
| **αKlotho** | One of the three genes in Davidsohn 2019; AAV-delivered ✅ [26] | The PNAS paper's single formulation that treated all 4 diseases was **AAV:sTGFβR2 + AAV:FGF21 — αKlotho was not in it** ✅ [26]; αKlotho did contribute elsewhere (sTGFβR2 + αKlotho gave the largest heart-failure gains) ✅ [26] [verifier-corrected: resolved from full text] | ✅ mouse only |
| **sTGFβR2** (TGF-β decoy) | Reduced renal medullary atrophy by **75%** in combination with FGF21 in mice ✅ [26]; in RJB-01 it is the TGFβ1-lowering arm 🟡 [20] | TGF-β is immunoregulatory and tumour-suppressive; chronic blockade carries autoimmunity and neoplasia concerns ❓ | ✅ mouse; 🟡 dog |
| **OSK (Oct4/Sox2/Klf4) partial reprogramming** | Cyclic AAV9-OSK in 124-week-old male mice: **+109% median remaining lifespan**, improved frailty ✅ [28]; epigenetic age-reversal markers shown in **human keratinocytes**, not the mice ✅ [28] [verifier-corrected] | **No dog study.** Teratoma/dedifferentiation risk is the central hazard; a mouse study of in vivo **chemical** reprogramming (preprint 2025, now published in *Aging Cell* 2026) reports toxic lipid-droplet accumulation and weight loss at higher doses ✅ [29] [verifier-corrected] | ✅ mouse only |

**Why these are the better near-term bets [SPECULATIVE]:** they are **secreted factors deliverable somatically to the liver or muscle**, with a dose-response you can titrate, no developmental consequence, no germline, and — critically — dogs already tolerate liver- and muscle-directed AAV for years ✅ [6][8].

### 3.3 Other loci sometimes named

- **TP53 / CDKN2A** copy-number approaches (cancer resistance): cancer is the dominant cause of death in many large breeds, so cancer-resistance edits are a plausible *lifespan* lever distinct from "slowing ageing." No dog work ❓. **[SPECULATIVE]**
- **Breed-specific disease alleles** (e.g. the Cavalier King Charles MMVD predisposition, the Briard RPE65 mutation ✅ [7]): editing these is uncontroversially *therapeutic* and would raise breed-average lifespan without touching ageing biology. **This is the least ethically fraught and most tractable genomic intervention on dog lifespan, and it is strangely under-discussed [SPECULATIVE].**
- **Multimorbidity genetics**: a 2026 GeroScience paper treats multimorbidity as a mortality predictor in companion dogs 🟡 [30] — useful for endpoint design rather than target selection.

### 3.4 Risks that apply to all of the above

1. **Off-targets.** Zou et al. screened 16 sites and found none ✅ [1] — reassuring but a 2015-era standard; modern whole-genome off-target assessment in dogs is essentially absent from the literature I surveyed ❓.
2. **Mosaicism.** Only 1 of 2 edited beagles had a usable genotype ✅ [1]. This is why CRISPR→SCNT dominates.
3. **Pleiotropy.** Van Eenennaam's point on the Colossal work applies in full: edits selected for one trait may have effects "not compatible with survival" ✅ [4]. The dog ageing targets are all pleiotropic by construction — IGF1 sets body size, FGF21 sets energy balance, TGF-β sets immune tone.
4. **Dwarfism and metabolic cost** of GH/IGF-1-axis germline edits **[SPECULATIVE]**.
5. **Immunogenicity and re-dosing.** A 12-year dog on an AAV therapy will need re-dosing; pre-existing and induced capsid immunity is the known obstacle, and the dog haemophilia work shows re-dosing is possible only by switching serotype 🟡 [8].
6. **Welfare cost of the production pipeline** — surrogates, oocyte donors, surgery, C-sections, perinatal losses ✅ [3][4].
7. **No long-term data.** The longest canine editing follow-up I found is 8 weeks (Amoasii ✅ [6]); the longest canine AAV *gene therapy* follow-up is multi-year (RPE65 ≥3 yr in primary data, >7 yr unconfirmed ❓ [7], FIX >17 mo ✅ [8], RJB-01 up to 3 yr 🟡 [20]) [verifier-corrected].

---

## 4. Ethics, welfare, regulation, public opinion

### 4.1 Ethical structure of the problem

The dog case has a feature human gene editing does not: **the dog cannot consent and does not benefit from the owner's motivation.** Bioethicist Jessica Pierce's argument against longevity *drugs* applies with more force to editing — "These drugs are not about dogs or dog welfare. They're about humans," and owner decisions "may have a profound capacity to inflict suffering" 🟡 [31]. Against this: much of what shortens dog lives is **human-created**, via breed standards that fixed disease alleles and extreme morphologies. An argument that editing is *corrective* of a human-imposed harm is available and, in my view, stronger for disease-allele correction than for enhancement **[SPECULATIVE]**.

Distinct ethical tiers, which should not be collapsed:

| Tier | Example | Creates a new animal? | Ethical weight |
|---|---|---|---|
| **1. Somatic therapy for a diagnosed disease** | AAV-CRISPR for DMD ✅ [6]; RJB-01 for MMVD 🟡 [20] | No | Conventional veterinary ethics |
| **2. Somatic prophylaxis / ageing intervention in an existing pet** | Hypothetical AAV-FGF21 for healthspan | No | Needs consent proxy, reversibility, long-term safety |
| **3. Germline correction of a breed disease allele** | Removing the Briard RPE65 mutation | Yes | Arguably welfare-positive for the breed; still requires SCNT pipeline |
| **4. Germline ageing engineering** | IGF1-AS edit for longevity | Yes | Highest burden: pleiotropy, surrogates, no consent, irreversible, heritable |
| **5. Enhancement / novelty** | MSTN knockout for muscle 🟡 [16]; coat-colour edits ✅ [5] | Yes | Weakest justification; also the category with the most actual completed work |

**That tier 5 has the most completed dog work while tier 2 has none is the field's central moral embarrassment [SPECULATIVE].**

### 4.2 Regulation

- Heritable IGAs in animals are regulated by FDA CVM **as new animal drugs** 🟡 [11][12].
- **GFI #187A** (risk-based approach, **final May 2024**) sorts IGAs into **Category 1** (no pre-market consultation), **Category 2** (may avoid an approval application where risks are understood and mitigated; enforcement discretion; FDA aims to respond to a Category 2 request within 180 days), and **Category 3** (approval application required, data proportionate to risk) ✅ [11] [verifier-corrected: 180-day window is a general 187A Category 2 target, not specific to disease models].
- **GFI #187B** (approval process, draft 2 May 2024, **final January 2025**) covers multi-IGA applications, molecular and phenotypic characterisation, durability across generations, food safety where relevant, and environmental containment 🟡 [12].
- **GFI #251** (draft, Jan 2025) covers food-producing species as contained disease models 🟡 [12].
- **Companion animals are not worked through.** The 187A PDF itself never mentions dogs or companion animals; its Category 1 covers only non-food species regulated by another agency or kept in contained lab research, and its examples centre on food-producing species and research models ✅ [11] [verifier-corrected: checked in primary]. The nearest pet precedent it cites is **GloFish** (fluorescent aquarium fish), which FDA let go to market without an approval application ✅ [11]. I could find **no dog-specific category determination, approval, guidance example, or enforcement action** ❓ [12]. (#187B was not read in the primary.) A gene-edited pet dog would nominally need a Category determination or a new-animal-drug approval, but **there is no precedent**.
- **Somatic gene therapy in dogs** falls under the ordinary new-animal-drug / conditional-approval framework (which is how Rejuvenate Bio and Phibro framed RJB-01) 🟡 [20][32] — i.e. the **expanded conditional approval** pathway created by ADUFA IV (2018), §571 FD&C Act, GFI #261 final July 2021 ✅ [33].
- **Colossal's wolf work has no identified regulator** in the sources I read ✅ [4] — created in the US, from a non-domestic species, with dog surrogates, apparently outside any described premarket framework ❓. This is a live gap: the same technical pipeline applied to dogs would sit in the same grey zone **[SPECULATIVE]**.
- **EU/UK:** EU veterinary medicines fall under Regulation (EU) 2019/6 (EMA); the UK under the Veterinary Medicines Regulations (VMD) 🟡 [34]. **No EU or UK position on gene-edited companion animals or on lifespan-extension indications was located** ❓. The EU's general stance on GMO animals is substantially more restrictive than the US framework, which would likely make Europe a non-market for edited dogs **[SPECULATIVE]**.
- **Cloning** is commercially legal in the US, South Korea and China with no species-specific federal premarket approval that I could identify ❓; several jurisdictions restrict pet cloning on welfare grounds ❓.

### 4.3 Public opinion

Direct survey data on **gene-editing pet dogs** appears not to exist ❓. The adjacent literature is consistent:

- Gene-edited **animals** attract **less public support than gene-edited plants**, and support is **higher when the purpose is animal health** rather than production or enhancement 🟡 [13].
- In a US study (n=338), the topics people asked most about were **gene editing in general and animal welfare** — welfare is the public's primary lens 🟡 [14].
- An Australian study found respondents comfortable with editing human and animal embryos **for research and human-health purposes**, with **moral concern a stronger predictor than hereditary concern** in nearly all applications 🟡 [15].
- Pew's earlier work on genetically engineered and cloned animals documents substantial moral unease about animal biotechnology 🟡 [35].

**Inference [SPECULATIVE]:** a *somatic therapy to keep an existing, loved dog healthier* is likely to be publicly acceptable; *creating a cloned, germline-edited "longevity breed"* is likely not — and the surrogate-dog and C-section logistics would be the flashpoint, exactly as they were in the Colossal coverage ✅ [4].

---

## Open questions / gaps

1. **Has anyone edited an ageing gene in a dog?** I found nothing — but Chinese academic and Sinogene-affiliated programmes are the most likely place for unpublished or non-English-indexed work ❓. Worth a targeted CNKI / Chinese-language search.
2. **Colossal's embryo-transfer numbers conflict** between Time ("one embryo took hold in each mother", no miscarriage/stillbirth) and Wikipedia ("4 implanted, 3 survived") ❓. The dire-wolf genome preprint is now published (*Cell Genomics*, Aug 2026) [36], but its abstract is about ancestry only; the editing and transfer data remain unpublished as far as the verifier could find ❓ [verifier-corrected].
3. **What regulator, if any, reviewed the Colossal wolves?** Not stated in any source I read ❓.
4. **Does GFI #187A/#187B actually cover companion animals?** Verifier read the 187A PDF (May 2024): it contains no dog or companion-animal example; GloFish is its only pet precedent ✅. The final #187B (Jan 2025) was **not** read in the primary ❓ [verifier-corrected].
5. **Base/prime editing in dogs** — I found no in vivo canine study, and a verifier Europe PMC search (2019–2026) also found none ❓. That search did turn up other recent germline-edited dog work this file does not cover — e.g. an RPGR-edited X-linked retinitis pigmentosa beagle model made by zygote editing (Xie et al., *Exp Eye Res* 2025), SCNT-based genome-edited dogs (Kim et al., *BMC Biotechnol* 2022), and a Can f 1 allergen knockout (Walker et al., *CRISPR J* 2026; not checked whether live dogs were produced) — none ageing-related [verifier-added].
6. **Long-term immunology of AAV in dogs** across repeat dosing over a 12-year lifespan: unaddressed in anything I read ❓.
7. **IGF1-AS mechanism.** Plassais 2022 localises the causal variant to a non-coding antisense transcript ✅ [10]; whether it is editable in a graded, adult-onset, non-dwarfing way is entirely unknown ❓. This is the highest-value open biological question for the editing route.
8. **Off-target standards for dogs.** No modern whole-genome off-target survey in edited dogs was located ❓.
9. **No public-opinion survey on editing pet dogs** exists that I could find ❓ — a cheap, high-value study for anyone wanting to anticipate the social licence problem.
10. **Welfare-cost accounting.** Nobody has published a per-animal welfare audit of the CRISPR→SCNT→surrogate dog pipeline (oocyte donors, recipient surgeries, pregnancy losses, perinatal deaths) ❓. Without it, tier-3/4/5 ethical arguments are being made on anecdote.

---

## Sources

1. Zou Q, Wang X, Liu Y, Ouyang Z, Long H, Wei S, Xin J, Zhao B, Lai S, Shen J, Ni Q, Yang H, Zhong H, Li L, Hu M, Zhang Q, Zhou Z, He J, Yan Q, Fan N, Zhao Y, Liu Z, Guo L, Huang J, Zhang G, Ying J, Lai L, Gao X. "Generation of gene-target dogs using CRISPR/Cas9 system." *Journal of Molecular Cell Biology* 7(6):580–583 (2015). DOI 10.1093/jmcb/mjv061. https://academic.oup.com/jmcb/article/7/6/580/2459501
2. Zhao H, Zhao J, Wu D, Sun Z, Hua Y, Zheng M, Liu Y, Yang Q, Huang X, Li Y, Piao Y, Wang Y, Lam SM, Xu H, Shui G, Wang Y, Yao H, Lai L, Du Z, Mi J, Liu E, Ji X, Zhang YQ. "Dogs lacking Apolipoprotein E show advanced atherosclerosis leading to apparent clinical complications." *Science China Life Sciences* 65(7):1342–1356 (2022). DOI 10.1007/s11427-021-2006-y.
3. Wikipedia, "Snuppy," accessed 2026-10-04 (summarising Lee BC et al., *Nature*, 2005; and the 2017 *Scientific Reports* re-cloning paper). https://en.wikipedia.org/wiki/Snuppy
4. Jeffrey Kluger, "The Return of the Dire Wolf," *Time*, April 2025. https://time.com/7274542/colossal-dire-wolf/
5. Wikipedia, "Colossal Biosciences dire wolf project," accessed 2026-10-04. https://en.wikipedia.org/wiki/Colossal_Biosciences_dire_wolf_project
6. Amoasii L, Hildyard JCW, Li H, Sanchez-Ortiz E, Mireault A, Caballero D, Harron R, Stathopoulou TR, Massey C, Shelton JM, Bassel-Duby R, Piercy RJ, Olson EN. "Gene editing restores dystrophin expression in a canine model of Duchenne muscular dystrophy." *Science* 362(6410):86–91 (2018). DOI 10.1126/science.aau1549.
7. Acland GM, et al. "Gene therapy restores vision in a canine model of childhood blindness." *Nature Genetics* 28:92–95 (2001); context via **Pierce EA, Bennett J**, "The Status of RPE65 Gene Therapy Trials: Safety and Efficacy," *Cold Spring Harb Perspect Med* 5(9):a017285 (2015) [verifier-corrected: not Cideciyan]; durability via Acland GM, Aguirre GD, Bennett J, et al., *Mol Ther* 12(6):1072–1082 (2005); https://perspectivesinmedicine.cshlp.org/content/5/9/a017285.full.pdf ; Cornell Chronicle, "Gene therapy restores vision to dogs blinded by inherited disease," April 2001.
8. Mount JD, et al. "Sustained phenotypic correction of hemophilia B dogs with a factor IX null mutation by liver-directed gene therapy." *Blood* 99(8):2670–2676 (2002), PMID 11929752; Herzog RW et al., "Long-term correction of canine hemophilia B by gene transfer of blood coagulation factor IX mediated by adeno-associated viral vector," *Nature Medicine* 5:56–63 (1999); and AAV2/8 re-treatment work in *Blood*.
9. Sutter NB, Bustamante CD, Chase K, et al. "A single IGF1 allele is a major determinant of small size in dogs." *Science* 316(5821):112–115 (2007). DOI 10.1126/science.1137045. https://www.science.org/doi/10.1126/science.1137045
10. Plassais J, vonHoldt BM, Parker HG, et al. "Natural and human-driven selection of a single non-coding body size variant in ancient and modern canids." *Current Biology* 32(4):889–897 (2022). DOI 10.1016/j.cub.2021.12.036. https://www.cell.com/current-biology/fulltext/S0960-9822(21)01723-1 ; summarised in Science, "Gene for 'toy' dog breeds found in ancient wolves," Jan 2022.
11. FDA CVM GFI #187A, "Heritable Intentional Genomic Alterations in Animals: Risk-Based Approach" (final, May 2024). https://www.fda.gov/media/74614/download
12. Covington & Burling, "FDA Finalizes Guidance on its Approval Process for Intentional Genomic Alterations in Animals, Proposes Framework for Regulating Alterations in Food-Producing Disease Models," Jan 2025; and "FDA Updates its Approach to Genomic Alterations in Animals," May 2024. https://www.cov.com/en/news-and-insights/insights/2025/01/fda-finalizes-guidance-on-its-approval-process-for-intentional-genomic-alterations-in-animals-proposes-framework-for-regulating-alterations-in-food-producing-disease-models ; Federal Register notice 2024-09279 (2 May 2024) and 2024-31532 (7 Jan 2025).
13. "Public attitudes toward the use of technology to create new types of animals and animal products." *Animal Welfare* (Cambridge). https://www.cambridge.org/core/journals/animal-welfare/article/public-attitudes-toward-the-use-of-technology-to-create-new-types-of-animals-and-animal-products/43767D9B43A65E03829174A1741088DF
14. Kuo C, Koralesky KE, von Keyserlingk MAG, Weary DM. "Gene editing in animals: What does the public want to know and what information do stakeholder organizations provide?" *Public Understanding of Science* 33(6) (2024), DOI 10.1177/09636625241227091; n=338 US residents. https://www.researchgate.net/publication/378068511
15. Critchley C, Nicol D, Bruce G, Walshe J, Treleaven T, Tuch B. "Predicting Public Attitudes Toward Gene Editing of Germlines: The Impact of Moral and Hereditary Concern in Human and Animal Applications." *Frontiers in Genetics* (2018); Australian sample n=1,004. PMC6334182. https://pmc.ncbi.nlm.nih.gov/articles/PMC6334182/
16. MIT Technology Review, "First Gene-Edited Dogs Reported in China," 19 Oct 2015; CNN, "Super-strong, genetically engineered dogs in China," 28 Oct 2015; Science News Explores, "Gene editing creates buff beagles."
17. Feng C, Wang X, Shi H, Yan Q, Zheng M, Li J, Zhang Q, Qin Y, Zhong Y, Mi J, Lai L. "Generation of ApoE deficient dogs via combination of embryo injection of CRISPR/Cas9 with somatic cell nuclear transfer." *J Genet Genomics* 45(1):47–50 (2018). DOI 10.1016/j.jgg.2017.11.003 [verifier-corrected: full citation]; ResearchGate record https://www.researchgate.net/publication/322960056
18. CNN, "Chinese firm clones gene-edited dog in bid to treat cardiovascular disease," 25 Dec 2017. https://www.cnn.com/2017/12/25/health/china-dog-cloning-for-disease-intl
19. Kim MJ, Oh HJ, Kim GA, Setyawan EMN, Choi YB, Lee SH, Petersen-Jones SM, Ko CJ, Lee BC (Seoul National University et al.). "Birth of clones of the world's first cloned dog." *Scientific Reports* 7:15235 (2017). https://www.nature.com/articles/s41598-017-15328-2
20. dvm360, "Gene therapy demonstrates benefit to dogs with myxomatous mitral valve disease," 18 May 2023 (Rejuvenate Bio RJB-01 data at the 26th ASGCT Annual Meeting). https://www.dvm360.com/view/gene-therapy-demonstrates-benefit-to-dogs-with-myxomatous-mitral-valve-disease
21. "Safer and efficient base editing and prime editing via ribonucleoproteins delivered through optimized lipid-nanoparticle formulations." *Nature Biomedical Engineering* (Nov 2024). https://www.nature.com/articles/s41551-024-01296-2 ; "Improved split prime editors enable efficient in vivo genome editing," *Cell Reports* (2024); "Engineered virus-like particles for transient delivery of prime editor ribonucleoprotein complexes in vivo," *Nature Biotechnology* (2023).
22. "Diverse breeds, diverse lifespans: understanding longevity in domestic dogs." *J Vet Sci* 26(Suppl 1) (2025). DOI 10.4142/jvs.25175. https://pmc.ncbi.nlm.nih.gov/articles/PMC12520860/
23. dvm360, "FDA determines drug for lifespan extension in large dogs to have a Reasonable Expectation of Effectiveness," 28 Nov 2023 (source of the "up to 28×" IGF-1 figure). https://www.dvm360.com/view/fda-determines-drug-for-lifespan-extension-in-large-dogs-to-have-a-reasonable-expectation-of-effectiveness
24. "BobBurgers," "The likely first longevity drug is based on sketchy science," LessWrong, 12 Dec 2023 — non-peer-reviewed re-analysis of a 2011 canine IGF-1 dataset. https://www.lesswrong.com/posts/vHSkxmYYqW59sySqA/the-likely-first-longevity-drug-is-based-on-sketchy-science
25. BioSpace (Business Wire), "Loyal Earns Third Efficacy Acceptance (RXE) from the FDA for Canine Lifespan Extension," 16 Sep 2026. https://www.biospace.com/press-releases/loyal-earns-third-efficacy-acceptance-rxe-from-the-fda-for-canine-lifespan-extension
26. Davidsohn N, Pezone M, Vernet A, Graveline A, Oliver D, Slomovic S, Punthambaker S, Sun X, Liao R, Bonventre JV, Church GM. "A single combination gene therapy treats multiple age-related diseases." *PNAS* 116(47):23505–23511 (2019). DOI 10.1073/pnas.1910073116.
27. PackGene industry summary, "Rejuvenate Bio Raises $6M and Partners with Merck Animal Health to Advance Veterinary Gene Therapies," 8 Jun 2026 (describes RJB-0402 as liver-directed FGF21). https://www.packgene.com/frontier/060826-rejuvenate-bio/
28. Macip CC, Hasan R, Hoznek V, Kim J, Lu YR, Metzger LE, Sethna S, Davidsohn N. "Gene Therapy-Mediated Partial Reprogramming Extends Lifespan and Reverses Age-Related Changes in Aged Mice." *Cellular Reprogramming* 26(1):24–32 (2024), DOI 10.1089/cell.2023.0072, PMC10909732; Rejuvenate Bio press release; bioRxiv preprint DOI 10.1101/2023.01.04.522507 (4 Jan 2023). https://rejuvenatebio.com/press-releases/rejuvenate-bio-announces-gene-therapy-mediated-partial-reprogramming-extends-lifespan-and-reverses-age-related-changes-in-the-journal-cellular-reprogramming
29. Mitchell W, et al. "In vivo chemical reprogramming is associated with a toxic accumulation of lipid droplets hindering rejuvenation." bioRxiv, 25 Jun 2025; published in *Aging Cell* (2026); PMC12835892 [verifier-corrected].
30. Foreman ER, Corlin L, Creevy KE, Hoffman JM, Dog Aging Project Consortium. "Multimorbidity as a predictor of mortality in companion dogs." *GeroScience* (2026). DOI 10.1007/s11357-026-02342-4.
31. Slate, "This pill from Loyal promises to extend your pet's life—but some experts think that's a bad idea," April 2025 (Jessica Pierce; Daniela Korec). https://slate.com/technology/2025/04/dogs-pets-pill-longevity-extend-lifespan-loyal-veterinary-ethics.html
32. Business Wire, "Phibro Animal Health Corporation and Rejuvenate Bio Announce Agreement to Develop Gene Therapy for Mitral Valve Disease in Canines," 22 Jun 2022. https://www.businesswire.com/news/home/20220622005079/en/
33. FDA CVM GFI #261, "Eligibility Criteria for Expanded Conditional Approval of New Animal Drugs," final, July 2021. https://www.fda.gov/regulatory-information/search-fda-guidance-documents/cvm-gfi-261-eligibility-criteria-expanded-conditional-approval-new-animal-drugs
34. EMA, "Veterinary Medicinal Products Regulation" (Regulation (EU) 2019/6) overview. https://www.ema.europa.eu/en/veterinary-regulatory-overview/veterinary-medicinal-products-regulation ; UK Veterinary Medicines Directorate.
35. Pew Initiative on Food and Biotechnology, "Exploring the Moral and Ethical Aspects of Genetically Engineered and Cloned Animals." https://www.pew.org/-/media/legacy/uploadedfiles/wwwpewtrustsorg/news/press_releases/food_and_biotechnology/pifbmoralethicalaspectsgeandclonedanimalspdf.pdf
36. Gedman GL, Pirovich KM, Oppenheimer J, Hyseni C, Cassatt-Johnstone M, … Lamm B, Shapiro B. "On the ancestry and evolution of the extinct dire wolf." *Cell Genomics* 6(8):101306 (Aug 2026). DOI 10.1016/j.xgen.2026.101306; PMID 42508403; PMC13477035. Preprint: bioRxiv DOI 10.1101/2025.04.09.647074. [added by verifier]
37. Peer-reviewed critiques of the Colossal project, located via Europe PMC by the verifier (bibliographic details only): Jensen-Seaman MI, *Anat Rec* (2026), DOI 10.1002/ar.70049; Ilic D, *Stem Cell Reports* (2025), DOI 10.1016/j.stemcr.2025.102505; Höglund J, *EMBO Rep* (2025), DOI 10.1038/s44319-025-00474-w; Azevedo A, *Animals* 15(13):1839 (2025), DOI 10.3390/ani15131839. [added by verifier]

---

## Verification notes

Independent check by Opus 5.5 on 2026-10-04 (full report: ../07_verification/interventions_verification.md). Corrections made in this file, each marked [verifier-corrected]:

1. **Zou 2015 mosaicism**: puppy #5 had essentially 100% mutated reads (86.8% +1 bp / 13.1% −8 bp). "~87% of reads" was one allele's share, not the edited fraction. Dog names (Tiangou #5, Hercules #11) confirmed in the primary paper.
2. **Snuppy re-clones (2017)** were made by **Seoul National University** (Lee BC group; *Sci Rep* 7:15235), not Sooam Biotech as Wikipedia states.
3. **ApoE dogs**: Zhao 2022 has 23 authors, not 24. The generation-numbers source is now cited as Feng et al. 2018 *J Genet Genomics* (numbers still unverified). The "13 puppies from 13 recipients" was presented as an efficiency gain, but only 1 of those 13 puppies was edited.
4. **Colossal**: all ✅ tags based on Time and Wikipedia lowered to 🟡, since these are secondary sources. Added the Aug 2026 *Cell Genomics* paleogenome paper (it does not report the edits) and four peer-reviewed critiques. Time's transfer account clarified (two surrogates, plus a third in a later procedure).
5. **RPE65**: the CSH Perspect Med review is by Pierce & Bennett, not Cideciyan. ">7 years" durability is unconfirmed; primary data show ERG stable at 3 years.
6. **Plassais 2022**: the abstract shows the small-size allele is ancestral (it does predate the large allele). The "≥54,000 years" figure is not in the abstract and is flagged ❓. Full citation added.
7. **Davidsohn 2019 combination** resolved from the full text: sTGFβR2 + FGF21 treated all four diseases, and αKlotho was not part of that formulation.
8. **OSK (Macip 2024)** upgraded to ✅; epigenetic reversal was shown in human keratinocytes. The chemical-reprogramming lipid-droplet preprint is now published in *Aging Cell* 2026.
9. **GFI #187A** read in the FDA PDF: no dog or companion-animal examples; GloFish is the nearest pet precedent; the 180-day window is a general Category 2 target. #187B was not read in the primary.
10. **LessWrong r≈0.07** described more precisely (correlation with age, from an 88-dog 2011 dataset).
11. Haemophilia B (Mount 2002) upgraded to ✅ from the abstract. Public-opinion citations [14][15] completed (Kuo 2024; Critchley 2018, n=1,004).
12. Added a note on recent non-ageing germline-edited dog models (RPGR beagles 2025, and others) found in a verifier literature search.

**Confirmed without change** (selection): Zou 2015 numbers (35 zygotes → 10 recipients → 8 pregnancies → 27 puppies → 2 edited; 16 off-target sites clean); ApoE dog phenotype and germline transmission (Zhao 2022 abstract); Amoasii 2018 (3–90% skeletal, 92% cardiac, n = 4); Sutter 2007; Colossal 20 edits / 14 genes / 15 + 5 split / MC1R + MFSD12 / birth dates (secondary sources agree); Snuppy 1,095 embryos / 123 surrogates; Kuo 2024 n=338.
