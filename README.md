# RDKit-molecule-editor
A lightweight RDKit-based toolkit for interactively editing molecular structures. This tool provides an intuitive workflow for renumbering atoms, selecting molecular fragments, and extracting substructures while preserving the original molecule.

---

## Features

- 📂 Load molecules from SDF files
- 🔢 Renumber atom indices using graph-based Breadth-First Search (BFS)
- 👀 Visualize atom indices in Jupyter Notebook
- ✂️ Select arbitrary atoms interactively
- 🧩 Extract molecular fragments
- 🔒 Preserve the original molecule throughout the editing process
- ✅ Validate extracted fragments using RDKit sanitization

---

## Motivation

Atom indices in SDF files are often assigned arbitrarily, making manual fragment selection cumbersome and error-prone.

This toolkit simplifies the process by providing:

- Connectivity-based atom renumbering
- Interactive atom index visualization
- Easy extraction of pharmacophores or molecular fragments

It is particularly useful for medicinal chemistry, pharmacophore modeling, fragment-based drug design, and molecular preprocessing workflows.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/<your_username>/MolFragmenter.git
cd MolFragmenter
```

Install RDKit using conda:

```bash
conda install -c conda-forge rdkit
```

or install via pip (if RDKit is available for your platform):

```bash
pip install rdkit
```

---

## Workflow

```
Original Molecule
        │
        ▼
Renumber atoms (BFS)
        │
        ▼
Visualize atom indices
        │
        ▼
Select atoms to keep
        │
        ▼
Extract fragment
        │
        ▼
RDKit Sanitization
```

---

## Example

```python
from rdkit import Chem

mol = Chem.SDMolSupplier(
    "ligand.sdf",
    sanitize=False,
    removeHs=False
)[0]

renumbered_mol = renumber_by_bfs(mol)

atoms_to_keep = [0, 1, 2, 3, 4, 5, 6]

fragment = keep_atoms(
    renumbered_mol,
    atoms_to_keep
)
```

---

## Main Functions

### `renumber_by_bfs(mol, start_atom=0)`

Renumber atom indices according to molecular connectivity using a Breadth-First Search (BFS) traversal.

```python
renumbered_mol = renumber_by_bfs(mol)
```

---

### `keep_atoms(mol, atoms_to_keep)`

Extract a molecular fragment by keeping only selected atom indices.

```python
fragment = keep_atoms(
    renumbered_mol,
    atoms_to_keep
)
```

---

### Atom Index Visualization

Display atom indices in Jupyter Notebook for convenient fragment selection.

```python
draw_molecule_with_atom_indices(renumbered_mol)
```

---

## Applications

- Pharmacophore extraction
- Fragment-based drug design
- Scaffold editing
- Molecular preprocessing
- Interactive molecular editing
- RDKit workflow development

---

## Dependencies

- Python ≥ 3.10
- RDKit
- Jupyter Notebook / IPython

---

## License

This project is released under the MIT License.
