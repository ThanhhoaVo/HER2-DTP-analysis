# Integrative analysis of drug-tolerant persister (DTP) states in HER2-positive breast cancer

Code accompanying the manuscript. All analyses are consolidated in a single, sectioned notebook:
**`DTP_master_analysis.ipynb`**.

## Sections and figures

| Section | Analysis | Figure(s) |
|---|---|---|
| 1 | scRNA-seq DTP discovery and signature derivation | Fig 1 |
| 2 | Pathway enrichment (GSEA) and module scoring | Figs 2–4 |
| 3 | Clinical survival analysis + proportional-hazards test | Fig 5 |
| 4 | Perturbational (LINCS/iLINCS) drug repurposing | Fig 6 |
| 5 | Spatial transcriptomics + patient-level sensitivity | Fig 7 |

## Data availability (public)

| Dataset | Accession / source |
|---|---|
| Single-cell RNA-seq (BT474, HCC1419) | GEO **GSE156246** (Chang et al., 2022) |
| Spatial transcriptomics (HER2+) | **Zenodo 4751624** / GitHub `almaan/her2st` (Andersson et al., 2021) |
| METABRIC clinical + expression | cBioPortal study `brca_metabric` |
| TCGA breast cohort | cBioPortal / curatedTCGAData |
| Perturbational signatures | iLINCS platform (`findConcordancesSC`) |

Sections 3 and 5 fetch their data automatically. Section 1 downloads GSE156246. Place the signature files
`shared_list_day2.csv`, `bt_list_day2.csv`, `hcc_list_day2.csv` in the working directory for Sections 3–5
(or generate them in Section 1, which writes them to `outputs/signatures/`).

## Running

```bash
pip install -r requirements.txt
jupyter notebook DTP_master_analysis.ipynb   # or open in Google Colab
```

Run section by section. Key parameters are set inline in each section and summarised in the notebook's
reproducibility notes. Outputs (figures, signatures, tables) are written to `outputs/`.

## Software

See `requirements.txt`. Core: scanpy 1.12.1, gseapy, lifelines, statsmodels, squidpy; iLINCS, Enrichr (GO BP),
and ChEMBL are accessed via their public APIs.
