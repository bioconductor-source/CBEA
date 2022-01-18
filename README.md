
<!-- README.md is generated from README.Rmd. Please edit that file -->

# `CBEA`: Taxonomic Enrichment Analysis in R <img src='man/figures/hex-CBEA.png' align="right" height="137" />

<!-- badges: start -->

[![Codecov test
coverage](https://codecov.io/gh/qpmnguyen/CBEA/branch/master/graph/badge.svg)](https://codecov.io/gh/qpmnguyen/CBEA?branch=master)
[![Project Status: Active – The project has reached a stable, usable
state and is being actively
developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![R-CMD-check](https://github.com/qpmnguyen/CBEA/workflows/R-CMD-check-bioc/badge.svg)](https://github.com/qpmnguyen/CBEA/actions)
[![BioC
status](http://www.bioconductor.org/shields/build/release/bioc/CBEA.svg)](https://bioconductor.org/checkResults/release/bioc-LATEST/CBEA)
<!-- badges: end -->

### Quang Nguyen

The `CBEA` package provides basic functionality to perform taxonomic
enrichment analysis in R. This package mainly supports the `CBEA`
method, and provides additional support for generating sets for analyses
using approaches commonly used in the gene set testing literature.

**This package is under ongoing development and might not be stable at
the moment. Only install the development version if R CMD CHECK badge is
green (passed) or if the error is due to dependency installation.**

### Installation

And the development version from [GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("qpmnguyen/CBEA")
```

### Features

This package supports the implementation of the CBEA approach (formerly
known as cILR) for taxonomic enrichment analysis.

### Dependency Graph

<img src="man/figures/dep.png" width="100%" />
