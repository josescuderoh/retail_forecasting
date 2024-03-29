# Summary


# Problem Statement

A large north american retailer  operates 11,450 stores in 27 countries, managing inventory across varying climates and cultures. Extreme weather events, like hurricanes, blizzards, and floods, can have a huge impact on sales at the store and product level. 

They want to accurately predict the sales of 111 potentially weather-sensitive products (like umbrellas, bread, and milk) around the time of major weather events at 45 of their retail locations.

Intuitively, we may expect an uptick in the sales of umbrellas before a big thunderstorm, but it's difficult for replenishment managers to correctly predict the level of inventory needed to avoid being out-of-stock or overstock during and after that storm. They rely on a variety of vendor tools to predict sales around extreme weather events, but it's an ad-hoc and time-consuming process that lacks a systematic measure of effectiveness.

## Assumptions

1. These are the records of all transactions involving the 111 "weather-sensitive" products from 2012 to 2014.
2. Stores with similar weather behavior will grouped into cities and people from the city is expected to present the similar weather sensiste shopping patterns.

## Exploratory Analysis

Some highlights about EDA:

1. Overall sales trend is in **decline** for these products.
2. There is significant **seasonality in the sales**, which is why forecasting sales for most representative products could be important for the company.
3. About 92% of the sales are represented by the top 10 products in sales (out of 111), being the top 3 (45, 9 and 5) accountable for 61%, which is over 2.7 M products during the three years. These top 3 products will be used for this analysis.
4. There's demand variability over time, with an overall declining trend for all top 3 products. 
5. There are significant null values in some weather stations, this require some data preprocessing.
6 Station 5 and station 8 (and all stores related to these stations) **will be ommited** from the analysis since these time-series are incomplete and mostly null.
7 We can evidence that, the behavior across stations is not constant at all, hence, we will will not be able to aggregate the data in order to generate predictions for the whole company warehouse.
8. Our approach is to generalize the model across weather conditions. This is to say, clustering the stores given its weather and then model the sales for products of each cluster (called cities in this analysis).

## Data preprocessing

Some steps were performed for preprocessing the data before analysis:

* The data was queried according to EDA performed, extracting only relevant products and weather stations.
* The column for weather features `codesum` was broken appart into multiple columns in order to identify extreme events such as: tornadoes, thunderstorms, hail, rain, snow, etc. For more information visit the [docs](Docs/noaa_weather_qclcd_documentation.pdf).
* A variable describing the number of items sold the previous day at the specific store was added to as a feature.
* A flag for indicating if the day was weekend or weekday was implemented.
* The month of the year was included as a cyclical variable by transforming it into two components (sine and cosine) or polar coordinates. This helps us define proximity between first month of a year and last month of the previous year.
* Added a city variable using the clusters obtained from step 8 in EDA.
* Removed NAs by imputing a local average around the NA using a 5 previous and following rows.

## Modeling

*

## References

* Watanabe, T., Muroi, H., Naruke, M., Yono, K., Kobayashi, G., & Yamasaki, M. (2016, December). Prediction of regional goods demand incorporating the effect of weather. In 2016 IEEE International Conference on Big Data (Big Data) (pp. 3785-3791). IEEE.