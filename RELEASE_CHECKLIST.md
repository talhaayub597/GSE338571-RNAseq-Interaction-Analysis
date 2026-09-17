# GSE338571 Repository Release Checklist

Use this checklist before making the repository a permanent public research resource.

## 1. Author information

- [ ] Confirm the final author list.
- [ ] Confirm each author's affiliation.
- [ ] Confirm the corresponding author's email.
- [ ] Confirm ORCID information where applicable.
- [ ] Replace author placeholders in `CITATION.cff`.

## 2. Repository information

- [ ] Confirm the GitHub repository name.
- [ ] Replace `REPLACE_WITH_GITHUB_REPOSITORY_URL` in `CITATION.cff`.
- [ ] Confirm that the repository is public.
- [ ] Confirm that no passwords, API keys, tokens, or other secrets are present.

## 3. Data

- [ ] Confirm that the source dataset is GSE338571.
- [ ] Confirm that original GEO source data are not unintentionally redistributed.
- [ ] Confirm that the data instructions in `data/README.md` are accurate.
- [ ] Confirm the documented sample order.

## 4. Reproducibility

- [ ] Install dependencies from `requirements.txt`.
- [ ] Run `code/01_reproduce_interaction.py`.
- [ ] Confirm 15,313 retained genes.
- [ ] Confirm 0 interaction genes with FDR < 0.05.
- [ ] Confirm the minimum FDR is approximately 0.559615.
- [ ] Confirm `ENSG00000260526` is the top nominal interaction candidate.
- [ ] Run `code/02_validate_primary_results.py`.
- [ ] Run `code/03_make_audit_summary.py`.
- [ ] Review the generated results.

## 5. Figures

- [ ] Upload all six final corrected figures.
- [ ] Confirm each figure opens correctly.
- [ ] Confirm figure filenames match the manuscript.
- [ ] Confirm every figure is referenced in the manuscript.
- [ ] Confirm figures contain no unintended placeholder content.

## 6. Results

- [ ] Upload the verified derived results that are intended for public release.
- [ ] Confirm the complete interaction result contains 15,313 genes.
- [ ] Confirm the pathway-hit table contains 19 genes.
- [ ] Confirm the coexpression network contains 50 edges.
- [ ] Confirm the audit materials correspond to the final analysis version.

## 7. Scientific wording

- [ ] State that no individual interaction gene passed FDR < 0.05.
- [ ] Describe cell cycle and homologous recombination as pathway-level findings.
- [ ] Use "pathway-hit genes" or "rank-prioritized pathway-associated genes".
- [ ] Do not describe the pathway-hit genes as formal GSEA leading-edge genes.
- [ ] Describe Network #5 as a Pearson coexpression network.
- [ ] Do not describe Network #5 as a PPI network.
- [ ] Do not claim that the analysis establishes causality.
- [ ] Describe GSE62208 as independent biological context rather than exact replication.

## 8. Version control

- [ ] Review all files before release.
- [ ] Commit the complete repository.
- [ ] Use a clear commit message.
- [ ] Create the first versioned release as `v1.0.0`.
- [ ] Record the release date.

## 9. DOI and archival

- [ ] Connect the public repository to Zenodo or another appropriate archival service.
- [ ] Archive the exact `v1.0.0` release.
- [ ] Confirm that the archive was successfully created.
- [ ] Record the DOI actually issued by the archive.
- [ ] Update the manuscript with the permanent repository URL and DOI.

## 10. Final verification

- [ ] Clone the public repository into a clean environment.
- [ ] Install dependencies.
- [ ] Run the reproduction script from the cloned repository.
- [ ] Run the validation script.
- [ ] Confirm that the documented primary results are reproduced.
- [ ] Confirm that the repository contains no private or confidential material.
- [ ] Confirm that the repository URL in the manuscript is correct.

## Important

Do not claim that a permanent DOI exists until an archival service has actually issued one.

Do not claim that the repository reproduces an analysis unless the reproduction workflow has been successfully executed and checked.
