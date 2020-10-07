# MSU-Project1
## Does climate impact the number of COVID cases?

This analysis takes a look at climate factors, including temperature and humidity, for ten cities around the United States. Additionally, we look at the impact the climate factors have on time outside of the home in comparison to the amount of COVID cases. Does a warmer climate cause a higher new case rate of COVID in these cities? Does higher humidity mean higher percentage of cases? We also analyze the latitude of each city to see if that relates to climate and COVID-cases as well by utilizing Google API.


## Data Gathering:
There are three sources of Data in our project :-

Visual Crossing API - historical weather
https://www.visualcrossing.com/weather-data 

Track the Recovery Data
https://tracktherecovery.org 

Coordinate data from Google API
https://developers.google.com/maps/documentation/geocoding/start

## Data Cleaning :

1) Covid Data - Track the recovery put their data into multiple CSV broken down by multiplie categories including COVID deaths, cases, gps data for metropolitan areas, consumer spending, job positings etc. We decided that we wanted to use COVID cases and GPS data to see if increased time outside lead to increased cases among other tests. We merged three data sets together (city data, covid daily cases data, and google mobility data) to create our usable data set. Since the 10 cities we picked have such a drastic range of populations we normalized the case data to be per million people. 

2) Weather Data - 


Analysis-

We use the CSV datasheets for both the COVID and Weather to perform 9 different analysis to find conclusions.
We divided our analysis in following parts:

1) Average Temperature (F) vs. New Case Count (Monthly) - All Cities
2) Average Temperature (F) vs. New Case Count (Monthly) - Detroit
3) Relative Humidity (%) vs. New Case Count (Monthly) - All Cities
4) Relative Humidity (%) vs. New Case Count (Monthly) - Detroit
5) Avg Time spent away from Home(vs the baseline) vs New Covid Case Count
6) Detroit Time spent away from home(vs the baseline) vs New Covid Cases
7) Avg Time spent away from Home(vs the baseline) vs Average Monthly Temperature
8) Detroit Avg Time spent away from Home(vs the baseline) vs Average Monthly Temperature
9) Latitude vs. Total New Cases (March - September)

1 & 2) Average Temperature (F) vs. New Case Count (Monthly) - All Cities & Just Detroit
**Step 1 : Identifying the data **

For our first and second analysis we wanted to see if average monthly temperature had any effect on monthly new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.

The two below charts are shown below:









## Final Analysis & Limitations:

Based on our research, we can conclude that there is no strong correlation between the ten cities' weather (temperature/relative humidity) and increases with new COVID cases. In regards to time spent outside, we did find a positive correlation between increased temperatures and time spent away from the home. However, as the populations spent more time away from home, the COVID new cases did not increase.

1) Individual City/State Reaction to COVID 

A. Did the cities in our study put Stay at Home Orders in place? If so, when did the initial order start and how long did it last? 

B. Outside of Stay at Home Orders, were restrictions on public places put in place? How strict were the guidelines for people being allowed to leave their homes?

2) Sample Size and Profile 
  
A. Did 10 cities accurately reflect the country? B. Could we have found better data sources to pull both the historical weather, COVID tracker, and GPS data from?

3) Weather Standards 
 
A. What is considered normal weather for the selected cities? Are we able to see outliers in weather patterns that may had led to an increase/decrease in cases or time spent outside the home?

4) Time-Series Data 
  
A. What other factors occurring during the same time could have led to our conclusions?
