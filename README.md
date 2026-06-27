
# Protein & Ligand Visualization using py3Dmol

A short, reproducible Jupyter notebook demonstrating 3D molecular visualization of a small-molecule ligand and a protein target directly from public structural databases (PubChem and RCSB PDB), using [py3Dmol](https://github.com/3dmol/3Dmol.js).

## Overview

<img align="right" width="300" height="300" alt=" protein Animation" src="https://structuralbioinformatician.wordpress.com/wp-content/uploads/2013/03/1ece.gif" />

This notebook covers two visualization tasks:

1. **Ligand visualization** — Nirmatrelvir (Paxlovid), the SARS-CoV-2 main protease (Mᵖʳᵒ) inhibitor, fetched by PubChem CID and rendered as a stick model with spectrum coloring, with and without a Van der Waals surface overlay.
2. **Protein visualization** — SARS-CoV-2 main protease (Mᵖʳᵒ), PDB ID [`7RFS`](https://www.rcsb.org/structure/7RFS), rendered as a cartoon structure with spectrum coloring, with and without a transparent surface overlay.

The goal is to show the same structure at two levels of resolution — atom-level detail (sticks) and fold-level overview (cartoon) — and how adding a molecular surface changes what information is visible (shape/volume vs. backbone topology).

## What's inside

| Cell | Content |
|---|---|
| 1 | Install `py3Dmol` |
| 2–3 | Nirmatrelvir — stick representation, spectrum-colored |
| 4 | Nirmatrelvir — stick representation + VDW surface (opacity 0.5, red-white-blue gradient) |
| 5 | Mᵖʳᵒ (PDB 7RFS) — cartoon representation, spectrum-colored |
| 6 | Mᵖʳᵒ (PDB 7RFS) — cartoon representation + VDW surface (opacity 0.1, red-white-blue gradient) |

## Requirements

- Python 3.8+
- Jupyter Notebook / JupyterLab
- `py3Dmol`

```bash
pip install py3Dmol notebook
```

## Usage

```bash
git clone https://github.com/kush021104/protein-visulaisation-using-py3dmol.git
cd protein-visulaisation-using-py3dmol
jupyter notebook
```

Open the notebook and run all cells. Structures are fetched live from PubChem and RCSB PDB, so an internet connection is required — no local structure files are needed.

## Data sources

- **Nirmatrelvir**: [PubChem CID 155903259](https://pubchem.ncbi.nlm.nih.gov/compound/155903259)
- **SARS-CoV-2 Mᵖʳᵒ**: [RCSB PDB 7RFS](https://www.rcsb.org/structure/7RFS)

## Notes

- `query='cid:<id>'` and `query='pdb:<id>'` pull structures directly via py3Dmol's built-in fetchers — no manual download/parsing step required.
- Surface opacity is deliberately different between the ligand (0.5) and protein (0.1) views: a denser surface is legible on a small molecule, while a fold-level structure needs a near-transparent surface so the cartoon backbone remains visible underneath.
