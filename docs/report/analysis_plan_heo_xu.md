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
The packages we used are 'sf', 'tidyverse', 'ggplot2', 'here', 'spdep', 'spatialreg', 'car', 'ggmap', and 'dplyr'. 

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
| adjdrt630_ | (formerly) adjdrt | age adjusted death rate | float | [0, 411] | - | - | 
| adjcrt630_ | adjdrt | age adjusted case rate | float | [0, 8919] | - | - | 
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

At the time of this study pre-registration, we, the authors, had 0 prior knowledge of the geography of the study region with regards to the COVID positive rates distribution in regards to various demographics phenomena to be studied.
This study is related to 0 prior studies by the authors. 
After acquiring the secondary data, we observed the full dataset and were able to explore the data by altering the shapefile and correcting the hexagon grids connectivity. 

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

We do not intend to transform data or use data from different data sources to what are provided from the Vijayan et al. study. Our goal is to create a hexagonal grid that overlays the data better as to not create gaps between the hexagons for a more accurate presentation of the data. 
The original analyses are retrospective and use observational data collected from federal and private sources. Although not publicly available, we were able to obtain the original study data after contacting the authors. However, the analysis code was not made available, nor was information about the computational environment used.

### Analysis

The major difference we intend to make in the study is the hexagonal grid. We found that in the original study's hexagon grid, many adjacent hexagons have gaps between them or have overlap with each other, affecting the result of spatial regression. Hence, we decided to create a new hexagon grid that fixed the connectivity problem of the hexagon grid in the original study.

Sampling Plan and Data Description: Vijayan et al. collected data from online, publicly available datasets.
Predictor variables were obtained from the 2018 5-year American Community Survey at the census tract level. Syndrome Coronavirus 2 (SARS-CoV-2) or COVID-19 testing and diagnosis data were obtained from the LAC Department of Public Health COVID-19 surveillance dashboard (http://dashboard.publichealth. lacounty.gov/covid19_surveillance_dashboard/) through 30 June 2022. 
Prior to analysis, the data were reapportioned to a hexagonal grid created by the authors. However, the authors provided limited details about how the hexagonal grid was generated. The authors did not provide any details about the algorithm or parameters used to create the grid. Each hexagon in the grid encompassed an area of 10 square kilometers. Once created, the grid was overlaid onto the centroids of city, community, and census tract boundaries within LAC, and all data were summarized and joined to the hexagon layer by location. Hexagons that either contained missing COVID-19 data, had a population of less than 1,000 people, or did not have contiguous neighbors were excluded from the analysis. The final analysis sample contained 184 hexagons. 
Variables: Predictor variables used in the spatial regression analysis included measures of: race/ethnicity, poverty, insurance status, educational status, population density and household density. The percentage of those under the age of 18 and above the age of  65 were also assessed in relation to COVID-19 positivity rates. 
●	Race/ethnicity was expressed as a percentage of the population and segmented into four categories - non-Hispanic white, non-Hispanic Black, Asian, and Hispanic or Latino/a groups. 
●	Poverty was measured as the percentage of households living below the federal family poverty threshold. 
●	Educational status was measured as the percentage who completed a bachelor’s degree or higher. 
●	Population density was calculated by dividing the total population within each hexagon by the area of the hexagon. Although referred to as household density by Vijayan et al., this variable was calculated by dividing the total population within the hexagon by the number of reported households in the hexagon, and therefore captures the average household size within each hexagon as opposed to density. 
Because the Census data were originally obtained at the tract level, a spatial transformation was needed to convert the tract data to the hexagon level. According to the original paper, this transformation was achieved by associating tracts to the hexagon in which the centroid was located, however, the authors do not provide details regarding whether additional manipulation of the raw data occurred (e.g. averaging the values of characteristics across multiple tracts located within a single hexagon).
The response variables examined by the original authors were 1) COVID-19 age-adjusted testing rates, 2) age-adjusted diagnosis rates, and 3) crude positivity rates. The crude positivity rate was calculated by dividing the count of positive COVID-19 cases by the number of tests conducted and multiplying by 100. We will identify the same three response variables, making sure to clarify the case rate, death rate, and diagnosis rate as they are crucial for a clear presentation of the data. 

## Results

Describe how results are to be presented.

## Discussion

Describe how the results are to be interpreted *vis a vis* each hypothesis or research question.

## Integrity Statement

We completed this preregistration to the best of our knowledge and that no other preregistration exists pertaining to the same hypotheses and research.

This report is based upon the template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## References

> Vijayan, T., M. Shin, P. C. Adamson, C. Harris, T. Seeman, K. C. Norris, and D. Goodman-Meza. 2020. Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County. Clinical Infectious Diseases 73 (9):e2970–e2975. DOI: 10.1093/cid/ciaa1692

> Kedron, P., Bardin, S., Holler, J., Gilman, J., Grady, B., Seeley, M., Wang, X. and Yang, W. (2023), A Framework for Moving Beyond Computational Reproducibility: Lessons from Three Reproductions of Geographical Analyses of COVID-19. Geogr Anal. https://doi.org/10.1111/gean.12370
