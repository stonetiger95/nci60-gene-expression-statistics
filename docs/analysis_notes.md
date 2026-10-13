# Analysis notes and audit trail

## Scope

This repository preserves the actual coursework methods without adding a new predictive model or retuning results. The focused data are five cancer types (40 cell lines) and 6,830 expression variables from `ISLR2::NCI60`.

## Preserved methods

- One-way ANOVA across five cancer types for each variable
- Benjamini-Hochberg adjustment as a later portfolio review check
- Euclidean hierarchical clustering with the coursework linkage comparison
- K-means with K = 5 and `nstart = 50` on the top 20 raw-p-ranked variables
- PCA of the standardized expression matrix
- 1,000-resample bootstrap interval for the leading-two-eigenvalue share of the resampled cell-line correlation matrix
- 1,000 label permutations for association tests on the first 20 PCs

## Corrections made during portfolio reconstruction

1. Duplicate standardization in the original third assignment was reduced to one explicit variable-wise standardization.
2. K-means now uses a fixed seed.
3. A between-type correlation summary retains the sign of the correlation with the largest absolute magnitude.
4. The top 20 are consistently labeled as a raw-p-ranked exploratory set.
5. The BH calculation is explicitly identified as a post-coursework portfolio review, not part of the original third assignment.
6. Personal names, student numbers, local usernames, submission metadata, and absolute paths were removed.

## Interpretation guardrails

- A raw p-value ranking is not an FDR-controlled discovery list.
- Feature selection used the same samples and labels later used to describe K-means agreement. This creates optimistic, in-sample evidence and is not classification validation.
- Complete linkage is discussed only as relatively aligned with labels in this dataset—not universally best.
- Component-wise permutation p-values are unadjusted across 20 PCs, so a multiple-testing limitation remains.
- Variable ID `282` is a matrix column identifier, not an asserted gene symbol or biomarker.
- NCI-60 cell lines do not constitute a patient cohort.

## Key reproduced values

| Quantity | Reproduced result |
|---|---:|
| Selected observations | 40 |
| Expression variables | 6,830 |
| BH-adjusted p < 0.05 | 1,437 |
| BH-adjusted p < 0.10 | 2,169 |
| Coursework-defined leading-two-eigenvalue bootstrap interval | 22.12480%–30.07429% |
| Unadjusted permutation p < 0.05 | PC1, PC2, PC3, PC5, PC9 |
| Largest leave-one-variable-out K-means change | ID 282; 18.205 (rounded) |

The README rounds these values only for presentation; the analysis report prints the calculated values.

