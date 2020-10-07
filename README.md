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

2) Weather Data - Visual Crossing API allows the user to download a designated amount of time of historical weather date for specified locations.  You can download it for each individual city, or as one large CSV of all cities for all specified times. In the case of this project, we downloaded the monthly averages from January to September for all 10 cities into one CSV. After analyzing the data and attempting to merge with the COVID data from track the recovery, we noted that we needed to delete all January and February data, focusing solely on March through September. After looking at the data, the cleaning was simple as the file was fairly clean.  For the Humidity test, we did have to replace NaN values as they downloaded as 'NaN' rather than 0 for humidity in San Francisco.  Outside of cleaning up the headers to be a nicer format, the data cleaning was streamlined.  We then used iloc to break down the large dataframe in to Detroit specific data to look at a smaller sample size of the population. 


## Analysis:

We use the merged datasets for both the COVID and Weather to perform 9 different analysis to find conclusions.
We divided our analysis in following parts:

1) Average Temperature in Detroit from March to Septemer 2020
2) New Cases of COVID (per million people) in Detroit from March to September 2020
3) Average Temperature (F) vs. New Case Count (Monthly) - All Cities
4) Average Temperature (F) vs. New Case Count (Monthly) - Detroit
5) Relative Humidity (%) vs. New Case Count (Monthly) - All Cities
6) Relative Humidity (%) vs. New Case Count (Monthly) - Detroit
7) Avg Time spent away from Home(vs the baseline) vs New Covid Case Count
8) Detroit Time spent away from home(vs the baseline) vs New Covid Cases
9) Avg Time spent away from Home(vs the baseline) vs Average Monthly Temperature
10) Detroit Avg Time spent away from Home(vs the baseline) vs Average Monthly Temperature
11) Latitude vs. Total New Cases (March - September)




3 & 4) Average Temperature (F) vs. New Case Count (Monthly) - All Cities & Just Detroit

For our first and second analysis we wanted to see if average monthly temperature had any effect on monthly new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.

The two below charts are shown below:

![alt text](https://github.com/[username]/[reponame]/blob/[branch]/image.jpg?raw=true)




From these charts you can see that their is almost no coorelation between avg monthly temperature and new monthly cases per million people in the cities as a whole and just Detroit. We can see a slight increase in cases as temperature goes up in the first chart but it is not enough to be able to predict the number of cases at a certain temperature. Detroit shows us a different story with cases decreasing slightly as avgerage monthly temperature raised. This could be due to warmer temperatures coming later in the year after the height of COVID died down but without more data we cannot confirm that.


5 & 6) Relative Humidity (%) vs. New Case Count (Monthly) - All Cities & Just Detroit

For these analyses we wanted to see if average monthly relative humiditiy had any effect on monthly new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.

The two below charts are shown below:






From these charts you can see that their is almost no coorelation between avg monthly relative humiditiy and new monthly cases per million people in the cities as a whole and just Detroit. We can see a slight increase in cases as humidity goes up in the first chart but it is not enough to be able to predict the number of cases at a certain humidity percentage. Detroit shows us a different story with cases decreasing slightly as avgerage monthly humidity raised.

7 & 8) Avg Time spent away from Home(vs the baseline) vs New Covid Case Count - All Cities & Just Detroit

For these analyses we wanted to see if average time spent away from home had any effect on new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. All of this data was provided by "Track the Recovery" so after we normalized the case coust to per million and cleaned up the data in previous steps we had everything we needed to show this scatter plot. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.

The two below charts are shown below:

9 & 10) Avg Time spent away from Home(vs the baseline) vs Average Monthly Temperature - All Cities & Just Detroit

For these analyses we wanted to see if average monthly temperature had any effect on average time spent away from home in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.


The two below charts are shown below:


11) Latitude vs. Total New Cases (March - September)
 

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
