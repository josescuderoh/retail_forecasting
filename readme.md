# Summary

A large north american retailer  operates 11,450 stores in 27 countries, managing inventory across varying climates and cultures. Extreme weather events, like hurricanes, blizzards, and floods, can have a huge impact on sales at the store and product level. 

They want to accurately predict the sales of 111 potentially weather-sensitive products (like umbrellas, bread, and milk) around the time of major weather events at 45 of their retail locations. 

Intuitively, we may expect an uptick in the sales of umbrellas before a big thunderstorm, but it's difficult for replenishment managers to correctly predict the level of inventory needed to avoid being out-of-stock or overstock during and after that storm. They rely on a variety of vendor tools to predict sales around extreme weather events, but it's an ad-hoc and time-consuming process that lacks a systematic measure of effectiveness. 

## Assumptions

1. Weather stations are within the same city
2. Behavior of product sales across all stores has similar characteristics.
3. These are the records of all transactions involving the 111 "weather-sensitive" products from 2012 to 2014.

## EDA

Some highlights about EDA:

1. Overall sales trend is in decline for these 111 products.
2. There is significant seasonality in the sales, which is why forecasting sales for most representative products could be important for the company.
3. About 92% of the sales are represented by the top 10 products in sales (out of 111), being products 45, 9 and 5 accountable for about 61% of the total items sold, which is over 2.7 M products during the three years. These top 3 products will be used for this analysis.
4. The variability in the demand changes over time, with an overall declining trend for all top 3 products. 
5. There are significant null values in weather stations, this require some data preprocessing.
6 Station 5 and station 8 (and all stores related to these stations) will be ommited from the analysis since these time-series are incomplete and mostly null.
7 We can evidence that the behavior across stations is not constant at all, hence, we will will not be able to aggregate the data in order to generate predictions for the whole company warehouse.
8. Our option is to generalize the model across weather conditions. This is to say, we can treat each day at each store as a data point that results in a count of sales at each store for each product.

## Data preprocessing

Some processes were carried out for preprocessing the data before analysis:

* The data was queried according to EDA performed.
