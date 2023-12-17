- `Title`: block_groups.shp
- `Abstract`: multipart polygon layer of the block groups and counties for the 4 southernmost counties in Vermont
- `Spatial Coverage`: Bennington, Rutland, Windham, and Windsor counties
- `Spatial Resolution`: N/A
- `Spatial Reference System`: EPSG 32145 - NAD 83 Vermont
- `Temporal Coverage`: 2014-2018 ACS estimates
- `Temporal Resolution`: N/A
- `Lineage`: Downloaded from the US Census American Community Survey by GEOG 0261 instructors, and cleaned to only include the 4 southernmost counties, and select the variables for number mobile housing units and number of total housing units
- `Distribution`: The raw data is publicly available from the US Census/ACS
- `Constraints`: N/A
- `Data Quality`: Assumed to be complete (so far as the ACS estimates are complete) for the 4 southern VT counties
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Expected range of Maximum and Minimum of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: Values used to represent missing data and frequency of missing data observations
  - `Missing Data Frequency`: Frequency of missing data observations: not yet known for data to be collected

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| fid | unique identifier | ... | numeric | ... | ... | n/a | n/a |
| GEOID | unique identifier | ... | numeric | ... | ... | n/a | n/a |
| mobileHU | estimated total of mobile home housing units in each block group| ... | numeric | ... | ... | n/a | n/a |
| totalHU | estimated total of all housing units in each block group| ... | numeric | ... | ... | n/a | n/a |
| COUNTYFP | code indicating which county the block group is in | ... | numeric | ... | ... | n/a | n/a |
| county | name of county in which the block_group is located | ... | character | ... | ... | n/a | n/a |
| geometry | point geometry| ... | unknown | ... | ... | n/a | n/a |
