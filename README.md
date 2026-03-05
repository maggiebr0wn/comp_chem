# Cheminformatics for Bioinformaticians 🧬🔬

A self-study notebook series for computational biologists transitioning into cheminformatics and drug discovery data science. Covers the core tools and data formats used in modern computational drug discovery — RDKit, SMILES, SDF files, molecular descriptors, fingerprints, and ML modeling on chemical data.

---

## Who this is for

If you already know Python, pandas, and scikit-learn from a bioinformatics or genomics background, this series gets you up to speed on the **chemistry-specific** layer: how molecular data is structured, how to featurize it, and how to build and validate predictive models on it.

---

## Notebooks

| # | Notebook | Topics | Dataset |
|---|----------|--------|---------|
| 1 | `01_smiles_and_rdkit.ipynb` | SMILES syntax, RDKit basics, molecular descriptors, Lipinski's Rule of Five | ESOL (solubility) |
| 2 | `02_sdf_files.ipynb` | SDF file format, reading/writing with RDKit and pandas, handling multi-molecule files | BACE (BACE-1 inhibitors) |
| 3 | `03_pandas_for_cheminformatics.ipynb` | Pandas workflows with chemical data: filtering, groupby, merging, cleaning | ESOL + Lipophilicity |
| 4 | `04_feature_engineering.ipynb` | Morgan fingerprints, RDKit descriptor matrix, feature selection | Lipophilicity |
| 5 | `05_ml_models_and_validation.ipynb` | Regression, classification, cross-validation, scaffold splits, statistical rigor | ESOL + BBBP |

---

## Datasets

All datasets come from [MoleculeNet](http://moleculenet.ai/) via the [Molecules Dataset Collection](https://github.com/GLambard/Molecules_Dataset_Collection) by G. Lambard.

| Dataset | Task | Size | Description |
|---------|------|------|-------------|
| **ESOL** | Regression | ~1,100 | Water solubility (log mol/L) |
| **Lipophilicity** | Regression | ~4,200 | LogD at pH 7.4 (octanol/water distribution) |
| **FreeSolv** | Regression | ~640 | Hydration free energy |
| **BACE** | Regression + Classification | ~1,500 | BACE-1 inhibitor binding (IC50) |
| **BBBP** | Classification | ~2,050 | Blood-brain barrier permeability |

---

## Setup

### 1. Clone this repo

```bash
git clone https://github.com/YOUR_USERNAME/chem-learning.git
cd chem-learning
```

### 2. Create the conda environment

> ⚠️ **Important:** Always install `rdkit` via `conda-forge`, not `pip`. The pip version can have broken C++ dependencies on some systems.

```bash
conda env create -f environment.yml
```

This will create an environment called `chem-learning` with all required packages.

### 3. Activate the environment

```bash
conda activate chem-learning
```

### 4. Register the environment as a Jupyter kernel

This makes the `chem-learning` environment appear in the JupyterLab kernel selector:

```bash
python -m ipykernel install --user --name chem-learning --display-name "Python (chem-learning)"
```

### 5. Launch JupyterLab

```bash
jupyter lab
```

---

## Updating the environment

If you add new packages later:

```bash
# Add the package to environment.yml first, then:
conda env update -f environment.yml --prune
```

---

## Key libraries

| Library | Purpose | Docs |
|---------|---------|------|
| [RDKit](https://www.rdkit.org/) | Molecule parsing, drawing, descriptor calculation | [rdkit.org/docs](https://www.rdkit.org/docs/) |
| [pandas](https://pandas.pydata.org/) | Tabular data handling | [pandas.pydata.org](https://pandas.pydata.org/docs/) |
| [scikit-learn](https://scikit-learn.org/) | Machine learning models and validation | [scikit-learn.org](https://scikit-learn.org/stable/) |
| [matplotlib](https://matplotlib.org/) / [seaborn](https://seaborn.pydata.org/) | Visualization | — |

---

## Concepts covered

- **SMILES** — text representation of molecular structures
- **SDF files** — multi-molecule file format with associated data
- **Molecular descriptors** — numerical properties computed from structure (MW, LogP, TPSA, etc.)
- **Morgan fingerprints** — bit-vector representations of molecular topology for ML
- **Lipinski's Rule of Five** — classic druglikeness filter
- **Scaffold splits** — chemistry-aware train/test splitting to avoid data leakage
- **ADME properties** — Absorption, Distribution, Metabolism, Excretion — the key pharmacokinetic endpoints

---

## References

- Landrum, G. RDKit: Open-source cheminformatics. https://www.rdkit.org
- Wu, Z. et al. MoleculeNet: A Benchmark for Molecular Machine Learning. *arXiv:1703.00564* (2017)
- Delaney, J. S. ESOL: Estimating Aqueous Solubility Directly from Molecular Structure. *J. Chem. Inf. Comput. Sci.* 44, 1000–1005 (2004)
- Lipinski, C. A. et al. Experimental and computational approaches to estimate solubility and permeability in drug discovery. *Adv. Drug Deliv. Rev.* 23, 3–25 (1997)
