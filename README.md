# RDKit-molecule-editor
This project provides a simple workflow for editing molecules stored in SDF format. It renumbers atom indices using molecular connectivity, allows interactive atom selection, and exports the selected fragment as a new SDF file.

---

## Features

- 🔢 **DFS-based atom renumbering**
  - Renumber atoms using deterministic Depth-First Search (DFS).
  - Useful for graph-based molecular representations.

- 🖼️ **Atom index visualization**
  - Display atom indices directly on the molecular structure.
  - Easy identification of atoms for editing.

- ✂️ **Interactive pharmacophore extraction**
  - Select atoms to retain using a simple input format. (e.g. 0-5,8,10-14)

- 🧪 **Chemical sanitization**
  - Automatically sanitizes the edited molecule before export.

- 💾 **SDF export**
  - Save the edited molecule as an SDF file for further analysis.

---


## Workflow

```
Input SDF
    │
    ▼
Load molecule
    │
    ▼
Renumber atom indices (DFS)
    │
    ▼
Visualize atom indices
    │
    ▼
Input atoms to keep (e.g. 0-10, 15, 20-25)
    │
    ▼
Extract fragment
    │
    ▼
Preview fragment
    │
    ▼
Save as SDF
```

---

## Requirements

- Python 3.10+
- RDKit
- Jupyter Notebook

Install RDKit using Conda:

```bash
conda install -c conda-forge rdkit
```

---

## Usage

### 1. Specify the input molecule

```python
sdf_name = "7x9p_ligand"
```

The notebook will automatically load:

```
7x9p_ligand.sdf
```

---

### 2. Renumber atoms

The notebook automatically performs DFS-based atom renumbering.

This provides a deterministic atom ordering that can be useful for:

- graph neural networks
- pharmacophore generation
- molecular editing
- reproducible atom indexing

---

### 3. Inspect atom indices

The notebook generates a 2D depiction with atom numbers.

Use the displayed indices to determine which atoms should be retained.

---

### 4. Select atoms to keep

Input atoms using ranges and comma-separated values.

Input examples:

```
0-15
```

```
0-8, 15, 20-25
```

The parser automatically converts the input into a list of atom indices.

---

### 5. Export the fragment

The extracted fragment is written as

```
<sdf_name>_pharmacophore.sdf
```

For example,

```
7x9p_ligand_pharmacophore.sdf
```

---

## Notes

- Hydrogen atoms are preserved if present in the input structure.
- Molecules are initially loaded with

```python
sanitize=False
removeHs=False
```

to preserve the original structure.

- The edited molecule is sanitized before export.

- Atom numbering after editing follows the DFS-renumbered structure.

---

## Applications

- Pharmacophore extraction
- Scaffold simplification
- Fragment-based drug design
- Manual molecular editing
- RDKit preprocessing workflows

---

## License

This project is released under the MIT License.
