# scvi-apptainer

A GPU-enabled **Apptainer (Singularity)** container for single-cell RNA-seq analysis using **Scanpy** and **scVI-tools**.  
Built automatically via **GitHub Actions** and tested on the **Brown CCV (Oscar)** cluster.

---

## 🧠 Overview

This repository defines a reproducible scientific computing environment for single-cell transcriptomics.  
It bundles:
- **Scanpy** for preprocessing, visualization, and clustering  
- **scVI-tools** for probabilistic modeling and integration  
- **CUDA-enabled PyTorch** for GPU acceleration  
- Common utilities (`pandas`, `numpy`, `matplotlib`, `plotly`, `seaborn`, etc.)

---

## 🧩 Files

| File | Purpose |
|------|----------|
| `scvi_gpu.def` | Apptainer definition file — describes the environment |
| `.github/workflows/build-sif.yml` | GitHub Actions workflow that builds the `.sif` automatically |

---

## 🚀 Build Instructions (Automatic)

The `.sif` container is built automatically using **GitHub Actions**.

1. Go to the **Actions** tab in this repository.  
2. Select **Build SIF** → **Run workflow**.  
3. Wait for the run to complete (green checkmark ✅).  
4. Scroll down and download the **`scvi_env.sif`** artifact.

The build uses the **Docker Hub PyTorch CUDA base image** (`pytorch/pytorch:2.3.1-cuda12.1-cudnn8-runtime`) and installs all required packages.

---

## 📦 Uploading to Brown CCV (Oscar)

After downloading the `scvi_env.sif` artifact:

```bash
scp ~/Downloads/scvi_env.sif <your_netid>@ssh.ccv.brown.edu:/oscar/data/<your_lab>/_
