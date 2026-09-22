# SweetTooth 

**SweetTooth** is an interactive PyMOL visualization plugin that transforms raw DSSP secondary-structure assignments into intuitive, food-inspired molecular representations.

The original protein remains fully available in PyMOL, so structures can still be rotated, selected, measured, edited, simulated, and saved normally. SweetTooth only adds visualization objects and never generates or exports images automatically.

## Visual Language

SweetTooth represents secondary-structure states using clean food-inspired materials drawn directly along the protein trace:

- **H / G / I — Helices:** smooth red candy rods with a continuous white spiral
- **E / B — β-structures:** chocolate ribbons with sparse golden wafer layers
- **C — Coil:** smooth green translucent gummy worm
- **S — Bend:** smooth cyan translucent jelly-bean-like bend
- **T — Turn:** smooth blue translucent gummy hook
- **P — PPII / κ:** dark licorice with restrained charcoal ridges

The visualization is intentionally minimal. There is no legend, generic gloss overlay, or unnecessary decorative geometry.

The only additional geometry is the **continuous white spiral used to make helices visually recognizable as candy canes**.

SweetTooth creates only objects prefixed with `STF_`. Running `sweettooth_reset` removes only these SweetTooth-generated objects and leaves the original molecular structure untouched.

---

## Installation

Install the Python distribution:

```bash
python -m pip install --upgrade --force-reinstall \
  sweettooth_pymol-1.1.0-py3-none-any.whl
```

Then start PyMOL using the packaged launcher:

```bash
sweettooth-pymol
```

The launcher avoids incompatible Python/PyMOL wrappers and automatically loads SweetTooth.

`sweettooth-pymol` is a Python console entry point rather than a shell script. It launches the system PyMOL interpreter with only the narrowly scoped compatibility shims required by SweetTooth.

### Optional system installation

SweetTooth can also be installed permanently into a system PyMOL installation:

```bash
sudo "$(command -v sweettooth-install)" \
  --pymol-path /usr/share/pymol \
  --force
```

`--pymol-path` may point either to a PyMOL root directory containing `data/startup` or directly to the PyMOL startup directory.

Administrator privileges may be required for system-wide installations.

---

## Quick Start

SweetTooth currently uses DSSP secondary-structure assignments.

Make sure `mkdssp` is available on your `PATH`.

Then, from the PyMOL command line:

```text
sweet_load /absolute/path/to/protein.pdb
```

For example:

```text
sweet_load /home/sray/THESIS_WORK_2026-2027/SWEETOOTH/ALPHAFOLD2HNP.pdb
```

SweetTooth generates the required DSSP assignments in a temporary working directory. **The original structure file is never modified.**

---

## Commands

```text
sweet_load path [, object [, auto|dssp]]
sweettooth_load path, dssp
sweettooth object [, force]
sweettooth_mode dssp
sweettooth_residue residue
sweettooth_residue chain, residue
sweettooth_status
sweettooth_reset
```

### Example

```text
sweet_load /path/to/protein.pdb
sweettooth_status
sweettooth_residue A, 215
```

To remove the SweetTooth representation:

```text
sweettooth_reset
```

The underlying protein remains available throughout the session.

---

## Design Philosophy

SweetTooth is a **visualization layer, not a secondary-structure predictor**.

It converts existing structural annotations into a more immediately readable representation while preserving the normal PyMOL environment underneath.

The goal is to make secondary-structure organization visually intuitive without replacing the molecular structure or interfering with downstream structural analysis.

---

## Compatibility

SweetTooth remains compatible with **Python 3.8** for older PyMOL builds.

It also includes a narrowly scoped compatibility shim for older PyMOL lighting plugins that pass floating-point values to modern PyQt slider methods.

All ordinary PyMOL functionality remains available.

---

## Coming Soon

A new SweetTooth visualization mode is currently under development.

**It will extend SweetTooth beyond deterministic secondary-structure assignments and introduce a richer way to explore protein structure inside PyMOL**.

**More details coming soon. 🍬**

---

## Status

**SweetTooth Final v1.1.0**

Interactive DSSP visualization: **available**  
Advanced structural-state visualization: **coming soon**
