# Introductory Spatial Analysis Using and Open Source Code-based Program

## Contributors

- William Procter, wprocter@middlebury.edu, @whprocter, Middlebury College Department of Geography
- Using materials and lesson plans created by the Middlebury College Department of Geography Faculty

## Abstract

This study is a reproduction of a course-based assignment used in teaching Middlebury College's GEOG 0261 course - Human Geography of GIS.  The analysis - titled Flood Hazard Vulnerability in Vermont's Mobile Homes - is used to teach undergraduate geography students the fundamentals of spatial analysis, and it is taught and conducted entirely using QGIS's graphical user interface.  The assignment focuses on identifying the locations of mobile homes in southeastern Vermont that sit in known flood hazard areas, as determined by FEMA's 100-year flood zones and Flood Ready Vermont's VT river corridors.  Additionally, the assignment asks students contrast these two different methods for defining flood risk: the federal FEMA flood zones and the Vermont River Corridors (inclusive of rivers and small streams). The analysis is a motivated by Baker et al.'s (2014), who studied the vulnerability of Vermont mobile home parks to flooding following the major flooding that Vermont experienced during Hurricane Irene.  The course assignment and this reproduction study follow GIS methodology outlined by Baker, Hamshaw and Hamshaw (2014) in the Mobile Home Park Flood Hazard Identification section, and Figure 5 of the paper. Their method includes creating a 60-foot buffer around point locations of mobile homes, since a typical mobile home is 120 feetlong. They consider a mobile home to be at risk of flooding if any part of the buffer is in the 100-year FEMA flood zone.  The assignment also tests if any part of the buffer is in the VT River Corridors.

I reproduce the spatial analysis steps of the **Flood Hazard Vulnerability in Vermont's Mobile Homes** using a code-based approach in R to see if it yields same results as when using QGIS.  Additionally, I seek to decrease sources of geographic uncertainty, namely boundary effects along the eastern border of the state (Connecticut River).

I reproduced this study in R in hopes that my R code can be used by GEOG 0261 (or other course) instructors to teach fundamental spatial analysis techniques using a code-based approach.

Vermont is especially vulnerable to flooding because of how its steep terrain funnels water. Water draining into a valley surrounded by mountains piles up faster and higher than water spread over wider, flatter spaces. This not only increases the risk of flooding, but it also heightens the likelihood of landslides.  Ultimately' the steep terrain in many parts of the state intensifies runoff, and makes flooding "flashier."  The study demonstrates that mobile homes in southeastern Vermont are highly to flooding. Thus, the vulnerability findings of this study can also be used by stakeholders to direct and identify resiliency projects to reduce the vulnerability of these homes.

For the sake of simplicity and to save time, this study will use the pre-cleaned datasets that the GEOG 0261 instructors provide to students in the course.  The data is believed to have been downloaded sometime between 2014 and 2022.

A copy of the assignment used in the GEOG 0261 course can be found in the `docs` folder of the repository.

Baker et al. (2014) study:
Baker, D., Hamshaw, S. D., & Hamshaw, K. A. (2014). Rapid flood exposure assessment of Vermont mobile home parks following Tropical Storm Irene. Natural Hazards Review, 15(1), 27-37. DOI: 10.1061/(ASCE)NH.1527-6996.0000112.

## Study Metadata

- `Key words`: vulnerability, flooding, natural hazards, spatial analysis
- `Subject`: Geography: Geographic Information Sciences
- `Date created`: 2 December 2023
- `Date modified`: 17 December 2023
- `Spatial Coverage`: Southeastern Vermont (Bennington, Windsor, Windham, Rutland Counties)
- `Spatial Resolution`: County and town levels, as well as point location data
- `Spatial Reference System`: EPSG 32145 - NAD 83 VT
- `Temporal Coverage`: 2014-2022 (inferred)
- `Temporal Resolution`: N/A
- `Funding Name`: N/A
- `Funding Title`: N/A
- `Award info URI`: N/A
- `Award number`: N/A

## Related to

- `OSF Project`: N/A
- `Pre-analysis Registration`: See docs folder
- `Post-analysis Report Registration`: N/A
- `Preprint`: N/A
- `Conference Presentation`: N/A
- `Publication`: N/A
- `Prior Study`: https://doi.org/10.1061/(ASCE)NH.1527-6996.0000112
- `...`:

## Metadata for access

- `Rights`: [LICENSE](LICENSE): BSD 3-Clause "New" or "Revised"
- `Resource type`: Collection
- `Resource language`: English
- `Conforms to`: Template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences version 1.0, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

## Compendium structure and contents

This research compendium is structured with four main directories:

- `data`: contains subdirectories for `raw` data and `derived` data.
- `docs`: contains subdirectories for `manuscript`, `presentation`, and `report`
- `procedure`: contains subdirectories for `code` or software scripts, information about the computational `environment` in which the research was conducted, and non-code research `protocols`
- `results`: contains subdirectories for `figures`, formatted data `tables`, or `other` formats of research results.

The data, procedures, and results of this repository are outlined in three tables:
- Data: [data/data_index.csv](data/data_index.csv)
- Procedures: [procedure/procedure_index.csv](procedure/procedure_index.csv)
- Results: [results/results_index.csv](results/results_index.csv)

Important local **documents** include:
- Pre-analysis plan: [docs/report/preanalysis.pdf](docs/report/preanalysis.pdf)
- Study report: [docs/report/report.pdf](docs/report/report.pdf)
- Manuscript: [docs/manuscript/manuscript.pdf](docs/manuscript/manuscript.pdf)
- Presentation: [docs/presentation/presentation.pdf](docs/presentation/presentation.pdf)

#### Compendium reference

The [template_readme.md](template_readme.md) file contains more information on the design of this template and references used in the design.
The [Template_LICENSE](Template_LICENSE) file provides the BSD 3-Clause license for using this template.
To cite the template, please use [template_reference.bib](template_reference.bib) or:
> Kedron, P., & Holler, J. (2023). Template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences. https://doi.org/10.17605/OSF.IO/W29MQ
