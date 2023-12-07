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
8. [Contributing](#contributing)
9. [License](#license)

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

7. **Note:**
   - Outliers identified during EDA were noted but left untreated at this stage.
  
The cleaned dataset is now ready for more in-depth exploratory data analysis and visualization in the `mt_rainier_eda.ipynb` notebook.
