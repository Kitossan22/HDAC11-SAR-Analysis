# HDAC11 Inhibitor SAR Analysis
### Cheminformatics pipeline for structure-activity relationship analysis using RDKit, pandas, and ChEMBL

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![RDKit](https://img.shields.io/badge/RDKit-2023+-green.svg)](https://www.rdkit.org/)
[![ChEMBL](https://img.shields.io/badge/ChEMBL-v33-orange.svg)](https://www.ebi.ac.uk/chembl/)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Kitossan22/HDAC11-SAR-Analysis/blob/main/HDAC.ipynb)

---

## Overview

This project presents a complete cheminformatics SAR analysis of two HDAC11 inhibitor 
series developed at the University of Copenhagen:

- **Series D** — Bis-aryl sulfate scaffold (12 compounds), Tobias N. Hansen et al., *JACS Au* 2024
- **EVB Sulfamate series** — Sulfamate ZBG with benzylamine cap (5 compounds), from 
Balatsos, E. MSc Thesis, KU 2025 (supervised by Christian A. Olsen and co-supervised by Marcos San Segundo Eizaguirre)

**Key question:** Do the same physicochemical trends drive HDAC11 potency across two 
structurally distinct scaffolds sharing the same zinc-binding group strategy?

---

## Background

HDAC11 is the sole member of class IV histone deacetylases and an emerging therapeutic 
target in oncology and immunology. Unlike class I/II HDACs, HDAC11 shows both 
deacetylase and defatty-acylase activity, making selective inhibition particularly 
valuable for dissecting its biology.

Both series studied here use a **substrate-inspired ZBG strategy**: using the 
classical hydroxamate with either an aryl sulfate (Series D) or sulfamate (EVB), 
aiming for improved selectivity over pan-HDAC inhibition.

---

## Notebook Structure

| Section | Description |
|---|---|
| 1. Series D data | SMILES parsing, descriptor calculation, activity tiering |
| 2. Series D molecules | 2D structure grid with Ki labels |
| 3. EVB Sulfamate data | SMILES parsing, descriptor calculation, activity tiering |
| 4. EVB molecules | 2D structure grid with Ki and cap group labels |
| 5. SAR descriptor plots | MW, LogP, TPSA, RotBonds vs Ki (log scale) — both series |
| 6. Molecular fingerprints | Morgan/ECFP4 fingerprints, Tanimoto similarity heatmaps |
| 7. Drug-likeness filters | Lipinski Ro5, Veber rules, PAINS filter |
| 8. ChEMBL landscape | 713 HDAC11 inhibitors fetched via API, scaffold clustering, chemical space plot |

---

## Key Findings

- **EVB-30** (N-methyl sulfamate, Ki = 68 nM) is the most potent compound across both 
series and sits in the top 15% of all ChEMBL HDAC11 inhibitors by potency
- **Series D lead D21** (Ki = 149 nM) and **D3** (Ki = 187 nM) achieve sub-200 nM 
potency with favorable drug-like properties (MW ~380 Da, LogP ~3)
- Cross-series Tanimoto similarity (0.42–0.68) confirms both scaffolds occupy distinct 
chemical space while converging on similar potency — suggesting a shared pharmacophoric 
model
- All potent compounds pass Lipinski Ro5 and Veber rules; PAINS flags are expected for 
hydroxamate-containing compounds due to metal chelation (intentional ZBG mechanism)
- ChEMBL scaffold analysis reveals 302 unique scaffolds among 713 HDAC11 inhibitors, 
with high-MW outliers (>800 Da) consistent with cyclic peptide natural products and PROTACs

---

## Technologies

| Tool | Use |
|---|---|
| RDKit | SMILES parsing, descriptor calculation, fingerprints, PAINS filter |
| pandas | Data manipulation and analysis |
| matplotlib / seaborn | Visualization |
| ChEMBL API | Public bioactivity database query (713 HDAC11 inhibitors) |
| Google Colab | Notebook environment |

---

## How to Run

Click the **Open in Colab** badge above — no local installation needed.

All dependencies are installed within the notebook:
```bash
pip install rdkit chembl_webresource_client
```

Run cells sequentially from top to bottom. ChEMBL data is fetched live via API 
(requires internet connection). If the ChEMBL server is temporarily unavailable, 
re-run the fetch cell after a few minutes.

---

## References

1. Tobias N. Hansen et al. *JACS Au* 2024. DOI: 10.1021/jacsau.4c00042
2. Balatsos, E. MSc Thesis, University of Copenhagen, 2025
3. Wishart, D. et al. ChEMBL: a large-scale bioactivity database for drug discovery. 
*Nucleic Acids Res.* 2012, 40, D1100–D1107

---

## Author

**Marcos San Segundo Eizaguirre, PhD**  
Postdoctoral Researcher — Chemical Biology & Drug Discovery  
University of Copenhagen (Olsen Group)  
[ORCID: 0000-0002-0149-5485](https://orcid.org/0000-0002-0149-5485)  
[GitHub: Kitossan22](https://github.com/Kitossan22)
