# Flight Delay Analysis: Uncovering Delay Trends and Pattern

Flight delays are an inevitable part of air travel, but the question is: *how can we minimize them to improve efficiency and passenger satisfaction?* This analysis uncovers critical insights into the causes and patterns of flight delays across airlines and airports, offering practical solutions to improve operational performance.

## I. Executive Summary
### **Key Insights**

**Relationship Between Departure and Arrival Delays:**
- Strong positive correlation between departure and arrival delays—late departures lead to late arrivals.
- No significant impact of flight distance on delays; both short- and long-haul flights follow the same delay patterns.
- Extreme outliers likely represent disruptions (e.g., weather, technical issues).

**Impact of Traffic Volume on Delays by Airline:**
- Delta, JetBlue, and United Airlines maintain delays under 15 minutes despite high traffic, indicating efficient operations.
- ExpressJet experiences highest delays (avg. 19 minutes), suggesting operational challenges.
- Airlines with lower volumes, like Hawaiian and Alaska, see shorter delays.
- Airlines like Frontier and Mesa face significant delays despite low volumes, pointing to operational inefficiencies.

**Monthly Delays:**
- January-May: Lower delays (9-13 minutes), likely due to fewer flights or better management.
- June-July: Increased delays (20-21 minutes), reflecting higher traffic and operational strain.
- August-November: Reduced delays (5-12 minutes), possibly due to fewer flights or improved management.
- December: Increased delays (15-16 minutes), likely due to higher traffic as the year ends.

**Hourly Delays:**
- 5:00 to 14:00: Relatively low delays (41s to 13m 42s) due to lower traffic.
- 15:00 to 21:00: Delays rise (16-24 minutes), peaking at 19:00-21:00 due to higher traffic.
- 22:00 to 23:00: Delays decrease (14-18 minutes) as traffic declines.

**Impact of Flight Volume on Delays by Origin:**
- EWR, the busiest, has the longest delays for both departure (15m 1s) and arrival (9m 6s).
- JFK has shorter delays than EWR, indicating better efficiency despite high traffic.
- LGA experiences the shortest delays, likely due to lower flight volume and efficient management.

**Departure Delays by Origin:**
- **EWR:** 58.8% of flights delayed >15 minutes, with delays ranging from 15m 8s to 41m 39s, suggesting operational inefficiencies.
- **LGA:** 33.8% of flights delayed >15 minutes, with delays ranging from 15m 11s to 31m 20s.
- **JFK:** 31.4% of flights delayed >15 minutes, with delays ranging from 15m 12s to 27m 20s, indicating better efficiency.

**Common Delayed Destinations:**
- **RIC, MKE, IAD, ORF** consistently experience delays across all origin airports, with RIC having the highest delays (23m 37s departure, 20m 7s arrival), pointing to systemic inefficiencies at these destinations.


### **Key Recommendations**

- **Optimize EWR Operations**: Address inefficiencies and congestion, improve scheduling, and enhance weather response strategies to reduce delays, especially during peak hours.
- **Enhance LGA Efficiency**: Streamline delay management systems and improve coordination between ground and air operations to reduce delays, particularly during peak periods.
- **Maintain JFK Efficiency**: Continue monitoring and optimizing current practices while investing in technology like predictive scheduling to sustain low delays.
- **Address Delays at RIC, MKE, IAD, and ORF**: Investigate recurring delays, especially at RIC, and enhance air traffic management and infrastructure.
- **Manage Flight Volume During Peak Periods**: Adjust flight schedules to reduce congestion during high-volume periods (June-July, December) and improve queuing and baggage handling.
- **Leverage Traffic Volume Data for Fleet Management**: Use traffic data insights to optimize fleet scheduling and reduce delays, especially for high-volume airlines.
- **Manage Delays by Time of Day**: Implement interventions to reduce delays during peak hours (15:00-21:00), focusing on the 19:00-21:00 window.
- **Enhance Collaboration**: Foster stronger coordination between airports, airlines, and ground teams to improve operations and reduce delays.

By implementing these strategies, airlines and airports can enhance punctuality, reduce delays, and deliver a better travel experience for passengers.

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
<video controls src="Data_Vizualization/Relationship Between Departure and Arrival Delays Based on Flight Distance.mp4" title="Title"></video>