# msImpute [![DOI](https://zenodo.org/badge/239129382.svg)](https://zenodo.org/badge/latestdoi/239129382)

Methods for label-free mass spectrometry proteomics imputation

**Installation (R)**

```
install.packages("devtools") # devtools is required to download and install the package
devtools::install_github("DavisLaboratory/msImpute")
```

**Quick Start**

```
library(reticulate)
library(msImpute)

selectFeatures(xna)  # xna is a numeric matrix with NAs (for MAR/MNAR diagnosis only)
xna <- scaleData(xna) 
msImpute(xna, rank.max = 2) # rank 2 approximaiton
xcomplete <- msImpute(xna)  # optimal rank determined by msImpute


# Requires python. See Manual for more information.
top.hvp <- findVariableFeatures(xna$E)
computeStructuralMetrics(xcomplete, 
                         # "group" denotes experimental condition (e.g. control, treatment etc).
                         group, 
                         xna$E[rownames(top.hvp)[1:50],], 
                         k = 2) 


```
 


**Reference**

Cite our [preprint](https://www.biorxiv.org/content/10.1101/2020.08.12.248963v1)

