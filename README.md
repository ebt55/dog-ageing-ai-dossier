# Dog ageing × AI: a research dossier

**AlphaFold, IBM's MAMMAL model, AI for dogs and wolves, why dogs age so fast, and research paths to change it**

*Compiled 2026-10-04. Statuses of trials, companies and software change quickly, so check the dates.*

---

## Start here

| If you want… | Read |
|---|---|
| Answers to every question in one page | [00_synthesis/executive_summary.md](00_synthesis/executive_summary.md) |
| **The ranked research paths for understanding and changing dog ageing** | [00_synthesis/research_paths_dog_ageing.md](00_synthesis/research_paths_dog_ageing.md) |
| How trustworthy each file is | [07_verification/](07_verification/) |
| Every source and credit, grouped | [CREDITS.md](CREDITS.md) |

## Folder map

| Folder | Contents |
|---|---|
| [`00_synthesis/`](00_synthesis/) | Executive summary; ranked research paths |
| [`01_alphafold/`](01_alphafold/) | [Complete guide](01_alphafold/alphafold_complete_guide.md) (history to Oct 2026, how it works, limits, competitors) · [How to use it](01_alphafold/how_to_use_alphafold.md) (DB API, Server, local AF3, open alternatives, worked dog IGF-1/IGF1R example) · [AlphaFold and dogs/wolves](01_alphafold/alphafold_and_dogs.md) (coverage, gaps, veterinary uses) |
| [`02_mammal/`](02_mammal/) | [Video documentation](02_mammal/video_transcript_documented.md) (chapters, 144-row timestamped claims table, ASR corrections, glossary) · [Paper deep dive](02_mammal/mammal_paper_deep_dive.md) (architecture, data, all 11 benchmarks, AF3 comparison, carfilzomib experiment) · [Video fact-check](02_mammal/video_claims_factcheck.md) (77 claims) · [Can MAMMAL do dogs?](02_mammal/mammal_for_dogs.md) |
| [`03_canine_bio_ai/`](03_canine_bio_ai/) | [Is there a foundation model for dogs/wolves?](03_canine_bio_ai/dog_foundation_models_landscape.md) · [Companies and research groups](03_canine_bio_ai/companies_and_research_groups.md) |
| [`04_dog_aging_biology/`](04_dog_aging_biology/) | [Why dogs age fast](04_dog_aging_biology/why_dogs_age_fast.md) (evolution, mechanisms, "dog years") · [Breed size, genetics and lifespan](04_dog_aging_biology/breed_size_genetics_lifespan.md) · [Wolves vs dogs](04_dog_aging_biology/wolves_vs_dogs.md) |
| [`05_interventions/`](05_interventions/) | [Longevity interventions](05_interventions/dog_longevity_interventions.md) (Loyal, TRIAD/rapamycin, caloric restriction, gene therapy, supplements, FDA pathway) · [Gene editing in dogs](05_interventions/gene_editing_in_dogs.md) (feasibility, ethics, regulation) |
| [`06_ai_toolkit/`](06_ai_toolkit/) | [Canine data resources](06_ai_toolkit/canine_data_resources.md) · [AI tools for dog ageing](06_ai_toolkit/ai_tools_for_dog_aging.md) (45+ tools, dog-readiness, licences) · [18 research-path candidates](06_ai_toolkit/research_path_candidates.md) |
| [`07_verification/`](07_verification/) | One audit report per topic, with claim tables, corrections and open issues |
| [`CREDITS.md`](CREDITS.md) | **All credits and resource links in one place**: curated key resources plus a grouped index of every source cited |
| [`LICENSE`](LICENSE) · [`CITATION.cff`](CITATION.cff) | CC BY 4.0 licence; citation metadata |

## Headline findings

1. **The dog–human lifespan gap is about 5–6×, not 10×.** For their body size, dogs live about as long as a typical mammal. **Humans are the outlier**, at about 4.6× the expected lifespan.
2. **Dogs inherited the wolf's fast life history.** Almost every biological clock runs 4–10× faster in dogs: somatic mutations, telomere loss, maturation, and the doubling time of mortality. These are probably readouts of one coordinated "tempo", not separate causes.
3. **Within dogs, big breeds age faster.** The genetics are few and mapped, on the GH/IGF-1 axis (IGF1-AS, IGF1R, GHR…). Captive wolves of similar size reach 15–20 y, so large-breed brevity looks like a product of selection, which makes it the most tractable dog-specific lever.
4. **Nothing is approved to extend dog lifespan** (Oct 2026). Lifelong caloric restriction (+1.8 y median) is the only proven intervention. Loyal's LOY-002 has 2 of 3 FDA sections accepted, and the TRIAD rapamycin trial is under way.
5. **No dog- or wolf-specific molecular foundation model exists.**
   - AlphaFold covers about 90.6% of dog proteins but misses long ones, including full-length IGF1R and MTOR.
   - Evo 2 and NTv3 saw a dog genome during training.
   - Single-cell and regulatory models exclude dogs, and variant-effect tools are the weakest link.
6. **The MAMMAL video is accurate on numbers but inflated in framing (hype 7/10).** MAMMAL is state of the art on 9/11 benchmarks, not 11. It has no DNA modality. Its "beat AlphaFold 3" result came from fine-tuning on those exact targets. It is not canine-ready without fine-tuning: 78% of dog gene symbols have a token.

## How this dossier was made

- **Research.** Eight research subagents ran in parallel, a mix of Claude Opus 5.5 and Claude Fable 5.1. Each researched one topic from primary sources (papers, preprints, official docs, regulatory filings, GitHub repos, database APIs) and tagged its claims:
  - ✅ primary source opened
  - 🟡 abstract or secondary source
  - ❓ unconfirmed
- **Verification.** Every topic was then audited by a subagent from the **other** model family. The auditors:
  - re-checked numbers against primary sources and re-ran calculations;
  - corrected errors in place, marked `[verifier-corrected]`;
  - wrote a report in `07_verification/`.
  - **No fabricated citations were found.** The corrections were mostly wrong numbers, wrong attributions, outdated statuses and over-confident tags.
- **Synthesis.** The orchestrating model (Opus 5.5) wrote `00_synthesis/` from the verified files.

| Topic | Reliability after audit |
|---|---|
| Video transcript documentation | High |
| AlphaFold | High |
| MAMMAL (paper, fact-check, dogs) | High |
| Why dogs age fast | High |
| Breed size, genetics, wolves | Medium-high |
| Canine bio-AI landscape | Medium-high |
| Interventions and gene editing | Medium |
| AI toolkit: data and tools | High |
| AI toolkit: research proposals | Medium-high (verifier comments added to each proposal) |

## Caveats

- **This is AI-generated research, audited by AI rather than by human domain experts.** Treat it as a well-sourced starting point, and check the primary sources (all linked) before relying on any claim.
- **This is not veterinary advice.** Don't give any drug or supplement mentioned here to a dog without a veterinarian.
- **Proposals are proposals.** Everything labelled PROPOSAL is speculative by design, and cost and time estimates are rough.
- **Results can be date-sensitive.** Live database counts (UniProt, AlphaFold DB) and company milestones were correct on 2026-10-04.

## About the video analysis

`02_mammal/` analyses the YouTube video *The biggest AI breakthrough in medicine & drug discovery* by **AI Search** (https://www.youtube.com/watch?v=s3rNDndvav0).
- The video's script is the creator's copyrighted work.
- This public edition therefore **does not include the transcripts**, and it paraphrases the video's claims, with timestamps, so you can check the exact wording in the video.

## Credits and sources

Every source is cited in the file that uses it. All credits and resource links are also collected and grouped in **[CREDITS.md](CREDITS.md)**:
- the video creator and the MAMMAL authors;
- AlphaFold and the data providers;
- key papers by topic;
- the full source index.

## Licence

**Text and documentation:** © 2026 Ebin Babu Thomas, licensed under **[Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/)** (full text in [`LICENSE`](LICENSE)). You may share and adapt it for any purpose, including commercially, as long as you give appropriate credit, link to the licence and indicate any changes.

**Third-party material is not covered by this licence.** It remains under its owners' terms. This includes:
- papers, figures, data and software referenced or briefly quoted here;
- the YouTube video;
- AlphaFold weights, which are under non-commercial terms;
- the Dog Aging Project data, which are under a data-use agreement.
