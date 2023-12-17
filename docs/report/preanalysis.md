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

Lastly, I will attempt to address boundary effects contributing to geographic uncertainty of the original study.  Because the VT River Corridors seem to omit the Connecticut River, mobile homes along the banks of the Connecticut River were not included in River Corridor flood risk.  I will attempt to create my own River Corridor polygon for the Connecticut River and report how many mobile homes lie within it, indicating how many mobile homes are "missed" by the original analysis.  I will try to indicate how many mobile homes were missed by county (this will only work for the eastern counties because only these are touching the Connecticut River). I plan to do this by loading a linestring layer of the Connecticut River into QGIS, buffering it to fill the width of the river channel, and then additionally buffering it to 6x the width of the river channel (which approximates the meander belt of the river...the authors of the VT River Corridor system say that a rule of thumb for creating a river corridor is 6x the width of a river channel).  I will put this polygon file in the data\derived\public folder.

All data that is provided to the students, including my Connecticut River river corridor polygon, will go in the data\derived\public folder.


