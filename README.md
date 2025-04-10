# Flight Delay Analysis: Uncovering Delay Trends and Pattern

Flight delays are an inevitable part of air travel, but the question is: *how can we minimize them to improve efficiency and passenger satisfaction?* This analysis uncovers critical insights into the causes and patterns of flight delays across airlines and airports, offering practical solutions to improve operational performance.

## I. Executive Summary

This analysis reveals a strong positive correlation between departure and arrival delays, with minimal influence from flight distance. Airlines like Delta, JetBlue, and United perform efficiently despite high traffic, while ExpressJet, Frontier, and Mesa struggle with delays, suggesting operational challenges. Monthly trends show higher delays during peak travel periods (June–July, December), and hourly patterns highlight increased delays from 15:00 to 21:00, peaking between 19:00–21:00. Among the New York-area airports, EWR records the longest delays due to its high volume, while JFK and LGA demonstrate better efficiency. Notably, destinations like RIC and MKE consistently suffer from delays, indicating systemic issues.

To address these challenges, targeted improvements are recommended: optimize EWR operations, maintain JFK’s efficiency, and streamline LGA’s processes during peak hours. Addressing persistent delays at destinations like RIC and managing flight volumes during peak months can reduce congestion. Leveraging traffic data for better fleet and schedule management, especially during high-delay hours, can improve overall punctuality. Enhanced coordination between airports, airlines, and ground teams will be key in delivering a more efficient and reliable travel experience.

## II. Background

Flight delays are a significant issue in the aviation industry, affecting millions of passengers every year. These delays not only lead to frustration for travelers but also cause operational inefficiencies for airlines and airports. Understanding the factors that contribute to delays—such as airline performance, time of day, and airport conditions—can help improve punctuality and reduce the impact on passengers.

This analysis is crucial because it identifies patterns and trends that can help stakeholders, including airlines, airports, and passengers, make informed decisions. By uncovering the root causes of delays, airlines can optimize their operations, airports can improve traffic management, and passengers can better anticipate and plan for disruptions. This work is especially important as air travel continues to grow, and the demand for more efficient flight operations increases.

## III. Objectives
The primary goal of this project is to analyze flight delay data and uncover patterns related to airlines, airports, and time factors. The analysis will address the following key questions:

1. **Airline Performance**: How do different airlines compare in terms of their departure and arrival times? Are there noticeable trends in their on-time performance over the course of the year?
   
2. **Delays by Time**: Are there specific months, weeks, or times of the day where there is a general trend of greater delays across all carriers? What factors could contribute to these delays?

3. **Airport Performance**: How do different airports compare in terms of departure and arrival punctuality? What role do factors like location, traffic volume, and operational efficiency play in delays? Are there patterns in delays across various airports?

By answering these questions, the analysis will provide actionable insights into the operational challenges airlines and airports face, with a focus on identifying specific time periods and locations where improvements could reduce delays.

## IV. Data Description

The flight dataset consists of 21 columns and a total of 327,346 records, collected in 2013. The dataset is available [here](https://www.kaggle.com/datasets/mahoora00135/flights/data).

| Column Name       | Description                                                                 | Data Type   |
|-------------------|-----------------------------------------------------------------------------|-------------|
| id                | A unique identifier for each flight record                                  | Integer     |
| year              | The year in which the flight took place (2013)                              | Integer     |
| month             | The month of the flight (1 to 12)                                            | Integer     |
| day               | The day of the month of the flight (1 to 31)                                 | Integer     |
| dep_time          | Actual local departure time (hhmm, 24-hour format)                          | Integer     |
| sched_dep_time    | Scheduled local departure time (hhmm, 24-hour format)                       | Integer     |
| dep_delay         | Departure delay in minutes (positive = delayed, negative = early)           | Integer     |
| arr_time          | Actual local arrival time (hhmm, 24-hour format)                            | Integer     |
| sched_arr_time    | Scheduled local arrival time (hhmm, 24-hour format)                         | Integer     |
| arr_delay         | Arrival delay in minutes (positive = delayed, negative = early)             | Integer     |
| carrier           | Two-letter airline carrier code                                              | String      |
| flight            | Flight number                                                                | Integer     |
| tailnum           | Aircraft identifier                                                          | String      |
| origin            | Origin airport code (e.g., JFK, LGA, EWR)                                    | String      |
| dest              | Destination airport code                                                     | String      |
| air_time          | Duration of the flight in minutes                                            | Integer     |
| distance          | Distance between airports in miles                                           | Integer     |
| hour              | Hour component of the scheduled departure time                               | Integer     |
| minute            | Minute component of the scheduled departure time                             | Integer     |
| time_hour         | Scheduled departure timestamp (YYYY-MM-DD HH:MM:SS)                         | Datetime    |
| name              | Name of the airline carrier                                                  | String      |

## V. Data Quality Check and Cleaning

### Data Quality Check

I checked the dataset’s quality by first looking at a preview using `df.head()` and making sure all columns were visible. I then looked at the unique values in each column with `df.nunique()` and checked the data types using `df.dtypes`. I looked for duplicates using `df.duplicated().sum()` and checked for missing values with `df.isnull().sum()`, focusing on columns with missing data. This helped me find problems like missing values, duplicates, and wrong data types, making sure the data is reliable before cleaning.

### Data Cleaning

I cleaned the dataset by first removing rows with missing values using `df.dropna()`. Then, I converted the month numbers to their corresponding names using a mapping dictionary. I also standardized the time columns (`'dep_time'`, `'sched_dep_time'`, `'arr_time'`, and `'sched_arr_time'`) to a consistent `HHMM` format and handled the 2400 values appropriately. Lastly, I converted the `'dep_delay'`, `'arr_delay'`, and `'air_time'` columns from float to integer to ensure consistency. These steps helped prepare the dataset for analysis.

## Insight Deep-dive
### Relationship Between Departure and Arrival Delays Based on Flight Distance

- The scatter plot shows a strong positive correlation between departure and arrival delays—flights that depart late tend to arrive late, while early departures often lead to early arrivals
- There are some extreme outliers with very high delays. These may represent exceptional cases, like weather disruptions or technical issues.
- Flight distance shows no significant correlation with delays; both short-haul and long-haul flights follow a similar pattern—arrival delays increase with departure delays, and early departures often lead to early arrivals.

![alt text](0410(1).gif)