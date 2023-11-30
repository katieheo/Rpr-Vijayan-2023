- `Title`: COVID-19 Data from Los Angeles, California in 2020
- `Abstract`: Predictor variables were obtained from the 2018 5-year American Community Survey at the census tract level. Syndrome Coronavirus 2 (SARS-CoV-2) or COVID-19 testing and diagnosis data were obtained from the LAC Department of Public Health COVID-19 surveillance dashboard (http://dashboard.publichealth. lacounty.gov/covid19_surveillance_dashboard/) through 30 June 2022.
- `Spatial Coverage`: Los Angeles County (LAC), California
- `Spatial Resolution`: The total area of the hexagons are 4380 squared kilometers, each being 10 square kilometers. 
- `Spatial Reference System`: ESPG:32611
- `Temporal Coverage`: The census data was from 2018 and the LAC public health data was from the start of the pandemic to 30 June 2022. 
- `Lineage`: 
  - With the 2018 5-year American Community Survey (U.S. Census) and LAC Department of Public Health COVID-19 surveillance dashboard data, Vijayan et al. created a grid of hexagons. The authors did not provide any details about the algorithm or parameters used to create the grid. Each hexagon in the grid encompassed an area of 10 square kilometers. Once created, the grid was overlaid onto the centroids of city, community, and census tract boundaries within LAC, and all data were summarized and joined to the hexagon layer by location. Hexagons that either contained missing COVID-19 data, had a population of less than 1,000 people, or did not have contiguous neighbors were excluded from the analysis. The initial analysis sample contained 184 hexagons. However, we recreated the hexagon layer to contain the contiguous neighbors so that it did not have any gaps. Our final analysis sample contained 188 hexagons.
  - Census data was obtained at the tract level.
- `Distribution`: U.S. Census and the LAC Department of Public Health
- `Constraints`: No legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: State any planned quality assessment
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Expected range of Maximum and Minimum of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: NULL values reported three times. We found the median value of all hexagons to replace these NULL values. 

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| variable1 | ... | ... | ... | ... | ... | ... | ... |
| variable2 | ... | ... | ... | ... | ... | ... | ... |
