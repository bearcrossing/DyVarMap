# DyVarMap: Dynamic Variant Mapping 🧬⚙️

![Python](https://img.shields.io/badge/python-3.10-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![DOI](https://img.shields.io/badge/DOI-10.3390%2Fbioengineering1300126-blue)

**DyVarMap** is an end-to-end, interpretable computational framework that integrates AlphaFold2-based ensemble generation, physics-driven molecular dynamics (MD) refinement, nonlinear manifold learning, and explainable AI. It is designed to decode the biophysical mechanisms underlying cancer-associated missense variants, with a specific focus on complex receptor tyrosine kinases like **FGFR2**.

By mapping high-dimensional structural data onto interpretable free energy landscapes, DyVarMap moves beyond black-box pathogenicity scores (e.g., AlphaMissense) to pinpoint precise biophysical disruptions such as salt-bridge breakages and allosteric shifts.

---

## 🔬 Pipeline Overview

The framework is highly modularized into four distinct engineering and analytical stages:

![DyVarMap Workflow](assets/figure1_workflow.png)

1. **Stage 1: Conformational Sampling (AF2-RAVE)** Generation of diverse initial structural ensembles across wild-type (WT) and variants using modified AlphaFold2 pipelines.
2. **Stage 2: Physics-Driven Refinement (OpenMM)** Automated energy minimization in a vacuum environment to resolve steric clashes and optimize side-chain geometries.
3. **Stage 3: High-Dimensional Feature Extraction (MDTraj/MDAnalysis)** Extraction of biophysically motivated geometric features: Salt-bridge distances, A-loop lengths, $\alpha$C-helix angles, and DFG-motif dihedral angles.
4. **Stage 4: Manifold Learning & Explainable ML (SPIB + SHAP)** Nonlinear dimensionality reduction (SPIB) and density-based clustering (HDBSCAN) to identify metastable states, followed by Random Forest/SVM classification with SHAP-based feature attribution.

---

## 🛠️ Installation & Setup

We highly recommend using `conda` to manage the dependencies and ensure reproducibility.

```bash
# Clone the repository
git clone [https://github.com/bearcrossing/DyVarMap.git](https://github.com/bearcrossing/DyVarMap.git)
cd DyVarMap

# Create and activate the conda environment
conda env create -f environment.yml
conda activate dyvarmap