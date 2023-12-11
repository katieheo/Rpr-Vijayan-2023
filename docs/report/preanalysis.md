# Reproduction of Vijayan et al 2020 Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County

### Authors

- Katie Heo, jheo@middlebury.edu, @katieheo, Middlebury College
- Alex Xu, yidex@middlebury.edu, @alexxuyide, Middlebury College

### Abstract

This study replicates and extends the spatial analysis conducted by Vijayan et al. (2020) on SARS-CoV-2 outcomes in Los Angeles County (LAC). Vijayan et al. (2020) examined whether spatial patterns existed in SARS-CoV-2 age-adjusted testing rates, age-adjusted diagnosis rates, and crude positivity rates in Los Angeles County (LAC), utilizing a hexagonal grid to explore associations between COVID-19 crude positivity rates and a series of predictor variables. However, issues with the grid's connectivity prompted the creation of a new grid for this reproduction. The study also addressed data imputation challenges in variables 'age18' and 'age65'. Using R and spatial analysis packages, we performed LISA analyses, reproducing clusters for testing rates, diagnosis rates, and positivity rates. The spatial lag models were replicated to assess predictors' effects on crude positivity rates, age-adjusted diagnosis rates, and age-adjusted testing rates. Our results provides insights into spatial patterns and predictors of SARS-CoV-2 outcomes in Los Angeles County.

This study is a *reproduction* study of:

> Vijayan, T., M. Shin, P. C. Adamson, C. Harris, T. Seeman, K. C. Norris, and D. Goodman-Meza. 2020. Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County. Clinical Infectious Diseases 73 (9):e2970–e2975. DOI: 10.1093/cid/ciaa1692

> Kedron, P., Bardin, S., Holler, J., Gilman, J., Grady, B., Seeley, M., Wang, X. and Yang, W. (2023), A Framework for Moving Beyond Computational Reproducibility: Lessons from Three Reproductions of Geographical Analyses of COVID-19. Geogr Anal. https://doi.org/10.1111/gean.12370

#### Original study spatio-temporal metadata

- `Spatial Coverage`: LAC
- `Spatial Resolution`: 10 km hexagons
- `Spatial Reference System`: -
- `Temporal Coverage`: 2020 March 1st - 2020 June 30th  
- `Temporal Resolution`: -

## Study design

This study is a reproduction study of the Vijayan et al. 2020 study. 

The original analyses are retrospective and use observational data collected from federal and private sources. Although not publicly available, we were able to obtain the original study data after contacting the authors. However, the analysis code was not made available, nor was information about the computational environment used.

Research hypotheses:
H1: There is a difference in mean values of key socioeconomic and demographic variables by positivity rate groupings of low, medium, and high areas.
Original test: One-way analysis of variance (ANOVA) indicated that all variables, except the percentage black, exhibited statistically significant differences among the three subgroups (Table 1).

H2: (a) COVID-19 age-adjusted testing rate, (b) age-adjusted diagnosis rate, and (c) crude positivity rate were non-randomly distributed throughout LA County.
Original test: Local indicators of spatial association (LISA) identified elevated values of each variable around the center of LA, and depressed values around the edges of the county (Fig. 1)

H3: Socio-structural characteristics of LAC have non-zero association with crude positivity rate.
Original test: The authors used a regression model with a spatially lagged response was to identify significant positive associations between crude positivity and (i) proportion of population over 65, (ii) proportion Latino, proportion living in poverty, and (iii) housing density. 

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

The choice of a hexagonal grid as the spatial unit of analysis may introduce the risk of the Modifiable Areal Unit Problem. 
This problem arises when the results of an analysis are dependent on the arbitrary choice of spatial units. In this case, 
aggregating data into hexagons masked important variations at a finer spatial scale and introduce distortion in the observed
relationships. Hence, we will recreate the hexagonal layer to get rid of the gaps. 

Another issue that may come up is assumptions in data translation to hexagonal grid, as Vijayan et al. did not provide sufficient 
details on how the translation from original geographic units (tract, city, and county levels) to the hexagonal grid was performed. 
The lack of clarity on how centroids were associated and whether multiple tracts, cities, or counties intersected the same 
hexagonal unit introduced uncertainty and potential bias in the analysis.

Another threat may be standardization of variables as there is a lack of clarity on whether the response variables were standardized in addition to the predictor variables raises concerns about the proper interpretation of coefficients in the spatial regression models. The omission of the model intercept further complicates the interpretation of results.

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

## Results and Discussion

Similar to how the former reproduction study's report is structured, we are going to compare our reproduction result with the original study's result on descriptive statistical analyses of predictors, spatial pattern analysis, and Spatial Lag Model Regression (SLMR) testing for predictors. We expect to see small changes in spatial pattern analysis and SLM regression testing as we changed the hexagons of the original study that fixed the connectivity problems of the hexagon in LAC. We will then discuss the significance of each predictors on the three response variables. 

## Integrity Statement

We completed this preregistration to the best of our knowledge and that no other preregistration exists pertaining to the same hypotheses and research.

This report is based upon the template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## References

> Vijayan, T., M. Shin, P. C. Adamson, C. Harris, T. Seeman, K. C. Norris, and D. Goodman-Meza. 2020. Beyond the 405 and the 5: Geographic Variations and Factors Associated With Severe Acute Respiratory Syndrome Coronavirus 2 (SARS-CoV-2) Positivity Rates in Los Angeles County. Clinical Infectious Diseases 73 (9):e2970–e2975. DOI: 10.1093/cid/ciaa1692

> Kedron, P., Bardin, S., Holler, J., Gilman, J., Grady, B., Seeley, M., Wang, X. and Yang, W. (2023), A Framework for Moving Beyond Computational Reproducibility: Lessons from Three Reproductions of Geographical Analyses of COVID-19. Geogr Anal. https://doi.org/10.1111/gean.12370
