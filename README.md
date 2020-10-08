# MSU-Project1
## Does climate impact the number of COVID cases?

This analysis takes a look at climate factors, including temperature and humidity, for ten cities around the United States. Additionally, we look at the impact the climate factors have on time outside of the home in comparison to the amount of COVID cases. Does a warmer climate cause a higher new case rate of COVID in these cities? Does higher humidity mean higher percentage of cases? We also analyze the latitude of each city to see if that relates to climate and COVID-cases as well by utilizing Google API.

## Conclusion & Presentation
Please reference the google slide presentation for an overall conclusion and synopsis of our study.


[Google Slide Presentation](https://docs.google.com/presentation/d/1dTi3ePExsWxlIbdCpVKDt8ftej8rfsQZBBAf_oh08Ek/edit?usp=sharing)


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


<b> 1 & 2) Average Temperature in Detroit from March to September 2020 & New Cases of COVID (per million people) in Detroit from March to September 2020</b>

[![Cases in Detroit](https://www.linkpicture.com/q/tempcaseslinedetroit.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)
[![Temperature in Detroit](https://www.linkpicture.com/q/tempdetroit.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)

The above charts tell story of the temperature in Detroit and the new cases of COVID over the time of the study, March to September 2020. You can see from the data that the temperature follows the normal pattern of the seasonal change in Michigan with it increasing in temperature for the mid year months and starting to cool down going in to fall. For the COVID cases, we see a high spike in cases in the early time of the study, April and May, when the pandemic was in full force.  The cases decreased in Detroit until June where they increased and followed the same pattern as the temperature increase/decrease in Detroit.  This sparked further testing to see if there was truly a relationship between the temperature and the number of cases for the 10 cities and Detroit specifically.

<b>3 & 4) Average Temperature (F) vs. New Case Count (Monthly) - All Cities & Just Detroit</b>

For our first and second analysis we wanted to see if average monthly temperature had any effect on monthly new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.

<i>The two below charts are shown below:</i>

[![Temperature vs. Cases All Cities](https://www.linkpicture.com/q/tempcasesall.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)
[![Temperature vs. Cases Detroit](https://www.linkpicture.com/q/tempcasesdetroit.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)



From these charts you can see that their is almost no coorelation between avg monthly temperature and new monthly cases per million people in the cities as a whole and just Detroit. We can see a slight increase in cases as temperature goes up in the first chart but it is not enough to be able to predict the number of cases at a certain temperature. Detroit shows us a different story with cases decreasing slightly as avgerage monthly temperature raised. This could be due to warmer temperatures coming later in the year after the height of COVID died down but without more data we cannot confirm that.


<b>5 & 6) Relative Humidity (%) vs. New Case Count (Monthly) - All Cities & Just Detroit</b>

For these analyses we wanted to see if average monthly relative humiditiy had any effect on monthly new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.

<i>The two below charts are shown below:</i>

[![Humidity All Cities](https://www.linkpicture.com/q/newcaseshumidityall.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)
[![Humidity in Detroit](https://www.linkpicture.com/q/humiditynewcasesdetroit.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)


From these charts you can see that their is almost no coorelation between avg monthly relative humiditiy and new monthly cases per million people in the cities as a whole and just Detroit. We can see a slight increase in cases as humidity goes up in the first chart but it is not enough to be able to predict the number of cases at a certain humidity percentage. Detroit shows us a different story with cases decreasing slightly as average monthly humidity raised.

<b>7 & 8) Avg Time spent away from Home(vs the baseline) vs New Covid Case Count - All Cities & Just Detroit</b>

For these analyses we wanted to see if average time spent away from home had any effect on new cases of covid (per million people) in the 10 cities for our study and then in just Detroit. All of this data was provided by "Track the Recovery" so after we normalized the case count to per million and cleaned up the data in previous steps we had everything we needed to show this scatter plot. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the r-value to determine coorelation.

<i>The two below charts are shown below:</i>

[![Time Away New Cases All Cities](https://www.linkpicture.com/q/newcasestimeawayall.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)
[![Time Away New Cases Detroit](https://www.linkpicture.com/q/awaynewcasesscatter.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)



<b>9 & 10) Avg Time spent away from Home(vs the baseline) vs Average Monthly Temperature - All Cities & Just Detroit</b>

For these analyses we wanted to see if average monthly temperature had any effect on average time spent away from home in the 10 cities for our study and then in just Detroit. Since we merged our weather data and covid data together all of the data we needed to show this scatter plot was all in one place. A linregress function was done on the data (x=temperature, y=new cases per million people) so we could get both slope and intercept for our linear equation and the rvalue to determine coorelation.


<i>The two below charts are shown below:</i>


[![Time Away Temp All Cities](https://www.linkpicture.com/q/timeawaytempscatter.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)
[![Time Away Temp Detroit](https://www.linkpicture.com/q/monthlytemptimedetroit.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)


From the above graphs and the regression line, we can see that specifically in Detroit there is a strong positive correlation between the average Temperature and the amount of time people are spending outside of their homes. The corrleation coefficient is 0.81 meaning there is a strong positive correlation.
The Linear Regress model for this is y=148.02x + 80.48.  We are confident in stating that as the temperature increases, the time spent outside of the home increases. We also see this same trend throughout the scatterplot taking in to account all 10 cities in the study. 


<b>11) Latitude vs. Total New Cases (March - September)</b>
 
 [![Latitude Cases](https://www.linkpicture.com/q/latitude.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)





## Hypothesis Testing

Independent t-tests will compare the means of 2 independent populations. 

Assumptions 
-Data is normally distributed
-Data is independent
-Data is homogenous (The standard deviations are roughly equal)


<b>Null Hypothesis</b> Cities with an average temperature greater than 70 are not less likely to have a higher amount of new COVID cases, compared to cities with average temperatures less than 70.


<b>Alternative Hypothesis</b> Cities with an average temperature greater than 70 are likely to have higher new COVID cases, compared to cities with average temperatures less than 70.

We picked two cities that we noted have varying differences in temperatures, with Detroit's average at 61.2 and Miami's average at 81.6, in order to test if the warmer temperature increased COVID cases over this time study.

Below you can see boxplots showing the spread of temperatures for both Detroit and Miami.  We calculated the statistical summary of each city to determine the mean averages listed above. These are independent populations being tested using a T-Test.


[![Detroit Temperatures](https://www.linkpicture.com/q/tempboxplotdetroit.png)](https://www.linkpicture.com/view.php?img=LPic5f7e53563281e864952677)
[![Miami Temperature](https://www.linkpicture.com/q/tempboxplotmiami.png)](https://www.linkpicture.com/view.php?img=LPic5f7e5c35ca353310964748)


<b>Significance Level</b> The significance level is 0.05


<b>P-Value</b> The P-Value is calculated to be 0.19


<b>Conclusion</b> After conducting a statistical test comparing the new COVID cases in both Detroit and Miami over the 6 month span, we determined the p-value to be 0.19. This is above the desired significance level of 0.05 and thus fails to reject the null hypothesis. Based on the test, there is no support that the (altherntive) hypothesis stating that temperatures above 70 causes there to be more new COVID cases.
Population1 below is Detroit's new cases per million people and Population2 below is Miamia's new cases per million people.



## Final Analysis & Limitations:

<b>Based on our research, we can conclude that there is no strong correlation between the ten cities' weather (temperature/relative humidity) and increases with new COVID cases. In regards to time spent outside, we did find a positive correlation between increased temperatures and time spent away from the home. However, as the populations spent more time away from home, the COVID new cases did not increase.</b>

The relationships between temperature and cases, humidity and cases, and latitude and cases all showed weak correlations, if any. We did find that time spent outside increased as temperatures increased.  With 81% of the data being represented by the regression line, we could with slight confidence use our regression line to predict the average amount of time spent outside based off a given temperature.  We looked to see if there was a transitive property bridging temperature to time spent outside to new cases, however; the time spent outside did not have a strong correlation with the number of cases amongst all cities in the study. 

Finally, we utilized a T-Test to test the alternate hypothesis that cities with average temperatures over 70 saw higher COVID cases.To do so we utilized Miami and Detroit as independent populations. These cities had average temperatures of 61.2 and 81.6, however; the t-test came back with a p-value of .19, showing there is no support to the alternative hypothesis. 

<b>Overall, after analyzing multiple factors of weather and their impact on COVID cases around the US, there is no strong correlation between the two. </b>


### 1) Individual City/State Reaction to COVID 


A. Did the cities in our study put Stay at Home Orders in place? If so, when did the initial order start and how long did it last? 

B. Outside of Stay at Home Orders, were restrictions on public places put in place? How strict were the guidelines for people being allowed to leave their homes?


### 2) Sample Size and Profile 
  
A. Did 10 cities accurately reflect the country? B. Could we have found better data sources to pull both the historical weather, COVID tracker, and GPS data from?

### 3) Weather Standards 
 
A. What is considered normal weather for the selected cities? Are we able to see outliers in weather patterns that may had led to an increase/decrease in cases or time spent outside the home?

### 4) Time-Series Data 
  
A. What other factors occurring during the same time could have led to our conclusions?
