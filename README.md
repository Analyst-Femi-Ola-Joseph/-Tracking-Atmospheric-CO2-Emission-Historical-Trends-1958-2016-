<img width="239" alt="missing values" src="https://github.com/user-attachments/assets/c4286f2d-ce64-4a8b-8d36-d2b318f165d5" /># -Tracking-Atmospheric-CO2-Emission-Historical-Trends-1958-2016-
This data science research project investigates the long-term trends in atmospheric carbon dioxide (CO₂) concentrations from 1958 to 2016.


## Project Overview
This data science research project investigates the long-term trends in atmospheric carbon dioxide (CO₂) concentrations from 1958 to 2016.

Utilizing high-resolution time-series data from the Mauna Loa Observatory and other verified sources, the project explores the seasonal and annual patterns of CO₂ emissions over nearly six decades.

Through trend analysis and robust data visualization, the study provides compelling evidence of the accelerating rise in CO₂ levels driven by anthropogenic activity.

By presenting clear, data-backed insights into historical CO₂ emissions, this project aims to inform public discourse, support environmental advocacy, and encourage policy interventions for climate action.

### Objectives

- To analyze the trend of atmospheric CO₂ concentrations from 1958 to 2016.

- To quantify the annual growth rate in CO₂ levels.

- To communicate findings using visualizations that are accessible to both scientific and non-scientific audiences.

### Data Source

**Mauna Loa Observatory CO₂ Data:** Provided by NOAA [National Oceanic and Atmospheric Administration](https://gml.noaa.gov/ccgg/trends/)

### Methodology

- Loaded the data from a CSV file into a Pandas Dataframe

- Converted the data into time-series format for seasonal decomposition

- Handled missing values and smoothed data using rolling averages

- Visualized the data to uncover the trend in co2 emmision from 1958 to 2016.

### Data Pre-Processing

The dataset is provided by NOAA [National Oceanic and Atmospheric Administration](https://gml.noaa.gov/ccgg/trends/),  contains records of the change in climate in the last half a century or so. 

The data is in a CSV file called `climate_change` with three columns. 

- 1. The `"date"` column indicates when the recording was made and is stored in the year-month-date format.
     A measurement was taken on the 6th day of every month from 1958 until 2016. 


- 2. The  `"co2"` column contains measurements of the carbon dioxide in the atmosphere.
     The number shown in each row is parts-per-million of carbon dioxide. 


- 3. The  `"relative_temp"` column denotes the temperature measured at this date, relative to a baseline which is the average        temperature in the first ten years of measurements. 

### Data Loading

```python
# solution 

import pandas as pd

import matplotlib.pyplot as plt

climate_change_df = pd.read_csv("C:/Users/steph/OneDrive/Desktop/_DATA SCIENCE BOOTCAMP TRAINING/DATA SET/climate_change.csv")

climate_change_df.head()
```
<img width="278" alt="Data Loading" src="https://github.com/user-attachments/assets/f6dff71e-58fb-4382-bdb9-f923ad27d027" />


###  Data Analysis

- **Time-Series Decomposition**: This was used to separate trend, seasonality, and residuals.

- **Visualization:** Created line plots,  seasonal subseries plots, and anomaly detection visuals using Python library (Matplotlib)

``` python
# Converting the datasaet into a Time-Series Decomposition:

climate_change_df = pd.read_csv("C:/Users/steph/OneDrive/Desktop/_DATA SCIENCE BOOTCAMP TRAINING/DATA SET/climate_change.csv",
                               parse_dates = ["date"], index_col = "date")

climate_change_df.head()

```

<img width="221" alt="Conversion to time - seires" src="https://github.com/user-attachments/assets/3d1620a8-7be1-43ea-b3c6-d261e3704b85" />


###  Data Inspection(check for missing values)

``` python

# Check for any missing value on each column
# isna().any() is a better code than just isna()

climate_change_df.isna().any()

```

<img width="239" alt="missing values" src="https://github.com/user-attachments/assets/6fd4988b-6103-4787-9d86-3bb3b846a2f2" />

``` python

# Counting the number of missing values.

climate_change_df.isna().sum()

```
<img width="239" alt="missing values" src="https://github.com/user-attachments/assets/df5c644f-0f8f-4034-aa43-89d63746fd61" />


### Data Cleaning (handling missing values) 

``` python
climate_change_df.shape
```

<img width="157" alt="data size" src="https://github.com/user-attachments/assets/117d2f5e-6196-48d9-926e-7a0e393ab796" />


``` python
climate_change_df["co2"].mean()
```

<img width="101" alt="mean" src="https://github.com/user-attachments/assets/d6e43b00-9e84-40c9-a3af-98c80db0a77f" />


``` python
# Filling the missing values with the mean value 352.32 on the co2 column.

climate_change_df = climate_change_df.fillna(352.32)

climate_change_df.head()

```

<img width="239" alt="missing values" src="https://github.com/user-attachments/assets/8ed8e9a4-e651-457d-aaa7-6802ebb6f595" />


``` python
# To confirm that there are no more missing values , use the function below.

climate_change_df.isna().any()
```

<img width="161" alt="Confirm missing values replaced with mean" src="https://github.com/user-attachments/assets/6bf0415e-aec7-440b-891c-2cfcbf8169fa" />

### Data Visualization

```python
# Data visualisation using the object orirnted interface of matplotlib 

import matplotlib.pyplot as plt

fig, ax = plt.subplots()

# visualizing the co2 emission vs time(date)

ax.plot(climate_change_df.index, climate_change_df["co2"], color = "red")

# add axis label : 
# label the x-axis : "Time"
# label the y-axis : "C02 (ppm)"

ax.set_xlabel("Time")

ax.set_ylabel("C02 (ppm)")

# add general title : Tracking Atmospheric CO2 Emission Historical Trends (1958–2016)

fig.suptitle("Tracking Atmospheric CO2 Emission Historical Trends (1958–2016)")

plt.show()

```

<img width="511" alt="Data Visualization" src="https://github.com/user-attachments/assets/16399161-4126-46cb-a884-58e9961f6734" />

###  Data Interpretation

* The data visualization above shows that there is an overall steady increase of CO2 emission from 1958 to 2016

### Key Findings

**Steady Increase**: CO₂ levels rose from approximately 315 ppm in 1958 to over 403 ppm by 2016.

**Seasonal Patterns**: A regular saw-tooth pattern was observed, corresponding to seasonal plant activity (photosynthesis cycles).

**Acceleration in Emissions**: Linear curve indicates steady growth and increasing acceleration in emissions, especially post-2000.

### Conclusion

- The findings of this study provide compelling evidence of the dramatic rise in atmospheric CO₂ over the last half-century.

- While natural seasonal variations exist, the long-term upward trend is unmistakably driven by industrialization, fossil fuel combustion, and land-use changes. 

- These results underscore the urgency for global climate mitigation strategies and support the scientific consensus on anthropogenic climate change.

### Recommendations

- I strongly reconmmend  the global adoption of renewable energy sources.

- I strongly reconmmend the Promotion of  global CO₂ emission monitoring for real-time policy response.

- I strongly reconmmend that this  findings should be used as part of educational material in environmental science curricula.

- I strongly reconmmend the Extension of this  study to include temperature anomaly data for correlation analysis.

