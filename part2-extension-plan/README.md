# Part 2: Extension Plan
The proposed analysis is designed to address the problems impacting our community by the effects of wildfire smoke on urban life. The impact focus that I want to focus on is economics. Specifically, I am going to revolve around the crime rate of the city. A study that examined the effect of air pollution exposure on crime in the US over eight years found a robust positive relationship between air pollution and violent crimes, specifically assaults.

# License and Sources
- This repository is under the [MIT License](https://tlo.mit.edu/learn-about-intellectual-property/software-and-open-source-licensing).
- The crime dataset is from [NIBRS](https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/downloads), collected and managed by the FBI. This original dataset is available in CSV formats.

# Data Files
## NIBRS Crime Data
- The source of this data is [here](https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/downloads).
- This dataset is large (1.51GB) and messy (each year has its own incidents and distribution summary), so I'm not pushing this dataset into my repository.
- This data file is in CSV format. The crime data for each year has 50 CSV files. Among all the files, only a few are selected to do further aggregation (the file names listed here align with the 2022 data, the previous years may have different file names):
  - *agencies.csv*: a list of agencies in Utah state
  - *NIBRS_incident.csv*: a file of all incidents that happened in the year in Utah state
  - *NIBRS_OFFENSE_TYPE.csv*: a file of all offense types with offense code and its corresponding name

# Intermediate Data Files
## nibrs_crime_data.csv
- This data file is produced in the [notebook](https://github.com/jennywong01/data-512-course-project/blob/main/part2-extension-plan/nibrs_data_cleaning.ipynb) under the current folder.
- This dataset is 9KB, and it is an aggregated dataset with 4 columns.
- This data file is in CSV format. The attributes include:
  - *data_year*: the year when the incident happened
  - *offense_code*: the code of the type of the incident
  - *offense_name*: the name of the offense type
  - *offense_count*: the total count of the corresponding offense of the year
 
# Notes to Data
Since Cedar City is not a major city in Utah, the crime data might not be fully collected by the NIBRS. Instead, I also used the crime data from police departments around Cedar City.
