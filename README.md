# README

# Acute Myeloid Leukemia Heatmap Analysis

A bioinformatics analysis pipeline for visualizing RNA-seq expression patterns in Acute Myeloid Leukemia (AML) samples using clustering heatmaps.

## Overview

This analysis uses RNA-seq data from 19 AML model mice samples 
 to identify patterns of gene expression across different treatment conditions. The pipeline processes quantile-normalized data from [refine.bio](https://www.refine.bio/) and generates annotated heatmaps to visualize expression patterns.

## Requirements

### R Packages

* `pheatmap` for heatmap visualization
* `magrittr` for data manipulation
* `readr` for data import
* `dplyr` for data processing
* `tibble` for data manipulation
* `sessioninfo` for environment reporting

### Data Requirements

* RNA-seq expression data (TSV format)
* Sample metadata (TSV format)
* Pre-processed and quantile-normalized data

## Installation

```r
# Install required packages
if (!("pheatmap" %in% installed.packages())) {
  install.packages("pheatmap")
}
if (!("magrittr" %in% installed.packages())) {
  install.packages("magrittr")
}
if (!("readr" %in% installed.packages())) {
  install.packages("readr")
}
if (!("dplyr" %in% installed.packages())) {
  install.packages("dplyr")
}
if (!("tibble" %in% installed.packages())) {
  install.packages("tibble")
}
if (!("sessioninfo" %in% installed.packages())) {
  install.packages("sessioninfo")
}
```

## Usage

1. Clone the repository:
```bash
git clone https://github.com/your-username/aml-heatmap-analysis.git
```

2. Create required directories:
```r
# Create necessary directories
dir.create(c("data", "plots", "results"), showWarnings = FALSE)
```

3. Download data from [refine.bio](https://www.refine.bio/experiments/SRP070849) and place in the `data` directory.

4. Run the analysis pipeline:
```r
# Load required libraries
library(pheatmap)
library(magrittr)
library(readr)
library(dplyr)
library(tibble)
library(sessioninfo)

# Set random seed for reproducibility
set.seed(12345)
```

## Analysis Pipeline

The pipeline performs the following steps:

1. Data Import
   - Reads expression data and metadata
   - Ensures consistent sample ordering

2. Gene Selection
   - Calculates gene variance
   - Selects top 25% most variable genes
   - Saves selected genes to results directory

3. Heatmap Generation
   - Creates annotated heatmap
   - Includes sample metadata
   - Uses custom color scheme
   - Saves visualization to plots directory

## Output Files

* `results/top_90_var_genes.tsv`: Selected genes by variance
* `plots/aml_heatmap.png`: Final heatmap visualization
* Session information report

## Citation

This analysis uses data from Shih et al., 2017 
, which investigated IDH2 and TET2 mutant AML models treated with AG-221 and 5-Azacytidine respectively.

## Contributing

Contributions are welcome. Please:
1. Fork the repository
2. Make changes in a feature branch
3. Submit a pull request with detailed changes
4. Include updated documentation if necessary

## License

[MIT License](LICENSE)

## Acknowledgments

This analysis was adapted from the [refine.bio-examples notebook](https://alexslemonade.github.io/refinebio-examples/03-rnaseq/clustering_rnaseq_01_heatmap.html) and modified for this repository by Candace Savonen.
