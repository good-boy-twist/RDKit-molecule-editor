# RDKit-molecule-editor
This project provides a simple workflow for editing molecules stored in SDF format. It renumbers atom indices using molecular connectivity, allows interactive atom selection, and exports the selected fragment as a new SDF file.

---

## Features

- 📂 Load molecules directly from SDF files
- 🔢 Renumber atom indices using Breadth-First Search (BFS)
- 👀 Visualize atom indices for easy inspection
- ✍️ Select atoms using intuitive range expressions (e.g. `0-10`, `0-5, 10, 15-20`)
- ✂️ Extract selected atoms as a molecular fragment
- 💾 Export the fragment as a new SDF file
- 🔒 Preserve the original molecule throughout the workflow

---

## Workflow

```
Input SDF
    │
    ▼
Load molecule
    │
    ▼
Renumber atom indices (BFS)
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

### 2. Choose the BFS starting atom

```python
renumbered_mol = renumber_by_bfs(mol, start_atom=0)
```

Changing the starting atom changes the numbering order, making it easier to select contiguous fragments.

---

### 3. Inspect atom indices

The notebook generates a 2D depiction with atom numbers.

---

### 4. Select atoms to keep

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

## Functions

### `renumber_by_bfs()`

Renumber atom indices according to molecular connectivity using Breadth-First Search.

### `parse_atom_indices()`

Convert user-friendly range expressions into a list of atom indices.

Example:

```
0-5, 10, 20-22
```

↓

```python
[0, 1, 2, 3, 4, 5, 10, 20, 21, 22]
```

### `keep_atoms()`

Extract a molecular fragment by preserving only the selected atom indices.

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
