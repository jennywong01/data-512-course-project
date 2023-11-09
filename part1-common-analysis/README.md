# Part 1: Common Analysis
More and more frequently summers in the western US have been characterized by wildfires with smoke billowing across multiple western states. There are many proposed causes for this: climate change, US Forestry policy, and growing awareness, just to name a few. Regardless of the cause, the impact of wildland fires is widespread. There is a growing body of work pointing to the negative impacts of smoke on health, tourism, property, and other aspects of society.

# License and Sources
- This repository is under the [MIT License](https://tlo.mit.edu/learn-about-intellectual-property/software-and-open-source-licensing).
- The wildfire dataset is from [USGS](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81), collected and aggregated by the US geological Survey. This dataset is available in ArcGIS and GeoJSON formats.
- The AQI data is from the API provided by the United States Environmental Protection Agency [AQS](https://aqs.epa.gov/aqsweb/documents/data_api.html).

# Data Files
## USGS_Wildland_Fire_Combined_Dataset.json
- The source of this data is [here](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81).
- This dataset is large (2.17GB), so I'm not pushing this dataset in my repository.
- This data file is in GeoJSON format. The fire information is stored under the key `features`. More data exploration can be found in the notebook `part1_common_analysis.ipynb`. For each fire object under `features`, only a few fields are used for analysis:
  - *attributes*: all the attributes of the fire
    - *Fire_Year*: the year when the fire occurred
    - *GIS_Acres*: the size of the fire
  - *geometry*: the geometry of the fire. The first *ring* of this field is used to calculate the distance between the city and the fire
