
<!-- README.md is generated from README.Rmd. Please edit that file -->

# gvalidatorR

### Developed as part of the  [MSU IBEEM](https://ibeem.msu.edu)

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/commruleR)](https://CRAN.R-project.org/package=commruleR)
<!-- badges: end -->

*This is very early version under heavy development.*

## Overview

This R package was design as part of git repositories that support the data entry,
validation, and accumulation of data for collaborative meta-analysis 
projects that are depend on Google Sheets for daa entry.  This package
fits into this workflow as part of the EDI 

1.  data entry using google sheets: data templates, data sheets and data definitions (fields, lists,etc)
    the origin of this project was data pulled from a literature review / meta anlaysis based on prism
2.  data transform and validation (this package): read in data from list of google sheets urls,
    validate using data defintions from step 1, export to CSV files
3.  data accumulation using git.   The validated CSV outputs from 3 are commited and pushed
    into a 'data' repository that can then use git for tracking data provenance.  this is the "L0"
    data layer in the EDI data framework. 
5.  data analysis:  a final repository that contains code the reads data from L0, wrangles the
    data as necessary to pull into single data file and performs analysis/visualizations.
    this corresponds to the L1 layer in the EDI data framework

## Installation

This package uses [renv](https://rstudio.github.io/renv/) to manage the
packages you need to install, which creates an `renv.lock` file for you.

- install RENV: this can go into your R environment used for all
  packages, so fire up R with now project select and
  `install.packages('renv')`
- clone this repository into a [new Rstudio
  project](https://docs.posit.co/ide/user/ide/guide/code/projects.html)
  and open it
- inside the Rstudio project in the R console, `renv::restore()`
