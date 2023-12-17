- `Title`: FEMA_100yr.shp
- `Abstract`: multipart polygons of flood zones determined by FEMA
- `Spatial Coverage`: Bennington, Rutland, Windham, and Windsor counties
- `Spatial Resolution`: N/A
- `Spatial Reference System`: EPSG 32145 - NAD 83 Vermont
- `Temporal Coverage`: Some time 2014-2022
- `Temporal Resolution`: N/A
- `Lineage`: Downloaded from the VT Open GeoData Portal by GEOG 0261 instructors, and cleaned to only include the 4 southernmost counties.
- `Distribution`: The raw data is publicly available from the VT Open GeoData Portal
- `Constraints`: N/A
- `Data Quality`: Assumed to be accurate and representative of all determined FEMA flood zones in southern VT
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
| FLD_ZONE | Identifies type of flood zone...FEMA Flood Zone Codes| All codes beginning with 'A' are included in the 1% flood risk zone (100-year flood risk) | character | ... | ... | n/a | n/a |
| geometry | point geometry| ... | unknown | ... | ... | n/a | n/a |
