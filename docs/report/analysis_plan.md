# Reproduction of Vijayan et al 2020 Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County

### Authors

- Katie Heo, jheo@middlebury.edu, @katieheo, Middlebury College
- Alex Xu, yidex@middlebury.edu, @alexxuyide, Middlebury College

### Abstract

Write a brief abstract about your research project.

This study is a *reproduction* study of:

> Vijayan, T., M. Shin, P. C. Adamson, C. Harris, T. Seeman, K. C. Norris, and D. Goodman-Meza. 2020. Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County. Clinical Infectious Diseases 73 (9):e2970–e2975. DOI: 10.1093/cid/ciaa1692

> Kedron, P., Bardin, S., Holler, J., Gilman, J., Grady, B., Seeley, M., Wang, X. and Yang, W. (2023), A Framework for Moving Beyond Computational Reproducibility: Lessons from Three Reproductions of Geographical Analyses of COVID-19. Geogr Anal. https://doi.org/10.1111/gean.12370

### Study metadata

- `Key words`: Comma-separated list of keywords (tags) for searchability. Geographers often use one or two keywords each for: theory, geographic context, and methods.
- `Subject`: select from the [BePress Taxonomy](http://digitalcommons.bepress.com/cgi/viewcontent.cgi?article=1008&context=reference)
- `Date created`: date when project was started
- `Date modified`: date of most recent revision
- `Spatial Coverage`: Specify the geographic extent of your study. This may be a place name and link to a feature in a gazetteer like GeoNames or OpenStreetMap, or a well known text (WKT) representation of a bounding box.
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study, e.g. EPSG:4326
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant
- `Award info URI`: web address for award information
- `Award number`: award number

#### Original study spatio-temporal metadata

- `Spatial Coverage`: extent of original study
- `Spatial Resolution`: resolution of original study
- `Spatial Reference System`: spatial reference system of original study
- `Temporal Coverage`: temporal extent of original study
- `Temporal Resolution`: temporal resolution of original study

## Study design

Describe how the study relates to prior literature, e.g. is it a **original study**, **meta-analysis study**, **reproduction study**, **reanalysis study**, or **replication study**?

Also describe the original study archetype, e.g. is it **observational**, **experimental**, **quasi-experimental**, or **exploratory**?

Enumerate specific **hypotheses** to be tested or **research questions** to be investigated here, and specify the type of method, statistical test or model to be used on the hypothesis or question.

## Materials and procedure

### Computational environment

We are working on R (version 4.3.1). 

Define the hardware, operating system, and software requirements for the research.
Include citations to important software projects, plugins or packages and their versions.

### Data and variables

All data used in the study is secondary. The data sources are the 2018 5-year American Community Survey (U.S. Census) and LAC Department of Public Health COVID-19 surveillance dashboard. 
Predictor variables were obtained from the 2018 5-year American Community Survey at the census tract level. Syndrome Coronavirus 2 (SARS-CoV-2) or COVID-19 testing and diagnosis data were obtained from the LAC Department of Public Health COVID-19 surveillance dashboard (http://dashboard.publichealth. lacounty.gov/covid19_surveillance_dashboard/) through 30 June 2022.

**Standard Metadata**
- `Title`: COVID-19 Data from Los Angeles, California in 2020
- `Abstract`: Predictor variables were obtained from the 2018 5-year American Community Survey at the census tract level. Syndrome Coronavirus 2 (SARS-CoV-2) or COVID-19 testing and diagnosis data were obtained from the LAC Department of Public Health COVID-19 surveillance dashboard (http://dashboard.publichealth. lacounty.gov/covid19_surveillance_dashboard/) through 30 June 2022.
- `Spatial Coverage`: Los Angeles County (LAC), California
- `Spatial Resolution`: The total area of the hexagons are 4380 squared kilometers, each being 10 square kilometers. 
- `Spatial Reference System`: ESPG:32611
- `Temporal Coverage`: The census data was from 2018 and the LAC public health data was from the start of the pandemic to 30 June 2022. 
- `Lineage`:
  - Census data was obtained at the tract level.
  - With the 2018 5-year American Community Survey (U.S. Census) and LAC Department of Public Health COVID-19 surveillance dashboard data, Vijayan et al. created a grid of hexagons. The authors did not provide any details about the algorithm or parameters used to create the grid.
  - Each hexagon in the grid encompassed an area of 10 square kilometers. Once created, the grid was overlaid onto the centroids of city, community, and census tract boundaries within LAC, and all data were summarized and joined to the hexagon layer by location. Hexagons that either contained missing COVID-19 data, had a population of less than 1,000 people, or did not have contiguous neighbors were excluded from the analysis.
  - The initial analysis sample contained 184 hexagons. However, we recreated the hexagon layer to contain the contiguous neighbors so that it did not have any gaps. Our final analysis sample contained 188 hexagons.
- `Distribution`: U.S. Census and the LAC Department of Public Health
- `Constraints`: No legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: We don't have access to the raw data from U.S. census, we got the already aggregated data to work with from the reproduction study. 
- `Variables`: 

| Label | Alias | Definition | Type | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| DP05_0019P | age18 | percent of population below 18 | float | [6.45, 33.1] | FID number 19, 434, and 437 were reported as NULL. We found the median value of all hexagons to replace these NULL values. | 0.016 |
| DP05_0024P | age65 | percent of population above 65 | float | [5.88, 34.2] | FID number 19, 434, and 437 were reported as NULL. We found the median value of all hexagons to replace these NULL values. | 0.016 | 
| DP05_0071P | latino | percent of Latino population | float | [2.75, 98.18] | - | - | 
| DP05_0037P | white | percent of White population | float | [10.57, 88.6] | - | - | 
| DP05_0038P | black | percent of Black population | float | [0, 67.39] | - | - |
| DP05_0044P | asian | percent of Asian population | float | [0.2, 75.51] | - | - | 
| DP03_0119P | poverty | percent of population in poverty | float | [0.55, 33.69] | - | - | 
| DP03_0099P | uninsured | percent of uninsured population | float | [1, 26.02] | - | - | 
| DP02_0067P | bachelor | percent of population with bachelor's degrees | float | [4.79, 85.2] | - | - | 
| DP05_0001E | pop.tot | population total | integer | [1092, 134718] | - | - |
| DP05_0086E | hh_tot | household total | integer | [535, 52972] | - | - |
| tested630_ | tests | accumulated test conducted since the start of covid | integer | [36, 19819] | - | - |
| cases630_s | cases | accumulated cases since the start of covid | integer | [0, 2964] | - | - |
| fid | fid | hexagon ID number | integer | [14, 438] | - | - |
| areasqkm | area | area in squared kilometers | float | [10.01, 10.02] | - | - | 
| adjdrt630_ | adjdrt | age adjusted diagnosed rate | float | [0, 411] | - | - | 
| adjtrt630_ | adjtrt | age adjusted testing rate | float | [1428, 98183] | - | - | 
| Westside | westside | undefined and unused in code | Boolean | [0, 1] | - | - | 
| pop.dens | pop.dens | population density | float | [109.2, 13471.8] | - | - |
| hh.dens | hh.dens | household density | float | [1.47, 4.43] | - | - | 
| prt | prt | crude positivity rates | float | [0, 23.3] | - | - | 
| prt_level | prt_level | variable created to fill values later | 0 | [0] | - | - | 

  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Domain`: Expected range of Maximum and Minimum of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: NULL values reported three times. We found the median value of all hexagons to replace these NULL values. 

### Prior observations  

Prior experience with the study area, prior data collection, or prior observation of the data can compromise the validity of a study, e.g. through p-hacking.
Therefore, disclose any prior experience or observations at the time of study pre-registration here, with example text below:

At the time of this study pre-registration, the authors had _____ prior knowledge of the geography of the study region with regards to the ____ phenomena to be studied.
This study is related to ____ prior studies by the authors

For each primary data source, declare the extent to which authors had already engaged with the data:

- [ ] no data collection has started
- [ ] pilot test data has been collected
- [ ] data collection is in progress and data has not been observed
- [ ] data collection is in progress and __% of data has been observed
- [ ] data collection is complete and data has been observed. Explain how authors have already manipulated / explored the data.

For each secondary source, declare the extent to which authors had already engaged with the data:

- [ ] data is not available yet
- [ ] data is available, but only metadata has been observed
- [ ] metadata and descriptive statistics have been observed
- [ ] metadata and a pilot test subset or sample of the full dataset have been observed
- [ ] the full dataset has been observed. Explain how authors have already manipulated / explored the data.

If pilot test data has been collected or acquired, describe how the researchers observed and analyzed the pilot test, and the extent to which the pilot test influenced the research design.

### Bias and threats to validity

Given the research design and primary data to be collected and/or secondary data to be used, discuss common threats to validity and the approach to mitigating those threats, with an emphasis on geographic threats to validity.

These include:
  - uneven primary data collection due to geographic inaccessibility or other constraints
  - multiple hypothesis testing
  - edge or boundary effects
  - the modifiable areal unit problem
  - nonstationarity
  - spatial dependence or autocorrelation
  - temporal dependence or autocorrelation
  - spatial scale dependency
  - spatial anisotropies
  - confusion of spatial and a-spatial causation
  - ecological fallacy
  - uncertainty e.g. from spatial disaggregation, anonymization, differential privacy

### Data transformations

Describe all data transformations planned to prepare data sources for analysis.
This section should explain with the fullest detail possible how to transform data from the **raw** state at the time of acquisition or observation, to the pre-processed **derived** state ready for the main analysis.
Including steps to check and mitigate sources of **bias** and **threats to validity**.
The method may anticipate **contingencies**, e.g. tests for normality and alternative decisions to make based on the results of the test.
More specifically, all the **geographic** and **variable** transformations required to prepare input data as described in the data and variables section above to match the study's spatio-temporal characteristics as described in the study metadata and study design sections.
Visual workflow diagrams may help communicate the methodology in this section.

Examples of **geographic** transformations include coordinate system transformations, aggregation, disaggregation, spatial interpolation, distance calculations, zonal statistics, etc.

Examples of **variable** transformations include standardization, normalization, constructed variables, imputation, classification, etc.

Be sure to include any steps planned to **exclude** observations with *missing* or *outlier* data, to **group** observations by *attribute* or *geographic* criteria, or to **impute** missing data or apply spatial or temporal **interpolation**.

### Analysis

Describe the methods of analysis that will directly test the hypotheses or provide results to answer the research questions.
This section should explicitly define any spatial / statistical *models* and their *parameters*, including *grouping* criteria, *weighting* criteria, and *significance thresholds*.
Also explain any follow-up analyses or validations.

## Results

Describe how results are to be presented.

## Discussion

Describe how the results are to be interpreted *vis a vis* each hypothesis or research question.

## Integrity Statement

Include an integrity statement - The authors of this preregistration state that they completed this preregistration to the best of their knowledge and that no other preregistration exists pertaining to the same hypotheses and research.
If a prior registration *does* exist, explain the rationale for revising the registration here.

## Acknowledgements

- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant
- `Award info URI`: web address for award information
- `Award number`: award number

This report is based upon the template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## References
