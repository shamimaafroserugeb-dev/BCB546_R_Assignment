# BCB 546: R Assignment - Maize and Teosinte SNP Analysis

## Project Overview

This project performs a genome-wide analysis of SNP variation between domesticated Maize and its wild relative, Teosinte. The analysis includes data cleaning, chromosomal subsetting, and visualizations of genetic diversity (heterozygosity) and marker distribution.

## Directory Structure and File Descriptions

* `BCB546_R_Assignment.Rmd`: The primary R Markdown script containing the code for data processing and visualization.
* `BCB546_R_Assignment.pdf`: The final knitted report.
* `fang_et_al_genotypes.txt`: Raw genotype data for various Zea mays groups.
* `snp_position.txt`: Metadata containing physical coordinates (Chromosome and Position) for each SNP.
* `README.md`: Project documentation (this file).
* `output/` folder has `figures`, `maize` and `teosinte` folders (Containing your 40 organized text files), Details below

* The analysis generates a total of 40 output files, organized by taxon and genomic ordering


| Taxon  | Ordering  | Missing Data Symbol | File Count  | Filename Pattern |
|---|---|---|---|---|
| Maize  | Increasing  | ? | 10  | maize_chr[1-10]_increasing.txt |
| Maize  | decreasing  | - | 10  | maize_chr[1-10]_decreasing.txt |
| Teosinte  | Increasing  | ? | 10  | teosinte_chr[1-10]_increasing.txt |
| Teosinte  | decreasing  | - | 10  | teosinte_chr[1-10]_decreasing.txt |

Each group contains 10 files, one for each of the 10 chromosomes of Zea mays:

Increasing Files: Sorted by physical position (ascending). Missing genotypes are left as `?/?`.

Decreasing Files: Sorted by physical position (descending). Missing genotypes are re-encoded as `-/-` to satisfy assignment requirements.


## Data Processing Workflow

### 1. R Analysis

The R script executes the following steps:

1. **Data Inspection**: Checks dimensions and structure of raw files.
2. **Subsetting**: Extracts specific groups (Maize: `ZMMIL`, `ZMMLR`, `ZMMMR`; Teosinte: `ZMPBA`, `ZMPIL`, `ZMPJA`).
3. **Transposition**: Rotates the genotype data to allow merging with SNP positions.
4. **File Generation**: Produces 40 output files (10 per chromosome for each taxon) with specific encodings for missing data (`?` for increasing order and `-` for decreasing order).
5. **Visualization**:
* SNP distribution across the 10 chromosomes.
* Proportions of Homozygous, Heterozygous, and Missing data.
* Genotype status across the genomic landscape, faceted by taxon.



### 2. Unix Organization

After the R script generated the 40 chromosomal files, Unix commands were used to organize the workspace for better accessibility and cleaner directory management.

```bash
# Example of organization commands used:
mkdir -p output/maize output/teosinte
mv maize_chr* output/maize/
mv teosinte_chr* output/teosinte/

```

## How to Reproduce this Analysis

1. Ensure `R`, `RStudio`, and the `tidyverse` suite are installed.
2. Place the raw data files (`fang_et_al_genotypes.txt` and `snp_position.txt`) in the same directory as the `.Rmd` file.
3. Open `R_Assignment.Rmd` and click the **Knit** button.
4. All visualizations will appear in the resulting PDF, and the 40 text files will be generated in the working directory.

## Author

**Prince Ameyaw** March 2026

---

