# 🧬 scVI + Seurat + Scrublet Container (CUDA-Ready, CCV-Optimized)

A unified **Apptainer/Singularity** container for single-cell RNA-seq analysis in **Python and R**, built for Brown CCV’s Oscar cluster.

This image integrates:
- 🧠 **Python (GPU-enabled)** — `scvi-tools` (torch-only), `scanpy`, `scrublet`, `umap-learn`, `matplotlib`, `pytorch-lightning`
- 🧪 **R (Bioconductor + CRAN)** — `Seurat`, `SeuratDisk`, `zellkonverter`, `SingleCellExperiment`, `qs`
- 🧰 **JupyterLab + IRkernel** — seamless notebooks in both R and Python

---

## 🧱 Contents

| Component | Version | Notes |
|------------|----------|-------|
| Base image | `pytorch/pytorch:2.3.1-cuda12.1-cudnn8-runtime` | GPU compatible |
| Python | 3.10 | with `scanpy`, `scvi-tools`, `scrublet`, etc. |
| R | 4.3+ | with `Seurat`, `zellkonverter`, `SingleCellExperiment` |
| JupyterLab | 4.2.5 | includes `ipywidgets` and `IRkernel` |
| CUDA / cuDNN | 12.1 / 8 | works on CCV GPU partitions |

---

## 🧩 Build Instructions (GitHub Actions)

1. Add these two files to your repository:
   - `scvi_ccv.def` (Apptainer definition file)
   - `.github/workflows/build_sif.yml` (GitHub Actions workflow)

2. Push to your repo and trigger a build manually or on push to `main`.

The workflow builds your image and uploads `scvi_ccv.sif` as an artifact.

---

## 📦 Files in this repo

| File | Purpose |
|------|----------|
| `scvi_ccv.def` | Definition file for building the Apptainer container |
| `.github/workflows/build_sif.yml` | Workflow to build `.sif` automatically on GitHub |
| `README.md` | This documentation |

---

## 🖥️ Use on Brown CCV (Oscar)

1. **Copy your SIF file to Oscar:**
   ```bash
   scp scvi_ccv.sif <user>@oscar.ccv.brown.edu:/oscar/home/<user>/data/containers/
