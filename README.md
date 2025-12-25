# Quality Assessment of Ab-Ag Complex Predictions

This project evaluates protein complex predictions from **AlphaFold2 (AF2)**, **Boltz-1**, **Chai-1**, and **Protenix** by calculating **DockQ** scores (using native references) and **pDockQ2** confidence scores.

**Based on original script by Elofsson Lab:**  
https://gitlab.com/ElofssonLab/afm-benchmark/-/blob/main/src/pdockq2.py

## Installation

### Prerequisites
```bash
pip install -r requirements.txt
```

### Install DockQ

This tool requires the DockQ library:
```bash
pip install DockQ
```

## Directory Structure

Organize your prediction folders as follows:
```
project/
├── analysis_notebook.ipynb
├── requirements.txt
├── data/
│   └── metadata_200Ab-Ag_complex_rev.csv
│
├── original_pdbs/              # Native PDB reference files
│   ├── 7ar0.pdb
│   ├── 7bnv.pdb
│   └── ...
│
├── af2/                        # AlphaFold2 predictions
│   ├── 7ar0_B_A_af2/
│   │   ├── *_unrelaxed_rank_00*.pdb
│   │   ├── *_scores_rank_00*.json
│   │   └── log.txt
│   ├── 7bnv_H_L_A_af2/
│   │   └── ...
│   └── ...
│
├── boltz1/                     # Boltz-1 predictions
│   ├── 7ar0_B_A_boltz1/
│   │   └── predictions/
│   │       └── result/
│   │           ├── model_0.pdb
│   │           └── ...
│   ├── 7bnv_H_L_A_boltz1/
│   │   └── ...
│   └── ...
│
├── chai/                       # Chai-1 predictions
│   ├── 7ar0_B_A_chai/
│   │   ├── pred.model_idx_0.pdb
│   │   └── ...
│   ├── 7bnv_H_L_A_chai/
│   │   └── ...
│   └── ...
│
├── protenix/                   # Protenix predictions
│   ├── 7ar0_B_A_px/
│   │   └── 7ar0_B_A_px/
│   │       └── seed1/
│   │           └── predictions/
│   │               ├── sample_0.pdb
│   │               └── ...
│   ├── 7bnv_H_L_A_px/
│   │   └── ...
│   └── ...
│
└── results/                    # Output CSVs (generated)
    ├── *_dockq_scores.csv
    ├── *_pdockq2_fit.csv
    └── *_combined.csv
```

## Usage

1. **Prepare your data:**
   - Place native PDB structures in `original_pdbs/`
   - Organize predictions in their respective folders (`af2/`, `boltz1/`, `chai/`, `protenix/`)

2. **Run analysis:**
   - Open the appropriate Jupyter Notebook in `scripts/`
   - Update `complex_list` or folder paths in the first cell
   - Run all cells to process predictions

3. **Access results:**
   - Output CSV files will be saved in `results/`

## Output Files

| File | Description |
|------|-------------|
| `*_dockq_scores.csv` | DockQ, fnat, iRMSD, LRMSD scores |
| `*_pdockq2_fit.csv` | Interface pLDDT, iPAE, and pDockQ2 scores |
| `*_combined.csv` | Summary including pTM, ipTM, and other metrics |

## Citation

If you use this code, please cite DockQ, pDockQ and AntiConf publications: 
```
@article{Basu2016DockQ,
  title     = {DockQ: A Quality Measure for Protein-Protein Docking Models},
  author    = {Basu, Sankar and Wallner, Bj{\"o}rn},
  journal   = {PLOS ONE},
  volume    = {11},
  number    = {8},
  pages     = {e0161879},
  year      = {2016},
  doi       = {10.1371/journal.pone.0161879},
}
```
```
@article{Zhu2023pDockQ2,
  title     = {Evaluation of {AlphaFold-Multimer} prediction on multi-chain protein complexes},
  author    = {Zhu, Wensi and Shenoy, Aditi and Kundrotas, Petras and Elofsson, Arne},
  journal   = {Bioinformatics},
  volume    = {39},
  number    = {7},
  pages     = {btad424},
  year      = {2023},
  doi       = {10.1093/bioinformatics/btad424},
}
```
```
@article {Unsal2025AntiConf,
	title = {Confidence Scoring for AI-Predicted Antibody{\textendash}Antigen Complexes: AntiConf as a Precision-driven Metric},
   author = {Unsal, Serbulent and Holland, Benjamin and Sardag, Inci and Timucin, Emel},
	year = {2025},
	doi = {10.1101/2025.07.25.666870},
   journal = {bioRxiv}	
}
```
