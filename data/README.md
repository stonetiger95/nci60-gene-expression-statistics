# Data access and redistribution

This repository does not redistribute a raw NCI-60 data file.

The analysis loads `NCI60` from the CRAN package `ISLR2`:

```r
install.packages("ISLR2")
data("NCI60", package = "ISLR2")
```

`NCI60$data` contains 64 cell lines × 6,830 expression variables, and `NCI60$labs` contains the cancer-type labels. The focused analysis selects 40 cell lines from five types.

## Provenance

- CRAN package: https://cran.r-project.org/package=ISLR2
- Dataset help page: https://search.r-project.org/CRAN/refmans/ISLR2/html/NCI60.html
- Original study: Ross et al. (2000), *Nature Genetics*, https://doi.org/10.1038/73432
- Public NCBI GEO record for the NCI-60 expression study: https://www.ncbi.nlm.nih.gov/sites/GDSbrowser?acc=GDS1761

## License decision

`ISLR2` is distributed under GPL-2, but the package documentation does not state a separate, explicit redistribution license for the underlying original dataset. To avoid implying broader rights, this public repository includes only analysis code and retrieval instructions. The repository MIT License applies only to original code and documentation, not to third-party data.

