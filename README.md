# TDA-Based Critical Transition Detection

**Author:** Adel ADRAOUI (Université Paris Cité)

This repository contains a Jupyter Notebook that implements the pipeline described in *Topological Recognition of Critical Transitions in Time Series of Cryptocurrencies*. The goal is to detect regime changes and critical transitions in time series data using tools from Topological Data Analysis (TDA) combined with clustering and predictive modeling.

---

## Original Research Paper

For further details on the methodology behind this notebook, please refer to the original research paper:

**[TOPOLOGICAL RECOGNITION OF CRITICAL TRANSITIONS  
IN TIME SERIES OF CRYPTOCURRENCIES  
by Marian Gidea, Daniel Goldsmith, Yuri Katz, Pablo Roldan, and Yonah Shmalo](https://arxiv.org/pdf/1809.00695)**

---

## Overview

The notebook covers the following steps:

1. **Time–Delay Coordinate Embedding (Takens Embedding):**  
   Reconstructs the state space of the time series.

2. **Sliding Windows:**  
   Generates point clouds by partitioning the embedded time series into overlapping windows.

3. **Persistent Homology Computation:**  
   Computes 1-dimensional persistent homology using the Vietoris–Rips filtration.

4. **Persistence Landscape Extraction:**  
   Calculates persistence landscapes and their L1 norms from the persistent homology diagrams.

5. **Clustering Analysis:**  
   Applies k–means clustering on a feature set that includes log–price, log–return, and the TDA-based L1 norm to detect market regimes.

6. **Predictive Modeling:**  
   Uses TDA-based features in a predictive framework (with walk–forward validation) comparing Linear Regression and Random Forest models for forecasting future log–returns.

The notebook demonstrates the pipeline on two examples:

- **Simulated Lorenz-type Noisy Chaotic Time Series:**  
  This example simulates a discrete-time Lorenz–type map to illustrate bifurcation behavior and critical transitions.

- **Cryptocurrency Data Example (BTC-USD):**  
  This example fetches Bitcoin data from Yahoo Finance and applies the TDA pipeline to analyze market regimes.

---

## Notebook Contents

### 1. Setup and Library Imports
- **Core Libraries:** NumPy, Pandas, and Matplotlib.
- **TDA Libraries:** giotto-tda (for Takens embedding, persistent homology, and persistence landscapes).
- **Modeling and Evaluation:** scikit-learn for clustering, PCA, and regression models.
- **Data Acquisition:** yfinance for fetching cryptocurrency data.
- **Additional Tools:** SciPy for simulation support.

### 2. Helper Functions
- **`create_sliding_windows`:**  
  Splits the embedded time series into overlapping windows.

- **`compute_persistence_landscape_norm`:**  
  Computes the L1 norm of the persistence landscape from a persistence diagram.

### 3. Simulated Data Example: Lorenz-type Map
- **Simulation:**  
  Generates a noisy chaotic time series using a discrete Lorenz–type map.

- **Visualization:**  
  Includes a bifurcation diagram and attractor visualizations along with a demonstration of persistence diagrams and landscapes.

- **TDA Pipeline:**  
  Applies time–delay embedding, sliding window segmentation, and computes L1 norm of persistence landscapes.

### 4. Cryptocurrency Example: BTC-USD Data
- **Data Acquisition:**  
  Fetches historical BTC-USD data using Yahoo Finance.

- **Feature Engineering:**  
  Computes log–price and log–returns, and performs time–delay embedding and sliding window TDA on the log–return series.

- **Clustering:**  
  Constructs a feature set (normalized log–price, log–return, lagged L1 norm) for k–means clustering to identify potential regimes.

- **Visualization:**  
  Uses PCA for 2D visualization of cluster assignments and overlays cluster labels on time-series plots.

### 5. Predictive Modeling Using TDA-Based Features
- **Target Construction:**  
  Creates a target for a 5-day future log–return.

- **Walk–Forward Validation:**  
  Compares Linear Regression and Random Forest models with the TDA feature set using time-series cross-validation.

- **Performance Metrics:**  
  Reports MSE, RMSE, and R², and provides visualizations comparing actual vs. predicted returns.

---

## Requirements

### Python Environment
- Python 3.7 or higher is recommended.

### Required Libraries
Install the libraries using pip:

```bash
pip install numpy pandas matplotlib scipy scikit-learn giotto-tda yfinance
