
<!-- README.md is generated from README.Rmd. Please edit that file -->

# `CBEA`: Taxonomic Enrichment Analysis in R <img src='man/figures/hex-CBEA.png' align="right" height="137" />

<!-- badges: start -->

[![Codecov test
coverage](https://codecov.io/gh/qpmnguyen/CBEA/branch/master/graph/badge.svg)](https://codecov.io/gh/qpmnguyen/CBEA?branch=master)
[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![R-CMD-check](https://github.com/qpmnguyen/CBEA/workflows/R-CMD-check-bioc/badge.svg)](https://github.com/qpmnguyen/CBEA/actions)
<!-- [![BioC status](http://www.bioconductor.org/shields/build/release/bioc/CBEA.svg)](https://bioconductor.org/checkResults/release/bioc-LATEST/CBEA) -->
<!-- badges: end -->

### Quang Nguyen

The `CBEA` package provides basic functionality to perform taxonomic
enrichment analysis in R. This package mainly supports the `CBEA`
method, and provides additional support for generating sets for analyses
using approaches commonly used in the gene set testing literature.

### Installation

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("qpmnguyen/CBEA")
```

### Features

This package implements the CBEA approach for performing set-based
enrichment analysis for microbiome relative abundance data. A preprint
of the package can be found [on
bioXriv](https://www.biorxiv.org/content/10.1101/2021.09.07.459294v1.full).
In summary, CBEA (Competitive Balances for taxonomic Enrichment
Analysis) provides an estimate of the activity of a set by transforming
an input taxa-by-sample data matrix into a corresponding set-by-sample
data matrix. The resulting output can be used for additional downstream
analyses such as differential abundance, classification, clustering,
etc. using set-based features instead of the original units.

The transformation that CBEA applies is based on the isometric log ratio
transformation:  

![
CBEA\_{i,\\mathbb{S}} = \\sqrt{\\frac{\|\\mathbb{S}\|\|\\mathbb{S\_c}\|}{\|\\mathbb{S}\| + \|\\mathbb{S\_c}\|}} \\ln \\frac{g(X\_{i,j \| j\\in \\mathbb{S}})}{g(X\_{i,j \| j \\notin \\mathbb{S}})}
](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%0ACBEA_%7Bi%2C%5Cmathbb%7BS%7D%7D%20%3D%20%5Csqrt%7B%5Cfrac%7B%7C%5Cmathbb%7BS%7D%7C%7C%5Cmathbb%7BS_c%7D%7C%7D%7B%7C%5Cmathbb%7BS%7D%7C%20%2B%20%7C%5Cmathbb%7BS_c%7D%7C%7D%7D%20%5Cln%20%5Cfrac%7Bg%28X_%7Bi%2Cj%20%7C%20j%5Cin%20%5Cmathbb%7BS%7D%7D%29%7D%7Bg%28X_%7Bi%2Cj%20%7C%20j%20%5Cnotin%20%5Cmathbb%7BS%7D%7D%29%7D%0A "
CBEA_{i,\mathbb{S}} = \sqrt{\frac{|\mathbb{S}||\mathbb{S_c}|}{|\mathbb{S}| + |\mathbb{S_c}|}} \ln \frac{g(X_{i,j | j\in \mathbb{S}})}{g(X_{i,j | j \notin \mathbb{S}})}
")

Where
![\\mathbb{S}](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmathbb%7BS%7D "\mathbb{S}")
is the set of interest,
![\\mathbb{S}\_C](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;%5Cmathbb%7BS%7D_C "\mathbb{S}_C")
is it’s complement,
![g()](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;g%28%29 "g()")
is the geometric mean operation, and
![X](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;X "X")
is the original data matrix where
![i](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;i "i")
is the index representing samples and
![j](https://latex.codecogs.com/png.image?%5Cdpi%7B110%7D&space;%5Cbg_white&space;j "j")
is the index representing variables (or taxa).

The inference procedure is performed through estimating the null
distribution of the test statistic. This can be done either via
permutations or a parametric fit of a distributional form on the
permuted scores. Users can also adjust for variance inflation due to
inter-taxa correlation. Please refer to the main manuscript for any
additional details.
