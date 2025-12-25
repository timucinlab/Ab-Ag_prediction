# Quality Assessment of Ab-Ag Complex Predictions by AF2, Boltz-1, Chai-1 and Protenix 

This project evaluates protein complex predictions from AlphaFold2 (AF2) by calculating **DockQ** scores (using native references) and **pDockQ2** confidence scores.

Based on original script by Elofsson Lab
https://gitlab.com/ElofssonLab/afm-benchmark/-/blob/main/src/pdockq2.py

## Setup

1. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   
2. **Install DockQ: This tool requires the DockQ library.**

**Directory Structure for AF2**
Ensure your folders are organized as follows:

├── analysis_notebook.ipynb
├── requirements.txt
├── original_pdbs/               # Place native PDB files here (e.g., 7ar0.pdb)
├── af2/                         # Place AlphaFold prediction folders here
│   ├── 7ar0_B_A_af2/
│   │   ├── *_unrelaxed_rank_00*.pdb
│   │   ├── *_scores_rank_00*.json
│   │   └── log.txt
│   └── ...
└── result/                      # Output CSVs will appear here

boltz1 				 # Place Boltz prediction folders here
├── 7ar0_B_A_boltz1
│   ├── predictions
│       ├── result
│           ├── xxx.pdb
│           ├── ...
├── 7bnv_H_L_A_af2
│   ├── predictions
│       ├── result
│           ├── ...

chai				# Place chai-1 prediction folders here
├── 7ar0_B_A_chai
│   ├── xxx.pdb
│   ├── ...
├── 7bnv_H_L_A_chai
│   ├── xxx.pdb
│   ├── ...

protenix		        # Place Protenix prediction folders here
├── 7ar0_B_A_px
│   ├── 7ar0_B_A_px
│       ├── seed1
│           ├── predictions
│               ├── .pdb
│               ├── ...
├── 7bnv_H_L_A_px
│   ├── 7bnv_H_L_A_px
│       ├── seed1
│           ├── predictions
│               ├── .pdb
│               ├── ...

Usage
    Open the Jupyter Notebook.
    Update the complex_list or folder paths in the first cell if needed.
    Run all cells to process the predictions.

Outputs
    *_dockq_fnat_scores.csv: fnat, iRMSD, lRMSD and DockQ scores
    *_pdockq2_fit.csv: iplddt, iPAE and pDockQ2
    *_combined.csv: Summary of all metrics including pTM, ipTM and AntiConf
