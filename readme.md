<div align=center><img width="300" height="320" src="https://github.com/Gavin-Yinld/csmFInder/blob/master/figures/csmFinder.gif"/></div>

# csmFinder

# Introduction

csmFinder is an R package for identifying putative cell-subset specific methylation (pCSM) loci from methylation datasets generated by single cells or bulk tissue. For single cell methylomes, it uses beta mixture model to identify the genomic loci with bipolar methylation pattern across single cells. For bulk methylomes, a nonparametric Bayesian clustering algorithm is used for grouping the sequence reads into hyper- and hypo-methylated subset and determining the genomic loci with significant difference bwtween two subsets as so called pCSM loci. 

The package includes two main function modules, the first one identify pCSM loci from bismark output file. The other perform co-methylation analysis and extract eigen-pCSM loci from each co-methylation module.

# Current Features
* Generate 4-CpG segments from bismark extractor results
* Identify candidate segments covered by totally methylated and unmethylated reads (or single cells)
* Identify pCSM 4-CpG segments with bipolar methylation pattern
* Merge pCSM segments to pCSM loci
* Calculate methylation level in pCSM loci
* Co-methylation analysis to cluster pCSM loci with similar methylation pattern into co-methylated modules
* PCA analysis to extract eigen-pCSM loci representing methylation trend of ecah co-methylation module

# Installation
csmFinder needs the following tools to be installed and available in the `PATH` environment:
1.  [R](https://www.r-project.org/)(>=3.4.4)
2.  [python2](https://www.python.org/downloads/) (>=2.7.10), to process the bismark extractor results
3.  [bedtools2](https://github.com/arq5x/bedtools2) (>=2.28.0), to merge the overlapped pCSM segments into pCSM loci

In R console,
```R
source("http://bioconductor.org/biocLite.R")
biocLite(c("GenomicRanges","WGCNA"))
library("devtools")
devtools::install_github(c("PhanstielLab/bedtoolsr","Gavin-Yinld/csmFinder"))
```
# How to Use

## Step 1. Process bismark extractor result  to 4-CpG segment
Typically, bisulfite converted reads are aligned to the genome by processing alignments. `csmFinder` takes that methylation value per base information in each sequence read as input. Such input file may be obtained from `bismark` pipeline, a typical input file should in ".gz" compressed format and looks like this:
```ST-E00523:376:HL7JTCCXY:4:1102:23054:14494_1:N:0:ATGAGCAT + chr1  3023890 Z
ST-E00523:376:HL7JTCCXY:4:1102:23054:14494_1:N:0:ATGAGCAT + chr1  3023859 Z
ST-E00523:376:HL7JTCCXY:4:1107:31730:36592_1:N:0:ATGAGCAT + chr1  3023890 Z
ST-E00523:376:HL7JTCCXY:4:1107:31730:36592_1:N:0:ATGAGCAT + chr1  3023859 Z
ST-E00523:376:HL7JTCCXY:4:1204:29305:15232_1:N:0:ATGAGCAT + chr1  3022537 Z
```






