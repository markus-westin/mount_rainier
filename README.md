# Data Analysis Project README

## Project Name

Mount Rainier Weather Analysis

## Overview

The Mount Rainier Weather Analysis project aims to explore the relationship between weather conditions on Mount Rainier and the success of climbers in reaching the summit. The project further involves an interactive visualization of the data, as well as a predictive model to assess a climber's likelihood of summiting based on various weather parameters.



## Table of Contents

1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Getting Started](#getting-started)
4. [Data Extraction](#data-extraction)
5. [Data Cleaning](#data-cleaning)
6. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
7. [Results](#results)


## Introduction

### Background

Mount Rainier, standing as the highest peak in the Cascade Range, is a challenging climb attracting adventurers from around the world. Weather conditions play a crucial role in the safety and success of a climb. Adverse weather, including storms, low visibility, and extreme temperatures, can pose significant risks to climbers. This project seeks to uncover patterns in historical weather data and understand how these conditions impact a climber's ability to reach the summit.

### Data Source

The primary data source for this analysis is historical weather data collected on Mount Rainier. This dataset includes information on temperature, wind speed, precipitation, visibility, and other relevant weather metrics. Additionally, summit success and failure records will be integrated, providing a comprehensive dataset for analysis. Data has been sourced from kaggle.com 

### Data Sources:
The primary data source for this analysis is historical weather data collected on Mount Rainier. This dataset includes information on temperature, wind speed, precipitation, visibility, and other relevant weather metrics. Additionally, summit success and failure records will be integrated, providing a comprehensive dataset for analysis.

### Key Components:

1. **Data Exploration:**
   - Investigate the historical weather data to identify patterns and trends.
   - Analyze the correlation between weather variables and climbers' success rates.

2. **Predictive Model:**
   - Develop a machine learning model to predict a climber's chance of summiting based on current and forecasted weather conditions.
   - Evaluate the model's accuracy, sensitivity, and specificity.

3. **Visualizations:**
   - Create visualizations to communicate key insights, such as the impact of temperature, wind, and visibility on summit success.
   - Generate interactive charts and graphs for a user-friendly exploration of the data.

### Significance:
Understanding the relationship between weather conditions and climbers' success on Mount Rainier can provide valuable insights for expedition planning, risk management, and safety protocols. The predictive model aims to offer a tool for climbers and guides to assess the feasibility of a summit attempt based on real-time weather forecasts.

### Expected Outcomes:
- Identification of critical weather variables influencing summit success.
- A reliable predictive model for climbers to assess summit probability.
- Enhanced safety measures and decision-making for Mount Rainier expeditions.

This project strives to contribute valuable information to the mountaineering community, aiding climbers in making informed decisions and ensuring a safer and more successful climbing experience on Mount Rainier.


## Project Structure

/mount_rainier
│
├── data
│ ├── kaggle_export.ipynb
│ └── mount-rainier-weather-and-climbing-data.zip
│ ├── climbing_statistics.csv
│ └── Rainier_Weather.csv
│ ├── clean_data.csv
│
├── data_cleaning
│ ├── data_cleaning_workbook.ipynb
│ └── [Other relevant files]
│
├── notebooks
│ ├── clean_data.ipynb
│ └── mt_rainier_eda.ipynb
│
├── models
│ ├── mlr_model.ipynb
│
├── visualizations
│ ├── tableau.md
│
├── .gitignore
├── README.md


## Getting Started


## Data Extraction
The data for this project was extracted from Kaggle using the Kaggle API, which facilitates seamless access to datasets hosted on the Kaggle platform. The dataset is available at [Mount Rainier Weather and Climbing Data](https://www.kaggle.com/datasets/codersree/mount-rainier-weather-and-climbing-data). Utilizing the Kaggle API, the extraction process involved authenticating with Kaggle, downloading the datasets and extracting them to .csv files.

## Data Cleaning

The clean_data.ipynb workbook provides the data cleaning operations used on the weather and climbing dat. The key operations performed are as follows:

1. **Importing Data:**
   - The two datasets, `climbing_statistics.csv` and `Rainier_Weather.csv`, are imported as Pandas DataFrames.
   - 'Date' columns are formatted as datetime.

2. **Merging Datasets:**
   - The climbing statistics and weather datasets are merged using a left outer join on the 'Date' column.
   - Rows with null weather data are dropped from the resulting dataset.

3. **Review and Clean Data:**
   - Undesired columns ('Battery Voltage AVG', 'Solare Radiation AVG') are removed.
   - Route names are standardized and certain routes are dropped

4. **Handling Anomalies:**
   - Anomaly was identified where successful summits exceed attempts in a given day.
   - Six rows with this anomaly were dropped.

5. **High-Level Exploratory Data Analysis (EDA):**
   - Brief EDA included exploration of correlations and box plots to identify outliers and data skewing.

6. **Exporting Cleaned Data:**
   - Cleaned dataset exported to 'clean_data.csv' for further EDA and visualization.

*Note:*
   - Outliers identified during EDA were noted but left untreated at this stage.
  
The cleaned dataset is now ready for more in-depth exploratory data analysis and visualization in the `mt_rainier_eda.ipynb` notebook.

## Exploratory Data Analysis

### Goals
The goal of this exploratory data analysis (EDA) is to investigate and understand the structure, patterns, and characteristics of the Mount Rainier dataset. The analysis aims to uncover insights, detect anomalies, and formulate hypotheses for more in-depth statistical analysis and data visualization.

### Key Questions & Answers

**Question 1: What route has been summited the most? Which has the highest summit success rate? Are they the same?**

*Answer:* The Disappointment Cleaver was by far the most summited route with 3647 summits, however it did not have the highest summit success rate. The Emmons-Winthrop route had the highest meaningful summit rate of 53.8%. We can further analyse the data to determine whether Emmons-Winthrop had a higher success rate due to weather at the time of the summits, or if the Emmons-Winthrop had a higher success rate due to it being an easier (although less popular, indicated by the lower number of attempts) route. Refer to Question 1A for additional analysis.

**Question 1A: Did Emmons-Winthrop have a higher summit rate due to better temperatures at the time of summit compared to Disappointment Cleaver?**
*Answer:* Interestingly, the average weather on the days in which there had been at least one successful summit did significantly vary between Emmons and Disappointment. Based on this, we may conclude that perhaps weather conditions was not the reason for Emmons having a higher summit rate as compared to Disappointment, despite having a significantly lower total number of summits.

There are countless other reasons as to why this is the case. For example, the Emmons route may be easier to summit overall when compared to Disappointment, the Disappointment summit rate may be skewed as significantly more people made attempts (where as perhaps only experienced climbers attempot Emmons, and therefore have a higher chance of summitting), or there are other qualitative factors related to the expertise and skillset of the climbers or the route itself (e.g., whether the route requires mixed-climbing, dry-tooling, ice-climbing, etc.). None of these are captured within the current dataset, therefore further analysis cannot be performed at this time.

**Question 2: What route has been summited the least? Which has the lowest summit success rate? Are they the same?**

*Answer:* Based upon the analysis performed above in Question 1, Nisqually Glacier, Sunset Ingraham Direct, Gibralter Chute, and Wilson Headwall all have zero summits recorded. Similarly, these routes have the lowest summit success rate of 0.0%. The lowest non-zero summit rate is on the Ingraham Direct route with a success rate of 7.1%. 

**Question 3: Is there a relationship between summit success rate and various weather factors?**

*Answer:* 
>*Summit Success & Temperature:*
<br>
<br>
>There is a small positive correlation **(0.13)** between the average temperature and the success percentage of the climb. 
>As temperature increases, the success rate tends to increase.
<br>
<br>

>*Summit Success & Humidity* 
<br>
<br>
>There is a small negative correlation **(-0.07)** between the average relative humidity and the success percentage of the climb.
>As humidity increases, the success rate tends to decrease.
<br>
<br>

>*Summit Success & Wind Speed*
<br>
<br>
>There is a small negative correlation **(-0.13)** between the average daily wind speed and the success percentage of the climb.
>As wind speed increases, the success rate tends to decrease.
<br>
<br>

>*Summit Success & Wind Direction*
<br>
<br>
>There is a small negative correlation **(-0.08)** between the average wind direction and the success percentage of the climb.
>As wind direction increases (i.e., moves clockwise from the north), the success rate tends to decrease.
>This interpretation however is difficult to understand as wind direction would be better understood as a categorical value as opposed to numeric. This change will be made in developing the model.
<br>
<br>

The conclusion is that while there is evidence of a linear relationship between the weather factors and summit success rate, the magnitude of the relationship is quite small. 

**Question 4: Are there any identifiable patterns in the dataset?**
*Answer:*
>*Attempts & Summits:*
<br>
<br>
>The vast majority of attempts and summits took place during the months of May 2015 to October 2015, which corresponds to the months that saw the highest average temperature (i.e., the summer months).
> This makes sense as climbers would be inclined to attempt a summit during the summer when the weather conditions are most optimal.
>Similarly the summit success percentage was highest during the same time frame.
<br>
<br>

>*Humidity* 
<br>
<br>
>The average humidity was quite volatile throughout the time period.
>During the summer months hummidity ranged from between 100% - 10%.
<br>
<br>


The conclusion is that there is a seasonality trend within the climbing statistics and weather data, which aligns with expecatations based on the nature of the data.

**Question 5: Are there outliers in the data?**
*Answer:* There are a significant number of outliers within the Wind Speed dimension, which is due to the highly skewed nature of the data. Additionally, there are some outliers in the Succeeded and Temperature dimensions.