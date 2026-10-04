# MAMMAL video (AI Search, 2026-05-13) — high-precision documentation of what the video says
> Part of the dog-ageing research dossier · Written 2026-10-04 by Fable 5.1 subagent · Status: independently verified by Opus 5.5 on 2026-10-04 — see ../07_verification/video_transcript_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

> **Public edition:** the video's spoken script is the creator's copyrighted work, so claims are paraphrased with timestamps rather than quoted; watch the [video](https://www.youtube.com/watch?v=s3rNDndvav0) at the timestamp for exact wording. The transcripts used for this analysis are not redistributed.

**Scope and rules of this document.** This is documentation of *what the video says*, not of what is true. Every timestamp comes from the Whisper SRT/JSON (segment start, `mm:ss`); the analysis worked from the Whisper transcript, cross-checked against the YouTube auto-captions; in this public edition the video's wording is paraphrased rather than quoted, apart from a few short quotes where the exact words are the point. Where the two ASR sources disagree, both readings are given. The documenter's own additions are confined to clearly labelled **Note** boxes, the "flag" column of the claims table, the correction table, and the rhetorical-analysis section. Claims are *not* fact-checked here against the MAMMAL paper; that is a separate agent's job (see "Hand-off to the fact-checker" at the end). The companion clean corrected transcript (same chapter numbering) is not redistributed; see the [video](https://www.youtube.com/watch?v=s3rNDndvav0).

---

## 1. Video metadata

| Field | Value | Source |
|---|---|---|
| Title | **The biggest AI breakthrough in medicine & drug discovery** | YouTube oEmbed + watch page |
| Channel | **AI Search** (handle `@theAIsearch`; channel ID `UCIgnGlGkVRhd4qNFcEwLL4A`) | oEmbed (`author_name`, `author_url`), watch page (`ownerChannelName`) |
| URL / video ID | https://www.youtube.com/watch?v=s3rNDndvav0 · `s3rNDndvav0` | — |
| Published | **2026-05-13**, 20:27:14 (UTC−7) = 2026-05-14 03:27 UTC; page shows "May 13, 2026" | watch page `publishDate` / `uploadDate` / `datePublished` |
| Length | **1,914 s ≈ 31:54** (YouTube `lengthSeconds` 1914; a second field says 1915). Speech ends at **31:53.7** (last Whisper segment 1912.98–1913.74 s; last auto-caption cue starts 31:53). | watch page; Whisper JSON; auto-caption SRT (transcripts not redistributed) |
| View count | 122,790 (at fetch time, 2026-10-04) | watch page `viewCount` |
| Sponsor | **Runway** (product: *Runway Agent*; code "AGENT50", 50 % off first 3 months). Segment **13:48–15:17**. Description link: `https://runwayml.com/aisearch-agent` | transcript; description |
| Description (first line) | (paraphrased) presents MAMMAL as a biology foundation model covering genes, proteins and small molecules, claims it beats AlphaFold 3, and adds the hashtags #ai #ainews #science #agi #singularity | watch page `shortDescription` |
| Paper linked in description | "Full paper: https://www.nature.com/articles/s44386-026-00047-4" (npj Drug Discovery) | description |
| Other description links | a related-video recommendation, https://youtu.be/QvN6Tu6dHYM; newsletter https://aisearch.substack.com/; https://ai-search.io/; https://ko-fi.com/aisearch; equipment affiliate links | description |
| Presenter's own chapter markers (from description) | 0:00 MAMMAL intro · 0:38 Problems with drug design · 1:36 How biology works · 3:23 How drug design works · 5:24 Why modern tech fails · 6:47 How MAMMAL works · 10:10 How good is it · 10:59 Predicting drug toxicity · 13:48 Runway Agent · 15:19 Labelling cells based on gene activity · 16:05 New cancer drug discovery · 20:19 Implications for drug repurposing · 21:16 Antibodies · 22:17 MAMMAL vs Alphafold · 23:29 Why Alphafold failed · 26:05 Designing new drugs · 27:27 Generating antibody fingers · 29:29 Implications for medicine | description |
| Format | Single presenter voice-over with on-screen slides/figures (e.g. he refers to an on-screen results table at 10:33, to on-screen drug labels at 18:25 and to an on-screen Tylenol SMILES at 07:58). On-screen content is **not** in the transcripts. | transcript |
| Source files used | Whisper ASR transcript as text, SRT and JSON (1,966 segments, word-level `s/e` times, no confidence scores); YouTube auto-captions as text and SRT (825 cues). Transcripts not redistributed (creator's copyright); [watch the video](https://www.youtube.com/watch?v=s3rNDndvav0) instead | — |

> **Note (documenter, not from the video).** The video never names who built MAMMAL. The paper linked in its own description is the npj Drug Discovery article "MAMMAL – Molecular Aligned Multi-Modal Architecture and Language for biomedical discovery" (IBM Research; preprint arXiv:2410.22367, first posted Oct 2024). The video's remark that a new paper has just come out (00:06) therefore refers to the journal version (published early May 2026, nine days before the video), not to a new model. The fact-check agent should confirm dates.

---

## 2. TL;DR — the video's argument in 14 bullets

1. **Premise:** drug development is framed as a 10-year, billion-dollar gamble with a ~90 % failure rate (00:45–01:05), despite genome sequencing and protein-structure AI.
2. **Biology primer:** DNA → genes → proteins; gene expression = which genes are active and how strongly; disease (e.g. cancer) arises from mutations or mis-set expression (01:41–03:20).
3. **Drug design = identify the culprit target, then make a key that fits its lock**; two drug classes matter for the paper: small molecules (Tylenol-like, able to slip into cells) and antibodies (large, precise binders likened to clamps; act outside or on cells); side effects = the key also fitting other locks (03:22–05:24).
4. **Today's AI tools are siloed** (AlphaFold for structure, Evo 2 for DNA, separate compound screeners) — likened to crime-scene detectives, each holding one clue, who barely communicate [verifier-corrected: "detectives who each hold one clue" was printed as a quote but is a paraphrase] (05:24–06:43).
5. **MAMMAL's pitch:** a single model said to grasp chemistry, genetics and protein structure at the same time (06:46), **pre-trained on 2 billion samples** drawn from OAS, UniProt, ZINC, PubChem and CELLxGENE (06:58–07:22).
6. **Everything becomes text:** SMILES strings for molecules; a cell = genes **ranked by expression level**, most active first [verifier-corrected: wording; paraphrased in this edition]; proteins/antibodies = amino-acid chains (07:41–08:42).
7. **A "modular tokenizer"** (umbrella tokenizer with per-domain sub-dictionaries) turns each modality into tokens/embeddings that are **combined in one shared multi-dimensional space**, letting the model learn cross-domain relationships (09:05–10:05).
8. **Results claim:** evaluated on **11 benchmarks** spanning the drug-discovery pipeline, with state-of-the-art results claimed on every one of them (10:18–10:44).
9. **Safety benchmarks:** beat the specialist MoLFormer (trained on >1 billion molecules) on **BBBP** (blood-brain-barrier penetration) and **ClinTox** (clinical toxicity / FDA approval) — framed as an all-round decathlete beating a specialist swimmer [verifier-corrected: wording; paraphrased in this edition] (10:59–13:05); the presenter infers that multimodality is an advantage, not a distraction (13:11–13:46).
10. **Cell-type annotation on Zheng68K:** +7.5 % over state of the art (15:18–16:01).
11. **Headline: cancer drug response.** Four drugs absent from training (carfilzomib, nintedanib, infigratinib, vemurafenib; 3 of 4 with max Tanimoto < 0.7 to anything seen) ranked for potency across **805** tumour cell types; MAMMAL put **carfilzomib first** although it is approved only for blood cancers and, according to the video, doctors had regarded it as useless against solid tumours; a physical lab experiment is said to have matched the ranking in **~95 %** of the 805 cell types (16:04–20:17). Implication: drug repurposing at scale (20:18–21:09).
12. **MAMMAL vs AlphaFold 3** on antibody–antigen binding (a yes/no question: do the two bind?) across **7 targets: MAMMAL won on 5** (22:46–23:08). Presenter's explanation: **30–40 % of human protein sequence is intrinsically disordered** (a wet-spaghetti analogy); targets like EGFR and HER2 are full of IDRs; AlphaFold learned only from static structural snapshots, whereas a sequence model works from the mathematics of the sequence itself (23:23–25:57).
13. **Generative test:** CDRs (the antibody's "fingers" in the video's metaphor) erased from thousands of SAbDab antibodies and MAMMAL asked to fill them in from the target alone; beat specialised methods, with a **19 % improvement on CDR-H3**, described as the hardest and most variable part (25:58–29:27).
14. **Zoom-out (hype + hedges):** the presenter suggests MAMMAL may be "the first true foundation model for biology" [verifier-corrected]; predicts a massive acceleration in new drugs within months, if true; personalised medicine from a DNA/blood sample; new cancer cures very soon; one of the year's most impactful papers — each hedged on the paper's claims proving true (29:27–31:11).

---

## 3. Chapter-by-chapter outline

Chapter numbers match the clean corrected transcript used for this analysis (not redistributed; [watch the video](https://www.youtube.com/watch?v=s3rNDndvav0) instead). Time ranges are Whisper segment starts; the presenter's own chapter markers (from the description) are given where they exist. Key points are paraphrases of the Whisper text with ASR errors corrected; at most one short quote is kept per chapter, and only where the exact wording matters.

### Ch. 1 — Cold open / hook · 00:00–00:36 · (presenter: "0:00 MAMMAL intro")
**Summary.** Maximal framing: the presenter calls this possibly among the largest advances in medicine and drug discovery for decades; a newly released paper about a model called MAMMAL; promises of new cures (cancer named), faster/cheaper/more accurate drug discovery, personalised medicine. Presenter states intent to simplify a very technical paper.
**Key points.**
- 00:00 Opens by calling the work possibly "one of the biggest breakthroughs" of recent decades for drug discovery and medicine.
- 00:06 Says a new paper has just come out about a new AI model, MAMMAL.
- 00:15 Says it could potentially yield many new cures, naming cancer.

### Ch. 2 — The problem: 90 % failure · 00:38–01:35 · (presenter: "0:38 Problems with drug design")
**Summary.** Sets up the cost/time/failure framing: 10 years, a billion dollars, 90 % failure; roughly 90 % of candidates fail to gain approval. Contrasts with the sequenced genome, smartphones and structure-prediction AI. Bridge analogy: a builder whose bridges collapsed 9 times out of 10 would be out of business [verifier-corrected: wording; paraphrased in this edition].
**Key points.**
- 00:45 Asks the viewer to picture a 10-year, billion-dollar project with a 90 % chance of failure.
- 00:56 Says that, from a promising new medicine through clinical trials, roughly 90 % fail to win approval.

### Ch. 3 — Biology primer · 01:35–03:20 · (presenter: "1:36 How biology works")
**Summary.** DNA as the code of life; genes as instruction manuals for proteins; proteins as tiny machines (signalling, structure, catalysis, immunity). Gene expression introduced as which genes are active and to what degree, controlling protein amounts. Mutation is listed alongside turned up/down (loose). Disease arises from mutations (wrong/no protein) or expression too high/low. Cancer sketched: mutation in a cell-division gene → altered expression/protein → cells grow, ignore stop signals, form tumour. Presenter flags that he is oversimplifying.
**Key points.**
- 02:10 Groups genes being turned up, turned down or mutated under the label gene expression (mutation is not part of the standard definition).
- 03:01 Cancer sketch: a mutation damages a gene controlling cell division, and the resulting proteins push the cell to grow, ignore stop signals and form a tumour.

### Ch. 4 — How drugs are designed · 03:22–05:24 · (presenter: "3:23 How drug design works")
**Summary.** Find the culprit (e.g. a protein telling cancer cells to divide; a viral enzyme), then design a drug to interact with it: lock-and-key analogy (block or change the protein). Two drug types said to be relevant to the paper: small molecules (Tylenol; tiny, stable, pills, enter cells) and antibodies (likened to very precise biological clamps; large; act outside/on cell surface). Difficulty: the body has a billion moving parts → off-target effects (the key may open other locks); need efficacy at safe doses.
**Key points.**
- 03:46 Lock-and-key analogy: the target is the lock and the drug the key.
- 04:14 Introduces antibodies as a much larger drug type, likened to very precise biological clamps.
- 05:02 A drug must be potent enough to halt the disease, selective enough to avoid harming other tissues, and safe to give to people.

### Ch. 5 — Siloed tools · 05:24–06:43 · (presenter: "5:24 Why modern tech fails")
**Summary.** Existing tools are said to grasp only one slice: Google's AlphaFold (protein structure), Evo 2 (reading/generating DNA; presenter has a prior video), compound screeners, clinical-trial analytics. Disease, the presenter argues, runs through the whole system — DNA, gene activity, proteins, cells, whole bodies — but the tools are siloed (different datasets/teams/tasks). Crime-scene analogy: three detectives holding fingerprints / CCTV / autopsy evidence who barely communicate [verifier-corrected: wording; paraphrased in this edition].
**Key points.**
- 05:35 Gives AlphaFold, from Google, as the example of an AI model that predicts protein structures.
- 05:58 Argues that disease does not stay inside the separate silos (folders) that the data are kept in.

### Ch. 6 — MAMMAL introduced · 06:43–07:27 · (presenter: "6:47 How MAMMAL works" starts here)
**Summary.** MAMMAL is said to understand chemistry, genetics and protein structure all at the same time. Scale: pre-trained on **two billion samples**, said to be scraped from essentially every major biological database: Observed Antibody Space (billions of antibody sequences), UniProt (nearly every known protein), ZINC and PubChem (millions of small-molecule structures), CELLxGENE (a large volume of gene-expression data).
**Key points.**
- 06:58 Pre-training used two billion samples.
- 07:01 The data are said to come from essentially every major biological database.

### Ch. 7 — One unified text format · 07:27–08:42
**Summary.** Problem: molecule, gene and antibody data look nothing alike. Solution: every modality is forced into one shared format — character sequences — with each domain keeping its own grammar. Molecules → **SMILES** strings (a 3D structure flattened into a single line; letters = atoms, symbols such as "=" = bonds; Tylenol shown on screen). Genes → every gene in a cell is ranked by activity, most active first (a cell is read as a priority list). Proteins/antibodies → amino-acid chain.
**Key points.**
- 07:52 SMILES is described as compressing a 3D chemical structure into one line of text.
- 08:28 The model treats each cell as a priority list of the genes currently doing the most work.

### Ch. 8 — Modular tokenizer and shared space · 08:42–10:07
**Summary.** Mixed formats are likened to a book that switches from English to sheet music to JavaScript paragraph by paragraph [verifier-corrected: the earlier quoted wording was a paraphrase]. MAMMAL uses a **modular tokenizer**: a tokenizer is explained as a dictionary that translates raw data into a consistent language the AI can use; here an **umbrella tokenizer with specialised sub-dictionaries** (chemistry / genetics / proteins), each converting its modality into tokens and embeddings. The step the presenter highlights: all embeddings are blended into one shared multi-dimensional space, letting the model learn the three domains together, along with the relationships between them.
**Key points.**
- 09:05 Names the design a modular tokenizer.
- 09:46 After conversion to embeddings, all modalities are blended into one shared multi-dimensional space.

### Ch. 9 — Benchmark overview · 10:07–10:48 · (presenter: "10:10 How good is it")
**Summary.** 11 distinct, highly rigorous benchmarks said to span the whole drug-discovery pipeline. A results table is shown on screen. Claim: state of the art across the 11, outright beating the world's previous best models on every task.
**Key points.**
- 10:18 Evaluated on 11 distinct, rigorous benchmarks covering the entire drug-discovery pipeline.
- 10:37 Claims state-of-the-art performance, outright beating the world's previous best models "on all of these tasks".

### Ch. 10 — Safety benchmarks (BBBP, ClinTox) vs MoLFormer · 10:48–13:48 · (presenter: "10:59 Predicting drug toxicity")
**Summary.** Two safety benchmarks described as critical: **BBBP** (blood-brain barrier penetration) and **ClinTox** (clinical toxicity and FDA approval). Digression on the blood-brain barrier (the brain's tight security system): Alzheimer's/Parkinson's drugs must cross it; a heavy liver chemotherapy must not. The prior best on BBBP was **MoLFormer**, said to have been trained solely on more than a billion small-molecule sequences. MAMMAL (a generalist) beat MoLFormer on BBBP and on ClinTox (margin "a few" / "a huge" percentage points — ASR disagreement). Decathlete-vs-swimmer analogy; presenter infers that multimodality is an advantage rather than a distraction, because small molecules exist to act on proteins and change gene expression.
**Key points.**
- 11:04 Introduces BBBP (blood-brain barrier penetration) and ClinTox (a dataset for predicting clinical toxicity and FDA approval).
- 11:59 [verifier-corrected; was 11:57] MoLFormer is described as trained exclusively on more than a billion small-molecule sequences.
- 12:16 Says the hyper-specialised MoLFormer scored very well on BBBP, yet MAMMAL beat it.
- 13:16 Says this proves multimodality is an advantage, not a distraction.

### Ch. 11 — **SPONSOR SEGMENT (Runway)** · **13:48–15:17** · (presenter: "13:48 Runway Agent")
**Boundaries.** Starts 13:48 (the presenter recommends the sponsor, Runway, to people who make videos or online content) and ends 15:17 (the AGENT50 promo code); MAMMAL content resumes at 15:17 (the cell-type labelling test). Content: Runway Agent — autonomous idea-to-video generation, plan preview before rendering, multi-scene/voice-over/music output, 50 % off first three months with code AGENT50, link/QR in description. **Excluded from all content analysis below.** Note the lead-in at 13:46 (the researchers went further) belongs to the MAMMAL content and is interrupted by the ad.

### Ch. 12 — Cell-type annotation (Zheng68K) · 15:17–16:03 · (presenter: "15:19 Labelling cells based on gene activity")
**Summary.** Task: label immune cell types in blood from gene activity (e.g. CD4+ T cell, NK cell) using the **Zheng68K** dataset (described as thousands of gene-activity profiles from many immune cell types). Motivated as important for reading a patient's immune response. Result: **beats the state-of-the-art model by 7.5 %.**
**Key points.**
- 15:55 Reports that MAMMAL beat the state-of-the-art model by 7.5 % and again calls it a huge leap.

### Ch. 13 — Cancer drug response (the "highlight") · 16:02–20:17 · (presenter: "16:05 New cancer drug discovery")
**Summary.** Presenter presents this as proof of a genuine biomedical breakthrough. Setup: show MAMMAL is not regurgitating memorised data — pick **four drugs said to be definitely absent from its training data**: carfilzomib, nintedanib, infigratinib, vemurafenib. Inputs: the drugs' chemical strings (i.e. SMILES; the video does not say SMILES here [verifier-corrected]) plus genetic profiles of over 800 kinds of cancer tumour cells (lung, breast, colon…). Question: rank the four by potency across the cell types. Novelty check: **Tanimoto similarity**; three of the four drugs had maximum Tanimoto similarity below 0.7 to anything in training, and a score below 0.7 is presented as meaning the drugs are essentially structurally different. Task size restated as **805** cancer tumour variations. Prediction: **carfilzomib most potent across most tumours**, nintedanib second, the other two third and fourth (not named at 18:25, where the presenter points at the screen; however, at 19:40 the presenter says the experimental order — which matched the prediction exactly — ran down to vemurafenib as least potent, so the video implies vemurafenib was 4th and, by elimination, infigratinib 3rd [verifier-corrected]). Plot twist: carfilzomib is FDA-approved **only for blood cancers**, and the presenter claims "doctors believed that carfilzomib was useless against solid tumors". Validation: a physical lab experiment testing the drugs on solid cancer cells is said to have matched MAMMAL's predictions exactly — carfilzomib most potent, down to vemurafenib least — with the relative order preserved in approximately 95 % of the 805 cancer cell types. Presenter's gloss: a text-only model correctly inferred an effect that, he says, human experts had for decades assumed would not occur.
**Key points.**
- 16:09 Calls the result proof of a genuine biomedical breakthrough.
- 16:27 Four drugs said to be definitely absent from training were chosen: carfilzomib, nintedanib, infigratinib and vemurafenib. [verifier-corrected: wording; paraphrased in this edition]
- 17:38 Three of the four had maximum Tanimoto similarity below 0.7 to anything MAMMAL had seen.
- 18:17 MAMMAL predicted carfilzomib to be the most potent across most tumours.
- 18:32 Carfilzomib is FDA-approved, but its current approval and use are limited to blood cancers.
- 19:21 The researchers are said to have tested the drugs on solid cancer cells in a physical lab experiment.
- 19:44 The relative order is said to hold in approximately 95 % of the 805 cancer cell types.

### Ch. 14 — Implication: drug repurposing · 20:18–21:09 · (presenter: "20:19 Implications for drug repurposing")
**Summary.** MAMMAL is said to generalise to entirely new compounds and accurately predict their uses — which the presenter equates with the whole field of drug discovery, and repurposing in particular. Repurposing defined (existing/failed drugs tested for other diseases); de novo discovery said to take about 10–15 years and billions of dollars; an AI that scans the existing library is said to open up major opportunities.
**Key points.**
- 20:36 Defines drug repurposing as testing whether an existing drug can treat a different disease.

### Ch. 15 — Antibodies, folding, AlphaFold 3 set-up · 21:09–22:46 · (presenter: "21:16 Antibodies"; "22:17 MAMMAL vs Alphafold")
**Summary.** Antibodies = larger proteins that clamp precisely onto the problem protein. Protein = amino-acid chain folding into a 3D shape that determines binding; Levinthal-style framing (a random search of all folds would outlast the age of the universe, yet physics guides proteins to fold almost instantly). Designing antibody drugs needs sequence + fold + motion + binding. AlphaFold is praised in superlatives (legendary, the industry standard, among the greatest scientific achievements of modern times; Nobel Prize in Chemistry). Rhetorical question: MAMMAL is only a sequence model reading one-dimensional text — how could it beat a 3D-structure specialist?
**Key points.**
- 21:28 Describes a protein as a long amino-acid chain that folds into a complex 3D shape.
- 22:21 Calls AlphaFold highly accurate and notes that its team won a Nobel Prize in Chemistry.
- 22:34 Describes MAMMAL as merely a sequence model that reads text in one dimension.

### Ch. 16 — Antibody–antigen binding vs AlphaFold 3 · 22:46–23:23
**Summary.** Both models are given an antibody and a disease target and asked a yes/no question — will the two bind? — across **seven well-documented targets**; **MAMMAL beat AlphaFold 3 on five of seven.** The presenter finds this remarkable because AlphaFold 3, as he puts it, can directly see 3D shapes.
**Key points.**
- 22:57 Both models were tested on seven well-documented targets.
- 23:03 MAMMAL beat AlphaFold 3 on five of the seven.

### Ch. 17 — Why: intrinsically disordered regions · 23:23–25:57 · (presenter: "23:29 Why Alphafold failed")
**Summary.** The presenter calls the textbook picture of proteins as rigid, static shapes a deeply flawed assumption. He says that for human proteins around 30–40 % of the sequence is made up of intrinsically disordered regions (IDRs), which have no stable 3D shape (a wet-spaghetti analogy). Important targets **EGFR and HER2** (described as notoriously aggressive drivers of breast and stomach cancer) are said to contain many such floppy regions. AlphaFold 3 is said to struggle with them because it was trained only on static, solid 3D structures (frozen snapshots); MAMMAL is said to win on floppy proteins because it does not try to draw a static picture and instead works from the mathematics of the sequence. Claimed consequences: far more robust prediction of antibody binding; every antibody candidate can now be run through this AI.
**Key points.**
- 23:45 For human proteins, around 30–40 % of the sequence is said to be made up of intrinsically disordered regions (IDRs).
- 24:24 Key targets such as EGFR and HER2 are said to contain many floppy disordered regions.
- 25:10 MAMMAL is said to win on floppy proteins because it does not try to depict them as a static picture.
- 25:31 MAMMAL is said to rely on the mathematics of the sequence rather than a structural snapshot.

### Ch. 18 — From analyst to inventor; antibody anatomy · 25:58–27:24 · (presenter: "26:05 Designing new drugs")
**Summary.** Shift from scoring existing candidates to generating new ones: MAMMAL is said to be an inventor as well as an analyst, and its ability to design entirely new antibodies is said to have been tested. Antibody anatomy: Y-shaped protein likened to a giant microscopic claw; stable main body; highly variable tips = **CDRs (complementarity-determining regions)**, likened to fingers, whose amino-acid sequence is said to determine exactly which disease target the antibody can grab; antibody engineering = designing better fingers.
**Key points.**
- 26:14 Says MAMMAL is not only an analyst but can also act as an inventor.
- 26:56 Names the variable tips CDRs (complementarity-determining regions).

### Ch. 19 — CDR fill-in-the-blank on SAbDab · 27:24–28:27 · (presenter: "27:27 Generating antibody fingers")
**Summary.** Dataset **SAbDab**; thousands of known, successful antibodies had their CDRs artificially erased; MAMMAL was given the target and asked to predict the CDR amino-acid sequences (a fill-in-the-blank test). Stressed: text-only, with no access to any 3D structural maps. Result: MAMMAL is said to have generated the correct sequences for all the fingers, outperforming specialised state-of-the-art methods.
**Key points.**
- 27:36 The CDRs (the fingers) were artificially erased so the AI could not see them.
- 28:17 MAMMAL is said to have generated correct sequences for all the fingers, beating other state-of-the-art methods.

### Ch. 20 — CDR-H3: +19 % · 28:27–29:27
**Summary.** **CDR-H3** is described as the antibody's longest, most complex and most variable region, almost entirely responsible for what the antibody binds, and the hardest part for any AI to predict. MAMMAL is said to have crushed the competition with a **19 % improvement** over previous leading models. Gloss: the model is not merely memorising common patterns but "truly understands the rules of biology".
**Key points.**
- 29:04 Reports a massive 19 % improvement over the previous leading models.

### Ch. 21 — Zoom-out: foundation model, predictions · 29:27–31:11 · (presenter: "29:29 Implications for medicine")
**Summary.** The presenter suggests we may now have biology's first genuine foundation model — one unified model that understands everything. Conditional futures: drug discovery no longer a 10-year, billion-dollar bet with a 90 % failure rate; repurposing at scale; a massive acceleration in new drugs within months, if true; personalised medicine from a DNA and blood sample (diagnose the cause, choose drugs, even custom-design an antibody for the individual patient) — which he labels a bold prediction; new cancer cures very soon; one of the year's most impactful papers so far, provided the claims hold.
**Key points.**
- 29:29 Suggests MAMMAL may potentially be biology's first genuine foundation model.
- 30:05 Predicts a massive acceleration in new drugs within the coming months, if this proves true.
- 30:55 Says new cancer cures could potentially arrive very soon.
- 31:00 Calls it, without qualification, among the year's most impactful papers so far.

### Ch. 22 — Outro · 31:11–31:53
**Summary.** Sign-off, comments call-to-action, like/share/subscribe, newsletter plug (link in description). No content claims.

---

## 4. Master claims table

Legend — **Category**: BIO = biology/pharmacology background · ARCH = model architecture/design · DATA = training data · BENCH = benchmark set-up or result · INTERP = presenter's interpretation/explanation · HYPE = hype, prediction or evaluative framing · META = framing about the paper/video. **Flag** (documenter's pointer for the fact-checker, not a verdict): KEY = central numeric/result claim; CHECK = wording likely to differ from the paper or from standard biology; OK = standard background. Timestamps = Whisper segment start.

| # | mm:ss | Claim (paraphrased; see timestamp) | Category | Flag |
|---|---|---|---|---|
| 1 | 00:00 | Calls this possibly among the biggest medical and drug-discovery breakthroughs in decades. | HYPE | opinion |
| 2 | 00:06 | A new paper has just come out about a new AI model called MAMMAL. | META | CHECK — journal version May 2026; preprint Oct 2024 |
| 3 | 00:11 | Says it could transform bioscience and medicine, potentially yield many new cures (e.g. for cancer), make drug discovery much faster, cheaper and more accurate, and lead to personalised medicine. | HYPE | opinion |
| 4 | 00:45 | Asks the viewer to picture a 10-year, billion-dollar effort with a 90 % chance of failing. | BIO | OK (order of magnitude) |
| 5 | 00:54 | Gives this as the failure rate of new drugs: of promising candidates taken through clinical trials, roughly 90 % fail to win approval. | BIO | CHECK — ~90 % is the usual clinical-stage attrition figure |
| 6 | 01:07 | Notes that the human genome is sequenced and that AI can predict protein structures and even understand DNA. | BIO | OK |
| 7 | 01:41 | All living things have DNA, the code that lets them function and survive. | BIO | OK (simplified; RNA viruses aside) |
| 8 | 01:47 | Genes are sections of DNA, likened to instruction manuals, that encode proteins. | BIO | OK (ignores non-coding genes) |
| 9 | 01:55 | Proteins are the tiny machines doing most of the body's work: signalling, building structures, speeding up reactions, controlling immune responses, keeping cells alive. | BIO | OK |
| 10 | 02:08 | Genes are not always active; they can be turned up, turned down or mutated, and this is called gene expression. | BIO | CHECK — mutation is not gene expression |
| 11 | 02:17 | Gene expression is described as a measure of which genes are on and how strongly, which controls how much protein is made. | BIO | OK |
| 12 | 02:42 | Mutations in DNA can cause proteins to be made wrongly or not at all, or expression can be too high or too low. | BIO | OK |
| 13 | 03:01 | Cancer: a mutation damages a gene that controls cell division, changing expression or protein function, so that the proteins push the cell to grow, ignore stop signals and form a tumour. | BIO | OK (simplified) |
| 14 | 03:26 | Scientists usually start by locating the faulty step in the disease pathway (the culprit), then aim to design a drug that interacts with that target. | BIO | OK (target-based discovery) |
| 15 | 03:46 | Lock-and-key analogy: if the drug (key) fits the target (lock), it can block the protein or alter its activity. | BIO | analogy |
| 16 | 03:56 | Two main drug types are said to be relevant to this paper (small molecules and antibodies). | META | CHECK — paper also covers other modalities (e.g. TCRs) |
| 17 | 04:00 | Small molecules such as Tylenol are tiny, stable, often easy to make as pills, and can sometimes slip into cells and bind proteins there. | BIO | OK |
| 18 | 04:14 | Antibodies are a much larger drug type, likened to very precise biological clamps; because of their size they usually act outside cells or on their surface. | BIO | OK |
| 19 | 04:39 | The body is not one simple machine but has a billion moving parts. | BIO | rhetorical figure |
| 20 | 04:45 | A drug that binds its target may still affect other parts of the body and cause side effects — the key may also open other locks. | BIO | OK (off-target effects) |
| 21 | 05:16 | A drug must also be shown to work at safe doses without accidentally killing the patient. | BIO | OK |
| 22 | 05:35 | Gives Google's AlphaFold as the example of an AI model that predicts protein structures. | BIO | OK (Google DeepMind) |
| 23 | 05:41 | Another AI may excel at reading and generating DNA; Evo 2 is named. | BIO | OK |
| 24 | 05:51 | Other tools screen chemical compounds or analyse clinical-trial data. | BIO | OK |
| 25 | 06:09 | These tools are often siloed: trained on different datasets, built by different teams, optimised for different tasks. | INTERP | motivation |
| 26 | 06:46 | The team is said to have built one model that understands chemistry, genetics and protein structure all at the same time. | ARCH | CHECK — the protein-structure claim: the video itself later calls MAMMAL a 1-D sequence model (22:34) |
| 27 | 06:58 | Pre-training used two billion samples. | DATA | KEY |
| 28 | 07:01 | The data are said to be scraped from essentially every major biological database. | DATA | hyperbole |
| 29 | 07:04 | Observed Antibody Space, said to hold billions of antibody sequences. | DATA | CHECK magnitude |
| 30 | 07:09 | UniProt, said to hold nearly every known protein. | DATA | OK |
| 31 | 07:13 | ZINC and PubChem, said to hold millions of small-molecule structures. [verifier-corrected: both ASR sources say "contains"] | DATA | OK |
| 32 | 07:18 | CELLxGENE, said to hold a large volume of gene-expression data. | DATA | OK |
| 33 | 07:22 | Hence the training covered everything relating to chemistry, genetics and proteins. | DATA | hyperbole |
| 34 | 07:41 | All data were forced into one unified format — character sequences — with each domain keeping its own grammar. | ARCH | KEY (design principle) |
| 35 | 07:48 | Molecules are written as SMILES strings, which flatten a 3D chemical structure into a single line of text. | ARCH/BIO | OK |
| 36 | 08:02 | Each letter stands for an atom and each symbol (e.g. "=") for a chemical bond. | BIO | OK (simplified SMILES) |
| 37 | 08:07 | The AI learns chemistry purely by tracking patterns across millions of such strings. | INTERP | OK as gloss |
| 38 | 08:16 | For genes, every gene in a cell is ranked by activity — most active first, silent ones last — so each cell becomes a priority list for the model. | ARCH | KEY — expression encoded as rank-ordered gene list |
| 39 | 08:34 | Proteins and antibodies (also proteins) are read simply as amino-acid chains. | ARCH | OK |
| 40 | 09:05 | MAMMAL uses what is called a modular tokenizer. | ARCH | KEY (paper term) |
| 41 | 09:08 | A tokenizer is likened to a dictionary that translates raw data into a consistent language the AI can understand. | ARCH | gloss |
| 42 | 09:19 [verifier-corrected; was 09:16] | An umbrella tokenizer sits over specialised sub-dictionaries — one each for chemistry, genetics and proteins. [verifier-corrected: wording; paraphrased in this edition] | ARCH | CHECK exact sub-tokenizer list |
| 43 | 09:30 | Each input type is converted into tokens and embeddings by its own dictionary (small molecules, proteins, and likewise genes). | ARCH | OK |
| 44 | 09:46 | Once everything is converted into embeddings, all modalities are blended into one shared multi-dimensional space. | ARCH | KEY |
| 45 | 10:01 | Merging the domains lets the model learn how all these different things relate. | INTERP | gloss |
| 46 | 10:18 | Evaluated on 11 distinct, highly rigorous benchmarks said to span the whole drug-discovery pipeline. | BENCH | KEY — 11 |
| 47 | 10:35 | State-of-the-art performance on the 11 benchmarks, outright beating the world's previous best models on every one of the tasks. | BENCH | KEY/CHECK — paper abstract says SOTA on 9 of 11, competitive on 2 |
| 48 | 10:59 | Evaluated on two safety benchmarks described as critical; the first is BBBP (blood-brain barrier penetration). | BENCH | OK |
| 49 | 11:09 | ClinTox, described as a dataset for predicting clinical toxicity and FDA approval. | BENCH/BIO | OK (ClinTox has two labels: FDA approval, clinical-trial toxicity) |
| 50 | 11:19 | The blood-brain barrier is a major hurdle in pharmacology; the brain has a very tight security system. | BIO | OK |
| 51 | 11:29 | Drugs for Alzheimer's or Parkinson's must cross the barrier; conversely, a heavy chemotherapy drug aimed at the liver must on no account cross it. | BIO | OK |
| 52 | 11:52 | MoLFormer is cast as the reigning champion at predicting BBBP. | BENCH | CHECK — is this champion simply the paper's chosen baseline? |
| 53 | 11:59 [verifier-corrected; was 11:57] | MoLFormer's training data were over a billion small-molecule sequences and nothing else. | BIO | CHECK (MoLFormer-XL ≈ 1.1 B SMILES) |
| 54 | 12:13 | On BBBP the hyper-specialised MoLFormer scored very well, but MAMMAL beat it. | BENCH | KEY — no numbers given |
| 55 | 12:22 | Likewise on ClinTox, MAMMAL beat MoLFormer by **a few** [auto] / **a huge** [Whisper] percentage points. | BENCH | KEY — ASR UNRESOLVED; margin not otherwise stated |
| 56 | 12:34 | In almost every field a specialist beats a generalist in the specialist's own domain. | INTERP | rhetorical |
| 57 | 13:11 | Biology is interconnected, and this is said to prove that being multimodal is an advantage rather than a distraction. | INTERP | CHECK — proof claimed from two benchmarks |
| 58 | 13:25 | Small molecules exist in order to interact with proteins and change gene expression. | BIO | loose/teleological |
| 59 | 13:30 | Because training forced MAMMAL to learn the relationships between modalities, it is said to have gained a much deeper understanding of the molecules' overall biology. | INTERP | presenter's causal story |
| 60 | 15:18 | Next test: labelling cell types with the Zheng68K dataset. | BENCH | OK |
| 61 | 15:24 | Zheng68K is described as thousands of gene-activity profiles from many immune cell types in blood. | BIO | CHECK — ~68 k PBMCs |
| 62 | 15:30 | The AI reads a cell's gene activity and must label it correctly, e.g. CD4+ T cell or NK cell. | BENCH | OK |
| 63 | 15:44 | Called vital for working out how a patient's immune system reacts to a disease or a treatment. | INTERP | motivation |
| 64 | 15:55 | MAMMAL improved 7.5 % over the state-of-the-art model. | BENCH | KEY — metric & baseline unnamed |
| 65 | 16:04 | The cancer drug-response section is called the paper's highlight and proof of a genuine biomedical breakthrough. | HYPE | opinion |
| 66 | 16:14 | The aim was to show MAMMAL was not just regurgitating memorised information, by predicting how entirely new, unseen drugs would fare against human cancer cells. | BENCH | set-up |
| 67 | 16:27 | Four drugs said to be definitely absent from the training data were chosen: carfilzomib, nintedanib, infigratinib and vemurafenib. [verifier-corrected: wording; paraphrased in this edition] | BENCH | KEY |
| 68 | 16:40 | MAMMAL was given the four drugs' chemical strings plus genetic profiles of over 800 kinds of cancer tumour cells (lung, breast, colon cancer). | BENCH | KEY — tumour cells = cell lines? |
| 69 | 16:59 | The question posed: how effective are the four new drugs across the 800 tumour cell types? Rank them from most to least deadly. | BENCH | set-up (ranking task) |
| 70 | 17:27 | The researchers computed Tanimoto similarity, a measure of how structurally alike two molecules are. | BIO | OK |
| 71 | 17:38 | Three of the four drugs had maximum Tanimoto similarity below 0.7 to anything MAMMAL had seen. | BENCH | KEY — implies the 4th drug was ≥ 0.7 |
| 72 | 17:49 | In rigorous chemistry, a score below 0.7 is said to mean the drugs are essentially structurally different. | BIO | CHECK — conventional-ish threshold, not a rule |
| 73 | 18:05 | The model has to rank each drug's potency against 805 different cancer-tumour variations. | BENCH | KEY — 805 |
| 74 | 18:17 | Predicted carfilzomib as most potent across most tumours, nintedanib second, and the remaining two third and fourth (indicated only on screen at this point). | BENCH | KEY — 3rd/4th not named here (on screen only), but #79 (19:40) implies vemurafenib 4th and so infigratinib 3rd [verifier-corrected] |
| 75 | 18:32 | Carfilzomib is FDA-approved, but its current approval and use are limited to blood cancers. | BIO | OK (multiple myeloma) |
| 76 | 18:40 | Doctors are said to have long believed carfilzomib useless against solid tumours, which the presenter calls the currently accepted view of expert oncologists. | BIO/INTERP | CHECK — strong; proteasome inhibitors have been trialled in solid tumours |
| 77 | 18:52 | The AI ranked it the single strongest drug against solid cancer types. | BENCH | KEY |
| 78 | 19:19 | The researchers are said to have tested this in a physical lab experiment on solid cancer cells. | BENCH | KEY/CHECK — wet-lab by the authors, or pre-existing cell-line screening data? |
| 79 | 19:30 | The results are said to match MAMMAL's predictions perfectly, with the exact potency order: carfilzomib most potent, down to vemurafenib least potent. | BENCH | KEY |
| 80 | 19:44 | The relative order is said to hold in approximately 95 % of the 805 cancer cell types. | BENCH | KEY — 95 % |
| 81 | 19:57 | A text-only AI looked at a blood-cancer drug new to it and correctly inferred it would work against these solid tumours, although human experts had, the presenter says, assumed for decades that such drugs would not. | INTERP | CHECK the decades timeframe |
| 82 | 20:21 | An AI said to generalise to entirely new compounds and accurately predict their uses in treating disease. | INTERP | generalisation claim |
| 83 | 20:36 | Drug repurposing is testing an existing drug (approved, or a failed candidate) against a different disease. | BIO | OK |
| 84 | 20:53 | Developing a brand-new drug de novo is said to take about 10–15 years and billions of dollars. | BIO | OK (order of magnitude) |
| 85 | 21:18 | Antibodies are larger proteins that clamp very precisely onto the problem protein. | BIO | OK |
| 86 | 21:28 | A protein is a long amino-acid chain that folds into a complex 3D shape, which determines what it binds and what effect it has. | BIO | OK |
| 87 | 21:38 | A protein could in theory fold in an enormous number of ways, and a random search could outlast the age of the universe; in practice physics guides it to its most stable shape almost instantly. | BIO | OK (Levinthal's paradox) |
| 88 | 22:07 | Predicting protein folding is exactly what Google's celebrated AlphaFold does. | BIO | OK |
| 89 | 22:21 | AlphaFold is described as highly accurate, the industry standard and one of the great modern scientific achievements, with its team winning a Nobel Prize in Chemistry. | BIO | OK (2024 Nobel, Hassabis & Jumper) |
| 90 | 22:34 | MAMMAL is merely a sequence model that reads text in one dimension. | ARCH | KEY (contrast with #26) |
| 91 | 22:48 | MAMMAL and AlphaFold were each given an antibody and a disease target and asked a yes/no question: will they bind? | BENCH | KEY — binary binding task |
| 92 | 22:57 | Both models were tested on seven well-documented targets. | BENCH | KEY — 7 |
| 93 | 23:03 | MAMMAL beat AlphaFold 3 on five of the seven targets. | BENCH | KEY — 5/7; video omits that paper compares fine-tuned MAMMAL scores to AF3 confidence scores |
| 94 | 23:10 | AlphaFold 3 is said to be able to directly see proteins' 3D shapes. | INTERP | loose — AF3 predicts structure from sequence |
| 95 | 23:29 | Textbooks often depict proteins as rigid, static structures, because historically that was the only way to draw or image them. | BIO | OK |
| 96 | 23:45 | For human proteins, around 30–40 % of the sequence is said to consist of intrinsically disordered regions (IDRs). | BIO | CHECK — commonly cited range (~30–40 % of residues/proteins) |
| 97 | 23:58 | These regions lack a stable 3D shape and are floppy and highly flexible, likened to wet spaghetti. | BIO | OK |
| 98 | 24:13 | Protein structures are dynamic rather than static; they can change shape or move. | BIO | OK |
| 99 | 24:24 | Key targets such as EGFR and HER2, described as notoriously aggressive drivers of breast and stomach cancer, are said to have many such floppy disordered regions. | BIO | CHECK — degree of disorder in EGFR/HER2; is this from the paper? |
| 100 | 24:38 | AlphaFold 3 is said to struggle with these floppy regions because it was trained to predict static, solid 3D structures and learned only from frozen snapshots. | INTERP | presenter's explanation |
| 101 | 24:55 | Asked whether a specific antibody binds such flexible, chaotic targets, AlphaFold 3 is said to answer poorly. | INTERP/BENCH | CHECK — is the IDR explanation in the paper? |
| 102 | 25:10 [verifier-corrected; was 25:05] | MAMMAL is said to win on floppy proteins because it does not try to depict them as a fixed snapshot. | INTERP | CHECK — causal claim |
| 103 | 25:17 | As a large language model working on sequences, MAMMAL does not force a protein into any shape; it seems to grasp the underlying grammar or rules of proteins and relies on the mathematics of the sequence. | INTERP | hedged (presenter says it seems to) |
| 104 | 25:38 [verifier-corrected; was 25:36] | Said to be much more robust at telling whether an antibody binds a disease target. | INTERP | generalises 5/7 |
| 105 | 25:47 | Any antibody candidate can now be run through this AI to ask whether it binds particular disease targets. | HYPE | extrapolation |
| 106 | 26:09 | MAMMAL was designed to generate entirely new drugs too — an inventor as well as an analyst. | ARCH | OK (generation tasks) |
| 107 | 26:18 | The team is said to have tested whether it can design entirely new antibodies. | BENCH | CHECK — task described is CDR *infilling*, not de novo design |
| 108 | 26:28 | An antibody is a large Y-shaped protein the immune system uses to identify and neutralise things such as viruses or cancer cells. | BIO | OK |
| 109 | 26:43 | The Y's main body is stable and consistent, but its tips are highly variable; these tips are the CDRs (complementarity-determining regions). | BIO | OK |
| 110 | 27:09 | The amino-acid sequence of these fingers is said to determine exactly which disease target the antibody can grab. | BIO | OK (simplified) |
| 111 | 27:27 | The test used SAbDab, described as a huge dataset of many different antibodies. | BENCH | OK |
| 112 | 27:33 | Thousands of known, successful antibodies had their CDRs artificially erased, and MAMMAL was given the disease target to aim at — a fill-in-the-blank test. | BENCH | KEY set-up — how many antibodies? all CDRs or one at a time? |
| 113 | 27:57 | MAMMAL reads only one-dimensional text and was given no 3D structural maps of either the antibody or the disease target. | ARCH/BENCH | CHECK — paper's input description |
| 114 | 28:17 | MAMMAL is said to have generated the correct sequences for all the fingers, outperforming specialised state-of-the-art methods. | BENCH | KEY/CHECK — correctness and completeness claims; which baselines? |
| 115 | 28:40 [verifier-corrected; was 28:34, which is the first mention of CDR-H3] | CDR-H3 is described as notoriously the antibody's longest, most complex and most variable region. | BIO | OK |
| 116 | 28:49 | Its length and flexibility are said to make it almost entirely responsible for what the antibody binds, and therefore the hardest part for any AI to predict. | BIO | CHECK the near-total attribution |
| 117 | 29:04 | A massive 19 % improvement over the previous leading models [on CDR-H3]. | BENCH | KEY — 19 %; metric unnamed |
| 118 | 29:21 | The model is said not merely to memorise common patterns but to truly understand biology's rules. | HYPE | opinion |
| 119 | 29:29 | We may potentially now have biology's first genuine foundation model — one unified model that understands everything. | HYPE | opinion ("potentially") |
| 120 | 29:43 | If MAMMAL works the way the paper claims, drug discovery might no longer be a 10-year, billion-dollar bet with a 90 % failure rate. | HYPE | conditional |
| 121 | 30:05 | A massive acceleration in new drugs is predicted within the coming months, if this proves true. | HYPE | prediction (months) |
| 122 | 30:10 | Because the model also understands DNA and gene expression, personalised medicine could become mainstream. | HYPE | CHECK — video never shows MAMMAL ingesting DNA; modalities named are molecules, proteins, gene expression |
| 123 | 30:16 | A patient's DNA and blood sample could simply be run through the AI to find what is causing their disease and which proteins are faulty, choose the best drugs, or even custom-design an antibody for that patient. | HYPE | prediction, self-labelled as bold |
| 124 | 30:41 | The paper is said to have already shown that it is very good at predicting drug candidates' binding to cancer cells, and to have already made a genuine new breakthrough. | INTERP | CHECK — drug response ≠ binding |
| 125 | 30:55 | New cures for cancer, and for other diseases, could potentially arrive very soon. | HYPE | prediction |
| 126 | 31:00 | Called definitely one of the year's most impactful papers so far, provided the claims hold. | HYPE | opinion, hedged |
| 127 | 01:15 | Despite all our technology, we are still wrong most of the time when making new medicines. [verifier-added] | BIO/HYPE | restates the 90 % failure framing |
| 128 | 04:30 | The hope is that shutting down the culprit makes the disease (e.g. cancer) stop growing and die. [verifier-added] | BIO | OK (simplified) |
| 129 | 05:58 | Disease is not confined to separate silos; it runs through the whole system, from DNA to gene activity, proteins, cells and whole bodies. [verifier-added] | INTERP | motivation for multimodality |
| 130 | 08:57 | Training a neural network on all this raw data would leave it badly confused. [verifier-added] | ARCH/INTERP | presenter's justification for the tokenizer |
| 131 | 10:28 | Everything was thrown at it, and the results were phenomenal across the board. [verifier-added] | HYPE | evaluative framing of #46–47 |
| 132 | 15:51 | Calls cell typing a fundamental classification task, and the 7.5 % improvement on it a huge leap. [verifier-added] | HYPE | evaluative framing of #64 |
| 133 | 18:14 | MAMMAL is said to have produced a very confident, specific ranking. [verifier-added] | INTERP | CHECK: the video gives no confidence measure |
| 134 | 18:57 | Reminds viewers that this knowledge did not exist before and experts never expected it, so a real-world test would be expected to fail badly. [verifier-added] | INTERP | CHECK: same framing as #76/#81 |
| 135 | 19:07 | MAMMAL is said to have examined the drug's structure and confidently declared it strong against solid tumour cells, contrary to doctors' views. [verifier-added] | INTERP | anthropomorphic gloss |
| 136 | 21:56 | Making a protein drug such as an antibody requires knowing not only the sequence but how it folds, moves and binds. [verifier-added] | BIO | OK |
| 137 | 22:13 | Since MAMMAL was also trained on proteins, the presenter sets up a head-to-head with AlphaFold 3. [verifier-added] | BENCH/META | set-up for #91–93 |
| 138 | 25:05 | Given the same question, MAMMAL is said to have predicted much better. [verifier-added] | BENCH/INTERP | CHECK: implies a result specific to the IDR-rich (EGFR/HER2) targets; is one reported? |
| 139 | 25:54 | This could lead to many major discoveries and new drugs. [verifier-added] | HYPE | prediction |
| 140 | 25:58 | Notes that MAMMAL has so far only been asked about existing candidates and their response to diseases, then asks what if we want an entirely new drug. [verifier-added; Whisper dropped most of the first sentence, so the wording is from the auto-captions] | META | transition to generation |
| 141 | 27:03 | The fingers are called the antibody's most important part because they are highly specific. [verifier-added] | BIO | OK (simplified) |
| 142 | 27:17 | The whole field of modern antibody design is said to revolve around engineering new, better fingers to grab a given target. [verifier-added] | BIO/INTERP | CHECK: whole-field claim (framework, Fc and developability engineering also matter) |
| 143 | 28:07 | It had to work out both molecules' physical shapes purely from its grasp of the grammar or rules of proteins. [verifier-added] | INTERP | CHECK: presenter's inference about mechanism |
| 144 | 29:53 | Drugs could instead be designed much faster, more cheaply and more accurately, and existing candidates screened against other diseases. [verifier-added] | HYPE | conditional on #120 |

---

## 5. All numbers mentioned

| Number | Context (paraphrased; see timestamp) | mm:ss |
|---|---|---|
| 10 years | time to build a drug (the opening hypothetical of 10 years and a billion dollars) | 00:45; again 29:49 (the 10-year, billion-dollar gamble) |
| a billion dollars | cost of building a drug | 00:45; 29:50 |
| 90 % | chance that a new drug fails; the failure rate; roughly 90 % of candidates failing to gain approval; failing 90 % of the time | 00:49, 00:53, 01:02, 29:52 |
| 9 out of 10 | bridge analogy (collapse rate) | 01:23 |
| decades | the opening superlative (biggest breakthrough in decades) [verifier-added] | 00:00 (word at 00:05) |
| two (main types of drugs) | small molecules and antibodies, said to be relevant to the paper [verifier-added] | 03:56 |
| a billion moving parts | the body / biology | 04:42, 13:15 |
| two (2) billion samples | MAMMAL pre-training set | 06:58 |
| billions | antibody sequences in Observed Antibody Space | 07:07 |
| millions | small-molecule structures in ZINC + PubChem; millions of text strings (SMILES) | 07:15, 08:11 |
| 3D / one dimension | 3D chemical structure flattened to text; MAMMAL reads text in one dimension; one-dimensional text reader/sequences | 07:52, 22:39, 23:19, 27:59 |
| three (paragraphs/dictionaries) | book analogy (English / sheet music / JavaScript); three sub-dictionaries (chemistry, genetics, proteins) | 08:47–08:51, 09:24–09:27 |
| 11 | distinct benchmarks | 10:21, 10:35 |
| two | safety benchmarks described as critical (BBBP, ClinTox) | 11:01 |
| over a billion | small-molecule sequences MoLFormer was trained on | 12:00 |
| a few / a huge percentage points | MAMMAL's margin over MoLFormer on ClinTox (ASR disagreement) | 12:29 |
| 50 %, three months, "AGENT50" | sponsor discount (Runway) | 15:13–15:16 |
| 68K | in dataset name Zheng68K | 15:22 |
| thousands | gene-activity data points in Zheng68K; thousands of known, successful antibodies (SAbDab test) | 15:24, 27:34 |
| 7.5 % | improvement over SOTA on cell-type labelling | 15:56 |
| four (4) | held-out drugs | 16:28, 17:00, 18:29 |
| over 800 / 800 | cancer tumour cell types | 16:48, 17:03 |
| three out of four | drugs with max Tanimoto < 0.7 | 17:39 |
| 0.7 | Tanimoto threshold (max value below 0.7; a score below 0.7) | 17:44, 17:51 |
| 805 | cancer-tumour variations / cancer cell types | 18:08, 19:50 |
| second, third, fourth | predicted ranks of nintedanib and two unnamed drugs | 18:23–18:27 |
| number one | carfilzomib's predicted rank against solid cancers | 18:53 |
| approximately 95 % | share of the 805 cell types where relative order was preserved | 19:48 |
| hundreds | solid tumours whose genetics were examined | 20:05 |
| decades | how long experts supposedly assumed such drugs would not work (see also 00:00 above) | 20:15 |
| 10 to 15 years; billions of dollars | de novo drug discovery time/cost | 20:57–20:58 |
| longer than the age of the universe | random fold search (Levinthal framing) | 21:46 |
| 3 | AlphaFold **3** | 22:19 and throughout |
| seven; five of seven | antibody–antigen binding targets; MAMMAL wins | 22:59, 23:06 |
| 30 to 40 percent | share of human protein sequence that is intrinsically disordered | 23:48 |
| 3 | CDR-H**3** | 28:35, 28:41 |
| 19 % | improvement on CDR-H3 over previous leading models | 29:06, 29:10 |
| months | horizon for the predicted massive acceleration in new drugs | 30:08 |
| first | the first-true-foundation-model claim [verifier-added] | 29:29 |
| this year (so far) | one of the year's most impactful papers so far [verifier-added] | 31:00 |
| one (unified model / one question / one slice) | rhetorical units | 05:31, 06:18, 16:58, 29:40 |

---

## 6. Named entities

| Entity | Type | ASR spelling(s) — Whisper / auto | Correct form | First mm:ss |
|---|---|---|---|---|
| MAMMAL | model (subject of video) | "MAML" (W 00:06, 06:43, 06:58; A 15:54–16:58) / "Mammal" / "mammal" / "Mammoth" (A 10:15–11:00) / "mammals" (possessive) | **MAMMAL** (Molecular Aligned Multi-Modal Architecture and Language) | 00:06 |
| AlphaFold / AlphaFold 3 | model (comparator) | "Alpha Fold" (W) / "AlphaFold" (A); "alpha fold three", "Alphafold" (description) | **AlphaFold**, **AlphaFold 3** (Google DeepMind) | 05:38; 22:19 |
| Evo 2 | model (DNA) | "EVO2" (W) / "Evo 2" (A) | **Evo 2** | 05:44 |
| MoLFormer | model (small-molecule baseline) | "mole former" (W) / "MoleFormer" (A) | **MoLFormer** | 11:56 |
| Observed Antibody Space | database | "the observed antibody space" (W) / "They observed antibody space" (A) | **Observed Antibody Space (OAS)** | 07:04 |
| UniProt | database | "uniprot" (W) / "UniProt" (A) | **UniProt** | 07:09 |
| ZINC | database | "zinc" / "Zinc" | **ZINC** | 07:13 |
| PubChem | database | "pub chem" (W) / "PubChem" (A) | **PubChem** | 07:13 |
| CELLxGENE | database | "cell X gene" (W) / "Cell X Gene" (A) | **CELLxGENE** (CZ CELLxGENE) | 07:18 |
| BBBP | benchmark | "BBBP" | **BBBP** (Blood–Brain Barrier Penetration, MoleculeNet) | 11:04 |
| ClinTox | benchmark | "ClinTalks", "ClinTalk" (W) / "ClinTox" (A) | **ClinTox** (MoleculeNet) | 11:10; 12:23 |
| Zheng68K | dataset | "Zeng 68K" (W) / "Zang 68K" (A) | **Zheng68K** (68 k PBMC scRNA-seq) | 15:21 |
| SAbDab | database | "Sabdab" (W) / "SabDab" (A) | **SAbDab** (Structural Antibody Database) | 27:30 |
| Tylenol | drug (example) | "Tylenol" | **Tylenol** (acetaminophen / paracetamol) | 04:00; 07:58 |
| aspirin | drug (example) | "aspirin" | **aspirin** | 07:32 |
| carfilzomib | drug (held-out) | "carfilzomib" (both) | **carfilzomib** (Kyprolis; proteasome inhibitor) | 16:33 |
| nintedanib | drug (held-out) | "nintedanib" (both) | **nintedanib** | 16:34 |
| infigratinib | drug (held-out) | "infigretinib" (W) / "infigratinib" (A) | **infigratinib** | 16:35 |
| vemurafenib | drug (held-out) | "vimura fenib" (W 16:37), "venmerafenib" (W 19:41) / "vemurafenib" (A) | **vemurafenib** | 16:37 |
| EGFR | protein target | "EGFR" | **EGFR** (epidermal growth factor receptor) | 24:27 |
| HER2 | protein target | — (dropped by W) / "HER2" (A) | **HER2** (ERBB2) | 24:28 (auto) |
| CD4+ T cell | cell type | "CD4 plus t-cell" (W) / "CD4+ T cell" (A) | **CD4⁺ T cell** | 15:36 |
| NK cell | cell type | "NK cell" | **NK (natural killer) cell** | 15:39 |
| SMILES | notation | "smile string", "the smile for Tylenol" (W) / "SMILES" (A) | **SMILES** | 07:48 |
| Tanimoto similarity | metric | "tanimoto" (W) / "Tanimoto" (A) | **Tanimoto similarity** | 17:28 |
| IDR | concept | "IDRs" | **intrinsically disordered region** | 23:55 |
| CDR / CDR-H3 | antibody region | "CDRs"; "CDRH 3" (W) / "CDRH3" (A) | **CDR**; **CDR-H3** (heavy-chain CDR3) | 26:56; 28:34 |
| Google | company | "Google's Alpha Fold" | **Google** (DeepMind) | 05:38 |
| FDA | regulator | "FDA" | **US FDA** | 11:14 |
| Nobel Prize in Chemistry | award | "Nobel prize in chemistry" | **Nobel Prize in Chemistry** (2024) | 22:31 |
| Runway / Runway Agent | sponsor | "runway", "runway agent" | **Runway**, **Runway Agent** | 13:53 |
| Alzheimer's, Parkinson's | diseases | — | — | 11:31 |
| lung / breast / colon / stomach cancer; blood cancers; solid tumours | diseases | — | — | 16:51; 24:32; 18:39 |
| JavaScript | analogy | — | — | 08:51 |
| **Not named anywhere in the video** | — | — | IBM (or any author/affiliation), the paper's title, journal (only in description), model size/parameters, code or weights availability, licence, scGPT, dyMEAN, STRING, the other benchmarks (TCR binding, PPI ΔΔG, DTI, drug-response variants) | — |

---

## 7. ASR error / correction table

Whisper (W) is the primary transcript; auto-captions (A) are YouTube's. "Correct form" = documenter's judgement from context plus the paper's spelling where relevant. Items marked **UNRESOLVED** could not be settled from the files.

| mm:ss | Whisper | Auto-captions | Correct / adopted form | Type |
|---|---|---|---|---|
| 00:06, 06:43, 06:58 | "MAML" | "Mammal" | **MAMMAL** | name |
| 10:15, 10:37, 10:55, 11:00 | "mammal" | "Mammoth" | **MAMMAL** | name (auto error) |
| 15:55, 16:15, 16:43, 16:58 | "mammal" | "MAML" | **MAMMAL** | name (auto error) |
| 19:32, 19:44 | "mammals predictions", "mammals successfully" | "mammals' predictions", "Mammals successfully" | **MAMMAL's predictions**; **MAMMAL successfully** | name/possessive |
| 01:23 | "9 out of 10" | "nine out of 10" | 9 out of 10 | trivial |
| 03:34 | "**selling**" | "telling" | **telling** | word |
| 04:14 | "an antibody **body**" | "an antibody" | **antibody** (Whisper duplication) | word |
| 05:38 (and all later) | "Alpha Fold" | "AlphaFold" | **AlphaFold** | name |
| 05:44 | "EVO2" | "Evo 2" | **Evo 2** | name |
| 07:01 | "two billion" | "2 billion" | 2 billion | trivial |
| 07:04 | "**the** observed antibody space" | "**They** observed antibody space" | **the Observed Antibody Space** (auto error) | name |
| 07:09 | "uniprot" | "UniProt" | **UniProt** | name |
| 07:13 | "zinc and pub chem" | "Zinc and PubChem" | **ZINC and PubChem** | name |
| 07:18 | "cell X gene" | "Cell X Gene" | **CELLxGENE** | name |
| 07:48, 07:58 | "smile string", "the smile for Tylenol" | "SMILES string", "the SMILES for Tylenol" | **SMILES** | term |
| 11:10 | "ClinTalks" | "ClinTox" | **ClinTox** | name |
| 11:56, 12:18, 12:27, 13:01 | "mole former" | "MoleFormer" | **MoLFormer** | name |
| 12:23 | "ClinTalk safety benchmark" | "ClinTox safety benchmark" | **ClinTox** | name |
| **12:29** | "by **a huge** percentage points" | "by **a few** percentage points" | **UNRESOLVED** — opposite magnitudes; "a few percentage points" is grammatical and more plausible, but no confidence scores exist in the JSON to adjudicate; verify against the paper's ClinTox table or by re-listening. [verifier-added evidence: Whisper JSON segment 749.24–751.00 s has "huge", where the word "huge" is 749.82–750.02 s, only **0.20 s** long. Whisper's five other "huge" tokens last 0.30–0.42 s, and its one "few" (02:38) lasts 0.16 s. Auto SRT cue 325 (12:26.72–12:29.59) ends with "by", and cue 326 (12:29.60–12:31.79) begins "a few percentage points". The duration and the grammar both point to "few", but this is still not settled without the audio; no audio file is in the dossier.] | content word |
| 14:38 | "redirected" | "redirect it" | redirect it (sponsor) | word |
| 14:55 | "still **give** you fragments" | "still you fragments" | still give you fragments (auto dropped a word; sponsor) | word |
| 15:16 | "agent 50" | "agent50" | **AGENT50** (promo code; sponsor) | name |
| 15:21 | "Zeng 68K" | "Zang 68K" | **Zheng68K** | name |
| 15:36 | "CD4 plus t-cell" | "CD4+ T cell" | **CD4+ T cell** | term |
| 16:35 | "infigretinib" | "infigratinib" | **infigratinib** | drug name |
| 16:37 | "vimura fenib" | "vemurafenib" | **vemurafenib** | drug name |
| 19:41 | "venmerafenib" | "vemurafenib" | **vemurafenib** | drug name |
| 17:33 | "similar **to** molecules" | "two molecules" | **two** | word |
| 17:44, 17:51 | "0.7" | ".7" | 0.7 | trivial |
| 18:05 | "**as** it needs…" | "Now, back to the task…" | auto reading adopted (Whisper dropped words) | dropped words |
| 18:50 | "oncologist" | "oncologists" | oncologists | trivial |
| 19:58 | "text **rings**" | "text strings" | **text strings** | word |
| 20:31 | "…discovery **for** drug…" | "…discovery, **and especially** for…" | auto reading adopted | dropped words |
| 22:44 | "the 3 D structure" | "the 3D structure" | 3D | trivial |
| 22:59 | "across seven different **well** [1.3-s gap, 1380.28→1381.54 s; verifier-corrected, was 2-s]" | "seven different well-documented targets" | auto reading adopted | dropped words |
| **23:58–24:01** | "these these [2.4-s gap, 1438.86→1441.30 s] **have a stable 3d shape**" [verifier-corrected: Whisper repeats "these"] | gap filled by a phrase naming the protein sections, plus "**don't**" | auto reading adopted — Whisper's version inverts the meaning | dropped words (meaning-critical) |
| 24:27–24:31 | "like EGFR [2.2-s gap, 1468.32→1470.52 s; verifier-corrected, was 3-s] and aggressive…" | "like EGFR and **HER2, which are notoriously**…" | auto reading adopted — Whisper dropped the entity HER2 | dropped words (entity) |
| 25:29–25:31 | "rules of proteins including [1.0-s gap, 1530.34→1531.30 s; verifier-added] it relies" | "…including **floppy parts**. It relies" | auto reading adopted | dropped words |
| 25:58–26:01 | "now [2.6-s gap, 1558.70→1561.30 s; verifier-corrected, was 3-s] existing candidates" | gap filled by a clause saying MAMMAL had so far only been asked about existing candidates | auto reading adopted | dropped words |
| 26:41 | "blood stream" | "bloodstream" | bloodstream | trivial |
| 27:10 | "that **coat** up these fingers" | "code up" | **code up** | word |
| 27:30 | "Sabdab" | "SabDab" | **SAbDab** | name |
| 28:34, 28:40 | "CDRH 3" | "CDRH3" | **CDR-H3** | term |
| 28:52–28:57 | "…responsible [3.4-s gap, 1733.60→1737.04 s; verifier-corrected, was 4-s] and consequently" | gap filled by a clause on what the antibody can bind to | auto reading adopted | dropped words |
| 29:55 | "design way faster" | "design **drugs** way faster" | auto reading adopted | dropped word |
| 30:29 | "**they say I**" | "**this AI**" | **this AI** | words |
| 30:39 | "this is a bold…" | "this This bold…" | Whisper reading adopted | auto stutter |
| 05:45 | "One of them is called EVO2" | "One One is called Evo 2" | Whisper reading adopted (auto stutter) [verifier-added] | words |
| 07:15 | "which contains millions" | "which contains millions" | **contains** (both sources; the earlier draft's quote and clean text had silently changed it to "contain") [verifier-added] | grammar left intact |
| 18:41 | "doctors **believe** that carfilzomib" | "doctors **believed** that carfilzomib" | **believed** (auto reading adopted; it fits "All this time") [verifier-added] | word (tense) |
| 23:23 | "**so** understand why" | "**To** understand why" | **To** (auto reading adopted) [verifier-added] | word |
| 24:06 | "**and** IDR kind of looks" | "**An** IDR kind of looks" | **An** (auto reading adopted) [verifier-added] | word |
| 25:34 | "not just **the** snapshot" | "not just **a** snapshot" | Whisper reading kept; meaning unaffected [verifier-added] | trivial |
| 31:50–31:53 | (identical) | — | — | — |

**Systematic observations.** (1) Whisper mis-hears domain names (ClinTox, MoLFormer, Zheng68K, SAbDab, SMILES) and two drug names; auto-captions get these right but mangle the model's name ("Mammoth", "MAML") and "the OAS" ("They observed"). (2) [verifier-corrected] Whisper silently drops words in **nine places**. A full token-level alignment of the two sources found four gaps of 2 s or more (23:58, 2.4 s; 24:27, 2.2 s; 25:58, 2.6 s; 28:52, 3.4 s) and five shorter ones (18:05, 1.5 s; 20:31, 1.0 s; 22:59, 1.3 s; 25:29, 1.0 s; 29:55, 0.8 s). The draft said "five multi-second dropouts" but listed six, two of them under 2 s. One dropout (23:58) flips a negation, and one (24:27) removes the entity HER2. Every gap-fill in this table matches the auto-captions word for word. For any quotation, consult the auto-captions wherever Whisper has an inter-word gap of about 0.8 s or more. (3) Neither source gives word confidences (JSON fields are only `w`, `s`, `e`).

---

## 8. Rhetorical analysis

### 8.1 Reported results vs presenter's interpretation vs hype

**A. Results the presenter attributes to the paper (reported, checkable):** 2 billion pre-training samples (06:58); five named data sources (07:04–07:18); SMILES / ranked-gene / amino-acid encodings (07:48–08:40); modular tokenizer + shared embedding space (09:05–09:51); 11 benchmarks (10:21); beat MoLFormer on BBBP and ClinTox (12:13–12:29); +7.5 % on Zheng68K cell typing (15:56); four held-out drugs, 3/4 with Tanimoto < 0.7, 805 cell types, carfilzomib ranked first, ~95 % order preservation (16:27–19:50); 5/7 targets vs AlphaFold 3 (23:03); CDR infilling on SAbDab beating specialised methods, +19 % on CDR-H3 (28:17–29:06).

**B. Presenter's interpretations/explanations presented as fact (not clearly attributed to the paper):**
- The claim that MAMMAL outright beat the world's previous best models on **every one** of the tasks (10:40) — an absolute reading of the results table.
- The claim that this **proves** multimodality is an advantage (13:16), and the causal story that cross-modal training gave the model a much deeper understanding of the molecules' overall biology (13:36).
- The entire IDR explanation of why MAMMAL beat AlphaFold 3 (23:23–25:35): AlphaFold is said to have learned only from frozen snapshots (24:49), and MAMMAL to win on floppy proteins **because** it does not try to draw a static picture (25:10). Whether the paper itself offers this mechanism is a fact-check item.
- The claim that doctors believed carfilzomib useless against solid tumours, presented as the current consensus of expert oncologists (18:40–18:49), and that human experts had for decades assumed such drugs would not work (20:15) — strong characterisation of clinical consensus, unsourced.
- The claim that the model is not just memorising common patterns but genuinely understands the rules of biology (29:21).
- The claim that the paper has already shown MAMMAL to be very good at predicting drug candidates' **binding** to cancer cells (30:43) — the drug-response task was about potency/response, not binding.

**C. Hype and forward predictions (clearly the presenter's):** the opening biggest-breakthrough-in-decades framing (00:00); calling the result proof of a genuine biomedical breakthrough (16:09); the first-true-foundation-model claim (29:29, hedged with "potentially"); a massive acceleration in new drugs within months (30:05); personalised medicine from a DNA + blood sample, patient-specific antibodies (30:10–30:38, self-labelled as a bold prediction); new cancer cures very soon (30:55); one of the year's most impactful papers (31:00).

**D. Hedges.** The presenter does hedge, but almost exclusively in the last two minutes: a condition that MAMMAL really works as the paper claims (29:43), an if-true rider (30:09), "potentially" (29:29, 30:55), self-labelling as a bold prediction (30:39), a closing condition that the paper's claims are indeed true (31:09), plus the remark that MAMMAL **seems** to understand protein rules (25:25). The body of the video (10:07–29:27) uses unhedged language. [verifier-added: there are two more soft modals: a could-potentially about new cures in the cold open (00:15), and a could about the binding screen leading to many major discoveries (25:54). Neither changes the overall pattern.]

**E. Intensifier register.** "insane" ×6 (01:05, 01:29, 06:56, 12:11, 19:55, 25:45), "shocking" ×3 (19:30, 23:03, 28:17), "crazy/crazier" ×3 outside the ad (23:09, 26:09, 28:28), two competition-crushing idioms (29:03, 28:32), "phenomenal" (10:32), "massive" ×6 (11:19, 20:20, 21:08, 26:30, 29:05, 30:06). The structure of each result segment is: set-up → the results are announced as shocking → number → gloss about "understanding".

### 8.2 What the video does **not** say (gaps a reader should know about)
- **Who built MAMMAL.** Never named — not IBM, not any author, lab or country. Only generic references to the researchers or the team (the latter also used for AlphaFold's Nobel). The word "IBM" does not occur in either transcript.
- **The paper's title, venue or date.** Only a remark that a new paper has just come out (00:06). The description links the npj Drug Discovery article; the video itself does not say the work was first posted as a preprint in 2024.
- **Model size, architecture family, training compute.** No parameter count, no "encoder-decoder/transformer", no mention of fine-tuning vs zero-shot for any benchmark.
- **Code, weights, licence, availability.** Not mentioned at all.
- **Evaluation metrics.** No metric is ever named (AUROC, accuracy, Spearman, recovery rate…). The 7.5 %, the 19 % and the few-percentage-point ClinTox margin are given without units or baselines' names (except MoLFormer and AlphaFold 3).
- **The other benchmarks.** Only 5 of the 11 benchmarks are discussed (BBBP, ClinTox, Zheng68K cell typing, cancer drug response, antibody–antigen binding) plus the CDR infilling task. Nothing on any task where MAMMAL did not win.
- **How the AlphaFold 3 comparison was set up.** The video frames it as a yes/no question put to both models (22:54). It does not say what AlphaFold 3 output was used as a binding predictor, whether MAMMAL was fine-tuned for the task, or what the seven targets were (only EGFR and HER2 are mentioned, in the IDR digression).
- **Whether the physical lab experiment (19:21) was new wet-lab work by the authors** or existing cell-line drug-sensitivity data; where the 805 cancer tumour cells come from (cell lines vs patient tumours is never clarified — the video alternates between tumour cells, tumours, cancer cell types and variations of cancer tumours).
- **Which drug was the one of four with Tanimoto ≥ 0.7**. [verifier-corrected] The 3rd and 4th ranks are not named when the prediction is given (the presenter points at the screen, 18:25). But the presenter then says the experimental order matched MAMMAL's predictions perfectly, running down to vemurafenib as least potent (19:30–19:42), which implies vemurafenib was predicted 4th and infigratinib 3rd.
- **Limitations, failure modes, or caveats from the paper.** None reported. No discussion of data leakage beyond the Tanimoto check, of benchmark saturation, or of the gap between cell-line potency and clinical efficacy.
- **The gene-expression modality's limits.** The video says the model understands DNA (30:12, 30:17) and will work from a DNA and blood sample, but the only genetic input described is ranked gene-expression lists (08:16); no DNA-sequence modality is ever described for MAMMAL (Evo 2 is the DNA model mentioned).
- **Anything about animals or ageing.** Nothing canine, veterinary or longevity-related appears anywhere in the video. Relevance to the dog-ageing dossier must come from the model's general capabilities, not from anything stated here.

> **Note (documenter).** Several of these gaps are filled by the paper's public abstract and model card (IBM Research authorship; a 458 M-parameter model `ibm/biomed.omics.bl.sm.ma-ted-458m`; code and weights on GitHub/Hugging Face; "state-of-the-art on nine tasks and competitive results on two"; "fine-tuned MAMMAL prediction scores significantly outperform AlphaFold3 confidence scores on five of seven antigen targets"). These are **not** claims the video makes and are left to the fact-check agent to verify and cite.

---

## 9. Glossary of technical terms used in the video (plain English)

Terms are defined as generally understood; where the video's usage is looser than the standard meaning, this is noted.

- **DNA** — the long molecule carrying an organism's genetic code (01:41).
- **Gene** — a stretch of DNA that encodes a product, usually a protein; the video's instruction-manual analogy (01:47).
- **Protein** — a chain of amino acids folded into a shape that lets it do a job (enzyme, signal, structure, antibody…) (01:55, 21:28).
- **Amino acid** — one of 20 building blocks; proteins are written as strings of their one-letter codes (08:38).
- **Gene expression** — how much each gene is being "read out" (transcribed) in a cell at a given time; measured e.g. by single-cell RNA sequencing. The video folds mutation into this term (02:10), which is non-standard: mutation changes the sequence, expression changes the activity level.
- **Mutation** — a change in the DNA sequence (02:42).
- **Cell division / stop signals / tumour** — cancer sketched as cells dividing when they should not (03:01).
- **Target (cast as the villain in the video)** — the molecule (usually a protein) a drug is designed to act on (03:32).
- **Enzyme** — a protein that speeds up a chemical reaction (03:38).
- **Lock-and-key** — classic metaphor: drug (key) fits a binding site on the target (lock) (03:46).
- **Small molecule** — a low-molecular-weight drug (e.g. Tylenol/acetaminophen, aspirin) that can be made as a pill and often enters cells (04:00).
- **Antibody** — a large Y-shaped immune protein that binds a specific target (antigen); engineered antibodies are a major drug class (04:14, 26:28).
- **Antigen** — the thing an antibody binds; here the disease antigen or disease target (26:52).
- **Side effect / off-target** — an off-target effect is a drug acting on molecules other than its intended target, which is the video's image of a key that opens other locks too (04:45). [verifier-corrected] Side effects can also be *on-target*, for example when the intended target also does a job in healthy tissue.
- **Dose / safe doses** — the amount given; efficacy must be shown at non-toxic doses (05:16).
- **Clinical trials / approval** — human testing stages before a regulator (e.g. FDA) approves a drug (00:59, 11:14).
- **AlphaFold / AlphaFold 3** — Google DeepMind's protein-structure prediction systems; AF3 also models complexes with other molecules (05:38, 22:19).
- **Evo 2** — a DNA-sequence foundation model (05:44).
- **Foundation model** — a large model pre-trained on broad data and then adapted to many tasks; the video suggests MAMMAL may be biology's first genuine foundation model (29:29).
- **Pre-training / samples** — the initial large-scale training phase; "2 billion samples" = 2 billion training examples (06:58).
- **Observed Antibody Space (OAS)** — a public database of antibody sequences (07:04).
- **UniProt** — the main public protein-sequence database (07:09).
- **ZINC, PubChem** — public databases of small-molecule structures (07:13).
- **CELLxGENE** — Chan Zuckerberg Initiative's portal of single-cell gene-expression datasets (07:18).
- **SMILES** — Simplified Molecular Input Line Entry System: a text notation for molecules (letters = atoms, "=" = double bond, etc.) (07:48). [verifier-added] The video's claim that each letter is an atom is a simplification: some atoms take two letters (Cl, Br), lowercase letters mark aromatic atoms, hydrogens are usually left implicit, and digits and parentheses encode rings and branches.
- **Sequence model / language model / LLM** — a neural network that reads and predicts sequences of tokens; the video calls MAMMAL merely a sequence model and a large language model working on sequences (22:34, 25:17).
- **Tokenizer / token** — the component that splits raw input into the units (tokens) a model consumes; likened to a dictionary in the video (09:08).
- **Modular tokenizer** — MAMMAL's design: one umbrella tokenizer with separate sub-vocabularies per modality (molecules, genes, proteins) (09:05–09:27).
- **Embedding** — a vector of numbers representing a token; the video speaks of converting each input into tokens and embeddings (09:34) [verifier-corrected: wording; paraphrased in this edition].
- **Shared multi-dimensional (embedding/latent) space** — all modalities' embeddings live in the same vector space, so relationships across them can be learned (09:51).
- **Multimodal** — handling several data types in one model (13:18).
- **Benchmark / state of the art (SOTA)** — a standard test set; the best published result on it (10:21, 10:37).
- **Generalist vs specialist** — the decathlete/swimmer analogy: a broad model vs one trained on a single modality (12:34).
- **BBBP** — Blood–Brain Barrier Penetration: a MoleculeNet classification benchmark (does a molecule cross into the brain?) (11:04).
- **Blood-brain barrier** — the tightly sealed vessel lining that keeps most substances out of the brain (11:16).
- **ClinTox** — a MoleculeNet benchmark with two labels: FDA approval status and clinical-trial toxicity (11:10).
- **MoLFormer** — IBM's large chemical language model trained on >1 billion SMILES; used as the specialist baseline (11:56).
- **Cell-type annotation / labelling** — assigning a cell identity (e.g. CD4+ T cell, NK cell) from its gene-expression profile (15:18).
- **Zheng68K** — a benchmark dataset of ~68,000 human peripheral-blood immune cells with single-cell RNA-seq and cell-type labels (15:21).
- **CD4+ T cell; NK cell** — two immune cell types (helper T cells; natural killer cells) (15:36).
- **Drug response (cancer)** — how strongly a drug inhibits/kills cancer cells; typically measured on cell lines (16:07).
- **Cell line / tumour cell types** — laboratory-grown cancer cells from a given tumour; the video's 805 cancer-tumour variations (16:48, 18:08) [verifier-corrected: wording; paraphrased in this edition].
- **Potency ranking** — ordering drugs by how little is needed to produce an effect (18:06).
- **Held-out / unseen drugs** — compounds deliberately excluded from training to test generalisation (16:27).
- **Memorisation vs generalisation** — reproducing training data vs correctly handling new inputs (16:14).
- **Tanimoto similarity** — a 0–1 score of structural similarity between two molecules based on their chemical fingerprints; the video treats < 0.7 as meaning essentially structurally different (17:28).
- **Carfilzomib** — a proteasome inhibitor approved for multiple myeloma (a blood cancer) (16:33).
- **Nintedanib** — a multi-target kinase inhibitor, approved for idiopathic pulmonary fibrosis and other fibrosing lung diseases. [verifier-corrected] Its approval for lung cancer (non-small-cell lung adenocarcinoma, with docetaxel) is in the EU, not the US (16:34).
- **Infigratinib** — an FGFR kinase inhibitor (16:35).
- **Vemurafenib** — a BRAF kinase inhibitor used in melanoma (16:37).
- **FDA-approved** — licensed for sale by the US Food and Drug Administration (18:34).
- **Blood cancers vs solid tumours** — leukaemias/lymphomas/myeloma vs tumours of organs (18:39).
- **Drug repurposing** — finding new uses for existing or failed drugs (20:33).
- **Protein folding / Levinthal's paradox** — the fact that proteins reach their native shape in microseconds to seconds [verifier-corrected: was "in microseconds"; only small fast-folders fold in µs] despite an astronomical number of possible conformations (21:38).
- **Antibody–antigen binding** — whether a given antibody sticks to a given target; here posed as a yes/no question (22:48).
- **Nobel Prize in Chemistry (2024)** — awarded in part for AlphaFold (22:31).
- **Intrinsically disordered region (IDR)** — a part of a protein that has no single stable 3D structure; the video's wet-spaghetti image (23:52).
- **EGFR; HER2** — receptor tyrosine kinases that drive several cancers; both are antibody-drug targets (24:27).
- **Static vs dynamic structure** — a single fixed 3D model vs the moving ensemble of shapes a protein actually adopts (24:13).
- **Generative / inventor mode** — producing new sequences rather than scoring existing ones (26:14).
- **CDR (complementarity-determining region)** — the hypervariable loops at the antibody's tips that make most of the contacts with the antigen; the video's fingers metaphor (26:56). [verifier-corrected] There are six per antigen-binding site: H1–H3 on the heavy chain and L1–L3 on the light chain. A two-armed IgG has twelve in total.
- **CDR-H3** — the third CDR of the heavy chain; longest, most variable, most important for specificity (28:34).
- **SAbDab** — the Structural Antibody Database of antibody structures (27:30).
- **Fill-in-the-blank / infilling** — masking part of a sequence and asking the model to regenerate it (27:46).
- **Personalised medicine** — tailoring diagnosis and treatment to an individual's molecular profile (00:24, 30:14).
- **Runway Agent** — sponsor's AI video-generation product; not a biology term (13:56).

---

## 10. Hand-off to the fact-checker — the claims that most need verification

In rough priority order (row numbers refer to §4):

1. #47 (10:35) — the claim of SOTA on **all** 11 benchmarks vs the paper's wording.
2. #78–80 (19:19–19:44) — the nature of the physical lab experiment, the 805 cell lines, and the ~95 % order-preservation figure.
3. #67, #71 (16:27, 17:38) — the four held-out drugs and the Tanimoto < 0.7 claim (3 of 4).
4. #74, #77 (18:17, 18:52) — carfilzomib ranked first; which drugs were 3rd/4th. The video implies vemurafenib 4th and infigratinib 3rd (19:40) [verifier-corrected].
5. #76 (18:40) — the claim that doctors believed carfilzomib useless against solid tumours.
6. #92–93 (22:57, 23:03) — 5 of 7 targets vs AlphaFold 3; what exactly was compared.
7. #99–102 (24:24–25:10) — whether the IDR / EGFR / HER2 explanation is in the paper.
8. #117 (29:04) — 19 % CDR-H3 improvement: metric and baseline.
9. #114 (28:17) — the claim that CDR infilling beat specialised state-of-the-art methods [verifier-corrected: wording; paraphrased in this edition]; which baselines.
10. #64 (15:55) — 7.5 % on Zheng68K: metric and baseline.
11. #54–55 (12:13–12:29) — BBBP/ClinTox margins vs MoLFormer; resolve "a few" vs "a huge".
12. #27–32 (06:58–07:18) — 2 billion samples and the five data sources (any omitted?).
13. #38, #40–44 (08:16–09:51) — encoding of expression as ranked genes; modular tokenizer; shared space.
14. #96 (23:45) — 30–40 % IDR figure.
15. #53 (11:57) — MoLFormer trained on over a billion molecules.
16. #26 vs #90 (06:46 vs 22:34) — the claim that MAMMAL understands chemistry, genetics and protein structure all at once vs its description as merely a sequence model [verifier-corrected: wording; paraphrased in this edition].
17. #107 (26:18) — the claim of designing entirely new antibodies vs CDR infilling.
18. #122 (30:10) — the claim that the model understands DNA.
19. #2 (00:06) — the just-released-paper framing vs preprint/journal dates.
20. #5 (00:54) — the 90 % failure-rate figure.
21. [verifier-added] #133, #135, #138, #143 — presenter attributions of confidence and of much better predictions on the floppy (IDR-rich) targets; check whether the paper reports anything specific to those targets.

---

## Verification notes

*Independent fidelity audit by Opus 5.5, 2026-10-04. Full report: `../07_verification/video_transcript_verification.md`.*

- **Scope.** This audit checked fidelity to the video, not the science. It compared the file against the Whisper JSON (word-level timings), SRT and text, the auto-caption SRT and text (transcripts not redistributed), the live YouTube watch page and the oEmbed record.
- **Timestamps.** All 126 original rows of §4 were located by script. 121 matched within ±2 s. Five were corrected (#42, #53, #102, #104 and #115, off by 2.1–6.2 s), along with the matching Ch. 10 key quote. All 22 chapter starts, all 58 clean-transcript paragraph stamps (clean transcript not redistributed), every §5 number stamp and the §6 first-mention stamps are confirmed.
- **Numbers.** All headline figures are verbatim in **both** ASR sources at the stated times: 2 billion, 11 benchmarks, 7.5 %, 805, ~95 %, < 0.7 Tanimoto, 3 of 4, 7 targets / 5 of 7, 19 %, 30–40 %, 90 %, 10 years / a billion dollars, 10–15 years.
- **Wording.** The quotes were near-verbatim (in this public edition they have since been replaced by paraphrases). Fixed: two paraphrases printed as quotes in the TL;DR (#4 detectives, #9 decathlete), three in the chapter summaries (bridge, detectives, book analogy) and minor elisions (#42, #67, #87, glossary, hand-off). One substantive omission is corrected: the video *does* imply the 3rd and 4th-ranked drugs (vemurafenib last, 19:40).
- **Completeness.** 18 substantive claims were added (#127–#144), and four numbers were added to §5.
- **ASR.** Every correction in §7 is justified by the two sources. All nine Whisper word dropouts are real, and every auto-caption gap-fill is word-exact; the gap lengths were corrected. Six small unlisted source differences were added.
- **12:29 "a few" vs "a huge".** **Still unresolved** from the transcripts. Whisper has "huge" and the auto-captions have "few". The word's 0.20 s duration and the grammar favour "few"; listening to the audio or reading the paper's ClinTox table would settle it.
- **Metadata.** Re-fetched 2026-10-04 and all confirmed: title, channel and ID, `publishDate`/`uploadDate` 2026-05-13T20:27:14-07:00, `lengthSeconds` 1914 (a second field says 1915; `approxDurationMs` 1914399–1914400), `viewCount` 122,790, the description text, the paper link, and all 18 chapter markers. A web search confirms the link is the npj Drug Discovery article (published 4 May 2026).
- **Sponsor bounds** are confirmed: 13:48.94 (start of the sponsor pitch) to 15:17.52 (end of the promo code, "agent 50"); MAMMAL content resumes at 15:17.52.
- **Glossary.** No outright errors in the definitions of SMILES, Tanimoto, CDR-H3, IDR, ClinTox or BBBP. Five precision fixes were made: CDR (six per binding site), protein-folding speed, nintedanib's lung-cancer approval (EU), side effects (on- vs off-target) and the SMILES simplification.
