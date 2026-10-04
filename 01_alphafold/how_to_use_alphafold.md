# How to Use AlphaFold (and its open alternatives): A Practical Guide
> Part of the dog-ageing research dossier · Written 2026-10-04 by Opus 5.5 subagent · Status: independently verified by Fable 5.1 on 2026-10-04 — see ../07_verification/alphafold_verification.md · Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

**Confidence tags:** ✅ = confirmed in a primary source I opened, or by a live query I ran on 2026-10-04 · 🟡 = secondary source or partially checked · ❓ = unconfirmed.

---

## TL;DR

- **Need a single protein's structure fast?** Look it up in **AlphaFold DB**: `https://alphafold.ebi.ac.uk/api/prediction/<UniProt accession>`. That call returns the URLs for mmCIF/bCIF/PDB, PAE, pLDDT and MSA files (current version **v6**). The data are CC BY 4.0, free for commercial use [1][2][3] ✅.
- **Need a complex (protein + protein / DNA / ligand / ion / PTM)?** Use **AlphaFold Server** (AF3). It is free and non-commercial, limited to **30 jobs/day** and **5,000 tokens/job**. You can add any ligand by its PDB CCD code (no SMILES), and choose from a fixed list of ions and PTMs [4][5] ✅.
- **Need many runs, custom ligands (SMILES) or full control?** Run **AF3 locally**.
  - Code is Apache 2.0 since June 2026; weights can be downloaded directly since 23 July 2026, but are **for non-commercial use only** [6][7] ✅.
  - Hardware: Linux plus an NVIDIA GPU with compute capability ≥8.0 is the verified path; an A100/H100 80 GB fits 5,120 tokens [8] ✅.
  - You need ≥64 GB RAM and up to 1 TB of disk; the genetic databases are 252 GB compressed / 630 GB unpacked [8] ✅.
  - CPU-only and Apple Silicon modes have existed since v3.0.4 [6] ✅.
- **Need commercial freedom?** Use **Boltz-2** (MIT; also predicts small-molecule affinity), **Chai-1** (Apache 2.0), **Protenix v1** (Apache 2.0), **OpenFold3/OpenBind-0** (Apache 2.0) or **RF3** (BSD) [9][10][11][12][13] ✅.
- **Quick and free on a laptop?** **ColabFold** notebooks offer AF2/Multimer, an "AlphaFold3 (OpenFold3)" notebook, Boltz, ESMFold and BioEmu, using the MMseqs2 MSA server [14][15] ✅.
- **Dog worked example (§7).**
  - The *mature* dog IGF-1 is 100% identical to human IGF-1 (70/70 residues). The mature dog IGF1R is 98.1% identical to human IGF1R (1,312/1,337) [computed, §7] ✅.
  - The dog full-length IGF1R has **no** AlphaFold DB model, because unreviewed entries longer than 1,280 aa are excluded. You must model it yourself [3][16] ✅.
  - Any AF3 model of IGF-1/IGF1R will largely be **recall** of pre-2021 PDB structures (5U8Q, 6PYH) [17] ✅.

---

## 0. Which route should I use?

| Goal | Best route | Cost / licence | Notes |
|---|---|---|---|
| One protein, already in UniProt, ≤2,700 aa (Swiss-Prot / model proteomes) or ≤1,280 aa (rest of UniProt) | AlphaFold DB | Free; CC BY 4.0 [2] ✅ | Monomer only (plus some NVIDIA dimers for model organisms) |
| A protein not in AFDB (too long, has X residues, a variant, a new isoform) | ColabFold AF2, AF Server, or Boltz/Chai | Free | |
| Protein–protein, –DNA/RNA, –ligand, –ion complex | AF Server (non-commercial) or local AF3 / Boltz-2 / Chai-1 / Protenix | See §5 | |
| Small-molecule binding **affinity** | Boltz-2 | MIT | AF3 does not output affinity |
| Variant-effect scores (human) | AlphaMissense precomputed scores | CC BY 4.0 | **No dog or other non-human scores**; see `alphafold_and_dogs.md` |
| Commercial work | Boltz-2 / Chai-1 / Protenix v1 / OpenFold3 / RF3, or AF3 via Google Cloud | | AF Server, AF3 weights and AF3 outputs are non-commercial |

---

## 1. (a) Look up a precomputed structure in AlphaFold DB

### 1.1 Web
1. Go to https://alphafold.ebi.ac.uk. Search by UniProt accession, gene/protein name, or sequence (≥20 aa, standard amino acids only) [3] ✅.
2. The entry URL format is `https://alphafold.ebi.ac.uk/entry/AF-<ACCESSION>-F1` (also reachable as `https://alphafold.com/entry/AF-<ACCESSION>-F1`). [verifier-corrected] The claim that the older format without "AF-…-F1" no longer resolves was wrong: on 2026-10-04 both `https://alphafold.ebi.ac.uk/entry/P33712` and `https://alphafold.ebi.ac.uk/entry/AF-P33712-F1` loaded the same v6 entry page in a browser ✅.
3. The entry page shows the 3D model coloured by pLDDT, an interactive PAE plot, domain (TED) annotations and, for human proteins, AlphaMissense annotations [3] ✅. Since October 2026 it also shows literature-mined residue and mutation annotations [3] ✅.

### 1.2 REST API (current, v6 era)
The OpenAPI specification lists these endpoints [1] ✅:

| Endpoint | Returns |
|---|---|
| `GET https://alphafold.ebi.ac.uk/api/prediction/{accession or model ID}` | All models for that accession (canonical plus isoforms), with file URLs and summary metrics |
| `GET /api/complex/{accession or model ID}` | Complex (dimer) models containing that protein, e.g. NVIDIA-generated dimers |
| `GET /api/uniprot/summary/{accession}.json` | 3D-Beacons-style summary (model URL, coverage, created date) |
| `GET /api/annotations/{accession}.json?type=MUTAGEN` | Annotations. For human proteins this includes AlphaMissense ("AM score"). |
| `GET /api/sequence/summary` | Sequence-based lookup |

- Legacy API fields were **sunset on 25 June 2026**. Use the current field names [2] ✅.
- Live example, run 2026-10-04 for dog IGF-1 (P33712) [1] ✅. The response includes:
  - `"latestVersion":6`, `"toolUsed":"AlphaFold Monomer v2.0 pipeline"`, `"globalMetricValue":55.19`, `"modelCreatedDate":"2025-08-01"`
  - `"cifUrl":"https://alphafold.ebi.ac.uk/files/AF-P33712-F1-model_v6.cif"`
  - `"pdbUrl": ".../AF-P33712-F1-model_v6.pdb"`, `"bcifUrl": ".../AF-P33712-F1-model_v6.bcif"`
  - `"paeDocUrl": ".../AF-P33712-F1-predicted_aligned_error_v6.json"`, `"paeImageUrl": "..._v6.png"`
  - `"plddtDocUrl": ".../AF-P33712-F1-confidence_v6.json"`
  - `"msaUrl": ".../files/msa/AF-P33712-F1-msa_v6.a3m"` ([verifier-corrected] on 2026-10-04 this URL returned HTTP 403 "AccessDenied … Anonymous caller does not have storage.objects.get access" from Google Cloud Storage, on plain and range GETs, with or without a browser user-agent and referer; the AFDB FAQ says MSAs "are available on individual entry pages", so use the entry page's download control or re-check later ❓)
  - For a human entry (e.g. P08069), the same call also returns `amAnnotationsUrl` (AlphaMissense CSVs). The dog entry does not.

```bash
# Get metadata + file URLs (Windows users: add --ssl-no-revoke if curl complains about revocation)
curl -s "https://alphafold.ebi.ac.uk/api/prediction/P33712" | python -m json.tool | head -40
# Download the model and per-residue confidence
curl -O "https://alphafold.ebi.ac.uk/files/AF-P33712-F1-model_v6.cif"
curl -O "https://alphafold.ebi.ac.uk/files/AF-P33712-F1-confidence_v6.json"
```

```python
import requests, statistics
acc = "P33712"  # dog IGF1
meta = requests.get(f"https://alphafold.ebi.ac.uk/api/prediction/{acc}").json()[0]
conf = requests.get(meta["plddtDocUrl"]).json()          # keys: residueNumber, confidenceScore, confidenceCategory
mature = [s for r, s in zip(conf["residueNumber"], conf["confidenceScore"]) if 49 <= r <= 118]
print(meta["entryId"], meta["latestVersion"], round(statistics.mean(mature), 1))
```

### 1.3 File types

| File | Content |
|---|---|
| `.cif` / `.bcif` (ModelCIF) / `.pdb` | Coordinates. The B-factor column holds **pLDDT** (higher is better), not a real B-factor. Beware when using models for molecular replacement [15] ✅. |
| `confidence_v6.json` | Per-residue pLDDT and category [1] ✅ |
| `predicted_aligned_error_v6.json` | `predicted_aligned_error` (N×N, integers) and `max_predicted_aligned_error` (31.75) [3] ✅ |
| `msa_v6.a3m` | The MSA used as input. Available per entry since v6; "bulk access is not currently planned" [2] ✅. [verifier-corrected] Direct download of the API's `msaUrl` returned HTTP 403 on 2026-10-04 (see §1.2) ❓ |

### 1.4 Bulk downloads
- FTP: `https://ftp.ebi.ac.uk/pub/databases/alphafold/latest/` [16] ✅. It has:
  - **46 proteome tarballs** (`UP…_<taxid>_<CODE>_v6.tar`), e.g. HUMAN 4.8 GB, MOUSE 3.5 GB
  - `swissprot_cif_v6.tar` (37 GB) and `swissprot_pdb_v6.tar` (27 GB)
  - **Dog (taxid 9615) is not among them.**
- Older versions (v1–v5) are on the FTP site, together with `accession_ids.csv`, `sequences.fasta` and `diffs.ndjson.gz` [16] ✅.
- Google Cloud Public Datasets access is also offered [18] 🟡.

### 1.5 Coverage rules (why a protein may be missing)
The AFDB FAQ lists these reasons [3] ✅:
- Length outside **16 to 2,700 aa** (proteomes/Swiss-Prot) or **16 to 1,280 aa** (rest of UniProt).
- Non-standard residues (X, O).
- Not in a reference proteome's "one sequence per gene" set.
- Added or changed in a newer UniProt release than AFDB's sync (UniProt **2025_03**, while UniProt itself was at **2026_03** on 2026-10-04 [19] ✅).
- Only human long proteins are fragmented (F1, F2, …).
- Swiss-Prot/proteome entries use the best of 5 models; the rest of UniProt uses a single model ("model_2_ptm") [3] ✅.

---

## 2. (b) AlphaFold Server (AF3), terms as of 2026-10-04

**Access.** Go to https://alphafoldserver.com and sign in with a Google account. Signing up means accepting the non-commercial terms [4][5] ✅.

| Item | Current value | Src |
|---|---|---|
| Daily quota | **30 jobs per day** (saved drafts can be queued). Drafts are capped at 500; up to 100 jobs per uploaded JSON file. | [4] ✅ |
| Job size | **5,000 tokens.** Protein: 1 token per residue. DNA/RNA: 1 per nucleotide. Ligand: 1 per atom. Ion: 1 each. Modified residue: 1 per atom. Glycan: 1 per atom. Each chain needs at least 4 residues. | [4] ✅ |
| Molecule types | Protein, DNA, RNA | [4] ✅ |
| Curated ligands | ATP, ADP, AMP, GTP, GDP, FAD, NADP, NADPH, NDP, heme, heme C, myristic, oleic, palmitic and citric acid, chlorophylls A/B, bacteriochlorophylls A/B | [4] ✅ |
| Any other ligand | Any **CCD code** from the Chemical Component Dictionary (version 2024_10_28), 1–5 alphanumeric characters, up to 50 copies. Example: `STI` for imatinib, `RAP` for rapamycin. **No SMILES; no custom molecules.** | [4] ✅; RAP checked at RCSB [17] ✅ |
| Ions | Ca²⁺, Co²⁺, Cu²⁺, Fe³⁺, K⁺, Mg²⁺, Mn²⁺, Na⁺, Zn²⁺, Cl⁻ | [4] ✅ |
| PTMs | Phosphorylation (S/T/Y/H); Lys acetylation; Lys/Arg methylation; Cys malonylation, palmitoylation and S-nitrosylation; Pro/Lys/Asn hydroxylation; Asn succinylation; Trp formylation; Lys crotonylation; Lys/Arg citrullination | [4] ✅ |
| Glycans | Up to 8 residues, branched trees allowed, built from BGC, BMA, GLC, MAN, NAG, FUC attached to N/S/T (e.g. `NAG(NAG(MAN(MAN(MAN))))`) | [4] ✅ |
| Nucleic-acid modifications | DNA/RNA methylations, pseudouridine and others | [4] ✅ |
| Templates / MSA | The default PDB template cutoff is **30 Sep 2021**. You can change the date, turn templates off, upload up to 4 custom mmCIF templates per chain, or upload a custom paired/unpaired A3M MSA. | [4] ✅ |
| Seeds and samples | 5 diffusion samples per seed. The seed is auto-set or chosen manually (0 to 4,294,967,295). Clone a job to re-run it with a new seed. | [4] ✅ |
| Output | Zip containing all samples (mmCIF), two JSONs per sample (summary metrics and full arrays), templates, MSAs, and `<job>_job_request.json` for re-import | [4] ✅ |
| Not supported | Waters, hydrogens, membrane planes, unknown residues (replace X with A) | [4] ✅ |
| **Terms** (last modified **8 May 2024**) | Only for non-commercial use by individuals and non-commercial organisations, or for journalism. **You must not** use the Server or its outputs (i) in connection with commercial activities, including research on behalf of commercial organisations; (ii) "in any automated system that predicts the binding or interaction of the protein with ligands or peptides, such as Glide or AutoDock"; or (iii) to train ML models for structure prediction. You may publish, share and adapt outputs with notice that ongoing use is subject to the Output Terms. Not for clinical use. Cite Abramson et al. 2024. | [5] ✅ |

**Step by step.**
1. Click **"+ Add entity"** and choose the type: Protein / DNA / RNA / Ligand / Ion / CCD code.
2. Paste the sequence (FASTA headers are allowed) and set **copies**. For example, use 2 copies for a homodimeric receptor.
3. Optionally add PTMs or glycans from the residue menu, and set template or MSA options per chain.
4. Click **"Continue and preview job"**. You can fix the seed here.
5. Submit, then open the result page. It shows the top-ranked sample coloured by pLDDT, plus an interactive PAE plot. **Download** the zip to get all 5 samples and the JSON files.
6. Re-run with new seeds (**"Clone and reuse"**) and rank across all of them. This is especially important for antibody–antigen complexes [4] ✅.

**Batch input.** You can upload JSON jobs; the Server uses its own JSON dialect. Start from the `<job>_job_request.json` file in any results zip and edit it [4] ✅. I did not verify the exact field names for protein chains ❓. The CCD ligand field is `{"ligand": {"ligand": "STI", "count": 1}}` [4] ✅.

**Server vs local AF3.** They use the same weights. However, the Server's sharded Jackhmmer search runs without `--domZ`, which gives an effectively about 100× more permissive filter. As a result, Server MSAs can be deeper than local ones, and a few targets (e.g. one protein–DNA case in GitHub issue #492) score higher on the Server [4] ✅.

**Stale FAQ warning.** As of 2026-10-04 the Server FAQ still says AF3 weights require a request form. Since 23 July 2026, GitHub instead gives a direct download link [4][6] ✅.

---

## 3. (c) ColabFold (free GPUs in Google Colab, or local install)

- ColabFold pairs fast MMseqs2 homology search with AF2 (or RoseTTAFold). The paper reports a **40–60× faster search** and close to 1,000 structures/day on one GPU [14] ✅.
- Current version: **v1.6.3** (MIT licence) [15] ✅. Notebooks available [15] ✅:
  - `AlphaFold2_mmseqs2` (monomers and complexes, templates)
  - `AlphaFold2_batch`
  - **`AlphaFold3 (OpenFold3)`**
  - ESMFold
  - Beta notebooks: RoseTTAFold2, **Boltz**, **BioEmu** (ensembles), OmegaFold
- Practical limits: with a ~16 GB Colab GPU, the maximum total length is about 2,000 aa [15] ✅. The public MSA server is a shared resource; send queries serially from one IP [15] ✅.
- To run locally: `localcolabfold` (Linux, macOS, Windows via WSL2) or `pip install "colabfold[alphafold,openmm]" "jax[cuda12]" "openmm[cuda12]"` ([verifier-corrected] this is the README's command; a bare `pip install colabfold` omits the AlphaFold and JAX/CUDA extras) → `colabfold_batch input.fasta outdir/` [15] ✅. Databases are available at https://colabfold.mmseqs.com [15] ✅.
- Complexes: put the chains on one FASTA line separated by `:` (ColabFold convention 🟡). AF-Multimer weights are used automatically for complexes [15] 🟡.
- Colouring by pLDDT in PyMOL: `spectrum b, red_yellow_green_cyan_blue, minimum=50, maximum=90` [15] ✅.

---

## 4. (d) Running AlphaFold 3 locally

| Item | Value (2026-10-04) | Src |
|---|---|---|
| Code | `github.com/google-deepmind/alphafold3`. **Apache 2.0** since v3.0.3 (9 June 2026); latest release **v3.0.4** (28 July 2026). | [6] ✅ |
| Weights | Direct download `https://storage.googleapis.com/alphafold3/af3.bin.zst` (since 23 July 2026; previously a Google form with a 2–3 business-day review). Governed by the **AF3 Model Parameters Terms**: non-commercial organisations only, no commercial research, no training of similar models on outputs, **do not redistribute the weights**. "You may only use AlphaFold 3 model parameters if received directly from Google." | [6][7] ✅ |
| Watermarked variant | `af3_synthid.bin.zst` (SynthID Bio-structure) | [6] ✅ |
| Commercial | "AlphaFold 3 is available via Gemini Enterprise Agent Platform on Google Cloud". Pricing and allowlist details were not retrieved. | [6] ✅ / details ❓ |
| OS | Linux (instructions for Ubuntu 22.04). CPU-only mode is about 100× slower. Apple Silicon `--jax_backend="mps"` is about 3× faster than CPU. | [8] ✅ |
| GPU | NVIDIA, compute capability ≥8.0. A100 80 GB or H100 80 GB verified for **≤5,120 tokens**. Blackwell GPUs supported since v3.0.2. | [6][8] ✅ |
| RAM / disk | ≥64 GB RAM recommended. Up to **1 TB** of disk, SSD recommended for the databases. | [8] ✅ |
| Genetic databases | About **252 GB** download / **630 GB** unzipped: BFD, MGnify, PDB, UniProt, UniRef90, NT, Rfam, RNACentral. About 45 min to download. | [8] ✅ |
| Container | Docker (host needs CUDA 12.6) or Singularity | [8] ✅ |
| Inputs | JSON (`"dialect": "alphafold3"`). Ligands by CCD code **or SMILES**, plus `userCCD` for custom components. `bondedAtomPairs` for covalent links. `modifications` for PTMs. Custom MSAs and templates. | [20] ✅ |
| Key flags | `--run_data_pipeline` (CPU, genetic search) and `--run_inference` (GPU) can be run separately. Also `--num_seeds`, `--num_recycles`, `--max_template_date`, `--save_distogram`. Embeddings can be output. | [6] ✅ |

Minimal run (from the README) [6] ✅:
```bash
docker run -it \
  --volume $HOME/af_input:/root/af_input --volume $HOME/af_output:/root/af_output \
  --volume <MODEL_PARAMETERS_DIR>:/root/models --volume <DATABASES_DIR>:/root/public_databases \
  --gpus all alphafold3 \
  python run_alphafold.py --json_path=/root/af_input/fold_input.json \
  --model_dir=/root/models --output_dir=/root/af_output
```

---

## 5. (e) Open alternatives you can run without AF3's restrictions

| Tool | Install / run | Input | Licence | Special features | Src |
|---|---|---|---|---|---|
| **Boltz-2** | `pip install boltz[cuda] -U` → `boltz predict input.yaml --use_msa_server` | YAML: `sequences:` → `protein` / `dna` / `rna` / `ligand` (`smiles:` or `ccd:`); `constraints:` (bond, pocket, contact); `templates:`; `properties: - affinity: binder: <ligand chain>` | **MIT**, code and weights, academic and commercial | Affinity for **one small molecule ≤128 atoms** (best ≤56). Outputs `affinity_probability_binary` (binder vs decoy) and `affinity_pred_value` (log10 IC50 in µM). Unreliable for nucleic-acid or co-factor targets. `--use_potentials` improves physical plausibility. | [9][21] ✅ |
| **Chai-1** | `pip install chai_lab==0.6.1` → `chai-lab fold --use-msa-server --use-templates-server input.fasta out/` | FASTA-like: `>protein\|name=…`, `>ligand\|name=…` (SMILES), plus RNA/DNA; modified residues inline, e.g. `AAA(SEP)AAA` | **Apache 2.0, code and weights** | Restraints; runs without MSA. Needs Linux and a bfloat16 CUDA GPU (A100/H100/L40S recommended; RTX 4090 reported to work). | [10][22] ✅ |
| **Protenix v1** (ByteDance) | `pip install protenix` → `protenix pred -i input.json -o out -n protenix_base_default_v1.0.0` | JSON | **Apache 2.0** (v1); **v2 weights proprietary** | Inference-time scaling for antibodies. Web server at protenix-server.com. | [11] ✅ |
| **OpenFold3** (AlQuraishi lab / OpenFold consortium) | `pip install openfold3` → `setup_openfold` | JSON; ColabFold MSA server or JackHMMER | **Apache 2.0** | Default weights "OpenBind-0" (June 2025 data cutoff). Full training data released. | [12] ✅ |
| **RF3 / RFdiffusion3 / ProteinMPNN** (Foundry) | `pip install "rc-foundry[all]"` → `foundry install base-models` | mmCIF/JSON | **BSD-3** | Design (RFD3) plus folding (RF3) in one toolkit. [verifier-corrected] Apple Silicon (MPS) runs only via a community fork, inference-only, float32 | [13] ✅ |
| **ESMFold** | ColabFold notebook or ESM package | Single sequence | Open | Very fast, no MSA; lower accuracy on hard targets | [15][23] ✅ |

---

## 6. (f) How to read the outputs (checklist)

1. **Look at pLDDT first.**
   - >90 is very high and 70–90 is confident.
   - 50–70 is low.
   - Below 50, treat the region as probably disordered and don't interpret its geometry [3][4] ✅.
2. **Look at the PAE plot.** Square low-error blocks along the diagonal are domains. Off-diagonal blocks tell you whether domain or chain *relative positions* are reliable. A domain with high pLDDT but high inter-domain PAE has a "floppy" placement [3][4] ✅.
3. **For complexes, use ipTM and `chain_pair_iptm`.**
   - ipTM >0.8 is confident and <0.6 is likely wrong; 0.6–0.8 is a grey zone.
   - pTM >0.5 means the overall fold is plausible.
   - For a specific interface, use `chain_pair_iptm[i][j]` and `chain_pair_pae_min[i][j]` [4] ✅.
4. **Rank with `ranking_score` across seeds**, but don't treat it as an accuracy estimate [4] ✅.
5. **Red flags:**
   - `has_clash = true`
   - Helices with pLDDT <50 in an IDR (AF3 hallucination)
   - Wrong chirality in ligands; check with RDKit or PoseBusters
   - Very short peptides with pTM ≈0.03 (expected; use PAE instead) [4] ✅
6. **Sanity-check against experiment.** Superpose onto any PDB structure, for example with ChimeraX `matchmaker` or TM-align 🟡 (standard tools, not re-verified). Remember that AF can be confidently wrong in domain orientation or side chains [24] ✅.
7. **Data leakage.** If your complex (or a close homolog) was in the PDB before **30 Sep 2021**, AF3 probably saw it in training [25] ✅.

---

## 7. (g) Worked example: dog IGF-1, GHR and IGF1R (growth-hormone/IGF axis)

**Why this axis?**
- An IGF1 haplotype is a major determinant of small size in dogs [26] ✅.
- A non-coding variant in an IGF1 antisense lncRNA (IGF1-AS) explains part of breed size. IGF1 accounts for about 15% of between-breed size variation [27] ✅.
- Small breeds tend to live longer; see `04_dog_aging_biology/` for the ageing link (not re-verified here).

### Step 1: Find the UniProt accessions
All UniProt queries were run 2026-10-04 against release 2026_03 [19] ✅.

| Protein | Dog (Canis lupus familiaris, taxid 9615) | Human ortholog | Notes |
|---|---|---|---|
| IGF-1 | **P33712** (IGF1_CANLF, Swiss-Prot, 153 aa; mature chain **49–118**) | **P05019** (195 aa; mature 49–118) | Dog has 4 more unreviewed IGF1 entries (isoforms) |
| GH receptor | **Q9TU69** (GHR_CANLF, Swiss-Prot, 638 aa; ECD 19–264, TM 265–288, cytoplasmic 289–638) | **P10912** | |
| Growth hormone | **P33711** (SOMA_CANLF, 216 aa) | **P01241** | |
| IGF-1 receptor | **No Swiss-Prot entry.** Unreviewed: **A0A8I3RQ77** (1,425 aa; Ensembl canonical ENSCAFP00845002510), A0A8I3MER7 (1,344 aa), A0A8I3MMA7 (1,403 aa), all from reference proteome UP000805418 | **P08069** (1,367 aa) | Dog transcripts from Ensembl ROS_Cfam_1.0 [28] ✅ |

### Step 2: Retrieve the precomputed dog models from AlphaFold DB
- `GET /api/prediction/P33712` returns **AF-P33712-F1, v6** (global pLDDT 55.19; 0% of residues "very high") [1] ✅.
- `GET /api/prediction/Q9TU69` returns **AF-Q9TU69-F1, v6** (global pLDDT 59.06) [1] ✅.
- `GET /api/prediction/A0A8I3RQ77` returns `{}`. **There is no model for dog IGF1R**, and A0A8I3MER7 also returns `{}`, as does dog full-length MTOR (A0A8I3MJG3, 2,324 aa). This fits the AFDB rule that unreviewed entries outside Swiss-Prot and the model proteomes are capped at **1,280 aa** [1][3] ✅.

Regional pLDDT, computed from the v6 `confidence_v6.json` files on 2026-10-04 ✅:

| Region | Dog model | Human model |
|---|---|---|
| IGF-1 mature domain (49–118) | **56.3** (AF-P33712-F1) | **68.7** (AF-P05019-F1) |
| GHR extracellular domain (19–264) | 81.5 | 81.2 |
| GHR transmembrane helix (265–288) | 85.3 | – |
| GHR cytoplasmic tail (289–638) | 41.6 (disordered, as expected) | 41.1 |

The mature IGF-1 sequences are *identical*, yet their AFDB confidences differ by about 12 pLDDT points. A plausible but **untested** explanation is that the precursor context (153 vs 195 aa, different E-peptides) and MSA differences affect the prediction ❓. **Lesson: for small, disulfide-rich hormones, model the mature chain, and prefer the experimental structure** (e.g. human IGF-1, PDB 1GZR, 2.0 Å [17] ✅). Because the mature sequence is 100% identical, that structure applies directly to dog IGF-1.

### Step 3: Compare dog to human
Pairwise global alignment (Biopython 1.88, BLOSUM62, gap open −10 / extend −0.5), run 2026-10-04 ✅:

| Pair | Identity |
|---|---|
| IGF-1 mature (49–118) | **70/70 = 100%** |
| IGF-1 precursor (dog 153 vs human 195 aa) | 136/148 aligned = 91.9% (differences are in the E-peptide/propeptide) |
| GHR (638 vs 638 aa) | 525/638 = 82.3% |
| GH1 (216 vs 217 aa) | 147/215 = 68.4% |
| IGF1R mature (dog A0A8I3RQ77 from residue 89 vs human 31–1367) | **1,312/1,337 = 98.1%** |
| TERT (Q6A548 vs O14746), for interest | 819/1,089 = 75.2% |

**Gene-model caveat.** The two dog IGF1R entries differ from human *only* at the N-terminus/signal peptide. A0A8I3RQ77 carries an odd about 60-residue N-terminal extension, and A0A8I3MER7 lacks a normal signal peptide. Both are likely gene-model artefacts ❓. So start the mature dog chain at the conserved motif `…CGPGIDIRND…` (dog residue 89).

The 25 dog/human differences in mature IGF1R fall at these human positions:
- **L1/CR/L2 ligand-binding region:** 31, 32, 191, 218, 263, 286, 407
- **FnIII-1:** 501
- **FnIII-2:** 655, 680
- **FnIII-3:** 743, 746, 759, 760
- **FnIII-4:** 842, 873, 925
- **Linker/juxtamembrane:** 928, 929, 961
- **Kinase domain:** 1098, 1192, 1268
- **Disordered C-tail:** 1287, 1320

The activation-loop autophosphorylation tyrosines (Y1161/Y1165/Y1166) are conserved [19] ✅ (UniProt features of P08069; positions computed). Whether any of these differences touch the IGF-1 contact surface is a **hypothesis to check** in the model; I have not done that analysis ❓.

### Step 4: Model the dog IGF-1:IGF1R complex in AlphaFold Server
The experimental reference is PDB **6PYH**: cryo-EM of full-length IGF1R with IGF-1 at 4.3 Å. It contains **2 receptor chains and 1 IGF-1** (mouse IGF1R, human IGF-1) [17] ✅. **5U8Q** (human IGF1R ectodomain + IGF-I, 3.27 Å) is the other one [17] ✅.

1. **Get the sequences.** The dog mature IGF-1 is exactly:
   `GPETLCGAELVDALQFVCGDRGFYFNKPTGYGSSSRRAPQTGIVDECCFRSCDLRRLEMYCAPLKPAKSA` (70 aa = P33712 residues 49–118) ✅.
   Extract the dog IGF1R ectodomain reproducibly:
   ```python
   import requests
   s = "".join(requests.get("https://rest.uniprot.org/uniprotkb/A0A8I3RQ77.fasta").text.splitlines()[1:])
   start = s.find("GPGIDIRND") - 3                      # -> index 88 = residue 89
   tm = s.find("LIIALPVAVLLIVGGLVIMLYVFH")             # human TM helix, conserved in dog -> residue 994
   ecto = s[start:tm]                                   # dog residues 89-993, 905 aa
   print(len(ecto), ecto[:20])                           # 905 SVCGPGIDIRNDYQQLKRLE
   ```
   This returned 905 aa when run on 2026-10-04 ✅.
   - Option A (ectodomain): ~1,880 tokens = 905 × 2 + 70.
   - Option B (full mature receptor, dog residues 89–1425): 1,337 × 2 + 70 = 2,744 tokens. Both fit the 5,000-token cap.
   - Note: the native receptor is cleaved at RKRR into α and β chains (dog RKRR at residue 795, human 737) [computed ✅]. You may enter α and β as separate chains (4 receptor chains in total) to mimic the mature heterotetramer.
2. **Build the job on AlphaFold Server:**
   - Entity 1: Protein, dog IGF1R ectodomain, **copies = 2**.
   - Entity 2: Protein, dog IGF-1 mature, **copies = 1**.
   - Optional: add N-linked glycans (`NAG`) at sequons; this increases the token count.
3. **Run at least 3–5 seeds** (clone the job). Download all zips.
4. **Read the outputs:**
   - **`chain_pair_iptm`** between the IGF-1 chain and each receptor chain. One receptor protomer should dominate (asymmetric 1:2 binding as in 6PYH) 🟡 (expectation).
   - **ipTM** overall: >0.8 is confident; 0.6–0.8 is a grey zone.
   - **PAE** off-diagonal blocks: low PAE between IGF-1 and the receptor's L1 domain and αCT segment indicates a reliable placement. The αCT location is from the structural literature, not verified here ❓.
   - **Superpose** the result on 5U8Q/6PYH and compute the interface RMSD or DockQ.
5. **Interpret honestly.** Because human IGF-1/IGF1R complexes were in the PDB before the AF3 cutoff, and the dog sequences are ≥98% identical, a high ipTM mostly reflects **memory of known structures**. It is not independent evidence about dog biology. The model is useful for:
   - (i) placing dog-specific substitutions or breed variants on the 3D structure;
   - (ii) generating hypotheses about interface residues to test experimentally;
   - (iii) providing a starting point for designing dog-specific binders.
   It does **not** tell you binding affinity, signalling strength or ageing effects.
6. **For affinity of small molecules** (e.g. a candidate IGF1R kinase inhibitor), use **Boltz-2** with `properties: affinity`. AF3 does not predict affinity, and **Server outputs cannot be fed to docking/screening tools** under its terms [5][9] ✅.

### Step 5: Same recipe for dog GH:GHR
Use the same recipe with dog GH (P33711 minus its signal peptide; check UniProt features) × 1 and dog GHR ECD (Q9TU69 residues 19–264) × 2. The reference structure is the classic 1:2 human complex **3HHR** [17] ✅. Dog GH is only 68% identical to human GH, so this is a less trivially "memorised" case. Still, treat it as a hypothesis generator.

### Equivalent local or commercial-friendly input (Boltz-2 YAML) [21] ✅
```yaml
version: 1
sequences:
  - protein:
      id: [A, B]
      sequence: <dog IGF1R residues 89-993>
  - protein:
      id: C
      sequence: GPETLCGAELVDALQFVCGDRGFYFNKPTGYGSSSRRAPQTGIVDECCFRSCDLRRLEMYCAPLKPAKSA
```
Run with: `boltz predict dog_igf1r.yaml --use_msa_server --use_potentials`

### Equivalent local AF3 JSON [6] ✅
```json
{
  "name": "dog_IGF1R_ecto_IGF1",
  "sequences": [
    {"protein": {"id": ["A", "B"], "sequence": "<dog IGF1R residues 89-993>"}},
    {"protein": {"id": ["C"], "sequence": "GPETLCGAELVDALQFVCGDRGFYFNKPTGYGSSSRRAPQTGIVDECCFRSCDLRRLEMYCAPLKPAKSA"}}
  ],
  "modelSeeds": [1, 2, 3, 4, 5],
  "dialect": "alphafold3",
  "version": 1
}
```

---

## Open questions / gaps

- I did **not** actually run AF Server, AF3, Boltz-2 or Chai-1 jobs, so the outcome of the worked example (ipTM values etc.) is unknown. Running it is the obvious next step.
- The exact AF Server JSON field names for protein chains were not verified ❓. The official example linked from the FAQ should be used.
- Google Cloud commercial AF3: price, quotas and allowlist were not retrieved ❓.
- Why do dog and human AFDB models of the identical mature IGF-1 differ in pLDDT? Not investigated ❓.
- The dog IGF1R gene models (N-termini) look partly artefactual. A curated dog IGF1R sequence (e.g. from RefSeq/NCBI or cDNA) should be checked before serious modelling ❓.

---

## Sources

1. AlphaFold DB API (OpenAPI spec at https://alphafold.ebi.ac.uk/api/openapi.json). Live calls on 2026-10-04 to `/api/prediction/{P33712, Q9TU69, P08069, P05019, P10912, A0A8I3RQ77, A0A8I3MER7}`, `/api/complex/{Q9TU69, P10912}`, `/api/annotations/{P05019, P33712}.json` and `/api/uniprot/summary/P33712.json`, plus `confidence_v6.json` files.
2. PDBe/EMBL-EBI. AlphaFold Database release notes (v6), 21 Oct 2025. https://www.ebi.ac.uk/pdbe/news/alphafold-database-release-notes
3. AlphaFold DB homepage and FAQ ("Which proteins are included?", coverage rules, PAE format, dataset descriptions). https://alphafold.ebi.ac.uk/faq (accessed 2026-10-04)
4. AlphaFold Server FAQ. https://alphafoldserver.com/faq (accessed 2026-10-04 via browser)
5. AlphaFold Server Additional Terms of Service, Last Modified 8 May 2024. https://alphafoldserver.com/terms (accessed 2026-10-04)
6. google-deepmind/alphafold3 GitHub: README, releases v3.0.0 (2024-11-11) to v3.0.4 (2026-07-28), commit history. https://github.com/google-deepmind/alphafold3
7. AlphaFold 3 Model Parameters Terms of Use (Last Modified 2024-11-09). https://github.com/google-deepmind/alphafold3/blob/main/WEIGHTS_TERMS_OF_USE.md
8. AlphaFold 3 installation documentation. https://github.com/google-deepmind/alphafold3/blob/main/docs/installation.md
9. jwohlwend/boltz README (MIT). https://github.com/jwohlwend/boltz ; Passaro S et al. (2025) Boltz-2, bioRxiv doi:10.1101/2025.06.14.659707
10. chaidiscovery/chai-lab README (Apache 2.0 code and weights) and `examples/predict_structure.py`. https://github.com/chaidiscovery/chai-lab
11. bytedance/Protenix README. https://github.com/bytedance/Protenix
12. aqlaboratory/openfold-3 README. https://github.com/aqlaboratory/openfold-3
13. RosettaCommons/foundry README. https://github.com/RosettaCommons/foundry
14. Mirdita M et al. (2022). ColabFold: making protein folding accessible to all. *Nat Methods* 19:679–682. doi:10.1038/s41592-022-01488-1
15. sokrypton/ColabFold README v1.6.3. https://github.com/sokrypton/ColabFold (accessed 2026-10-04)
16. AlphaFold DB FTP listing. https://ftp.ebi.ac.uk/pub/databases/alphafold/latest/ and CHANGELOG.txt (accessed 2026-10-04)
17. RCSB PDB entry metadata (data.rcsb.org REST, 2026-10-04): 5U8Q, 6PYH (entities: IGF1R ×2 chains, IGF-1 ×1 chain), 1GZR, 3HHR; chemical component RAP (rapamycin).
18. Varadi M et al. (2024). AlphaFold Protein Structure Database in 2024. *Nucleic Acids Res* 52:D368–D375. doi:10.1093/nar/gkad1011 (abstract mentions Google Cloud Public Datasets access)
19. UniProt REST API (release 2026_03, 2 Sep 2026). Queries run 2026-10-04: entries P33712, Q9TU69, P33711, P05019, P08069, P10912, P01241, A0A8I3RQ77, A0A8I3MER7, A0A8I3MMA7, A0A8I3MJG3, Q6A548, O14746; P08069 feature table. https://rest.uniprot.org
20. AlphaFold 3 input documentation. https://github.com/google-deepmind/alphafold3/blob/main/docs/input.md
21. Boltz prediction documentation (YAML schema, affinity rules). https://github.com/jwohlwend/boltz/blob/main/docs/prediction.md
22. Chai Discovery et al. (2024). Chai-1. bioRxiv doi:10.1101/2024.10.10.615955
23. Lin Z et al. (2023). ESMFold. *Science* 379:1123–1130. doi:10.1126/science.ade2574
24. Terwilliger TC et al. (2024). AlphaFold predictions are valuable hypotheses… *Nat Methods* 21:110–116. doi:10.1038/s41592-023-02087-4
25. Abramson J et al. (2024). AlphaFold 3. *Nature* 630:493–500. doi:10.1038/s41586-024-07487-w
26. Sutter NB et al. (2007). A single IGF1 allele is a major determinant of small size in dogs. *Science* 316:112–115. doi:10.1126/science.1137045
27. Plassais J et al. (2022). Natural and human-driven selection of a single non-coding body size variant in ancient and modern canids. *Curr Biol* 32(4):889–897.e9. doi:10.1016/j.cub.2021.12.036
28. Ensembl REST API (2026-10-04): `lookup/symbol/canis_lupus_familiaris/IGF1R` (canonical transcript ENSCAFT00845003151 → protein ENSCAFP00845002510, 1,425 aa; assembly ROS_Cfam_1.0). https://rest.ensembl.org

---

## Verification notes

*Independent check by Fable 5.1, 2026-10-04. Full report: `../07_verification/alphafold_verification.md`.*

- **Live endpoints re-tested** (all on 2026-10-04): `/api/prediction/{P05019, P33712, Q9TU69, P08069, A0A8I3RQ77, A0A8I3MER7, A0A8I3MMA7, A0A8I3MJG3, Q8WNN6 + 10 more}`, `/api/complex/{Q9TU69, P33712, P10912}`, `/api/uniprot/summary/P33712.json`, `/api/annotations/{P05019, P33712}.json?type=MUTAGEN`, `/api/openapi.json` (lists exactly the five paths in §1.2), the v6 `confidence` and `predicted_aligned_error` JSON files (max PAE 31.75), the FTP `latest/` listing (46 proteome tarballs + 2 Swiss-Prot tarballs, no dog), UniProt REST (release 2026_03; all 16 count queries reproduced exactly), Ensembl lookup and VEP (SIFT returned, no PolyPhen), RCSB (5U8Q, 6PYH, 3HHR, 1GZR, RAP). All matched the text except the AFDB `msaUrl`, which returns HTTP 403 to direct download.
- **Re-computed from UniProt sequences** (Biopython 1.88, BLOSUM62, −10/−0.5, global): mature IGF-1 70/70 identical; precursor 136/148; GHR 525/638; GH1 147/215; TERT 819/1,089; IGF1R mature 1,312/1,337 with the same 25 difference positions and conserved Y1161/Y1165/Y1166; mTOR FRB 100/100 (the human 2015–2114 segment occurs verbatim in dog A0A8I3MJG3 at 1790–1889); FKBP1A 91/92 with the 16-residue gap at human 13–28. The `GPGIDIRND` motif, TM start (dog 994), 905-aa ectodomain and RKRR positions (795/737) all reproduce. Regional pLDDT means (56.3/68.7; 81.5/81.2/85.3/41.6/41.1) reproduce from the v6 confidence files.
- **AlphaFold Server FAQ and Terms** were read in a browser: every quota, token, ligand, ion, PTM, glycan, template, seed, output and terms statement in §2 matches, including the stale "request form" sentence, the `--domZ` explanation and issue #492. Terms "Last Modified: May 8, 2024" confirmed.
- **AF3 docs**: installation.md and input.md support every value in §4 (Linux only; CC ≥ 8.0; 5,120 tokens on A100/H100 80 GB; 64 GB RAM; 1 TB; 252/630 GB; CUDA 12.6; CPU ~100× slower; `mps` ~3× faster than CPU; `dialect: alphafold3`, versions 1–4; `ccdCodes`/`smiles`/`userCCD`/`bondedAtomPairs`/`modifications`). Release dates and commits confirmed via the GitHub API.
- **Open alternatives**: Chai-1 Apache 2.0 (code and weights), Boltz MIT, OpenFold3 Apache 2.0 (OpenBind-0, June 2025 cutoff), Protenix v1 Apache 2.0 / v2 weights proprietary, Foundry BSD-3, ColabFold v1.6.3 MIT — all confirmed from the repositories; the `chai-lab fold`, `protenix pred`, `setup_openfold` and Boltz affinity details match the docs.
- **Corrected in place** (`[verifier-corrected]`): the entry-URL claim in §1.1 (the old `/entry/<ACCESSION>` form still resolves); the `msaUrl` download status (§1.2, §1.3); the ColabFold pip command (§3); Foundry's Apple Silicon support (community fork only, §5).
- **Still open:** whether the entry page itself serves the MSA file; the exact AF Server JSON schema for protein chains (not re-verified here either); Google Cloud AF3 pricing.
