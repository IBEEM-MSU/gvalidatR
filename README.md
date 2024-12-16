
<!-- README.md is generated from README.Rmd. Please edit that file -->

# gvalidatorR

### Developed as part of the [MSU Institute for Biodiversity, Ecology, Evolution, and Macrosystems (IBEEM)](https://ibeem.msu.edu)   github: https://github.com/IBEEM-MSU

<!-- badges: start -->

[![Lifecycle:
experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html#experimental)
[![CRAN
status](https://www.r-pkg.org/badges/version/commruleR)](https://CRAN.R-project.org/package=commruleR)
<!-- badges: end -->

*This is very early version under heavy development.*

## Motivation

Team research projects often require a shared process to enter complex data, in particular liteture reviews 
and [meta-analyses](https://en.wikipedia.org/wiki/Meta-analysis) that collects and harmonizes quantitative data from multiple publications to 
synthesize a new analyses.    However there are few off-the shelf tools that help design the data structures and collaboratively enter tabuluar data, 
both quantitative and qualitative. 

Hence most teams turn to spreadsheet tools to design their data models and enter data, such as Microsoft Office and Google Sheets.  On-line tools are 
especially effective for collaboration.  Ultimately the data entered into a spreadsheet must be exported to a format readable by systems used for analysis, such as R or Python.   Meta-analysis research projects frequently employ iterative design, where the structure of the data, the protocols and analyses are adjusted as it's discovered.   This requires then repeated export of data and import into 
the analysis system.  For teams of even modest size with several dozens of data sheets this process 
can be time consuming an error prone. 

In addition, spreadsheets do not offer a seamless way to record the process, or provenance of the data as entered or 
the many changes made to correct errors, adjusted protocols or miscommunications.     For that we've found that 
employing git version control on tabular, text-based data files such as CSV format gives a way to add communication to 
changes as they happen in data sheets and in fact in protocols. 

Hence our goal was to explore ways automate data transfer from binary or on-line formats of spreadsheets into text-based format so that we may git and github to track and communicate changes to the data. 

## Overview

The goal of the small R package to is help a collaborative research team design and enter data using Google Sheets but
then use git to help document changes to these data sheets, and validate the data along the way. 

This R package primarily combines the excellent packages [gsheets]() and [validate] in a workflow that pulls the data 
out of google sheets given a list of URLs, validates the data given a set of column formats and validation rules, and
saves as CSV for commiting to a git repository and pushing up to a shared git server (for example github).   

This is research-agnostic but was originally designed and developed  as part of git repositories that support the data entry,
validation, and accumulation of data for collaborative meta-analysis project.  A goal of this package is to adhere to the 
scheme of [data processing levels](https://edirepository.org/resources/cleaning-data-and-quality-control#data-processing-levels) 
defined by the [Environmental Data Initiative](https://edirepository.org) to aid in creating a data package for their repository. 

This package fits into the following workflow:

1.  data entry using google sheets: data templates, data sheets and data definitions (fields, lists,etc)
    the origin of this project was data pulled from a literature review / meta anlaysis based on prism
2.  data transform and validation (this package): read in data from list of google sheets urls,
    validate using data defintions from step 1, export to CSV files
3.  data accumulation using git.   The validated CSV outputs from 3 are commited and pushed
    into a 'data' repository that can then use git for tracking data provenance.  this is the "L0"
    data layer in the EDI data framework. 
4.  data analysis:  a final repository that contains code the reads data from L0, wrangles the
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
- inside the Rstudio project in the R console,
-  `renv::restore()`
