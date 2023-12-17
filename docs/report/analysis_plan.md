# Reproduction of Middlebury College's GEOG 0261's Analysis Flood Hazard Vulnerability in Vermont's Mobile Homes

## Pre-analysis Plan

I plan to follow the same procedure that the GEOG 0261 course follows in GQIS, just in R. This is essentially a reproduction of the methods used by Baker et al. (2014).

To perform my analysis, I plan to take the following steps:
- Load in the e911 point data for buildings and structures in VT
- Load in FEMA 100 year flood zones polygons
- Load in VT River corridor polygons
- Load in county polygons for Bennington, Rutland, Windsor, and Windham counties
- Load in state

I will follow the work flow described by Middlebury's GEOG 0261 instructors, and will revise the workflow to tailor it to the functions I use in R.  All of my spatial analysis will be conducted in R.  I will include the workflow(s) in the docs folder of the repository.

For the sake of time, I will utilize the pre-cleaned data that is provided to GEOG 0261 students, but I will address where this data originally came from, and will include the raw unprocessed data in the data\raw\public folder.  

I will attempt to reproduce Table 1 from the GEOG 0261 analysis, which includes the following table structure:
- For each of the four counties (which are listed as 4 rows), I will provide:
  1) The total number of mobile homes in the county (based on e911 point data)
  2) The number of mobile homes in the county based on e911 point data that are located in the FEMA 100 year flood zone (aka mobile homes at risk - FEMA)
  3) The number of mobile homes in the county based on e911 point data that are located in the VT River Corridors (aka mobile homes at risk - VT river corridors)
 
The GEOG 0261 analysis also utilizes an area-weighted reaggregation approach to identifying the number of mobile homes in each county.  However, the analysis concludes that this AWR approach is **less accurate** than using the e911 point data.  Thus, this reproduction will **only** use e911 point data to count and locate mobile homes in southeastern Vermont.

Additionally, I will attempt to reproduce a map and table that many students chose to make in GEOG 0261. Many students chose to also analyze mobile home flooding risk by town.  They identified mobile homes that were in the FEMA 100 year flood zone **and/or** the VT River Corridors to capture the most mobile homes possible that are at risk to flooding.  Then, students grouped these MHs by town, and calculated a % of mobile homes at risk rate for each town.  This ratio was calculated by dividing the number of mobile homes at risk (mobile homes in at least one of the flood hazard areas) and divided this by the total number of mobile homes in each town.  The resulting rate indicates what % of a towns mobile homes are at risk to flooding.

These by-town percentages of mobile homes at risk were mapped on a choropleth map by town.  Additionally, the ten towns with the highest percentages of mobile homes at risk are reported in a table, with the town name, total number of mobile homes in the town, number of mobile homes in the town at risk of flooding, and the calculated percentage of mobile homes at risk.

Lastly, I will attempt to address boundary effects contributing to geographic uncertainty of the original study.  Because the VT River Corridors seem to omit the Connecticut River, mobile homes along the banks of the Connecticut River were not included in River Corridor flood risk.  I will attempt to create my own River Corridor polygon for the Connecticut River and report how many mobile homes lie within it, indicating how many mobile homes are "missed" by the original analysis.  I plan to do this by loading a linestring layer of the Connecticut River into QGIS, buffering it to fill the width of the river channel, and then additionally buffering it to 6x the width of the river channel (which approximates the meander belt of the river...the authors of the VT River Corridor system say that a rule of thumb for creating a river corridor is 6x the width of a river channel)


















## Study design

Describe how the study relates to prior literature, e.g. is it a **original study**, **meta-analysis study**, **reproduction study**, **reanalysis study**, or **replication study**?

Also describe the original study archetype, e.g. is it **observational**, **experimental**, **quasi-experimental**, or **exploratory**?

Enumerate specific **hypotheses** to be tested or **research questions** to be investigated here, and specify the type of method, statistical test or model to be used on the hypothesis or question.

## Materials and procedure

### Computational environment

I utilized R version 4.3.1 (2023-06-16 ucrt) -- "Beagle Scouts" with the following platform: x86_64-w64-mingw32/x64 (64-bit).  I accessed R using the RStudio interface.  All code was run successfully using this enviornment on 12/17/23.

Packages are indicated in the procedure code (accessed via Groundhog).  The packages include "downloader", "rdhs", "haven", "readr", "tidyverse", "pastecs", "stars", "sf", "sp", "classInt", "tmap", "units", "knitr", "tibble", "here", "dplyr", "rgdal".


### Data and variables

Describe the **data sources** and **variables** to be used.
Data sources may include plans for observing and recording **primary data** or descriptions of **secondary data**.
For secondary data sources with numerous variables, the analysis plan authors may focus on documenting only the variables intended for use in the study.

Primary data sources for the study are to include ... .
Secondary data sources for the study are to include ... .

Each of the next subsections describes one data source.

#### Primary data source1 name

**Standard Metadata**

- `Abstract`: Brief description of the data source
- `Spatial Coverage`: Specify the geographic extent of your study. This may be a place name and link to a feature in a gazetteer like GeoNames or OpenStreetMap, or a well known text (WKT) representation of a bounding box.
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Lineage`: Describe and/or cite data sources and/or methodological steps planned to create this data source.
  - sampling scheme, including spatial sampling
  - target sample size and method for determining sample size
  - stopping criteria for data collection and sampling (e.g. sample size, time elapsed)
  - de-identification / anonymization
  - experimental manipulation
- `Distribution`: Describe who will make the data available and how?
- `Constraints`: Legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: State any planned quality assessment
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
| variable1 | ... | ... | ... | ... | ... | ... | ... |
| variable2 | ... | ... | ... | ... | ... | ... | ... |

#### Primary data source2 name

... same form as above...

#### Secondary data source1 name

**Standard Metadata**

- `Abstract`: Brief description of the data source
- `Spatial Coverage`: Specify the geographic extent of your study. This may be a place name and link to a feature in a gazetteer like GeoNames or OpenStreetMap, or a well known text (WKT) representation of a bounding box.
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Lineage`: Describe and/or cite data sources and/or methodological steps used to create this data source
- `Distribution`: Describe how the data is distributed, including any persistent identifier (e.g. DOI) or URL for data access
- `Constraints`: Legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: State result of quality assessment or state "Quality unknown"
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Range (Maximum and Minimum) of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: Values used to represent missing data and frequency of missing data observations
  - `Missing Data Frequency`: Frequency of missing data observations

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| variable1 | ... | ... | ... | ... | ... | ... | ... |
| variable2 | ... | ... | ... | ... | ... | ... | ... |

#### Secondary data source2 name

... same form as above...

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
