# Reproduction of Vijayan et al 2020 Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County

This study is a *reproduction* study of:

> Vijayan, T., M. Shin, P. C. Adamson, C. Harris, T. Seeman, K. C. Norris, and D. Goodman-Meza. 2020. Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County. Clinical Infectious Diseases 73 (9):e2970–e2975. DOI: 10.1093/cid/ciaa1692

> Kedron, P., Bardin, S., Holler, J., Gilman, J., Grady, B., Seeley, M., Wang, X. and Yang, W. (2023), A Framework for Moving Beyond Computational Reproducibility: Lessons from Three Reproductions of Geographical Analyses of COVID-19. Geogr Anal. https://doi.org/10.1111/gean.12370


## Contributors

- Peter Kedron
- Joseph Holler
- Sarah Bardin
- Joshua Gilman
- Bryant Grady
- Megan Seeley
- Xin Wang
- Wenxin Yang
- Alex Xu
- Katie Heo

## Abstract

This study replicates and extends the spatial analysis conducted by Vijayan et al. (2020) on SARS-CoV-2 outcomes in Los Angeles County (LAC). Vijayan et al. (2020) examined whether spatial patterns existed in SARS-CoV-2 age-adjusted testing rates, age-adjusted diagnosis rates, and crude positivity rates in Los Angeles County (LAC), utilizing a hexagonal grid to explore associations between COVID-19 crude positivity rates and a series of predictor variables. However, issues with the grid's connectivity prompted the creation of a new grid for this reproduction. The study also addressed data imputation challenges in variables 'age18' and 'age65'. Using R and spatial analysis packages, we performed LISA analyses, reproducing clusters for testing rates, diagnosis rates, and positivity rates. The spatial lag models were replicated to assess predictors' effects on crude positivity rates, age-adjusted diagnosis rates, and age-adjusted testing rates. Our results provides insights into spatial patterns and predictors of SARS-CoV-2 outcomes in Los Angeles County.

## Study Metadata

- Key words: COVID-19, health disparity, geography, methods
- Subject: Medicine and Health Sciences, Public Health, Epidemiology
- Date created: 2020
- Date modified: 2023, November
- `Spatial Coverage`: Specify the geographic extent of your study. This may be a place name and link to a feature in a gazetteer like GeoNames or OpenStreetMap, or a well known text (WKT) representation of a bounding box.
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant
- `Award info URI`: web address for award information
- `Award number`: award number

## Related to

- `OSF Project`:
- `Pre-analysis Registration`:
- `Post-analysis Report Registration`:
- `Preprint`:
- `Conference Presentation`:
- `Publication`:
- `Prior Study`:
- `...`:

## Metadata for access

- `Rights`: [LICENSE](LICENSE): BSD 3-Clause "New" or "Revised"
- `Resource type`: Collection
- `Resource language`: English
- `Conforms to`: Template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences version 1.0, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## Compendium structure and contents

This research compendium is structured with four main directories:
The contents of this repository are outlined in three tables:
- Data: contains subdirectories for `raw` data and `derived` data.
- Docs: contains subdirectories for 'manuscript','presentation', and 'report'
- Procedures: contains subdirectories for `code` or software scripts, information about the computational `environment` in which the research was conducted, and non-code research `protocols`
- Results: contains subdirectories for `figures`, formatted data `tables`, or `other` formats of research results.

Important local **documents** include:
- [Pre-analysis plan](docs/report/preanalysis.md)
- [Study report](docs/report/index.html)

#### Compendium reference

The [template_readme.md](template_readme.md) file contains more information on the design and rationale of this research template repository and references used in the design.

The [Template_LICENSE](Template_LICENSE) file provides the BSD 3-Clause license for using this template.

The template used can be found at [template_reference.bib](template_reference.bib) or:
> Kedron, P., & Holler, J. (2023). Template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences. https://doi.org/10.17605/OSF.IO/W29MQ
