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
