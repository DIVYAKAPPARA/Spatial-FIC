# Spatial Econometrics Model Selection using FIC, VFIC, and AFIC

This repository contains R code for implementing FIC based variable selection, specifically for Spatial Lag Models (SLM). The project implements Focused Information Criterion (FIC), Vector Focused Information Criterion (VFIC), and Average Focused Information Criterion (AFIC) for variable selection in spatial regression models.



The code provides a framework for model selection, variable selection in Spatial Lag Models, simulation studies to compare different selection criteria.


- **Focused Information Criterion (FIC)**: Model selection based on a specific focus parameter
- **Vector Focused Information Criterion (VFIC)**: Extension for multiple focus parameters
- **Average Focused Information Criterion (AFIC)**: Model averaging with kernel-based weighting
- **Spatial Lag Model estimation** using `lagsarlm` from `spatialreg` package
- **Simulation framework** for performance evaluation across 100 iterations
- **Gaussian kernel weighting** for local model averaging
- **Projection matrix generation** for all possible submodels

## Code Structure

### Main Functions

**`compute_FIC()`** - Computes Focused Information Criterion for model selection. Takes response variable, covariates, spatial weights matrix, and parameters as input. Returns FIC values, bias, variance, and MSE for all submodels.

**`compute_VFIC()`** - Computes Vector Focused Information Criterion as an extension for multiple focus parameters.

**`AFIC()`** - Computes Average Focused Information Criterion and implements model averaging with weighting matrices.

**`gaussian_kernel_weights()`** - Creates Gaussian kernel weight matrix by computing weights based on Euclidean distance between covariate vectors using a bandwidth parameter for smoothing.

### Core Components

- **Spatial weights**: Row-standardized and binary weight matrices from contiguity
- **Submodel generation**: All possible variable combinations (2^p submodels)
- **Projection matrices**: Maps full models to submodels
- **Simulation framework**: 100 Monte Carlo iterations with varying covariate generation

## Quick Start

1. Load the required R packages
2. Prepare your spatial data (shapefile or RDS format)
3. Generate spatial weights from contiguity matrix
4. Define parameters: true coefficients (beta), spatial autoregressive parameter (rho), and number of covariates
5. Generate all submodel combinations using projection matrices
6. Run simulations to compute FIC, VFIC, and AFIC values
7. Export results to Excel for analysis

## Key Parameters

- **beta**: True coefficient vector
- **rho**: Spatial autoregressive parameter (typically -1 to 1)
- **h**: Bandwidth parameter for Gaussian kernel
- **focus**: Focus parameter index for FIC computation
- **psi**: Weight matrix for AFIC (uniform or kernel-based)

## Output

Results are saved in Excel format containing FIC, VFIC, and AFIC values, along with MSE calculations. The code also generates model selection frequencies showing which submodel gets selected most often across simulations.

## Methodology

The implementation uses:
- Maximum likelihood estimation for Spatial Lag Models via `lagsarlm`
- Information matrix partitioning for bias correction
- Bias-variance decomposition in prediction error
- Locally weighted model averaging with kernel weighting
- Comparison of uniform versus Gaussian kernel weighting effects


The output provides:
- Model selection frequencies
- Bias-variance tradeoff analysis
- Kernel weights effect comparison
- Impact of spatial dependence on selection



