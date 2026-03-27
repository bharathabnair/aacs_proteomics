# Proteomics workflow for quality control and post-processing of secretome of acid-adapted breast cancer cells

This repository contains Jupyter notebooks used to perform quality control and subcellular localization analysis for a proteomics study comparing control cells with acid-adapted cells.

## Repository purpose
The files are structured to support:
- transparent re-use of the analysis workflow,
- straightforward execution after cloning from GitHub,
- archival deposition in Zenodo with clear input/output provenance.

## Included notebooks
### `quality_control.ipynb`
Quality-control workflow for the quantitative proteomics matrix.

Main steps:
1. Load the processed OmicsQ quantitative matrix.
2. Detect control (`C_*`) and acid-adapted (`AA_*`) sample columns.
3. Optionally apply log2 transformation.
4. Generate:
   - PCA plots,
   - pairwise sample correlation heatmap,
   - per-sample intensity boxplots.
5. Save figures to `analysis_outputs/figures/`.

## Expected data layout
Place input data under a top-level `data/` directory.

Recommended structure:

```text
├── data/
│   ├── OmicsQ/
│   │   └── OmicsQResults.csv
├── quality_control.ipynb
└── analysis_outputs/
    ├── figures/
```

## Dataset description
The workflow expects processed quantitative proteomics tables exported from OmicsQ/DIA analysis.

### QC dataset
The QC notebook uses a processed intensity matrix in CSV format, where:
- rows represent protein features,
- columns represent samples,
- control replicates are named with the prefix `C_`,
- acid-adapted replicates are named with the prefix `AA_`.

Because file naming can differ between exports, the notebooks define `DATA_PATH` explicitly near the top. Update those paths if your archived filenames differ.

## Software environment
The notebooks are written for Python 3 and use common scientific Python packages:
- pandas
- numpy
- matplotlib
- scipy
- scikit-learn
- jupyter

A minimal environment can be installed with:

```bash
pip install pandas numpy matplotlib scipy scikit-learn notebook
```

## Reproducibility guidance
- Run each notebook from top to bottom in a fresh kernel.
- Keep the input filenames and folder structure consistent with the paths declared in the first code cell of each notebook.
- Review the sample grouping logic before rerunning on a renamed export.
- Generated outputs are written to relative repository paths so that the workflow remains portable across computers and archival systems.

## Citation and reuse
Please cite the associated manuscript and Zenodo repository (https://doi.org/10.5281/zenodo.19252198) when reusing this workflow.
