# Springboard_Capstone2
Springboard Capstone2 Project
 
![alt text](https://github.com/smrubin1987/Springboard_Capstone2/blob/main/Images/Cap2_HeadlineImagine.png)

**Air Quality Health Differs Between Major U.S. Counties**

*Summary and Background*

Ground level Ozone (O3) is considered hazardous to human health. In high-enough concentrations, Ozone can trigger a suite of health concerns including damage to the lungs, asthma, and other chronic respiratory diseases. Ground level Ozone is a by-product pollutant, in the form of combustion exhaust, from cars, power plants, refineries, and boilers when in the presence of sunlight. In this project I create a binary classification system from the Environmental Protection Agency's (EPA) air quality data Outdoor Monitors in ten of the most populous counties in the United States from 2019 to determine the health concern related to ground level Ozone.

*Problem Identification, Methodology, and Datasets*

Air quality throughout the U.S. fluctuates based on various environmental, climatic, and
anthropogenic features, and varies at both geographic and temporal scales. Air quality
measurements include particulate matter, nitrous oxides, sulfurous oxides, and ozone,
all which have an impact on human health depending on threshold, quantity, and
exposure limits, and that are monitored by either the state or federal EPA.
Understanding what features are influencing air quality will allow environmental
regulators, city planners, and government agencies opportunities to improve poor air
quality by understanding the influence of the changes at a temporal scale in the U.S.
Specifically, ground level ozone (O3), a direct byproduct of fossil fuel consumption,
plays a major role in human health. How does ground-level air quality fluctuate between
various urban areas throughout the U.S.?

The EPA 8-hour Ozone threshold is set at 0.07ppm (2019), although concentrations of 0.06ppm are shown to have health impacts on the human respiratory system. By classifying health concerns (above or below 0.06ppm) and the EPA Ozone threshold (0.07ppm), we can further understand county-level concerns for air quality health. 

In this project, we utlized each county's total population estimation in 2019 as the primary feature for modeling Ozone health concerns. Ground level Ozone is measured as "8-hour Ozone Concentrations (ppm)" at various EPA measurement (air quality) stations throughout each county.

*Data Wrangling and Cleaning*

The following counties were included in the dataset:
    - Los Angeles County, CA
    - Riverside County, CA
    - Orange County, CA
    - San Diego County, CA
    - Maricopa County, AZ
    - Dallas County, TX
    - Harris County, TX
    - Queens County, NY
    - Miami-Dade County, FL
    - Cook County, IL
        * Kings County, NY, was not included since there are not full datasets 
        available in this county through the EPA

Population estimation data for 2019 was acquired from https://www.census.gov/ for each county. The 8-hour Ozone measurement data was acquired from https://www.epa.gov/. With multiple measurement stations throughout each county, data was grouped and summarized for each day for each county to acquire the "Max 8-Hour Ozone (ppm)". A tidy-dataframe was created from the Maximum 8-hour Ozone concentration data for the entire year (daily) of 2019, by county. 

*Exploratory Data Analysis*

The distrubition of the maximum daily 8-hour Ozone concentrations by county for 2019 were shown through histrograms, a swarm plot, and a boxplot. Exploring the distribution and summary statistics of the Ozone concentrations by county indicates differences in both the distribution of Ozone by county throughout the year, and that certain counties have a much higher distribution of days with maximum 8-hour Ozone concentrations both over the health-concern threshold of 0.06ppm and the EPA attainment threshold of 0.07pm.

![alt text](https://github.com/smrubin1987/Springboard_Capstone2/blob/main/Images/Histogram_O3.PNG)

*Pre-processing and Training The Data*

The maximum 8-hour Ozone concentrations were scaled using sklearn's StandardScaler. Population data by county was categorized by the median population of the ten counties as either above or below the median population value. Ozone health concern and the EPA attainment threshold were catogorized as either above or below. County level categorization was established as well. Dummy variables were created using panda's create_dummy(). 

*Modeling and Classification*

The dataset was balaced using SMOTE through the imblearn libary.

Three model types (supervised learning) were chosen for classifying the dataset using sklearn model types:
    - Logistic Regression
    - Tree Classifier
    - Random Forest Classifer

Model accuracy ranged between 88-90% for classifying the county-level health concerns for Ozone based on county-level total population. 
![Screenshot](https://github.com/smrubin1987/Springboard_Capstone2/blob/main/Images/ROC_AUC.png)


*Conclusions*

Predicting county-level air health (ground level Ozone) based upon total population size using a Logistic Regression classifier can be highly accurate. The more people in an area, the more industry and automobile exhaust, the more likely Ozone concentrations will be higher. Concerns for health should be delimited by counties with days above either 0.06ppm (for sensitive groups, children), and for the general populous at 0.07ppm (since this creates an EPA non-attainment region). Reviewing county population will provide a strong indication of these concerns: a lower total population means less Ozone-related health concern; a larger population means a higher Ozone-related health concern.

Further feature selection should be performed for county-level population density, density of cars and drivable mileage per person, and incorporating geologic and meterological factors such as a wind speed, daily temperature, and sunshine/UV-index, all which play a role with ground level Ozone production.
