# Verification report: MAMMAL video transcript documentation

> Part of the dog-ageing research dossier · 2026-10-04 · Verifier: Opus 5.5 (independent fidelity audit) · Files audited were written by Fable 5.1 · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**Files audited**
- `02_mammal/video_transcript_documented.md` (claims table, numbers, entities, ASR corrections, rhetorical analysis, glossary)
- `02_mammal/video_transcript_clean.md` (clean, corrected full transcript; not redistributed in this public copy because the script is the creator's copyrighted work; [watch the video](https://www.youtube.com/watch?v=s3rNDndvav0) instead)

**Ground truth used**
- The Whisper JSON: 1,966 segments, 5,326 word tokens with start/end times. Fields are only `w`/`s`/`e`, with no confidence scores.
- The Whisper SRT and plain-text transcript
- The YouTube auto-caption SRT (825 cues) and plain-text transcript
- (The transcripts are not redistributed: the script is the creator's copyrighted work.)
- The live YouTube watch page and oEmbed record, fetched 2026-10-04
- A web search to identify the article linked in the description

**Scope.** This is a *fidelity* audit: does the documentation faithfully say what the video says? The science is checked by a separate agent against the MAMMAL paper.

**Method.** Every check was scripted against the word-level JSON and the auto SRT, so nothing rests on a by-eye sample:
- an exact and fuzzy phrase locator for every quote;
- a full `difflib` token alignment of Whisper against the auto-captions, which lists every place the two sources diverge;
- a per-paragraph token diff of the clean transcript against both sources.

Every flag the scripts raised was then inspected by hand. The scripts are in the session scratchpad; they are not part of the dossier.

---

## 1. Fidelity rating: **HIGH**

The documentation is accurate and carefully sourced:
- All headline numbers are verbatim in both ASR sources at the stated times.
- 121 of 126 claim-table timestamps were already within ±2 s; the other five were 2.1–6.2 s off.
- No claim is attributed to the video that it does not make.
- The clean transcript drops no sentence and invents none.

Most errors were small: paraphrases printed inside quotation marks, slightly wrong gap lengths, and a miscount of the Whisper dropouts. **One substantive fidelity error was found and fixed.** The draft said the 3rd- and 4th-ranked drugs were "shown only on screen". But at 19:40 the presenter says the measured order ran down to vemurafenib as least potent, which implies vemurafenib was 4th and infigratinib 3rd.

---

## 2. Counts

| Check | Items checked | Confirmed as written | Corrected / added |
|---|---|---|---|
| Claims-table timestamps (§4, rows #1–126) | 126 | 121 | 5 corrected (#42, #53, #102, #104, #115) |
| Chapter key-quote timestamps (§3) | 51 | 50 | 1 (Ch. 10, 11:57 → 11:59) |
| Chapter boundaries: 22 starts, 21 ends | 43 | 43 (ends within 1–2 s rounding) | 0 |
| Clean-transcript paragraph timestamps | 58 | 58 | 0 |
| Numbers-table timestamps (§5) | 37 rows / ~48 stamps | all within ±2 s (word or segment start) | 4 rows added |
| Entity first-mention timestamps (§6) | 24 | 24 | 0 |
| Headline numbers, verbatim in both sources (2 billion, 11, 7.5 %, 805, ~95 %, < 0.7, 3 of 4, 7, 5 of 7, 19 %, 30–40 %, 90 %, 10 yr / $1B, 10–15 yr) | 14 | 14 | 0 |
| Quote wording: claims rows plus key quotes (fuzzy match ≥ 0.9) | 177 | 171 | 6 (#31, #42, #67 and its key quote, #87, #115) |
| Quoted phrases in TL;DR, summaries, glossary and hand-off | ~60 | ~48 | 12 paraphrases-in-quotes fixed (TL;DR 4, chapter summaries 3, glossary 3, hand-off 2) |
| Fidelity of interpretation (is any claim attributed to the video that it doesn't make?) | all sections | — | 1 substantive (3rd/4th drug), 1 nuance (hedge pattern in §8.1 D) |
| Completeness: substantive claims missing from §4 | full scan of both transcripts | — | 18 rows added (#127–#144) |
| Completeness: numbers missing from §5 | every numeric token in Whisper | — | 4 added (decades @00:00, two drug types @03:56, "first" @29:29, "this year" @31:00) |
| ASR correction table (§7) rows | 48 | 48 (sources differ exactly as stated; every fix plausible) | 5 gap lengths corrected, 1 gap length added, 6 rows added, summary corrected |
| Whisper dropouts and auto gap-fills | 9 | 9 real, 9 fills word-exact | count and lengths corrected |
| Sponsor bounds | 1 | yes: 13:48.94 → 15:17.52 | 0 |
| Clean transcript, paragraphs diffed against both sources | 58 of 58 (all, not 15) | 54 with no unmarked change | 4 unmarked edits marked or reverted; 5 marker gap lengths fixed; header note fixed |
| Metadata fields | 10 | 10 | 0 |
| Glossary entries scanned for scientific errors | 66 | 61 | 5 precision fixes: side effect, SMILES, Levinthal, CDR, nintedanib (the quote fixes are counted above). No outright errors in SMILES, Tanimoto, IDR, ClinTox, BBBP or CDR-H3. |

The edited files carry 69 `[verifier-…]` markers in the documented file and 10 in the clean file.

---

## 3. Table of corrections

"Doc" = `video_transcript_documented.md`; "Clean" = `video_transcript_clean.md` (not redistributed). In this public edition the video's wording in the "Was"/"Now" columns is described or paraphrased rather than quoted.

| # | File / location | Was | Now | Evidence |
|---|---|---|---|---|
| 1 | Doc §4 #42 | 09:16; a shortened version of the sub-dictionary sentence | **09:19**; the full sentence (one dictionary each for chemistry, genetics and proteins) | W segment for the umbrella-tokenizer sentence starts 559.18 s |
| 2 | Doc §4 #53 and Ch. 10 key quote | 11:57 | **11:59** | W segment for the MoLFormer training-data sentence starts 719.44 s |
| 3 | Doc §4 #102 | 25:05 | **25:10** | W segment for the floppy-proteins sentence starts 1510.38 s; 25:05 is the preceding sentence (now row #138) |
| 4 | Doc §4 #104 | 25:36 | **25:38** | W segment for the robustness sentence starts 1538.10 s |
| 5 | Doc §4 #115 | 28:34; opening "The CDR-H3 region…" | **28:40**; opening "This CDR-H3 region…" | W 1720.22 s; 28:34 is the first mention of CDR-H3 |
| 6 | Doc Ch. 13 summary, §4 #74, §8.2, §10 item 4 | 3rd/4th drugs "named only on screen" | Video **implies vemurafenib 4th and infigratinib 3rd** (19:40: the measured order is said to run down to vemurafenib as least potent, and to match the prediction) | W 1180.18–1184.00 s; A cue at 19:39 |
| 7 | Doc §2 TL;DR item 4 | "detectives who each hold one clue" (in quotes) | paraphrase + the verbatim phrase about the detectives not really talking to each other (paraphrased in this public edition) | phrase does not occur in either source |
| 8 | Doc §2 TL;DR item 9 | a paraphrase of the decathlete/swimmer line printed in quotes | the verbatim line (paraphrased in this public edition) | W/A 12:53 |
| 9 | Doc §2 TL;DR items 6, 14 | two clipped paraphrases printed in quotes (gene ranking; foundation-model claim) | the verbatim lines (paraphrased in this public edition) | verbatim |
| 10 | Doc Ch. 2, 5, 8 summaries | paraphrases printed in quotes (bridge analogy with 9 out of 10, detectives and book analogies) | verbatim wording restored (paraphrased in this public edition) | W 01:23, 06:38, 08:42 |
| 11 | Doc Ch. 13 summary | the drugs' SMILES | the drugs' chemical strings (i.e. SMILES) | the video speaks of chemical strings, not SMILES, at 16:40 |
| 12 | Doc §4 #67 and key quote | list lead-in elided | lead-in words restored | W 16:32 |
| 13 | Doc §4 #31 and Clean 06:43 | "which contain millions" | "which contains millions" | both sources say "contains"; the draft had silently changed the speaker's grammar |
| 14 | Doc §4 #87 | an aside ("of course") silently dropped | aside restored | W 21:49 |
| 15 | Doc §7 and Clean markers | gaps "2-s" (22:59), "2.5-s" (23:58), "3-s" (24:27), "3-s" (25:58), "4-s" (28:52); 25:29 unstated | **1.3, 2.4, 2.2, 2.6, 3.4 s**; 25:29 = **1.0 s** | W word end→start times (listed in §5 below) |
| 16 | Doc §7 summary and Clean conventions | "five multi-second dropouts" (six listed) / "five such gaps, each 2–5 s long" | **nine** dropouts: four ≥ 2 s and five of 0.8–1.5 s (18:05, 20:31, 22:59, 25:29, 29:55) | full token alignment |
| 17 | Doc §7 rows added | — | 05:45 "One of them / One One"; 07:15 "contains"; 18:41 "believe/believed"; 23:23 "So/To"; 24:06 "and/An"; 25:34 "the/a" | alignment diff |
| 18 | Clean 18:30, 23:23, 23:56 paragraphs | auto readings adopted without marks | now marked `[ASR: … — verifier-added]` | alignment diff |
| 19 | Doc §7 row 23:58 and Clean marker | Whisper "these [gap] have…" | Whisper "these **these** [gap] have…" | W 1437.92–1438.86 s |
| 20 | Doc §4 #127–#144 | — | 18 substantive claims added (e.g. the confident-ranking remark, 18:14; the much-better-predictions remark, 25:05; the inferred-shape remark, 28:07; the faster-drug-design remark, 29:53) | each located in W (or A where Whisper dropped words) |
| 21 | Doc §5 | — | 4 numbers added | numeric-token scan |
| 22 | Doc §8.1 D (hedges) | hedges "almost exclusively in the last two minutes"; body "unhedged" | kept, with an added note on two further soft modals at 00:15 and 25:54 | W token scan |
| 23 | Doc §9 glossary | Side effect = off-target only | adds on-target side effects | standard pharmacology |
| 24 | Doc §9 glossary | SMILES "letters = atoms" | notes two-letter atoms, aromatic lowercase, implicit H, ring/branch symbols | SMILES specification |
| 25 | Doc §9 glossary | Levinthal: proteins fold "in microseconds" | "microseconds to seconds" | protein-folding kinetics |
| 26 | Doc §9 glossary | CDR: "the six hypervariable loops at the antibody's tips" | six **per antigen-binding site** (H1–H3, L1–L3); twelve on an IgG | antibody structure |
| 27 | Doc §9 glossary | Nintedanib "approved for lung fibrosis and some lung cancers" | IPF/fibrosing ILDs; lung-cancer (NSCLC adenocarcinoma, with docetaxel) approval is EU, not US | regulatory status |
| 28 | Doc §9 glossary; §10 items 9, 16 | five paraphrases printed in quotes (embeddings, tumour cell types, 805 variations, specialised methods, protein structure) | verbatim wording (paraphrased in this public edition) | W/A |
| 29 | Both headers | Status: draft | "independently verified by Opus 5.5 on 2026-10-04 — see ../07_verification/video_transcript_verification.md" | — |

---

## 4. Ambiguities

| Ambiguity | Status | Detail |
|---|---|---|
| **12:29: "a few" vs "a huge" percentage points (MAMMAL's ClinTox margin over MoLFormer)** | **UNRESOLVED from the transcripts; leaning "few"** | **Whisper JSON:** segment 749.24–751.00 s has "huge"; the word spans 749.82–750.02 s (0.20 s). The SRT cue at 00:12:29,240 → 00:12:31,000 reads the same. **Auto SRT:** cue 325 (00:12:26,720 → 00:12:29,590) ends with "by"; cue 326 (00:12:29,600 → 00:12:31,790) begins "a few percentage points". The auto .txt agrees. **Evidence for "few":** (a) the Whisper phrasing with "huge" is ungrammatical, while the auto phrasing with "few" is idiomatic; (b) Whisper's other five "huge" tokens last 0.30–0.42 s, but this one lasts 0.20 s, close to its only "few" token (0.16 s, 02:38). No audio file is in the dossier and no confidence scores exist. To settle it, either listen at 12:29 or read the ClinTox row of the paper's results table (the fact-check agent's job). |
| 23:58: Whisper omits the subject and the negation ("don't") that the auto-captions have before "have a stable 3D shape" | **Resolved: auto reading** | Whisper has a 2.4 s hole (1438.86 → 1441.30 s) exactly where the auto words fall; Whisper's version inverts the meaning. |
| 24:27: HER2 missing from Whisper | **Resolved: auto reading** | 2.2 s Whisper hole (1468.32 → 1470.52 s); auto cue 1468.68–1471.83 s contains HER2. |
| Other dropouts (18:05, 20:31, 22:59, 25:29, 25:58, 28:52, 29:55) | **Resolved: auto readings** | Each Whisper gap aligns with the missing auto words; each fill is word-exact. |
| 3rd/4th predicted drugs (18:25, where the presenter points at the screen) | **Partly resolved from the audio track** | 19:40 implies vemurafenib 4th, so infigratinib 3rd. The explicit on-screen labels are not in the transcripts. |
| Which drug had Tanimoto ≥ 0.7 | **Not stated in the video** | Must come from the paper. |
| 18:41 "believe" (W) vs "believed" (A) | **Resolved: "believed"** | fits the past-tense framing of the sentence; meaning unchanged. |

---

## 5. Whisper dropout measurements (word end → next word start, from JSON)

| Location | Last W word before | Gap | Restored from auto-captions |
|---|---|---|---|
| 18:05 | "before" ends 1084.08 → "as" 1085.56 | 1.48 s | a short back-to-the-task transition |
| 20:31 | "discovery" ends 1232.44 → "for" 1233.48 | 1.04 s | "and especially" |
| 22:59 | "well" ends 1380.28 → "and" 1381.54 | 1.26 s | "well-documented targets" |
| 23:58 | "these" ends 1438.86 → "have" 1441.30 | 2.44 s | the subject (the protein sections) plus "don't" |
| 24:27 | "EGFR" ends 1468.32 → "and" 1470.52 | 2.20 s | "HER2, which are notoriously" |
| 25:29 | "including" ends 1530.34 → "it" 1531.30 | 0.96 s | "floppy parts" |
| 25:58 | "now" ends 1558.70 → "existing" 1561.30 | 2.60 s | a clause saying MAMMAL had so far only been asked about existing candidates |
| 28:52 | "responsible" ends 1733.60 → "and" 1737.04 | 3.44 s | a clause on what the antibody can bind to |
| 29:55 | "design" ends 1795.60 → "way" 1796.42 | 0.82 s | "drugs" |

---

## 6. Metadata re-check (fetched 2026-10-04)

| Claim | Independently confirmed? | Source |
|---|---|---|
| Title "The biggest AI breakthrough in medicine & drug discovery" | Yes | oEmbed `title`; watch page |
| Channel "AI Search", @theAIsearch, ID UCIgnGlGkVRhd4qNFcEwLL4A | Yes | oEmbed `author_name`/`author_url`; watch page `ownerChannelName`, `channelId`, `externalChannelId` |
| Video ID s3rNDndvav0 | Yes | — |
| Upload date 2026-05-13 | **Yes**: `publishDate` and `uploadDate` both read "2026-05-13T20:27:14-07:00"; microdata `datePublished` is the same; the page shows "May 13, 2026" | watch page HTML |
| Duration 1,914 s | Yes: `lengthSeconds` "1914" (a second field says "1915"); `approxDurationMs` 1914399–1914400. Last speech 1912.98–1913.74 s (W); last auto cue 1913.12–1915.84 s | watch page; JSON; SRT |
| View count 122,790 | Yes, the same value at this fetch (it is a moving figure) | watch page `viewCount` |
| Description first line, sponsor link, "Full paper: https://www.nature.com/articles/s44386-026-00047-4" | Yes, verbatim | watch page `shortDescription` |
| 18 presenter chapter markers (0:00 … 29:29) | Yes, all 18 verbatim | `shortDescription` |
| Linked article is npj Drug Discovery, "MAMMAL – Molecular Aligned Multi-Modal Architecture and Language for biomedical discovery" | Yes (title and journal) | web search result for that URL. nature.com redirected to an auth page, so the article page itself was not opened. The search index gives publication as 4 May 2026, 9 days before the video, which is consistent with the documenter's note. |

---

## 7. Remaining issues and limits

1. **12:29 magnitude ("a few" vs "a huge")** is still open; see §4. Do not quote the ClinTox margin from this video until the audio or the paper's table is checked.
2. **On-screen content is not in either transcript.** This covers the results table (10:33), the Tylenol SMILES (07:58) and the 3rd/4th drug labels (18:25). Anything the presenter "shows" cannot be verified from these files.
3. **Minor chapter-range inconsistencies were left as they are, within tolerance.** Ch. 12 ends 16:03 but Ch. 13 starts 16:02. The Ch. 13 end is 20:17 in the documented file and 20:19 in the clean file; the true boundary is 20:18.7 (the 20:18 segment start).
4. **Out of scope and not verified here:** the documenter's notes in the documented file that go beyond the video, namely IBM authorship, arXiv 2410.22367, the 458 M-parameter model card, and "SOTA on 9 of 11". The search snippet is consistent with "nine tasks… competitive on two" and "five of seven antigen targets", but these belong to the paper fact-check.
5. **Two glossary refinements rest on general knowledge, not this audit's sources:** nintedanib's EU-only lung-cancer approval and protein-folding timescales. The science fact-checker may wish to confirm them.
6. The 18 added claims (#127–#144) carry provisional Category and Flag labels from the verifier. Four of them (#133, #135, #138, #143) are queued for the fact-checker as hand-off item 21.
