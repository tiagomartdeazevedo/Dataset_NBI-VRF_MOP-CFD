# Dataset for VRF-NBI Multi-Objective CFD Optimization

This repository provides the dataset used in the study **"Analysis and Implementation of VRF-NBI in the Multi-Objective Optimization of High-Dimensional Hydraulic Systems"**, developed by **Tiago Martins de Azevedo**.  
The data support the implementation of a multivariate and multi-objective optimization framework that integrates **Response Surface Methodology (RSM)** and **Computational Fluid Dynamics (CFD)** through the **Varimax Rotated Factor–Normal Boundary Intersection (VRF-NBI)** method.

---

## 🧭 Project Overview

The dataset represents a **parametric CFD study** of an **axial hydraulic turbine inlet duct**, modeled according to IEC 60193 recommendations.  
Each record in the database corresponds to a simulation performed according to a **Central Composite Design (CCD)** with five independent variables (control factors) and fourteen dependent variables (performance metrics).

The data were used to:
- Evaluate the influence of mesh, flow, and convergence parameters on hydrodynamic performance.  
- Build quadratic response surfaces for each metric.  
- Apply **Principal Component Analysis (PCA)** and **Factor Analysis (FA)** to reduce dimensionality.  
- Integrate the latent variables (rotated factor scores) into a **Normal Boundary Intersection (NBI)** framework for Pareto frontier generation.

---

## 📁 Dataset Structure

**File:** `Database.xlsx`  
**Sheets:**  
- `Data` – Main dataset with input and output variables.  
- `Metadata` (if included) – Summary of variable definitions and statistical notes.  

Each row corresponds to a single CFD run performed under specific mesh, flow, and convergence conditions defined by the CCD.

---

## ⚙️ Input Variables (Factors)

| Symbol | Description | Unit | Range / Levels |
|:------:|:-------------|:------|:---------------|
| MV | Mesh volume size | mm | 1.5 – 4.0 |
| ME | Inlet mesh size | mm | 1.5 – 4.0 |
| MS | Outlet mesh size | mm | 1.5 – 4.0 |
| ṁ | Mass flow rate | kg/s | 22.455 – 34.930 |
| CC | Convergence criterion (RMS) | – | 1×10⁻⁵ – 1×10⁻⁴ |

---

## 📊 Output Variables (Responses)

| Symbol | Description | Unit |
|:------:|:-------------|:------|
| CM | Mesh generation cost | ×10⁻¹ USD |
| CS | Simulation cost | ×10⁻¹ USD |
| Nel | Number of mesh elements | ×10⁶ |
| Q | Average mesh quality | ×10⁻³ |
| AR | Aspect ratio | ×10⁻⁴ |
| Ortho | Average orthogonality | ×10⁻⁴ |
| Skew | Average skewness | ×10⁻⁴ |
| It | Number of iterations | – |
| VM_RMS | Root Mean Square of vertical momentum | ×10⁶ |
| ΔP | Pressure difference | ×10³ Pa |
| k | Turbulent kinetic energy | ×10¹ m²/s² |
| ε | Turbulence dissipation rate | ×10⁻³ |
| Re | Reynolds number | ×10⁻⁶ |
| y+ | Wall coordinate (dimensionless) | ×10⁻¹ |

These 14 responses were grouped into three main performance dimensions through **Varimax-rotated Factor Analysis (FA)**:
- **VRF1:** Mesh quality and cost metrics  
- **VRF2:** Flow and energy-related metrics  
- **VRF3:** Convergence behavior metrics  

---

## 🧮 Methodological Context

Although this repository focuses on the data, the underlying methodology combines:
- **Response Surface Methodology (RSM)** for regression modeling,  
- **PCA/FA** for dimensionality reduction, and  
- **Normal Boundary Intersection (NBI)** for Pareto frontier generation.  

This hybrid framework—referred to as **VRF-NBI**—aims to rationalize CFD simulations by reducing computational cost and improving accuracy while preserving multivariate consistency among performance indicators.

---

## 🚀 Usage Instructions

1. Download the `Database.xlsx` file.  
2. Load the dataset into Python, MATLAB, or R for analysis.  
3. Perform regression or statistical modeling using the provided variables.  
4. (Optional) Apply PCA/FA to reconstruct the VRF latent variables for multi-objective optimization.  
5. Use RSM or meta-modeling tools to reproduce or extend the optimization study.  

Example in Python:

```python
import pandas as pd

df = pd.read_excel('Database.xlsx', sheet_name='Data')
print(df.head())
