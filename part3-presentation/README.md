# Part 1: Common Analysis
More and more frequently summers in the western US have been characterized by wildfires with smoke billowing across multiple western states. There are many proposed causes for this: climate change, US Forestry policy, and growing awareness, just to name a few. Regardless of the cause, the impact of wildland fires is widespread. There is a growing body of work pointing to the negative impacts of smoke on health, tourism, property, and other aspects of society.

# License and Sources
- This repository is under the [MIT License](https://tlo.mit.edu/learn-about-intellectual-property/software-and-open-source-licensing).
- The wildfire dataset is from [USGS](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81), collected and aggregated by the US geological Survey. This dataset is available in ArcGIS and GeoJSON formats.
- The AQI data is from the API provided by the United States Environmental Protection Agency [AQS](https://aqs.epa.gov/aqsweb/documents/data_api.html).

# Data Files
## USGS_Wildland_Fire_Combined_Dataset.json
- The source of this data is [here](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81).
- This dataset is large (2.17GB), so I'm not pushing this dataset into my repository.
- This data file is in GeoJSON format. The fire information is stored under the key `features`. More data exploration can be found in the notebook `part1_common_analysis.ipynb`. For each fire object under `features`, only a few fields are used for analysis:
  - *attributes*: all the attributes of the fire
    - *Fire_Year*: the year when the fire occurred
    - *GIS_Acres*: the size of the fire
  - *geometry*: the geometry of the fire. The first *ring* of this field is used to calculate the distance between the city and the fire

# Intermediate Data Files
## df_attributes_estimator.csv
- This data file is produced in the [notebook](https://github.com/jennywong01/data-512-course-project/blob/main/part1-common-analysis/part1_common_analysis.ipynb) under the current folder.
- This dataset is 7.1MB, and it is an aggregated dataset with 5 columns.
- This data file is in CSV format. The attributes include:
  - *Fire_Year*: the year when the fire happened
  - *GIS_Acres*: the size of the fire in acre
  - *Avg_Distance*: the distance between the fire and Cedar City, Utah
  - *Smoke_Estimate*: the smoke estimate calculated using Fire_Year, GIS_Acres, and Avg_Distance
  - *Scaled_Smoke_Estimate*: the scaled smoke estimate with a range from 0-500

## df_average_aqi.csv
- The source of this data is [here](https://aqs.epa.gov/aqsweb/documents/data_api.html#monitors).
- This data file is produced in the [notebook](https://github.com/jennywong01/data-512-course-project/blob/main/part1-common-analysis/epa_air_quality_history.ipynb) under the current folder.
- This dataset is only 945 bytes, as it is an aggregated dataset with 2 columns.
- This data file is in CSV format. The attributes include:
  - *year*: the year when the AQI is collected
  - *aqi*: the average AQI of all available parameters of the year

## df_average_param_aqi.csv
- The source of this data is [here](https://aqs.epa.gov/aqsweb/documents/data_api.html#monitors).
- This data file is produced in the [notebook](https://github.com/jennywong01/data-512-course-project/blob/main/part1-common-analysis/epa_air_quality_history.ipynb) under the current folder.
- This dataset is only 6KB, as it is an aggregated dataset with 3 columns.
- This data file is in CSV format. The attributes include:
  - *year*: the year when the AQI is collected
  - *parameter*: the specific name of the AQI parameter
  - *aqi*: the average AQI of all available parameters of the year
 
# Notes to Data
Since Cedar City is not a major city in Utah, there are no air quality monitors inside the city. Instead, I collected the AQI data with a 150-mile range around Cedar City, while in this way I was still not able to get every AQI data for all the parameters. For the AQI data provided here, I only have relatively complete data for each AQI parameter since the 2000s. Using the AQI data prior to 2000 might result in a biased result.
