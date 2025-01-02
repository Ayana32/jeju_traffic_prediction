# Jeju Traffic Data Analysis

This repository contains the code and data used for analyzing traffic patterns and predicting traffic volume in Jeju Island. The project incorporates various data sources, such as traffic data, public holidays, and airport passenger statistics, to build a comprehensive model for traffic analysis.

## Project Overview

The project aims to:
1. Analyze traffic volume trends using historical data.
2. Incorporate additional contextual data such as public holidays and airport passenger volumes.
3. Provide insights for traffic prediction and management on Jeju Island.

## Dataset Details

### Traffic Data
- **Source**: Jeju Traffic Data (`jejudata_info.csv`)
- **Columns**:
  - `base_date`: Date of observation
  - `base_hour`: Hour of observation
  - `lane_count`: Number of lanes
  - `road_rating`: Road quality rating
  - `maximum_speed_limit`: Speed limit on the road
  - `start_latitude`, `start_longitude`: Start point coordinates
  - `end_latitude`, `end_longitude`: End point coordinates
  - `target`: Target traffic volume for prediction

### Public Holiday Data
- **Source**: Korean holiday information retrieved using `pytimekr`.
- **Integration**:
  - Holidays are added as binary indicators (`holiday`) to the traffic dataset.

### Airport Passenger Data
- **Source**: Korean Airports Corporation Open API
- **Columns**:
  - `date`: Date
  - `passenger`: Number of departing passengers from Jeju International Airport

## Usage
### Data Preprocessing
1. Load the datasets:
* Traffic data: jejudata_info.csv
* Public holiday data: Generated using pytimekr
* Airport passenger data: Retrieved from the API and saved as airport.csv.
  
2. Add public holiday information to the traffic dataset:
```# Example snippet
from pytimekr import pytimekr
import pandas as pd
import re # Process holidays
holidays = pytimekr.holidays(year=2021) + pytimekr.holidays(year=2022)
holidays = [int(re.sub('-', '', str(holiday))) for holiday in holidays
```
4. Add airport passenger statistics to the dataset.

### Analysis and Visualization
* Use the matplotlib and seaborn libraries for visualizing traffic trends.
* Example visualizations:
    Traffic volume trends during holidays vs. non-holidays.
* Correlation between airport passenger volume and traffic volume.
  
### Modeling
Train machine learning models using the processed dataset to predict traffic volume.
Potential models: Linear Regression, Random Forest, or Neural Networks.

### Results
* Key insights:
    Significant increase in traffic volume during holidays and weekends.
    Strong correlation between airport passenger volume and traffic volume near the airport.
