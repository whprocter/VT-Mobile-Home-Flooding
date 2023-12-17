- `Title`: e911pts.shp
- `Abstract`: Point location data for all ocations of residences and buildings in Bennington, Rutland, Windham, and Windsor counties for use with emergency response
- `Spatial Coverage`: Bennington, Rutland, Windham, and Windsor counties
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: EPSG 32145 - NAD 83 Vermont
- `Temporal Coverage`: Some time 2014-2022
- `Temporal Resolution`: N/A
- `Lineage`: Downloaded from the VT Open GeoData Portal by GEOG 0261 instructors, and cleaned to only include the 4 southernmost counties, and to select only the `sitetype` variable.
- `Distribution`: The raw data is publicly available from the VT Open GeoData Portal, although the e911 point data is intended for use with emergency response
- `Constraints`: N/A
- `Data Quality`: Assumed to be accurate and representative of all residences and structures in Southern VT
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
| OBJECTID | unique identifier for each unique structure/residence | ... | numeric | ... | ... | n/a | n/a |
| sitetype | Type of location, of which one category is 'MOBILE HOME' | ... | character | ... | ... | n/a | n/a |
| geometry | point geometry| ... | unknown | ... | ... | n/a | n/a |

