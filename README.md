# LUCid

A R package allows users to achieve joint estimation of latent or unobserved clusters using multi-omics data with/without outcome of interest.

## Getting Started

This supplementary package is based on the research paper "Integrated Analysis of Germline, Omic and Disease Data" (Under development, will replace this field with a citation when we have one). 

### Prerequisites

R (>= 3.1.0).

```
Package Dependencies: "mvtnorm", "nnet", "glmnet", "glasso", "lbfgs".
```

### Installing

We have a plan to submit the package to CRAN/Bioconductor when the development cycle is done.

For now, it can be installed from GitHub using the following codes:

```
install.packages("devtools")
devtools::install_github("USCbiostats/LUCid")
```
Otherwise, one can download the package from GitHub, and run the following codes from the parent working directory that contains the LUCid folder:

```
install.packages("devtools")
setwd("..")
devtools::install("LUCid")
```

## Fitting the latent cluster models

Three functions, including *est_cluster*, *sem_cluster*, & *tune_cluster*, are currently available for model fitting and selection. 

### *est_cluster*

Estimating latent clusters with multi-omics data

#### Example

```
est_cluster(G=G1,Z=Z1,Y=Y1,K=2,family="binary",Pred=TRUE,
            initial=def_initial(), itr_tol=def_tol(),
            tunepar = def_tune(Select_G=TRUE,Select_Z=TRUE,Rho_G=0.02,Rho_Z_InvCov=0.1,Rho_Z_CovMu=93))
```

### *sem_cluster*

Supplemented EM-algorithm for latent cluster estimation

#### Example

```
sem_cluster(G=G2,Z=Z2,Y=Y2,useY=TRUE,K=2,Pred=TRUE,family="normal",Get_SE=TRUE,
            def_initial(),def_tol(MAX_ITR=1000,MAX_TOT_ITR=3000))
```

### *tune_cluster*

Grid search for tuning parameters using parallel computing

#### Example

```
GridSearch <- tune_cluster(G=G1, Z=Z1, Y=Y1, K=2, Family="binary", USEY = TRUE,
                           LRho_g = 0.001, URho_g = 0.1, NoRho_g = 10,
                           LRho_z_invcov = 0.05, URho_z_invcov = 0.3, NoRho_z_invcov = 6,
                           LRho_z_covmu = 75, URho_z_covmu = 100, NoRho_z_covmu = 6)
GridSearch$Results
GridSearch$Optimal
```
For more details, see documentations for each function in the R package.


## Built With

* [devtools](https://cran.r-project.org/web/packages/devtools/index.html) - Tools to Make Developing R Packages Easier
* [roxygen2](https://cran.r-project.org/web/packages/roxygen2/index.html) - In-Line Documentation for R

## Versioning

The current version is 0.3.0.

For the versions available, see the [Version on this repository](https://github.com/your/project/Version) (not available yet). 

## Authors

* **Cheng Peng**

## License

This project is licensed under the GPL-2 License.

## Acknowledgments

* Dr. David V. Conti
* Dr. Zhao Yang
* etc.
