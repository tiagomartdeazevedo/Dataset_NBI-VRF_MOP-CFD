# Dataset and Code for VRF-NBI Multi-Objective CFD Optimization

This repository provides the dataset and Python codes used in the study **"Analysis and Implementation of VRF-NBI in the Multi-Objective Optimization of High-Dimensional Hydraulic Systems"**, developed by **Tiago Martins de Azevedo**.

The repository supports the reproduction and extension of a multivariate and multi-objective optimization framework that integrates **Design of Experiments (DOE)**, **Response Surface Methodology (RSM)**, **multivariate statistical analysis**, and **Computational Fluid Dynamics (CFD)** through the **Varimax-Rotated Factor–Normal Boundary Intersection (VRF-NBI)** method.

---

## 🧭 Project Overview

The dataset represents a **parametric CFD study** of an **axial hydraulic turbine inlet duct**, modeled according to IEC 60193 recommendations.

Each record in the database corresponds to a CFD simulation performed according to a **Central Composite Design (CCD)** with five independent variables and fourteen dependent performance metrics.

The data and codes were used to:

- Evaluate the influence of mesh, flow, and convergence parameters on CFD performance.
- Build quadratic response surface models for the performance metrics.
- Apply **Principal Component Analysis (PCA)** and **Factor Analysis (FA)** with Varimax rotation to reduce dimensionality.
- Represent the 14 original responses through three latent factors.
- Integrate the rotated factor scores into a **Normal Boundary Intersection (NBI)** framework.
- Generate and evaluate Pareto-optimal solutions.
- Compare VRF-NBI with alternative multi-objective optimization approaches, including **NSGA-II, MOEA/D**, and other implemented methods.
- Evaluate the performance of the different optimization strategies using quantitative performance indicators.

---

## 📁 Repository Structure

### Dataset

**File:** `Database.xlsx`

**Sheets:**

- `Data` – Main dataset containing the input factors and output responses.
- `Metadata` – Variable definitions and additional statistical information, when available.

Each row corresponds to a CFD run performed under specific mesh, flow, and convergence conditions defined by the CCD.

### Python Codes

The repository also includes Python scripts for data processing, statistical analysis, dimensionality reduction, surrogate modeling, multi-objective optimization, and comparison of optimization methods.

The codes can be used to:

1. Load and preprocess the CFD dataset.
2. Construct response surface models.
3. Perform PCA and Factor Analysis with Varimax rotation.
4. Generate the latent variables used in VRF-NBI.
5. Perform multi-objective optimization.
6. Generate Pareto-optimal solutions.
7. Compare VRF-NBI with alternative optimization methods.
8. Calculate the performance indicators used for the comparison.

---

## ⚙️ Input Variables (Factors)

| Symbol | Description | Unit | Range / Levels |
|---|---|---|---|
| MV | Mesh volume size | mm | 1.5 – 4.0 |
| ME | Inlet mesh size | mm | 1.5 – 4.0 |
| MS | Outlet mesh size | mm | 1.5 – 4.0 |
| ṁ | Mass flow rate | kg/s | 22.455 – 34.930 |
| CC | Convergence criterion (RMS) | – | 1×10⁻⁵ – 1×10⁻⁴ |

---

## 📊 Output Variables (Responses)

| Symbol | Description | Unit |
|---|---|---|
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
| y+ | Wall coordinate | ×10⁻¹ |

These 14 responses were grouped into three main performance dimensions through **Varimax-rotated Factor Analysis (FA)**:

- **VRF1:** Mesh quality and cost metrics
- **VRF2:** Flow and energy-related metrics
- **VRF3:** Convergence behavior metrics

---

## 🧮 Methodological Context

The underlying methodology combines:

- **Design of Experiments (DOE)** for systematic exploration of the CFD parameter space;
- **Response Surface Methodology (RSM)** for surrogate modeling;
- **Principal Component Analysis (PCA)** and **Factor Analysis (FA)** for dimensionality reduction;
- **Varimax rotation** for obtaining interpretable latent factors;
- **Normal Boundary Intersection (NBI)** for multi-objective optimization;
- **Simplex-Lattice mixture design** for systematic generation of objective-weight combinations.

The resulting framework is referred to as **VRF-NBI (Varimax-Rotated Factor–Normal Boundary Intersection)**.

The approach is designed to rationalize CFD simulations by considering multiple correlated performance metrics simultaneously and by systematically exploring the trade-offs among mesh, flow, convergence, and computational-cost criteria.

---

## 🔬 Optimization Methods

The repository includes codes for evaluating and comparing different optimization strategies.

The implemented approaches include:

### VRF-NBI

The proposed methodology combines multivariate dimensionality reduction with the NBI formulation. The rotated factor scores are used as objective functions, and the Simplex-Lattice design is used to systematically explore different objective-weight combinations.

### NSGA-II

The **Non-dominated Sorting Genetic Algorithm II (NSGA-II)** is used as an evolutionary multi-objective optimization benchmark.

### MOEA/D

The **Multi-Objective Evolutionary Algorithm based on Decomposition (MOEA/D)** is used as an alternative decomposition-based optimization strategy.

### Other optimization approaches

Additional optimization approaches implemented in the repository can be used to reproduce the comparative analysis presented in the study.

The comparison allows the performance of VRF-NBI to be evaluated against alternative strategies under the same problem formulation and dataset.

---

## 📈 Optimization Comparison

The Python codes allow the user to reproduce the comparison between the optimization approaches.

The analysis includes the generation and evaluation of Pareto-optimal solutions and the calculation of performance indicators used to assess the quality of the obtained solution sets.

Depending on the implemented analysis, the comparison includes metrics such as:

- **Generational Distance (GD)**
- **Hypervolume (HV)**
- **Spread / distribution metrics**
- **S/GPE**
- Other indicators implemented in the corresponding Python scripts.

The comparison is intended to evaluate different aspects of the optimization results, including convergence toward the reference Pareto frontier and the distribution of solutions.

---

## 🚀 Usage Instructions

### 1. Download the repository

Clone or download this repository and ensure that the dataset and Python scripts are available in the same working environment.

### 2. Load the dataset

Load `Database.xlsx` using the provided Python scripts. The dataset contains the CFD observations used in the statistical analysis and multi-objective optimization.

### 3. Run the analysis

The Python codes can be used to reproduce the statistical and optimization analyses presented in the study.

The general computational workflow is:

```text
Database.xlsx
      ↓
Data preprocessing
      ↓
DOE / Statistical analysis
      ↓
PCA + Factor Analysis
      ↓
Varimax rotation
      ↓
Latent factors
      ↓
Response Surface Models
      ↓
Multi-objective optimization
      ↓
Pareto solutions
      ↓
VRF-NBI / NSGA-II / MOEA/D comparison
      ↓
Performance indicators
```

### 4. Reproduce or extend the study

The dataset and Python codes can be adapted for further investigations, including:

investigating alternative statistical models;
testing different dimensionality-reduction techniques;
implementing alternative multi-objective optimization algorithms;
modifying objective functions and optimization weights;
investigating additional CFD performance metrics;
extending the methodology to other CFD problems.

### 📚 Reproducibility

This repository is intended to support reproducibility, transparency, and further development of the methodology presented in the study.

The dataset contains the CFD observations used in the statistical and optimization analyses, while the Python codes provide computational procedures for reproducing the main analyses and comparing alternative optimization strategies.

In particular, the optimization comparison code provides a computational basis for evaluating the performance of VRF-NBI, NSGA-II, MOEA/D, and other implemented approaches within the framework investigated in this study.

The repository should therefore be considered a complementary computational resource to the thesis and associated scientific publication, allowing researchers to inspect, reproduce, modify, and extend the proposed methodology.

### 📖 Reference

If you use this dataset or code, please cite:

Azevedo, T. M. or de Azevedo, T. M. or Azevedo, T. M. de

Analysis and Implementation of VRF-NBI in the Multi-Objective Optimization of High-Dimensional Hydraulic Systems.

### 👤 Author

Tiago Martins de Azevedo

Mechanical Engineer | CFD | R&D | Multi-Objective Optimization | Hydraulic Systems

GitHub: tiagomartdeazevedo

ORCID: 0000-0001-6086-5039

E-mail: tiago.deazevedo@yahoo.com.br
