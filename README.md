# Global Weather and Air Quality Analysis

## Project Overview

This project aims to analyze and visualize global weather patterns and air quality data to identify trends, correlations, and insights. By leveraging multiple free-to-use APIs, we will gather data on weather conditions and air quality for various cities around the world. The analysis will be performed using Python libraries such as `pandas`, `numpy`, and `matplotlib`.

## Objectives

- Fetch weather data for multiple cities using the OpenWeatherMap API.
- Obtain air quality data for the same cities using the AirVisual API.
- Perform data cleaning and preparation to handle missing values and merge datasets.
- Conduct exploratory data analysis (EDA) to identify trends and correlations.
- Visualize the data using various plotting techniques.
- Summarize key findings and provide actionable insights.

## APIs Used

1. **OpenWeatherMap API**: For fetching weather data such as temperature, humidity, wind speed, and weather conditions.
2. **AirVisual API**: For obtaining air quality data including AQI (Air Quality Index), PM2.5, PM10, and other pollutants.
3. **Geoapify API**: For geocoding and reverse geocoding to get location coordinates.

## Libraries Used

- `pandas`
- `numpy`
- `matplotlib`
- `requests`
- `hvplot`
- `bokeh`

## Steps to Implement

1. **Set Up Environment**:
   - Install necessary libraries: `pandas`, `numpy`, `matplotlib`, `requests`, `hvplot`, `bokeh`.
   - Obtain API keys for OpenWeatherMap, AirVisual, and Geoapify.

2. **Fetch Data**:
   - Use the OpenWeatherMap API to fetch current weather data for multiple cities around the world.
   - Use the AirVisual API to get air quality data for the same cities.
   - Use the Geoapify API to get the coordinates of the cities if needed.

3. **Data Cleaning and Preparation**:
   - Clean the fetched data to handle missing values, incorrect data types, and duplicates.
   - Merge the weather and air quality data based on city names or coordinates.

4. **Exploratory Data Analysis (EDA)**:
   - **Descriptive Statistics**: Calculate mean, median, standard deviation, and other statistics for weather and air quality parameters.
   - **Correlation Analysis**: Analyze the correlation between weather parameters (e.g., temperature, humidity) and air quality indices.
   - **Visualization**:
     - **Scatter Plots**: Plot temperature vs. AQI, humidity vs. AQI, etc.
     - **Heatmaps**: Create heatmaps to visualize the correlation matrix.
     - **Time Series Analysis**: If historical data is available, analyze trends over time.

5. **Insights and Conclusions**:
   - Summarize the key findings from the EDA.
   - Identify any significant trends or correlations.
   - Provide actionable insights or recommendations based on the analysis.

6. **Documentation and Presentation**:
   - Document the entire process, including code, visualizations, and findings.
   - Create a presentation or report to showcase the results.

## Example Code Snippet

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import requests

# Fetch weather data from OpenWeatherMap API
weather_api_key = 'your_openweathermap_api_key'
weather_url = f'http://api.openweathermap.org/data/2.5/weather?q=London&appid={weather_api_key}'
weather_response = requests.get(weather_url)
weather_data = weather_response.json()

# Fetch air quality data from AirVisual API
airvisual_api_key = 'your_airvisual_api_key'
airvisual_url = f'http://api.airvisual.com/v2/city?city=London&state=England&country=UK&key={airvisual_api_key}'
airvisual_response = requests.get(airvisual_url)
airquality_data = airvisual_response.json()

# Example data processing and visualization
weather_df = pd.DataFrame([weather_data])
airquality_df = pd.DataFrame([airquality_data['data']['current']['pollution']])

# Merge dataframes
merged_df = pd.concat([weather_df, airquality_df], axis=1)

# Plot temperature vs. AQI
plt.scatter(merged_df['main']['temp'], merged_df['aqius'])
plt.xlabel('Temperature (K)')
plt.ylabel('Air Quality Index (AQI)')
plt.title('Temperature vs. AQI')
plt.show()
